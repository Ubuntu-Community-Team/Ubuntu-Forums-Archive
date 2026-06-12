---
title: "slow hdd"
date: 2008-06-23
forum: Hardware
---

### Post by coffee on 2008-06-23
Hello,

I recently upgraded to 8.04, and now I am having slow boots due to "waiting for root" during boot.

This is what I get from hdparm on my root drive: 

```
dad@dads-den:~$ sudo hdparm /dev/sda
sudo: unable to resolve host dads-den

/dev/sda:
 IO_support    =  0 (default) 
16-bit)
 HDIO_GET_UNMASKINTR failed: Inappropriate ioctl for device
 HDIO_GET_DMA failed: Inappropriate ioctl for device
 HDIO_GET_KEEPSETTINGS failed: Inappropriate ioctl for device
 readonly      =  0 (off)
 readahead     = 256 (on)
 geometry      = 4865/255/63, sectors = 78165360, start = 0

```

---

### Post by sdennie on 2008-06-23
What is the output of /etc/hosts?  My guess is that this thread will fix the problem: [http://ubuntuforums.org/showthread.php?t=723361](http://ubuntuforums.org/showthread.php?t=723361)

---

### Post by coffee on 2008-06-23
I booted with the 2.6.22-15-generic kernel and all was good.

thank you

---

