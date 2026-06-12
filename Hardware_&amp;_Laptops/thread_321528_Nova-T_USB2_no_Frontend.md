---
title: "Nova-T USB2 no Frontend"
date: 2006-12-19
forum: Hardware &amp; Laptops
---

### Post by pmbsa on 2006-12-19
Hi, I just installled ubuntu 6.10, I am trying to get my Nova-T USB2 tv device working. The device seems to start ok (in WARM state) I have the dvb-usb-nova-t-usb2-01.fw firmware in the /lib/firmware directory which made a difference (as in the device seemed to then at least start) but I cannot seem to get the thing to attach a frontend so I am guessing I am missing something key.
I have searched the forums but I cant find anything that tells me what I might be missing, everybody simply says tomake sure the firmware is in the right place.

Any help would be appreciated, I am very much new to linux.
thanks
Paul

---

### Post by Ozzee on 2006-12-26
You can use Kaffeine as a frontend.

In the teminal type:
```

sudo apt-get install kaffeine

```

Now you can find the program under Applications - Sound & Video

:)

---

