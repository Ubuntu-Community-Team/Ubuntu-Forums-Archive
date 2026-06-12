---
title: "What keyboard layout is this?"
date: 2013-04-03
forum: Hardware
---

### Post by aantoon on 2013-04-03
I am installing ubuntu for a Belgian friend and it has this [http://www.gemwon.com/sp15914](http://www.gemwon.com/sp15914) keyboard. The model on the back say V090562bk1. I have tryed all begium, german uk and dutch varieties but non match. Do you recognise this layout?

TIA

---

### Post by schragge on 2013-04-03
I have no idea what keyboard layouts are used in Belgium. The only thing I see is that it's definitely AZERTY. Try things like
```

setxkbmap -rules evdev -model asus_laptop -layout be -variant [COLOR=blue]some_variant[/COLOR]

```
where [COLOR=blue]some_variant[/COLOR] can be one of *oss*, *oss_latin9*, *oss_sundeadkeys*, *iso-alternative*, *nodeadkeys*, *sundeadkeys*, *wang*. Those are all belgian keyboard layout variants XKB knows about (see [xkeyboard-config(7)]("http://manpages.ubuntu.com/manpages/precise/en/man7/xkeyboard-config.7.html")).

---

### Post by aantoon on 2013-04-03
As i said "I have tryed all begium, german uk and dutch varieties but non match"
btw it is a asus pro 79a series laptop

---

### Post by schragge on 2013-04-03
But have you also selected keyboard model *asus_laptop* or you've tried them with the standard *pc105*?

---

### Post by aantoon on 2013-04-03
Ok, I tried them just now as you said but in all varieties the number pad to the right is not working number 4-5-6, del not working and space-to right also not working
and iso-alternative gives error

---

### Post by Peter Maunder on 2013-04-03
Looks like a Belgian Keyboard according to my 1993 Keyboard Manual. The layout is described in [http://en.wikipedia.org/wiki/AZERTY](http://en.wikipedia.org/wiki/AZERTY). Ubuntu has a choice of 8 Belgian Keyboards with options for special keys etc. Have you tried using the Keyboard Layout application? I use French French and Swiss French as well as English and found I needed  needed options to be set as well as the base Language. For example the little 3 and 2 on the top left hand key is often just a 2 on some settings. If you are in Belgian, have any neighbours a similar keyboard?

---

### Post by aantoon on 2013-04-03
Yes, I found the same keyboard on a other computer but it has windoze installed and i have no idea how to get the info and...there are differed names for same keuboards so I'm not sure that even if i get the name from windows it will help me any further, it's a mess

---

### Post by Peter Maunder on 2013-04-03
IF I was adding a new keyboard I would go to the  KEYBOARD LAYOUT module which can be found under SYSTEM SETTINGS.  On the LAYOUT tab you can add additional country keyboard. Select the Belgian keyboard you wish to check and select PREVIEW. This will show you the provisional layout. Go through the 8 keyboards until you find the one closest to your requirement.  With luck one of the 8 should meet your needs.  The KEYBOARD LAYOUT OPTIONS will allow you to fine tune the alternate keys, where to put EURO etc. - Good luck

---

