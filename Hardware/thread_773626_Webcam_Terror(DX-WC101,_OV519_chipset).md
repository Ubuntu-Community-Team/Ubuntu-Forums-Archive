---
title: "Webcam Terror(DX-WC101, OV519 chipset)"
date: 2008-04-29
forum: Hardware
---

### Post by survient on 2008-04-29
ok, trying to install this webcam, trying to use that easycam2 program, but I've also tried to compile the drivers from source. I get similar errors either way:
```

user@dewicide:~$ lauchcam2
Reading package lists... Done
Building dependency tree       
Reading state information... Done
linux-headers-2.6.24-16-generic is already the newest version.
linux-headers-2.6.24-16-generic set to manually installed.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
ERROR: Module ov51x does not exist in /proc/modules
cp: cannot stat `/lib/modules/2.6.24-16-generic/kernel/drivers/usb/media/*': No such file or directory
cd: 1: can't cd to /lib/modules/2.6.24-16-generic/kernel/drivers/usb/media/
SSSSSSSSSSSSSSSSSSSSSSSSmake -C /lib/modules/2.6.24-16-generic/build M=/usr/share/EasyCam2/drivers/ov51x clean
make[1]: Entering directory `/usr/src/linux-headers-2.6.24-16-generic'
make[1]: Leaving directory `/usr/src/linux-headers-2.6.24-16-generic'
make -C /lib/modules/2.6.24-16-generic/build M=/usr/share/EasyCam2/drivers/ov51x modules
make[1]: Entering directory `/usr/src/linux-headers-2.6.24-16-generic'
  CC [M]  /usr/share/EasyCam2/drivers/ov51x/ov51x.o
/usr/share/EasyCam2/drivers/ov51x/ov51x.c:42:26: error: linux/config.h: No such file or directory
/usr/share/EasyCam2/drivers/ov51x/ov51x.c:207: error: expected ‘)’ before string constant
/usr/share/EasyCam2/drivers/ov51x/ov51x.c:209: error: expected ‘)’ before string constant
/usr/share/EasyCam2/drivers/ov51x/ov51x.c:211: error: expected ‘)’ before string constant
/usr/share/EasyCam2/drivers/ov51x/ov51x.c:213: error: expected ‘)’ before string constant
/usr/share/EasyCam2/drivers/ov51x/ov51x.c:216: error: expected ‘)’ before string constant
/usr/share/EasyCam2/drivers/ov51x/ov51x.c:220: error: expected ‘)’ before string constant
/usr/share/EasyCam2/drivers/ov51x/ov51x.c:223: error: expected ‘)’ before string constant
/usr/share/EasyCam2/drivers/ov51x/ov51x.c:227: error: expected ‘)’ before string constant
/usr/share/EasyCam2/drivers/ov51x/ov51x.c:229: error: expected ‘)’ before string constant
/usr/share/EasyCam2/drivers/ov51x/ov51x.c:231: error: expected ‘)’ before string constant
/usr/share/EasyCam2/drivers/ov51x/ov51x.c:234: error: expected ‘)’ before string constant
/usr/share/EasyCam2/drivers/ov51x/ov51x.c:236: error: expected ‘)’ before string constant
/usr/share/EasyCam2/drivers/ov51x/ov51x.c:239: error: expected ‘)’ before string constant
/usr/share/EasyCam2/drivers/ov51x/ov51x.c:242: error: expected ‘)’ before string constant
/usr/share/EasyCam2/drivers/ov51x/ov51x.c:244: error: expected ‘)’ before string constant
/usr/share/EasyCam2/drivers/ov51x/ov51x.c:246: error: expected ‘)’ before string constant
/usr/share/EasyCam2/drivers/ov51x/ov51x.c:248: error: expected ‘)’ before string constant
/usr/share/EasyCam2/drivers/ov51x/ov51x.c:250: error: expected ‘)’ before string constant
/usr/share/EasyCam2/drivers/ov51x/ov51x.c:252: error: expected ‘)’ before string constant
/usr/share/EasyCam2/drivers/ov51x/ov51x.c:254: error: expected ‘)’ before string constant
/usr/share/EasyCam2/drivers/ov51x/ov51x.c:256: error: expected ‘)’ before string constant
/usr/share/EasyCam2/drivers/ov51x/ov51x.c:258: error: expected ‘)’ before string constant
/usr/share/EasyCam2/drivers/ov51x/ov51x.c:260: error: expected ‘)’ before string constant
/usr/share/EasyCam2/drivers/ov51x/ov51x.c:262: error: expected ‘)’ before string constant
/usr/share/EasyCam2/drivers/ov51x/ov51x.c:264: error: expected ‘)’ before string constant
/usr/share/EasyCam2/drivers/ov51x/ov51x.c:267: error: expected ‘)’ before string constant
/usr/share/EasyCam2/drivers/ov51x/ov51x.c:270: error: expected ‘)’ before string constant
/usr/share/EasyCam2/drivers/ov51x/ov51x.c:272: error: expected ‘)’ before string constant
/usr/share/EasyCam2/drivers/ov51x/ov51x.c:274: error: expected ‘)’ before string constant
/usr/share/EasyCam2/drivers/ov51x/ov51x.c:276: error: expected ‘)’ before string constant
/usr/share/EasyCam2/drivers/ov51x/ov51x.c:278: error: expected ‘)’ before string constant
/usr/share/EasyCam2/drivers/ov51x/ov51x.c:280: error: expected ‘)’ before string constant
/usr/share/EasyCam2/drivers/ov51x/ov51x.c:282: error: expected ‘)’ before string constant
/usr/share/EasyCam2/drivers/ov51x/ov51x.c:285: error: expected ‘)’ before string constant
/usr/share/EasyCam2/drivers/ov51x/ov51x.c:288: error: expected ‘)’ before string constant
/usr/share/EasyCam2/drivers/ov51x/ov51x.c:290: error: expected ‘)’ before string constant
/usr/share/EasyCam2/drivers/ov51x/ov51x.c:292: error: expected ‘)’ before string constant
/usr/share/EasyCam2/drivers/ov51x/ov51x.c:294: error: expected ‘)’ before string constant
/usr/share/EasyCam2/drivers/ov51x/ov51x.c: In function ‘ov51x_init_isoc’:
/usr/share/EasyCam2/drivers/ov51x/ov51x.c:5449: warning: assignment from incompatible pointer type
/usr/share/EasyCam2/drivers/ov51x/ov51x.c: In function ‘ov51x_v4l1_open’:
/usr/share/EasyCam2/drivers/ov51x/ov51x.c:5705: error: implicit declaration of function ‘video_devdata’
/usr/share/EasyCam2/drivers/ov51x/ov51x.c:5705: warning: initialization makes pointer from integer without a cast
/usr/share/EasyCam2/drivers/ov51x/ov51x.c:5707: error: implicit declaration of function ‘video_get_drvdata’
/usr/share/EasyCam2/drivers/ov51x/ov51x.c:5707: warning: initialization makes pointer from integer without a cast
/usr/share/EasyCam2/drivers/ov51x/ov51x.c: In function ‘ov51x_v4l1_close’:
/usr/share/EasyCam2/drivers/ov51x/ov51x.c:5784: warning: initialization makes pointer from integer without a cast
/usr/share/EasyCam2/drivers/ov51x/ov51x.c: In function ‘ov51x_v4l1_ioctl_internal’:
/usr/share/EasyCam2/drivers/ov51x/ov51x.c:5842: warning: initialization makes pointer from integer without a cast
/usr/share/EasyCam2/drivers/ov51x/ov51x.c:6246: error: dereferencing pointer to incomplete type
/usr/share/EasyCam2/drivers/ov51x/ov51x.c: In function ‘ov51x_v4l1_ioctl’:
/usr/share/EasyCam2/drivers/ov51x/ov51x.c:6358: warning: initialization makes pointer from integer without a cast
/usr/share/EasyCam2/drivers/ov51x/ov51x.c:6364: error: implicit declaration of function ‘video_usercopy’
/usr/share/EasyCam2/drivers/ov51x/ov51x.c: In function ‘ov51x_v4l1_read’:
/usr/share/EasyCam2/drivers/ov51x/ov51x.c:6384: warning: initialization makes pointer from integer without a cast
/usr/share/EasyCam2/drivers/ov51x/ov51x.c: In function ‘ov51x_v4l1_mmap’:
/usr/share/EasyCam2/drivers/ov51x/ov51x.c:6554: warning: initialization makes pointer from integer without a cast
/usr/share/EasyCam2/drivers/ov51x/ov51x.c: At top level:
/usr/share/EasyCam2/drivers/ov51x/ov51x.c:6625: error: variable ‘vdev_template’ has initializer but incomplete type
/usr/share/EasyCam2/drivers/ov51x/ov51x.c:6626: error: unknown field ‘owner’ specified in initializer
/usr/share/EasyCam2/drivers/ov51x/ov51x.c:6626: warning: excess elements in struct initializer
/usr/share/EasyCam2/drivers/ov51x/ov51x.c:6626: warning: (near initialization for ‘vdev_template’)
/usr/share/EasyCam2/drivers/ov51x/ov51x.c:6627: error: unknown field ‘name’ specified in initializer
/usr/share/EasyCam2/drivers/ov51x/ov51x.c:6627: warning: excess elements in struct initializer
/usr/share/EasyCam2/drivers/ov51x/ov51x.c:6627: warning: (near initialization for ‘vdev_template’)
/usr/share/EasyCam2/drivers/ov51x/ov51x.c:6628: error: unknown field ‘type’ specified in initializer
/usr/share/EasyCam2/drivers/ov51x/ov51x.c:6628: warning: excess elements in struct initializer
/usr/share/EasyCam2/drivers/ov51x/ov51x.c:6628: warning: (near initialization for ‘vdev_template’)
/usr/share/EasyCam2/drivers/ov51x/ov51x.c:6629: error: unknown field ‘hardware’ specified in initializer
/usr/share/EasyCam2/drivers/ov51x/ov51x.c:6629: error: ‘VID_HARDWARE_OV511’ undeclared here (not in a function)
/usr/share/EasyCam2/drivers/ov51x/ov51x.c:6629: warning: excess elements in struct initializer
/usr/share/EasyCam2/drivers/ov51x/ov51x.c:6629: warning: (near initialization for ‘vdev_template’)
/usr/share/EasyCam2/drivers/ov51x/ov51x.c:6630: error: unknown field ‘fops’ specified in initializer
/usr/share/EasyCam2/drivers/ov51x/ov51x.c:6630: warning: excess elements in struct initializer
/usr/share/EasyCam2/drivers/ov51x/ov51x.c:6630: warning: (near initialization for ‘vdev_template’)
/usr/share/EasyCam2/drivers/ov51x/ov51x.c:6632: error: unknown field ‘release’ specified in initializer
/usr/share/EasyCam2/drivers/ov51x/ov51x.c:6632: error: ‘video_device_release’ undeclared here (not in a function)
/usr/share/EasyCam2/drivers/ov51x/ov51x.c:6632: warning: excess elements in struct initializer
/usr/share/EasyCam2/drivers/ov51x/ov51x.c:6632: warning: (near initialization for ‘vdev_template’)
/usr/share/EasyCam2/drivers/ov51x/ov51x.c:6634: error: unknown field ‘minor’ specified in initializer
/usr/share/EasyCam2/drivers/ov51x/ov51x.c:6634: warning: excess elements in struct initializer
/usr/share/EasyCam2/drivers/ov51x/ov51x.c:6634: warning: (near initialization for ‘vdev_template’)
/usr/share/EasyCam2/drivers/ov51x/ov51x.c: In function ‘ov51x_probe’:
/usr/share/EasyCam2/drivers/ov51x/ov51x.c:8298: error: implicit declaration of function ‘video_device_alloc’
/usr/share/EasyCam2/drivers/ov51x/ov51x.c:8298: warning: assignment makes pointer from integer without a cast
/usr/share/EasyCam2/drivers/ov51x/ov51x.c:8302: error: dereferencing pointer to incomplete type
/usr/share/EasyCam2/drivers/ov51x/ov51x.c:8302: error: dereferencing pointer to incomplete type
/usr/share/EasyCam2/drivers/ov51x/ov51x.c:8302: error: dereferencing pointer to incomplete type
/usr/share/EasyCam2/drivers/ov51x/ov51x.c:8304: error: dereferencing pointer to incomplete type
/usr/share/EasyCam2/drivers/ov51x/ov51x.c:8306: error: implicit declaration of function ‘video_set_drvdata’
/usr/share/EasyCam2/drivers/ov51x/ov51x.c:8314: error: implicit declaration of function ‘video_register_device’
/usr/share/EasyCam2/drivers/ov51x/ov51x.c:8314: error: ‘VFL_TYPE_GRABBER’ undeclared (first use in this function)
/usr/share/EasyCam2/drivers/ov51x/ov51x.c:8314: error: (Each undeclared identifier is reported only once
/usr/share/EasyCam2/drivers/ov51x/ov51x.c:8314: error: for each function it appears in.)
/usr/share/EasyCam2/drivers/ov51x/ov51x.c:8321: error: dereferencing pointer to incomplete type
/usr/share/EasyCam2/drivers/ov51x/ov51x.c:8331: error: dereferencing pointer to incomplete type
/usr/share/EasyCam2/drivers/ov51x/ov51x.c:8354: error: dereferencing pointer to incomplete type
/usr/share/EasyCam2/drivers/ov51x/ov51x.c:8355: error: implicit declaration of function ‘video_device_release’
/usr/share/EasyCam2/drivers/ov51x/ov51x.c:8357: error: implicit declaration of function ‘video_unregister_device’
/usr/share/EasyCam2/drivers/ov51x/ov51x.c: At top level:
/usr/share/EasyCam2/drivers/ov51x/ov51x.c:8464: error: unknown field ‘owner’ specified in initializer
/usr/share/EasyCam2/drivers/ov51x/ov51x.c:8464: warning: initialization from incompatible pointer type
make[2]: *** [/usr/share/EasyCam2/drivers/ov51x/ov51x.o] Error 1
make[1]: *** [_module_/usr/share/EasyCam2/drivers/ov51x] Error 2
make[1]: Leaving directory `/usr/src/linux-headers-2.6.24-16-generic'
make: *** [all] Error 2

```
any ideas for resolving this? I tried replacing the lines that had "include linux/config.h" to "include linux/autoconf.h" in the source but it gave the same errors. This is the same error running the generic kernel on 32 bit and the realtime kernel(ubuntustudio) on 64 bit, so it doesn't seem to be bit or kernel specific..... I saw this thread [http://ubuntuforums.org/showthread.php?t=551009](http://ubuntuforums.org/showthread.php?t=551009) and the guy said it seemed to work, but didn't specify really which version he downloaded, I tried all 3, all failed....... I'm missing something, I just need help figuring out what. Thanks.

---

