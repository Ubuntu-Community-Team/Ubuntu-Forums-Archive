---
title: "VMWare Tools Won't Work"
date: 2008-08-25
forum: General Help
---

### Post by jcarson83 on 2008-08-25
Sorry if this isn't the right section to put this in but I've been searching for a couple of days and can't find anything useful.  Be warned I'm a linux noob that started out trying gentoo and have recently picked up ubuntu in an attempt to redeem myself after my massive failure with gentoo.

I can't get vmware-tools to configure right.  It goes through all the steps and then at the end it gives me this.

Guest operating system daemon: failed
/etc/init.d/vmware-tools: 1050: vmware-guestd: permission denied
unable to start services for vmware tools

Forgive me in advance for not following rules of the forum.  I'm new here.

Oh and if this helps.  I've got the resolution set to 1680x1050.

---

### Post by jcarson83 on 2008-08-26
I figured it out.  Something with the permissions is weird with VMWare tools.

chmod +x /usr/sbin/vmware-guestd

This fixed it in case anyone else runs into the issue.

---

