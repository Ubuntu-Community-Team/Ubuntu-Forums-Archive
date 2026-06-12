---
title: "Mozilla and terminal starting everytime i boot ubuntu."
date: 2008-07-23
forum: General Help
---

### Post by Avinash.Rao on 2008-07-23
Hi all,

I noticed this since yesterday, everytime i boot my Ubuntu 8.0 - Hardy on my laptop and login, an instance of mozilla and a terminal window starts!! How do i stop this?

---

### Post by WRDN on 2008-07-23
That seems very odd. Anyway, look in System > Preferences > Sessions for the applicable options, and if they are there, switch them off/ delete the entries.

---

### Post by Avinash.Rao on 2008-07-23
I checked all this, these services are not listed. I am wondering if its in the profile!

Can anyone help me with this?



> **WRDN said:**
> That seems very odd. Anyway, look in System > Preferences > Sessions for the applicable options, and if they are there, switch them off/ delete the entries.

---

### Post by Tim Sharitt on 2008-07-23
Look in ~/.gnome2/ for a file named session. If it exists, rename it (session.old or something) and logout and back in. That may fix your problem.

---

### Post by Avinash.Rao on 2008-07-24
Thanks, it worked. I would like to know more about this. How is this created? Does .gnome/2 directory store the gnome profile? 

> **Tim Sharitt said:**
> Look in ~/.gnome2/ for a file named session. If it exists, rename it (session.old or something) and logout and back in. That may fix your problem.

---

### Post by Tim Sharitt on 2008-07-24
The file is created by gnome-session-save. There are some configuration files in the folder, but others are scattered about elsewhere.

---

### Post by Execute_Method on 2008-07-24
> **Avinash.Rao said:**
> Thanks, it worked. I would like to know more about this. How is this created? Does .gnome/2 directory store the gnome profile?

System-->Preferences-->Sessions-->Session Options-->Remember Currently Running Applications

---

### Post by Tim Sharitt on 2008-07-24
> **Execute_Method said:**
> System-->Preferences-->Sessions-->Session Options-->Remember Currently Running Applications

I knew there had to be a way to save from the gui.

---

### Post by Avinash.Rao on 2008-07-25
Thanks :)

---

