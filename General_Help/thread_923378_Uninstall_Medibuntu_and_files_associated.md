---
title: "Uninstall Medibuntu and files associated"
date: 2008-09-18
forum: General Help
---

### Post by NuNn DaDdY on 2008-09-18
I recently got the medibuntu package and repository's, however whenever I try to get online my browser attempts to open and then immediately closes.  Also, I tried to run a video test and apparently have problems with that now also.  How would I revert back to my settings previously and/or remove Medibuntu

---

### Post by NuNn DaDdY on 2008-09-18
Any Suggestions?

---

### Post by LowSky on 2008-09-18
Medibuntu shouldnt cause any of those issues, could you please post any errors firefox has when you start it from a terminal

the command to run from a terminal is firefox
Also what did you install with the medibuntu repos?

---

### Post by retrow on 2008-09-18
Most people (including me) get Medibuntu repository and packages for w32codecs (or w64 if you're on AMD). That shouldn't get in the way of firefox. The only package which seemed to have affect Firefox (in a good way) was msttcorefonts, which installed some ttf fonts that are normally used by Firefox.

Try:
```
sudo apt-get remove msttcorefonts
```

---

### Post by NuNn DaDdY on 2008-09-18
When I try to run firefox from the terminal I receive the following error message:

GnomeUT-Warning* :  While connected to session manager:  Authentication rejected, reason:  
None of the the authentication protocols specified are supported and host-based authentication failed.

Segmentation Fault



Also, whenever I try to restart my system so I can run windows the system toolbar to choose all the options disapears and all that is left is my desktop picture and icons so I have to shutdown the system by pressing the power button.

---

### Post by NuNn DaDdY on 2008-09-18
bump

---

