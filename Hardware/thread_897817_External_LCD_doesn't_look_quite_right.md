---
title: "External LCD doesn't look quite right"
date: 2008-08-22
forum: Hardware
---

### Post by ludicrous on 2008-08-22
I'm using a Samsung SyncMaster 2053bw with my laptop, which has a geforce Go 7400. It's working fine, but doesn't look quite as sharp as it should. It's mostly noticeable in text, just a little blurry. I don't notice this with Windows, and it's even more noticeable when I compare the image on my laptop display to the external monitor. Any suggestions?

---

### Post by cariboo on 2008-08-22
Have you changed the font at all? Go to System-->Preferences-->Appearance-->Fonts and make sure Subpixel Smoothing is selected and then click the details button and make your selections for the best look.

Jim

---

### Post by ludicrous on 2008-08-22
Yeah, I did. I'm thinking it may just be the fact that I'm using a VGA connection for the external display the the laptop display has a digital connection.

---

### Post by JedV on 2008-08-26
I just bought this monitor, Ubuntu keeps detecting it as 1600 x 1024 (instead of the native resolution of 1680 x 1050).  That's what's causing the not so sharp text.

I think that I'll need to edit the xorg.conf file.

---

### Post by JedV on 2008-08-26
Right on, reconfiguring the xorg.conf file did the trick.

```
sudo dpkg-reconfigure xserver-xorg
```

---

