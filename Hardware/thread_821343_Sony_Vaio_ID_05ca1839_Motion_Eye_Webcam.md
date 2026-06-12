---
title: "Sony Vaio ID 05ca:1839 Motion Eye Webcam"
date: 2008-06-07
forum: Hardware
---

### Post by steve101101 on 2008-06-07
I have a Sony Vaio CR120 with a Motion Eye Webcam that doesn't work with the newest kernel. It seems that I would be able to get it to work with kernels 2.6.24-17-generic or 2.6.24-16-generic, but 8.04 Ubuntu is running 2.6.24-18-generic. 

Here is the output for the lsusb command. 
```

steven@steven-laptop:~/Desktop/r5u870-VCC6$ lsusb
Bus 006 Device 001: ID 0000:0000  
Bus 005 Device 001: ID 0000:0000  
Bus 004 Device 001: ID 0000:0000  
Bus 003 Device 001: ID 0000:0000  
Bus 007 Device 001: ID 0000:0000  
Bus 002 Device 001: ID 0000:0000  
Bus 001 Device 002: ID 05ca:1839 Ricoh Co., Ltd 
Bus 001 Device 001: ID 0000:0000  

```

I have some experience with linux and can usually get around okay, but no ones solution on the forums so far. Every ones fix fails when i try to compile it on the make command. It looks something like this ...

```

steven@steven-laptop:~/Desktop/r5u870-VCC6$ make
make -C /lib/modules/2.6.24-18-generic/build M=/home/steven/Desktop/r5u870-VCC6 V=0 modules
make[1]: Entering directory `/usr/src/linux-headers-2.6.24-18-generic'
  CC [M]  /home/steven/Desktop/r5u870-VCC6/r5u870_md.o
In file included from /home/steven/Desktop/r5u870-VCC6/r5u870_md.c:55:
/home/steven/Desktop/r5u870-VCC6/usbcam.h:36:29: error: media/video-buf.h: No such file or directory
/home/steven/Desktop/r5u870-VCC6/r5u870_md.c:3064: fatal error: opening dependency file /home/steven/Desktop/r5u870-VCC6/.r5u870_md.o.d: Permission denied
compilation terminated.
make[2]: *** [/home/steven/Desktop/r5u870-VCC6/r5u870_md.o] Error 1
make[1]: *** [_module_/home/steven/Desktop/r5u870-VCC6] Error 2
make[1]: Leaving directory `/usr/src/linux-headers-2.6.24-18-generic'
make: *** [all] Error 2

```

Thanks for the help.

---

### Post by Nepherte on 2008-06-07
Looks like a permisson error or it can't find the file:
```
/home/steven/Desktop/r5u870-VCC6/usbcam.h:36:29: error: media/video-buf.h: No such file or directory
/home/steven/Desktop/r5u870-VCC6/r5u870_md.c:3064: fatal error: opening dependency file /home/steven/Desktop/r5u870-VCC6/.r5u870_md.o.d: Permission denied
```

I installed the same driver on my Sony Vaio SZ61X/N without trouble.

I suggest you check the permissions of all the files (ls -l) and see if you have the necessary rights. Normally you shouldn't run the make command with sudo privileges but you can always try.

---

### Post by steve101101 on 2008-06-07
Well I ran it with sudo, but now i get a different error ...

```

steven@steven-laptop:~/Desktop/r5u870-VCC6$ sudo make
[sudo] password for steven: 
make -C /lib/modules/2.6.24-18-generic/build M=/home/steven/Desktop/r5u870-VCC6 V=0 modules
make[1]: Entering directory `/usr/src/linux-headers-2.6.24-18-generic'
  CC [M]  /home/steven/Desktop/r5u870-VCC6/r5u870_md.o
In file included from /home/steven/Desktop/r5u870-VCC6/r5u870_md.c:55:
/home/steven/Desktop/r5u870-VCC6/usbcam.h:36:29: error: media/video-buf.h: No such file or directory
make[2]: *** [/home/steven/Desktop/r5u870-VCC6/r5u870_md.o] Error 1
make[1]: *** [_module_/home/steven/Desktop/r5u870-VCC6] Error 2
make[1]: Leaving directory `/usr/src/linux-headers-2.6.24-18-generic'
make: *** [all] Error 2

```

---

### Post by steve101101 on 2008-06-07
after adding the media/video-buf.h file to the folder i get this output ...

