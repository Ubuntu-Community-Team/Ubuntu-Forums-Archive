---
title: "Enabling advanced desktop effects"
date: 2008-09-11
forum: General Help
---

### Post by ShOuT1 on 2008-09-11
I've been trying to figure this out since I installed ubuntu a week ago.  Whenever I try to enable advanced desktop features I get an error message saying " Can not enable advanced effects ".  I have been reading that this has something to do with my gpu driver.  I even followed these steps from this ubuntu docs page [https://help.ubuntu.com/community/RadeonDriver](https://help.ubuntu.com/community/RadeonDriver).
By the way I am running on a Dell Latitude D600 and my gpu is a Radeon RV250 9000

any ideas are appreciated thanks.

---

### Post by Freiberg on 2008-09-11
I have the same problem, and am just looking around for a solution now.  I have a 64-bit Gateway M6862, and am not sure how to find out what my gpu is.

---

### Post by Another Monkey on 2008-09-11
> **ShOuT1 said:**
> By the way I am running on a Dell Latitude D600 and my gpu is a Radeon RV250 9000

any ideas are appreciated thanks.
I am another newb, but I am running the effects on a lappy with the exact same card.  This is what I did:
0. Nothing.  No fancy drivers or other gubbins.  Just installed straight from the CD.
1. Update from all repositories using "Synaptic Package Manager" under "System/Administration" (do this via "Settings/Repositories", I enabled the CD one (lower part of first tab) and the Canonical partner (top one) on the Thirdparty tab).
2. Also install the compizconfig-settings-manager (plus the python dependency).
3. Your card, like mine, is blacklisted, so you need to tell compiz to skip its blacklist check and just go for it.  This is a simple little command:
```
mkdir -p ~/.config/compiz/ && echo SKIP_CHECKS=yes >> ~/.config/compiz/compiz-manager
```

Then reboot (you'll probably need to after the full update anyway).

Then try to enable the effects and see if they take (the cube etc can be enabled using System/Preferences/Advanced Desktop Settings).  If it's working, you can expect to get a frame rate of about 100fps, that's what I get and it's pretty good (it's twice as fast as the 4GB Dell GX270 which I chucked Ubuntu on to today).

If you need more help from people who actually know what they are doing, then [look here]("http://ubuntuforums.org/showthread.php?t=764633"), it's a good place to start.  Or just look at my more recent posts (I've been going through this pain).

As for what GPU etc you have, I gave a full list of mine [here]("http://ubuntuforums.org/showthread.php?t=913803"), along with the commands to get them.  If you have trouble, this info can help the real experts.

HTH!

(Crikey, I think I just answered my first question!)

---

### Post by ShOuT1 on 2008-09-11
Freiberg:  use the command lspci | grep VGA
lspci displays your hardware, grep searches for patterns in files, the | means pipe to another command.  very powerful.

---

### Post by ShOuT1 on 2008-09-12
Another Monkey: Thanks, that totally worked, it was so simple compared to all the things i have read and been told.  You rock!

---

### Post by Another Monkey on 2008-09-12
Glad to be of service.  As fellow newb I assume a knowledge level of zero (like me).  My one criticism some posts on here is that they assume you already know Linux.

If I (we?) already knew Linux, I wouldn't be asking simple questions!

---

### Post by Shadow stewart on 2008-09-12
If you want windows vista effects in windows xp then install application named CrystalXP bricopack, with this application you can change icons, visual effects, themes and much more.


[Outsourcing Solution in BPO](http://www.iwaayconsultant.com)

---

