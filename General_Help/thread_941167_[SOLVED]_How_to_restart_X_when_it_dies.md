---
title: "[SOLVED] How to restart X when it dies?"
date: 2008-10-07
forum: General Help
---

### Post by the real omni on 2008-10-07
I'm wondering how I can have my system automatically run startx as soon as x dies.

Background:

I've removed gnome and gdm, and I've installed kdebase (but no kdm).

The .bashrc in my /home/kiosk directory automatically calls 'startx' when the user 'kiosk' logs in, so there's no chance for the user to cause trouble in the console.

The .xinitrc in the /home/kiosk directory calls 'exec firefox' to replace 'exec $PROGRAMS' so instead of a full-blown KDE desktop, all the user gets is X with a full-screen firefox. As soon as the user quits firefox, X dies.

The problem is that when X dies, it doesn't start itself back up, it just drops the user to console, which is bad bad bad for a public web kiosk.

So basically I just need to know how to make the system start X again as soon as it dies for the 'kiosk' user (or, alternatively, how to make firefox automatically re-start as soon as it's closed by the 'kiosk' user, without restarting X). In either case, I need to stop the user from gaining console access. (I'm also going to disable virtual consoles but that's the next phase of the project, first I need to make X or firefox persistent.)

Any thoughts or URL's? :)

---

### Post by deanjm1963 on 2008-10-07
In Kcontrol under User Management, if you log as in super user, there is an option to restart X if it crashes ... it might be what you're after.

You'll need to click thru the tabs to find the option, I'm not on KDE at the moment, but I normally enable it when I use KDE.

Hope this helps

---

### Post by LoneWolfJack on 2008-10-07
I'm not sure if this is really restarting X, but try shift+backspace when the desktop locks up or starts acting weird.

---

### Post by the real omni on 2008-10-07
Figured this one out.

I just had to put

```

while [ 1 == 1 ]
  do
    startx
  done

```

...into the .bashrc file in the kiosk user's home directory.

MAN linux is cool! :D

---

