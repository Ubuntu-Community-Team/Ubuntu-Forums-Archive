---
title: "Problem with linux kernel module compiling"
date: 2008-10-24
forum: General Help
---

### Post by koenb on 2008-10-24
Hi,

I'm currently having a problem when trying to compile a linux kernel module, the stdio.h and other files are not found. However when compiling a general helloworld.c file with gcc these are found correctly and they are in the /usr/include folder where they belong. However when I run my makefile they aren't found. I've tried two different types of makefile, the first:

```

koen@mvision:~/SoftEmb/practicum/driver$ cat Makefile
obj-m += driver.o

all:
	make -C /lib/modules/$(shell uname -r)/build M=$(PWD) modules

clean:
	make -C /lib/modules/$(shell uname -r)/build M=$(PWD) clean

```
In the second makefile i've changed the /lib/modules/ part with the location of my kernel src: /usr/src/linux-2.6.27.3 these can't find the normal header include files:

```

koen@mvision:~/SoftEmb/practicum/driver$ make -I/usr/include
make -C /lib/modules/2.6.27.3/build M=/home/koen/SoftEmb/practicum/driver modules
make[1]: Entering directory `/usr/src/linux-2.6.27.3'
  CC [M]  /home/koen/SoftEmb/practicum/driver/driver.o
In file included from /home/koen/SoftEmb/practicum/driver/driver.c:10:
/home/koen/SoftEmb/practicum/driver/driver.h:5:19: error: stdio.h: No such file or directory
/home/koen/SoftEmb/practicum/driver/driver.h:6:19: error: fcntl.h: No such file or directory
/home/koen/SoftEmb/practicum/driver/driver.h:7:20: error: unistd.h: No such file or directory
/home/koen/SoftEmb/practicum/driver/driver.h:8:20: error: signal.h: No such file or directory
/home/koen/SoftEmb/practicum/driver/driver.h:9:22: error: sys/stat.h: No such file or directory
/home/koen/SoftEmb/practicum/driver/driver.h:10:23: error: sys/types.h: No such file or directory
/home/koen/SoftEmb/practicum/driver/driver.h:11:38: error: sys/ioctl.h: No such file or directory

```

I even tried to include the folder with the -I option, but this has no result. I've run these make file as root and as user but this doesn't make any difference.

Can anyone help me?

---

### Post by Aessa on 2008-10-24
[http://ubuntuforums.org/showthread.php?t=800251&page=2](http://ubuntuforums.org/showthread.php?t=800251&page=2)
[http://ubuntuforums.org/showthread.php?t=933477&page=2](http://ubuntuforums.org/showthread.php?t=933477&page=2)

I am presently dropping links to useful info regarding this wherever I post.

In answer to your question, you can't use standard stuff. I suppose you'll get the same dismayed feeling I got. Once you enter module world, you enter kernel space and therefore are severely limited to what you can do. There are several other methods for writing user space driver, most notably FUSE, but you have to decide for yourself if this is the way to go.

---

### Post by koenb on 2008-10-24
How do I control another module from in my own LKM?
For example I want to control the /dev/tty with the ioctl command:

```

iotctl(tty_fd, KDSETLED, ledstatus);

```

How do I execute this command from in my LKM?

---

