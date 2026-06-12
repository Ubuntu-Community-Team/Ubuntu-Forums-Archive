---
title: "NTLDR is missing &amp; cannot mount a drive"
date: 2009-02-03
forum: Installation &amp; Upgrades
---

### Post by jbuntuman on 2009-02-03
Hi

Currently i cannot boot up Windows XP nor access a data drive (shared between Windown and Linux) which I was previously able to. I have a Dell laptop. It has been a couple of years since i first installed it so I have forgotten much, so please sympathise with me ;)

Here is the background. I have my machine setup for dual boot, either Ubuntu or Windows XP. The partitioning is such that my Windows installation is on drive C, and I have a data drive D, which is shared between Windows and Linux.

Here is what happened. I booted windows as I normally did but then up came that blue screen and the words "UNMOUNTABLE BOOT VOLUME". So i searched the net for advice on what to do and here is what i did.

1. Loaded the Windows installation CD and pressed 'R' to start recovery mode. It took me to C: drive. 

2. Then i did a 'chkdsk /r' and it said "The volume appears to contain one or more unrecoverable problems". 

3. Then i did a 'fixboot' and it said:
>Target partition is C:
>Are you sure you want to write a new bootsector to the partition C:?
 ... to which i ansewered 'Y'
>The file system on the startup partition is FAT

>FIXBOOT is writing a new bootsector
>The new bootsector was written successfully 


Now, when i restarted the computer I got a new error. Here is what I got:

*****
Booting 'Microsoft Windows XP Home Edition'

root (hd0,0)
  Filessystem type unknown, partition type 0x7
savedefault
makeactive
chainloader +1

NTLDR is missing
Press any key to restart
*****


So currently I can only boot Ubuntu and this is how i type this message. When i try to mount my shared data drive this is what happens:

johnny@jkd:~$ sudo mount -t vfat -o umask=000 /dev/sda2 /mnt/shared
mount: wrong fs type, bad option, bad superblock on /dev/sda2,
       missing codepage or other error
       In some cases useful info is found in syslog - try
       dmesg | tail  or so

*****

For your information, here is what i get for "fdsik -lu"

johnny@jkd:~$ sudo fdisk -l
Password:

Disk /dev/sda: 80.0 GB, 80026361856 bytes
255 heads, 63 sectors/track, 9729 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        1558    12514603+   7  HPFS/NTFS
/dev/sda2            1559        8171    53118922+   c  W95 FAT32 (LBA)
/dev/sda3            8172        9661    11968425   83  Linux
/dev/sda4            9662        9729      546210    f  W95 Ext'd (LBA)
/dev/sda5            9662        9729      546178+  82  Linux swap / Solaris

*****

And the bottom section of my /boot/grub/menu.lst file looks like this  

## ## End Default Options ##

title		Ubuntu, kernel 2.6.15-27-686
root		(hd0,2)
kernel		/boot/vmlinuz-2.6.15-27-686 root=/dev/sda3 ro quiet splash
initrd		/boot/initrd.img-2.6.15-27-686
savedefault
boot

title		Ubuntu, kernel 2.6.15-27-686 (recovery mode)
root		(hd0,2)
kernel		/boot/vmlinuz-2.6.15-27-686 root=/dev/sda3 ro single
initrd		/boot/initrd.img-2.6.15-27-686
boot

title		Ubuntu, kernel 2.6.15-27-386
root		(hd0,2)
kernel		/boot/vmlinuz-2.6.15-27-386 root=/dev/sda3 ro quiet splash
initrd		/boot/initrd.img-2.6.15-27-386
savedefault
boot

title		Ubuntu, kernel 2.6.15-27-386 (recovery mode)
root		(hd0,2)
kernel		/boot/vmlinuz-2.6.15-27-386 root=/dev/sda3 ro single
initrd		/boot/initrd.img-2.6.15-27-386
boot

title		Ubuntu, kernel 2.6.15-26-386
root		(hd0,2)
kernel		/boot/vmlinuz-2.6.15-26-386 root=/dev/sda3 ro quiet splash
initrd		/boot/initrd.img-2.6.15-26-386
savedefault
boot

title		Ubuntu, kernel 2.6.15-26-386 (recovery mode)
root		(hd0,2)
kernel		/boot/vmlinuz-2.6.15-26-386 root=/dev/sda3 ro single
initrd		/boot/initrd.img-2.6.15-26-386
boot

title		Ubuntu, memtest86+
root		(hd0,2)
kernel		/boot/memtest86+.bin 
boot

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title		Other operating systems:
root


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda1
title		Microsoft Windows XP Home Edition
root		(hd0,0)
savedefault
makeactive
chainloader	+1

*****

I would be eternally grateful if someone could help me out with this. It is really two problems: 1. I want to be able to boot Windows, and 2. I REALLY need the data on my D drive


Thanks in advance to anyone who responds, johnny

---

### Post by caljohnsmith on 2009-02-03
Can you mount the sda1 partition at least? What is the output of:
```
sudo mount /dev/sda1 /mnt && ls -l /mnt
```
Also, did you run the chkdsk on your sda2 partition:
```
chkdsk /r D:
```
If not, I would start there. Please let me know what happens when you do that.

