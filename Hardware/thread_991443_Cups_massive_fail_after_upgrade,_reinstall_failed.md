---
title: "Cups massive fail after upgrade, reinstall failed"
date: 2008-11-23
forum: Hardware
---

### Post by ironslave on 2008-11-23
Ok, so i upgraded to Intrepid and now Cups is broken, i Removed cups and reinstalled it but it still wont run.

init.d is missing cups/cupsys. all it has is cups.dpkg-new and no other cups files, how am i supposed to run cups if theres nothing to start it! ive been trying to fix this for days!!!!!! any help would be appreciated :(

---

### Post by ironslave on 2008-11-26
anyone :(

---

### Post by nzadLithium on 2008-11-28
hmm i'm not sure if this is the same problem, but everytime I install cups it breaks dpkg, i saw a bug report about this so i'm hoping it will be fixed sometime soon. Its possible that cups isn't loading on your pc for the same reason (if its not installed properly it probly won't run XP) can you try installing cups from the commandline? See if apt-get dies on you and tells you dpkg needs to be reconfigured? :D

---

### Post by ironslave on 2008-11-28
thanks for the input! i will try it and report back

---

### Post by ironslave on 2008-11-28
Problem solved!

heres what i did

```
 sudo apt-get remove cups
sudo apt-get clean cups 
```

Next we will open nautilus

```
 sudo nautilus file:///etc/init.d 
```

look for a symbolic link called cups and delete it if it exists (it would link to cupsys)

close nautilus 

```
 sudo apt-get install cups 
```

open up your web brower and type in:
```
 http://localhost:631/ 
```

if cups interface shows then you have success


the cups install isnt breaking my dpkg though, you should give this a shot

---

### Post by nzadLithium on 2008-11-29
Nope didn't work XD but your problems fixed, and mine has a bug report, so theoretically there should be a fix for my prob in some future update (i hope) :D

---

### Post by ironslave on 2008-12-19
sorry it didnt help :( did you try restarting after 

```
  sudo apt-get remove cups
sudo apt-get clean cups 
```

---

### Post by bdoe on 2008-12-20
> **nzadLithium said:**
> hmm i'm not sure if this is the same problem, but everytime I install cups it breaks dpkg, i saw a bug report about this so i'm hoping it will be fixed sometime soon. Its possible that cups isn't loading on your pc for the same reason (if its not installed properly it probly won't run XP) can you try installing cups from the commandline? See if apt-get dies on you and tells you dpkg needs to be reconfigured? :D
Very interesting!  I wonder if this is related to a strange issue I had this morning...

Update manager told me an update was available. I clicked on the notification icon as I always do, and it told me that, due to "problems", only a partial upgrade could be performed. The update was a kernel bump to 2.6.21.11 (yes, I have both the backport and proposed repos set). I let update manager do its thing, then went back to check on the updates it could not install. They were the Linux-Restricted modules. Installing them went fine, but it took out package "cups-pdf", which I reinstalled after everything else was done. Apt shows no dependency issues or broken packages, so that was a bit of a brain-scratcher for me.

---

### Post by ironslave on 2008-12-21
ive been having problems with performing Updates in the same maner as well. 

one of the weirder things ive run into was when when my extra printer drivers i had installed were uninstalled when i performed an apt get over the commandline!?

I do belive i had attempted to remove them with synaptic earlier that month and it failed. I was to lazy to try to remove it again.

---

