---
title: "cube not a cube"
date: 2008-07-17
forum: General Help
---

### Post by Torsion on 2008-07-17
Hello, I once had SUSE 10 installed and when I pressed Ctrl + left click and drag, a 3-d cube would rotate.  But in Ubuntu (unless I'm missing something) it's not a cube at all, it's flat.

[IMG]http://img174.imageshack.us/img174/9393/cubemq5.png[/IMG]

---

### Post by Locutus_of_Borg on 2008-07-17
ccsm > general options > increase number of desktops to 4

---

### Post by tuxxy on 2008-07-17
Yes add 3 desktops so you have 4, then the reason it is showing like that is because you ahve desktop wall effect enabled instead of cube.  Simply enable the desktop cube effect in CCSM and it should tell you desktop wall is being disabled.

if you dont have the seetings manager run command from terminal below, the app will be in preferences

```
sudo apt-get install ccsm
```

---

### Post by Torsion on 2008-07-17
> **Locutus_of_Borg said:**
> ccsm > general options > increase number of desktops to 4

For some reason it won't let me change the values.

Edit: It was "horizontal virtual size" that needed to be changed.  Thanks for the help

---

### Post by Archimedes0212 on 2008-07-17
if you have the workspace window on the bottom panel of your screen, you can right-click there and click preferences.  from there one of the options is the number of workspaces.  hopefully that helps.  :-\

---

### Post by stitchmysmile93 on 2008-07-17
enable 12 desktops and have a 3d polygon... that would be tight...

I have an octagon...

---

### Post by stitchmysmile93 on 2008-07-17
Do you have advanced desktop effects settings installed... when I installed compiz I couldn't add more I did it with that the fusion icon is nice to have also...

---

### Post by PinkFloyd102489 on 2008-07-17
The package isnt called "ccsm", it's called "compizconfig-settings-manager".

---

### Post by DaymItzJack on 2008-07-19
> **PinkFloyd102489 said:**
> The package isnt called "ccsm", it's called "compizconfig-settings-manager".

Yeah, he was also wrong about it being a "desktop wall", but who's complaining? ;p

---

### Post by stldirty on 2008-07-19
> **PinkFloyd102489 said:**
> The package isnt called "ccsm", it's called "compizconfig-settings-manager".

take a second and tell me what the abbreviation of "compizconfig-settings-manger" is?

i'll wait...

---

### Post by ad_267 on 2008-07-19
> **stldirty said:**
> take a second and tell me what the abbreviation of "compizconfig-settings-manger" is?

i'll wait...

I think the issue is someone posted "sudo apt-get install ccsm" It's fine to call it ccsm but when you ask someone to install the ccsm package:

```
sudo apt-get install ccsm
Reading package lists... Done
Building dependency tree        
Reading state information... Done
E: Couldn't find package ccsm

```

---

