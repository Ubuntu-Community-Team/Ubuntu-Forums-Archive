---
title: "Scanner not working, how to use older version of SANE?"
date: 2006-01-30
forum: Hardware &amp; Laptops
---

### Post by yetanothersteve on 2006-01-30
Under Hoary and now under Breezy my Acer / Benq 310u USB scanner does not function correctly. I think it has something to do with the newer SANE libraries as Suse 10 also has the problem.

[My original Hoary post on this.]("http://www.ubuntuforums.org/showthread.php?t=54495")

Solutions:
1. Boot into Suse 9.2 when I need to use the scanner. Inelegant, but it works. Because this is now my only use for Suse 9.2, this is clumsy.
2. I noticed that Qemu now supports using host usb devices. [I can now scan from Suse 9.1 without leaving Ubuntu.]("http://coding.home.comcast.net/ubu_suse.jpg") Goofy, but it works.
3. Roll back libsane to 1.0.13 or 1.0.14, I think 1.0.15 is the problem. Gotcha! Removing libsane will cause Ubuntu-Desktop to be removed.

After much digression, this brings me back to the topic of my post, how do I remove libsane 1.0.15 without removing the Ubuntu-desktop.

Could I build my own deb from the 1.0.14 source and install it or find the deb from an older version of Ubuntu and install it?

As you can tell by my option 2, I am fairly open to any ideas and work arounds  of which anyone can think.

---

### Post by yetanothersteve on 2006-02-02
Fixed it myself. The problem is in the sane source in /backend/snapscan.h

Incorrect:
```
/* Acer product IDs */
#define USB_PRODUCT_PRISA310 0x12a0
```

Correct:
```

/* Acer product IDs */
#define USB_PRODUCT_PRISA310 0x1a20
```

So, I posted it to the bug tracker:
[http://alioth.debian.org/tracker/index.php?func=detail&aid=302983&group_id=30186&atid=410366]("http://alioth.debian.org/tracker/index.php?func=detail&aid=302983&group_id=30186&atid=410366")

And then I installed both the latest sane and xsane sources via checkinstall:

```

sudo apt-get install checkinstall
./configure
make
sudo checkinstall
```

checkinstall is an excellent replacement for "make install" when using source code because it creates a deb that it installs and that can be managed via apt or synaptic.

xsane and scanning now work from Breezy. I can delete Suse 9.2. :D Happiness is a "pure" Ubuntu box.

---

