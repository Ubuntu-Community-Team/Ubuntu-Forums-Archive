---
title: "mouse out of sync..."
date: 2007-10-28
forum: Hardware &amp; Laptops
---

### Post by chr1831 on 2007-10-28
so here is my problem when i use ubuntu/kubuuntu 7.10 (note i had no problems b4 the upgrade) i decided to do a fresh install so installer finishes and what do u know my mouse keeps going out of control, here is a small snippet dmesg

```

[ 2648.012000] psmouse.c: TouchPad at isa0060/serio4/input0 lost sync at byte 4
[ 2648.024000] psmouse.c: TouchPad at isa0060/serio4/input0 - driver resynched.
[ 2648.040000] psmouse.c: TouchPad at isa0060/serio4/input0 lost sync at byte 4
[ 2648.044000] psmouse.c: TouchPad at isa0060/serio4/input0 lost sync at byte 4
[ 2648.048000] psmouse.c: TouchPad at isa0060/serio4/input0 lost sync at byte 1
[ 2648.048000] psmouse.c: TouchPad at isa0060/serio4/input0 lost sync at byte 1
[ 2648.052000] psmouse.c: TouchPad at isa0060/serio4/input0 lost sync at byte 1
[ 2648.052000] psmouse.c: issuing reconnect request
[ 2778.004000] psmouse.c: TouchPad at isa0060/serio4/input0 lost sync at byte 4
[ 2778.008000] psmouse.c: TouchPad at isa0060/serio4/input0 lost sync at byte 1
[ 2778.008000] psmouse.c: TouchPad at isa0060/serio4/input0 lost sync at byte 1
[ 2778.012000] psmouse.c: TouchPad at isa0060/serio4/input0 lost sync at byte 1
[ 2778.012000] psmouse.c: TouchPad at isa0060/serio4/input0 lost sync at byte 1
[ 2778.012000] psmouse.c: issuing reconnect request
[ 3038.036000] psmouse.c: TouchPad at isa0060/serio4/input0 lost sync at byte 1
[ 3038.040000] psmouse.c: TouchPad at isa0060/serio4/input0 lost sync at byte 1
[ 3038.040000] psmouse.c: TouchPad at isa0060/serio4/input0 lost sync at byte 1
[ 3038.064000] psmouse.c: TouchPad at isa0060/serio4/input0 - driver resynched.
[ 3038.064000] psmouse.c: TouchPad at isa0060/serio4/input0 lost sync at byte 1
[ 3038.068000] psmouse.c: TouchPad at isa0060/serio4/input0 lost sync at byte 1
[ 3038.068000] psmouse.c: TouchPad at isa0060/serio4/input0 lost sync at byte 1
[ 3038.084000] psmouse.c: TouchPad at isa0060/serio4/input0 lost sync at byte 4
[ 3038.084000] psmouse.c: TouchPad at isa0060/serio4/input0 lost sync at byte 1
[ 3038.084000] psmouse.c: issuing reconnect request
[ 3168.044000] psmouse.c: TouchPad at isa0060/serio4/input0 lost sync at byte 4
[ 3168.056000] psmouse.c: TouchPad at isa0060/serio4/input0 lost sync at byte 4
[ 3168.056000] psmouse.c: TouchPad at isa0060/serio4/input0 lost sync at byte 1
[ 3168.076000] psmouse.c: TouchPad at isa0060/serio4/input0 - driver resynched.
[ 3168.080000] psmouse.c: TouchPad at isa0060/serio4/input0 lost sync at byte 1
[ 3168.080000] psmouse.c: TouchPad at isa0060/serio4/input0 lost sync at byte 1
[ 3168.084000] psmouse.c: TouchPad at isa0060/serio4/input0 lost sync at byte 1
[ 3168.100000] psmouse.c: TouchPad at isa0060/serio4/input0 - driver resynched.
[ 3168.104000] psmouse.c: TouchPad at isa0060/serio4/input0 lost sync at byte 1
[ 3168.108000] psmouse.c: TouchPad at isa0060/serio4/input0 lost sync at byte 1
[ 3168.108000] psmouse.c: TouchPad at isa0060/serio4/input0 lost sync at byte 1
[ 3168.128000] psmouse.c: TouchPad at isa0060/serio4/input0 - driver resynched.
[ 3168.128000] psmouse.c: TouchPad at isa0060/serio4/input0 lost sync at byte 1
[ 3168.136000] psmouse.c: TouchPad at isa0060/serio4/input0 lost sync at byte 1
[ 3168.136000] psmouse.c: TouchPad at isa0060/serio4/input0 lost sync at byte 1
[ 3168.156000] psmouse.c: TouchPad at isa0060/serio4/input0 - driver resynched.
[ 3168.156000] psmouse.c: TouchPad at isa0060/serio4/input0 lost sync at byte 1
[ 3168.160000] psmouse.c: TouchPad at isa0060/serio4/input0 lost sync at byte 1
[ 3168.160000] psmouse.c: TouchPad at isa0060/serio4/input0 lost sync at byte 1
[ 3168.164000] psmouse.c: TouchPad at isa0060/serio4/input0 lost sync at byte 1
[ 3168.164000] psmouse.c: TouchPad at isa0060/serio4/input0 lost sync at byte 1
[ 3168.164000] psmouse.c: issuing reconnect request
[ 4338.220000] psmouse.c: TouchPad at isa0060/serio4/input0 lost sync at byte 4
[ 4338.224000] psmouse.c: TouchPad at isa0060/serio4/input0 lost sync at byte 1
[ 4338.228000] psmouse.c: TouchPad at isa0060/serio4/input0 lost sync at byte 1
[ 4338.228000] psmouse.c: TouchPad at isa0060/serio4/input0 lost sync at byte 1
[ 4338.228000] psmouse.c: TouchPad at isa0060/serio4/input0 lost sync at byte 1
[ 4338.228000] psmouse.c: issuing reconnect request
[ 5508.380000] psmouse.c: TouchPad at isa0060/serio4/input0 lost sync at byte 1
[ 5508.384000] psmouse.c: TouchPad at isa0060/serio4/input0 lost sync at byte 1
[ 5508.384000] psmouse.c: TouchPad at isa0060/serio4/input0 lost sync at byte 1
[ 5508.404000] psmouse.c: TouchPad at isa0060/serio4/input0 - driver resynched.
[ 5508.404000] psmouse.c: TouchPad at isa0060/serio4/input0 lost sync at byte 1
[ 5508.412000] psmouse.c: TouchPad at isa0060/serio4/input0 lost sync at byte 1
[ 5508.412000] psmouse.c: TouchPad at isa0060/serio4/input0 lost sync at byte 1
[ 5508.432000] psmouse.c: TouchPad at isa0060/serio4/input0 - driver resynched.
[ 5508.432000] psmouse.c: TouchPad at isa0060/serio4/input0 lost sync at byte 1
[ 5508.436000] psmouse.c: TouchPad at isa0060/serio4/input0 lost sync at byte 1
[ 5508.436000] psmouse.c: TouchPad at isa0060/serio4/input0 lost sync at byte 1
[ 5508.440000] psmouse.c: TouchPad at isa0060/serio4/input0 lost sync at byte 1
[ 5508.460000] psmouse.c: TouchPad at isa0060/serio4/input0 - driver resynched.
[ 5508.460000] psmouse.c: TouchPad at isa0060/serio4/input0 lost sync at byte 1
[ 5508.464000] psmouse.c: TouchPad at isa0060/serio4/input0 lost sync at byte 1
[ 5508.468000] psmouse.c: TouchPad at isa0060/serio4/input0 lost sync at byte 1
[ 5508.468000] psmouse.c: TouchPad at isa0060/serio4/input0 lost sync at byte 1
[ 5508.488000] psmouse.c: TouchPad at isa0060/serio4/input0 - driver resynched.
[ 5508.488000] psmouse.c: TouchPad at isa0060/serio4/input0 lost sync at byte 1
[ 5508.492000] psmouse.c: TouchPad at isa0060/serio4/input0 lost sync at byte 1
[ 5508.492000] psmouse.c: TouchPad at isa0060/serio4/input0 lost sync at byte 1
[ 5508.496000] psmouse.c: TouchPad at isa0060/serio4/input0 lost sync at byte 1
[ 5508.496000] psmouse.c: TouchPad at isa0060/serio4/input0 lost sync at byte 1
[ 5508.496000] psmouse.c: issuing reconnect request
[ 7328.628000] psmouse.c: TouchPad at isa0060/serio4/input0 lost sync at byte 1
[ 7328.632000] psmouse.c: TouchPad at isa0060/serio4/input0 lost sync at byte 1
[ 7328.632000] psmouse.c: TouchPad at isa0060/serio4/input0 lost sync at byte 1
[ 7328.652000] psmouse.c: TouchPad at isa0060/serio4/input0 - driver resynched.
[ 7328.652000] psmouse.c: TouchPad at isa0060/serio4/input0 lost sync at byte 1
[ 7328.656000] psmouse.c: TouchPad at isa0060/serio4/input0 lost sync at byte 1
[ 7328.656000] psmouse.c: TouchPad at isa0060/serio4/input0 lost sync at byte 1
[ 7328.660000] psmouse.c: TouchPad at isa0060/serio4/input0 lost sync at byte 1
[ 7328.668000] psmouse.c: TouchPad at isa0060/serio4/input0 - driver resynched.
[ 7328.688000] psmouse.c: TouchPad at isa0060/serio4/input0 lost sync at byte 4
[ 7328.688000] psmouse.c: TouchPad at isa0060/serio4/input0 lost sync at byte 1
[ 7328.692000] psmouse.c: TouchPad at isa0060/serio4/input0 lost sync at byte 1
[ 7328.692000] psmouse.c: TouchPad at isa0060/serio4/input0 lost sync at byte 1
[ 7328.692000] psmouse.c: TouchPad at isa0060/serio4/input0 lost sync at byte 1
[ 7328.692000] psmouse.c: issuing reconnect request
[ 7458.648000] psmouse.c: TouchPad at isa0060/serio4/input0 lost sync at byte 4
[ 7458.656000] psmouse.c: TouchPad at isa0060/serio4/input0 - driver resynched.
[ 7458.672000] psmouse.c: TouchPad at isa0060/serio4/input0 lost sync at byte 4
[ 7458.684000] psmouse.c: TouchPad at isa0060/serio4/input0 - driver resynched.
[ 7458.708000] psmouse.c: TouchPad at isa0060/serio4/input0 lost sync at byte 1
[ 7458.708000] psmouse.c: TouchPad at isa0060/serio4/input0 lost sync at byte 1
[ 7458.708000] psmouse.c: TouchPad at isa0060/serio4/input0 lost sync at byte 1
[ 7458.724000] psmouse.c: TouchPad at isa0060/serio4/input0 lost sync at byte 4
[ 7458.736000] psmouse.c: TouchPad at isa0060/serio4/input0 - driver resynched.
[ 7458.740000] psmouse.c: TouchPad at isa0060/serio4/input0 lost sync at byte 1
[ 7458.740000] psmouse.c: TouchPad at isa0060/serio4/input0 lost sync at byte 1
[ 7458.752000] psmouse.c: TouchPad at isa0060/serio4/input0 lost sync at byte 1
[ 7458.752000] psmouse.c: TouchPad at isa0060/serio4/input0 lost sync at byte 1
[ 7458.756000] psmouse.c: TouchPad at isa0060/serio4/input0 lost sync at byte 1
[ 7458.756000] psmouse.c: issuing reconnect request
[ 7848.704000] psmouse.c: TouchPad at isa0060/serio4/input0 lost sync at byte 1
[ 7848.708000] psmouse.c: TouchPad at isa0060/serio4/input0 lost sync at byte 1
[ 7848.712000] psmouse.c: TouchPad at isa0060/serio4/input0 lost sync at byte 1
[ 7848.728000] psmouse.c: TouchPad at isa0060/serio4/input0 - driver resynched.
[ 7848.732000] psmouse.c: TouchPad at isa0060/serio4/input0 lost sync at byte 1
[ 7848.736000] psmouse.c: TouchPad at isa0060/serio4/input0 lost sync at byte 1
[ 7848.736000] psmouse.c: TouchPad at isa0060/serio4/input0 lost sync at byte 1
[ 7848.740000] psmouse.c: TouchPad at isa0060/serio4/input0 lost sync at byte 1
[ 7848.756000] psmouse.c: TouchPad at isa0060/serio4/input0 - driver resynched.
[ 7848.764000] psmouse.c: TouchPad at isa0060/serio4/input0 lost sync at byte 1
[ 7848.764000] psmouse.c: TouchPad at isa0060/serio4/input0 lost sync at byte 1
[ 7848.764000] psmouse.c: TouchPad at isa0060/serio4/input0 lost sync at byte 1
[ 7848.784000] psmouse.c: TouchPad at isa0060/serio4/input0 - driver resynched.
[ 7848.784000] psmouse.c: TouchPad at isa0060/serio4/input0 lost sync at byte 1
[ 7848.792000] psmouse.c: TouchPad at isa0060/serio4/input0 lost sync at byte 1
[ 7848.792000] psmouse.c: TouchPad at isa0060/serio4/input0 lost sync at byte 1
[ 7848.812000] psmouse.c: TouchPad at isa0060/serio4/input0 - driver resynched.
[ 7848.812000] psmouse.c: TouchPad at isa0060/serio4/input0 lost sync at byte 1
[ 7848.820000] psmouse.c: TouchPad at isa0060/serio4/input0 lost sync at byte 1
[ 7848.820000] psmouse.c: TouchPad at isa0060/serio4/input0 lost sync at byte 1
[ 7848.840000] psmouse.c: TouchPad at isa0060/serio4/input0 - driver resynched.
[ 7848.840000] psmouse.c: TouchPad at isa0060/serio4/input0 lost sync at byte 1
[ 7848.844000] psmouse.c: TouchPad at isa0060/serio4/input0 lost sync at byte 1
[ 7848.844000] psmouse.c: TouchPad at isa0060/serio4/input0 lost sync at byte 1
[ 7848.848000] psmouse.c: TouchPad at isa0060/serio4/input0 lost sync at byte 1
[ 7848.848000] psmouse.c: TouchPad at isa0060/serio4/input0 lost sync at byte 1
[ 7848.848000] psmouse.c: issuing reconnect request
[ 7979.080000] psmouse.c: TouchPad at isa0060/serio4/input0 lost sync at byte 1
[ 7979.088000] psmouse.c: TouchPad at isa0060/serio4/input0 lost sync at byte 1
[ 7979.088000] psmouse.c: TouchPad at isa0060/serio4/input0 lost sync at byte 1
[ 7979.096000] psmouse.c: TouchPad at isa0060/serio4/input0 - driver resynched.
[ 8239.008000] psmouse.c: TouchPad at isa0060/serio4/input0 lost sync at byte 1
[ 8239.012000] psmouse.c: TouchPad at isa0060/serio4/input0 lost sync at byte 1
[ 8239.012000] psmouse.c: TouchPad at isa0060/serio4/input0 lost sync at byte 1
[ 8239.016000] psmouse.c: TouchPad at isa0060/serio4/input0 lost sync at byte 1
[ 8239.032000] psmouse.c: TouchPad at isa0060/serio4/input0 - driver resynched.
[ 8239.044000] psmouse.c: TouchPad at isa0060/serio4/input0 lost sync at byte 1
[ 8239.048000] psmouse.c: TouchPad at isa0060/serio4/input0 lost sync at byte 1
[ 8239.068000] psmouse.c: TouchPad at isa0060/serio4/input0 - driver resynched.
[ 8239.076000] psmouse.c: TouchPad at isa0060/serio4/input0 lost sync at byte 4
[ 8239.076000] psmouse.c: TouchPad at isa0060/serio4/input0 lost sync at byte 1
[ 8239.092000] psmouse.c: TouchPad at isa0060/serio4/input0 lost sync at byte 4
[ 8239.100000] psmouse.c: TouchPad at isa0060/serio4/input0 lost sync at byte 4
[ 8239.116000] psmouse.c: TouchPad at isa0060/serio4/input0 lost sync at byte 4
[ 8239.116000] psmouse.c: issuing reconnect request
[ 8369.052000] psmouse.c: TouchPad at isa0060/serio4/input0 lost sync at byte 4
[ 8369.056000] psmouse.c: TouchPad at isa0060/serio4/input0 lost sync at byte 1
[ 8369.064000] psmouse.c: TouchPad at isa0060/serio4/input0 - driver resynched.
[ 8369.080000] psmouse.c: TouchPad at isa0060/serio4/input0 lost sync at byte 4
[ 8369.084000] psmouse.c: TouchPad at isa0060/serio4/input0 lost sync at byte 1
[ 8369.092000] psmouse.c: TouchPad at isa0060/serio4/input0 - driver resynched.
[ 8369.108000] psmouse.c: TouchPad at isa0060/serio4/input0 lost sync at byte 4
[ 8369.108000] psmouse.c: TouchPad at isa0060/serio4/input0 lost sync at byte 1
[ 8369.120000] psmouse.c: TouchPad at isa0060/serio4/input0 - driver resynched.
[ 8369.132000] psmouse.c: TouchPad at isa0060/serio4/input0 lost sync at byte 4
[ 8369.136000] psmouse.c: TouchPad at isa0060/serio4/input0 lost sync at byte 1
[ 8369.136000] psmouse.c: TouchPad at isa0060/serio4/input0 lost sync at byte 1
[ 8369.140000] psmouse.c: TouchPad at isa0060/serio4/input0 lost sync at byte 1
[ 8369.140000] psmouse.c: TouchPad at isa0060/serio4/input0 lost sync at byte 1
[ 8369.140000] psmouse.c: issuing reconnect request
[ 8888.844000] psmouse.c: TouchPad at isa0060/serio4/input0 lost sync at byte 4
[ 8888.844000] psmouse.c: TouchPad at isa0060/serio4/input0 lost sync at byte 1
[ 8888.856000] psmouse.c: TouchPad at isa0060/serio4/input0 - driver resynched.
[ 8888.868000] psmouse.c: TouchPad at isa0060/serio4/input0 lost sync at byte 4
[ 8888.872000] psmouse.c: TouchPad at isa0060/serio4/input0 lost sync at byte 1
[ 8888.884000] psmouse.c: TouchPad at isa0060/serio4/input0 - driver resynched.
[ 8888.896000] psmouse.c: TouchPad at isa0060/serio4/input0 lost sync at byte 4
[ 8888.900000] psmouse.c: TouchPad at isa0060/serio4/input0 lost sync at byte 1
[ 8888.908000] psmouse.c: TouchPad at isa0060/serio4/input0 lost sync at byte 4
[ 8888.912000] psmouse.c: TouchPad at isa0060/serio4/input0 lost sync at byte 1
[ 8888.912000] psmouse.c: TouchPad at isa0060/serio4/input0 lost sync at byte 1
[ 8888.912000] psmouse.c: issuing reconnect request
[ 8890.064000] Synaptics Touchpad, model: 1, fw: 6.2, id: 0x1a0b1, caps: 0xa04713/0x200000
[ 8890.128000] input: SynPS/2 Synaptics TouchPad as /class/input/input7
[ 9468.968000] psmouse.c: TouchPad at isa0060/serio4/input0 lost sync at byte 1
[ 9468.972000] psmouse.c: TouchPad at isa0060/serio4/input0 lost sync at byte 1
[ 9468.972000] psmouse.c: TouchPad at isa0060/serio4/input0 lost sync at byte 1
[ 9468.972000] psmouse.c: TouchPad at isa0060/serio4/input0 lost sync at byte 1
[ 9468.976000] psmouse.c: TouchPad at isa0060/serio4/input0 lost sync at byte 1
[ 9468.976000] psmouse.c: issuing reconnect request
[ 9729.016000] psmouse.c: TouchPad at isa0060/serio4/input0 lost sync at byte 4
[ 9729.016000] psmouse.c: TouchPad at isa0060/serio4/input0 lost sync at byte 1
[ 9729.016000] psmouse.c: TouchPad at isa0060/serio4/input0 lost sync at byte 1
[ 9729.020000] psmouse.c: TouchPad at isa0060/serio4/input0 lost sync at byte 1
[ 9729.020000] psmouse.c: TouchPad at isa0060/serio4/input0 lost sync at byte 1
[ 9729.020000] psmouse.c: issuing reconnect request

```

---

### Post by chr1831 on 2007-10-29
anyone???, please i really need help with this.....

-Chris

---

### Post by robotsperm on 2007-10-30
Chris, I have the same issue with the lenovo C200 2fu.  So far, I haven't heard anything or gotten a response.  It seems to be a widespread issue with the polling of the mouse in Ubuntu, and it is making the Ubuntu experience almost impossible.  Some people are even thinking about switching just because of this issue, and I am afraid to admitting to being one of them! 

I hope someone takes notice of this issue and addresses it quickly!

---

