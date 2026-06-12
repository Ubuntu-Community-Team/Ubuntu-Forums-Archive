---
title: "Razer Taipan Mouse - Binding Macro Commands to Buttons"
date: 2014-11-28
forum: Hardware
---

### Post by Echis on 2014-11-28
[IMG]http://webchetna.com/wp-content/uploads/2012/07/Razer-Taipan-Mouse-2.jpg[/IMG]

For quite some time, I've been trying to figure out how I can program the side buttons (the silver ones in the photo above) on my Razer Taipan so that I can use one button to copy (like ctrl + C)  and another to paste (like ctrl + V). This is easily done in windows using the Synapse program provided with the mouse, however I've reached my wits end with how to get them to function the same on linux (because I'd honestly prefer to use linux if I could!).

Using this feature:

```
xev | grep button
```

I've been able to determine that the buttons I want to bind the macro features to are "button 9" and "button 8," but I'm not sure what to do next, please help!

---

### Post by CantankRus on 2014-11-30
An easy way is to use easystroke.
See [**_[COLOR="#B22222"]HERE[/COLOR]_**]("http://ubuntuforums.org/showpost.php?p=10495426&postcount=11")

---

### Post by Echis on 2014-12-01
Oh my god! That's awesome - it works perfectly!! Thanks so much!!!!!! :)

---

