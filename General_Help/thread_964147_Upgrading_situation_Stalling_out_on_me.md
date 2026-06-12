---
title: "Upgrading situation? Stalling out on me?"
date: 2008-10-30
forum: General Help
---

### Post by emoric on 2008-10-30
Here, take a look.

[IMG]http://i33.tinypic.com/2qwzgb4.png[/IMG]

I've been stuck on that screen going on about 15 minutes now.

Is this bad? What should I do? I don't want to interrupt the upgrade process and end up with an un-bootable ubuntu. :confused:

---

### Post by ju2wheels on 2008-10-30
Click on the triangle next to terminal and what is the output? I recall this happening to me after a regular update when I was using the Alpha 6 and I just manually rebooted and then ran Synaptic afterwards to make sure there werent any problems.

There are some old threads discussing this, I dont have them handy, but for the most part restarting shouldnt cause you any problems.

---

### Post by emoric on 2008-10-30
Well, terminal says..

'ldconfig deferred processing now taking place'


If I can reboot with no problem, then I will do.

I would just like to confirm :lolflag:

---

### Post by ju2wheels on 2008-10-30
Heres the link to the thread where I had the same issue [http://ubuntuforums.org/showthread.php?t=941515](http://ubuntuforums.org/showthread.php?t=941515) . I just rebooted my machine and ran Synaptic and then in a command line 

```

sudo dpkg --configure -a

```

Just to make sure everything got configured properly. Restarting left no visibile problems whatsoever and everything worked fine.

---

