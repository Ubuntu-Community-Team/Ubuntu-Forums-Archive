---
title: "Is there any possible chance to get this to work? (A828)"
date: 2007-01-11
forum: Hardware &amp; Laptops
---

### Post by Enverex on 2007-01-11
I bought the AverTV Hybrid+FM USB device a week or so ago because it was the only TV device I could find that had everything I wanted and claimed "LINUX COMPATABLE!" but much to my dismay when I got it, the drivers are a joke.

The driver doesn't work for Ubuntu Edgy 6.10 and doesn't manually compile because it tries to use functions not available in the 2.6.17 kernel.

Basically it comes with an installer that lets you select a few different distros (with specific versions) and unless you have one that matches those then it doesn't work (that'll fail). If you try and copy the .ko module to the kernels modules folder and load it manually, for instance using the Dapper one, and try and load it, you just get this: "a828: version magic '2.6.15-23-686 SMP preempt 686 gcc-4.0' should be '2.6.17-10-generic SMP mod_unload 586 REGPARM gcc-4.1'".

So I thought, well, I could try compiling it, that should work.... well after a few hours of trying to figure out why it was looking in weird places for kernel source (/lib/modules/whatever/build - since when is it ever in there?) I managed to get it to start compiling by editing the Makefile to look in the right place, but it still doesn't work because it looks like it uses functions that have changed, moved or something else. This is the compile log.

```
make -C /usr/src/linux-headers-2.6.17-10-generic/ O=./ SUBDIRS=`pwd` 
make[1]: Entering directory `/usr/src/linux-headers-2.6.17-10-generic'
  LD      /home/enverex/src/a828-install/built-in.o
  CC [M]  /home/enverex/src/a828-install/aver/osdep.o
  CC [M]  /home/enverex/src/a828-install/a828-core.o
  CC [M]  /home/enverex/src/a828-install/aver/osdep_usb.o
  CC [M]  /home/enverex/src/a828-install/aver/osdep_dvb.o
