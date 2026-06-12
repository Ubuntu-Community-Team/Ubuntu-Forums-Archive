---
title: "Nvidia driver problems..."
date: 2008-08-11
forum: General Help
---

### Post by colonelsanders15 on 2008-08-11
Hey all, I tried to install the latest Nvidia driver on Ubuntu for my 8600m gt, and when i went to restart gnome, it didn't work. I think the problem was that I had already gotten some kind of Nvidia driver automatically from the Ubuntu updater, and these drivers were conflicting, but I'm not sure. So I edited the configuration file so I could use my old setup (nv is the old, nvidia is new), now it all works, except compiz isn't working. How can I check my current driver version, and how can I get Compiz and Emerald back up and running?

,Thanks

---

### Post by Crafty Kisses on 2008-08-11
Post the following output of:
```
glxinfo
```
Then in Terminal try running:
```
compiz
```

---

### Post by colonelsanders15 on 2008-08-14
ok, thanks, I disabled the driver ubuntu automatically installed, and installed the one i want, and it works great, its just that every time i restart, it doesn't recognize hardware, goes back to default driver, then I have to reinstall again.

---

### Post by tuxxy on 2008-08-14
search in synaptic for glx and there should be two listed a glx and a glx-new, remove either you have installed fully. 

Now enable the driver supplied at system > admin > hardware drivers

---

### Post by liam j dyer on 2008-08-14
[http://www.rewards1.com/index.php?referrer_id=89832](http://www.rewards1.com/index.php?referrer_id=89832)

rewards1 is a website where you fill out surveys for points from 0-4 each point is worth $1 and you can spend the money on what ever you want like a..ps3,ps2,psp,nintendo wii,ds,dildo if you really wanted :lolflag:

http://www.xtremetop100.com/in.php?site=1132252565[/url][/U][/B]

if you used the first link and liked it or using it then vote for it at the second link thanks XD

please vistit them and help me thank you XD

---

### Post by colonelsanders15 on 2008-08-16
thanks for the replies.. I don't see a glx or glx-new package in synaptic when I install the driver via the .run file. But it works fine, except that i have to reinstall it every time i restart my computer, its like its not loading the driver on start up or something, when i install the driver it asks me if it wants me to modify the x config file, and I say yes, so maybe it's not saving? I'm not sure why the driver doesn't work at startup..

---

### Post by colonelsanders15 on 2008-08-17
nvm i got it now, to anyone else having this problem look here:[http://ubuntuforums.org/showthread.php?t=724200](http://ubuntuforums.org/showthread.php?t=724200)
,Thanks

---

