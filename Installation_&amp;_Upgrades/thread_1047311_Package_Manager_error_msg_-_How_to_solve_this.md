---
title: "Package Manager error msg - How to solve this?"
date: 2009-01-22
forum: Installation &amp; Upgrades
---

### Post by aneslin85 on 2009-01-22
Guys,
I tried to install some deb applications, ( picasa )
i followed all steps which u guys mentioned in this same forum.

and those applications are works fine.

Now, in my Ubuntu8.10 Top bar Package manager indicate there is an error.

when i open the Package Manager, it says:
> E: Type '“deb' is not known on line 60 in source list /etc/apt/sources.list
E: The list of sources could not be read.
Go to the repository dialog to correct the problem.
E: _cache->open() failed, please report.

How can i solv this problem,?
i am totally new to Ubuntu/Linux.
cud u pls gv me the step by step info?
than ks in advance.

---

### Post by avtolle on 2009-01-22
Could you please do (in Terminal)```
cat /etc/apt/sources.list
``` then paste the output here in your next post?

---

### Post by aneslin85 on 2009-01-24
> **avtolle said:**
> Could you please do (in Terminal)```
cat /etc/apt/sources.list
``` then paste the output here in your next post?

thanks avtolle,

here is the output,

```
home@ubuntu:~$ cat /etc/apt/sources.list
# deb cdrom:[Ubuntu 8.10 _Intrepid Ibex_ - Release i386 (20081029.5)]/ intrepid main restricted
# See http://help.ubuntu.com/community/UpgradeNotes for how to upgrade to
# newer versions of the distribution.

deb http://us.archive.ubuntu.com/ubuntu/ intrepid main restricted
deb-src http://us.archive.ubuntu.com/ubuntu/ intrepid main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb http://us.archive.ubuntu.com/ubuntu/ intrepid-updates main restricted
deb-src http://us.archive.ubuntu.com/ubuntu/ intrepid-updates main restricted

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team. Also, please note that software in universe WILL NOT receive any
## review or updates from the Ubuntu security team.
deb http://us.archive.ubuntu.com/ubuntu/ intrepid universe
deb-src http://us.archive.ubuntu.com/ubuntu/ intrepid universe
deb http://us.archive.ubuntu.com/ubuntu/ intrepid-updates universe
deb-src http://us.archive.ubuntu.com/ubuntu/ intrepid-updates universe

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
## team, and may not be under a free licence. Please satisfy yourself as to 
## your rights to use the software. Also, please note that software in 
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
deb http://us.archive.ubuntu.com/ubuntu/ intrepid multiverse
deb-src http://us.archive.ubuntu.com/ubuntu/ intrepid multiverse
deb http://us.archive.ubuntu.com/ubuntu/ intrepid-updates multiverse
deb-src http://us.archive.ubuntu.com/ubuntu/ intrepid-updates multiverse

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
# deb http://us.archive.ubuntu.com/ubuntu/ intrepid-backports main restricted universe multiverse
# deb-src http://us.archive.ubuntu.com/ubuntu/ intrepid-backports main restricted universe multiverse

## Uncomment the following two lines to add software from Canonical's
## 'partner' repository. This software is not part of Ubuntu, but is
## offered by Canonical and the respective vendors as a service to Ubuntu
## users.
# deb http://archive.canonical.com/ubuntu intrepid partner
# deb-src http://archive.canonical.com/ubuntu intrepid partner

# Line commented out by installer because it failed to verify:
# deb http://security.ubuntu.com/ubuntu intrepid-security main restricted
# Line commented out by installer because it failed to verify:
# deb-src http://security.ubuntu.com/ubuntu intrepid-security main restricted
# Line commented out by installer because it failed to verify:
# deb http://security.ubuntu.com/ubuntu intrepid-security universe
# Line commented out by installer because it failed to verify:
# deb-src http://security.ubuntu.com/ubuntu intrepid-security universe
# Line commented out by installer because it failed to verify:
# deb http://security.ubuntu.com/ubuntu intrepid-security multiverse
# Line commented out by installer because it failed to verify:
# deb-src http://security.ubuntu.com/ubuntu intrepid-security multiverse
“deb http://www.getautomatix.com/apt edgy main”
home@ubuntu:~$ 

```

---

### Post by aneslin85 on 2009-01-30
any help ????

---

### Post by encmonkey on 2009-01-30
Hey there - 

Yup, the issue is that last line that got added to the file:
“deb [http://www.getautomatix.com/apt](http://www.getautomatix.com/apt) edgy main”

first - the quotes there are what's breaking it - it doesn't recognize an entry like "deb.

I'd delete that last line using any kind of text editor and then run (in a terminal)
sudo apt-get update

Hope this helps
-ian

---

### Post by aneslin85 on 2009-02-03
> **encmonkey said:**
> Hey there - 

Yup, the issue is that last line that got added to the file:
“deb [http://www.getautomatix.com/apt](http://www.getautomatix.com/apt) edgy main”

first - the quotes there are what's breaking it - it doesn't recognize an entry like "deb.

I'd delete that last line using any kind of text editor and then run (in a terminal)
sudo apt-get update

Hope this helps
-ian


thanks for the repyl bro,
i opend that file using a text editor, but i could not edit that,
when i try to save the edited one, it says 
```
Could not save the file /etc/apt/sources.list.
You do not have the permissions necessary to save the file. Please check that you typed the location correctly and try again.
```
:(

how can i edit that file using terminal?
pls help.
thansk in advance.

---

### Post by howefield on 2009-02-03
Use a terminal and type 

```
sudo gedit /etc/apt/sources.list
```

Then enter your password and you should be able to edit and save.

---

### Post by aneslin85 on 2009-02-03
ahhh Its worked Bro,

I used 
>  sudo nano /etc/apt/sources.list


now its OKay.

thanks a lot for ur time. :)

and thx a lot for > [http://ubuntuforums.org/showthread.php?t=276879](http://ubuntuforums.org/showthread.php?t=276879)

---

### Post by aneslin85 on 2009-02-04
> **howefield said:**
> Use a terminal and type 

```
sudo gedit /etc/apt/sources.list
```

Then enter your password and you should be able to edit and save.

thanks a lot howefield,
i got some experiences, thank u all forum guys. :popcorn:

---