```

include/media/video-buf.h:262: error: expected identifier or &#8216;(&#8217; before &#8216;-&#8217; token
include/media/video-buf.h:263: error: expected identifier or &#8216;(&#8217; before &#8216;-&#8217; token
include/media/video-buf.h:265: error: expected identifier or &#8216;(&#8217; before &#8216;-&#8217; token
include/media/video-buf.h:267: error: expected identifier or &#8216;(&#8217; before &#8216;-&#8217; token
include/media/video-buf.h:268: error: expected identifier or &#8216;(&#8217; before &#8216;-&#8217; token
include/media/video-buf.h:269: error: expected identifier or &#8216;(&#8217; before &#8216;-&#8217; token
include/media/video-buf.h:271: error: expected identifier or &#8216;(&#8217; before &#8216;-&#8217; token
include/media/video-buf.h:272: error: expected identifier or &#8216;(&#8217; before &#8216;-&#8217; token
include/media/video-buf.h:275: error: expected identifier or &#8216;(&#8217; before &#8216;-&#8217; token
include/media/video-buf.h:278: error: expected identifier or &#8216;(&#8217; before &#8216;-&#8217; token
include/media/video-buf.h:281: error: expected identifier or &#8216;(&#8217; before &#8216;-&#8217; token
include/media/video-buf.h:285: error: expected identifier or &#8216;(&#8217; before &#8216;-&#8217; token
include/media/video-buf.h:286: error: expected identifier or &#8216;(&#8217; before &#8216;-&#8217; token
include/media/video-buf.h:288: error: expected identifier or &#8216;(&#8217; before &#8216;-&#8217; token
In file included from /home/steven/Desktop/r5u870-VCC6/r5u870_md.c:55:
/home/steven/Desktop/r5u870-VCC6/usbcam.h:178: error: expected specifier-qualifier-list before &#8216;usbcam_minidrv_t&#8217;
/home/steven/Desktop/r5u870-VCC6/usbcam.h:433: error: expected &#8216;)&#8217; before &#8216;*&#8217; token
/home/steven/Desktop/r5u870-VCC6/usbcam.h:448: error: expected &#8216;)&#8217; before &#8216;*&#8217; token
/home/steven/Desktop/r5u870-VCC6/r5u870_md.c: In function &#8216;r5u870_get_ctrl&#8217;:
/home/steven/Desktop/r5u870-VCC6/r5u870_md.c:209: error: &#8216;struct usbcam_dev&#8217; has no member named &#8216;ud_minidrv_data&#8217;
/home/steven/Desktop/r5u870-VCC6/r5u870_md.c: In function &#8216;r5u870_query_ctrl&#8217;:
/home/steven/Desktop/r5u870-VCC6/r5u870_md.c:221: error: &#8216;struct usbcam_dev&#8217; has no member named &#8216;ud_minidrv_data&#8217;
/home/steven/Desktop/r5u870-VCC6/r5u870_md.c: In function &#8216;r5u870_set_gen_reg&#8217;:
/home/steven/Desktop/r5u870-VCC6/r5u870_md.c:279: error: &#8216;struct usbcam_dev&#8217; has no member named &#8216;ud_dev_name&#8217;
/home/steven/Desktop/r5u870-VCC6/r5u870_md.c: In function &#8216;r5u870_microcode_upload&#8217;:
/home/steven/Desktop/r5u870-VCC6/r5u870_md.c:301: error: &#8216;struct usbcam_dev&#8217; has no member named &#8216;ud_debug&#8217;
/home/steven/Desktop/r5u870-VCC6/r5u870_md.c:301: error: &#8216;struct usbcam_dev&#8217; has no member named &#8216;ud_debug&#8217;
/home/steven/Desktop/r5u870-VCC6/r5u870_md.c:301: error: &#8216;struct usbcam_dev&#8217; has no member named &#8216;ud_dev_name&#8217;
/home/steven/Desktop/r5u870-VCC6/r5u870_md.c:309: error: &#8216;struct usbcam_dev&#8217; has no member named &#8216;ud_dev_name&#8217;
/home/steven/Desktop/r5u870-VCC6/r5u870_md.c:320: error: &#8216;struct usbcam_dev&#8217; has no member named &#8216;ud_dev_name&#8217;
/home/steven/Desktop/r5u870-VCC6/r5u870_md.c:331: error: &#8216;struct usbcam_dev&#8217; has no member named &#8216;ud_dev_name&#8217;
/home/steven/Desktop/r5u870-VCC6/r5u870_md.c:360: error: &#8216;struct usbcam_dev&#8217; has no member named &#8216;ud_dev_name&#8217;
/home/steven/Desktop/r5u870-VCC6/r5u870_md.c:365: error: &#8216;struct usbcam_dev&#8217; has no member named &#8216;ud_dev_name&#8217;
/home/steven/Desktop/r5u870-VCC6/r5u870_md.c: In function &#8216;r5u870_microcode_get_state&#8217;:
/home/steven/Desktop/r5u870-VCC6/r5u870_md.c:383: error: &#8216;struct usbcam_dev&#8217; has no member named &#8216;ud_debug&#8217;
/home/steven/Desktop/r5u870-VCC6/r5u870_md.c:383: error: &#8216;struct usbcam_dev&#8217; has no member named &#8216;ud_debug&#8217;
/home/steven/Desktop/r5u870-VCC6/r5u870_md.c:383: error: &#8216;struct usbcam_dev&#8217; has no member named &#8216;ud_dev_name&#8217;
/home/steven/Desktop/r5u870-VCC6/r5u870_md.c:393: error: &#8216;struct usbcam_dev&#8217; has no member named &#8216;ud_dev_name&#8217;
/home/steven/Desktop/r5u870-VCC6/r5u870_md.c:397: error: &#8216;struct usbcam_dev&#8217; has no member named &#8216;ud_debug&#8217;
/home/steven/Desktop/r5u870-VCC6/r5u870_md.c:397: error: &#8216;struct usbcam_dev&#8217; has no member named &#8216;ud_debug&#8217;
/home/steven/Desktop/r5u870-VCC6/r5u870_md.c:397: error: &#8216;struct usbcam_dev&#8217; has no member named &#8216;ud_dev_name&#8217;
/home/steven/Desktop/r5u870-VCC6/r5u870_md.c: In function &#8216;r5u870_microcode_get_ver&#8217;:
/home/steven/Desktop/r5u870-VCC6/r5u870_md.c:408: error: &#8216;struct usbcam_dev&#8217; has no member named &#8216;ud_debug&#8217;
/home/steven/Desktop/r5u870-VCC6/r5u870_md.c:408: error: &#8216;struct usbcam_dev&#8217; has no member named &#8216;ud_debug&#8217;
/home/steven/Desktop/r5u870-VCC6/r5u870_md.c:408: error: &#8216;struct usbcam_dev&#8217; has no member named &#8216;ud_dev_name&#8217;
/home/steven/Desktop/r5u870-VCC6/r5u870_md.c:418: error: &#8216;struct usbcam_dev&#8217; has no member named &#8216;ud_dev_name&#8217;
/home/steven/Desktop/r5u870-VCC6/r5u870_md.c:423: error: &#8216;struct usbcam_dev&#8217; has no member named &#8216;ud_debug&#8217;
/home/steven/Desktop/r5u870-VCC6/r5u870_md.c:423: error: &#8216;struct usbcam_dev&#8217; has no member named &#8216;ud_debug&#8217;
/home/steven/Desktop/r5u870-VCC6/r5u870_md.c:423: error: &#8216;struct usbcam_dev&#8217; has no member named &#8216;ud_dev_name&#8217;
/home/steven/Desktop/r5u870-VCC6/r5u870_md.c: In function &#8216;r5u870_microcode_enable&#8217;:
/home/steven/Desktop/r5u870-VCC6/r5u870_md.c:433: error: &#8216;struct usbcam_dev&#8217; has no member named &#8216;ud_debug&#8217;
/home/steven/Desktop/r5u870-VCC6/r5u870_md.c:433: error: &#8216;struct usbcam_dev&#8217; has no member named &#8216;ud_debug&#8217;
/home/steven/Desktop/r5u870-VCC6/r5u870_md.c:433: error: &#8216;struct usbcam_dev&#8217; has no member named &#8216;ud_dev_name&#8217;
/home/steven/Desktop/r5u870-VCC6/r5u870_md.c:444: error: &#8216;struct usbcam_dev&#8217; has no member named &#8216;ud_dev_name&#8217;
/home/steven/Desktop/r5u870-VCC6/r5u870_md.c: In function &#8216;r5u870_microcode_reset&#8217;:
/home/steven/Desktop/r5u870-VCC6/r5u870_md.c:454: error: &#8216;struct usbcam_dev&#8217; has no member named &#8216;ud_debug&#8217;
/home/steven/Desktop/r5u870-VCC6/r5u870_md.c:454: error: &#8216;struct usbcam_dev&#8217; has no member named &#8216;ud_debug&#8217;
/home/steven/Desktop/r5u870-VCC6/r5u870_md.c:454: error: &#8216;struct usbcam_dev&#8217; has no member named &#8216;ud_dev_name&#8217;
/home/steven/Desktop/r5u870-VCC6/r5u870_md.c: In function &#8216;r5u870_dev_test_234&#8217;:
/home/steven/Desktop/r5u870-VCC6/r5u870_md.c:481: error: &#8216;struct usbcam_dev&#8217; has no member named &#8216;ud_dev_name&#8217;
/home/steven/Desktop/r5u870-VCC6/r5u870_md.c:499: error: &#8216;struct usbcam_dev&#8217; has no member named &#8216;ud_dev_name&#8217;
/home/steven/Desktop/r5u870-VCC6/r5u870_md.c:509: error: &#8216;struct usbcam_dev&#8217; has no member named &#8216;ud_dev_name&#8217;
/home/steven/Desktop/r5u870-VCC6/r5u870_md.c: In function &#8216;r5u870_dev_init&#8217;:
/home/steven/Desktop/r5u870-VCC6/r5u870_md.c:562: error: &#8216;struct usbcam_dev&#8217; has no member named &#8216;ud_dev_name&#8217;
/home/steven/Desktop/r5u870-VCC6/r5u870_md.c: In function &#8216;r5u870_decide_pkt_wdm&#8217;:
/home/steven/Desktop/r5u870-VCC6/r5u870_md.c:757: error: &#8216;struct usbcam_dev&#8217; has no member named &#8216;ud_debug&#8217;
/home/steven/Desktop/r5u870-VCC6/r5u870_md.c:757: error: &#8216;struct usbcam_dev&#8217; has no member named &#8216;ud_debug&#8217;
/home/steven/Desktop/r5u870-VCC6/r5u870_md.c:757: error: &#8216;struct usbcam_dev&#8217; has no member named &#8216;ud_dev_name&#8217;
/home/steven/Desktop/r5u870-VCC6/r5u870_md.c:769: error: &#8216;struct usbcam_dev&#8217; has no member named &#8216;ud_format&#8217;
/home/steven/Desktop/r5u870-VCC6/r5u870_md.c:774: error: &#8216;struct usbcam_dev&#8217; has no member named &#8216;ud_debug&#8217;
/home/steven/Desktop/r5u870-VCC6/r5u870_md.c:774: error: &#8216;struct usbcam_dev&#8217; has no member named &#8216;ud_debug&#8217;
/home/steven/Desktop/r5u870-VCC6/r5u870_md.c:774: error: &#8216;struct usbcam_dev&#8217; has no member named &#8216;ud_dev_name&#8217;
/home/steven/Desktop/r5u870-VCC6/r5u870_md.c:774: error: &#8216;struct usbcam_dev&#8217; has no member named &#8216;ud_format&#8217;
/home/steven/Desktop/r5u870-VCC6/r5u870_md.c:792: error: &#8216;struct usbcam_dev&#8217; has no member named &#8216;ud_debug&#8217;
/home/steven/Desktop/r5u870-VCC6/r5u870_md.c:792: error: &#8216;struct usbcam_dev&#8217; has no member named &#8216;ud_debug&#8217;
/home/steven/Desktop/r5u870-VCC6/r5u870_md.c:792: error: &#8216;struct usbcam_dev&#8217; has no member named &#8216;ud_dev_name&#8217;
/home/steven/Desktop/r5u870-VCC6/r5u870_md.c:803: error: &#8216;struct usbcam_dev&#8217; has no member named &#8216;ud_format&#8217;
/home/steven/Desktop/r5u870-VCC6/r5u870_md.c:808: error: &#8216;struct usbcam_dev&#8217; has no member named &#8216;ud_debug&#8217;
/home/steven/Desktop/r5u870-VCC6/r5u870_md.c:808: error: &#8216;struct usbcam_dev&#8217; has no member named &#8216;ud_debug&#8217;
/home/steven/Desktop/r5u870-VCC6/r5u870_md.c:808: error: &#8216;struct usbcam_dev&#8217; has no member named &#8216;ud_dev_name&#8217;
/home/steven/Desktop/r5u870-VCC6/r5u870_md.c: In function &#8216;r5u870_set_manual_ctrls_wdm&#8217;:
/home/steven/Desktop/r5u870-VCC6/r5u870_md.c:835: error: &#8216;struct usbcam_dev&#8217; has no member named &#8216;ud_debug&#8217;
/home/steven/Desktop/r5u870-VCC6/r5u870_md.c:835: error: &#8216;struct usbcam_dev&#8217; has no member named &#8216;ud_debug&#8217;
/home/steven/Desktop/r5u870-VCC6/r5u870_md.c:835: error: &#8216;struct usbcam_dev&#8217; has no member named &#8216;ud_dev_name&#8217;
/home/steven/Desktop/r5u870-VCC6/r5u870_md.c: In function &#8216;r5u870_set_ctrl_wdm&#8217;:
/home/steven/Desktop/r5u870-VCC6/r5u870_md.c:848: error: &#8216;struct usbcam_dev&#8217; has no member named &#8216;ud_minidrv_data&#8217;
/home/steven/Desktop/r5u870-VCC6/r5u870_md.c:858: error: &#8216;struct usbcam_dev&#8217; has no member named &#8216;ud_debug&#8217;
/home/steven/Desktop/r5u870-VCC6/r5u870_md.c:858: error: &#8216;struct usbcam_dev&#8217; has no member named &#8216;ud_debug&#8217;
/home/steven/Desktop/r5u870-VCC6/r5u870_md.c:858: error: &#8216;struct usbcam_dev&#8217; has no member named &#8216;ud_dev_name&#8217;
/home/steven/Desktop/r5u870-VCC6/r5u870_md.c:862: error: &#8216;struct usbcam_dev&#8217; has no member named &#8216;ud_debug&#8217;
/home/steven/Desktop/r5u870-VCC6/r5u870_md.c:862: error: &#8216;struct usbcam_dev&#8217; has no member named &#8216;ud_debug&#8217;
/home/steven/Desktop/r5u870-VCC6/r5u870_md.c:862: error: &#8216;struct usbcam_dev&#8217; has no member named &#8216;ud_dev_name&#8217;
/home/steven/Desktop/r5u870-VCC6/r5u870_md.c:867: error: &#8216;struct usbcam_dev&#8217; has no member named &#8216;ud_debug&#8217;
/home/steven/Desktop/r5u870-VCC6/r5u870_md.c:867: error: &#8216;struct usbcam_dev&#8217; has no member named &#8216;ud_debug&#8217;
/home/steven/Desktop/r5u870-VCC6/r5u870_md.c:867: error: &#8216;struct usbcam_dev&#8217; has no member named &#8216;ud_dev_name&#8217;
/home/steven/Desktop/r5u870-VCC6/r5u870_md.c: In function &#8216;r5u870_wdm_add_ctrls&#8217;:
/home/steven/Desktop/r5u870-VCC6/r5u870_md.c:1281: error: &#8216;struct usbcam_dev&#8217; has no member named &#8216;ud_debug&#8217;
/home/steven/Desktop/r5u870-VCC6/r5u870_md.c:1281: error: &#8216;struct usbcam_dev&#8217; has no member named &#8216;ud_debug&#8217;
/home/steven/Desktop/r5u870-VCC6/r5u870_md.c:1281: error: &#8216;struct usbcam_dev&#8217; has no member named &#8216;ud_dev_name&#8217;
/home/steven/Desktop/r5u870-VCC6/r5u870_md.c: In function &#8216;r5u870_uvc_req&#8217;:
/home/steven/Desktop/r5u870-VCC6/r5u870_md.c:1375: error: &#8216;struct usbcam_dev&#8217; has no member named &#8216;ud_dev_name&#8217;
/home/steven/Desktop/r5u870-VCC6/r5u870_md.c:1379: error: &#8216;struct usbcam_dev&#8217; has no member named &#8216;ud_dev_name&#8217;
/home/steven/Desktop/r5u870-VCC6/r5u870_md.c:1384: error: &#8216;struct usbcam_dev&#8217; has no member named &#8216;ud_dev_name&#8217;
/home/steven/Desktop/r5u870-VCC6/r5u870_md.c: In function &#8216;r5u870_set_fmt_uvc&#8217;:
/home/steven/Desktop/r5u870-VCC6/r5u870_md.c:1404: error: &#8216;struct usbcam_dev&#8217; has no member named &#8216;ud_dev_name&#8217;
/home/steven/Desktop/r5u870-VCC6/r5u870_md.c:1411: error: &#8216;struct usbcam_dev&#8217; has no member named &#8216;ud_dev_name&#8217;
/home/steven/Desktop/r5u870-VCC6/r5u870_md.c:1420: error: &#8216;struct usbcam_dev&#8217; has no member named &#8216;ud_dev_name&#8217;
/home/steven/Desktop/r5u870-VCC6/r5u870_md.c:1426: error: &#8216;struct usbcam_dev&#8217; has no member named &#8216;ud_dev_name&#8217;
/home/steven/Desktop/r5u870-VCC6/r5u870_md.c:1432: error: &#8216;struct usbcam_dev&#8217; has no member named &#8216;ud_dev_name&#8217;
/home/steven/Desktop/r5u870-VCC6/r5u870_md.c:1440: error: &#8216;struct usbcam_dev&#8217; has no member named &#8216;ud_dev_name&#8217;
/home/steven/Desktop/r5u870-VCC6/r5u870_md.c: In function &#8216;r5u870_decide_pkt_uvc&#8217;:
/home/steven/Desktop/r5u870-VCC6/r5u870_md.c:1462: error: &#8216;struct usbcam_dev&#8217; has no member named &#8216;ud_dev_name&#8217;
/home/steven/Desktop/r5u870-VCC6/r5u870_md.c:1478: error: &#8216;struct usbcam_dev&#8217; has no member named &#8216;ud_dev_name&#8217;
/home/steven/Desktop/r5u870-VCC6/r5u870_md.c:1483: error: &#8216;struct usbcam_dev&#8217; has no member named &#8216;ud_format&#8217;
/home/steven/Desktop/r5u870-VCC6/r5u870_md.c:1484: error: &#8216;struct usbcam_dev&#8217; has no member named &#8216;ud_dev_name&#8217;
/home/steven/Desktop/r5u870-VCC6/r5u870_md.c:1492: error: &#8216;struct usbcam_dev&#8217; has no member named &#8216;ud_format&#8217;
/home/steven/Desktop/r5u870-VCC6/r5u870_md.c:1493: error: &#8216;struct usbcam_dev&#8217; has no member named &#8216;ud_dev_name&#8217;
/home/steven/Desktop/r5u870-VCC6/r5u870_md.c:1493: error: &#8216;struct usbcam_dev&#8217; has no member named &#8216;ud_format&#8217;
/home/steven/Desktop/r5u870-VCC6/r5u870_md.c: In function &#8216;r5u870_uvc_add_resolution&#8217;:
/home/steven/Desktop/r5u870-VCC6/r5u870_md.c:1533: error: &#8216;struct usbcam_dev&#8217; has no member named &#8216;ud_debug&#8217;
/home/steven/Desktop/r5u870-VCC6/r5u870_md.c:1533: error: &#8216;struct usbcam_dev&#8217; has no member named &#8216;ud_debug&#8217;
/home/steven/Desktop/r5u870-VCC6/r5u870_md.c:1533: error: &#8216;struct usbcam_dev&#8217; has no member named &#8216;ud_dev_name&#8217;
/home/steven/Desktop/r5u870-VCC6/r5u870_md.c:1548: error: &#8216;struct usbcam_dev&#8217; has no member named &#8216;ud_debug&#8217;
/home/steven/Desktop/r5u870-VCC6/r5u870_md.c:1548: error: &#8216;struct usbcam_dev&#8217; has no member named &#8216;ud_debug&#8217;
/home/steven/Desktop/r5u870-VCC6/r5u870_md.c:1548: error: &#8216;struct usbcam_dev&#8217; has no member named &#8216;ud_dev_name&#8217;
/home/steven/Desktop/r5u870-VCC6/r5u870_md.c:1560: error: &#8216;struct usbcam_dev&#8217; has no member named &#8216;ud_debug&#8217;
/home/steven/Desktop/r5u870-VCC6/r5u870_md.c:1560: error: &#8216;struct usbcam_dev&#8217; has no member named &#8216;ud_debug&#8217;
/home/steven/Desktop/r5u870-VCC6/r5u870_md.c:1560: error: &#8216;struct usbcam_dev&#8217; has no member named &#8216;ud_dev_name&#8217;
/home/steven/Desktop/r5u870-VCC6/r5u870_md.c: In function &#8216;r5u870_uvc_add_fmt&#8217;:
/home/steven/Desktop/r5u870-VCC6/r5u870_md.c:1583: error: &#8216;struct usbcam_dev&#8217; has no member named &#8216;ud_debug&#8217;
/home/steven/Desktop/r5u870-VCC6/r5u870_md.c:1583: error: &#8216;struct usbcam_dev&#8217; has no member named &#8216;ud_debug&#8217;
/home/steven/Desktop/r5u870-VCC6/r5u870_md.c:1583: error: &#8216;struct usbcam_dev&#8217; has no member named &#8216;ud_dev_name&#8217;
/home/steven/Desktop/r5u870-VCC6/r5u870_md.c:1626: error: &#8216;struct usbcam_dev&#8217; has no member named &#8216;ud_debug&#8217;
/home/steven/Desktop/r5u870-VCC6/r5u870_md.c:1626: error: &#8216;struct usbcam_dev&#8217; has no member named &#8216;ud_debug&#8217;
/home/steven/Desktop/r5u870-VCC6/r5u870_md.c:1626: error: &#8216;struct usbcam_dev&#8217; has no member named &#8216;ud_dev_name&#8217;
/home/steven/Desktop/r5u870-VCC6/r5u870_md.c: In function &#8216;r5u870_uvc_parse_vs&#8217;:
/home/steven/Desktop/r5u870-VCC6/r5u870_md.c:1668: error: &#8216;struct usbcam_dev&#8217; has no member named &#8216;ud_dev_name&#8217;
/home/steven/Desktop/r5u870-VCC6/r5u870_md.c:1677: error: &#8216;struct usbcam_dev&#8217; has no member named &#8216;ud_dev_name&#8217;
/home/steven/Desktop/r5u870-VCC6/r5u870_md.c:1692: error: &#8216;struct usbcam_dev&#8217; has no member named &#8216;ud_dev_name&#8217;
/home/steven/Desktop/r5u870-VCC6/r5u870_md.c:1697: error: &#8216;struct usbcam_dev&#8217; has no member named &#8216;ud_debug&#8217;
/home/steven/Desktop/r5u870-VCC6/r5u870_md.c:1697: error: &#8216;struct usbcam_dev&#8217; has no member named &#8216;ud_debug&#8217;
/home/steven/Desktop/r5u870-VCC6/r5u870_md.c:1697: error: &#8216;struct usbcam_dev&#8217; has no member named &#8216;ud_dev_name&#8217;
/home/steven/Desktop/r5u870-VCC6/r5u870_md.c: In function &#8216;r5u870_uvc_ctrl_req&#8217;:
/home/steven/Desktop/r5u870-VCC6/r5u870_md.c:1832: error: &#8216;struct usbcam_dev&#8217; has no member named &#8216;ud_dev_name&#8217;
/home/steven/Desktop/r5u870-VCC6/r5u870_md.c:1846: error: &#8216;struct usbcam_dev&#8217; has no member named &#8216;ud_dev_name&#8217;
/home/steven/Desktop/r5u870-VCC6/r5u870_md.c:1880: error: &#8216;struct usbcam_dev&#8217; has no member named &#8216;ud_dev_name&#8217;
/home/steven/Desktop/r5u870-VCC6/r5u870_md.c: In function &#8216;r5u870_set_ctrl_uvc&#8217;:
/home/steven/Desktop/r5u870-VCC6/r5u870_md.c:1892: error: &#8216;struct usbcam_dev&#8217; has no member named &#8216;ud_minidrv_data&#8217;
/home/steven/Desktop/r5u870-VCC6/r5u870_md.c:1899: error: &#8216;struct usbcam_dev&#8217; has no member named &#8216;ud_debug&#8217;
/home/steven/Desktop/r5u870-VCC6/r5u870_md.c:1899: error: &#8216;struct usbcam_dev&#8217; has no member named &#8216;ud_debug&#8217;
/home/steven/Desktop/r5u870-VCC6/r5u870_md.c:1899: error: &#8216;struct usbcam_dev&#8217; has no member named &#8216;ud_dev_name&#8217;
/home/steven/Desktop/r5u870-VCC6/r5u870_md.c:1904: error: &#8216;struct usbcam_dev&#8217; has no member named &#8216;ud_debug&#8217;
/home/steven/Desktop/r5u870-VCC6/r5u870_md.c:1904: error: &#8216;struct usbcam_dev&#8217; has no member named &#8216;ud_debug&#8217;
/home/steven/Desktop/r5u870-VCC6/r5u870_md.c:1904: error: &#8216;struct usbcam_dev&#8217; has no member named &#8216;ud_dev_name&#8217;
/home/steven/Desktop/r5u870-VCC6/r5u870_md.c: In function &#8216;r5u870_uvc_init_ctrl&#8217;:
/home/steven/Desktop/r5u870-VCC6/r5u870_md.c:1991: error: &#8216;struct usbcam_dev&#8217; has no member named &#8216;ud_debug&#8217;
/home/steven/Desktop/r5u870-VCC6/r5u870_md.c:1991: error: &#8216;struct usbcam_dev&#8217; has no member named &#8216;ud_debug&#8217;
/home/steven/Desktop/r5u870-VCC6/r5u870_md.c:1991: error: &#8216;struct usbcam_dev&#8217; has no member named &#8216;ud_dev_name&#8217;
/home/steven/Desktop/r5u870-VCC6/r5u870_md.c: In function &#8216;r5u870_uvc_add_ctrls&#8217;:
/home/steven/Desktop/r5u870-VCC6/r5u870_md.c:2012: error: &#8216;struct usbcam_dev&#8217; has no member named &#8216;ud_debug&#8217;
/home/steven/Desktop/r5u870-VCC6/r5u870_md.c:2012: error: &#8216;struct usbcam_dev&#8217; has no member named &#8216;ud_debug&#8217;
/home/steven/Desktop/r5u870-VCC6/r5u870_md.c:2012: error: &#8216;struct usbcam_dev&#8217; has no member named &#8216;ud_dev_name&#8217;
/home/steven/Desktop/r5u870-VCC6/r5u870_md.c: In function &#8216;r5u870_uvc_parse_vc&#8217;:
/home/steven/Desktop/r5u870-VCC6/r5u870_md.c:2090: error: &#8216;struct usbcam_dev&#8217; has no member named &#8216;ud_dev_name&#8217;
/home/steven/Desktop/r5u870-VCC6/r5u870_md.c:2099: error: &#8216;struct usbcam_dev&#8217; has no member named &#8216;ud_dev_name&#8217;
/home/steven/Desktop/r5u870-VCC6/r5u870_md.c:2112: error: &#8216;struct usbcam_dev&#8217; has no member named &#8216;ud_dev_name&#8217;
/home/steven/Desktop/r5u870-VCC6/r5u870_md.c: In function &#8216;r5u870_do_stop&#8217;:
/home/steven/Desktop/r5u870-VCC6/r5u870_md.c:2132: error: &#8216;struct usbcam_dev&#8217; has no member named &#8216;ud_capturing&#8217;
/home/steven/Desktop/r5u870-VCC6/r5u870_md.c:2133: error: &#8216;struct usbcam_dev&#8217; has no member named &#8216;ud_capturing&#8217;
/home/steven/Desktop/r5u870-VCC6/r5u870_md.c:2139: error: &#8216;struct usbcam_dev&#8217; has no member named &#8216;ud_disconnected&#8217;
/home/steven/Desktop/r5u870-VCC6/r5u870_md.c: In function &#8216;r5u870_iso_packet_done&#8217;:
/home/steven/Desktop/r5u870-VCC6/r5u870_md.c:2162: error: &#8216;struct usbcam_dev&#8217; has no member named &#8216;ud_minidrv_data&#8217;
/home/steven/Desktop/r5u870-VCC6/r5u870_md.c: In function &#8216;r5u870_iso_submit_error&#8217;:
/home/steven/Desktop/r5u870-VCC6/r5u870_md.c:2231: error: &#8216;struct usbcam_dev&#8217; has no member named &#8216;ud_minidrv_data&#8217;
/home/steven/Desktop/r5u870-VCC6/r5u870_md.c:2232: error: &#8216;struct usbcam_dev&#8217; has no member named &#8216;ud_debug&#8217;
/home/steven/Desktop/r5u870-VCC6/r5u870_md.c:2232: error: &#8216;struct usbcam_dev&#8217; has no member named &#8216;ud_debug&#8217;
/home/steven/Desktop/r5u870-VCC6/r5u870_md.c:2232: error: &#8216;struct usbcam_dev&#8217; has no member named &#8216;ud_dev_name&#8217;
/home/steven/Desktop/r5u870-VCC6/r5u870_md.c: In function &#8216;r5u870_usbcam_release&#8217;:
/home/steven/Desktop/r5u870-VCC6/r5u870_md.c:2244: error: &#8216;struct usbcam_dev&#8217; has no member named &#8216;ud_minidrv_data&#8217;
/home/steven/Desktop/r5u870-VCC6/r5u870_md.c: In function &#8216;r5u870_usbcam_init&#8217;:
/home/steven/Desktop/r5u870-VCC6/r5u870_md.c:2277: error: &#8216;struct usbcam_dev&#8217; has no member named &#8216;ud_minidrv_data&#8217;
/home/steven/Desktop/r5u870-VCC6/r5u870_md.c:2289: error: &#8216;struct usbcam_dev&#8217; has no member named &#8216;ud_dev_name&#8217;
/home/steven/Desktop/r5u870-VCC6/r5u870_md.c:2308: error: &#8216;struct usbcam_dev&#8217; has no member named &#8216;ud_dev_name&#8217;
/home/steven/Desktop/r5u870-VCC6/r5u870_md.c:2312: error: &#8216;struct usbcam_dev&#8217; has no member named &#8216;ud_minidrv_id&#8217;
/home/steven/Desktop/r5u870-VCC6/r5u870_md.c:2316: error: &#8216;struct usbcam_dev&#8217; has no member named &#8216;ud_dev_name&#8217;
/home/steven/Desktop/r5u870-VCC6/r5u870_md.c:2328: error: &#8216;struct usbcam_dev&#8217; has no member named &#8216;ud_dev_name&#8217;
/home/steven/Desktop/r5u870-VCC6/r5u870_md.c:2342: error: &#8216;struct usbcam_dev&#8217; has no member named &#8216;ud_dev_name&#8217;
/home/steven/Desktop/r5u870-VCC6/r5u870_md.c:2349: error: &#8216;struct usbcam_dev&#8217; has no member named &#8216;ud_dev_name&#8217;
/home/steven/Desktop/r5u870-VCC6/r5u870_md.c:2354: error: &#8216;struct usbcam_dev&#8217; has no member named &#8216;ud_fmt_array&#8217;
/home/steven/Desktop/r5u870-VCC6/r5u870_md.c:2355: error: &#8216;struct usbcam_dev&#8217; has no member named &#8216;ud_fmt_array_elem_size&#8217;
/home/steven/Desktop/r5u870-VCC6/r5u870_md.c:2356: error: &#8216;struct usbcam_dev&#8217; has no member named &#8216;ud_fmt_array_len&#8217;
/home/steven/Desktop/r5u870-VCC6/r5u870_md.c:2359: error: &#8216;struct usbcam_dev&#8217; has no member named &#8216;ud_ctrl_array&#8217;
/home/steven/Desktop/r5u870-VCC6/r5u870_md.c:2360: error: &#8216;struct usbcam_dev&#8217; has no member named &#8216;ud_ctrl_array_len&#8217;
/home/steven/Desktop/r5u870-VCC6/r5u870_md.c:2361: error: &#8216;struct usbcam_dev&#8217; has no member named &#8216;ud_ctrl_array_elem_size&#8217;
/home/steven/Desktop/r5u870-VCC6/r5u870_md.c:2367: error: &#8216;struct usbcam_dev&#8217; has no member named &#8216;ud_format&#8217;
/home/steven/Desktop/r5u870-VCC6/r5u870_md.c:2368: error: &#8216;struct usbcam_dev&#8217; has no member named &#8216;ud_format&#8217;
/home/steven/Desktop/r5u870-VCC6/r5u870_md.c:2369: error: &#8216;struct usbcam_dev&#8217; has no member named &#8216;ud_format&#8217;
/home/steven/Desktop/r5u870-VCC6/r5u870_md.c:2370: error: &#8216;struct usbcam_dev&#8217; has no member named &#8216;ud_format&#8217;
/home/steven/Desktop/r5u870-VCC6/r5u870_md.c:2371: error: &#8216;struct usbcam_dev&#8217; has no member named &#8216;ud_format&#8217;
/home/steven/Desktop/r5u870-VCC6/r5u870_md.c:2371: error: &#8216;struct usbcam_dev&#8217; has no member named &#8216;ud_format&#8217;
/home/steven/Desktop/r5u870-VCC6/r5u870_md.c:2372: error: &#8216;struct usbcam_dev&#8217; has no member named &#8216;ud_format&#8217;
/home/steven/Desktop/r5u870-VCC6/r5u870_md.c:2372: error: &#8216;struct usbcam_dev&#8217; has no member named &#8216;ud_format&#8217;
/home/steven/Desktop/r5u870-VCC6/r5u870_md.c:2373: error: &#8216;struct usbcam_dev&#8217; has no member named &#8216;ud_format&#8217;
/home/steven/Desktop/r5u870-VCC6/r5u870_md.c:2374: error: &#8216;struct usbcam_dev&#8217; has no member named &#8216;ud_format&#8217;
/home/steven/Desktop/r5u870-VCC6/r5u870_md.c:2379: error: &#8216;struct usbcam_dev&#8217; has no member named &#8216;ud_dev_name&#8217;
/home/steven/Desktop/r5u870-VCC6/r5u870_md.c: In function &#8216;r5u870_usbcam_disconnect&#8217;:
/home/steven/Desktop/r5u870-VCC6/r5u870_md.c:2392: error: &#8216;struct usbcam_dev&#8217; has no member named &#8216;ud_minidrv_data&#8217;
/home/steven/Desktop/r5u870-VCC6/r5u870_md.c: In function &#8216;r5u870_usbcam_suspend&#8217;:
/home/steven/Desktop/r5u870-VCC6/r5u870_md.c:2404: error: &#8216;struct usbcam_dev&#8217; has no member named &#8216;ud_minidrv_data&#8217;
/home/steven/Desktop/r5u870-VCC6/r5u870_md.c: In function &#8216;r5u870_usbcam_resume&#8217;:
/home/steven/Desktop/r5u870-VCC6/r5u870_md.c:2411: error: &#8216;struct usbcam_dev&#8217; has no member named &#8216;ud_minidrv_data&#8217;
/home/steven/Desktop/r5u870-VCC6/r5u870_md.c:2416: error: &#8216;struct usbcam_dev&#8217; has no member named &#8216;ud_dev_name&#8217;
/home/steven/Desktop/r5u870-VCC6/r5u870_md.c: In function &#8216;r5u870_try_format&#8217;:
/home/steven/Desktop/r5u870-VCC6/r5u870_md.c:2429: error: &#8216;struct usbcam_dev&#8217; has no member named &#8216;ud_minidrv_data&#8217;
/home/steven/Desktop/r5u870-VCC6/r5u870_md.c:2446: error: &#8216;struct usbcam_dev&#8217; has no member named &#8216;ud_dev_name&#8217;
/home/steven/Desktop/r5u870-VCC6/r5u870_md.c: In function &#8216;r5u870_usbcam_set_format&#8217;:
/home/steven/Desktop/r5u870-VCC6/r5u870_md.c:2505: error: &#8216;struct usbcam_dev&#8217; has no member named &#8216;ud_minidrv_data&#8217;
/home/steven/Desktop/r5u870-VCC6/r5u870_md.c:2514: error: &#8216;struct usbcam_dev&#8217; has no member named &#8216;ud_format&#8217;
/home/steven/Desktop/r5u870-VCC6/r5u870_md.c:2515: error: &#8216;struct usbcam_dev&#8217; has no member named &#8216;ud_format&#8217;
/home/steven/Desktop/r5u870-VCC6/r5u870_md.c:2516: error: &#8216;struct usbcam_dev&#8217; has no member named &#8216;ud_format&#8217;
/home/steven/Desktop/r5u870-VCC6/r5u870_md.c:2517: error: &#8216;struct usbcam_dev&#8217; has no member named &#8216;ud_format&#8217;
/home/steven/Desktop/r5u870-VCC6/r5u870_md.c:2520: error: &#8216;struct usbcam_dev&#8217; has no member named &#8216;ud_format&#8217;
/home/steven/Desktop/r5u870-VCC6/r5u870_md.c: In function &#8216;r5u870_usbcam_cap_stop&#8217;:
/home/steven/Desktop/r5u870-VCC6/r5u870_md.c:2528: error: &#8216;struct usbcam_dev&#8217; has no member named &#8216;ud_minidrv_data&#8217;
/home/steven/Desktop/r5u870-VCC6/r5u870_md.c: In function &#8216;r5u870_config_iso_ep&#8217;:
/home/steven/Desktop/r5u870-VCC6/r5u870_md.c:2547: error: &#8216;struct usbcam_dev&#8217; has no member named &#8216;ud_dev_name&#8217;
/home/steven/Desktop/r5u870-VCC6/r5u870_md.c:2552: error: &#8216;struct usbcam_dev&#8217; has no member named &#8216;ud_debug&#8217;
/home/steven/Desktop/r5u870-VCC6/r5u870_md.c:2552: error: &#8216;struct usbcam_dev&#8217; has no member named &#8216;ud_debug&#8217;
/home/steven/Desktop/r5u870-VCC6/r5u870_md.c:2552: error: &#8216;struct usbcam_dev&#8217; has no member named &#8216;ud_dev_name&#8217;
/home/steven/Desktop/r5u870-VCC6/r5u870_md.c:2559: error: &#8216;struct usbcam_dev&#8217; has no member named &#8216;ud_dev_name&#8217;
/home/steven/Desktop/r5u870-VCC6/r5u870_md.c: In function &#8216;r5u870_usbcam_cap_start&#8217;:
/home/steven/Desktop/r5u870-VCC6/r5u870_md.c:2568: error: &#8216;struct usbcam_dev&#8217; has no member named &#8216;ud_minidrv_data&#8217;
/home/steven/Desktop/r5u870-VCC6/r5u870_md.c:2571: error: &#8216;struct usbcam_dev&#8217; has no member named &#8216;ud_capturing&#8217;
/home/steven/Desktop/r5u870-VCC6/r5u870_md.c:2583: error: &#8216;struct usbcam_dev&#8217; has no member named &#8216;ud_debug&#8217;
/home/steven/Desktop/r5u870-VCC6/r5u870_md.c:2583: error: &#8216;struct usbcam_dev&#8217; has no member named &#8216;ud_debug&#8217;
/home/steven/Desktop/r5u870-VCC6/r5u870_md.c:2583: error: &#8216;struct usbcam_dev&#8217; has no member named &#8216;ud_dev_name&#8217;
/home/steven/Desktop/r5u870-VCC6/r5u870_md.c:2590: error: &#8216;struct usbcam_dev&#8217; has no member named &#8216;ud_dev_name&#8217;
/home/steven/Desktop/r5u870-VCC6/r5u870_md.c:2611: error: &#8216;struct usbcam_dev&#8217; has no member named &#8216;ud_dev_name&#8217;
/home/steven/Desktop/r5u870-VCC6/r5u870_md.c:2615: error: &#8216;struct usbcam_dev&#8217; has no member named &#8216;ud_capturing&#8217;
/home/steven/Desktop/r5u870-VCC6/r5u870_md.c:2624: error: &#8216;struct usbcam_dev&#8217; has no member named &#8216;ud_debug&#8217;
/home/steven/Desktop/r5u870-VCC6/r5u870_md.c:2624: error: &#8216;struct usbcam_dev&#8217; has no member named &#8216;ud_debug&#8217;
/home/steven/Desktop/r5u870-VCC6/r5u870_md.c:2624: error: &#8216;struct usbcam_dev&#8217; has no member named &#8216;ud_dev_name&#8217;
/home/steven/Desktop/r5u870-VCC6/r5u870_md.c:2629: error: &#8216;struct usbcam_dev&#8217; has no member named &#8216;ud_dev_name&#8217;
/home/steven/Desktop/r5u870-VCC6/r5u870_md.c:2639: error: &#8216;struct usbcam_dev&#8217; has no member named &#8216;ud_debug&#8217;
/home/steven/Desktop/r5u870-VCC6/r5u870_md.c:2639: error: &#8216;struct usbcam_dev&#8217; has no member named &#8216;ud_debug&#8217;
/home/steven/Desktop/r5u870-VCC6/r5u870_md.c:2639: error: &#8216;struct usbcam_dev&#8217; has no member named &#8216;ud_dev_name&#8217;
/home/steven/Desktop/r5u870-VCC6/r5u870_md.c:2660: error: &#8216;struct usbcam_dev&#8217; has no member named &#8216;ud_capturing&#8217;
/home/steven/Desktop/r5u870-VCC6/r5u870_md.c: At top level:
/home/steven/Desktop/r5u870-VCC6/r5u870_md.c:3056: error: expected &#8216;=&#8217;, &#8216;,&#8217;, &#8216;;&#8217;, &#8216;asm&#8217; or &#8216;__attribute__&#8217; before &#8216;*&#8217; token
/home/steven/Desktop/r5u870-VCC6/r5u870_md.c: In function &#8216;usbcam_minidrv_init&#8217;:
/home/steven/Desktop/r5u870-VCC6/r5u870_md.c:3056: error: implicit declaration of function &#8216;usbcam_register_mod&#8217;
/home/steven/Desktop/r5u870-VCC6/r5u870_md.c:3056: error: &#8216;usbcam_minidrv_driver&#8217; undeclared (first use in this function)
/home/steven/Desktop/r5u870-VCC6/r5u870_md.c:3056: error: (Each undeclared identifier is reported only once
/home/steven/Desktop/r5u870-VCC6/r5u870_md.c:3056: error: for each function it appears in.)
/home/steven/Desktop/r5u870-VCC6/r5u870_md.c: In function &#8216;usbcam_minidrv_exit&#8217;:
/home/steven/Desktop/r5u870-VCC6/r5u870_md.c:3056: error: implicit declaration of function &#8216;usbcam_unregister&#8217;
/home/steven/Desktop/r5u870-VCC6/r5u870_md.c:3056: error: &#8216;usbcam_minidrv_driver&#8217; undeclared (first use in this function)
make[2]: *** [/home/steven/Desktop/r5u870-VCC6/r5u870_md.o] Error 1
make[1]: *** [_module_/home/steven/Desktop/r5u870-VCC6] Error 2
make[1]: Leaving directory `/usr/src/linux-headers-2.6.24-18-generic'
make: *** [all] Error 2

