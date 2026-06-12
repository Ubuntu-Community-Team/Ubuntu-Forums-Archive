---
title: "Missing top panel on live-cd + grub question"
date: 2008-12-12
forum: Installation &amp; Upgrades
---

### Post by JohnFante on 2008-12-12
I am trying to install 8.10 on my primary desktop machine but I have a strange graphical problem that makes my hesitate to install.

When I boot the live CD (using a USB stick that I have used to install my AcerAspireOne mininote) Ubuntu boots fine but the top panel (with applications, system, netvork etc.) is missing!

I can see the background and the two desktop icons and thats that! The systems looks like it works fine. I can start firefox (internet works fine) via a terminal and when I click install the install program starts fine.

My graphics card is an Nvidia 7800GS (ond a 24" IIlyama flatscreen). I think the problem is related to that but I do not know what boot options to use to correct the problem and how and where to use them.

Can I just safely install the system and will the problem correct itself when I install the Nvidia drivers or do I have to do anything else?

Finenally: Where does Ubuntu instll the bootloader? I have a Windows XP / opensuse setup now but would like to give Ubuntu a spin (I am not a big KDE4.1 fan). opensuse installs grub on my root partition (sda12) which is fine since I use OSL2000 ([http://www.osloader.com/](http://www.osloader.com/)) to chose between my OS's.

Thank you in advance.

---

### Post by caljohnsmith on 2008-12-12
I think it is likely that you will run into the same Video problems after installing Ubuntu as you have with the Live CD; you could try installing the Nvidia drivers while using the Live CD to see if you can fix the problem, or I would probably just install Ubuntu and see if you can correct the Video problem once you boot into your new Ubuntu install. 

And about Grub, since you want to use OSL2000 as your bootloader, you could have Ubuntu install Grub to the boot sector of its own partition so that you can keep OSL2000 in your MBR (Master Boot Record). To do that, just click the "advanced" button near the end of the installation process, and have Grub installed to /dev/sda10 or whichever is your Ubuntu partition (sda10 is just an example). Then Ubuntu shouldn't touch your OSL2000 boot loader. How about giving that a shot and let me know how it goes, or if you run into problems.

---

### Post by JohnFante on 2008-12-12
Thanks for the reply :-) Especially the grub part.

This maby a stupid question but how do I install the nvidia drivers with the live CD? I thought it did'nt write anything to the system/USB stick!

No matter what I think I will give the install a try tomorrow and see what happens. Who dares wins! ;-)

---

