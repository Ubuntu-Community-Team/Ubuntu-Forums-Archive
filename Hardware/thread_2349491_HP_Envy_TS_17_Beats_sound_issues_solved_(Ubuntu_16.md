---
title: "HP Envy TS 17 Beats sound issues solved (Ubuntu 16.04)"
date: 2017-01-15
forum: Hardware
---

### Post by Ramaddan on 2017-01-15
Hi,

I have gone through a few years with this problem, and I finally solved it, and decided to share the years of pain, so that others can benefit from it, and hope it reduces their anxiety and pain.

I have always had problem with Beats on Ubuntu through a few versions, and sometimes it would work somewhat and sometimes less, depending on kernel version, where I would suddenly lose more or gain something.

In the end, I decided to look more into it, and finally came across the following, which gave some explanation and was very useful, so thanks to the person who wrote it:
[http://www.asyndetic.com/2013/04/11/on-debugging-intel-high-definition-audio-in-linux-part-i/](http://www.asyndetic.com/2013/04/11/on-debugging-intel-high-definition-audio-in-linux-part-i/)

And many other threads such as the following:
[http://www.linux.org/threads/beats-audio-on-linux.4443/](http://www.linux.org/threads/beats-audio-on-linux.4443/)

As well as the following for the final touch:
[http://askubuntu.com/questions/225017/how-do-i-change-which-audio-jacks-are-used-for-input-and-output/225594#225594](http://askubuntu.com/questions/225017/how-do-i-change-which-audio-jacks-are-used-for-input-and-output/225594#225594)

I thank all those who worked on this before me and shared their efforts.

You can find the model of your HP Envy by doing the following:
> sudo dmidecode | grep -A3 '^System Information'


You can also see if you have the same HDA codec as me with the following, just to double check and reference:
> cat /proc/asound/card*/codec* | grep Codec

Mine gives out:> 
Codec: Intel Haswell HDMI
Codec: IDT 92HD91BXX

We are interested in second one, not the HDMI, which is the 92HD91BXX codec.

So using both [HDA Analyzer]("http://www.alsa-project.org/main/index.php/HDA_Analyzer") (you will need to use "sudo", and make sure that "python-gtk2" is installed) and HDA Jack Retask (present in 16.04 repo under alsa-tools-gui), I finally managed to get most of my sound out of the speakers, adjust the volumes as I wish, and the headphone jack to work, which was a big problem for many.

To save some time and effort, I will try to explain a bit of what I did, and give the settings I used that got everything working.


1) First, HDA analyzer was not that intuitive, and thus I ended up relying on HDA jack retask to get speakers to turn on, and the headphones to detect.

The main key was to play with the following pins for the speakers:
> 0x0d -> Internal Back speakers
0x0f -> Internal speakers
0x10 -> Internal LFE/Center speaker

The following were for the line out rewiring:
> 0x0b -> Line out front
0x0c -> line out back
0x0e -> line out center

Don't touch the rest.

A picture is attached to help, an it should also show here:
[IMG]https://ubuntuforums.org/attachment.php?attachmentid=273212&d=1484492197[/IMG]

For some reason, the headphone jack, which is pin 0x0b on HDA Jack retask was the most confusing, as it also controls the capability to be able to control speaker volumes together, and at the same time, to detect the headphones and play through them, and I finally figured out how to set it up.

After you have chosen the correct settings and pins, click on:
> Install boot override

You will need to restart for this to take effect.


2) Now after restarting, we will need to make a few modifications.

Honestly, I got so tired after the many trial and errors I did for so long that I will just pass you the final settings I settled for.

You can run HDA analyzer yourself and fiddle around with it if you want, but I eyes might start getting an allergic reaction due to over exposure if I look at it again.

The file is attached with the final settings I did.

What is important to do with this file is to save it as:
> /etc/hda-mods.py

I will also quote what is contained in the hda-mods.py file just in case the attachments do not work:
> 
#!/usr/bin/env python

import os
import struct
from fcntl import ioctl

def __ioctl_val(val):
  # workaround for OverFlow bug in python 2.4
  if val & 0x80000000:
    return -((val^0xffffffff)+1)
  return val

IOCTL_INFO = __ioctl_val(0x80dc4801)
IOCTL_PVERSION = __ioctl_val(0x80044810)
IOCTL_VERB_WRITE = __ioctl_val(0xc0084811)

def set(nid, verb, param):
  verb = (nid << 24) | (verb << 8) | param
  res = ioctl(FD, IOCTL_VERB_WRITE, struct.pack('II', verb, 0))  

FD = os.open("/dev/snd/hwC1D0", os.O_RDONLY)
info = struct.pack('Ii64s80si64s', 0, 0, '', '', 0, '')
res = ioctl(FD, IOCTL_INFO, info)
name = struct.unpack('Ii64s80si64s', res)[3]
if not name.startswith('HDA Codec'):
  raise IOError, "unknown HDA hwdep interface"
res = ioctl(FD, IOCTL_PVERSION, struct.pack('I', 0))
version = struct.unpack('I', res)
if version < 0x00010000:	# 1.0.0
  raise IOError, "unknown HDA hwdep version"

# initialization sequence starts here...

set(0x0c, 0x707,   0x40) # 0x0c070740 (SET_PIN_WIDGET_CONTROL)
set(0x0e, 0x707,   0x40) # 0x0e070740 (SET_PIN_WIDGET_CONTROL)
set(0x0f, 0x707,   0x40) # 0x0f070740 (SET_PIN_WIDGET_CONTROL)
set(0x10, 0x707,   0x40) # 0x10070740 (SET_PIN_WIDGET_CONTROL)

#set(0x0e, 0x701,   0x00) # 0x0e070100 (SET_CONNECT_SEL)
set(0x0f, 0x701,   0x02) # 0x0f070102 (SET_CONNECT_SEL)
#set(0x19, 0x701,   0x00) # 0x19070100 (SET_CONNECT_SEL)

set(0x0c, 0x701,   0x02) # 0x0c070102 (SET_CONNECT_SEL)
set(0x0d, 0x701,   0x02) # 0x0d070102 (SET_CONNECT_SEL)
set(0x0e, 0x701,   0x02) # 0x0e070102 (SET_CONNECT_SEL)
set(0x17, 0x701,   0x00) # 0x17070100 (SET_CONNECT_SEL)
set(0x19, 0x701,   0x00) # 0x19070101 (SET_CONNECT_SEL)

set(0x13, 0x300, 0xa07f) # 0x1303a07f (SET_AMP_GAIN_MUTE)
set(0x13, 0x300, 0x907f) # 0x1303907f (SET_AMP_GAIN_MUTE)
set(0x14, 0x300, 0xa07f) # 0x1403a07f (SET_AMP_GAIN_MUTE)
set(0x14, 0x300, 0x907f) # 0x1403907f (SET_AMP_GAIN_MUTE)
set(0x17, 0x300, 0xa02e) # 0x1703a0ae (SET_AMP_GAIN_MUTE)
set(0x17, 0x300, 0x902e) # 0x170390ae (SET_AMP_GAIN_MUTE)
set(0x18, 0x300, 0xa02e) # 0x1803a02e (SET_AMP_GAIN_MUTE)
set(0x18, 0x300, 0x902e) # 0x1803902e (SET_AMP_GAIN_MUTE)
set(0x1b, 0x300, 0x601f) # 0x1b03601f (SET_AMP_GAIN_MUTE)
set(0x1b, 0x300, 0x611f) # 0x1b03611f (SET_AMP_GAIN_MUTE)
set(0x1b, 0x300, 0x501f) # 0x1b03501f (SET_AMP_GAIN_MUTE)
set(0x1b, 0x300, 0x511f) # 0x1b03511f (SET_AMP_GAIN_MUTE)

set(0x1c, 0x300, 0xa01f) # 0x1c03a01f (SET_AMP_GAIN_MUTE)
set(0x1c, 0x300, 0x901f) # 0x1c03901f (SET_AMP_GAIN_MUTE)

set(0x0b, 0x707,   0xc0) # 0x0b0707c0 (SET_PIN_WIDGET_CONTROL)

# Set Internal Mic location
set(0x17, 0x701,   0x05) # 0x17070105 (SET_CONNECT_SEL)

os.close(FD)


3) Finally, you will have to do the following to keep changes.

As quoted from a previous post I mentioned above:
> edit /etc/rc.local as root (e.g. using gksudo gedit /etc/rc.local) and add the line python /etc/hda-mods.py right before the exit 0 line, then save it and reboot.

This will keep the changes done in HDA Analyzer when you reboot your machine.

Hope this is of benefit to anyone and helps frustrated people out there.


**Note: I cannot promise that I will check this post for comments, replies, etc, as said earlier, I am finally happy this is over :-P**

[B]
Note 2 (updated 23 Jan 2017): I just noticed a few things in case they come up for others:[/B]


1) You will need to set automute enabled in alsamixer in the terminal for line out, so that when you plug in the headphones, it turns OFF the speakers.

