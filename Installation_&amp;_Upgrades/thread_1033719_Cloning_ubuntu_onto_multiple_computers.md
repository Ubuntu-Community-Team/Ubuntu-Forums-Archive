---
title: "Cloning ubuntu onto multiple computers"
date: 2009-01-07
forum: Installation &amp; Upgrades
---

### Post by ITB Compsoc on 2009-01-07
I have 5 computers and they are all exactly the same. If I were to install Ubuntu 8.10 onto the first computer as well as install all the software and games I have for that PC, would I then be able to clone the drive and put all the same information on the other 4 computers? To me this seems like an easier way to install the same thing multiple times, and it wouldn't hurt to have a clone lying around to restore the PC to new if something went wrong.

Would it work? would it not? would it result in poor performance?

---

### Post by Coreigh on 2009-01-07
Yes it does work. I have done it. Don't even bother asking if it works for Window$ though.

If the hard drives are identical too you can clone them with dd
```
 sudo dd if=/dev/sda of=/dev/sdb
```

Where sda is the hard drive to be copied and sdb is the new one. (You put them both in one computer to do the cloning.)

You do have to watch out for the disk partition ID (UUID ?) in fstab I think these are unique to each disk partition. There are methods of correcting this using the LiveCD after the disk is cloned and installed. Or you can use /dev identification in the fstab, but I believe there is a good reason to use the proper UUID convention.

Find UUID with this:
```
sudo /sbin/dumpe2fs /dev/sdX | grep UUID
```
Replace sdX with the hard disk and partition you are looking for and it will tell you the UUID.
So if you want to know the UUID for the second partition on the first disk replace sdX with sda2.

---

### Post by bullium on 2009-01-07
You should be able to clone your linux machines without much fuss. The only thing you'll have to make sure you do is, when you bring a cloned machine up is to change it's hostname. g4u should work for the cloning part of your question. [http://www.feyrer.de/g4u/](http://www.feyrer.de/g4u/) I've used it before and it works very well.

---

### Post by albinootje on 2009-01-07
> **ITB Compsoc said:**
> I have 5 computers and they are all exactly the same.

I like the whole-diks cloning with CloneZilla.
See : [http://clonezilla.sf.net](http://clonezilla.sf.net)

If you want to try it, then check which hard disk is the smallest, and make the clone image to an usb-disk from that one.
With CloneZilla you can choose a few options for compression for the clone image.

---

### Post by edu1962 on 2009-01-07
I use Remastersys for backup of my installation.
You could install your first machine and then use Remastersys.

[http://maketecheasier.com/backup-ubuntu-with-remastersys/2008/12/22]("http://maketecheasier.com/backup-ubuntu-with-remastersys/2008/12/22")

                  There are two thing that Remastersys can do:

   1. To do a full system backup, including all installed applications, their settings and your personal data, to a live CD or DVD. You can use this live CD or DVD to restore your system or to install it in another computer. You can also bring it around and use it everywhere as a Live CD.
  
 2. To create a custom distributable copy of your current Ubuntu system and share it with your friends.

---

### Post by ITB Compsoc on 2009-01-08
Thanks lads loads of info there, i'll get back to you if I run into any problems.

---

### Post by kevin101ex on 2009-01-08
This post are quite old, lets talk about something else...

---

### Post by bullium on 2009-01-09
> **edu1962 said:**
> I use Remastersys for backup of my installation.
You could install your first machine and then use Remastersys.


This utility looks great! Who doesn't like a handy tool that was built for Ubuntu and apt-able (after a new repository was added). I'll definitely be giving this tool a shot myself.

---

