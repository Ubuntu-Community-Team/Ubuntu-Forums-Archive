---
title: "Ubuntu 8.10 won't boot after installation"
date: 2009-01-01
forum: Installation &amp; Upgrades
---

### Post by logic_guy76 on 2009-01-01
I have a single hard drive partitioned like this:
/dev/sdb
   sdb1       ntfs  (WinXP)
   sdb2       Extended
      sdb5    ntfs  (extra storage for WinXP)
      sdb6    ext3  (Fedora Linux 2)
      sdb7    ext3  (Ubuntu)
      sdb8    ext3  (extra storage for Linux)
      sdb9    linux-swap

I previously had WinXP and Fedora Linux 2 running with GRUB used to select which one.

I installed Ubuntu 8.10 in sdb7 from the live CD. (sdb7 was previously empty.) The installation seemed to proceed with out a hitch.  Now, when I power on the PC I get this GRUB menu:
Ubuntu 8.10. kernel 2.6.27-7-generic
Ubuntu 8.10. kernel 2.6.27-7-generic (recovery mode)
Ubuntu 8.10. memtest86+
Other operating systems:
Windows NT/2000/XP
Fedora Linux 2 (2.6.5-1.358smp) (on /dev/sdb6)
Fedora Linux 2-up (2.6.5-1.358) (on /dev/sdb6)

XP and Fedora still boot OK.  HOWEVER, when I select any of the Ubuntu options, I immediately get this message from GRUB:
Boot from (hd0,5) ext3 638746f-...(a bunch more digits)
Error 15: File not found
Press an key to continue...

Pressing a key takes me back to the GRUB menu.

All 3 Ubuntu 8.10... selections give the same Error 15 message.

I tried wiping the sdb7 partition clean (reformatted).  Also removed GRUB temporarily so I had just a single boot into XP only.  Tried the Ubuntu installation again.  Exactly the same results.  Trying to boot Ubuntu immediately gives the Error 15 message and take me back to the GRUB menu.

It seems that the install procedure is not configuring GRUB correctly.

Any suggestions?

---

### Post by cdnLilwolf on 2009-01-02
How old is your grub version (should be at least .97-21)?  You may need to update it as I had a similar problem when running Fedora 8 and installed Ibex as well.

---

### Post by caljohnsmith on 2009-01-02
In order to get a clearer picture of your setup, how about booting your Live CD (the Ubuntu install CD), open a terminal (Applications > Accessories > Terminal) and do:
```
cd ~/Desktop && wget 'http://home.comcast.net/~ubuntu_grub/boot_info_script.txt' && sudo bash boot_info_script.txt
```
That will create a "RESULTS.txt" file in the same directory from where the script is run, namely your desktop; please copy/paste the contents of that file to your next post, highlight the copied text, and click the pound sign # graphic in the Ubuntu forum message box so that the text will get "code" tags put around it.

If you don't have internet connectivity when using the Live CD, how about instead right-clicking [this link]("http://home.comcast.net/~ubuntu_grub/boot_info_script.txt") to the script in your web browser, choose "Save link as...", save the "boot_info_script.txt" file, transfer it to your Ubuntu desktop on the Live CD via USB stick, floppy, or however you want to do it, and then do the following in a terminal:
```
sudo bash ~/Desktop/boot_info_script.txt
```
The results of that script will help clarify your setup and hopefully what your problem might be.

---

### Post by logic_guy76 on 2009-01-03
Thanks,caljohnsmith. I tried running your script and looked at the RESULTS.txt file.  It gave some warnings about my ntfs partitions; but, XP is running fine and chkdsk doesn't report any errors, so I think those are OK.

After lots more experimentation, I have finally discovered that the problem all along was with the way the installation process coded the grub/menu.lst file.

I did lots of reading up on GRUB and created a GRUB boot diskette.  I booted the diskette and entered the appropriate "root", "kernel", and "initrd" commands from the grub command line.  Ubuntu booted right up.  I went into the /boot/grub directory and edited the menu.lst file.  The original commands for booting Ubuntu were like this:
```
title		Ubuntu 8.10, kernel 2.6.27-7-generic
uuid		6368746f-2074-616b-6f65-207575696400
kernel		/boot/vmlinuz-2.6.27-7-generic root=UUID=6368746f-2074-616b-6f65-207575696400 ro quiet splash 
initrd		/boot/initrd.img-2.6.27-7-generic
quiet
```

The commands for booting my old Fedora partition were like this:
```
title		Fedora Linux 2 (2.6.5-1.358smp) (on /dev/sdb6)
root		(hd0,5)
kernel		/boot/vmlinuz-2.6.5-1.358smp ro root=LABEL=FEDORA_CORE rhgb quiet 
initrd		/boot/initrd-2.6.5-1.358smp.img
```

So, I changed the Ubuntu boot commands to be similar to the Fedora ones:
```
title		Ubuntu 8.10, kernel 2.6.27-7-generic
root		(hd0,6)
kernel		/boot/vmlinuz-2.6.27-7-generic root=LABEL=UBUNTU ro quiet splash 
initrd		/boot/initrd.img-2.6.27-7-generic
quiet
```
I changed the "uuid	6368746f-2074-616b-6f65-207575696400" command to "root	(hd0,6)" and changed the "root=" portion of the kernel command to "root=LABEL=UBUNTU", the volume label I used when I created the Ubuntu partition.  I shut down, rebooted from the hard disk, selected Ubuntu from the GRUB menu, and this time it booted right up.  Typing this reply from Ubuntu now.

---

