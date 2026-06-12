---
title: "xorg.conf"
date: 2010-12-05
forum: Hardware
---

### Post by azedddine on 2010-12-05
hello,

i use ubuntu in acer aspire one D255, with intel 3510 as graphic card, i can't find xorg.conf file, how can generate that file?

thank you

---

### Post by sikander3786 on 2010-12-05
Unless the graphics are not working properly, you might not need that. Modern X deals directly with all the graphics stuff ;-)

If you still want to generate it, this might do it.

```
sudo dpkg-reconfigure -phigh xserver-xorg
```

Or in case of Nvidia drivers,

```
sudo nvidia-xconfig
```

---

### Post by IcarusR on 2010-12-05
You can not find xorg.conf because, as sikander3786 says  xorg no longer uses it. 
However you can create one & it will be used.

I think you have to reconfigure xorg with x not running as here

[http://www.osguides.net/operation-systems/217-how-to-create-xorgconf-in-ubuntu-910.html]("http://www.osguides.net/operation-systems/217-how-to-create-xorgconf-in-ubuntu-910.html")

---

