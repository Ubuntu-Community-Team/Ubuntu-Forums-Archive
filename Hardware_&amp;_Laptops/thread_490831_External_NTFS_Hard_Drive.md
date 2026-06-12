---
title: "External NTFS Hard Drive"
date: 2007-07-02
forum: Hardware &amp; Laptops
---

### Post by seismicmike on 2007-07-02
I have my laptop almost exactly the way I want it, with one exception. I have a 200GB external hard drive that I would love to use for backing up my files and such, but it's formatted as an NTFS. Now this ordinarily wouldn't be much of a problem if my life was Linux only - I'd just reformat it to ext3. However, I also have two Windows workstations which I frequent and I don't want to mess with the utility required for connecting ext3s in Windows (mostly b/c it keeps changing the drive letters of the external hard drive and any other usb media I insert - like sticks... not during my session, but between them... so my stick which is F today might be R tomorrow.... It's quite annoying)...

Anyway, the long and short of my question is: how can I mount my ntfs external read/write in Linux? I've got ntfs-3g installed as per the directions [here]("http://www.debianadmin.com/mount-your-widows-partitions-and-make-it-readwritable-in-ubuntu.html"), but I don't know really how to use it for external... I also don't know if it's ok to use fstab b/c the external isn't always connected to my laptop... Most of the information online I've found regarding this has been about accessing the windows partition on a dual boot machine, which I do not have (my laptop is 100% Linux)...

Any help? Thanks in advance :)

---

### Post by haftan on 2007-07-05
there is a slightly older post here called "network drives" and the command line that worked for me was:

sudo mkdir /media/PCNAME-C
sudo mount //PCNAME/C$ /media/PCNAME-C/ -o username=USERNAME,password=PASSWORD

---

### Post by lisati on 2007-07-05
Thank you - that might help me too on my desktop which has an external drive that I've nearly filled up using XP

---

### Post by augustose on 2008-03-16
does it solved the problem ??

> how can I mount my ntfs external read/write in Linux?

I have almost the same problem, Y have an external USB HD formated and used in Windows XP and in a month I changed my 4 family computers to Ubuntu Gusty  ( including 2 notebooks and 2 desktops ) now I realize that I completely lost access to that drive.

Do any one know how can I do to recover access to the data inside my external disk Without installing XP again.

thanks you in advance

---

### Post by yang83 on 2008-03-22
i would like to know too... i have mp3 and movie files saved on my NFTS HD. i would like to access it with Linux.  Anyone have a solution??????

---

