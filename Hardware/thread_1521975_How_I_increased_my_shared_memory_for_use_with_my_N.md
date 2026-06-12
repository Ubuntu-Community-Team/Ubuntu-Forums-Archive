---
title: "How I increased my shared memory for use with my NVIDIA card"
date: 2010-07-01
forum: Hardware
---

### Post by Azazel on 2010-07-01
I knew my NVIDIA card supported up to 256mb of shared memory, but it didnt seem like my system was utilizing it. This is what i did

First i used the **xdpyinfo** command to checked if my xserver had the required **MIT-SHM extension**.
```
user@ubuntu:~$ **xdpyinfo**
name of display:    :0.0
version number:    11.0
vendor string:    The X.Org Foundation
vendor release number:    10706000
X.Org version: 1.7.6
maximum request size:  16777212 bytes
motion buffer size:  256
bitmap unit, bit order, padding:    32, LSBFirst, 32
image byte order:    LSBFirst
number of supported pixmap formats:    7
supported pixmap formats:
    depth 1, bits_per_pixel 1, scanline_pad 32
    depth 4, bits_per_pixel 8, scanline_pad 32
    depth 8, bits_per_pixel 8, scanline_pad 32
    depth 15, bits_per_pixel 16, scanline_pad 32
    depth 16, bits_per_pixel 16, scanline_pad 32
    depth 24, bits_per_pixel 32, scanline_pad 32
    depth 32, bits_per_pixel 32, scanline_pad 32
keycode range:    minimum 8, maximum 255
focus:  window 0x3200062, revert to PointerRoot
number of extensions:    30
    BIG-REQUESTS
    Composite
    DAMAGE
    DOUBLE-BUFFER
    DPMS
    DRI2
    GLX
    Generic Event Extension
    MIT-SCREEN-SAVER
    **MIT-SHM**
    ...
    ...
    ...

```
If MIT-SHM is not listed here then your kernel probably doesn't have the necessary kernel module loaded and shared memory will not work

Next I checked that the extension was installed by searching for **XShm.h**
```
user@ubuntu:~$ locate XShm.h
**/usr/include/X11/extensions/XShm.h**

```
if nothing is listed here then you are missing the required file

Next I checked the amount of currently allocated shared memory 
```
sudo kwrite **/proc/sys/kernel/shmmax**
sudo kwrite **/proc/sys/kernel/shmall**
```
the values in these files is your shared memory in bytes
mine was only 32mb (32*1024*1024=33554432)
the value here is created at boot by the kernel, so changing these files will only work until reboot. There are two solutions: recompile the kernel with different options, or change these files at boot.

To automatically edit this value after every reboot:
```
sudo kwrite **/etc/sysctl.conf**
```
and add these two lines to the bottom of the file
[B]kernel.shmmax=[amount in bytes]
kernel.shmall=[amount in bytes][/B]
replace [amount in bytes] with however much you want to use.
you only want to put as much as your card is going to use, adding more will not help, and could possible slow down your system.
my NVIDIA card can borrow up to 256mb, as described in the technical specs. so the value i used was 268435456 (256*1024*1024)

**reboot**
```
sudo reboot now
```

**check** to see if the changes persisted:
```
sudo kwrite /proc/sys/kernel/shmall
sudo kwrite /proc/sys/kernel/shmmax
```

the number in these files should be the value you specified in sysctl.conf

---

### Post by Endless_Nameless on 2011-01-22
Thank you for this! I was searching about how to do this for a long time. Maybe I am wrong and don't need 256Mb for video (Linux seems to relay more on processor than on RAM) but I will give it a try!

---

