---
title: "Triple boot Win XP, Win 7 and Ubuntu 8.10 - Single screen wanted"
date: 2009-03-09
forum: Installation &amp; Upgrades
---

### Post by Corbin Dallas on 2009-03-09
Ok, so before everyone goes nuts on why, I am using Ubuntu and XP for work duties and beta testing Win 7 for work as well.

Here's what I have already done:

160GB drive in 4 partitions.

Main partition - XP
Extended partition 1 - Ubuntu 8.10
Extended partition 2 - Win 7
Extended partition 3 - Ghost images of each OS

When I installed Ubuntu 8.10 the grub took over which I did not want to happen. So I used EasyBCD to reinstall the Vista boot loader, set up the triple boot and write the XP boot and drive MBR. 

What happens is XP and Win7 work great. Ubuntu tells me it cannot find the loader for the OS.

In EasyBCD, I set the options to Linux and pointed the loader to the swap, but I'm still not getting the result I'm looking for.

Any suggestions would be great!

---

### Post by Mark Phelps on 2009-03-10
EasyBCD is supported by NeoSoft.  It's not a Linux product; it's an MS Windows product.  For support on EasyBCD, suggest you check the NeoSoft forums.  They have threads dealing exactly with what you're trying to do.

---

### Post by vginov on 2009-03-10
I do not understand why do you need to edit the grub with EasyBCD.. 

Ubuntu supports loading al. the OS. 

I am using 

1. Windows XP
2. Windows Vista
3. Windows 2008 Servr
4. Fedora 10 
5. Ubuntu 8.10 

In a single system. I never had a problem or i never used any other thing to edit the Grub.

I think the only thing you can do is to edit the grub.

To do that 

1. Use your Ubuntu as Live CD 

2. Once it loaded in side open the terminal 

3. Issue the command sudo gedit **/boot/grub/menu.lst** and edit the grub hard disk. 

If you have any problem in that take a look at the bellow link

[http://www.vginov.com/linux/fedora/Setting%20up%20the%20Grub%20Screen/index.php](http://www.vginov.com/linux/fedora/Setting%20up%20the%20Grub%20Screen/index.php)

the above link does not show exactly about your need but something simular to your need.

---

### Post by issih on 2009-03-10
[http://neosmart.net/wiki/display/EBCD/Ubuntu](http://neosmart.net/wiki/display/EBCD/Ubuntu)

You need to reinstall grub into the partition that ubuntu live on, and point easy bcd at that, pointing it at your swap partition makes little sense to me.

By default ubuntu installs grub into the mbr of the primary hard disk, which is what happened to you. Easiest solution it to reinstall ubuntu and follow that guide to put grub into the right place, but if you have things on the ubuntu partition that you want to keep, you can do it using either of the methods shown here:

[https://help.ubuntu.com/community/GrubHowto#Backup,%20Repairing%20and%20Reinstalling%20GRUB](https://help.ubuntu.com/community/GrubHowto#Backup,%20Repairing%20and%20Reinstalling%20GRUB)

Hope that helps.

---

