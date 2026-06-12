---
title: "Keyboard and Mouse"
date: 2006-01-04
forum: Hardware &amp; Laptops
---

### Post by tonyisntcreative on 2006-01-04
I FINALLY installed Ubuntu today and I'm really quite happy with it...everything went smoothly, and the thing I was most worried about (my ethernet card not being detected/supported) worked out fine.  All I had to do was change my DNS settings and I was online doing all I wanted.

After booting everything seemed to be working well.  After I got online though, I realized the back and forward buttons on my mouse weren't working (it's a five button Belkin).  I looked online for linux drivers for a while, but didn't seem to have any luck.  

After I had restarted the computer once, I noticed two problems with my keyboard.  The first was that the 0 in the numpad did not work when it did before on the first boot.  I KNOW it worked because the DNS numbers I had to use had 0's in them....207.69.188.185 and .186.  Also, the arrows don't work and I think they did while I was online before hand.


Any help with these things would be wonderful.


EDIT: Don't worry about the keyboard anymore...I've gotten it to work.  The arrows AND numpad keys all work, so it's fine.  Mouse would still be nice to get working, though.

---

### Post by tonyisntcreative on 2006-01-05
Still looking for any help on the mouse.

---

### Post by tonyisntcreative on 2006-01-05
I don't mean to spam, but come on...

Anyone???

---

### Post by Amon_Re on 2006-01-05
[QUOTE=tonyisntcreative]I FINALLY installed Ubuntu today and I'm really quite happy with it...everything went smoothly, and the thing I was most worried about (my ethernet card not being detected/supported) worked out fine.  All I had to do was change my DNS settings and I was online doing all I wanted.

After booting everything seemed to be working well.  After I got online though, I realized the back and forward buttons on my mouse weren't working (it's a five button Belkin).  I looked online for linux drivers for a while, but didn't seem to have any luck.  [/QUOTE]

Didn't know belkin made mouses, but anyways:

```
Section "InputDevice"
        Identifier      "Configured Mouse"
        Driver          "mouse"
        Option          "CorePointer"
        Option          "Device"                "/dev/input/mice"
        Option          "Protocol"              "auto" *Don't touch this line *
        Option          "Buttons"               "5" * Number of buttons on mouse *
        Option          "ZAxisMapping"          "4 5" * The scroll wheel *
        Option          "Resolution"            "300" * If your mouse can do better, change it, when in doubt, don't touch ;) *
EndSection
```

This is how i remember it being, do not modify your protocol line, might take some experimenting with the ZAxisMapping.

Also, you might still have to assign functions to said buttons, i think that was done with **xmodmap**

---

### Post by tonyisntcreative on 2006-01-05
Thanks, I'll let you know how it works.

---

### Post by tonyisntcreative on 2006-01-05
I still can't get the back or forward buttons to work on the sides, and I obviously have no idea how to use xmodmap.  Everything I can find on google is saying something different, and none of them are doing what I want.

---

### Post by lpf on 2006-05-24
[QUOTE=tonyisntcreative]
EDIT: Don't worry about the keyboard anymore...I've gotten it to work.  The arrows AND numpad keys all work, so it's fine.  Mouse would still be nice to get working, though.[/QUOTE]

Hello, I have the same problem with a Belkin wireless keyboard.](*,) 
If you are still there can you tell me how you made the arrows AND numpad keys work.
Thanks.

---

