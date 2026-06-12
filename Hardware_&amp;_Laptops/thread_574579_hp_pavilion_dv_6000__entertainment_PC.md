---
title: "hp pavilion dv 6000  entertainment PC"
date: 2007-10-13
forum: Hardware &amp; Laptops
---

### Post by perfecxion on 2007-10-13
hi i have looked all over and i still can't get my laptop to start ubuntu live cd. I have used these links:
[https://wiki.ubuntu.com/hp_dv6000_series_%28dv6116eu%29](https://wiki.ubuntu.com/hp_dv6000_series_%28dv6116eu%29)
[http://aldeby.wordpress.com/2007/09/11/howto-ubuntu-on-hp-dv65xx-series-laptop/](http://aldeby.wordpress.com/2007/09/11/howto-ubuntu-on-hp-dv65xx-series-laptop/)

none of these solutions seem to work. I have also tried to install debian and was able to. But to my surprise when i when i ran lspci everything was "unknown device" except for the amd athlonX2 processor. So i can't even get on the internet with it which was a real hit to my hope of getting it work at all. Are there any other ways to install ubuntu on it? do i have to download some other drivers to make it work? I have tried ubuntu 6.10 and i am about to try 7.04 to see if that works. O yeah i forgot i also tried to update the bios but none of those work either.

---

### Post by jpyanowski on 2007-10-13
Sorry you're having trouble. Hoa that Fiesty will work for you.

---

### Post by jonathanmotes on 2007-10-14
Look a at this if Feisty doesn't work: [http://ubuntuforums.org/showthread.php?t=512059]("http://ubuntuforums.org/showthread.php?t=512059")
I have tried Ubuntu Feisty on two different HP laptops and had to use the bootup parameters described in the post to get the live disc to work. (it will work fine with them though!)

---

### Post by aldeby on 2007-11-13
perfexion, 
my blog refers to Intel based HP Pavilion laptop.
Being yours an AMD Athlon based one I have no means to test if booting with Gutsy works. I'm sorry. 

You maybe should have a try with the Alternate CD, also it is suggested to insert into GRUB longest boot string (the one with kernel image, press '**e**' to edit it) arguments **'noapic irqpoll noirqdebug' **without quotes.

These should disable nForce based acpi and apic which are reported to cause troubles being bugous. If you manage to boot with this parameters you should consider adding them to /boot/grub/menu.lst

cheers

---

### Post by emmanuel-aclla on 2007-12-06
hi,
have you succeeded in installing gutsy on your dv 6000. I am stuck.

---

### Post by aldeby on 2007-12-06
I'm sorry for that, 
however I wonder how you could expect us to help you if you don't even say what your problems are!

---

### Post by Z_o-s-o on 2007-12-07
It seems kind of hit and miss with dv6000's to me.

I've got a Dv6215 with the following:

-Amd Turion 64 (single core)
-2 gigs of ram
-120 gig SATA drive
- Go6150 graphics

..the whole deal and I've never had trouble booting from the live cd's.

---

### Post by buccaneere on 2007-12-07
[http://ubuntuforums.org/showthread.php?t=431815](http://ubuntuforums.org/showthread.php?t=431815)

Might be some info there for ya'...

---

### Post by perfecxion on 2007-12-26
so sorry. I forgot about this post. I did get it to work. what i do is boot the CD in safe graphics mode. This will make the live cd boot with "vesa" modules. This will make the graphics look very bad but you can fix it later, u just want to get it installed 1st that's the most important part. To get your video to work properly just uses envy, you get it from: [http://albertomilone.com/nvidia_scripts1.html](http://albertomilone.com/nvidia_scripts1.html)

---