```

---

### Post by steve101101 on 2008-06-08
i have tried everything i have found on the internet to no avail. please help me. I really want to use my webcam.

---

### Post by OrionFyre on 2008-06-13
Steve, I just had the same error while attempting to get my webcam working in ARCH. 

You may try this out:

firstly
* verify you have svn installed
* remove any instance of r5u870 or the ry5u870 modules you may already have from previous attempts.

```
svn co http://svn.mediati.org/svn/r5u870/trunk ~/r5u870
cd ~/r5u870
sudo make
sudo make install
modprobe r5u870

```

then try xawtv to see if it works (sudo apt-get install xawtv)

test it using ```
xawtv /dev/video0
```

---

### Post by steve101101 on 2008-06-13
okay i will try this when i get back home. thanks for the help. I will keep you posted if it works.

---

### Post by steve101101 on 2008-06-13
D*mn that works. I have tried everything and nothing else works. Thanks so much.

---

### Post by steve101101 on 2008-06-13
> **OrionFyre said:**
> Steve, I just had the same error while attempting to get my webcam working in ARCH. 

You may try this out:

firstly
* verify you have svn installed
* remove any instance of r5u870 or the ry5u870 modules you may already have from previous attempts.

```
svn co http://svn.mediati.org/svn/r5u870/trunk ~/r5u870
cd ~/r5u870
sudo make
sudo make install
modprobe r5u870

