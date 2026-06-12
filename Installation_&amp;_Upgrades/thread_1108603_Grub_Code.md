---
title: "Grub Code"
date: 2009-03-27
forum: Installation &amp; Upgrades
---

### Post by SuperIntense on 2009-03-27
Can someone give me the grub code for this scenario and how to put it in. Two hard drives. One with Vista and one with Ubunto. I am taking out the Vista to install Ubunto so grub installs on it. I do not want to affect my Vista at all. whe Ubunto is ionstalled I will put Vista drive back in. I was tol that I need a code for Grub so Vista would think it was the first hard drive. I need the code and how to install it. I want to learn Linux but not mess with Vista at all especially change the boot on my vista.

---

### Post by pbpersson on 2009-03-28
Well.....you might want to read a few manuals on Grub.

There is an article I found on the web about this, it is here:

[http://www.pctipsbox.com/dual-boot-vista-and-linux/]("http://www.pctipsbox.com/dual-boot-vista-and-linux/")

A great many people have run into problems doing this, so proceed with caution and BACKUP YOUR DATA!!!

I have not read the article in great detail, but here is the plan:

Get your BIOS to boot from the Ubuntu drive.  Install Grub into the MBR of the Linux drive.  Insert the code into the /boot/grub/menu/lst file that is needed to boot into Vista.

The only part of that article I don't like.....if I were doing this....when I installed Grub on the MBR of the Linux drive, I would make sure the Vista drive is unplugged.  Also, all I use is SATA now so I would tell the BIOS which was the boot drive.

Let us know if you run into any problems.

---

### Post by tommcd on 2009-03-28
Here is the official Ubuntu documentation for dual booting with 2 hard drives with Ubuntu as the 1st drive and Windows as the 2nd.
[https://help.ubuntu.com/community/How_to_dual-boot_Ubuntu_and_XP_after_installing_them_separately_on_two_HDs](https://help.ubuntu.com/community/How_to_dual-boot_Ubuntu_and_XP_after_installing_them_separately_on_two_HDs)
It should work with Vista just as well.

---

