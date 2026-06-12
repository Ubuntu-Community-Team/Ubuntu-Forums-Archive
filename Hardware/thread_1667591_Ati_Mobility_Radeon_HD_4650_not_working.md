---
title: "Ati Mobility Radeon HD 4650 not working"
date: 2011-01-15
forum: Hardware
---

### Post by CharlieK83 on 2011-01-15
Hi I have a Acer Aspire 8530G with Maverick installed, and i can't seem to get the high performance GPU working.
Here's the output for lspci -nn
```
01:05.0 VGA compatible controller [0300]: ATI Technologies Inc RS780M/RS780MN [Radeon HD 3200 Graphics] [1002:9612]
02:00.0 VGA compatible controller [0300]: ATI Technologies Inc M96 [Mobility Radeon HD 4650] [1002:9480] (rev ff)
```

I understand that switching on the fly is not supported yet, but how do i go about, if i want to at least get the HD 4650 Controller working on boot when adding BusID 2:0:0 to xorg.conf i only get a blank screen

please help...

---

