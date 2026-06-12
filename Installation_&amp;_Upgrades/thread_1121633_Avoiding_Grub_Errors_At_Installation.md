---
title: "Avoiding Grub Errors At Installation"
date: 2009-04-10
forum: Installation &amp; Upgrades
---

### Post by Jimmy9pints on 2009-04-10
Hi, I have had a problem several times (but not consistently) after installing Ubuntu. That is, that I get a Grub 17 error. The temporary bodge-fix was to leave the installation medium in the computer. 

I have installed Ubuntu on say...10 computers. I only had this problem with desktops - not laptops. 

So if the media used for installation was a CD leave a CD in the drive, or if installed from a USB, leave a USB plugged in. Weird I know. 

However, this didn't work with just any CD or USB, it had to have a boot loader present on the media, which would start to load, then if you cancelled it would then go on to load Ubuntu which is installed on the hard disk. I found a Windows CD did the job or a USB made with unetbootin - both have bootloaders on there. 

The problem must lie with something I am doing at installation or with something to do with the cable/BIOS configuration. 

I would like to avoid the problem when I reinstall my server tonight so please, if anyone has any ideas what I am doing to cause this, please give me a clue. 

I'd appreciate any answers asap because I plan to run the installation overnight tonight. 

Thanks!

---

### Post by Jimmy9pints on 2009-04-12
I still haven't sorted that problem out - I reinstalled my server in the hope of gaining a new, clean start. I hoped sorting out the grub error and a number of other problems.

My server has 3 disks, two for storage and one for the OS. During installation I noticed that all three had boot flags. I removed the boot flags from the two storage disks and only mounted the OS-containing disk. 

I thought, this way, Grub can't go wrong. Unfortunately it did. I got error 17 again. :(

I booted up a super-grub disk. Chose to automatically fix Linux/GNU. It returned a message saying that "SGD Succeeded". Then I rebooted, straight back into error 17! Ahhhhh!

So then, I tried to go back into Supergrub (which is on a unetbootin made USB), this time, it failed to load supergrub and loaded Ubuntu instead. 

So I am basically back to square one. As long as I have that USB present and I actually opt to load supergrub, it will then load Ubuntu.

If anyone has any ideas how to solve this that would be great - otherwise, I'll just continue to use this work around (which means I can't make my server headless).

Cheers,

James.

---

