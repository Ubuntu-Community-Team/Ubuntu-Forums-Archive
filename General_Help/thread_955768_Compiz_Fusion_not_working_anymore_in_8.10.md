---
title: "Compiz Fusion not working anymore in 8.10"
date: 2008-10-22
forum: General Help
---

### Post by XAVeRY on 2008-10-22
So, I installed the dist-upgrade from my 8.04 to the 8.10 two weeks ago or so. Couple days ago, compiz stopped working at all - it doesn't run automatically when the system boots up, and trying to enable the desktop effects in GUI effects in a failure.

This is what I get from the console when I try to run "compiz.real --replace" :
```
compiz.real (core) - Fatal: glXCreateContext failed
compiz.real (core) - Error: Failed to manage screen: 0
compiz.real (core) - Fatal: No manageable screens found on display :0.0
```

And this is the effect of "sudo compiz --replace" :
```
Checking for Xgl: not present. 
Detected PCI ID for VGA: 
Checking for texture_from_pixmap: not present. 
Trying again with indirect rendering:
Checking for texture_from_pixmap: not present. 
aborting and using fallback: /usr/bin/metacity 
```

My system is an AMD64 equipped with a GeForce 8600M GT and manually installed nvidia proprietary drivers, version 177.80 (latest as of today).

Compiz has always worked fine, until one upgrade after I had already upgraded to 8.10.

Thank you in advance for all your help,
D.K.

---

### Post by loomsen on 2008-10-22
Same setup, git-compiz working better than ever...

[url=http://ubuntuforums.org/showpost.php?p=5997471&postcount=6]
Here's how
[/url]

[And here you may obtain my X-layout as well as my xorg.conf](http://ubuntuforums.org/showthread.php?t=955056&page=2)

---

### Post by Tanker Bob on 2008-10-22
Curiousity question: Why do you need Compiz for 8.10? It has a composite manager built into it with quite a number of effects in the configuration settings.

---

