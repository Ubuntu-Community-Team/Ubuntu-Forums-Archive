---
title: "Problem with toolbar?"
date: 2008-09-13
forum: General Help
---

### Post by Mr.Carioca on 2008-09-13
Hello guys,

well I was customizing my ubuntu when I came across this Emerald theme, alright installed the theme to the emerald theme stuff and then open terminal "emeral --replace" alright got my new theme (hated those) then I exit the terminal, my regular "close, minimize and expand" bottoms disappear!

here is the idea:
[IMG]http://i91.photobucket.com/albums/k311/DiscoveryVACEO/Screenshot-1-1.png[/IMG]
[IMG]http://i91.photobucket.com/albums/k311/DiscoveryVACEO/Screenshot-2.png[/IMG]

any ideas?
now I tried on sudo remove emeral and I removed emeral theme manager, but the problem still stayed.

---

### Post by northern lights on 2008-09-13
Hit Alt+F2 and execute ```
metacity --replace
``` or run ```
metacity --replace &
```from a terminal.

---

### Post by Mr.Carioca on 2008-09-13
Nice, it worked!

thx

---

