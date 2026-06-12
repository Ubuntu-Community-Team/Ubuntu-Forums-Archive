---
title: "username and password"
date: 2009-03-17
forum: Installation &amp; Upgrades
---

### Post by Ramaseko on 2009-03-17
Hi Friends!

I,ve just installed latest ubuntu and everything was fine until on start up the system asked me to enter username and password. I've not set up any username or password so i don't know what to type in. Is there a default usermane and password or what should i do, i'm confused. I can't wait to use my ubuntu.

Thanks!:(

---

### Post by D3ath on 2009-03-17
> **Ramaseko said:**
> Hi Friends!

I,ve just installed latest ubuntu and everything was fine until on start up the system asked me to enter username and password. I've not set up any username or password so i don't know what to type in. Is there a default usermane and password or what should i do, i'm confused. I can't wait to use my ubuntu.

Thanks!:(
When you installed ubuntu why didn't you put in a user or password it give you that option in the install.

you can use:
Press 
```
e
``` 
when it briefly pauses before booting. You will then be able to edit the boot options. Go to the end of the line and enter 
```
init=/bin/bash
``` 
This will bypass all startup procedures and give you root access. 

Run 
```
tail /etc/passwd
```
identify your username. Your root filesystem will be mounted readonly, so you'll want to run ```
mount -o remount,rw /
``` 
Then set your password with 
```
passwd yourusername
```

If there is no username just use the command
```
adduser
```

this will add a new user for you to login in with will also set the password for the user.

---

### Post by oldos2er on 2009-03-17
> **Ramaseko said:**
> Hi Friends!

I,ve just installed latest ubuntu and everything was fine until on start up the system asked me to enter username and password. I've not set up any username or password so i don't know what to type in. Is there a default usermane and password or what should i do, i'm confused. I can't wait to use my ubuntu.

Thanks!:(

 There's no default username and password. Something went seriously wrong with your installation if you didn't create a username and password.

---

### Post by sisco311 on 2009-03-17
> **D3ath said:**
> When you installed ubuntu why didn't you put in a user or password it give you that option in the install.

...

No need to edit the grub menu.
Just boot in *recovery mode *to reset the password.
Step-by-step instructions(with screen shots): [http://psychocats.net/ubuntu/resetpassword]("http://psychocats.net/ubuntu/resetpassword")

---

### Post by D3ath on 2009-03-17
> **oldos2er said:**
> There's no default username and password. Something went seriously wrong with your installation if you didn't create a username and password.

He must have a user name ubuntu wouldn't let the installer proceed without the user name and password.  There is something there he just has to find it.  and if not those steps should let him create another user without the re installation of the OS.

---

### Post by D3ath on 2009-03-17
> **sisco311 said:**
> No need to edit the grub menu.
Just boot in *recovery mode *to reset the password.
Step-by-step instructions(with screen shots): [http://psychocats.net/ubuntu/resetpassword]("http://psychocats.net/ubuntu/resetpassword")

Yes the problem is he doesn't know his username. so he either has to find out what it is or create a new user.

---

### Post by Ramaseko on 2009-03-17
Well i've just installed within windows and it did not prompt me to enter any username or password, I swear. I'll try the codes i,ve got from you guys and see if i can login.

---

### Post by sisco311 on 2009-03-17
> **Ramaseko said:**
> Well i've just installed within windows and it did not prompt me to enter any username or password, I swear. I'll try the codes i,ve got from you guys and see if i can login.


You are asked to enter your user name and password in Windows: 
[IMG]http://psychocats.net/ubuntu/images/wubi02.png[/IMG]

---

### Post by oldos2er on 2009-03-17
> **D3ath said:**
> He must have a user name ubuntu wouldn't let the installer proceed without the user name and password.  There is something there he just has to find it.  and if not those steps should let him create another user without the re installation of the OS.

 If the install CD is defective, it's possible. This isn't the first time it's happened.

---

### Post by Ramaseko on 2009-03-17
Thanks sisco311 I've used the rocovery console and your step-by-step guide, It's worked Bingo!!!, I'm loving't.

Thanks again:D

---

### Post by D3ath on 2009-03-17
> **Ramaseko said:**
> Thanks sisco311 I've used the rocovery console and your step-by-step guide, It's worked Bingo!!!, I'm loving't.

Thanks again:D

I'm curious. So was there a username u didn't know about? did you guess? How did you do it without knowing the username?

---

### Post by sisco311 on 2009-03-17
> **Ramaseko said:**
> Thanks sisco311 I've used the rocovery console and your step-by-step guide, It's worked Bingo!!!, I'm loving't.

Thanks again:D

You are welcome. 

BTW, it's [aysiu]("http://ubuntuforums.org/member.php?u=21941")'s guide. :)

---

### Post by sisco311 on 2009-03-17
> **D3ath said:**
> I'm curious. So was there a username u didn't know about? did you guess? How did you do it without knowing the username?

Your home directory name by default is the same as your username. :)
```
ls /home
```

---

### Post by D3ath on 2009-03-17
> **sisco311 said:**
> Your home directory name by default is the same as your username. :)
```
ls /home
```

gotcha. thats good to know. thanks. :D

---

### Post by theozzlives on 2009-03-17
That's something I did not know, I'll have to save this Thread.

---

