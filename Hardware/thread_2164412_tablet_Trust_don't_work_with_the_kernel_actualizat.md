---
title: "tablet Trust don't work with the kernel actualization"
date: 2013-07-31
forum: Hardware
---

### Post by enpipes on 2013-07-31
My tablet 'Trust e-Brush' (than was appearing with the name 'WALTOP      Batteryless Tablet') don't work, and don't appear with 'grep -i name  /proc/bus/input/devices'. All from yesterday when the linux kernel was  actualized.
 Thanks to you was working fine from when I bought it. So I hope you can help me again.

You advise me than if this happen, I only need to reload your driver writing:
sudo ./waltop.sh unbind
sudo insmod waltop.ko
When I enter the 1st line the output is:
sudo: ./waltop.sh: command not found

I'm sad:sad: by my wonderfull tablet, help, please
Thanks

---

### Post by gordintoronto on 2013-07-31
Use this command: locate waltop.sh

Then cd to its location.

---

### Post by enpipes on 2013-08-01
Thanks for so fast reply, gordintoronto.
I did it, and tried again      sudo ./waltop.sh unbind
the output was:
insmod: error inserting '/usr/local/waltop/waltop.ko': -1 Invalid module format
./waltop.sh: 7: ./waltop.sh: cannot create /sys/bus/usb/drivers/hiddev/unbind: Directory nonexistent

-The folder non-existent is hiddev. Need I to create it?

(the next command     sudo insmod waltop.ko
gave me: 
insmod: error inserting 'waltop.ko': -1 Invalid module format
)

Thanks for your help
                             _Antoni

---

### Post by enpipes on 2013-08-01
Sorry:
before I did:
locate waltop.sh
with this output:
/usr/local/waltop/waltop.sh

---

### Post by enpipes on 2013-08-03
So, I did:
locate waltop.sh
with this output:
/usr/local/waltop/waltop.sh
then:
cd /usr/local/waltop
and:
./waltop.sh unbind
the output was:
insmod: error inserting '/usr/local/waltop/waltop.ko': -1 Invalid module format
./waltop.sh: 7: ./waltop.sh: cannot create /sys/bus/usb/drivers/hiddev/unbind: Directory nonexistent
What can I do, please?
Thanks a lot

---

### Post by yusuke494 on 2013-08-03
Hi, enpipes, I'm sorry for this late reply.
Please build and install driver again as follows.

1. If you already removed waltop-0.0.6beta2.tar.gz, download from [https://docs.google.com/file/d/0B6aj3ami693uMEg2NldscWplZzA](https://docs.google.com/file/d/0B6aj3ami693uMEg2NldscWplZzA)
2. Extract files
```
tar zxvf waltop-0.0.6beta2.tar.gz
```
3. Uninstall driver
```
cd waltop-0.0.6beta2
sudo make uninstall
make clean
```
4. Rebuild and install driver
```
make
sudo make install
```
5. Reboot your PC

---

### Post by enpipes on 2013-10-11
Hi Yusuke494, here I am again with my bl..dy Trust tablet

I got a new monitor, and I use this to 1360x768.
I tried the intro you gave me for calibrate:
sudo wizardpen-calibrate /dev/bus/usb/004/002

but the output was:
Please, press the stilus at ANY
corner of your desired working area: short read: Success
Don't let me time for press the stylus in any corner, 
and I don't know really what to do for apply the new resolution to your driver.

May you help me?
Have I to begin a new thread?

Regards

---

### Post by yusuke494 on 2013-10-18
Hi enpipes,

Please edit 70-wizardpen.conf manually.

gksu gedit /usr/share/X11/xorg.conf.d/70-wizardpen.conf
Option    "TopX"        "0"
Option    "TopY"        "0"
Option    "BottomX"    "32000"
Option    "BottomY"    "18000"

Finally, reboot your computer.

Best regards

---

