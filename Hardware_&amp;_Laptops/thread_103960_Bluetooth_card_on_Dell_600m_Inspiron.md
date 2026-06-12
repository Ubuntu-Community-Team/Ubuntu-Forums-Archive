---
title: "Bluetooth card on Dell 600m Inspiron"
date: 2005-12-15
forum: Hardware &amp; Laptops
---

### Post by raffrules on 2005-12-15
Hey everybody,

I'm kind off new to both Ubuntu and this forum but I find it very friendly and smart. And to my surprise I managed so far with all my problems related to hardware and software. HOWEVER I spent last three days trying to make my bluetooth work, with no result unfortunately.

I own (a very new one as you may suspect) Dell Inspiron 600m with internally built Dell TrueMobile 300 Bluetooth Internal Card and Ubuntu doesn't see this device. I tried billions of ways but i cannot make it work.

If ANYONE knows how to solve this problem, I'd be extremely greatful!!!

Thanks. :)

---

### Post by ranf on 2005-12-15
Telling what you tried already, would be helpful.

Just some stuff:
```
dmesg | less
```
has no trace of "Bluetooth"?

Have a look at the output of these commands:

lspci
lsusb
lshw

Any special key combination on your keyboard that turns it on/off?

---

### Post by nickj6282 on 2005-12-15
I have the same laptop with the same Bluetooth module. Is the blue LED next to the charge light on? If not try Fn+F2 and see if it comes on. Ubuntu automagically recognized the card for me and I was able to get my bluetooth mouse working in a snap.

---

### Post by raffrules on 2005-12-16
This is amazing! I pressed Fn+F2 and It works!!! I had no idea that the only thing I hadn't done was this tiny procedure.

Thanks a lot!!!!!

---

### Post by nickj6282 on 2005-12-16
Glad I was able to help! Just remember that the Fn+F2 combo controls the hardware switches for both the bluetooth card and internal wireless card simultaneously, so double-check and make sure you didn't turn one off while turning the other one on. It shouldn't work that way but sometimes my laptop gets funky on me and I have to cycle a few times to get both working.

-Nick

---

