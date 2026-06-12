---
title: "Terminal problem :S"
date: 2008-10-23
forum: General Help
---

### Post by Spider44 on 2008-10-23
hello, i am using Ubuntu 8.10 and after the first update i did my terminal got me this, every time i try to connect as su


```
stevosteve@stevosteve-laptop:~$ su
Password: 
su: Authentication failure

```

the strange is that the password is not incorrect becouse i use it for all other cases that it needs password, like when i use the add/remove application thing etc.

thanks for your time

---

### Post by jerome1232 on 2008-10-23
That's because root login is disabled in Ubuntu, if you need to run a command as root just prepend 'sudo' to it, and authenticate with your own password.

You can also use 'sudo -i' to gain a root shell.

I think you should give this a read [https://wiki.ubuntu.com/RootSudo](https://wiki.ubuntu.com/RootSudo)

---

### Post by sisco311 on 2008-10-23
by default the root account is disabled in ubuntu.

you can start a root shell with:
```
sudo -i
```


read more here:[https://help.ubuntu.com/community/RootSudo]("https://help.ubuntu.com/community/RootSudo")

---

### Post by mschutte on 2008-10-23
> **Spider44 said:**
> hello, i am using Ubuntu 8.10 and after the first update i did my terminal got me this, every time i try to connect as su


```
stevosteve@stevosteve-laptop:~$ su
Password: 
su: Authentication failure

```

the strange is that the password is not incorrect becouse i use it for all other cases that it needs password, like when i use the add/remove application thing etc.

thanks for your time

Hi there,

The su command in linux is used to switch to anonther user. When you do not specify a user name e.g. fred, the system defaults to the root account. So the password it requires when using su is that of the root user. I would suggest you use ***sudo su -***.

Martin.

---

### Post by Spider44 on 2008-10-23
Thanks for the help ppl :D :D :D :D

---

### Post by sisco311 on 2008-10-23
You're welcome.

Please mark the thread solved by selecting 
**Mark this thread as solved** from the [COLOR="Red"]**Thread Tools**[/COLOR].

---

