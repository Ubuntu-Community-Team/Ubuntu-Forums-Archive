---
title: "Headset Mic not detected (SONY  MDRZX770BN)"
date: 2020-07-06
forum: Hardware
---

### Post by gabbello on 2020-07-06
Hello, 

I have a headset (SONY  MDRZX770BN) for which the MIc is not detected  when I plug in the jack into a lenovo ideapad 500S laptop. Please see  below screenshot from sound settings




```
 cat /proc/asound/card*/codec* | grep Codec
Codec: Realtek ALC236
Codec: Intel Skylake HDMI

```

Pavucontrol also reports this as unplugged as well.



I did try using hdajackretask, but I get error "Device or resource busy".

Also, I don't know what module I could add from here: [https://www.kernel.org/doc/html/latest/sound/hd-audio/models.html](https://www.kernel.org/doc/html/latest/sound/hd-audio/models.html) to /etc/modprobe.d/alsa-base.conf

---

### Post by slickymaster on 2020-07-06
*Thread moved to **Hardware**.*

---

### Post by gabbello on 2020-07-08
Update, it seems that Sony sells this headset with jack cable of type TRS (and not TRRS), which basically makes it impossible to use Mic on Jack for this model with the original cable

---

