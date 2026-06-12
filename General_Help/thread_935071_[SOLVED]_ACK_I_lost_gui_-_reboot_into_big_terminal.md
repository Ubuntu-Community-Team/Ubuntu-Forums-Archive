---
title: "[SOLVED] ACK I lost gui - reboot into big terminal help!"
date: 2008-10-01
forum: General Help
---

### Post by dazzlindonna on 2008-10-01
I decided to uninstall Beagle because it was using 100% cpu. Uninstalling (via synaptic) took a long time but it finally finished.  At that point, my cursor was jerky and system was moving dog slow, so I assumed I needed to reboot after the Beagle removal.  I rebooted, and now, all GUI is gone! It boots me into a full screen terminal window, where it asks me for username and password to login. Then it just sits there waiting for me to type in more commands.

What do I do? Any way to get my gui back? Do I have to reinstall?  Frantic...

---

### Post by Peter09 on 2008-10-01
If you are at a command prompt try typing
```
startx
```

to see what happens.

You may need to install the desktop again, which I think is
[I]
removed line here because it is inaccurate[/I]

it would be good to know what has happened.

---

### Post by dazzlindonna on 2008-10-01
Ok, this is encouraging! typing startx does indeed get my gui back!  hooray!  however... if i try to logout of the session, instead of returning to the logout gui, it returns me to the big terminal prompt.  So I then rebooted again, hoping that would help but i'm back at the big terminal again. How do I now keep the gui in place at login, etc.  Do I still need to reinstall gnome-desktop?

and thanks for the help!

---

### Post by Peter09 on 2008-10-01
I believe you gdm is what starts your session automatically.

That may be worth re-installing.

```
sudo apt-get install gdm
```

---

### Post by dazzlindonna on 2008-10-01
tried that, but it said it was already at the latest version, so 0 upgraded, 0 newly installed, 0 removed and 0 not upgraded

---

### Post by Peter09 on 2008-10-01
Yeah, missed that one.

If you go to synaptic package manager you can mark it for re-installation.

I'm not sure what the command line is for that.

There is a file, somewhere, (name escapes me) which indicates to the system if it should bring up a window manager. I'll see if I can find the name of it.

Also try sudo dpkg-reconfigure gdm

---

### Post by dazzlindonna on 2008-10-01
Got it all fixed.  Thanks for the help. I used synaptic to reinstall as many of the gdm related things i could find.  Not sure which was the trigger, but it now works fine.  Oh, and during the process root took over my home directory, but i managed to get ownership back, so all is well.  thanks much.

---

### Post by Peter09 on 2008-10-01
Great - happy to help

---

