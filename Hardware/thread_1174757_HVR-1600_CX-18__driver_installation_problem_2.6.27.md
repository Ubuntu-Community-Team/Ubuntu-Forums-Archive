---
title: "HVR-1600 CX-18  driver installation problem 2.6.27.14(ubuntu 32bit) on M2N68-VM"
date: 2009-05-31
forum: Hardware
---

### Post by anupindi007 on 2009-05-31
Hi,
From quite some time i am struggling to configure HVR-1600 card(CX18
 From quite some time i am struggling to configure HVR-1600 card(CX18
  Drivers) with remote.   Could you let me know what can be done to
  resolve the problem and where i can get proper  "v4l-dvb" version bz2
  repository to 2.6.27.14 ubuntu kernel.
 
  I have followed the link:
  [http://www.mythtv.org/wiki/Hauppauge_HVR-1600](http://www.mythtv.org/wiki/Hauppauge_HVR-1600) &
  [http://www.linuxtv.org/hg/](http://www.linuxtv.org/hg/)
 
  My system configuration as follows:
  Motherboard           : Asus M2N68-VM
  Graphics Card         : GeForce 7050PV + nForce 630a
  TV tuner & remote : Hauppauge HVR-1600 (remote :A415-HPG-A  )

 
 
 
  # uname -r
  2.6.27-14-generic
  (installed 32bin os on 64bin hardware) 
  # lspci
  01:07.0 Multimedia video controller: Conexant CX23418 Single-Chip
  MPEG-2 Encoder with Integrated Analog Video/Broadcast Audio Decoder
 
  #lspci -vn
  01:07.0 0400: 14f1:5b7a
        Subsystem: 0070:7444
        Flags: bus master, medium devsel, latency 64, IRQ 11
        Memory at d8000000 (32-bit, non-prefetchable) [size=64M]
        Capabilities: [44] Vital Product Data <?>
        Capabilities: [4c] Power Management version 2
        Kernel modules: cx18
 
  #lspci -v
 
  01:07.0 Multimedia video controller: Conexant CX23418 Single-Chip
  MPEG-2 Encoder with Integrated Analog Video/Broadcast Audio Decoder
        Subsystem: Hauppauge computer works Inc. Device 7444
        Flags: bus master, medium devsel, latency 64, IRQ 11
        Memory at d8000000 (32-bit, non-prefetchable) [size=64M]
        Capabilities: [44] Vital Product Data <?>
        Capabilities: [4c] Power Management version 2
        Kernel modules: cx18
 
  # modprobe cx18
  FATAL: Error inserting cx18
  (/lib/modules/2.6.27-14-generic/kernel/drivers/media/video/cx18/cx18.ko):
  Unknown symbol in module, or unknown parameter (see dmesg)
 
 
  #  dmesg | grep cx18
  Note: Now I am getting this error now and earlier i got "cx18:
 Unknown symbol __udivdi3" :
  [  407.288401] cx18: disagrees about version of symbol
  v4l2_i2c_new_probed_subdev
  [  407.288409] cx18: Unknown symbol v4l2_i2c_new_probed_subdev
  [  407.288587] cx18: disagrees about version of symbol
  v4l2_device_register_subdev
  [  407.288592] cx18: Unknown symbol v4l2_device_register_subdev
  [  407.288697] cx18: disagrees about version of symbol video_devdata
  [  407.288701] cx18: Unknown symbol video_devdata
  [  407.289374] cx18: disagrees about version of symbol
  video_unregister_device
  [  407.289379] cx18: Unknown symbol video_unregister_device
  [  407.289519] cx18: disagrees about version of symbol
  video_device_alloc
  [  407.289522] cx18: Unknown symbol video_device_alloc
  [  407.289584] cx18: disagrees about version of symbol
  video_register_device
  [  407.289586] cx18: Unknown symbol video_register_device
  [  407.289716] cx18: disagrees about version of symbol
  v4l2_device_register
  [  407.289719] cx18: Unknown symbol v4l2_device_register
  [  407.290176] cx18: disagrees about version of symbol
  v4l2_device_unregister
  [  407.290179] cx18: Unknown symbol v4l2_device_unregister
  [  407.290368] cx18: disagrees about version of symbol
  video_device_release
  [  407.290371] cx18: Unknown symbol video_device_release
  [  407.290419] cx18: disagrees about version of symbol
  v4l2_i2c_new_subdev
  [  407.290422] cx18: Unknown symbol v4l2_i2c_new_subdev
  [ 2924.550531] cx18: disagrees about version of symbol
  v4l2_i2c_new_probed_subdev
  [ 2924.550547] cx18: Unknown symbol v4l2_i2c_new_probed_subdev
  [ 2924.550713] cx18: disagrees about version of symbol
  v4l2_device_register_subdev
  [ 2924.550715] cx18: Unknown symbol v4l2_device_register_subdev
  [ 2924.550818] cx18: disagrees about version of symbol video_devdata
  [ 2924.550819] cx18: Unknown symbol video_devdata
  [ 2924.552070] cx18: disagrees about version of symbol video_unregister_device
  [ 2924.552075] cx18: Unknown symbol video_unregister_device
  [ 2924.552216] cx18: disagrees about version of symbol video_device_alloc
  [ 2924.552217] cx18: Unknown symbol video_device_alloc
  [ 2924.552280] cx18: disagrees about version of symbol video_register_device
  [ 2924.552281] cx18: Unknown symbol video_register_device
  [ 2924.552411] cx18: disagrees about version of symbol v4l2_device_register
  [ 2924.552413] cx18: Unknown symbol v4l2_device_register
  [ 2924.552870] cx18: disagrees about version of symbol v4l2_device_unregister
  [ 2924.552871] cx18: Unknown symbol v4l2_device_unregister
  [ 2924.553061] cx18: disagrees about version of symbol video_device_release
  [ 2924.553063] cx18: Unknown symbol video_device_release
  [ 2924.553110] cx18: disagrees about version of symbol v4l2_i2c_new_subdev
  [ 2924.553112] cx18: Unknown symbol v4l2_i2c_new_subdev
 
  I have tried with different : V4L-DVB repositories   and i couldn't
  find the right version.
  v4l-dvb-25bc0580359a.tar.bz2
  v4l-dvb-65ec132f20df.tar.bz2
  95301c2a088a.tar.bz2
  zr364xx-95301c2a088a
 
  #find /lib/modules -name dvb-core.ko -print
  <returns null>
 
  # find /lib/modules -name dvb-core.ko -exec modinfo -F vermagic {} \; -print
  2.6.27-14-generic SMP mod_unload modversions 586
  /lib/modules/2.6.27-14-generic/kernel/drivers/media/dvb/dvb-core/dvb-core.ko
 
  2.6.27-7-generic SMP mod_unload modversions 586
  /lib/modules/2.6.27-7-generic/kernel/drivers/media/dvb/dvb-core/dvb-core.ko
 
  #find /lib/modules -name cx18.ko -exec modinfo -F vermagic {} \; -print
  2.6.27-14-generic SMP mod_unload modversions 586
  /lib/modules/2.6.27-14-generic/kernel/drivers/media/video/cx18/cx18.ko
 
  2.6.27-7-generic SMP mod_unload modversions 586
  /lib/modules/2.6.27-7-generic/kernel/drivers/media/video/cx18/cx18.ko
 
  # modinfo -F vermagic cx18
  2.6.27-14-generic SMP mod_unload modversions 586
 
  Earlier moved the following files to different location  for trouble
  shooting ( mv
  /lib/modules/2.6.27-14-generic/kernel/drivers/media/video/<>
  /lib/modules/2.6.27-14-generic/kernel/drivers/media/video/sri)
 
  - cx2341x.ko
  -  tveeprom.ko
  -  v4l1-compat.ko
  -  v4l2-common.ko
  -  videodev.ko
 
 
  Thanks in advance,
  Srinivasu Anupindi

---

