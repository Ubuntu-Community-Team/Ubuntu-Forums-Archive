---
title: "please help with some composite managers"
date: 2008-10-24
forum: General Help
---

### Post by skater-dude on 2008-10-24
i need a composite manager from cairo-dock and i have tried compiz but it doesnt work so can u give me a list of composite managers

---

### Post by Paqman on 2008-10-24
XFCE has a built-in compositor, can't remember for the life of me what it's called.

---

### Post by skater-dude on 2008-10-24
i have gnome though

---

### Post by fabounet on 2008-10-24
xcompgr
in the last resort, activate the fake transparency in the config panel.

---

### Post by skater-dude on 2008-10-24
how do i set xcompmgr as my main composite manager
and how do i activate fake transperancy in the config menu on cairo-dock

---

### Post by kpkeerthi on 2008-10-24
[https://help.ubuntu.com/community/CairoDock](https://help.ubuntu.com/community/CairoDock) has everything you need to know about cairo and fake transparency

You can test xcompmgr with the following command in a terminal
```
xcompmgr -cCfF &
```
This should give some basic shadows and fading effects. More examples [here]("http://wiki.archlinux.org/index.php/Xcompmgr")

Add the command to a list of session startup programs under System -> Prefs -> Sessions

---

### Post by skater-dude on 2008-10-24
thank you sooo much
it worked

---

