---
title: "touchpad and keyboard aren't responding"
date: 2008-04-24
forum: Hardware
---

### Post by yakovyarmo on 2008-04-24
;-)i just did a fresh install of hardy on my hp dv6500t.
everything run smoothly out of the box but after some time ( hour or so ) the touchpad and keyboard stops responding.
but if i hook up an external usb mouse it works flawlessly.

what can be the problem??
maybe because i have enabled the laptop_mode?

appreciate any help.

and sorry for my bad English ;-)

---

### Post by nukedathlonman on 2008-04-24
I just upgraded, and like you I've suddenly can't use my touch pad...  (Different system, Acer 5002WLMi)  I've tried numerous things, and I can't use my touch pad what-so-ever. #-o

---

### Post by nukedathlonman on 2008-04-24
I also tried the obvious Fn-F7 to enable/disable it, no effect.  Everything loads up fine, but no registering of buttons presses or moving my finger across the pad - it's completely dead under Ubuntu at present time.

---

### Post by Ayuthia on 2008-04-24
What are you using for your boot parameters (noapic)?  If you are using noapic, it might be causing the interrupts to your USB ports to turn off.  You might need to add something like noirqdebug or irqpoll to help it work.

If you aren't, you might check your /var/log/messages and see if any error messages are showing up.

---

### Post by yakovyarmo on 2008-04-25
it happened again and this is what i got in the massage log

```
Apr 25 17:05:22 yakov-laptop kernel: [  747.127964] r8169: eth0: link down
Apr 25 17:05:22 yakov-laptop kernel: [  747.130847] ADDRCONF(NETDEV_UP): eth0: link is not ready
Apr 25 17:05:22 yakov-laptop kernel: [  747.143989] ADDRCONF(NETDEV_UP): wlan0: link is not ready
Apr 25 17:06:20 yakov-laptop kernel: [  777.298480] ADDRCONF(NETDEV_UP): wlan0: link is not ready
Apr 25 17:06:37 yakov-laptop kernel: [  786.337830] ADDRCONF(NETDEV_CHANGE): wlan0: link becomes ready
Apr 25 17:11:50 yakov-laptop kernel: [  943.431965] usb 2-2: USB disconnect, address 2
Apr 25 17:20:08 yakov-laptop kernel: [ 1132.505495] usb 2-2: new low speed USB device using uhci_hcd and address 3
Apr 25 17:20:08 yakov-laptop kernel: [ 1132.621831] usb 2-2: configuration #1 chosen from 1 choice
Apr 25 17:20:08 yakov-laptop kernel: [ 1132.642903] input: Logitech USB Receiver as /devices/pci0000:00/0000:00:1a.1/usb2/2-2/2-2:1.0/input/input11
Apr 25 17:20:08 yakov-laptop kernel: [ 1132.683469] input,hidraw0: USB HID v1.10 Mouse [Logitech USB Receiver] on usb-0000:00:1a.1-2
Apr 25 17:30:15 yakov-laptop kernel: [ 1296.624984] python[23047]: segfault at 0000000d eip b7753b69 esp bfeed2c0 error 4
Apr 25 17:57:24 yakov-laptop -- MARK --
Apr 25 18:17:24 yakov-laptop -- MARK --
Apr 25 18:30:38 yakov-laptop kernel: [ 2781.289069] psmouse.c: TouchPad at isa0060/serio1/input0 lost sync at byte 4
Apr 25 18:30:38 yakov-laptop kernel: [ 2781.290697] psmouse.c: TouchPad at isa0060/serio1/input0 lost sync at byte 1
Apr 25 18:30:38 yakov-laptop kernel: [ 2781.300595] psmouse.c: TouchPad at isa0060/serio1/input0 - driver resynched.
Apr 25 18:33:19 yakov-laptop kernel: [ 2902.412828] psmouse.c: TouchPad at isa0060/serio1/input0 lost sync at byte 1
Apr 25 18:33:19 yakov-laptop kernel: [ 2902.416205] psmouse.c: TouchPad at isa0060/serio1/input0 lost sync at byte 1
Apr 25 18:33:19 yakov-laptop kernel: [ 2902.417932] psmouse.c: TouchPad at isa0060/serio1/input0 lost sync at byte 1
Apr 25 18:33:19 yakov-laptop kernel: [ 2902.420529] psmouse.c: TouchPad at isa0060/serio1/input0 lost sync at byte 1
Apr 25 18:33:19 yakov-laptop kernel: [ 2902.422426] psmouse.c: TouchPad at isa0060/serio1/input0 lost sync at byte 1
Apr 25 18:33:19 yakov-laptop kernel: [ 2902.422430] psmouse.c: issuing reconnect request
Apr 25 18:33:21 yakov-laptop kernel: [ 2903.994112] Synaptics Touchpad, model: 1, fw: 6.3, id: 0x1a0b1, caps: 0xa04713/0x200000
Apr 25 18:33:21 yakov-laptop kernel: [ 2904.102189] input: SynPS/2 Synaptics TouchPad as /devices/platform/i8042/serio1/input/input12
Apr 25 18:33:21 yakov-laptop kernel: [ 2904.199986] psmouse.c: TouchPad at isa0060/serio1/input0 lost sync at byte 1
Apr 25 18:33:21 yakov-laptop kernel: [ 2904.202809] psmouse.c: TouchPad at isa0060/serio1/input0 lost sync at byte 1
Apr 25 18:33:21 yakov-laptop kernel: [ 2904.204393] psmouse.c: TouchPad at isa0060/serio1/input0 lost sync at byte 1
Apr 25 18:33:21 yakov-laptop kernel: [ 2904.205879] psmouse.c: TouchPad at isa0060/serio1/input0 lost sync at byte 1
Apr 25 18:33:21 yakov-laptop kernel: [ 2904.208096] psmouse.c: TouchPad at isa0060/serio1/input0 lost sync at byte 1
Apr 25 18:33:21 yakov-laptop kernel: [ 2904.208104] psmouse.c: issuing reconnect request
```

someone can please tell me what it says?

---

### Post by yakovyarmo on 2008-04-26
bump!!

---

