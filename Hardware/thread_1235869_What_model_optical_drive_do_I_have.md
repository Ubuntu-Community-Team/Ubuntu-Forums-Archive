---
title: "What model optical drive do I have?"
date: 2009-08-09
forum: Hardware
---

### Post by Psychic Saw on 2009-08-09
Hi,

I was just wondering, how do I find out what model optical drive I have? I searched online and can't seem to find how to do it on Ubuntu.

---

### Post by sergiom99 on 2009-08-09
in a terminal type:
```
$ sudo lshw -C disk
```
and will you the available data.

Alternative if you have cdrecod installed:
```
$ cdrecord --scanbus
```

Good luck!

---

