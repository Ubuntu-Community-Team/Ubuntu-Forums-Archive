---
title: "Intel HD Graphics Help"
date: 2010-09-09
forum: Hardware
---

### Post by MadhavS on 2010-09-09
I recently bought a [Sager NP5125 Laptop]("http://www.xoticpc.com/sager-np5125-built-clevo-b5100m-p-2840.html") which has an Intel i5-450m CPU and a Nvidia GT330m gpu. I am trying to dual boot Windows with Ubuntu 10.04. However, Ubuntu, by default, is using my Nvidia gpu. I only want to use the Intel HD Graphics in Ubuntu (not doing anything graphics intensive, want better battery life), but I can't figure out how to force the Intel graphics.

I have tried uninstalling every nvidia driver (I believe the command I used was sudo apt-get --purge remove nvidia-*) and the nouveau driver (sudo apt-get --purge remove xserver-xorg-video-nouveau), but for some reason, Ubuntu continues to use the Nvidia card...

Can someone please help me make it so that Ubuntu uses Intel HD Graphics? Thanks in advance for any help.

---

### Post by Fafler on 2010-09-09
Theres a long thread in here about switchable graphics. You should look into that.

---

### Post by MadhavS on 2010-09-09
Can you direct me to some of these threads that might help me? I looked through several I found, but many of them pertain to ATI cards...the few solutions I tried gave me no results (no change, still uses Nvidia Card...)

---

### Post by MadhavS on 2010-09-09
I'm trying to disable any driver it would use in order to use the Nvidia card, in the hope that it would turn to the Intel chip...

I tried these intructions:

> 2) Open module blacklist as admin:

sudo gedit /etc/modprobe.d/blacklist.conf
3) Add these lines and save: 

blacklist vga16fb
blacklist nouveau
blacklist rivafb
blacklist nvidiafb
blacklist rivatv
4) Uninstall any previously installed Nvidia drivers: 

sudo apt-get --purge remove nvidia-*
5) Reboot your computer

However, after I reboot, the card still powers on...I checked my graphics drivers using: ```
sudo lshw -C video
``` It says that it is still using the Nouveau driver in order to run the card, even though it's blacklisted...advice? I've been looking all over ubuntuforums, and documentations, and I feel like I have nowhere to turn...

---

### Post by MadhavS on 2010-09-09
Got it, if I disable Optimus in BIOS, Ubuntu only sees the integrated chip.

---

### Post by shteren on 2010-09-17
there is another solution:

[FONT=monospace]sudo gedit /etc/modprobe.d/blacklist.conf[/FONT]

 [FONT=monospace]Add these lines and save:[/FONT]   [FONT=monospace]blacklist vga16fb

blacklist nouveau
blacklist rivafb
blacklist nvidiafb
blacklist rivatv

this negates all nvidia drivers, no use for them now since it won't let you manually install the 256 driver (mybe in the future)

works perfectly for me, i have the np5125 aswell.
[/FONT]

---

### Post by glomerulus on 2011-05-17
hello **shteren**,

is there anything specific you did after adding those blacklist lines to **blacklist.conf** ?

i cannot use** MadhavS'** solution as my bios does not have option to disable Optimus (i have a Dell XPS 15-L502X)

---

