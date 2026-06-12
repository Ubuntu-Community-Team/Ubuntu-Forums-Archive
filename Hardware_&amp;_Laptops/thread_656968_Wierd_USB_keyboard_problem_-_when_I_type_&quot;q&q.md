---
title: "Wierd USB keyboard problem - when I type &quot;q&quot;, I get &quot;qw&quot; on screen!"
date: 2008-01-03
forum: Hardware &amp; Laptops
---

### Post by paulphillips on 2008-01-03
i just installed Feisty on a friend's computer and the USB travel keyboard the have seems to be behaving strangely sometimes.

Every other boot-up, the "a" key when pressed, produces "as" or "sa"; as does the "s" key.  Similar behaviour happens for "q/w", "z/x" and the tab-key and capslock get merged to!!  Pressing tab, turns caps lock on!

No other keys seem to be affected.

Ubuntu hardware listing reports the devices as a "Chesen" usb keyboard.  It also has only 99 keys.

If this happened every bootup, I'd think the keyboard wasn't supported, but as it works sometimes, it's got me stumped!  Any suggestions?

Thanks.

---

### Post by jespdj on 2008-01-03
This really sounds like a hardware problem with the keyboard. Note that those are all keys that are close together on the left side of the keyboard.

Try the keyboard on a different computer, or with Windows instead of Ubuntu. Does it have the same problem? If yes, then it's really likely that they keyboard itself isn't working properly.

---

### Post by frodon on 2008-01-03
Maybe ubuntu selected the wrong keyboard layout, so i would try to change the keyboard layout to something else.

---

### Post by paulphillips on 2008-01-11
Update: Noticed that if I pull the USB chord out and then put straight back in - it fixes the problem everytime!

Can anyone explain why this works?

Also, is there a way of doing the above in software instead - perhaps a rmmod and then a modprobe of the usbhid module?

---

