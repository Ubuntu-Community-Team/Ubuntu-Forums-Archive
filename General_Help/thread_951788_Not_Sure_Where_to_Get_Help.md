---
title: "Not Sure Where to Get Help"
date: 2008-10-18
forum: General Help
---

### Post by dcampbell on 2008-10-18
So, I have a problem, it's repeatable, I think I have an idea of what's causing it, but I'm still not sure which forum/where to get help.

I want to not have X start automatically, but manually start it when needed.   So I removed gdm from run levels 2, 3, 4, 5.  I login and I type "startx" and everything loads just fine.  But when I start NetBeans, instead of a splash screen, with the loading bar.  It just starts after about a minute.  And it will constantly freeze not allowing me to type anything.  If I put gdm back into runlevels 2, 3, 4, 5, NetBeans works perfectly.

This is repeatable for Netbeans 6.1 and Netbeans 6.5 Beta,  I'm running 64 bit kernel, with a 32 bit Sun JDK.  

I think it has something to do with file permissions.  The reason is that when I first turned off gdm, I had trouble killing X at all.  I solved this problem because my .Xauthority file was owned by root and now me.  After that X started and stopped fine.

I installed both Netbeans versions by downloading the installer off their website and running the installer without root access (both installed in home directory).  

I'm not sure if I should be on some NetBeans specific site looking for answers.  If I should be here, or Someplace that deals with problems with X.  But I don't know where to go from here.

---