```


then try xawtv to see if it works (sudo apt-get install xawtv)

test it using ```
xawtv /dev/video0
```

This is the complete fix. You do not need to do anything else to get this web cam working.

---

### Post by steve101101 on 2008-06-14
oh btw you have to run modprobe with sudo.

---

### Post by rafttrip on 2008-06-24
I am having a simaler problem with my webcan on my VAIO.

when I try the fix above this is what I get

 svn co [http://svn.mediati.org/svn/r5u870/trunk](http://svn.mediati.org/svn/r5u870/trunk) ~/r5u870
svn: PROPFIND request failed on '/svn/r5u870/trunk'
svn: PROPFIND of '/svn/r5u870/trunk': Could not resolve hostname `svn.mediati.org': No address associated with hostname ([http://svn.mediati.org](http://svn.mediati.org))

lsusb
Bus 007 Device 001: ID 0000:0000  
Bus 006 Device 002: ID 05ca:1839 Ricoh Co., Ltd 
Bus 006 Device 001: ID 0000:0000  
Bus 004 Device 002: ID 046d:c521 Logitech, Inc. MX620 Laser Cordless Mouse
Bus 004 Device 001: ID 0000:0000  
Bus 002 Device 001: ID 0000:0000  
Bus 005 Device 002: ID 0483:2016 SGS Thomson Microelectronics Fingerprint Reader
Bus 005 Device 001: ID 0000:0000  
Bus 003 Device 001: ID 0000:0000  
Bus 001 Device 001: ID 0000:0000 

uname -r
2.6.24-19-generic

I am using Ubuntu hardy 8.04. any help would be awesome!!!

I had this camera working in Ubuntu 7.10 before but the method I used before is no longer working.

I am using Ubuntu hardy 8.04. any help would be awesome!!!

---

