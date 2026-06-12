---
title: "later the installation 3d, the notebook don't turn off!"
date: 2007-02-16
forum: Hardware &amp; Laptops
---

### Post by ledmauro on 2007-02-16
Hello, I'm Italian and so excuse you if I don't speak English very well. I'm a problem with Kubuntu. Yesterday I installed the 3D in the my ATI RADEON XPRESS 200M following this link:
[http://wiki.cchtml.com/index.php/Ubuntu_Edgy_Installation_Guide](http://wiki.cchtml.com/index.php/Ubuntu_Edgy_Installation_Guide)
I installed the driver 8.33.6, but now i can't  turn off or restart Kubuntu. In fact when I turn off or restart, listen him the music of turn off and later appears the black screen. The notebook remain ady and I am obligated to turn off by switch. Can you help me please?Thanks and by!

---

### Post by dannyboy79 on 2007-02-16
did you follow method 1 first? if so did you first blacklist the old fglrx? please post the output from
```
cat /etc/default/linux-restricted-modules-common
```

one of the important steps that it has at the bottom regarding your problem is this:
the file /etc/default/acpi-support  
you need to make sure you have this in it

POST_VIDEO=false 

just boot the machine to recovery mode, then make sure this is in there. if you can't veen get into the recovery mode, then at least boot to the command line and type in this code
```
sudo dpkg-reconfigure xserver-xorg
```
and just except all the defaults if you don't know the answer, this should get you back to normal NON-3d acceleratiion display, so that then you can go back to the guide and review the troubleshooting section.
 good luck

---

