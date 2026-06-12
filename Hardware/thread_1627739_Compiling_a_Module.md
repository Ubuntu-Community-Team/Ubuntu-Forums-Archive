---
title: "Compiling a Module"
date: 2010-11-21
forum: Hardware
---

### Post by Lyoko on 2010-11-21
i'm trying to compile a driver for ubuntu, its a module apparently, im getting all the time errors ending with 
```
make: *** [LINUX] Error 2
```i don't know what to do, i tried to install almost all of the linux-source, linux-headers packages, it does not help. i keep getting it...


what i'm doing wrong?

---

### Post by mIXpRo on 2010-11-21
how do compile what do you write ,
and what are you trying to build , list file examples

---

### Post by Lyoko on 2010-11-21
> **mIXpRo said:**
> how do compile what do you write ,
and what are you trying to build , list file examples
trying to compile this:
[http://ubuntuforums.org/showthread.php?t=1285828](http://ubuntuforums.org/showthread.php?t=1285828)

---

### Post by mIXpRo on 2010-11-21
try installing gcc compiler 
```

sudo apt-get install gcc
sudo apt-get install g++

```

and then try again

---

### Post by Lyoko on 2010-11-21
> **mIXpRo said:**
> try installing gcc compiler 
```

sudo apt-get install gcc
sudo apt-get install g++

```and then try again
i  had gcc, installed g++, didnt help, trying to restart the system and recheck...

---

### Post by Lyoko on 2010-11-21
> **Lyoko said:**
> i  had gcc, installed g++, didnt help, trying to restart the system and recheck...

edit: Did not help...

---

### Post by Lyoko on 2010-11-22
```
root@arazy-htpc:~/Downloads/2009_0525_RT3070_Linux_STA_v2.1.1.0/os/linux# cd ../..;make
make -C tools
make[1]: Entering directory `/home/arazy/Downloads/2009_0525_RT3070_Linux_STA_v2.1.1.0/tools'
gcc -g bin2h.c -o bin2h
make[1]: Leaving directory `/home/arazy/Downloads/2009_0525_RT3070_Linux_STA_v2.1.1.0/tools'
/home/arazy/Downloads/2009_0525_RT3070_Linux_STA_v2.1.1.0/tools/bin2h
cp -f os/linux/Makefile.6 /home/arazy/Downloads/2009_0525_RT3070_Linux_STA_v2.1.1.0/os/linux/Makefile
make  -C  /lib/modules/2.6.35-22-generic/build SUBDIRS=/home/arazy/Downloads/2009_0525_RT3070_Linux_STA_v2.1.1.0/os/linux modules
make[1]: Entering directory `/usr/src/linux-headers-2.6.35-22-generic'
  CC [M]  /home/arazy/Downloads/2009_0525_RT3070_Linux_STA_v2.1.1.0/os/linux/../../os/linux/rt_linux.o
/home/arazy/Downloads/2009_0525_RT3070_Linux_STA_v2.1.1.0/os/linux/../../os/linux/rt_linux.c: In function ‘RtmpOSNetDevAttach’:
/home/arazy/Downloads/2009_0525_RT3070_Linux_STA_v2.1.1.0/os/linux/../../os/linux/rt_linux.c:1510: error: ‘struct net_device’ has no member named ‘open’
/home/arazy/Downloads/2009_0525_RT3070_Linux_STA_v2.1.1.0/os/linux/../../os/linux/rt_linux.c:1511: error: ‘struct net_device’ has no member named ‘stop’
/home/arazy/Downloads/2009_0525_RT3070_Linux_STA_v2.1.1.0/os/linux/../../os/linux/rt_linux.c:1512: error: ‘struct net_device’ has no member named ‘hard_start_xmit’
/home/arazy/Downloads/2009_0525_RT3070_Linux_STA_v2.1.1.0/os/linux/../../os/linux/rt_linux.c:1513: error: ‘struct net_device’ has no member named ‘do_ioctl’
/home/arazy/Downloads/2009_0525_RT3070_Linux_STA_v2.1.1.0/os/linux/../../os/linux/rt_linux.c:1519: error: ‘struct net_device’ has no member named ‘get_stats’
/home/arazy/Downloads/2009_0525_RT3070_Linux_STA_v2.1.1.0/os/linux/../../os/linux/rt_linux.c:1553: error: ‘struct net_device’ has no member named ‘validate_addr’
make[2]: *** [/home/arazy/Downloads/2009_0525_RT3070_Linux_STA_v2.1.1.0/os/linux/../../os/linux/rt_linux.o] Error 1
make[1]: *** [_module_/home/arazy/Downloads/2009_0525_RT3070_Linux_STA_v2.1.1.0/os/linux] Error 2
make[1]: Leaving directory `/usr/src/linux-headers-2.6.35-22-generic'
make: *** [LINUX] Error 2
root@arazy-htpc:~/Downloads/2009_0525_RT3070_Linux_STA_v2.1.1.0# cd /home/arazy/Downloads/2009_0525_RT3070_Linux_STA_v2.1.1.0/os/linux
root@arazy-htpc:~/Downloads/2009_0525_RT3070_Linux_STA_v2.1.1.0/os/linux# cd ../..;make
make -C tools
make[1]: Entering directory `/home/arazy/Downloads/2009_0525_RT3070_Linux_STA_v2.1.1.0/tools'
gcc -g bin2h.c -o bin2h
make[1]: Leaving directory `/home/arazy/Downloads/2009_0525_RT3070_Linux_STA_v2.1.1.0/tools'
/home/arazy/Downloads/2009_0525_RT3070_Linux_STA_v2.1.1.0/tools/bin2h
cp -f os/linux/Makefile.6 /home/arazy/Downloads/2009_0525_RT3070_Linux_STA_v2.1.1.0/os/linux/Makefile
make  -C  /lib/modules/2.6.35-22-generic/build SUBDIRS=/home/arazy/Downloads/2009_0525_RT3070_Linux_STA_v2.1.1.0/os/linux modules
make[1]: Entering directory `/usr/src/linux-headers-2.6.35-22-generic'
  CC [M]  /home/arazy/Downloads/2009_0525_RT3070_Linux_STA_v2.1.1.0/os/linux/../../os/linux/rt_linux.o
/home/arazy/Downloads/2009_0525_RT3070_Linux_STA_v2.1.1.0/os/linux/../../os/linux/rt_linux.c: In function ‘RtmpOSNetDevAttach’:
/home/arazy/Downloads/2009_0525_RT3070_Linux_STA_v2.1.1.0/os/linux/../../os/linux/rt_linux.c:1510: error: ‘struct net_device’ has no member named ‘open’
/home/arazy/Downloads/2009_0525_RT3070_Linux_STA_v2.1.1.0/os/linux/../../os/linux/rt_linux.c:1511: error: ‘struct net_device’ has no member named ‘stop’
/home/arazy/Downloads/2009_0525_RT3070_Linux_STA_v2.1.1.0/os/linux/../../os/linux/rt_linux.c:1512: error: ‘struct net_device’ has no member named ‘hard_start_xmit’
/home/arazy/Downloads/2009_0525_RT3070_Linux_STA_v2.1.1.0/os/linux/../../os/linux/rt_linux.c:1513: error: ‘struct net_device’ has no member named ‘do_ioctl’
/home/arazy/Downloads/2009_0525_RT3070_Linux_STA_v2.1.1.0/os/linux/../../os/linux/rt_linux.c:1519: error: ‘struct net_device’ has no member named ‘get_stats’
/home/arazy/Downloads/2009_0525_RT3070_Linux_STA_v2.1.1.0/os/linux/../../os/linux/rt_linux.c:1553: error: ‘struct net_device’ has no member named ‘validate_addr’
make[2]: *** [/home/arazy/Downloads/2009_0525_RT3070_Linux_STA_v2.1.1.0/os/linux/../../os/linux/rt_linux.o] Error 1
make[1]: *** [_module_/home/arazy/Downloads/2009_0525_RT3070_Linux_STA_v2.1.1.0/os/linux] Error 2
make[1]: Leaving directory `/usr/src/linux-headers-2.6.35-22-generic'
make: *** [LINUX] Error 2
root@arazy-htpc:~/Downloads/2009_0525_RT3070_Linux_STA_v2.1.1.0#
```



that is the exact log..

---

### Post by deathgod on 2010-11-22
Hey, I have the same problem just with another module I'm trying to compile, exactly the same error.
I would be really grateful if someone can give me an example (and for Lyoko at the same time I assume) how to correctly compile this so we won't have any errors.

Cheers! :D

---

### Post by Lyoko on 2010-11-22
someone? Please, i can't really get internet connection permanently without doing it..

---

### Post by deathgod on 2010-11-22
Last bumping I guess..

---

### Post by Lyoko on 2010-11-23
Please someone.... it will be really appreciated.

---

