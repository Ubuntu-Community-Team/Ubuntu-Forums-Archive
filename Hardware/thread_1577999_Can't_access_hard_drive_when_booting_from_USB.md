---
title: "Can't access hard drive when booting from USB"
date: 2010-09-19
forum: Hardware
---

### Post by iBuck on 2010-09-19
So my windows installation pooped out on me and (of course) I don't have a backup of the important files that I need. I installed Ubuntu onto a USB flash drive to try and recover some of the files but when I try to access it from Places->Computer I'm greeted first with 

> Opening "160 GB Hard Disk: OS".

Followed by:

> Unable to mount location

DBus error org.freedesktop.DBus.Error.NoReply: Did not receive a reply. Possible causes include: the remote application did not send a reply, the message bus security policy blocked the reply, the reply timeout expired, or the network connection was broken.

The same thing happened when booting from the LiveCD. I can't access the hard drive in any programs (such as partitioning programs) either.


I'm running 10.04 (lucid) with Linux Kernel 2.6.32-24-generic on a Dell Inspiron 1525

---

### Post by dmurphy787 on 2010-09-19
Hi,
My understanding is that it only sets up a small temporary mount position on your existing drive to allow you to evaluate the Ubuntu System.  It may show the other mount(Drive) but it will not mount it unless you tell it to mount it, without mounting any other drive you cant access it.

---

### Post by thinkinhurtz on 2010-09-19
Not 100% sure if you can do this from the live cd or usb but give it a shot:

First open terminal then: 

$ adduser yourname 

then:

sudo chown -R username:computername /media/newvolume

hope that helps.

---

### Post by sidzen on 2010-09-19
Use puppy

---

