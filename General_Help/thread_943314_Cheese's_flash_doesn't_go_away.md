---
title: "Cheese's flash doesn't go away"
date: 2008-10-10
forum: General Help
---

### Post by wersdaluv on 2008-10-10
Whenever I take a picture with Cheese, the flash doesn't go away (or do I have to wait for minutes?). The white screen stays on my monitor so I just keep on finding ways to kill cheese every time I take a picture.

How do I fix this?

---

### Post by Lee_Machine on 2009-01-13
Im have the exact problem. Did you find a fix?

---

### Post by wersdaluv on 2009-01-13
I deleted cheese's configuration files sitting on /home/user/.gconf/apps. I hope, it works for you too. :)

---

### Post by Lee_Machine on 2009-01-25
Nope, didnt work. I fogot about this issue until I was just using cheese.

Any other ideas?

---

### Post by Lee_Machine on 2009-01-25
So according to a thread on gnome bugzilla this is an issue with gnome and cheese but it's a cheese upsteam issue.

[HERE]("http://http://bugzilla.gnome.org/attachment.cgi?id=125572&action=view") is the patch that needs to applied to cheese.webcam.c

Fixed it for me.

Antother work around was to use the spacebar to take a picture.

The bug is suppoed to be gone in the next cheese release.

Which I checked the cheese homepage and the unstable version is out.

---

### Post by wersdaluv on 2009-01-26
Ooh. Mine works fine now. I'm on Intrepid, btw

---

