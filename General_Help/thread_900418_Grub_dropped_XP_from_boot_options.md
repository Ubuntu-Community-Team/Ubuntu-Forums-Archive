---
title: "Grub dropped XP from boot options"
date: 2008-08-25
forum: General Help
---

### Post by twobobs on 2008-08-25
First, I am a true newbie with Ubuntu - love the OS and have enjoyed using it. 

Over the weekend I was utilizing the auto-update feature and the system was upgrading to ver. 8.0.X. Partially through the upgrade the system indicated that the partition did not have sufficient free space and aborted the upgrade. When I rebooted the Windows XP boot option was no longer in Grub and was replaced by the Ubuntu kernel 2.6.15-52-386. The previous kernel (2.6.15-29-386) is still there.

I have one HD onto which Ubuntu and Windows are installed in their own partitions.

How can I get Grub to see the Windows XP install and allow me to boot to it?

I have apps in XP that I must access or I'd drop Windows completely - alas, that is not an option.

Thanks in advance for your help... ;)

---

### Post by WRDN on 2008-08-25
The easiest way (imo) would be to add the Windows entry to the menu file manually.

First, in the Terminal type:

```
sudo fdisk -l
```

This will allow you to find what drive/ partition Windows is installed on.

Now, type:

```
gksudo gedit /boot/grub/menu.lst
```

Now, add a divider and the entry for Windows to the bottom of the file.

This is an extract from my menu.lst file:

> 
### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title		Other operating systems:
root


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda1
title		Microsoft Windows XP Home Edition
root		**(hd0,0)**
savedefault
makeactive
chainloader	+1


Replace (hd0,0) with the drive (first "0") and partition (second "0") Windows is located on.

When I type "sudo fdisk -l" this is my output:

> 
 Disk /dev/sda: 122.9 GB, 122942324736 bytes
255 heads, 63 sectors/track, 14946 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x93109310

   Device Boot      Start         End      Blocks   Id  System
**/dev/sda1   *           1       13212   106125358+   7  HPFS/NTFS**
/dev/sda3           13213       14946    13928355    5  Extended
/dev/sda5           13213       14791    12683254+  83  Linux
/dev/sda6           14792       14855      514048+  82  Linux swap / Solaris
/dev/sda7           14856       14946      730926   83  Linux


The bold entry is the one for Windows. /dev/sdaN (where N represents a number) is the device, and sda refers to drive 0. The 3rd letter changes for every new drive. For example, if the first HDD is sd**a**, then the second may be sd**b**.
The number (in my case, "1") refers to the partition. When counting, start from zero. Thus, it is "(hd0,0)".

---

### Post by twobobs on 2008-08-25
OK, I've added XP to the menu file as directed. Here goes... :popcorn:

---

### Post by twobobs on 2008-08-25
I made the suggested changes to the menu file, but when I attempted to boot into Windows I received "Error 23 - could not parse the number". What have I done wrong?

When I ran 'sudo fdisk -l' this is the output:

```
Disk /dev/hda: 60.0 GB, 60011642880 bytes
255 heads, 63 sectors/track, 7296 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hda1   *           1        5471    43945776    c  W95 FAT32 (LBA)
/dev/hda2            5472        5478       56227+  83  Linux
/dev/hda3            5479        5601      987997+  82  Linux swap / Solaris
/dev/hda4            5602        7296    13615087+  83  Linux
```


This is the output from my updated menu.lst file per suggestions: 

```
## ## End Default Options ##

title 		Microsoft Windows XP Home Edition
root		(hda1,1)
savedefault
makeactive
chainloader +1

title		Ubuntu, kernel 2.6.15-52-386
root		(hd0,1)
kernel		/vmlinuz-2.6.15-52-386 root=/dev/hda4 ro quiet splash
initrd		/initrd.img-2.6.15-52-386
savedefault
boot

title		Ubuntu, kernel 2.6.15-52-386 (recovery mode)
root		(hd0,1)
kernel		/vmlinuz-2.6.15-52-386 root=/dev/hda4 ro single
initrd		/initrd.img-2.6.15-52-386
boot

title		Ubuntu, kernel 2.6.15-29-386
root		(hd0,1)
kernel		/vmlinuz-2.6.15-29-386 root=/dev/hda4 ro quiet splash
initrd		/initrd.img-2.6.15-29-386
savedefault
boot

title		Ubuntu, kernel 2.6.15-29-386 (recovery mode)
root		(hd0,1)
kernel		/vmlinuz-2.6.15-29-386 root=/dev/hda4 ro single
initrd		/initrd.img-2.6.15-29-386
boot

title		Ubuntu, kernel 2.6.15-23-386
root		(hd0,1)
kernel		/vmlinuz-2.6.15-23-386 root=/dev/hda4 ro quiet splash
initrd		/initrd.img-2.6.15-23-386
savedefault
boot

title		Ubuntu, kernel 2.6.15-23-386 (recovery mode)
root		(hd0,1)
kernel		/vmlinuz-2.6.15-23-386 root=/dev/hda4 ro single
initrd		/initrd.img-2.6.15-23-386
boot

title		Ubuntu, memtest86+
root		(hd0,1)
kernel		/memtest86+.bin 
boot



### END DEBIAN AUTOMAGIC KERNELS LIST
```

