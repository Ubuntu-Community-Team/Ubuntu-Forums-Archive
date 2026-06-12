---
title: "[SOLVED] make gnome-bar transparent with compiz?"
date: 2008-08-14
forum: General Help
---

### Post by Mgiacchetti on 2008-08-14
I am using compiz's desktop cube feature to make the cube 25% transparent all the time, the only thing is the gnome bar is not transparent, it shows the wallpaper or background color.

Anyone know a workaround besides killing it?

---

### Post by tuxxy on 2008-08-14
Maybe you could right click it, properties, and edit its transparency level?

---

### Post by sayakb on 2008-08-14
Right click on panel->Properties->Background tab->Solid color and adjust the slider to make it transparent.

---

### Post by mcduck on 2008-08-14
Adjusting the panel transparency from panel's settings won't give real transparency. It will only result in fake transparency showing the background picture/color through the panel. And this looks very stupid if everything else is transparent, like with transparent cube..

It _is_ possible to get real transparency using Compiz, but the downside is that it won't only make the panel background trasnparent, itnstead it makes _everything_ in the panel trasnparent, including all icons & text..

---

### Post by Mgiacchetti on 2008-08-14
> **tuxxy said:**
> Maybe you could right click it, properties, and edit its transparency level?

> **LinuxIsInnovation said:**
> Right click on panel->Properties->Background tab->Solid color and adjust the slider to make it transparent.

Nope. still shows the background without transparency.

---

### Post by Mgiacchetti on 2008-08-14
> **mcduck said:**
> Adjusting the panel transparency from panel's settings won't give real transparency. It will only result in fake transparency showing the background picture/color through the panel. And this looks very stupid if everything else is transparent, like with transparent cube..

It _is_ possible to get real transparency using Compiz, but the downside is that it won't only make the panel background trasnparent, itnstead it makes _everything_ in the panel trasnparent, including all icons & text..

how would i go about this?

---

### Post by sayakb on 2008-08-14
You may press Alt+Scroll Down on the panel to make it transparent. I knew how to change specific windows' opacity in beryl, but not in compiz. I'll be waiting for mcduck's reply :)

---

### Post by DaymItzJack on 2008-08-14
CCSM -> General Options -> Opacity Settings

New -> Opacity Windows: class=Gnome-panel 
    -> Opacity Window Values: 25%

However, like mcduck said, even the icons are transparent and it gets hard to see.

---

### Post by Mgiacchetti on 2008-08-16
> **DaymItzJack said:**
> CCSM -> General Options -> Opacity Settings

New -> Opacity Windows: class=Gnome-panel 
    -> Opacity Window Values: 25%

However, like mcduck said, even the icons are transparent and it gets hard to see.

Awesome, dont really care about icons showing through or not, just want alt+f2 working again,... Plus the huge shutdown button from cairo-dock dont look right...

This totally looks awesome now!

---

