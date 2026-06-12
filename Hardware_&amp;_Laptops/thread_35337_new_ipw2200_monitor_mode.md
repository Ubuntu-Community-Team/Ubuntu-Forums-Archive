---
title: "new ipw2200 monitor mode"
date: 2005-05-18
forum: Hardware &amp; Laptops
---

### Post by Technoviking on 2005-05-18
The new ipw2200 driver has monitor mode built in. But when I try to use it, it fails.

```

dbasinge@pheonix: ~ $ sudo iwconfig eth1 mode monitor
Error for wireless request "Set Mode" (8B06) :
    SET failed on device eth1 ; Invalid argument.

```

Any ideas?
Mike

---

### Post by Amarack on 2005-05-18
According to [http://www.kismetwireless.net/documentation.shtml#readme](http://www.kismetwireless.net/documentation.shtml#readme) monitor mode does not work with ipw2200 right now because of the driver. If this is not so someone please correct me.

---

### Post by beefsprocket on 2005-05-19
Not sure on this one (my driver, after rebooting, won't load or recompile now) but have you tried  using 2 as the mode when you load the module i.e. "modprobe ipw2200 mode = 2" (or mode 2, not sure which)? This sets the kernel module in monitor mode according to the documentation.

---

### Post by kyle01 on 2005-05-23
I installed the new ipw2200 driver as described here:
[http://www.ubuntuforums.org/showthread.php?t=26623](http://www.ubuntuforums.org/showthread.php?t=26623)

Now I can do

iwconfig eth1 mode monitor

without any problems. Ethereal now captures packets in monitor mode.
However, I only get beacon packets and have not yet seen any "real" traffic, although there are several wlans around here...

---

### Post by goudiemark on 2005-05-23
[QUOTE=juicewvu]when trying to follow this tutorial i recieve the following error(s) when trying to compile the ipw2200 driver:

```

make -C /lib/modules/2.6.10-5-386/build SUBDIRS=/home/jcsmith/ipw2200-1.0.3 MODVERDIR=/home/jcsmith/ipw2200-1.0.3 modules
make: *** /lib/modules/2.6.10-5-386/build: No such file or directory.  Stop.
make: *** [modules] Error 2

```

I tried making the /lib/modules/2.6.10-5-386/build directory as it infact does not exist, after which I recieve the following error(s):
```

make -C /lib/modules/2.6.10-5-386/build SUBDIRS=/home/jcsmith/ipw2200-1.0.3 MODVERDIR=/home/jcsmith/ipw2200-1.0.3 modules
make[1]: Entering directory `/lib/modules/2.6.10-5-386/build'
make[1]: *** No rule to make target `modules'.  Stop.
make[1]: Leaving directory `/lib/modules/2.6.10-5-386/build'
make: *** [modules] Error 2

```
I'm kind of stuck here, do i need to copy the source files to the /lib/modules/2.6.10-5-386/build directory before trying to compile?


-Juice[/QUOTE]


Im getting the same error and the reply to this post was to update the kernel headers which I think i did and create a symlink which i dont know how to do, i was hoping you could help me.

---

### Post by Legion on 2005-05-24
[QUOTE=kyle01]I installed the new ipw2200 driver as described here:
[http://www.ubuntuforums.org/showthread.php?t=26623](http://www.ubuntuforums.org/showthread.php?t=26623)

Now I can do

iwconfig eth1 mode monitor

without any problems. Ethereal now captures packets in monitor mode.
However, I only get beacon packets and have not yet seen any "real" traffic, although there are several wlans around here...[/QUOTE]
 Read the mailing lists - monitor mode ain't finished.

---

### Post by apu95 on 2005-05-28
[QUOTE=Legion]Read the mailing lists - monitor mode ain't finished.[/QUOTE]

Did *you* read the mailing lists? Monitor works. You gotta update the drivers and firmware. You can even use Kismet-devel and sniff the packets (users have confirmed it works). Personally I haven't gotten it to work, I get the same message:

Error for wireless request "Set Mode" (8B06):
                  SET failed on device eth0 ; Invalid Argument

I have already opened packets that were captured by the ipw2200 on another laptop, worked very well.

---

