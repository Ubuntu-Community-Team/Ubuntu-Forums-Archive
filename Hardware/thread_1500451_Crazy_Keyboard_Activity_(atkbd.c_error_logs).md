---
title: "Crazy Keyboard Activity (atkbd.c error logs)"
date: 2010-06-03
forum: Hardware
---

### Post by rookcifer on 2010-06-03
I have noticed that lately my keyboard has a mind of its own.  Often I will be typing something and suddenly I lose control of the keyboard -- it will begin scrolling random characters or start printing the same character for many lines or scrolling multiple characters.  Sometimes I will be typing and it will delete the line I just wrote or just add a lot of whitespaces uncontrollably on the screen, etc.

Needless to say, this is a major PITA.  I do have an old keyboard but I am reluctant to chalk it up to that as I am getting error messages in /var/log/messages and syslog.  The messages look like this:

```

Jun  3 04:53:03 blackline kernel: [ 1477.641090] atkbd.c: Unknown key released (translated set 2, code 0x5b on isa0060/serio0).
Jun  3 04:53:03 blackline kernel: [ 1477.641093] atkbd.c: Use 'setkeycodes 5b <keycode>' to make it known.
Jun  3 04:59:03 blackline kernel: [ 1837.451865] atkbd.c: Spurious NAK on isa0060/serio0. Some program might be trying access hardware directly.
Jun  3 04:59:05 blackline kernel: [ 1839.970259] atkbd.c: Spurious NAK on isa0060/serio0. Some program might be trying access hardware directly.
Jun  3 04:59:06 blackline kernel: [ 1840.170950] atkbd.c: Spurious NAK on isa0060/serio0. Some program might be trying access hardware directly.
```

I have Googled and every report of these error messages I have seen was related to either a laptop or a wireless keyboard.  I am using a **wired** keyboard through a standard PS/2 port on a standard desktop PC.

Anyone have any idea what is going on inside atkbd.c?

---

