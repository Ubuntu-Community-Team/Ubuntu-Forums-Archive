---
title: "New Intrepid setup, grub gives error 21 w/ XP disk"
date: 2009-03-21
forum: Installation &amp; Upgrades
---

### Post by epsilon72 on 2009-03-21
**SOLVED**
Hello, I'm sort of new to ubuntu but not as new to linux in general.  I'm mainly a Gentoo user.  I'm trying to install Ubuntu on a Dell Dimension 8400 PC for my parents and have it dual boot XP and Ubuntu.

Since the computer's bios is too inflexible (ugh...dell :rolleyes:)to even let me choose which drive to boot from, I had to move the original drive to SATA port 1 and plug the new Ubuntu drive into port 0.

Ubuntu installs fine, and runs fine, but whenever I try to boot into windows, I get -

Error 21: The selected disk does not exist.

Which obviously is wrong, since I can switch the XP drive back to port 0 and boot into it just fine.  The Windows XP disk is set up as follows:

partition 1: ??? (some very small partition, on there by default from dell)
partition 2: ntfs partition (has the bootable flag)- where windows XP resides
partition 3: Dell recovery partition

Grub was installed onto Ubuntu's drive.  I'm trying to get it so that the ubuntu drive is /dev/sda and the xp drive is /dev/sdb.

Grub *looks* like it's pointed to (hd1,1) for the windows entry, so I'm not sure what's going on here.  Any ideas?  Could it be a Dell hardware specific problem?

---

### Post by epsilon72 on 2009-03-21
Hmmm I just had an idea come to me...

Anyone know about using the windows XP bootloader to boot into linux?  I seem to remember reading something about that a while back...maybe as a last resort though, I'd much rather get grub working.

---

### Post by meierfra. on 2009-03-21
At the grub menu at boot up, press "c". 
This will get you to the grub command line


Type

```
geometry (hd0)

geometry (hd1)

geometry (hd2)
```

This should show the partitions of your 1st, 2nd and  3rd hard drive. 

(If "geometry (hd1)" gives an error messages,  try "geometry (hd2)" even if you only have two hard drives)

Judging from the output:

Is grub detecting your hard drive correctly?
Which hard drive contains XP?


Pressing "Esc" will  get you back to the grub menu.
Boot into Ubuntu, open a terminal and post the output of

```
sudo fdisk -lu
```



> Anyone know about using the windows XP bootloader to boot into linux? 

I can show you how to add Ubuntu the XP boot loader, but let's first try to figure out what's going on.

---

### Post by epsilon72 on 2009-03-21
> **meierfra. said:**
> At the grub menu at boot up, press "c". 
This will get you to the grub command line


Type

```
geometry (hd0)

geometry (hd1)

geometry (hd2)
```

This should show the partitions of your 1st, 2nd and  3rd hard drive. 

(If "geometry (hd1)" gives an error messages,  try "geometry (hd2)" even if you only have two hard drives)

Judging from the output:

Is grub detecting your hard drive correctly?
Which hard drive contains XP?


Pressing "Esc" will  get you back to the grub menu.
Boot into Ubuntu, open a terminal and post the output of

```
sudo fdisk -lu
```





I can show you how to add Ubuntu the XP boot loader, but let's first try to figure out what's going on.
Thanks a bunch, I'll try that as soon as I can get on that PC again.

---

### Post by epsilon72 on 2009-03-21
According to grub, no device exists except hd0 (the linux drive).  Does grub have problems with certain bios setups?

Output of fdisk:
```
Disk /dev/sda: 320.0 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders, total 625142448 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x000f2987

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *          63   622133189   311066563+  83  Linux
/dev/sda2       622133190   625137344     1502077+   5  Extended
/dev/sda5       622133253   625137344     1502046   82  Linux swap / Solaris

Disk /dev/sdb: 160.0 GB, 160000000000 bytes
255 heads, 63 sectors/track, 19452 cylinders, total 312500000 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x9dc96e9e

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1              63      112454       56196   de  Dell Utility
/dev/sdb2   *      112455   306198899   153043222+   7  HPFS/NTFS
/dev/sdb3       306198900   312496379     3148740   db  CP/M / CTOS / ...

```

---

### Post by meierfra. on 2009-03-21
> Something is strange here...after I select the linux partition, it mentions that the drive is 0x9dc96e9e.

From everything else I have seen so far, it seems that grub is installed to the linux drive. But just to make sure:

Download the Boot Info Script to  your desktop:

[https://sourceforge.net/projects/bootinfoscript/]("https://sourceforge.net/projects/bootinfoscript/")

Then open a terminal (Applications > Accessories > Terminal) and type:

```
sudo bash ~/Desktop/boot_info_script*.sh
```

That will create a "RESULTS.txt" file in the same directory from where the script is run, namely your desktop; please copy/paste the contents of the RESULTS.txt file to your next post, highlight the copied text, and click the pound/hash sign "#" graphic button in the Ubuntu forum message box so that the text will get "code" tags put around it. 

> 
According to grub, no device exists except hd0 (the linux drive).

That's what I was worried about. 

Check on the setting in your bios.  See whether you can find  anything which might  cause the problem. Make sure that the second drive isn't disabled somewhere.  See what happens if you plug the Windows drive in a different port (but leave Ubuntu in port 0).
Try one thing at the time and use the "geometry" commands to check whether XP drive is detected. You might also try geometry (hd3).

---

### Post by epsilon72 on 2009-03-21
Grub is installed to the right drive, I just saw the 0x9 at grub's boot and thought it was referring to the drive number when it's actually part of the grub boot entry (UUID=somethingsomething)

I'll try different SATA ports.  I think though that there aren't really any options in the bios setup screen that would affect booting, but I'll try everything.

---

### Post by epsilon72 on 2009-03-22
Haha, well, it seems the solution was more or less right in front of my face, but your suggestion to check my bios again helped.  It turns out that all of the SATA ports except for 0 were disabled by default - activating the windows drive's port solved the problem completely.

---

### Post by meierfra. on 2009-03-22
> activating the windows drive's port solved the problem completely.

Great. Have fun with XP and Ubuntu.

---

