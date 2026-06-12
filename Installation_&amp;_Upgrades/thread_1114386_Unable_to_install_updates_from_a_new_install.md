---
title: "Unable to install updates from a new install"
date: 2009-04-02
forum: Installation &amp; Upgrades
---

### Post by capitolfelony on 2009-04-02
new install of 8.10 i386 on my sony, i have downloaded all the updates and have tried to install them many times. each time i get this error message:

E: /var/cache/apt/archives/perl-modules_5.10.0-11.1ubuntu2.2_all.deb: short read in buffer_copy (backend dpkg-deb during `./usr/share/perl/5.10.0/Pod/Perldoc.pm')
E: /var/cache/apt/archives/libc6_2.8~20080505-0ubuntu9_i386.deb: short read in buffer_copy (backend dpkg-deb during `./usr/share/doc/libc6/log-test-i486-linux-gnu-libc.gz')

im trying to teach myself as i go but i have no idea how to fix this problem.

it seems like it wont install libc6, thats when errors occur.

---

### Post by capitolfelony on 2009-04-02
When i boot up the system im getting this message now before xubuntu starts:

SMART Failure Predicted on Hard Disk 0: TOSHIBA MK6021GAS-(PM) Warning: Immediately back-up your data an replace your hard disk drive. A failure may be imminent. Press F1 to continue

is the hard drive damaged and its stopping the updates to install. im on the computer typing this and it seems to be running fine except for about 184 updates that wont install.

---

### Post by Partyboi2 on 2009-04-02
> SMART Failure Predicted on Hard Disk 0: TOSHIBA MK6021GAS-(PM) Warning: Immediately back-up your data an replace your hard disk drive. A failure may be imminent. Press F1 to continue This is a warning that your hard drive is on its way out.

For the update problem open a terminal (Applications>Accessories>Terminal) and try
```
sudo apt-get clean
sudo apt-get -f install
sudo apt-get update
sudo apt-get upgrade

```In that order.

---

### Post by capitolfelony on 2009-04-02
thanks for the help but im getting this message:
186 upgraded, 0 newly installed, 0 to remove and 4 not upgraded.
E: Could not get lock /var/cache/apt/archives/lock - open (11 Resource temporarily unavailable)
E: Unable to lock the download directory

---

### Post by Partyboi2 on 2009-04-02
Make sure you only have one package manager running at a time eg synaptic, update manager, apt-get. So for example if update manager is open close that before typing or pasting those commands.

---

### Post by capitolfelony on 2009-04-02
it seems like the clean command isnt working even though im rooted.

---

### Post by capitolfelony on 2009-04-02
yep u were right i had update open. its currently downloading everything in terminal i hope it works this time thanks for the help

---

