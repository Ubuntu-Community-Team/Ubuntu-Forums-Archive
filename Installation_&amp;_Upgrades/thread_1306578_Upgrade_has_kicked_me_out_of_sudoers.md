---
title: "Upgrade has kicked me out of sudoers"
date: 2009-10-30
forum: Installation &amp; Upgrades
---

### Post by davehouston on 2009-10-30
After upgrading from 9.04 to 9.10 I can no longer run Synaptic or apt-get. I am told "**[COLOR="Red"]dave is not in sudoers file[/COLOR]**".:(

---

### Post by zalberico on 2009-10-30
I looked around on the internet and found this...

You need to edit the sudoers file with the visudo command by first logging in as root.  Or from the failsafe gnome in the grub boot loader.

There should be a line like: root ALL=(ALL) ALL. You can simply create a second line like that but replacing "root" with your username. 

Alternatively, you can use 
%admin ALL=(ALL) ALL
In that case, however, you'll have to add yourself to the admin group (/etc/groups).

---

### Post by blur xc on 2009-10-30
> **zman14321 said:**
> I looked around on the internet and found this...

You need to edit the sudoers file with the visudo command by first logging in as root.  Or from the failsafe gnome in the grub boot loader.

There should be a line like: root ALL=(ALL) ALL. You can simply create a second line like that but replacing "root" with your username. 

Alternatively, you can use 
%admin ALL=(ALL) ALL
In that case, however, you'll have to add yourself to the admin group (/etc/groups).

That's the first thing I'd check- is to make sure you are a member of the admin group.

You can add yourself back in recovery mode.  

BM

---

### Post by davehouston on 2009-10-30
It rejects my password when I try to login as root. Plus, it now has crashed with a kernel error. I think it's hosed.

---

### Post by blur xc on 2009-10-30
logging in recovery mode doesn't ask for a password, does it?

BM

---

### Post by davehouston on 2009-10-30
Both Ubuntu 9.10 and Kubuntu 9.10 are crashing after the upgrade so I'm just going to wipe them out and start with a new install.

---

