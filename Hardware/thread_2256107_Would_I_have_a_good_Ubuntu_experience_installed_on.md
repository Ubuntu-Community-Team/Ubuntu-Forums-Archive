---
title: "Would I have a good Ubuntu experience installed on this Pen Drive?"
date: 2014-12-09
forum: Hardware
---

### Post by tiger6 on 2014-12-09
I tried to dual boot Windows and Ubuntu on the same hard drive, but Ubuntu installer just would not detect the windows installation. So I decided to use a Pen Drive to install Ubuntu in. I'm planning to purchase a USB 3.0 pen drive that has practically 90 MBps sequential read and 15 MBps sequential write speeds. Will this speed be enough to give a smooth Ubuntu experience? (I'm concerned about the write speed)

I've decided to use non-journaling file system like ext2 and not use swap partitions so as to minimize the read-write cycles, thereby increasing performance. 

Should I go and buy this pen drive for the purpose? Or do I need a much faster one?

Thank you.

---

### Post by tiger6 on 2014-12-09
[IMG]https://images-na.ssl-images-amazon.com/images/I/614Lm+n2AfL._SL1600_.jpg[/IMG]

---

### Post by QIII on 2014-12-09
It might be better if that graphic were interpreted, tiger6.  Please don't leave that to the OP to sort out.

At any rate -- I have been very happy with performance with USB 3.0 thumb drives, although there is some speed hit.  I have several thumb drive installs that I have used for quite some time.  However, be sure to make regular backups as those things do fail sometimes.

As far as format, I would still go with ext4 if you have a quality drive.  A cheapie may not be up to the task.  If you have enough memory and don't plan to hibernate, avoiding swap might be a good idea.

---

### Post by sudodus on 2014-12-10
Have a look at the following links

[https://help.ubuntu.com/community/Installation/FromUSBStick#Prerequisites](https://help.ubuntu.com/community/Installation/FromUSBStick#Prerequisites)

[Link to USB 3.0 Flash Drive Speed Tests]("http://usb.userbenchmark.com/")

[Link to USB 2 and USB 3 speed tests for installers]("http://ubuntuforums.org/showthread.php?t=2196858&p=12907085#post12907085")

I have good experience of Sandisk Extreme for installed operating systems and persistent live systems.

-o-

Installed systems and persistent live systems benefit from good read/write speed of small files (tested by *4k* and *4k qd32* in your screendump picture). Standard live systems (without persistence) work well also with slower flash and depend more on reading of the single big squashfs file that is expanded into RAM.

---

### Post by C.S.Cameron on 2014-12-10
I'm not sure where the idea that flash drives quickly burn out comes from, but if you do the math, based on a minimum lifetime of 10000 writes:

10000 writes x 64 GB / 15 MB/s = 42666666 sec or 1481 eight hour days, but you will never write to a pendrive full time during a work day.

Go with an ext4 filesystem.

Good info in the previous posts.

---