/home/enverex/src/a828-install/aver/osdep_dvb.c:88:20: error: dvbdev.h: No such file or directory
/home/enverex/src/a828-install/aver/osdep_dvb.c:89:19: error: demux.h: No such file or directory
/home/enverex/src/a828-install/aver/osdep_dvb.c:90:23: error: dvb_demux.h: No such file or directory
/home/enverex/src/a828-install/aver/osdep_dvb.c:91:20: error: dmxdev.h: No such file or directory
/home/enverex/src/a828-install/aver/osdep_dvb.c:92:24: error: dvb_filter.h: No such file or directory
/home/enverex/src/a828-install/aver/osdep_dvb.c:93:21: error: dvb_net.h: No such file or directory
/home/enverex/src/a828-install/aver/osdep_dvb.c:94:28: error: dvb_ringbuffer.h: No such file or directory
/home/enverex/src/a828-install/aver/osdep_dvb.c:95:26: error: dvb_frontend.h: No such file or directory
In file included from /home/enverex/src/a828-install/aver/osdep_dvb.c:101:
/home/enverex/src/a828-install/aver/osdep_dvb.h:98: warning: ‘struct dvb_frontend_info’ declared inside parameter list
/home/enverex/src/a828-install/aver/osdep_dvb.h:98: warning: its scope is only this definition or declaration, which is probably not what you want
/home/enverex/src/a828-install/aver/osdep_dvb.h:110: error: expected declaration specifiers or ‘...’ before ‘fe_status_t’
/home/enverex/src/a828-install/aver/osdep_dvb.h:114: warning: ‘struct dvb_frontend_parameters’ declared inside parameter list
/home/enverex/src/a828-install/aver/osdep_dvb.h:115: warning: ‘struct dvb_frontend_parameters’ declared inside parameter list
/home/enverex/src/a828-install/aver/osdep_dvb.h:122: warning: ‘struct dvb_diseqc_master_cmd’ declared inside parameter list
/home/enverex/src/a828-install/aver/osdep_dvb.h:123: warning: ‘struct dvb_diseqc_slave_reply’ declared inside parameter list
/home/enverex/src/a828-install/aver/osdep_dvb.h:124: error: expected declaration specifiers or ‘...’ before ‘fe_sec_mini_cmd_t’
/home/enverex/src/a828-install/aver/osdep_dvb.h:125: error: expected declaration specifiers or ‘...’ before ‘fe_sec_tone_mode_t’
/home/enverex/src/a828-install/aver/osdep_dvb.h:126: error: expected declaration specifiers or ‘...’ before ‘fe_sec_voltage_t’
/home/enverex/src/a828-install/aver/osdep_dvb.c:123: error: field ‘fe’ has incomplete type
/home/enverex/src/a828-install/aver/osdep_dvb.c:124: error: field ‘dmxdev_sw’ has incomplete type
/home/enverex/src/a828-install/aver/osdep_dvb.c:125: error: field ‘demux_sw’ has incomplete type
/home/enverex/src/a828-install/aver/osdep_dvb.c:127: error: field ‘hw_frontend’ has incomplete type
/home/enverex/src/a828-install/aver/osdep_dvb.c:128: error: field ‘mem_frontend’ has incomplete type
/home/enverex/src/a828-install/aver/osdep_dvb.c:131: error: field ‘dvbfe_ops’ has incomplete type
/home/enverex/src/a828-install/aver/osdep_dvb.c:149: warning: ‘struct dvb_demux_feed’ declared inside parameter list
/home/enverex/src/a828-install/aver/osdep_dvb.c:150: warning: ‘struct dvb_demux_feed’ declared inside parameter list
/home/enverex/src/a828-install/aver/osdep_dvb.c:152: warning: ‘struct dvb_frontend_parameters’ declared inside parameter list
/home/enverex/src/a828-install/aver/osdep_dvb.c:154: warning: ‘struct dvb_frontend_parameters’ declared inside parameter list
/home/enverex/src/a828-install/aver/osdep_dvb.c:155: error: expected declaration specifiers or ‘...’ before ‘fe_status_t’
/home/enverex/src/a828-install/aver/osdep_dvb.c:161: warning: ‘struct dvb_frontend_tune_settings’ declared inside parameter list
/home/enverex/src/a828-install/aver/osdep_dvb.c:168: warning: ‘struct dvb_diseqc_master_cmd’ declared inside parameter list
/home/enverex/src/a828-install/aver/osdep_dvb.c:169: warning: ‘struct dvb_diseqc_slave_reply’ declared inside parameter list
/home/enverex/src/a828-install/aver/osdep_dvb.c:170: error: expected declaration specifiers or ‘...’ before ‘fe_sec_mini_cmd_t’
/home/enverex/src/a828-install/aver/osdep_dvb.c:171: error: expected declaration specifiers or ‘...’ before ‘fe_sec_tone_mode_t’
/home/enverex/src/a828-install/aver/osdep_dvb.c:172: error: expected declaration specifiers or ‘...’ before ‘fe_sec_voltage_t’
/home/enverex/src/a828-install/aver/osdep_dvb.c:220: warning: ‘struct dvb_frontend_info’ declared inside parameter list
/home/enverex/src/a828-install/aver/osdep_dvb.c:221: error: conflicting types for ‘SysDVBRegisterFrontend’
/home/enverex/src/a828-install/aver/osdep_dvb.h:98: error: previous declaration of ‘SysDVBRegisterFrontend’ was here
/home/enverex/src/a828-install/aver/osdep_dvb.c: In function ‘SysDVBRegisterFrontend’:
/home/enverex/src/a828-install/aver/osdep_dvb.c:259: error: dereferencing pointer to incomplete type
/home/enverex/src/a828-install/aver/osdep_dvb.c:274: error: ‘FE_QPSK’ undeclared (first use in this function)
/home/enverex/src/a828-install/aver/osdep_dvb.c:274: error: (Each undeclared identifier is reported only once
/home/enverex/src/a828-install/aver/osdep_dvb.c:274: error: for each function it appears in.)
/home/enverex/src/a828-install/aver/osdep_dvb.c:274: error: dereferencing pointer to incomplete type
/home/enverex/src/a828-install/aver/osdep_dvb.c:306: warning: implicit declaration of function ‘dvb_register_frontend’
/home/enverex/src/a828-install/aver/osdep_dvb.c: In function ‘SysDVBRegisterAdapter’:
/home/enverex/src/a828-install/aver/osdep_dvb.c:346: error: invalid application of ‘sizeof’ to incomplete type ‘struct dvb_adapter’ 
/home/enverex/src/a828-install/aver/osdep_dvb.c:359: warning: implicit declaration of function ‘dvb_register_adapter’
/home/enverex/src/a828-install/aver/osdep_dvb.c:359: error: ‘THIS_MODULE’ undeclared (first use in this function)
/home/enverex/src/a828-install/aver/osdep_dvb.c:373: error: dereferencing pointer to incomplete type
/home/enverex/src/a828-install/aver/osdep_dvb.c:390: error: invalid application of ‘sizeof’ to incomplete type ‘struct dvb_demux’ 
/home/enverex/src/a828-install/aver/osdep_dvb.c:390: error: invalid application of ‘sizeof’ to incomplete type ‘struct dvb_demux’ 
/home/enverex/src/a828-install/aver/osdep_dvb.c:390: error: invalid application of ‘sizeof’ to incomplete type ‘struct dvb_demux’ 
/home/enverex/src/a828-install/aver/osdep_dvb.c:390: error: invalid application of ‘sizeof’ to incomplete type ‘struct dvb_demux’ 
/home/enverex/src/a828-install/aver/osdep_dvb.c:390: error: invalid application of ‘sizeof’ to incomplete type ‘struct dvb_demux’ 
/home/enverex/src/a828-install/aver/osdep_dvb.c:390: error: invalid application of ‘sizeof’ to incomplete type ‘struct dvb_demux’ 
/home/enverex/src/a828-install/aver/osdep_dvb.c:398: error: ‘DMX_TS_FILTERING’ undeclared (first use in this function)
/home/enverex/src/a828-install/aver/osdep_dvb.c:399: error: ‘DMX_SECTION_FILTERING’ undeclared (first use in this function)
/home/enverex/src/a828-install/aver/osdep_dvb.c:400: error: ‘DMX_MEMORY_BASED_FILTERING’ undeclared (first use in this function)
/home/enverex/src/a828-install/aver/osdep_dvb.c:403: warning: implicit declaration of function ‘dvb_dmx_init’
/home/enverex/src/a828-install/aver/osdep_dvb.c:416: warning: implicit declaration of function ‘dvb_dmxdev_init’
/home/enverex/src/a828-install/aver/osdep_dvb.c:425: error: ‘DMX_FRONTEND_0’ undeclared (first use in this function)
/home/enverex/src/a828-install/aver/osdep_dvb.c:436: error: ‘DMX_MEMORY_FE’ undeclared (first use in this function)
/home/enverex/src/a828-install/aver/osdep_dvb.c:464: warning: implicit declaration of function ‘dvb_dmxdev_release’
/home/enverex/src/a828-install/aver/osdep_dvb.c:466: warning: implicit declaration of function ‘dvb_dmx_release’
/home/enverex/src/a828-install/aver/osdep_dvb.c:472: warning: implicit declaration of function ‘dvb_unregister_adapter’
/home/enverex/src/a828-install/aver/osdep_dvb.c: In function ‘SysDVBUnRegisterFrontend’:
/home/enverex/src/a828-install/aver/osdep_dvb.c:489: warning: implicit declaration of function ‘dvb_unregister_frontend’
/home/enverex/src/a828-install/aver/osdep_dvb.c: In function ‘SysDVBFeedTSPackets’:
/home/enverex/src/a828-install/aver/osdep_dvb.c:528: warning: implicit declaration of function ‘dvb_dmx_swfilter_packets’
/home/enverex/src/a828-install/aver/osdep_dvb.c: At top level:
/home/enverex/src/a828-install/aver/osdep_dvb.c:545: warning: ‘struct dvb_demux_feed’ declared inside parameter list
/home/enverex/src/a828-install/aver/osdep_dvb.c:546: error: conflicting types for ‘demux_sw_start_feed’
/home/enverex/src/a828-install/aver/osdep_dvb.c:149: error: previous declaration of ‘demux_sw_start_feed’ was here
/home/enverex/src/a828-install/aver/osdep_dvb.c: In function ‘demux_sw_start_feed’:
/home/enverex/src/a828-install/aver/osdep_dvb.c:547: error: dereferencing pointer to incomplete type
/home/enverex/src/a828-install/aver/osdep_dvb.c:548: error: dereferencing pointer to incomplete type
/home/enverex/src/a828-install/aver/osdep_dvb.c:555: error: dereferencing pointer to incomplete type
/home/enverex/src/a828-install/aver/osdep_dvb.c: At top level:
/home/enverex/src/a828-install/aver/osdep_dvb.c:579: warning: ‘struct dvb_demux_feed’ declared inside parameter list
/home/enverex/src/a828-install/aver/osdep_dvb.c:580: error: conflicting types for ‘demux_sw_stop_feed’
/home/enverex/src/a828-install/aver/osdep_dvb.c:150: error: previous declaration of ‘demux_sw_stop_feed’ was here
/home/enverex/src/a828-install/aver/osdep_dvb.c: In function ‘demux_sw_stop_feed’:
/home/enverex/src/a828-install/aver/osdep_dvb.c:581: error: dereferencing pointer to incomplete type
/home/enverex/src/a828-install/aver/osdep_dvb.c:582: error: dereferencing pointer to incomplete type
/home/enverex/src/a828-install/aver/osdep_dvb.c: At top level:
/home/enverex/src/a828-install/aver/osdep_dvb.c:603: warning: ‘struct dvb_frontend_parameters’ declared inside parameter list
/home/enverex/src/a828-install/aver/osdep_dvb.c:604: error: conflicting types for ‘dvbfe_set_parameters’
/home/enverex/src/a828-install/aver/osdep_dvb.c:152: error: previous declaration of ‘dvbfe_set_parameters’ was here
/home/enverex/src/a828-install/aver/osdep_dvb.c: In function ‘dvbfe_set_parameters’:
/home/enverex/src/a828-install/aver/osdep_dvb.c:605: error: dereferencing pointer to incomplete type
/home/enverex/src/a828-install/aver/osdep_dvb.c:607: warning: passing argument 2 of ‘SetParameters’ from incompatible pointer type
/home/enverex/src/a828-install/aver/osdep_dvb.c: At top level:
/home/enverex/src/a828-install/aver/osdep_dvb.c:611: warning: ‘struct dvb_frontend_parameters’ declared inside parameter list
/home/enverex/src/a828-install/aver/osdep_dvb.c:612: error: conflicting types for ‘dvbfe_get_parameters’
/home/enverex/src/a828-install/aver/osdep_dvb.c:154: error: previous declaration of ‘dvbfe_get_parameters’ was here
/home/enverex/src/a828-install/aver/osdep_dvb.c: In function ‘dvbfe_get_parameters’:
/home/enverex/src/a828-install/aver/osdep_dvb.c:613: error: dereferencing pointer to incomplete type
/home/enverex/src/a828-install/aver/osdep_dvb.c:615: warning: passing argument 2 of ‘GetParameters’ from incompatible pointer type
/home/enverex/src/a828-install/aver/osdep_dvb.c: At top level:
/home/enverex/src/a828-install/aver/osdep_dvb.c:618: error: expected declaration specifiers or ‘...’ before ‘fe_status_t’
/home/enverex/src/a828-install/aver/osdep_dvb.c: In function ‘dvbfe_read_status’:
/home/enverex/src/a828-install/aver/osdep_dvb.c:620: error: dereferencing pointer to incomplete type
/home/enverex/src/a828-install/aver/osdep_dvb.c:622: error: ‘status’ undeclared (first use in this function)
/home/enverex/src/a828-install/aver/osdep_dvb.c:622: error: too many arguments to function ‘GetStatus’
/home/enverex/src/a828-install/aver/osdep_dvb.c: In function ‘dvbfe_read_ber’:
/home/enverex/src/a828-install/aver/osdep_dvb.c:627: error: dereferencing pointer to incomplete type
/home/enverex/src/a828-install/aver/osdep_dvb.c: In function ‘dvbfe_read_signal_strength’:
/home/enverex/src/a828-install/aver/osdep_dvb.c:634: error: dereferencing pointer to incomplete type
/home/enverex/src/a828-install/aver/osdep_dvb.c: In function ‘dvbfe_read_snr’:
/home/enverex/src/a828-install/aver/osdep_dvb.c:641: error: dereferencing pointer to incomplete type
/home/enverex/src/a828-install/aver/osdep_dvb.c: In function ‘dvbfe_read_ucblocks’:
/home/enverex/src/a828-install/aver/osdep_dvb.c:648: error: dereferencing pointer to incomplete type
/home/enverex/src/a828-install/aver/osdep_dvb.c: In function ‘dvbfe_init’:
/home/enverex/src/a828-install/aver/osdep_dvb.c:655: error: dereferencing pointer to incomplete type
/home/enverex/src/a828-install/aver/osdep_dvb.c: In function ‘dvbfe_sleep’:
/home/enverex/src/a828-install/aver/osdep_dvb.c:662: error: dereferencing pointer to incomplete type
/home/enverex/src/a828-install/aver/osdep_dvb.c: At top level:
/home/enverex/src/a828-install/aver/osdep_dvb.c:668: warning: ‘struct dvb_frontend_tune_settings’ declared inside parameter list
/home/enverex/src/a828-install/aver/osdep_dvb.c:669: error: conflicting types for ‘dvbfe_get_tune_settings’
/home/enverex/src/a828-install/aver/osdep_dvb.c:161: error: previous declaration of ‘dvbfe_get_tune_settings’ was here
/home/enverex/src/a828-install/aver/osdep_dvb.c: In function ‘dvbfe_get_tune_settings’:
/home/enverex/src/a828-install/aver/osdep_dvb.c:671: error: dereferencing pointer to incomplete type
/home/enverex/src/a828-install/aver/osdep_dvb.c:672: error: dereferencing pointer to incomplete type
/home/enverex/src/a828-install/aver/osdep_dvb.c:673: error: dereferencing pointer to incomplete type
/home/enverex/src/a828-install/aver/osdep_dvb.c: In function ‘dvbfe_diseqc_reset_overload’:
/home/enverex/src/a828-install/aver/osdep_dvb.c:682: error: dereferencing pointer to incomplete type
/home/enverex/src/a828-install/aver/osdep_dvb.c: At top level:
/home/enverex/src/a828-install/aver/osdep_dvb.c:687: warning: ‘struct dvb_diseqc_master_cmd’ declared inside parameter list
/home/enverex/src/a828-install/aver/osdep_dvb.c:688: error: conflicting types for ‘dvbfe_diseqc_send_master_cmd’
/home/enverex/src/a828-install/aver/osdep_dvb.c:168: error: previous declaration of ‘dvbfe_diseqc_send_master_cmd’ was here
/home/enverex/src/a828-install/aver/osdep_dvb.c: In function ‘dvbfe_diseqc_send_master_cmd’:
/home/enverex/src/a828-install/aver/osdep_dvb.c:689: error: dereferencing pointer to incomplete type
/home/enverex/src/a828-install/aver/osdep_dvb.c:691: warning: passing argument 2 of ‘DiseqcSendMasterCMD’ from incompatible pointer type
/home/enverex/src/a828-install/aver/osdep_dvb.c: At top level:
/home/enverex/src/a828-install/aver/osdep_dvb.c:694: warning: ‘struct dvb_diseqc_slave_reply’ declared inside parameter list
/home/enverex/src/a828-install/aver/osdep_dvb.c:695: error: conflicting types for ‘dvbfe_diseqc_recv_slave_reply’
/home/enverex/src/a828-install/aver/osdep_dvb.c:169: error: previous declaration of ‘dvbfe_diseqc_recv_slave_reply’ was here
/home/enverex/src/a828-install/aver/osdep_dvb.c: In function ‘dvbfe_diseqc_recv_slave_reply’:
/home/enverex/src/a828-install/aver/osdep_dvb.c:696: error: dereferencing pointer to incomplete type
/home/enverex/src/a828-install/aver/osdep_dvb.c:698: warning: passing argument 2 of ‘DiseqcRecvSlaveReply’ from incompatible pointer type
/home/enverex/src/a828-install/aver/osdep_dvb.c: At top level:
/home/enverex/src/a828-install/aver/osdep_dvb.c:701: error: expected declaration specifiers or ‘...’ before ‘fe_sec_mini_cmd_t’
/home/enverex/src/a828-install/aver/osdep_dvb.c: In function ‘dvbfe_diseqc_send_burst’:
/home/enverex/src/a828-install/aver/osdep_dvb.c:703: error: dereferencing pointer to incomplete type
/home/enverex/src/a828-install/aver/osdep_dvb.c:705: error: ‘arg’ undeclared (first use in this function)
/home/enverex/src/a828-install/aver/osdep_dvb.c:705: error: too many arguments to function ‘DiseqcSendBurst’
/home/enverex/src/a828-install/aver/osdep_dvb.c: At top level:
/home/enverex/src/a828-install/aver/osdep_dvb.c:708: error: expected declaration specifiers or ‘...’ before ‘fe_sec_tone_mode_t’
/home/enverex/src/a828-install/aver/osdep_dvb.c: In function ‘dvbfe_set_tone’:
/home/enverex/src/a828-install/aver/osdep_dvb.c:710: error: dereferencing pointer to incomplete type
/home/enverex/src/a828-install/aver/osdep_dvb.c:712: error: ‘arg’ undeclared (first use in this function)
/home/enverex/src/a828-install/aver/osdep_dvb.c:712: error: too many arguments to function ‘SetTone’
/home/enverex/src/a828-install/aver/osdep_dvb.c: At top level:
/home/enverex/src/a828-install/aver/osdep_dvb.c:715: error: expected declaration specifiers or ‘...’ before ‘fe_sec_voltage_t’
/home/enverex/src/a828-install/aver/osdep_dvb.c: In function ‘dvbfe_set_voltage’:
/home/enverex/src/a828-install/aver/osdep_dvb.c:717: error: dereferencing pointer to incomplete type
/home/enverex/src/a828-install/aver/osdep_dvb.c:719: error: ‘arg’ undeclared (first use in this function)
/home/enverex/src/a828-install/aver/osdep_dvb.c:719: error: too many arguments to function ‘SetVoltage’
/home/enverex/src/a828-install/aver/osdep_dvb.c: In function ‘dvbfe_enable_high_lnb_voltage’:
/home/enverex/src/a828-install/aver/osdep_dvb.c:728: error: dereferencing pointer to incomplete type
make[3]: *** [/home/enverex/src/a828-install/aver/osdep_dvb.o] Error 1
make[2]: *** [_module_/home/enverex/src/a828-install] Error 2
make[1]: *** [_all] Error 2
make[1]: Leaving directory `/usr/src/linux-headers-2.6.17-10-generic'
make: *** [default] Error 2

```

So no success there either (I searched the kernel source folder just to check but those files don't exist).

Does anyone have any ideas how I could possibly get this working or do I have another "Windows only" expensive paperweight?

---

### Post by esofron on 2008-01-02
Hello,

i have the same problem with the A828 driver install on ubuntu 7.10 .

Is there any solution for this, or something to try?

Thanks,

:(

---

