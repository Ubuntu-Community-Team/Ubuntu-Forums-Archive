---
title: "install on 2nd drive"
date: 2005-12-11
forum: Installation &amp; Upgrades
---

### Post by mugs on 2005-12-11
Hi, first post!  I have 1 drive running Fedora and I have another hard drive in my system that I want to install Ubuntu on.  I have the first drive set up as the boot drive and grub resides on it.  I would like to keep it the way it is, install Ubuntu on the 2nd drive and then manually modify grub for the Ubuntu drive which I eventually will make the default. 

Do I have any options during installation when it comes to installing grub?  I would think the best thing would be to not install it at all.  Is that an option?  If not, what is the best way to go about this?

Thanks!

---

### Post by infoseeker on 2005-12-11
I installed Linux on a second drive by selecting it as the boot drive (in the pc's CMOS setup) so I could boot from either drive as I wished.  Only problem was having to do the changes in CMOS each time.

---

### Post by taurus on 2005-12-11
Yes, you can skip GRUB when you get to that stage.  When Ubuntu asks you to reboot, of course your machine will boot into Fedora Core so you need to modify your /boot/grub/grub.conf to include an entry for Ubuntu.  Then, reboot your machine, pick Ubuntu from the menu, and continue installing Ubuntu.  :cool:

---

### Post by mugs on 2005-12-11
Thanks Taurus, am I right to assume that I will only get the choice of installing Grub or not if I install in expert mode?

Also, if I go ahead and install grub on the 2nd drive, I guess it wont matter if I keep booting from the first drive?

Thanks!

---

### Post by taurus on 2005-12-11
It doesn't matter if you hit enter or pick an expert mode.  When you get to the GRUB stage, it will ask you where you want to install it so in your case, bail out by telling it to skip that step.  However, you can install GRUB from Ubuntu (with 2nd HD) and it should be able to boot whatever you want.  Just make sure you install it on MBR and everything should be fine.

---

### Post by mugs on 2005-12-11
Thanks Taurus, am I right to assume that I will only get the choice of installing Grub or not if I install in expert mode?

Also, if I go ahead and install grub on the 2nd drive, I guess it wont matter if I keep booting from the first drive?

Thanks!

---

### Post by taurus on 2005-12-11
You must install GRUB on MBR of you want to boot other OSes and that is the easiest way to handle mutlti-booting...  Just follow the instructions on the screen and you should be fine.

---

### Post by mugs on 2005-12-12
Well, having mixed success.  I installed it on 2 of my other machines, NOT with expert install.  Those boxes only have 1 drive.  It went very smooth.

So, I tried it on the machine I was asking about with the 2 drives.  I did an expert install and got up to Installing Grub.  I hit enter becuase I thought that it would then give me the choice to install it or not or where to install it.  Well, right away it seemed like it was installing it, I panicked and escaped out.  When I went to boot Fedora on hda, it gets stuck on "starting system logger".  Because I didnt install grub from ubuntu, I had no option to boot to it and finish the installation (I wasnt entirely sure what to add to grub for it).  So, I decided to try again, this time  I installed grub and it kept my old items (fedora).  But, when I reboot and take out the CD, it hangs at preparing for installation at 0%.  I let it sit and sit and it never moves.

I was wondering it it could have something to do with the partitioning scheme or any other options in the expert install.  I let it make the partitions for me, for a multi user system, so it created 5 or 6 partitions.  I did also pick a few extra options during the install, including letting it pick the mirror.  

If any of those are the problem or if anyone has any other ideas, please let me know.

Thanks!

---

