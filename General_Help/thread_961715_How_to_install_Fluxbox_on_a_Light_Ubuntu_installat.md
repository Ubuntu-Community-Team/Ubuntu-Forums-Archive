---
title: "How to install Fluxbox on a Light Ubuntu installation?"
date: 2008-10-28
forum: General Help
---

### Post by NintendoTogepi on 2008-10-28
It currently has XFCE but I want to try Fluxbox.

How would I do this? I typed sudo apt-get fluxbox but that didn't work.

---

### Post by Elfy on 2008-10-28
what error did you get from that command?

---

### Post by snowpine on 2008-10-28
> **NintendoTogepi said:**
> It currently has XFCE but I want to try Fluxbox.

How would I do this? I typed sudo apt-get fluxbox but that didn't work.

The correct command is actually 'sudo apt-get install fluxbox'. The 'install' part is pretty important!

Then, log out and from the login screen choose Sessions then Fluxbox.

---

### Post by Elfy on 2008-10-28
didn't see that :)

---

### Post by snowpine on 2008-10-28
> **forestpixie said:**
> didn't see that :)

Couldn't see the forest for the trees, eh?

---

### Post by Elfy on 2008-10-28
yep - it was snow on the pines :lol:

---

### Post by kerry_s on 2008-10-28
> **NintendoTogepi said:**
> It currently has XFCE but I want to try Fluxbox.

How would I do this? I typed sudo apt-get fluxbox but that didn't work.

```
sudo apt-get install fluxbox menu
sudo update-menus
```

if you don't update-menus before switch to fluxbox you won't have one.

---

### Post by NintendoTogepi on 2008-10-29
Thanks, it worked...I prefer XFCE, though.

---

### Post by kerry_s on 2008-10-29
> **NintendoTogepi said:**
> Thanks, it worked...I prefer XFCE, though.

yeah, everyone 1 has there preference, me i'm a jwm fan, all other wm's aren't worth my time.

---

### Post by darrenn on 2008-10-29
They just released the Fluxbox version of linux mint. I hear it's pretty good. Might want to give it a try.

---

### Post by Xiong Chiamiov on 2008-10-29
You could, of course, use [fluxbuntu]("http://fluxbuntu.org/").

---

### Post by Elfy on 2008-10-29
I don't think fluxbuntu has been worked on since 7.10

The new fluxbox mint looks ok from what I've seen of it - installed but not used much yet.

---

### Post by Xiong Chiamiov on 2008-10-29
> **forestpixie said:**
> I don't think fluxbuntu has been worked on since 7.10


Oh, I see that now.  I don't believe I've ever looked past the front page, and I didn't notice that the copyright is 2007...  It's a shame.

---

### Post by Elfy on 2008-10-29
Nothing to stop you doing a minimal and fluxbox install though - I have one that uses 1.7Gb

[https://help.ubuntu.com/community/Installation/MinimalCD](https://help.ubuntu.com/community/Installation/MinimalCD)
[https://help.ubuntu.com/community/Installation/LowMemorySystems](https://help.ubuntu.com/community/Installation/LowMemorySystems)

---

