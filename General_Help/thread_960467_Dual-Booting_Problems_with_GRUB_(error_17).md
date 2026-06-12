---
title: "Dual-Booting Problems with GRUB (error 17)"
date: 2008-10-27
forum: General Help
---

### Post by zylya on 2008-10-27
I installed Ubuntu onto a brand new pc which already had vista on it, using the ubuntu disk and getting the installer to automatically partition my disk. Since then I've been able to get into both Vista and Ubuntu but now Grub doesn't boot anything but tells me I have an error 17. I checked on these forums and google and a whole host of other places and tried various things to get it to work, but still no luck. I'm currently booted into Ubuntu off the install disk, although I haven't tried installing it again.

This is what /fdisk -lu tells me I have for my disks, I have no idea which one is which.

> Disk /dev/sda: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders, total 976773168 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x8e691921

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1            2048    19458047     9728000   27  Unknown
/dev/sda2        19458048    22530047     1536000    7  HPFS/NTFS
/dev/sda3   *    22530048   582806069   280138011    7  HPFS/NTFS
/dev/sda4       582806070   976768064   196980997+   5  Extended
/dev/sda5       960703128   976768064     8032468+  82  Linux swap / Solaris

Another post said to try and find /boot/grub/menu.lst but I couldn't find it anywhere. There is no 'grub' folder in /boot/ or anywhere as far as I can tell. I did a file search for 'menu.lst' but it could only find examples of it.

I tried using the grub command then root(hd0,4) - which I was hoping points to /dev/sda4/ which I *think* is the disk with Ubuntu on, but I got the error 21: Selected Disk does not exist.

Essentially, is there any way for me to solve this problem? It seems as though grub doesn't even exist, and yet it's still trying to boot. I can't get into either Vista or Ubuntu, Grub finds error 17 and then just hangs there. Help much appreciated!! :)

---

### Post by ajgreeny on 2008-10-27
It is difficult to figure out what has happened here, but I think you will have grub on the windows MBR if you let the system install by default, so will need to find where the grub files actually are so in the live CD do the following:-

open a terminal and run :
    ```
sudo grub
```
This gets you to a simple grub command line.
Then:
    ```
find /boot/grub/stage1
```
This will tell you where your /boot/grub/stage1 is which is needed to boot ubuntu. Replace the question marks in the following command with the output of the this last command :
   ```
 root (hd?,?)
```
[like : root (hdo,1) ,probably]
then:
    ```
setup (hd0)
```
This is where your windows partition and MBR normally is, but if you want grub on another disk, use hd1, etc as appropriate. It's much easier to use the windows MBR and then just change the default boot system later if others in the family demand windows boots by default.
Then:
    quit
Finally reboot, and hopefully you will now have a working grub bootloader.

If you are using hardy 8.04 and have fully updated it is just possible that the new kernel 2.6.24-21 has caused problems with the grub update, but try the suggestion above first and if that doesn't work, come back again.

There must be a /boot/grub folder on the sda4 partition, as far as I can see, so using the live CD try to see the /boot/grub/menu.lst file and copy the contents here so we can see where it is pointing.

---

### Post by caljohnsmith on 2008-10-27
> **zylya said:**
> ```
Disk /dev/sda: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders, total 976773168 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x8e691921

Device Boot Start End Blocks Id System
[COLOR="Red"]/dev/sda1 2048 19458047 9728000 27 Unknown[/COLOR]
/dev/sda2 19458048 22530047 1536000 7 HPFS/NTFS
[COLOR="Red"]/dev/sda3 * 22530048 582806069 280138011 7 HPFS/NTFS[/COLOR]
/dev/sda4 582806070 976768064 196980997+ 5 Extended
/dev/sda5 960703128 976768064 8032468+ 82 Linux swap / Solaris
``` 
Since sda3 is marked as the bootable partition and is NTFS, that is probably your Vista partition. But then the only partition that Ubuntu could be on is sda1, which is type "unknown" when it should be file system type 83, or linux. I think that is where your problem is, because that would explain the Grub error 17 on start up. What happened on your computer before you started to get the error 17? Can you give any more clues? 

I would start by first changing the file system of sda1 back to ext3, and then do a file system check on it. First boot your Live CD, open a terminal (applications > accessories > terminal) and do:
```
sudo fdisk /dev/sda
```
Then enter "t" to change the file system, "1" for the partition number, then "83" for the file system type, then "w" to write the changes to the disk. Then again run:
```
sudo fdisk -l
```
And make sure it shows the change to sda1, otherwise you may need to reboot. If it shows the change, try:
```
sudo fsck -y /dev/sda1
```
And post the results of that. Let me know how it goes. :)

---

### Post by ajgreeny on 2008-10-27
I had not noticed that the partition sda1 was so large, I just assumed it was a restore partition that the OEM had putthere for restore purposes, but I see you are right, and it must be the ubuntu partition.  I wonder how it got to that place on the disk if you left the system to install by default, as it would usually end up at the end of the disk.

Anyway try what caljohnsmith suggested and you may at least get more useful info, even if it does not solve the problem in one go.

---

### Post by meierfra. on 2008-10-27
Vista's recovery partition is usually around 10GB. So sda1 is probably a recovery partition.  

I would guess that  Ubuntu is hiding in the roughly 190 GB of unallocated space in front of the swap partition.

---

### Post by zylya on 2008-10-28
Ok I tried the things you suggested - I got into the grub command and it gave me an error 15 on find /boot/grub/stage1 - saying it couldn't find the file.

The partition will be partition 4 because that matches the amount of space I told Ubuntu to make for itself in installation - nearly 200GB. Nonetheless I changed partition 1 to type 83 as you suggested, then rebooted (it told me the re-read wouldn't work until after a reboot). I rebooted using the Live CD because it gave the error message again for Grub. The change went through (type set to 83) and the fsck command gave this:

fsck 1.40.8 (13-Mar-2008)
fsck: fsck.ntfs: not found
fsck: Error 2 while excuting fsck.ntfs for /dev/sda1

I ran the same command for partition 4, which gave:

fsck 1.40.8 (13-Mar-2008)
e2fsck 1.40.8 (13-Mar-2008)
fsck.ext2: Attempt to read block from filesystem resulted in short read while trying to open /dev/sda4
Could this be a zero-length partition?

Any ideas from here? Is there a way to totally remove Grub & Ubuntu so that it will boot straight into Windows Vista and I can start over again. I think I must've made a mistake somewhere and hope there's some sort of 'reset' button I can press now!!

---

### Post by caljohnsmith on 2008-10-28
Based on your description, meierfra must be right in that your Ubuntu partition must have been part of your sda4 extended partition. You should at some point change the file system of sda1 back to whatever it should be, maybe it was FAT (I'm not sure, but meierfra would know about Vista recovery partitions). In the meantime, I think your idea of booting into Vista and starting over might work. If you have your Vista Install CD, just go to the command line and run:
```
bootrec /fixmbr
```
Or if you don't have a Vista Install CD, you can download a Vista Recovery CD from [here]("http://neosmart.net/blog/2008/download-windows-vista-x64-recovery-disc/"). Let us know how it goes. :)

---

