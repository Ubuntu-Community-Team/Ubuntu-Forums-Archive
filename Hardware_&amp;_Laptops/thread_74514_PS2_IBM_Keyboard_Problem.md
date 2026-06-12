---
title: "PS/2 IBM Keyboard Problem"
date: 2005-10-11
forum: Hardware &amp; Laptops
---

### Post by joaoeb on 2005-10-11
First a note. I'm using breezy, i686-smp kernel.

Ok, now the problem. I have a (very) old (buckling spring) IBM keyboard with a PS/2 interface (the keyboard come with a 386, it plugs in the PS/2 socket and works, so I'm assuming it is a PS/2 keyboard). When I boot in the system the keyboard works perfectly. But my /var/log/messages shows this kind of errors every time a non standard key (arrows, numpad, etc) is pressed:

```
Oct 11 23:01:54 localhost kernel: [4294735.819000] atkbd.c: Unknown key pressed (translated set 2, code 0xaa on isa0060/serio0).
Oct 11 23:01:54 localhost kernel: [4294735.819000] atkbd.c: Use 'setkeycodes e02a <keycode>' to make it known.
Oct 11 23:01:54 localhost kernel: [4294735.943000] atkbd.c: Unknown key released (translated set 2, code 0xaa on isa0060/serio0).
Oct 11 23:01:54 localhost kernel: [4294735.943000] atkbd.c: Use 'setkeycodes e02a <keycode>' to make it known.
```

So, I disconnect the keyboard and reconnect it again. It causes /var/log/messages to show this message:

```
Oct 11 23:02:30 localhost kernel: [4294771.845000] input: AT Translated Set 2 keyboard on isa0060/serio0
Oct 11 23:02:30 localhost input.agent[8086]:      evdev: already loaded
Oct 11 23:02:30 localhost input.agent[8094]:      evdev: already loaded

```

And the previous error stops. 

It's not critical, the only problem it causes is giant log files (witch I can delete), and I know the workaround. But if someone knows what causes this errors (and possibly the solution) I will be very glad. 

Thanks in advance :)

---

