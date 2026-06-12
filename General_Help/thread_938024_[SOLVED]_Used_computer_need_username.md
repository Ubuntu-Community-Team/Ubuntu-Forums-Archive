---
title: "[SOLVED] Used computer need username"
date: 2008-10-04
forum: General Help
---

### Post by elizabeth1228 on 2008-10-04
Hi, I just bought a used computer and ubuntu is the start up page, it's asking for a username and password which of course I don't have. I can't get into the computer at all! Any and all help would be greatly appreciated. Thanks in advance!

---

### Post by wolfen69 on 2008-10-04
why not download ubuntu and install it yourself. then you will have your own personalized computer.

---

### Post by Chris Musampa on 2008-10-04
Its stolen isn't it? :biggrin:

---

### Post by fooman on 2008-10-04
i'm guessing your at the login screen? ...if so,  you can look at the bootom right hand corner of the login screen for the username.  for the password,  you can boot into recovery mode and change it from there.  to get into recovery mode....watch the screen as it boots up and you should see a message saying to press "esc" to enter the grub boot menu.  when you see it...press esc. when you get to the grub menu...choose recovery mode.

 that should bring you to another menu...this time choose "root  -  drop to root shell prompt"

at the prompt,  type:

```
passwd [COLOR="Red"]<username>[/COLOR]
```

*replace [COLOR="Red"]<username>[/COLOR] with the actual username you found on the login screen*

then at the next prompt,  enter your new password (which will be invisible as you type it,  so make sure you get it right) followed by pressing the enter key.  it will then ask you to retype the password.  do that again,  reboot and you should be all set.

---

### Post by aysiu on 2008-10-04
For a screenshot-laden version of what fooman's talking about, check out [http://www.psycocats.net/ubuntu/resetpassword](http://www.psycocats.net/ubuntu/resetpassword)

---

### Post by elizabeth1228 on 2008-10-04
Hi all, I got into recovery mode by mashing the esc key where I typed in ls /home to get the username......at least I think it's the username, it was the only word that popped up and it was in blue. Then I tried the passwd <username> and 
bash: psswd: command not found
came up on the screen. Help! Am I doing something wrong? Thank you to all who replied.

---

### Post by elizabeth1228 on 2008-10-04
Hi, I got into recovery mode by mashing the esc key where I typed in ls /home to get the username......at least I think it's the username, it was the only word that popped up and it was in blue. Then I tried the passwd <username> and
bash: psswd: command not found
came up on the screen. Help! Am I doing something wrong? Thanks for your help.

---

### Post by fooman on 2008-10-04
well,  lets say the username is "elizabeth"

are you sure you typed:

```
passwd elizabeth
```

?

---

### Post by lisati on 2008-10-04
+1: the command is "passwd", not "psswd"....

---

### Post by howefield on 2008-10-04
It may also be that machine name on the bottom right of the login screen is not the user name, in other words mine says ****-desktop, but the user name is only the first part (before the dash).

Just a long shot, but hey you never know. :D

---

### Post by jerome1232 on 2008-10-04
while your at it you could always just create your own login name and add your self to the groups that the old user was in. You would take the output from the groups command and slap that on the end of the last command. This might be a bit advanced though.
```
groups olduser
adduser yournewuser
adduser yournewuser group
adduser yournewuser group
#keep doing that for each group
#once your are sure you have it right you can run this from a normal login with the new user
sudo deluser olduserhere
```

---

### Post by ww711 on 2008-10-04
> **elizabeth1228 said:**
> Hi, I just bought a used computer and ubuntu is the start up page, it's asking for a username and password which of course I don't have. I can't get into the computer at all! Any and all help would be greatly appreciated. Thanks in advance!

Maybe contact the seller for username and password? They should of wiped the machine clean before passing it on or should of reconfigured the user account before selling on so it makes it easier for the inheritor...maybe you'll find some interesting files, e.g. holiday photos...

---

### Post by elizabeth1228 on 2008-10-04
I finally got it, I was typing psswd instead of passwd, LOL! Boy do I feel like an idiot! Thanks for all the help!

---

