---
title: "Installing Languages"
date: 2009-09-29
forum: Installation &amp; Upgrades
---

### Post by jtrulen on 2009-09-29
Hello everyone,

I am trying to install a font type onto my Ubuntu box, but I have no idea where to begin.

Could someone enlighten me as to how to accomplish this?

Thank you,

Jordan

---

### Post by p2bc on 2009-09-29
Any font that you have the rights to (i.e. paid for) you can dump in "/usr/share/fonts/"

If it is a True Type Font (.ttf) you can put it in "/usr/share/fonts/truetype/" and you will be able to access it from any app in Linux, like OpenOffice or Gimp and so on.

You can also install MS fonts by:
```

sudo apt-get install msttcorefonts cabextract

```

Please be advise you do it at your own risk, base of the laws and rights in your country or region. You will also have to enable some repositories in you "/etc/apt/sources.list" file

Again at your own risk.

---

### Post by jtrulen on 2009-09-29
Thank you much p2bc.

---

