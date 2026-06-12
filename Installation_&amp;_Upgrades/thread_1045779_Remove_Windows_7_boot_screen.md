---
title: "Remove Windows 7 boot screen"
date: 2009-01-20
forum: Installation &amp; Upgrades
---

### Post by Stibily on 2009-01-20
Hi.

I recently reformatted my whole hard disk. So started with intalling Windows XP under the first partition, and a second partition was created for Ubuntu. However, before I installed Ubuntu, I decided to trial Windows 7 beta, installing to the second partition. This then attached the Windows 7 boot menu to the MBR. I have now since removed Windows 7, and have installed Ubuntu in it's place on the second partition, installing the GRUB menu to the MBR also.

My problem is this, when I select the Windows XP partition from the GRUB menu, it still has the old Windows 7 boot menu, rather than launching XP immediately. I wish to remove this screen completely.

How do I go about this?

Many thanks.

---

### Post by philgenius on 2009-03-09
I wish to bump this thread; I, too, have the same problem. And my Windows 7 Partition has been reformatted completely.

---

### Post by Mark Phelps on 2009-03-09
When you installed Windows 7, it actually wrote its boot loader files to the XP partition -- which remained when you removed Windows 7.

Remove the boot directory and bootmgr file.

When you boot into XP, it should then run NTLDR as usual.

---

### Post by philgenius on 2009-03-19
Where is this boot directory and bootmgr file? I have looked in the root directory of the C:\ drive but have only found bootsqt.dat. I deleted that, and the boot menu from Windows 7 still pops up upon restart.

---

### Post by Mark Phelps on 2009-03-19
The following info is courtesy of meierfra:

**Step 3 Fix the XP bootsector.**

There are various ways to accomplish this. I will give you two options:

_Option 1:_

Insert your Win 7 CD in the CDRom drive and wait for a few second. At the command line type:

```
E:\boot\bootsect  /nt52 D: /force
```

Here "E" needs to be replaced by the drive letter of your CDrom drive and "D" by the drive letter of your XP partition. (Just look in "My Computer" to determine the drive letters. Even if you know the drive letters, I suggest to double check. Win 7 and XP probably use different drive letters assigns. You need to use the drive letters used by Win 7)

_Option 2:_

Boot from your XP CD.
Press "r" to enter the repair console.
Use
```
map

```
to determine the drive letter of your XP partition. 

Type
```
fixboot C:
```

Here "C" needs to be replaced by the drive letter of your XP partition.

---

### Post by meierfra. on 2009-03-19
> Where is this boot directory and bootmgr file? I have looked in the root directory of the C:\ drive but have only found bootsqt.dat. I deleted that, and the boot menu from Windows 7 still pops up upon restart.

The boot files are usually hidden. You have the  check "show hidden file" and  uncheck "hide system files" in the View tab of the "folder options". But  deleting those boot files will do you no good. As Mark Phelps said in his last post,   you will need to fix your boot sector.

After you fixed the boot sector and successfully boot into XP, you can delete the Win 7 boot files (but you don't have do)


> Insert your Win 7 CD in the CDRom drive and wait for a few second. 

Those instruction only work, while one is booted into Win 7.  Instead one needs to boot from the "Win 7 CD", choose "Install Now" and press "SHIFT+F10" at the next screen to get a command prompt.

---

### Post by philgenius on 2009-03-27
> **Mark Phelps said:**
> The following info is courtesy of meierfra:

**Step 3 Fix the XP bootsector.**

There are various ways to accomplish this. I will give you two options:

_Option 1:_

Insert your Win 7 CD in the CDRom drive and wait for a few second. At the command line type:

```
E:\boot\bootsect  /nt52 D: /force
```

Here "E" needs to be replaced by the drive letter of your CDrom drive and "D" by the drive letter of your XP partition. (Just look in "My Computer" to determine the drive letters. Even if you know the drive letters, I suggest to double check. Win 7 and XP probably use different drive letters assigns. You need to use the drive letters used by Win 7)

_Option 2:_

Boot from your XP CD.
Press "r" to enter the repair console.
Use
```
map

```
to determine the drive letter of your XP partition. 

Type
```
fixboot C:
```

Here "C" needs to be replaced by the drive letter of your XP partition.


Yeah, I found the files and removed them, but when I booted up the recovery CD, it could not find my hard drive. I could boot up into my Ubuntu partition just fine, and am typing to you through it now, though. Any idea?

---

### Post by graysky on 2009-03-27
I think you just wanna rebuild your MBR from your Windows XP CD (google this topic for more, I'm thinking the command was fixmbr but I can't remember).  After you have XP booting, then boot into your live Ubuntu CD and install GRUB.

See [this thread](http://gparted-forum.surf4.info/viewtopic.php?id=13281) for how I did a similar fix when I more or less 'ghosted' a HDD to a new HDD using gparted.

---

### Post by meierfra. on 2009-03-28
Try this:

Download the attached file "XP_nine.txt" to your desktop. Open a terminal
and type

```

sudo dd if=~/Desktop/XP_nine.txt of=/dev/sda1 bs=1 seek=80 skip=80 
```
Here /dev/sda1 needs to be replaced by the actual device name of your Windows Partition 
(use "sudo fdisk -lu" to determine the device name 
**Do not use  use that command if you are not sure what   correct device name is** 
Instead, post the output of "sudo fdisk -lu" and I should be able to tell you the device name)

Be very careful with the "dd" command. If it runs for more than just a couple of seconds, stop the process with "ctrl+C".

Reboot, and see whether you are now able to boot XP.

---

### Post by philgenius on 2009-03-28
I actually found that the Boot folder and bootmgr files did not delete completely, so that was the cause of the error. Now I boot Windows freely and without the boot menu. Thanks for all your help!

---

