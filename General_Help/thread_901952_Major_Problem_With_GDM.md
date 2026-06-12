---
title: "Major Problem With GDM"
date: 2008-08-26
forum: General Help
---

### Post by Unanimated on 2008-08-26
EDIT: I'm really sorry for being impatient, but 6 views? This is an extremely major problem! Please help!

I'm on the Live CD right now, because whenever I boot into Ubuntu the normal way, it comes up with tty1. I rebooted in recovery mode, and I selected reconfigure X, and dpkg, then I selected continue with normal boot. The commands showed up, and then it said "Starting GNOME Display Manager," across the screen it said "Fail." Is there any way to restore GDM? I really don't want to spend the time and not-money reinstalling Ubuntu from scratch.

---

### Post by Unanimated on 2008-08-26
**bump**

---

### Post by Unanimated on 2008-08-26
bump

---

### Post by Unanimated on 2008-08-26
bump

---

### Post by -Zeus- on 2008-08-26
try running "sudo dpkg-reconfigure gdm"

---

### Post by LateNiteTV on 2008-08-26
why dont u kill the xserver, drop to a shell and startx from there?

---

### Post by Unanimated on 2008-08-26
@LateNiteTV: I've tried that already.

@-Zeus-: It said reload failed. I think that GDM was literally deleted from my computer, so I tried apt-get install gdm. It said it was already the latest version, so I tried apt-get remove gdm. It came back with an error message. I tried apt-get install gdm again, and it came back with another error message. I tried apt-get update, and it failed to get it from all my software sources. I tried apt-get --fix-missing, and nothing happened. I tried apt-get update --fix-missing, and it failed to get anything from any of my sources once again.

---

### Post by -Zeus- on 2008-08-26
try this;
```
sudo apt-get -f install
sudo apt-get update
sudo apt-get remove --purge gdm
sudo apt-get install gdm
```

---

### Post by Unanimated on 2008-08-27
I tried to do that, but it couldn't get the packages from any of my software sources. It said "failed to fetch" in front of all of them. I guess I'll do a clean reinstall - all I really want is my music and my virtualbox hard drive, and I can burn those to a CD.

---

### Post by Unanimated on 2008-08-27
bump

---

