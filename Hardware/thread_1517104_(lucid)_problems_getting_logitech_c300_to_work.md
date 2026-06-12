---
title: "(lucid) problems getting logitech c300 to work"
date: 2010-06-24
forum: Hardware
---

### Post by unchartedstarr on 2010-06-24
I had read that the c300 webcam would work out of the box, but it did not. I did some research and found that it's supposed to be supported by the V4L-DVB drivers, so I followed the instructions here: [http://www.linuxtv.org/wiki/index.php/How_to_Obtain,_Build_and_Install_V4L-DVB_Device_Drivers](http://www.linuxtv.org/wiki/index.php/How_to_Obtain,_Build_and_Install_V4L-DVB_Device_Drivers)

but this happened: starr@starr-desktop:~/Desktop/v4l-dvb$ make
make -C /home/starr/Desktop/v4l-dvb/v4l 
make[1]: Entering directory `/home/starr/Desktop/v4l-dvb/v4l'
creating symbolic links...
make -C firmware prep
make[2]: Entering directory `/home/starr/Desktop/v4l-dvb/v4l/firmware'
make[2]: Leaving directory `/home/starr/Desktop/v4l-dvb/v4l/firmware'
make -C firmware
make[2]: Entering directory `/home/starr/Desktop/v4l-dvb/v4l/firmware'
make[2]: Nothing to be done for `default'.
make[2]: Leaving directory `/home/starr/Desktop/v4l-dvb/v4l/firmware'
Kernel build directory is /lib/modules/2.6.32-22-generic/build
make -C /lib/modules/2.6.32-22-generic/build SUBDIRS=/home/starr/Desktop/v4l-dvb/v4l  modules
make[2]: Entering directory `/usr/src/linux-headers-2.6.32-22-generic'
  CC [M]  /home/starr/Desktop/v4l-dvb/v4l/firedtv-1394.o
/home/starr/Desktop/v4l-dvb/v4l/firedtv-1394.c:22:17: error: dma.h: No such file or directory
/home/starr/Desktop/v4l-dvb/v4l/firedtv-1394.c:23:21: error: csr1212.h: No such file or directory
/home/starr/Desktop/v4l-dvb/v4l/firedtv-1394.c:24:23: error: highlevel.h: No such file or directory
/home/starr/Desktop/v4l-dvb/v4l/firedtv-1394.c:25:19: error: hosts.h: No such file or directory
/home/starr/Desktop/v4l-dvb/v4l/firedtv-1394.c:26:22: error: ieee1394.h: No such file or directory
/home/starr/Desktop/v4l-dvb/v4l/firedtv-1394.c:27:17: error: iso.h: No such file or directory
/home/starr/Desktop/v4l-dvb/v4l/firedtv-1394.c:28:21: error: nodemgr.h: No such file or directory
/home/starr/Desktop/v4l-dvb/v4l/firedtv-1394.c:41: warning: 'struct hpsb_iso' declared inside parameter list
/home/starr/Desktop/v4l-dvb/v4l/firedtv-1394.c:41: warning: its scope is only this definition or declaration, which is probably not what you want
/home/starr/Desktop/v4l-dvb/v4l/firedtv-1394.c: In function 'rawiso_activity_cb':
/home/starr/Desktop/v4l-dvb/v4l/firedtv-1394.c:57: error: dereferencing pointer to incomplete type
/home/starr/Desktop/v4l-dvb/v4l/firedtv-1394.c:58: error: implicit declaration of function 'hpsb_iso_n_ready'
/home/starr/Desktop/v4l-dvb/v4l/firedtv-1394.c:65: error: dereferencing pointer to incomplete type
/home/starr/Desktop/v4l-dvb/v4l/firedtv-1394.c:66: error: implicit declaration of function 'dma_region_i'
/home/starr/Desktop/v4l-dvb/v4l/firedtv-1394.c:66: error: dereferencing pointer to incomplete type
/home/starr/Desktop/v4l-dvb/v4l/firedtv-1394.c:66: error: expected expression before 'unsigned'
/home/starr/Desktop/v4l-dvb/v4l/firedtv-1394.c:68: error: dereferencing pointer to incomplete type
/home/starr/Desktop/v4l-dvb/v4l/firedtv-1394.c:72: error: dereferencing pointer to incomplete type
/home/starr/Desktop/v4l-dvb/v4l/firedtv-1394.c:86: error: implicit declaration of function 'hpsb_iso_recv_release_packets'
/home/starr/Desktop/v4l-dvb/v4l/firedtv-1394.c: In function 'node_of':
/home/starr/Desktop/v4l-dvb/v4l/firedtv-1394.c:91: error: dereferencing pointer to incomplete type
/home/starr/Desktop/v4l-dvb/v4l/firedtv-1394.c:91: warning: type defaults to 'int' in declaration of '__mptr'
/home/starr/Desktop/v4l-dvb/v4l/firedtv-1394.c:91: warning: initialization from incompatible pointer type
/home/starr/Desktop/v4l-dvb/v4l/firedtv-1394.c:91: error: invalid use of undefined type 'struct unit_directory'
/home/starr/Desktop/v4l-dvb/v4l/firedtv-1394.c: In function 'node_lock':
/home/starr/Desktop/v4l-dvb/v4l/firedtv-1394.c:96: error: 'quadlet_t' undeclared (first use in this function)
/home/starr/Desktop/v4l-dvb/v4l/firedtv-1394.c:96: error: (Each undeclared identifier is reported only once
/home/starr/Desktop/v4l-dvb/v4l/firedtv-1394.c:96: error: for each function it appears in.)
/home/starr/Desktop/v4l-dvb/v4l/firedtv-1394.c:96: error: 'd' undeclared (first use in this function)
/home/starr/Desktop/v4l-dvb/v4l/firedtv-1394.c:97: warning: ISO C90 forbids mixed declarations and code
/home/starr/Desktop/v4l-dvb/v4l/firedtv-1394.c:99: error: implicit declaration of function 'hpsb_node_lock'
/home/starr/Desktop/v4l-dvb/v4l/firedtv-1394.c:100: error: 'EXTCODE_COMPARE_SWAP' undeclared (first use in this function)
/home/starr/Desktop/v4l-dvb/v4l/firedtv-1394.c: In function 'node_read':
/home/starr/Desktop/v4l-dvb/v4l/firedtv-1394.c:108: error: implicit declaration of function 'hpsb_node_read'
/home/starr/Desktop/v4l-dvb/v4l/firedtv-1394.c: In function 'node_write':
/home/starr/Desktop/v4l-dvb/v4l/firedtv-1394.c:113: error: implicit declaration of function 'hpsb_node_write'
/home/starr/Desktop/v4l-dvb/v4l/firedtv-1394.c: In function 'start_iso':
/home/starr/Desktop/v4l-dvb/v4l/firedtv-1394.c:124: error: implicit declaration of function 'hpsb_iso_recv_init'
/home/starr/Desktop/v4l-dvb/v4l/firedtv-1394.c:124: error: dereferencing pointer to incomplete type
/home/starr/Desktop/v4l-dvb/v4l/firedtv-1394.c:126: error: 'HPSB_ISO_DMA_DEFAULT' undeclared (first use in this function)
/home/starr/Desktop/v4l-dvb/v4l/firedtv-1394.c:135: error: implicit declaration of function 'hpsb_iso_recv_start'
/home/starr/Desktop/v4l-dvb/v4l/firedtv-1394.c:138: error: implicit declaration of function 'hpsb_iso_shutdown'
/home/starr/Desktop/v4l-dvb/v4l/firedtv-1394.c: In function 'stop_iso':
/home/starr/Desktop/v4l-dvb/v4l/firedtv-1394.c:149: error: implicit declaration of function 'hpsb_iso_stop'
/home/starr/Desktop/v4l-dvb/v4l/firedtv-1394.c: At top level:
/home/starr/Desktop/v4l-dvb/v4l/firedtv-1394.c:164: warning: 'struct hpsb_host' declared inside parameter list
/home/starr/Desktop/v4l-dvb/v4l/firedtv-1394.c: In function 'fcp_request':
/home/starr/Desktop/v4l-dvb/v4l/firedtv-1394.c:177: error: dereferencing pointer to incomplete type
/home/starr/Desktop/v4l-dvb/v4l/firedtv-1394.c:178: error: dereferencing pointer to incomplete type
/home/starr/Desktop/v4l-dvb/v4l/firedtv-1394.c: In function 'node_probe':
/home/starr/Desktop/v4l-dvb/v4l/firedtv-1394.c:192: error: dereferencing pointer to incomplete type
/home/starr/Desktop/v4l-dvb/v4l/firedtv-1394.c:192: warning: type defaults to 'int' in declaration of '__mptr'
/home/starr/Desktop/v4l-dvb/v4l/firedtv-1394.c:192: warning: initialization from incompatible pointer type
/home/starr/Desktop/v4l-dvb/v4l/firedtv-1394.c:192: error: invalid use of undefined type 'struct unit_directory'
/home/starr/Desktop/v4l-dvb/v4l/firedtv-1394.c:197: error: dereferencing pointer to incomplete type
/home/starr/Desktop/v4l-dvb/v4l/firedtv-1394.c:198: error: dereferencing pointer to incomplete type
/home/starr/Desktop/v4l-dvb/v4l/firedtv-1394.c:199: error: implicit declaration of function 'CSR1212_TEXTUAL_DESCRIPTOR_LEAF_DATA'
/home/starr/Desktop/v4l-dvb/v4l/firedtv-1394.c:199: error: dereferencing pointer to incomplete type
/home/starr/Desktop/v4l-dvb/v4l/firedtv-1394.c: At top level:
/home/starr/Desktop/v4l-dvb/v4l/firedtv-1394.c:258: warning: 'struct unit_directory' declared inside parameter list
/home/starr/Desktop/v4l-dvb/v4l/firedtv-1394.c: In function 'node_update':
/home/starr/Desktop/v4l-dvb/v4l/firedtv-1394.c:260: error: dereferencing pointer to incomplete type
/home/starr/Desktop/v4l-dvb/v4l/firedtv-1394.c: At top level:
/home/starr/Desktop/v4l-dvb/v4l/firedtv-1394.c:268: error: variable 'fdtv_driver' has initializer but incomplete type
/home/starr/Desktop/v4l-dvb/v4l/firedtv-1394.c:269: error: unknown field 'name' specified in initializer
/home/starr/Desktop/v4l-dvb/v4l/firedtv-1394.c:269: warning: excess elements in struct initializer
/home/starr/Desktop/v4l-dvb/v4l/firedtv-1394.c:269: warning: (near initialization for 'fdtv_driver')
/home/starr/Desktop/v4l-dvb/v4l/firedtv-1394.c:270: error: unknown field 'id_table' specified in initializer
/home/starr/Desktop/v4l-dvb/v4l/firedtv-1394.c:270: warning: excess elements in struct initializer
/home/starr/Desktop/v4l-dvb/v4l/firedtv-1394.c:270: warning: (near initialization for 'fdtv_driver')
/home/starr/Desktop/v4l-dvb/v4l/firedtv-1394.c:271: error: unknown field 'update' specified in initializer
/home/starr/Desktop/v4l-dvb/v4l/firedtv-1394.c:271: warning: excess elements in struct initializer
/home/starr/Desktop/v4l-dvb/v4l/firedtv-1394.c:271: warning: (near initialization for 'fdtv_driver')
/home/starr/Desktop/v4l-dvb/v4l/firedtv-1394.c:272: error: unknown field 'driver' specified in initializer
/home/starr/Desktop/v4l-dvb/v4l/firedtv-1394.c:272: error: extra brace group at end of initializer
/home/starr/Desktop/v4l-dvb/v4l/firedtv-1394.c:272: error: (near initialization for 'fdtv_driver')
/home/starr/Desktop/v4l-dvb/v4l/firedtv-1394.c:275: warning: excess elements in struct initializer
/home/starr/Desktop/v4l-dvb/v4l/firedtv-1394.c:275: warning: (near initialization for 'fdtv_driver')
/home/starr/Desktop/v4l-dvb/v4l/firedtv-1394.c:278: error: variable 'fdtv_highlevel' has initializer but incomplete type
/home/starr/Desktop/v4l-dvb/v4l/firedtv-1394.c:279: error: unknown field 'name' specified in initializer
/home/starr/Desktop/v4l-dvb/v4l/firedtv-1394.c:279: warning: excess elements in struct initializer
/home/starr/Desktop/v4l-dvb/v4l/firedtv-1394.c:279: warning: (near initialization for 'fdtv_highlevel')
/home/starr/Desktop/v4l-dvb/v4l/firedtv-1394.c:280: error: unknown field 'fcp_request' specified in initializer
/home/starr/Desktop/v4l-dvb/v4l/firedtv-1394.c:280: warning: excess elements in struct initializer
/home/starr/Desktop/v4l-dvb/v4l/firedtv-1394.c:280: warning: (near initialization for 'fdtv_highlevel')
/home/starr/Desktop/v4l-dvb/v4l/firedtv-1394.c: In function 'fdtv_1394_init':
/home/starr/Desktop/v4l-dvb/v4l/firedtv-1394.c:287: error: implicit declaration of function 'hpsb_register_highlevel'
/home/starr/Desktop/v4l-dvb/v4l/firedtv-1394.c:288: error: implicit declaration of function 'hpsb_register_protocol'
/home/starr/Desktop/v4l-dvb/v4l/firedtv-1394.c:291: error: implicit declaration of function 'hpsb_unregister_highlevel'
/home/starr/Desktop/v4l-dvb/v4l/firedtv-1394.c: In function 'fdtv_1394_exit':
/home/starr/Desktop/v4l-dvb/v4l/firedtv-1394.c:298: error: implicit declaration of function 'hpsb_unregister_protocol'
make[3]: *** [/home/starr/Desktop/v4l-dvb/v4l/firedtv-1394.o] Error 1
make[2]: *** [_module_/home/starr/Desktop/v4l-dvb/v4l] Error 2
make[2]: Leaving directory `/usr/src/linux-headers-2.6.32-22-generic'
make[1]: *** [default] Error 2
make[1]: Leaving directory `/home/starr/Desktop/v4l-dvb/v4l'
make: *** [all] Error 2


the only thing the instructions say about it is to see if it's on the list of known bugs, but I can't really tell if it's the same as any on this list... and either way, it doesn't explain what to do to get past the problem! I really want to get this camera working.. please help!

---

### Post by Michalxo on 2010-07-06
[http://forum.ubuntuusers.de/topic/technisat-skystar-s2-will-nicht/?highlight=j](http://forum.ubuntuusers.de/topic/technisat-skystar-s2-will-nicht/?highlight=j)

Seems like it works via method in post from nycon123
>     
compiling fails because of FiredTV just  run:
```
    sudo make menuconfig 
```
before the *make* command and disable -> Multimedia Support -> DVB/ATSC Adapter -> Firedtv/Floppydtv


If needed install ncurses-devel as proposed
```

aptitude install ncurses-dev

```

---

