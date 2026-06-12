---
title: "USB Hard Disk completely unrecognized"
date: 2010-08-26
forum: Hardware
---

### Post by adamsu on 2010-08-26
Hello all, hope that someone can give me a suggestion for how to approach fixing this problem.

I have a 80Gb USB hard disk that has been on the shelf for about a year. Today when I plugged it in, the power light comes on and the disk starts to whir, but Ubuntu does not mount it. I checked in gparted, but it did not show up. I tried running 'dmesg' before and after plugging it in, and there is no difference in the output. (I also ran 'dmesg' before and after plugging in a working USB hard disk, just so I would know what it should look like.) I also ran 'testdisk', which did not show the disk as choice, only the computer's main hard drive.

I tried plugging the disk into different USB ports, on different computers, and even on a Windows computer, all with the same results- power light on, disk spinning, no recognition by the computer.

I am at a bit of a loss, as this appears to be a hardware problem, but I would like to hear suggestions from anyone as to other methods to try. 

Thanks in advance for any advice!

---

### Post by gordintoronto on 2010-08-27
It's a hardware problem. The most common hardware problem is a loose cable...

---

### Post by amac777 on 2010-08-27
Check syslog before and after you plug it in:

```
tail /var/log/syslog
```

About 10 seconds after plugging it in, try this command to see if the computer can detect it:

```
sudo fdisk -l
```

---

