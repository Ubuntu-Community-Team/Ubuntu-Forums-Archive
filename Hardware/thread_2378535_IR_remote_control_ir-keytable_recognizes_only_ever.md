---
title: "IR remote control: ir-keytable recognizes only every second button press"
date: 2017-11-24
forum: Hardware
---

### Post by endeavour79 on 2017-11-24
Hi,

I am still a Linux Newbie and slowly finding my way around. Recently I set-up a new media centre and now  am trying to get the remote to work.

I'm on Ubuntu 17.10 Kernel 4.13.14, running on Intel NUC7i5BNH.
Ubuntu recognizes the built-in IR receiver.

```


I: Bus=0019 Vendor=1283 Product=0000 Version=0000
N: Name="ITE8708 CIR transceiver"
P: Phys=
S: Sysfs=/devices/virtual/rc/rc0/input4
U: Uniq=
H: Handlers=kbd event4 
B: PROP=0
B: EV=100013
B: KEY=fc000 0 0 8000 108000000000 e3fc000000000 2046002908a4ffc
B: MSC=10

```

```


sudo ir-keytable 
Found /sys/class/rc/rc0/ (/dev/input/event4) with:
        Driver ite-cir, table rc-rc6-mce
        Supported protocols: lirc rc-5 rc-5-sz jvc sony nec sanyo mce_kbd rc-6 sharp xmp 
        Enabled protocols: lirc rc-6 
        Name: ITE8708 CIR transceiver
        bus: 25, vendor/product: 1283:0000, version: 0x0000
        Repeat delay = 150 ms, repeat period = 150 ms

```


I've configured a keytable for my Phillips RC6 remove (came originally with Zotac AD12+).
As you can see below, ir-keytable recognizes the button pressed and maps the keys to it.. BUT, it does so only for every **second** time I press each button. The first time (same scan code) doesn't get mapped.

```
1511522191.321882: event type EV_MSC(0x04): scancode = 0x80348458

1511522191.321882: event type EV_SYN(0x00).

1511522192.867006: event type EV_MSC(0x04): scancode = 0x80340458

1511522192.867006: event type EV_KEY(0x01) key_down: KEY_UP(0x0067)

1511522192.867006: event type EV_SYN(0x00).

1511522193.104232: event type EV_MSC(0x04): scancode = 0x80340458

1511522193.104232: event type EV_SYN(0x00).

1511522193.116266: event type EV_KEY(0x01) key_down: KEY_UP(0x0067)

1511522193.116266: event type EV_SYN(0x00).

1511522194.641659: event type EV_MSC(0x04): scancode = 0x80348459

1511522194.641659: event type EV_SYN(0x00).

1511522195.603883: event type EV_MSC(0x04): scancode = 0x80340459

1511522195.603883: event type EV_KEY(0x01) key_down: KEY_DOWN(0x006c)

1511522195.603883: event type EV_SYN(0x00).

1511522197.845591: event type EV_MSC(0x04): scancode = 0x8034845a

1511522197.845591: event type EV_MSC(0x00)

1511522198.845591: event type EV_MSC(0x04): scancode = 0x8034845a

1511522198.845591: event type EV_KEY(0x01) key_down: KEY_LEFT(0x0069)

1511522198.845591: event type EV_SYN(0x00).
```


Is this a bug or intended behaviour?
Is there a way for me to fix this issue and make the system respond correctly to each button press?

Thanks for your help!

Regards,
Alex

---

