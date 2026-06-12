---
title: "grub- boot from ubuntu partition"
date: 2008-10-15
forum: General Help
---

### Post by Seks on 2008-10-15
hi, I'm deleting my original windows partition, but it has the boot flag on it so I'm not sure what will happen.

find /boot/grub/stage1 returned (hd0,2), which is my ubuntu partition

I ran root (hd0,2) in grub and moved the flag but I'm not sure if it will still boot, and won't deleting the first partition change it's number to 1? (theres another windows before it)

So, how do I set the boot flag to my Ubuntu partition and do any necessary grub work so it will actually boot?

---

### Post by Spaceman9 on 2008-10-15
Can you type this into a terminal and post the output

cat /etc/fstab

and also 
sudo blkid

---

### Post by Seks on 2008-10-15
**fstab:**

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda2
UUID=24dc29df-6dbd-49da-b51b-2861daac26b8 /               ext3    relatime,errors=remount-ro 0       1
# /dev/sda5
UUID=6f3937bd-4ec1-4b74-b8e3-40fd55b11ec0 none            swap    sw              0       0
/dev/sda1       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0
/dev/scd0       /media/cdrom1   udf,iso9660 user,noauto,exec,utf8 0       0
/dev/scd1       /media/cdrom2   udf,iso9660 user,noauto,exec,utf8 0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto,exec,utf8 0       0
none /proc/bus/usb usbfs devgid=1001,devmode=664 0 0

**sudo blkid:**

/dev/sda1: UUID="7C2CD7212CD6D4EC" TYPE="ntfs" 
/dev/sda2: UUID="240C53BC0C538826" TYPE="ntfs" 
/dev/sda5: TYPE="swap" UUID="6f3937bd-4ec1-4b74-b8e3-40fd55b11ec0" 
/dev/sda3: UUID="24dc29df-6dbd-49da-b51b-2861daac26b8" TYPE="ext3"

---

### Post by Spaceman9 on 2008-10-15
How many cdroms do you have? This info shows 3.

---

### Post by Seks on 2008-10-15
I just have 2 actual optical drives, but it mounts that ntfs partition on media/cdrom0 for some reason

---

### Post by Spaceman9 on 2008-10-15
Ok, then that needs to be correced too. Can you tell me what it is you want to do? Do you want to keep all of these partitions or do you just want the root and home partition for Ubuntu?

Do you want to reformat your ntfs partitions for Linux or keep them?

---

### Post by Seks on 2008-10-15
I want to delete the first ntfs partition, /dev/sda1, but it had the "boot" flag on it in gparted. It's the one with the cdrom0 thing, but I'm deleting it anyways.

I want to keep the second ntfs, the ext3 and the swap of course.
After that I plan to move everything to the left and extend the ext3 with the newly made space. The problem is I don't think it will boot next time without the original ntfs.

---

### Post by Spaceman9 on 2008-10-15
Ok, so if I understand you don't have windows on your hard drive anymore but you want to keep the ntfs partition.

Ok, when you delete that one partition it will renumber all the partitions any you'll have to get the new UUID numbers for the Ubuntu GRUB. For it's fstab file.

If you're in a position to use the live CD and then reinstall Ubuntu into just the root partition it will recreate the fstab file with the new UUID numbers. That could save you some time. Otherwise it could be a long night.

If you reinstall just format the root partition of Ubuntu. you can install the GRUB from Ubuntu on the MBR.

---

### Post by Seks on 2008-10-15
I don't have the disk space, time, or backups to reinstall ubuntu; could I just make reformat the ntfs partition as ext3 and still be able to boot the main ubuntu partition from it?

---

### Post by Spaceman9 on 2008-10-15
If there is anyway for you to boot into Ubuntu you should reformat the ntfs partition from your installed Ubuntu. That would automatically change the UUID in the fstab file. 

If you can't get into your installed Ubuntu use the live CD to reformat the ntfs partition. You will have to add the new UUID to the installed Ubuntu fstab file.

After you get everything working again instal StartUp-Manager from Synaptic. That will let you make a GRUB floppy disk of your Ubuntu GRUB so if anything like this happens again you can still boot into Ubuntu from the floppy disk. Also you can reinstall the GRUB from the floppy disk.

---

### Post by Seks on 2008-10-15
Oh, I'm in ubuntu and everything is running smoothly. I'm just trying to free up disk space. 

I'm not totally sure how grub works though. If menu.lst and stuff are in with ubuntu, then why is the boot flag on the first ntfs partition?

So basically, what I'm looking for now, is if I can format the ntfs partition to ext3 with the boot flag or are there grub files hidden in there that it needs to boot?

---

### Post by Spaceman9 on 2008-10-15
> **Seks said:**
> Oh, I'm in ubuntu and everything is running smoothly. I'm just trying to free up disk space. 

I'm not totally sure how grub works though. If menu.lst and stuff are in with ubuntu, then why is the boot flag on the first ntfs partition?

So basically, what I'm looking for now, is if I can format the ntfs partition to ext3 with the boot flag or are there grub files hidden in there that it needs to boot?

Ok, the GRUB files are all in your root "/" partition. First it runs menu.lst and then fstab. The UUID numbers are in the fstab file. You have to be root to edit those files. you can become root by pressing Alt+F2. In the window that opens type "gksudo nautilus". That will bring up the Nautilus file browser in root mode.

The boot flag is where it is because of windows. It always wants to have it's GRUB on the MBR. Really because Linux works with NTFS you could just leave the partitions the way they are until you have some way of copying your data files to CD or DVD. 

Or, you could move your data files to the ntfs partitions and delete Ubuntu from the live cd. The reforamt the partitions Ubuntu was in with ext3. Then move the data files to the reformatted partitons and delete the partiton you don't want any more.

Then using the live CD reformat the new partition. Then move the data files to the one ntfs partition, reinstall Ubuntu and use your new Ubuntu install to move the data files into your new install of Ubuntu. 

If I had this problem though I'd buy a good DVD burner at newegg. I got  a Samsung a few months ago for just $26.00 with free shipping. I've been in backup hell with no way to backup before so I know what it's like and it's not a nice place to be.

To move GRUB to the MBR 
Try these steps from a terminal in your installed Ubuntu.
Code:
sudo grub
grub> find /boot/grub/stage1
grub> find /grub/stage1

One of the above commands should return your Ubuntu partition in the form of (hdX,Y) where X and Y are numbers, for example (hd0,4), but use whatever it returns as follows:
Code:
grub> root (hdX,Y)
grub> setup (hd0)
grub> quit

---

### Post by Seks on 2008-10-15
Alright, thanks for your help. I ended up just reformatting the ntfs as ext3, and the computer still boots fine, with the added space.

Again, I never really had a "problem", I was just confused and didn't want to screw anything up :P

---

### Post by Spaceman9 on 2008-10-15
> **Seks said:**
> Alright, thanks for your help. I ended up just reformatting the ntfs as ext3, and the computer still boots fine, with the added space.

Again, I never really had a "problem", I was just confused and didn't want to screw anything up :P

I'm glad it worked out. Don't forget StartUp-Manger. It saved my life a few times. Take care.

---

