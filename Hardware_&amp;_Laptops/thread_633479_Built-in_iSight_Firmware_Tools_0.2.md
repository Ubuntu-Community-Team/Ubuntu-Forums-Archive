---
title: "Built-in iSight Firmware Tools 0.2"
date: 2007-12-06
forum: Hardware &amp; Laptops
---

### Post by bersace on 2007-12-06
Hi,

I guess that most of you owners of Mactel with built-in isight have use the extract tool from Ronald S. Bultje. Since Ronald switched back to OS X, the code was unmaintained. So, i forked it in order to improve it.

So, the news :

[LIST]
[*]Properly create a project using autotools.
[*]Splitted extract into ift-extract and ift-load
[*]Added Mac OS X.4 PPC driver support
[/LIST]

All is available at [http://bersace03.free.fr/ift/](http://bersace03.free.fr/ift/)

Regards,
Étienne.

---

### Post by bersace on 2007-12-07
Hi,

I updated the tools and the patch against linux-uvc. So, here are the overall changes :

[LIST]
[*]Proper firmware extraction and patching in userspace
[*]Proper firmware loading in userspace (udev rules)
[*]Cleaner patch (no kernelspace firmware extraction nor loading)
[*]Port to powerpc
[*]Port to linux 2.6.24
[*]Misc : migrate to autotools, i18n, website, etc.
[/LIST]

[http://bersace03.free.fr/ift](http://bersace03.free.fr/ift)

Regards,
Étienne

---

