---
title: "Thinkpad X41T: New kernel kills wacom resume after suspend"
date: 2007-06-03
forum: Hardware &amp; Laptops
---

### Post by jgordon510 on 2007-06-03
I installed feisty on my thinkpad tablet with kernel 2.6.20-15-generic.  I followed the instructions on the [URL="http://www.google.com/url?sa=t&ct=res&cd=1&url=http%3A%2F%2Fwww.thinkwiki.org%2Fwiki%2FInstalling_Ubuntu_6.10_on_a_ThinkPad_X41_Tablet&ei=QRxjRo-DF5nagQPazvXkBg&usg=AFQjCNFrFZgN2On2bRQACCfXVIgXi5QZdg&sig2=FdyD2kREI5DKOZRKI_sZkA"]thinkpad wiki
[/URL] and got everything working including suspend with wacom support.  The key to getting resume for the wacom was putting this line:

```
/bin/setserial /dev/ttyS0 port 0x0200 irq 5 autoconfig
```

into an acpi resume script.  Life was good.

Then I updated the kernel to 2.6.20-16 and resume kills wacom.  The script is still there.  If I run the command manually, I still don't get wacom.  If I try booting into the old kernel, my atheros wireless no longer works.

UPDATE:
On a whim, I tried adding the lowlatency kernel from the ubuntustudio package and that one doesn't seem to be giving me the same problem.

---

