---
title: "Swaping Drive/Battery Crash"
date: 2006-08-15
forum: Hardware &amp; Laptops
---

### Post by gbadali on 2006-08-15
I have an Inspiron 600m running dapper drake and i got the extra battery that swaps with the DVD writer drive.  My problem is when i try and remove the DVD drive from the computer i get a hard and imediate crash, i have to hold the power button down to restart.  I dont know if i need to run some sort of unmount command before i do this, kind of new to linux myself, it was some thing that just worked in windows (one of the few).  I would appreciate any help.

---

### Post by kaens on 2006-08-15
What solved this for me - on a Thinkpad T30 here, is the module lt_hotswap.

You can get it [here](http://sourceforge.net/projects/lths/)

Now, for the installation - 

first, make sure you have the kernel sources and headers installed. You can accomplish that by ```
 cat /proc/version
apt-cache search linux | grep <whatever you got from the cat command>
apt-get install linux-source-<version number> linux-headers-<version number>

```

now you need to open up a terminal and cd to the directory that has the lt_hotswap archive in it. Then issue the commands:
```
 tar xzf lt_hotswap-0.3.6.tar.gz
cd lt_hotswap-0.3.6
make

```

Now if you ls, you should see a few more files in the directory, including 
lt_hotswap.ko. You can now ```
sudo modprobe lt_hotswap auto_eject=1
```

The auto-eject=1 means that it will unmount correctly when the release lever is pulled on the hotswap drive. 

The downside is that you will need to either issue that modprobe command every time you boot, or set up a script to do that. You can't load lt_hotswap on boot through adding it to /etc/modules - at least not on my Thinkpad - it borks the imb_acpi module, seemingly due to it being needed to be loaded after the ACPI modules, and udev not loading modules in a particular order....a bit over my head at the moment.

This may or may not work for you - but hopefully it will.

---

