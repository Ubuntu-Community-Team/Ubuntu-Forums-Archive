---
title: "Unable to mount USB, Error: device descriptor read/64, error -71"
date: 2010-02-15
forum: Hardware
---

### Post by shredder12 on 2010-02-15
Earlier I was having some real trouble with my USB.. It seemed to have messed up somehow. This was the output I got when I did ls in terminal. Take a look at this pic showing the output.

[http://i47.tinypic.com/mkj10.jpg](http://i47.tinypic.com/mkj10.jpg)

After that I tried to format it using gparted, but it wasn't able to unmount. It just kept on looping. So, I decided to go for manual formatting using mkfs. While doing that the command didn't return to prompt after a long time. So, thinking that it hanged I removed the USB in the process and since then I am unable to mount it. This is the output of syslog when I plug in the USB [http://paste.ubuntu.com/376872/](http://paste.ubuntu.com/376872/). 

After plugging it in, when I run
```
sudo fdisk -l
```
after listing out the hard drive partitions, it doesn't return to the prompt until I either remove the USB or after sometime(may be timeout).

And this is the output of syslog when I remove it, after not getting recognised [http://paste.ubuntu.com/376870/](http://paste.ubuntu.com/376870/)

I am not sure what the issue really is but someone suggested that I might be dealing with a broken/corrupted file system. any suggestions to fix things?

---

