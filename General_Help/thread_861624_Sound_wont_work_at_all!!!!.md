---
title: "Sound wont work at all!!!!"
date: 2008-07-16
forum: General Help
---

### Post by !@!@! on 2008-07-16
I followed a tutorial somewhere, trying to get my mic to work.
what iv done:
-opened volume control (set to alsa) and ticked every box i could
-modified /etc/esound/esd.conf

I'm trying to get the esd.conf back to normal (need someones) and i dont know what to tick and what not to on switches!
i have no sound right now!
please help!
:(:(:(:(
edit:
sudo /etc/init.d/alsa-utils reset
worked like a charm!

---

### Post by Nexusx6 on 2008-07-16
Honestly, I can't imagine why you'd have to mess with esd to get your mic working. 

First off, lets try to get your sound back. Got to [this link]("http://ubuntuforums.org/showthread.php?t=776739&highlight=perfect+pulseaudio") to make sure you have Pulseaudio configured correctly. Restart your computer and then test sound.

For mic: Often the Gnome sound mixer will hid options it thinks are irrelevant, like "Line In" or "Mic boost". Go into your sound mixer (usually just double click on the speaker icon on one of your panels) and then try to find a menu option that says "preferences" something like that. What you should find is a window full of check boxes - check all of them and press okay. I would try to be more descriptive, but I run Kubuntu.. so I don't know what the window is called. 

From here, getting mic to work is just a matter of un-muting everything and raising the bars to the maximum (Do not do that for Mic Boost.. its a HUGE boost, just raise it a little until you can hear sound). Under "switches" make sure all input is "front mic" or just "mic". That *should* do the trick.

---

### Post by opobo on 2009-11-13
Dear All,
I am using ubuntu 9.04 version on a ThinkCentre lenovo desktop computer.
Ever since i installed ubuntu, i have never experienced sound when playing my music or logging in.

i downloaded and installed hwinfo to find out my system info so u guy scan help me.

My sound system according to the hwinfo --sound is:

dos@dos-desktop:~$ sudo su
root@dos-desktop:/home/dos# hwinfo --sound
21: PCI 1b.0: 0403 Audio device                                 
  [Created at pci.314]
  UDI: /org/freedesktop/Hal/devices/pci_8086_27d8
  Unique ID: u1Nb.d3natzzc2SD
  SysFS ID: /devices/pci0000:00/0000:00:1b.0
  SysFS BusID: 0000:00:1b.0
  Hardware Class: sound
  Model: "Intel 82801G (ICH7 Family) High Definition Audio Controller"
  Vendor: pci 0x8086 "Intel Corporation"
  Device: pci 0x27d8 "82801G (ICH7 Family) High Definition Audio Controller"
  SubVendor: pci 0x17aa "Lenovo"
  SubDevice: pci 0x1015 
  Revision: 0x01
  Driver: "HDA Intel"
  Driver Modules: "snd_hda_intel"
  Memory Range: 0xd0200000-0xd0203fff (rw,non-prefetchable)
  IRQ: 22 (4891 events)
  Module Alias: "pci:v00008086d000027D8sv000017AAsd00001015bc04sc03i00"
  Driver Info #0:
    Driver Status: snd_hda_intel is active
    Driver Activation Cmd: "modprobe snd_hda_intel"
  Config Status: cfg=new, avail=yes, need=no, active=unknown

Please help, am in desperate need. :(

---

### Post by ScribeAmos on 2009-11-13
A lot of the mic issues are related to not being able to adjust the mic volume through the gui.  if you run command alsamixer in the terminal you should be able to turn them up.  If so, try that and let us know the outcome.

esd.conf:


[esd]
# autospawning is not recommended, since it can't really be done
# right.  If you want your login session to be using a sound daemon,
# you should start it from the session controller, not some random
# app inside.
auto_spawn=0
spawn_options=-terminate -nobeeps -as 2
spawn_wait_ms=100
# default options are used in spawned and non-spawned mode
default_options=

---

### Post by klemes on 2009-11-13
> **opobo said:**
> Dear All,
I am using ubuntu 9.04 version on a ThinkCentre lenovo desktop computer.
Ever since i installed ubuntu, i have never experienced sound when playing my music or logging in.

i downloaded and installed hwinfo to find out my system info so u guy scan help me.

My sound system according to the hwinfo --sound is:

dos@dos-desktop:~$ sudo su
root@dos-desktop:/home/dos# hwinfo --sound
21: PCI 1b.0: 0403 Audio device                                 
  [Created at pci.314]
  UDI: /org/freedesktop/Hal/devices/pci_8086_27d8
  Unique ID: u1Nb.d3natzzc2SD
  SysFS ID: /devices/pci0000:00/0000:00:1b.0
  SysFS BusID: 0000:00:1b.0
  Hardware Class: sound
  Model: "Intel 82801G (ICH7 Family) High Definition Audio Controller"
  Vendor: pci 0x8086 "Intel Corporation"
  Device: pci 0x27d8 "82801G (ICH7 Family) High Definition Audio Controller"
  SubVendor: pci 0x17aa "Lenovo"
  SubDevice: pci 0x1015 
  Revision: 0x01
  Driver: "HDA Intel"
  Driver Modules: "snd_hda_intel"
  Memory Range: 0xd0200000-0xd0203fff (rw,non-prefetchable)
  IRQ: 22 (4891 events)
  Module Alias: "pci:v00008086d000027D8sv000017AAsd00001015bc04sc03i00"
  Driver Info #0:
    Driver Status: snd_hda_intel is active
    Driver Activation Cmd: "modprobe snd_hda_intel"
  Config Status: cfg=new, avail=yes, need=no, active=unknown

Please help, am in desperate need. :(



First of all try the command :

```
sudo modprobe snd_hda_intel
```

and then :

```
sudo alsa force-reload
```

If this doesnt work edit your /etc/modprobe.d/alsa-base.conf
and add in the last line :

```
options snd-hda-intel model=auto
```

save and then give in the terminal sudo alsa force-reload.
This will most propably work.It worked for me with the same soundcard.

---

### Post by opobo on 2009-11-17
> **klemes said:**
> First of all try the command :

```
sudo modprobe snd_hda_intel
```and then :

```
sudo alsa force-reload
```If this doesnt work edit your /etc/modprobe.d/alsa-base.conf
and add in the last line :

```
options snd-hda-intel model=auto
```save and then give in the terminal sudo alsa force-reload.
This will most propably work.It worked for me with the same soundcard.


Klemes,
I tried the command you gave but it didn't work. I also failed to edit the /etc/modprobe.d/alsa-base.conf

Please help me and give a step by step guide to editing this.
I am still new to Ubuntu and i really need some advice.

Thanks in advance

---

