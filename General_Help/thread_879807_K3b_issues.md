---
title: "K3b issues"
date: 2008-08-04
forum: General Help
---

### Post by bbabiuk on 2008-08-04
Hi all,

I recently installed k3b on Hardy,  Something went wrong.  Have never encountered this before.  After installing with synaptic and trying to run krb i get the following:

> bbabiuk@bbabiuk-desktop:~$ k3b
startkdeinitlock: WARNING: KTempFile: Error trying to create /home/bbabiuk/.kde/tmp-bbabiuk-desktop/startkdeinitlockXXXXXX.tmp: Permission denied
startkdeinitlock: WARNING: KTempFile: Error trying to create /home/bbabiuk/.kde/tmp-bbabiuk-desktop/startkdeinitlockXXXXXX.tmp: Permission denied
startkdeinitlock: WARNING: KTempFile: Error trying to create /home/bbabiuk/.kde/tmp-bbabiuk-desktop/startkdeinitlockXXXXXX.tmp: Permission denied
startkdeinitlock: WARNING: KTempFile: Error trying to create /home/bbabiuk/.kde/tmp-bbabiuk-desktop/startkdeinitlockXXXXXX.tmp: Permission denied
startkdeinitlock: WARNING: KTempFile: Error trying to create /home/bbabiuk/.kde/tmp-bbabiuk-desktop/startkdeinitlockXXXXXX.tmp: Permission denied
startkdeinitlock: WARNING: KTempFile: Error trying to create /home/bbabiuk/.kde/tmp-bbabiuk-desktop/startkdeinitlockXXXXXX.tmp: Permission denied
kdeinit: Aborting. bind() failed: : Permission denied
Could not bind to socket '/home/bbabiuk/.kde/socket-bbabiuk-desktop/kdeinit__0'
startkdeinitlock: ERROR: KUniqueApplication: Can't setup DCOP communication.
bbabiuk@bbabiuk-desktop:~$ 



If I try to sudo k3b I can run it.  (But this isn't really an option I want to explore)

It looks like a security setting.  Any suggestions?

thanks.

---

### Post by K2712 on 2008-08-04
```
sudo chown -R bbabiuk /home/bbabiuk/.kde
sudo chmod -R a+rwx /home/bbabiuk/.kde

```

---

### Post by bbabiuk on 2008-08-04
Thanks,  Did the trick!

---

