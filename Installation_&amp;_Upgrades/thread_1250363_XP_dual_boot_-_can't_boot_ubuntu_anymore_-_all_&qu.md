---
title: "XP dual boot - can't boot ubuntu anymore - all &quot;howto&quot; failed"
date: 2009-08-26
forum: Installation &amp; Upgrades
---

### Post by glasnhost on 2009-08-26
Hi,

I had a working dual boot PC WindowsXP+Ubuntu.
When I reinstalled windows, ubuntu disappeared from the boot list.

I discovered that this is a well known problem and I tried the steps in
[https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows](https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows) 
and its many variations.

However grub fails at the command "setup" with "error 12 invalid device requested":

```

ubuntu@ubuntu:~$ sudo mkdir /mnt/root
ubuntu@ubuntu:~$ sudo mount -t ext3 /dev/sda5 /mnt/root
ubuntu@ubuntu:~$ sudo mount -t proc none /mnt/root/proc
ubuntu@ubuntu:~$ sudo mount -o bind /dev /mnt/root/dev
ubuntu@ubuntu:~$ sudo chroot /mnt/root /bin/bash
root@ubuntu:/# sudo grub
sudo: unable to resolve host ubuntu
Probing devices to guess BIOS drives. This may take a long time.
root@ubuntu:/# sudo grub
grub> find /boot/grub/stage1 
 (hd0,5)
grub> root (hd0,5)
grub> setup (hd0)
 Checking if "/boot/grub/stage1" exists... yes
 Checking if "/boot/grub/stage2" exists... yes
 Checking if "/boot/grub/e2fs_stage1_5" exists... yes
 Running "embed /boot/grub/e2fs_stage1_5 (hd0)"...  17 sectors are embedded.
succeeded
 Running "install /boot/grub/stage1 (hd0) (hd0)1+17 p (hd0,5)/boot/grub/stage2 /boot/grub/menu.lst"... failed

Error 12: Invalid device requested
grub> 

```I also tried grub-install:
```

ubuntu@ubuntu:~$ sudo mkdir /media/root
ubuntu@ubuntu:~$ sudo mount /dev/sda5 /media/root
ubuntu@ubuntu:~$ sudo grub-install --root-directory=/media/root /dev/sda
grub-probe: error: Cannot open `/boot/grub/device.map'
[: 494: =: unexpected operator
The file /media/root/boot/grub/stage1 not read correctly.
```My fdisk output is:
sudo fdisk -l
/dev/sda1               1          11       88326   de  Dell Utility
/dev/sda2   *          12        8729    70027335    7  HPFS/NTFS
/dev/sda3            8730       14201    43953840    f  W95 Ext'd (LBA)
/dev/sda4           13941       14201     2096451   dd  Unknown
/dev/sda5            8730       13721    40098177   83  Linux
/dev/sda6           13722       13940     1759086   82  Linux swap / Solaris

I'll keep trying, if anybody has any suggestion, please let me know.
This problem is very annoying.

thanks

---

### Post by jimmers on 2009-08-26
Hi,
Are you installing Windows on a separate partition, or are you using the whole disk, if you are using the whole disk Windows will eradicate any other operating systems on the disk, entailing a complete fresh re-install of Ubuntu, use the partitioner to resize the hard disk to fit  Ubuntu.


Hope this helps


Jimmers

---

### Post by enli on 2009-08-26
The easier method is to recover grub manually. (That is what I think and it always worked while explaining to my non-techy friends)

Open terminal from Live-CD and
```

sudo grub

```
This will give you a prompt like MS-DOS in windows, type
```
find /boot/grub/stage1
```
which will return something like (hd0,X). Note the number X.
```

root (hd0,X)
setup (hd0)

```
Replace X in above command. The last command should show 4-5 lines of messages and at the end something that says SUCCESSFUL. Reboot and you have your grub menu back.

---

### Post by glasnhost on 2009-08-26
Hi, thanks!

first, Windows was already installed in another partition of the same disk. 
It seems that re-installing Windows only disabled grub bootloader, ubuntu is still there.

Any attempt to reinstall grub through the console, as suggesteed by enli, fails with 
"Error 12 invalid device requested"
or "The file /media/root/boot/grub/stage1 not read correctly"
(see original post)

Las new is that I managed to reboot my existing Ubuntu partition with a SuperGrub usb-disk ([http://www.supergrubdisk.org/w/index.php5?title=Main_Page)]("http://www.supergrubdisk.org/w/index.php5?title=Main_Page").

However, I still need the usb disk to boot. I can't find how to restore permanently the grub bootloader.

g.

---

### Post by presence1960 on 2009-08-26
Let's get a better look at your setup. Boot the Ubuntu Live CD. Choose "try ubuntu without any changes", when the desktop loads come back here and use the link in my signature to download the Boot Info Script 0.32 to the desktop. Once on desktop open a terminal and run this command ```
sudo bash ~/Desktop/boot_info_script*.sh
``` This will create a RESULTS.txt file on the desktop. Paste the entire contents of that file back here. Once pasted highlight all text and click the # sign on the toolbar to place code tags around the text.

---

### Post by glasnhost on 2009-08-27
Thank you, very useful script.

However I've already found how to fix grub from the SuperGrub usb disk ([http://www.supergrubdisk.org/w/index.php5?title=Howto_Fix_Grub#Quick_solution]("http://ubuntuforums.org/Thank%20you,%20very%20useful%20script.%20%20However%20I%27ve%20already%20found%20how%20to%20fix%20grub%20from%20the%20SuperGrub%20usb%20disk%20%28http://www.supergrubdisk.org/w/index.php5?title=Howto_Fix_Grub#Quick_solution%29%20and%20now%20everything%20is%20fine"))
and now everything is fine.

The script output doesn't show anything strange, probably because now GRUB is fixed...

thanks
g.

---

