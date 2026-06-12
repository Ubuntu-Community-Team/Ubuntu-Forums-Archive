---
title: "Hang after Partitioner"
date: 2005-12-26
forum: Installation &amp; Upgrades
---

### Post by askadefull on 2005-12-26
I am trying to install Ubuntu on an old compaq that runs Windows 98 and meets the system requirements for Ubuntu. The installation goes smoothly until the partitioner starts. The partitioner starts up, then there is a hang in the system. 
The Ctrl-Alt-F3 window gives me:

/dev/hdd: open failed: Input/Output error:
No volume groups found
Reading all physical volumes. This may take a while...

And then the system has no apparent activity.

Thanks for any help.

---

### Post by Luke771 on 2005-12-27
Well, I got a similar problem the firt time I tried to install Ubuntu.
The system is a two year-old 1600mhz 512-ram running WinXP.
After the partitioner, on "installing base system" it took a long time to get past 6%, and then the installation failed.
I did this a couple of times, then I found that the time zone setting i configured at the very beginning ("location" menu) did not match my hardware clock setting; when I installed everything all over again with the right time zone, then it worked.
It sounds strange, I know, and on the other hand why would someone install an OS with the wrong time zone set up, but that's what I did and I got the same error as you, that's the only reason why I'm answering; to tell you to check that, even if I know that probably that's not the problem... it may be it after all.
If not, well keep searching the forum and waiting for answers here, looks like you are not the only one getting that error and I guess that it can be caused by more than one problem, so I told you what it was for me.

---

### Post by Edward The Bonobo on 2005-12-27
Same problem...but, nope, my time zone is set to the same as I selected.

---

### Post by askadefull on 2005-12-27
I tried using 5.04 and that seemed to do the trick. Must be something with the 5.10 version.

---

### Post by Edward The Bonobo on 2005-12-28
Confirmed.  5.04 installed OK...although I tried the LiveCD first, and it didn't run.

5.04 still won't detect my serial mouse - but I think there's a known solution to that.

It looks lovely!  If only I could move my cursor.....:(

---

### Post by xsnslaine on 2006-01-03
i am having the same problem, i just done a search on bugzilla, has anyone raised this yet???

---

