---
title: "X800XL driver problem"
date: 2009-07-23
forum: Installation &amp; Upgrades
---

### Post by extibo on 2009-07-23
Hello guys & girls.

First of all, I'm just amazed with Ubuntu. Speed, reliability, inferface (:o)... Awesome.

So here's the problem - I can't install ATi X800XL drivers. I've downloaded them from AMD website, but there's an error. It's about characted encoding (see the screenshot below).

[IMG]http://img268.imageshack.us/i/59692075.png/[/IMG][IMG]http://img268.imageshack.us/i/59692075.png/[/IMG][http://img268.imageshack.us/i/59692075.png/](http://img268.imageshack.us/i/59692075.png/) (grrr, insert image doesn't work)

Yes, I tried to change character coding. No results however.

I've recently managed to play World of Warcraft from Linux, with Wine ofcourse. But when I enter WoW, FPS is so low, like 1-2. I think it's because the drivers are outdated.

Every suggestion is appreciated. :D

---

### Post by Mark Phelps on 2009-07-23
I didn't catch what version of Ubuntu you're running, but if it's 9.04, there are no AMD/ATI restricted drivers for your card that will work with 9.04, so don't try to force an install or you'll be left with a black screen and a blinking cursor.

---

### Post by extibo on 2009-07-23
> **Mark Phelps said:**
> I didn't catch what version of Ubuntu you're running, but if it's 9.04, there are no AMD/ATI restricted drivers for your card that will work with 9.04, so don't try to force an install or you'll be left with a black screen and a blinking cursor.

I've downloaded these drivers - [http://support.amd.com/us/gpudownload/linux/Legacy/Pages/radeon_linux.aspx?type=2.4.1&product=2.4.1.3.17&lang=English](http://support.amd.com/us/gpudownload/linux/Legacy/Pages/radeon_linux.aspx?type=2.4.1&product=2.4.1.3.17&lang=English).

---

### Post by Mark Phelps on 2009-07-23
AMD/ATI dropped support for your card, and lots of others, in their new drivers.  The old drivers, the ones that WILL work with your card, will not work with the Xserver in Ubuntu 9.04. You have NO CHOICE other than to use the open source drivers -- which are installed by default.

It doesn't matter what you download, it won't work -- which is why I said "there are no AMD/ATI restricted drivers for your card that will work with 9.04".

---

