---
title: "10 steps to make your EeePC not boot!"
date: 2008-10-01
forum: General Help
---

### Post by NAM on 2008-10-01
1. Well I'm in a predicament as well. I made a bootable USB stick with UNetbootin on a 2 gig USB stick.

2. Booted "live" into eeebuntu with the usb stick.

3. As soon as eeebuntu started I got a window saying Welcome Ready to install? I just chose next till I got to chose where to  install.
4. At the where to install window  at the top it said Guided-resize SCI 0,0,0, partition #1 sda Microsoft Windows XP.

5. I thought no "I dont want to over write XP!" So I chose Guided-use entire disc SCSI4 (sdb) 8.2 GB Single Flash Reader.

6. I chose next and chose my login and password and computer name.

7. Next window says "select any accounts you want to import from Microsoft Windows XP (sda1)" I left it unchecked and choose next.

8. Next window says the following partition tables of the following devices will be changed. SCSI4 (0.0.0) (sdb)

9. I chose advanced and left "install boot loader" checked  and for "device for boot loader install" I chose /dev/sdb
Installation starts and finally completes.

10. Upon reboot I get the boot choices as far as:
_____________________________________________________________________________
Ubuntu 8.04.1 kernel 2.6 24-1-if I chose this I get "Error 17: Cannot mount selected partition."
""recovery mode
""memtest 86+
Other operating systems:
Microsoft windows XP Home Edition.- Choosing this gives me "error 13: Invalid or unsupported executable format."
_______________________________________________________________________________
Pressing any key takes me back to the OS choices menu

What can I do to fix this? I guess all is not lost since I can always boot into ubuntu with the USB stick. Or just reinstall XP.
I followed the bouncing ball from with in eeebuntu and made what I thought were logical choices on where to install this on
the SDHC card. What gives?

---

### Post by NAM on 2008-10-02
Well I got it to boot somehow. If I try to boot XP or Ubuntu off of the hard drive or internal sdhc card I get a grub 15 or grub 21 boot error. If i put the USB stick in that I installed eeebuntu onto and made live with UNetbootin ,it gives me a boot OS choice menu and if I choose Windows XP it will boot just fine. Does that mean that grub or my menu.lst is on the USB stick or something? 

I use the USB stick to boot into XP for now since it works but how can i fix this? Since I can boot into XP can I fix the mbr from with in XP so that it will boot off of the hard drive like it use too?

---

### Post by LowSky on 2008-10-02
Google Fix XP MBR, FYI you will need a XP recovery or install CD to fix the MBR. I hope you got an external CDROM drive.

---

### Post by NAM on 2008-10-02
I don't have an external drive but I was planning on buying one anyway so now is the perfect time i guess!

---

### Post by Herman on 2008-10-02
You can change a MBR to boot Windows again easily using the ms-sys program if you install it in Ubuntu.
```
sudo apt-get install ms-sys
```Before you run ms-sys, you will probably want to check first and see which hard disk is which, so you can work on the right MBR, run 'sudo fdisk -lu' for that,
```
sudo fdisk -lu
```From the output from the above command, you should be able to tell if your USB or your internal drive is called '/dev/sda', or '/dev/sdb'
```
sudo ms-sys -m  /dev/sdb
```Where: /dev/sdb is the MBR of your internal hard drive, (the one you want to boot Windows XP).
NOTE: For most people it would be /dev/sda

That will 'fix' your internal disk's MBR so it will boot only Windows XP again, you don't need a CD/DVD drive or any Windows CD, and it should only take most people a minute or two.

---

### Post by NAM on 2008-10-02
Herman, thank you very much I will try this as soon as I get off work today! It looks easy enough to do. I hope it works for me. Thanks again for taking the time to help me guys,I really appreciate it.

---

### Post by Herman on 2008-10-02
:D Okay, 

