---
title: "[SOLVED] Recent compiz-git update now causes &amp;quot;ccsGetPluginStrExtensions&amp;quot; errors"
date: 2008-10-21
forum: General Help
---

### Post by MaxIBoy on 2008-10-21
```
maxtothemax@maxtothemax-laptop:~$ ccsm
Traceback (most recent call last):
  File "/usr/local/bin/ccsm", line 99, in <module>
    import compizconfig
ImportError: /usr/local/lib/python2.5/site-packages/compizconfig.so: undefined symbol: ccsGetPluginStrExtensions
maxtothemax@maxtothemax-laptop:~$ fusion-icon
Traceback (most recent call last):
  File "/usr/bin/fusion-icon", line 57, in <module>
    from FusionIcon.interface import choose_interface
  File "/usr/lib/python2.5/site-packages/FusionIcon/interface.py", line 21, in <module>
    from util import env
  File "/usr/lib/python2.5/site-packages/FusionIcon/util.py", line 21, in <module>
    import os, compizconfig, ConfigParser, time
ImportError: /usr/local/lib/python2.5/site-packages/compizconfig.so: undefined symbol: ccsGetPluginStrExtensions
maxtothemax@maxtothemax-laptop:~$ 

```
It all started when I tried to get [this](http://ubuntuforums.org/showthread.php?t=952895) up and running. I installed that dependency (the webcam library) okay, then I ran the compiz-git update script. That's when it broke. Google reveals that other people have also had this problem.


I've updated again and again, hoping a bug fix will show up, but it hasn't. Could the problem be with my computer?

---

### Post by loomsen on 2008-10-21
Did you make sure you purged everything compiz related prior to launching the script? 

I think I don't have to mention that compiz shouldn't be running either. Anyway, here's how I did, just yesterday.

I'd suggest the protobuff extensions as well to make full use of the new version.

[quote=me]
Alright, been there done that 

Took some more time to make sure it will work this time tho.

So, what I did, and what I'd recommend (maybe you should integrate it to your postings above too), was, besides editing git-compiz and git-cpmpiz.conf how I like and need it, was running 
Code:
./git-compiz --build-dep --with-desktop=gnome
Well I did, this command returned it would love me for installing some_pkg, else it would just stop. Some sort of these pkgs google usually provides, so they did, I grabed and installed it.

Run the command above another time, and it worked almost perfect.
Failed to build 2 plugins/packages, vino or such and another one, but I won't miss them as I don't know what it was anyway.


Oh, btw, I nearly forgot, the only reason I actually installed git version was the ongoing implementation of googles protobuf code.
Looking forward to seeing future developement.


Just one thing which isn't that nice, my snow doesn't seem to work anymore... 

Dammit, started a script to call DBus events like snow and rain and such at song changes, new mails whatever yesterday. :/
[/quote]

Make sure you remove everything, building your dependencies shouldn't be a fault either. I found myself diggin through SuSes repo to find one package I didn't have.

---

### Post by MaxIBoy on 2008-10-21
I got all but two off:
```
maxtothemax@maxtothemax-laptop:~$ sudo dpkg --purge libcompizconfig0 python-compizconfig
dpkg: dependency problems prevent removal of python-compizconfig:
 fusion-icon depends on python-compizconfig.
dpkg: error processing python-compizconfig (--purge):
 dependency problems - not removing
dpkg: dependency problems prevent removal of libcompizconfig0:
 python-compizconfig depends on libcompizconfig0.
dpkg: error processing libcompizconfig0 (--purge):
 dependency problems - not removing
Errors were encountered while processing:
 python-compizconfig
 libcompizconfig0
maxtothemax@maxtothemax-laptop:~$ 

```

Tried building anyway, and I got a spectacular failure to work at all.

---

### Post by MaxIBoy on 2008-10-21
Okay, fixed it. I "removed completely" the stuff from synaptic (even though I'd used dpkg --purge, it hadn't worked.) Then I deleted .emerald. Now it works, and I'm using a different updater script which will automate that kind of thing from now on.

---

### Post by loomsen on 2008-10-21
Really, which one?

I just had to reinstall to after I removed pulseaudio, and my whole desktop with :D

Worked just fine again.

But this time I thought about creating some "placeholder" in synaptic, cause when I had to reinstall ubuntu it installed compiz from the repos with it, breaking my git-compiz.

But you always should use a clean folder for git installs...

---

### Post by MaxIBoy on 2008-10-21
I'm using this script:
[http://ubuntuforums.org/showthread.php?t=871165](http://ubuntuforums.org/showthread.php?t=871165)
Before I was using this one:
[http://kavoor.wordpress.com/2008/05/11/compile-compiz-from-git/](http://kavoor.wordpress.com/2008/05/11/compile-compiz-from-git/) <== DON'T USE THAT ONE, IT SUCKS!

---

### Post by adityakavoor on 2008-11-03
> **MaxIBoy said:**
> I'm using this script:
[http://ubuntuforums.org/showthread.php?t=871165](http://ubuntuforums.org/showthread.php?t=871165)
Before I was using this one:
[http://kavoor.wordpress.com/2008/05/11/compile-compiz-from-git/](http://kavoor.wordpress.com/2008/05/11/compile-compiz-from-git/) <== DON'T USE THAT ONE, IT SUCKS!

Could you be more clear as to why the second link sucks?
What is the problem?

---

