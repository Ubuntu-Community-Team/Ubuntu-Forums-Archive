---
title: "No sound in precise after kernel upgrade"
date: 2012-06-14
forum: Hardware
---

### Post by ShadowMage on 2012-06-14
Hi all,

In Ubuntu 12.04, after performing an upgrade that included a kernel update, I no longer have any sound. The sound worked fine before the upgrade. Oddly enough, if I plug in headphones I do get sound through the headphones, but without them I am no longer able to get any sound from my laptop's internal speakers.

I'm not quite sure what additional info I should provide, so here's some info to start. Please let me know if there is anything else I should add.

Laptop: HP Pavilion DV6
OS: Ubuntu 12.04 (Precise Pangolin) 64-bit

$ lspci | grep Audio
00:1b.0 Audio device: Intel Corporation 82801I (ICH9 Family) HD Audio Controller (rev 03)

$ uname -r
3.2.0-25-generic

Many thanks in advance for any help!

---

### Post by grojo on 2012-06-15
Same problem for me
12.04, pavilion dv6
 lspci | grep -i audio 
00:1b.0 Audio device: Intel Corporation 5 Series/3400 Series Chipset High Definition Audio (rev 05)
01:00.1 Audio device: NVIDIA Corporation High Definition Audio Controller (rev a1)

---

### Post by guillaumec on 2012-06-16
Same problem for me.

$ uname -a
Linux Pavilion 3.2.0-25-generic #40-Ubuntu SMP Wed May 23 20:30:51 UTC 2012 x86_64 x86_64 x86_64 GNU/Linux

