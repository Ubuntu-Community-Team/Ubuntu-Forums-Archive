---
title: "How to remove deb package?"
date: 2005-11-09
forum: General Help
---

### Post by lehardi on 2005-11-09
Some time ago I've installed cedega and point2play deb packages. Now I want to remove these packages, but apt-get says that there aren't such packages installed. It's strange 'cos they are installed and I can run them as other normal programs. I've tried:
apt-get remove point2play
and
apt-get purge point2play
Nothing. What can I do? How can I check if these packages are in deb package database?
-- 
LeHardi

---

### Post by earobinson on 2005-11-09
man dpkg i think there is an uninstall option  (not on linux right now)

---

### Post by Arktis on 2005-11-09
If you use synaptec, you can click the status button on the lower left and choose the 'Installed (local or obsolete)' category from the left side pane.  cedega and point2play should show up...

---

### Post by earobinson on 2005-11-09
I think we can assume since apt-get can not remove it synaptic cant since synaptic is just a gui for apt-get

---

### Post by Arktis on 2005-11-09
Meh, my internet connection just dropped, but I was gonna add that if it didn't show up in synaptec, that there is a possibility he didn't install it with a .deb and just simply forgot.

---

### Post by earobinson on 2005-11-09
[QUOTE=Arktis]Meh, my internet connection just dropped, but I was gonna add that if it didn't show up in synaptec, that there is a possibility he didn't install it with a .deb and just simply forgot.[/QUOTE]
that is possiable never thought of that. (sorry if i sounded harsh)

---

### Post by lehardi on 2005-11-09
Yes, it didn't show in synaptic :) , but it's installed with deb - when I'm trying to install a new cedega version I'm getting error about conflict with point2play-small: 
"point2play-small (version 2.0.3) is installed". Besides I've installed point2play deb package 6 days ago and I remember it. :) Maybe --force-architecture option caused this situation?
-- 
LeHardi

---

### Post by az on 2005-11-09
dpkg -l |grep Point

dpkg -l |grep cedega

(they use capitals, I think)

If it is installed, though, it should show up in synaptic.

anyway, to remove a package with dpkg, use

dpkg -r (packagename)

Ex:
sudo dpkg -r mozilla-firefox

---

### Post by lehardi on 2005-11-09
[QUOTE=azz]
Ex:
sudo dpkg -r mozilla-firefox[/QUOTE]

Thanks! It solved my problem (BTW it's point - not Point:) )
-- 
LeHardi

---

### Post by Arktis on 2005-11-09
Boy, that is strange!  What conditions would cause dpkg not to add a package to the database?  And yet it's still aware of the package since it can remove it.  Is there a separate package database or does dpkg just keep it's own records in a file somewhere (more likely IMO)?  Should a bug report be filed?

**earobinson:** My pride may have been injured, but there is no need for appology.  I should have remebered the fact you reminded me of, but I didn't.

---

### Post by earobinson on 2005-11-10
It boggles the mind

---

