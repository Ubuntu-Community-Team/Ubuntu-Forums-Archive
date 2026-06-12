---
title: "Unable to install updates, games, downloads, etc."
date: 2009-03-10
forum: Installation &amp; Upgrades
---

### Post by Kushing on 2009-03-10
When ever i try to install my updates or install downloaded content from the internet it is saying I need to run a "<something> config -a" application before trying to install. whenever I copy and past the name of this application to the run window and click run, it doesn't work. I am also a new user so it is kind of confusing to use. A little help?

---

### Post by avtolle on 2009-03-10
Open a terminal (Applications>Accessories>Terminal) and at the prompt do```
sudo dpkg --configure -a
```which will ask you for your password. Type in your password with which you log in; you **will not**see anything on the screen as you type, no *s, nada. After entering your password, press Enter. Post any error messages you get. If no error messages, then (still in the terminal) do ```
sudo aptitude update
sudo aptitude safe-upgrade
```and, if you get any error messages, post them here. Good luck.

---

### Post by Kushing on 2009-03-10
so the whole sudo dpkg --configure -a, will i have to just type that this one time or anytime i want to install or update something?

---

### Post by avtolle on 2009-03-10
> **Kushing said:**
> so the whole sudo dpkg --configure -a, will i have to just type that this one time or anytime i want to install or update something?
Hopefully, only this once (no guarantees). Apparently, something happened when you were doing a previous update/download such as a network problem, which didn't allow the package(s) to be finally installed. Running this command will (hopefully) fix the problem, thereby allowing you to update, etc, as you wish; often it does, and unless another condition such as the one which created the first problem appears in a subsequent attempt, you won't need to run it again.

---

