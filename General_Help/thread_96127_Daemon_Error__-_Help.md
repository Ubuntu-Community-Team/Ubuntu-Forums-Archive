---
title: "Daemon Error??  - Help"
date: 2005-11-28
forum: General Help
---

### Post by shane2peru on 2005-11-28
Ubuntu told me there were updates, so I updated.  I believe that it updated the kernel from 2.6.12.9 to 2.6.12.10.  Now when I boot into Ubuntu I always get this error:

[B]There was an error starting the GNOME Settings Daemon.

Some things, such as themes, sounds, or background settings may not work correctly.

The Settings Daemon restarted too many times.

The last error message was:

Child process did not give an error message, unknown failure occurred

GNOME will still try to restart the Settings Daemon next time you log in.[/B]

Can anyone Help???  Thanks.

Shane

---

### Post by timw on 2005-12-10
Hi there,

Yeah I had the same message but it wasn't caused by an update. I (stupidly) changes the permissions to every file in the /usr directory and all hell broke loose!

I'm slowly re-setting the permissions back but one of the errors I got was this one.

To solve the problem I restored the permissions to: 

-rwxr-xr-x  1 root root /usr/lib/control-center/gnome-settings-daemon

Hope this helps!

---

