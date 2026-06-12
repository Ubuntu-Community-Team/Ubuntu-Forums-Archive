---
title: "[SOLVED] Compiz-Fusion / Bottom panel &amp;quot;shadow&amp;quot;"
date: 2008-11-12
forum: General Help
---

### Post by em007a on 2008-11-12
When I adjust the transparency *(panel on bottom of screen only)*, I get an annoying shadow on top of the panel. It somewhat defeats the purpose of having a transparent panel. 

It only occurs when I turn on compiz-fusion. So far I haven't been able to locate the setting to turn it off. Anyone know which setting controls the shadow?

---

### Post by em007a on 2008-11-12
I attached a couple pics to show what I am talking about. 

1st ppic shows with emerald window decorator turned on, 2nd is with emerald turned off. Thanks for any help.

---

### Post by pdescham49 on 2008-11-12
> **em007a said:**
> I attached a couple pics to show what I am talking about. 

1st ppic shows with emerald window decorator turned on, 2nd is with emerald turned off. Thanks for any help.

The first with emerald on Is showing you the shadow you can disable it by playing around with the emerald admin tool modify the theme play with the radius or disable it all together. don't have emerald installed so i can not assist however:

the second is a shadow from compiz go into your CCSM tool click on window decoration 

add this to the shadow windows 

```
any & !(class=Gnome-panel) 
```

---

### Post by em007a on 2008-11-12
Thanks! It was the frame Shadow in Emerald Themer. Turned Opacity as low as it would go.

Problem solved!

---

### Post by pdescham49 on 2008-11-12
NP. 
Cheers

---

