---
title: "Totem and text size"
date: 2005-11-23
forum: General Help
---

### Post by Owdy on 2005-11-23
When i play .div movies with .sub text files, text size wont resize. No matter how big i set them from settings. Any ideas why? Totem 1.2.0

---

### Post by Owdy on 2005-11-26
Anyone? This has to be bug of somekind.

---

### Post by Bachstelze on 2005-11-26
Try VLC, it works fine with it for external subtitles. About using Totem for I have absolutely no idea :/

---

### Post by Owdy on 2005-11-26
[quote=HymnToLife]Try VLC, it works fine with it for external subtitles. [/quote]No thanks. I like Totem.

---

### Post by dudus on 2005-11-28
Same problem here. I'm using avi files encoded in xvid and .srt files for the subs. Everything plays fine but the subs won't resize. I like Totem too. I like gxine also but the subs won't even display at all. 

Xine seems to work fine

---

### Post by wurtel on 2005-12-06
find the totem-configuration file in ~/.gnome2/totem_config.
Open this file ith gedit and search for "size" and you'll find this lines:

# subtitle size
# { tiny small normal large very large huge }, default: 1
subtitles.separate.subtitle_size:large

On my system there was a # before that last line and the 'large' was 'small' before. I changed it and now I can enjoy the movie :)

Hope this was helpful?

---

### Post by Owdy on 2005-12-06
[quote=wurtel]

Hope this was helpful?[/quote] From file that i can change font size yes. But there are that settings area in Totem where you can change font settings. Why that wont work?

---

### Post by Franko30 on 2006-01-14
[QUOTE=Owdy]But there are that settings area in Totem where you can change font settings. Why that wont work?[/QUOTE]

Hmmm - here in Breezy I don't see any font setting dialogues in Totem - at least not when using external subs with *.avi files.

Maybe that's because I use Totem Xine?

Franko30

---

### Post by marx06 on 2006-05-08
Do you know where is the Totem config file in Breezy? I can't find it. I have same problem - can change subtitles size in Settings but with no effect. Totem 1.2.1 with xine-lib 1.0.1 Thanks.

---

### Post by Owdy on 2006-05-08
[quote=marx06] I have same problem[/quote] Please report that in there [https://launchpad.net/distros/ubuntu/+source/totem/+bug/37587](https://launchpad.net/distros/ubuntu/+source/totem/+bug/37587) . They dont belive me :D

That config file should be in same place as Dapper. 

Home/you/.gnome2/totem_config . Its hidden dir.

If you cant find it, run search with 'totem_config'.

---

### Post by marx06 on 2006-05-08
Thanks, I reported that at the link you wrote. I found config file, changed it as WURTEL adviced and it works well now.

---

### Post by Sandu on 2006-05-14
Font size of subtitles can be changed via menu "Edit" - "Preferences" in Totem 1.4.1  (Gstreamer 0.10.6) in Ubuntu Dapper Drake 6.06 Beta.

---

### Post by Owdy on 2006-05-22
[quote=Sandu]Font size of subtitles can be changed via menu "Edit" - "Preferences" in Totem 1.4.1  (Gstreamer 0.10.6) in Ubuntu Dapper Drake 6.06 Beta.[/quote] [https://launchpad.net/bugs/37587](https://launchpad.net/bugs/37587)

---

### Post by warjowuch on 2006-10-01
*BUMP*

I found the config file, changed it, but totem changed it back. I set permissions to read only, but totem makes a totem-config~ and uses that... No subtitlechange here. Anybody?

---

### Post by warjowuch on 2006-10-01
Never mind, I found out I had to uncomment the items to make them function.
THanks! Sorry for the inconvenience...

---

