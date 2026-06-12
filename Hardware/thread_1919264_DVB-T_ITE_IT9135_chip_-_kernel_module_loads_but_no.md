---
title: "DVB-T ITE IT9135 chip - kernel module loads but no device"
date: 2012-02-02
forum: Hardware
---

### Post by steryd_net on 2012-02-02
Hi,
I just got myself a usb dvb-t tuner based on IT9135 chip. I installed 3.2 kernel from repositories and build v4l. When running lsmod | grep dvb I get this:
```
dvb_usb_it913x         22173  0 
dvb_usb                32387  1 dvb_usb_it913x
dvb_core              109744  1 dvb_usb
rc_core                 26333  10  ir_lirc_codec,ir_mce_kbd_decoder,ir_sanyo_decoder,ir_sony_decoder,ir_jvc_decoder,ir_rc6_decoder,ir_rc5_decoder,ir_nec_decoder,dvb_usb_it913x,dvb_usb
```So everything seems to be fine... however there is no device visible in /dev/v4l/ and no application can detect the tuner. Any ideas?
Thanks for any help.

---

