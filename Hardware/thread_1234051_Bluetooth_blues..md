---
title: "Bluetooth blues."
date: 2009-08-07
forum: Hardware
---

### Post by burmanabhay88 on 2009-08-07
I have bluetooth on my laptop. I have bluetooth on my mobile. How do I connect them? Very specifically how do I send a file from my mobile to my laptop. The mobile's not detecting my laptop. The light indicating bluetooth is on (laptop). But nothing seems to work.

---

### Post by alexandari on 2009-08-07
make the laptop detect the phone. Sounds weird,but it works for me. You can connect them and just browse into the phone`s files.

---

### Post by burmanabhay88 on 2009-08-07
> **alexandari said:**
> make the laptop detect the phone. Sounds weird,but it works for me. You can connect them and just browse into the phone`s files.

and how do I go about that???

---

### Post by burmanabhay88 on 2009-08-07
I solved the problem myself.
Apparently my bluetooth daemon was not on.
To turn it on. Goto terminal and type
```
sudo bluetoothd
```

After that goto System > Preferences > Bluetooth and change your bluetooth settings as per desire, or use the bluetooth icon in the taskbar.
Hope this helps some one else.

---

### Post by alexandari on 2009-08-07
sorry I didnt know your daemon wasnt on :) I could have helped but... sorry :<

---

### Post by burmanabhay88 on 2009-08-07
> **alexandari said:**
> sorry I didnt know your daemon wasnt on :) I could have helped but... sorry :<

That's all right. Actually... I should have mentioned that I use to use it before, and now I can't see the icon at all.

---

