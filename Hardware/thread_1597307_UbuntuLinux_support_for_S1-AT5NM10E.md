---
title: "Ubuntu/Linux support for S1-AT5NM10E?"
date: 2010-10-15
forum: Hardware
---

### Post by forbjok on 2010-10-15
Anyone know if Ubuntu supports the hardware in ASUS S1-Series S1-AT5NM10E (ION2-based barebone)?

---

### Post by dennisbinkhorst on 2010-11-18
I am currently testing this system with Ubuntu 10.10.

All drivers except NVIDIA ION2 GT218 are installed correctly by default.
Proprietary NVIDIA drivers are available but I am unable to play 720p and 1080p films so far.

Working on it, but progress is slow.

---

### Post by Allochtoon on 2010-11-27
Im interested in its performance in running concurrently:

1080p hd video
apache/mysql

or concurrently:

sdlmame
apache/mysql

What specs do u have, is the system loud?

What is your exact issue in running 1080p?

---

### Post by floppydisc on 2010-11-28
I'm still struggling with bluetooth and haven't had opportunity to test IR.

Nvidia drivers was pretty straight forward.
Sound over hdmi was little more troublesome but with google I was able to solve it.

Even though I haven't tried the combination apache/mysql I believe that it should work for "home"-usage. I'm running nginx and have no trouble watching 1080p using xbmc simultaneously. I'm just using 2gb ram.

I had some issues with horizontal lag in xbmc and flash when compiz was activated so I disabled it.

---

### Post by chmanie on 2011-01-24
Did someone fix the bluetooth issue? It doesn't work out of the box for me with 10.10. I just can't switch it on. I get a timeout error.

---

### Post by PaulCheap on 2011-01-24
HAs anyone been able to power up the system by using a remote control? I just can't get it to work.

I try to get the system to Suspend and/or Hibrnate mode, but it just doesn't work.. any hints are highly appreciated!

Thanks!

Kind regards
Paul

---

### Post by kcsc on 2011-01-29
[QUOTE=floppydisc;10173098]I'm still struggling with bluetooth and haven't had opportunity to test IR.

Nvidia drivers was pretty straight forward.
Sound over hdmi was little more troublesome but with google I was able to solve it.


Hello

I'd love it if you could explain how you got sound over hdmi working! I have googled and googled and can't get it working (have tried many suggestions). I have eliminated the cable (by playing another device through it).

Thanks

kcsc

---

### Post by kcsc on 2011-01-29
> **kcsc said:**
> [QUOTE=floppydisc;10173098]I'm still struggling with bluetooth and haven't had opportunity to test IR.

Nvidia drivers was pretty straight forward.
Sound over hdmi was little more troublesome but with google I was able to solve it.


Hello

I'd love it if you could explain how you got sound over hdmi working! I have googled and googled and can't get it working (have tried many suggestions). I have eliminated the cable (by playing another device through it).

Thanks

kcsc


I have updated Ubuntu 10.10 running on this box.

Here is what I've tried:

Based on ubuntuforums.org/showpost.php?p=9219191&postcount=212 and the results of aplay -l I created /etc/asoung.conf and added:

 ctl.!default {
     type hw
     card 1
  }
This changed the NVidia HDMI card to the default card in alsamixer rather than the Intel card.

Based on ubuntuforums.org/archive/index.php/t=1617334.html and ubuntuforums.org/showpost.php?p=9988441&postcount=18 I ammended asound.conf to:

pcm.!default {
type hw
card 0
device 1
}

ctl.!default {
     type hw
     card 1
  }

I loaded the backports module as suggested by some posts.

I tried putting "Options    "IgnoreEDID"   "True" in /etc/X11/xorg.conf and turning off "Force full GPU scaling" in the NVidia X settings.

I tried adding these lines (one at a time, not together) to /etc/modprobe.d/alsa-base.conf:

options snd-hda-intel model=ALC887
options snd-hda-intel model=3stack

HDMI is the default option in System > Preferences > Sound on the Output tab and is listed under the Hardware tab with a profile of "Digital Stereo (HDMI) Output".

Not sure what to do next....

Thanks

kcsc

---

### Post by kraff on 2011-02-03
I get sound over hdmi editting the file "/etc/pulse/default.pa" uncomment and change the line

load-module module-alsa-sink device=hw:1,7

