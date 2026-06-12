---
title: "Building Creative Webcam (PD1001) driver for Hoary"
date: 2005-04-17
forum: Hardware &amp; Laptops
---

### Post by NeTo on 2005-04-17
Hi! I have been running Ubuntu for a few months now, attempting to switch from windows.

I have solved several problems just by reading previous post in this forum, but now after researching I'm stuck.

I'm trying to use my Creative Webcam (it's a PD1001 model) in Hoary. I didn't realise it wasn't correctly setup until I tried GnomeMetting today. It always turned on at startup, so I thought it was automatically configured by Ubuntu . Well that sounded too good to be true, even Windows couldn't do that :p

I have been looking the net and I found this driver: [http://www.gaesi.org/~nmct/epcam/](http://www.gaesi.org/~nmct/epcam/) . The description sounds good, as I don't have to patch the kernel (especially considering I don't know how to).

So I downloaded the sources, and attemped to build them. I am very new at Linux and my programming knowledge only covers Visual Basic (shame on me). 

I tried running at terminal:
```
make --makefile=/home/neto/Desktop/epcam-src-0.7.1.tar.gz_FILES/Makefile
```
where */home/neto/Desktop/epcam-src-0.7.1.tar.gz_FILES* is the folder where I uncompressed the source.

I got as a result:
```

Remember: you must have read/write access to your kernel source tree.
make -C /lib/modules/`uname -r`/build SUBDIRS=/home/neto modules
make: *** /lib/modules/2.6.10-5-k7/build: No such file or directory.  Stop.
make: *** [default] Error 2
```
I installed linux-tree from synaptic because I though that was the kernel source tree the file was refering to. But I got the same message.

So after, that lenghty description my question is, how do I build the driver?
Or is there at least a nice site where I can guide on?

I feel too frightened to try patching the kernel to install the Jeroen Vreeken's driver mentioned on that site. Is it really as complicated as it sounds?

---

### Post by soul_rebel on 2005-04-18
```
sudo apt-get install linux-headers-2.6.10-5-k7
```

---

### Post by NeTo on 2005-04-18
Thank you a lot! I never though that was the package I needed. It was in fact the only one needed to compile the module.

Now, I could get the driver to work with gnomemeeting...

---

