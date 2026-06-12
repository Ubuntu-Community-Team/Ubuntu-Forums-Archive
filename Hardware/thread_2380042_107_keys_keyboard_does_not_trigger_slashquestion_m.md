---
title: "107 keys keyboard does not trigger slash/question mark key event"
date: 2017-12-12
forum: Hardware
---

### Post by rsdias on 2017-12-12
I have a keyboard which is a 107 key (supposed) *brazilian abnt2* model.

The key for _slash_ and q_uestion mark_ does not trigger any event with **xev**, **showkeys** and other scanning tools.

However, If I sniff the USB communications with **WireShark**/**usbmon**, I can see that it is reporting the key press.

Other *brazilian abnt2* model keyboards reports this key press just fine.  Which makes me wonder if it is the same scancode at all.

So, I need at least some direction on where to start to get the key events.

thanks,
-rsd

---

