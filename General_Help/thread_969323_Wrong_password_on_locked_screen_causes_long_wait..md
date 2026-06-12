---
title: "Wrong password on locked screen causes long wait."
date: 2008-11-03
forum: General Help
---

### Post by skmassey on 2008-11-03
Every time I mistype my password while the screen is locked, it takes about 10 minutes before I can attempt to re-enter my password.  I have dug through the logs and found that this message pops up in /var/log/auth.log

Nov  2 13:43:05 yizhi gnome-keyring-daemon[7428]: couldn't write 8 bytes to client: Broken pipe
Nov  2 13:43:05 yizhi gnome-screensaver-dialog: gkr-pam: couldn't unlock 'login' keyring: 1

I can't figure out how to fix this issue.  I know I could probably provide more information, but I don't know what would be needed to diagnose the problem.  None of the other system logs (syslog or messages) have any pertinent information.

Thank you

---

### Post by pgngp on 2008-11-24
Hello!

I'm having the same issue with Ubuntu 8.04. Was anyone able to solve this issue?

Thank you!

---

### Post by neozzion on 2009-02-03
i am experiencing the same annoyance! hope my echoing helps to make this problem get a little more visibility. 

i am on 8.04 as well. thanks! -Neo

---

### Post by guidos on 2009-02-06
Same problem here, although I just tried it and it did not happen.  I hate those intermittent bugs!:x

This bug seems to have been fixed before, but is back in Ubuntu 8.04.2.

I found this discussion helpful:
[https://bugs.launchpad.net/ubuntu/+source/gdm/+bug/76632](https://bugs.launchpad.net/ubuntu/+source/gdm/+bug/76632)

Take away quote by Emilio Pozuelo Monfort:
[INDENT]Read at ubuntuforums.org:

Logging to virtual terminal and

killall gnome-screensaver

is workaround

Regards
Pochu
[/INDENT]

I looked around for this thread over here, but couldn't find it. 

In case you never used a virtual terminal; push **CTRL+ALT+F1**.  You can have more by using the other function keys. **CTRL+ALT+F8** is your regular graphical "terminal."

I'll try this fix out, as soon as this bug shows up again.

Hope it will work for you,

Guido.

---

