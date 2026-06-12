---
title: "Driver for Sealevel 5104 compilation errors on Ubuntu 10.04"
date: 2010-08-11
forum: Hardware
---

### Post by anemecek on 2010-08-11
Greetings to all. 

I'm trying to compile the linux driver for the card Sealevel 5104 
```
http://www.sealevel.com/store/5104-low-profile-pci-rs-232-rs-422-rs-485-rs-530-rs-530a-v-35-synchronous-serial-interface-uses-z16c.html
```
but every time I try to compile it, I get the following errors (route56 is the name of the driver):

```
n file included from /home/protoexist/anemecek/route56/driver/route56.c:109:
/home/protoexist/anemecek/route56/driver/compat.h: In function ‘cpat_ldisc_receive_buf’:
/home/protoexist/anemecek/route56/driver/compat.h:366: error: ‘struct tty_ldisc’ has no member named ‘receive_buf’
/home/protoexist/anemecek/route56/driver/compat.h:367: error: ‘struct tty_ldisc’ has no member named ‘receive_buf’
/home/protoexist/anemecek/route56/driver/route56.c: In function ‘r56_close’:
/home/protoexist/anemecek/route56/driver/route56.c:3139: error: ‘struct tty_driver’ has no member named ‘flush_buffer’
/home/protoexist/anemecek/route56/driver/route56.c:3140: error: ‘struct tty_driver’ has no member named ‘flush_buffer’
/home/protoexist/anemecek/route56/driver/route56.c: At top level:
/home/protoexist/anemecek/route56/driver/route56.c:4362: warning: initialization from incompatible pointer type
/home/protoexist/anemecek/route56/driver/route56.c:4371: warning: initialization from incompatible pointer type
/home/protoexist/anemecek/route56/driver/route56.c:4373: error: unknown field ‘read_proc’ specified in initializer
/home/protoexist/anemecek/route56/driver/route56.c:4373: warning: initialization from incompatible pointer type
make[3]: *** [/home/protoexist/anemecek/route56/driver/route56.o] Error 1

```

I'm running Ubuntu 10.04 with the kernel version 2.6.32-24-generic.

In the README of the driver for the card, it says that when compiling, make will search the folder /usr/src/linux for the kernel source. At first, I tried to create a symlink in /usr/src named linux targeting the folder /usr/src/linux-headers-2.6.32-24-generic but I was getting the same errors (I found somewhere that compiling with the headers as opposed to the actual kernel source should be sufficient). The I downloaded the kernel source and tried to create a link called linux targeting the folder containing the kernel source. I got the same errors. Then I actually viewed the files tty_ldisc.h and tty_ldisc.c and was surprised that the header file tty_ldisc.h contains the declaration of the function receive_buf (the function which make cannot find) but the file tty_ldisc.c does not contain the definition of the function. 

On this website ```
http://forum.comtrol.com/index.php?t=msg&th=1534&rid=&S=c06d15aacbd51f474b1f2d233cba73e4&pl_view=&start=0#msg_3950
``` someone mentioned that the layout of the structures has changed and the new definitions do not contain the required member functions (e.g. receive_buf). Therefore, I download some older kernel source versions and tried to compile it but I was getting the same errors. One suspicious thing is that some of these older kernel versions did not even contain the tty_ldisc.c file (but did contain the tty_ldisc.h file) which ***** me to believe that some hierarchical changes must have taken place at some point. 

So the questions are:
[LIST]
[*] Most importantly, how can I get the driver to compile?
[*] Do I actually need the kernel source? 
[*] I have not tried this yet because I would prefer making this to work, but could I maybe get it running using the Windows driver and ndiswrapper? Or Wine? Are there any alternatives that I'm missing?
[/LIST]

---

