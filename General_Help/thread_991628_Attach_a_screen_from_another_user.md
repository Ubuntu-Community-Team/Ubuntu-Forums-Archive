---
title: "Attach a screen from another user?"
date: 2008-11-24
forum: General Help
---

### Post by orion2087 on 2008-11-24
I have rTorrent running for wTorrent in a dedicated user (disabled SSH) with a screen session. I've been looking for a way to attach this screen in my normal user but I haven't found what I'm looking for quite yet.

I've read something about changing permissions on a pts, but aside from what I see in /dev/pts I'm not quite sure what a pts is and how to attach the other user's screen afterwards.

Any insight guys?
Thanks!

---

### Post by __Ryan__ on 2008-11-24
Is there a reason you can't switch to that user and then reattch to the screen session?

```
sudo -u *username* screen -dr
```

---

### Post by orion2087 on 2008-11-24
Yes, sudo or su cause this error:

```
Cannot open your terminal '/dev/pts/2' - please check.
```

---

### Post by linux_tech on 2008-11-24
You may need to change the permissions for the terminal, see this for more details
[http://ubuntuforums.org/archive/index.php/t-813115.html](http://ubuntuforums.org/archive/index.php/t-813115.html)

---

