---
title: "thinkpad T510 graphics driver"
date: 2010-02-13
forum: Hardware
---

### Post by linux_noob0 on 2010-02-13
hey there. i got a lenovo thinkpad t510, and it's graphics card - nvidia quadro nvs31000M is not listed on nvidia's site. how do i get the proper drivers for it? or is it not supported yet? thanks!

---

### Post by peepingtom on 2010-02-26
It works with nVidia proprietary drivers under Lucid and probably Karmic too. VDPAU works.

I can't get Lucid Alpha 3 to properly boot with Nouveau drivers. All I get is a blank screen from the point where Plymouth loads.

---

### Post by peepingtom on 2010-03-10
The machine now boots to an X server, but the screen is blank while plymouth loads. adding th following to "Devices" section of xorg.conf will allow you to control the backlight while using nVidia proprietary drivers:
Option "RegistryDwords" "EnableBrightnessControl=1"

---

