---
title: "Mouse freezes and resets"
date: 2008-06-09
forum: Hardware
---

### Post by zensuckit on 2008-06-09
Running Hardy on a Dell Latitude D630.  It has a touchpad and the little button on the keyboard to move the mouse.  Almost everytime I use my laptop, it powers on with my touchpad settings (no click on tap, vertical scroll).  After a random amount of time (seconds, minutes, hours), the mouse freezes for about 30 seconds.  Touchpad and button don't work.  I don't think the keyboard works either, but I usually can't test before it unfreezes.  Once it unfreezes, the touchpad settings are reset - it clicks on tap and doesn't scroll any more (the default settings).

I've searched these forums for a few weeks and haven't found anything.  Is this a known issue?  What logs/settings can I check?

Thanks in advance.

---

### Post by aldeby on 2008-07-29
Hi! 
I experience the very same issue on an Intel HP Pavilion: after a random amount of time the touchpad freezes for a while and then it gets resetted to default settings (tapping, no vertical scroll).

You can check your system logs (messages/syslog/etc) and I bet you will find these strings

```
 psmouse.c: TouchPad at isa0060/serio1/input0 lost synchronization, throwing 1 bytes away.
 psmouse.c: resync failed, issuing reconnect request
 Synaptics Touchpad, model: 1, fw: 6.3, id: 0x1a0b1, caps: 0xa04713/0x200000
 input: SynPS/2 Synaptics TouchPad as /devices/platform/i8042/serio1/input/input16
```

It's a very annoying issue and so far I haven't found any valid solution or workaround. 
Are Ubuntu devs addressing this issue?

---

