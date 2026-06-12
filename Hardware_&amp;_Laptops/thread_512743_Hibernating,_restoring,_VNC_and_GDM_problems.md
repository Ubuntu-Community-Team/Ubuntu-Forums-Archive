---
title: "Hibernating, restoring, VNC and GDM problems"
date: 2007-07-29
forum: Hardware &amp; Laptops
---

### Post by NigO on 2007-07-29
I've got a problem which seems to be related to hibernate and restore, running Feisty on a Dell SC440.  All seems to be working well, **except** restoring the main login window after a hibernate.

I've set the main GDM login to auto-login to one llimited account, which is set up to share its desktop using vino-server.  There are 3 other VNC sessions available using Xvnc.

As a result, I can vnc to :0 for the standard login, ie the same as the local monitor, or :1, :2 or :3 for remote sessions.  It all works a treat, and after hibernate the sessions :1 to :3 are restored just as they were.

However the local monitor doesn't come up with a graphical screen, just a flashing line cursor in the top left corner, and a VNC session to :0 connects OK but gives a blank screen.

Where should I look to see why the GDM session doesn't restart but the Xvnc ones do?  Any other possible reasons?

Thanks,

Nigel

---

