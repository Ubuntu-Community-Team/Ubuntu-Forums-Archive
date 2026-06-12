---
title: "moving user accounts from Suse 11.0"
date: 2009-06-13
forum: Installation &amp; Upgrades
---

### Post by vielmaj on 2009-06-13
I am moving from suse 11.0 to ubuntu 9.04.  There is three accounts I wanted to move: vielmaj, guestuser, and heidi.  Here is the files I copied from etc in suse.  There are a colon x missing after each name in passwd and group files because this forum assume they are images for some reason

/etc/passwd

guest:1002:100:Guest User:/home/guest:/bin/bash
heidi:1001:100:Heidi E. Helms:/home/heidi:/bin/bash
vielmaj:1000:100:Jason Vielma:/home/vielmaj:/bin/bash

/etc/shadow

guest:$2a$05$Y3kw9fGoLgBNMH12NFBwtuufMzxSNf.ZcENmE1DMvI8BkobOv8l4C:14053:0:99999:7:::
heidi:$2a$05$wPm5ZVJ/v4Iq60oYg8hqM.dS38x8skBwAsdjUmL3K9euBugJTh8zq:14053:0:99999:7:::
vielmaj:$2a$05$poZodIArGcUygVG74r6Nreqi6xqYBAoI8Ii1li8WZ0AA1LNFRSQnu:14044:0:99999:7:::

/etc/group

dialout:16:guest,heidi,vielmaj
disk:6:vielmaj
video:33:guest,heidi,vielmaj

I appended these to /etc/passwd /etc/group and /etc/shadow in ubuntu.  The problem I see is in /etc/passwd, which at the bottom reads

ubuntu:1000:1000:ubuntu,,,:/home/ubuntu:/bin/bash
guest:1002:100:Guest User:/home/guest:/bin/bash
heidi:1001:100:Heidi E. Helms:/home/heidi:/bin/bash
vielmaj:1000:100:Jason Vielma:/home/vielmaj:/bin/bash

ubuntu is the account I created on install.  When I type ls -l in /home I get

drwxr-xr-x  8 guest  users   4096 2008-06-22 22:32 guest
drwxr-xr-x  8 heidi  users   4096 2008-06-22 22:32 heidi
drwxr-xr-x  2 root   root   16384 2008-06-13 16:14 lost+found
drwxr-xr-x 24 ubuntu ubuntu  4096 2009-06-13 11:23 ubuntu
drwxr-xr-x 71 ubuntu ubuntu  4096 2009-06-13 11:03 vielmaj

I am not able to login as vielmaj.  How do I fix this?  Thanks, Jason

---

