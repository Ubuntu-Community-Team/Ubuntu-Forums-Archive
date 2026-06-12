---
title: "OK, what's the su password?"
date: 2008-11-01
forum: General Help
---

### Post by Qu0ll on 2008-11-01
I have just installed Intrepid and it asked me to setup a user name and password which I entered.  Now when I need to run something as su it asks for the super user password but this does not appear to be the same as my user password.

So how do I know what Ubuntu has configured the su password to be???

-Qu0ll

---

### Post by SunnyRabbiera on 2008-11-01
We do not use the su command in ubuntu
to gain root access use the command sudo and then type in your password

---

### Post by Earl_Maroon on 2008-11-01
To use su you need to use the command
```
sudo su
```
su on its own won't work as the poster before me said.

---

### Post by SuperSonic4 on 2008-11-01
> **SunnyRabbiera said:**
> We do not use the su command in ubuntu
to gain root access use the command sudo and then type in your password

+1

su -username is used to change users in terminal without logging out. For example:```
sonic@sonic-desktop:$ su - tails
``` you'd get

```
tails@sonic-desktop
``` even though you logged in initially as sonic and will be sonic when you close the terminal

---

### Post by Qu0ll on 2008-11-01
Ah, go it now - thanks!

-Qu0ll

---

### Post by SunnyRabbiera on 2008-11-01
yeh if you bunp into a set of instructions or something that suggest using su, substitute it with sudo and it will work a good percent of the time

---

### Post by wgrant on 2008-11-01
> **Earl_Maroon said:**
> To use su you need to use the command
```
sudo su
```
su on its own won't work as the poster before me said.

Redundancy is present in this redundant sentence.

sudo -i, please.

---

### Post by juanbretti on 2008-11-29
Oh, now I get it! Thanks!

---

### Post by davidbilla on 2008-11-29
The password for su is that of your root account, if you have one. The password, I mean!:)

---

### Post by juanbretti on 2008-11-29
Also, another way is to write:

```
$ sudo bash
```

---

