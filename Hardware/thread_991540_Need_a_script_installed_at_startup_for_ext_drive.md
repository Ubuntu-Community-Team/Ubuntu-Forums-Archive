---
title: "Need a script installed at startup for ext drive"
date: 2008-11-23
forum: Hardware
---

### Post by larrikin71 on 2008-11-23
k, i am running Ubuntu 8.10 on a AMD 64bit machine and loving it..!!!, but anyway i have a freeagent drive and after much research i have found a script which will mount the drive :

#!/bin/bash
if `mount | grep -q /media/freeagent`
then
        sudo umount /media/freeagent
else
        sudo mount /media/freeagent
fi


wat i would like to do is have this script installed at startup, or failing that have it made executable with a link on my desktop just to make things a little easier...
:KS

Strangely sometimes the drive will mount without me having to execute this script and sometimes it doesn't.....weird!

---

