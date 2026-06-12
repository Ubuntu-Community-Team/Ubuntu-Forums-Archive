---
title: "Toughbook Touchscreen psmouse: Unknown symbol"
date: 2009-02-22
forum: Hardware
---

### Post by dieselpower on 2009-02-22
Toughbook CF-72 Touchscreen.

There is an error in the kernel source for the psmouse module, see here, [https://bugs.launchpad.net/ubuntu/+bug/300868](https://bugs.launchpad.net/ubuntu/+bug/300868).

So what I'm trying to do is compile only the psmouse module following these instructions, [http://www.linlap.com/wiki/panasonic+toughbook+72](http://www.linlap.com/wiki/panasonic+toughbook+72)

When I issue "make", I get this,
```
root@lap:~/mouse# make
make -C /lib/modules/`uname -r`/build M=`pwd` modules
make[1]: Entering directory `/usr/src/linux-headers-2.6.28-8-generic'
make[2]: Circular /root/mouse/psmouse.o <- /root/mouse/psmouse.o dependency dropped.
  CC [M]  /root/mouse/psmouse-base.o
  CC [M]  /root/mouse/synaptics.o
  CC [M]  /root/mouse/alps.o
  CC [M]  /root/mouse/lifebook.o
  CC [M]  /root/mouse/trackpoint.o
  CC [M]  /root/mouse/logips2pp.o
  LD [M]  /root/mouse/psmouse.o
  Building modules, stage 2.
  MODPOST 1 modules
WARNING: "hgpk_detect" [/root/mouse/psmouse.ko] undefined!
WARNING: "elantech_detect" [/root/mouse/psmouse.ko] undefined!
WARNING: "elantech_init" [/root/mouse/psmouse.ko] undefined!
WARNING: "hgpk_init" [/root/mouse/psmouse.ko] undefined!
  CC      /root/mouse/psmouse.mod.o
  LD [M]  /root/mouse/psmouse.ko
make[1]: Leaving directory `/usr/src/linux-headers-2.6.28-8-generic'
```

When I try to insert my module, I get
```
root@lap:~/mouse# modprobe psmouse
FATAL: Error inserting psmouse (/lib/modules/2.6.28-8-generic/kernel/drivers/input/mouse/psmouse.ko): Unknown symbol in module, or unknown parameter (see dmesg)
```

and so dmesg says,
```
[32235.248156] psmouse: Unknown symbol hgpk_init
[32235.248647] psmouse: Unknown symbol elantech_init
[32235.250938] psmouse: Unknown symbol elantech_detect
[32235.251288] psmouse: Unknown symbol hgpk_detect
```

This is just a little beyond me here. I really don't want to compile a whole kernel here. It's probably something stupidly simple I'm missing!

---

### Post by bnr on 2009-02-24
I have not tried this on jaunty, so I can only make a few guesses. The four warnings appear to reflect a undefined variable, this either means that a source file reference is missing from the make file, or that one of the source files is missing some information.

In the first case; look at the original makefile from the source and see if it associates any other files with the psmouse.o file. All files associated with psmouse.o in the original makefile will need to be in your new one.

The second case could happen if you where mixing source files (or maybe because jaunty is still beta). Make sure that all the files are from the same place, either Ubuntu Repos or Kernel.org, not both. I'd just go with the repos myself.

Good luck with jaunty, and report back your results. I tend to wait a few weeks (or months) after the official release from ubuntu. Every time I don't wait, I end up regretting it.

---

### Post by bnr on 2009-06-08
I got this working on jaunty, you need to add;
    elantech.o hgpk.o
to the make file.
 the fix is at;
[http://www.linlap.com/wiki/panasonic+toughbook+72]("http://www.linlap.com/wiki/panasonic+toughbook+72")

or download the automated script here;
[http://1bnr.wordpress.com/2009/05/28/cf-72-touchscreen-script-1-0/#more-166]("http://1bnr.wordpress.com/2009/05/28/cf-72-touchscreen-script-1-0/#more-166")

---

