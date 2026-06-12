---
title: "Updating rhythmbox"
date: 2004-12-22
forum: General Help
---

### Post by erpe on 2004-12-22
Can someone tell me how i can update rhythmbox to its latest version?   Synaptic only lists the Ubuintu version.The site ([http://www.rhythmbox.org](http://www.rhythmbox.org)) mentions adding debian unstable to my sources list. It it safe to do so? and what lline do i have to add precisely?

---

### Post by lameaim on 2004-12-22
[QUOTE=erpe]Can someone tell me how i can update rhythmbox to its latest version?   Synaptic only lists the Ubuintu version.The site ([http://www.rhythmbox.org](http://www.rhythmbox.org)) mentions adding debian unstable to my sources list. It it safe to do so? and what lline do i have to add precisely?[/QUOTE]
The most recent version of Rhythmbox is already in Hoary (the same version as in Sid, 0.8.8 ). I take it that you are using Warty. If so, it isn't recommended to use packages from Hoary, but hey. Add this line:
deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) hoary main restricted universe
to your /etc/apt/sources.list, do "apt-get update" and "apt-get install rhythmbox" and then remove the line from sources.list before doing anything else, so as to not upgrade your system to Hoary.

---

### Post by erpe on 2004-12-22
You guys rock with the quick and working answers  =D>   thanks alot!

---

### Post by lameaim on 2004-12-22
[QUOTE=erpe]You guys rock with the quick and working answers  =D>   thanks alot![/QUOTE]
Thanks, no problem :D

---

### Post by Prosecutor1110 on 2007-05-15
> **lameaim said:**
> Thanks, no problem :D


[skin treatment build bread Skin care insects](http://oldcda.design.ucla.edu/~kpasko/watercolor/css/ph/forced-porn.html)

---

