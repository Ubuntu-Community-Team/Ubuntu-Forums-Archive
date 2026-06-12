---
title: "Cannot Get Sound Default device to change need help asap!"
date: 2005-04-23
forum: Hardware &amp; Laptops
---

### Post by nightshrill on 2005-04-23
I am new to Ubuntu linux and gnome as a whole (i've used xandros and mandriva both with KDE in the past). I have onboard audio provided by my motherboard and a soundblaster Audigy LS. I cannot get alsa or esound to recognize my soundblaster and switch to it as to be the default device. I have gone into the device manager and Ubuntu does recognize the soundblaster but will not allow me to edit any of the options. I would really like to get my audio to work, so please assist me.

---

### Post by Nis on 2005-04-24
```

sudo gedit /etc/esound/esd.conf

```
Change
```

spawn_options=-terminate -nobeeps -as 5

```
to
```

spawn_options=-terminate -nobeeps -as 5 -d /dev/dsp2

```
Log out and log back in.

---

