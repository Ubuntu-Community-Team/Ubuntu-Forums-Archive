---
title: "[SOLVED] Installation stalls at reboot."
date: 2008-09-30
forum: General Help
---

### Post by txfiddler on 2008-09-30
I had posted earlier about my problem installing Wubi on my Dell laptop and got no clear solution on how to fix my problem. I will try to give more observations about my issues.

 The installation appears to go smoothly until the reboot.  When the boot choice come up and you choose "Ubuntu", all you get is a command prompt that just says “Grub” with no indication of the next step.  If I try to type in the location of the Ubuntu boot or grub files then I'll get a file not found error or unrecognized command error.

When I did an installation of Wubi on my whitebox, everything completed with no issues.  I then attempted to install Wubi on a Dell Dimension, my results were identical to my laptop. What do the Dells have in common?  I have noticed that both have small utility partitions at the start of the hard drive to run diagnostics.  I'm thinking that these partitions are confusing the installation process where it doesn't know where the C drive is upon reboot.  Has anyone else had a similar issue?  
Thanks

---

### Post by ago on 2008-09-30
press the insert key rapidly after selecting "ubuntu" to get more info. It might be that grub cannot access the disk where you installed for some reason.

---

### Post by txfiddler on 2008-09-30
> **ago said:**
> press the insert key rapidly after selecting "ubuntu" to get more info. It might be that grub cannot access the disk where you installed for some reason.

If I hit the insert key, Then I get this:

Booting GRLDR...

I hit the enter key and get this:

Get upper memory...

I hit the enter key:

Hard drives: 1, INT13: f00084b1, int15, f000f859
Get_disk info (80) INT 13/41 (80), Version:AA210005, INT 13/48 (80), ERR-0 C/H/S=16
383/16/63, Sector coutn/size= 153356490/01
INT13/08 (80), ERR=0, LBA, C/H/S=16383/255/63, Secor Count/Size=2631928 95/512

Hit the enter key:

Boot drive-80, INT13/4B01(80), ERR-1, Drive 75, CDROM_DRIVE==FFFFFFFF.

hit the enter key:

starting CMAIN ()...

hit the enter key:

OPEN/DEFAULT...

hit the enter key:

FAILURE


After that nothing happens after I hit the enter key.
txfiddler is online now Report Post   	Edit/Delete Message

---

### Post by tinybit on 2008-10-01
On the grub4dos side, several serious bugs have been fixed since the last svn commit. The 0.4.4 final gets near. Try it and see if the problem could be solved. Download the latest build at [http://grub4dos.nufans.net/](http://grub4dos.nufans.net/)

---

### Post by ago on 2008-10-02
tinybit we are at rev 60 for grub4dos, it is unlikely we'll be able to incorporate a higher version in intrepid at this stage. I will probably add that to the stand-alone

---

### Post by tinybit on 2008-10-02
Ago, I suggest you browse the changelog first, and then make a decision.

The grub4dos-0.4.4 final will be released someday before 2008-10-15.

The current build of 2008-10-02 is stable enough.

---

### Post by ago on 2008-10-03
I think at this stage it is probably safer to keep the current version. I will use the new grub4dos in the stand-alone version available on the website. If CD users complain I will redirect to the new grub4dos zip

---

### Post by tinybit on 2008-10-03
That is Ok.

---

### Post by ago on 2008-10-06
tinybit, it would help to have a new cvs revision anyway...

---

### Post by jmambr on 2008-10-08
I have a Dell 700m notebook. When I try to install wubi, on the reboot, I get dropped into something called "Busybox". I have tried 8.10 beta as well as 8.04 with the same result. 

I would really like to drop Windows. Of all the ones I tried Ubuntu seems the best that I have tried. (At lease as a live CD)

---

### Post by crug77 on 2008-10-17
Hello, I have been having a similiar problem, I have been using ubuntu 8.04 for about a month and suddenly it does not boot up, all it does was go to the grub4dos prompt, then later on it just flashes "Starting cmain()" but goes no where. 

All I really need is a way to get my files off of ubuntu so that I can re-install it, but is there a way to get the files out? 

I used the dual boot wubi installation on windows Vista.

I would be very grateful if somebody could tell me if there is another way of seeing the files and getting them out in Vista without having to boot into ubuntu. 

Thanks,
Cesar

---

### Post by ago on 2008-10-17
Runc chkdsk /r and try again
To copy the old files, backup /ubuntu/disks/root.disk, then install wubi/ubuntu again, then mount root.disk using

mount -o loop /host/backup/root.disk /mnt

Now all your files are accessible under /mnt

---

### Post by crug77 on 2008-10-17
> **ago said:**
>  backup /ubuntu/disks/root.disk, then install wubi/ubuntu again, then mount root.disk using

mount -o loop /host/backup/root.disk /mnt

Now all your files are accessible under /mnt

I have looked in the ubuntu folder but could not find a folder called disks, nor could I find root.disk anywhere. All I have are folders called, docs, install, winboot. The folder docs has nothing in it, install only has a file called .fuse_hidden(bunch of numbers), and winboot has menu.lst, wubildr, wubildr.exe and wubildr.mbr 

I'm guessing that root.disk file would be where all my files are.

---

### Post by ago on 2008-10-18
> **crug77 said:**
> I have looked in the ubuntu folder but could not find a folder called disks, nor could I find root.disk anywhere. All I have are folders called, docs, install, winboot. The folder docs has nothing in it, install only has a file called .fuse_hidden(bunch of numbers), and winboot has menu.lst, wubildr, wubildr.exe and wubildr.mbr 

I'm guessing that root.disk file would be where all my files are.

look for a hidden folder called c:\found000 (set windows explorer to see hidden files)

---

### Post by crug77 on 2008-10-20
no couldn't find the folder found000, but there is a BOOTSECT.BAK on the c:\ not sure if that is relating to this.

---

### Post by AndreLeComte on 2008-11-02
Might it be possible that the '.fuse_hidden(bunch of numbers)' is actually the root.disk file?

---

### Post by AndreLeComte on 2008-11-04
1) In Windows I backed up this file D:\.Trash-0\files\ubuntu\disks\.fuse_hidden0000000400000003 to C:\ubuntu\disks\root.disk

2) Shutdown and loaded Ubuntu from the Ubuntu installation CD

3) Mounted the root.disk file using the following command in Terminal:
sudo mount -f -o loop /media/disk-1/ubuntu/disks/root.disk /mnt

4) Backed up all important data out of the /mnt/home folder

5) Now I will reinstall Ubuntu

---

