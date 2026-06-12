---
title: "Application Panel and brightness control on Fujitsu T4215"
date: 2007-02-06
forum: Hardware &amp; Laptops
---

### Post by atlanta800 on 2007-02-06
First off the Application Panel. I know there is a driver specifically for these tablets: [fjbtndrv]("http://jan.rychter.com/software/fjbtndrv/fjbtndrv.ucw"). I've gotten this to work, but the functions are useless to me (up/down, enter) what I truly care about is the rotation button and being able to tie it to xrandr. [apanel]("http://apanel.sourceforge.net/") is supposed to be another driver for it. However, whenever I try to compile this I get the following output:
```
$ sudo make KERNEL_SOURCE=/usr/src/linux-headers-2.6.17-10-generic/
make -C /usr/src/linux-headers-2.6.17-10-generic/ SUBDIRS=`pwd` modules
make[1]: Entering directory `/usr/src/linux-headers-2.6.17-10-generic'
  CC [M]  /home/atlanta800/apanel-linux-1.4/linux/apanel.o
/home/atlanta800/apanel-linux-1.4/linux/apanel.c:89: error: unknown field &#8216;owner&#8217; specified in initializer
/home/atlanta800/apanel-linux-1.4/linux/apanel.c:89: warning: initialization makes integer from pointer without a cast
/home/atlanta800/apanel-linux-1.4/linux/apanel.c:91: error: unknown field &#8216;name&#8217; specified in initializer
/home/atlanta800/apanel-linux-1.4/linux/apanel.c:91: warning: initialization makes integer from pointer without a cast
/home/atlanta800/apanel-linux-1.4/linux/apanel.c:93: error: unknown field &#8216;flags&#8217; specified in initializer
/home/atlanta800/apanel-linux-1.4/linux/apanel.c:93: error: &#8216;I2C_DF_NOTIFY&#8217; undeclared here (not in a function)
/home/atlanta800/apanel-linux-1.4/linux/apanel.c: In function &#8216;apanel_attach&#8217;:
/home/atlanta800/apanel-linux-1.4/linux/apanel.c:604: error: &#8216;struct i2c_algorithm&#8217; has no member named &#8216;id&#8217;
/home/atlanta800/apanel-linux-1.4/linux/apanel.c:604: error: &#8216;I2C_ALGO_SMBUS&#8217; undeclared (first use in this function)
/home/atlanta800/apanel-linux-1.4/linux/apanel.c:604: error: (Each undeclared identifier is reported only once
/home/atlanta800/apanel-linux-1.4/linux/apanel.c:604: error: for each function it appears in.)
make[2]: *** [/home/atlanta800/apanel-linux-1.4/linux/apanel.o] Error 1
make[1]: *** [_module_/home/atlanta800/apanel-linux-1.4/linux] Error 2
make[1]: Leaving directory `/usr/src/linux-headers-2.6.17-10-generic'
make: *** [default] Error 2

```

Second, as with the application panel buttons, my brightness controls (Fn+F6/F7) have no xev output at all, let alone actually adjust the brightness. I'd really like to be able to use these keys.

Lastly, I thought I'd throw this in here, since I don't feel like making a new post about it (and I haven't extensively searched for a solution) but after I installed Beryl, all of my gnome shortcuts no longer respond (e.g. Ctrl+Alt+l locks the screen).

My spec's:
Fujitsu T4215
Ubuntu Edgy Eft
2.6.17-10-generic

---

### Post by anasofiapaixao on 2008-04-01
I know this comes late and it's not the best solution, but:

- In Hardy Heron beta the T4215 Fn shortcuts work like a charm out of the box, so maybe you should consider upgrading.
- In my old Tecra M4 the accelerometer (rotation-detecting thingy) just didn't even exist as a device nor was it reachable in any way, and my workaround was adding a pair of nice shortcuts to the Applications bar. They linked to two shell scripts that simply rotated the screen to the vertical and back, as well as the stylus, so all you have to do is click on them when you switch from pc to tablet mode and back. I'll be back with the exact content of the scripts once I bother to RTFM the xrandr and xsetwacom manpages. I also did two pretty icons to match the NuoveXT iconset that also don't feel too off with Ubuntu's default iconset, I'll also post then once I find them.
- Yup, beryl does that. As I just played with desktop compositing for fun and don't use it regularly I simply tuned it off. Anyway now that compiz and beryl have fused again and are/is supported by default since gutsy (and enabled by default on hardy) the gnome shortcuts work perfectly well, so... upgrade.

---

