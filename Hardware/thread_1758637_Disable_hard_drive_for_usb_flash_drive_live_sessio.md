---
title: "Disable hard drive for usb flash drive live session"
date: 2011-05-14
forum: Hardware
---

### Post by oldmankit on 2011-05-14
Hello,

I'm trying to get the most out of my battery for occasions when I go to coffee shops/restaurants to do some writing.  I only need to use lyx, and don't even need the internet.

There are several distributions based on ubuntu which are aimed at low power, including wattos and lubuntu.  I would like to install one of those onto the flash drive.

What would be super-awesome in terms of power is a way to not use the hard drive at all.  Before I set-off for my writing I could copy the single file that I need onto the flash drive, using  my regular install of ubuntu.  Easy.

I've searched around but no solutions are clear.  People suggest doing it from the BIOS, but my BIOS is crappy and has no such options.  It seems there are kernel arguments (or something like that) which can turn hard drives off, but that sounds really hard...I don't know how to compile a kernel, or even if that's what I'd need to do.

:confused:

---

### Post by mikewhatever on 2011-05-14
I think the easiest way to achieve disk power saving would be with hdparm. For example, the following command will put /dev/sda in an aggressive power saving mode after 60 seconds of idle time:
```
sudo hdparm -B 1 -S 12 /dev/sda
```

Look at 'man hdparm' for more info.

---

### Post by oldmankit on 2011-05-21
> **mikewhatever said:**
> I think the easiest way to achieve disk power saving would be with hdparm. For example, the following command will put /dev/sda in an aggressive power saving mode after 60 seconds of idle time:
```
sudo hdparm -B 1 -S 12 /dev/sda
```

Look at 'man hdparm' for more info.
Thank you very much for that.  I will try it.

---

