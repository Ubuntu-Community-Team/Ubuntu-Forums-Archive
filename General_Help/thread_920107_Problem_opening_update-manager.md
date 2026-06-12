---
title: "Problem opening update-manager"
date: 2008-09-14
forum: General Help
---

### Post by mdotcomin on 2008-09-14
I am coming here from [http://ubuntuforums.org/archive/index.php/t-540938.html](http://ubuntuforums.org/archive/index.php/t-540938.html).

I followed the instructions in this mail thread. However I am not able to solve the problem. When I try to open the update-manager it fails with the same error:

mkshirsa@mkshirsa-laptop:~$ sudo update-manager 
[sudo] password for mkshirsa: 
/var/lib/python-support/python2.5/gtk-2.0/gtk/__init__.py:48: RuntimeWarning: tp_compare didn't return -1 or -2 for exception
  from gtk import _gtk
ImportError: could not import atk
Traceback (most recent call last):
  File "/usr/bin/update-manager", line 29, in <module>
    import gtk.glade
ImportError: cannot import name Widget from gtk


The only thing I didn't try is to manually uninstall atk which I had compiled few days back. I dont know how to do it.

Can you please help me?

Thanks,
Mayuresh

---

### Post by Pro-reason on 2008-09-14
> **mdotcomin said:**
> 


The only thing I didn't try is to manually uninstall atk which I had compiled few days back. I dont know how to do it.


If you manually installed something, all the files will be somewhere in /usr/local.  Find them and delete them.

---

### Post by Nicole on 2008-11-23
Did you ever find an answer to this? I'm struggling with the same problem...

---

