---
title: "HP fingerprint reader"
date: 2007-03-04
forum: Hardware &amp; Laptops
---

### Post by rocketman768 on 2007-03-04
I have bought a new HP fingerprint reader (usb), but now I can't find any info about how to use it in Linux. Does someone know what driver/software I need?

---

### Post by seldenthuis on 2007-03-04
There are basically two options. Using the binary drivers (installation instructions: [http://www.thinkwiki.org/wiki/How_to_enable_the_fingerprint_reader]("http://www.thinkwiki.org/wiki/How_to_enable_the_fingerprint_reader")) or using the open source ThinkFinger driver (project page: [http://thinkfinger.sourceforge.net/]("http://thinkfinger.sourceforge.net/"), installation instructions: [http://www.thinkwiki.org/wiki/How_to_enable_the_fingerprint_reader_with_ThinkFinger]("http://www.thinkwiki.org/wiki/How_to_enable_the_fingerprint_reader_with_ThinkFinger")).

I chose ThinkFinger since it is easier to install. The drawback is that you cannot yet get it to work with xscreensaver. It also will not give you a prompt when you use gksudo. The first time it will just wait for you to swipe your finger. If it times out, the second time you use it it will ask for your password and ignore the fingerprint reader.

I've read that the binary drivers do not have this problem, but I ran into problems while trying to install them, so I used ThinkFinger instead.

---

### Post by rocketman768 on 2007-03-05
I thought ThinkFinger was only for the Lenovo laptops...

Well, I tried it anyway and no such luck. "dmesg | tail" just shows me:

```

[12053.320428] usb 5-2: new full speed USB device using uhci_hcd and address 4
[12053.487672] usb 5-2: configuration #1 chosen from 1 choice

```

and when I run "tf-tool acquire", I get:

```

ThinkFinger 0.2.2 (http://thinkfinger.sourceforge.net/)
Copyright (C) 2006, 2007 Timo Hoenig <thoenig@suse.de>

Initializing...USB device not found.

```

---

### Post by rocketman768 on 2007-03-05
...and lsusb shows nothing.

---

### Post by LinuxIsInnovation on 2007-12-10
I followed thinkwiki forums.. This is what I get on firing configure..

root@glade-laptop:~/bioapi-linux# ./configure --with-Qt-dir=no
checking for a BSD-compatible install... /usr/bin/install -c
checking whether build environment is sane... yes
checking for a thread-safe mkdir -p... /bin/mkdir -p
checking for gawk... gawk
checking whether make sets $(MAKE)... yes
checking for style of include used by make... GNU
checking for gcc... gcc
checking for C compiler default output file name... a.out
checking whether the C compiler works... yes
checking whether we are cross compiling... no
checking for suffix of executables... 
checking for suffix of object files... o
checking whether we are using the GNU C compiler... yes
checking whether gcc accepts -g... yes
checking for gcc option to accept ISO C89... none needed
checking dependency style of gcc... gcc3
checking how to run the C preprocessor... gcc -E
checking for grep that handles long lines and -e... /bin/grep
checking for egrep... /bin/grep -E
checking for ANSI C header files... yes
checking for sys/types.h... yes
checking for sys/stat.h... yes
checking for stdlib.h... yes
checking for string.h... yes
checking for memory.h... yes
checking for strings.h... yes
checking for inttypes.h... yes
checking for stdint.h... yes
checking for unistd.h... yes
checking whether byte ordering is bigendian... no
checking for g++... g++
checking whether we are using the GNU C++ compiler... yes
checking whether g++ accepts -g... yes
checking dependency style of g++... gcc3
checking for gcc... (cached) gcc
checking whether we are using the GNU C compiler... (cached) yes
checking whether gcc accepts -g... (cached) yes
checking for gcc option to accept ISO C89... (cached) none needed
checking dependency style of gcc... (cached) gcc3
checking for flex... flex
checking lex output file root... lex.yy
checking lex library... -lfl
checking whether yytext is a pointer... yes
checking for a BSD-compatible install... /usr/bin/install -c
checking for bison... bison -y
configure: error: cannot run /bin/bash ./config.sub
root@glade-laptop:~/bioapi-linux#

---

### Post by Slywire on 2008-01-07
> **rocketman768 said:**
> I thought ThinkFinger was only for the Lenovo laptops...

Well, I tried it anyway and no such luck. "dmesg | tail" just shows me:

```

[12053.320428] usb 5-2: new full speed USB device using uhci_hcd and address 4
[12053.487672] usb 5-2: configuration #1 chosen from 1 choice

```

and when I run "tf-tool acquire", I get:

```

ThinkFinger 0.2.2 (http://thinkfinger.sourceforge.net/)
Copyright (C) 2006, 2007 Timo Hoenig <thoenig@suse.de>

Initializing...USB device not found.

```

I get the same problem, only when I type in "lsusb" I get the following:
```

Bus 001 Device 005: ID 045e:00ca Microsoft Corp.

```

Im trying to install a DigitalPersona/Microsoft Fingerprint Reader. Any help would be appreciated

---

### Post by cudjoe on 2008-01-18
It clearly says that ThinkFinger is for *SGS Thomson Microelectronics fingerprint reader found in most IBM/Lenovo ThinkPads.*

I have a Compaq 6710b, and it comes with an AuthenTec device. At least, this is what I figured out with *lsusb*
```
Bus 003 Device 005: ID 08ff:2580 AuthenTec, Inc.
```

The hardware4line page of this device :
[http://hardware4linux.info/component/15599/](http://hardware4linux.info/component/15599/)

---

### Post by simplyw00x on 2008-01-18
[http://reactivated.net/fprint/wiki/Main_Page](http://reactivated.net/fprint/wiki/Main_Page)

Fprint works for some authentec devices, mostly USB iirc. Try it out - I think debs are available.

---

