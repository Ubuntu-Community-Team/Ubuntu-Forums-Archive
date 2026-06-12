---
title: "How to login as root?"
date: 2008-10-19
forum: General Help
---

### Post by rrajath on 2008-10-19
I'm using Ubuntu 8.04. How do I login as root?

---

### Post by Monotoko on 2008-10-19
You dont want to login as root, for any root commands, use "sudo" as a prefix before it

[https://help.ubuntu.com/community/RootSudo](https://help.ubuntu.com/community/RootSudo) 
will explain it in more detail

---

### Post by rrajath on 2008-10-19
Yeah. I can do that. But I just wanted to know how to login as root.

---

### Post by Monotoko on 2008-10-19
Logging in as root requires activating and putting a password on the root account, which really is not a good idea, as anyone trying to hack your box will know there is a root account, but will not know the names of your other accounts.

Besides, root cant run under x anyway, it must be run through terminal.

In order to give yourself root privileges in the terminal, use
```

sudo su

```
This will open a new terminal window, and you will have all root privileges, without comprising your system by making the root account active

---

### Post by sethvath on 2008-10-19
sudo su

---

### Post by geirha on 2008-10-19
The proper way is with either of 
```

sudo -s # non-login shell
sudo -i # login shell

```
As is explained in the link Monotoko posted.

---

### Post by rrajath on 2008-10-19
Thanx a lot.

---

### Post by sea_monkey987 on 2008-10-19
i would post it here, but i believe it is against the forum rules.  just google "login as root ubuntu" and it shows up as the second entry for ubuntux.org

---

### Post by Jonny0204 on 2008-10-19
if you're wanting to edit files which are restricted to root users, just type in the command:

sudo nautilus

then type ya password in, simple :)

---

### Post by humangod on 2008-10-19
I don't think it's such a good idea to discuss this. I mean seriously I don't think we ever need to log in as root permanently.

I hope I am not wrong.

---

### Post by Sam on 2008-10-19
> **humangod said:**
> I don't think it's such a good idea to discuss this. I mean seriously I don't think we ever need to log in as root permanently.

I hope I am not wrong.

You're right. Especially if you login to Gnome using root. But opening a terminal session as root is a time saver if you need to work as root on a box for a long time.

---

### Post by Amol Parithosh on 2008-10-19
Thanks a ton Jonny:)..,

---

### Post by aysiu on 2008-10-19
Just a couple of corrections here:

Do not use *sudo -s*. The proper command is ```
sudo -i
``` And do not use *sudo nautilus*. The proper command is ```
gksudo nautilus
```

The difference between the formers and the latters is a matter of which environment you use. If you use the formers, the environment is the user environment but with root privileges (which can result in files and settings accidentally changing ownership to root, which will leave you with a broken system). If you use the latters, the environment is root's, and the privileges are also root's.

---

### Post by bodhi.zazen on 2008-10-19
> **Jonny0204 said:**
> if you're wanting to edit files which are restricted to root users, just type in the command:

sudo nautilus

then type ya password in, simple :)

Thread closed. The OP question has been asked and answered, thank you everyone.

For graphical applications, such as nautilus, please use gksu

```
gksu nautilus
```

And, yes root logins are NOT supported here (with a few rare exceptions).

[Forum policy on log-in-as-root tutorials - Ubuntu Forums]("http://ubuntuforums.org/showthread.php?t=765414") 

[YARP - Yet another root post]("http://ubuntuforums.org/showpost.php?p=5769207&postcount=77")

---

