---
title: "Numlock"
date: 2005-11-17
forum: General Help
---

### Post by summit on 2005-11-17
Is there anyway to have numlock come up on the keyboard when you boot up?

I remember reading it somewhere in the forum but could not find it.

---

### Post by sirlancelot on 2005-11-17
type in the terminal
```
sudo apt-get install numlockx
```

---

### Post by ubuntu27 on 2005-11-17
Can this also work for BREEZY? [http://ubuntuguide.org/#numlockx](http://ubuntuguide.org/#numlockx)

---

### Post by sirlancelot on 2005-11-17
[QUOTE=ubuntu27]Can this also work for BREEZY? [http://ubuntuguide.org/#numlockx](http://ubuntuguide.org/#numlockx)[/QUOTE]
It should work, though for breezy all you need to do is install numlockx and it will do everything else for you.

---

### Post by aysiu on 2005-11-17
[QUOTE=ubuntu27]Can this also work for BREEZY? [http://ubuntuguide.org/#numlockx](http://ubuntuguide.org/#numlockx)[/QUOTE] Yes, it does. I used that for Breezy.

---

### Post by Mozzer on 2005-11-20
Alas, it didn't work for me...

```
mozzer@ubuntu:~$ sudo apt-get install numlockx
E: Could not get lock /var/lib/dpkg/lock - open (11 Resource temporarily unavailable)
E: Unable to lock the administration directory (/var/lib/dpkg/), is another process using it?

```

Any suggestions?

Thanks,
Mozzer

---

### Post by aysiu on 2005-11-20
It means you already have a program open that is conflicting with apt-get in the terminal--Synaptic Package Manager maybe? Or "Add Applications"?

---

### Post by BathroomNinja on 2005-12-03
Thank you for this thread!  I used Automatix on my wife's laptop and turning on numlock on a laptop = very bad.  So I just used apt-get remove to fix the problem, I just didn't know what package to remove.

Thanks again internet!

---

### Post by masingerz on 2005-12-04
i just tried it in breezy and this worked [http://ubuntuguide.org/#numlockx](http://ubuntuguide.org/#numlockx)
just installing numlockx didnt fix it I had to do all the steps in the doc

---

### Post by atoponce on 2005-12-04
Will this be included in Dapper?  It seems silly to have the user install this software, definitely if they don't know about it.  Honestly, who uses the 10-key without numlock?  It has to be one of those pet-peeves for most users.  I know it is for me.

---

### Post by aysiu on 2005-12-04
[QUOTE=atoponce]Honestly, who uses the 10-key without numlock?[/QUOTE] Laptop users. Their 10-key is part of the letters, I think.

I think ideally, Gnome should operate the way KDE does. You go to System > Preferences > Keyboard and then check a box that says "turn numlock on at startup."

---

### Post by atoponce on 2005-12-04
[quote=aysiu]Laptop users. Their 10-key is part of the letters, I think.[/quote] Depends on the laptop.  Some laptops with widescreens have a 10-key on the side of the keyboard.

[quote=ausiu]I think ideally, Gnome should operate the way KDE does. You go to System > Preferences > Keyboard and then check a box that says "turn numlock on at startup."[/quote] Agreed.

---

### Post by BathroomNinja on 2005-12-05
[QUOTE=aysiu]Laptop users. Their 10-key is part of the letters, I think.

I think ideally, Gnome should operate the way KDE does. You go to System > Preferences > Keyboard and then check a box that says "turn numlock on at startup."[/QUOTE]


I concur.  It sucks to have it enabled on my tiny laptop, but on my 2 desktops, it drives me nuts if it's not on.

---

