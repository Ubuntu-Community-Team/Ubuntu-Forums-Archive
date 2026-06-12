---
title: "Dell Wireless Fn Key Doesn't Work"
date: 2007-07-20
forum: Hardware &amp; Laptops
---

### Post by Ashly on 2007-07-20
Hi there. Ubuntu forums newbie here, sorry if this is the wrong area.

My problem: I recently bought a Dell Inspiron 6400. I did the research, and figured the *Intel Corporation PRO/Wireless 3945ABG* device would work. The thing I wasn't counting on was the wireless kill switch being a function key combo.

Anyway, a friend had experience with an older version of Ubuntu on a similar laptop, and reports the function keys work fine. Sadly, when I press the Fn+F2 combo, the wireless light doesn't light up, and an error is written to dmesg:

```
[12497.072000] atkbd.c: Unknown key pressed (translated set 2, code 0x88 on isa0060/serio0).
[12497.072000] atkbd.c: Use 'setkeycodes e008 <keycode>' to make it known.
```

The wireless device is permanently disabled, and I can't work out how to enable it. Any help would be appreciated; I'm one too few wired ports on my switch. :-)

Edit:
I just found a <a href="https://bugs.launchpad.net/ubuntu/+source/hotkey-setup/+bug/92090">Launchpad bug</a>. It's really old, and doesn't help me any. Does anyone know how to disable the kill switch?

---

### Post by Ashly on 2007-07-21
For anyone who is interested, I found a solution to my problem. I booted the Ubuntu live CD and found that the wireless hotkeys were working there.

Since I installed gnome-desktop, and the generic kernel from an Ubuntu Server disc, this leads me to conclude that there was either a misconfiguration or something not installed that was supposed to take care of the wireless hotkey on my hard drive install.

After some minimal backups and a reinstall from the "desktop" disc, it's all working peachy.

---

