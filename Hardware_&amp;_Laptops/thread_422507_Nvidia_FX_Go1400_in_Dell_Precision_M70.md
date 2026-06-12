---
title: "Nvidia FX Go1400 in Dell Precision M70"
date: 2007-04-25
forum: Hardware &amp; Laptops
---

### Post by markfc on 2007-04-25
Hi,

I've just installed Ubuntu 7.04 for the first time.

Please could someone take the time to explain to a complete newbie, how to get Nvidia drivers for this graphics card installed.

At the moment I'm stuck with 800 by 600 and 1024 by 768.

Many Thanks

Mark

---

### Post by renzokuken on 2007-04-25
in feisty the easy way is to go

System -> Administration -> Restricted Drivers Manager and use the wizard.

alternatively, you could use the Envy script ( [www.albertomilone.com](www.albertomilone.com) )

---

### Post by markfc on 2007-04-25
Cool, ok.

I've enabled the driver and 3d support works now but I can only get 1024x768 resolution and this laptop does 1920 x 1200.

Do I need a monitor driver?

Thanks

---

### Post by renzokuken on 2007-04-25
go to the terminal and run

```
sudo dpkg-reconfigure xserver-xorg
```

leave every option as it is and just add the resolutions you want at the appropriate section, then continue just selecting the defaults.

restart and then the new resolutions should be available

---

