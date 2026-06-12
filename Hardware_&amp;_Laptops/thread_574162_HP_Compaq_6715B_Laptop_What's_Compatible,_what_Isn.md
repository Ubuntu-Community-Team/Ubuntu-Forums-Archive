---
title: "HP Compaq 6715B Laptop: What's Compatible, what Isn't?"
date: 2007-10-12
forum: Hardware &amp; Laptops
---

### Post by Xanderfoxx on 2007-10-12
I'm going to check the Hardware Compatibility Lists, but I'd like the help of thosw who already shopped:

Does this laptop support Ubuntu GNU/Linux?

If it's partial, what will I have to give up?

---
**HP Compaq 6715B Laptop:**

[COLOR="Red"]AMD Turion 64 X2 Mobile Technology (2.0 GHz, 2x 512 KB L2 cache)
AMD M690T Chipset[/COLOR]
1024 MB DDR2 SDRAM, 667 MHz, 1 DIMM
SATA 80 GB HDD @5400 rpm
DVD/CD-RW Combo (reads DVD, reads/writes CD)[COLOR="DarkSlateGray"]          -- [alex:] I don't know what make and model yet, but I'll look it up.[/COLOR]
15.4 inch diagonal WSXGA+WVA (1680 x 1050 and 16M colors) display
[COLOR="red"]ATI Radion X1250, up to 512 MB shared system memory[/COLOR]
[COLOR="red"]Integrated HiDef audio          [/COLOR][COLOR="DarkSlateGray"]-- [alex:] I don't know what chipset, probably integrated with AMD M690T[/COLOR][COLOR="red"]Wireless 802.11b/a/g[/COLOR][COLOR="darkslategray"]          -- [alex:] I don't know what chipset, probably integrated with AMD M690T, or Athros chipset[/COLOR]Bluetooth 2.0, HP Wireless Assistant
[COLOR="Red"]Broadcom NetLink Gigabit Ethernet PCI Controller (10/100/1000 NIC)[/COLOR]
Touchpad
TPM Embedded Security Chip          -- [alex:] I have no idea what that is. Kinda like LoJack for Laptops?
HP Fingerprint Sensor          -- [alex:] It would be really cool if that was supported, but I don't expect it.
---

Thank you for any saved time and help. I really appreciate it.

---

### Post by 4leite on 2007-10-16
I have Feisty running on my 6715b, but it wasn't easy. I am currently trying Gutsy - without much success so far  (I'll post again in few days).

Fingerprint reader does not work.

For Feisty:

By far the easiest way to install is buy plugging an external screen in and pressing the fn+f4 key at startup until the external screen is working and the laptop screen is disabled. This bypasses the problems with 'no screens found' that a lot of users have experienced with the ati x1200 video card. Once you have installed and rebooted, enable the restricted drivers and you will be able to use the laptop with out the screen.

If you are new to linux then I do not recommend this distibution with this laptop as it is a bit of mish to get going - having said that, if you wanna give it a go I''ll try and help best I can.

Wireless is working now with ndiswrapper + bcmw15.inf driver - I tried a heap of howto's but I can't remember which one worked, sorry.

Managed to get 3d effects with a lot of effort but then reverted so i could dual screen nicely.

No hibernation or suspend. (With either video / wireless driver combination)

For Gutsy:

As above, I highly recommend plugging an external monitor in and playing with the fn+f4 key as this will mean you can use the live cd. Enable restricted drivers as above and 3d should work.

I have not yet managed to get wireless working.

Yet to get system working well enough to test suspend/hibernate.

---

### Post by Xanderfoxx on 2007-10-16
Thanks. I'll need more info on what works, what doesn't,
but I appreciate your input.

At least I know it will boot, and will accept Ubuntu, and the tip about the external monitior was extremely helpful. Thanks, man.

I want to know if it is possible to get wireless working, or if I have to get a cardbus, if that is a possibility.

3D Would be absolutely awesome, but I won't get my hopes up. I refuse.

---

### Post by fitzybhoy on 2007-10-22
bump,

anybody know how to install linux on the 6715B??


i tried 7.10 (my first try) and couldnt get it going. i kept getting [OK] to all the parts then it started saying "microcode : file failed to load" then it does nothing ...

shame, i wanted to run this OS over vista...

---

### Post by Xanderfoxx on 2007-10-22
*Sigh*

Well, I was hoping that I could get Mr. Gibbon to settle in for the long haul, but I'll probably have better luck on my Frankenmachine I have at a friend's place. (My experimental machine.)

I really hope that Rosegarden will work on this machine. But that's for another thread.

Tough breaks, guy. I guess this laptop and Ubuntu were not made for each other. A marrage would only start drama, it would seem.

