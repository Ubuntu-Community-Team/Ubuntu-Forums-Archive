---
title: "my home folder is not where it should be...."
date: 2005-11-26
forum: General Help
---

### Post by floyd27 on 2005-11-26
Hi..
I just had to reinstall breezy..
I reinstalled just the /root partition.. I already had a /home partition and just left it..
Now I have to go into /media floder to access my stuff.
if i go to /home folder its a new one with nothing in it..
How do i just get it to load the first /home folder?
thanx

---

### Post by teaker1s on 2005-11-26
sounds like it's been deleted

---

### Post by Xian on 2005-11-26
[QUOTE=floyd27]if i go to /home folder its a new one with nothing in it.
[/QUOTE]
I would think you just have the mountpoint set incorrectly. 
Go into your fstab file and change the /media path to /home.

---

### Post by keybreckaba on 2005-11-26
did you tell breezy during the instatllation to use that partition as /home?

---

### Post by floyd27 on 2005-11-26
Yes i tod it that it was the home folder.
I can access it as normal but its in the media folder?
I will try to rename it and ill tell how it goes..
thanx

---

### Post by floyd27 on 2005-11-26
Got it..
had to change the fstab..
thanx a bunch...

---

