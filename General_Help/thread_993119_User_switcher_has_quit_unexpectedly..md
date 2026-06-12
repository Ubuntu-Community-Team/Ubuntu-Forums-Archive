---
title: "User switcher has quit unexpectedly."
date: 2008-11-25
forum: General Help
---

### Post by Jerfo on 2008-11-25
I've been having this problem lately, I am not entirely sure but I think it appeared since I installed KDE. The User Switcher won't run on startup and when I try to manually add it to the panel I keep getting the "User switcher has quit unexpectedly." error message. Could you help me with this?

---

### Post by adityakavoor on 2008-12-03
yeah, same problem here, since I installed KDE this is happening

---

### Post by monkeyking on 2009-01-04
I got the same problem after installing kubuntu-desktop.

Did you efter find a solution?

---

### Post by monkeyking on 2009-01-04
apparantly this is a problem with user switch applet and kdm.

After going back to gdm it works again

[https://bugs.launchpad.net/ubuntu/+source/fast-user-switch-applet/+bug/301218](https://bugs.launchpad.net/ubuntu/+source/fast-user-switch-applet/+bug/301218)

---

### Post by Jerfo on 2009-01-04
Nope, and it doesn't seem like I'm finding it any time soon, no answer in over a month...

---

### Post by monkeyking on 2009-01-04
hmm, thats annoying.
If I were you, I'd try to remove gdm completely,
reboot
reinstall gdm
reboot
see if that works.

I don't know if gdm depends on other stuff though.

---

### Post by daveysan on 2009-01-08
I have just had something similar. I am running gnome and got this error, along with a problem starting the HAL. 

Just prior to these errors, I had set some programs to autostart using update-rc.d. I removed those programs from autostarting, rebooted and the problem has gone away. So I need to look at which of those programs was causing the error. 

Hope this helps someone ...

---

### Post by karatedog on 2009-09-30
After reboot:
select GNOME in login as Session
then select "Don't reload" when User Switcher crashes
in a terminal window type: sudo dpkg-reconfigure gdm
Select gdm, then select OK
restart

This helped me. Everything was fine, but you have to manually add the User Switcher application to the Panel again, and have to reorganize the order of the apps.

---

