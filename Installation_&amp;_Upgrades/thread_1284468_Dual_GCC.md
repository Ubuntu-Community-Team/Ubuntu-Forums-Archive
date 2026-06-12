---
title: "Dual GCC"
date: 2009-10-06
forum: Installation &amp; Upgrades
---

### Post by LinLux451 on 2009-10-06
Hello, I am a long time linux user.... well.. kinda.. I know my way around, let's just say that. I am currently running Hardy on an old P4. My true intention is to build a beowulf off of openMosix and an old vanilla 2.24.26 kernel for a CISCO project. I have patched and configurated off of [http://ubuntuforums.org/showthread.php?t=17012]("http://ubuntuforums.org/showthread.php?t=17012") and tried to compile and install but alas, I was shut down by the fact openMosix kernel require the 2.95.3 and I'm still using whatever Hardy came with (not usually a compiler.. usually a firefoxer), anyway, I downloaded the tarball from a mirror, and have been using [http://www.tellurian.com.au/whitepapers/multiplegcc.php]("http://www.tellurian.com.au/whitepapers/multiplegcc.php") as my guide to installing gcc-2.95.3. My problem is I get compiling errors with the bootstrap command. The last few lines of output being:
```
/usr/local/gcc/2.95.3/i686-pc-linux-gnu/bin/ -c -g -O2 -I. -I/home/skynet/gcc-2.95.3/libio -D_IO_MTSAFE_IO  /home/skynet/gcc-2.95.3/libio/iogetline.c -o pic/iogetline.o
/home/skynet/gojb/gcc/xgcc -B/home/skynet/gojb/gcc/ -B/usr/local/gcc/2.95.3/i686-pc-linux-gnu/bin/ -c -g -O2 -I. -I/home/skynet/gcc-2.95.3/libio -D_IO_MTSAFE_IO /home/skynet/gcc-2.95.3/libio/iogetline.c
In file included from /home/skynet/gcc-2.95.3/libio/libio.h:167,
                 from /home/skynet/gcc-2.95.3/libio/iolibio.h:1,
                 from /home/skynet/gcc-2.95.3/libio/libioP.h:47,
                 from /home/skynet/gcc-2.95.3/libio/iogetline.c:26:
/usr/include/bits/stdio-lock.h:24: lowlevellock.h: No such file or directory
make[2]: *** [iogetline.o] Error 1
make[2]: Leaving directory `/home/skynet/gojb/i686-pc-linux-gnu/libio'
make[1]: *** [all-target-libio] Error 2
make[1]: Leaving directory `/home/skynet/gojb'
make: *** [bootstrap] Error 2

```

Any help with getting gcc 2.95 installed would be lovely! I should be in the clear for "Unibuntu" after that, but... no promises. Thanks for all the help with Ubuntu, Debain, Linux, and life. The ubuntuforums is probably one of the most amazing communities on the web! (BTW, I couldn't think of a better beowulf name then skynet:lolflag:)

---

### Post by LinLux451 on 2009-10-07
I hate doing this but...
*bump

---

### Post by nbo10 on 2009-12-01
Did you find a solution?

---

### Post by LinLux451 on 2009-12-02
Hm.. I got farther. I haven't fired up that old terminal in awhile. Kind of evaded me. I did eventually get it installed but it got hung up with some BCC? errors? I don't know, I will surely kick 'er on tomorrow and find out the exact reasons. 
- Thanks for continued interest

---

