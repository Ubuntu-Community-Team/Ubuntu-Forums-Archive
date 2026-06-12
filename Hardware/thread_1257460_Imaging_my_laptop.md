---
title: "Imaging my laptop"
date: 2009-09-03
forum: Hardware
---

### Post by smoothcne on 2009-09-03
I have a perfect working image of 7.1 on my HP nc6320 that won't update anymore. I want to upgrade to the latest version so I can install HamLibs, but I don't want it to wipe out all of my already installed packages and repositories (although I know it prolly will). How can I tell my laptop to make an image of itself and burn it to a DVD? One that would be easy to restore?
Can someone advise me please?
Thanks,
JJ N5MNX

---

### Post by aysiu on 2009-09-04
Just do a dist-upgrade. You won't lose your packages--they'll just be updated.
[http://www.ubuntu.com/getubuntu/upgrading](http://www.ubuntu.com/getubuntu/upgrading)

---

### Post by aysiu on 2009-09-04
Just do a dist-upgrade. You won't lose your packages--they'll just be updated.
[http://www.ubuntu.com/getubuntu/upgrading](http://www.ubuntu.com/getubuntu/upgrading)

---

### Post by smoothcne on 2009-09-04
Many THANKS aysiu! 
I'll give that a try!
JJ

---

### Post by smoothcne on 2009-09-06
Ok, I got the Distro Update to 8.04 Hardy!
What technique can I use to make a good image of it to save off to a DVD or another system? 

How do folks move images from system to system on servers and workstations?

JJ

---

### Post by aysiu on 2009-09-06
Remastersys:
[http://www.psychocats.net/ubuntu/remastersys](http://www.psychocats.net/ubuntu/remastersys)

---

### Post by aysiu on 2009-09-06
Remastersys:
[http://www.psychocats.net/ubuntu/remastersys](http://www.psychocats.net/ubuntu/remastersys)

---

### Post by JC Cheloven on 2009-09-06
If you plan to (eventually) restore on the same exact hardware, you can save your partition(s) using some backup software. I use FSArchiver, which lets you restore to a partition of different type/size if needed. The easiest way to use it is perhaps to burn systemrescuecd (google for it), in which it comes.

Note: fsarchiver works for unix/linux filesystems only, ie no ntfs.

---

