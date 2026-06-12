---
title: "Can't Change Resolution Above 1024"
date: 2005-11-06
forum: General Help
---

### Post by michaelb on 2005-11-06
Hello there!

I just started using Ubuntu (I had been using WinXP on that computer previously -- now it's a duel boot on separate hard drives) a few days ago, and I have been quite pleased with how smoothly the transition has gone. However, I am accustomed to the resolution 1280x1024 (anything less than that looks giant to me), and the resolution changer doesn't have that as an option in the combo box -- the highest listed is 1024x786. I did some googling, and found that -- in most cases -- editing the file /etc/X11/xorg.conf will fix everything up good and proper. When I took a peek, I saw 
```
Modes "1280x1024" "1024x768" "800x600" "640x480"
```
Unfortunately, 1280x1024 was already there.

On XP, 1280x1024 worked perfectly.

If it is important, I am using an nVidia GeForce 4 Graphics Card and the drivers seem to be functioning properly.

If there's anything more you would like to know, please tell me so.

Any suggestions? Thanks!

---

### Post by aysiu on 2005-11-06
[These](http://ubuntuforums.org/showpost.php?p=129379&postcount=21) are all the suggestions I know.

---

### Post by michaelb on 2005-11-06
[QUOTE=aysiu][These](http://ubuntuforums.org/showpost.php?p=129379&postcount=21) are all the suggestions I know.[/QUOTE]

Thanks for the prompt reply! I'll give it a try (I'm not on that computer right this minute).

[COLOR="DarkRed"]
EDIT: I tried going through those steps listed in the link your provided, and everything is working beautifully now! Thanks![/COLOR]

---

### Post by jvictor on 2005-11-06
Lookup the H& V refresh rates of ur monitor from the net/ manual and put them in ur xorg.conf, it will b solved

---

### Post by Wabbit on 2005-11-07
The maximum horizontal refresh rate is not set high enough to achieve 1280x1024, so just do what jvictor wrote and you'll get 1280x1024.

Tony.

---

