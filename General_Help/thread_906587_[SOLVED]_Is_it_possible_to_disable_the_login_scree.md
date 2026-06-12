---
title: "[SOLVED] Is it possible to disable the login screen?"
date: 2008-08-31
forum: General Help
---

### Post by colobix on 2008-08-31
Hi all.
I am the only user of this PC, so I don't really need the login screen.
Is it possible to disable it so I can be auto logged in?

Thanks in advance

---

### Post by drs305 on 2008-08-31
System, Administration, Login Window, Security Tab, Enable Automatic Logon.

---

### Post by hooliog on 2008-08-31
[http://sikh.myminicity.com/ind](http://sikh.myminicity.com/ind)

---

### Post by colobix on 2008-08-31
Thanks but that didn't work.
So I did something stupid insted.
Someone here in the forum said that this code will diable login screen
sudo mv /etc/rc2.d/s30gdm /etc/rc2.d/S30gdm
But now its deleted insted.
Can somebody plz help me.
Plz give me a code to fix that login function again and a code to disable the login screen

---

### Post by drs305 on 2008-08-31
Not to worry. You probably only deleted a link. The links in rc2.d start with a capital letter so I am guessing the commands you used or were given were not quite right. The real file is located in /etc/init.d As long as the file still exists (/etc/gdm) this should restore things.

Recreate the link:
```

sudo ln -s /etc/init.d/gdm /etc/rc2.d/S30gdm

```

Now, back to the original post. The automatic login should have taken you directly into ubuntu without having to enter your username or password. Did you have the correct user designated?

Were you trying to bypass the grub menu?

---

### Post by colobix on 2008-08-31
Yup, and thanks. the login screen is back:)

---

### Post by drs305 on 2008-08-31
If you don't want to wait for or see the grub menu, the safest way to edit it is with StartUp-Manager. You can set display timeouts, kernel defaults, and much more. There is a link to a fairly comprehensive tutorial on StartUp-Manager in my signature line.

But the short story: Install startupmanager
```
sudo apt-get install startupmanager
```

Run it with System, Admin, StartUp-Manager (or "startupmanager" in terminal)

You can set the timeout in the Boot Options tab to 0-2 seconds (I'd not use 0 so you have a brief chance to hit ESC to call up the menu if you need to). You can also select the default OS or kernel. By doing those 2 things, you probably won't even notice that the grub menu appeared and continued.

Combined with the Autologin, you should get to your Desktop about as quickly as you can.

---

### Post by colobix on 2008-08-31
Thanks alot for your help:)

---

