---
title: "Lucid + Hibernate|suspend = full cpu ??"
date: 2010-12-14
forum: Hardware
---

### Post by astrobob.tk on 2010-12-14
Hello guys,

1) I always face this issue when I hibernate or suspend my Lucid Lynx. It always shows a full cpu (i have a core 2 duo; so it alternates between cpu 1 & 2. See image below:

[IMG]http://ubuntuforums.org/picture.php?albumid=1552&pictureid=7117[/IMG]

Why is that ? & how can I resolve this ?

2) When I use sound converter to convert tracks, the cpu history (of both cores) is 100%:

[IMG]http://ubuntuforums.org/picture.php?albumid=1552&pictureid=7119[/IMG]

Moreover I see this process in the system monitor (152& ????). How is that possible ??

[IMG]http://ubuntuforums.org/picture.php?albumid=1552&pictureid=7118[/IMG]

3) Uptime issue: How is it possible that "5 users" is printed when I run the command "uptime" in the terminal though there's only one account logged in ? I once read that it sometimes can show 2 even if 1 user is logged in. Can you please explain this & what's happening here ?
[IMG]http://ubuntuforums.org/picture.php?albumid=1552&pictureid=7122[/IMG]


thanks in advance

---

### Post by astrobob.tk on 2010-12-17
anyone ?

---

### Post by astrobob.tk on 2010-12-25
Hello :roll:

---

### Post by astrobob.tk on 2011-04-12
> **astrobob.tk said:**
> Hello guys,

1) I always face this issue when I hibernate or suspend my Lucid Lynx. It always shows a full cpu (i have a core 2 duo; so it alternates between cpu 1 & 2. See image below:

[IMG]http://ubuntuforums.org/picture.php?albumid=1552&pictureid=7117[/IMG]

Why is that ? & how can I resolve this ?

thanks in advance

I believe I found the source of this problem, just recently.

it seems to be "snort". check the [filed bug on launchpad]("https://bugs.launchpad.net/ubuntu/+source/snort/+bug/757295").

---