Well, see ya.
:(

---

### Post by fitzybhoy on 2007-10-24
> **maurin.alex@gmail.com said:**
> *Sigh*

Well, I was hoping that I could get Mr. Gibbon to settle in for the long haul, but I'll probably have better luck on my Frankenmachine I have at a friend's place. (My experimental machine.)

I really hope that Rosegarden will work on this machine. But that's for another thread.

Tough breaks, guy. I guess this laptop and Ubuntu were not made for each other. A marrage would only start drama, it would seem.

Well, see ya.
:(

from a seperate forum...

 Christian Reichlin  	
Jun 10, 2007 14:46:50 GMT    Unassigned 	
i installed ubuntu on a 6715b about one week ago. i had to use the "alternate desktop CD" with the text installer, because only the proprietary ati/amd graphics driver works with x (not even vesa or vga). i didn't use it a lot yet but network, mouspad and audio works (wireless adapter is recognized but i didn't test it). fan is mostly running but not overly loud. hibernating works too if i remember correctly.

---

### Post by Xanderfoxx on 2007-10-28
Awesome. That's great. I'll keep that in mind.

I have a success story.. I'll update this post, once I post the success story, with the link.

---

### Post by 4leite on 2007-10-29
update: got gutsy running ok, only to be foiled by a three foot drop and a bottle of red wine. At least now I can get a laptop without a pesky ATI card...

---

### Post by mike102282 on 2007-10-29
At least some good cam out of it then.

---

### Post by rsullivan on 2007-12-01
I had 2 problems with Gutsy on the HP6715b.
1. ATI video driver

2. problem with SATA hard-drive controller


For problem 1. I was able to use the tips provided elsewhere on this forum by david.wahlstedt (pasted at end of this post).  This let me use X with the live Cd.  

For 2. I was unable to persuade  the live cd or installer to recognise the controller so gutsy couldn' t see my hard-drive.  This was a knockout for me.  I eventually ended up instaling Gentoo (more exactly Sabayon which is a derivative of Gentoo).   Sabayon at least was able to load a driver for the ATI and used the correct resolution (even if it couldn't enable 3D out of the box).  It also found my hard drive but unfortunately the driver module treats the drive as if it were an external SCSI drive and therefore feels unable to hibernate or suspend since it thinks it wouldn't be able to re-activate such an external hard drive after suspend/hibernate.

Sorry I can't provide more detail but hope it helps anyway.

Ciao,
Richard

ATI recipe: 

sudo -s
killall gdm (kdm)
apt-get install xorg-driver-fglrx
depmod -a
aticonfig --initial
gdm (kdm) start

If ur got erro messa like there is no xorg.conf file or somethin like that

Type dpkg-reconfigure xserver-xorg, and when its ask ur card just use ati or radeon, when ur have done that xorg.conf file type aticonfig --initial and
gdm (kdm) start again...

---

### Post by hekto5 on 2007-12-22
Suspend/hibernate works for me. Just install the newest ATI drivers. 8.3 works fine.

---

### Post by Xanderfoxx on 2008-01-04
> **4leite said:**
> I have Feisty running on my 6715b, but it wasn't easy. I am currently trying Gutsy - without much success so far  (I'll post again in few days).

Fingerprint reader does not work.

For Feisty:

By far the easiest way to install is buy plugging an external screen in and pressing the fn+f4 key at startup until the external screen is working and the laptop screen is disabled. This bypasses the problems with 'no screens found' that a lot of users have experienced with the ati x1200 video card. Once you have installed and rebooted, enable the restricted drivers and you will be able to use the laptop with out the screen.

If you are new to linux then I do not recommend this distibution with this laptop as it is a bit of mish to get going - having said that, if you wanna give it a go I''ll try and help best I can.

Wireless is working now with ndiswrapper + bcmw15.inf driver - I tried a heap of howto's but I can't remember which one worked, sorry.

Managed to get 3d effects with a lot of effort but then reverted so i could dual screen nicely.

No hibernation or suspend. (With either video / wireless driver combination)

For Gutsy:

As above, I highly recommend plugging an external monitor in and playing with the fn+f4 key as this will mean you can use the live cd. Enable restricted drivers as above and 3d should work.

I have not yet managed to get wireless working.

Yet to get system working well enough to test suspend/hibernate.

Thank you!

---

### Post by Xanderfoxx on 2008-01-04
> **fitzybhoy said:**
> from a seperate forum...

 Christian Reichlin      
Jun 10, 2007 14:46:50 GMT    Unassigned     
i installed ubuntu on a 6715b about one week ago. ... hibernating works too if i remember correctly.

Thank you!

---

### Post by Xanderfoxx on 2008-01-04
> **rsullivan said:**
> I had 2 problems with Gutsy on the HP6715b.
1. ATI video driver

2. problem with SATA hard-drive controller


...

Sorry I can't provide more detail but hope it helps anyway.

Ciao,
Richard

ATI recipe: 

... .


Thank you!

---

### Post by Xanderfoxx on 2008-01-04
> **hekto5 said:**
> Suspend/hibernate works for me. Only thing I needed to do is to edit /etc/default/acpi-support and change MODULES="" to MODULES="ndiswrapper". This will unload ndiswrapper just before suspending/hibernating and load it on wakeup.

Thank you! :lolflag:

---

### Post by niclone on 2008-03-27
> **rsullivan said:**
> I had 2 problems with Gutsy on the HP6715b.
2. problem with SATA hard-drive controller


Hi,

The problem with SATA disk (extremly slow) seem to be resolved from kernel 2.6.25rc7. I've finally installed ubuntu 8.04 beta on this laptop and manually compiled this latest kernel. Everythink work fine (sata, suspend, sound, video (without opengl, I didn't tried fglrx driver), wifi, etc.)

hope this help...

---

