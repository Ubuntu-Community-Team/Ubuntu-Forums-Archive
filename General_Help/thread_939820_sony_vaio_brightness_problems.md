---
title: "sony vaio brightness problems"
date: 2008-10-06
forum: General Help
---

### Post by xGutsAndGloryx on 2008-10-06
i am having bad brightness problems with my sony vaio pcg-k23. i have tried the other sony vaio post on the forum. it was no help. does anyone have any other ideas?

---

### Post by jokkerjoss on 2009-06-02
I have  sony vaio pcg-k23 laptop. Previously, I had a version Ubuntu Gutsy, but recently I upgraded it to Ubuntu Jaunty. The major downside is:

THE LOST BRIGHTNESS.

Additional to that:
 a FN key is not working plus I´m not able to readjust it from the menu at POWER MANAGEMENT option and finaly I run the program SPICCTRL which is the SOny Vaio ACPI manager program, but the result which I got was negative!

jokkerjoss@jokkerjoss:~$ spicctrl -B
/dev/sonypi: No such file or directory
jokkerjoss@jokkerjoss:~$ 

It stated that that particular file does not exist! Is somebody has any clue what to do for next?

---

### Post by Soul-Sing on 2009-06-02
Maybe this is hulpful?:

> Sony Vaio controller program to set LCD backlight brightness
spicctrl is a small program that can use the Sony Programmable I/O Control
device (SPIC), which is part of Sony Vaio's, to do a few simple things.
Currently, it can only be used to control the brightness on the LCD
backlight, and print out some information about the battery.

You need a kernel with the sonypi module (and a Vaio laptop..) to use this
program.

---

### Post by jokkerjoss on 2009-06-02
Well! Laptop Sony Vaio PCG-K23 I'm already having, But where or how I will be able to get or create the module SONYPI for my kernel?

---

### Post by Soul-Sing on 2009-06-02
> **jokkerjoss said:**
> Well! Laptop Sony Vaio PCG-K23 I'm already having, But where or how I will be able to get or create the module SONYPI for my kernel?

I am busy/googling on that...;)

---

### Post by Soul-Sing on 2009-06-02
: [http://ubuntuforums.org/archive/index.php/t-10539.html](http://ubuntuforums.org/archive/index.php/t-10539.html)

---

### Post by jokkerjoss on 2009-06-03
Well I went throw that forum thread and threads
[http://ubuntuforums.org/archive/index.php/t-10539.html](http://ubuntuforums.org/archive/index.php/t-10539.html)
 and did some research in Google, but still I have to say that I &#7743; quit newby in Linux and according to that I believe that I `m not doing it properly or I do not know how to do it!

That what I did:

jokkerjoss@jokkerjoss:~$ sudo modprobe sonypi
[sudo] password for jokkerjoss: 
jokkerjoss@jokkerjoss:~$ locate sonypi
/lib/modules/2.6.28-11-generic/kernel/drivers/char/sonypi.ko
/usr/include/linux/sonypi.h
/usr/lib/directfb-1.0-0/inputdrivers/libdirectfb_sonypi.so
/usr/lib/hal/hal-system-sonypic
/usr/src/linux-headers-2.6.28-11/include/linux/sonypi.h
/usr/src/linux-headers-2.6.28-11-generic/include/config/sonypi
/usr/src/linux-headers-2.6.28-11-generic/include/config/sonypi.h
/usr/src/linux-headers-2.6.28-11-generic/include/config/sonypi/compat.h
/usr/src/linux-headers-2.6.28-11-generic/include/linux/sonypi.h
jokkerjoss@jokkerjoss:~$ locate sonypid
jokkerjoss@jokkerjoss:~$ sudo modprobe sonypid
FATAL: Module sonypid not found.
jokkerjoss@jokkerjoss:~$ spicctrl -B
100
jokkerjoss@jokkerjoss:~$ spicctrl -b 255
jokkerjoss@jokkerjoss:~$ spicctrl -B
255
jokkerjoss@jokkerjoss:~$ sudo updatedb
[sudo] password for jokkerjoss: 
jokkerjoss@jokkerjoss:~$ locate sonypi
/lib/modules/2.6.28-11-generic/kernel/drivers/char/sonypi.ko
/usr/include/linux/sonypi.h
/usr/lib/directfb-1.0-0/inputdrivers/libdirectfb_sonypi.so
/usr/lib/hal/hal-system-sonypic
/usr/src/linux-headers-2.6.28-11/include/linux/sonypi.h
/usr/src/linux-headers-2.6.28-11-generic/include/config/sonypi
/usr/src/linux-headers-2.6.28-11-generic/include/config/sonypi.h
/usr/src/linux-headers-2.6.28-11-generic/include/config/sonypi/compat.h
/usr/src/linux-headers-2.6.28-11-generic/include/linux/sonypi.h
jokkerjoss@jokkerjoss:~$ locate spicctrl
/usr/bin/spicctrl
/usr/share/doc/spicctrl
/usr/share/doc/spicctrl/AUTHORS
/usr/share/doc/spicctrl/README.Debian
/usr/share/doc/spicctrl/changelog.Debian.gz
/usr/share/doc/spicctrl/changelog.gz
/usr/share/doc/spicctrl/copyright
/usr/share/man/man1/spicctrl.1.gz
/var/cache/apt/archives/spicctrl_1.9-2_i386.deb
/var/lib/dpkg/info/spicctrl.list
/var/lib/dpkg/info/spicctrl.md5sums
jokkerjoss@jokkerjoss:~$ 


 but still the screen is dark even if the SPICCTRL program shows the maximum brightness level. I m confused. Does somebody have a clue how to fix this terrible display brightness problem?

---

