---
title: "Install CPiA2 on Ubuntu 11.04"
date: 2011-09-18
forum: Hardware
---

### Post by Jack Jon Cade on 2011-09-18
Hi,
I'm tring to install the [CPiA2 drivers]("http://cpia2.sourceforge.net/") on Natty Narwhal with 2.6.38-11-generic-pae but I have some trouble here and I need some help ;)

The first problem was that the Makefile contained $(PWD) instead of $(shell pwd), solved with Internet
```
default: Makefile
	$(MAKE) -C $(KERNEL_DIR)/build SUBDIRS=$(PWD) modules

clean: Makefile
	$(MAKE) -C $(KERNEL_DIR)/build SUBDIRS=$(PWD) clean
```


```
default: Makefile
	$(MAKE) -C $(KERNEL_DIR)/build SUBDIRS=$(shell pwd) modules

clean: Makefile
	$(MAKE) -C $(KERNEL_DIR)/build SUBDIRS=$(shell pwd) clean
```

The Second problem is that when I try *make install*, it fail with > /home/nicola/Desktop/cpia2_driver-2.0/cpia2.h:40:28: fatal error: linux/videodev.h: No such file or directory. 

The problem is that kernel 2.6.38 dropped support for v4l: [http://kubuntuforums.net/forums/index.php?topic=3115676.0](http://kubuntuforums.net/forums/index.php?topic=3115676.0)
At now I tried:
[LIST=1]
[*]Rename videodev.h include with videodev2.h

[*]Use *#include </usr/include/libv4l1-videodev.h>* instead *#include <linux/videodev.h> *
Source: [http://dolot.kipdola.com/wiki/Install_SASC-NG#Further_dependencies_for_kernel_2.6.38_and_above](http://dolot.kipdola.com/wiki/Install_SASC-NG#Further_dependencies_for_kernel_2.6.38_and_above)
[/LIST]
but both methods fail and give a lot of error and mistake :(

Someone could help?

---

