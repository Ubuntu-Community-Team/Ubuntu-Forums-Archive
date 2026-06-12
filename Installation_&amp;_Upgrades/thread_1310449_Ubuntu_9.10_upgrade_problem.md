---
title: "Ubuntu 9.10 upgrade problem"
date: 2009-11-01
forum: Installation &amp; Upgrades
---

### Post by gordon3913 on 2009-11-01
When tyring to upgrade from 9.04 to 9.10 the computer froze while at trying to install xfonts-100dpi. Waited for an hour and eventually decided to reboot.

When I rebooted there nis a message that one or more of the mounts listed in /etc/fstab cannot yet be mounted.

What should I do?

---

### Post by jjcv on 2009-11-01
> **gordon3913 said:**
> When tyring to upgrade from 9.04 to 9.10 the computer froze while at trying to install xfonts-100dpi. Waited for an hour and eventually decided to reboot.

When I rebooted there nis a message that one or more of the mounts listed in /etc/fstab cannot yet be mounted.

What should I do?

Without more detail it is hard to know.   Are you able to get a login prompt to your system?

If so then login and type:

cat /etc/fstab

and past the results into a message here so we can see what is going on.

Also type:

df

and paste the results.

---

### Post by gordon3913 on 2009-11-02
I could not get a login prompt.
I had downloaded a cd of 9.10 just in case something went wrong.
I used the cd to install 9.10 and with a separate home partition every thing seems to be ok except that I have to install the other 9 programs that I use that do not come with the standard system.
I hope that not too many other people are put off by a dodgy upgrade as I really like using Ubuntu.

---

