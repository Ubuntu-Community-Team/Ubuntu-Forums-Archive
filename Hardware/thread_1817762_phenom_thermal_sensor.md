---
title: "phenom thermal sensor"
date: 2011-08-03
forum: Hardware
---

### Post by boblizar on 2011-08-03
taken and modified from [http://blog.morrigan.ch/?p=9](http://blog.morrigan.ch/?p=9) because i like copy paste better than having to rework improper codes.

open a terminal (press alt + f2)

then type 

gnome-terminal

then hit run

then paste this block of code.

```

mkdir $HOME/k10temp && cd $HOME/k10temp
wget http://lists.lm-sensors.org/pipermail/lm-sensors/attachments/20080718/d51be536/attachment.bin && mv $HOME/k10temp/attachment.bin k10temp.c
cat > $HOME/k10temp/Makefile << "EOF"
obj-m := k10temp.o
KDIR := /lib/modules/$(shell uname -r)/build
PWD := $(shell pwd)
default:
$(MAKE) -C $(KDIR) SUBDIRS=$(PWD) modules
EOF
make -C /lib/modules/$(uname -r)/build M=$HOME/k10temp modules
sudo mv $HOME/k10temp/k10temp.ko /lib/modules/$(uname -r)/kernel/drivers/hwmon

```

enter sudo pass and then immediately run this block....

```

sudo depmod
sudo modprobe k10temp
echo 'k10temp' | sudo tee -a /etc/modules >/dev/null
cd
rm -rf $HOME/k10temp
exit

```

adding k10temp snagged from this thread......  [http://ubuntuforums.org/showthread.php?t=1287819](http://ubuntuforums.org/showthread.php?t=1287819)

---

