---
title: "[printing] High speed print &amp; advanced setup"
date: 2007-03-06
forum: Hardware &amp; Laptops
---

### Post by f3ua on 2007-03-06
Hi all!

I've got a little problem setting up my HP PSC 2175 all in one, on ubuntu 6.10. The printer & scanner works well, but in windows I can modify the quality of the print. There is an option called "high speed" that reduces a lot of quality (preview print), but prints at lightspeed and save lots of ink.

How can i get the same result? I repeat, I don't want quality but speed, if possible.

Thanks

---

### Post by seldenthuis on 2007-03-06
Try using the hp-toolbox program. It's a HP device manager with a GUI and it has print quality options.

If it complains that there are no printers installed you could try
```

sudo apt-get install hpijs-ppd hplip-doc
sudo hp-setup

```
and then follow the instructions on the screen. This will reconfigure the printer so you can use it with the HPLIP tools.

---

