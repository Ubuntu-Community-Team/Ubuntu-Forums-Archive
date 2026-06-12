---
title: "Dont remember password    HELP"
date: 2008-09-29
forum: General Help
---

### Post by rokkyofnh on 2008-09-29
I just installed and set a user name password at start up. I cannot remember what I used for a password and consequently cannot get logged into my desktop. Does anyone out there know how this newbie can reset or bypass the login password to start using ubuntu

---

### Post by jerome1232 on 2008-09-29
Okay, you will need to:

Reboot your machine Start mashing the escape key until you get a GRUB menu that gives you a list of options, you want the second one down it'll say recovery in the name, hit enter to boot into it.

Some text will fly by, some magic will happen, then you should have a blue screen with options.

One of those options is to drop to a root prompt, go ahead and select it.

Now you will be at a prompt that should look something like
```
root@computer:~#
```
great now type the following code to change your user's password

```
passwd [usernamehere]
reboot
```
If your username were joe that would be
passwd joe

It should ask you for a new password twice, then after you type reboot and enter the computer will........ reboot!

Go ahead and login with your new password.



If you don't remember the username you chose at the intial setup either then do this, it will list all users home directories on your system, they are titled the same as your users
```
ls /home
```

---

### Post by rokkyofnh on 2008-09-30
Thank you jerome I will give it a shot! I am new to ubuntu and linux so I've got some learning to do. Just had it with Microsoft. Now I need to find drivers and I'm on my way. Can you recomend any good books on the OS.

I appreciate your assistance

---

