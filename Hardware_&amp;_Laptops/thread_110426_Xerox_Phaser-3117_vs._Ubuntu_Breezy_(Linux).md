---
title: "Xerox Phaser-3117 vs. Ubuntu Breezy (Linux)"
date: 2005-12-30
forum: Hardware &amp; Laptops
---

### Post by krisek on 2005-12-30
I succeeded to install a Xerox Phaser-3117 printer on my Breezy box. I prepared a small howto, hope it helps somebody.

[http://loliboli.hu/node/8](http://loliboli.hu/node/8)

---

### Post by drtvasudevan on 2006-06-15
wow!
at last!
:D 
i got alink to xerox phaser 3117
but the problem is things seems tohave changed a little bit with dapper.
:-( 

in short no Edit /etc/linuxprint.cfg: to edit

i hopelessly hope that you have upgraded to dapper and succeeded in etting up xerox phaser 3117

pl post new guidelines.

now after some experimenting there is a xerox 3115 printer recognised but test page does not print

tv

---

### Post by krisek on 2006-10-28
Hi,

actually this printer is connected to my parents PC; I upgraded it to Dapper in August, but I looked at the printing stuff only today. The sad thing is that there's libc incompatibility between cups (in dapper) and the drivers provided by Xerox. (Cups crashes with signal 11.)

I'll come back with the solution (if I find it)

Chris.

---

### Post by mifmif on 2006-10-29
I'm not sure if it applies to Phaser 3117 as well. However, many Phaser printers can be used and are reported to work with CUPS drivers for Samsung ML printers (I think they are interally identical). You can used the driver which comes with your Ubuntu distribution.

I have Phaser 3116 which can be used with the CUPS driver for ML-1210; it works perfectly.

In addition to this, useful information can be found in the LinuxPrinting.org discussion:

[http://lists.freestandards.org/pipermail/printing-user-xerox/](http://lists.freestandards.org/pipermail/printing-user-xerox/)

M.

---

### Post by krisek on 2006-11-04
It applies. It works well, at least the test page is printed correctly :).
Thanks a lot for the tip!

k-

---

