---
title: "Appearance theme changes on boot (AspireOne)"
date: 2009-08-05
forum: Hardware
---

### Post by the12plus on 2009-08-05
Hello everybody,

Here is a problem I have been having recently with Ubuntu Netbook Remix 9.04 on my Acer AspireOne ZG5. Every now and then, Gnome appearance changes when I boot UNR, looking like **[[COLOR="Blue"]this[/COLOR]]("http://the12plus.googlepages.com/unr-appearance.png")** (check the icons and the upper bar), instead of the default Human-Netbook theme. A "workaround" I have accidentally come up with is launching gnome-appearance-properties (the same as Preferences->Appearance, from the menu). This restores the default Gnome theme (Human Netbook).

Does anybody know what could be wrong? I even tried adding the gnome-appearance-properties in the start-up applications but it was no good, the theme still changes sometimes...

Thanks in advance! :)

---

### Post by Tr4ffic on 2009-09-02
Hi

I don't know if you've already found an solution to your problem but I had the exact same problem as you. My solution was:


1. Create a new user.
2. Copy all the things you need from your old home folder into the new users home folder
3. Don't copy everything in the old home folder only the things you need or else you will have the same problem when you log in with the new user.
4. Delete the old user and continue working with the new user.

I hope you found this information useful.

Regards

---

### Post by the12plus on 2009-09-02
Being kind of fed up with lots of things that just happen in the Netbook Remix version, I finally installed the Desktop version (not just switched to the Desktop-like mode) that seems to work really smoothly, at least until now ;) Therefore, I cannot check whether what you are suggesting does the trick. However, thanks a lot for your response :)

---

### Post by Nowaker on 2010-02-05
I have got the same issue - the workaround is launching gnome-appearance-properties. I use Ubuntu 9.10 - a fresh installation on 15th Nov. Does anyone know how to fix it? Deleting a user is not a good idea.

---

### Post by Nowaker on 2010-02-16
I investigated it - launching gnome-settings-daemon resolved the problem. You just have to run it on GNOME startup (use gnome-session-properties and add /usr/lib/gnome-settings-daemon/gnome-settings-daemon to startup).

---

