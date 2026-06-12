---
title: "Fix Darter Backlight Buttons"
date: 2007-04-22
forum: Hardware &amp; Laptops
---

### Post by QuinnStorm on 2007-04-22
The Darter is a wonderful machine, but as shipped it has a few little bugs, one being the backlight buttons on the keyboard do nothing.  This is a simple fix on Feisty (untested on Edgy), and easy for even the amateur.

Just download the attached file and run:
```

gunzip *filename.gz*
sudo cp *filename* /etc/initramfs-tools/DSDT.aml
sudo update-initramfs -u

```

Then reboot...its that simple.

Good luck!

---

