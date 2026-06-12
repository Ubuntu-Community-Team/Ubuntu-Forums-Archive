---
title: "Keyboard and mouse"
date: 2011-02-26
forum: Hardware
---

### Post by WiuEmPe on 2011-02-26
Hi, I recently changed distro from Arch to Ubuntu. Using Arch linux I occured a weird problem: both mouse and keyboard used to stop working randomly. The problem disappeared when I installed Ubuntu. Everything was allright for about one week till now. The problem returned. The whole system works great and I am not doing anything special (apart from doing some boinc computing, but the cpu isn't overheating). And I also can't turn the numlock on/off.

/var/log/messages file is empty and this is /var/log/Xorg.0.log.old:

```

[    10.331] (II) config/udev: Adding input device ImPS/2 Generic Wheel Mouse (/dev/input/event3)
[    10.331] (**) ImPS/2 Generic Wheel Mouse: Applying InputClass "evdev pointer catchall"
[    10.331] (**) ImPS/2 Generic Wheel Mouse: always reports core events
[    10.331] (**) ImPS/2 Generic Wheel Mouse: Device: "/dev/input/event3"
[    10.400] (II) ImPS/2 Generic Wheel Mouse: Found 3 mouse buttons
[    10.400] (II) ImPS/2 Generic Wheel Mouse: Found scroll wheel(s)
[    10.400] (II) ImPS/2 Generic Wheel Mouse: Found relative axes
[    10.400] (II) ImPS/2 Generic Wheel Mouse: Found x and y relative axes
[    10.400] (II) ImPS/2 Generic Wheel Mouse: Configuring as mouse
[    10.400] (**) ImPS/2 Generic Wheel Mouse: YAxisMapping: buttons 4 and 5
[    10.400] (**) ImPS/2 Generic Wheel Mouse: EmulateWheelButton: 4, EmulateWheelInertia: 10, EmulateWheelTimeout: 200
[    10.400] (II) XINPUT: Adding extended input device "ImPS/2 Generic Wheel Mouse" (type: MOUSE)
[    10.400] (II) ImPS/2 Generic Wheel Mouse: initialized for relative axes.
[    10.400] (II) config/udev: Adding input device ImPS/2 Generic Wheel Mouse (/dev/input/mouse0)
[    10.400] (II) No input driver/identifier specified (ignoring)
[  3168.766] (II) XKB: reuse xkmfile /var/lib/xkb/server-4A04795684EB268A18236823B755207B06C43B57.xkm
[  3796.740] (II) XKB: reuse xkmfile /var/lib/xkb/server-4A04795684EB268A18236823B755207B06C43B57.xkm
[ 27376.460] (II) config/udev: removing device ImPS/2 Generic Wheel Mouse
[ 27376.461] (II) ImPS/2 Generic Wheel Mouse: Close
[ 27376.462] (II) UnloadModule: "evdev"
[ 27432.210] (II) Power Button: Close
[ 27432.210] (II) UnloadModule: "evdev"
[ 27432.280] (II) Power Button: Close
[ 27432.280] (II) UnloadModule: "evdev"
[ 27432.350] (II) AT Translated Set 2 keyboard: Close
[ 27432.350] (II) UnloadModule: "evdev"

```

This is my issue on archlinux: [https://bugs.archlinux.org/task/22915]("https://bugs.archlinux.org/task/22915")

And my hardware: 

[list]
[*]Processor: AMD Phenom(tm) II X4 955 Processor ( [Specyfication](http://products.amd.com/en-us/DesktopCPUDetail.aspx?id=682&f1=&f2=&f3=&f4=&f5=&f6=&f7=&f8=&f9=&f10=&f11=&f12=) )
[*]MO: Asrock 770 Extreme3 ( [Specyfikacja](http://www.asrock.com/mb/overview.asp?Model=770%20Extreme3&cat=Specifications) )
[*]RAM: DDR3 Kingston 4GB PC1600 CL9 HyperX Dual ( [Specyfication](http://www.ec.kingston.com/ecom/configurator_new/PartsInfo.asp?root=us&LinkBack=&ktcpartno=KHX1600C9D3X1K2/4G) )
[/list]

---

### Post by WiuEmPe on 2011-02-27
Log from /var/log/messages:
```

Feb 27 12:11:57 ubuntu kernel: [ 2783.850663] lo: Disabled Privacy Extensions
Feb 27 12:23:57 ubuntu kernel: [ 3503.508927] lo: Disabled Privacy Extensions
Feb 27 12:50:50 ubuntu kernel: [ 5116.187361] lo: Disabled Privacy Extensions
Feb 27 13:05:36 ubuntu kernel: [ 6002.032396] psmouse.c: Wheel Mouse at isa0060/serio1/input0 lost synchronization, throwing 1 bytes away.
Feb 27 13:05:38 ubuntu kernel: [ 6004.102516] psmouse.c: failed to re-enable mouse on isa0060/serio1
Feb 27 13:05:38 ubuntu kernel: [ 6004.102519] psmouse.c: resync failed, issuing reconnect request
Feb 27 13:05:39 ubuntu kernel: [ 6005.326858] atkbd serio0: Unknown key released (translated set 2, code 0xff on isa0060/serio0).
Feb 27 13:05:39 ubuntu kernel: [ 6005.326862] atkbd serio0: Use 'setkeycodes e07f <keycode>' to make it known.
Feb 27 13:11:32 ubuntu kernel: [ 6358.541895] show_signal_msg: 3 callbacks suppressed
Feb 27 13:11:32 ubuntu kernel: [ 6358.541900] python[2017]: segfault at 40 ip 00007f03679313b5 sp 00007fff623160d8 error 4 in libQtCore.so.4.7.0[7f03677ac000+28

```

i noticed that after a long time, characters typed on keyboard start to appear on screen

---

