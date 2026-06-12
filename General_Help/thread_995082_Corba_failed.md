---
title: "Corba failed"
date: 2008-11-27
forum: General Help
---

### Post by radiogirl on 2008-11-27
Whenever I try to run anything on my computer I get this message.


Adding client to server's list failed, CORBA error: IDL:omg.org/CORBA/COMM_FAILURE:1.0
Adding client to server's list failed, CORBA error: IDL:omg.org/CORBA/COMM_FAILURE:1.0
Adding client to server's list failed, CORBA error: IDL:omg.org/CORBA/COMM_FAILURE:1.0
Adding client to server's list failed, CORBA error: IDL:omg.org/CORBA/COMM_FAILURE:1.0
Adding client to server's list failed, CORBA error: IDL:omg.org/CORBA/COMM_FAILURE:1.0
Adding client to server's list failed, CORBA error: IDL:omg.org/CORBA/COMM_FAILURE:1.0
Adding client to server's list failed, CORBA error: IDL:omg.org/CORBA/COMM_FAILURE:1.0



Please!!!!!!  Please!!!!   Help!!!!

---

### Post by jon66xxx on 2009-12-11
Any luck with the error? I have the same problem.

---

### Post by jon66xxx on 2009-12-13
Along with the corba/comm failure i also get a Gnome power manager config defaults error. Any help please

---

### Post by john newbuntu on 2009-12-13
These are CORBA errors and they appear to be from the orbit libraries used by gnome.  Perhaps you could try reinstalling gdm and/or ubuntu-desktop, preferably from a terminal session and after stopping the gdm daemon.

---

### Post by jon66xxx on 2009-12-14
Thanks for the reply. Now do i reinstall gnome power manager or gnome desktop manager? I tried sudo apt-get --reinstall install gnome-power-manager  but had no luck. Or do i need a live cd? And if i do,how do i reinstall gnome?

---

### Post by john newbuntu on 2009-12-14
For the configuration errors, could you try doing this and see if it helps:
sudo dpkg --configure -a

---

### Post by jon66xxx on 2009-12-14
Nope that didnt fix it,i also tried going into recovery mode and updating the distro to 8.10 but no luck.

---

