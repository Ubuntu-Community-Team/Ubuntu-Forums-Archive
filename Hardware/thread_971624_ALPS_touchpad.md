---
title: "ALPS touchpad"
date: 2008-11-05
forum: Hardware
---

### Post by tornike on 2008-11-05
I am using ubuntu 8.10 on toshiba laptop. Unfortunately I couldn't make my ALPS touchpad work. The system seems to detect it but the pointer is not responding. 
```
[COLOR="Red"]xinput list[/COLOR]
"AlpsPS/2 ALPS GlidePoint"	id=3	[XExtensionPointer]
	Num_buttons is 12
	Num_axes is 2
	Mode is Relative
	Motion_buffer is 256
	Axis 0 :
		Min_value is 0
		Max_value is -1
		Resolution is 1
	Axis 1 :
		Min_value is 0
		Max_value is -1
		Resolution is 1
```

```
[COLOR="Red"]/var/log/Xorg.0.log[/COLOR]

(II) config/hal: Adding input device AlpsPS/2 ALPS GlidePoint
(II) LoadModule: "synaptics"

(II) Loading /usr/lib/xorg/modules/input//synaptics_drv.so
(II) Module synaptics: vendor="X.Org Foundation"
	compiled for 1.5.2, module version = 0.15.2
	Module class: X.Org XInput Driver
	ABI class: X.Org XInput driver, version 2.1
(II) Synaptics touchpad driver version 0.15.2
(II) AlpsPS/2 ALPS GlidePoint: x-axis range 0 - 1023
(II) AlpsPS/2 ALPS GlidePoint: y-axis range 0 - 767
(**) Option "Device" "/dev/input/event8"
(--) AlpsPS/2 ALPS GlidePoint touchpad found
(**) AlpsPS/2 ALPS GlidePoint: always reports core events
(II) XINPUT: Adding extended input device "AlpsPS/2 ALPS GlidePoint" (type: TOUCHPAD)
(II) AlpsPS/2 ALPS GlidePoint: x-axis range 0 - 1023
(II) AlpsPS/2 ALPS GlidePoint: y-axis range 0 - 767
(--) AlpsPS/2 ALPS GlidePoint touchpad found
```

Can anyone tell me what is going wrong?
Thanks.

---