### Post by subaruwrc01 on 2008-08-31
Is there a missing step in that guide?  I'm having trouble.
[http://ubuntuforums.org/showthread.php?t=906855](http://ubuntuforums.org/showthread.php?t=906855)

---

### Post by IntuitiveNipple on 2008-09-01
I keep the latest r5u870 driver in my Ubuntu PPA (Personal Package Archive) so it is easy to install. It is a DKMS (Dynamic Kernel Module Support) package too, which means when the kernel is updated it will automatically be rebuilt against the new kernel headers, rather than you having to do it manually.

To use it, add my PPA to apt's sources list:
```

sudo sh -c "echo 'deb http://ppa.launchpad.net/intuitivenipple/ubuntu $(lsb_release -sc) main' >/etc/apt/sources.list.d/intuitivenipple.list"
sudo sh -c "echo 'deb-src http://ppa.launchpad.net/intuitivenipple/ubuntu $(lsb_release -sc) main' >>/etc/apt/sources.list.d/intuitivenipple.list"
sudo apt-get update

```
Install the driver:
```

sudo apt-get install r5u870-dkms

```
Remove my PPA from apt's sources list (to prevent Update Manager offering you all my latest backport and test packages!).
```

sudo rm /etc/apt/sources.list.d/intuitivenipple.list
sudo apt-get update

```

---

### Post by chavita on 2008-09-19
Thank's a lot thats do the job!, now I have my webcam working. I'm Very Glad! greets from Mexico.

---

### Post by SteveMcQwark on 2008-10-07
Okay, followed the instructions, but I keep running into errors unpacking it. This is the message:

```
Unpacking r5u870-dkms (from .../r5u870-dkms_0.11.1-0ubuntu1~ppa2h_all.deb) ...
dpkg: error processing /var/cache/apt/archives/r5u870-dkms_0.11.1-0ubuntu1~ppa2h_all.deb (--unpack):
 trying to overwrite `/lib/firmware/r5u870_1870_1.fw', which is also in package ricoh-webcam-r5u870-firmware
dpkg-deb: subprocess paste killed by signal (Broken pipe)
Errors were encountered while processing:
 /var/cache/apt/archives/r5u870-dkms_0.11.1-0ubuntu1~ppa2h_all.deb
E: Sub-process /usr/bin/dpkg returned an error code (1)

```

The contents of '/lib/firmware' are 

```
2.6.24-16-generic  r5u870_1832.fw  r5u870_1836.fw  r5u870_1841.fw
2.6.24-19-generic  r5u870_1833.fw  r5u870_1839.fw  r5u870_1870_1.fw
r5u870_1810.fw     r5u870_1834.fw  r5u870_183a.fw  r5u870_1870.fw
r5u870_1830.fw     r5u870_1835.fw  r5u870_183b.fw

```

---

### Post by rcrc on 2008-10-25
Thanks IntuitiveNipple, this worked for me, apparently. 

For info: 
Linux tux-laptop 2.6.24-21-generic 
lsusb: Bus 006 Device 003: ID 05ca:1839 Ricoh Co., Ltd

---

### Post by quini on 2008-10-26
> **IntuitiveNipple said:**
> I keep the latest r5u870 driver in my Ubuntu PPA (Personal Package Archive)

Hi.  I've got compilation errors here... I'm using Intrepid & 2.6.27 & x86_64.  Attached is the make.log file, but I'll post some output here:


```
DKMS make.log for r5u870-0.11.1 for kernel 2.6.27.2-627c (x86_64)
dg oct 26 19:54:00 CET 2008
make: Entering directory `/usr/src/2.6.27-7.14-627c'
  LD      /var/lib/dkms/r5u870/0.11.1/build/built-in.o
  CC [M]  /var/lib/dkms/r5u870/0.11.1/build/r5u870.o
/var/lib/dkms/r5u870/0.11.1/build/r5u870.c:867:1: warning: "V4L2_CID_SHARPNESS" redefined
In file included from include/linux/videodev.h:16,
                 from /var/lib/dkms/r5u870/0.11.1/build/usbcam/usbcam.h:38,
                 from /var/lib/dkms/r5u870/0.11.1/build/r5u870.c:59:
include/linux/videodev2.h:868:1: warning: this is the location of the previous definition
  LD      /var/lib/dkms/r5u870/0.11.1/build/usbcam/built-in.o
  CC [M]  /var/lib/dkms/r5u870/0.11.1/build/usbcam/usbcam_dev.o
/var/lib/dkms/r5u870/0.11.1/build/usbcam/usbcam_dev.c: In function ‘usbcam_work_ref’:
/var/lib/dkms/r5u870/0.11.1/build/usbcam/usbcam_dev.c:779: warning: format not a string literal and no format arguments
  CC [M]  /var/lib/dkms/r5u870/0.11.1/build/usbcam/usbcam_fops.o
/var/lib/dkms/r5u870/0.11.1/build/usbcam/usbcam_fops.c: In function ‘usbcam_v4l_ioctl’:
/var/lib/dkms/r5u870/0.11.1/build/usbcam/usbcam_fops.c:1167: error: implicit declaration of function ‘video_usercopy’
/var/lib/dkms/r5u870/0.11.1/build/usbcam/usbcam_fops.c:1171: error: implicit declaration of function ‘video_ioctl2’
...
/var/lib/dkms/r5u870/0.11.1/build/usbcam/usbcam_fops.c:1195: error: ‘v4l_compat_ioctl32’ undeclared here (not in a function)
/var/lib/dkms/r5u870/0.11.1/build/usbcam/usbcam_fops.c:1213: error: unknown field ‘type’ specified in initializer
/var/lib/dkms/r5u870/0.11.1/build/usbcam/usbcam_fops.c:1214: error: unknown field ‘type2’ specified in initializer
/var/lib/dkms/r5u870/0.11.1/build/usbcam/usbcam_fops.c:1217: error: unknown field ‘vidioc_querycap’ specified in initializer
...
```


I've also noticed mine is an slightly different model... but I cannot try the driver unless it compiles!
Bus 005 Device 005: ID 05ca:183a Ricoh Co., Ltd

Any idea?  Help! ;)

---

### Post by mnk on 2008-10-28
I get the same problem on intrepid. 
Did anyone find a solution?

Building module:
cleaning build area....
make KERNELRELEASE=2.6.27-7-generic -C /lib/modules/2.6.27-7-generic/build M=/var/lib/dkms/r5u870/0.11.1/build.....(bad exit status: 2)

Error! Bad return status for module build on kernel: 2.6.27-7-generic (i686)
Consult the make.log in the build directory
/var/lib/dkms/r5u870/0.11.1/build/ for more information.
0
0
dpkg: error processing r5u870-dkms (--configure):
 subprocess post-installation script returned error exit status 10
Errors were encountered while processing:
 r5u870-dkms
E: Sub-process /usr/bin/dpkg returned an error code (1)

---

### Post by PeppeDG on 2008-11-16
I got the same errors of user mnk...

Does anyone solved???

