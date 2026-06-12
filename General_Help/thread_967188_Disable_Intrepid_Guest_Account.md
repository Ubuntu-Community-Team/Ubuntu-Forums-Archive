---
title: "Disable Intrepid Guest Account?"
date: 2008-11-01
forum: General Help
---

### Post by Greslore on 2008-11-01
How does one disable this new guest account in Intrepid?

---

### Post by taurus on 2008-11-01
You can edit /etc/passwd and in the field that says /bin/bash, replace it with /bin/false.  Then, guest won't be able to log in anymore.

Applications -> Accessories -> Terminal
```
gksudo gedit /etc/passwd
```

---

### Post by pauljz on 2008-11-03
In my upgraded install there was no entry in /etc/passwd for the guest user.  Maybe this is different from a fresh install?

Anyway, after I added a guest user to /etc/passwd with /bin/false as the shell, guest login was effectively disabled.  Unfortunately the options are still present in the dodgy little user menu in Gnome, and now there's also a "guest" option embedded in the menu.  When you click either of these it presents a login window, fails to log in, and returns you to a locked session.

Surely there's a legitimate way to disable this entirely?


Edit: Above post really needs to be edited since if followed literally naive users will end up revoking their own account's ability to log in.

---

### Post by wgrant on 2008-11-03
Try removing gdm-guest-session.

---

### Post by pauljz on 2008-11-03
I could've sworn I tried that but must've been using the wrong package name.  Lovely though, works like a charm.

```
sudo apt-get remove gdm-guest-session
```

Followed by a <Ctrl><Alt><Backspace> restart of GDM did the trick.

---

### Post by britton on 2008-11-05
There is also an option in gconf-editor  -->  fast user switch, although I'm unsure how well this works... I can't get it to enable on my system.

---

