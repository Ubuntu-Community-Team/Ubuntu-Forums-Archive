---
title: "Disable Wireless Radio for Dell Inspiron 9300"
date: 2007-02-01
forum: Hardware &amp; Laptops
---

### Post by jfinkels on 2007-02-01
Ubuntu 6.10 on Dell Inspiron 9300 (a little more than a year old) with Intel PRO/Wireless 2915ABG wireless controller.

Pressing Fn+F2 when I had Windows enabled/disabled the wireless radio (including toggling the little blue "WiFi" indicator light). On Ubuntu, Fn+F2 appears to enable/disable the Bluetooth signal (or at least, the little blue "Bluetooth" indicator light goes on and off, that's all I know; I don't use any Bluetooth devices :D).

I tried to use *xev* to figure out what was happening when I pressed Fn+F2, but I guess it doesn't do combinations of keys. I figured that *xmodmap -pke* might be able to give me some hint, but I really don't know that much about using these two programs.

Does anyone know how to change the program that runs when I press Fn+F2?

---

### Post by jfinkels on 2007-02-01
bump...

---

### Post by Priit Tamboom on 2007-02-25
I have Inspiron 6400 and the tings might be same.

You can change the Fn+F2 action in the bios. However there are three options: turn off/on only wifi, turn off/on only bluetooth, turn off both. So I haven't googled much how to turn off/on from Ubuntu (I'm still newby :-). I also would like to manage those things separately. 

As much I know Fn does not reach to the operation system at all. Bios deals it directly, so xmodmap can not use to manage it.

Priit

---

