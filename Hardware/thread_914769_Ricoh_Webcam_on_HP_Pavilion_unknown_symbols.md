---
title: "Ricoh Webcam on HP Pavilion: unknown symbols"
date: 2008-09-09
forum: Hardware
---

### Post by HalphaZ on 2008-09-09
Hello,

I've a HP Pavilion Laptop with a ricoh 1810 webcam and Hardy 32 bit.
I added
deb [http://download.tuxfamily.org/arakhne/ubuntu](http://download.tuxfamily.org/arakhne/ubuntu) hardy-arakhne universe

to my sources.list, following the instructions in [http://nakinub.noblogs.org/post/2007/05/18/webcam-05ca-1810-ricoh](http://nakinub.noblogs.org/post/2007/05/18/webcam-05ca-1810-ricoh)  and in  [http://www.arakhne.org/download.html](http://www.arakhne.org/download.html)

I ran: "sudo apt-get install ricoh-webcam-r5u870" and it installed the driver, but when it tries to load, dmesg says that there Unkown symbols...

Here there are details:

```
uname -a
Linux MasterChief 2.6.24-21-generic #1 SMP Mon Aug 25 17:32:09 UTC 2008 i686 GNU/Linux
```

```
lsusb
Bus 002 Device 003: ID 0518:0005 EzKEY Corp. 
Bus 002 Device 002: ID 04f3:0801 Elan Microelectronics Corp. 
Bus 002 Device 001: ID 0000:0000  
Bus 001 Device 004: ID 05ca:1810 Ricoh Co., Ltd 
Bus 001 Device 001: ID 0000:0000 
```

```
dmesg | grep -i uvc
[   38.544642] uvcvideo: disagrees about version of symbol video_devdata
[   38.544648] uvcvideo: Unknown symbol video_devdata
[   38.545009] uvcvideo: disagrees about version of symbol video_unregister_device
[   38.545012] uvcvideo: Unknown symbol video_unregister_device
[   38.545122] uvcvideo: disagrees about version of symbol video_device_alloc
[   38.545124] uvcvideo: Unknown symbol video_device_alloc
[   38.545201] uvcvideo: disagrees about version of symbol video_register_device
[   38.545203] uvcvideo: Unknown symbol video_register_device
[   38.545427] uvcvideo: disagrees about version of symbol video_device_release
[   38.545429] uvcvideo: Unknown symbol video_device_release
```


Moreover, I tried compiling the driver following these istructions: [http://wiki.mediati.org/Installation](http://wiki.mediati.org/Installation)

but:

```
 dmesg | grep -i r5u870
[   39.000444] r5u870: Unknown symbol usbcam_ctrl_add
[   39.000496] r5u870: Unknown symbol usbcam_curframe_get
[   39.000551] r5u870: Unknown symbol usbcam_claim_interface
[   39.000601] r5u870: Unknown symbol usbcam_curframe_testpattern
[   39.000650] r5u870: Unknown symbol usbcam_urbstream_stop
[   39.000700] r5u870: Unknown symbol usbcam_urbstream_start
[   39.000749] r5u870: Unknown symbol usbcam_ctrl_add_tmpl
[   39.000798] r5u870: Unknown symbol usbcam_urbstream_cleanup
[   39.000854] r5u870: Unknown symbol usbcam_register_mod
[   39.001038] r5u870: Unknown symbol usbcam_curframe_abortall
[   39.001090] r5u870: Unknown symbol usbcam_curframe_complete_detail
[   39.001140] r5u870: Unknown symbol usbcam_unregister
[   39.001195] r5u870: Unknown symbol usbcam_urbstream_init
[   39.001250] r5u870: Unknown symbol usbcam_choose_altsetting
[   39.001305] r5u870: Unknown symbol usbcam_ctrl_alloc
[   39.001354] r5u870: Unknown symbol usbcam_urbstream_config_iso
[   41.125521] r5u870: Unknown symbol usbcam_ctrl_add
[   41.125574] r5u870: Unknown symbol usbcam_curframe_get
[   41.125628] r5u870: Unknown symbol usbcam_claim_interface
[   41.125678] r5u870: Unknown symbol usbcam_curframe_testpattern
[   41.125727] r5u870: Unknown symbol usbcam_urbstream_stop
[   41.125777] r5u870: Unknown symbol usbcam_urbstream_start
[   41.125826] r5u870: Unknown symbol usbcam_ctrl_add_tmpl
[   41.125875] r5u870: Unknown symbol usbcam_urbstream_cleanup
[   41.125931] r5u870: Unknown symbol usbcam_register_mod
[   41.126116] r5u870: Unknown symbol usbcam_curframe_abortall
[   41.126169] r5u870: Unknown symbol usbcam_curframe_complete_detail
[   41.126218] r5u870: Unknown symbol usbcam_unregister
[   41.126274] r5u870: Unknown symbol usbcam_urbstream_init
[   41.126329] r5u870: Unknown symbol usbcam_choose_altsetting
[   41.126384] r5u870: Unknown symbol usbcam_ctrl_alloc
[   41.126434] r5u870: Unknown symbol usbcam_urbstream_config_iso
[11336.556147] r5u870: Unknown symbol usbcam_ctrl_add
[11336.556210] r5u870: Unknown symbol usbcam_curframe_get
[11336.556269] r5u870: Unknown symbol usbcam_claim_interface
[11336.556323] r5u870: Unknown symbol usbcam_curframe_testpattern
[11336.556392] r5u870: Unknown symbol usbcam_urbstream_stop
[11336.556445] r5u870: Unknown symbol usbcam_urbstream_start
[11336.556497] r5u870: Unknown symbol usbcam_ctrl_add_tmpl
[11336.556551] r5u870: Unknown symbol usbcam_urbstream_cleanup
[11336.556611] r5u870: Unknown symbol usbcam_register_mod
[11336.556805] r5u870: Unknown symbol usbcam_curframe_abortall
[11336.556861] r5u870: Unknown symbol usbcam_curframe_complete_detail
[11336.556914] r5u870: Unknown symbol usbcam_unregister
[11336.556974] r5u870: Unknown symbol usbcam_urbstream_init
[11336.557033] r5u870: Unknown symbol usbcam_choose_altsetting
[11336.557091] r5u870: Unknown symbol usbcam_ctrl_alloc
[11336.557144] r5u870: Unknown symbol usbcam_urbstream_config_iso
[11338.629901] r5u870: Unknown symbol usbcam_ctrl_add
[11338.629961] r5u870: Unknown symbol usbcam_curframe_get
[11338.630019] r5u870: Unknown symbol usbcam_claim_interface
[11338.630076] r5u870: Unknown symbol usbcam_curframe_testpattern
[11338.630129] r5u870: Unknown symbol usbcam_urbstream_stop
[11338.630181] r5u870: Unknown symbol usbcam_urbstream_start
[11338.630249] r5u870: Unknown symbol usbcam_ctrl_add_tmpl
[11338.630302] r5u870: Unknown symbol usbcam_urbstream_cleanup
[11338.630361] r5u870: Unknown symbol usbcam_register_mod
[11338.630556] r5u870: Unknown symbol usbcam_curframe_abortall
[11338.630612] r5u870: Unknown symbol usbcam_curframe_complete_detail
[11338.630665] r5u870: Unknown symbol usbcam_unregister
[11338.630723] r5u870: Unknown symbol usbcam_urbstream_init
[11338.630782] r5u870: Unknown symbol usbcam_choose_altsetting
[11338.630839] r5u870: Unknown symbol usbcam_ctrl_alloc
[11338.630891] r5u870: Unknown symbol usbcam_urbstream_config_iso
[11366.430441] r5u870: Unknown symbol usbcam_ctrl_add
[11366.430501] r5u870: Unknown symbol usbcam_curframe_get
[11366.430559] r5u870: Unknown symbol usbcam_claim_interface
[11366.430612] r5u870: Unknown symbol usbcam_curframe_testpattern
[11366.430664] r5u870: Unknown symbol usbcam_urbstream_stop
[11366.430717] r5u870: Unknown symbol usbcam_urbstream_start
[11366.430769] r5u870: Unknown symbol usbcam_ctrl_add_tmpl
[11366.430821] r5u870: Unknown symbol usbcam_urbstream_cleanup
[11366.430879] r5u870: Unknown symbol usbcam_register_mod
[11366.431073] r5u870: Unknown symbol usbcam_curframe_abortall
[11366.431128] r5u870: Unknown symbol usbcam_curframe_complete_detail
[11366.431181] r5u870: Unknown symbol usbcam_unregister
[11366.431239] r5u870: Unknown symbol usbcam_urbstream_init
[11366.431297] r5u870: Unknown symbol usbcam_choose_altsetting
[11366.431355] r5u870: Unknown symbol usbcam_ctrl_alloc
[11366.431407] r5u870: Unknown symbol usbcam_urbstream_config_iso
[11446.402721] r5u870: Unknown symbol usbcam_ctrl_add
[11446.402786] r5u870: Unknown symbol usbcam_curframe_get
[11446.402846] r5u870: Unknown symbol usbcam_claim_interface
[11446.402901] r5u870: Unknown symbol usbcam_curframe_testpattern
[11446.402956] r5u870: Unknown symbol usbcam_urbstream_stop
[11446.403019] r5u870: Unknown symbol usbcam_urbstream_start
[11446.403073] r5u870: Unknown symbol usbcam_ctrl_add_tmpl
[11446.403128] r5u870: Unknown symbol usbcam_urbstream_cleanup
[11446.403189] r5u870: Unknown symbol usbcam_register_mod
[11446.403391] r5u870: Unknown symbol usbcam_curframe_abortall
[11446.403450] r5u870: Unknown symbol usbcam_curframe_complete_detail
[11446.403504] r5u870: Unknown symbol usbcam_unregister
[11446.403563] r5u870: Unknown symbol usbcam_urbstream_init
[11446.403636] r5u870: Unknown symbol usbcam_choose_altsetting
[11446.403695] r5u870: Unknown symbol usbcam_ctrl_alloc
[11446.403749] r5u870: Unknown symbol usbcam_urbstream_config_iso
[11448.576080] r5u870: Unknown symbol usbcam_ctrl_add
[11448.576143] r5u870: Unknown symbol usbcam_curframe_get
[11448.576203] r5u870: Unknown symbol usbcam_claim_interface
[11448.576257] r5u870: Unknown symbol usbcam_curframe_testpattern
[11448.576326] r5u870: Unknown symbol usbcam_urbstream_stop
[11448.576380] r5u870: Unknown symbol usbcam_urbstream_start
[11448.576434] r5u870: Unknown symbol usbcam_ctrl_add_tmpl
[11448.576488] r5u870: Unknown symbol usbcam_urbstream_cleanup
[11448.576549] r5u870: Unknown symbol usbcam_register_mod
[11448.576747] r5u870: Unknown symbol usbcam_curframe_abortall
[11448.576805] r5u870: Unknown symbol usbcam_curframe_complete_detail
[11448.576859] r5u870: Unknown symbol usbcam_unregister
[11448.576919] r5u870: Unknown symbol usbcam_urbstream_init
[11448.576979] r5u870: Unknown symbol usbcam_choose_altsetting
[11448.577042] r5u870: Unknown symbol usbcam_ctrl_alloc
[11448.577097] r5u870: Unknown symbol usbcam_urbstream_config_iso
[11507.034398] r5u870: Unknown symbol usbcam_ctrl_add
[11507.034455] r5u870: Unknown symbol usbcam_curframe_get
[11507.034515] r5u870: Unknown symbol usbcam_claim_interface
[11507.034569] r5u870: Unknown symbol usbcam_curframe_testpattern
[11507.034624] r5u870: Unknown symbol usbcam_urbstream_stop
[11507.034679] r5u870: Unknown symbol usbcam_urbstream_start
[11507.034733] r5u870: Unknown symbol usbcam_ctrl_add_tmpl
[11507.034787] r5u870: Unknown symbol usbcam_urbstream_cleanup
[11507.034848] r5u870: Unknown symbol usbcam_register_mod
[11507.035045] r5u870: Unknown symbol usbcam_curframe_abortall
[11507.035102] r5u870: Unknown symbol usbcam_curframe_complete_detail
[11507.035157] r5u870: Unknown symbol usbcam_unregister
[11507.035217] r5u870: Unknown symbol usbcam_urbstream_init
[11507.035276] r5u870: Unknown symbol usbcam_choose_altsetting
[11507.035336] r5u870: Unknown symbol usbcam_ctrl_alloc
[11507.035390] r5u870: Unknown symbol usbcam_urbstream_config_iso

```

Can anyone help me please??? Thanks!!!

---

