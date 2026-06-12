---
title: "Built in webcam doesn't work - Acer Aspire A515-57G"
date: 2022-08-01
forum: Hardware
---

### Post by pipou02 on 2022-08-01
Hey there,

I am having some troubles with my new acer laptop with a just bought a couple of months ago and installed ubuntu 22.04.

I have been using ubuntu for some year now already, and although I am not very good or experience when using the terminal, this is the first time I come up with a hardware problem that I can't seem to solve.

So basically my builtin webcam won't work, and when I open cheese or any other webcam app, it says "no device detected". However, it was working when I bought and the seller tested it with me, when it was still on Windows.

I have an old usb webcam here which happens to work just fine.

I usually wouldn't mind so much, but especially after covid I need to give several talks and classes online, so I was hoping someone could help me.

Here is my lsusb output (it detects the webcam):

```
Bus 004 Device 001: ID 1d6b:0003 Linux Foundation 3.0 root hub
Bus 003 Device 003: ID 0408:4033 Quanta Computer, Inc. ACER HD User Facing
Bus 003 Device 002: ID 062a:4106 MosArt Semiconductor Corp. Wireless Mouse 2.4G
Bus 003 Device 005: ID 062a:4101 MosArt Semiconductor Corp. Wireless Keyboard/Mouse
Bus 003 Device 004: ID 8087:0026 Intel Corp. AX201 Bluetooth
Bus 003 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 002 Device 001: ID 1d6b:0003 Linux Foundation 3.0 root hub
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub

```


dmesg output:

```
[    3.464886] uvcvideo 3-7:1.1: Failed to query (129) UVC probe control : 26 (exp. 48).
[    3.464919] uvcvideo 3-7:1.1: Failed to initialize the device (-5).
[    3.501727] usbcore: registered new interface driver uvcvideo

```

I went to linux-hardware and created a probe. However, there already seems to be a kernel module:

```
/usr/include/linux/uvcvideo.h
/usr/include/linux/usb/g_uvc.h
/usr/lib/modules/5.15.0-25-generic/kernel/drivers/media/usb/uvc
/usr/lib/modules/5.15.0-25-generic/kernel/drivers/media/usb/uvc/uvcvideo.ko
/usr/lib/modules/5.15.0-25-generic/kernel/drivers/usb/gadget/function/usb_f_uvc.ko
/usr/lib/modules/5.15.0-41-generic/kernel/drivers/media/usb/uvc
/usr/lib/modules/5.15.0-41-generic/kernel/drivers/media/usb/uvc/uvcvideo.ko
/usr/lib/modules/5.15.0-41-generic/kernel/drivers/usb/gadget/function/usb_f_uvc.ko

```

I hope someone can help me with this, and thank you already to whoever takes their time to read it.

Cheers

---

### Post by chessbucket on 2023-01-03
Same with me. My Acer Aspire-A515-57 webcam is detected in Windows 11 but not Ubuntu 22.04.

Running **guvcview** from command line resulted in:
```

GUVCVIEW: version 2.0.7
GUVCVIEW: couldn't open /home/<REDACTED>/.config/guvcview2/video0 for read: No such file or directory
V4L2_CORE: ERROR opening V4L interface: No such file or directory
GUVCVIEW (1): Guvcview error
no video device (/dev/video0) found

```

Then I tried running **cheese** and was met with a black window saying "No device found"


Then I tried to see if the video device was even found:

$ ls -la /dev/video*
```

ls: cannot access '/dev/video*': No such file or directory

```

$ v4l2-ctl --all
```

Cannot open device /dev/video0, exiting.

```

$ v4l2-ctl --list-devices
```

Cannot open device /dev/video0, exiting.

```

$ lsusb
```

Bus 004 Device 001: ID 1d6b:0003 Linux Foundation 3.0 root hub
Bus 003 Device 003: ID 0408:4033 Quanta Computer, Inc. ACER HD User Facing
Bus 003 Device 002: ID 046d:c534 Logitech, Inc. Unifying Receiver
Bus 003 Device 004: ID 04ca:3802 Lite-On Technology Corp. Wireless_Device
Bus 003 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 002 Device 001: ID 1d6b:0003 Linux Foundation 3.0 root hub
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub

```

