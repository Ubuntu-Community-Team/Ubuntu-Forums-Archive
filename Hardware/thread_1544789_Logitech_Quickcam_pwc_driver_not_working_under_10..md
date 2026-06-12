---
title: "Logitech Quickcam pwc driver not working under 10.04"
date: 2010-08-03
forum: Hardware
---

### Post by Zookalicious on 2010-08-03
Hey all, I've been having one hell of a time trying to get either of my logitech quickcams to work. I'm trying mostly to get the Quickcam pro 4000 working. Everyone says that it works out of the box, but all I got was a black screen when I opened it in cheese. After searching for a solution, I tried installing the driver, but when I typed in "make" I got this massive block of errors. 
```

make -C /lib/modules/2.6.32-24-generic/build SUBDIRS=/home/chris/pwc-10.0.12-rc1 modules
make[1]: Entering directory `/usr/src/linux-headers-2.6.32-24-generic'
  CC [M]  /home/chris/pwc-10.0.12-rc1/pwc-if.o
In file included from /home/chris/pwc-10.0.12-rc1/pwc-if.c:69:
/home/chris/pwc-10.0.12-rc1/pwc.h:28:26: error: linux/config.h: No such file or directory
/home/chris/pwc-10.0.12-rc1/pwc.h:37:27: error: asm/semaphore.h: No such file or directory
/home/chris/pwc-10.0.12-rc1/pwc-if.c:166: error: variable ‘pwc_template’ has initializer but incomplete type
/home/chris/pwc-10.0.12-rc1/pwc-if.c:167: error: unknown field ‘owner’ specified in initializer
/home/chris/pwc-10.0.12-rc1/pwc-if.c:167: warning: excess elements in struct initializer
/home/chris/pwc-10.0.12-rc1/pwc-if.c:167: warning: (near initialization for ‘pwc_template’)
/home/chris/pwc-10.0.12-rc1/pwc-if.c:168: error: unknown field ‘name’ specified in initializer
/home/chris/pwc-10.0.12-rc1/pwc-if.c:168: warning: excess elements in struct initializer
/home/chris/pwc-10.0.12-rc1/pwc-if.c:168: warning: (near initialization for ‘pwc_template’)
/home/chris/pwc-10.0.12-rc1/pwc-if.c:169: error: unknown field ‘type’ specified in initializer
/home/chris/pwc-10.0.12-rc1/pwc-if.c:169: warning: excess elements in struct initializer
/home/chris/pwc-10.0.12-rc1/pwc-if.c:169: warning: (near initialization for ‘pwc_template’)
/home/chris/pwc-10.0.12-rc1/pwc-if.c:170: error: unknown field ‘hardware’ specified in initializer
/home/chris/pwc-10.0.12-rc1/pwc-if.c:170: error: ‘VID_HARDWARE_PWC’ undeclared here (not in a function)
/home/chris/pwc-10.0.12-rc1/pwc-if.c:170: warning: excess elements in struct initializer
/home/chris/pwc-10.0.12-rc1/pwc-if.c:170: warning: (near initialization for ‘pwc_template’)
/home/chris/pwc-10.0.12-rc1/pwc-if.c:171: error: unknown field ‘release’ specified in initializer
/home/chris/pwc-10.0.12-rc1/pwc-if.c:171: error: ‘video_device_release’ undeclared here (not in a function)
/home/chris/pwc-10.0.12-rc1/pwc-if.c:171: warning: excess elements in struct initializer
/home/chris/pwc-10.0.12-rc1/pwc-if.c:171: warning: (near initialization for ‘pwc_template’)
/home/chris/pwc-10.0.12-rc1/pwc-if.c:172: error: unknown field ‘fops’ specified in initializer
/home/chris/pwc-10.0.12-rc1/pwc-if.c:172: warning: excess elements in struct initializer
/home/chris/pwc-10.0.12-rc1/pwc-if.c:172: warning: (near initialization for ‘pwc_template’)
/home/chris/pwc-10.0.12-rc1/pwc-if.c:173: error: unknown field ‘minor’ specified in initializer
/home/chris/pwc-10.0.12-rc1/pwc-if.c:173: warning: excess elements in struct initializer
/home/chris/pwc-10.0.12-rc1/pwc-if.c:173: warning: (near initialization for ‘pwc_template’)
/home/chris/pwc-10.0.12-rc1/pwc-if.c: In function ‘pwc_isoc_init’:
/home/chris/pwc-10.0.12-rc1/pwc-if.c:921: warning: assignment from incompatible pointer type
/home/chris/pwc-10.0.12-rc1/pwc-if.c: At top level:
/home/chris/pwc-10.0.12-rc1/pwc-if.c:1017: warning: ‘struct class_device’ declared inside parameter list
/home/chris/pwc-10.0.12-rc1/pwc-if.c:1017: warning: its scope is only this definition or declaration, which is probably not what you want
/home/chris/pwc-10.0.12-rc1/pwc-if.c: In function ‘cd_to_pwc’:
/home/chris/pwc-10.0.12-rc1/pwc-if.c:1019: error: implicit declaration of function ‘to_video_device’
/home/chris/pwc-10.0.12-rc1/pwc-if.c:1019: warning: initialization makes pointer from integer without a cast
/home/chris/pwc-10.0.12-rc1/pwc-if.c:1020: error: implicit declaration of function ‘video_get_drvdata’
/home/chris/pwc-10.0.12-rc1/pwc-if.c:1020: warning: return makes pointer from integer without a cast
/home/chris/pwc-10.0.12-rc1/pwc-if.c: At top level:
/home/chris/pwc-10.0.12-rc1/pwc-if.c:1023: warning: ‘struct class_device’ declared inside parameter list
/home/chris/pwc-10.0.12-rc1/pwc-if.c: In function ‘show_pan_tilt’:
/home/chris/pwc-10.0.12-rc1/pwc-if.c:1025: warning: passing argument 1 of ‘cd_to_pwc’ from incompatible pointer type
/home/chris/pwc-10.0.12-rc1/pwc-if.c:1017: note: expected ‘struct class_device *’ but argument is of type ‘struct class_device *’
/home/chris/pwc-10.0.12-rc1/pwc-if.c: At top level:
/home/chris/pwc-10.0.12-rc1/pwc-if.c:1030: warning: ‘struct class_device’ declared inside parameter list
/home/chris/pwc-10.0.12-rc1/pwc-if.c: In function ‘store_pan_tilt’:
/home/chris/pwc-10.0.12-rc1/pwc-if.c:1032: warning: passing argument 1 of ‘cd_to_pwc’ from incompatible pointer type
/home/chris/pwc-10.0.12-rc1/pwc-if.c:1017: note: expected ‘struct class_device *’ but argument is of type ‘struct class_device *’
/home/chris/pwc-10.0.12-rc1/pwc-if.c: At top level:
/home/chris/pwc-10.0.12-rc1/pwc-if.c:1046: error: expected ‘)’ before ‘(’ token
/home/chris/pwc-10.0.12-rc1/pwc-if.c:1049: warning: ‘struct class_device’ declared inside parameter list
/home/chris/pwc-10.0.12-rc1/pwc-if.c: In function ‘show_snapshot_button_status’:
/home/chris/pwc-10.0.12-rc1/pwc-if.c:1051: warning: passing argument 1 of ‘cd_to_pwc’ from incompatible pointer type
/home/chris/pwc-10.0.12-rc1/pwc-if.c:1017: note: expected ‘struct class_device *’ but argument is of type ‘struct class_device *’
/home/chris/pwc-10.0.12-rc1/pwc-if.c: At top level:
/home/chris/pwc-10.0.12-rc1/pwc-if.c:1057: error: expected ‘)’ before ‘(’ token
/home/chris/pwc-10.0.12-rc1/pwc-if.c: In function ‘pwc_create_sysfs_files’:
/home/chris/pwc-10.0.12-rc1/pwc-if.c:1062: warning: initialization makes pointer from integer without a cast
/home/chris/pwc-10.0.12-rc1/pwc-if.c:1064: error: implicit declaration of function ‘video_device_create_file’
/home/chris/pwc-10.0.12-rc1/pwc-if.c:1064: error: ‘class_device_attr_pan_tilt’ undeclared (first use in this function)
/home/chris/pwc-10.0.12-rc1/pwc-if.c:1064: error: (Each undeclared identifier is reported only once
/home/chris/pwc-10.0.12-rc1/pwc-if.c:1064: error: for each function it appears in.)
/home/chris/pwc-10.0.12-rc1/pwc-if.c:1065: error: ‘class_device_attr_button’ undeclared (first use in this function)
/home/chris/pwc-10.0.12-rc1/pwc-if.c: In function ‘pwc_remove_sysfs_files’:
/home/chris/pwc-10.0.12-rc1/pwc-if.c:1070: warning: initialization makes pointer from integer without a cast
/home/chris/pwc-10.0.12-rc1/pwc-if.c:1072: error: implicit declaration of function ‘video_device_remove_file’
/home/chris/pwc-10.0.12-rc1/pwc-if.c:1072: error: ‘class_device_attr_pan_tilt’ undeclared (first use in this function)
/home/chris/pwc-10.0.12-rc1/pwc-if.c:1073: error: ‘class_device_attr_button’ undeclared (first use in this function)
/home/chris/pwc-10.0.12-rc1/pwc-if.c: In function ‘pwc_video_open’:
/home/chris/pwc-10.0.12-rc1/pwc-if.c:1112: error: implicit declaration of function ‘video_devdata’
/home/chris/pwc-10.0.12-rc1/pwc-if.c:1112: warning: initialization makes pointer from integer without a cast
/home/chris/pwc-10.0.12-rc1/pwc-if.c:1117: error: dereferencing pointer to incomplete type
/home/chris/pwc-10.0.12-rc1/pwc-if.c: In function ‘pwc_video_close’:
/home/chris/pwc-10.0.12-rc1/pwc-if.c:1231: error: dereferencing pointer to incomplete type
/home/chris/pwc-10.0.12-rc1/pwc-if.c: In function ‘pwc_video_read’:
/home/chris/pwc-10.0.12-rc1/pwc-if.c:1292: error: dereferencing pointer to incomplete type
/home/chris/pwc-10.0.12-rc1/pwc-if.c: In function ‘pwc_video_poll’:
/home/chris/pwc-10.0.12-rc1/pwc-if.c:1359: error: dereferencing pointer to incomplete type
/home/chris/pwc-10.0.12-rc1/pwc-if.c: In function ‘pwc_video_ioctl’:
/home/chris/pwc-10.0.12-rc1/pwc-if.c:1375: error: implicit declaration of function ‘video_usercopy’
/home/chris/pwc-10.0.12-rc1/pwc-if.c: In function ‘pwc_video_mmap’:
/home/chris/pwc-10.0.12-rc1/pwc-if.c:1388: error: dereferencing pointer to incomplete type
/home/chris/pwc-10.0.12-rc1/pwc-if.c: In function ‘usb_pwc_probe’:
/home/chris/pwc-10.0.12-rc1/pwc-if.c:1722: error: implicit declaration of function ‘video_device_alloc’
/home/chris/pwc-10.0.12-rc1/pwc-if.c:1722: warning: assignment makes pointer from integer without a cast
/home/chris/pwc-10.0.12-rc1/pwc-if.c:1729: error: invalid application of ‘sizeof’ to incomplete type ‘struct video_device’ 
/home/chris/pwc-10.0.12-rc1/pwc-if.c:1730: error: dereferencing pointer to incomplete type
/home/chris/pwc-10.0.12-rc1/pwc-if.c:1731: error: dereferencing pointer to incomplete type
/home/chris/pwc-10.0.12-rc1/pwc-if.c:1732: error: dereferencing pointer to incomplete type
/home/chris/pwc-10.0.12-rc1/pwc-if.c:1733: error: implicit declaration of function ‘video_set_drvdata’
/home/chris/pwc-10.0.12-rc1/pwc-if.c:1756: error: dereferencing pointer to incomplete type
/home/chris/pwc-10.0.12-rc1/pwc-if.c:1757: error: implicit declaration of function ‘video_register_device’
/home/chris/pwc-10.0.12-rc1/pwc-if.c:1757: error: ‘VFL_TYPE_GRABBER’ undeclared (first use in this function)
/home/chris/pwc-10.0.12-rc1/pwc-if.c:1760: error: implicit declaration of function ‘video_device_release’
/home/chris/pwc-10.0.12-rc1/pwc-if.c:1765: error: dereferencing pointer to incomplete type
/home/chris/pwc-10.0.12-rc1/pwc-if.c: In function ‘usb_pwc_disconnect’:
/home/chris/pwc-10.0.12-rc1/pwc-if.c:1819: error: implicit declaration of function ‘video_unregister_device’
make[2]: *** [/home/chris/pwc-10.0.12-rc1/pwc-if.o] Error 1
make[1]: *** [_module_/home/chris/pwc-10.0.12-rc1] Error 2
make[1]: Leaving directory `/usr/src/linux-headers-2.6.32-24-generic'
make: *** [all] Error 2

```I followed the directions to remove the old module which gave me the gray screen, but now I don't get anything from Cheese or Camorama but the "No Input" error. lsusb shows the webcam with its proper name, but I can't get any applications to detect it. Can anybody help me out with this?

---

### Post by digbysellers on 2010-08-08
I believe I am in the same situation.

---

### Post by Zookalicious on 2010-08-08
After some research apparently the problems I am having are mostly because I can't compile the driver since the newer linux kernel doesn't have config.h......

Can anyone help us out with this? Is there a precompiled driver somewhere out there for Ubuntu or a way to successfully compile this one? Otherwise this webcam is going in the garbage...

---

### Post by robert shearer on 2010-08-08
what happens when you run...
```
LD_PRELOAD=/usr/lib/libv4l/v4l1compat.so cheese 
```

in a terminal.

---

### Post by whyameye on 2010-09-28
> **robert shearer said:**
> what happens when you run...
```
LD_PRELOAD=/usr/lib/libv4l/v4l1compat.so cheese 
```

in a terminal.

still a black screen

I also have a logitech quickcam pro 4000 and it is not working. Worked in earlier versions of ubuntu...

---

### Post by Chriis on 2010-10-03
exactly same problem in here
keep searchin

---

### Post by Keronn on 2010-11-05
Hi,

Do you know if the issue is still occuring, with Ubuntu 10.10 ?


[EDIT]

Ok, I was asking that because I installed Ubuntu on a computer and I noticed the issue with a Quickcam.  

But yesterday I met the user, I checked his computer and his webcam is now working well under Lucid (with Cheese and Skype)

Some update might have fixed the issue.

---

### Post by theSWiT on 2010-11-19
I'm having the same problem.  The video from my QuickCam Pro 4000 is just a black square.  The audio from it works.  I tried to install the pwc driver manually and the make command failed mentioning linux/config.h was missing.

I am running Ubuntu 10.10 64bit

My second machine is running 10.04 64bit and the Pro 4000 "just worked" in Cheese.

---

### Post by p4trykx on 2011-01-14
I'm running Ubuntu 10.10 with 2.6.35-24-generic kernel and also have problems with pwc driver.
It seems to work when i plug the camera first time after reboot but when I disconnect it and plug it in again cheese or mplayer shows black screen.
But I've found a solution. You just have to unload pwc module and then plug the camera in.

---

### Post by p4trykx on 2011-01-14
I'm running Ubuntu 10.10 with 2.6.35-24-generic kernel and also have problems with pwc driver.
It seems to work when I plug the camera first time after reboot but when I disconnect it and plug it in again cheese or mplayer shows black screen.
But I've found a solution. You just have to unload pwc module and then plug the camera in.
It's a known bug 
[https://bugs.launchpad.net/ubuntu/+source/linux/+bug/443278](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/443278)

---

### Post by nanonils on 2011-01-16
Can you please say how you "unload"?

I have the same problem: just a black screen but camera is showing as recognized and green light is coming on. Presario CQ56 with 10.10 64bit.

EDIT: enter in terminal: "modprobe -r pwc", that fixed my problem as well.

---

### Post by craver84 on 2011-02-16
I have the same problem... news?

---

### Post by nanonils on 2011-02-16
> **craver84 said:**
> I have the same problem... news?

As mentioned in my EDIT above, this worked for me: 
"enter in terminal: "modprobe -r pwc", that fixed my problem as well."

---

### Post by craver84 on 2011-02-16
I'm sorry... 
Know it works! many thanks ):P

---

### Post by nanonils on 2011-02-16
> **craver84 said:**
> I'm sorry... 
Know it works! many thanks ):P

Great! I got a little distressed myself when I realized mine wasn't working...

---

