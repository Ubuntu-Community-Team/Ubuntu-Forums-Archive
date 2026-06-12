---
title: "PS/2 not working with 2.6.11"
date: 2005-08-23
forum: Hardware &amp; Laptops
---

### Post by NumbSkullMD on 2005-08-23
Hey all,

Love the forum. And love Ubuntu! Anyway, I installed the 2.6.11 kernel for my architecture via apt-get along with the headers and when I boot into that kernel, my mouse refuses to work. There is a light on the mouse (intellimouse explorer) that normally turns on during the 2.6.10 boot when loading modules. The same is not true with 2.6.11.  Here are the results of lsmod | grep ouse in 2.6.10:

```
psmouse                21320  0
mousedev               11288  1
```

In 2.6.11, both are loaded, but the "Used by" field for mousedev is 0, not 1. All other modules are the same. Here is the results of dmesg | grep ouse in 2.6.10:

```
mice: PS/2 mouse device common for all mice
input: ImExPS/2 Generic Explorer Mouse on isa0060/serio1
```

In 2.6.11, the "input" line is not there, but there don't appear to be any error messages.

Anyone have any thoughts?

:?

---

