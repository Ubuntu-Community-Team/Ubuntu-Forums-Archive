---
title: "Not all multimedia keys are working on my keyboard"
date: 2008-07-18
forum: General Help
---

### Post by wolfshark on 2008-07-18
My keyboard is A4Tech KBS-26
[IMG]http://e-katalog.com.ua/jpg_zoom1/42513.gif[/IMG]
The only buttons that aren't working are almost all on the left side - cut, copy, paste, undo, toggle, close and the scroll. Also in the upper left corner - New, Word and Excell. Everything else is working. I tried to "detect" the non-working buttons with xev but there is no reaction at all, the other buttons are giving signals. How can i fix this?

---

### Post by schauerlich on 2008-07-18
Keyboards like this with multimedia keys are often only written with Windows in mind, as you can see by the "Word" and "Excel" keys. Unfortunately you're not likely to get an equivalent functionality from the keyboard in Linux.

---

### Post by wolfshark on 2008-07-18
> **EDavidBurg said:**
> Keyboards like this with multimedia keys are often only written with Windows in mind, as you can see by the "Word" and "Excel" keys. Unfortunately you're not likely to get an equivalent functionality from the keyboard in Linux.
That's true but it would be nice to start OpenOffice with the "Word" key for example. I am not searching for equivalent functionality.

---

### Post by schauerlich on 2008-07-18
> **wolfshark said:**
> That's true but it would be nice to start OpenOffice with the "Word" key for example. I am not searching for equivalent functionality.

The problem is that Linux might not be able to "see" the Word key. The keyboard probably came with a special driver that let Windows know where all the keys were and what to do with them. This driver won't work in Linux.

---

### Post by sujoy on 2008-07-18
yes, if xev doesn't detect the signal from the keys, then AFAIK theres no hope

---

### Post by strid3r on 2008-10-15
You can use keytouch and keytouch editor to configure all of your media keys: 
[http://maketecheasier.com/keytouch-regain-the-full-functionality-of-your-keyboard/2008/07/16](http://maketecheasier.com/keytouch-regain-the-full-functionality-of-your-keyboard/2008/07/16)

---

### Post by jrdecastro on 2008-10-27
Having similar but not identical problem. I have two wireless keyboards on my work and home machines - a Microsoft Wireless Keyboard and a Microsoft Wireless Multimedia keyboard. I don't actually use or need all the extra multimedia keys - I bought the keyboard with them because they were selling it cheap. The problem is that fairly fundamental basic functionality like Ctrl+Alt+F1 / F2 / F3 etc... for getting to a virtual terminal works Ok on the wireless keyboard but does not work at all on the wireless multimedia keyboard.
Is there any known way to resolve this? The keyboard is Microsoft Wireless Multimedia Keyboard v1.1 and I am running Ubuntu 8.04
Thanks!
James

---

