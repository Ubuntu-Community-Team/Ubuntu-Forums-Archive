---
title: "How do I find my system specs?"
date: 2007-01-03
forum: Hardware &amp; Laptops
---

### Post by st0ney on 2007-01-03
I am trying to find a way to tell me what my system specs are in ubuntu.  This is a friends system but he has no idea what his specs are and he is interested it selling it to me.  I want to know things like, proc speed, ram, video card info, HDD info.  I used to used Belarc in my windows daze but I don't know of a program that does the same in linux.  Please help and advise.  Thanks.

---

### Post by meng on 2007-01-03
Processor speed and RAM should show up at boot time, reported by the BIOS. Video card would probably be reported by:
lspci
(if it is PCI card)

and hard disk info and partition table by:
sudo fdisk -l
(l as in Larry)

---

### Post by taurus on 2007-01-03
You can ask him about the brand new and model of the machine and check it with the manufacturer's site.  

Unless he already has Linux running on it...

```
sudo fdisk -l  <-- harddrive
free  <-- amount of RAM
lspci  <-- graphic card, sound card, etc.
lshw  <-- everything about the mobo
```

---

### Post by kebes on 2007-01-03
Some useful commands in Linux to tell you about the system:

Find out version of Linux and kernel:
uname -a
cat /proc/version
dmesg | grep "Linux version"

Find out about size of hard drive partitions:
df

Find out about processor/memory
cat /proc/cpuinfo
cat /proc/meminfo

Find out about installed pci hardware (may need to run as root):
lspci
scanpci


These will give you a bunch of information... but of course interpreting it will be somewhat difficult. Reading "cpuinfo" and "meminfo" is fairly straightforward (and there are guides on the net for interpreting these things). Getting a list of devices is usually overwhelming unless you know what you're looking for.

Also, watching the screen during bootup usually gives lots of tidbits about the hardware being installed (although it usually goes by too fast!). Despite all this, I usually have to open up the case and read the product number straight off each piece if I really want to know what's in there!

Hope that helps!

---

