---
title: "GRUB help"
date: 2009-03-10
forum: Installation &amp; Upgrades
---

### Post by gEEEk on 2009-03-10
Hello guys.

When I boot up my computer I use GRUB to select my diffrent OS'.

What I'm trying to accomplish is so that the only things showing is:
[SIZE="3"]
Ubuntu 8.10, kernel 2.5.26-11-generic
Windows NT/2000/XP (loader)
[/SIZE]

But currently it looks like this:

[SIZE="3"]Ubuntu 8.10, kernel 2.5.26-11-generic
Ubuntu 8.10, kernel 2.5.26-11-generic (recovery mode)
Ubuntu 8.10, kernel 2.5.26-7-generic
Ubuntu 8.10, kernel 2.5.26-7-generic (recovery mode)
Windows NT/2000/XP (loader)[/SIZE]

**Is there a quick easy way to change this?** Because I don't need the other options but the ones listed before.

---

### Post by Neo_The_User on 2009-03-10
Yes you can. Open up a terminal and type in this.

```

cat /boot/grub/menu.lst

```

I will then give you a new menu.lst file and you can do

```

sudo nano /boot/grub/menu.lst

```

And replace the entire file with what I gave you. Just to make sure you won't mess anything up, I'll do it for you by giving you a new menu.lst that you can just copy and paste. One more thing, it should be 2.6.27 not 2.5 that is if you are using the Ubuntu stock kernels which is what it looks like. This would be much easier for you if you installed gedit so you could use gedit instead of nano.

Terminal:

```

sudo apt-get update && sudo apt-get dist-upgrade && sudo apt-get install gedit && gksudo gedit /boot/grub/menu.lst

```

---

### Post by gEEEk on 2009-03-10
What file?

Which one did you send me?

---

### Post by Neo_The_User on 2009-03-10
> **gEEEk said:**
> What file?

Which one did you send me?

/boot/grub/menu.lst

I haven't sent you it yet because I want to make sure its all right. If you're new to linux, i recommend not doing it yourself because it can lead to a messed up system.

---

### Post by gEEEk on 2009-03-10
No, I'm not new to Linux.

But I am new to GRUB.

Send me the file.

---

### Post by gEEEk on 2009-03-10
Nevermind, fixed it myself. Super easy.

Thank you for your help anyways!

---

### Post by Neo_The_User on 2009-03-10
> **gEEEk said:**
> Nevermind, fixed it myself. Super easy.

Thank you for your help anyways!

ah goodie

---

