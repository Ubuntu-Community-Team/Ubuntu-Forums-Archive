---
title: "Mail led stuck blinking after hibernate"
date: 2009-11-05
forum: Hardware
---

### Post by Tort on 2009-11-05
Hi, just installed 9.10 on my Acer Aspire 5630. After hibernating for the first time my mail button led has been flashing.

To be honest, I never knew there was an led in there. Would be fantastic if I could configure it to flash on new mails in Evolution but I really need help turning it off. The flashing is really distracting

I'm not scared of the terminal, does anyone know what conf file I need to change to access it? (I don't have any special acer driver packs installed, fresh 9.10 install)

Thanks

---

### Post by d7415 on 2009-11-13
Mine did the same thing today. I'm not sure about the long term, but I stopped mine by playing with the control file here:
/sys/devices/platform/acer-wmi/leds/acer-wmi::mail/brightness

It's root-owned 644 by default, and for me seemed to contain "0" (off state). I set it and unset it and it seemed to go off.

Sorry I can't be more useful, but I played for a while and I can't quite remember what stopped it. If it happens again I'll try to get a clearer/better answer.

---

### Post by Tort on 2009-11-14
Cool thanks, what do I need to do to unset it. Set it to 1 or null or blank?

---

### Post by d7415 on 2009-11-14
As I said, I can't remember exactly. 0 is the off state, but mine started like that. Maybe:

```
sudo -s
echo 1 > /sys/devices/platform/acer-wmi/leds/acer-wmi::mail/brightness
echo 0 > /sys/devices/platform/acer-wmi/leds/acer-wmi::mail/brightness
exit
```

If it comes up again, I'll see if I can do better for you.

Let me know if it works!

---

### Post by CDrewing on 2009-11-26
Had the same problem here!

Setting it to "1" and then again to "0" will help. I really hate these papercuts. You learn a lot of things about your OS but you lose a lot of time, too.

---

