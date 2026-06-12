---
title: "Freeze when open or saving from application"
date: 2008-07-20
forum: General Help
---

### Post by roantreb on 2008-07-20
I've searched for solutions to this problem elsewhere but to no avail.


In a nutshell, when I open or save a file that requires me to choose a location (ie home/documents/College/) from an application, the application freezes for a few seconds.

I'm using Ubuntu Hardy with all updates installed. The problem only started during some stage of my hardy installation having upgraded form Gutsy. Unfortunately I'm unsure as to the first date of problem.


Any help greatly appreciated as problem severely irritating. The problem has occurred on firefox, open office, gimp and all other applications that I've tried, so its not app specific.


Regards
B

---

### Post by Dauthi4 on 2008-08-21
Hi,

Sorry if I'm late but I've experienced the same issue and I've found that it came with Tracker, because when I stopped it, the problem disappeared...

I think it's due to the "Search" option in the dialog windows ;-)

I hope that can solve your problem.

---

### Post by roantreb on 2008-08-21
FYI, disabling tracker seems to work. I'm not sure how to log a bug - any volunteers?



B

---

### Post by Fredo on 2008-09-03
I think this is due to a broken tracker index. For me, it helped to force tracker to rebuild the index:

```
killall trackerd
trackerd --reindex
```

But it really is a bug that tracker doesn't fix this by itself. There also is a bug report on launchpad: [https://bugs.launchpad.net/ubuntu/+source/tracker/+bug/196011](https://bugs.launchpad.net/ubuntu/+source/tracker/+bug/196011)

I hope this helps.

---

### Post by SergeyR on 2009-05-13
> **Fredo said:**
> ...I hope this helps.

I had a same problem. But your solution has helped. Instead of trackerd I called 
```
tracker-processes -r
```

---

### Post by deadcow on 2009-06-03
Dude, thank you so much, this problem was ticking me off to no end!
Cheerz!

I should add that the "tracker-processes -r" is the proper fix for this issue. And that My problem was with opening any "save" dialog. In any program, mainly firefox, if I clicked to save anything it would hang for a bit, then give me a selection area to save the file to a particular location. What a bummer, now it is fixed, many thanx!

---

### Post by PBrn46 on 2009-06-09
> **SergeyR said:**
> 
```
tracker-processes -r
```

Interesting... I'm running 9.04, and facing the same problem. Although I do not have a tracker-processes command available to me. Does anybody know why?

---

### Post by PBrn46 on 2009-06-09
Actually, I have it fixed. I simply did a
```
sudo apt-get remove tracker
sudo apt-get install tracker
```

I noticed that ...
```
sudo apt-get install --reinstall tracker
```
...does not work.

---

