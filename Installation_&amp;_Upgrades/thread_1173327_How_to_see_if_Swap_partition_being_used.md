---
title: "How to see if Swap partition being used?"
date: 2009-05-29
forum: Installation &amp; Upgrades
---

### Post by Nima1972 on 2009-05-29
I'm trying to see if Jaunty is using the swap partition.

Here's the drama:

I reinstalled Ubuntu Jaunty over the same exact version.  It seems to be running a little slow.  I had a partition allocated specifically for swap on the previous install.  I formatted the install and never pointed this version towards the swap partition.

How do I check to see what Ubuntu is using for the swap files?

I'm not sure if this helps:

top - 12:27:17 up  1:38,  2 users,  load average: 1.61, 1.04, 0.91
Tasks: 118 total,   2 running, 116 sleeping,   0 stopped,   0 zombie
Cpu(s): 32.6%us,  7.3%sy,  0.0%ni, 58.5%id,  1.0%wa,  0.3%hi,  0.3%si,  0.0%st
Mem:    509028k total,   476256k used,    32772k free,     8456k buffers
Swap:  1951856k total,    80924k used,  1870932k free,    67588k cached

---

### Post by Mark Phelps on 2009-05-30
Suggest you read the following:

[https://help.ubuntu.com/community/SwapFaq]("https://help.ubuntu.com/community/SwapFaq")

---

### Post by pastalavista on 2009-05-30
> **Nima1972 said:**
> I'm trying to see if Jaunty is using the swap partition.

Here's the drama:

I reinstalled Ubuntu Jaunty over the same exact version.  It seems to be running a little slow.  I had a partition allocated specifically for swap on the previous install.  I formatted the install and never pointed this version towards the swap partition.

How do I check to see what Ubuntu is using for the swap files?

I'm not sure if this helps:

top - 12:27:17 up  1:38,  2 users,  load average: 1.61, 1.04, 0.91
Tasks: 118 total,   2 running, 116 sleeping,   0 stopped,   0 zombie
Cpu(s): 32.6%us,  7.3%sy,  0.0%ni, 58.5%id,  1.0%wa,  0.3%hi,  0.3%si,  0.0%st
Mem:    509028k total,   476256k used,    32772k free,     8456k buffers
[COLOR="Red"]Swap:  1951856k total,    80924k used,  1870932k free,    67588k cached[/COLOR]

[COLOR="Red"]That tells you swap is being used. You have 2 gigs total and were using 80 megs at the time.[/COLOR]

In terminal enter ```
sudo fdisk -l
``` to find out which partition it's using. Probably same as before if you didn't change anything when you reinstalled.

---

