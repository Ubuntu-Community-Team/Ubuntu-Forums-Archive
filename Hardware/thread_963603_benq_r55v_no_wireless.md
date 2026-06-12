---
title: "benq r55v no wireless"
date: 2008-10-30
forum: Hardware
---

### Post by elleander on 2008-10-30
Hello,
I have benq r55v and i use it for some time with ubuntu and i have upgraded my ubuntu to 8.10 and now i have a problem. actualny i can't get my wireless card online.
After i push my wireless on button i get this info:
```

# dmesg -c
[ 1767.954309] atkbd.c: Unknown key pressed (translated set 2, code 0xe1 on isa0060/serio0).
[ 1767.954325] atkbd.c: Use 'setkeycodes e061 <keycode>' to make it known.
[ 1768.134446] atkbd.c: Unknown key released (translated set 2, code 0xe1 on isa0060/serio0).
[ 1768.134465] atkbd.c: Use 'setkeycodes e061 <keycode>' to make it known.

```

When i tried to modprobe iwl3945, my wireless card module, nothing 
happened.
```
# ifconfig wlan0 up
SIOCSIFFLAGS: No such device
```

---

