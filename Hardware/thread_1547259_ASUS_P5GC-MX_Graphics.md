---
title: "ASUS P5GC-MX Graphics"
date: 2010-08-06
forum: Hardware
---

### Post by cpressland on 2010-08-06
Hey Guys,

I've convinced my boss to install Ubuntu on one of his desktop machines which is running with an asus p5gc-mx with integrated 945G Graphics (GMA 950) but Ubuntu doesn't seam to have detected the graphics chipset properly and is only offering up 800x600 as a resolution.

Any ideas? (noob responses please)

Thanks

Chris

---

### Post by utilitytrack on 2010-08-06
Hello, please pass my greetings to your boss :)

Linux has good support of Intel 945G chipset, with respect to GMA950 graphics it's ensure by **xserver-xorg-video-intel** package. Do you sure that you have last version? Check on [http://intellinuxgraphics.org/2010Q2.html]("http://intellinuxgraphics.org/2010Q2.html") Also may be your Xserver need a modified [FONT="Courier New"]/etc/X11/xorg.conf[/FONT] file? Post it here if it exist.

---

