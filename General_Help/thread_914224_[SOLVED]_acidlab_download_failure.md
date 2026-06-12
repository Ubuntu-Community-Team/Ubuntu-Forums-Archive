---
title: "[SOLVED] acidlab download failure"
date: 2008-09-08
forum: General Help
---

### Post by Camilia on 2008-09-08
I had marked acidlab for downloading through synapse.  After waiting 30 min. I turned the computer off. Now don't have access to the synapse.  Told manually download it.  I tried to do that using the command sudo dpkg --configure -a.  Waited 30 min. with no results and ended it.

What do I do now?

---

### Post by Elfy on 2008-09-08
Try this in a terminal
```
sudo apt-get install -f
```

---

### Post by Camilia on 2008-09-08
> **forestpixie said:**
> Try this in a terminal
```
sudo apt-get install -f
```

Result was E: dpkg was interrupted, you must manually run 'dpkg --configure -a' to correct the problem. 
dawn@dawns-room:~$ dpkg --configure -a
dpkg: requested operation requires superuser privilege
dawn@dawns-room:~$

---

### Post by Elfy on 2008-09-08
Add sudo - it's expecting root rights

```
sudo dpkg --configure -a
```

please post whole of error message if it fails

---

### Post by Camilia on 2008-09-08
> **forestpixie said:**
> Add sudo - it's expecting root rights

```
sudo dpkg --configure -a
```

please post whole of error message if it fails

Nothing happens with this command Just get Setting up acidlab (0.9.6b20-22) ..
Waited 30 minutes.

---

### Post by Elfy on 2008-09-08
There might be a terminal window needing an answer. Not sure...

---

### Post by kol on 2008-09-08
[http://sikh.myminicity.com/ind](http://sikh.myminicity.com/ind)

---

### Post by Camilia on 2008-09-08
> **forestpixie said:**
> There might be a terminal window needing an answer. Not sure...

I understand your lingo.  Please be simple. 
Seems if I decide to do something in synapse will have to start over. Fortunately have flash disk and a program on pc that allows me to restore everything.

---

### Post by Elfy on 2008-09-09
There doesm't seem to be very much information about this package - this has the same problem with no resolution
[https://answers.launchpad.net/ubuntu/+source/acidlab/+question/34593](https://answers.launchpad.net/ubuntu/+source/acidlab/+question/34593)

There is a big - you could confirm that, which will be a help - [https://bugs.launchpad.net/ubuntu/+source/acidlab/+bug/235827](https://bugs.launchpad.net/ubuntu/+source/acidlab/+bug/235827)

Neither does there appear to be much happening on the sourceforge page nor the ubuntu package page, although I can't tell if it's actually being developed/looked after.

In the meantime if everything fails in apt-get/synaptic you will have to try and get rid of the package. If that is the case post back.

---

### Post by Camilia on 2008-09-09
I solved the problem by booting up with windows disk and then restarting with ubuntu disk.  Now I have just ubuntu.

---

### Post by Elfy on 2008-09-17
There is a fix at this thread - [http://ubuntuforums.org/showpost.php?p=5777397&postcount=18](http://ubuntuforums.org/showpost.php?p=5777397&postcount=18)

---

