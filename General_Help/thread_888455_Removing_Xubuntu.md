---
title: "Removing Xubuntu"
date: 2008-08-13
forum: General Help
---

### Post by brandon826 on 2008-08-13
I need help removing Xubuntu completely off my computer. Can anyone give me instructions? Thanks!

---

### Post by Ryadt on 2008-08-13
Removing to install what OS?

---

### Post by hyper_ch on 2008-08-13
have you tried to find some instructions yet yourself?

---

### Post by iaculallad on 2008-08-13
By booting a LiveCD and use the Gparted utility to format you're drive.

---

### Post by brandon826 on 2008-08-14
It already is dual booting off windows and xubuntu. Will i need to format the whole drive or just its partition? 

I am doing this because I forgot the username and password and I have no idea on how to recover or change them. I saw a few command line ideas, but they were for ubuntu and didn't work!

Please help! I would rather just change the login info...

---

### Post by jolx on 2008-08-14
the only difference between Xubuntu and Ubuntu is the desktop environment

i think you might be able to boot into recovery mode and add a new user, but idk

how about u search for some info on it im sure theres heaps

---

### Post by tangibleorange on 2008-08-14
> **brandon826 said:**
> It already is dual booting off windows and xubuntu. Will i need to format the whole drive or just its partition? 

I am doing this because I forgot the username and password and I have no idea on how to recover or change them. I saw a few command line ideas, but they were for ubuntu and didn't work!

Please help! I would rather just change the login info...

When you boot up your computer there should be an option called "recovery boot". Press down on the keyboard and then enter when you are highlighted on it.
After some messages fly by (ignore them), you should be left with a black screen (you may be asked what you want to do, if so, select 'root prompt').
Type this:
```
cat /etc/passwd | grep /bin/bash
```
you should then see your username and an entry for 'root'. now type
```
passwd *username*
```
replacing *username* with the username you found from above (not 'root').
You should then be prompted to enter a new password. After you have entered and confirmed one, type:
```
shutdown -r now
```
to reboot. when you reboot, select the normal boot option and log in with your new password :).

---

### Post by LitusMayol on 2008-08-14
(How can I fire out this post!? I got wrong and now I don't know how to erase it. Sorry)

---

