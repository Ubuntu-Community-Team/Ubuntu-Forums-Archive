---
title: "Remmina Display Doesn't Properly Refresh"
date: 2012-08-15
forum: Hardware
---

### Post by rhdinah on 2012-08-15
When making a VNC Remmina connection from my 12.04 desktop to my newly set up 12.04 notebook the remote display doesn't follow all the refresh changes. If I attempt to move windows about remotely ... part of screen repaints, but the entire window does not become invalidated and thus a complete repaint does not happen. Googling produced [[COLOR="Red"]this[/COLOR]]("http://askubuntu.com/questions/14484/how-to-actually-use-remote-desktop?s=804a0c89-56a0-4c9c-a952-10e250511997#new-answer") find ... which is exactly my problem. Unfortunately the last reply indicates that this key is no longer applicable in gconfig-editor ... which is correct. Anyway I would appreciate a idea on how to get around this issue please as it makes Remmina remote control almost unusable. BTW when the notebook was running 10.04 this issue did not happen ... so I am assuming that perhaps it is still a Compiz problem.

Thanks for your information and help!

.... I'll give it a few more days for ideas, otherwise it is clearly a bug and I'll submit same ...

---

### Post by WyomngGeezer on 2012-11-23
I have encountered the same problem in other similar programs a few months ago. Sorry, I cannot recall which. The point is that they all exhibited some form of not refreshing the screen. The only way I can use the remote is to mouse-down drag from one corner to another to refresh the screen. Really a pain.

What did not work:
 dconf-editor->desktop->gnome->remote-access->disable-xdamage (Google this) seems to have no effect.

I tried this: (from Google search):
"Went to remote desktop, logged out and then logged back in "Ubuntu 2D". Problem solved. "

Hey, it worked! I shall stick with Ubuntu 2D for awhile to see what I might be missing. First impression, not much.

Hey, spoke too soon. The 2D fix appeared to resolve the problem at first. However, after a few minutes, the problem seemed to reappear. I have no idea why and I have had too much wine to be abel to spurrsuue it ftherther.

---

### Post by henjj on 2013-03-28
Has anyone found a solution to this?  I have the same issue.  I'm trying to VNC from one ubuntu Machine to the other using Remmina and I can connect to the machine but the screen does not refresh.  Any other ideas?

---

### Post by hansheijmans on 2013-05-28
Same problem here using Remmina to connect to remote MacMini.

---

