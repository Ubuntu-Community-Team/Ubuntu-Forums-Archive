---
title: "help installing vmware server 2.0..."
date: 2008-09-28
forum: General Help
---

### Post by Mia_tech on 2008-09-28
guys I've decided to upgrade my vmware server install to 2.0, but in the configuration process, I'm getting this error:
```
None of the pre-built vmci modules for VMware Server is suitable for your 
running kernel.  Do you want this program to try to build the vmci module for 
your system (you need to have a C compiler installed on your system)? [yes] 

```
which basically is telling me to get linux-headers, which I downloaded sometime ago...

any help appreciated

---

### Post by ThrobbingBrain66 on 2008-09-28
It's not really an error.  It's just saying that the module doesn't exist and wants to know if you'd like to build it.  What happens when you choose to build it?

---

### Post by Mia_tech on 2008-09-28
> **ThrobbingBrain66 said:**
> It's not really an error.  It's just saying that the module doesn't exist and wants to know if you'd like to build it.  What happens when you choose to build it?

is the new interface for vmware is the browser?... after installing it I did "sudo vmware",an it launched firefox, but it won't load the interface it sits there loading.. what is expected to do?

---

### Post by ThrobbingBrain66 on 2008-09-28
> **Mia_tech said:**
> is the new interface for vmware is the browser?... after installing it I did "sudo vmware",an it launched firefox, but it won't load the interface it sits there loading.. what is expected to do?

I remember reading something about a web interface in 2.0, but am not totally sure as I use Virtualbox for my virtualization.

You might want to try this link...it's instructions for installing 1.0.6 or 2.0 rc1, but I'm sure the same step apply for the final release.

[http://ubuntuforums.org/showthread.php?t=779934](http://ubuntuforums.org/showthread.php?t=779934)

---

### Post by Mia_tech on 2008-09-28
> **ThrobbingBrain66 said:**
> I remember reading something about a web interface in 2.0, but am not totally sure as I use Virtualbox for my virtualization.

You might want to try this link...it's instructions for installing 1.0.6 or 2.0 rc1, but I'm sure the same step apply for the final release.

[http://ubuntuforums.org/showthread.php?t=779934](http://ubuntuforums.org/showthread.php?t=779934)

wow, I'm completely lost with this interface, ... anyway how's your experience with virtualbox?

---

### Post by ThrobbingBrain66 on 2008-09-28
Virtualbox works really well for me.  I used nlite to strip XP down to a 1.5 GB base install.  It's so fast on my laptop's modest specs that I can barely tell it's a virtual machine.

The one thing I don't like is that it Virtualbox uses QT, so it doesn't quite theme correctly with GNOME.  Having said that, QT4 does a *much* better job at fitting in with GNOME than QT3 did.

---

### Post by Mia_tech on 2008-09-28
to be honest, after playing around a bit with the interface it's a big improvemnet over the past version, the interface looks better, and you have kind of a dashboard where you can monitor resources, also usb supports now works for a change, that was a problem in past versions of vmware for linux, that been said the install messed up my browsers bookmarks, and bookmark toolbar it's gone, thanks god for backups, other than that lol..seems to be better. I still would give a try to virtualbox :0)

---

