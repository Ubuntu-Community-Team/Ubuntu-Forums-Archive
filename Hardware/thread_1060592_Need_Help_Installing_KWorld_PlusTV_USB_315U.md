---
title: "Need Help Installing KWorld PlusTV USB 315U"
date: 2009-02-04
forum: Hardware
---

### Post by wlbragg on 2009-02-04
Hey all,

Wow, got to say I love Ubuntu (Linux). I just wish I had the same knowledge base on it as I do in Microsoft. I am totally new to Linux and Ubuntu and it's like pulling teeth for me to get around in it. I'm a total dweeb newbee.

I am slowly but surely getting my system up and running. I am currently tying to get a couple of USB devices working. The first one I am stuck on is the  KWorld PlusTV USB 315U. I found a URL that I thought might get me to a point where I can figure the rest out but have hit a wall. My system info is:

Ubuntu 8.10 - Intrepid Ibex
nVidia 6800
3200+ eMachine

The URL I was trying to follow is
[http://www.2nrds.com/digital-tv-in-linux-with-em28xx-devices](http://www.2nrds.com/digital-tv-in-linux-with-em28xx-devices)
I got stuck at trying to compile the driver

cd v4l-dvb-kernel 
make 
sudo make install

I get the following errors

```
running ./build.sh build

make[1]: Entering directory `/home/wayne/Desktop/em28driver/v4l-dvb-kernel'
rm -rf Module.symvers; 
make -C /lib/modules/`if [ -d /lib/modules/2.6.21.4-eeepc ]; then echo 2.6.21.4-eeepc; else uname -r; fi`/build SUBDIRS=`pwd` modules
make[2]: Entering directory `/usr/src/linux-headers-2.6.27-11-generic'
  CC [M]  /home/wayne/Desktop/em28driver/v4l-dvb-kernel/em2880-dvb.o
In file included from /home/wayne/Desktop/em28driver/v4l-dvb-kernel/em2880-dvb.c:37:
/home/wayne/Desktop/em28driver/v4l-dvb-kernel/em28xx.h:32:20: error: dmxdev.h: No such file or directory
/home/wayne/Desktop/em28driver/v4l-dvb-kernel/em28xx.h:33:23: error: dvb_demux.h: No such file or directory
/home/wayne/Desktop/em28driver/v4l-dvb-kernel/em28xx.h:34:21: error: dvb_net.h: No such file or directory
/home/wayne/Desktop/em28driver/v4l-dvb-kernel/em28xx.h:35:26: error: dvb_frontend.h: No such file or directory
In file included from /home/wayne/Desktop/em28driver/v4l-dvb-kernel/em2880-dvb.c:37:
/home/wayne/Desktop/em28driver/v4l-dvb-kernel/em28xx.h:560: error: field &#8216;demux&#8217; has incomplete type
/home/wayne/Desktop/em28driver/v4l-dvb-kernel/em28xx.h:568: error: field &#8216;adapter&#8217; has incomplete type
/home/wayne/Desktop/em28driver/v4l-dvb-kernel/em28xx.h:571: error: field &#8216;dmxdev&#8217; has incomplete type
/home/wayne/Desktop/em28driver/v4l-dvb-kernel/em28xx.h:573: error: field &#8216;dvbnet&#8217; has incomplete type
In file included from /home/wayne/Desktop/em28driver/v4l-dvb-kernel/em2880-dvb.c:44:
/home/wayne/Desktop/em28driver/v4l-dvb-kernel/mt352/mt352.h: In function &#8216;mt352_write&#8217;:
/home/wayne/Desktop/em28driver/v4l-dvb-kernel/mt352/mt352.h:68: error: dereferencing pointer to incomplete type
/home/wayne/Desktop/em28driver/v4l-dvb-kernel/mt352/mt352.h:69: error: dereferencing pointer to incomplete type
In file included from /home/wayne/Desktop/em28driver/v4l-dvb-kernel/em2880-dvb.c:46:
/home/wayne/Desktop/em28driver/v4l-dvb-kernel/drx3973d/drx3973d_demod.h: At top level:
/home/wayne/Desktop/em28driver/v4l-dvb-kernel/drx3973d/drx3973d_demod.h:9: error: field &#8216;frontend&#8217; has incomplete type
/home/wayne/Desktop/em28driver/v4l-dvb-kernel/em2880-dvb.c:52:22: error: lgdt330x.h: No such file or directory
/home/wayne/Desktop/em28driver/v4l-dvb-kernel/em2880-dvb.c:245: warning: &#8216;struct dvb_frontend_tune_settings&#8217; declared inside parameter list
/home/wayne/Desktop/em28driver/v4l-dvb-kernel/em2880-dvb.c:245: warning: its scope is only this definition or declaration, which is probably not what you want
/home/wayne/Desktop/em28driver/v4l-dvb-kernel/em2880-dvb.c: In function &#8216;em2880_fe_get_tune_settings&#8217;:
/home/wayne/Desktop/em28driver/v4l-dvb-kernel/em2880-dvb.c:246: error: dereferencing pointer to incomplete type
/home/wayne/Desktop/em28driver/v4l-dvb-kernel/em2880-dvb.c:247: error: dereferencing pointer to incomplete type
/home/wayne/Desktop/em28driver/v4l-dvb-kernel/em2880-dvb.c:248: error: dereferencing pointer to incomplete type
/home/wayne/Desktop/em28driver/v4l-dvb-kernel/em2880-dvb.c: At top level:
/home/wayne/Desktop/em28driver/v4l-dvb-kernel/em2880-dvb.c:276: error: variable &#8216;em2880_fe_template_ops&#8217; has initializer but incomplete type
/home/wayne/Desktop/em28driver/v4l-dvb-kernel/em2880-dvb.c:277: error: unknown field &#8216;info&#8217; specified in initializer
/home/wayne/Desktop/em28driver/v4l-dvb-kernel/em2880-dvb.c:277: error: extra brace group at end of initializer
/home/wayne/Desktop/em28driver/v4l-dvb-kernel/em2880-dvb.c:277: error: (near initialization for &#8216;em2880_fe_template_ops&#8217;)
/home/wayne/Desktop/em28driver/v4l-dvb-kernel/em2880-dvb.c:287: warning: excess elements in struct initializer
/home/wayne/Desktop/em28driver/v4l-dvb-kernel/em2880-dvb.c:287: warning: (near initialization for &#8216;em2880_fe_template_ops&#8217;)
/home/wayne/Desktop/em28driver/v4l-dvb-kernel/em2880-dvb.c:288: error: unknown field &#8216;init&#8217; specified in initializer
/home/wayne/Desktop/em28driver/v4l-dvb-kernel/em2880-dvb.c:288: warning: excess elements in struct initializer
/home/wayne/Desktop/em28driver/v4l-dvb-kernel/em2880-dvb.c:288: warning: (near initialization for &#8216;em2880_fe_template_ops&#8217;)
/home/wayne/Desktop/em28driver/v4l-dvb-kernel/em2880-dvb.c:289: error: unknown field &#8216;release&#8217; specified in initializer
/home/wayne/Desktop/em28driver/v4l-dvb-kernel/em2880-dvb.c:289: warning: excess elements in struct initializer
/home/wayne/Desktop/em28driver/v4l-dvb-kernel/em2880-dvb.c:289: warning: (near initialization for &#8216;em2880_fe_template_ops&#8217;)
/home/wayne/Desktop/em28driver/v4l-dvb-kernel/em2880-dvb.c:291: error: unknown field &#8216;sleep&#8217; specified in initializer
/home/wayne/Desktop/em28driver/v4l-dvb-kernel/em2880-dvb.c:291: warning: excess elements in struct initializer
/home/wayne/Desktop/em28driver/v4l-dvb-kernel/em2880-dvb.c:291: warning: (near initialization for &#8216;em2880_fe_template_ops&#8217;)
/home/wayne/Desktop/em28driver/v4l-dvb-kernel/em2880-dvb.c:292: error: unknown field &#8216;set_frontend&#8217; specified in initializer
/home/wayne/Desktop/em28driver/v4l-dvb-kernel/em2880-dvb.c:292: warning: excess elements in struct initializer
/home/wayne/Desktop/em28driver/v4l-dvb-kernel/em2880-dvb.c:292: warning: (near initialization for &#8216;em2880_fe_template_ops&#8217;)
/home/wayne/Desktop/em28driver/v4l-dvb-kernel/em2880-dvb.c:293: error: unknown field &#8216;get_frontend&#8217; specified in initializer
/home/wayne/Desktop/em28driver/v4l-dvb-kernel/em2880-dvb.c:293: warning: excess elements in struct initializer
/home/wayne/Desktop/em28driver/v4l-dvb-kernel/em2880-dvb.c:293: warning: (near initialization for &#8216;em2880_fe_template_ops&#8217;)
/home/wayne/Desktop/em28driver/v4l-dvb-kernel/em2880-dvb.c:294: error: unknown field &#8216;get_tune_settings&#8217; specified in initializer
/home/wayne/Desktop/em28driver/v4l-dvb-kernel/em2880-dvb.c:294: warning: excess elements in struct initializer
/home/wayne/Desktop/em28driver/v4l-dvb-kernel/em2880-dvb.c:294: warning: (near initialization for &#8216;em2880_fe_template_ops&#8217;)
/home/wayne/Desktop/em28driver/v4l-dvb-kernel/em2880-dvb.c:295: error: unknown field &#8216;read_status&#8217; specified in initializer
/home/wayne/Desktop/em28driver/v4l-dvb-kernel/em2880-dvb.c:295: warning: excess elements in struct initializer
/home/wayne/Desktop/em28driver/v4l-dvb-kernel/em2880-dvb.c:295: warning: (near initialization for &#8216;em2880_fe_template_ops&#8217;)
/home/wayne/Desktop/em28driver/v4l-dvb-kernel/em2880-dvb.c:296: error: unknown field &#8216;read_ber&#8217; specified in initializer
/home/wayne/Desktop/em28driver/v4l-dvb-kernel/em2880-dvb.c:296: warning: excess elements in struct initializer
/home/wayne/Desktop/em28driver/v4l-dvb-kernel/em2880-dvb.c:296: warning: (near initialization for &#8216;em2880_fe_template_ops&#8217;)
/home/wayne/Desktop/em28driver/v4l-dvb-kernel/em2880-dvb.c:297: error: unknown field &#8216;read_signal_strength&#8217; specified in initializer
/home/wayne/Desktop/em28driver/v4l-dvb-kernel/em2880-dvb.c:297: warning: excess elements in struct initializer
/home/wayne/Desktop/em28driver/v4l-dvb-kernel/em2880-dvb.c:297: warning: (near initialization for &#8216;em2880_fe_template_ops&#8217;)
/home/wayne/Desktop/em28driver/v4l-dvb-kernel/em2880-dvb.c:298: error: unknown field &#8216;read_snr&#8217; specified in initializer
/home/wayne/Desktop/em28driver/v4l-dvb-kernel/em2880-dvb.c:298: warning: excess elements in struct initializer
/home/wayne/Desktop/em28driver/v4l-dvb-kernel/em2880-dvb.c:298: warning: (near initialization for &#8216;em2880_fe_template_ops&#8217;)
/home/wayne/Desktop/em28driver/v4l-dvb-kernel/em2880-dvb.c:299: error: unknown field &#8216;read_ucblocks&#8217; specified in initializer
/home/wayne/Desktop/em28driver/v4l-dvb-kernel/em2880-dvb.c:300: warning: excess elements in struct initializer
/home/wayne/Desktop/em28driver/v4l-dvb-kernel/em2880-dvb.c:300: warning: (near initialization for &#8216;em2880_fe_template_ops&#8217;)
/home/wayne/Desktop/em28driver/v4l-dvb-kernel/em2880-dvb.c: In function &#8216;em2880_complete_irq&#8217;:
/home/wayne/Desktop/em28driver/v4l-dvb-kernel/em2880-dvb.c:339: error: implicit declaration of function &#8216;dvb_dmx_swfilter&#8217;
/home/wayne/Desktop/em28driver/v4l-dvb-kernel/em2880-dvb.c: At top level:
/home/wayne/Desktop/em28driver/v4l-dvb-kernel/em2880-dvb.c:448: warning: &#8216;struct dvb_demux_feed&#8217; declared inside parameter list
/home/wayne/Desktop/em28driver/v4l-dvb-kernel/em2880-dvb.c: In function &#8216;em2880_start_feed&#8217;:
/home/wayne/Desktop/em28driver/v4l-dvb-kernel/em2880-dvb.c:450: error: dereferencing pointer to incomplete type
/home/wayne/Desktop/em28driver/v4l-dvb-kernel/em2880-dvb.c:451: error: dereferencing pointer to incomplete type
/home/wayne/Desktop/em28driver/v4l-dvb-kernel/em2880-dvb.c: At top level:
/home/wayne/Desktop/em28driver/v4l-dvb-kernel/em2880-dvb.c:465: warning: &#8216;struct dvb_demux_feed&#8217; declared inside parameter list
/home/wayne/Desktop/em28driver/v4l-dvb-kernel/em2880-dvb.c: In function &#8216;em2880_stop_feed&#8217;:
/home/wayne/Desktop/em28driver/v4l-dvb-kernel/em2880-dvb.c:467: error: dereferencing pointer to incomplete type
/home/wayne/Desktop/em28driver/v4l-dvb-kernel/em2880-dvb.c:468: error: dereferencing pointer to incomplete type
/home/wayne/Desktop/em28driver/v4l-dvb-kernel/em2880-dvb.c: In function &#8216;em28xx_ts_bus_ctrl&#8217;:
/home/wayne/Desktop/em28driver/v4l-dvb-kernel/em2880-dvb.c:494: error: dereferencing pointer to incomplete type
/home/wayne/Desktop/em28driver/v4l-dvb-kernel/em2880-dvb.c: In function &#8216;mt352_pinnacle_init&#8217;:
/home/wayne/Desktop/em28driver/v4l-dvb-kernel/em2880-dvb.c:545: error: dereferencing pointer to incomplete type
/home/wayne/Desktop/em28driver/v4l-dvb-kernel/em2880-dvb.c: At top level:
/home/wayne/Desktop/em28driver/v4l-dvb-kernel/em2880-dvb.c:573: error: variable &#8216;em2880_lgdt3303_dev&#8217; has initializer but incomplete type
/home/wayne/Desktop/em28driver/v4l-dvb-kernel/em2880-dvb.c:574: error: unknown field &#8216;demod_address&#8217; specified in initializer
/home/wayne/Desktop/em28driver/v4l-dvb-kernel/em2880-dvb.c:574: warning: excess elements in struct initializer
/home/wayne/Desktop/em28driver/v4l-dvb-kernel/em2880-dvb.c:574: warning: (near initialization for &#8216;em2880_lgdt3303_dev&#8217;)
/home/wayne/Desktop/em28driver/v4l-dvb-kernel/em2880-dvb.c:575: error: unknown field &#8216;demod_chip&#8217; specified in initializer
/home/wayne/Desktop/em28driver/v4l-dvb-kernel/em2880-dvb.c:575: error: &#8216;LGDT3303&#8217; undeclared here (not in a function)
/home/wayne/Desktop/em28driver/v4l-dvb-kernel/em2880-dvb.c:576: warning: excess elements in struct initializer
/home/wayne/Desktop/em28driver/v4l-dvb-kernel/em2880-dvb.c:576: warning: (near initialization for &#8216;em2880_lgdt3303_dev&#8217;)
/home/wayne/Desktop/em28driver/v4l-dvb-kernel/em2880-dvb.c: In function &#8216;kworld355u_i2c_gate_ctrl&#8217;:
/home/wayne/Desktop/em28driver/v4l-dvb-kernel/em2880-dvb.c:590: error: field &#8216;frontend&#8217; has incomplete type
/home/wayne/Desktop/em28driver/v4l-dvb-kernel/em2880-dvb.c:596: error: dereferencing pointer to incomplete type
/home/wayne/Desktop/em28driver/v4l-dvb-kernel/em2880-dvb.c: In function &#8216;em28xx_set_params&#8217;:
/home/wayne/Desktop/em28driver/v4l-dvb-kernel/em2880-dvb.c:610: error: dereferencing pointer to incomplete type
/home/wayne/Desktop/em28driver/v4l-dvb-kernel/em2880-dvb.c:619: error: dereferencing pointer to incomplete type
/home/wayne/Desktop/em28driver/v4l-dvb-kernel/em2880-dvb.c: In function &#8216;em28xx_get_frequency&#8217;:
/home/wayne/Desktop/em28driver/v4l-dvb-kernel/em2880-dvb.c:737: error: dereferencing pointer to incomplete type
/home/wayne/Desktop/em28driver/v4l-dvb-kernel/em2880-dvb.c: In function &#8216;em28xx_get_bandwidth&#8217;:
/home/wayne/Desktop/em28driver/v4l-dvb-kernel/em2880-dvb.c:744: error: dereferencing pointer to incomplete type
/home/wayne/Desktop/em28driver/v4l-dvb-kernel/em2880-dvb.c: In function &#8216;em28xx_dvb_init&#8217;:
/home/wayne/Desktop/em28driver/v4l-dvb-kernel/em2880-dvb.c:752: error: dereferencing pointer to incomplete type
/home/wayne/Desktop/em28driver/v4l-dvb-kernel/em2880-dvb.c: In function &#8216;em28xx_s921_init&#8217;:
/home/wayne/Desktop/em28driver/v4l-dvb-kernel/em2880-dvb.c:807: error: dereferencing pointer to incomplete type
/home/wayne/Desktop/em28driver/v4l-dvb-kernel/em2880-dvb.c: In function &#8216;em28xx_zl10353_init&#8217;:
/home/wayne/Desktop/em28driver/v4l-dvb-kernel/em2880-dvb.c:824: error: dereferencing pointer to incomplete type
/home/wayne/Desktop/em28driver/v4l-dvb-kernel/em2880-dvb.c: In function &#8216;em28xx_zl10353_sleep&#8217;:
/home/wayne/Desktop/em28driver/v4l-dvb-kernel/em2880-dvb.c:873: error: dereferencing pointer to incomplete type
/home/wayne/Desktop/em28driver/v4l-dvb-kernel/em2880-dvb.c: In function &#8216;em28xx_dvb_sleep&#8217;:
/home/wayne/Desktop/em28driver/v4l-dvb-kernel/em2880-dvb.c:889: error: dereferencing pointer to incomplete type
/home/wayne/Desktop/em28driver/v4l-dvb-kernel/em2880-dvb.c: In function &#8216;em2880_dvb_init&#8217;:
/home/wayne/Desktop/em28driver/v4l-dvb-kernel/em2880-dvb.c:960: error: implicit declaration of function &#8216;dvb_attach&#8217;
/home/wayne/Desktop/em28driver/v4l-dvb-kernel/em2880-dvb.c:964: warning: assignment makes pointer from integer without a cast
/home/wayne/Desktop/em28driver/v4l-dvb-kernel/em2880-dvb.c:983: warning: assignment makes pointer from integer without a cast
/home/wayne/Desktop/em28driver/v4l-dvb-kernel/em2880-dvb.c:986: warning: assignment makes pointer from integer without a cast
/home/wayne/Desktop/em28driver/v4l-dvb-kernel/em2880-dvb.c:991: warning: assignment makes pointer from integer without a cast
/home/wayne/Desktop/em28driver/v4l-dvb-kernel/em2880-dvb.c:997: error: &#8216;lgdt330x_attach&#8217; undeclared (first use in this function)
/home/wayne/Desktop/em28driver/v4l-dvb-kernel/em2880-dvb.c:997: error: (Each undeclared identifier is reported only once
/home/wayne/Desktop/em28driver/v4l-dvb-kernel/em2880-dvb.c:997: error: for each function it appears in.)
/home/wayne/Desktop/em28driver/v4l-dvb-kernel/em2880-dvb.c:998: warning: assignment makes pointer from integer without a cast
/home/wayne/Desktop/em28driver/v4l-dvb-kernel/em2880-dvb.c:1007: warning: assignment makes pointer from integer without a cast
/home/wayne/Desktop/em28driver/v4l-dvb-kernel/em2880-dvb.c:1012: warning: assignment makes pointer from integer without a cast
/home/wayne/Desktop/em28driver/v4l-dvb-kernel/em2880-dvb.c:1018: warning: assignment makes pointer from integer without a cast
/home/wayne/Desktop/em28driver/v4l-dvb-kernel/em2880-dvb.c:1021: error: dereferencing pointer to incomplete type
/home/wayne/Desktop/em28driver/v4l-dvb-kernel/em2880-dvb.c:1022: error: dereferencing pointer to incomplete type
/home/wayne/Desktop/em28driver/v4l-dvb-kernel/em2880-dvb.c:1023: error: dereferencing pointer to incomplete type
/home/wayne/Desktop/em28driver/v4l-dvb-kernel/em2880-dvb.c:1035: error: invalid application of &#8216;sizeof&#8217; to incomplete type &#8216;struct dvb_frontend&#8217; 
/home/wayne/Desktop/em28driver/v4l-dvb-kernel/em2880-dvb.c:1036: error: invalid application of &#8216;sizeof&#8217; to incomplete type &#8216;struct dvb_frontend_ops&#8217; 
/home/wayne/Desktop/em28driver/v4l-dvb-kernel/em2880-dvb.c:1036: error: dereferencing pointer to incomplete type
/home/wayne/Desktop/em28driver/v4l-dvb-kernel/em2880-dvb.c:1036: error: invalid application of &#8216;sizeof&#8217; to incomplete type &#8216;struct dvb_frontend_ops&#8217; 
/home/wayne/Desktop/em28driver/v4l-dvb-kernel/em2880-dvb.c:1036: error: dereferencing pointer to incomplete type
/home/wayne/Desktop/em28driver/v4l-dvb-kernel/em2880-dvb.c:1036: error: invalid application of &#8216;sizeof&#8217; to incomplete type &#8216;struct dvb_frontend_ops&#8217; 
/home/wayne/Desktop/em28driver/v4l-dvb-kernel/em2880-dvb.c:1050: error: dereferencing pointer to incomplete type
/home/wayne/Desktop/em28driver/v4l-dvb-kernel/em2880-dvb.c:1051: error: dereferencing pointer to incomplete type
/home/wayne/Desktop/em28driver/v4l-dvb-kernel/em2880-dvb.c:1053: error: dereferencing pointer to incomplete type
/home/wayne/Desktop/em28driver/v4l-dvb-kernel/em2880-dvb.c:1055: error: dereferencing pointer to incomplete type
/home/wayne/Desktop/em28driver/v4l-dvb-kernel/em2880-dvb.c:1059: error: dereferencing pointer to incomplete type
/home/wayne/Desktop/em28driver/v4l-dvb-kernel/em2880-dvb.c:1061: error: dereferencing pointer to incomplete type
/home/wayne/Desktop/em28driver/v4l-dvb-kernel/em2880-dvb.c:1070: error: dereferencing pointer to incomplete type
/home/wayne/Desktop/em28driver/v4l-dvb-kernel/em2880-dvb.c:1084: error: dereferencing pointer to incomplete type
/home/wayne/Desktop/em28driver/v4l-dvb-kernel/em2880-dvb.c:1086: error: dereferencing pointer to incomplete type
/home/wayne/Desktop/em28driver/v4l-dvb-kernel/em2880-dvb.c:1087: error: dereferencing pointer to incomplete type
/home/wayne/Desktop/em28driver/v4l-dvb-kernel/em2880-dvb.c:1105: error: dereferencing pointer to incomplete type
/home/wayne/Desktop/em28driver/v4l-dvb-kernel/em2880-dvb.c:1108: error: implicit declaration of function &#8216;dvb_register_adapter&#8217;
/home/wayne/Desktop/em28driver/v4l-dvb-kernel/em2880-dvb.c:1126: error: implicit declaration of function &#8216;dvb_register_frontend&#8217;
/home/wayne/Desktop/em28driver/v4l-dvb-kernel/em2880-dvb.c:1133: error: &#8216;DMX_TS_FILTERING&#8217; undeclared (first use in this function)
/home/wayne/Desktop/em28driver/v4l-dvb-kernel/em2880-dvb.c:1134: error: &#8216;DMX_SECTION_FILTERING&#8217; undeclared (first use in this function)
/home/wayne/Desktop/em28driver/v4l-dvb-kernel/em2880-dvb.c:1135: error: &#8216;DMX_MEMORY_BASED_FILTERING&#8217; undeclared (first use in this function)
/home/wayne/Desktop/em28driver/v4l-dvb-kernel/em2880-dvb.c:1137: error: implicit declaration of function &#8216;dvb_dmx_init&#8217;
/home/wayne/Desktop/em28driver/v4l-dvb-kernel/em2880-dvb.c:1148: error: implicit declaration of function &#8216;dvb_dmxdev_init&#8217;
/home/wayne/Desktop/em28driver/v4l-dvb-kernel/em2880-dvb.c:1152: error: implicit declaration of function &#8216;dvb_dmxdev_release&#8217;
/home/wayne/Desktop/em28driver/v4l-dvb-kernel/em2880-dvb.c:1163: error: implicit declaration of function &#8216;dvb_net_init&#8217;
/home/wayne/Desktop/em28driver/v4l-dvb-kernel/em2880-dvb.c:1163: error: dereferencing pointer to incomplete type
/home/wayne/Desktop/em28driver/v4l-dvb-kernel/em2880-dvb.c: In function &#8216;em2880_dvb_fini&#8217;:
/home/wayne/Desktop/em28driver/v4l-dvb-kernel/em2880-dvb.c:1183: error: implicit declaration of function &#8216;dvb_net_release&#8217;
/home/wayne/Desktop/em28driver/v4l-dvb-kernel/em2880-dvb.c:1184: error: implicit declaration of function &#8216;dvb_unregister_frontend&#8217;
/home/wayne/Desktop/em28driver/v4l-dvb-kernel/em2880-dvb.c:1191: error: implicit declaration of function &#8216;dvb_frontend_detach&#8217;
/home/wayne/Desktop/em28driver/v4l-dvb-kernel/em2880-dvb.c:1196: error: implicit declaration of function &#8216;dvb_dmx_release&#8217;
/home/wayne/Desktop/em28driver/v4l-dvb-kernel/em2880-dvb.c:1198: error: implicit declaration of function &#8216;dvb_unregister_adapter&#8217;
make[3]: *** [/home/wayne/Desktop/em28driver/v4l-dvb-kernel/em2880-dvb.o] Error 1
make[2]: *** [_module_/home/wayne/Desktop/em28driver/v4l-dvb-kernel] Error 2
make[2]: Leaving directory `/usr/src/linux-headers-2.6.27-11-generic'
make[1]: *** [default] Error 2
make[1]: Leaving directory `/home/wayne/Desktop/em28driver/v4l-dvb-kernel'

```

FYI, in the firmware step I used firmware 2 for the KWorld 110
I don't know if I should even continue down this path or need to take a whole new approach? 
I also found this
[http://linuxtv.org/wiki/index.php/KWorld_ATSC_315U](http://linuxtv.org/wiki/index.php/KWorld_ATSC_315U)
which is the technical on my card.
Any help, suggestions or reference direction would be greatly appreciated.

---

### Post by fmeng on 2009-06-06
Check out the linuxtv wiki for the 315U again.   Support (digital only) was added in one of the experimental trees.  You will need to follow instructions here: [http://www.linuxtv.org/wiki/index.php/How_to_Obtain,_Build_and_Install_V4L-DVB_Device_Drivers](http://www.linuxtv.org/wiki/index.php/How_to_Obtain,_Build_and_Install_V4L-DVB_Device_Drivers) for information on how to build and install the driver.

---

