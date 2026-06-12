---
title: "VPC 2004 Sound Support"
date: 2004-10-20
forum: Hardware &amp; Laptops
---

### Post by babcocca on 2004-10-20
I have everything else working. The previous post about the networking was an error on my part. I've been working hard on getting sound working. Can anyone help?

Its an emulated SB16 ISAPnP

modprobe snd-sb16
modprobe snd-sb16-dsp

does not work

EDIT: [http://lkml.org/lkml/2004/5/24/164](http://lkml.org/lkml/2004/5/24/164)

Can we get this rolling? I have no idea how to implement this.

Devs?

---

### Post by RichNRockville on 2004-10-20
[quote=babcocca]I have everything else working. The previous post about the networking was an error on my part. I've been working hard on getting sound working. Can anyone help?

Its an emulated SB16 ISAPnP

modprobe snd-sb16
modprobe snd-sb16-dsp

does not work[/quote]

I have the same problem in vpc 2004, even with sp1.

I get an error alsact1 failed  load state 1134

also, I can't seem to get my printer working on a linksys print server. I know the IP and name but can't seem to do anything. Printing just never goes.
still in que but not printing..

---

