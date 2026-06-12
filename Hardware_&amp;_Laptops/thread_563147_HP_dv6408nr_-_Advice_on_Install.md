---
title: "HP dv6408nr - Advice on Install?"
date: 2007-09-29
forum: Hardware &amp; Laptops
---

### Post by anthonyvinciguerra on 2007-09-29
Hi All - 

Recently got an HP dv6408nr laptop - with the hopes of trying out ubuntu... But I've tried using the 7.04 live disk and after beginning to boot up the screen eventually just goes blank... and nothing.

Any advice? I'd love to try to use Ubuntu - but I might just return it while I can, and wait until this all gets easier...

system specs -
AND Turionx64  TL-56
NVidea GeForce Go 6150
2 Gig RAM

Thanks!

-Anthony

---

### Post by jpyanowski on 2007-09-29
Have you checked the ISO file on the CD? That could be bad.

---

### Post by anthonyvinciguerra on 2007-09-29
Yup - In fact I also downloaded (checked the md5sums, burned to cd etc) - kubuntu as well... the disks worked in another laptop, but I get the same blank screen on the dv6408nr... Advice?

---

### Post by davidph on 2008-01-01
Have you followed the directions in the wiki.
I have some success on both my dv6000z and dv6408nr laptops with this. 
[https://wiki.ubuntu.com/hp_dv6000_series_(dv6116eu](https://wiki.ubuntu.com/hp_dv6000_series_(dv6116eu))

I have been using (Hardy Heron) Alpha 2 recently but have used earlier versions as well and debian testing and unstable on them. The greatest problem I have have had is getting wifi to work reliably. 

(Hardy Heron) Alpha 2
[http://cdimage.ubuntu.com/kubuntu/releases/hardy/alpha-2/hardy-desktop-amd64.iso](http://cdimage.ubuntu.com/kubuntu/releases/hardy/alpha-2/hardy-desktop-amd64.iso)

---

### Post by mett on 2008-01-31
When the menu appears to "Start disc, boot from hard exist, install" etc. Try pushing F6. A string of commands should appear at the bottom with the ending looking something like:

splash --

Type noapic in between the splash and the -- so it'll look like this

splash noapic--

and then press enter.

---

