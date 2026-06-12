---
title: "How to bootup into different user accounts from GRUB?"
date: 2008-10-14
forum: General Help
---

### Post by DominicF on 2008-10-14
Please help.

I'd like to know how to setup my system so that at boot time I can select which ubuntu user account to boot into from the GRUB menu.  For example, I'd like my default to boot into my Mythtv account which is setup to auto login.  My second option would be to boot into my own Dom user account (a non-auto login account).

1) Mythtv (default)
2) Dom User
3) Another User


Can this be done with GRUB?

---

### Post by justleen on 2008-10-14
No.

Grub loads a kernel, not a 'user'

---

### Post by geirha on 2008-10-14
In theory, if you add one kernel entry for each of those three options, and add a unique string at the end of each kernel line, e.g.:
```
kernel /boot/vmlinuz-2.6.24-19-386 root=UUID=<...> ro quiet splash mythtv
```

After booting, you will find this line if you cat /proc/cmdline.

Based on that, you could change the initscript for gdm, or create a seperate one that runs before gdm, to link the appropriate gdm.conf-custom file to /etc/gdm/gdm.conf-custom.

No guarantees it will work, just giving you an idea that you could try. I suggest you install ubuntu in virtualbox-ose and try it out there first, as it may well break your system.

---

### Post by kokkus on 2008-10-14
By user do you mean operating system or an ubuntu user account?
You choose the user from GDM, not from grub.
Grub is the boot loader.

---

### Post by mikewhatever on 2008-10-14
The problem is, GRUB is a boot loader, so it loads the kernel and modules, which are user irrelevant. The difference between user accounts is usually in user related setting, GRUB cares not about. You can only log into different accounts, not boot into them.

---

### Post by meganox on 2008-10-14
Simpler way: Gnome has a timed login option (System -> Administration -> Login Window -> Security), you could use that to login to the mythtv account if you haven't logged in to another account after however many seconds.

---

### Post by DominicF on 2008-10-14
Thank you all for your input.  I think meganox has high-lighted a way forward with the timed login option of Gnome.  I'll give it a try tonight.

---

