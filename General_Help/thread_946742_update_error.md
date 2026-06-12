---
title: "update error"
date: 2008-10-13
forum: General Help
---

### Post by metalmaniac248 on 2008-10-13
i get this error when i try and update hardy

```

W: Failed to fetch http://giss.tv/~vale/ubuntu32/./libquicktimehv_2.1.0-2svn20080707ubuntu_i386.deb
  404 Not Found
```



any ideas?

---

### Post by drs305 on 2008-10-13
If you go to the site you will see that there are no '2008' packages currently listed. Why they were removed or whether they will be restored is a question I cannot answer.

[http://giss.tv/~vale/ubuntu32/]("http://giss.tv/~vale/ubuntu32/")

---

### Post by metalmaniac248 on 2008-10-13
could this be the cause of me not be able to get my nvidia dirvers?

---

### Post by drs305 on 2008-10-13
That doesn't appear to be a site you should be getting official nvidia drivers from. The 'failed to fetch' looks like it was trying to download some sort of Quick Time deb. 

For nvidia drivers, there are those listed in synaptic, you can install EnvyNG (envyng-gtk - also in synaptic) and let it download and install the drivers, or go to the nvidia site directly and complile the drivers yourself (I don't know if they have .deb packages but doubt it).

I would recommend the first or second option. There are threads in these forums that describe how to do it.

---

### Post by metalmaniac248 on 2008-10-13
```
E: python-awn: subprocess post-installation script returned error exit status 1
E: awn-manager: dependency problems - leaving unconfigured
E: avant-window-navigator: dependency problems - leaving unconfigured
```



i get this error when installing anything from synaptic however the software usually installs

---

### Post by Bluebell392 on 2008-10-13
It appears that there are dependency problems. Locate the packages in question, right click on them, and choose properties. Click on the dependencies tab, make sure that there are no problems.

---

### Post by metalmaniac248 on 2008-10-13
how wud i locate the packages

sorry just figured that out

---

### Post by metalmaniac248 on 2008-10-13
wot shud i be looking for

---

### Post by Bluebell392 on 2008-10-13
You should be looking for the dependencies of the packages that fail to install. In your case, awn-manager and avant-window-navigator have dependency problems, and you should try those packages and any others that report having dependency problems.

---

### Post by metalmaniac248 on 2008-10-14
well as far as i can tell ther are no porblems however i dont think this error is actually causing any problems for me

---

