---
title: "USB ADSL Modem Prolink 8000"
date: 2005-07-10
forum: Hardware &amp; Laptops
---

### Post by ngensys on 2005-07-10
Hi I'm a newbie in Linux.
I have installed Ubuntu and it has no problems except for detecting my Prolink Hurricane 8000 usb modem.
I found a compatible driver in the web called amedyn.
The problem is when I try to "make" I get this :

root@FreedomZGMF:/tmp/amedyn # make
cd init && make clean
make[1]: Entering directory `/tmp/amedyn/init'
rm -f amload amioctl amloaddbg amloaddbgt
make[1]: Leaving directory `/tmp/amedyn/init'
cd module && make clean
make[1]: Entering directory `/tmp/amedyn/module'
rm -f *.o .*.flags *.ko *.mod.* .*.o.cmd .*.ko.cmd
make[1]: Leaving directory `/tmp/amedyn/module'
cd bridged && make clean
make[1]: Entering directory `/tmp/amedyn/bridged'
rm -f br2684ctl
make[1]: Leaving directory `/tmp/amedyn/bridged'
cd amcontrol && make clean
make[1]: Entering directory `/tmp/amedyn/amcontrol'
rm -f amcontrol amcontroldbg amcontroldbgt
make[1]: Leaving directory `/tmp/amedyn/amcontrol'
cd init && make && make install
make[1]: Entering directory `/tmp/amedyn/init'
gcc -O2 -Wstrict-prototypes -fomit-frame-pointer -pipe -march=i686 -Wall -DLINUX -Wsign-compare -I../include -lusb  amload.c -o amload
amload.c:65:17: usb.h: No such file or directory
In file included from amload.c:66:
../include/usbi.h:4:17: usb.h: No such file or directory
In file included from amload.c:66:
../include/usbi.h:49: error: syntax error before '*' token
../include/usbi.h:49: warning: function declaration isn't a prototype
../include/usbi.h:54: error: syntax error before '*' token
../include/usbi.h:54: warning: function declaration isn't a prototype
../include/usbi.h:55: error: syntax error before '*' token
../include/usbi.h:55: warning: function declaration isn't a prototype
amload.c:223: error: syntax error before '*' token
amload.c:224: warning: function declaration isn't a prototype
amload.c: In function `transfer_ctrl_msg':
amload.c:234: warning: implicit declaration of function `usb_control_msg'
amload.c:234: error: `adsl_handle' undeclared (first use in this function)
amload.c:234: error: (Each undeclared identifier is reported only once
amload.c:234: error: for each function it appears in.)
amload.c:234: error: `requesttype' undeclared (first use in this function)
amload.c:234: error: `request' undeclared (first use in this function)
amload.c:234: error: `value' undeclared (first use in this function)
amload.c:234: error: `buf' undeclared (first use in this function)
amload.c:234: error: `size' undeclared (first use in this function)
amload.c:244: warning: implicit declaration of function `usb_strerror'
amload.c:244: warning: format argument is not a pointer (arg 2)
amload.c:246: warning: implicit declaration of function `usb_clear_halt'
amload.c: At top level:
amload.c:262: error: syntax error before '*' token
amload.c:263: warning: function declaration isn't a prototype
amload.c: In function `read_bulk':
amload.c:268: error: `buf' undeclared (first use in this function)
amload.c:274: warning: implicit declaration of function `usb_bulk_read'
amload.c:274: error: `adsl_handle' undeclared (first use in this function)
amload.c:274: error: `ep' undeclared (first use in this function)
amload.c:274: error: `size' undeclared (first use in this function)
amload.c:284: warning: format argument is not a pointer (arg 2)
amload.c: At top level:
amload.c:301: error: syntax error before '*' token
amload.c:302: warning: function declaration isn't a prototype
amload.c: In function `send_bulk':
amload.c:308: error: `nfil' undeclared (first use in this function)
amload.c:314: warning: implicit declaration of function `usb_bulk_write'
amload.c:314: error: `adsl_handle' undeclared (first use in this function)
amload.c:314: error: `ep' undeclared (first use in this function)
amload.c:314: error: `buf' undeclared (first use in this function)
amload.c:314: error: `ncol' undeclared (first use in this function)
amload.c:324: warning: format argument is not a pointer (arg 2)
amload.c: At top level:
amload.c:361: error: syntax error before '*' token
amload.c:361: warning: function declaration isn't a prototype
amload.c: In function `clear_endpoints':
amload.c:362: error: `op' undeclared (first use in this function)
amload.c:363: warning: implicit declaration of function `usb_resetep'
amload.c:363: error: `adsl_handle' undeclared (first use in this function)
amload.c: At top level:
amload.c:373: error: syntax error before '*' token
amload.c:374: warning: function declaration isn't a prototype
amload.c: In function `send_block':
amload.c:377: error: `bufin' undeclared (first use in this function)
amload.c:377: error: `len' undeclared (first use in this function)
amload.c:380: error: `place' undeclared (first use in this function)
amload.c:383: error: `adsl_handle' undeclared (first use in this function)
amload.c: At top level:
amload.c:389: error: syntax error before '*' token
amload.c:390: warning: function declaration isn't a prototype
amload.c: In function `jump_to_address':
amload.c:396: error: `place' undeclared (first use in this function)
amload.c:400: error: `adsl_handle' undeclared (first use in this function)
amload.c: At top level:
amload.c:411: error: syntax error before '*' token
amload.c:412: warning: function declaration isn't a prototype
amload.c: In function `send_cmds_sync':
amload.c:420: error: `adsl_handle' undeclared (first use in this function)
amload.c: At top level:
amload.c:451: error: syntax error before '*' token
amload.c:452: warning: function declaration isn't a prototype
amload.c: In function `load_firmware':
amload.c:465: error: `adsl_handle' undeclared (first use in this function)
amload.c:611: error: `tmodem' undeclared (first use in this function)
amload.c: In function `init_modem':
amload.c:739: error: dereferencing pointer to incomplete type
amload.c:740: error: dereferencing pointer to incomplete type
amload.c: In function `main':
amload.c:783: error: `usb_dev_handle' undeclared (first use in this function)
amload.c:783: error: `adsl_handle' undeclared (first use in this function)
amload.c:834: warning: implicit declaration of function `usb_init'
amload.c:835: warning: implicit declaration of function `usb_find_busses'
amload.c:840: warning: implicit declaration of function `usb_find_devices'
amload.c:847: error: `usb_busses' undeclared (first use in this function)
amload.c:851: error: dereferencing pointer to incomplete type
amload.c:854: error: dereferencing pointer to incomplete type
amload.c:854: error: dereferencing pointer to incomplete type
amload.c:861: error: dereferencing pointer to incomplete type
amload.c:864: error: dereferencing pointer to incomplete type
amload.c:871: error: dereferencing pointer to incomplete type
amload.c:871: error: dereferencing pointer to incomplete type
amload.c:885: warning: implicit declaration of function `usb_open'
amload.c:892: warning: implicit declaration of function `usb_set_configuration'
amload.c:894: warning: format argument is not a pointer (arg 2)
amload.c:898: warning: implicit declaration of function `usb_claim_interface'
amload.c:900: warning: format argument is not a pointer (arg 2)
amload.c:905: warning: format argument is not a pointer (arg 2)
amload.c:910: warning: format argument is not a pointer (arg 2)
amload.c:919: warning: implicit declaration of function `usb_release_interface'
amload.c:921: warning: implicit declaration of function `usb_close'
make[1]: *** [amload] Error 1
make[1]: Leaving directory `/tmp/amedyn/init'
make: *** [AME_INIT] Error 2

==========================================================

Can someone help please.. :???: 
Thanks.

---

### Post by bernardfrancois on 2006-03-15
```
amload.c:65:17: usb.h: No such file or directory
```

Probably you don't have **libusb-dev**. Check the documentation ( the doc/index.htm file in the amedyn folder from the archive you downloaded ) for a full list of things you need to install prior to the installation.

---

