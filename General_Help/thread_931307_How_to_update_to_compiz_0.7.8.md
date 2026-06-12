---
title: "How to update to compiz 0.7.8"
date: 2008-09-27
forum: General Help
---

### Post by SandyM on 2008-09-27
Please tell me how can I upgrade to compiz fusion 0.7.8. I search the net and the only thing I got was tar ball file namely 'compiz-0.7.8.tar.gz'. But being a newbie I don't know how to use it. Isn't there any terminal command which directly download and install the latest compiz fusion edition.
Also tell if there is any repository to regularly update compiz fusion

---

### Post by el-mar01 on 2008-09-27
Compiz-Fusion 0.7.8 will be avaliable (via a third-party software source) for Ubuntu Intrepid Ibex which is coming out on October 30th.

---

### Post by Aiello on 2008-09-27
I'm not sure if 0.7.8 will be released for Hardy, but if it is, then here is how to get it(Note, it might not be as stable as the version that is currently built into Hardy):

1. Go to "system=> administration=> software sources"
2. Select the "third party software" TAB
3. Click on the "Add" button and add the following lines one by                
one:
```
deb http://ppa.launchpad.net/compiz/ubuntu hardy main
```
```
deb-src http://ppa.launchpad.net/compiz/ubuntu hardy main
```

4. Close the "software sources" by clicking on the close button
5 Cystem will ask you to reload the package information , choose to reload
6. Open "system=> administration=> update manager" and hit check for updates. If Compiz 0.7.8 is available for Hardy, it will appear as an update.

---

### Post by fingal12 on 2008-09-27
Hi if you trie this link [http://ubuntuforums.org/showthread.php?t=781218](http://ubuntuforums.org/showthread.php?t=781218)
you will get compiz 0.7.9. I have it and it works very well. 
Sorry for my poor english :(

---

### Post by Harry.k on 2011-11-21
after you add the repo, search for compiz in synaptic and update. That would be easier than updating everything

---

