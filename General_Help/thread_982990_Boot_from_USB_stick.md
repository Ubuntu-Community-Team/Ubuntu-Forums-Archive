---
title: "Boot from USB stick"
date: 2008-11-15
forum: General Help
---

### Post by sprybry on 2008-11-15
I have made several attempts(tutorials) at loading Ubuntu 8.10 on a usb stick so that I can boot from it, but have had no success.  I know that someone out there has done this, I just cannot find the correct process.  What I want to be able to do is load Ubuntu 8.10 on to a USB stick and have it boot normally just as if I installed in on a hard drive.  I am not interested in the USB persistant method because it takes way too long to boot with the live CD method.  Any help would be appreciated

---

### Post by Bigneil on 2008-11-15
Have you tried altering the boot order in BIOS?

---

### Post by sprybry on 2008-11-15
Yes. booting from the USB is not a problem.  The problem is, it boots just like booting from a live CD which takes 5 to 7 minutes to boot up.  I want to be able to boot in a minute or 2 just like booting from a disk.

---

### Post by Mardoct909 on 2008-11-15
Try patience.

Or try getting the alternate install CD. It isn't a liveCD, so it needs less time and resources. When you download, look for a little checkbox asking if you want the alternate CD image.

---

### Post by Bigneil on 2008-11-15
There must be a bottle neck somewhere.... i know that it takes me a lot longer to transfer files from my pc to an external drive than it does to transfer from internal drive to internal drive. Perhaps there is little you can do to speed up booting from usb?? Why not not set up a dual boot where you can decide which operating system you want at start up?  it would be a much quicker?

---

### Post by sprybry on 2008-11-15
Yes that is true that making a dual boot would be fast.  However I am experimenting to see if I can build a solid state linux system without any hard drive which is why I want it to boot from the USB.  I have seen several tutorials and have tried some of them, but when booting, I get the options, to boot from live cd, install or whatever.  I just want to boot like I would be as if I loaded Ubuntu or Kubuntu on a hard drive.

---

### Post by Npl on 2008-11-15
then install it directly like you would on a HDD and dont use any scripts that build a "Live USB Stick" - cause thats what you have got. Just make sure grub gets installed on your stick and nowhere else.

---

### Post by C.S.Cameron on 2008-11-15
You can do a Full install to flash drive using the same method as to internal HDD. Boot from Live CD or Live USB and click install on the desktop.
(I suggest disabling your internal HDD first so you don't mess up it's MBR).
When you get to partitioning you can choose any of the three methods, use full disk, use remaining space or manual.
If you use remaining space or manual you can leave a little FAT32, (on the left side), so windows can see the flash drive.
For manual partitioning on a 4G drive, (minimum), 500 MB FAT32, 1 GB /home and 2.5 GB root, (/), is a good starting point and can be adjusted later using gparted.
Home and root can be formatted as ext3 or reiserfs.
This should make a flash drive that works just like a HDD install only a little slower at times.

---

### Post by ugm6hr on 2008-11-15
> **sprybry said:**
> Yes that is true that making a dual boot would be fast.  However I am experimenting to see if I can build a solid state linux system without any hard drive which is why I want it to boot from the USB.  I have seen several tutorials and have tried some of them, but when booting, I get the options, to boot from live cd, install or whatever.  I just want to boot like I would be as if I loaded Ubuntu or Kubuntu on a hard drive.

As others have said - you don't need USB specific tutorials.  A USB Flash drive can be treated like a regular HD (and is faster).

Be aware that Flash drives have a lower number of read/writes than a regular HD, so it would be best to avoid including a swap partition.

---

### Post by sprybry on 2008-11-16
Ahhhhh.  I feel silly now.  Installing to the UDB drive worked perfect.  Thanks

---

