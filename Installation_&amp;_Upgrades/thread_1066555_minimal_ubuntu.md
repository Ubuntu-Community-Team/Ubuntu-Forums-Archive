---
title: "minimal ubuntu"
date: 2009-02-11
forum: Installation &amp; Upgrades
---

### Post by socomhacker239 on 2009-02-11
I have ubuntu but i want ubuntu minimal with out all the applications and extra features i just want to use the computer for programming and internet i have looked at other os's but i want to stick with ubuntu.

---

### Post by cmay on 2009-02-11
i sometimes if i really want to try something new but do not want to completely reinstall just run tasksel. then it gives me the options to install with or with out the desktop enviroment which i just uncheck then i start building from there.

 there is a minimal ubuntu image and a alternative installer cd and if you want to have ubuntu with out some of the restricted drivers then you can use gobuntu. 

hope it was what you was looking for.

---

### Post by socomhacker239 on 2009-02-11
thank you, But can you give me a link to the minimal iso thank you

---

### Post by cmay on 2009-02-11
[https://help.ubuntu.com/community/Installation/MinimalCD](https://help.ubuntu.com/community/Installation/MinimalCD)
here it is. i used the gobuntu cd image at one time since i like the standard textbased installer where i can uncheck desktop and use what ever desktop of my own choice but i have not tried this cd image my self.
good luck.

---

### Post by socomhacker239 on 2009-02-11
Im sorry i cant use that iso it require a internet connection and i only have a wireless card so i cant set it up properly.
Im tring to explain it my best i know im confusing. Okay so i downloaded the iso and burned it to a cd then i ran the cd then i was following the directions, Everything was running fine then it asked me for my ip so i enterd it then it said no internet connection found its because i have a wireless card. so if someone can give me a link directly to the iso so i can download it i want just a plain no app ubuntu. thanks

---

### Post by cmay on 2009-02-11
use the alterative installer then. under installation uncheck install desktop , standard system and printerservers this will leave you with a absolute minimal ubuntu system with no gui apps or desktops. then use at-get to install programs as yo see fit as you go along. 

i use to do this. then i as the first thing when i reboot install xorg and then after this opebox or lxde or jwm or even gnome if i want to use this desktop enviroment. the main difference is i can build my destop as i want. 

the gobuntu image contains no properatiary addons so its not theright one to use for you. just use the alternative installer cd. of which version you want.

---

### Post by avtolle on 2009-02-11
> **socomhacker239 said:**
> Im sorry i cant use that iso it require a internet connection and i only have a wireless card so i cant set it up properly.
Im tring to explain it my best i know im confusing. Okay so i downloaded the iso and burned it to a cd then i ran the cd then i was following the directions, Everything was running fine then it asked me for my ip so i enterd it then it said no internet connection found its because i have a wireless card. so if someone can give me a link directly to the iso so i can download it i want just a plain no app ubuntu. thanks
I'm confused; first you say you cannot d/l the iso for the minimal install the link for which was provided due to wireless problems, and then you ask for a link to the iso so you can download it. The link has been provided, so that's where you go to download it.

---

### Post by avtolle on 2009-02-11
If you are saying (after rereading, I came up with another thought) that you cannot use the minimal cd iso because it requires a connection so you can download what is needed, and because you can't use your wireless card, you can't download the rest of the packages you need, then I apologize for the shortness of the prior post. 

Do you know what wireless card you have? You post that you have ubuntu; is it already installed? If so, go to the terminal (Applications>Accessories>Terminal) and type```
lspci
```to find the identity of your wireless card. If you can, post the results here; if you are accessing the web via another computer, or O/S, then write down the lines which begin Ethernet Controller and post them here. Of course, if you already know what your wireless card is, then post that information.

---

