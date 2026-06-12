---
title: "synaptics mouse driver hangups"
date: 2006-11-18
forum: Hardware &amp; Laptops
---

### Post by s_p_a_r_k_y on 2006-11-18
I have a synaptic touchpad. Under dapper and breezy it was fine and I didn't notice any real problems. However since I installed edgy my mouse will just hang and I have to alt-tab sometimes or ctrl-alt-f1 and then come back to the desktop to regain the mouse. Here is some dmesg output
```

 [17179983.612000] psmouse.c: TouchPad at isa0060/serio2/input0 lost sync at byte 1
[17179983.616000] psmouse.c: TouchPad at isa0060/serio2/input0 lost sync at byte 1
[17179983.616000] psmouse.c: TouchPad at isa0060/serio2/input0 lost sync at byte 1
[17179983.620000] psmouse.c: TouchPad at isa0060/serio2/input0 lost sync at byte 1
[17179983.620000] psmouse.c: TouchPad at isa0060/serio2/input0 lost sync at byte 1
[17179983.620000] psmouse.c: issuing reconnect request
[17179985.940000] psmouse.c: TouchPad at isa0060/serio2/input0 lost sync at byte 1
[17179985.940000] psmouse.c: TouchPad at isa0060/serio2/input0 lost sync at byte 1
[17179985.944000] psmouse.c: TouchPad at isa0060/serio2/input0 lost sync at byte 1
[17179985.944000] psmouse.c: TouchPad at isa0060/serio2/input0 lost sync at byte 1
[17179985.956000] psmouse.c: TouchPad at isa0060/serio2/input0 lost sync at byte 4
[17179985.956000] psmouse.c: issuing reconnect request
[17180048.936000] psmouse.c: TouchPad at isa0060/serio2/input0 lost sync at byte 1
[17180048.936000] psmouse.c: TouchPad at isa0060/serio2/input0 lost sync at byte 1
[17180048.940000] psmouse.c: TouchPad at isa0060/serio2/input0 lost sync at byte 1
[17180048.940000] psmouse.c: TouchPad at isa0060/serio2/input0 lost sync at byte 1
[17180048.944000] psmouse.c: TouchPad at isa0060/serio2/input0 lost sync at byte 1
[17180048.944000] psmouse.c: issuing reconnect request

```

Is there something I can change in xorg conf or ...?

---