I think the *solved* tag cannot be applied to intrepid ibex...:(:(

thanks for your efforts...

---

### Post by 2dvisio on 2008-11-27
> **PeppeDG said:**
> I got the same errors of user mnk...

Does anyone solved???

I think the *solved* tag cannot be applied to intrepid ibex...:(:(

thanks for your efforts...


Same problem here.... :(

---

### Post by fivestarleaf on 2008-11-27
i've tried most of the methods posted but can't get the motion eye to work. 
sony vaio VGN-CR320E/N champagne gold model. any known methods for my model that have been tested?

---

### Post by ivainsencher on 2008-11-29
it worked till I switched to intrepid.
now the output is uglier than me:-(
~/r5u870$ sudo make
make -C /lib/modules/2.6.27-9-generic/build M=/home/israel/r5u870 V=0 modules
make[1]: Entering directory `/usr/src/linux-headers-2.6.27-9-generic'
  CC [M]  /home/israel/r5u870/r5u870.o
/home/israel/r5u870/r5u870.c:867:1: warning: "V4L2_CID_SHARPNESS" redefined
In file included from include/linux/videodev.h:16,
                 from /home/israel/r5u870/usbcam/usbcam.h:38,
                 from /home/israel/r5u870/r5u870.c:59:
include/linux/videodev2.h:868:1: warning: this is the location of the previous definition
  CC [M]  /home/israel/r5u870/usbcam/usbcam_dev.o
/home/israel/r5u870/usbcam/usbcam_dev.c: In function ‘usbcam_work_ref’:
/home/israel/r5u870/usbcam/usbcam_dev.c:779: warning: format not a string literal and no format arguments
  CC [M]  /home/israel/r5u870/usbcam/usbcam_fops.o
/home/israel/r5u870/usbcam/usbcam_fops.c: In function ‘usbcam_v4l_ioctl’:
/home/israel/r5u870/usbcam/usbcam_fops.c:1167: error: implicit declaration of function ‘video_usercopy’
/home/israel/r5u870/usbcam/usbcam_fops.c:1171: error: implicit declaration of function ‘video_ioctl2’
/home/israel/r5u870/usbcam/usbcam_fops.c:1159: warning: unused variable ‘udp’
/home/israel/r5u870/usbcam/usbcam_fops.c: At top level:
/home/israel/r5u870/usbcam/usbcam_fops.c:1213: error: unknown field ‘type’ specified in initializer
/home/israel/r5u870/usbcam/usbcam_fops.c:1214: error: unknown field ‘type2’ specified in initializer
/home/israel/r5u870/usbcam/usbcam_fops.c:1217: error: unknown field ‘vidioc_querycap’ specified in initializer
/home/israel/r5u870/usbcam/usbcam_fops.c:1217: warning: initialization makes integer from pointer without a cast
/home/israel/r5u870/usbcam/usbcam_fops.c:1218: error: unknown field ‘vidioc_enum_fmt_cap’ specified in initializer
/home/israel/r5u870/usbcam/usbcam_fops.c:1218: warning: initialization makes integer from pointer without a cast
/home/israel/r5u870/usbcam/usbcam_fops.c:1219: error: unknown field ‘vidioc_g_fmt_cap’ specified in initializer
/home/israel/r5u870/usbcam/usbcam_fops.c:1219: warning: initialization makes integer from pointer without a cast
/home/israel/r5u870/usbcam/usbcam_fops.c:1219: error: initializer element is not computable at load time
/home/israel/r5u870/usbcam/usbcam_fops.c:1219: error: (near initialization for ‘usbcam_videodev_template.tvnorms’)
/home/israel/r5u870/usbcam/usbcam_fops.c:1220: error: unknown field ‘vidioc_s_fmt_cap’ specified in initializer
/home/israel/r5u870/usbcam/usbcam_fops.c:1220: warning: initialization makes integer from pointer without a cast
/home/israel/r5u870/usbcam/usbcam_fops.c:1220: error: initializer element is not computable at load time
/home/israel/r5u870/usbcam/usbcam_fops.c:1220: error: (near initialization for ‘usbcam_videodev_template.current_norm’)
/home/israel/r5u870/usbcam/usbcam_fops.c:1221: error: unknown field ‘vidioc_try_fmt_cap’ specified in initializer
/home/israel/r5u870/usbcam/usbcam_fops.c:1221: warning: initialization from incompatible pointer type
/home/israel/r5u870/usbcam/usbcam_fops.c:1222: error: unknown field ‘vidioc_reqbufs’ specified in initializer
/home/israel/r5u870/usbcam/usbcam_fops.c:1222: warning: initialization from incompatible pointer type
/home/israel/r5u870/usbcam/usbcam_fops.c:1223: error: unknown field ‘vidioc_querybuf’ specified in initializer
/home/israel/r5u870/usbcam/usbcam_fops.c:1224: error: unknown field ‘vidioc_qbuf’ specified in initializer
/home/israel/r5u870/usbcam/usbcam_fops.c:1224: warning: initialization makes integer from pointer without a cast
/home/israel/r5u870/usbcam/usbcam_fops.c:1225: error: unknown field ‘vidioc_dqbuf’ specified in initializer
/home/israel/r5u870/usbcam/usbcam_fops.c:1225: warning: missing braces around initializer
/home/israel/r5u870/usbcam/usbcam_fops.c:1225: warning: (near initialization for ‘usbcam_videodev_template.lock’)
/home/israel/r5u870/usbcam/usbcam_fops.c:1225: warning: initialization makes integer from pointer without a cast
/home/israel/r5u870/usbcam/usbcam_fops.c:1226: error: unknown field ‘vidiocgmbuf’ specified in initializer
/home/israel/r5u870/usbcam/usbcam_fops.c:1226: warning: excess elements in struct initializer
/home/israel/r5u870/usbcam/usbcam_fops.c:1226: warning: (near initialization for ‘usbcam_videodev_template’)
/home/israel/r5u870/usbcam/usbcam_fops.c:1227: error: unknown field ‘vidioc_enum_input’ specified in initializer
/home/israel/r5u870/usbcam/usbcam_fops.c:1227: warning: excess elements in struct initializer
/home/israel/r5u870/usbcam/usbcam_fops.c:1227: warning: (near initialization for ‘usbcam_videodev_template’)
/home/israel/r5u870/usbcam/usbcam_fops.c:1228: error: unknown field ‘vidioc_streamon’ specified in initializer
/home/israel/r5u870/usbcam/usbcam_fops.c:1228: warning: excess elements in struct initializer
/home/israel/r5u870/usbcam/usbcam_fops.c:1228: warning: (near initialization for ‘usbcam_videodev_template’)
/home/israel/r5u870/usbcam/usbcam_fops.c:1229: error: unknown field ‘vidioc_streamoff’ specified in initializer
/home/israel/r5u870/usbcam/usbcam_fops.c:1229: warning: excess elements in struct initializer
/home/israel/r5u870/usbcam/usbcam_fops.c:1229: warning: (near initialization for ‘usbcam_videodev_template’)
/home/israel/r5u870/usbcam/usbcam_fops.c:1230: error: unknown field ‘vidioc_g_input’ specified in initializer
/home/israel/r5u870/usbcam/usbcam_fops.c:1230: warning: excess elements in struct initializer
/home/israel/r5u870/usbcam/usbcam_fops.c:1230: warning: (near initialization for ‘usbcam_videodev_template’)
/home/israel/r5u870/usbcam/usbcam_fops.c:1231: error: unknown field ‘vidioc_s_input’ specified in initializer
/home/israel/r5u870/usbcam/usbcam_fops.c:1231: warning: excess elements in struct initializer
/home/israel/r5u870/usbcam/usbcam_fops.c:1231: warning: (near initialization for ‘usbcam_videodev_template’)
/home/israel/r5u870/usbcam/usbcam_fops.c:1232: error: unknown field ‘vidioc_queryctrl’ specified in initializer
/home/israel/r5u870/usbcam/usbcam_fops.c:1232: warning: excess elements in struct initializer
/home/israel/r5u870/usbcam/usbcam_fops.c:1232: warning: (near initialization for ‘usbcam_videodev_template’)
/home/israel/r5u870/usbcam/usbcam_fops.c:1233: error: unknown field ‘vidioc_g_ctrl’ specified in initializer
/home/israel/r5u870/usbcam/usbcam_fops.c:1233: warning: excess elements in struct initializer
/home/israel/r5u870/usbcam/usbcam_fops.c:1233: warning: (near initialization for ‘usbcam_videodev_template’)
/home/israel/r5u870/usbcam/usbcam_fops.c:1234: error: unknown field ‘vidioc_s_ctrl’ specified in initializer
/home/israel/r5u870/usbcam/usbcam_fops.c:1234: warning: excess elements in struct initializer
/home/israel/r5u870/usbcam/usbcam_fops.c:1234: warning: (near initialization for ‘usbcam_videodev_template’)
/home/israel/r5u870/usbcam/usbcam_fops.c:1235: error: unknown field ‘vidioc_querymenu’ specified in initializer
/home/israel/r5u870/usbcam/usbcam_fops.c:1235: warning: excess elements in struct initializer
/home/israel/r5u870/usbcam/usbcam_fops.c:1235: warning: (near initialization for ‘usbcam_videodev_template’)
make[3]: *** [/home/israel/r5u870/usbcam/usbcam_fops.o] Error 1
make[2]: *** [/home/israel/r5u870/usbcam] Error 2
make[1]: *** [_module_/home/israel/r5u870] Error 2
make[1]: Leaving directory `/usr/src/linux-headers-2.6.27-9-generic'
make: *** [all] Error 2

---

### Post by marco1986 on 2009-02-10
Hey!

I've used this thread to get my motion eye up and runnig - it work! Thanks :)

It also runs with interpid ibex on ubuntu and kubuntu 4.2.

There is just one problem i would like to get solved. When I start my desktop and I want to launch skype the camera isn't visible. When I want to test it with: ```
 xawtv /dev/video0 
``` it sais that I dont have permission. So I've got a work around ```
sudo chmod 777 /dev/video0
```
then everything works fine. Is there a way to get it work with not changing the permission to /dev/video0 to 777 ?

---

### Post by paco85 on 2009-02-12
i'm new and i've went off everybody else to get my cam to work.... but now I get a message like the following.....

paco-laptop ~ $ xawtv /dev/video0
This is xawtv-3.95.dfsg.1, running on Linux/i686 (2.6.24-23-generic)
xinerama 0: 1280x800+0+0
/dev/video0 [v4l2]: no overlay support
v4l-conf had some trouble, trying to continue anyway
Warning: Cannot convert string "-*-ledfixed-medium-r-*--39-*-*-*-c-*-*-*" to type FontStruct
Xlib:  extension "GLX" missing on display ":0.0".
ioctl: VIDIOC_S_FMT(type=VIDEO_CAPTURE;fmt.pix.width=384;fmt.pix.height=288;fmt.pix.pixelformat=0x56595559 [YUYV];fmt.pix.field=ANY;fmt.pix.bytesperline=0;fmt.pix.sizeimage=0;fmt.pix.colorspace=unknown;fmt.pix.priv=0): Device or resource busy
ioctl: VIDIOC_S_FMT(type=VIDEO_CAPTURE;fmt.pix.width=384;fmt.pix.height=288;fmt.pix.pixelformat=0x32315559 [YU12];fmt.pix.field=ANY;fmt.pix.bytesperline=0;fmt.pix.sizeimage=0;fmt.pix.colorspace=unknown;fmt.pix.priv=0): Device or resource busy
ioctl: VIDIOC_S_FMT(type=VIDEO_CAPTURE;fmt.pix.width=384;fmt.pix.height=288;fmt.pix.pixelformat=0x59565955 [UYVY];fmt.pix.field=ANY;fmt.pix.bytesperline=0;fmt.pix.sizeimage=0;fmt.pix.colorspace=unknown;fmt.pix.priv=0): Device or resource busy
ioctl: VIDIOC_S_FMT(type=VIDEO_CAPTURE;fmt.pix.width=384;fmt.pix.height=288;fmt.pix.pixelformat=0x34524742 [BGR4];fmt.pix.field=ANY;fmt.pix.bytesperline=0;fmt.pix.sizeimage=0;fmt.pix.colorspace=unknown;fmt.pix.priv=0): Device or resource busy
ioctl: VIDIOC_S_FMT(type=VIDEO_CAPTURE;fmt.pix.width=384;fmt.pix.height=288;fmt.pix.pixelformat=0x33524742 [BGR3];fmt.pix.field=ANY;fmt.pix.bytesperline=0;fmt.pix.sizeimage=0;fmt.pix.colorspace=unknown;fmt.pix.priv=0): Device or resource busy
ioctl: VIDIOC_S_FMT(type=VIDEO_CAPTURE;fmt.pix.width=384;fmt.pix.height=288;fmt.pix.pixelformat=0x33424752 [RGB3];fmt.pix.field=ANY;fmt.pix.bytesperline=0;fmt.pix.sizeimage=0;fmt.pix.colorspace=unknown;fmt.pix.priv=0): Device or resource busy
ioctl: VIDIOC_S_FMT(type=VIDEO_CAPTURE;fmt.pix.width=384;fmt.pix.height=288;fmt.pix.pixelformat=0x33524742 [BGR3];fmt.pix.field=ANY;fmt.pix.bytesperline=0;fmt.pix.sizeimage=0;fmt.pix.colorspace=unknown;fmt.pix.priv=0): Device or resource busy
ioctl: VIDIOC_S_FMT(type=VIDEO_CAPTURE;fmt.pix.width=384;fmt.pix.height=288;fmt.pix.pixelformat=0x00000000 [....];fmt.pix.field=ANY;fmt.pix.bytesperline=0;fmt.pix.sizeimage=0;fmt.pix.colorspace=unknown;fmt.pix.priv=0): Device or resource busy
ioctl: VIDIOC_S_FMT(type=VIDEO_CAPTURE;fmt.pix.width=384;fmt.pix.height=288;fmt.pix.pixelformat=0x34524742 [BGR4];fmt.pix.field=ANY;fmt.pix.bytesperline=0;fmt.pix.sizeimage=0;fmt.pix.colorspace=unknown;fmt.pix.priv=0): Device or resource busy
ioctl: VIDIOC_S_FMT(type=VIDEO_CAPTURE;fmt.pix.width=384;fmt.pix.height=288;fmt.pix.pixelformat=0x59455247 [GREY];fmt.pix.field=ANY;fmt.pix.bytesperline=0;fmt.pix.sizeimage=0;fmt.pix.colorspace=unknown;fmt.pix.priv=0): Device or resource busy
ioctl: VIDIOC_S_FMT(type=VIDEO_CAPTURE;fmt.pix.width=384;fmt.pix.height=288;fmt.pix.pixelformat=0x56595559 [YUYV];fmt.pix.field=ANY;fmt.pix.bytesperline=0;fmt.pix.sizeimage=0;fmt.pix.colorspace=unknown;fmt.pix.priv=0): Device or resource busy
ioctl: VIDIOC_S_FMT(type=VIDEO_CAPTURE;fmt.pix.width=384;fmt.pix.height=288;fmt.pix.pixelformat=0x50323234 [422P];fmt.pix.field=ANY;fmt.pix.bytesperline=0;fmt.pix.sizeimage=0;fmt.pix.colorspace=unknown;fmt.pix.priv=0): Device or resource busy
ioctl: VIDIOC_S_FMT(type=VIDEO_CAPTURE;fmt.pix.width=384;fmt.pix.height=288;fmt.pix.pixelformat=0x32315559 [YU12];fmt.pix.field=ANY;fmt.pix.bytesperline=0;fmt.pix.sizeimage=0;fmt.pix.colorspace=unknown;fmt.pix.priv=0): Device or resource busy
ioctl: VIDIOC_S_FMT(type=VIDEO_CAPTURE;fmt.pix.width=384;fmt.pix.height=288;fmt.pix.pixelformat=0x00000000 [....];fmt.pix.field=ANY;fmt.pix.bytesperline=0;fmt.pix.sizeimage=0;fmt.pix.colorspace=unknown;fmt.pix.priv=0): Device or resource busy
ioctl: VIDIOC_S_FMT(type=VIDEO_CAPTURE;fmt.pix.width=384;fmt.pix.height=288;fmt.pix.pixelformat=0x00000000 [....];fmt.pix.field=ANY;fmt.pix.bytesperline=0;fmt.pix.sizeimage=0;fmt.pix.colorspace=unknown;fmt.pix.priv=0): Device or resource busy
ioctl: VIDIOC_S_FMT(type=VIDEO_CAPTURE;fmt.pix.width=384;fmt.pix.height=288;fmt.pix.pixelformat=0x00000000 [....];fmt.pix.field=ANY;fmt.pix.bytesperline=0;fmt.pix.sizeimage=0;fmt.pix.colorspace=unknown;fmt.pix.priv=0): Device or resource busy
ioctl: VIDIOC_S_FMT(type=VIDEO_CAPTURE;fmt.pix.width=384;fmt.pix.height=288;fmt.pix.pixelformat=0x00000000 [....];fmt.pix.field=ANY;fmt.pix.bytesperline=0;fmt.pix.sizeimage=0;fmt.pix.colorspace=unknown;fmt.pix.priv=0): Device or resource busy
ioctl: VIDIOC_S_FMT(type=VIDEO_CAPTURE;fmt.pix.width=384;fmt.pix.height=288;fmt.pix.pixelformat=0x00000000 [....];fmt.pix.field=ANY;fmt.pix.bytesperline=0;fmt.pix.sizeimage=0;fmt.pix.colorspace=unknown;fmt.pix.priv=0): Device or resource busy
ioctl: VIDIOC_S_FMT(type=VIDEO_CAPTURE;fmt.pix.width=384;fmt.pix.height=288;fmt.pix.pixelformat=0x00000000 [....];fmt.pix.field=ANY;fmt.pix.bytesperline=0;fmt.pix.sizeimage=0;fmt.pix.colorspace=unknown;fmt.pix.priv=0): Device or resource busy
ioctl: VIDIOC_S_FMT(type=VIDEO_CAPTURE;fmt.pix.width=384;fmt.pix.height=288;fmt.pix.pixelformat=0x00000000 [....];fmt.pix.field=ANY;fmt.pix.bytesperline=0;fmt.pix.sizeimage=0;fmt.pix.colorspace=unknown;fmt.pix.priv=0): Device or resource busy
ioctl: VIDIOC_S_FMT(type=VIDEO_CAPTURE;fmt.pix.width=384;fmt.pix.height=288;fmt.pix.pixelformat=0x00000000 [....];fmt.pix.field=ANY;fmt.pix.bytesperline=0;fmt.pix.sizeimage=0;fmt.pix.colorspace=unknown;fmt.pix.priv=0): Device or resource busy
ioctl: VIDIOC_S_FMT(type=VIDEO_CAPTURE;fmt.pix.width=384;fmt.pix.height=288;fmt.pix.pixelformat=0x00000000 [....];fmt.pix.field=ANY;fmt.pix.bytesperline=0;fmt.pix.sizeimage=0;fmt.pix.colorspace=unknown;fmt.pix.priv=0): Device or resource busy
ioctl: VIDIOC_S_FMT(type=VIDEO_CAPTURE;fmt.pix.width=384;fmt.pix.height=288;fmt.pix.pixelformat=0x00000000 [....];fmt.pix.field=ANY;fmt.pix.bytesperline=0;fmt.pix.sizeimage=0;fmt.pix.colorspace=unknown;fmt.pix.priv=0): Device or resource busy
ioctl: VIDIOC_S_FMT(type=VIDEO_CAPTURE;fmt.pix.width=384;fmt.pix.height=288;fmt.pix.pixelformat=0x00000000 [....];fmt.pix.field=ANY;fmt.pix.bytesperline=0;fmt.pix.sizeimage=0;fmt.pix.colorspace=unknown;fmt.pix.priv=0): Device or resource busy
ioctl: VIDIOC_S_FMT(type=VIDEO_CAPTURE;fmt.pix.width=384;fmt.pix.height=288;fmt.pix.pixelformat=0x00000000 [....];fmt.pix.field=ANY;fmt.pix.bytesperline=0;fmt.pix.sizeimage=0;fmt.pix.colorspace=unknown;fmt.pix.priv=0): Device or resource busy
ioctl: VIDIOC_S_FMT(type=VIDEO_CAPTURE;fmt.pix.width=384;fmt.pix.height=288;fmt.pix.pixelformat=0x00000000 [....];fmt.pix.field=ANY;fmt.pix.bytesperline=0;fmt.pix.sizeimage=0;fmt.pix.colorspace=unknown;fmt.pix.priv=0): Device or resource busy
ioctl: VIDIOC_S_FMT(type=VIDEO_CAPTURE;fmt.pix.width=384;fmt.pix.height=288;fmt.pix.pixelformat=0x00000000 [....];fmt.pix.field=ANY;fmt.pix.bytesperline=0;fmt.pix.sizeimage=0;fmt.pix.colorspace=unknown;fmt.pix.priv=0): Device or resource busy
ioctl: VIDIOC_S_FMT(type=VIDEO_CAPTURE;fmt.pix.width=384;fmt.pix.height=288;fmt.pix.pixelformat=0x00000000 [....];fmt.pix.field=ANY;fmt.pix.bytesperline=0;fmt.pix.sizeimage=0;fmt.pix.colorspace=unknown;fmt.pix.priv=0): Device or resource busy
ioctl: VIDIOC_S_FMT(type=VIDEO_CAPTURE;fmt.pix.width=384;fmt.pix.height=288;fmt.pix.pixelformat=0x00000000 [....];fmt.pix.field=ANY;fmt.pix.bytesperline=0;fmt.pix.sizeimage=0;fmt.pix.colorspace=unknown;fmt.pix.priv=0): Device or resource busy
ioctl: VIDIOC_S_FMT(type=VIDEO_CAPTURE;fmt.pix.width=384;fmt.pix.height=288;fmt.pix.pixelformat=0x00000000 [....];fmt.pix.field=ANY;fmt.pix.bytesperline=0;fmt.pix.sizeimage=0;fmt.pix.colorspace=unknown;fmt.pix.priv=0): Device or resource busy
ioctl: VIDIOC_S_FMT(type=VIDEO_CAPTURE;fmt.pix.width=384;fmt.pix.height=288;fmt.pix.pixelformat=0x00000000 [....];fmt.pix.field=ANY;fmt.pix.bytesperline=0;fmt.pix.sizeimage=0;fmt.pix.colorspace=unknown;fmt.pix.priv=0): Device or resource busy
ioctl: VIDIOC_S_FMT(type=VIDEO_CAPTURE;fmt.pix.width=384;fmt.pix.height=288;fmt.pix.pixelformat=0x00000000 [....];fmt.pix.field=ANY;fmt.pix.bytesperline=0;fmt.pix.sizeimage=0;fmt.pix.colorspace=unknown;fmt.pix.priv=0): Device or resource busy
ioctl: VIDIOC_S_FMT(type=VIDEO_CAPTURE;fmt.pix.width=384;fmt.pix.height=288;fmt.pix.pixelformat=0x00000000 [....];fmt.pix.field=ANY;fmt.pix.bytesperline=0;fmt.pix.sizeimage=0;fmt.pix.colorspace=unknown;fmt.pix.priv=0): Device or resource busy
ioctl: VIDIOC_S_FMT(type=VIDEO_CAPTURE;fmt.pix.width=384;fmt.pix.height=288;fmt.pix.pixelformat=0x00000000 [....];fmt.pix.field=ANY;fmt.pix.bytesperline=0;fmt.pix.sizeimage=0;fmt.pix.colorspace=unknown;fmt.pix.priv=0): Device or resource busy
ioctl: VIDIOC_S_FMT(type=VIDEO_CAPTURE;fmt.pix.width=384;fmt.pix.height=288;fmt.pix.pixelformat=0x00000000 [....];fmt.pix.field=ANY;fmt.pix.bytesperline=0;fmt.pix.sizeimage=0;fmt.pix.colorspace=unknown;fmt.pix.priv=0): Device or resource busy
ioctl: VIDIOC_S_FMT(type=VIDEO_CAPTURE;fmt.pix.width=384;fmt.pix.height=288;fmt.pix.pixelformat=0x00000000 [....];fmt.pix.field=ANY;fmt.pix.bytesperline=0;fmt.pix.sizeimage=0;fmt.pix.colorspace=unknown;fmt.pix.priv=0): Device or resource busy
ioctl: VIDIOC_S_FMT(type=VIDEO_CAPTURE;fmt.pix.width=384;fmt.pix.height=288;fmt.pix.pixelformat=0x00000000 [....];fmt.pix.field=ANY;fmt.pix.bytesperline=0;fmt.pix.sizeimage=0;fmt.pix.colorspace=unknown;fmt.pix.priv=0): Device or resource busy
ioctl: VIDIOC_S_FMT(type=VIDEO_CAPTURE;fmt.pix.width=384;fmt.pix.height=288;fmt.pix.pixelformat=0x00000000 [....];fmt.pix.field=ANY;fmt.pix.bytesperline=0;fmt.pix.sizeimage=0;fmt.pix.colorspace=unknown;fmt.pix.priv=0): Device or resource busy
station "/dev/video0" not found

ioctl: VIDIOC_S_FMT(type=VIDEO_CAPTURE;fmt.pix.width=384;fmt.pix.height=288;fmt.pix.pixelformat=0x34524742 [BGR4];fmt.pix.field=ANY;fmt.pix.bytesperline=0;fmt.pix.sizeimage=0;fmt.pix.colorspace=unknown;fmt.pix.priv=0): Device or resource busy
ioctl: VIDIOC_S_FMT(type=VIDEO_CAPTURE;fmt.pix.width=384;fmt.pix.height=288;fmt.pix.pixelformat=0x33524742 [BGR3];fmt.pix.field=ANY;fmt.pix.bytesperline=0;fmt.pix.sizeimage=0;fmt.pix.colorspace=unknown;fmt.pix.priv=0): Device or resource busy
ioctl: VIDIOC_S_FMT(type=VIDEO_CAPTURE;fmt.pix.width=384;fmt.pix.height=288;fmt.pix.pixelformat=0x33424752 [RGB3];fmt.pix.field=ANY;fmt.pix.bytesperline=0;fmt.pix.sizeimage=0;fmt.pix.colorspace=unknown;fmt.pix.priv=0): Device or resource busy
ioctl: VIDIOC_S_FMT(type=VIDEO_CAPTURE;fmt.pix.width=384;fmt.pix.height=288;fmt.pix.pixelformat=0x33524742 [BGR3];fmt.pix.field=ANY;fmt.pix.bytesperline=0;fmt.pix.sizeimage=0;fmt.pix.colorspace=unknown;fmt.pix.priv=0): Device or resource busy
ioctl: VIDIOC_S_FMT(type=VIDEO_CAPTURE;fmt.pix.width=384;fmt.pix.height=288;fmt.pix.pixelformat=0x00000000 [....];fmt.pix.field=ANY;fmt.pix.bytesperline=0;fmt.pix.sizeimage=0;fmt.pix.colorspace=unknown;fmt.pix.priv=0): Device or resource busy
ioctl: VIDIOC_S_FMT(type=VIDEO_CAPTURE;fmt.pix.width=384;fmt.pix.height=288;fmt.pix.pixelformat=0x34524742 [BGR4];fmt.pix.field=ANY;fmt.pix.bytesperline=0;fmt.pix.sizeimage=0;fmt.pix.colorspace=unknown;fmt.pix.priv=0): Device or resource busy
ioctl: VIDIOC_S_FMT(type=VIDEO_CAPTURE;fmt.pix.width=384;fmt.pix.height=288;fmt.pix.pixelformat=0x59455247 [GREY];fmt.pix.field=ANY;fmt.pix.bytesperline=0;fmt.pix.sizeimage=0;fmt.pix.colorspace=unknown;fmt.pix.priv=0): Device or resource busy
ioctl: VIDIOC_S_FMT(type=VIDEO_CAPTURE;fmt.pix.width=384;fmt.pix.height=288;fmt.pix.pixelformat=0x56595559 [YUYV];fmt.pix.field=ANY;fmt.pix.bytesperline=0;fmt.pix.sizeimage=0;fmt.pix.colorspace=unknown;fmt.pix.priv=0): Device or resource busy
ioctl: VIDIOC_S_FMT(type=VIDEO_CAPTURE;fmt.pix.width=384;fmt.pix.height=288;fmt.pix.pixelformat=0x50323234 [422P];fmt.pix.field=ANY;fmt.pix.bytesperline=0;fmt.pix.sizeimage=0;fmt.pix.colorspace=unknown;fmt.pix.priv=0): Device or resource busy
ioctl: VIDIOC_S_FMT(type=VIDEO_CAPTURE;fmt.pix.width=384;fmt.pix.height=288;fmt.pix.pixelformat=0x32315559 [YU12];fmt.pix.field=ANY;fmt.pix.bytesperline=0;fmt.pix.sizeimage=0;fmt.pix.colorspace=unknown;fmt.pix.priv=0): Device or resource busy
no way to get: 384x288 32 bit TrueColor (LE: bgr-) 

what can i do... i want to see it in the "cheese" program and see it in the "amorama".... I also have the "Camera monitor" in my system... since installing the other stuff on this page... the webcam light has been flashing. 

:confused:pls lookin 4 help!

---

### Post by epvipas on 2009-02-14
```
 $ sudo gpasswd -a yourusername video
```

That should sort out the permissions.

---

### Post by marco1986 on 2009-02-18
@epvipas: it actually worked :) thanks!

---

### Post by Clockmender on 2009-03-02
I'm probably being thick but I have followed everything here to the letter and I still get:

alan@vaio:~/r5u870$ xawtv
This is xawtv-3.95.dfsg.1, running on Linux/i686 (2.6.27-11-generic)
xinerama 0: 1440x900+0+0
WARNING: No DGA direct video mode for this display.
can't open /dev/video0: No such file or directory
v4l-conf had some trouble, trying to continue anyway
v4l2: open /dev/video0: No such file or directory
v4l2: open /dev/video0: No such file or directory
v4l: open /dev/video0: No such file or directory
no video grabber device available

HELP - how do I uninstall all of this and start again or can it be rescued?

Oh this may be helpful

alan@vaio:~/r5u870$ lsusb
Bus 007 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 003 Device 002: ID 05ca:1839 Ricoh Co., Ltd 
Bus 003 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 001 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 006 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 002: ID 045e:00e1 Microsoft Corp. Wireless Laser Mouse 6000 Reciever
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub

Any ideas guys - also I cannot get anything out of the built-in mic.....I have checked the Volume control....

---

### Post by Clockmender on 2009-03-04
In the absence of any help here I went to:


[http://www.palmix.org/r5u870-en.html](http://www.palmix.org/r5u870-en.html)

and downloading the 0.11.2 driver - I got error messages in the Make process but it works with xawtv - still problems with the mic however. Picture detail is good, colour is good but my mug is not! oh well - the vagaries of Anno Domini

The cam works now but I'm still having problems with the mic.......

---

### Post by Mr Goode on 2009-03-07
Thanks alot for this!! I had given up on getting the motioneye working, but now it works! Im very happy!

---

### Post by Mr Goode on 2009-03-12
Hello again, my web cam was working perfectly but all of a sudden the picture turned upside down. And now its like that all the time.
I have reinstalled it but the picture is still upside down!
Anybody know how to fix this??
Being upside down I kind of look like spiderman, but its getting very tiresome, please help!

---

### Post by McGerger on 2009-11-01
Hello. I just installed the latest version (9.10) and I'm having with my webcam. I installed it in my Sony Vaio CR305E.

I followed the instructions on the previous posts but it didn't work for me.

Can someone please help me? Thanks in advance.

---

### Post by ganesh on 2009-11-08
Is there a version available for Karmic?

Thanks in advance.

---

### Post by seanscullion on 2010-04-12
The previous instructions worked for me back in a previous version of ubuntu, but since installing ubuntu 9.10, karmic koala, my camera has been lost completely and the above instructions no longer work to restore it:

[COLOR="RoyalBlue"][FONT="Courier New"]
sean@renegade:~/tmp/2/r5u870$ sudo make clean
make -C /lib/modules/2.6.31-17-generic/build M=/home/sean/tmp/2/r5u870 clean
make[1]: Entering directory `/usr/src/linux-headers-2.6.31-17-generic'
  CLEAN   /home/sean/tmp/2/r5u870/.tmp_versions
make[1]: Leaving directory `/usr/src/linux-headers-2.6.31-17-generic'
rm -f Module.symvers

sean@renegade:~/tmp/2/r5u870$ 

sean@renegade:~/tmp/2/r5u870$ sudo make
make -C /lib/modules/2.6.31-17-generic/build M=/home/sean/tmp/2/r5u870 V=0 modules
make[1]: Entering directory `/usr/src/linux-headers-2.6.31-17-generic'
  CC [M]  /home/sean/tmp/2/r5u870/usbcam/usbcam_fops.o
/home/sean/tmp/2/r5u870/usbcam/usbcam_fops.c: In function ‘usbcam_v4l_vidioc_querycap’:
/home/sean/tmp/2/r5u870/usbcam/usbcam_fops.c:522: error: ‘struct device’ has no member named ‘bus_id’
/home/sean/tmp/2/r5u870/usbcam/usbcam_fops.c: In function ‘usbcam_v4l_ioctl’:
/home/sean/tmp/2/r5u870/usbcam/usbcam_fops.c:1170: warning: passing argument 1 of ‘video_usercopy’ from incompatible pointer type
include/media/v4l2-ioctl.h:298: note: expected ‘struct file *’ but argument is of type ‘struct inode *’
/home/sean/tmp/2/r5u870/usbcam/usbcam_fops.c:1170: warning: passing argument 2 of ‘video_usercopy’ makes integer from pointer without a cast
include/media/v4l2-ioctl.h:298: note: expected ‘unsigned int’ but argument is of type ‘struct file *’
/home/sean/tmp/2/r5u870/usbcam/usbcam_fops.c:1170: warning: passing argument 4 of ‘video_usercopy’ makes pointer from integer without a cast
include/media/v4l2-ioctl.h:298: note: expected ‘v4l2_kioctl’ but argument is of type ‘long unsigned int’
/home/sean/tmp/2/r5u870/usbcam/usbcam_fops.c:1170: error: too many arguments to function ‘video_usercopy’
/home/sean/tmp/2/r5u870/usbcam/usbcam_fops.c:1174: warning: passing argument 1 of ‘video_ioctl2’ from incompatible pointer type
include/media/v4l2-ioctl.h:302: note: expected ‘struct file *’ but argument is of type ‘struct inode *’
/home/sean/tmp/2/r5u870/usbcam/usbcam_fops.c:1174: warning: passing argument 2 of ‘video_ioctl2’ makes integer from pointer without a cast
include/media/v4l2-ioctl.h:302: note: expected ‘unsigned int’ but argument is of type ‘struct file *’
/home/sean/tmp/2/r5u870/usbcam/usbcam_fops.c:1174: error: too many arguments to function ‘video_ioctl2’
/home/sean/tmp/2/r5u870/usbcam/usbcam_fops.c:1162: warning: unused variable ‘udp’
make[3]: *** [/home/sean/tmp/2/r5u870/usbcam/usbcam_fops.o] Error 1
make[2]: *** [/home/sean/tmp/2/r5u870/usbcam] Error 2
make[1]: *** [_module_/home/sean/tmp/2/r5u870] Error 2
make[1]: Leaving directory `/usr/src/linux-headers-2.6.31-17-generic'
make: *** [all] Error 2
[/FONT]
[/COLOR]



did anyone else have this problem? better still, did anyone else recover from this problem?

[COLOR="Purple"][FONT="Courier New"]sean@renegade:~/tmp/2/r5u870$ lsusb
Bus 001 Device 003: ID 05ca:1839 Ricoh Co., Ltd Visual Communication Camera VGP-VCC6 [R5U870]
[/FONT]
[/COLOR]
someone back on page 1 suggested removing all old version of r5u870 - but i'm not sure how to check i've done that successfully. any pointers?

and last question, does the r5u870 work under both gnome and kde? or only one of these?

thanks for your help :)

Sean

---

### Post by zotrules on 2010-04-14
Yo, Sean, try this:
Get the r5u870 folder and put it somewhere; like "/Documents", for example.
Now shoot a terminal and type:

.........................
sudo modprobe -r uvcvideo

sudo modprobe -r r5u870

cd Documents/r5u870
sudo make
sudo make install
sudo modprobe r5u870

Now type again: 

dmesg

this will list a couple of things, but at the end it should say something like "registering r5u870..." something like this.
Try now to open skype or emesene, or amsn. check at the properties>video devices. it should work. otherwise, something else should be wrong.
i've got it working some time ago, but i've got to be flat honest with you; linux sucks in these areas. Darn it, once you install something in windows, you know where to look, you know exactly what to do if something goes wrong... this ubuntu appears to be a challenge.
by the way, i am using 10.04 lucid, which is still in beta release, although, 100 times better than koala, yet, it fails badly to satisfy me as i wish it to /// i wanted to give up on window$ once and for all, but still...  let me know if anything changed.

---

### Post by aveminus on 2010-07-09
**@zotrules**
:popcorn:
Thanx for the info. It worked out fine for me.

---

### Post by siabost on 2010-08-08
Hi zotrules,

Thanks for that.

Mine was a new install of 10.04 on a Sony VAIO VGN-Z18E so I didn't use the two lines > sudo modprobe -r uvcvideo

sudo modprobe -r r5u870

Should I have done? EDIT: Just had to, as when I rebooted the image was upside down! Right way up now though :-)

The reason I ask is that the webcam works fine with Cheese on 320x240 but on 640x480 I get two duplicate images in the top third of the window with the bottom two thirds a solid green colour.

Is there any way to clear this final hurdle?

Thanks again. :D

---

### Post by zotrules on 2010-08-21
Siabost, for some reasons, this webcam will work on Ubuntu only in one resolution. I think it has to do with the programs being used. I get the very same problem if i use it with skype. I have tried everything and cannot fix it. But, i suppose, since in Ubuntu everything is a file, even the configuration settings, it must be curable.
when you try it with cheese and switch to the unsupported resolution; try running dmesg in a terminal, and you will see exactly what is going wrong with it. For some reasons, the program is trying to force the camera work on an, apparently, unsupported resolution. I have no idea to this point as to why this is happening. that is exactly why i wrote above that i tend to dislike Ubuntu about this. I could fix it if that happened on windows, but Ubuntu??? very, very much unsupported -  at least to my liking.
I am very certain though that this problem CAN be solved. I just don't have the neccessary expertise. sorry. :D

---

### Post by RDT1 on 2010-09-14
Well i am a complete an utter beginner and having some 1 problem. After doing the terminal commands at the start i ran into issues so used the .deb package @ [http://www.palmix.org/r5u870-en.html](http://www.palmix.org/r5u870-en.html) which installed etc fine. 

My issue is cheese only runs at th 320x240 resolution (which above you say cannot be fixed at present :S and also the image is upside down ! if anyone can help would be much appreciated.

Oh and just relised i have the 05ca:1837 Motion eye according to skype.

Upsidedown Fix: [http://ubuntuforums.org/showthread.php?t=838210](http://ubuntuforums.org/showthread.php?t=838210) source is down currently though....

---

### Post by siabost on 2010-09-15
Hi RTD1,

I had the same upside down problem upon reboot.

Check the middle part of my post of 8th Aug above for the two commands (in terminal) that worked for me.

---

### Post by RDT1 on 2010-09-16
> **siabost said:**
> Hi RTD1,

I had the same upside down problem upon reboot.

Check the middle part of my post of 8th Aug above for the two commands (in terminal) that worked for me.
Cheers man. Just tried them now and still have the same problem.... oh well .. without them i would occasionally have it right way the "boot" seemed to chose its position. so illl just reboot until i get it right ahah

---

### Post by srinivas_m on 2010-10-25
Hi, I am using ubuntu 10.4 on my Sony vaio(VGN-CR320E) laptop.
In that Motion eye inbuilt camera is there. Camera is not working in ubuntu 10.4, but it worked fine in XP and windows vista.

The output for the #lsusb command is
 srinivas@srinivas-laptop:~$ lsusb
Bus 007 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 006 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 005: ID 044e:3012 Alps Electric Co., Ltd 
Bus 003 Device 004: ID 044e:3013 Alps Electric Co., Ltd 
Bus 003 Device 003: ID 044e:3010 Alps Electric Co., Ltd Bluetooth Adapter
Bus 003 Device 002: ID 044e:3011 Alps Electric Co., Ltd 
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub

In The above info there is no info about camera. What should i do get the camera info and make it to work.
please help me to resolve this problem so that i can use inbuilt motion eye camera.


Thanks in advance
srinivas

---

### Post by Jonners59 on 2010-12-04
At least I have found a thread with the problem I have.  Not getting much response on my thread....
[URL="http://ubuntu-ky.ubuntuforums.org/showthread.php?t=1628821"]
http://ubuntu-ky.ubuntuforums.org/showthread.php?t=1628821[/URL]

I tried below on my wife's sony viao running 10.10

I still gets errors:

[HTML]chiara@chiara-Pinkviao:~/r5u870$ sudo make install
make -C /lib/modules/2.6.35-23-generic/build M=/home/chiara/r5u870 V=0 modules
make[1]: Entering directory `/usr/src/linux-headers-2.6.35-23-generic'
  CC [M]  /home/chiara/r5u870/usbcam/usbcam_fops.o
/home/chiara/r5u870/usbcam/usbcam_fops.c: In function ‘usbcam_v4l_vidioc_querycap’:
/home/chiara/r5u870/usbcam/usbcam_fops.c:522: error: ‘struct device’ has no member named ‘bus_id’
/home/chiara/r5u870/usbcam/usbcam_fops.c: In function ‘usbcam_v4l_ioctl’:
/home/chiara/r5u870/usbcam/usbcam_fops.c:1170: warning: passing argument 1 of ‘video_usercopy’ from incompatible pointer type
include/media/v4l2-ioctl.h:320: note: expected ‘struct file *’ but argument is of type ‘struct inode *’
/home/chiara/r5u870/usbcam/usbcam_fops.c:1170: warning: passing argument 2 of ‘video_usercopy’ makes integer from pointer without a cast
include/media/v4l2-ioctl.h:320: note: expected ‘unsigned int’ but argument is of type ‘struct file *’
/home/chiara/r5u870/usbcam/usbcam_fops.c:1170: warning: passing argument 4 of ‘video_usercopy’ makes pointer from integer without a cast
include/media/v4l2-ioctl.h:320: note: expected ‘v4l2_kioctl’ but argument is of type ‘long unsigned int’
/home/chiara/r5u870/usbcam/usbcam_fops.c:1170: error: too many arguments to function ‘video_usercopy’
/home/chiara/r5u870/usbcam/usbcam_fops.c:1174: warning: passing argument 1 of ‘video_ioctl2’ from incompatible pointer type
include/media/v4l2-ioctl.h:324: note: expected ‘struct file *’ but argument is of type ‘struct inode *’
/home/chiara/r5u870/usbcam/usbcam_fops.c:1174: warning: passing argument 2 of ‘video_ioctl2’ makes integer from pointer without a cast
include/media/v4l2-ioctl.h:324: note: expected ‘unsigned int’ but argument is of type ‘struct file *’
/home/chiara/r5u870/usbcam/usbcam_fops.c:1174: error: too many arguments to function ‘video_ioctl2’
/home/chiara/r5u870/usbcam/usbcam_fops.c:1162: warning: unused variable ‘udp’
make[3]: *** [/home/chiara/r5u870/usbcam/usbcam_fops.o] Error 1
make[2]: *** [/home/chiara/r5u870/usbcam] Error 2
make[1]: *** [_module_/home/chiara/r5u870] Error 2
make[1]: Leaving directory `/usr/src/linux-headers-2.6.35-23-generic'
make: *** [all] Error 2
chiara@chiara-Pinkviao:~/r5u870$ modprobe r5u870
FATAL: Module r5u870 not found.
chiara@chiara-Pinkviao:~/r5u870$ xawtv /dev/video0
This is xawtv-3.95.dfsg.1, running on Linux/i686 (2.6.35-23-generic)
xinerama 0: 1280x800+0+0
can't open /dev/video0: No such file or directory
v4l-conf had some trouble, trying to continue anyway
v4l2: open /dev/video0: No such file or directory
v4l2: open /dev/video0: No such file or directory
v4l: open /dev/video0: No such file or directory
no video grabber device available
chiara@chiara-Pinkviao:~/r5u870$ [/HTML]

AND YES, it really is pink!

---

### Post by Hellaxe on 2010-12-19
Hello guys:
this camera is annoying me to much.
This is what i get from the make.log:
```
/var/lib/dkms/r5u870/0.11.5/build/usbcam/usbcam_util.c: In function &#8216;usbcam_urb_allocbuf&#8217;:
/var/lib/dkms/r5u870/0.11.5/build/usbcam/usbcam_util.c:164: error: implicit declaration of function &#8216;usb_buffer_alloc&#8217;
/var/lib/dkms/r5u870/0.11.5/build/usbcam/usbcam_util.c:167: warning: assignment makes pointer from integer without a cast
/var/lib/dkms/r5u870/0.11.5/build/usbcam/usbcam_util.c: In function &#8216;usbcam_urb_freebuf&#8217;:
/var/lib/dkms/r5u870/0.11.5/build/usbcam/usbcam_util.c:178: error: implicit declaration of function &#8216;usb_buffer_free&#8217;
make[2]: *** [/var/lib/dkms/r5u870/0.11.5/build/usbcam/usbcam_util.o] Error 1
make[1]: *** [/var/lib/dkms/r5u870/0.11.5/build/usbcam] Error 2
make: *** [_module_/var/lib/dkms/r5u870/0.11.5/build] Error 2
```

By the way I'm using this *.deb
[http://www.arakhne.org/ricoh/](http://www.arakhne.org/ricoh/)
I think it's the same thing but for some reason the dkms package is not working with the kernel 2.6.35-23-generic.
Any help???
thanks


BIG EDIT: somehow I discovered the link: [http://www.gilesbathgate.com/tag/linux/](http://www.gilesbathgate.com/tag/linux/)
and now this stupid camera is working. Thanks to this man, all credits are to him.

---

### Post by Jonners59 on 2010-12-20
> **Hellaxe said:**
> Hello guys:
this camera is annoying me to much.

Any help???
thanks.

Me, too...  But no replies to the thread for support, which is even more frustrating.

Many thanks....  Your link worked!!!!!!!!!!!!!!!!!

---

### Post by zotrules on 2011-01-17
> **Jonners59 said:**
> Me, too...  But no replies to the thread for support, which is even more frustrating.

Many thanks....  Your link worked!!!!!!!!!!!!!!!!!

Yet, you get a very lousy picture. the quality is very bad, to say the least. very dark picture. unclear, noisy. it works with one program and's dead with any other. I've arrived to the conclusion that It's not the driver. it could be the kernel, video card or the programs.

---

### Post by siabost on 2011-04-30
It's the latest kernels. Support for videodev.h has been removed - see comment on Kubuntu Forum [http://kubuntuforums.net/forums/index.php?topic=3115676.0]("http://kubuntuforums.net/forums/index.php?topic=3115676.0")

SOLVED (for me anyway):
[http://ubuntuforums.org/showthread.php?t=1544564&highlight=videodev.h&page=3]("http://ubuntuforums.org/showthread.php?t=1544564&highlight=videodev.h&page=3")
I'm running Ubuntu 11.04, kernel 2.6.38-8-generic & works splendidly

Enter the following lines (one at a time) in the terminal - you will be asked your password after entering the first line (the password entry will not show in the terminal but it is being registered).

> sudo add-apt-repository ppa:r5u87x-loader/ppa
sudo apt-get update
sudo apt-get install r5u87x
sudo /usr/share/r5u87x/r5u87x-download-firmware.sh 

You'll get a GPG authentication warning but ignore that & also a y/n warning (enter y) after the last line shown above.

Good Luck :-)

---

### Post by reflux21 on 2011-08-12
Thanks siabost!

You have helped immensely!

---

### Post by klopi on 2011-09-21
thank you [siabost]("http://ubuntuforums.org/member.php?u=579328") so much.
I have used your guide and now the webcam is turn on
My pc is a sony vaio vgn-cr21z

Thank you more

---

