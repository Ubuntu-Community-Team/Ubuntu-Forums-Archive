---
title: "Setup Guide:- Toshiba Dynabook UX/ NB200 / NB205"
date: 2009-07-17
forum: Hardware
---

### Post by Ultim8Fury on 2009-07-17
So you have a Toshiba NB200 / Dynabook UX / NB205. Some things don't work out of the box in Jaunty UNR 9.04. The following guide should help get as much as possible up and working. I'll try to keep it up to date. 

**_WiFi - _**

First and foremost if you want WiFi to work in Linux the DO NOT turn it off in Windows. A mistake I made and have learnt from. Turning off the WiFi in Windows will disable the WiFi in Linux, completely. The best you can hope for then is that the interface shows up in ifconfig. It will not broadcast or detect any signals. You can ensure it's on by the presense of the the WiFi LED on the front of the machine. 

Making WiFi work once activated is simply a matter of

```
sudo apt-get install linux-backports-modules-jaunty
```Congratulations you've made WiFi work. 

[U][B]
Sound -[/B][/U]

This being linux there are, as always, many paths to the same destination, configuring sound is no exception. 

_**The Easy and Partial Method.**_

The NB200 contains a Realtek ALC272 chip apparently this chip can be configured in many, many ways. The good news, the chip is supported in Linux by the ALSA drivers, the not so good news is that in UNR 9.04 the best you can currently hope for is headphone audio only. If you're willing to live without the latest software, apparently audio works fine in 8.04. Since the internal speakers on the NB200 are completely crap anyway, personally I'd rather have 9.04 and headphones. 

**update to the latest (1.0.20 ) Alsa drivers. **

add the following repository to your sources. 

