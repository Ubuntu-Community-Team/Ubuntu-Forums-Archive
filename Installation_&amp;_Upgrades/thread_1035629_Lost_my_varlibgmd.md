---
title: "Lost my /var/lib/gmd"
date: 2009-01-09
forum: Installation &amp; Upgrades
---

### Post by The Bane on 2009-01-09
I used Clamtk (antivirus) and ended up deleting my /var/lib/gmd folder... doh!

I get something to the following warning when I try to boot:

Server Auth direct (daemon/ServAuthDir) is set to /var/lib/gdm does not exist. Please correct gdm conf and restart gdm.

Lost, can someone help me?

edit: I found an older tar_system_backup_'date' on the hard drive while looking through what I wanted to try to recover before reinstalling... I try to extract it but I get a 'you do not have permission' when I try to untar it. Suggestions? /edit

Best,
The Bane

---

### Post by Partyboi2 on 2009-01-10
Have you tried to reinstall gdm?
```
sudo apt-get --reinstall install gdm
```

---

### Post by albinootje on 2009-01-10
> **Partyboi2 said:**
> Have you tried to reinstall gdm?
```
sudo apt-get --reinstall install gdm
```

Indeed.
To do this, boot into "recovery mode" at the Grub menu.
Then choose "drop to root shell prompt".

And next time, think twice before deleting something.
Anti virus software for Linux is meant to project you against *MS-Windows* viruses, and nothing else.
If you don't use Windows yourself, then you can use it to scan files from friends which you will give to other friends.

---

### Post by christhegoth on 2009-01-10
Wise words... *ahem*

*Shuffles away sheepishly...*


Oh, and the fix works :D

---

