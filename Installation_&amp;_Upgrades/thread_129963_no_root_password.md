---
title: "no root password"
date: 2006-02-15
forum: Installation &amp; Upgrades
---

### Post by bela on 2006-02-15
Hi, 
this is not my first installation of ubuntu, but at each release there is a root passwd problem. At the installation step, it didn't ask for a root passwd, and so threre is not root passwd at all, and of course couldn't administrate.
To fix that I alwaus use my sarge disk 1 to repear the password.
Is it not time to fix the problem?
best regards
bela

---

### Post by Lanrond on 2006-02-15
In Ubuntu there is **no root password** because the root user is not enabled.
When you need to perform a *command* with root privileges you have to type: **sudo *command***.
The password you will be asked for is you user password.

I think this also should be a FAQ. :-)

---

### Post by Tiede on 2006-02-15
Actually, it is a [ wiki entry](https://wiki.ubuntu.com/RootSudo) on it. It should help him understand the whys and what-nots of the root password being disabled.

---

### Post by Simian on 2006-02-15
[QUOTE=Lanrond]
When you need to perform a *command* with root privileges you have to type: **sudo *command***.
[/QUOTE]

I didn't like this at first. But you get used to it (or I did anyway) and now I miss it when I'm using another distro.

Sudo give me an extra sense of security...

---

### Post by anirban.sam on 2006-02-15
if you want to use root, just issue: sudo passwd root

---

### Post by LordBug on 2006-02-15
I would *really* suggest you never enable the root account.  It's absolutely unnecessary and just presents a target for remote attacks.  If you need root for an extended period of time, you can use:

sudo -i
sudo -s  (my choice)
sudo bash  (I'm told this works, never tried it)

Any of those will switch you into a root console until you exit out of it.

---

### Post by Simian on 2006-02-15
What about:

sudo su

doesn't that give you an equivelent of root

---

### Post by LordBug on 2006-02-15
[QUOTE=Simian]What about:

sudo su

doesn't that give you an equivelent of root[/QUOTE]

No idea :)  Never tried that one.  I just posted commands I could remember right off hand.

---

### Post by aysiu on 2006-02-15
Ubuntu is not built to have a root account enabled. Even if you enable a root login, the password you're asked for to use Synaptic and other programs requiring root privileges will be your *sudo* password.

Just get used to it. See the third link of my signature for details.

---

