---
title: "MS LifeCam VX-1000 webcam driver"
date: 2010-01-10
forum: Hardware
---

### Post by hobo14 on 2010-01-10
There have been several threads on this, but none have helped me.

The most promising one was this: [http://ubuntuforums.org/showthread.php?t=1321194]("http://ubuntuforums.org/showthread.php?t=1321194")

but (as you can see in that thread - started a new thread because that one's tagged SOLVED) I had a problem when trying to make.

It went fine until this:
```

CC [M]  /home/collins/Desktop/v4l-dvb-b6b82258cf5e/v4l/et61x251_core.o
/home/collins/Desktop/v4l-dvb-b6b82258cf5e/v4l/et61x251_core.c: In function 'et61x251_ioctl_v4l2':
/home/collins/Desktop/v4l-dvb-b6b82258cf5e/v4l/et61x251_core.c:2500: warning: the frame size of 1256 bytes is larger than 1024 bytes
  CC [M]  /home/collins/Desktop/v4l-dvb-b6b82258cf5e/v4l/et61x251_tas5130d1b.o
  CC [M]  /home/collins/Desktop/v4l-dvb-b6b82258cf5e/v4l/firedtv-avc.o
  CC [M]  /home/collins/Desktop/v4l-dvb-b6b82258cf5e/v4l/firedtv-ci.o
  CC [M]  /home/collins/Desktop/v4l-dvb-b6b82258cf5e/v4l/firedtv-dvb.o
  CC [M]  /home/collins/Desktop/v4l-dvb-b6b82258cf5e/v4l/firedtv-fe.o
  CC [M]  /home/collins/Desktop/v4l-dvb-b6b82258cf5e/v4l/firedtv-1394.o
/home/collins/Desktop/v4l-dvb-b6b82258cf5e/v4l/firedtv-1394.c:21:17: error: dma.h: No such file or directory
/home/collins/Desktop/v4l-dvb-b6b82258cf5e/v4l/firedtv-1394.c:22:21: error: csr1212.h: No such file or directory
/home/collins/Desktop/v4l-dvb-b6b82258cf5e/v4l/firedtv-1394.c:23:23: error: highlevel.h: No such file or directory
/home/collins/Desktop/v4l-dvb-b6b82258cf5e/v4l/firedtv-1394.c:24:19: error: hosts.h: No such file or directory
/home/collins/Desktop/v4l-dvb-b6b82258cf5e/v4l/firedtv-1394.c:25:22: error: ieee1394.h: No such file or directory
/home/collins/Desktop/v4l-dvb-b6b82258cf5e/v4l/firedtv-1394.c:26:17: error: iso.h: No such file or directory
/home/collins/Desktop/v4l-dvb-b6b82258cf5e/v4l/firedtv-1394.c:27:21: error: nodemgr.h: No such file or directory
/home/collins/Desktop/v4l-dvb-b6b82258cf5e/v4l/firedtv-1394.c:40: warning: 'struct hpsb_iso' declared inside parameter list
/home/collins/Desktop/v4l-dvb-b6b82258cf5e/v4l/firedtv-1394.c:40: warning: its scope is only this definition or declaration, which is probably not what you want
/home/collins/Desktop/v4l-dvb-b6b82258cf5e/v4l/firedtv-1394.c: In function 'rawiso_activity_cb':
/home/collins/Desktop/v4l-dvb-b6b82258cf5e/v4l/firedtv-1394.c:56: error: dereferencing pointer to incomplete type
/home/collins/Desktop/v4l-dvb-b6b82258cf5e/v4l/firedtv-1394.c:57: error: implicit declaration of function 'hpsb_iso_n_ready'
/home/collins/Desktop/v4l-dvb-b6b82258cf5e/v4l/firedtv-1394.c:64: error: dereferencing pointer to incomplete type
/home/collins/Desktop/v4l-dvb-b6b82258cf5e/v4l/firedtv-1394.c:65: error: implicit declaration of function 'dma_region_i'
/home/collins/Desktop/v4l-dvb-b6b82258cf5e/v4l/firedtv-1394.c:65: error: dereferencing pointer to incomplete type
/home/collins/Desktop/v4l-dvb-b6b82258cf5e/v4l/firedtv-1394.c:65: error: expected expression before 'unsigned'
/home/collins/Desktop/v4l-dvb-b6b82258cf5e/v4l/firedtv-1394.c:66: warning: assignment makes pointer from integer without a cast
/home/collins/Desktop/v4l-dvb-b6b82258cf5e/v4l/firedtv-1394.c:67: error: dereferencing pointer to incomplete type
/home/collins/Desktop/v4l-dvb-b6b82258cf5e/v4l/firedtv-1394.c:71: error: dereferencing pointer to incomplete type
/home/collins/Desktop/v4l-dvb-b6b82258cf5e/v4l/firedtv-1394.c:85: error: implicit declaration of function 'hpsb_iso_recv_release_packets'
/home/collins/Desktop/v4l-dvb-b6b82258cf5e/v4l/firedtv-1394.c: In function 'node_of':
/home/collins/Desktop/v4l-dvb-b6b82258cf5e/v4l/firedtv-1394.c:90: error: dereferencing pointer to incomplete type
/home/collins/Desktop/v4l-dvb-b6b82258cf5e/v4l/firedtv-1394.c:90: warning: type defaults to 'int' in declaration of '__mptr'
/home/collins/Desktop/v4l-dvb-b6b82258cf5e/v4l/firedtv-1394.c:90: warning: initialization from incompatible pointer type
/home/collins/Desktop/v4l-dvb-b6b82258cf5e/v4l/firedtv-1394.c:90: error: invalid use of undefined type 'struct unit_directory'
/home/collins/Desktop/v4l-dvb-b6b82258cf5e/v4l/firedtv-1394.c: In function 'node_lock':
/home/collins/Desktop/v4l-dvb-b6b82258cf5e/v4l/firedtv-1394.c:97: error: implicit declaration of function 'hpsb_node_lock'
/home/collins/Desktop/v4l-dvb-b6b82258cf5e/v4l/firedtv-1394.c:97: error: 'EXTCODE_COMPARE_SWAP' undeclared (first use in this function)
/home/collins/Desktop/v4l-dvb-b6b82258cf5e/v4l/firedtv-1394.c:97: error: (Each undeclared identifier is reported only once
/home/collins/Desktop/v4l-dvb-b6b82258cf5e/v4l/firedtv-1394.c:97: error: for each function it appears in.)
/home/collins/Desktop/v4l-dvb-b6b82258cf5e/v4l/firedtv-1394.c:98: error: 'quadlet_t' undeclared (first use in this function)
/home/collins/Desktop/v4l-dvb-b6b82258cf5e/v4l/firedtv-1394.c:98: error: expected expression before ')' token
/home/collins/Desktop/v4l-dvb-b6b82258cf5e/v4l/firedtv-1394.c: In function 'node_read':
/home/collins/Desktop/v4l-dvb-b6b82258cf5e/v4l/firedtv-1394.c:106: error: implicit declaration of function 'hpsb_node_read'
/home/collins/Desktop/v4l-dvb-b6b82258cf5e/v4l/firedtv-1394.c: In function 'node_write':
/home/collins/Desktop/v4l-dvb-b6b82258cf5e/v4l/firedtv-1394.c:111: error: implicit declaration of function 'hpsb_node_write'
/home/collins/Desktop/v4l-dvb-b6b82258cf5e/v4l/firedtv-1394.c: In function 'start_iso':
/home/collins/Desktop/v4l-dvb-b6b82258cf5e/v4l/firedtv-1394.c:122: error: implicit declaration of function 'hpsb_iso_recv_init'
/home/collins/Desktop/v4l-dvb-b6b82258cf5e/v4l/firedtv-1394.c:122: error: dereferencing pointer to incomplete type
/home/collins/Desktop/v4l-dvb-b6b82258cf5e/v4l/firedtv-1394.c:124: error: 'HPSB_ISO_DMA_DEFAULT' undeclared (first use in this function)
/home/collins/Desktop/v4l-dvb-b6b82258cf5e/v4l/firedtv-1394.c:126: warning: assignment makes pointer from integer without a cast
/home/collins/Desktop/v4l-dvb-b6b82258cf5e/v4l/firedtv-1394.c:133: error: implicit declaration of function 'hpsb_iso_recv_start'
/home/collins/Desktop/v4l-dvb-b6b82258cf5e/v4l/firedtv-1394.c:136: error: implicit declaration of function 'hpsb_iso_shutdown'
/home/collins/Desktop/v4l-dvb-b6b82258cf5e/v4l/firedtv-1394.c: In function 'stop_iso':
/home/collins/Desktop/v4l-dvb-b6b82258cf5e/v4l/firedtv-1394.c:147: error: implicit declaration of function 'hpsb_iso_stop'
/home/collins/Desktop/v4l-dvb-b6b82258cf5e/v4l/firedtv-1394.c: At top level:
/home/collins/Desktop/v4l-dvb-b6b82258cf5e/v4l/firedtv-1394.c:162: warning: 'struct hpsb_host' declared inside parameter list
/home/collins/Desktop/v4l-dvb-b6b82258cf5e/v4l/firedtv-1394.c: In function 'fcp_request':
/home/collins/Desktop/v4l-dvb-b6b82258cf5e/v4l/firedtv-1394.c:175: error: dereferencing pointer to incomplete type
/home/collins/Desktop/v4l-dvb-b6b82258cf5e/v4l/firedtv-1394.c:176: error: dereferencing pointer to incomplete type
/home/collins/Desktop/v4l-dvb-b6b82258cf5e/v4l/firedtv-1394.c: In function 'node_probe':
/home/collins/Desktop/v4l-dvb-b6b82258cf5e/v4l/firedtv-1394.c:190: error: dereferencing pointer to incomplete type
/home/collins/Desktop/v4l-dvb-b6b82258cf5e/v4l/firedtv-1394.c:190: warning: type defaults to 'int' in declaration of '__mptr'
/home/collins/Desktop/v4l-dvb-b6b82258cf5e/v4l/firedtv-1394.c:190: warning: initialization from incompatible pointer type
/home/collins/Desktop/v4l-dvb-b6b82258cf5e/v4l/firedtv-1394.c:190: error: invalid use of undefined type 'struct unit_directory'
/home/collins/Desktop/v4l-dvb-b6b82258cf5e/v4l/firedtv-1394.c:195: error: dereferencing pointer to incomplete type
/home/collins/Desktop/v4l-dvb-b6b82258cf5e/v4l/firedtv-1394.c:195: error: 'quadlet_t' undeclared (first use in this function)
/home/collins/Desktop/v4l-dvb-b6b82258cf5e/v4l/firedtv-1394.c:196: error: implicit declaration of function 'CSR1212_TEXTUAL_DESCRIPTOR_LEAF_DATA'
/home/collins/Desktop/v4l-dvb-b6b82258cf5e/v4l/firedtv-1394.c:196: error: dereferencing pointer to incomplete type
/home/collins/Desktop/v4l-dvb-b6b82258cf5e/v4l/firedtv-1394.c:196: warning: assignment makes pointer from integer without a cast
/home/collins/Desktop/v4l-dvb-b6b82258cf5e/v4l/firedtv-1394.c: At top level:
/home/collins/Desktop/v4l-dvb-b6b82258cf5e/v4l/firedtv-1394.c:252: warning: 'struct unit_directory' declared inside parameter list
/home/collins/Desktop/v4l-dvb-b6b82258cf5e/v4l/firedtv-1394.c: In function 'node_update':
/home/collins/Desktop/v4l-dvb-b6b82258cf5e/v4l/firedtv-1394.c:254: error: dereferencing pointer to incomplete type
/home/collins/Desktop/v4l-dvb-b6b82258cf5e/v4l/firedtv-1394.c: At top level:
/home/collins/Desktop/v4l-dvb-b6b82258cf5e/v4l/firedtv-1394.c:262: error: variable 'fdtv_driver' has initializer but incomplete type
/home/collins/Desktop/v4l-dvb-b6b82258cf5e/v4l/firedtv-1394.c:263: error: unknown field 'name' specified in initializer
/home/collins/Desktop/v4l-dvb-b6b82258cf5e/v4l/firedtv-1394.c:263: warning: excess elements in struct initializer
/home/collins/Desktop/v4l-dvb-b6b82258cf5e/v4l/firedtv-1394.c:263: warning: (near initialization for 'fdtv_driver')
/home/collins/Desktop/v4l-dvb-b6b82258cf5e/v4l/firedtv-1394.c:264: error: unknown field 'id_table' specified in initializer
/home/collins/Desktop/v4l-dvb-b6b82258cf5e/v4l/firedtv-1394.c:264: warning: excess elements in struct initializer
/home/collins/Desktop/v4l-dvb-b6b82258cf5e/v4l/firedtv-1394.c:264: warning: (near initialization for 'fdtv_driver')
/home/collins/Desktop/v4l-dvb-b6b82258cf5e/v4l/firedtv-1394.c:265: error: unknown field 'update' specified in initializer
/home/collins/Desktop/v4l-dvb-b6b82258cf5e/v4l/firedtv-1394.c:265: warning: excess elements in struct initializer
/home/collins/Desktop/v4l-dvb-b6b82258cf5e/v4l/firedtv-1394.c:265: warning: (near initialization for 'fdtv_driver')
/home/collins/Desktop/v4l-dvb-b6b82258cf5e/v4l/firedtv-1394.c:266: error: unknown field 'driver' specified in initializer
/home/collins/Desktop/v4l-dvb-b6b82258cf5e/v4l/firedtv-1394.c:266: error: extra brace group at end of initializer
/home/collins/Desktop/v4l-dvb-b6b82258cf5e/v4l/firedtv-1394.c:266: error: (near initialization for 'fdtv_driver')
/home/collins/Desktop/v4l-dvb-b6b82258cf5e/v4l/firedtv-1394.c:269: warning: excess elements in struct initializer
/home/collins/Desktop/v4l-dvb-b6b82258cf5e/v4l/firedtv-1394.c:269: warning: (near initialization for 'fdtv_driver')
/home/collins/Desktop/v4l-dvb-b6b82258cf5e/v4l/firedtv-1394.c:272: error: variable 'fdtv_highlevel' has initializer but incomplete type
/home/collins/Desktop/v4l-dvb-b6b82258cf5e/v4l/firedtv-1394.c:273: error: unknown field 'name' specified in initializer
/home/collins/Desktop/v4l-dvb-b6b82258cf5e/v4l/firedtv-1394.c:273: warning: excess elements in struct initializer
/home/collins/Desktop/v4l-dvb-b6b82258cf5e/v4l/firedtv-1394.c:273: warning: (near initialization for 'fdtv_highlevel')
/home/collins/Desktop/v4l-dvb-b6b82258cf5e/v4l/firedtv-1394.c:274: error: unknown field 'fcp_request' specified in initializer
/home/collins/Desktop/v4l-dvb-b6b82258cf5e/v4l/firedtv-1394.c:274: warning: excess elements in struct initializer
/home/collins/Desktop/v4l-dvb-b6b82258cf5e/v4l/firedtv-1394.c:274: warning: (near initialization for 'fdtv_highlevel')
/home/collins/Desktop/v4l-dvb-b6b82258cf5e/v4l/firedtv-1394.c: In function 'fdtv_1394_init':
/home/collins/Desktop/v4l-dvb-b6b82258cf5e/v4l/firedtv-1394.c:281: error: implicit declaration of function 'hpsb_register_highlevel'
/home/collins/Desktop/v4l-dvb-b6b82258cf5e/v4l/firedtv-1394.c:282: error: implicit declaration of function 'hpsb_register_protocol'
/home/collins/Desktop/v4l-dvb-b6b82258cf5e/v4l/firedtv-1394.c:285: error: implicit declaration of function 'hpsb_unregister_highlevel'
/home/collins/Desktop/v4l-dvb-b6b82258cf5e/v4l/firedtv-1394.c: In function 'fdtv_1394_exit':
/home/collins/Desktop/v4l-dvb-b6b82258cf5e/v4l/firedtv-1394.c:292: error: implicit declaration of function 'hpsb_unregister_protocol'
make[3]: *** [/home/collins/Desktop/v4l-dvb-b6b82258cf5e/v4l/firedtv-1394.o] Error 1
make[2]: *** [_module_/home/collins/Desktop/v4l-dvb-b6b82258cf5e/v4l] Error 2
make[2]: Leaving directory `/usr/src/linux-headers-2.6.31-16-generic'
make[1]: *** [default] Error 2
make[1]: Leaving directory `/home/collins/Desktop/v4l-dvb-b6b82258cf5e/v4l'
make: *** [all] Error 2
```

Can anyone tell me why this is happening, or what to do about it?

---

### Post by jesterthejedi on 2010-01-11
I used to do

make distclean
make clean
sudo make menuconfig
make
sudo make install

but now this doesnt work, as the input is scrambled, see image

you can however erase the errors by unselecting all but the v4l gspca sncxx9 drivers on the menuconfig dialog box.

---

### Post by jesterthejedi on 2010-01-11
gstreamer-properties box

---