-> Problem is tough, it will always start the headphones as muted, and then you will have to reset the headphones volume to required level.


2) Even the headphone mic was fine, it turns out it took out the internal mic, but this was easily fixed with the following:

-> In HDA Jack Retask, set 0x11 to internal mic, and install boot override


3) When coming out of "suspend" mode, it seems to lose the volume settings set in HDA Analyzer and have been trying to call hda-mods.py when coming out of "suspend" mode, but it seems to conflict with hardware permissions.

-> I would be open to any suggestion for a fix.

If anyone has a more elegant solution for all the above three, it would be much appreciated, then this post can also be updated.


[B]UPDATE (3 May 2017) - Figured how to "tame" volume issue after coming back from suspend.
------------------------[/B]

The volume was always out of sync every time I came back from suspend, so this issue was tamed after adding a script to:
> /lib/systemd/system-sleep

This location seems to be for 15.10 and above. Not sure for 15.04.

Before 15.10 location seems to be:
> /etc/pm/sleep.d

The contents of the added script is copied here. The file was placed in /lib/systemd/system-sleep (for 16.04) and named zzzz_hdamods.

Of course, you can change the name accordingly, but keep in mind that the script was written with the above solution and locations in mind.

The content of the script is (formatting seems to disappear):
> #!/bin/bash