$ lspci | grep Audio
00:1b.0 Audio device: Intel Corporation 5 Series/3400 Series Chipset High Definition Audio (rev 05)
01:00.1 Audio device: NVIDIA Corporation High Definition Audio Controller (rev a1

---

### Post by JamezQ on 2012-06-16
Yup, count me in, same problem for me.


uname -a
Linux Ubuntu 3.2.0-25-generic #40-Ubuntu SMP Wed May 23 20:30:51 UTC 2012 x86_64 x86_64 x86_64 GNU/Linux


lspci |grep Audio
00:1b.0 Audio device: Intel Corporation 82801I (ICH9 Family) HD Audio Controller (rev 03)
01:00.1 Audio device: Advanced Micro Devices [AMD] nee ATI RV710/730 HDMI Audio [Radeon HD 4000 series]

---

### Post by andre01 on 2012-06-16
Same problem.

Change kernel to 3.2.0-24. Works for me.

---

### Post by fendervr on 2012-06-16
Same problem for me. This morning I upgrade from 3.2.0-25-generic-pae  to 3.2.0-26 generic-pae, but nothing changed. Linux kernel 3.2.0-24-generic-pae works fine.

Is it not possible to see the difference between two kernel in any way?

Thanks

---

### Post by paspartu on 2012-06-16
Laptop: HP Pavilion DV6
OS: Ubuntu 12.04 (Precise Pangolin) 64-bit

the same problem on 3.2.0-25 kernel
3.2.0-24 works fine

---

### Post by Squonk07 on 2012-06-17
Yep, same here. Ubuntu 12.04 (64-bit) and HP Pavilion DV6. The 3.2.0-24 kernel works fine. Is there a bug filed against this somewhere?

---

### Post by robbied on 2012-06-17
**DV6 (1375DX) with 3.2.0-25 had two problems. ** 
I dual boot win7 so I know it's all software, windows works great.

1.  No sound via laptop speakers but front jacks work as usual.  I tried everything to fix, kernel downgrade is the only solution I found.

2.  After resuming from standby the unit powers on.  You see the background for a instant then ALL power cuts out.  The only way to get the unit to power up is to unplug and remove the battery.  After this it will work fine until it has to resume again.


Wow developers, in six years nothing like this has happened.  Not one major problem but two totally unrelated issues with one update.  I have been using Windows again for the last few days.....

---

### Post by ShadowMage on 2012-06-17
Hey guys, I found a bug report on launchpad describing the sound issue we are all experiencing:
 [https://bugs.launchpad.net/ubuntu/+source/linux/+bug/1013183](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/1013183)

---

### Post by mattgeb84 on 2012-06-17
same problem here except i have no sound at all through the headphones or the speakers

---

### Post by mattgeb84 on 2012-06-19
does any body have a solution to this
its really hard to use ubuntu as my primary pc with idiotic problems such as this im really annoyed with the ubuntu developers first unity and now this

---

### Post by jallejo on 2012-06-19
Hi!! you should try this [https://bbs.archlinux.org/viewtopic.php?id=143572](https://bbs.archlinux.org/viewtopic.php?id=143572)

it works on my laptop. bye

---

### Post by mattgeb84 on 2012-06-19
im having trouble figuring out exactly what this guy did, could you possibly explain it to me ?

---

### Post by mattgeb84 on 2012-06-19
solved solved solved solved solved yyyeeeeeaaaaahhhh and the solve is easy !@!!
first let me say i tried typing alsamixer into the terminal and unmuting the speaker and headphones but this did not work

BUT !!! this did work 
go to the ubuntu software center download and install gnome alsa mixer then just unmute your speaks or headphones YYYEEEAAAAHHHHH!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!

I HAVE SOUND HALI FREAKEN LU YA

---

### Post by jallejo on 2012-06-19
> **mattgeb84 said:**
> im having trouble figuring out exactly what this guy did, could you possibly explain it to me ?

Open a terminal and put the next line to open alsa-base.conf

```
sudo gedit /etc/modprobe.d/alsa-base.conf
```and add the following lines at the end:

options snd-hda-intel model=***dell-m4-1***

then reboot.

That worked for me. Hp pavilion dv6. bye

---

### Post by AdministratorX on 2012-06-20
> **ShadowMage said:**
> Hi all,

In Ubuntu 12.04, after performing an upgrade that included a kernel update, I no longer have any sound. The sound worked fine before the upgrade. Oddly enough, if I plug in headphones I do get sound through the headphones, but without them I am no longer able to get any sound from my laptop's internal speakers.

I'm not quite sure what additional info I should provide, so here's some info to start. Please let me know if there is anything else I should add.

Laptop: HP Pavilion DV6
OS: Ubuntu 12.04 (Precise Pangolin) 64-bit

$ lspci | grep Audio
00:1b.0 Audio device: Intel Corporation 82801I (ICH9 Family) HD Audio Controller (rev 03)

$ uname -r
3.2.0-25-generic

Many thanks in advance for any help!

**I found that updating my kernel to 3.3.4 solved this problem for me. My system is 64bit (HP DV7-2180us) and these were the directions.**

```

cd /tmp && wget -O linux-headers-3.3.4_all.deb http://goo.gl/TchWu


sudo dpkg -i linux-headers-3.3.4_all.deb


cd /tmp && wget -O linux-headers-3.3.4-generic_amd64.deb http://goo.gl/qJcW4


sudo dpkg -i linux-headers-3.3.4-generic_amd64.deb


cd /tmp && wget -O linux-image-3.3.4-generic_amd64.deb http://goo.gl/arQWv


sudo dpkg -i linux-image-3.3.4-generic_amd64.deb

```

[http://www.upubuntu.com/2012/05/how-to-install-linux-kernel-334-under.html](http://www.upubuntu.com/2012/05/how-to-install-linux-kernel-334-under.html)

---

### Post by minimalism on 2012-06-23
> **jallejo said:**
> Open a terminal and put the next line to open alsa-base.conf

```
sudo gedit /etc/modprobe.d/alsa-base.conf
```and add the following lines at the end:

options snd-hda-intel model=***dell-m4-1***

then reboot.

That worked for me. Hp pavilion dv6. bye

This also worked for me! Thnx

---

### Post by Heeney.CS on 2012-06-25
This alsa( pun intended ) worked 4 me :)

Many thanks!!!

---

### Post by cccanovas73 on 2012-06-30
> **jallejo said:**
> Open a terminal and put the next line to open alsa-base.conf

```
sudo gedit /etc/modprobe.d/alsa-base.conf
```and add the following lines at the end:

options snd-hda-intel model=***dell-m4-1***

then reboot.

That worked for me. Hp pavilion dv6. bye




This also worked for me!!! Thanks! HP Pavilion dv6 1100es

---

### Post by jansteen on 2012-06-30
Adding the suggested module config worked for me too (Dell Studio).

But I see no reason to be happy about it. A simple upgrade of a stable Ubuntu version turns the sound off. This suggests it might be better to not upgrade to the latest stable release but instead take a one-year old one to ensure everything remains working in your working environment after your weekly package updates.

What's Ubuntu's opinion about this? Was this a one-time issue or is current hardware simply too complicated to ensure upgrades are working everywhere, anytime?

---

### Post by Lestazz on 2012-07-03
Module config worked for me too!!
HP DV6
Thanks guys!!

---

### Post by ShadowMage on 2012-07-27
Hi guys,

This issue has been fixed in the 3.2.0-27 kernel as mentioned in the [bug report]("https://bugs.launchpad.net/ubuntu/+source/linux/+bug/1013183"). Marking thread as solved.

Thank you developers and community! =D

---

### Post by davea88 on 2012-08-06
Linux q2 3.2.0-27-generic-pae #43-Ubuntu SMP Fri Jul 6 15:06:05 UTC 2012 i686 i686 i386 GNU/Linux

and I have no sound out at all. Desktop, not laptop.  Precise 12.04.

The sound settings panel cannot find any hardware to turn on.

It all worked fine  earlier (in 12.04).

---

### Post by rickm1945 on 2012-08-16
Module confg worked for me also.

---

### Post by davea88 on 2012-08-24
Never mind about my report. For some unknown(!) reason I installed
oss4-base on 12.04 [on] July 17, and that package by default
has a /etc/modprobe.d/*noALSA   file that prevents most
sound modules from loading at boot.  Uninstalled oss4-base
and sound works fine.  Crazy package (IMO).

---

### Post by hawaiiman on 2012-09-30
Not so. Sound worked fine on 12.04 32 bit (server), but now, with 64bit the speakers don't show up on the sound page. I wouldn't say this was near fixed. BTW I tried upgrading kernel to 3.2.0-31 and same same. Discouraging.

---

### Post by bro brian on 2013-04-13
> **mattgeb84 said:**
> solved solved solved solved solved yyyeeeeeaaaaahhhh and the solve is easy !@!!
first let me say i tried typing alsamixer into the terminal and unmuting the speaker and headphones but this did not work
BUT !!! this did work 
go to the ubuntu software center download and install gnome alsa mixer then just unmute your speaks or headphones YYYEEEAAAAHHHHH!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!
I HAVE SOUND HALI FREAKEN LU YA

This worked for me as well. Thanks for posting. :cool:

---

