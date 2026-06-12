---
title: "[SOLVED] How do I put home on a seperate partition during install of 8.10"
date: 2008-11-02
forum: General Help
---

### Post by LeeHamo on 2008-11-02
I really want to do this so any future updates or releases I can do without worrying if ill delete any precious data.

Lee.

---

### Post by Mr_JMM on 2008-11-02
When you install Ubuntu, where you select partitions, create the partition you want as /home then go to the drop down box that lists the mount points and select /home

---

### Post by eternalnewbee on 2008-11-02
When you are in the partitioner, and suppose you make two partitions, choose "/" for the first partition, and "home" for the second. That way your system, when you want to update it, will be in "/".
There you go.

---

### Post by LeeHamo on 2008-11-02
sounds easy enough, thankyou ill try that and let you know how it went.

---

### Post by ugm6hr on 2008-11-02
In the Manual partitioner (or in GParted on LiveCD prior to installing - easier GUI):

create 3 partitions:
"/" ext3 (about 5-10GB)
"/home" ext3
"swap" Linux swap (about 3xRAM or 1GB)

---

### Post by LeeHamo on 2008-11-03
Thankyou all I done what was said in the last post but now how can I check it has worked? How can I check the partitions are in place and if i reinstall i wont wipe my home folder?

I created /home about 230gb and / 15gb on ext3 as logical partitions and a 2gb swap logical.

When I go into disk useage analyser I get this:

[ATTACH]90986[/ATTACH]

the drive is 250gb

---

### Post by LeeHamo on 2008-11-03
Ok maybe i have done something wrong here...

Check this picture of system monitor..

[ATTACH]90988[/ATTACH]

Whats the bottom one all about and where is my swap?

---

### Post by ugm6hr on 2008-11-03
Easiest (GUI) method to review your partitions is with GParted (Partition Editor).

```
sudo aptitude install gparted
```

Then go to System->Administration->Partition Editor.

But it looks like everything (well, at least / and /home) is fine.

If you do reinstall - remember to backup anyway (it's good practice), and use the "manual" installation method, and select each partition to be mounted the same as at present, and **make sure you leave the "format" box unticked for /home.**

---

### Post by LeeHamo on 2008-11-03
Thanks for the reply why do you think disk useage analyser is giving me diff results?

do you know what the bottom one is on the system monitor?

How come i cant see swap?

---

### Post by LeeHamo on 2008-11-03
Here is an image of Gparted results.

[ATTACH]91005[/ATTACH]

Does it look ok?

Lee.

---

### Post by ugm6hr on 2008-11-03
> **LeeHamo said:**
> Does it look ok?

It looks exactly as you intended.

And the other GUI's are correct too.  They tell the same story - just from a different viewpoint.

---

### Post by LeeHamo on 2008-11-03
Thankyou very much you are an absolute legend.

Thanked.

Lee.

---

