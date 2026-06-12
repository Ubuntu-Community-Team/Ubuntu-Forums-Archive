---
title: "file copy/moving speed"
date: 2009-06-13
forum: Hardware
---

### Post by ngsupb on 2009-06-13
Hi,

I found a weird thing. 
Is something wrong here?

I get about 1.6 MB/s when I copy a large file over 500Mb file size. I doesn't meter if I copy over network, or just use cp or just through nautilus somewhere.


In case I copy small files the speed as good as it is supposed to be.
Do you have any ideas what is wrong?


hdparm -t /dev/sda
/dev/sda:
 Timing buffered disk reads:  124 MB in  3.04 seconds =  40.74 MB/sec

But why 1.5-1.6MB only for large files?

---

### Post by ActiveFrost on 2009-06-13
Haven't seen my speed going over 2Mb/s ( on 3 PC's ), so - I would say, it's ok to have such a "speed" :)

---

### Post by H2SO_four on 2009-06-13
disk to disk I get about 10 MB/s, however over network I get much lower, around 1.5 Mb

---

### Post by ngsupb on 2009-06-13
but at least it should be fine if I copy a large file from one place to another on the same hdd? 1.6 - 2.0MB too low.

Even for a network card (100mb) there should be about 8-9 MB.


Just tested by copying small files, 
it is around 10MB/s by copying files from one location to another.
and 1.6MB/s for a large file ~600MB

It is wrong :(

---

### Post by ngsupb on 2009-06-14
it is a bug:(

[https://bugs.launchpad.net/ubuntu/+source/linux/+bug/119730?comments=all](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/119730?comments=all)

---

