---
title: "Advanced Desktop Effects Settings Will Not Open"
date: 2008-09-28
forum: General Help
---

### Post by Hunter2034 on 2008-09-28
Alright I have a very annoying problem that won't go away. When I try to go into the Advanced Desktop Effects Settings options, nothing happens. It used to work, now it doesn't. It just won't open it at all. I've already uninstalled and reinstalled Compiz-Fusion completely and that didn't even work. Help would be greatly appreciated.

---

### Post by loligager on 2008-09-28
please specify your version of ubuntu, what you did prior to it going away, and did you install any video drivers, what id your video card. How you removed compiz. 


With that said, i think it might be a application you installed that is causing the problem. Futhermore, it might help to do this in terminal...

sudo apt-get purge compiz; sudo apt-get build-dep compiz; sudo install compiz

---

### Post by lswb on 2008-09-28
See if you get any error messages when trying to start the settings manager from the command line. Open a terminal and type:
ccsm
(then press enter)

---

### Post by Hunter2034 on 2008-09-28
okay i got it fixed. i put in that command line, tried it, and now it works. Thanks.

---

### Post by Hunter2034 on 2008-09-28
okay scratch that. it was working when compiz was disabled but when i turned it back on, it went back to doing the same thing.

Hardy 8.04

i dont remember what i did prior to it not opening.

---

### Post by lswb on 2008-09-28
So are there get any error messages when you run "ccsm" in a terminal?

---

### Post by Hunter2034 on 2008-10-06
No. It's very weird. when i try to open it i'll see it minimized on the panel for like less that a split second and then its gone

---

### Post by Helios1276 on 2008-10-06
Are you saying that you can't get the effects to stay? try alt+f2 'emerald --replace' or is it 'compiz --replace'. Been away too long ;)

---

### Post by Therion on 2008-10-06
Open Synaptic.

Search on **compizconfig-settings-manager**.

Either remove it and reinstall the package; or simply mark it for re-installation.

---

### Post by Hunter2034 on 2008-10-07
okay I tried to reinstall it and it still does the exact same thing.

And no, im trying to just open the settings but the window does not open.

---

