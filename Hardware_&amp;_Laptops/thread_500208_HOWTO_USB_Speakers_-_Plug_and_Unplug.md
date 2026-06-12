---
title: "HOWTO: USB Speakers - Plug and Unplug"
date: 2007-07-13
forum: Hardware &amp; Laptops
---

### Post by oiper on 2007-07-13
This is the best I could do after a bit of searching around for a solution. My problem was specifically dealing with the Logitech V10 USB Portable Speakers. I bought them to may up for my laptop's astonishingly poor excuse for speakers. When I plug in the V10's, nothing happens. I can test the audio, but my laptop's sound card takes precedence over the V10's. All of this trouble is because the USB Speakers have their own sound card built into them. So I banged my head against the wall and few times, searched the web high and low, and came up with something.

This solution should also work for a slew of other speakers, including the obvious, Logitech V20 USB Portable Speakers, of which I found quite a few confused posts about. This may also solve some headset woes. Before we start, I also encourage anyone who can improve this/correct me to do so. Ok, here's what to do.

Unplug your USB speakers and run **asoundconf list**.
```

Names of available sound cards:
Intel

```
The **Intel** above refers to my laptop's sound card. Yours will probably be different.

Now plug in your USB speakers and run **asoundconf list** again.
```

Names of available sound cards:
Intel
Audio

```

There are hopefully 2 cards listed. So in my case, **Audio** refers to my Logitech USB speakers.

