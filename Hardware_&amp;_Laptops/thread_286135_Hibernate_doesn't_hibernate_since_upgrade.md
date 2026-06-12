---
title: "Hibernate doesn't hibernate since upgrade"
date: 2006-10-27
forum: Hardware &amp; Laptops
---

### Post by Falcon.Geek on 2006-10-27
Ever since i upgraded to 6.10 and installed beryl.  Hibernate no longer runs.

Occasionally it gives me an error saying it cannot find swap device.  So i checked to see if i could find the swap device.

The following is what i see in GParted

/dev/sda1    /media/sda1    39.1Mb  7.48Mb    fat16
/dev/sda2    /media/sda2    43.9Gb  17.3Gb    NTFS
/dev/sda3    /              28.1GB  4.87Gb    EXT3
/dev/sda4                   1004.6Mb          Unknown

if tried redsetting sda4 as linux-swap, just went back to unknown.  I would really like to hibernate,

Let me know what to try

Thanks

---

### Post by zgornel on 2006-10-29
> **Falcon.Geek said:**
> Ever since i upgraded to 6.10 and installed beryl.  Hibernate no longer runs.

Occasionally it gives me an error saying it cannot find swap device.  So i checked to see if i could find the swap device.

The following is what i see in GParted

/dev/sda1    /media/sda1    39.1Mb  7.48Mb    fat16
/dev/sda2    /media/sda2    43.9Gb  17.3Gb    NTFS
/dev/sda3    /              28.1GB  4.87Gb    EXT3
/dev/sda4                   1004.6Mb          Unknown

if tried redsetting sda4 as linux-swap, just went back to unknown.  I would really like to hibernate,

Let me know what to try

Thanks
Same happened to me. I reformated the swap partition (GParted) and worked afterwords. Try removing the swap partition and recreating it. If it still does not work create your own swap file on the ext3 partition ([http://www.redhat.com/docs/manuals/linux/RHL-8.0-Manual/custom-guide/s1-swap-adding.html](http://www.redhat.com/docs/manuals/linux/RHL-8.0-Manual/custom-guide/s1-swap-adding.html))

---

### Post by Falcon.Geek on 2006-11-01
Nope, my partition now seems to stay there but when i try to hibernate it just says that it cannot find the swap space.

---

### Post by zgornel on 2006-11-01
> **Falcon.Geek said:**
> Nope, my partition now seems to stay there but when i try to hibernate it just says that it cannot find the swap space.
Before hibernating, try *$ sudo swapon -a*

---

### Post by Falcon.Geek on 2006-11-02
Alright i finally got it working!!! it seems I had two problems

1) swap partition too small
2) had to run
  sudo update-initramfs -c -k `uname -r`

And now it works

---

