---
title: "Privleges and Hard Drive Installation"
date: 2010-03-02
forum: Hardware
---

### Post by xplaner800 on 2010-03-02
I have successfully formatted and installed two additional internal hard drives in my computer. However, the first time (after booting) that I try to access one, I keep getting a message asking me to enter my password and click "Authenticate".

I don't like this :) How can I configure it so that I don't need to continue to enter my password and authenticate after every boot. 

My system recognizes both drives just fine and I am able to read and write to both.

Any assistance is appreciated,

Patrick

Using Ubuntu 9.10 on Dell XPS

---

### Post by cjhabs on 2010-03-02
Are they encrypted?

---

### Post by xplaner800 on 2010-03-02
No they are not encrypted. When I right-click and select Encrypt... it says that no encryption keys were found and will start a program to let me create and key or import one.
Is this important and/or required. i.e. Will creating a key, eliminate my authentication issue?

Please excuse my stupidity as I am a noob to Ubuntu and linux in general.

Thanks,

Patrick

---

### Post by cjhabs on 2010-03-03
No, but if they were that might explain why you are being asked to authenticate before accessing it.

Are these drives being mounted in fstab? If not, add them to /etc/fstab and that should resolve the problem. Do "man fstab" for details. If you are stuck, post here.

---

### Post by xplaner800 on 2010-03-03
Well, I did make those entries in fstab and the entries are below

/dev/sda1 / ext3 defaults 0 1
/dev/sda5 swap swap sw 0 0
/dev/sdb  /media/sdb ext3 defaults 0 0
/dev/sdc  /media/sdc ext3 defaults 0 0

I made directories for the mount point etc and did sudo mount -a and got the following entries.

patrick@patrick-desktop:~$ sudo mkdir /media/sdb
patrick@patrick-desktop:~$ sudo mkdir /media/sdc
patrick@patrick-desktop:~$ sudo mount -a
mount: wrong fs type, bad option, bad superblock on /dev/sdb,
       missing codepage or helper program, or other error
       In some cases useful info is found in syslog - try
       dmesg | tail  or so

mount: wrong fs type, bad option, bad superblock on /dev/sdc,
       missing codepage or helper program, or other error
       In some cases useful info is found in syslog - try
       dmesg | tail  or so

I formatted them using the ext3 fs, so I'm not sure what the problem still is??

Any suggestions?

Patrick

---

### Post by cjhabs on 2010-03-04
Can you post the results of:
```

sudo fdisk -l

```

How did you prepare the disk for use - fdisk then mkfs.ext3?

---

