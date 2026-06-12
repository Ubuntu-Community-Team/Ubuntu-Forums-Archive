---
title: "Reinstalling XP on slave partition - unable to reboot.... anything"
date: 2009-04-20
forum: Installation &amp; Upgrades
---

### Post by JR_Moneybags on 2009-04-20
Okay, so I guess I've done something really stupid along the line here, but meh.... that's how we learn isn't it?

And perhaps this is not really one for the Ubuntu forum, but generally people respond really well here.

So I have attempted to reinstall Windoze XP back onto my desktop - at the request of the wife for the purpose of playing Sims2.

I wanted to put if on some partition right at the back there (I think it's hdb2 and like f: according to the Windows install).

Anyway, when WinXP went for it's first reboot during the install it must have screwed up the MBR and now I simply get "Disk Error" when I try to reboot my system..

Is this what has happened? How can I fix things up a) to get back into Ubuntu and b) to finish the install for XP.

Is there a good boot disk that I should try to rebuild and reorganise the boot loader?

Thanks for the help.
Cheers

---

### Post by Herman on 2009-04-20
It sounds like Windows Xp has done something to the MBR. I'm not sure about Windows, but Super Grub Disk can help you boot your Ubuntu install and/or re-install your GRUB to MBR, [Super Grub Disk]("http://www.supergrubdisk.org/").

---

### Post by upchucky on 2009-04-20
there is a utility on the windows disk, called fixmbr

it will get the windows bootloader working again.

if you still need to install windows and want to keep ubuntu then look here.

[http://apcmag.com/how_to_dual_boot_linux_and_windows_xp_linux_installed_first.htm](http://apcmag.com/how_to_dual_boot_linux_and_windows_xp_linux_installed_first.htm)

HOW TO: Recover Windows MBR using Ubuntu LIVE CD
Tested on Ubuntu 7.04; Ubuntu 7.10 and Linux Mint 4.0 Live CDs

If want to restore Windows Bootloader and for some reason cannot use the windows installation cd, there is a simple way to do it:

NOTE: make sure you have internet working.

Before the first step:
(I needed to enable the 'universe' repository (System->Administration->Software Sources) before I could install the ms-sys package. I also needed to put "sudo" in front of the ms-sys command (e.g. "sudo ms-sys --mbr /dev/sda") otherwise I got permission denied.)

1) Boot with Ubuntu Live CD or Linux Mint Live CD


2) On the terminal:

sudo apt-get install ms-sys

then

ms-sys --mbr /dev/hdX

NOTE: in my case the main windows xp system is located in hda1 so I used

sudo ms-sys --mbr /dev/hda

***
ubuntu@ubuntu:~$ sudo ms-sys --mbr /dev/hda
Windows 2000/XP/2003 master boot record successfully written to /dev/hda

---

### Post by JR_Moneybags on 2009-04-20
Hi guys... Thanks for the replies.

Tried fixmbr - no success.

I had already downloaded another system rescue cd with ms-sys on it. I ran that as you suggested with:
ms-sys --mbr -f /dev/sdb2

It said it worked, however I still have the Disk error.

I am about to try with the super grub disk.

I'll let you know.

---

### Post by JR_Moneybags on 2009-04-20
Okay, finally something going my way.

Now I have been able to use Grub Super Disk to get Ubuntu back up. Now how do I make the MBR look for the grub list in Ubuntu rather than the WinXP one?

Once I get that restored I can try windows again later.

---

### Post by Herman on 2009-04-20
There are two ways you can install GRUB to MBR using Super Grub Disk.
One way is by using the menus and the other way is by pressing your 'c' key from a menu and using GRUB's [GRUB's Command Line Interface]("http://users.bigpond.net.au/hermanzone/p15.htm#cli").

With the menus in Super Grub Disk, there should be one in there somewhere titled something like 'Restore the boot of Linux', or something like that, with sub-menus which allow you to select your /boot partition and which partition or which hard disk's MBR you want to install GRUB to.

If you use [GRUB's Command Line Interface]("http://users.bigpond.net.au/hermanzone/p15.htm#cli"), you will need to be able to type your own commands, but really, it's pretty easy. This link shows you how to do a chainloader boot from the command line, [Chainloader Boot]("http://users.bigpond.net.au/hermanzone/p15.htm#Third_method_chainloader_boot") .
First you need to install GRUB to the first sector of the Ubuntu partition before that will work. The linked web page shows you how to do that right underneath, (it's backwards I know, but it needs to be that way for a reason). 
You can modify and adapt the same instructions but install GRUB to (hd0) and chainload your first hard disk's MBR (hd0). 
In your case you want to install GRUB to (hd0), but you can install GRUB to both locations, that's what I do.

The reason why the instructions are backwards like that is in case someone only needs to chainload their partition or MBR without installing GRUB anywhere first. Maybe somebody already has GRUB installed to the boot sector or they might have some other boot loader there like LiLo. In that case they might not want to install GRUB somewhere before they run the chainloader sequence. I hope that how-to is clear enough and easy to follow.

---

