---
title: "management &amp; networking of 100+ ubuntu"
date: 2008-07-11
forum: General Help
---

### Post by socram on 2008-07-11
I'm working at a Corp. that is running mostly by windowz machines. I'm changing this workstations to Ubuntu because of the ease of use to the final user ( coming from windowz ). The main work being mail and running a QVTterm terminal with wine (couldn't find any term that worked for me like QVT, the screen refresh is slow though).

What's the best sane way to admin all this workstations? ie: Install updates an all of them. Maybe using one server as an internal repo? Howto?

I want to give them a desktop that they can't modify, the user you create at installation time can change most things just by sudoing with their password. Plus, i don't want them to have access to some Menus like Preferences, Administration, Add&Remove Packg.

---

### Post by MasterXandrex on 2008-07-11
To give them a machine they can't admin, simply don't add the user to the wheel group. As far as an internal repo here's a link I followed and it work beautifully

[http://www.howtoforge.com/local_debian_ubuntu_mirror]("http://www.howtoforge.com/local_debian_ubuntu_mirror")

You could then use a cron script to do the updates -- but it's a bit risky:

```

0 3 * * * apt-get -y update && apt-get -y upgrade && apt-get -y dist-upgrade && apt-get -y autoremove && apt-get -y autoclean

```


As far as remote administration, I would just use static DHCP and openssh-server with X11 forwarding if I needed it.

Xan

---

### Post by socram on 2008-07-11
i don't see any wheel group, maybe i've to create it? according to this: [http://www.kernel-panic.org/wiki/GroupWheel](http://www.kernel-panic.org/wiki/GroupWheel)

i've a fresh install of Ubuntu 8.04 - Hardy Heron (no wheel group here)

---

### Post by The Cog on 2008-07-11
Forget the wheel group. Make sure your user isn't a member of the **admin** group. Then they can't use the **sudo** commands.

---

### Post by MasterXandrex on 2008-07-11
Yeah sorry, wheel was the old admin group in like Ubuntu 5.10. Forgot it had changed.


Xan

---

