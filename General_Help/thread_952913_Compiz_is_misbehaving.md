---
title: "Compiz is misbehaving"
date: 2008-10-19
forum: General Help
---

### Post by Samueltehg33k on 2008-10-19
so i decided to install compiz today so i did including XGL and it seems none of it works i enable what i wanted out of the advanced desktop settings and none of the effects do anything :/ i restartede my comp and reinstalled everything still no chance any help?

---

### Post by aashay on 2008-10-19
> **Samueltehg33k said:**
> so i decided to install compiz today so i did including XGL and it seems none of it works i enable what i wanted out of the advanced desktop settings and none of the effects do anything :/ i restartede my comp and reinstalled everything still no chance any help?

run ```
compiz --replace
```in a terminal and post the output. Better yet, plug the error message (assuming you get one)from the output into google. Chances are very bright that you can get a fix for it on the web.

---

### Post by Samueltehg33k on 2008-10-19
> **aashay said:**
> run ```
compiz --replace
```in a terminal and post the output. Better yet, plug the error message (assuming you get one)from the output into google. Chances are very bright that you can get a fix for it on the web.
samuel@samuel-desktop:~$ compiz --replace
Checking for Xgl: not present. 
No whitelisted driver found
aborting and using fallback: true 
no true found, exiting
samuel@samuel-desktop:~$ 

hmmmm its not detecting my install of XGL

---

### Post by EnGorDiaz on 2008-10-19
> **Samueltehg33k said:**
> samuel@samuel-desktop:~$ compiz --replace
Checking for Xgl: not present. 
No whitelisted driver found
aborting and using fallback: true 
no true found, exiting
samuel@samuel-desktop:~$ 

hmmmm its not detecting my install of XGL

your drivers are blacklisted have you tryed going to hardware drivers? in ur admin

---

### Post by kdub432 on 2008-10-19
Make sure your composited environment is setup properly. This is not an issue with compiz, but an issue with the underlying graphics environment you have set up. You need a working 3d accelerated graphics card with proper driver installed and configured, as well as an X server that is capable of compositing. Seeing as most modern Xserver versions do have this functionality, you are more likely than not seeing a problem with the installation of your graphics card. Specifics as to the type of card you have will be helpful.

---

### Post by Samueltehg33k on 2008-10-19
> **kdub432 said:**
> Make sure your composited environment is setup properly. This is not an issue with compiz, but an issue with the underlying graphics environment you have set up. You need a working 3d accelerated graphics card with proper driver installed and configured, as well as an X server that is capable of compositing. Seeing as most modern Xserver versions do have this functionality, you are more likely than not seeing a problem with the installation of your graphics card. Specifics as to the type of card you have will be helpful.
the strange thing is its only happening in xubuntu in my GNOME version of Ubuntu, Fedora, and gOS compiz works fine

---

