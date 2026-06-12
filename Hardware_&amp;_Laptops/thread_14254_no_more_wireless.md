---
title: "no more wireless"
date: 2005-02-05
forum: Hardware &amp; Laptops
---

### Post by vale on 2005-02-05
Hi all,
I hope this is the rigth thread for my problem.
I installed ubuntu and it immediatly detected my wireless and it worked properly for a day. Now nothing: the icons at the rigth of the screen says N/A "no wireless devices"...
 what's the matter?

thanks in advance
  vale

---

### Post by Jspired on 2005-02-05
What wireless card do you have and have you gone into your settings to make sure they're still registering correctly?

---

### Post by jak on 2005-02-06
[QUOTE=vale]Hi all,
I hope this is the rigth thread for my problem.
I installed ubuntu and it immediatly detected my wireless and it worked properly for a day. Now nothing: the icons at the rigth of the screen says N/A "no wireless devices"...
 what's the matter?

thanks in advance
  vale[/QUOTE]
 I'm not too sure about yours, but this works for me when it happens.
```

sudo ifdown wlan0 && sudo ifup wlan0

```
where wlan0 is the wireless device.

---

