---
title: "Suspend to ram working."
date: 2005-12-20
forum: Hardware &amp; Laptops
---

### Post by strawman on 2005-12-20
hi there,
the suspend to ram never worked properly on my laptop (hp nc8000): it would work a few times - and this is from a clean install -  then it would suspend but not wake properly; very frustrating. 

I decided to re-install but this time instead of using wpa_supplicant for the internal wireless i just used wep 64 bit - nothing fancy - for the wireless hookup.  I removed the splash option from the kernel line in /boot/grub/menu.lst and uncommented "suspend to ram" in /etc/default/acpi-support; that's it and now suspend works on my laptop.  It has worked now four times in a row and i hope i'm not jinxing myself with this post;) 

I also used reiserfs for the file system instead of ext3 but i'm not sure if this would have a bearing on acpi/suspend.  The system seems to boot a little faster with reiserfs.

So, for others that have trouble with suspend maybe try using WEP and see if it helps:)

---

### Post by earobinson on 2005-12-21
thanks for the tip

---

### Post by neuweiler on 2006-02-17
It works !!! :KS :D :-D \\:D/ 

After spending days ans nights trying all the different hints and tips I found in the web (fglrx / radeon driver, splash screen, framebuffer off, different kernel/bootloader parameters, etc.) this one finally helped me. Thank you again strawman !!

Switching from WPA to WEP 64 bit encryption for the WLAN adapter really did the job! It's even possible in a already set-up and running system. I changed the config, restarted the nework and suspend-to-ram worked on my nc8000 (even without a reboot)

From a pm from strawman:
> My wpa set-up required a special script and i think that was preventing the resumption of video

So it's not Radeon messing up, it's not framebuffer, it's not fglrx - it's WLAN configuration !!

My current config: 
hw: HP Compaq nc8000
kernel: 2.6.13-15.8
gfx driver: fglrx 8.22.5-1 for xorg 6.8.0
distro: suse10 (sorry, I know wrong place for that but I'd just wanted to point out that it's not distro specific)
desktop: kde 3.4.2
bootconfig: normal
splashscreen: on
framebuffer: on

Cheer! Joy! Happyness! :D Now there's no more regret for my move from win xp to linux..

---

### Post by neuweiler on 2006-03-14
Erm.. small correction to the above:

Didn't work anymore after a reboot. :-k 
I got it working again when I did a suspend-to-disk first after a real shutdown/reboot. This is really strange behaviour. Got to investigate further.

Just that you don't get frustrated... [-( 

neuweiler

---

### Post by strawman on 2006-03-15
i have since updated to dapper flight 5 with fglrx-xorg-drivers and suspend works very well on my nc8000.  I'm also still using wep instead of wpa for wireless encryption.

---

### Post by neuweiler on 2006-03-16
Yup, in dapper flight 5 suspend-2-ram works perfect.

I tried and moved all scripts to a suse 10.1 installation because I suspected there was some magic done there before going to sleep. But to no use. Still just works after a suspend-2-disk. :cry: 

So I suspect it's either a kernel param that's different in ubuntu, additional software running or a different version of a package.

Will compare a suse and an ubuntu installation side by side tomorrow.

neuweiler

---

### Post by Tomas_IV on 2006-05-26
> So I suspect it's either a kernel param that's different in ubuntu, additional software running or a different version of a package.
Hey, so just in case it is the first possibility: Show us your current kernel parameters from grub.conf please!

---