If you want to be able to boot your USB Ubuntu, you'll probably be able to do that in your EeePC from the BIOS. 
Just in case you're not sure what I mean, here's a link, [How I boot from my BIOS]("http://www.users.bigpond.net.au/hermanzone/p1.htm#How_I_boot_from_my_BIOS_with_my_F12_key").
My wife is using her EeePC at the moment, but I'm pretty sure something like that works with the EeePC, I think I can remember doing it.

But I left out something important.
You'll need GRUB in the MBR of your Ubuntu USB Flash Memory MBR though, or it won't boot.
If you do this while you still have Ubuntu booted, (and before you run ms-sys), you can [Re-install GRUB with a GRUB shell]("http://users.bigpond.net.au/hermanzone/p15.htm#Re-install_Grub_with_Live_CD").
Another way to do it is to boot with [GRUB's Command Line Interface]("http://users.bigpond.net.au/hermanzone/p15.htm#cli") and do a [Chainloader Boot]("http://users.bigpond.net.au/hermanzone/p15.htm#Third_method_chainloader_boot").Or, you might need toinsert the USB flash memory in some other computer with Linux in it, and install GRUB to MBR in the flash memory that way.
Whichever way you do it, you'll need to make the USB disk's MBR bootable somehow.

---

### Post by C.S.Cameron on 2008-10-03
Google ms-sys before trying, I've heard lots of bad things.
Recently had similar problem, booting the windows disk and using the recovery panel to run fixmbr worked for me, (twice this morning already).

---

### Post by Herman on 2008-10-03
:D If you google mssys.exe you'll come up with lots of bad things alright. 

Are you sure you're not confusing ms-sys with mssys.exe? 
mssys.exe is a different program.

If anyone finds a bug in ms-sys, then please report the bug. Bugs should be reported to the     [     SourceForge Bug Tracking System]("http://sourceforge.net/tracker/?atid=490227&group_id=59200").

Regards, Herman :D

---

### Post by NAM on 2008-10-03
Well the thing is the only way that I can boot into XP is by inserting my USB flash drive into the USB port prior to booting the Eee Pc. Then I get a menu that gives me a choice to boot ubuntu (which i havent tried yet) or XP. It lets me boot into XP just fine.

So Im guessing XP's MBR got wriiten to the USB stick somehow? I'm gonna try Hermans suggestion.

---

### Post by C.S.Cameron on 2008-10-03
This is one of the article that convinced me to try the windows, fixmbr method.
After messing with the windows boot disk too often and further searching I will give ms-sys a try.

As a temporary solution, the pendrive, if working, can be used to boot windows, (thats mbr has been messed up installing the pendrive).
You should be able to select windows by hitting ESC at grub.
The flash drive can be removed after windows boots.

---

### Post by Herman on 2008-10-03
There are lots of ways to revert a MBR back to booting Windows again, I have a whole list of different ways to do it on this page, [Un-install Page]("http://www.users.bigpond.net.au/hermanzone/p18.htm"). 
Anyone can choose whichever software and method they like or can do easily.

---

### Post by anjilslaire on 2008-10-03
> **NAM said:**
> 
3. As soon as eeebuntu started I got a window saying Welcome Ready to install? I just chose next till I got to chose where to  install.
4. At the where to install window  at the top it said** Guided-resize** SCI 0,0,0, partition #1 **sda **Microsoft Windows XP.

This would have allowed you to properly dual-boot both XP & Ubuntu. 

> **NAM said:**
> 
5. I thought no "I dont want to over write XP!" So I chose Guided-use entire disc SCSI4 (sdb) 8.2 GB Single Flash Reader.

You selected to install on another drive, not the built-in installed hard drive.

> **NAM said:**
> 
8. Next window says the following partition tables of the following devices will be changed. SCSI4 (0.0.0) **(sdb)**

9. I chose advanced and left "install boot loader" checked  and for "device for boot loader install" I chose **/dev/sdb**
Installation starts and finally completes.

XP is installed on sda. Everything else you've installed has gone onto sdb, including the boot loader.

The best option would have been to install with the 1st option, Guided-resize. That would have allowed you to shrink the XP partition to make room for Ubuntu on the same SSD, and this could all have been avoided. Then your bootloader & both OSes would have been in separate partitions on the same drive.

---

### Post by NAM on 2008-10-03
Hmm thats all well and good but I was trying to install from usb ubuntu to an sdhc sd card!

---

### Post by Herman on 2008-10-03
> The best option would have been to install with the 1st option, Guided-resize. That would have allowed you to shrink the XP partition to make room for Ubuntu on the same SSD, and this could all have been avoided. Then your bootloader & both OSes would have been in separate partitions on the same drive.:D That's mostly correct, except that GRUB doesn't get installed in any other partition but your Ubuntu partition.

Like all boot loaders, it comes in seperate parts, one part, stage1, goes in the first half of the MBR, and tells the BIOS where to find the other part(s).
The optional stage1_5 normally goes into the first fifteen sectors of the otherwise empty first track of the hard disk. 
Stage1_5 can understand file systems and it's job is to help stage1 to point to the location of the much larger and useful stage2 file of GRUB, which is the one that does the real work. 
The stage2 file is actually in our /boot/grub/ directories, it's too large to be located anywhere else. (Unless you have a '[Dedicated GRUB Partition]("http://users.bigpond.net.au/hermanzone/p15.htm#How_to_make_a_separate_Grub_Partition_")').

When we say we are 'installing GRUB to the MBR of a device, or to a boot sector, we really mean just the stage1 and stage1_5 files. For a boot sector, the stage1_5 file is not used either, just the stage1.

The MBR and the entire first track of the hard disk (63 sectors), are not part of any file system. By convention, the first partition never starts before sector number 63, you can see for yourself when you read the output from 'sudo fdisk -lu',
```
sudo fdisk -lu
```So, GRUB is not installed in Windows XP or Vista, and cannot corrupt any part of those systems as is sometimes alleged by uninformed or misinformed computer users. :D

When we are using a flash memory stick, there's some extra software in the memory stick to make it seem as if it's a hard disk as far as the boot loader or an operating system is concerned. I suppose an sd card would be the same.
I haven't tried booting an SD card yet myself, but I imagine it should be possible.
Normally when a computer's BIOS supports booting any device, you'll be able to find that device listed in your BIOS menus when you are booting from your BIOS. [How I boot from my BIOS]("http://www.users.bigpond.net.au/hermanzone/p1.htm#How_I_boot_from_my_BIOS_with_my_F12_key").
If so, all you probably need to do to make an SD flash card bootable, is install GRUB to it, (or rather, the stage1 and stage1_5 files for GRUB, to be specific).

---

### Post by anjilslaire on 2008-10-03
> **Herman said:**
> :D That's mostly correct, except that GRUB doesn't get installed in any other partition but your Ubuntu partition.


That's correct. I meant to say, the bootloader and OSes would be on the same drive, with the OSes in their own partitions. Grub of course would not be on it's own partition (in most cases as you noted). Thanks for noting that :)

