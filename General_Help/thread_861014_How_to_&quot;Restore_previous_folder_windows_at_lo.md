---
title: "How to &quot;Restore previous folder windows at logon&quot; ?"
date: 2008-07-16
forum: General Help
---

### Post by MoToR on 2008-07-16
Hello everyone.

In Mac OS when you restart your system previously opened folders reopen automatically upon logon.

In Windows you can enable such behavior in Folder Options.

Is there something I can do in **Ubuntu** to have my (at least Nautilus) windows I left open before restart to reopen upon logon?

I searched this forum, googled it, but no result.

Thank you in advance for your time.

---

### Post by prshah on 2008-07-16
> **MoToR said:**
> 
Is there something I can do in **Ubuntu** to have my (at least Nautilus) windows I left open before restart to reopen upon logon?


Yes, of course! Click System-Preferences-Sessions-Session Options-"Automatically remember running applications when logging out".

Note that it will (slightly) add to your shutdown and startup times.

Note that this will remember _all_ running programs.

---

### Post by MoToR on 2008-07-17
Thanks for your help!

---

### Post by haud on 2008-12-17
it didn't help for me, I have checked and uncheck that box to remember running applications automatically but it haven't take any effect at all.

---

### Post by George Heine on 2011-02-07
"Sessions" is no longer on the "System-Preferences" menu in Lucid.  Is there an equivalent way to save open terminals somewhere else?

Better yet, is there a way to use Gconftool to accomplish this ?

thanks!

---

### Post by prshah on 2011-02-08
> **George Heine said:**
> "Sessions" is no longer on the "System-Preferences" menu in Lucid.  Is there an equivalent way to save open terminals somewhere else?

It's now in System-Preferences-Startup Programs (-Options).

---

### Post by Habitual on 2011-02-08
George Heine:

```
gnome-session-save
``` 
says

DESCRIPTION
       The gnome-session-save program can be used from a GNOME session to save a snapshot of  the  currently
       running applications. This session will be later restored at your next GNOME session.

Just run it in shell?

---

### Post by GutsyVirgin on 2011-05-29
For crying out loud, they keep moving crap. I can't find how to do this in Natty Narwhal (11.04). I've searched the documentation, but keep getting results on restoring grub or the boot manager, lol.

Not a huge deal, but a little assistance would sure be appreciated. It's just a time saver. Thankies ;)

---

### Post by adsbaer12 on 2011-08-08
This does not work for me! (running up-to-date Ubuntu 10.10 Maverick x86_64).
Also, wasn't the original post asking for restoring FOLDERS, not applications?
I want all my FOLDERS to be restored, but NOT the applications (I prefer those to be started manually).
Who can help? :confused:
Thanks for your time.

---

