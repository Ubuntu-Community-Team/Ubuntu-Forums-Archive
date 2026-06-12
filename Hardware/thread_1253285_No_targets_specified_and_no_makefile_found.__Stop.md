---
title: "No targets specified and no makefile found.  Stop"
date: 2009-08-29
forum: Hardware
---

### Post by GoldDragon on 2009-08-29
I am trying to get my Wacom Bamboo Fun tablet to work in Hardy ( I tried Jaunty, it didn't work well on my system ), I followed the directions found here [http://ubuntuforums.org/showthread.php?t=765915;](http://ubuntuforums.org/showthread.php?t=765915;) when I get to ```
./configure --enable-wacom
make
sudo make install
```
I get the following 
> checking for a BSD-compatible install... /usr/bin/install -c
checking whether build environment is sane... yes
checking for gawk... no
checking for mawk... mawk
checking whether make sets $(MAKE)... yes
checking whether to enable maintainer-specific portions of Makefiles... no
checking for gcc... gcc
checking for C compiler default output file name... configure: error: C compiler cannot create executables
See `config.log' for more details.
                           :~/wacom/linuxwacom-0.8.0-3$ make
make: *** No targets specified and no makefile found.  Stop.


Any ideas how I can fix this?

---

### Post by marshmallow1304 on 2009-08-30
Please post the contents of config.log

---