---

### Post by NAM on 2008-10-04
I see so if it doesn't write to XP mbr then why wont it boot off of the hdd when I enable it as first boot device in the bios? And why will XP which resides on the hdd then only boot if I insert the USB ubuntu stick which has grub on it? With the usb ubuntu stick in, I can boot into windows but NOT ubuntu!

 EDIT: Breakthrough I did the following (not my idea,its someone else's post but it works)
When you boot up from the SDHC, you'll get a Grub menu.  eeeXubuntu won't boot, because you need to hand edit menu.lst.  At boot time, the BIOS makes the SDHC be (hd0).  So you've got to edit entries in menu.lst like this...
Code:

title        Ubuntu 7.10, kernel 2.6.22-14-generic
root        (hd0,0)
kernel        /boot/vmlinuz-2.6.22-14-generic root=UUID=7ce21fae-dd4e-4596-bcf7-b0f61b5c9d44 ro quiet splash
initrd        /boot/initrd.img-2.6.22-14-generic
quiet

See that (hd0,0), that is the result of my hand editing it from (hd1,0).
Change all the entries that say (hd1,0) to (hd0,0).

So how can you do this if you boot SDHC, get to grub, but cannot boot?
Select the entry and hit e.  Then select the (hd1) line and edit that to (hd0).  These changes will not be written to disk.  Hit b to boot.  After you boot, you still need to hand-edit menu.lst.
_______________________________________________________________________________

Ok so now I booted eeeubuntu off of the sdhc sd card. Im in right now.
I will still have to fix the mbr using Hermans earlier method and remove windows from the menu.lst correct?
How do I get rights to save my edits to menu.lst again? I changed any reference to hd1,hd0 to hd0,hd0 now how do I save it again? I didnt sudo into the file I just opened the menu.lst up and started editing.

Edit: Nevermind I'm a noob, I'm using gksudo gedit /boot/grub/menu.lst in order to edit menu.lst.

---

### Post by NAM on 2008-10-04
> **Herman said:**
> You can change a MBR to boot Windows again easily using the ms-sys program if you install it in Ubuntu.
```
sudo apt-get install ms-sys
```Before you run ms-sys, you will probably want to check first and see which hard disk is which, so you can work on the right MBR, run 'sudo fdisk -lu' for that,
```
sudo fdisk -lu
```From the output from the above command, you should be able to tell if your USB or your internal drive is called '/dev/sda', or '/dev/sdb'
```
sudo ms-sys -m  /dev/sdb
```Where: /dev/sdb is the MBR of your internal hard drive, (the one you want to boot Windows XP).
NOTE: For most people it would be /dev/sda

That will 'fix' your internal disk's MBR so it will boot only Windows XP again, you don't need a CD/DVD drive or any Windows CD, and it should only take most people a minute or two.

Have a terminal open now and tried to install ms-sys. It says E: Couldn't find package ms-sys

---

### Post by Herman on 2008-10-04
Yeah, I don't know why, there must be something wrong in the repositories, it should be there. I get the same message.

Never mind, here's another way to do it,
Download a small utility called MbrFix.exe here, [http://www.sysint.no/en/Download.aspx](http://www.sysint.no/en/Download.aspx)
Paste the file to the root of drive C:
Boot into Windows XP
Click 'Start'->'Run', type CMD (for a Command Prompt).
Change it to just a C: prompt by typing: cd \ , then press 'Enter'. After that you should just have a plain C:\>_ prompt. 
Type this command after the C:\> prompt: MbrFix /drive 0 fixmbr /yes
Nothing much will appear to happen, your monitor may blink slightly, that's all. 
You will see the plain C:\>_ prompt again. Type 'exit'.
Reboot without you USB drive plugged in and you should boot right into Windows.

You can read all about MbrFix.exe here, [http://www.sysint.no/nedlasting/mbrfix.htm](http://www.sysint.no/nedlasting/mbrfix.htm)

---

### Post by NAM on 2008-10-04
I got it all working just fine now. Thanks to all of you that helped.  Funny, I used mbrfix (found it off your sig Herman) before your last message! Ok so now my status is: I don't need the USB stick at all. When I turn the Eeepc on it auto boots to XP off of the internal hard drive all by itself. If I want to boot ubuntu from the internal SDHC SD flash card I hit escape on boot and choose to boot off of the internal flash reader. I get the grub menu and I start Ubuntu.  All is well now. Thank you very much for your help!

---

### Post by Herman on 2008-10-04
:cool: Cool!
I'm glad I was able to help, and thanks for your patience.
Congratulations and happy Ubuntuing!

Regards, Herman :D

---

