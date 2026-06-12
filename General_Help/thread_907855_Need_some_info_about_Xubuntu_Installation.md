---
title: "Need some info about Xubuntu Installation"
date: 2008-09-01
forum: General Help
---

### Post by matrix14 on 2008-09-01
Hello for Every One,

I just downloaded Xubuntu iso and have burned it as a bootable CD. But wheen I try to install Xubuntu from CD just seem failed.

I can't found partitioning program within Xubuntu and the installer seem always switch to the shell command program.

Is this a failure installation, or my PC not supported by the Xubuntu installer?

I hope that some one can help inform me about this matter.

Thank you.

---

### Post by aysiu on 2008-09-02
You're not really supposed to burn it as a bootable CD. You're supposed to burn it as a disk image (since that's what it is).

If you're experiencing problems even after burning it as a disk image, it's possible the .iso got corrupted during download or burn.

More details here about how to ensure the integrity of the .iso:
[http://www.psychocats.net/ubuntu/iso](http://www.psychocats.net/ubuntu/iso)

---

### Post by matdombrock on 2008-09-02
When you boot up there should be an option that is somthing like "check cd for defects". You might try that.

---

### Post by matrix14 on 2008-09-13
Guys, thank you for your support...

@aysiu:

I have sure that the downloaded ISO is not corrupt, because I have check it before with use CRC utility program either from my old Debian and from Windows XP.

@matdombrock:

The cd boot up normally with xubuntu logo and all options displayed, wheen I choose - Install Xubuntu - then I am waiting the cd boot running and at last I only found that it switched to the BusyBox... Again, I am waiting untill up 15 minutes but at last only the BusyBox which is running, nothing else.

At last Guys, I've got idea:
I am installing from Win XP with use flash disk :( then I have made a new clean installation with entire hard-drive used, destroy my old Win XP.
Still, I've got error after install Xubuntu by use such unsuall method --
the flash disk inaccessible because unexpectedly mounted to the system folder /media/cdrom0/ during used to run install. Hi but it's ok, I've solved it by editing *fstab*.

Once again thanks for your support.

---

