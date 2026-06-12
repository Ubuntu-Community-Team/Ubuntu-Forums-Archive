---
title: "About to install Ubuntu 9.04"
date: 2009-09-27
forum: Installation &amp; Upgrades
---

### Post by Hiromi on 2009-09-27
Hello! As the title says, I am just about to install Ubuntu 9.04, and I would just like to say thanks to everyone whom has worked on Ubuntu for making such a great OS.

I am, however, new to the world of linux and ubuntu, and had a few questions before I made the switch from windows. 

I have to format my hard drive because my windows partition is corrupted.  Which is fine with me, because I have all my important files and whatnot backed up on flash drives and heck, now I have a reason to play with ubuntu. :P

Anywho, the only thing that is holding me back is because I'm not 100% sure everything will work right once I do switch. More specifically, my graphics card and my wireless card. 

My Wireless card is a D-link DWL-520, and worked alright since I've started using XUbuntu on a live cd, but again, I will have to format my hard drive which will delete the drives that I currently have, and the website for the card only provides drivers that supports windows. Is there any specific programs or drivers that I could/should get so that the wireless will work when I do put ubuntu on my computer? 

And about the graphics card. Its an ATI HIS radeon 9250, which I haven't ever used. I have the installation disk and everything, and wanted to know if it would work by just installing them strieght off the disk, or if I need different drivers or anything for ubuntu.

Yeah ^^;; I'm sorry that I'm extremely noobish in ubuntu. But thank you to whomever reads this and such, and I hope to be...ubuntuing? soon!

(>.<; And hopefully I posted this in the right board, if its not, I'm very sorry and I'll delete this and post it on the correct board ><; )

---

### Post by kranny on 2009-09-27
Welcome to the world of Ubuntu...Dont worry your card works in ubuntu

[https://help.ubuntu.com/community/Ha...workCardsDlink](https://help.ubuntu.com/community/Ha...workCardsDlink)
and it mmust be using the acx111 driver..

Please let us know if you face any problem post installation

---

### Post by wilee-nilee on 2009-09-27
When you run the live cd the computer is only reading the cd not the drivers installed in the windows setup. You can get a copy of whatever windows system is, legally from Microsoft for about 30$ if you have the sticker on the computer of the original OCA # and the key, if you would like to get that back for kicks and dual boot. There is also a free key reader that will tell you your windows key in about 500 milliseconds. 

Otherwise if your computer is running fine with the xubuntu live cd then hit install and it will repartition and install for you all at once, good luck and keep posting for help if you need it.

---

### Post by automaton26 on 2009-09-27
You've done the right thing in trying the LiveCD first, to test your network connection. But the graphics drivers won't be on the driver disk - you'll have to do some research on your specific card and the best way to install them. This is usually done either through the Hardware drivers application, or manually in a Terminal window.

However, if you're new to linux/ubuntu (and this is your only PC and you have enough disk space) then I would consider dual-booting. This means leaving your Windows installation alone, and just installing ubuntu "on top". During installation, it gives you the option to create a separate partition for ubuntu, and afterwards when you boot you will see a menu (GRUB) which will let you pick Windows or ubuntu. You will still be able to access the Windows partition and its files from ubuntu, but not the other way round.

That way you'll always have a working computer while you try to get your network/graphics/sound/printer working in ubuntu. Plus, there are things like games and BIOS flashing which are better being done from Windows.

---

