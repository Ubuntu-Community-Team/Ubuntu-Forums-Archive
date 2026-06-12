---
title: "SATA drives give errors and prevent booting"
date: 2007-08-31
forum: Hardware &amp; Laptops
---

### Post by Unholy Moley on 2007-08-31
I have a few hard drives that I converted to SATA using an SATA adapter. They fine in Windows, they works fine in Knoppix, but if I try to use Ubuntu I get errors like:

ata1.00: failed to set xfermode (err_mask=0x40)

I read some suggestions online about adding irqpoll to menu.lst, so I did and now I get this error:

Exception emask 0x0 SAct 0x0 SErr 0x0 action 0x2 frozen
cmd c8/00:08:00:00:00/00:00:00:00:00/e0 tag 0 cdb 0x0 data 4096 in

---

### Post by Unholy Moley on 2007-09-07
Anyone :|

---

### Post by SveinT on 2007-10-16
Do you know what sata chipset is used?

You might be interested in this bug:
[https://bugs.launchpad.net/ubuntu/+source/linux-source-2.6.22/+bug/153096](https://bugs.launchpad.net/ubuntu/+source/linux-source-2.6.22/+bug/153096)

---

### Post by Ux64 on 2007-11-11
Sorry, I don't have knowledge how to fix this. But... 

I'm suffering from same problem. Strangest thing is that if I reboot it usually doesn't reappear. Which is really strange. Maybe hardware fault(?).

[[IMG]http://picozilla.com/files/141839timgp0878.jpeg[/IMG]](http://picozilla.com/en/141839/imgp0878.jpeg.html)

---

