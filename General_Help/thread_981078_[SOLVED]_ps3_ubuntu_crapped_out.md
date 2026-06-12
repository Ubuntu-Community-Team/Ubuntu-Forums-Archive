---
title: "[SOLVED] ps3 ubuntu crapped out"
date: 2008-11-13
forum: General Help
---

### Post by XarvoX on 2008-11-13
Im noob on ubuntu, but am familiar with mac os x.
Ive been trying to replace my stationary home computer with my ps3 running ubuntu (gnome, unknown version).

After spending several hours setting it up i finally got it working early this morning.

So i ran the software update (202 new updates) and left it running.

An hour later my girlfriend woke up, went out and turned off the ps3 with the switch, unaware of the software update.



So now comes the problem:

When i boot linux, it loads login-window, allows me to log in but nothing loads after the login-window.


from my mac experience i assume i crapped out my user account, so this shouldnt be a huge problem to take care of, but how do i do it?

i can access the shell (ctrl+alt+F1) during the login window (and after), but no menu, icons or others apppear after login.

---

### Post by Syock on 2008-11-13
You should try reinstalling the system. Maybe by doing 'dpkg --configure -a' on tty1, since you said you can ctrl-alt-f1

---

### Post by prshah on 2008-11-13
> **XarvoX said:**
> i can access the shell (ctrl+alt+F1) during the login window (and after), but no menu, icons or others apppear after login.

As suggested, use the command```
sudo dpkg-reconfigure -a
``` to recover from an interrupted update / upgrade. However, it's better you do this from a recovery mode prompt; can you access recovery mode? It's in the GRUB menu (Press ESC while booting) but I don't know if GRUB installs or not in a PS3 installation.

---

### Post by XarvoX on 2008-11-14
i dont know what caused it, but after running the sudo command hinted above, and restarting the gnome it logged me in just fine :D


im writing this on my ps3 :)


thanx guys!:popcorn:

---

### Post by prshah on 2008-11-14
> **XarvoX said:**
> 
im writing this on my ps3 :)


OK, If you consider the matter solved, can you mark the thread as solved? Near the top right hand side of the page is a link to "Thread Tools"; click this, then click "Mark thread as solved".

---

