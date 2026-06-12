---
title: "wine wine go away"
date: 2008-09-07
forum: General Help
---

### Post by Gdschaf on 2008-09-07
I've been searching around all day trying to find a solution to my problem
i installed wine to use itunes so i could remotely access my library but didn't really think it was going to work, and it didn't so now i want to get rid of it, the uninstaller doesn't show any programs to uninstall, i got rid of wine (i think) but the wine fold is still under applications with itunes and quicktime in it, any help would be appreciated

---

### Post by jerome1232 on 2008-09-07
What did you do to get rid of it?

Do the apps actually launch if you click on those launcher under applications.

Generally to remove software completely (for wine this removes all apps installed by it too)

```
sudo apt-get remove --purge wine
```

If you prefer synaptic you would mark wine for complete removal does the same thing.

---

### Post by bodhi.zazen on 2008-09-07
and then , if needed, ```
rm -rf ~/.wine
```

---

### Post by Gdschaf on 2008-09-07
i've tried many things
for starters
```
sudo rm -rvf ~/.wine

```
I can't remember what else i tried, all i know is even after doing what you told me to try, i still have a wine folder under applications with itunes and quicktime that don't launch when i click on them :-/

edit: and i just relized what u told me to try and what i remembered i tried, are nearly the same thing

---

### Post by stoneage on 2008-09-07
If it is just the entry under Applications, go to System => Main Menu and uncheck all the entries you do not want to display.

Wine is under Applications, itunes and quicktime are under Wine.

---

### Post by Gdschaf on 2008-09-07
thanks, i guess ill just forget all about it since it doesn't do ne thing :-/ weird

---