# This scripts makes sure to reset the HDA settings to the user's pre-defined settings

case "$1" in
      pre|suspend|suspend_hybrid|hibernate)
           # executed on suspend or hibernate
         ;;
      post|resume|thaw)	# executed when returning from suspend or hibernation
	   sudo /usr/bin/python /etc/hda-mods.py &
           su ramaddan -c  "pactl set-sink-volume 1 +1%"
           su ramaddan -c  "pactl set-sink-volume 1 -1%"
	   #su ramaddan -c  "/usr/bin/amixer -c 1 -M -D pulse set Master 1%+"
	   #su ramaddan -c  "/usr/bin/amixer -c 1 -M -D pulse set Master 1%-"
         ;;
      *)
         ;;
esac

Make sure to make the file executable by typing in terminal:
> sudo chmod +x /lib/systemd/system-sleep/zzzz_hdamods


The script also tries to give a kind of generic template that you can use for different versions of Ubuntu.

The "pre" and "post" cases for example were added for Ubuntu 15.10 and above, and the others were left for previous versions.

The "pre"case is currently empty, since it is not used, and the all other cases "*)", is also currently not used.

Notice that some commands have been commented it out, due to the fact that I found the "pactl" command to be more useful in this case, due to the fact that it lets you adjust volume beyond 100%, which the "amixer" command cannot do, but I left it just in case anyone needs it.

Keep in mind that the variables used in the commands are specific to my setup, and you might need to adjust it for yours, using "0" instead of "1", or some other number for example, after "set-sink-volume" or "-c" for example, to choose your specific card.

Again, this would not have been possible if it was not for the work of others, and in this case, these specific links:
[https://ubuntuforums.org/showthread.php?t=2349491&p=13594943#post13594943](https://ubuntuforums.org/showthread.php?t=2349491&p=13594943#post13594943)
[https://askubuntu.com/questions/97936/terminal-command-to-set-audio-volume](https://askubuntu.com/questions/97936/terminal-command-to-set-audio-volume)

I hope this helps anyone, and feedback and updates would be appreciated.

---

### Post by guido707 on 2017-05-12
Wow you made a great job. Unfortunately i tried but  this is too much, i am new on linux. I hope some day we can just download a simple file and that's it.   i could do it until the unconnected pins

---

### Post by Ramaddan on 2017-05-16
Hi,

I cannot promise that I can solve the problem or that I can reply soon, as I am during a busy phase right now.

However, to get things started, can you at least give me the exact codec number present on your laptop, so that we can make sure it is the same.

Other codecs, have different solutions, which is why it is hard to make a simple scripts code that will automatically fix everything for everyone on all laptops, until all codecs are solved.

However, that requires enough attention to all different models, which might not happen, because these different models of Envy might not be popular in the GNU/Linux world, not sure.

Open a terminal and copy paste what comes out with the following commands.

> sudo dmidecode | grep -A3 '^System Information'

> cat /proc/asound/card*/codec* | grep Codec

Regards

---

