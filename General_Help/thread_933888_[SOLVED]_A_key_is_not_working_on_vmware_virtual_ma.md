---
title: "[SOLVED] A key is not working on vmware virtual machines..."
date: 2008-09-29
forum: General Help
---

### Post by mamendes on 2008-09-29
Hi, I'm running VMware Server 1.0.6 build-91891 on ubuntu 8.04, and I created two machines, one with openSuse 11 and other with Win XP.

On both machines the [/ ?] is not working. My keyboard is brazilian ABNT and all others keys are normal, but the [/ ?] is simply dead inside vmware.

I found this thread that seems related:

[http://ubuntuforums.org/showthread.php?t=15574](http://ubuntuforums.org/showthread.php?t=15574)

But keep in mind my problem is only inside VMware machines. On Ubuntu the key is ok.

Now, what is that?? What could it be?

---

### Post by mamendes on 2008-09-29
Ok, solved:

[http://hamacker.wordpress.com/2007/06/20/vmware-e-os-caracteres-&#8220;&#8221;-e-&#8220;&#8221;-no-teclado-abnt2/](http://hamacker.wordpress.com/2007/06/20/vmware-e-os-caracteres-&#8220;&#8221;-e-&#8220;&#8221;-no-teclado-abnt2/)

Needed to add:

xkeymap.keycode.211 = 0x073

to /usr/lib/vmware/config.

Tks.

---

