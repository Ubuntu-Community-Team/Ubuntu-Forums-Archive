---
title: "Upgrading to 9.10 problem"
date: 2009-06-01
forum: Installation &amp; Upgrades
---

### Post by gamesnepal on 2009-06-01
Hi everyone,

I was trying to upgrade my ubuntu 8.04 to ubuntu 9.04 . First I knew I had to upgrade it to ubuntu 8.10 and I did it successfully from the update manager. 

Now to upgrade from 8.10 to 9.04 I ordered a free ubuntu cd and now when I want to upgrade from that cd and not by downloading it from the internet. When I insert the CD a prompt is displayed

> This medium contains software intended to be automatically started. Would you like to run it?
The software will run directly from the medium "Ubuntu 9.04 i386". You should never run software that you don't trust.

When I click on RUN it says:

> Error autorunning software
Cannot find the autorun program

So I read in the upgrade instructions and then I hit Alt+F2 and type in 
gksu "sh /cdrom/cdromupgrade"

But nothing happens.

How do I upgrade my ubuntu?

Help me out

Thanks
Ashish

---

### Post by Partyboi2 on 2009-06-01
Hi, if you ordered a free cd from shipit, it will be the desktop version. How ever you will need the alternate cd to upgrade with.
[http://noncdn.releases.ubuntu.com/jaunty/](http://noncdn.releases.ubuntu.com/jaunty/)

---

### Post by gamesnepal on 2009-06-03
Thanks. It worked.

---

