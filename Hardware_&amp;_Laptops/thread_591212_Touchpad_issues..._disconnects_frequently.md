---
title: "Touchpad issues... disconnects frequently"
date: 2007-10-25
forum: Hardware &amp; Laptops
---

### Post by bcardarella on 2007-10-25
I'm running Gutsy and have an issue with my touchpad. About every 5 minutes or so the mouse will stop responding for about 10 seconds, and sometime the cursor will jump to another part of my screen. After inspecting my /var/log/messages I see this:

Oct 25 11:28:59 laptop kernel: [  948.855541] psmouse.c: TouchPad at isa0060/serio2/input0 - driver resynched.
Oct 25 11:43:55 laptop kernel: [ 1842.125723] psmouse.c: TouchPad at isa0060/serio2/input0 lost sync at byte 1
Oct 25 11:43:55 laptop kernel: [ 1842.125734] psmouse.c: issuing reconnect request

I've searched the forums here for an answer and the only solutions I've seen have to do with the module powernowd. It was suggested that I disable this module, which I did, and it made no difference.

Any thoughts on how I should go about debugging this?

---

