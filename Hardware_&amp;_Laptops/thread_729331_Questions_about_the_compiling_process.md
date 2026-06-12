---
title: "Questions about the compiling process"
date: 2008-03-19
forum: Hardware &amp; Laptops
---

### Post by CoffeeBreath on 2008-03-19
I have a syntek webcam driver and did the following:

$ make
$ sudo modprobe videodev
$ sudo modprobe v4l1-compat
$ sudo insmod stk11xx.ko

(the insmod line won't work unless I'm in the Stk... directory.) The others I can do from home.

gksu gedit /etc/modules:
videodev
v4l1-compat
stk11xx.ko ([COLOR="RoyalBlue"]was it necessary to add this one?[/COLOR])

gksu gedit /etc/rc.local:
home/<my user name >/syntekdriver/trunk/driver/st k11xx.ko

As of now the syntek driver is located on my desktop so this line:"
gksu gedit /etc/rc.local:"
is actually
/home/my name/Desktop/stk11xx-1.3.1/st k11xx.ko

After running all of these commands in order i can get the camera to turn on, even after a reboot.

1.Should I have untarred the module into another directory?

2.why was I able to use different directories for the insmod and modprobe commands?

3. Exactly what are videodev and v4l1-compat?

4. Was it really necessary to put the driver into the modules script?

---

### Post by sdennie on 2008-03-19
If you built the kernel module from source, from the directory where you built it, you should be able to:

```

$ sudo make install

```

That should install the kernel module in the running kernels module directory (you may need to "sudo depmod -a" afterwards).  After that you likely only need to add

```

stk11xx

```

to /etc/modules and it should autoload the other needed modules.

---

### Post by CoffeeBreath on 2008-03-19
1. If depmod had been succesful would i have had to put that insmod in the rc.local file?

2. Why did I have to change directories for the first two modprobes and then the insmod. The modprobes were done in the drivers directory and the last could only be done from /myname@???

3. Which directory should I be building device drivers in?

---

### Post by sdennie on 2008-03-19
Well, I run a custom kernel and some of the things that the Ubuntu kernel provides I have to build manually.  Specifically, I build the uvcvideo module and install it (also a webcam driver).  If the drivers Makefile supports "sudo make install" (which it should), it means that things like directory switching and even using "insmod" are not needed.  Once a kernel module is installed in a findable place, a simple "modprobe the_module" should be sufficient and, just adding the module name to /etc/modules should give you the result you want.  The rc.local stuff is likely not needed.

---

