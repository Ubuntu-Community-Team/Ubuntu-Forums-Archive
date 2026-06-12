---
title: "GDM login window???  HELP!!!"
date: 2008-09-16
forum: General Help
---

### Post by vurwolf on 2008-09-16
GDM (GNOME Display Manager) is not running

You might be using a different display manager, such as KDM (KDE Display Manager), CDE login (dtlogin), or xdm. If you wish to use this feature, then your system will need to be configured to use GDM instead.


QUESTION: How do I activate GDM?

Thanks

---

### Post by iaculallad on 2008-09-16
We just had covered this topic earlier. Try relating to this [thread]("http://ubuntuforums.org/showthread.php?t=921436"), second post.

---

### Post by vurwolf on 2008-09-16
> **iaculallad said:**
> We just had covered this topic earlier. Try relating to this [thread]("http://ubuntuforums.org/showthread.php?t=921436"), second post.

Didn't work. This is what i got.

brian@brian-laptop:~$ sudo dpkg-reconfigure gdm
debconf: DbDriver "config": /var/cache/debconf/config.dat is locked by another process: Resource temporarily unavailable

I tried the kdesu kate /etc/X11/default-display-manager 
I changed it to /usr/sbin/gdm and the error stll comes up.

---

### Post by vurwolf on 2008-09-16
I also got this too

brian@brian-laptop:~$ sudo dpkg --configure -a
dpkg: status database area is locked by another process

---

### Post by bodhi.zazen on 2008-09-16
Are you running another application such as synaptic or add/remove programs or update manager ? close those first and re-try.

---

### Post by EmanresuusernamE on 2008-09-16
Load Ubuntu into Failsafe/Recovery mode, (second boot option with a default install) then tell it to Repair X Server.  Then continue with load.

---

