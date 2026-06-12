---
title: "Poweroff problems"
date: 2016-06-03
forum: Hardware
---

### Post by nick253 on 2016-06-03
I have some problems with suspend and power off of my laptop (HP 450 G1)
This problems were when I'm used Xubuntu 15.10, and proceeds with Xubuntu 16.04. I read few topics and as suggested - update kernel. But problem is not solved.
It not happens every time, when I switch off or suspend laptop, approximately 1 time for 10 actions.
After doing action - screen stucks with wallpeppers and computer don't power off or suspending. In some other cases screen becomes black. After it I hold power power button and off the computer

Can some one suggest me, in which direction I should move ? What I should check at first?

---

### Post by christiaan3 on 2016-06-07
You could check your /var/log/syslog, maybe it shows some errors in there.
You can enter this by, sudo tail /var/log/syslog.

I hope you will get some more info from that.

---

### Post by nick253 on 2016-06-11
> **christiaan3 said:**
> You could check your /var/log/syslog, maybe it shows some errors in there.
You can enter this by, sudo tail /var/log/syslog.

I hope you will get some more info from that.

Thanks for help! Will check it, when problem appears again!

---

### Post by sasseones on 2016-06-11
If your computer freezes, you can make sysrequests to the kernel. Meaning, you can use hotkeys to unfreeze the kernel.
First try > ctrl+prt scrn+s
Next try > ctrl+prt scrn+u
Lastly try > ctrl+prt scrn+b
I forgot what s means, but u is for emergency unmount and remount of drives, and b is for reboot.

---