---

### Post by -Zeus- on 2008-08-25
change (hd1,1) to (hd0,0)

Also, move the windows entry to the bottom (under ##END DEBIAN AUTOMAGIC KERNELS LIST) so it doesn't get wiped when you get a kernel update.

---

### Post by twobobs on 2008-08-25
> **-Zeus- said:**
> change (hd1,1) to (hd0,0)

Also, move the windows entry to the bottom (under ##END DEBIAN AUTOMAGIC KERNELS LIST) so it doesn't get wiped when you get a kernel update.

Thanks. I'll make the changes.

Another question: Can I set a period of time (30 sec., 60 sec.) so that Grub will boot into Windows automatically?

---

### Post by WRDN on 2008-08-25
> **twobobs said:**
> Thanks. I'll make the changes.

Another question: Can I set a period of time (30 sec., 60 sec.) so that Grub will boot into Windows automatically?

To change the time before booting, change the number on the "timeout" line. By default, it will say "timeout 10". Just change the number 10 to something else.
Regarding the second question, you can use different approaches to boot Windows first. The easiest way is to install Startup-Manager (in repos), and make Windows the default OS. Alternatively, in the menu.lst file, change the line "default 0". The number "0" must be changed to the entry for Windows, and you start counting from zero. An example of a GRUB menu:

Ubuntu 8.04
Ubuntu 8.04 Recovery Mode
Memory Test
Other OS:
Windows

In this case, to boot Windows automatically, you could change 0 to 5 ("Other OS:" title must also be counted).

---

### Post by twobobs on 2008-08-25
Made the recommended changes and received the following when I selected Windows XP from the Grub menu:

```
Booting Microsoft Windows XP Home Edition

root (hda0,0)

Error 23: Error while parsing number

Press any key to continue...
```

What is my next step? Is my problem more significant than it appears?  :confused:

---

### Post by WRDN on 2008-08-25
> **twobobs said:**
> Made the recommended changes and received the following when I selected Windows XP from the Grub menu:

```
Booting Microsoft Windows XP Home Edition

root (hd**a**0,0)

Error 23: Error while parsing number

Press any key to continue...
```

What is my next step? Is my problem more significant than it appears?  :confused:

The problem is, you have added an "a" for the root filesystem line (seen in bold). Remove this, and it should read "root (hd0,0)".

---

### Post by -Zeus- on 2008-08-25
> **WRDN said:**
> The problem is, you have added an "a" for the root filesystem line (seen in bold). Remove this, and it should read "root (hd0,0)".

ahhh! sorry for missing that :-(

---

### Post by twobobs on 2008-08-25
> **WRDN said:**
> The problem is, you have added an "a" for the root filesystem line (seen in bold). Remove this, and it should read "root (hd0,0)".

A-HAAAA!!

Fixed - now booting into XP with no problems (other than the usual and customary Windows issues I suffer through)  :)

I've made the changes to allow auto-boot into Windows after 30 seconds unless I want to use Ubuntu.

You all are fantastic - I appreciate your willingness to help a rookie.

Problem solved...

My original desire...how can I upgrade Ubuntu when it says that I need more space for version 8.0.X than I have room for?

---

### Post by WRDN on 2008-08-25
> **twobobs said:**
> A-HAAAA!!

Fixed - now booting into XP with no problems (other than the usual and customary Windows issues I suffer through)  :)

I've made the changes to allow auto-boot into Windows after 30 seconds unless I want to use Ubuntu.

You all are fantastic - I appreciate your willingness to help a rookie.

Problem solved...

My original desire...how can I upgrade Ubuntu when it says that I need more space for version 8.0.X than I have room for?

Happy to help :)

Regarding the question, I guess you will need to delete files or move them to another partition to allow for the updates to install. Out of interest, what source are you using for the space requirement(s)?

---

### Post by -Zeus- on 2008-08-25
> **twobobs said:**
> A-HAAAA!!

Fixed - now booting into XP with no problems (other than the usual and customary Windows issues I suffer through)  :)

I've made the changes to allow auto-boot into Windows after 30 seconds unless I want to use Ubuntu.

You all are fantastic - I appreciate your willingness to help a rookie.

Problem solved...

My original desire...how can I upgrade Ubuntu when it says that I need more space for version 8.0.X than I have room for?

Cool!  about the free space; do you have any free space in your windows partition?

---

### Post by twobobs on 2008-08-25
> **WRDN said:**
> Happy to help :)

Regarding the question, I guess you will need to delete files or move them to another partition to allow for the updates to install. Out of interest, what source are you using for the space requirement(s)?

Thanks again...

When I selected "Upgrade Manager" and the system was beginning the process of installing the new version (8.0) it aborted and indicated that it needed 40 MB and there was only 19 MB available in the partition it was attempting to install on. I'm sure I can increase the size of the partition (is there an Ubuntu version of Partition Magic?) but I was hoping that I wouldn't need to make any more changes to my system...

---

