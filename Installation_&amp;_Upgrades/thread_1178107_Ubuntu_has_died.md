---
title: "Ubuntu has died"
date: 2009-06-04
forum: Installation &amp; Upgrades
---

### Post by RogersBuck on 2009-06-04
Hi Folks,

I was trying to reconfigure my friends mini laptop, which has/had Ubuntu installed on it.

I don't no what I've done bit all I am getting now is :-

Intel UNDI PXE-2.1 (build 082)
Copyright (c) 1999 - 200 Intel Corporation for Realtek
RTL81016/810CE PCI-E Ethernet Contrller v1.08

PXE-E61 : Media test failure (080408) check cable
PXE-M0F : Exit PXE ROM
Operating system not found

What I have done so far (Besides pulling my hair out & scratching my head)

Disabled LAN in BIOS and disconnected & reconnected the battery. I'm using an external CD/DVD player (USB) connection, trying too re-install Ubuntu 8.04+ LTS DVD to no avail, just a black screen error message "No Operating system"

Any help would much appreciated

Cheers RogerBuck...

---

### Post by jerrrys on 2009-06-04
do you have an option in bios to boot from usb?

---

### Post by RogersBuck on 2009-06-05
Hi Jerrys,

Thanks for your reply.

I have just booted to GParted using USB. I am trying to reallocate (it's unallocated at the moment) my /dev/hda partition. But everything is greyed out, I can't do anything with GParted.

Any advice on this matter!!!

---

### Post by jerrrys on 2009-06-05
if you can boot from usb why not do a guided install. is there a second OS involved?

---

### Post by RogersBuck on 2009-06-05
Hi Jerrys,

Only one OS - How do you do a guided install? However my HDD doesn't seem to be formatted. When I ran GParted, it picked my HDD as unallocated. I'm stumped at the moment.

I've goggled "How to use GParted" but don't get any results with my problem.

---

### Post by RogersBuck on 2009-06-05
Re to my last post.

jerrys,
        I have no OS at all installed. I did have Ubuntu Hardy Heron, mucked about trying to install XP home. Now have nothing and can't seem to install anything.

I have a external CD/DVD player connected thought USB. However every time I try to load from it, I just get the flashing white dash line in the top right hand corner.

Any ideas on that one???

---

### Post by jerrrys on 2009-06-05
have you made it to a screen that gives the option to check cd? if so do that. also just to be sure, this is the live cd that your using.  and last, you can forget about gparted, its not necessary to do that on a hdd that has only one os on it. ubuntu cd will figure out the partitions for you...

[http://www.howtoforge.com/the-perfect-desktop-ubuntu-8.04-lts-hardy-heron](http://www.howtoforge.com/the-perfect-desktop-ubuntu-8.04-lts-hardy-heron)

---

### Post by RogersBuck on 2009-06-07
I have got nothing,just tried to boot from USB & external HDD & got nothing except error message 

"Operating system not found" 

However I can boot from USB into GParted. Can I use the terminal window to do anything from there

---

### Post by RogersBuck on 2009-06-09
Sorry jerrys for not getting back sooner. I have been trying to use that URL you suggested.

[COLOR="RoyalBlue"]http://www.howtoforge.com/the-perfec...ts-hardy-heron [/COLOR]

It will not open for me. Well it opens and then just goes blank, I can't read a thing.

Cheers RogersBuck

---

### Post by RogersBuck on 2009-06-10
Hi jerrys,

just a quick update, I got that website open. About installing Ubuntu "Hardy Heron".

However my problem is I can't seem to get any boot disks to work. I've tried Ubuntu instalation disk, you can hear it spinning around and the light flashing, but nothing boots up. Same when I tried to do the windows instalation.

Cheers Buck...

---

### Post by bugritall on 2009-06-10
I'm an ubie- newbie looking for help with an entirely different problem but I won't let that stop me suggesting something that you have probably already done anyway:

'Set Defaults' in BIOS.

---

### Post by RogersBuck on 2009-06-11
Thanks Bugritall,

I have reset Defaults in BIOS cheers anyhow.

Buck...

---

### Post by jerrrys on 2009-06-11
hi rogersbuck, sorry i did not get back sooner but out of the house.

anyhow, lets back up a minute. i have reread and i think you are telling me that your using both an external (usb) hdd and dvd. if this is the case, unplug hdd for now and just run ubuntu cd WITHOUT installing it. what we need to do is verify that you do have a good copy and your system will run on it. this will be slow, so be patient...

---

### Post by RogersBuck on 2009-06-13
Hi jerrys,

          The only external devices I'm using are USB & CDROM. My HDD is internal. I just don't know what it is jerrys, I've created bootable USB & CDROMs but nothing loads, just get a flashing dash line in the top left hand corner. Or it did read from a USB once &  told me I had no operating system.

confused Buck

---