[https://launchpad.net/~rlinfati/+archive/ppa]("https://launchpad.net/%7Erlinfati/+archive/ppa")

Instructions for how to add the PPA are listed on the site so I won't go over them here. Using your favourite package manager perform the update or from the command line. 

```
sudo apt-get update
sudo apt-get upgrade
```When complete, edit /etc/modprobe.d/alsa-base.conf using your favourite editor. Addthe following line to the bottom

```
options snd-hda-intel model=asus-mode4
```adjust the levels in alsamixer and reboot. Plug in some headphones or external speakers and you're good to go. 

_**Advanced but Complete Method**_

This method has been pointed out as fully working and will give speaker output, it is however significantly more involved and to my mind the speaker output just isn't worth the effort. However, for those that are willing to tinker, there is a detailed help tutorial [here]("https://help.ubuntu.com/community/OpenSound"). The general gist of it though it to remove the pulseaudio sound sever and the ALSA drivers and run on the OSS driver with the esound server instead. 

**_Video Playback Performance -_**

During playback of videos I noticed tearing of the material. After a little hunting I found that the problem is known about and fixed in the latest stable xorg release. 

Add the following PPA

[https://launchpad.net/~ubuntu-x-swat/+archive/x-updates]("https://launchpad.net/%7Eubuntu-x-swat/+archive/x-updates")

As above update your package list and upgrade a quick reboot and video is crisp and smooth.  

*update:: [further reading](http://ubuntuforums.org/showthread.php?t=1130582) on video performance in intel based systems *


**_Touchpad -_**

I couldn't seem to get the settings right on this for a few days, it was too sensitive and yet strangely sluggish at the same time. A bit of searching turned up the attached touchpad.fdi file. 

Download the attached file touchpad.fdi.gz and unzip it. As root copy the file to where it belongs and reboot. 

```
sudo cp touchpad.fdi /etc/hal/fdi/policy/
```after the reboot

```
apt-get install gsynaptics
```this program allows more complete setup of the touchpad than the included application but it requires the first step be performed before it will run. Something to do with SHMConfig option in the fdi file. I don't really understand it but I don't need to in order to know it made an appreciable difference. 


[U][B]Bluetooth - 
[/B][/U]
Unknown, I don't think it works but I don't know enough about using bluetooth under Linux to make a comment. 

_**Hibernate - **_

Suspend works from the moment the install is completed, however hibernate doesn't and whilst it's less used it's still nice to know it's there. 

First you need to install uswsusp

```
sudo apt-get install uswsusp
```This package give you access to two userspace utilities which allow suspend to disk and suspend to RAM. Since suspend to RAM works natively anyway I won't cover installing that portion however if you follow the link in the credits section it will take you to a tutorial covering that part. 

Begin by backing up the Ubuntu default script for hibernation so that in the event everything goes wrong you can restore it. 

*```
sudo cp /usr/lib/hal/scripts/linux/hal-system-power-hibernate-linux /usr/lib/hal/scripts/linux/hal-system-power-hibernate-linux.bak
```*
 
Then using your favourite text editor delete the contents of the file and replace it with

```
[I]#!/bin/sh
/usr/sbin/s2disk[/I]
```[I]

save the file and exit. 

Find out where your swap partition is kept. 

```
cat /etc/fstab
```Note the line which tells you. Mine is  /dev/sda6 yours may or may not be the same it depends on how you've partitioned your drive. 

edit the grub menu to include the resume partition so that everything comes back the way it should. 

```
sudo jed /etc/grub/menu.lst
``` ( where jed is my favourite editor ) 

add the line ```
resume=/dev/sda6
``` where, as stated above sda6 is your swap partition. Save the file and exit.

```
sudo update-grub
``` and you're done. 



[/I] **_Internal G-Sensors -_**

Fairly sure these don't work but I understandably didn't want to try too hard to crash the heads on my HDD. Under Windows they require a Toshiba supplied driver to function so it's safe to say that they probably don't work yet under Linux. 


My only remaining issue that bugs me a little. Is that if I'm downloading something sizable and don't touch the laptop at all for a few seconds it seemingly freezes until you move the touchpad. The length of time is not fixed it could be 3 minutes it could be 3 seconds. But it won't do anything until you move the mouse. Very strange and I'm sure there must be  a power management setting somewhere that's linked to inactivity but I've checked all the obvious ones and they made no difference. 


At this point everything else should work as far as I can see.


[SIZE=3]_**Credits**_[/SIZE]

Credit is due to the following people and websites who have both intentionally and unintentionally aided in the building of this guide.

Yorkzhang for the ALSA sound solution
Harty83 for the OSS and Hibernate solutions. 
[http://tjmcgrew.com/](http://tjmcgrew.com/) - For WiFi solution 
[https://help.ubuntu.com/community/OpenSound](https://help.ubuntu.com/community/OpenSound) - For OSS setup guide
[http://jrobbo.com/blog/?p=37](http://jrobbo.com/blog/?p=37)  - for Hibernate

---

### Post by dimeotane on 2009-07-17
If you think your webcam video is looking choppy, make sure you have enough bright light, to avoid getting slow frame rates. 

If that doesn't solve the issue you may wish to try changing gstreamer-properties video output

see here:  [http://live.gnome.org/Cheese/FAQ#head-fb51597a3f48dfc21f2d288bf07cf78ce00b2802]("http://live.gnome.org/Cheese/FAQ#head-fb51597a3f48dfc21f2d288bf07cf78ce00b2802")

---

### Post by harty83 on 2009-07-20
We've been discussing similar things [here]("http://ubuntuforums.org/showthread.php?t=1203480").  You can get basic sound working via OSS but as pointed out, the speakers suck by nature so don't expect much when you get it working :-)

I couldn't get hibernate working out of the box for the nb205 and had to use s2disk which works beautifully (and much quicker) than the standard.

I would love for someone to figure out how to get bluetooth working!! 

Thanks,
Alan

---

### Post by Ultim8Fury on 2009-07-20
do you mind if I add the hibernate tip to my list ? I kinda want it to be a one-stop setup thread.

---

### Post by harty83 on 2009-07-20
> **Ultim8Fury said:**
> do you mind if I add the hibernate tip to my list ? I kinda want it to be a one-stop setup thread.

Please do! You are welcome to put the OSS work around as well if you want.  

Thanks,
Alan

---

### Post by calibre97 on 2009-07-22
Heads up: Wifi still not working using Linux Mint 7 (based on Ubuntu 9.04). I've completely updated the system and installed the backports AND installed WiCD. At no step has wireless worked. Period. Granted, that's with Mint 7. Since I've got XP working fine on mine, I'll go ahead and try your setup guide using straight Ubuntu.

---

### Post by solidus126 on 2009-07-23
Hello all,

A bit back I was working on documentation for setting up the NB205 with UNR.  I started a (rather plain) wiki page on the Ubuntu documentation wiki directory:

[https://wiki.ubuntu.com/HardwareSupport/Machines/Netbooks/ToshibaNB205](https://wiki.ubuntu.com/HardwareSupport/Machines/Netbooks/ToshibaNB205)

It is fairly sparse at the moment, and I would love to see more edits made to it as time is a little lacking on my part.  I personally have not tested hibernate, bluetooth, full speaker support, and etc.

I hope that the visibility of the wiki will make the information even easier to access for those in need, and it is in fairly good need of more edits from those who have tried the tweaks I have not.

Happy computing,

-solidus126

---

### Post by harty83 on 2009-07-27
Just as a fyi for jaunty, uswsusp installs s2disk, etc in /usr/sbin rather than /sbin.

Thanks,
Alan

---

### Post by phi.schmidt on 2009-07-28
Thanks for these fantastic instructions! Worked perfectly for me. I have two remaining issues, and hope someone can help me. I suspect the issue is related to the NB200, but if it needs to be moved into a different thread, I'd kindly ask one of the admins to do so.

* Skype Audio: I can't get skype audio to work. Unfortunately most of my colleagues use skype extensively, and this is a crucial feature for me. In Options -> Sound Devices, I can see my headset is recognised. It lets me choose:

Sennheiser USB Headset (hw:Headset,0)
 ... or 
Sennheiser USB Headset (plughw:Headset,0)

as Sound In, Sound Out, or Other Sound device, but I can't hear anything on the headphones. I did test general audio with the headset before - and can listen to audio. 

I am not sure what information to post here in order to make it easier for others to troubleshoot, so please let me know how to find the information you would need to help.

* Less important: Video playback of youtube videos in Firefox is still very very choppy. If I download the files, I can play them at good quality using the standard Totem Movie Player 2.26.1 (Movie Player using GStreamer 0.10.22) 

Thanks for any ideas, pointers, comments!

P

---

### Post by Nick255 on 2009-07-28
Have you checked to see if the 2.6.30.3 kernel packages at [http://kernel.ubuntu.com/~kernel-ppa/mainline/v2.6.30.3/](http://kernel.ubuntu.com/~kernel-ppa/mainline/v2.6.30.3/) fix the issues with the wifi card not working if it is shut off in Windows?  It might also help with the sound issue.

---

### Post by mcgrew on 2009-07-31
@Ultim8fury - glad my wifi solution helped.

Has anyone else noticed that the wifi seems weak on the NB205? I can't seem to stay connected to my wireless router from across the house - the Dell I have running fedora connects just fine.I've had trouble with other wifi access points as well.

When I run a scan, *(iwlist wlan0 scan)*, all of the quality numbers are xx/70. Why 70 and not 100 like most laptops? I suspect this has something to do with the weak connections I get, and probably related to a power setting somewhere,  but I've yet to find a way to fix it. Anyone have any suggestions?

---

### Post by Ultim8Fury on 2009-08-01
Thanks for that.

 When I bought the netbook I went straight into the office and fired it up, being cautious of battery life I turned off the wifi and then within 5 minutes decided that XP wasn't staying on it. Half hour later and I'd wiped out Windows and was running jaunty. Still it's all good again now. 


Updated the main post to correct the hibernate command path. also added a link to the HUGE discussion regarding video performance on intel chipsets. Highly recommended reading since it goes further than the solution I posted.

---

### Post by spazzwig on 2009-08-01
Great post, thank you for pulling this info together. Have CrunchBang running on my nb205 very nicely now.

I don't suppose anyone has any xmodmap info for the keyboard? I would like to map FN+F9 back to a simple script to toggle the touchpad, the way the win driver is designed. Here's the script in case someone finds it useful... I've just aliased it to a key combo that works for the time being (Super+F9).

```

#!/bin/bash

if 
	synclient -l |grep -Pq TouchpadOff.*0;
	then synclient TouchpadOff=1 && echo Touchpad Off; 
	else synclient TouchpadOff=0 && echo Touchpad On; 
fi

```

There may be a better approach, and if so I'd love to know it. Otherwise, this seems to do the job, and all the better if it can be mapped to the original key command.

Thanks again for this great resource!

---

### Post by Leesa on 2009-08-02
Bluetooth is working with omnibook module:

[LIST=1]
[*]Get sources from [http://dl.getdropbox.com/u/362618/omnibook-source_2.20070211%2Bsvn20071217-1_all.deb](http://dl.getdropbox.com/u/362618/omnibook-source_2.20070211%2Bsvn20071217-1_all.deb)
[*]Make sure Bluetooth is enabled in Windows
[*]sudo apt-get install module-assistant build-essential
[*]sudo m-a a-i omnibook-source
[*]Try it: sudo modprobe omnibook ectype=14
[*]Make it autoload:
[/LIST]
 
[LIST]
[*]sudo nano /etc/modules
[*]Put "omnibook" at the latest line
[*]sudo nano /etc/modprobe.d/omnibook.conf:
[/LIST]
[INDENT]options omnibook ectype=14 userset=0 lcd=0 display=0 blank=0 battery=0 ac=0 bluetooth=1

[/INDENT]Works fine for my NB200, even enabling/disabling bluetooth via /proc/omnibook/bluetooth

---

### Post by harty83 on 2009-08-02
@Leesa: you are my hero!!!  How did you figure that out?  Works perfectly on my nb205 as well!  

@Ultim8Fury: please add this to your post ASAP!

Thanks,
Alan

---

### Post by harty83 on 2009-08-02
Well, it seems that after doing the bluetooth fix my touchpad is sluggish and does not recognize taps.  Anyone else experiencing this?

Later....never mind.  Had the sensitivity set too low in gsynaptics.

Thanks,
Alan

---

### Post by phoenix55 on 2009-08-03
External\internal microphones were not working on my NB200 after making the sound system alterations suggested by Ultim8Fury. I then came across the post:
[https://bugs.launchpad.net/ubuntu/+source/pulseaudio/+bug/354620?comments=all](https://bugs.launchpad.net/ubuntu/+source/pulseaudio/+bug/354620?comments=all)
specifically post #6 from Nighto. This suggested:
" ... System->Preferences->Sound->Sound Capture is set to "HDA Intel ALC268 Analog(ALSA)" not "ALSA"  ..."

After doing this the external microphone works (not really bothered about the built-in microphone so I don't remember testing it).

Now I can use Skype or other VOIP applications.

Postscript on 06/08/2009:

In my original post I stated that I hadn't tested the built-in microphone. This is to add the fact that the internal microphone on a NB200 DOES work after making the change I referred to above.

The volume is a bit low but. There is no +20dB Microphone Boost in the Volume Control GUI (Alsa Mixer). 

Joe P.

BTW. This thread is what enabled me to use Linux on my NB200. Thanks Ultim8Fury.

---

### Post by filipegatti on 2009-08-04
This thread is incredible and also enabled me to use Linux on my NB200. Unfortunately I tried what phoenix55 told and it did not work for me, so I still don't have the internal microphone working (tried Skype and Sound Recorder)

I don't even have this option in Sound Capture. Maybe this is because I'm using OSS in order to make my internal speakers work (as it doesn't work with ALSA).

Here follow how my Sound Preferences looks like, and for some reason I can't take a screenshot while clicking so the options for Sound Capture are:
# Alsa - Advanced Linux Sound Architecture
# OSS - Open Sound System
# PulseAudio Sound Server
# Test Sound
# Silent

[[IMG]http://img31.imageshack.us/img31/2306/screenshotens.th.png[/IMG]]("http://img31.imageshack.us/i/screenshotens.png/")

There is no other option in Devices as well, even if plugged external microphone or speakers.

In the other hand, WiFi is working perfectly, and so are my webcam and built-in speakers. The only problem I can see is the microphone not working.

---

### Post by harty83 on 2009-08-05
> **filipegatti said:**
> This thread is incredible and also enabled me to use Linux on my NB200. Unfortunately I tried what phoenix55 told and it did not work for me, so I still don't have the internal microphone working (tried Skype and Sound Recorder)

I don't even have this option in Sound Capture. Maybe this is because I'm using OSS in order to make my internal speakers work (as it doesn't work with ALSA).

Here follow how my Sound Preferences looks like, and for some reason I can't take a screenshot while clicking so the options for Sound Capture are:
# Alsa - Advanced Linux Sound Architecture
# OSS - Open Sound System
# PulseAudio Sound Server
# Test Sound
# Silent

[[IMG]http://img31.imageshack.us/img31/2306/screenshotens.th.png[/IMG]]("http://img31.imageshack.us/i/screenshotens.png/")

There is no other option in Devices as well, even if plugged external microphone or speakers.

In the other hand, WiFi is working perfectly, and so are my webcam and built-in speakers. The only problem I can see is the microphone not working.

To get the internal mic working with OSS you need to install ossxmix and open it.  The GUI sucks but gets the job done.  Look for Int Mic or something like that.  It will probably be set to mix2 or some other number.  Change it to input and adjust the volume.  The mic should work.  Switch it back and forth from mix#/input to enable/disable it.

Thanks,
Alan

---

### Post by filipegatti on 2009-08-06
> **harty83 said:**
> To get the internal mic working with OSS you need to install ossxmix and open it.  The GUI sucks but gets the job done.  Look for Int Mic or something like that.  It will probably be set to mix2 or some other number.  Change it to input and adjust the volume.  The mic should work.  Switch it back and forth from mix#/input to enable/disable it.

Thanks,
Alan
The ossxmix was already installed and indeed, the GUI really sucks. I changed the mix2-int-mic to input and it did not work at first. Actually all my sound was gone for a minute, then I restarted my session and everything - including the mic - was back.
If I try to use the Sound Recorder now I'm able to record any sound.

But, my Skype still doesn't recognize it. It gives me the "Problem with Audio Playback". I tried going to options in Skype and Audio Devices, but it only shows three options:
- Default device
- hdmi
- headset

And it doesn't work in any of them.
I didn't tried with a external mic, but it does'nt matter because the point here is to make the internal mic works.

Thank you anyway, the ossxmix was a great help, now my speakers are louder. :o

---

### Post by harty83 on 2009-08-06
Do you have the OSS version of skype installed?  

Thanks,
Alan

---

### Post by filipegatti on 2009-08-06
Actually I've downloaded the default Ubuntu version of Skype. Now that I looked, they have a Static OSS .tar.bz2 version. I'll give a try when I get home and post the results.

Thank you again.

---

### Post by harty83 on 2009-08-06
Add the [medibuntu repository]("https://help.ubuntu.com/community/Medibuntu") and you can install it from there via synaptic.

Thanks,
Alan

---

### Post by Nick255 on 2009-08-07
If you use the omnibook module with ectype=12, you can enable the wifi without needing Windows.  Also, do NOT enable bluetooth coexistance (do NOT use btcoex_enable=1) with the ath9k modules or wifi might not work.  I am sure getting sound to work fully with alsa is just a matter of trying different models for the snd-hda-intel module.  Also, the omnibook module might need to be removed before suspending/hibernating and re-loaded afterwards (this will cause kbluetooth4 to crash, so add export KDE_DEBUG=1 in your profile.  

Here is my options.conf:

options omnibook ectype=12 wifi=1 userset=1 bluetooth=1
options snd-hda-intel model=asus-mode4

---

### Post by ReneVYL on 2009-08-09
I see 60--80MB/s if I continuously move my finger on the touchpad when doing "dd bs=128K if=<7GB file> of=/dev/null". If I leave the touchpad alone, I get 1--6MB/s. (No typo: there's >10 times difference.)

Confirmed on 

[LIST]
[*]  UNR 09.04,
[/LIST]
[INDENT]
[LIST]
[*]with "pm-powersave true" and with "pm-powersave false",
[*]with and without the referenced touchpad.fdi,
[*]on ext3 and on ext4.
[/LIST]
[/INDENT]
[LIST]
[*]Ubuntu Desktop 09.04 (tested non-modified installation only),
[*]UNR 09.10, daily 20090810 (tested non-modified installation only).
[/LIST]
 

Anyone seeing something similar? Suggestions?


PS! Booting is somewhat faster (2--3x) if I similarly move a finger around on the touchpad, but I frequently end up with a non-functioning touchpad upon boot-up if I do that.

---

### Post by froggy7 on 2009-08-10
Thanks to Ultim8Fury for this useful thread!

I see the same freezes as ReneVYL...

Also, the sound quality of the internal microphone (using the ALSA solution suggested by Ultim8Fury) is much worse than in "the other OS".
Very quiet, and noisy.

Otherwise things work smoothly.

---

### Post by Leesa on 2009-08-10
Freezes: try to set kernel options nohz=off hpet=disable noapic.

```
/boot/grub/menu.lst:
# defoptions=quiet splash nohz=off hpet=disable noapic
```
Bluetooth & omnibook:> **harty83 said:**
> @Leesa: you are my hero!!!  How did you figure that out?  Works perfectly on my nb205 as well! 
Just found and tried bluetooth manual for Toshiba Satellite... And it worked.

---

### Post by ReneVYL on 2009-08-10
I believe my issue, see above [[http://ubuntuforums.org/showpost.php?p=7757745&postcount=25](http://ubuntuforums.org/showpost.php?p=7757745&postcount=25)], has now been fixed, by aligning the SSD's partitions to its block boundaries. Since doing that (and reinstalling) I am consistently seeing >100MB/s read speeds with dd, while the netbook is being left alone.

(That said, I am a little bit skeptical that misalignment can have that pronounced an effect but, just to be clear, I have not followed Leesa's suggestions nor done anything similarly explicit that I didn't do before.)


EDIT1: the increased dd-read speed apparently from properly aligning the partitions was a fluke, it seems. Alignment buys 10s of %, but I am back to sub-expected performance. Time to try the various suggestions by Leesa ...


EDIT2: Leesa's three suggestions: nohz=off hpet=disable noapic, seem to work. (Thanks, Leesa!) With all three in combination, I'm seeing 100--140+ MB/s read speeds, which is probably as much as can be expected from the little thing. Unfortunately, I'm out of time and will not be able to test the three options separately or in pairs for some time, unless using all three has a catastrophic impact on battery life. I'll update or repost if anything new comes up.


EDIT3: couldn't resist: nohz=off seems to be what makes (almost all) the difference. Additionally, powertop reports <8.5W idle power usage with nohz=off vs >11W when nohz=off is not specified.

---

### Post by filipegatti on 2009-08-11
I'm having this curious problem using UNR 9.04... I never used my netbook (Toshiba NB200) for a long time because I was in home and I have my desktop computer. But now that I'm using it, I can see that after some time, my WiFi stop working.

If I'm connected, after something like thirty minutes to one hour, I lose my connection and I can't connect back. I still can scan all the networks next to me, even my own network, but I can't connect, it stays as "connecting" for a few minutes until it does not connect at all.

I was using Windows before using UNR and the WiFi was working ok 24/7, that's why I've discarded a router problem (and I have other computers WiFi connected to this router and working).

I don't think anybody else here is having problems with the WiFi, but I'm having this curious one and I don't know what to do. I always lose my connection, so it's really pissing me off.

I, as anyone else, enabled the WiFi installing the linux-backports-modules-jaunty.

Someone else is having the same problem, or by any chance knows how to solve this?

---

### Post by epirsch on 2009-08-12
I have the same issue regarding WIFI reliability. Sitting next to my router, I get ~70%.

When I get disconnected, I try clicking againg on my network and when this fail, I disable wireless and re-enable it (right-click on the network icon).

---

### Post by froggy7 on 2009-08-12
How did you enable ACPI? I only see "no ACPI info available" in powertop when I try to see energy consumption...

---

### Post by ReneVYL on 2009-08-12
> **froggy7 said:**
> How did you enable ACPI? I only see "no ACPI info available" in powertop when I try to see energy consumption...

Don't know whether this helps: powertop only gives a Watt estimate on unplugged machines (because it relies on battery drain).

---

### Post by ReneVYL on 2009-08-12
As it turns out, the webcam is quite the little power consumer, @ around 1W when idle. Even when specifying "defoptions=... usbcore.autosuspend=1" (followed by "sudo update-grub" and a reboot), the webcam stays always on. (It never autosuspends.)


(The following is written based on the webcam being on bus 1 as device 3, i.e., device 1-2, where we count 0,1,2,... for devices --- verify with "lsusb".)


The standard trick, as it were, applies

[LIST]
[*] place a file (as root:root, with 755 permissions) in /etc/init.d/ with
[/LIST]
[INDENT]#!/bin/sh
echo suspend > /sys/bus/usb/devices/1-2/power/level[/INDENT]
[LIST]
[*]link to this file as "S<something>" from "/etc/rcS.d/"
[/LIST]

On every bootup, the camera is then put off automatically and permanently. (Verify with "lsusb"). Although I haven't confirmed the power draw, autosuspend can be had by "auto" in ".../power/level" (and always-on by "echo on").

---

### Post by froggy7 on 2009-08-13
I had the battery in and AC disconnected. It only gives me power information after collecting data for 5min. Perhaps this is related
to /proc/acpi/battery/BAT1/info giving a rate 0?

Thanks for the webcam suspend trick.

---

### Post by ReneVYL on 2009-08-13
> **froggy7 said:**
> Perhaps [5min.] is related to /proc/acpi/battery/BAT1/info giving a rate 0?

5 min is standard, for averaging.

> **froggy7 said:**
> Thanks for the webcam suspend trick.

It would appear that "suspend"ing the webcam interferes with sleep and hibernation of the machine; "auto" appears to be OK and the power draw appears to be in line with "suspend".

---

### Post by filipegatti on 2009-08-13
> **filipegatti said:**
> Actually I've downloaded the default Ubuntu version of Skype. Now that I looked, they have a Static OSS .tar.bz2 version. I'll give a try when I get home and post the results.

Thank you again.

Tried the OSS Skype version and worked perfectly. Also enabled the volume controller to be controlled by OSS and now I can turn on my internal microphone without needing to open the ossxmixer.

Thanks.

---

### Post by sorbus on 2009-08-13
> **Leesa said:**
> Freezes: try to set kernel options nohz=off hpet=disable noapic.

```
/boot/grub/menu.lst:
# defoptions=quiet splash nohz=off hpet=disable noapic
```


That's a rather heavy hammer; you're disabling tickless, high performance timers, and the IOAPIC. How about:
```
# defoptions=quiet splash processor.max_cstate=1
```

(assuming that your "processor" module is compiled in).

---

### Post by filipegatti on 2009-08-13
There is another thing which is getting on my nerves.
All the windows, while using the UNR default desktop (not the Ubuntu default), open maximized.

I've detected that a few softwares escape this rule. Pidgin is one of them. Unfortunately there is no way to disable the big and black message pop-up alert in Pidgin, so I changed to emesene, which does always open maximized, even the conversations windows open maximized, always.

Using some other softwares, like SCREEM or Bluefish, I've noticed that this also happens.
And also in Firefox a lot of times, if I try to see the source code of a page or properties of an item, these windows always come maximized.

I tried looking for something to change that in preferences, but without luck.
Maybe this is really easy to fix and I'm missing something, so please tell me if you know how to fix.

Thank you.

---

### Post by SirFunk on 2009-08-14
> **ReneVYL said:**
> As it turns out, the webcam is quite the little power consumer, @ around 1W when idle. Even when specifying "defoptions=... usbcore.autosuspend=1" (followed by "sudo update-grub" and a reboot), the webcam stays always on. (It never autosuspends.)

...

Although I haven't confirmed the power draw, autosuspend can be had by "auto" in ".../power/level" (and always-on by "echo on").

I tried this out. powertop was reporting 12.5 watts before i disabled it and 12.5 after. I let it sit a bit before and after to make sure nothing else was causing extra power usage. So, I think this doesn't really make a difference?:confused:

---

### Post by SirFunk on 2009-08-14
> **filipegatti said:**
> I'm having this curious problem using UNR 9.04... I never used my netbook (Toshiba NB200) for a long time because I was in home and I have my desktop computer. But now that I'm using it, I can see that after some time, my WiFi stop working.

...

Someone else is having the same problem, or by any chance knows how to solve this?

This happens for me to. I usually just restart NetworkManager /etc/init.d/NetworkManager restart and it's fine... However, you shouldn't have to do this. Maybe we should file this bug with ubuntu or the kernel?

---

### Post by SirFunk on 2009-08-14
OSSv4:

Just wanted to mention that OSSv4 does nto support suspending/resuming. I found a temporary solution to run soundoff via a suspend script and soundon an resume. This causes the mixera_applet to crash every suspend resume. I've reverted to alsa/pulse for now. I hope someone can get the speaker workign with alsa.

---

### Post by froggy7 on 2009-08-14
ReneVYL, I still envy you for your 8.5 watts idle... the best I get with powertop is 11w, which gives me roughly 6h, which, btw, is still much less than the advertised lifetime.

---

### Post by ReneVYL on 2009-08-15
> **SirFunk said:**
> I tried this out. powertop was reporting 12.5 watts before i disabled it and 12.5 after. I let it sit a bit before and after to make sure nothing else was causing extra power usage. So, I think this doesn't really make a difference?:confused:

There are many factors that affect power consumption, including whether the USB bus is allowed to go to sleep and for how long. If you have other USB devices attached, suspending the webcam will make less difference than if it is the only thing waking the bus up.

Procedure-wise, I'm testing for the lowest I can make the machine go, which does not (necessarily) translate to the longest battery life, of course. Concretely, I test by letting powertop run for more than 5mins after the screen turns off, not just dims, and then look at the reported number as I touch the touchpad and make the screen wake up. (I'm now down to 7.7W, by the way.)

I would imagine the biggest powersaver is the SSD I installed.

---

### Post by ReneVYL on 2009-08-15
> **sorbus said:**
> How about:
```
# defoptions=quiet splash processor.max_cstate=1
```(assuming that your "processor" module is compiled in).

That goes just as low as Leesa's combined three suggestions and as just using nohz=off on my system (7.7W). But, the system is able to stay in C1 for longer with processor.max_cstate=1 than with the others.

---

### Post by tzirtzi on 2009-08-16
Hi! :)

I'm in the process of setting up an NB200 to dual boot XP and Ubuntu - rather unsuccessfully, about which I've posted elsewhere... Anyway, I didn't read this (and other) thread(s) first, and so used the Ubuntu installer's automatic partitioner which has rendered XP non-working. I read that if I run the Windows/DOS utility *chkdsk*, it should fix this, and that this will run automatically if I put the harddrive in a working Windows computer. However, I don't have a torx screwdriver, which I would need to take the harddrive out, so I've been trying various other ways to run *chkdsk*.

The utility is on the Windows XP installation CD, so I've tried writing an image of that CD to a usb key and to a hard disk partition and booting from it - no success. I've also tried running *chkdsk* from the installation CD (copied to my hard drive) from DOSBox, but no success there either. Is there any way of doing this without taking the hard drive out, or am I banging my head against a brick wall?

Thanks!
-tzirtzi

---

### Post by tzirtzi on 2009-08-16
Some more details on the above:

* Check partition for errors in GParted runs and does nothing.
* ntfsfix says "Failed to determine whether /dev/hda2 is mounted: No such file or directory.
Mounting volume... Error opening partition device: No such file or directory.
Failed to startup volume: No such file or directory.
FAILED
Attempting to correct errors... Error opening partition device: No such file or directory.
FAILED
Failed to startup volume: No such file or directory.
Volume is corrupt. You should run chkdsk."
* chkdsk from the Windows install and from the Windows installation CD fail to run under Wine.
* BartPE gets a BSoD when starting and advises I run chkdsk.

---

### Post by filipegatti on 2009-08-17
More interesting info.

I've noticed that my Toshiba NB200 is always with no battery at all.
I charge my battery, then I use my netbook connected on AC Power. Ok, it shows that my battery is at 100%, no problem at all. Then I finish using my netbook and turn it off (Shut Down on options). After a few days, when I try to turn my netbook on using the battery, and not the AC Power, I can see that it doesn't turn on at all.
If I connect the AC Power, then it turns on and the battery starts charging like if it was on 0% (and it really was!)

Then I made some tests, I charged my battery, turned the netbook off and removed the battery. After a few days, I put the battery in again and everything was ok, running on battery with 100% charged (without AC Power).

Somehow, when I turn my netbook off, it still consumes my battery in a way that a couple of days later my battery simply runs out. Maybe Ubuntu is not shutting everything down? Leaving something working?

What is happening? This is really annoying. Anyone else with the same problem?

P.S.: I used it with the Windows XP for a month when I bought it and this didn't happen.

---

### Post by Nick255 on 2009-08-18
> **filipegatti said:**
> More interesting info.

I've noticed that my Toshiba NB200 is always with no battery at all.
I charge my battery, then I use my netbook connected on AC Power. Ok, it shows that my battery is at 100%, no problem at all. Then I finish using my netbook and turn it off (Shut Down on options). After a few days, when I try to turn my netbook on using the battery, and not the AC Power, I can see that it doesn't turn on at all.
If I connect the AC Power, then it turns on and the battery starts charging like if it was on 0% (and it really was!)

Then I made some tests, I charged my battery, turned the netbook off and removed the battery. After a few days, I put the battery in again and everything was ok, running on battery with 100% charged (without AC Power).

Somehow, when I turn my netbook off, it still consumes my battery in a way that a couple of days later my battery simply runs out. Maybe Ubuntu is not shutting everything down? Leaving something working?

What is happening? This is really annoying. Anyone else with the same problem?

P.S.: I used it with the Windows XP for a month when I bought it and this didn't happen.

I had the same problem.  I believe it is caused by the built in webcam being powered even when the system is turned off thanks to the Sleep and Charge feature.  Try adding 'echo auto > /sys/bus/usb/devices/1-2/power/level' and 'echo 1 >/sys/bus/usb/devices/1-2/power/autosuspend' to your init scripts or /etc/profile to make sure the camera gets shut off when you suspend or power down.  While you can blacklist the uvcvideo module to prevent the camera from working, that won't prevent it from sucking up power.

---

### Post by Nick255 on 2009-08-18
> **Leesa said:**
> Bluetooth is working with omnibook module:

[LIST=1]
[*]Get sources from [http://dl.getdropbox.com/u/362618/omnibook-source_2.20070211%2Bsvn20071217-1_all.deb](http://dl.getdropbox.com/u/362618/omnibook-source_2.20070211%2Bsvn20071217-1_all.deb)
[*]Make sure Bluetooth is enabled in Windows
[*]sudo apt-get install module-assistant build-essential
[*]sudo m-a a-i omnibook-source
[*]Try it: sudo modprobe omnibook ectype=14
[*]Make it autoload:
[/LIST]
 
[LIST]
[*]sudo nano /etc/modules
[*]Put "omnibook" at the latest line
[*]sudo nano /etc/modprobe.d/omnibook.conf:
[/LIST]
[INDENT]options omnibook ectype=14 userset=0 lcd=0 display=0 blank=0 battery=0 ac=0 bluetooth=1

[/INDENT]Works fine for my NB200, even enabling/disabling bluetooth via /proc/omnibook/bluetooth

You should use ectype=12 instead of ectype=14.  That way you can enable or disable wifi without needing to boot Windows.  Unfortunately, the hotkeys don't work, so you have to manually echo either 1 or 0 to /proc/omnibook/wifi (or if you prefer, just disable it in the bios when you want to be sure it is disabled).

---

### Post by harty83 on 2009-08-18
> **tzirtzi said:**
> Hi! :)

I'm in the process of setting up an NB200 to dual boot XP and Ubuntu - rather unsuccessfully, about which I've posted elsewhere... Anyway, I didn't read this (and other) thread(s) first, and so used the Ubuntu installer's automatic partitioner which has rendered XP non-working. I read that if I run the Windows/DOS utility *chkdsk*, it should fix this, and that this will run automatically if I put the harddrive in a working Windows computer. However, I don't have a torx screwdriver, which I would need to take the harddrive out, so I've been trying various other ways to run *chkdsk*.

The utility is on the Windows XP installation CD, so I've tried writing an image of that CD to a usb key and to a hard disk partition and booting from it - no success. I've also tried running *chkdsk* from the installation CD (copied to my hard drive) from DOSBox, but no success there either. Is there any way of doing this without taking the hard drive out, or am I banging my head against a brick wall?

Thanks!
-tzirtzi

For some reason, installing Ubuntu after windows on this machine renders Windows unbootable. To fix, you need to restore Windows boot loader then resinstall grub.

Boot up using your Windows disc and go into the repair console.  Type fixmbr.  This will restore Windows boot loader to the master boot record.  Now windows will boot but not linux :-)

So let's fix linux.  Boot up from your Ubuntu live jumpdrive or cd and open a console.

Follow these instructions taken from the [wiki]("https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows"):


> 
1. Boot from a Live CD, like Ubuntu Live, Knoppix, Mepis, or similar. Ideally use Ubuntu 8.04 or higher as this has NTFS write support and makes life a bit easier; this isn't necessary, just handy.

2. Open a Terminal. Open a root terminal (that is, type "su" in a non-Ubuntu distro, or "sudo -i" in Ubuntu). Enter root passwords as necessary.

3. Type "grub" which makes a GRUB prompt appear.

4. Type "find /boot/grub/stage1". You'll get a response like "(hd0)" or in my case "(hd0,3)". Use whatever your computer spits out for the following lines. Note that you should have mounted the partition which has your Linux system before typing this command. (e.g. In Knoppix Live CD partitions are shown on the desktop but they're not mounted until you double-click on them or mount them manually)

5. Type "root (hd0,3)" note the space between root and (hd0,3).

6. Type "setup (hd0,3)". This is key. Other instructions say to use "(hd0)", and that's fine if you want to write GRUB to the MBR. If you want to write it to your linux root partition, then you want the number after the comma, such as "(hd0,3)".

7. Type "quit".

8. At this stage you can either restart the system and install your own bootloader, or you can continue and tell the Windows bootloader where to find GRUB which will handle booting Linux. 

 
Thanks,
Alan

---

### Post by harty83 on 2009-08-18
> **SirFunk said:**
> OSSv4:

Just wanted to mention that OSSv4 does nto support suspending/resuming. I found a temporary solution to run soundoff via a suspend script and soundon an resume. This causes the mixera_applet to crash every suspend resume. I've reverted to alsa/pulse for now. I hope someone can get the speaker workign with alsa.

Works fine for me using s2disk.  See the first post on how to setup.

Thanks,
Alan

---

### Post by coldReactive on 2009-08-20
> **filipegatti said:**
> I've detected that a few softwares escape this rule. Pidgin is one of them. Unfortunately there is no way to disable the big and black message pop-up alert in Pidgin, so I changed to emesene, which does always open maximized, even the conversations windows open maximized, always.

libnotify can be disabled in pidgin through plugins.

I'm going to try this guide myself and see what happens, as I just got myself one.

By the way, can I reformat the entire windows drive and wifi will still work? Or will I be SOL?

---

### Post by filipegatti on 2009-08-21
> **coldReactive said:**
> By the way, can I reformat the entire windows drive and wifi will still work? Or will I be SOL?
My Toshiba NB200 has only Linux installed, the entire hard drive has been formatted (I left 8GB for a Windows but it's unused) and my WiFi is working perfectly.

---

### Post by coldReactive on 2009-08-21
> **filipegatti said:**
> My Toshiba NB200 has only Linux installed, the entire hard drive has been formatted (I left 8GB for a Windows but it's unused) and my WiFi is working perfectly.

Yeah, I found that out quickly when I reformatted the entire drive yesterday for UNR.

I was also able to switch to OSS to get the speaker working, though it's a bit crackly (not much, but is) in comparison to my desktop (but only when playing sounds.)

---

### Post by jordilin on 2009-08-22
Thanks indeed for this great thread. I got a toshiba nb200 and it has been of great help. The first thing I did is reduce the windows partition up to the minimum and wipe everything else to put Ubuntu. Up to now, works great and very nice laptop as well :guitar:

---

### Post by coldReactive on 2009-08-23
[https://bugs.launchpad.net/ubuntu/+source/linux/+bug/110784](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/110784)

This model of Toshiba netbooks have this bug apparently. (It seems mine does.)

---

### Post by ReneVYL on 2009-08-25
> **coldReactive said:**
> [https://bugs.launchpad.net/ubuntu/+source/linux/+bug/110784](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/110784)

This model of Toshiba netbooks have this bug apparently. (It seems mine does.)


I'm not seeing it: I fully charged the computer, hibernated it with the powerplug in, unplugged power, left it for 24 hours, and rebooted off of the battery, only for the battery indicator to show 99.9% charge.

In the event that part of my configuration may help you get around your problem, I'll list what I've done:

[LIST]
[*]followed the OP, where appropriate to my system (see next item)
[*]physically removed the WLAN card
[*]replaced the HDD with a SSD
[*]replaced the RAM with a 2GB PC2-5300 stick
[*]BIOS->Advanced
[LIST]
[*]Dyn CPU: Dynamic
[*]Exec-Disable bit: Enabled
[*]Built-in LAN: Enabled
[*]Wireless Comm SW: OFF
[*]Wake on kbd: Disabled
[*]Wake on LAN: Disabled
[*]Critical batt wake-up: Disabled
[*]USB sleep, charge: Disabled
[*]Legacy USB: Disabled
[*]SATA mode: AHCI
[/LIST]
 
[*]echo auto > /sys/bus/usb/devices/1-2/power/level
[*]pm-powersave true (activates laptop mode, among other things)
[*]boot with kernel options:
[LIST]
[*]processor.max_cstate=1
[*]usbcore.autosuspend=1
[/LIST]
 
[/LIST]

---

### Post by coldReactive on 2009-08-25
> **ReneVYL said:**
> [LIST]
[*]followed the OP, where appropriate to my system (see next item)
[*]**_physically removed the WLAN card_**
[*]replaced the HDD with a SSD
[*]replaced the RAM with a 2GB PC2-5300 stick
[*]BIOS->Advanced
[LIST]
[*]Dyn CPU: Dynamic
[*]Exec-Disable bit: Enabled
[*]Built-in LAN: Enabled
[*]**_Wireless Comm SW: OFF_**
[*]Wake on kbd: Disabled
[*]Wake on LAN: Disabled
[*]Critical batt wake-up: Disabled
[*]USB sleep, charge: Disabled
[*]Legacy USB: Disabled
[*]SATA mode: AHCI
[/LIST]
[*]echo auto > /sys/bus/usb/devices/1-2/power/level
[*]boot with kernel options:
[LIST]
[*]processor.max_cstate=1
[*]usbcore.autosuspend=1
[/LIST]
 
[/LIST]

Stuff in bold/underline I cannot do, I need WLAN. I'll try the other stuff EXCEPT upgrading the RAM and HDD to SSD. How do I add those kernel options?

To the op: You may also have to move the mouse when installing something for it to complete, not just for downloads.

---

### Post by remoryl on 2009-08-25
I have two NB205s.  Mine, with 2GB of RAM and my wife's with 1GB of RAM.  Both are running the same install of UNR on 2.6.28-15 with the WiFi fix, audio to the headphone jack, s2disk, webcam kill script, and the following kernel options:

```

ro quiet splash nohz=off hpet=disable noapic usbcore.autosuspend=1 resume=/dev/sda5

```Hers uses 8.9 Watts.  Mine uses 11.8.

She gets 7.5 hours of battery reported, I get 5.2 hours of battery reported.

Also interesting is that I had the brightness controls stop working right.  It would flicker the brightness settings and I couldn't set a default screen brightness in the Power Options for when on battery power, but I couldn't find out why it was arbitrarily changing the brightness.  It wasn't the screen dimming, the little pop-up notification in the top right corner would also become visible and not reflect the actual brightness setting.  It was very vexing.

The only way I knew to resolve it was to login with another user, move my home directory aside, and copy over the things I knew I wanted (~/.ssh, .evolution, ~/Documents, etc) and re-create the rest.  I think there are numerous ways to get configuration files corrupted or otherwise in a funky state, and I wish I knew what it was that I had done to do it so I could avoid it.

I also encountered a problem when using Desktop Switch to flip between UNR and a traditional Ubuntu Gnome desktop several times where the UNR would cease to behave correctly -- the background came up but the panels didn't all populate, etc.  That was after I had been using Control Center but I couldn't find any obvious errors that reference it so I didn't report a bug.  I had nothing to report!

---

### Post by coldReactive on 2009-08-25
> **ReneVYL said:**
> [LIST]
[*]BIOS->Advanced
[LIST]
[*]Dyn CPU: Dynamic
[*]Exec-Disable bit: Enabled
[*]Built-in LAN: Enabled
[*]Wake on kbd: Disabled
[*]Wake on LAN: Disabled
[*]Critical batt wake-up: Disabled
[*]USB sleep, charge: Disabled
[*]Legacy USB: Disabled
[*]SATA mode: AHCI
[/LIST]
[*]echo auto > /sys/bus/usb/devices/1-2/power/level
[*]boot with kernel options:
[LIST]
[*]processor.max_cstate=1
[*]usbcore.autosuspend=1
[/LIST]
 
[/LIST]

Followed these things, and now my battery capacity has been cut in half basically (5-6 hours max on 100%) in Ubuntu. What fun!

---

### Post by ReneVYL on 2009-08-25
> **coldReactive said:**
> Followed these things, and now my battery capacity has been cut in half basically (5-6 hours max on 100%) in Ubuntu. What fun!

A couple of things:

* projected battery life is not necessarily accurate 
* the purpose of "processor.max_cstate=1" is not battery life, but responsiveness: it prevents the deepest sleep modes of the processor, in order to prevent the observed extreme slowdown of a working HDD/SSD

To test battery life, I disable sleep on low battery and run the battery down from a full charge to flat
* when the laptop is left untouched
* while playing back a DVD-ISO in a loop, fullscreen

I'm currently seeing 11 hrs and 6 1/2 hrs for these.

(I'm not sure how representative the test are of anything, but they are relatively easy to do and they ought to be reasonably relevant, at least in pinpointing extremes.)

---

### Post by coldReactive on 2009-08-25
> **ReneVYL said:**
> A couple of things:

* projected battery life is not necessarily accurate 
* the purpose of "processor.max_cstate=1" is not battery life, but responsiveness: it prevents the deepest sleep modes of the processor, in order to prevent the observed extreme slowdown of a working HDD/SSD

To test battery life, I disable sleep on low battery and run the battery down from a full charge to flat
* when the laptop is left untouched
* while playing back a DVD-ISO in a loop, fullscreen

I'm currently seeing 11 hrs and 6 1/2 hrs for these.

(I'm not sure how representative the test are of anything, but they are relatively easy to do and they ought to be reasonably relevant, at least in pinpointing extremes.)

Also note that when setting the BIOS to the settings listed, USB Sticks won't boot anymore (they won't even show up in the Boot list for the BIOS, even with legacy USB on.) For some strange reason, restoring the BIOS to default settings remedies the issue.

---

### Post by ReneVYL on 2009-08-26
> **coldReactive said:**
> when setting the BIOS to the settings listed, USB Sticks won't boot anymore (even with legacy USB on.)

Are you sure that you can't boot from USB with legacy USB enabled in your BIOS? 

That's all I toggle when I boot off of USB to run fsarchiver (which I do very rarely).


PS! I added info on pm-powerrsave to the config list a couple of posts ago.

---

### Post by ReneVYL on 2009-08-26
> **remoryl said:**
> 
[1GB RAM] gets 7.5 hours of battery reported, [2GB RAM] get 5.2 hours of battery reported.


I re-ran my full screen DVD-ISO battery test, and went from 6 1/2 to 7 1/2 hrs with only 1GB RAM, which is almost exactly half of the difference you see predicted.

> **remoryl said:**
> 
```

ro quiet splash nohz=off hpet=disable noapic usbcore.autosuspend=1 resume=/dev/sda5

```

As **sorbus** pointed out earlier, the nohz, hpet, and noapic options are a big hammer if all you are interested in is not seeing extreme slowdown of file accesses. Using processor.max_cstate=1 has the same effect and, as I reported earlier, seems to allow the CPU to remain in C1 for longer. Irrespective of whether or not that translates to better battery life, directly setting max_cstate is likely to be a much more local change with less unexpected consequences.

---

### Post by remoryl on 2009-08-26
> **ReneVYL said:**
> Are you sure that you can't boot from USB with legacy USB enabled in your BIOS? 

I think the poster was refering to the tuning steps another user took where they disabled Legacy USB support.  Disabling Legacy USB in the BIOS will prevent the user from booting from USB flash devices.

> **ReneVYL said:**
> As **sorbus** pointed out earlier, the nohz, hpet, and noapic options are a big hammer if all you are interested in is not seeing extreme slowdown of file accesses. Using processor.max_cstate=1 has the same effect and, as I reported earlier, seems to allow the CPU to remain in C1 for longer. Irrespective of whether or not that translates to better battery life, directly setting max_cstate is likely to be a much more local change with less unexpected consequences.

I'll give that a whirl today and report back.  I was observing the same behavior as another user where if left alone the NB205 would suddenly become exceptionally lazy.  The nohz and hpet options seemed to resolve it.  I'll try processor.max_cstate and see what happens.

Does Ubuntu Netbook Remix respect the "laptop-mode" configurations in /etc?

---

### Post by remoryl on 2009-08-26
I was able to do a fresh install again using the same install media the other NB205 had, and got the WiFi working, installed the fix for Alsa audio via headphones, and went to processor.max_cstate=1.

I also did the Touchpad adjustment and installed Acrobat, Air, and Firefox 3.5.

I was idling at 13.3 watts with an estimated 4.5-5 hours on a fully charged battery.  

Putting the harddisk into a more aggressive power saving mode helped some:
```
hdparm -B 1 -S 12 /dev/sda
```


[FONT=Verdana]Asked my writebacks to be a little dirtier:

```
[/FONT]
echo 1500 > /proc/sys/vm/dirty_writeback_centisecs

```

Got me below 12 watts but only barely.  My wife's NB205 however has much lower power consumption.

We both use WiFi regularly.  I have no idea why my NB205 uses more power than hers does, but I'm thinking about exchanging the hardware.

---

### Post by tzirtzi on 2009-08-27
> **harty83 said:**
> For some reason, installing Ubuntu after windows on this machine renders Windows unbootable. To fix, you need to restore Windows boot loader then resinstall grub.

Boot up using your Windows disc and go into the repair console.  Type fixmbr.  This will restore Windows boot loader to the master boot record.  Now windows will boot but not linux :-)

So let's fix linux.  Boot up from your Ubuntu live jumpdrive or cd and open a console.

Follow these instructions taken from the [wiki]("https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows"):


Thanks,
Alan

Hey Alan,

Thanks for your reply :) Also sorry to have taken so long to reply myself.

I wasn't able to boot from the windows disk as the nb200 has no cd drive. I eventually managed to boot from an image of a windows xp cd on a usb key, but then it couldn't detect the harddrive. Then ubuntu stopped booting, for reasons unknown to me. Eventually, I gave up and wiped the harddrive of both OSs and started again. I've installed Windows 7, as that I've actually been able to boot from usb successfully. I'd like to install Xubuntu as well - is there any way to do this without causing the same problem again, and rendering windows unbootable?

Thanks!

---

### Post by Leesa on 2009-08-27
Alsa & no sound:
Ubuntu bug discussion: [https://bugs.launchpad.net/ubuntu/+source/linux/+bug/389040](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/389040)
Patches & patched kernel: [http://people.canonical.com/~ogasawara/lp389040/jaunty/](http://people.canonical.com/~ogasawara/lp389040/jaunty/)

---

### Post by coldReactive on 2009-08-27
> **Leesa said:**
> Alsa & no sound:
Ubuntu bug discussion: [https://bugs.launchpad.net/ubuntu/+source/linux/+bug/389040](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/389040)
Patches & patched kernel: [http://people.canonical.com/~ogasawara/lp389040/jaunty/](http://people.canonical.com/~ogasawara/lp389040/jaunty/)

Let's hope the patches go into the kernel rather than having us install them ourselves.

---

### Post by dimeotane on 2009-08-28
If you want sound through the speaker, headphones, and to have recording, there are some new patches for the kernel that have been released here.

[https://bugs.launchpad.net/ubuntu/+source/linux/+bug/389040](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/389040)

I've been enjoying sounds through my speaker all week.  It's small but glad it works now!  Please test the patch and give a bug report to Leann if it's not perfect yet.

---

### Post by msknight on 2009-08-30
Just come back from 2 week holiday so I'm probably behind.

filipegatti - I noticed that my battery was flat after charging - turned out my battery was slightly loose. It had enough power to start booting but would die shortly after the loading bar. Somehow I had flipped the battery lock below the machine and that was enough. The moment I secured the battery again, it was fine. Most odd.

The Wi-Fi can be turned on and off in the BIOS in my NB200 with no need to run in to Windows, however I have no sight of the Bluetooth adaptor yet. I'm going to wait until the next version and wipe the NB200 and start again.

In the mean time I'm trying to convince Toshiba that Linux is worthwhile. They cite dropping Linux because of lower sales and also the number of returns from people not willing to learn a new OS. I've argued that if they want it to work, then they need to put some elbow against education and I've given them a few suggestions. I'll continue to talk with them.

By the way, many thanks for this great resource thread.

---

### Post by remoryl on 2009-08-31
> **msknight said:**
> 
In the mean time I'm trying to convince Toshiba that Linux is worthwhile. They cite dropping Linux because of lower sales and also the number of returns from people not willing to learn a new OS. I've argued that if they want it to work, then they need to put some elbow against education and I've given them a few suggestions. I'll continue to talk with them.


If you have a contact over there that would appreciate some more information or user feedback I wouldn't mind telling them about my experience using Netbook Remix on the NB205.  I think with a more mature UNR it would solve a lot of the problems from Netbook Linux users out there since most of the Linux-based netbooks have very lackluster offerings.  Between Moblin and UNR getting more reliable it could be something they would reconsider.

---

### Post by msknight on 2009-08-31
I'll ask them for any particular e-mail address; if we can organise a petition so they can see how many potential customers are out here that they are letting down, it might spur them in to action.  They are normally quick to respond so I believe I should have an answer by this time tomorrow.

---

### Post by msknight on 2009-09-02
The only thing he'd give me was this link - [http://linux.toshiba-dme.co.jp/linux/](http://linux.toshiba-dme.co.jp/linux/) - not sure if it is of help to anyone.

It looks like if we want linux officially supported, we're going to have to get vocal and contact customer support to complain about the lack of Linux on the NB200. If we're silent, they won't care and Linux looses.

---

### Post by bushnoh on 2009-09-04
> **ReneVYL said:**
> I believe my issue, see above [[http://ubuntuforums.org/showpost.php?p=7757745&postcount=25](http://ubuntuforums.org/showpost.php?p=7757745&postcount=25)], has now been fixed, by aligning the SSD's partitions to its block boundaries. Since doing that (and reinstalling) I am consistently seeing >100MB/s read speeds with dd, while the netbook is being left alone.

(That said, I am a little bit skeptical that misalignment can have that pronounced an effect but, just to be clear, I have not followed Leesa's suggestions nor done anything similarly explicit that I didn't do before.)


EDIT1: the increased dd-read speed apparently from properly aligning the partitions was a fluke, it seems. Alignment buys 10s of %, but I am back to sub-expected performance. Time to try the various suggestions by Leesa ...


EDIT2: Leesa's three suggestions: nohz=off hpet=disable noapic, seem to work. (Thanks, Leesa!) With all three in combination, I'm seeing 100--140+ MB/s read speeds, which is probably as much as can be expected from the little thing. Unfortunately, I'm out of time and will not be able to test the three options separately or in pairs for some time, unless using all three has a catastrophic impact on battery life. I'll update or repost if anything new comes up.


EDIT3: couldn't resist: nohz=off seems to be what makes (almost all) the difference. Additionally, powertop reports <8.5W idle power usage with nohz=off vs >11W when nohz=off is not specified.

Is there a bug report filed for this? Or would this not qualify as a bug?

---

### Post by jordilin on 2009-09-06
What I notice sometimes when booting is that it seems like pausing the boot process till I press any key or move the mouse and then it goes on. Has someone else experienced that?

---

### Post by coldReactive on 2009-09-06
> **jordilin said:**
> What I notice sometimes when booting is that it seems like pausing the boot process till I press any key or move the mouse and then it goes on. Has someone else experienced that?

Yep happens even on Windows, unless you get all the Toshiba Drivers.

---

### Post by bushnoh on 2009-09-06
> **jordilin said:**
> What I notice sometimes when booting is that it seems like pausing the boot process till I press any key or move the mouse and then it goes on. Has someone else experienced that?

Yes, try page four of this thread, talking about adding 
```
defoptions=quiet splash processor.max_cstate=1
```
in the boot options.

---

### Post by neoanderthal on 2009-09-10
I'm trying out UNR 9.04 on my NB205, after using Win XP Home, Windows Vista Business, and Windows 7. Battery life so far under UNR has been pretty good - about what I had under XP (and quite a bit more than what I got with Vista or 7). I haven't tried any of the tweaks to decrease power, though I'll look into that if I determine that UNR is going to stay on this thing.
I experience the problem with WiFi dropping out as well. It works great for a bit, but then it will die and I'll have to restart networking to get it going again. For the time being I'm using wired ethernet, but this is just a temporary solution. I really would prefer to have the WiFi useable, since the lack of it removes the prime reason I use this netbook.
I have a fair number of messages under dmesg relating to wlan0 and disassociation, as well as beacon loss. I'd be happy to send the output, along with syslog or anything else that would be helpful, to someone who can make more sense of this than I.

---

### Post by dimeotane on 2009-09-13
A quick fix, that seems to work if wireless has flaked out (after resuming from suspend).  Right clicking on the wireless manager in the gnome bar and deselect enable wireless, and then re-enable it again.

Anyone else find this quick fix works?

---

### Post by diberard on 2009-09-13
In case anyone is a Linux noob like me, or can't figure out the hibernate fix, your menu.lst file may be in a different location, like mine was. Follow the directions until you need to edit the menu.lst file, and see if you can find it in the directory below:
```
sudo gedit /boot/grub/menu.lst
```

Also, as already suggested, after the original WiFi fix, deselecting and re-selecting "enable wireless" from the top right menu, then picking my SSID again re-establishes my WiFi.

---

### Post by diberard on 2009-09-14
Can anybody give me a quick tutorial (or point to a url I wasn't able to find) on how exactly to add the webcam stuff to the startup scripts? 

What I did: I opened /etc/profile and appended these two lines to the very end: 'echo auto > /sys/bus/usb/devices/1-2/power/level' and 'echo 1 >/sys/bus/usb/devices/1-2/power/autosuspend'

But as far as I can tell, my battery is still draining a little during hibernate or shutdown. And yes, I opened the file as root and saved successfully.

---

### Post by Doctor_Gonzo on 2009-09-15
Just curious but does anyone know if we can expect the next release to be a little more NB205 friendly? After doing most of the fixes I still find myself using windows as my primary OS...bleh. Hopefully all the workarounds we've all been having to do will be unnecessary come Koala... On a side note, this is the only computer I've ever had that didn't run near flawlessly out of the box with ubuntu...maybe it's a manufacturer issue or maybe I've just been lucky, but I can't help but be jealous of all my friends with their Dells and HPS that I've installed linux on when I ask them if they've had any problems and they just want to know if I can show them how Wine works so they can stop using windows completely...~sigh~.

---

### Post by coldReactive on 2009-09-15
> **Doctor_Gonzo said:**
> Just curious but does anyone know if we can expect the next release to be a little more NB205 friendly? After doing most of the fixes I still find myself using windows as my primary OS...bleh. Hopefully all the workarounds we've all been having to do will be unnecessary come Koala... On a side note, this is the only computer I've ever had that didn't run near flawlessly out of the box with ubuntu...maybe it's a manufacturer issue or maybe I've just been lucky, but I can't help but be jealous of all my friends with their Dells and HPS that I've installed linux on when I ask them if they've had any problems and they just want to know if I can show them how Wine works so they can stop using windows completely...~sigh~.

The only possibility is that Wifi might work out of the box in Karmic. Everything else you still have to do yourself.

---

### Post by Autocracy on 2009-09-15
Two things I didnt see mentioned

Someone said they had bluetooth working, have a link to a guide?

My wifi connection randomly drops, any reason for this? It is using a WPA2 encryption.

---

### Post by jeroenimo on 2009-09-17
Quick and dirty fix for OSS4 sound gone after sleep/suspend (and maybe hibernate)

After waking up the oss modules seem not loaded or put to sleep propely.

nano /etc/pm/power.d/00-ossreset.sh

add this:
```

#!/bin/sh
rmmod oss_usb
rmmod oss_hdaudio
rmmod osscore
modprobe oss_usb
modprobe oss_hdaudio
modprobe osscore

```after that chmod +x /etc/pm/power.d/00-ossreset.sh


I know its not the right way, but it works flawless, as I said it might even work after hibernate, but I have no hibernate enabled on my nb200.

Jeroenimo

---

### Post by Frihet on 2009-09-19
I tried the headphone sound fix a few days ago, and it worked fine. I rebuilt the machine yesterday to clear windows off the HD, and now I can't seem to get it to work.

Here is a part of my terminal session output:

user@NB205:~$ sudo apt-get upgrade
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages have been kept back:
  libpulse-browse0 libpulse0 pulseaudio pulseaudio-esound-compat
  pulseaudio-module-gconf pulseaudio-module-hal pulseaudio-module-x11
  pulseaudio-utils
0 upgraded, 0 newly installed, 0 to remove and 8 not upgraded.
user@NB205:~$ options snd-hda-intel model=asus-mode4
bash: options: command not found
user@NB205:~$ sudo cp touchpad.fdi /etc/hal/fdi/policy/
cp: cannot stat `touchpad.fdi': No such file or directory
user@NB205:~$ sudo apt-get update
Hit [http://security.ubuntu.com](http://security.ubuntu.com) jaunty-security Release.gpg
Ign [http://security.ubuntu.com](http://security.ubuntu.com) jaunty-security/main Translation-en_US          
Hit [http://archive.canonical.com](http://archive.canonical.com) jaunty Release.gpg                            
Ign [http://archive.canonical.com](http://archive.canonical.com) jaunty/partner Translation-en_US              
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) jaunty Release.gpg                            
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) jaunty/main Translation-en_US                 
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) jaunty Release.gpg                                
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) jaunty/main Translation-en_US                     
Hit [http://packages.medibuntu.org](http://packages.medibuntu.org) jaunty Release.gpg                           
Ign [http://packages.medibuntu.org](http://packages.medibuntu.org) jaunty/free Translation-en_US                
Ign [http://packages.medibuntu.org](http://packages.medibuntu.org) jaunty/non-free Translation-en_US            
Ign [http://security.ubuntu.com](http://security.ubuntu.com) jaunty-security/restricted Translation-en_US    
Ign [http://security.ubuntu.com](http://security.ubuntu.com) jaunty-security/universe Translation-en_US      
Ign [http://security.ubuntu.com](http://security.ubuntu.com) jaunty-security/multiverse Translation-en_US    
Hit [http://archive.canonical.com](http://archive.canonical.com) jaunty Release                                
Hit [http://security.ubuntu.com](http://security.ubuntu.com) jaunty-security Release                         
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) jaunty/restricted Translation-en_US           
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) jaunty/universe Translation-en_US   
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) jaunty/multiverse Translation-en_US 
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) jaunty-updates Release.gpg          
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) jaunty-updates/main Translation-en_US
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) jaunty-updates/restricted Translation-en_US
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) jaunty-updates/universe Translation-en_US
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) jaunty-updates/multiverse Translation-en_US
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) jaunty Release.gpg                      
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) jaunty/main Translation-en_US           
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) jaunty Release                          
Hit [http://packages.medibuntu.org](http://packages.medibuntu.org) jaunty Release                               
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) jaunty Release                                
Hit [http://archive.canonical.com](http://archive.canonical.com) jaunty/partner Packages                       
Hit [http://security.ubuntu.com](http://security.ubuntu.com) jaunty-security/main Packages                   
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) jaunty Release                                    
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) jaunty-updates Release                        
Hit [http://packages.medibuntu.org](http://packages.medibuntu.org) jaunty/free Packages                         
Hit [http://security.ubuntu.com](http://security.ubuntu.com) jaunty-security/restricted Packages             
Hit [http://security.ubuntu.com](http://security.ubuntu.com) jaunty-security/main Sources          
Hit [http://security.ubuntu.com](http://security.ubuntu.com) jaunty-security/restricted Sources    
Hit [http://security.ubuntu.com](http://security.ubuntu.com) jaunty-security/universe Packages     
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) jaunty/main Packages                              
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) jaunty/main Sources                               
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) jaunty/main Packages                          
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) jaunty/restricted Packages                    
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) jaunty/main Sources                           
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) jaunty/restricted Sources                     
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) jaunty/universe Packages                      
Hit [http://packages.medibuntu.org](http://packages.medibuntu.org) jaunty/non-free Packages                     
Hit [http://security.ubuntu.com](http://security.ubuntu.com) jaunty-security/universe Sources                
Hit [http://security.ubuntu.com](http://security.ubuntu.com) jaunty-security/multiverse Packages   
Hit [http://security.ubuntu.com](http://security.ubuntu.com) jaunty-security/multiverse Sources    
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) jaunty/main Packages                    
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) jaunty/main Sources
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) jaunty/universe Sources
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) jaunty/multiverse Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) jaunty/multiverse Sources
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) jaunty-updates/main Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) jaunty-updates/restricted Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) jaunty-updates/main Sources
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) jaunty-updates/restricted Sources
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) jaunty-updates/universe Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) jaunty-updates/universe Sources
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) jaunty-updates/multiverse Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) jaunty-updates/multiverse Sources
Reading package lists... Done
user@NB205:~$ sudo apt-get upgrade
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages have been kept back:
  libpulse-browse0 libpulse0 pulseaudio pulseaudio-esound-compat
  pulseaudio-module-gconf pulseaudio-module-hal pulseaudio-module-x11
  pulseaudio-utils
0 upgraded, 0 newly installed, 0 to remove and 8 not upgraded.
user@NB205:~$ options snd-hda-intel model=asus-mode4
bash: options: command not found
user@NB205:~$

The "held back text above puzzles me:

The following packages have been kept back:
  libpulse-browse0 libpulse0 pulseaudio pulseaudio-esound-compat
  pulseaudio-module-gconf pulseaudio-module-hal pulseaudio-module-x11
  pulseaudio-utils. 

Is this related to the problem?

Thanks for any help!

---

### Post by Frihet on 2009-09-19
> **Frihet said:**
> I tried the headphone sound fix a few days ago, and it worked fine. I rebuilt the machine yesterday to clear windows off the HD, and now I can't seem to get it to work. . . .

Now it's working. I have no idea.

But, if it works, I'm cool!

---

### Post by Elvish Legion on 2009-09-27
Anyword weather 9.10 is going to bring improvements for this netbook? I breifly tried it out and I was very disappointed with the speed and stability of it. I lost connection to wifi alot.  So heres hoping 9.1 brings improvemnts around

---

### Post by coldReactive on 2009-09-28
> **Elvish Legion said:**
> Anyword weather 9.10 is going to bring improvements for this netbook? I breifly tried it out and I was very disappointed with the speed and stability of it. I lost connection to wifi alot.  So heres hoping 9.1 brings improvemnts around

No, everything should still have to be done manually except wifi, which should work out of the box (but will probably still have connection issues as you said.)

Obviously, the battery drainage won't be fixed yet even though the kernel is newer... reason? Because the battery drainage had a fix release in debian, not ubuntu.

No word on bluetooth.

No word on hibernate/sleep either.

Thinking that everything will be fixed, would be very wishful thinking, but I have serious doubts, as I have outlined.

---

### Post by joey on 2009-09-28
I have the NB205.

9.10 UNR Alpha 6 is mostly working.

Bluetooth and sound-out do not work.  There are some folks Canonical kernel folks working on this to try and get it fixed before the Karmic release.

Hibernate seems to work like shutdown, not hibernate and checkbox (hardware-testing) crashes on sending bug reports to launchpad.

Don't count on everything being fixed by Karmic but there are folks looking into it for the NB200/205 series.   If I get more info I'll pass it along.

I'm getting about 6 hours on the battery vs 9 with XP.  I never launched XP. I overwrote it immediately with Ubuntu and the previous problems of having to enable something first in XP before installing Ubuntu appear to be addressed in the latest Karmic kernel.

Your mileage may vary.

Joey

---

### Post by joey on 2009-09-28
Got word that a Canonical developed sound fix was sent upstream a few weeks ago but hasn't been applied yet.

---

### Post by joey on 2009-09-28
These are the karmic bugs I'm tracking.

[https://bugs.edge.launchpad.net/ubuntu/+source/linux/+bug/438318](https://bugs.edge.launchpad.net/ubuntu/+source/linux/+bug/438318)

[https://bugs.edge.launchpad.net/ubuntu/+source/linux/+bug/438323](https://bugs.edge.launchpad.net/ubuntu/+source/linux/+bug/438323)

[https://bugs.edge.launchpad.net/ubuntu/+source/linux/+bug/428671](https://bugs.edge.launchpad.net/ubuntu/+source/linux/+bug/428671)

---

### Post by donmatas on 2009-10-04
> **Ultim8Fury said:**
> So you have a Toshiba NB200 / Dynabook UX / NB205. Some things don't work out of the box in Jaunty UNR 9.04. The following guide should help get as much as possible up and working. I'll try to keep it up to date. 

**_WiFi - _**

First and foremost if you want WiFi to work in Linux the DO NOT turn it off in Windows. A mistake I made and have learnt from. Turning off the WiFi in Windows will disable the WiFi in Linux, completely. The best you can hope for then is that the interface shows up in ifconfig. It will not broadcast or detect any signals. You can ensure it's on by the presense of the the WiFi LED on the front of the machine. 

Making WiFi work once activated is simply a matter of

```
sudo apt-get install linux-backports-modules-jaunty
```Congratulations you've made WiFi work. 



doesn't works on my toshiba NB200...what I can do?

---

### Post by joey on 2009-10-05
> **donmatas said:**
> doesn't works on my toshiba NB200...what I can do?

Upgrade to Karmic. I'm working with the kernel engineers to get all this fixed in time for the release. See above bugs.

---

### Post by ShaunG on 2009-10-05
Hey guys,

Not sure if these will be of any use to anyone, but they are really simple bash scripts to turn camera on/off and turn bluetooth on/off, they are based on ReneVYL's trick.

They work for me so far, and don't seem to be harming anything.

If you want to use them, stick them in /usr/local/bin.They will need to be run as root. You can verify they work by running lsusb before and after running them. You will need to replace BUS_AND_DEVICE_NUM_GOES_HERE with the bus and device number of the camera/bluetooth device. In my case I'd replace it with 1-2 for the camera, and 5-2 for my bluetooth.

Camera/Bluetooth ON
```
#!/bin/bash

# Make sure only root can run our script
if [[ $EUID -ne 0 ]]; then
   echo "This script must be run as root" 1>&2
   exit 1
fi

echo on > /sys/bus/usb/devices/BUS_AND_DEVICE_NUM_GOES_HERE/power/level

```

Camera/Bluetooth OFF

```
same as above, replace on with suspend

```

---

### Post by donmatas on 2009-10-05
> **Rinchen said:**
> Upgrade to Karmic. I'm working with the kernel engineers to get all this fixed in time for the release. See above bugs.

thanks, when is the release?

---

### Post by coldReactive on 2009-10-05
> **donmatas said:**
> thanks, when is the release?

29th of october

---

### Post by dabl on 2009-10-05
I have a new NB205-N310, with a 2GB SODIMM.  Over the weekend, with one eye on this thread, I installed sidux/KDE4 and then (to compare desktops and performance) Elive 1.9.47 (development version).  The Kubuntu 9.10 Beta daily live site wasn't cooperationg, so I booted the Ubuntu UNR Live CD, 3 OCT daily build, but the desktop is not at all to my taste, so I didn't go further with it.  KDE 4 on sidux was a bit sluggish, even though sidux is very fast. The Elive Enlightment desktop seems fastest, by quite a bit, so I went with it.  The same gsynaptics fix for the touchpad, with the fdi file in the OP, works for both sidux and Elive. For Elive, the "tapping" option needs to be disabled in gsynaptics to prevent the menu popping up whenever you move the mouse cursor. Everything else except audio "just works" out of the box -- webcam with cheese, wireless with wicd.

So, about the sound. The good news is, I installed OSS and libasound2-plugins, and it does indeed work fine with audio players and with flashplugin-nonfree in the mozilla browser. I didn't find it difficult to do -- about 5 steps and you're good to go (I didn't have to remove pulseaudio, however -- it wasn't installed). The bad news is, the speaker volume is pathetic (same issue as Windows users report).  I'm about to develop my skills with ossmix -- we'll see if I can make it better.

That's the report -- this is an excellent thread and I wanted to make my teeny contribution.  :)


EDIT:  YES! -- use a terminal window to run ossxmix, and in the GUI push up the PCM 1 volume slider, and you get very respectable (for a netbook) speaker output.

---

### Post by msknight on 2009-10-17
OK Folks, it looks like Toshiba is working double standards.

On the one hand they say that Linux was removed because of lack of feedback from the Linux community. However, they just won't give me an e-mail address so that the Linux community can send in comments.

Sounds to me like they want to ditch Linux :(

Comming in the next couple of days ... the e-mail address of one of the customer service people at Toshiba so that people can mail the bloke directly.

---

### Post by dabl on 2009-10-18
Inasmuch as they have a MS Windows sub-forum here:

[http://laptopforums.toshiba.com/](http://laptopforums.toshiba.com/)

one would think they COULD have a Linux sub-forum alongside.  :mad:

---

### Post by StolenPie on 2009-10-19
Has anyone else had difficulty getting the Desktop Effects in compiz to work? (I can switch mine on in the CCSM but they don't appear.) I'm suspecting it may be something to do with hardware drivers.

---

### Post by fmelo on 2009-10-26
Hi everybody, 
I just installed Ubuntu Karmic in my Toshiba nb200 (daily build 22.10.09), and I get a really slow internet connection. in fact it doesn't matter whether wi-fi or wired (both worked out of the box), the download rate is not more than 300 Kb/s, while within the Windows partition I get up to 7Mb/s.  Does anyone have the same problem? What to do?! I'm really new to Ubuntu.

Besides... it keeps crashing...

Thanks.

---

### Post by king20878 on 2009-10-27
> **fmelo said:**
> Hi everybody, 
I just installed Ubuntu Karmic in my Toshiba nb200 (daily build 22.10.09), and I get a really slow internet connection. in fact it doesn't matter whether wi-fi or wired (both worked out of the box), the download rate is not more than 300 Kb/s, while within the Windows partition I get up to 7Mb/s.  Does anyone have the same problem? What to do?! I'm really new to Ubuntu.

Besides... it keeps crashing...

Thanks.

I found turning off the power management for the network card improved throughput a lot.

```
sudo iwconfig wlan0 power off
```

I ended up adding this to rc.local so that it is set this way at startup.  Hope it helps.

---

### Post by dabl on 2009-10-27
> **fmelo said:**
> 

Besides... it keeps crashing...



It's probably not crashing, probably you are seeing Toshiba's hard drive firmware putting it to sleep more or less continuously.  If you tickle the touchpad or hit the spacebar, and watch the drive indicator light, and if it immediately "un-crashes" and starts to work, you'll know.

Once it gets booted to the GUI desktop, it seems to stay running better. But if you don't touch it periodically, the drive goes back to sleep.

Hint:  Copy some music files to the hard drive, and run a music player, while you are doing things like file transfers, that don't require touching the keyboard.  That will keep the drive alive.

---

### Post by fmelo on 2009-10-28
Hi,

thanks a lot for the replies, but it didn't improve much. I'm still not even close to get 1Mb/s. Note that actually I get low rates even with wired connection. 

Maybe this info might help:
ifconfig
```

eth0      Link encap:Ethernet  HWaddr 00:23:5a:fa:a1:9d  
          inet addr:10.33.164.38  Bcast:10.33.167.255  Mask:255.255.252.0
          inet6 addr: fe80::223:5aff:fefa:a19d/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:155895 errors:0 dropped:0 overruns:0 frame:0
          TX packets:78606 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:89168642 (89.1 MB)  TX bytes:26141876 (26.1 MB)
          Interrupt:29 Base address:0xa000 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:225 errors:0 dropped:0 overruns:0 frame:0
          TX packets:225 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:6525 (6.5 KB)  TX bytes:6525 (6.5 KB)

wlan0     Link encap:Ethernet  HWaddr 00:23:08:9c:62:d2  
          inet addr:10.8.3.138  Bcast:10.8.3.255  Mask:255.255.254.0
          inet6 addr: fe80::223:8ff:fe9c:62d2/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:15042 errors:0 dropped:0 overruns:0 frame:0
          TX packets:2144 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:4966545 (4.9 MB)  TX bytes:239053 (239.0 KB)

wmaster0  Link encap:UNSPEC  HWaddr 00-23-08-9C-62-D2-39-63-00-00-00-00-00-00-00-00  
          UP RUNNING  MTU:0  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)

```and iwconfig
```

lo        no wireless extensions.

eth0      no wireless extensions.

wmaster0  no wireless extensions.

wlan0     IEEE 802.11bgn  ESSID:"campusnet"  
          Mode:Managed  Frequency:2.412 GHz  Access Point: 00:14:1B:B4:CC:60   
          Bit Rate=12 Mb/s   Tx-Power=20 dBm   
          Retry  long limit:7   RTS thr:off   Fragment thr:off
          Power Management:off
          Link Quality=5/70  Signal level=-105 dBm  
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

```

Thanks once more!

---

### Post by dabl on 2009-10-28
OK, an Elive upgrade killed networking beyond my ability to fix it, so I went back to sidux/KDE and that's what it is running now.  Wireless is really working great -- I removed knemo and network-manager and installed wicd, and it just hooks up great.  Here are outputs that might be of interest:

> root@tosh205:/home/dabl# ifconfig
eth0      Link encap:Ethernet  HWaddr 00:23:5a:fa:a0:32  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1     
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)
          Interrupt:28 Base address:0xe000

lo        Link encap:Local Loopback
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:44 errors:0 dropped:0 overruns:0 frame:0
          TX packets:44 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0
          RX bytes:2200 (2.1 KiB)  TX bytes:2200 (2.1 KiB)

wlan0     Link encap:Ethernet  HWaddr 00:23:08:96:77:a1
          inet addr:192.168.10.149  Bcast:192.168.10.255  Mask:255.255.255.0
          inet6 addr: fe80::223:8ff:fe96:77a1/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:28450 errors:0 dropped:0 overruns:0 frame:0
          TX packets:16777 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:40140316 (38.2 MiB)  TX bytes:1819424 (1.7 MiB)

wmaster0  Link encap:UNSPEC  HWaddr 00-23-08-96-77-A1-77-6C-00-00-00-00-00-00-00-00
          UP RUNNING  MTU:0  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)

> root@tosh205:/home/dabl# iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

wmaster0  no wireless extensions.

wlan0     IEEE 802.11bgn  ESSID:"TRENDnet"
          Mode:Managed  Frequency:2.412 GHz  Access Point: 00:14:D1:C6:D9:B3
          Bit Rate=0 kb/s   Tx-Power=20 dBm
          Retry  long limit:7   RTS thr:off   Fragment thr:off
          Encryption key:1300-5B39-A6B8-9B3C-EB77-7DFD-82FB-05B8 [2]
          Power Management:on
          Link Quality=49/70  Signal level=-61 dBm
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

> root@tosh205:/home/dabl# cat /etc/network/interfaces
# This file describes the network interfaces available on your system
# and how to activate them. For more information, see interfaces(5).

# The loopback network interface
auto lo
iface lo inet loopback

allow-hotplug eth0
iface eth0 inet dhcp

allow-hotplug wlan0
iface wlan0 inet manual
  wpa-driver wext
  wpa-roam /etc/wpa_supplicant/wpa_supplicant.conf
iface default inet dhcp

> root@tosh205:/home/dabl# cat /etc/wpa_supplicant/wpa_supplicant.conf
#configuration per sidux manual

ctrl_interface=DIR=/var/run/wpa_supplicant GROUP=netdev
update_config=1

network={
        key_mgmt=NONE
}

> root@tosh205:/home/dabl# ping [www.google.com](www.google.com)
PING [www.l.google.com](www.l.google.com) (64.233.169.104) 56(84) bytes of data.
64 bytes from yo-in-f104.1e100.net (64.233.169.104): icmp_seq=1 ttl=245 time=42.2 ms
64 bytes from yo-in-f104.1e100.net (64.233.169.104): icmp_seq=2 ttl=245 time=35.2 ms
64 bytes from yo-in-f104.1e100.net (64.233.169.104): icmp_seq=3 ttl=245 time=35.5 ms
64 bytes from yo-in-f104.1e100.net (64.233.169.104): icmp_seq=4 ttl=245 time=34.9 ms
64 bytes from yo-in-f104.1e100.net (64.233.169.104): icmp_seq=5 ttl=245 time=44.9 ms
64 bytes from yo-in-f104.1e100.net (64.233.169.104): icmp_seq=6 ttl=245 time=35.9 ms
^C
--- [www.l.google.com](www.l.google.com) ping statistics ---
6 packets transmitted, 6 received, 0% packet loss, time 5006ms
rtt min/avg/max/mdev = 34.982/38.148/44.977/3.962 ms

This all while in wireless mode.

---

### Post by wnderinguy34 on 2009-10-29
Anybody do a clean install with 9.10 yet?

---

### Post by msknight on 2009-10-29
Done a clean install with 9.10 netbook remix. Webcam works, but sound and bluetooth don't.

---

### Post by wnderinguy34 on 2009-10-29
> **msknight said:**
> Done a clean install with 9.10 netbook remix. Webcam works, but sound and bluetooth don't.
Hmm.. how about wireless? or will I need to do the backports fix again.

---

### Post by fmelo on 2009-10-29
> Hmm.. how about wireless? or will I need to do the backports fix again.Wireless was working "out of the box" since the beta version... although still very slow to me, even after the upgrade.

@dabl: Thanks for the reply, but I cannot make sense out of all these numbers. Is this wicd just a networking manager interface (that is how it looks to me from their website) or does it really change the network settings? 

Cheers,
fmelo

---

### Post by msknight on 2009-10-29
Wireless was always working for me out of the box. There is a wireless switch in the bios settings.

Start up is still a bit on the slow side using conventional hard disk. A couple of minutes at least.

Only new thing in terms of function from 9.04 is that the web cam is now working out of the box.

---

### Post by wnderinguy34 on 2009-10-29
> **msknight said:**
> Wireless was always working for me out of the box. There is a wireless switch in the bios settings.

Start up is still a bit on the slow side using conventional hard disk. A couple of minutes at least.

Only new thing in terms of function from 9.04 is that the web cam is now working out of the box.

Never tried it as a "webcam" but was always able to use it to snap pics .


> Start up is still a bit on the slow side using conventional hard disk.

Is this using ext4 ?I here that speeds things up.

---

### Post by daskalos on 2009-10-30
I have been trying to install ubuntu on a nb 200 the last week and here are my conclusions:
ubuntu 8.04
sound, wired network, camera works out of the box. Problem with the atheros. Didn't manage to install either by hand.

ubuntu 9.04 
no sound (from speakers, haven't tried oss), wireless, camera, 
wired net works fine

ubuntu 9.10 
no sound (from speakers), wireless, cameram wired net works. Takes ages to install

ubuntu 8.10
sound works fine. I found out that up to kernel 2.6.26-7 sound works in all versions. The moment I updated to 2.6.27-15 sound no longer works. No wireless but its very easy to download and install ath9k drivers. After that I have very good signal and speeds with atheros. Do not install atheros drivers with backport modules because it will install 2.6.27-15 kernel also.
camera and wired network works also. One problem with wired network if i reboot having cable atached to the card, the net appears disconnected (no matter dhcp or not). Unplug the cable, reboot, reconnect and everything ok. 
I guess I will stick with 8.10 for now.

---

### Post by msknight on 2009-10-30
Yes, using ext4 on the hard disk that came with it.  I have boosted the RAM to 2gig 800Mhz.

Installation took a little over 10 minutes once the installation questions were answered. Hard drive was partitioned as follows...

30gig root filesystem
2gig swap
rest as /home

Bluetooth I can live without permanently but I'm hoping that an update for the sound comes down some time soon. I haven't messed with the sound solutions because...

1) I don't have the time to mess around - life is keeping me very busy.

2) I think that the resolution is using an internal speaker rather than the proper speakers. Not good sound and not worth it. I'd rather keep it simple in the hope that it will make it easier for a future update to get it working.

Comming up, it takes a couple of minutes to start, but only about ten seconds-ish to go down.

Netbook remix is going to take a while to get used to.

Wireless connects to simple encryption no problem without having to switch to Wicd - will test with more powerful encryption systems later to see if that holds up or whether I have to switch.

The biggie for me will be this weekend, I intend swapping out my Windows XP main computer for Kubuntu 9.10. I'm documenting it on You Tube in the hope that others will gain confidence and follow suit.

---

### Post by saiprakash on 2009-11-07
> **Leesa said:**
> Bluetooth is working with omnibook module:

[LIST=1]
[*]Get sources from [http://dl.getdropbox.com/u/362618/omnibook-source_2.20070211%2Bsvn20071217-1_all.deb](http://dl.getdropbox.com/u/362618/omnibook-source_2.20070211%2Bsvn20071217-1_all.deb)
[*]Make sure Bluetooth is enabled in Windows
[*]sudo apt-get install module-assistant build-essential
[*]sudo m-a a-i omnibook-source
[*]Try it: sudo modprobe omnibook ectype=14
[*]Make it autoload:
[/LIST]
 
[LIST]
[*]sudo nano /etc/modules
[*]Put "omnibook" at the latest line
[*]sudo nano /etc/modprobe.d/omnibook.conf:
[/LIST]
[INDENT]options omnibook ectype=14 userset=0 lcd=0 display=0 blank=0 battery=0 ac=0 bluetooth=1

[/INDENT]Works fine for my NB200, even enabling/disabling bluetooth via /proc/omnibook/bluetooth

Thanks - this seems to be the only solution (I could find :) ) on enabling BT in NB200.  Tried and need some help.

Installed the .deb and when I tried to build (sudo m-a ai omnibook-source) I am getting an error.  The description for the omnibook packages says -- Suitable for kernerl 2.6.9 or above.  My NB200 has the UNR9.10 installed with kernel 2.6.31.

Can anyone tell me what I should do?  Thanks in advance.

---

### Post by Lovecraftian Horror on 2009-11-15
I've been waiting for 9.10 to hit since I got my NB205, and it's been well worth it. 
Stuck with ext3 filesystem.

25GB Windows
4GB root fs
4GB swap
Rest as /home

Will post here as issues show up.

---

### Post by jeroenimo on 2009-11-16
Karmic koala runs fine so far, still no sound on the speaker, but there is a fix due, jaunty seems to be fixed in proposed.

I have Bluetooth running now and omnibook compiles fine now after some editing

here's how you do it:

```
sudo apt-get install module-assistant build-essential
```
```
wget http://dl.getdropbox.com/u/362618/omnibook-source_2.20070211%2Bsvn20071217-1_all.deb
```
```
sudo dpkg -i omnibook-source_2.20070211+svn20071217-1_all.deb
```
```
sudo cd /usr/src/
```
```
sudo tar xjf omnibook.tar.bz2
```
```
sudo cd modules/omnibook/
```
```
sudo nano init.c
```
hit ctrl-w and type "proc_entry->owner = THIS_MODULE;"
when you get to that line add two // in front of it and make sure it look like this"

// proc_entry->owner = THIS_MODULE;

ctrl-o ctrl-x to save the file

now we compile omnibook

```
sudo m-a build omnibook-source -O
```
```
sudo m-a install omnibook-source
```

now we test 

```
sudo modprobe omnibook ectype=14
```

The bluetooth should appear in you menubar

Now we make things persistent:

```
sudo nano /etc/modules
```

add the line "omnibook" (without "")

save the file

```
sudo nano /etc/modprobe.d/omnibook.conf
```

add this line without "" "options omnibook ectype=14 userset=0 lcd=0 display=0 blank=0 battery=0 ac=0 bluetooth=1"

save the file and voila you are ready ;-)

reboot and Bluetooth should be fine, after sleep or hibernate it could be it malfunctions, but for that you can create a file that restarts bluetooth

like this:

```
nano /etc/pm/power.d/89bluetooth
```

and put this in:

"#!/bin/bash
rmmod -f omnibook
modprobe omnibook ectype=14" (without "")

```
chmod +x /etc/pm/power.d/89bluetooth
```

and after sleep hibernate bluetooth should work too

---

### Post by RogerLK on 2009-11-17
Thank you, jeroenimo, for the instructions (and Leesa for finding the omnibook modules).  

There is, however, still a little snag in your instructions:
Following them step by step, I always got a compile error. It turned out that the modifications of the "init.c" file made before starting the compilation process were always overwritten, causing the error message. What I did was change the compile command from

sudo m-a build omnibook-source

to

sudo m-a build omnibook-source -O     (that is capital "O")

That way, the module assistant does no un-tar the source files again, thus overwriting the "init.c" file.

From there on, it was smooth sailing  :P

The recovery from sleep / hibernate works fine, the commands for setting that up must be entered as "sudo", though, otherwise there will be an error.

Again, thanks for the instructions!


On a different note: I have seen this mentioned a few times in this thread, but also in other threads:

The NB205 sometimes appears to be "freezing" during boot, waking up only if you touch the touchpad or press a key. This may not be a real big deal, but it can be annoying. I had the same problem until I updated my BIOS from the original shipping version 1.2 to the latest version 1.6 (available from the Toshiba website). Not only did that solve another boot related problem for me (which was the main reason for the update), but all the random freezing effects seem to be completely gone - at least I never had a problem with those again.

Maybe that is a piece of information somebody else can use... ;)

---

### Post by dimeotane on 2009-11-17
Thanks for the info about the new BIOS update.  For those of us who've deleted our windows partion, it might be necessary to create a bootable DOS formatted USB memory stick to run the BIOS .exe update program.  Any one manage to do this successfully?

I tried netbootin to create a bootable USB loaded with freedos. Except it gives an opcode error when booting from the USB to freedos.  (I also tried before to put freedos on the USB using dosemu and couldn't get it to happen either. 

[http://0sumgain.blogspot.com/2009/11/updating-motherboard-bios-from-ubuntu.html#comment-form](http://0sumgain.blogspot.com/2009/11/updating-motherboard-bios-from-ubuntu.html#comment-form)

---

### Post by RogerLK on 2009-11-18
I can't speak for all Toshiba notebooks / netbooks, but at least for the NB200 / NB205 the BIOS update comes as a self-extracting archive (under Windows). 

You can, however, open that archive ("ll20v160.exe") with archive manager, extract the "ll20v160.iso" file and make a bootable CD from it (if you have an external USB optical drive available, that is). So, even without Windows, it is no problem to update the BIOS (again, provided you have access to an optical drive).

Hope that helps.

Happy updating!

PS: it goes without saying that you perform all BIOS updates at your own risk...:-|

---

### Post by jeroenimo on 2009-11-19
Updating to bleeding edge compat-wireless has given me a LOT better performance and no more dropouts on wifi.

This is how you do it:

```
sudo apt-get install build essential
```

```
wget http://wireless.kernel.org/download/compat-wireless-2.6/compat-wireless-2.6.tar.bz2
```

If this does not work, surf to [http://linuxwireless.org/en/users/Download#Where_to_download_bleeding_edge](http://linuxwireless.org/en/users/Download#Where_to_download_bleeding_edge) and download the tarball in the directory you are..

```
tar xjf compat-wireless-*tar.bz2
```

```
cd compat
``` (hit tab to complete the path)

```
make
```
```
sudo make install
```
```
sudo make unload
```
```
sudo modprobe ath9k
```

enjoy you troublefree wifi with your atheros card

P.S. this IS beelding edge, it could also fail ofcourse,use at own risk, reverting to the original driver is very easy though

```
sudo make unload
```
```
sudo make uninstall
```
```
sudo modprobe ath9k
```

or reboot

---

### Post by Leesa on 2009-11-24
> **jeroenimo said:**
> Updating to bleeding edge compat-wireless has given me a LOT better performance and no more dropouts on wifi.
Yes, much better.
No more weak signal.
No more complete drop after 30 mins (till reboot).
Usable for usual internet browsing.
But still drops on heavy load... But reconnects fast.
Trying to copy 1Gb file via scp it dropped & reconnected 5 times.

---

### Post by Chargaff on 2009-11-27
Hi everyone,

Thanks for this great thread !

Here is my quick report on a fresh install of UNR 9.10 on NB200, wiped off windows at first boot ;). 

[LIST]
[*]Wireless : Worked out of the box. As some of you mentioned earlier, I did experienced some disconnections problems and some slow moments, but still very usable to my taste. Haven't tried the bleeding edge wireless-compat yet.
[*]Camera : Didn't work at first boot, worked flawlessly after first update.
[*]Sound : Not working, not a priority for me right now.
[*]Battery life : Heading for 7-8 hours doing internet, some software install and office work. Quite impressive !
[*]Suspend/hibernate : Resume crash computer on both. I haven't seen any of you guy's experience theses kind of troubles, google gave me no luck. Am I the only one with this problem ? Looking for a fix.
[/LIST]
I appreciate very much the overall feeling of UNR, it's my first experience with a netbook. I do miss the multiples workspace and the ability to configure the login screen on Karmic (gnome-related I think, strange decision to my taste...)

[EDIT]
Ok, I got the workspaces back...
[http://www.veen.ca/content/workspaces-ubuntu-netbook-remix-910](http://www.veen.ca/content/workspaces-ubuntu-netbook-remix-910)
Don't know why this didn't work yesterday... Good to have theses back !
[LEFT][/EDIT]

More later on BIOS update and wireless-compat. Anyone experiencing Suspend/hibernate crashes ?

Thanxalot,
[/LEFT]

---

### Post by Chargaff on 2009-11-29
Confirmed gain in stability and performance of the wireless with bleeding edge compat-wireless. No drop out on an 8gb transfer. Thanx !

---

### Post by MysticalRiotCandy on 2009-11-29
Running Karmic.  I can attest for the bleeding edge fix as well.  Works like a charm, gives me a little bit more range (although still a lot less than my iPod Touch).  Note: it took a pretty long time compiling the driver.

Something that's sort of bothering me right now is that the volume control is incredibly off.  That is, I have to use headphones, but the volume manager must think I'm using speakers because even if I leave the volume at 10%, the sound is *deafening*.  I have it set to 3% now.  I can't control the volume with the volume keys because raising the volume makes it hit about 10%, and lowering it makes it 0%.  Does anyone have a fix that makes the audio control recognize it as headphones, not speakers?

---

### Post by dimeotane on 2009-11-29
I've managed to successfully update my BIOS to 1.6.
My boot time is now 1 minute 8 seconds from grub to login. I think the new BIOS does reduce the freezing (hard drive reading used to slow until the trackpad was touched). 


  It took way too many hours to figure out how. I used the HP Disk Storage Format tool in windows in virtualbox to format my USB key as bootable, using files from here: 

[http://files.extremeoverclocking.com/file.php?f=197](http://files.extremeoverclocking.com/file.php?f=197)

Then I opened this file as an archive:
 [http://cdgenp01.csd.toshiba.com/content/support/downloads/ll20v160.exe](http://cdgenp01.csd.toshiba.com/content/support/downloads/ll20v160.exe)
and found inside it a CD image (ll20v160.iso) and inside that ISO was a floppy image 2355d160.ima.  (and also inside the 2355d160.exe self-extracting ZIP file).  
Inside that was a DOS BIOS flasher program (phlash16.exe) and the BIOS image (avaa160a.rom.  I copied the DOS flasher and the rom file to my USB key.  I ran it at the command prompt with "a:> plash16 avaa160a.rom" and it worked!

Some of my info came from this thread here:

[http://forums.computers.toshiba-europe.com/forums/thread.jspa?messageID=175994](http://forums.computers.toshiba-europe.com/forums/thread.jspa?messageID=175994)


Earlier I'd tried using all the linux programs to make a bootable USB drive to no avail, Freedos gave me opcode errors and other methods wouldn't boot the USB on this netbook. It would have been great to manage to do the whole process without needing to use windows, but I had no luck.

---

### Post by outdoorsman14 on 2009-11-30
> **jeroenimo said:**
> Karmic koala runs fine so far, still no sound on the speaker, but there is a fix due, jaunty seems to be fixed in proposed.

I have Bluetooth running now and omnibook compiles fine now after some editing

here's how you do it:

```
sudo apt-get install module-assistant build-essential
```
```
wget http://dl.getdropbox.com/u/362618/omnibook-source_2.20070211%2Bsvn20071217-1_all.deb
```
```
sudo dpkg -i omnibook-source_2.20070211+svn20071217-1_all.deb
```
```
sudo cd /usr/src/
```
```
sudo tar xjf omnibook.tar.bz2
```
```
sudo cd modules/omnibook/
```
```
sudo nano init.c
```
hit ctrl-w and type "proc_entry->owner = THIS_MODULE;"
when you get to that line add two // in front of it and make sure it look like this"

// proc_entry->owner = THIS_MODULE;

ctrl-o ctrl-x to save the file

now we compile omnibook

```
sudo m-a build omnibook-source
```
```
sudo m-a install omnibook-source
```

now we test 

```
sudo modprobe omnibook ectype=14
```

The bluetooth should appear in you menubar

Now we make things persistent:

```
sudo nano /etc/modules
```

add the line "omnibook" (without "")

save the file

```
sudo nano /etc/modprobe.d/omnibook.conf
```

add this line without "" "options omnibook ectype=14 userset=0 lcd=0 display=0 blank=0 battery=0 ac=0 bluetooth=1"

save the file and voila you are ready ;-)

reboot and Bluetooth should be fine, after sleep or hibernate it could be it malfunctions, but for that you can create a file that restarts bluetooth

like this:

```
nano /etc/pm/power.d/89bluetooth
```

and put this in:

"#!/bin/bash
rmmod -f omnibook
modprobe omnibook ectype=14" (without "")

```
chmod +x /etc/pm/power.d/89bluetooth
```

and after sleep hibernate bluetooth should work too

This worked for me quite well, the only thing that needed to be changed was the omnibook-source module to include the -O, so the package wasn't rebuilt and it works great!! Thank you so much, this is awesome the only thing left is the sound from the speaker, but that is okay with me.

---

### Post by aiyoaiyo on 2009-12-02
I am also using a Toshiba NB205. 

Adding this option in the /etc/modprobe.d/alsa-base.conf 
options snd-hda-intel model=auto
can make the internal speaker and headphone both work fine. However, this setting reduces my microphone reception quality. It's still not a perfect solution.

P.S. I have upgraded my alsa driver to the latest version 1.0.21. Not sure if this makes any difference.

---

### Post by dimeotane on 2009-12-02
Still no sound here using the same settings as the previously posted by aiyoaiyo.  (If it matters, I'm running UNR and have updated from alpha to current version)

cat /proc/asound/version shows
Advanced Linux Sound Architecture Driver Version 1.0.21.
kernel 2.6.31-15-generic (SMP).


in /etc/modprobe.d/alsa-base.conf I've added the line:
options snd-hda-intel model=auto

After rebooting, sound was muted before I put the volume setting up to 100%.  A new 'analog speaker' option was available in the output options.

---

### Post by aiyoaiyo on 2009-12-02
After rebooting, I did have to go to "Sound Preferences" to change the hardware to "Analog Stereo Duplex" for configuration before I started to hear sounds from the internal speakers. Maybe you have done this already?

Before that option line I posted, I have this other option to force snd-hda-intel to be my default sound card:
options snd-hda-intel index=0
Not sure if this will be helpful.

Also, when I installed alsa drivers (version 1.0.21) downloaded from the Realtek website, I did remove my old version of alsa with the instructions from this other thread:
[http://ubuntuforums.org/showthread.php?t=205449&highlight=nb205](http://ubuntuforums.org/showthread.php?t=205449&highlight=nb205)

Let me know if I can provide anymore information.

---

### Post by dimeotane on 2009-12-05
aiyoaiyo, you're a super :KS ! Thank you so much for your thoughtful follow up with those additional details about what worked for your sound config.  I'm trying them right now! :D

Looking on the alsa website for drivers;
I see at the bottom of the HD audio codecs page: 
Linux driver (2.6) 5.13rc6	2009/12/3
I see this contains Alsa drivers. 
I'll try this as well. 

Do you use this line in your alsa.config?  It appears it is put into the config by default:
options snd-hda-intel power_save=10 power_save_controller=N

Could you post your alsa-base.conf file here? Mine is now empty after manually installing the new version of alsa drivers.

---

### Post by aiyoaiyo on 2009-12-05
Here is my alsa-base.conf

# autoloader aliases
install sound-slot-0 /sbin/modprobe snd-card-0
install sound-slot-1 /sbin/modprobe snd-card-1
install sound-slot-2 /sbin/modprobe snd-card-2
install sound-slot-3 /sbin/modprobe snd-card-3
install sound-slot-4 /sbin/modprobe snd-card-4
install sound-slot-5 /sbin/modprobe snd-card-5
install sound-slot-6 /sbin/modprobe snd-card-6
install sound-slot-7 /sbin/modprobe snd-card-7

# Cause optional modules to be loaded above generic modules
install snd /sbin/modprobe --ignore-install snd $CMDLINE_OPTS && { /sbin/modprob
e --quiet --use-blacklist snd-ioctl32 ; /sbin/modprobe --quiet --use-blacklist s
nd-seq ; }
#
# Workaround at bug #499695 (reverted in Ubuntu see LP #319505)
install snd-pcm /sbin/modprobe --ignore-install snd-pcm $CMDLINE_OPTS && { /sbin
/modprobe --quiet --use-blacklist snd-pcm-oss ; : ; }
install snd-mixer /sbin/modprobe --ignore-install snd-mixer $CMDLINE_OPTS && { /
sbin/modprobe --quiet --use-blacklist snd-mixer-oss ; : ; }
install snd-seq /sbin/modprobe --ignore-install snd-seq $CMDLINE_OPTS && { /sbin
/modprobe --quiet --use-blacklist snd-seq-midi ; /sbin/modprobe --quiet --use-bl
acklist snd-seq-oss ; : ; }
#
install snd-rawmidi /sbin/modprobe --ignore-install snd-rawmidi $CMDLINE_OPTS &&
 { /sbin/modprobe --quiet --use-blacklist snd-seq-midi ; : ; }
# Cause optional modules to be loaded above sound card driver modules
install snd-emu10k1 /sbin/modprobe --ignore-install snd-emu10k1 $CMDLINE_OPTS &&
 { /sbin/modprobe --quiet --use-blacklist snd-emu10k1-synth ; }
install snd-via82xx /sbin/modprobe --ignore-install snd-via82xx $CMDLINE_OPTS &&
 { /sbin/modprobe --quiet --use-blacklist snd-seq ; }

# Load saa7134-alsa instead of saa7134 (which gets dragged in by it anyway)
install saa7134 /sbin/modprobe --ignore-install saa7134 $CMDLINE_OPTS && { /sbin
/modprobe --quiet --use-blacklist saa7134-alsa ; : ; }
# Prevent abnormal drivers from grabbing index 0
options bt87x index=-2
options cx88_alsa index=-2
options saa7134-alsa index=-2
options snd-atiixp-modem index=-2
options snd-intel8x0m index=-2
options snd-via82xx-modem index=-2
options snd-usb-audio index=-2
options snd-usb-us122l index=-2
options snd-usb-usx2y index=-2
options snd-usb-caiaq index=-2
# Ubuntu #62691, enable MPU for snd-cmipci
options snd-cmipci mpu_port=0x330 fm_port=0x388
# Keep snd-pcsp from being loaded as first soundcard
options snd-pcsp index=-2
# Power down HDA controllers after 10 idle seconds
#options snd-hda-intel power_save=10 power_save_controller=N
# Added by Ronin -- to force snd-hda-intel to be card 0
options snd-hda-intel index=0 model=auto

---

### Post by dimeotane on 2009-12-06
It's rather strange. I've updated my alsa to 1.0.21 and used your alsa-base.conf but no audio through headphones or speaker. 
If I unmute the mic inputs I hear the mic through the headphones.
If I use options=asus-mode4, and restart alsa, I get audio through headphones only.  So confused!
  Perhaps someone else might be able to repeat your success?

Perhaps I haven't done the Alsa upgrade correctly.
Could you explain in more detail the steps you followed in your alsa upgrade?

You said to remove the old drivers. Like this: 
sudo apt-get --purge remove linux-sound-base alsa-base alsa-utils

Did you reinstall them after like this?
sudo apt-get install linux-sound-base alsa-base alsa-utils

Or did you skip that step and then only compile the alsa-driver alsa-lib alsa-utils from the realtek website?

Did you follow the (vague) instructions from the realtek divers?  They included some into about what to add to your /etc/modules file.  If not were there some specific instructions you followed when installing ALSA ?

---

### Post by mike_richman on 2009-12-14
I haven't had time to follow this entire thread, but I know some people have reported trouble with wireless performance degrading during the course of a login.  Restarting NetworkManager can help, but it doesn't always do the trick.  To work around the problem, here is what seems to work best to me.  Put the following script in /usr/sbin/ath9k-restart:

```

#!/bin/sh
# restart the ath9k module when the network card stops working

modprobe -r ath9k && modprobe ath9k

exit 0
```

Make the script executable by running the following command in a terminal:

```

sudo chmod +x /usr/bin/ath9k-restart
```

To make it easy to use, create a launcher someplace convenient such as the desktop.  I called mine "Restart Network Module".  The command field should read

```

gksudo /usr/sbin/ath9k-restart
```

If I understand it as well as I think I do, /usr/sbin/ath9k-restart removes and re-inserts the kernel module responsible for the wireless card.  This has the effect of starting fresh, regardless of whatever has gotten messed up over time.

---

### Post by electechchris on 2009-12-17
Have been trying to get kubuntu 8.04.2 working on my nb200
(want to stay with kde 3.5 having tried 4.2 - too much for atom netbook in my opinion)
upgraded bios to v1.60 with usb cdrom
After upgrading some packages I have kernel 2.6.24-23

Sound works fine
not sure how to use bluetooth or camera yet but dmesg looks
 OK to me.

How do I get and load driver/module atheros 9k
looked at bleedin edge site and it does not support kernel <2.6.27 

daskalos posted his success with ubuntu 8.10 in oct. on this thread.

---

### Post by stina on 2009-12-23
I still cant get my wifi working on my NB200.

When I bought it I hurried to install netbook remix without thinking of turning wifi on in windows.
I have tried the sudo apt-get install linux-backports-modules-jaunty, but it doesnt work.

Linux is quite new to me, and I'll be very thankfull if someone please could explain exactly what to do, if there is anything else to do when sudo apt-get install linux-backports-modules-jaunty doesn't work.

It kind of sucks to have a netbook with no wifi (:

---

### Post by donmatas on 2009-12-24
> **stina said:**
> I still cant get my wifi working on my NB200.

When I bought it I hurried to install netbook remix without thinking of turning wifi on in windows.
I have tried the sudo apt-get install linux-backports-modules-jaunty, but it doesnt work.
(:

I'Ve the same problem!!! it's there a solution?

thanks
DM

---

### Post by aiyoaiyo on 2009-12-24
Sorry for getting back late.

After upgrading to the latest kernel 2.6.31-17, the speaker doesn't work again. This time, I did some experiment. The steps are: 
1.
I removed the new alsa-driver and alsa-utils (version 1.0.21, alsa-lib 1.0.21 is kept on my nb205).

2. 
sudo apt-get --purge remove linux-sound-base alsa-base alsa-utils
sudo apt-get install linux-sound-base alsa-base alsa-utils

3.
alsaconf

4.
in "alsa-base.conf", add:
options snd-hda-intel index=0 model=toshiba
to the end of the file, restart

5.
change the last line in "alsa-base.conf" (the one you added from step 4) to:
options snd-hda-intel index=0 model=auto
restart again.

And miraculously, the internal speaker starts working.

Some additional information:
a -- my "aplay -l" output:
**** List of PLAYBACK Hardware Devices ****
card 0: Intel [HDA Intel], device 0: ALC272 Analog [ALC272 Analog]
  Subdevices: 1/1
  Subdevice #0: subdevice #0

b -- my alsamixer options:
master, headphone, pcm, (front mic/and boost, mic/and boost, beep)
[options in () are muted, and I haven't found it necessary to unmute them yet.]

Hope this can be helpful.

> **dimeotane said:**
> It's rather strange. I've updated my alsa to 1.0.21 and used your alsa-base.conf but no audio through headphones or speaker. 
If I unmute the mic inputs I hear the mic through the headphones.
If I use options=asus-mode4, and restart alsa, I get audio through headphones only.  So confused!
  Perhaps someone else might be able to repeat your success?

Perhaps I haven't done the Alsa upgrade correctly.
Could you explain in more detail the steps you followed in your alsa upgrade?

You said to remove the old drivers. Like this: 
sudo apt-get --purge remove linux-sound-base alsa-base alsa-utils

Did you reinstall them after like this?
sudo apt-get install linux-sound-base alsa-base alsa-utils

Or did you skip that step and then only compile the alsa-driver alsa-lib alsa-utils from the realtek website?

Did you follow the (vague) instructions from the realtek divers?  They included some into about what to add to your /etc/modules file.  If not were there some specific instructions you followed when installing ALSA ?

---

### Post by dimeotane on 2009-12-26
I'm still using headphones, but I have bluetooth working now thanks to all you Ubuntu Gurus here! You all :guitar: rock & I couldn't figure it out without you!  I posted the steps I did on my blog. 

Now that bluetooth works, I'm hoping to soon set up the netbook to be tethered through bluetooth to my cell to use my (cheap) unlimited data cellphone plan.  Wouldn't that be cool? I'll keep you posted how it works out.

---

### Post by jeroenimo on 2010-01-03
Got sound worked out now, similar to the post above, but a little easier


this kernel:
root@NetBookPro:~# uname -a
Linux NetBookPro 2.6.32-02063202-generic #02063202 SMP Sat Dec 19 11:00:49 UTC 2009 i686 GNU/Linux

With this line in my /etc/modprobe.d/alsa-base.conf

options snd-hda-intel index=0 model=auto

kernel can be found here:

[http://kernel.ubuntu.com/~kernel-ppa/mainline/v2.6.32.2/](http://kernel.ubuntu.com/~kernel-ppa/mainline/v2.6.32.2/)

I have to say though, that this is an unstable kernel, and I have some issues, after suspend my screen starts flickering once in a while and I get sometimes a  blank screen, and only a reboot works then.. but hey I have alsa sound ;-)

---

### Post by donmatas on 2010-01-07
> **stina said:**
> I still cant get my wifi working on my NB200.

When I bought it I hurried to install netbook remix without thinking of turning wifi on in windows.
I have tried the sudo apt-get install linux-backports-modules-jaunty, but it doesnt work.

Linux is quite new to me, and I'll be very thankfull if someone please could explain exactly what to do, if there is anything else to do when sudo apt-get install linux-backports-modules-jaunty doesn't work.

It kind of sucks to have a netbook with no wifi (:

I had the same problem. The solution: reinstall win$ and turn on the wifi

salud
DM

---

### Post by donmatas on 2010-01-07
Hello everyone:

i have install 9.04 successfully. Until now i have no problem, wifi works even speakers sound. The only thing that doesn't work it's the capture function. Any one know how to configure it?

thanks
DM

---

### Post by Leesa on 2010-01-10
> **donmatas said:**
> I had the same problem. The solution: reinstall win$ and turn on the wifi

salud
DM
More simple solution:
[http://ubuntuforums.org/showpost.php?p=7807904&postcount=49](http://ubuntuforums.org/showpost.php?p=7807904&postcount=49)

> **Leesa said:**
> But still drops on heavy load... But reconnects fast.
Trying to copy 1Gb file via scp it dropped & reconnected 5 times.
This was wifi router issue, no drops with another router now.

---

### Post by elmer_fudd_gantry on 2010-01-16
I bought an NB205-N312 for my six-year-old daughter. Wanted to run Edubuntu Karmic. No sound. Tried Karmic NBR, Jaunty, and Hardy. No sound. No luck with Mint Helena or OpenSUSE 11.2 either. Tried Qimo (built on Xubuntu, probably Jaunty) and got sound. Gave up before trying Xubuntu Karmic. My daughter wanted her computer *now.* Reloaded Windows. I'm giving up for now and hoping the problem will get fixed in Lucid. Looks like there is a lot of work going on to fix this issue. Personally, I'm not ready to start recompiling the kernel.

---

### Post by jeroenimo on 2010-01-17
If you install the 2.6.32 kernel like I mentioned above, you will have problems if you suspend your nb200/nb205, the screen will flicker and will go dead after a time.

There is a fix for this issue

edit /etc/default/grub as root with your favorite editor and add this option to GRUB_CMDLINE_LINUX=""

i915.powersave=0

so it looks like this

GRUB_CMDLINE_LINUX="i915.powersave=0"

save the file and run

```
sudo update-grub2
```

reboot and the screen going dead and the annoying flicker will be gone.

I sometimes have after say 10 times suspending and waking up that sound drops out, although very rarely.

I have a fully working nb200 now.

even skype and other recording stuff works flawless..

---

### Post by donmatas on 2010-01-18
> **Nick255 said:**
> I had the same problem.  I believe it is caused by the built in webcam being powered even when the system is turned off thanks to the Sleep and Charge feature.  Try adding 'echo auto > /sys/bus/usb/devices/1-2/power/level' and 'echo 1 >/sys/bus/usb/devices/1-2/power/autosuspend' to your init scripts or /etc/profile to make sure the camera gets shut off when you suspend or power down.  While you can blacklist the uvcvideo module to prevent the camera from working, that won't prevent it from sucking up power.

I have the same problem but i'm not an expert and i 've some problems to understand English. could yo make a simple "how to" for making it easy, please?

thanks
M

---

### Post by Igneo676 on 2010-01-19
Though I am wondering, will the .deb for the kernel work in other distros like Debian or can I find a version to compile for Moblin? Fedora? OpenSuse?

Any guides for doing the latter? Could I use alien...?

Going to run Ubuntu Moblin Remix methinks, but that can only last for so long I am afraid...
...may use the Kubuntu Netbook when it comes out in its entirety in Lucid after I remove the custom netbook launcher...

A fully working Toshiba NB205 is quite exciting though...

---

### Post by pwebster25 on 2010-01-22
Based on all of your experience, would you use jaunty or karmic on a new nb205-325?  Is NBR necessary  or just a preferred display?  I don't really like the way it organizes the desktop.  Just not used to it.

I have 50 of these coming in and I will put xp pro on all of them but I want to dual boot a few on ubuntu, just to see what kids do (in a middle school).  I use karmic on an acer aspire one at home.

Looks like there will be some wifi and sound issues.  Not thinking I want to wrestle with that for 50 of them.

Thanks

---

### Post by muffinman on 2010-01-22
Has anyone had issues with using the auto changing wallpaper not being displayed / working on 9.10 & 10.04 alpha 2 UNR [B]ONLY [B]for Toshiba NB 200???? Desktop versions work fine.
Other wallpapers fine but would be nice to have this working as well :)

---

### Post by jay140261 on 2010-02-10
> **jeroenimo said:**
> Karmic koala runs fine so far, still no sound on the speaker, but there is a fix due, jaunty seems to be fixed in proposed.

I have Bluetooth running now and omnibook compiles fine now after some editing

here's how you do it:

```
sudo apt-get install module-assistant build-essential
```
```
wget http://dl.getdropbox.com/u/362618/omnibook-source_2.20070211%2Bsvn20071217-1_all.deb
```
```
sudo dpkg -i omnibook-source_2.20070211+svn20071217-1_all.deb
```
```
sudo cd /usr/src/
```
```
sudo tar xjf omnibook.tar.bz2
```
```
sudo cd modules/omnibook/
```
```
sudo nano init.c
```
hit ctrl-w and type "proc_entry->owner = THIS_MODULE;"
when you get to that line add two // in front of it and make sure it look like this"

// proc_entry->owner = THIS_MODULE;

ctrl-o ctrl-x to save the file

now we compile omnibook

```
sudo m-a build omnibook-source -O
```
```
sudo m-a install omnibook-source
```

now we test 

```
sudo modprobe omnibook ectype=14
```

The bluetooth should appear in you menubar

Now we make things persistent:

```
sudo nano /etc/modules
```

add the line "omnibook" (without "")

save the file

```
sudo nano /etc/modprobe.d/omnibook.conf
```

add this line without "" "options omnibook ectype=14 userset=0 lcd=0 display=0 blank=0 battery=0 ac=0 bluetooth=1"

save the file and voila you are ready ;-)

reboot and Bluetooth should be fine, after sleep or hibernate it could be it malfunctions, but for that you can create a file that restarts bluetooth

like this:

```
nano /etc/pm/power.d/89bluetooth
```

and put this in:

"#!/bin/bash
rmmod -f omnibook
modprobe omnibook ectype=14" (without "")

```
chmod +x /etc/pm/power.d/89bluetooth
```

and after sleep hibernate bluetooth should work too

Hi I am following your thread and get stuck at sudo cd /usr/src/

response is command not found

i have a NB 205 where the bluetooth is not working and I am trying to get your instructions done. Pls check and explain if something is wrong. This is a complete noob and am cutting and pasting from your thread. Thanks

---

### Post by RogerLK on 2010-02-10
jay140261, 

just drop the "sudo" in the command line for cd command and it will work.

Correct command:  cd /usr/src/

The same is true for the command two positions further down:

Correct command:  cd modules/omnibook/

Hope that helps!;)

---

### Post by jay140261 on 2010-02-10
> **RogerLK said:**
> jay140261, 

just drop the "sudo" in the command line for cd command and it will work.

Correct command:  cd /usr/src/

The same is true for the command two positions further down:

Correct command:  cd modules/omnibook/

Hope that helps!;)


Thanks. I had taken sudo off initiall but probably was in the changed directory. After your suggesting, opened the terminal window again and worked. Guess it can be intimidating but once you manage it, gives you that gleeful pleasure of having accomplished something. :)

thanks very much to you and to the initial Guru who laid out the steps. got bluetooth working!

---

### Post by jay140261 on 2010-02-10
> **jay140261 said:**
> Thanks. I had taken sudo off initiall but probably was in the changed directory. After your suggesting, opened the terminal window again and worked. Guess it can be intimidating but once you manage it, gives you that gleeful pleasure of having accomplished something. :)

thanks very much to you and to the initial Guru who laid out the steps. got bluetooth working!

I had loaded all the bluetooth packages like kdebluetooth as well as other Bluetooth packages. Can I now uninstall them as the compiled omnibook works?

Are there any dependencies that I must take care of? thanks

---

### Post by jay140261 on 2010-02-10
> **RogerLK said:**
> jay140261, 

just drop the "sudo" in the command line for cd command and it will work.

Correct command:  cd /usr/src/

The same is true for the command two positions further down:

Correct command:  cd modules/omnibook/

Hope that helps!;)

I had loaded all the bluetooth packages like kdebluetooth as well as other Bluetooth packages. Can I now uninstall them as the compiled omnibook works?

Are there any dependencies that I must take care of? thanks

---

### Post by jay140261 on 2010-02-10
I had loaded all the bluetooth packages like kdebluetooth as well as other Bluetooth packages. Can I now uninstall them as the compiled omnibook works?

Are there any dependencies that I must take care of? thanks
jay140261 is online now Report Post   	Edit/Delete Message

---

### Post by RogerLK on 2010-02-11
I do not believe you need to keep any of the Bluetooth packages you had installed previous to installing the omnibook package. I can not speak for any dependencies, though. But what can happen? Worst case you break your Bluetooth installation and just repeat the installation of the omnibook files. The only thing I have on my machine is the “Bluetooth Preferences” which came with the stock install of Karmic (if I remember correctly, has been a while ;)).

I’ve been following this thread for quiet some time and there have been many questions about what works, and what does not work. I found many great solutions in this thread – in fact, I’m at a point now where I would consider my NB205 working (almost) perfectly. 

For those who are interested, this is a summary of my configuration and experience.

Specs:
- NB205 with 2G RAM
- Karmic with Kernel 2.6.32-02063202-generic (per post 141)
- Omnibook modules installed for Bluetooth (per post 118)
- Bleeding edge drivers for WLAN not installed (had them on previous Kernel and they worked great, but didn’t install properly on new Kernel and I didn’t feel like spending much time on tracking down the problem). The WiFi performance with the new Kernel does not appear to be much different from what I had before with old Kernel and bleeding edge drivers (no dropped connections so far). :D

SD Card drive:	        OK
LAN:			OK
WiFi:			OK
Bluetooth:		OK
WiFi + BT together:	OK (no interference issues, use BT mouse and headset w/ WIFI)	
External monitor:	OK
USB ports:		OK
Webcam		        OK

Reason for the Kernel upgrade was sound, so here are the test results:

Standard sound :

Internal microphone:	OK
External microphone:	OK
Internal Speaker :	OK
Headphones :		OK
Internal speaker off when headphones plugged in : 	OK
Internal microphone off when microphone plugged in:	OK 

Sound via Bluetooth (on Motorola H375; after connecting, change input and output accordingly in sound preferences):

Headphone:	OK
Microphone:	OK
Automatic reconnection to standard sound when Bluetooth device switched off:	OK

Hot Keys:

FN-ESC (mute/unmute):	        OK
FN-F1 (lock screen):		OK (after editing keyboard shortcuts)
FN-F3 (suspend):		OK
FN-F6 (brightness down):	OK
FN-F7 (brightness up):	        OK
FN-F10 (cursor overlay):	OK
FN-F11 (num pad overlay):	OK
FN-3 (volume down):		OK
FN-4 (volume up):		OK

Not working (don’t get scan codes and don’t feel like messing with it; none of these functions are particularly important for me to have on a hot key):

FN-F2 (power options)
FN-F4 (hibernate)
FN-F5 (display select)
FN-F8 (wireless options)
FN-F9 (touchpad on/off)
FN-F12 (scroll lock)
FN-1 (zoom out)
FN-2 (zoom in)

Kernel stability seems good, no problems so far except for hibernate not working (which is really the least of my worries, I’m not in the habit of using hibernate at all after several fatal crashes with data loss when trying to hibernate the “other” operating system).

---

### Post by RogerLK on 2010-02-11
Oops, go caught by a smiley...   :oops:

In my previous post, the reference to the omnibook modules is post 118.

---

### Post by jay140261 on 2010-02-11
Thanks Roger, I have had quite a good experience loading Ubuntu NBR 9.10. Except Bluetooth everything worked and when I did try to take the other programs like libgnome-bluetooth7 and libgnome-bluetooth-dev, it also took the network-manager-gnome out. Due to this I lost the network icon on the menu bar but the network still worked.

I also had loaded Linum Mint, which was also good but it does partitioning which was irritating as I use Acronis to back up. I had a backup of my dual boot and loaded that back after using fdisk to delete and recover the partition space back for Acronis Recovery Zone.

I am quite happy and if I could manage to get a Lotus Organiser 6 work around, i would probably leave Windows for good. I travel a lot and need to keep track of the number of days I am out of India to ensure that I am a non resident Indian for the purpose of tax.

Like yourself I do not bother about hibernation so I am not really trying hard. I of course do not have the sound working on the laptops speakers so will try that and see if I can manage to kickstart the same.

thanks and appreciate your listing as it confirms what works on my NB205.

---

### Post by RogerLK on 2010-02-11
> Has anyone had issues with using the auto changing wallpaper not being displayed / working on 9.10 & 10.04 alpha 2 UNR [B]ONLY [B]for Toshiba NB 200???? Desktop versions work fine.
Other wallpapers fine but would be nice to have this working as well 

muffinman,

I assume you are trying "Drapes" to change the wallpaper automatically (if not, you can install it from the Ubuntu Software Center). The problem with drapes is that it will not start properly if put into "startup applications". Other apps seem to interfere with the loading process of Drapes. It will work fine, if you manually start the application. This is a bit annoying, but there is a work-around (this assumes that Drapes has been installed already).

Open a terminal and then type:

```
cd /usr/bin
sudo gedit drapestart
```

This opens a new file with the name "drapestart" in Gedit.

Now (in Gedit) type:

```
sh -c "sleep 20 && drapes &"
```

Save the file and exit Gedit.

Now you need to make the file "drapestart" executable.

The easiest way (that's my opinion, command line purists will disagree) is this. In the terminal, type:

```
gksudo nautilus
```

Now you can navigate to /usr/bin and change the properties of "drapestart" to executable (check box). Close Nautilus. Close the terminal. 

Start Drapes if it is not running already. Right-click on the icon in the panel and select "preferences". Click on the "general" tab and make sure the box "start desktop drapes on start" is unchecked.

Close the preferences window. Go to "system -> preferences" and open "startup applications". Add the "drapestart" file and close.

Next time you boot your computer, all apps in "startup applications" will load, but Drapes will only load after a 20 second delay. That takes care of the interference and the Drapes icon will show up in the panel.

Have fun! :D

---

### Post by -iceblade on 2010-02-11
is there any way to disable and enable the wifi without having to go into the BIOS? it'd be helpful in saving battery life. 

also, how much battery does everyone get? with wifi and minimum brightness i get something like 4 or 5 hours. 6 with 7, and 8 with the original XP as far as i could remember

i've tried using PowerTOP but can't seem to figure out how to make it save its changes. 

not a very experienced ubuntu user :(

---

### Post by wnderinguy34 on 2010-02-11
I've gotten BT working via the above posted,but now for some reason my Screensaver keeps trying to activate and asks for a password even though I have no password set ?
I'm thinking it may have something to do with this line 
> add this line without "" "options omnibook ectype=14 userset=0 lcd=0  display=0 blank=0 battery=0 ac=0 bluetooth=1"
Just to confirm those are Zeros not capital letter O, correct?

---

### Post by RogerLK on 2010-02-11
> I've gotten BT working via the above posted,but now for some reason my Screensaver keeps trying to activate and asks for a password even though I have no password set ?
I'm thinking it may have something to do with this line
Quote:
add this line without "" "options omnibook ectype=14 userset=0 lcd=0 display=0 blank=0 battery=0 ac=0 bluetooth=1"
Just to confirm those are Zeros not capital letter O, correct? 

You are correct, those are Zeros (and I don't think any of this should start your screensaver). I have no idea what messed that up. Are you able to change the settings, or does the system lock you out?

---

### Post by wnderinguy34 on 2010-02-11
> **RogerLK said:**
> You are correct, those are Zeros (and I don't think any of this should start your screensaver). I have no idea what messed that up. Are you able to change the settings, or does the system lock you out?

I've extended the time before the screensaver is set to kick in ,but haven't had too much time to test things,seems to be better though.This Netbook is only a test/play rig ,so I'll give it day or two before looking at it again through fresh eyes/mind.It took me several tries to get the Omnibook code type in ,because I was missed  a "space"  when typing.

---

### Post by roryd on 2010-02-18
> **jeroenimo said:**
> Updating to bleeding edge compat-wireless has given me a LOT better performance and no more dropouts on wifi.

This is how you do it:

```
sudo apt-get install build essential
```

```
wget http://wireless.kernel.org/download/compat-wireless-2.6/compat-wireless-2.6.tar.bz2
```

If this does not work, surf to [http://linuxwireless.org/en/users/Download#Where_to_download_bleeding_edge](http://linuxwireless.org/en/users/Download#Where_to_download_bleeding_edge) and download the tarball in the directory you are..

```
tar xjf compat-wireless-*tar.bz2
```

```
cd compat
``` (hit tab to complete the path)

```
make
```
```
sudo make install
```
```
sudo make unload
```
```
sudo modprobe ath9k
```

enjoy you troublefree wifi with your atheros card

P.S. this IS beelding edge, it could also fail ofcourse,use at own risk, reverting to the original driver is very easy though

```
sudo make unload
```
```
sudo make uninstall
```
```
sudo modprobe ath9k
```

or reboot

If you run the command just before the make then the compile will run considerably quicker :D

```
 ./scripts/driver-select ath9k 
```

---

### Post by muffinman on 2010-02-20
> **RogerLK said:**
> muffinman,

I assume you are trying "Drapes" to change the wallpaper automatically (if not, you can install it from the Ubuntu Software Center). The problem with drapes is that it will not start properly if put into "startup applications". Other apps seem to interfere with the loading process of Drapes. It will work fine, if you manually start the application. This is a bit annoying, but there is a work-around (this assumes that Drapes has been installed already).

Open a terminal and then type:

```
cd /usr/bin
sudo gedit drapestart
```

This opens a new file with the name "drapestart" in Gedit.

Now (in Gedit) type:

```
sh -c "sleep 20 && drapes &"
```

Save the file and exit Gedit.

Now you need to make the file "drapestart" executable.

The easiest way (that's my opinion, command line purists will disagree) is this. In the terminal, type:

```
gksudo nautilus
```

Now you can navigate to /usr/bin and change the properties of "drapestart" to executable (check box). Close Nautilus. Close the terminal. 

Start Drapes if it is not running already. Right-click on the icon in the panel and select "preferences". Click on the "general" tab and make sure the box "start desktop drapes on start" is unchecked.

Close the preferences window. Go to "system -> preferences" and open "startup applications". Add the "drapestart" file and close.

Next time you boot your computer, all apps in "startup applications" will load, but Drapes will only load after a 20 second delay. That takes care of the interference and the Drapes icon will show up in the panel.

Have fun! :D



Thanks for that Roger LK.
I was referring to the cosmos auto changing wallpaper that comes standard with 9.10 & so far with 10.04.
I've created an entry in launchpad.
[https://bugs.launchpad.net/ubuntu/+bug/518242](https://bugs.launchpad.net/ubuntu/+bug/518242)
See my screenshot attachments of the problem.

On a side note has anyone tried installing an SSD drive in their NB 200/205 with Ubuntu? Any performance improvements / battery life?
Cheers everyone. Great forum

---

### Post by Leesa on 2010-02-26
> **-iceblade said:**
> is there any way to disable and enable the wifi without having to go into the BIOS? it'd be helpful in saving battery life. 

echo 0 > /proc/omnibook/bluetooth
echo 0 > /proc/omnibook/wifi

echo 1 > /proc/omnibook/bluetooth
echo 1 > /proc/omnibook/wifi

---

### Post by frhost on 2010-02-27
Good thread.  Been reading through this the last week trying to set up my NB205. Unfortunately I have managed to end up worse than when I started.  Here is my story.
New Tosh NB205 250GB hd, 2gb ram, running 7 starter.
On install system was ok then crashed during updates so I had to reinstall grub.
Did some multimedia updates.
Wireless was working. Except for secure networks.
No sound.
I tried the OSS and got sound working only to find no place to get oss skype.(Part of the updates were in an attempt to get webcam capabilties with my family, all on windows)
Video fix helped a little for videos.
Experiencing the screen dimming and also the slowdown if I did not keep on the tougchpad to make it stay alive.
Somewhere along the way wireless just quit.  I finally got partially connected to my secure network then started getting all these weird symbols on the network manager and then it quit.
I tried the bleeding edge fix and still nothing.
I have spent way too much time on this little project.
I am using Ubuntu on two other computers btw with no issues.  Nature of the beast.
I haven't given up yet
Gues I will have to look at a clean install or other alternatives in the mean time.
I hope that these problems will get sorted out in future updates.
Thanks for the good tips here.

---

### Post by johnlogan on 2010-03-02
Hi,
I have an NB200 running ubuntu netbook remix 9.10. When I had problems controlling the volume using the slider on the gnome desktop I discovered this workaround.

I noticed using the alsamixer that the master did nothing to alter my volume output through the headphones and only when the gnome volume slider got down to low levels did it have any effect on the output.

my workaround was to alter the file analog-output.conf.common
```

$ sudo gedit /usr/share/pulseaudio/alsa-mixer/paths/analog-output.conf.common

```there is a section that begins
```

[Element PCM]
switch  = mute
volume = merge
override-map.1 = all
override-map.2 = all-left,all-right

```I added two more sections just before this so it looked like
```

[Element Master]
switch  = mute
volume = ignore

[Element Headphone]
switch = mute
volume = merge

[Element PCM]
switch  = mute
volume = merge
override-map.1 = all
override-map.2 = all-left,all-right
```The then did a reboot

This made the gnome-volume slider much better at controlling the volume through the headphones.

---

### Post by tzirtzi on 2010-03-04
I found this thread very useful when I tried to install Ubuntu on my NB200 last summer, but in the end stuck with Windows 7 as I couldn't get linux running stably. Now that the W7 RC is beginning to expire, I've installed Ubuntu Netbook Remix and everything seems to be working fine (...well. Enough things.). A notable exception is that *sudo apt-get install linux-backports-modules-jaunty* isn't working - Wifi is generally working, except that on my home wifi I only have 40-50% signal compared to more like 80% on Windows (which I've left on here, dual booting) and on my uni network I get 20% or so signal which then repeatedly falls to 0, disconnects, and then reconnects every few minutes (again, no such problems in Windows). When I run *sudo apt-get install linux-backports-modules-jaunty*, it can't find the package:

[i]Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Couldn't find package linux-backports-modules-jaunty[/i]

I don't remember encountering similar problems using Ubuntu Desktop last summer, and I read through the thread and couldn't find a solution. Any having a similar problem?

---

### Post by johnlogan on 2010-03-04
> **tzirtzi said:**
> I found this thread very useful when I tried to install Ubuntu on my NB200 last summer, but in the end stuck with Windows 7 as I couldn't get linux running stably. Now that the W7 RC is beginning to expire, I've installed Ubuntu Netbook Remix and everything seems to be working fine (...well. Enough things.). A notable exception is that *sudo apt-get install linux-backports-modules-jaunty* isn't working - Wifi is generally working, except that on my home wifi I only have 40-50% signal compared to more like 80% on Windows (which I've left on here, dual booting) and on my uni network I get 20% or so signal which then repeatedly falls to 0, disconnects, and then reconnects every few minutes (again, no such problems in Windows). When I run *sudo apt-get install linux-backports-modules-jaunty*, it can't find the package:

[I]Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Couldn't find package linux-backports-modules-jaunty[/I]

I don't remember encountering similar problems using Ubuntu Desktop last summer, and I read through the thread and couldn't find a solution. Any having a similar problem?

if you are running netbook remix 9.10 then it's karmic and not jaunty.

also you need to have backports ticked in your apt sources.

---

### Post by wnderinguy34 on 2010-03-05
> Wifi is generally working, except that on my home wifi I only have  40-50% signal compared to more like 80% on Windows (which I've left on  here, dual booting) and on my uni network I get 20% or so signal which  then repeatedly falls to 0, disconnects, and then reconnects every few  minutes (again, no such problems in Windows)


Some have had success with Karmic and bleeding edge  compat-wireless,if you are indeed running 9.10.


>                      Originally Posted by **jeroenimo**                     [[IMG]http://ubuntuforums.org/images/buttons/viewpost.gif[/IMG]]("http://ubuntuforums.org/showthread.php?p=8349644#post8349644")                 
                 Updating to bleeding edge  compat-wireless has given me a LOT better performance and no more  dropouts on wifi.the instructions are re-posted on page 17 of this thread(didn't want to **Quote** the full  instructions again ),not sure how far back the original instructions were given.

---

### Post by tzirtzi on 2010-03-06
> **johnlogan said:**
> if you are running netbook remix 9.10 then it's karmic and not jaunty.

also you need to have backports ticked in your apt sources.

ah ok thanks, that's got it working - the karmic point should have been pretty obvious really shouldn't it :P

wnderingguy - thanks for pointing that out, i'll try out bleeding edge compat-wireless later, see which get's better results :)

---

### Post by Kodiak-Qc on 2010-03-11
Hello Folks! I've been on Ubuntu since the 9.04 release and I'm more than proud of it. ya' know, Windows is like a hard drug on people who use computers. So let's say I've been sober for some months now... I purchased a netbook at the begining of my college semester (you bet, a NB200 by toshiba).

I installed Ubuntu Karmic (9.10) and I had some sound troubles. I fixed it with the complete and shitty solution just to try it out. I find the speakers not to worth it and I'd like only my headphones to work. Is there a method to inverse the long process? I'm not a brute but I understand the very basics of the linux system.

I used the first method (thelong and crapy one).

---

### Post by donmatas on 2010-03-11
does anyone knows a brief how to to make works ubuntu 9.10 in the NB200? Here it's a caos!

salud
DM

---

### Post by jordilin on 2010-03-13
> **donmatas said:**
> does anyone knows a brief how to to make works ubuntu 9.10 in the NB200? Here it's a caos!

salud
DM

What is exactly your problem? Karmik should install fine in nb-200 32 bits. I'm using that in my nb-200.

---

### Post by donmatas on 2010-03-16
> **jordilin said:**
> What is exactly your problem? Karmik should install fine in nb-200 32 bits. I'm using that in my nb-200.

The problem it's that the battery goes down even when the computer it's off

thanks

DM

NEW: now I have a new problem. 9.10 doesnt works in my toshiba nb200. it gets frozen after a couple of minutes. i cant make any update. I decided to install 9.04 and then upgrade to 9.10 but i have problems with the touchpad that i cant fix with gsynaptic.

help please!

---

### Post by donmatas on 2010-04-06
> **ShaunG said:**
> Hey guys,

Not sure if these will be of any use to anyone, but they are really simple bash scripts to turn camera on/off and turn bluetooth on/off, they are based on ReneVYL's trick.

They work for me so far, and don't seem to be harming anything.

If you want to use them, stick them in /usr/local/bin.They will need to be run as root. You can verify they work by running lsusb before and after running them. You will need to replace BUS_AND_DEVICE_NUM_GOES_HERE with the bus and device number of the camera/bluetooth device. In my case I'd replace it with 1-2 for the camera, and 5-2 for my bluetooth.

Camera/Bluetooth ON
```
#!/bin/bash

# Make sure only root can run our script
if [[ $EUID -ne 0 ]]; then
   echo "This script must be run as root" 1>&2
   exit 1
fi

echo on > /sys/bus/usb/devices/BUS_AND_DEVICE_NUM_GOES_HERE/power/level

```

Camera/Bluetooth OFF

```
same as above, replace on with suspend

```

thanks bro.very useful, but how I can get the bus and device numbers for the camera?

thanks again
DM

---

### Post by BelowGrade on 2010-04-08
I tried out 9.10 UNR on my NB205 in trial mode from a USB stick.  Wireless worked perfectly.   So I went ahead and installed in on the hard drive.   Now there is no wireless at all - the icon at the upper right does not appear, though ifconfig does list a wlan0 device as being present.

Do I still need to install the backport thing?  If so, how come it worked in run-from-USB mode?

Also, Windows will no longer boot, but that is a separate issue.

Oops, never mind.  The icon was just very faint and I missed the popup saying "click hear to connect".

---

### Post by psychok7 on 2010-04-13
hi there im using unr karmic in a nb200 .. any development on the sound (computer speakers) ? my wifi is working and my headphones.. by the way, when is the new unr coming out? thanks

---

### Post by donmatas on 2010-04-13
> **psychok7 said:**
> hi there im using unr karmic in a nb200 .. any development on the sound (computer speakers) ? my wifi is working and my headphones.. by the way, when is the new unr coming out? thanks

do you have the battery issue? if not, could you send us your lsusb?

thanks

DM

---

### Post by psychok7 on 2010-04-13
> **donmatas said:**
> do you have the battery issue? if not, could you send us your lsusb?

thanks

DM

wht battery issue? anyways here it is :
lsusb
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 003: ID 04f2:b128 Chicony Electronics Co., Ltd 
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 004: ID 04f3:0210 Elan Microelectronics Corp. AM-400 Hama Optical Mouse
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub

---

### Post by donmatas on 2010-04-13
> **psychok7 said:**
> hi there im using unr karmic in a nb200 .. any development on the sound (computer speakers) ? my wifi is working and my headphones.. by the way, when is the new unr coming out? thanks

> **psychok7 said:**
> wht battery issue? :


The "battery issue" is that the cam don't turn off when you turn off the NB so your battery goes down even when the computer is off. I was curios if you had the same camera that i have and it like the answer is yes.

---

### Post by psychok7 on 2010-04-13
> **donmatas said:**
> The "battery issue" is that the cam don't turn off when you turn off the NB so your battery goes down even when the computer is off. I was curios if you had the same camera that i have and it like the answer is yes.

well.the blue light from the camera turns off when i close any program that its related to it so i guess i dont have the same problem..havent really tested the battery only got the computer 2day..by the way have u found a workaround to it in case i have the same problem? how about the microphone and the computer speakers?

---

### Post by donmatas on 2010-04-13
> **psychok7 said:**
> well.the blue light from the camera turns off when i close any program that its related to it so i guess i dont have the same problem..havent really tested the battery only got the computer 2day..by the way have u found a workaround to it in case i have the same problem? how about the microphone and the computer speakers?

I haven't get the solution for the battery issue yet but i'm working on it with the help of Shaun. About microphone and speakers I solve it installing 9.04, the only version that work for me.

---

### Post by yourKami on 2010-04-14
my netbook toshiba nb200 boots up in like 60seg, i have no alternative OS. any ideas?

---

### Post by psychok7 on 2010-04-14
> **yourKami said:**
> my netbook toshiba nb200 boots up in like 60seg, i have no alternative OS. any ideas?

try this, let me know if it works:

**Kernel Boot Fix**

As of kernel 2.6.31-18, there have been problems relating to speed and the system intermittently freezing. By default, the NB 205 (and other related models such as the NB 200) sometimes freeze and suffer from low performance due to a power-saving feature of the Linux kernel. Dramatic speed increases have been noted with this feature disabled (boot speeds increased by 20 seconds). If you wish, this feature can be disabled.

To disable the kernel feature (if using the GRUB2 bootloader), use a text editor as root to open the file: /etc/grub.d/10_linux

Find the section near the top that looks as follows:

#############################################################
save_default_entry | sed -e "s/^/\t/"
  prepare_grub_to_access_device ${GRUB_DEVICE_BOOT} | sed -e "s/^/\t/"
  cat << EOF
        linux   ${rel_dirname}/${basename} root=${linux_root_device_thisversion} ro $2
############################################################

Add the following to the end of that last line:

nohz=off

...so the full line reads:

linux    ${rel_dirname}/${basename} root=${linux_root_device_thisversion} ro $2 nohz=off

Then run the following from the Terminal to complete the fix:

sudo update-grub

A reboot will be required to apply the change.

---

### Post by yourKami on 2010-04-15
> **psychok7 said:**
> try this, let me know if it works:

**Kernel Boot Fix**

As of kernel 2.6.31-18, there have been problems relating to speed and the system intermittently freezing. By default, the NB 205 (and other related models such as the NB 200) sometimes freeze and suffer from low performance due to a power-saving feature of the Linux kernel. Dramatic speed increases have been noted with this feature disabled (boot speeds increased by 20 seconds). If you wish, this feature can be disabled.

To disable the kernel feature (if using the GRUB2 bootloader), use a text editor as root to open the file: /etc/grub.d/10_linux

Find the section near the top that looks as follows:

#############################################################
save_default_entry | sed -e "s/^/\t/"
  prepare_grub_to_access_device ${GRUB_DEVICE_BOOT} | sed -e "s/^/\t/"
  cat << EOF
        linux   ${rel_dirname}/${basename} root=${linux_root_device_thisversion} ro $2
############################################################

Add the following to the end of that last line:

nohz=off

...so the full line reads:

linux    ${rel_dirname}/${basename} root=${linux_root_device_thisversion} ro $2 nohz=off

Then run the following from the Terminal to complete the fix:

sudo update-grub

A reboot will be required to apply the change.

I opened that file, but I can't find any of those lines.
Here's my 10_linux file

> #! /bin/sh -e

# grub-mkconfig helper script.
# Copyright (C) 2006,2007,2008,2009,2010  Free Software Foundation, Inc.
#
# GRUB is free software: you can redistribute it and/or modify
# it under the terms of the GNU General Public License as published by
# the Free Software Foundation, either version 3 of the License, or
# (at your option) any later version.
#
# GRUB is distributed in the hope that it will be useful,
# but WITHOUT ANY WARRANTY; without even the implied warranty of
# MERCHANTABILITY or FITNESS FOR A PARTICULAR PURPOSE.  See the
# GNU General Public License for more details.
#
# You should have received a copy of the GNU General Public License
# along with GRUB.  If not, see <http://www.gnu.org/licenses/>.

prefix=/usr
exec_prefix=${prefix}
bindir=${exec_prefix}/bin
libdir=${exec_prefix}/lib
. ${libdir}/grub/grub-mkconfig_lib

export TEXTDOMAIN=grub
export TEXTDOMAINDIR=@LOCALEDIR@

CLASS="--class gnu-linux --class gnu --class os"

if [ "x${GRUB_DISTRIBUTOR}" = "x" ] ; then
  OS=GNU/Linux
else
  OS="${GRUB_DISTRIBUTOR}"
  CLASS="--class $(echo ${GRUB_DISTRIBUTOR} | tr '[A-Z]' '[a-z]' | cut -d' ' -f1) ${CLASS}"
fi

# loop-AES arranges things so that /dev/loop/X can be our root device, but
# the initrds that Linux uses don't like that.
case ${GRUB_DEVICE} in
  /dev/loop/*|/dev/loop[0-9])
    GRUB_DEVICE=`losetup ${GRUB_DEVICE} | sed -e "s/^[^(]*(\([^)]\+\)).*/\1/"`
    # We can't cope with devices loop-mounted from files here.
    case ${GRUB_DEVICE} in
      /dev/*) ;;
      *) exit 0 ;;
    esac
  ;;
esac

if [ "x${GRUB_DEVICE_UUID}" = "x" ] || [ "x${GRUB_DISABLE_LINUX_UUID}" = "xtrue" ] \
    || ! test -e "/dev/disk/by-uuid/${GRUB_DEVICE_UUID}" \
    || [ "`grub-probe -t abstraction --device ${GRUB_DEVICE} | sed -e 's,.*\(lvm\).*,\1,'`" = "lvm"  ] ; then
  LINUX_ROOT_DEVICE=${GRUB_DEVICE}
else
  LINUX_ROOT_DEVICE=UUID=${GRUB_DEVICE_UUID}
fi

# add crashkernel option if we have the required tools
if [ -x "/usr/bin/makedumpfile" ] && [ -x "/sbin/kexec" ]; then
    GRUB_CMDLINE_EXTRA="$GRUB_CMDLINE_EXTRA crashkernel=384M-2G:64M,2G-:128M"
fi

linux_entry ()
{
  os="$1"
  version="$2"
  recovery="$3"
  args="$4"
  if ${recovery} ; then
    title="$(gettext_quoted "%s, with Linux %s (recovery mode)")"
  else
    title="$(gettext_quoted "%s, with Linux %s")"
  fi
  printf "menuentry '${title}' ${CLASS} {\n" "${os}" "${version}"
  cat << EOF
	recordfail
EOF
  save_default_entry | sed -e "s/^/\t/"

  if [ "x$GRUB_GFXPAYLOAD_LINUX" != x ]; then
	  cat << EOF
	set gfxpayload=$GRUB_GFXPAYLOAD_LINUX
EOF
  fi

  if [ -z "${prepare_boot_cache}" ]; then
    prepare_boot_cache="$(prepare_grub_to_access_device ${GRUB_DEVICE_BOOT} | sed -e "s/^/\t/")"
  fi
  printf '%s\n' "${prepare_boot_cache}"
  if [ "x$5" != "xquiet" ]; then
    cat << EOF
	echo	'$(printf "$(gettext_quoted "Loading Linux %s ...")" ${version})'
EOF
  fi
  cat << EOF
	linux	${rel_dirname}/${basename} root=${linux_root_device_thisversion} ro ${args}
EOF
  if [ "x$5" != "xquiet" ]; then
    cat << EOF
	echo	'$(gettext_quoted "Loading initial ramdisk ...")'
EOF
  fi
  if test -n "${initrd}" ; then
    cat << EOF
	initrd	${rel_dirname}/${initrd}
EOF
  fi
  cat << EOF
}
EOF
}

list=`for i in /boot/vmlinu[xz]-* /vmlinu[xz]-* ; do
        if grub_file_is_not_garbage "$i" ; then echo -n "$i " ; fi
      done`
prepare_boot_cache=

while [ "x$list" != "x" ] ; do
  linux=`version_find_latest $list`
  echo "Found linux image: $linux" >&2
  basename=`basename $linux`
  dirname=`dirname $linux`
  rel_dirname=`make_system_path_relative_to_its_root $dirname`
  version=`echo $basename | sed -e "s,^[^0-9]*-,,g"`
  alt_version=`echo $version | sed -e "s,\.old$,,g"`
  linux_root_device_thisversion="${LINUX_ROOT_DEVICE}"

  initrd=
  for i in "initrd.img-${version}" "initrd-${version}.img" \
	   "initrd-${version}" "initrd.img-${alt_version}" \
	   "initrd-${alt_version}.img" "initrd-${alt_version}"; do
    if test -e "${dirname}/${i}" ; then
      initrd="$i"
      break
    fi
  done
  if test -n "${initrd}" ; then
    echo "Found initrd image: ${dirname}/${initrd}" >&2
  else
    # "UUID=" magic is parsed by initrds.  Since there's no initrd, it can't work here.
    linux_root_device_thisversion=${GRUB_DEVICE}
  fi

  linux_entry "${OS}" "${version}" false \
      "${GRUB_CMDLINE_LINUX} ${GRUB_CMDLINE_EXTRA} ${GRUB_CMDLINE_LINUX_DEFAULT}" \
      quiet
  if [ "x${GRUB_DISABLE_LINUX_RECOVERY}" != "xtrue" ]; then
    linux_entry "${OS}" "${version}" true \
	"single ${GRUB_CMDLINE_LINUX}"
  fi

  list=`echo $list | tr ' ' '\n' | grep -vx $linux | tr '\n' ' '`
done

thanks by the way :]

---

### Post by psychok7 on 2010-04-15
> **yourKami said:**
> I opened that file, but I can't find any of those lines.
Here's my 10_linux file



thanks by the way :]

strange..are you using ubuntu karmic netbook remix? thats wht im using

---

### Post by yourKami on 2010-04-15
> **psychok7 said:**
> strange..are you using ubuntu karmic netbook remix? thats wht im using
No, I'm using Ubuntu Lucid Lynx "desktop version"

---

### Post by psychok7 on 2010-04-15
> **yourKami said:**
> No, I'm using Lucid Lynx "desktop version"

damn..isn't that heavy??i don't think this netbooks were made to support something that heavy, well i have the same netbook as you and my advice would be for you to install netbook remix karmic on your computer and wait till the next stable release

---

### Post by Igneo676 on 2010-04-15
There isn't actually much of a difference between desktop and netbook actually...

...all the netbook remix contains is the desktop edition with a new kernel and a few extra packages for a different user interface.

I usually install the netbook edition and just strip off the interface for plain-ol' Ubuntu with my fancy kernel

---

### Post by psychok7 on 2010-04-16
> **Igneo676 said:**
> There isn't actually much of a difference between desktop and netbook actually...

...all the netbook remix contains is the desktop edition with a new kernel and a few extra packages for a different user interface.

I usually install the netbook edition and just strip off the interface for plain-ol' Ubuntu with my fancy kernel

wht are the names of those packages so it can look like the desktop version?eitherways this new kernel its different more optimized for netbooks so i think its always best to install it

---

### Post by Igneo676 on 2010-04-17
I believe it's 2 packages...
...a little sick so lemme see if I can find/recall

netbook-launcher
maximus

...otherwise, just remove a few applets from the gnome panel, replace with desktop applets, and enable Nautilus to draw the desktop through gconf

---

### Post by YoungJim on 2010-04-26
Hi, thanks for this, it worked great for me.

Jim

---

### Post by BelowGrade on 2010-04-26
My NB205 goes into suspend just fine when I close the lid:  after a few seconds the power light goes off completely.   When I open the lid, it starts up instantly, and that is the problem.   I want it to ask for a password when it wakes up.

I have 'Suspend' checked in the gconf-editor power manager "lock" section.  It properly requests a password when booting from a complete shutdown.

---

### Post by psychok7 on 2010-04-29
I just installed the final version of Ubuntu 10.04 netbook remix on my NB200. I found that the boot time is extremely slow and i would like to know if i can use the same Workaround(as 9.10) that i posted before to speed boot time. 
Also my boot wallpaper (forgot about the technical term) doenst show up.. only black screen until the Gdm starts.how can i fix this?
My speakers still don't work also any solutions?

---

### Post by Igneo676 on 2010-04-29
I got it on my laptop and my only problem was sound...
...hmm

The workaround for sound is to add:

options snd-hda-intel index=0 model=auto

to the end of /etc/modprobe.d/alsa-base.conf

[SIZE="2"]- blatantly stole this from the bug report for the Toshiba I might add here 

[https://bugs.launchpad.net/ubuntu/+source/linux/+bug/438318](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/438318)

Not sure how to fix your splash screen, you might look around a little bit though and see if anyone else as the same problems...[/SIZE]

---

### Post by psychok7 on 2010-04-29
> **Igneo676 said:**
> I got it on my laptop and my only problem was sound...
...hmm

The workaround for sound is to add:

options snd-hda-intel index=0 model=auto

to the end of /etc/modprobe.d/alsa-base.conf

[SIZE="2"]- blatantly stole this from the bug report for the Toshiba I might add here 

[https://bugs.launchpad.net/ubuntu/+source/linux/+bug/438318](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/438318)

Not sure how to fix your splash screen, you might look around a little bit though and see if anyone else as the same problems...[/SIZE]

I will try the workaround.. and how about your boot speed?

---

### Post by psychok7 on 2010-04-30
> **psychok7 said:**
> I will try the workaround.. and how about your boot speed?

ok i did the same workaround that i posted previously for ubuntu 9.10 and it also works.. it speeds up boot

---

### Post by djmoore85 on 2010-05-01
Hey yall just wanted to say thanks to everyone, this post has been a lifesaver. Loaded Lucid on my NB205-N312 and thanks to this thread so far it has been seamless. I had some issues with the XP dual-bootability but after I perused the forums and came up with a fix and re-installed Lucid everything is gravy so far. I'll be getting Bluetooth done tomorrow and also getting the ALSA updated so speakers and mic are 100% good. Anyone have suggestions as to the best route for audio, seems to be a few different ways to go about it. Again, thank yall and if there are any questions I am more than happy to answer them. Lol don't know how much help I will be I consider myself still a noob when it comes to Ubuntu and I've been playin with it since 7.10.

---

### Post by Igneo676 on 2010-05-02
My boot speeds are magnificent, haven't had to change anything in the slightest with the minor exception of a quick fix for my sound

---

### Post by jonjonbdx on 2010-05-03
Thanks to everyone on this thread- it gave me the confidence to do the dualboot install of nrm 9.10. For me sound on headphones worked out of the box, as did wifi (70 %). Not bothered about getting the inbuilt speaker working.I updated the bios first through windows(followed toshiba instructions PRECISELY  on their website). My BIOS is 1.90 from 1.2 preinstalled, and I haven't experienced any freeze problems so far.In case some people don't know BIOS access is through f2 key and boot from live cd is with f12 key. Took me a while to figure this out.Next job is to get bluetooth working following leesas insructions.For the live cd install I defragmented c first and ran chdisk, then did the Linux dualboot install.Partitioned using guided install which gave me 30GB for Linux. No problems experienced with getting back into both OS's from GRUB.

---

### Post by EllyBilateralCI on 2010-05-10
> **RogerLK said:**
> muffinman,

I assume you are trying "Drapes" to change the wallpaper automatically (if not, you can install it from the Ubuntu Software Center). The problem with drapes is that it will not start properly if put into "startup applications". Other apps seem to interfere with the loading process of Drapes. It will work fine, if you manually start the application. This is a bit annoying, but there is a work-around (this assumes that Drapes has been installed already).

Open a terminal and then type:

```
cd /usr/bin
sudo gedit drapestart
```This opens a new file with the name "drapestart" in Gedit.

Now (in Gedit) type:

```
sh -c "sleep 20 && drapes &"
```Save the file and exit Gedit.

Now you need to make the file "drapestart" executable.

The easiest way (that's my opinion, command line purists will disagree) is this. In the terminal, type:

```
gksudo nautilus
```Now you can navigate to /usr/bin and change the properties of "drapestart" to executable (check box). Close Nautilus. Close the terminal. 

Start Drapes if it is not running already. Right-click on the icon in the panel and select "preferences". Click on the "general" tab and make sure the box "start desktop drapes on start" is unchecked.

Close the preferences window. Go to "system -> preferences" and open "startup applications". Add the "drapestart" file and close.

Next time you boot your computer, all apps in "startup applications" will load, but Drapes will only load after a 20 second delay. That takes care of the interference and the Drapes icon will show up in the panel.

Have fun! :D

Hey many thanks to you about this Drape - it works magically now!  Took me all morning! Sad, I know.  Many many thanks!

---

### Post by SpeechABZ on 2010-05-13
This thread has been an absolute god send!
Decided to ditch XP shortly after Karmic was released and got it to a pretty good state for a complete noob!  Well, I may as well have been since it was about 5/6 years since I last played with Linux - Red Hat at Uni and a mix of distros at my first Job who were running various mail/file servers of linux boxes.

Have recently upgraded to 2Gb RAM and installed Lucid and it wass pretty good, although about a week later I removed the HDD and stuck in a 40Gb Intel SSD.  The machine now absolutely flies!  Around 12-15 seconds boot time from cold is not to be sniffed at IMO!!!:)

Just getting round to the performance tweaks and sound is working fine with the additional line in alsa-base.conf mentioned previously, wi-fi worked straight from the box as well!  Battery seems to be draining a fair bit when it's powered off though but this may be the web-cam issue that many have posted about so will dig back this thread and bash away at it.

Great work to everyone in this thread though, without it I imagine I'd have possibly become quite disheartened in the beginning!

---

### Post by djbenny on 2010-05-18
updated the kernel to 2.6.34 and the sound from the intermnal speaker started working!!!

---

### Post by jojaba on 2010-05-27
> **djmoore85 said:**
> Hey yall just wanted to say thanks to everyone, this post has been a lifesaver. Loaded Lucid on my NB205-N312 and thanks to this thread so far it has been seamless. I had some issues with the XP dual-bootability but after I perused the forums and came up with a fix and re-installed Lucid everything is gravy so far. 
I also have a problem with boot. Here's my threat : [http://ubuntuforums.org/showthread.php?t=1491197](http://ubuntuforums.org/showthread.php?t=1491197)
Could you please give me your solution ? Thanks in advance. :)

PS : great thread indeed :)

---

### Post by lrgmmc on 2010-05-29
i also have a  unr 10.04 on nb205 and can confirm that upgrading to kernel 2.6.34 the speaker does start working and the muting of the speaker when headphones are plugged in works as well. The same goes for the internal mic. it all seams to be working just fine. This is how i did it. in terminal do ```
[I]mkdir 2.6.34 
cd 2.6.34 
wget  http://kernel.ubuntu.com/~kernel-ppa/mainline/v2.6.34-lucid/linux-headers-2.6.34-020634-generic_2.6.34-020634_i386.deb
wget  http://kernel.ubuntu.com/~kernel-ppa/mainline/v2.6.34-lucid/linux-image-2.6.34-020634-generic_2.6.34-020634_i386.deb
wget  http://kernel.ubuntu.com/~kernel-ppa/mainline/v2.6.34-lucid/linux-headers-2.6.34-020634_2.6.34-020634_all.deb
wget  http://kernel.ubuntu.com/~kernel-ppa/mainline/v2.6.34-lucid/linux-source-2.6.34_2.6.34-020634_all.deb[/I]
sudo dpkg -i *.deb
```when that finishes reboot and enjoy.

---

### Post by TheAsarya on 2010-05-31
Hello,

can someone tell me if the 2.6.34 kernel will eventually be included in the standard upgrade from 9.10 to lucid? In that case I might wait until then to upgrade and fix my sound. Tried reading a few pages on the kernels but it's a bit impenetrable for me.

Cheers

---

### Post by transhumantes on 2010-05-31
Hello everybody,
I have installed the new kernel, but the internal microphone don't work...
Any idea?
Thanks.

---

### Post by Netik09 on 2010-06-04
Did anybody find a way to get the NB205 out of low power mode on Lucid Remix? It's currently running pretty slow and all the solutions I've found are for earlier releases.

---

### Post by jojaba on 2010-06-14
> **lrgmmc said:**
> i also have a  unr 10.04 on nb205 and can confirm that upgrading to kernel 2.6.34 the speaker does start working and the muting of the speaker when headphones are plugged in works as well. The same goes for the internal mic. it all seams to be working just fine. This is how i did it. in terminal do ```
[I]mkdir 2.6.34 
cd 2.6.34 
wget  http://kernel.ubuntu.com/~kernel-ppa/mainline/v2.6.34-lucid/linux-headers-2.6.34-020634-generic_2.6.34-020634_i386.deb
wget  http://kernel.ubuntu.com/~kernel-ppa/mainline/v2.6.34-lucid/linux-image-2.6.34-020634-generic_2.6.34-020634_i386.deb
wget  http://kernel.ubuntu.com/~kernel-ppa/mainline/v2.6.34-lucid/linux-headers-2.6.34-020634_2.6.34-020634_all.deb
wget  http://kernel.ubuntu.com/~kernel-ppa/mainline/v2.6.34-lucid/linux-source-2.6.34_2.6.34-020634_all.deb[/I]
sudo dpkg -i *.deb
```when that finishes reboot and enjoy.
Sorry, I'm a (I'm afraid for all my life) beginner on Ubuntu. I did what you told us to do but, I guess this .deb files should be installed somewhere isn't it ? I reboot but nothing displays in grub (I have dualboot xp-ubuntu) to launch this new kernel.

Thanks in advance for your answer ;)

---

### Post by Igneo676 on 2010-06-24
To get it all working just head back a few pages and check out my solution. This kernel business is overkill when you can just amend a file and be good to go

-.-

---

### Post by jojaba on 2010-06-24
> **Igneo676 said:**
> To get it all working just head back a few pages and check out my solution. This kernel business is overkill when you can just amend a file and be good to go

I finally found how to update the kernel (there was some dependencies to nstall before relaunchng dpkg function). The sound works fine know.
Additionnally, I found a fix for my Ubuntu Boot. Just have to add in /etc/grub.d/10_linux this :
```
nohz=off
```
At the end of this line :
```
linux   ${rel_dirname}/${basename} root=${linux_root_device_thisversion} ro ${args}
```
So that we obtain this : 
```
linux   ${rel_dirname}/${basename} root=${linux_root_device_thisversion} ro ${args} nohz=off
```
After savng ths modifications, you have to update grub :
```
sudo update-grub
```
Ths fix was found here : [https://wiki.ubuntu.com/HardwareSupport/Machines/Netbooks/ToshibaNB205](https://wiki.ubuntu.com/HardwareSupport/Machines/Netbooks/ToshibaNB205) (thanks to djmoore85 for giving me this solution ;))
So now, Ubuntu launches in less than 30 seconds and the sound works good !:)

---

### Post by Cason on 2010-07-02
> **Igneo676 said:**
> To get it all working just head back a few pages and check out my solution. This kernel business is overkill when you can just amend a file and be good to go

-.-

Indeed, I can vouch for this working! I'm running an NB205 with Ubuntu Netbook Remix 10.04. I had followed the earlier instructions in the thread for installing the OSSX stuff for my sound, but while it was functional, it was patchy. So I reinstalled ASLA and PulseAudio, used Igneo's solution, and have full sound/mic functionality.

My only hiccup was that the volume control in the indicator applet was removed in all of that. After seaching for a couple of hours, I found that it could be restored by running "sudo apt-get install indicator-volume".

Also, there's an easier boot-speed work around than anything I've seen in this thread. The full discussion can be found [here]("http://ubuntuforums.org/showthread.php?t=1476638&highlight=toshiba+NB205+slow+boot"), but the pertinent information is:

"To resolve the boot issue with the Toshiba, enter the BIOS [F2] after you power it on, switch to the [Advanced] tab, and change the SATA controller mode from 'AHCI' to 'Compatibility'. That should put your boot time at around 30 seconds or so."

Hope that helps out other people; this thread has been a great help to me!

---

### Post by Cason on 2010-07-03
Oh, and for those who were wanting to know how to restore the battery life to Windows levels in Ubuntu, I found a work around for that too.

Having just gotten everything working, I tested my battery life yesterday: I ran for 4-1/2 hours before I reached the critical level in my battery, but I had been getting around 7 in Windows with the power settings set to preserve battery life. After digging around, I found a program called PowerTOP; you can get it by searching the Ubuntu Software Center. Once installed, however, you have to run it in the terminal by typing: 
```
sudo powertop
```

Once it's open, it will make suggest making various changes as it reads your system's power use (which you can make simply by pressing the key it asks you to). After you give it about a minute or so and you've made the suggested changes, it will be finished and you can quit.

When I did this and manually turned the screen brightness to minimum with the fn keys, I got more than 7 1/2 hours of battery life, which is even more than I ever had running windows (and I was doing things like browsing the internet, listening to music, playing games, etc. the whole time). The only downside is that you have to repeat the PowerTOP procedure every time you reboot. But it is well worth it! To make this easier, I created a "shortcut" so that I could run it from my programs menu.

I hope that helps with complaints about battery usage with the NB205s... :D

Note: I know some of you veterans probably know all of the above already, but I figured I'd post it for other noobs like me. ;)

---

### Post by Igneo676 on 2010-07-05
As far as my solution goes, you shouldn't need to do anything else. It works on a clean install of Ubuntu as of now as long as you do all your updates first

---

### Post by TheAsarya on 2010-07-23
deleted

---

### Post by febrile on 2010-08-27
NB200-10Z with xubuntu karmic 2.6.31-22-generic, fiddling with omnibook module 2.20090707-trunk to try & get things to work.

As reported by previous posters,
ectype=12 gets bluetooth functionality (not much interest to me)

BUT,
ectype=16 gives wifi AND hotkeys (as acpi events, incl the Fn+F8 correctly assigned to WLAN switch), though bluetooth support broken.

So I wonder how tough it is to hack a new ectype for the omnibook module that gets it all working...

---

### Post by pra5508 on 2010-08-28
> **Ultim8Fury said:**
> 

[U][B]
Sound -[/B][/U]

This being linux there are, as always, many paths to the same destination, configuring sound is no exception. 

_**The Easy and Partial Method.**_

The NB200 contains a Realtek ALC272 chip apparently this chip can be configured in many, many ways. The good news, the chip is supported in Linux by the ALSA drivers, the not so good news is that in UNR 9.04 the best you can currently hope for is headphone audio only. If you're willing to live without the latest software, apparently audio works fine in 8.04. Since the internal speakers on the NB200 are completely crap anyway, personally I'd rather have 9.04 and headphones. 

**update to the latest (1.0.20 ) Alsa drivers. **

add the following repository to your sources. 

[https://launchpad.net/~rlinfati/+archive/ppa]("https://launchpad.net/%7Erlinfati/+archive/ppa")

Instructions for how to add the PPA are listed on the site so I won't go over them here. Using your favourite package manager perform the update or from the command line. 

```
sudo apt-get update
sudo apt-get upgrade
```When complete, edit /etc/modprobe.d/alsa-base.conf using your favourite editor. Add the following line to the bottom

```
options snd-hda-intel model=asus-mode4
```adjust the levels in alsamixer and reboot. Plug in some headphones or external speakers and you're good to go. 

_**Advanced but Complete Method**_

This method has been pointed out as fully working and will give speaker output, it is however significantly more involved and to my mind the speaker output just isn't worth the effort. However, for those that are willing to tinker, there is a detailed help tutorial [here]("https://help.ubuntu.com/community/OpenSound"). The general gist of it though it to remove the pulseaudio sound sever and the ALSA drivers and run on the OSS driver with the esound server instead. 

Just An Update:- Just found a post somewhere on Ubuntu Forums (not sure where because I'm having problems with browser recently, and wouldn't show history or pull up previous tabs, however, this is a different, unimportant matter.

The method I have found to resolve audio is as follows:-
Follow 'Ultim8Fury's' guide up to the point of ```
sudo apt-get update
sudo apt-get upgrade
``` Then:-
Edit /etc/modprobe.d/alsa-base.conf using your favourite editor. My preference is gedit.
```
sudo gedit /etc/modprobe.d/alsa-base.conf
```


Now instead of adding the line
```
options snd-hda-intel model=asus-mode4
```
to the bottom of this document, add the following line:-
```
options snd-hda-intel model=auto
```

Finally, reboot the machine.
```
sudo reboot
```
This has resolved all of my problems such as volume keys not working correctly, not being able to use speakers and so on...

Lastly, hopes this works for others in my situation, who are getting infuriated by dodgy audio from their netbook.

---

### Post by Igneo676 on 2010-09-08
I ponder if using a maverick kernel would work on previous versions. Currently running Maverick beta and it gloriously allows everything to work and a kernel swap would be an exceedingly simple solution for say Lucid and before...

---

### Post by pwebster25 on 2010-09-08
What doesn't work in Lucid?  I have some NB205's and a clean install of Lucid seems to work fine.  The audio works both in the speaker and in the headphone jack.  I don't know for sure about the microphone.  I do have the netbook edition on it.

---

### Post by MikeCamel on 2010-09-08
I'm having real problems with Maverick booting on anything past the 2.6.35-15 kernel.  It takes 20 minutes or more to boot, and that's with various control-Cs at the console.  Any ideas appreciated!

---

### Post by Igneo676 on 2010-09-12
On Lucid bluetooth doesn't work, and yeah, takes ages to boot because the computer has a power saving "feature" that stops the hardrive if there is no input. "tickling" - moving finger side to side- on keypad will help speed the boot process or pressing buttons on the keyboard consistently.

So, going from Lucid to Maverick you gain bluetooth, lose reliable system performance because of hard drive.

---

### Post by conor on 2010-09-12
> **Igneo676 said:**
> On Lucid bluetooth doesn't work, and yeah, takes ages to boot because the computer has a power saving "feature" that stops the hardrive if there is no input. "tickling" - moving finger side to side- on keypad will help speed the boot process or pressing buttons on the keyboard consistently.

So, going from Lucid to Maverick you gain bluetooth, lose reliable system performance because of hard drive.

Igneo, you should be able to speed up boottime by changing the SATA control in the bios setting to compatibility.  

It is under the "Advanced" tab near the bottom, I think.  
Please let me know if this works out, as I just today wiped out the Maverick beta to put 10.04 back on.

---

### Post by Igneo676 on 2010-09-14
Yeah, have had that option on since before lucid but still experiencing some times where I gotta tickle the thing awake. It's beta so I guess I can't complain too badly (yet) and I suspect it'll be fixed in the kernel before release

---

### Post by psychok7 on 2010-09-14
dude try this workaround that worked for my nb200 for ubuntu 9.10 and 10.04. have not tried it on 10.10 please let me know if it works

FASTER BOOT (must do)
NOTE:IN UBUNTU LYNX ITS A LITTLE DIFERENT,BUT TRY FINDING SOMETHING SIMILAR TO THIS AND APPLY THE SAME WORKAROUND

To disable the kernel feature (if using the GRUB2 bootloader), use a text editor as root to open the file: /etc/grub.d/10_linux

Find the section near the top that looks as follows:


```

save_default_entry | sed -e "s/^/\t/"
prepare_grub_to_access_device ${GRUB_DEVICE_BOOT} | sed -e "s/^/\t/"
cat << EOF
linux ${rel_dirname}/${basename} root=${linux_root_device_thisversion} ro $2

```

Add the following to the end of that last line:

```
nohz=off
```

...so the full line reads:

```
linux ${rel_dirname}/${basename} root=${linux_root_device_thisversion} ro $2 nohz=off
```

Then run the following from the Terminal to complete the fix:

```
sudo update-grub
```

A reboot will be required to apply the change.

---

### Post by conor on 2010-09-20
There is a bug for this issue here: [https://bugs.launchpad.net/ubuntu/+source/linux/+bug/638434](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/638434)

---

### Post by psychok7 on 2010-10-02
tried upgrading to maverick RC and i am having problems with boot speed.

i read some solution about it but i cant seem to apply them. first 
what is boot parameters? i try adding this line when the boot drops to a shell or something. but it says /bin/sh: intel_idle.max_cstate=0 not found..

please help

---

### Post by conor on 2010-10-02
> **psychok7 said:**
> tried upgrading to maverick RC and i am having problems with boot speed.

i read some solution about it but i cant seem to apply them. first 
what is boot parameters? i try adding this line when the boot drops to a shell or something. but it says /bin/sh: intel_idle.max_cstate=0 not found..

please help

I thought I got this to you over on bug 638434.
What I did:

/etc/default/grub at the end of the options line (where it says quiet splash) or something to that effect, I added intel_idle.max_cstate=0

then run update-grub as root.

---

### Post by psychok7 on 2010-10-10
> **conor said:**
> I thought I got this to you over on bug 638434.
What I did:

/etc/default/grub at the end of the options line (where it says quiet splash) or something to that effect, I added intel_idle.max_cstate=0

then run update-grub as root.

for some reason i couldnt mount the partitions with a live cd to fix it..anyways the final release is out is the fix for the problem already there?

---

### Post by conor on 2010-10-10
I'm downloading it as we speak .. er type.
Here is what the release notes say:
> Lenovo S10-3 systems don't boot. Temporary workaround: add "intel_idle.max_cstate=0" as a kernel paremeter at boot (634702). A fix already exists that will be available only at release time (647071).
So? Someone made as error somewhere.

---

### Post by psychok7 on 2010-10-10
> **conor said:**
> I'm downloading it as we speak .. er type.
Here is what the release notes say:

So? Someone made as error somewhere.

what does this mean? isnt release time the final version?? i installed it and am trying to do this that i read in[https://bugs.launchpad.net/ubuntu/+source/linux/+bug/634702?comments=all]("https://bugs.launchpad.net/ubuntu/+source/linux/+bug/634702?comments=all") but its not working. they say > After install successfully, the first rebooting, press "left shift" after BIOS and enter grub prompt.

Press "e" edit boot parameter, append intel_idle.max_cstate=0 after splash, and press "ctrl-x" to boot. but its not working for some reason after i append intel_idle.max_cstate=0 i press CTRL-X and is goes back to initramfs. when i reboot its not there anymore.. for some reason its not saving the intel_idle.max_cstate=0.. what else should i do?

---

### Post by conor on 2010-10-10
> **psychok7 said:**
> what does this mean? isnt release time the final version?? i installed it and am trying to do this that i read in[https://bugs.launchpad.net/ubuntu/+source/linux/+bug/634702?comments=all]("https://bugs.launchpad.net/ubuntu/+source/linux/+bug/634702?comments=all") but its not working. they say  but its not working for some reason after i append intel_idle.max_cstate=0 i press CTRL-X and is goes back to initramfs. when i reboot its not there anymore.. for some reason its not saving the intel_idle.max_cstate=0.. what else should i do?

Well, release time should mean the final release, but I can tell you that the problem still exists in the final. Once you've done the above steps does it let you boot in once at least? Here it is from the top:

1 - When booting, hold left shift to access the grub menu. (If you have a dual-boot setup, then the menu might show up automatically)

2 - Highlight the ubuntu entry and press e to edit the options.

3 - Add 'intel_idle.max_cstate=0' after the words 'quiet splash'

4 - Hit ctrl-x to boot the computer.

5 - Once you've booted into ubuntu, press alt-F2 to open a run dialog and enter
```
gksu gedit /etc/default/grub
```

6 - look for the line that reads
> GRUB_CMDLINE_LINUX_DEFAULT="quiet splash"
this should be the 9th line. Modify it to read:
> GRUB_CMDLINE_LINUX_DEFAULT="quiet splash intel_idle.max_cstate=0"

7 - Save the file and exit. 

8 - Open a terminal and type the following:
```
sudo update-grub
```

This is all the steps. Now everytime you boot the computer, this option will be active.

---

### Post by bazmonkey on 2010-10-12
Does anyone else get random freezes (a.k.a. a complete crash, no response) when using the cstate=0 fix?  I have SATA set to "Compatability" as well.

I can't figure out how to tell what's going wrong when the crashes happen, but everything, cursor and all, just freezes every once in a while.  Leaving my netbook on for a period of time (for example, on and plugged in while I was at work for four hours) tends to result in a frozen system when I return.

It seems all of the "fixes" have side effects of some sort, be it worthless battery life or something else.  I realize I could just go back to Lucid, but it would be a shame because everything else that's been problematic on this netbook (sound and bluetooth) now work without a hitch.

---

### Post by muffinman on 2010-10-17
G'day Everyone,

I have 10.04 UNE running on my NB200 which works fantastic & just thought I'd share some install notes I've made which I've got from various sources (such as here) & put it all together which may help someone.
Anyway here it goes.

[B][COLOR="Blue"]# Make sure the BIOS is update to date (Version 2.10 currently) as there were some issues earlier on which I had done via Windows.
[/COLOR][/B]
**[COLOR="Blue"]# Install Ubuntu & once installed & running do updates & installing Ubuntu extras from the software centre for MP3, flash etc support.[/COLOR]**

Now for fixes

**[COLOR="Blue"]# No bootup splash screen[/COLOR]**

Open the terminal.
[COLOR="Red"]echo FRAMEBUFFER=y | sudo tee /etc/initramfs-tools/conf.d/splash
sudo update-initramfs -u[/COLOR]

**[COLOR="Blue"]# How to get the sound working[/COLOR]**

Open the terminal.
[COLOR="Red"]sudo gedit /etc/modprobe.d/alsa-base.conf[/COLOR]

Then add the follow line (below) at the bottom of the file then save & close.

[COLOR="Red"]options snd-hda-intel index=0 model=auto[/COLOR]

Then reboot.

**[COLOR="Blue"]# How to get bluetooth working[/COLOR]**

Open the terminal.

For the bluetooth icon appear in your system tray.
[COLOR="Red"]sudo modprobe omnibook ectype=12[/COLOR]

Now make it run upon booting your netbook
[COLOR="Red"]sudo nano /etc/modules[/COLOR]
Add the line below and save the file. (Note to save press ctrl o, press the enter key then ctrl x).
[COLOR="Red"]omnibook[/COLOR]

sudo nano /etc/modprobe.d/omnibook.conf
Add this line.
[COLOR="Red"]options omnibook ectype=12[/COLOR]

Save the file (Using the above method). Now when you reboot, the bluetooth icon should show that it is running.

If you wish bluetooth icon to appear after sleep / hibernate mode then follow below.
[COLOR="Red"]sudo nano /etc/pm/power.d/89bluetooth[/COLOR]
Then add the lines below
[COLOR="Red"]#!/bin/bash
rmmod -f omnibook
modprobe omnibook ectype=12[/COLOR]

Save the file (Using the above method).
To change the permissions so the file can run, type the command below.
[COLOR="Red"]sudo chmod +x /etc/pm/power.d/89bluetooth[/COLOR]

Now after sleep and resume, you should see the bluetooth icon reload in the system tray.

**[COLOR="Blue"]# Better volume control[/COLOR]**

Open the terminal.
[COLOR="Red"]sudo gedit /usr/share/pulseaudio/alsa-mixer/paths/analog-output.conf.common[/COLOR]

Locate section that looks like below

[COLOR="Red"][Element PCM]
switch  = mute
volume = merge
override-map.1 = all
override-map.2 = all-left,all-right[/COLOR]

Add two sections to look like this

[COLOR="Red"][Element Master]
switch  = mute
volume = ignore

[Element Headphone]
switch = mute
volume = merge

[Element PCM]
switch  = mute
volume = merge
override-map.1 = all
override-map.2 = all-left,all-right[/COLOR]

Then reboot.


Hope this helps :).
Cheers.

P.S. Haven't tried Maverick UNE with Unity as 10.04 UNE works fine & still early days for Unity.

---

### Post by psychok7 on 2010-10-17
sweet whoever finds the workarounds for maverick please let us know

---

### Post by tsixlas on 2010-10-23
muffinman, your guide rocks.... but you didn't mention anything about the HUGE stuck problem that every Toshiba NB200  owner has. I gave a try to your solution but no luck for me. Sound not working and whenever you leave the mouse alone, even the system time stack...

---

### Post by joey on 2010-10-25
A few people have had issues getting their Toshiba's to work on Maverick.  Here's the trick I used:
 From a fresh install of Maverick......
 
[LIST=1]
[*]Hop into bios and change AHCI to "compatibility"  - that gives you a (subjective) 400% increase on disk speed
[*]If you get stuck at the busybox menu when booting, follow this [http://ubuntuforums.org/showthread.php?t=1592331](http://ubuntuforums.org/showthread.php?t=1592331) (note you'll have to hold down left-shift after you control-x until you see the disk moving)
[/LIST]
 Notes:
 
[LIST]
[*]sound, bluetooth, etc, all work
[*]I recommend you that you DO NOT encrypt your home disk. (it works but it's slow and disk IO is not very fast on the Tosh)
[/LIST]

---

### Post by Igneo676 on 2010-10-27
Using a lucid kernel w/ muffinman's guide on maverick works fantastic...

---

### Post by pwebster25 on 2010-11-02
> **muffinman said:**
> [B][COLOR="Blue"]# Make sure the BIOS is update to date (Version 2.10 currently) as there were some issues earlier on which I had done via Windows.
[/COLOR][/B]


Is there a way to update the bios for the NB205 in ubuntu?  It appears that the [Toshiba bios tool]("http://www.csd.toshiba.com/cgi-bin/tais/support/jsp/modelContent.jsp?ct=SB&os=&category=&moid=2441128&rpn=PLL23U&modelFilter=NB205-N325WH&selCategory=2756709&selFamily=2336267") is a windows .exe.  I have Ubuntu Maverick installed and it is booting so slow I can't believe it.  Yes, I already had it on SATA compatibility mode in the bios.  I think 10.04 booted much faster.

---

### Post by pwebster25 on 2010-11-02
Conor's most recent post here about the grub fix resolved my problem with boot times in Maverick on the Toshiba NB205.  I've got 50 of them.  Hopefully the grub setup will carry over cleanly with the image, when I ghost them all with FOG.

Paul

---

### Post by Igneo676 on 2010-11-02
I have updated the BIOS using a guide earlier in this thread, but too lazy to find it again. Basically you download the update and extract an ISO file that you use to update :)

Edit:

[http://ubuntuguru.wordpress.com/2009/11/17/bluetooth-and-bios-fixes-for-the-nb200/](http://ubuntuguru.wordpress.com/2009/11/17/bluetooth-and-bios-fixes-for-the-nb200/)

^ This same guy posted something earlier, but I like this better

---

### Post by Fourcultures on 2010-12-04
Updating from Ubuntu 10.04 to 10.10 has caused a freezing problem for some NB200 and similar users. The symptoms are that the display freezes repeatedly, causes music playback stuttering and looping and these freezes can be ended while moving the pointer or pressing keys. One possible solution is listed here. 
[https://bugs.launchpad.net/linux/+bug/657990](https://bugs.launchpad.net/linux/+bug/657990) - especially post #22.

                 > try adding "clocksource=jiffies nolapic_timers" to the kernel command line
parameter.

 sudo pico /etc/default/grub

 change
 GRUB_CMDLINE_LINUX_DEFAULT="quiet splash"

 to
 GRUB_CMDLINE_LINUX_DEFAULT="quiet splash nolapci_timer clocksource=jiffies"

 save changes

 sudo update-grub

 reboot

 sfranzyshen


---

### Post by Dr Bratwurst on 2010-12-05
Hi I'm quite the newbie here and I need some help, I have a (UK) NB200 12N and I installed ubuntu the USB Stick way, I am always connected to my modem usually at 100%, but my internet sometimes fails to display the webpage and gives an error message, I know ubuntu is installed because I did it twice, right now I'm on windows because my internet won't stop failing, EPICALLY.
any help would be appreciated, thanks. :)

---

### Post by mengong on 2010-12-27
my netbook cant detect any sd card .. this is what happen when i type dmesg 

[46460.326486] usb 1-4: new high speed USB device using ehci_hcd and address 15
[46460.704437] usb 1-4: configuration #1 chosen from 1 choice
[46460.710621] scsi9 : SCSI emulation for USB Mass Storage devices
[46460.711112] usb-storage: device found at 15
[46460.711120] usb-storage: waiting for device to settle before scanning
[46465.112558] usb 1-4: USB disconnect, address 15

help plz ..

---

### Post by donmatas on 2010-12-28
In conclusion:
if you want to enyoy your Ubuntu, do not get a NB200!!!

---

### Post by Fourcultures on 2011-01-12
> **donmatas said:**
> In conclusion:
if you want to enyoy your Ubuntu, do not get a NB200!!!

People enjoy different things, don't we? My NB200 wouldn't switch on the wifi card due to having not turned wifi *on* under Windows first (I removed Windows before using it). This is Toshiba's fault, rather than Ubuntu's. There is a Linux fix for this using the omnibook kernel module but it isn't straightforward to implement. It has taken me a few late nights, but I'm sending this message with my newly working wifi connection. The feeling of making the thing work at last is, well, enjoyable.

---

### Post by Fourcultures on 2011-01-12
If you're still interested in fixing this problem, there are several wifi troubleshooting [guides]("https://help.ubuntu.com/community/TroubleShootingGuide") that might help. If you had an error message it would be helpful to quote it to give some idea of what the problem might be.

---

### Post by donmatas on 2011-01-12
> **Fourcultures said:**
> If you're still interested in fixing this problem, there are several wifi troubleshooting [guides]("https://help.ubuntu.com/community/TroubleShootingGuide") that might help. If you had an error message it would be helpful to quote it to give some idea of what the problem might be.

I fixed the wifi problem too, but I could not fix the battery problem (see above). It was a friends netbook, so I had to reinstall winXP. I really enyou to "free" computers form MS, but in this case was imposible

salud
DM

---

### Post by pdallas on 2011-01-16
> **tsixlas said:**
> muffinman, your guide rocks.... but you didn't mention anything about the HUGE stuck problem that every Toshiba NB200  owner has. I gave a try to your solution but no luck for me. Sound not working and whenever you leave the mouse alone, even the system time stack...

[COLOR=SeaGreen]Cheers, muffinman, your guide cleared all issues in one go![/COLOR] :KS

Just for completeness, regarding the issue tsixlas mentioned (geia sou tsikh...), a quote from: [https://wiki.ubuntu.com/HardwareSupport/Machines/Netbooks/ToshibaNB205](https://wiki.ubuntu.com/HardwareSupport/Machines/Netbooks/ToshibaNB205)

1. You must still do this:

Kernel Boot Fix

As of kernel 2.6.31-18, there have been problems relating to speed and the system intermittently freezing. By default, the NB 205 (and other related models such as the NB 200) sometimes freeze and suffer from low performance due to a power-saving feature of the Linux kernel. Dramatic speed increases have been noted with this feature disabled (boot speeds increased by 20 seconds). If you wish, this feature can be disabled.

To disable the kernel feature (if using the GRUB2 bootloader), use a text editor as root to open the file: /etc/grub.d/10_linux

Find the section near the top that looks as follows:

save_default_entry | sed -e "s/^/\t/"
  prepare_grub_to_access_device ${GRUB_DEVICE_BOOT} | sed -e "s/^/\t/"
  cat << EOF
        linux   ${rel_dirname}/${basename} root=${linux_root_device_thisversion} ro $2

Add the following to the end of that last line:

nohz=off

...so the full line reads:

linux    ${rel_dirname}/${basename} root=${linux_root_device_thisversion} ro $2 nohz=off

Then run the following from the Terminal to complete the fix:

sudo update-grub

A reboot will be required to apply the change.

---

### Post by donmatas on 2011-01-18
> **pdallas said:**
> [COLOR=SeaGreen]Cheers, muffinman, your guide cleared all issues in one go![/COLOR] :KS

Just for completeness, regarding the issue tsixlas mentioned (geia sou tsikh...), a quote from: [https://wiki.ubuntu.com/HardwareSupport/Machines/Netbooks/ToshibaNB205](https://wiki.ubuntu.com/HardwareSupport/Machines/Netbooks/ToshibaNB205)

1. You must still do this:

Kernel Boot Fix

As of kernel 2.6.31-18, there have been problems relating to speed and the system intermittently freezing. By default, the NB 205 (and other related models such as the NB 200) sometimes freeze and suffer from low performance due to a power-saving feature of the Linux kernel. Dramatic speed increases have been noted with this feature disabled (boot speeds increased by 20 seconds). If you wish, this feature can be disabled.

To disable the kernel feature (if using the GRUB2 bootloader), use a text editor as root to open the file: /etc/grub.d/10_linux

Find the section near the top that looks as follows:

save_default_entry | sed -e "s/^/\t/"
  prepare_grub_to_access_device ${GRUB_DEVICE_BOOT} | sed -e "s/^/\t/"
  cat << EOF
        linux   ${rel_dirname}/${basename} root=${linux_root_device_thisversion} ro $2

Add the following to the end of that last line:

nohz=off

...so the full line reads:

linux    ${rel_dirname}/${basename} root=${linux_root_device_thisversion} ro $2 nohz=off

Then run the following from the Terminal to complete the fix:

sudo update-grub

A reboot will be required to apply the change.

My gosh! What a nightmare!

---

### Post by ponga on 2011-04-08
All, 

I have a Toshiba netbook NB305. During the install of 10.10 Netbook Edition and even after that, the computer would completely freeze (even the clock stopped ticking) after only 5 seconds or so until I moved the mouse or hit a key - then it would chug again... until of course it would freeze again. Ridiculous! I had to kit a key or keep moving the mouse to keep the install going and just operate in the OS once installed...

Anyway, as some have suggested it's a kernel / ACPI / Atom processor issue. I thought I had to do some crazy stuff like kernel boot parameters that would jack my ACPI (kinda like to have that with a unit running on battery)... however, I dist-upgraded to the latest kernel (2.35.), and the problem appears to be corrected.... until... it froze again. This time, no amount of mouse movement or keyboard activity will bring it back to life. So, one problem fixed and another introduced... still trying to find a solution here unless someone has already figured this out.

Thanks,

ponga

---

### Post by evans5000 on 2011-04-23
Hello, is anyone able to suggest a solution for the following-

I'm running Ubuntu 10.04 Netbook Remix on a Toshiba NB200-10Z (Omnibook and various other tweaks described on previous pages have been isntalled for ages)

I just upgraded the memory from 1GB to 2GB. Now, I'm not sure if this is related, but I just tried to open System Monitor and Hardware test and neither open. 

I did a apt-get update,  which has showed various Python dependency errors for the following- python-semanagem , python-selinux,  python-sepolgen
 policycoreutils,  selinux,  python-gmenu, selinux-policy-default,  python-audit,  python-rpm,  setroubleshoot,  setroubleshoot-plugins,  python-wxversion,  python-wxgtk2.8

I don't know if this problem is memory upgrade related, or some kind of error from another software. Does anyone have any suggestions as to the best way to diagnose and fix this problem?  Or are they a series of inter-related problems.  (Pretty much everything else, software, Virtualbox etc still works fine)

Thanks.

---

### Post by elzy89 on 2011-06-26
Hi folks, had a good read through the thread and tried the instructions outlined in post #118. It didn't work for me, however I don't think the problem is with the drivers now. After running lsusb, I can see the adapter in question is recognised at boot.

On a side note, the bluetooth icon loads up at log on, however it indicates that bluetooth is on. When scanning from an external device, the netbook is undiscovered.

I'm running Natty on an NB200 and everything works except the bluetooth.

lsusb output:
```
Bus 005 Device 002: ID 0930:0508 Toshiba Corp. Integrated Bluetooth HCI
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 002: ID 04f2:b128 Chicony Electronics Co., Ltd 
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub

```Any help with this would be much appreciated.

---

### Post by Igneo676 on 2011-06-29
That's completely bizarre to me, ever since lucid (I think) we've had full bluetooth support. Have you attempted to turn visibility on?

I know that may sound obvious, but just checking, since we have the same laptop and I know bluetooth works fine for me here. I need to rule out the simple first :)

---

### Post by elzy89 on 2011-06-29
Visibility is always on by default on the drop down menu at launcher icon however, when you click the bluetooth icon and load up the next window, it says it is off. So I try turning it off and on again a few times, nothing happens.

I'm confident with nix, been using for a good few years now, although i'm fairly new to Ubuntu.

My main nix server at home is running Natty, serving DHCP, DNS (bind9), NTP, TFTP (PXE), NFS, Samba, LDAP, MySQL, Apache...

I also run another Natty server now for Fuppes, Transmission, OpenTTD, Teamspeak, DNS Rep, plus a few AIR apps that I connect and disconnect to and from the various machines on my network. Got into playing around with this when I bought my iMac and realised X11 was all built in! ;)

So far most things have gone smooth and Ubuntu is great. I'm really enjoying the community and I hope I can bring knowledge and support to others in the future.

---

### Post by Igneo676 on 2011-07-01
I think you surpass myself in computer knowledge then!

If I recall correctly, Natty had my bluetooth working out of the box. Currently I'm running Crunchbang though, so maybe I need to double check? I'll check what I can observe. In the meantime, you might try switching around some kernels, but you may have already done that. Tell us anything you have tried.

---