$ sudo dmesg | grep video
```

[ 2.544730] videodev: Linux video capture interface: v2.00
[ 2.750454] uvcvideo 3-7:1.1: Failed to query (129) UVC probe control : 26 (exp. 48).
[ 2.750573] uvcvideo 3-7:1.1: Failed to initialize the device (-5).
[ 2.750828] usbcore: registered new interface driver uvcvideo
[ 4.283448] ACPI: video: Video Device [GFX0] (multi-head: yes rom: no post: no)
[ 1215.915597] usbcore: deregistering interface driver uvcvideo
[ 1218.626803] uvcvideo 3-7:1.1: Failed to query (129) UVC probe control : 26 (exp. 48).
[ 1218.626836] uvcvideo 3-7:1.1: Failed to initialize the device (-5).
[ 1218.626919] usbcore: registered new interface driver uvcvideo
[ 1244.610388] usbcore: deregistering interface driver uvcvideo
[ 1256.869775] uvcvideo 3-7:1.1: Failed to query (129) UVC probe control : 26 (exp. 48).
[ 1256.869809] uvcvideo 3-7:1.1: Failed to initialize the device (-5).
[ 1256.869880] usbcore: registered new interface driver uvcvideo

```

---

### Post by andrianovigor on 2023-06-18
Hi everyone! Looks like I found a solution to this problem

```
[COLOR=#000000][FONT=Arial]sudo apt update[/FONT][/COLOR]
[COLOR=#000000][FONT=Arial]sudp apt upgrade[/FONT][/COLOR]
[COLOR=#000000][FONT=Arial]sudo apt install build-essential -y [/FONT][/COLOR]
[COLOR=#000000][FONT=Arial]cd ~  # change to your home directory[/FONT][/COLOR]
[COLOR=#000000][FONT=Arial]apt-get source linux-modules-extra-$(uname -r)[/FONT][/COLOR]
[COLOR=#000000][FONT=Arial]cd ~/linux-*/drivers/media/usb/uvc [/FONT][/COLOR]
[COLOR=#000000][FONT=Arial]mv uvc_driver.c uvc_driver.old[/FONT][/COLOR]
```

Next you need get new code uvc_driver.c:

```
[COLOR=#000000][FONT=Arial]wget [/FONT][/COLOR][[COLOR=#1155CC][FONT=Arial]https://raw.githubusercontent.com/Giuliano69/uvc_driver-for-Quanta-HD-User-Facing-0x0408-0x4035-/main/uvc_driver.c[/FONT][/COLOR]]("https://raw.githubusercontent.com/Giuliano69/uvc_driver-for-Quanta-HD-User-Facing-0x0408-0x4035-/main/uvc_driver.c")
```

