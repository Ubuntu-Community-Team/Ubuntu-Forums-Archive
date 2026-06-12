---
title: "Suspend works once then instantly resumes - Acer Revo"
date: 2010-03-16
forum: Hardware
---

### Post by colincliff on 2010-03-16
I have been struggling with this for a while now.

using both Ubuntu 9.10 and Kubuntu 9.10 i have a suspend/resume problem. On boot or after a hibernation i am able to get the unit to suspend correctly, but only once. The unit will suspend and resume when i want the first time, then anytime after that when i attempt to suspend the system it instanly resumes

the pm-suspend.log shows no problems, just an instant wake after 1sec or so.

is this a known problem? i was hoping the move from ubuntu to kubuntu would help but it seems no differnt. :(

---

### Post by ibuclaw on 2010-03-16
What type of motherboard, and what type of graphics card are you using?

You could also raise a bug on your issue.

See here for the stress testing script for suspend/resume.
[https://wiki.ubuntu.com/KernelTeam/SuspendResumeTesting](https://wiki.ubuntu.com/KernelTeam/SuspendResumeTesting)

Regards
Iain

---

### Post by colincliff on 2010-03-16
Its a Acer Revo nettop, so has a built in motherboard, the system has Nvidia ION graphics.

I'll try the stress test and report as a bug, thanks

---

### Post by ibuclaw on 2010-03-16
When you raise the bug report, can you also attach the output of:
```
lsmod
```
and the file:
```
/var/log/pm-suspend.log
```
to the bug.


(edit): See this report here: [https://bugs.launchpad.net/ubuntu/+source/linux/+bug/206952](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/206952)
It may be the same issue you are having, if you can confirm that.

Regards
Iain

---

### Post by colincliff on 2010-03-16
its definately the same behaviour as that bug ([https://bugs.launchpad.net/ubuntu/+source/linux/+bug/206952](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/206952)). Once complete suspend/resume, then all additional suspends result in the system resuming straight away.

i've not submitted a bug before, should i just add  my info to that one?

edit: i'm running the Nvidia Restricted drivers as a few people in the above bug seem to be

---

### Post by ibuclaw on 2010-03-16
> **colincliff said:**
> its definately the same behaviour as that bug ([https://bugs.launchpad.net/ubuntu/+source/linux/+bug/206952](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/206952)). Once complete suspend/resume, then all additional suspends result in the system resuming straight away.

i've not submitted a bug before, should i just add  my info to that one?

edit: i'm running the Nvidia Restricted drivers as a few people in the above bug seem to be

Adding your info to that one should be just fine.

If at all you need to raise a bug, [please read here]("https://help.ubuntu.com/community/ReportingBugs") on the appropriate ways of doing it.

I would suggest trying the Ubuntu Lucid LiveCD with the new Nouveau drivers, but am aware of other suspend issues with the driver. :)

Regards
Iain

---

