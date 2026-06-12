---
title: "Jaunty teething problems......help!"
date: 2009-05-01
forum: Installation &amp; Upgrades
---

### Post by dan1973 on 2009-05-01
Hello all,

Have just updated my wubi installed version of intrepid to jaunty and as a consequence am experiencing a few problems.

The most pressing one is that every time it boots up, it gets about a third of the way through the 'graphical bar' on the loading screen, then stops a while, then reverts to text display. There is an error present here along the lines of the following:

```
/etc/rcS.d/s25brltty: 21: md5sum not found
```

The start-up then stops at this point. The keyboard works to type but there is no command prompt available.

I then ctrl-alt-del which gives the message:

```
[CODE]
```rc5 killed
rc6 killed
```

```[/CODE]
and then jaunty gives the log-in screen and all goes well from there on.

When I had completed upgrading there was the following problem given:

```
[CODE]
```E: /var/cache/apt/archives/memtest86+_2.11-3ubuntu1_i386.deb: unable to make backup link of `./boot/memtest86+.bin' before installing new version ```

```[/CODE]

Not sure how relevant this is but thought i'd mention it.

Please can anyone help?

---

### Post by dan1973 on 2009-05-01
Anyone..?

---

