---
title: "Read/Write HFS Drive"
date: 2008-11-26
forum: Hardware
---

### Post by timjm25 on 2008-11-26
So far I love Ubuntu. I have not touched Windows in quite a while!!

I have a quick question. There is an IOMEGA drive that I have which is Mac OS Extended (I guess HFS+ in other words) that I am trying to get to accept read / write functions.

I have tried the HFS tools, but say that I cannot perform functions since the external drive is a "directory".

When I use the x-window function XHFS, it says that permission is denied.

I also tried to find a user manual for the HFS tools, but did not find anything.

Thanks in advance for your assistance.

---

### Post by ElectricBlue on 2008-12-18
First you need to install hfsutils. Once these are installed there should be a number of tools for mounting, reading, writing etc to an hfs volume. 
Then you need to mount the volume as root using
```
sudo mount -t hfsplus /dev/(your drive) /path/to/mount
```

This is where I get a little fuzzy because I have a similar but more complex issue. I am trying to automount an external drive using the fstab.

After some research, it turns out that hfsutils cannot mount a journalled HFS+ filesystem with write access. 

My search continues....

---

