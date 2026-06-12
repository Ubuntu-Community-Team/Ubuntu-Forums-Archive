---
title: "[SOLVED] Add/Remove Program List Empty"
date: 2008-12-20
forum: Installation &amp; Upgrades
---

### Post by DarKnyht on 2008-12-20
I started up ubuntu 8.10 this morning and was going to add an app, but when I went to the add/remove programs the list was empty.

Any advice on how to correct this?

---

### Post by lovelyvik293 on 2008-12-20
Try reloading the package list in the synaptic package manager.
Or i think you delete up all the software sources.

---

### Post by gb5757870 on 2008-12-20
Same problem here. Have tried reloading through synaptic and apt-get update. Still empty.

I presume a security update broke this?

---

### Post by Partyboi2 on 2008-12-20
try reinstalling gnome-app-install 
```
sudo apt-get --reinstall install gnome-app-install
```

---

### Post by gb5757870 on 2008-12-20
> **Partyboi2 said:**
> try reinstalling gnome-app-install 
```
sudo apt-get --reinstall install gnome-app-install
```

Thanks heaps, issue fixed for me. Any theories why this would happen?

---

### Post by DarKnyht on 2008-12-21
That also solved it for me.  Thanks.

---

### Post by eragon100 on 2008-12-22
Solved for me as well, thank you!

---

### Post by A*p on 2008-12-22
This just happened to me also, but the suggested fix worked, Thanks.

---

### Post by Milesey on 2008-12-22
This happened to me twice. Each tine, I'd just installed Adobe Air (in order to run the new BBC iPlayer Desktop application.

May be coincidental ???

Reinstalling using ...

 sudo apt-get --reinstall install gnome-app-install

... worked both times.

---

### Post by mrtorrent on 2008-12-23
I had the same problem, also solved by reinstalling. Like Milesey, the last thing I installed before the issue was Adobe Air and the new BBC iPlayer Desktop.

---

### Post by euchrid33 on 2008-12-23
Same thing happened to me.  You'll be shocked to learn that earlier today I installed Adobe Air.  At least we know what's causing it.  Any ideas why, though?

---

### Post by cms2337 on 2008-12-23
Thanks, ```
sudo apt-get --reinstall install gnome-app-install
``` worked for me.

---

### Post by MES5464 on 2008-12-23
> **euchrid33 said:**
> Same thing happened to me.  You'll be shocked to learn that earlier today I installed Adobe Air.  At least we know what's causing it.  Any ideas why, though?

Ok. Now I know what my problem is. I installed Adobe Air the other day and then just discovered my Add/Remove Apps was empty. Hmm. Thanks for the help.

---

### Post by johncolescarr on 2008-12-23
Also happened to me after installing adobe air and new bbc iplayer for unix based machines.  I'm sure its not a coincidence, but the fix worked a treat, thanks!!

---

### Post by Partyboi2 on 2008-12-23
Has anyone opened a [[COLOR=Blue]bugreport [/COLOR]]("https://bugs.launchpad.net/ubuntu")about this problem?

---

### Post by dekaru on 2008-12-25
> **Partyboi2 said:**
> Has anyone opened a [[COLOR=Blue]bugreport [/COLOR]]("https://bugs.launchpad.net/ubuntu")about this problem?


It's easy to do it yourself :)

[https://bugs.launchpad.net/ubuntu/+source/gnome-app-install/+bug/311455](https://bugs.launchpad.net/ubuntu/+source/gnome-app-install/+bug/311455)

---

### Post by Partyboi2 on 2008-12-25
> **dekaru said:**
> It's easy to do it yourself :)

[https://bugs.launchpad.net/ubuntu/+source/gnome-app-install/+bug/311455](https://bugs.launchpad.net/ubuntu/+source/gnome-app-install/+bug/311455)
I would have if I was suffering from the problem :) But thanks for opening the bug hopefully others that have had this problem can confirm the bug and maybe provide any extra info for it.

---

### Post by piojunbabia on 2008-12-26
I could not relate to the topic although i have almost the same problem... i posted a new thread and i need reply so that i could install YM and FF asap... the new thread is here:

[http://ubuntuforums.org/showthread.php?t=1021905](http://ubuntuforums.org/showthread.php?t=1021905) or
[http://ubuntuforums.org/showthread.php?t=1021905]("http://ubuntuforums.org/showthread.php?t=1021905")

---

### Post by rohit_kewlani on 2009-01-06
Just do `sudo update-app-install` and the cache would be updated.
We'll have it fixed in the upcomeing AIR release. Thanks for pointing this out.

Rohit Kewlani
Adobe AIR Linux Team

---

### Post by arm-c on 2009-01-11
I too installed Adobe Air... but I want to point out that I DID NOT INSTALL THE ADOBE iBBC Player.... although I did install the Adobe Player (and others).

Thanks for the post.  I would have never known about the connection to adobe Air install.  It NEVER happened to me when I was beta testing two or three PRE-RELeASE versions... something different in the release.  BUT I can say that there was a HUGE step in compatibility between the last pre-release and the final release.

CUDOs to the Adobe Team.

Now, where is the Acrobat Professional I need so desperately???  Seams like they would make one before some OpenSource developer creates a fabulous working version. :)

---

### Post by MilkSjeik on 2009-04-04
Same story, installed Adobe AIR, list empty, reinstalled, all ok now.

---

### Post by phil989 on 2009-04-15
Launchpad link:
[https://bugs.launchpad.net/gnome-app-install/+bug/311455](https://bugs.launchpad.net/gnome-app-install/+bug/311455)

It's a problem with AIR, to be fixed by Adobe in the next release.

---

### Post by f1ice on 2009-04-24
Thank you.  Problem solved for me.  Also happened after installed Abobe Air and BBC iPlayer.

---

### Post by andramaulana on 2009-07-02
Thank you so much for the solution. Problem appeared after I did an update and installed a couple of softwares on my Jaunty (via Wubi, fresh reinstall this morning)

I don't know about the AdobeAIR connection though, since I was joyfully using DestroyTwitter yesterday before I reinstalled Jaunty and nothing was wrong with the Add/Remove Application List.

Anyways, thanks again and kudos for the solution! ;)

---

