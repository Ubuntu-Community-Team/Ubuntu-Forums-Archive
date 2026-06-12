---
title: "Metacity does not load themes"
date: 2008-07-26
forum: General Help
---

### Post by nicjasno on 2008-07-26
Metacity does not load themes.
It just doesn't. As can be seen in the screenshot below, it somehow just reverts to a default grey gnome theme.

It's a fresh 8.04 install, with all updates, desktop effects disabled. Install went smooth without any errors.

It enables the human theme or any other theme just for the applications that are currently open, and only if i manually select the theme, only to "forget" it as soon as i restart or open any other application.

I have already reinstalled metacity.

Need help with this.

---

### Post by nicjasno on 2008-07-27
Am i the only one who expirienced this problem on a fresh hoary install?

---

### Post by nicjasno on 2008-08-04
This is driving me nuts... any help or suggestions would be very much appreciated.

---

### Post by lunalec on 2008-08-04
Try turning off desktop effects. Although I just did an update that seems to have crippled "human", with and without effects.

---

### Post by nicjasno on 2008-08-04
I have the effects turned off. I even tried other themes. It's always the same.

---

### Post by cicatriz on 2008-08-04
Do the other features of GNOME work?  I get similar results in booting to fluxbox because the application gnome-settings-daemon is not invoked at runtime.  This seems to control the appearance of any GTK+2 interface, and running it allows one to use GNOME's theme system under any WM (or at least this is what I have found).

If it is already running, it will complain about using two xsettings managers at once, and I have no idea where to go from here.  If it is not, try running it.  I'm not sure what permissions are required.  :)

If it is indeed running, then I can report that I'm having exactly the same issue as you with the Darklooks theme.  Nautilus is the only application that spawns with the correct chrome.

---

### Post by nicjasno on 2008-08-04
That's the exact same situation i'm having here.

---

### Post by cicatriz on 2008-08-04
Sorry, but I think I've confirmed that my problem was just with that particular theme.  :(

---

### Post by nicjasno on 2008-08-04
I have problems with every metacity theme. Compiz themes work fine though.

---

### Post by nicjasno on 2008-08-08
I went back to 7.10, where everything works 1a ok. I guess i'll have to wait for 8.10 . 8.04 seems like the vista of the ubuntu world.

---

