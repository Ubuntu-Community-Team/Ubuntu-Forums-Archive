---
title: "IBM Thinkpad R52, Samsung P40 1600 or HP nc6120?"
date: 2005-10-19
forum: Hardware &amp; Laptops
---

### Post by timetunnel on 2005-10-19
Hi, 
I'm looking for a notebook and  have narrowed may search down to the following three, but I haven't found out much about how ubuntu runs on them (I already searched at  tuxmobil, linux-on-laptops and at the LaptopTestingTeam site of the ubuntu wiki):

IBM Thinkpad R52
Samsung P40 1600
HP nc6120 would be my first choice, but it doesn't have DVD-RAM, which makes it my last choice.

Did anyone tried Breezy final on one of these already?

Thanks
Jens

---

### Post by tist on 2005-10-20
I'm just running Breezy on a Thinkpad R52, and until now I'm very happy about it. Everything that I can check works out of the box, except for the suspend to RAM (to disk is no problem).

If I happen to find an old phone socket, I'll start trying out the modem.

So until now, it's a thumbs up.

---

### Post by timetunnel on 2005-10-20
Many thanks for your reply. Glad to hear that. Does it mean that all the interfaces like Wifi, Bluetooth, Firewire work? Fn-Keys as well? Did it all work out-of-the-box or did you have to tweak some stuff to make it work?

Jens

---

### Post by GrumpyBob on 2005-10-21
I've installed Breezy on an R52.
WiFi works fine,  Haven't tried bluetooth, Firewire or the modem.
It suspends fine, haven't tried hibernate yet (to be honest, I'm not sure of the difference between hibernate and suspend!).
So, no problems so far, though there is time for some to surface, I guess.
The blue-shift functions keys seem OK.
Just an out-of the-box install.  Interestingly a Hoary CD did not work on the R52 - as soon as the Linux kernel booted during install, it could no longer see the CD-ROM.  The Breezy install was a breeze...

Robert

---

### Post by Predius on 2005-10-21
[http://aaltonen.us/archive/2005/03/02/ubuntu-linux-on-the-ibm-thinkpad-t42/]("http://aaltonen.us/archive/2005/03/02/ubuntu-linux-on-the-ibm-thinkpad-t42/")

Guide for T42, worked on a R40, probably will work on an R52.

It's for Hoary, though.

---

### Post by timetunnel on 2005-10-21
Thanks, Robert. Sounds promising. 

Just today I had the chance to test the R52 (15'' display with 1400x1050) with Breezy Live-CD. It booted up to the the desktop with no problems. The resolution was correct (didn't check 3D-stuff), FN-keys for adjusting the brightness and for turning the keyboard light on worked. Enough to say "ready to work with basically". 

What didn't work was the internal sound, though the device seemed to be detected properly. Could have been broken speakers, a wrong configuration or a live-CD issue. 

Couldn't check any of its connections to the outer world, like USB, firewire, wifi and so on. 
 
Jens

---

### Post by tist on 2005-10-27
So, I've come across my first obstacle with the R52: I'm having a bitchy time getting IrDA to work. All modules are listed in my lsmod, but that's as far as I got until now. I will update as soon as I get it working.

Batist

---

### Post by emendelson on 2005-10-28
[QUOTE=tist]So, I've come across my first obstacle with the R52: I'm having a bitchy time getting IrDA to work. All modules are listed in my lsmod, but that's as far as I got until now. I will update as soon as I get it working.[/QUOTE]

Please let us know what you figure out. I'm still trying...

---

### Post by Snapper187 on 2005-11-20
I'm a HP nc6120 user and I'm quite happy about it.

The LaptopTestingTeam has published two entries on my machine, [here]("https://wiki.ubuntu.com/LaptopTestingTeam/HPNC6120") and [here]("https://wiki.ubuntu.com/HardwareSupportMachinesLaptopsHewlettPackard"). I've based my decision to purchase the nc6120 on those, and I can't say I regret it. Basically, all the stuff I use (ethernet, WLAN, sound, modem, touchpad, notebook keys) work -- except for hibernation which apparantly ceased working on Breezy. It doesn't affect Suspend-to-RAM, however, which is fine.

There's an [ongoing discussion]("http://ubuntuforums.org/showthread.php?t=35244") about the HP machine in the forums.

---

### Post by timetunnel on 2005-11-21
I decided to buy an IBM Thinkpad R52 with ATI graphic card. An important criterion for me was DVD-RAM support, but that's not available for HP notebook, alas. I'm quite satisfied with it so far. Most things worked out of the box. Some had to be configured manually, and a few don't work at all. I'll post more details as soon as I manage to write them down properly.

Jens

---

### Post by Paul Casey on 2005-11-21
thanks for posting at the hp nc6120 box.  that's pretty good looking

---