I read this info in [Sound over HDMI] [http://ubuntuforums.org/showthread.php?t=1627050](http://ubuntuforums.org/showthread.php?t=1627050)


I can't run bluetooth, the chip is atheros (module ath3k) but dont work for me.

---

### Post by andlinux on 2011-02-06
> **kraff said:**
> I get sound over hdmi editting the file "/etc/pulse/default.pa" uncomment and change the line

load-module module-alsa-sink device=hw:1,7

I read this info in [Sound over HDMI] [http://ubuntuforums.org/showthread.php?t=1627050](http://ubuntuforums.org/showthread.php?t=1627050)


I can't run bluetooth, the chip is atheros (module ath3k) but dont work for me.
I installed XBMC live on the S1-AT5NM10E, but sound isn't working.

If I go to /etc/pulse/ then there is no default.pa file ?

But if I do **aplay -D plughw:1,3 /usr/share/sounds/alsa/Front_Center.wav** then I hear a woman speaking front center.

It's working now I had to uncheck DTS and AC3...

---

### Post by misteraph on 2011-02-18
Same problem with bluetooth...

I noticed another thing during the bios startup. It shows Single Channel mode, although I used the two ram slots. 

Do you see the same thing ?

---

### Post by buppelupp on 2011-05-19
Hello, 

Just a tip about the bluetooth (this is tested and verified)
I found that if you download the latest Windows driver and install it in a Windows environment the installation process also updates the firmware of the bluetooth adapter. 

When this is done, the bluetooth adapter is recognized and works as a normal Bluetooth adapter in Ubuntu. 

Previously I had to use the following trick to even identify the adapter as something useful:

killall bluetoothd
sleep 1
rmmod btusb
rmmod ath3k
modprobe -a ath3k
echo "13d3 3304" > /sys/bus/usb/drivers/ath3k/new_id
modprobe btusb
bluetoothd


Anyways, from here on I am struggling and almost to the point of giving up because there seems to be complete inconsistency between the documentation and reality. I am trying to set this up on an Ubuntu Server without GUI, but none of the files in the various docs exist or seems relevant anymore (for example hcid.conf to name one). So I can't set up my keyboard and mouse to re-connect at startup simply because I don't know if the changes I am making are even read by the bluetooth daemon due to the confusing documentation.

---

### Post by Aldoo on 2011-06-21
Building ath3k.ko from [ath3k.c in Linux-3.0 source]("http://git.kernel.org/?p=linux/kernel/git/torvalds/linux-2.6.git;a=blob_plain;f=drivers/bluetooth/ath3k.c;hb=HEAD") tree (using 2.6.38 headers) solves the issue for me.

A [patch]("http://git.kernel.org/?p=linux/kernel/git/torvalds/linux-2.6.git;a=commitdiff;h=2a7bccccdb9604a717c2128a931f022267d35629") added this device id a few weeks ago.

So that would mean that this bluetooth chip will be supported in next kernel (and therefore in Ubuntu 11.10).


PS:*still struggling with the infrared receiver. nuvoton-cir in 2.6.38 does not recognize this version of the chip, and although it is supposed to do so in Linux 3.0, I was not able to have my infrared working by using the same technique (building the 3.0 module on 2.6.38 headers). The modulse compiles and load fine, and dmesg even says my chip was detected, but then nothing works and modprobe freezes when trying to unload the module. If anybody has had more success than me, please PM me!

---

### Post by andlinux on 2011-06-21
> **Aldoo said:**
> If anybody has had more success than me, please PM me!

This is a forum, everybody has the right to know it.

---

### Post by misteraph on 2011-09-05
Hi !
Does someone tried with version 11.10 ?
Please can someone confirm that single channel mode is displayed during bios screen startup althouth the two ram slots are used ?

Thanks

---

### Post by unilogic on 2011-10-03
> **PaulCheap said:**
> HAs anyone been able to power up the system by using a remote control? I just can't get it to work.
 
I try to get the system to Suspend and/or Hibrnate mode, but it just doesn't work.. any hints are highly appreciated!
 
Thanks!
 
Kind regards
Paul
 
Did you finally managed to power up the S1 with a remote ? It does not work for me (bios option is ok in power management, and remote is a pronto philips emulating MCE)

---

### Post by unilogic on 2011-10-04
> **unilogic said:**
> Did you finally managed to power up the S1 with a remote ? It does not work for me (bios option is ok in power management, and remote is a pronto philips emulating MCE)
 
UPDATE: Finally it works, with the "power toggle" hex codes (but not with discrete on/off codes).

---

### Post by andlinux on 2011-10-04
What do you mean with that hex code ?

---

### Post by rileyp on 2012-03-20
I have one of these and I love it! 
Running natty mythbuntu/frontend
Audio never failed me
never used wifi  or btooth or nuvuton (I use mceusb as I need to blast to my receiver and projector)
Wakes from suspend via nuvuton

---

