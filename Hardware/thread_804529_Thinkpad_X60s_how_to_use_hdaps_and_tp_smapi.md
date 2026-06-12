---
title: "Thinkpad X60s how to use hdaps and tp_smapi ?"
date: 2008-05-23
forum: Hardware
---

### Post by Axx83 on 2008-05-23
I own a thinkpad x60s, as I read on [thinkwiki]("http://www.thinkwiki.org/wiki/Tp_smapi") ubuntu hardy has tp_smapi (some utility to regulate battery and hard drive) already in the modules:

> Installation on Ubuntu Hardy
Ubuntu ships tp_smapi in their linux-ubuntu-modules package since Hardy, so you don't have to build it yourself. Please note that they have renamed tp_smapi's modified hdaps module to hdaps_ec. You should load hdaps_ec, not hdaps.

how do i load this module?

I also installed hdaps from the repos but when I run it in the terminal it says:

> myname@myname-laptop:~$ hdapsd -d sda -s 15
WARNING: Cannot open hdaps position input file /dev/input/hdaps/accelerometer-event (No such file or directory). You may be using an incompatible version of the hdaps module, or missing the required udev rule. Falling back to reading the position from sysfs (uses more power). Use '-y' to silence this warning.
open(protect_file): No such file or directory

---

### Post by wenuswilson on 2008-05-23
At the bottom of the wiki page it says that the files can be accessed by /sys/devices/platfom/smapi.

I have a thinkpad t61 and that directory doesn't exist.

---

### Post by Axx83 on 2008-05-23
I managed to install the tp_smapi and hdaps_ec modules from start:
> To make sure your system loads the modules at boot time, do this:

```
echo "tp_smapi" >> /etc/modules
echo "hdaps_ec" >> /etc/modules
```

and update your initramfs:

```
update-initramfs -u
```

To get tp_smapi running now, just load the modules:

```
modprobe -a tp_smapi hdaps_ec
```

done this the modules are loaded from start, i can now set battery charging limit as in the guide:
> To set the thresholds for starting and stopping battery charging (in percent of current full charge capacity):
```
# echo 40 > /sys/devices/platform/smapi/BAT0/start_charge_thresh
# echo 70 > /sys/devices/platform/smapi/BAT0/stop_charge_thresh
# cat /sys/devices/platform/smapi/BAT0/*_charge_thresh
```
and it works, the problem is after reboot and after I plugged the battery in and out these settings are gone and it wants to charge my battery up to 100% !!!

Another thing, when i run:
```
hdapsd -d sda -s 15
```
it gives me the same answer but when i run
```
sudo hdapsd -d sda -s 15
```
it just says:
> open(protect_file): No such file or directory
the funny thing is that when i run hdaps-gl it works!!!!!!!!

What did i do wrong ???

---

### Post by Axx83 on 2008-05-23
> At the bottom of the wiki page it says that the files can be accessed by /sys/devices/platfom/smapi.

I have a thinkpad t61 and that directory doesn't exist.

maybe this is the problem, even tough I managed to load the modules now and they apparently work, not the hdapsd demon tough, and is by the way the most important thing I guess.

---

### Post by Axx83 on 2008-05-23
Searching more patiently I found that hdaps needs a udev rule and on this page: [http://article.gmane.org/gmane.linux.drivers.hdaps.devel/1040]("http://article.gmane.org/gmane.linux.drivers.hdaps.devel/1040") it says how to set it:
> In order to use the new-and-improved input device interface, you need
tp_smapi >= 0.32. Also, you need to add a udev rule to help hdapsd
find the input device. Do this:
```
# echo 'KERNEL=="event[0-9]*", ATTRS{phys}=="hdaps/input1",
ATTRS{modalias}=="input:b0019v1014p5054e4801-*",
SYMLINK+="input/hdaps/accelerometer-event"' >
/etc/udev/rules.d/51-hdaps.rules
```
Then reboot or run "/sbin/udevtrigger", and verify that the
"/dev/input/hdaps/accelerometer-event" symlink exists.

Needless to say...it doesn't work, putting these commands in the terminal just gives me weird terminal blanks...

---

### Post by nick cellular on 2008-05-23
I don't think Hardy has the necessary kernel patches to run hdaps properly.

What I did to get hdaps to work is install the source, patch the kernel with this [http://article.gmane.org/gmane.linux.drivers.hdaps.devel/1094](http://article.gmane.org/gmane.linux.drivers.hdaps.devel/1094) and this [http://mailman.linux-thinkpad.org/pipermail/linux-thinkpad/2008-February/042226.html](http://mailman.linux-thinkpad.org/pipermail/linux-thinkpad/2008-February/042226.html)

then installed that kernel and built tp_smapi from source and everything works fine.

---

### Post by Axx83 on 2008-05-23
Then why include tp_smapi in the modules and hdaps in the repos ? It's kinda stupid if they don't really work in the end, no one really wants to apply patches to the kernel, I don't even know how to do it...

---

### Post by nick cellular on 2008-05-23
Its fun to try once or twice.

Install the kernel sources and stuff
```

sudo apt-get update
sudo apt-get install kernel-package libncurses5-dev fakeroot wget bzip2 linux-source

```


make sure you change directories to the source
```

cd /usr/src/

```

uncompressed kernel source in /usr/src
```

bunzip2 linux-source-2.6.24.tar.bz2

```


then untar it
```

tar xvf linux-source-2.6.24.tar

```

change directories to the new source
```

cd /usr/src/linux-source-2.6.24-16

```

now you can patch the source, get patches from my previous link, just copy paste each onto into a txt file created in /usr/src/linux-source-2.6.24

```

patch -p1 -l < patch1.txt
patch -p1 -l < patch2.txt

```

copy the .config from /boot
```

cp /boot/config-2.6.24-16-generic ./.config

```

make any additional customizations (ntfs write support for example)
```

make menuconfig

```

now you're ready to build
```

make-kpkg clean
fakeroot make-kpkg --initrd --append-to-version=-custom kernel_image kernel_headers

```

to install and setup GRUB
```

dpkg -i /usr/src/linux-image-<your custom kernel>.deb
dpkg -i /usr/src/linux-headers-<your custom kernel>.deb

```

---

### Post by Axx83 on 2008-05-23
I could try since it's a new installation, I'll let you know, by the way thanks for the guide !

---