[COLOR=#008000]**And you need edit this file for change string with numbers 4035 to 4033 in one place (this model index camera for Acer Aspire A515-57G)**[/COLOR], save file and finish operation:

```
[COLOR=#000000][FONT=Arial]make -j4 -C /lib/modules/$(uname -r)/build M=$(pwd) modules  [/FONT][/COLOR]
[COLOR=#000000][FONT=Arial]sudo cp uvcvideo.ko /lib/modules/$(uname -r)/kernel/drivers/media/usb/uvc/ [/FONT][/COLOR]
[COLOR=#000000][FONT=Arial]reboot[/FONT][/COLOR]
```

Enjoy working webcam into your Acer Aspire A515-57G laptop.

Sources links: 

[[COLOR=#1155CC][FONT=Arial]https://bugs.launchpad.net/ubuntu/+source/linux/+bug/2000947[/FONT][/COLOR]]("https://bugs.launchpad.net/ubuntu/+source/linux/+bug/2000947")
[[COLOR=#1155CC][FONT=Arial]https://github.com/Giuliano69/uvc_driver-for-Quanta-HD-User-Facing-0x0408-0x4035-/blob/main/compile_module.sh[/FONT][/COLOR]]("https://github.com/Giuliano69/uvc_driver-for-Quanta-HD-User-Facing-0x0408-0x4035-/blob/main/compile_module.sh")

Have a nice day!

---

### Post by devyca on 2023-07-08
My camera worked after I disabled secure boot and tried the above commands. Thank you very much @andrianovigor for posting it.

---

### Post by andrianovigor on 2023-07-08
I am glad to help! If after updating Ubuntu the camera stops working again, you need to re-run the command: [COLOR=#000000][FONT=Arial]sudo cp uvcvideo.ko /lib/modules/$(uname -r)/kernel/drivers/media/usb/uvc/. 
[/FONT][/COLOR]Of course, provided that all the source codes are in place. Otherwise, just execute the instruction completely again.

---

### Post by pracrichard2 on 2023-08-09
Hi all,
I have a CLEVO N871EZ laptop (Entroware Hybris) Running Ubunntu 22.04.
It has a built in BisonCam, NB webcam
It used to work fine before a recent update.
Now I get the 'no camera found' message from cheese as did **dvyca**.

I also am unskilled with terminal. Please can someone explain how I can test the camera. 
Many thanks

---

### Post by rahulwrs on 2023-09-30
Hello, I tried above approach but facing below issues:[URL="https://github.com/Giuliano69/uvc_driver-for-Quanta-HD-User-Facing-0x0408-0x4035-/commit/4ecdbb7229f286d91ba8eab5a995bf8031e848ae#start-of-content"]
[/URL]


[LIST=1]
[*]not able to edit downloaded source file, it always open in read-only though i try "edit in text" option.
[*]While trying to compile gives me below error:
```
rahul@rahul-Aspire-A515-57G:/usr/src/linux-headers-6.2.0-33-generic/drivers/media/usb/uvc$ sudo make -j4 -C /lib/modules/$(uname -r)/build M=$(pwd) modules
make: Entering directory '/usr/src/linux-headers-6.2.0-33-generic'
warning: the compiler differs from the one used to build the kernel
The kernel was built by: x86_64-linux-gnu-gcc-11 (Ubuntu 11.4.0-1ubuntu122.04) 11.4.0
You are using: gcc-11 (Ubuntu 11.4.0-1ubuntu122.04) 11.4.0
make[1]: *** No rule to make target '/usr/src/linux-headers-6.2.0-33-generic/drivers/media/usb/uvc/uvc_queue.o', needed by '/usr/src/linux-headers-6.2.0-33-generic/drivers/media/usb/uvc/uvcvideo.o'. Stop.
make[1]: *** Waiting for unfinished jobs....
CC [M] /usr/src/linux-headers-6.2.0-33-generic/drivers/media/usb/uvc/uvc_driver.o
/usr/src/linux-headers-6.2.0-33-generic/drivers/media/usb/uvc/uvc_driver.c:25:10: fatal error: uvcvideo.h: No such file or directory
25 | #include "uvcvideo.h"
| ^~~~~~~~~~~~
compilation terminated.
make[1]: *** [scripts/Makefile.build:260: /usr/src/linux-headers-6.2.0-33-generic/drivers/media/usb/uvc/uvc_driver.o] Error 1
make: *** [Makefile:2026: /usr/src/linux-headers-6.2.0-33-generic/drivers/media/usb/uvc] Error 2
make: Leaving directory '/usr/src/linux-headers-6.2.0-33-generic'
```
[/LIST]

---

### Post by nessvah-horus on 2024-01-02
Mine is giving me the same error but for another kernel version 6.2.0-39-generic. I think it might have something to do with that.. Did you found a solution for the camera?

---

### Post by devyca on 2024-01-11
Hi,


My webcam also had issues with kernel version 6.2.0-39-generic. I ran the attached bash file in the terminal, and it fixed my camera problems. You can download this file, open the terminal, and then run the following commands:

chmod +x compile_module.sh
./compile_module.sh


I found the discussions on this site, [https://bugs.launchpad.net/ubuntu/+source/linux/+bug/2000947]("http://bugs.launchpad.net/ubuntu/+source/linux/+bug/2000947"), helpful. However, today, when I updated to 6.5.0-14-generic, it no longer works.

---

### Post by devyca on 2024-01-15
Hi,

The webcam issues caused by the 6.5 kernel update are now fixed. You can compile the attached file and try it as before.

---

### Post by nessvah on 2024-01-17
Thanks! I was getting an error but it was just gcc that wasn't installed and when i installed it, it worked perfectly ! O:) Let's see if this doesn't break any time soon.

---

### Post by itztarunsingh on 2024-07-16
mine a715-51G how i i get camera index code?

---

### Post by #&amp;thj^% on 2024-07-16
```
 lsusb |grep Camera
[COLOR="#FF0000"]Bus 001 Device 003: ID 5986:2137[/COLOR] Bison Electronics Inc. Integrated Camera

```

---

