---
title: "Help. Can't install Jaunty"
date: 2009-05-24
forum: Installation &amp; Upgrades
---

### Post by twistedblais1 on 2009-05-24
trying to install jaunty. I setup the partitions, and start the installation and a get a input/output error during read on /dev/sda. Any help is greatly appreciated.

---

### Post by LinuxRules1 on 2009-05-24
Your CD or Hard Drive might be bad, or the iso file that you burned to the CD might be corrupt.

---

### Post by twistedblais1 on 2009-05-24
Can't be the cd it's the official from Ubuntu. Is there any way to fix the hard drive if that's the problem?

---

### Post by LinuxRules1 on 2009-05-24
You might have to replace the hard drive. It could also be your CD-ROM drive. You can test the hard drive by downloading the Ultimate Boot CD. You can download it by going to this website [http://www.ultimatebootcd.com/download.html](http://www.ultimatebootcd.com/download.html)

---

### Post by tommcd on 2009-05-24
> **twistedblais1 said:**
> Can't be the cd it's the official from Ubuntu. Is there any way to fix the hard drive if that's the problem?
Just to rule out a bad CD as the source of the problem, boot up the Ubuntu CD and choose the option "check disc for defects". If it passes, then the disc is ok. If it does not pass, then you will need to dowload the iso and burn a new CD.

---

### Post by twistedblais1 on 2009-05-25
I figured out the problem. I was trying to install on a Acer laptop and apparently the hard drive doesn't support ext3 or ext4 format. I changed the format to XFS and it's fine now. everything is working great. Now if only logmein supported linux.

---

### Post by tommcd on 2009-05-25
> **twistedblais1 said:**
> I figured out the problem. I was trying to install on a Acer laptop and apparently the hard drive doesn't support ext3 or ext4 format. I changed the format to XFS and it's fine now. everything is working great. Now if only logmein supported linux.
What Acer laptop is this? I have never heard of a hard drive not supporting ext3, but working with XFS. I have been installing the last 4 or 5 versions of Ubuntu on my Acer laptop. I use ext3 and have never had a problem. I have not yet tried ext4.

---

### Post by lisati on 2009-05-25
> **twistedblais1 said:**
> Can't be the cd it's the official from Ubuntu.

Sure? I have one "official" Kubuntu CD that won't boot and one that does.

---

