---
title: "Cario Dock"
date: 2008-08-27
forum: General Help
---

### Post by Mhurst1 on 2008-08-27
I have installed cario dock sucessfully, however it will not load onto my desktop I select a theme and hit ok, but nothing loads. Any Ideas?

---

### Post by gjoellee on 2008-08-27
do you have Compiz Fusion running?

---

### Post by eggdeng on 2008-08-27
Open a terminal and type
```
cairo-dock
```
To get it to start when you start a session, just go to Preferences -> Sessions -> Startup Programs -> Add. For Command, put cairo-dock & whatever you like for the rest.

---

### Post by Mhurst1 on 2008-08-27
> **gjoellee said:**
> do you have Compiz Fusion running?


Yes

---

### Post by Mhurst1 on 2008-08-27
> **eggdeng said:**
> Open a terminal and type
```
cairo-dock
```
To get it to start when you start a session, just go to Preferences -> Sessions -> Startup Programs -> Add. For Command, put cairo-dock & whatever you like for the rest.

Done that same thing. However I do get a warning, but its in French or something so no clue what it says.

---

### Post by fabounet on 2008-08-28
are you sure it's not hiding somewhere on your desktop ?
if the theme has the auto-hide activated, it may be behind your gnome-panel for exemple.
try a "cairo-dock -l debug" and post it here.
also, after yo ulaunched it, check that it is running (ps -ef | grep cairo)

---

