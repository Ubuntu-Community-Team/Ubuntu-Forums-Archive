---
title: "Wipe Hard Drive"
date: 2008-11-10
forum: General Help
---

### Post by terrance on 2008-11-10
I am on an Ubuntu computer now, and I want to wipe the hard drive of a computer with a destroyed operating system on it. How would I easily prepare a usb stick on this Ubuntu computer that I could use to completely erase the hard drive on the messed up computer? I've tried dban and killdisk, but then found out that they only work with windows.

---

### Post by -Zeus- on 2008-11-10
well, you can boot to a live cd, open a console, and try this:

[COLOR="Red"]DANGER!!![/COLOR]```
i=0; while [i -lt 3] do dd if=/dev/urandom of=/dev/sda bs=1024; dd if=/dev/zero of=/dev/sda bs=1024; i=$((i+1)); done
```

This will repeat filling the drive with 0s and random data 3 times

---

### Post by caljohnsmith on 2008-11-10
If you install linux to your USB stick, you could wipe the entire HDD with:
```
sudo dd if=/dev/zero of=/dev/sdX bs=10M conv=notrunc
```
And change sdX to the drive you want to wipe. But really you only need to wipe the MBR (Master Boot Record) to make the drive look entirely unformatted and blank:
```
sudo dd if=/dev/zero of=/dev/sdX count=1
```
That's really all it takes, and then you can reformat/repartition the HDD as you please.

---

### Post by gpsmikey on 2008-11-10
If you just want to start over, basically, you can just partition the disk the way you want it and install (delete any existing partitions first) - use something like Gparted etc.

If you really want to erase the disk before starting over due to sensitive material on the disk, there are a number of utilities out there - this one "copywipe" from TerabyteInc is free and you can download the dos/bootable CD version from there.  You can get it at [http://www.terabyteunlimited.com/copywipe.php](http://www.terabyteunlimited.com/copywipe.php)
It gives you the option to completely destroy any information on the disk.

**[COLOR="Red"]WARNING -- recognize that with any of the mentioned methods, there is NO going back and if you take aim at the wrong disk, you are as they say "up the creek sans paddle" !!![/COLOR]**

mikey

---

