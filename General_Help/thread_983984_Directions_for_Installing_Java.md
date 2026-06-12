---
title: "Directions for Installing Java"
date: 2008-11-16
forum: General Help
---

### Post by Freiberg on 2008-11-16
When I tried to install Java on my computer, I was unable to find complete directions to install it.  I looked on the Java website, but it was missing part of the directions (I think).  [http://www.java.com/en/download/help/5000010500.xml#rpm](http://www.java.com/en/download/help/5000010500.xml#rpm)

I looked on the forums, but did not see anything.  If someone could give me directions, redirect me to a link, or give me another way to install Java, I would be grateful.

---

### Post by giuspen on 2008-11-16
put into the terminal:

sudo apt-get install sun-java6-plugin

if it's not enaugh system--administration--synaptic package manager and check all java packages available (with descriptions)
regards.

---

### Post by Freiberg on 2008-11-16
> **giuspen said:**
> put into the terminal:

sudo apt-get install sun-java6-plugin

if it's not enaugh system--administration--synaptic package manager and check all java packages available (with descriptions)
regards.

When I tried sudo apt-get install sun-java6-plugin, I got their terms and conditions, which I was unable to say ok to, for the simple reason that clicking the button did nothing, pressing enter did nothing, typing "Ok" did nothing, and exiting only restarted the whole process.

When I tried to open package manager, I got the error message: 

E: dpkg was interrupted, you must manually run 'dpkg --configure -a' to correct the problem. 
E: _cache->open() failed, please report

Any command I should run to give you more information?

---

### Post by Freiberg on 2008-11-16
Ok, this is starting to worry me.  Package manager was working before, but is now inoperative.  My update manager was also working, but now gets the same error message as the package manager, possibly due to my not being able to uncheck the update called "sun-java6-jre". Flash Player is not working either, even though it was working earlier, and I am unable to reinstall it because my package installer is not working.  Any ideas?

---

### Post by taurus on 2008-11-16
Shut down the package manager.  Then, open a terminal and type

Applications -> Accessories -> Terminal
```
sudo dpkg --configure -a
sudo apt-get update
```

---

### Post by jamesstansell on 2008-11-16
> **Freiberg said:**
> When I tried sudo apt-get install sun-java6-plugin, I got their terms and conditions, which I was unable to say ok to, for the simple reason that clicking the button did nothing, pressing enter did nothing, typing "Ok" did nothing, and exiting only restarted the whole process.


Some people have reported the same problem, and were able to accept the licence by pressing the tab key.  (And then presumably enter to accept the OK.)

---

