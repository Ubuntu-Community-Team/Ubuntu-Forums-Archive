---
title: "How to boot to runlevel 3"
date: 2008-08-16
forum: General Help
---

### Post by satimis on 2008-08-16
Hi folks,


Ubuntu 8.04 desktop amd64


Please advise how to boot to runlevel 2/3 (init 2/3)


1)
Temporarily at boot (guest OS running on a virtual machine)


2)
Permanently at boot.  Which file shall I edit and how.


TIA


B.R.
satimis

---

### Post by bingoUV on 2008-08-16
What do you want to achieve by booting into runlevel 2 or 3? In ubuntu, there is by default no difference between runlevels 2 to 5. Ubuntu has also screwed up the /etc/inittab logic so that appending runlevel to the end of kernel parameters does not cause a boot to that runlevel.

If , by runlevel 3, you mean "no graphical login" like traditional distributions do in runlevel 3, you have to stop gdm from running.

Default runlevel in Ubuntu is 2. This does start graphical login. There will be a file /etc/rc2.d/*gdm e.g. /etc/rc2.d/*gdm.  It will be a link to /etc/init.d/gdm. You need to remove the link this link to make gdm not start on bootup.

---

### Post by satimis on 2008-08-16
Hi bingoUV,


Thanks for your advice.


> **bingoUV said:**
> What do you want to achieve by booting into runlevel 2 or 3? In ubuntu, there is by default no difference between runlevels 2 to 5. Ubuntu has also screwed up the /etc/inittab logic so that appending runlevel to the end of kernel parameters does not cause a boot to that runlevel.

If , by runlevel 3, you mean "no graphical login" like traditional distributions do in runlevel 3, you have to stop gdm from running.

Yes.  I meant without graphic, similar to console for commands input.  /etc/inittab is on Fedora.  I can't find this file on Ubuntu.


> 
Default runlevel in Ubuntu is 2. This does start graphical login. There will be a file /etc/rc2.d/*gdm e.g. /etc/rc2.d/*gdm.  It will be a link to /etc/init.d/gdm. You need to remove the link this link to make gdm not start on bootup.
# ls -al /etc/init.d/gdm ```

-rwxr-xr-x 1 root root 3134 2008-05-21 22:48 /etc/init.d/gdm

```
There is no link.


Whether;
# mv /etc/init.d/gdm /etc/init.gdm.origin


On reboot Ubuntu will start non graphic mode waiting for command input?

Run;```

$ startx

```

will start Gnome desktop?  TIA


B.R.
satimis

---

### Post by bingoUV on 2008-08-16
No, /etc/init.d/ is the location for original files, you are not to touch them. 

```

ls -l /etc/rc2.d/*gdm

```

The above command should show you the file you need to remove. This file should be a link to /etc/init.d/gdm. Remove this link to /etc/init.d/gdm in /etc/rc2.d rather than /etc/init.d/gdm itself.

FYI, in fedora you just have to append 3 to the end of the boot options in grub menu, and you get into runlevel 3 which does not load graphical login manager. Sweet.

---

