---
title: "Wireless LED on Dell Ins 6000"
date: 2005-11-14
forum: Hardware &amp; Laptops
---

### Post by lee_connell on 2005-11-14
My wireless LED doesn't come on like it does in windows.  not a big deal but just interested if there is a way to get it to come on.

It is not related to the function keys turning it on or off.  Is there anyway I can have it come on when wireless is on?

Thanks.

---

### Post by Delvien on 2005-11-14
This actually seems to be a bug , no one has really spent the time to get it to turn on, i have a i6000d as well, doesnt work for me in kubuntu either.

---

### Post by GoodPanos on 2005-11-15
Yeah it would be nice to be able to turn on the wireless light on.  It's thrown me off a few times thinking that the wireless was on but not.

---

### Post by crichell on 2005-12-09
Give this How To a try.  Works on our notebooks.

[http://system76.com/knowledge/index.php/Wireless_LED_on_Ubuntu](http://system76.com/knowledge/index.php/Wireless_LED_on_Ubuntu)

---

### Post by jhnphm on 2005-12-10
Put "ipw2200 led=1 hwcrypto=0" in /etc/modules

The 2nd parameter fixes WPA dropouts.

---

### Post by er-ku on 2005-12-10
[QUOTE=lee_connell]My wireless LED doesn't come on like it does in windows.  not a big deal but just interested if there is a way to get it to come on.

It is not related to the function keys turning it on or off.  Is there anyway I can have it come on when wireless is on?

Thanks.[/QUOTE]

Try this (in a terminal):
```

sudo -s
echo "options ipw2200 led=1" >> /etc/modprobe.d/ipw2200.modprobe
rmmod ipw2200
modprobe ipw2200
exit

```

if rmmod and/or modprobe tells you about errors, don't worry. This most probably means that you're using your wireless device, so its module cannot be unloaded. In this case, simply reboot your computer instead.

---

