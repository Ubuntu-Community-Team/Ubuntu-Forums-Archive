---
title: "ThinkPad X200: sound doesn't work in Ubuntu 13.04"
date: 2013-08-02
forum: Hardware
---

### Post by Nickolai_Leschov on 2013-08-02
I have installed Ubuntu 13.04 to try it out and I can't make the sound work. It worked on 12.04, though.

Can't I make the sound work? Is my sound chipset not supported anymore?

[[IMG]http://i298.photobucket.com/albums/mm249/hrenistic/Screenshotfrom2013-08-03001645_zpsa9f3cda4.png[/IMG]]("http://s298.photobucket.com/user/hrenistic/media/Screenshotfrom2013-08-03001645_zpsa9f3cda4.png.html")

---

### Post by yoko_hama on 2013-08-02
Open a Terminal and type in ** aplay -l ** [br]...[/br] ( it is a lowercase  L ; it will show your sound devices)[br]...[/br] Next type in ** alsamixer **  [br]...[/br] Use your arrow keys to navigate.  Select your sound card by pressing F6. [br]...[/br] Select the new sound card and press enter. You should be able to hear your music.

---

