---
title: "Password different in GUI and CLI?"
date: 2008-09-18
forum: General Help
---

### Post by Sanix on 2008-09-18
I've just managed to install Ubuntu. It works fine but the root password doesn't work in the terminal but it works, when I have to enter it in the GUI directly. For example for Synaptics.
Why is it like that?

---

### Post by mb_webguy on 2008-09-18
"Root password"?  There shouldn't be a root password.

If you're talking about your user account password, which you are prompted to enter whenever you do anything that requires root privileges, on the other hand...  

If it works in one place it should work in the other.  However, in the command line, as a security measure the password prompt won't indicate that you're typing anything in.  If you type in the password correctly and hit enter, it will still work.  Other than one being designed for use with terminal applications and one being designed for use with GUI applications, "sudo" and "gksu" (or "gksudo") are the same thing.  What's good for one is good for the other as far as users and passwords are concerned.

---

### Post by iaculallad on 2008-09-18
If you're password works with Synaptics doesn't mean that it's a root account having the root password. It only mean that you're member of the admin group so you're given the privilege to do system configuration and application installation provided that you input the you're correct credentials when asked.
Ubuntu by default had disabled the root account thus, only users (usually user account created after Ubuntu installation) who are member of the admin (sudoer) group can do system-wide changes.

---

### Post by northern lights on 2008-09-18
[https://help.ubuntu.com/community/RootSudo]("https://help.ubuntu.com/community/RootSudo") might prove a worthy read.

---

### Post by Sanix on 2008-09-18
It is! Thanks a lot for all your answers!

---

