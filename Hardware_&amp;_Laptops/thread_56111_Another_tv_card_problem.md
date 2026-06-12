---
title: "Another tv card problem"
date: 2005-08-11
forum: Hardware &amp; Laptops
---

### Post by m477 on 2005-08-11
Hey guys,

I've run my tv card in Ubuntu before, but only from a base system install, and using xfree, and not xorg, so it seems to be differant.

**lspci output:** 
0000:02:0a.0 Multimedia video controller: Brooktree Corporation Bt878 Video Capture (rev 02)
0000:02:0a.1 Multimedia controller: Brooktree Corporation: Unknown device 0078 (rev 02)

**lsmod output:** 
root@bender:~# lsmod
Module                  Size  Used by
bt878                  10552  0

I'm using xawtv and, when running scantv, I get the following error:
[b]vbi: open failed [/dev/vbi]
open /dev/vbi: No such file or directory
[/b]

Any ideas on what I should do to get it running? I'm aware that I should add something to my modules, but not exactly sure how or what. I've tried forcing scantv to /dev/video0 instead of /dev/vbi, but to no avail.

---

### Post by m477 on 2005-08-11
Ah, got it, nevermind.

---

### Post by costoa on 2005-08-11
It's not an answer to your question but I happily use tvtime.

---

### Post by m477 on 2005-08-11
[QUOTE=costoa]It's not an answer to your question but I happily use tvtime.[/QUOTE]

tvtime's great, have you figured out a way to stream it across networks yet? Because that'd be helpful too :P

---

