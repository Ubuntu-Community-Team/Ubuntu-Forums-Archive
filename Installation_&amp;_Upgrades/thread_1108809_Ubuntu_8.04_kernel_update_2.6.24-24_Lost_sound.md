---
title: "Ubuntu 8.04 kernel update 2.6.24-24: Lost sound"
date: 2009-03-28
forum: Installation &amp; Upgrades
---

### Post by imbuto on 2009-03-28
Hi,

Tired of having the update manager saying me that very important updates were available I updated to kernel 2.6.24-24 (I had 2.6.24-22)... aware of the fact that this would have given me a terrible headache.
After spending more than one hour to get back my nvidia, I am now stuck on the soundcard. I'm browsing forums but I can't find a solution.

When I try to activate the speakers a windows pops up and says that either I don't have any soundcard or the gstreamer plugins are the wrong ones.

Does anybody had a similar issue and could help me in some way?

I've got this soundcard:

id:	
multimedia
description: 	Audio device
product: 	82801H (ICH8 Family) HD Audio Controller
vendor: 	Intel Corporation
physical id: 	
1b
bus info: 	
pci@0000:00:1b.0
version: 	03
width: 	64 bits
clock: 	33MHz
capabilities: 	pm msi pciexpress bus_master cap_list
configuration:	
driver	=	HDA Intel
latency	=	0
module	=	snd_hda_intel

As an extreme solution I am thinking of throwing the laptop out of the window. I guess I will hear something when it crashes.

---

### Post by Rayaz on 2009-03-28
Sorry don't have a solution to your problem but do have one for you frustration, just boot the older working kernel! You won't be prompted for the updates as you've done them and your sound will work. At least better than throwin' it out the window ;-)

---

### Post by lunus on 2009-04-04
I have same problem. Kernel 2.6.24-24 broke sound.

I followed this advice:
[http://linux.slashdot.org/comments.pl?sid=1185443&cid=27430009](http://linux.slashdot.org/comments.pl?sid=1185443&cid=27430009)

Now I am just waiting to hear from Songeyong Jooeypop! Happiness first!

---

### Post by djdjules on 2009-05-04
I just updated and had some crazy issues

After rebooting:

Gnome panels didnt have my applets anymore, they were gone
I tried to run gnome-do and nothing happened it didnt come up
I tried to open de sessions control panel and it didnt come up

I tried to open firefox to search for help and my profiles didnt show up in the profilemanager

at this point i started to worry.
I rebooted the system and came back to the same result

I then rebooted to the older kernel 2.6.24-23
Gnome panel was still crazy and my session was incomplete

I looked at the apt logs to see what it did during the update and everything looked normal.
I fired up synaptic and reinstalled 2.6.24-24
then proceeded to reboot and when it tried to boot to 2.6.24-24 it just stuck there saying that it couldnt find the device at /dev/disk/by-uuid/aoisoaiscnoascnoanco or something like that

wow, now I was really really worried

I rebooted to 2.6.24-23 and I got back into my session, this time programs are running, and the only weird thing is that my places menu and other customized options are back to defaults...

I was able to recover my firefox profiles since the files were still there. I just had to manually edit the profiles.ini file and read the desired profiles.

Im really surprised with the outcome of this latest kernel update
Maybe canonical is paying too much attention to Jaunty and forgot about Hardy...

Disappointing

---

### Post by akimo on 2009-05-10
I have nearly he same behaviour. Booting with kernel <2.6.24-24 - everything is fine.

Since the update to Kernel 2.6.24-24 the sound is only availlable over the OSS Mixer. Alsa doesn't support the hda-intel hardware of my asus notebook correctly, so i had allways to recompile my alsa drivers on my own when the kernel was updated. Furthermore, i had to set some special options in a config file "/etc/modprobe.d/alsa-base". 

Up to  Kernel 2.6.24-24 i had two mixer-devices:
1. HDA Intel (Alsa Mixer)
2. Realtec ALC660 (OSS Mixer)

Now i've got only the OSS Mixer, which doesn't support volume control - well, unusable. I've tried some older versions of ALSA, with no positive result.

Some Hardware Infos: >hwinfo --sound

> 
27: PCI 1b.0: 0403 Audio device
  [Created at pci.296]
  UDI: /org/freedesktop/Hal/devices/pci_8086_27d8
  Unique ID: u1Nb.WxIEzXSilF0
  SysFS ID: /devices/pci0000:00/0000:00:1b.0
  SysFS BusID: 0000:00:1b.0
  Hardware Class: sound
  Model: "ASUSTeK 82801G (ICH7 Family) High Definition Audio Controller"
  Vendor: pci 0x8086 "Intel Corporation"
  Device: pci 0x27d8 "82801G (ICH7 Family) High Definition Audio Controller"
  SubVendor: pci 0x1043 "ASUSTeK Computer Inc."
  SubDevice: pci 0x1338
  Revision: 0x02
  Driver: "HDA Intel"
  Driver Modules: "snd_hda_intel"
  Memory Range: 0xfebfc000-0xfebfffff (rw,non-prefetchable)
  IRQ: 16 (107836 events)
  Module Alias: "pci:v00008086d000027D8sv00001043sd00001338bc04sc03i00"
  Driver Info #0:
    Driver Status: snd_hda_intel is active
    Driver Activation Cmd: "modprobe snd_hda_intel"
  Config Status: cfg=new, avail=yes, need=no, active=unknown


This output is in all Kernel versions the same "Driver Status: snd_hda_intel is active" - but no Alsa Mixer is available.

Any ideas?

Thanks, akimo

---

### Post by ozzman2 on 2009-09-16
I ran into the same problem 2 days ago.  I was messing around trying to get Virtual Box running (I think I installed kernals I shouldn't have - I dunno - I'm a Linux noob).  I ended up with no sound and low resolution video (Ubuntu 8.04).

I followed this article here;
[http://tombuntu.com/index.php/2007/10/17/remove-ubuntu-kernels-you-dont-need/](http://tombuntu.com/index.php/2007/10/17/remove-ubuntu-kernels-you-dont-need/)

Searched for **linux-image-2** in **Synaptic** and removed **linux-image-2.6.24-24-generic** (as well as server, rt and openvz).  My machine boots into the right kernal (2.6.24-23) on it's own, and life is good again.

Just wondering, does anybody know when 2.6.24-24 came out?  Is this just a coincidence that my computer went bad when I was messing around with it?  Or was this thing just released on Sept 14, '09?  Are there any adverse effects to not using the latest kernel?  Thanks.  :)

---

