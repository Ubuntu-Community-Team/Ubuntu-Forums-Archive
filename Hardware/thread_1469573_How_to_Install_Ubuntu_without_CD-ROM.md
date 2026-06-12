---
title: "How to Install Ubuntu without CD-ROM?"
date: 2010-05-02
forum: Hardware
---

### Post by Jr.Minnaar on 2010-05-02
...

---

### Post by Edward C on 2010-05-02
Is the USB stick plugged in when you go into the BIOS setup?

Is there a key you can press to bring up a boot device selector at boot time? Often F8 or F11 will bring up such a menu, and sometimes USB drives will show up there, but not in the BIOS setup screen.

If none of those helps, you're probably stuck with options like tracking down a USB CD-ROM drive, or taking out the hard-drive and putting it into another machine to perform the installation.

---

### Post by sakisds on 2010-05-02
It seems that you can't boot from a usb flash disk. Now you are kinda stranded... Maybe a BIOS update could enable usb support, but i have no idea if thats possible or how to do it.

---

### Post by Jr.Minnaar on 2010-05-02
...

---

### Post by relva on 2010-05-02
Try the pressing ESC, although i'm almost sure your laptop is unable to boot from usb drives :(

---

### Post by GuitarG20 on 2010-05-02
You could use wubi...wubi-installer.org

However, that will put it inside windows and not as a seperate partition...

---

### Post by Jr.Minnaar on 2010-05-02
...

---

### Post by groost on 2010-11-09
Would this work?
1. Boot a LiveCD of Linux which has Gparted
2. Repartition with Gparted, to make/format a bootable Linux partition
3. Download the ~700K Ubuntu .ISO as a file into the partition.
4. "Mount" the file as a virtual CD
5. Mount the Linux partition
6. dd (bit-by-bit) copy the VirtualCD to the Linux partition
7. make the Windows partition unbootable
8. reboot the Linux partition
9. install Linux overtop the Windows partition
10. run gparted finally to Join the partitions

...probably not.

---