---

### Post by icanfly0307 on 2009-02-03
Okay, I've been through this same exact problem before. Here's what to do:

1. Boot the Windows Cd again and enter the recovery console. Type "fixboot" and press enter.

2. Type "fixmbr" and press enter.

This should fix you up. What you did before was erase the MBR but you didn't install NTLDR which is the bootloader which "lives" in the MBR. Hope this helps.

---

### Post by caljohnsmith on 2009-02-03
> **icanfly0307 said:**
> Okay, I've been through this same exact problem before. Here's what to do:

1. Boot the Windows Cd again and enter the recovery console. Type "fixboot" and press enter.

2. Type "fixmbr" and press enter.

This should fix you up. What you did before was erase the MBR but you didn't install NTLDR which is the bootloader which "lives" in the MBR. Hope this helps.
Grub is perfectly capable of booting Windows, so there is no need to run "fixmbr" to get rid of Grub and only try to boot Windows; but if jbuntuman wants to get rid of Grub, that certainly would work. Also, "ntldr" does not live in the MBR, ntldr is a Windows boot file that lives in the root directory of the Windows XP partition. In addition, a Windows MBR knows nothing of "ntldr"; all a Windows MBR does is try to boot the boot sector of whichever partition has the boot flag set. It is the Windows XP partition boot sector that then tries to boot "ntldr".

---

### Post by jbuntuman on 2009-02-03
Thanks guys. I appreciated the help.

Ok, so when i try to mount sda1 here is what i get

*****

johnny@jkd:~$ sudo mount /dev/sda1 /mnt && ls -l /mnt
Password:
total 221729896
-rwxr-xr-x 1 root root          0 1980-01-01 00:00 <
-rwxr-xr-x 1 root root  271067204 1908-11-24 16:31      ?
-rwxr-xr-x 1 root root  943557463 1940-10-24 16:40  ????<&?.?;?
-rwxr-xr-x 1 root root          0 1980-01-01 00:00 :???
-rwxr-xr-x 1 root root 1061109756 1980-01-31 07:56 ???
-rwxr-xr-x 1 root root       3338 1986-08-10 08:42 ?.?
-rwxr-xr-x 1 root root       4096 1980-01-01 00:00 ?.??
-rwxr-xr-x 1 root root        722 1980-01-01 00:00 ?.?
-rwxr-xr-x 1 root root      10310 2000-01-22 00:00 ?'.?'
-rwxr-xr-x 1 root root          0 1980-01-01 00:00 ?(
-rwxr-xr-x 1 root root      10594 1980-01-01 00:00 ?).?)
-rwxr-xr-x 1 root root      10594 1980-01-01 00:00 ?).?)
-r-xr-xr-x 1 root root 3897956982 1999-02-04 00:41 ?@&?????
-r-xr-xr-x 1 root root        974 1989-11-20 16:00 ?&?????
-r-xr-xr-x 1 root root  587631448 2012-01-07 05:06 ???????.?
-r-xr-xr-x 1 root root 1946092650 2020-01-13 08:44 ??.=$?
-rwxr-xr-x 1 root root 1107296320 1980-01-01 00:00 ??
-rwxr-xr-x 1 root root 4102613078 1981-01-09 23:50 ??.??\
-r-xr-xr-x 1 root root 4232939534 2014-12-11 00:31 ????????.???
-rwxr-xr-x 1 root root 1753219366 1969-12-31 09:31 ????.?&?
-rwxr-xr-x 1 root root       5248 1990-08-15 23:00 ??.??
-rwxr-xr-x 1 root root          0 1980-01-01 00:00 (??.$$

*****

I have only shown part of it, there is about 5 to 10 times tha amount that i have shown here, all very similar. What is this?


Also when i do the "chkdsk /r D:" I get the same as for the C drive, i.e. "the volume appears to contain one or more unrecoverable problems"


Now I wanted to ask about the "fixmbr" command. If i do that will that erase my GRUB and therefore i cannot boot linux? I certainly wouldn't want that.

So what do you think?

---

### Post by caljohnsmith on 2009-02-03
Unfortunately it looks like your sda1 partition has nothing but corrupted files. Do you have any idea what might have caused your sda1 and sda2 partitions to get so corrupted? You could try using a program like [photorec]("http://www.cgsecurity.org/wiki/PhotoRec") to see what files it might be able to recover, but I don't think there's alot of hope of fully recovering either partition. Also, since you want to keep Grub, I would not recommend running "fixmbr" since that will erase Grub in the MBR (Master Boot Record). Good luck and let us know how it goes.

---

### Post by jbuntuman on 2009-02-04
Thanks again

What is the command to use to try and mount my data (D) drive ... the sda2 partition? I'd like to try and check what i get with this.

I downloaded both Photorec and Testdisk, and will give those a whirl soon to see what comes up.

If you have any other suggestions please let me know.

Thanks

---

### Post by caljohnsmith on 2009-02-04
How about doing:
```
sudo vol_id --probe-all /dev/sda2
```
If that shows your sda2 partition is FAT32, then the mount command you used in your first post should have worked if sda2 is not corrupt. So if that's true, I think photorec might be the best thing to try now.

---