We are going to write a udev rule to run some scripts when our speakers are plugged/unplugged. To start, I ran **udevinfo -a -p $(udevinfo -q path -n /dev/dsp1)**
Notice that I used /dev/dsp1. This refers to my 2nd sound device, in this case, my Logitech Speakers. On your system, you could be working with something else. Chances are, that if you look at your dsp entries in **/dev/** it will be the highest dsp#. Mine is /dev/dsp1

The udevinfo command above gave me this:
```

  looking at device '/class/sound/dsp1':
    KERNEL=="dsp1"
    SUBSYSTEM=="sound"
    DRIVER==""
    ATTR{dev}=="14:19"

  looking at parent device '/devices/pci0000:00/0000:00:1d.0/usb1/1-2/1-2:1.0':
    KERNELS=="1-2:1.0"
    SUBSYSTEMS=="usb"
    DRIVERS=="snd-usb-audio"
    ATTRS{modalias}=="usb:v0D8Cp0001d0010dc00dsc00dp00ic01isc01ip00"
    ATTRS{bInterfaceProtocol}=="00"
    ATTRS{bInterfaceSubClass}=="01"
    ATTRS{bInterfaceClass}=="01"
    ATTRS{bNumEndpoints}=="00"
    ATTRS{bAlternateSetting}==" 0"
    ATTRS{bInterfaceNumber}=="00"

  looking at parent device '/devices/pci0000:00/0000:00:1d.0/usb1/1-2':
    KERNELS=="1-2"
    SUBSYSTEMS=="usb"
    DRIVERS=="usb"
    ATTRS{product}=="USB Audio"
    ATTRS{manufacturer}=="C-Media INC."
    ATTRS{maxchild}=="0"
  ...
  ...
  etc...

```

Knowing that on my laptop, nothing else should ever be dsp1 except my speakers, I used the first set of info to create a new udev rule.

```

gksudo gedit /etc/udev/rules.d/85-usb-audio.rules

```

Add the following to the new file:
```

KERNEL=="dsp1", ACTION=="add", SUBSYSTEM=="sound",\
        RUN+="/usr/local/bin/select_usb_audio.sh"
KERNEL=="dsp1", ACTION=="remove", SUBSYSTEM=="sound",\
        RUN+="/usr/local/bin/select_laptop_audio.sh"

```

Replace the values in this new file with any those that match your output from the udevinfo command we ran before this.

Taken from a post elsewhere in the forum, we will create some needed files.

Create a folder named **.asound_files** in your user home directory.
```
mkdir ~/.asound_files
```

Run **asoundconf set-default-card Audio**. Replace **Audio**, **Intel**, and my username with your information. (Note: Audio and Intel are the cards listed earlier.)

```

cp .asoundrc.asoundconf .asound_files/Audio
asoundconf set-default-card Intel
cp .asoundrc.asoundconf .asound_files/Intel

```

Now we create a script to manage these files.

```

gksudo gedit /usr/local/bin/select_usb_audio.sh

```

Add these lines to the new file:
```

#!/bin/bash
cd /home/bryan
rm -f .asoundrc.asoundconf
cp .asound_files/Audio .asoundrc.asoundconf

```

```

gksudo gedit /usr/local/bin/select_laptop_audio.sh

```

Add these lines to the new file:
```

#!/bin/bash
cd /home/bryan
rm -f .asoundrc.asoundconf
cp .asound_files/Intel .asoundrc.asoundconf

```

```

sudo chmod +x /usr/local/bin/select_laptop_audio.sh
sudo chmod +x /usr/local/bin/select_usb_audio.sh

```

Now restart udev
```

sudo /etc/init.d/udev restart

```

Ok, if all went well, you should be getting sound from your speakers after you plug them in, and sound from your laptop when you unplug your USB speakers. Note that due to the nature of swapping soundcards, you'll have to close and reopen applications for the sound to work. But hey, restarting Firefox or Banshee is a lot better than having no sound at all. Let me know if I confused anyone or left anything out.

---

### Post by Angelbeast on 2007-09-16
Hello...I'm sorry for troubling you but i'm not very good at this technical sort of stuff...I ran that first command and this is what i got back...

ron@ron-laptop:~$ asoundconf list
Names of available sound cards:
IXP
Modem
Speaker


So now would "Speaker" be my Logitechs? and why is Modem listed?

---

### Post by oiper on 2007-09-18
I don't know what the deal is with modems but they tend to show up in the soundcard lists. I guess the Speaker may be it. Try running the command with and without the Logitechs plugged in. Perhaps that will reveal the right one. If nothing is different, then your speakers are not working. I'd then check out the output from running the "dmesg" command after plugging in your speakers.

---

### Post by zmoink on 2007-10-06
> **oiper said:**
> I don't know what the deal is with modems but they tend to show up in the soundcard lists. I guess the Speaker may be it. Try running the command with and without the Logitechs plugged in. Perhaps that will reveal the right one. If nothing is different, then your speakers are not working. I'd then check out the output from running the "dmesg" command after plugging in your speakers.


I know that this is an "old" thread (2 weeks old ...) but here it goes ...

the modem that appears on the list of the audio hardware that is plugged into your computer, is the modem audio speaker, the one that makes that horrible noise, when dialing a phone number ...

;)

and now some off topic stuff ...

what do you think about the performance of the speakers ?? 

are you happy with the performance, or should i buy others ??

---

### Post by zmoink on 2007-10-06
ok ...

i've just bought a logitech v10 .... 

simply awesome ... 

clean sound ... and works like a charm in my ubuntu laptop :D 

many thanks !!!

---

### Post by nathanscottdaniels on 2008-01-31
I am sorry to reply to such an old thread but I have a small issue.  The master volume of Ubuntu does not affect my Logitech V20 USB Speakers.  They blast music and sound at full power even if Ubuntu says the sound is muted!  I can change the music volume while it is playing using Amarok but that does not affect sound effect volume.  Does anyone know why this is happening to me?

---

### Post by oiper on 2008-02-01
That's odd.

The only volume control that I have is the buttons on the side of the speakers. None of the software mixers control the V10 speakers.

---

### Post by nathanscottdaniels on 2008-02-01
NOTHING is controlling my V20s.  Not even their volume and mute buttons!

---

### Post by WarByte on 2008-02-27
well, seems like an old thread but i found it helpful since i just got the same speakers for myself. i was also wondering about the volume level cause in my case it was really low.

i followed all the steps to get them working but couldnt figure a way to increase the volume past 100% in the players (amarok, kaffeine) and i figured out that after kmix is restarted a new tab appears giving the option to select what mixer we will be using. i have two: 

ESS ES1938 (Solo-1) - ( my laptop speakers)
Logitech Speaker - (the V10 speakers)

once i select the Logitech Speaker the mixer shows one single bar for the volume. it can still not be controlled by the buttons on the speakers but it is originally at 80% i believe and the changes in that bar have noticeable change in the volume and is different from the ones in the players so i can get the desired volume. hope this helps someone.   :)

---

### Post by itsme_n8 on 2008-05-16
PLEASE HELP!!! Great... well I followed the directions (and I'm not blaming the author btw) to a T... and now I have no sound.  Admittedly this is my fault, I am inexperienced, and I didn't back up my home dir.  But please help me get my sound back. 

- I deleted the directory .asound_files.
- I cleared the entries out of: gksudo gedit /etc/udev/rules.d/85-usb-audio.rules.
- I restarted udev.

Now under Sounds, Master Volume is labeled as Volume, and I get no sounds for anything.

-BTW I don't even care about the USB Speakers... I would just like to have sound again.

---

### Post by itsme_n8 on 2008-05-16
Nevermind... I fixed it.  

That sucked.

Word to the wise (especially if you are inexperienced) back up your /home folder.

Nate

---

### Post by Krydahl on 2008-07-10
I've found this solution has stopped working for me in Hardy.

When I plug in my speakers, I get the start-up sound played through them. However, if I try to play music (rhythmbox, exaile, whatever) sound comes out of the laptop speakers.

If I go preferences->sound I can manually change the sound for music playback to the usb sound card and it all works ok, so this is not a big problem. It would be nice if it got autodetected however.

Anyone had any luck getting this to work?

---

### Post by EdThaSlayer on 2008-07-16
Thanks for this how-to! Everything works perfectly with my Logitech S-150 speakers!

---

