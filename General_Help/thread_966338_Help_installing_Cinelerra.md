---
title: "Help installing Cinelerra"
date: 2008-11-01
forum: General Help
---

### Post by FoxTheCave on 2008-11-01
Hey, I have Ubuntu 8.04 and I need some help installing Cinelerra.

I am using this guide to guide me: [http://cinelerra.org/docs/split_manual_en/cinelerra_cv_manual_en_2.html](http://cinelerra.org/docs/split_manual_en/cinelerra_cv_manual_en_2.html)

I installed the repository as it told me, here are the results

```
kayvan@kayvan-laptop:~$ sudo wget http://repository.akirad.net/dists/hardy.list -O /etc/apt/sources.list.d/akirad.list
[sudo] password for kayvan: 
--14:22:30--  http://repository.akirad.net/dists/hardy.list
           => `/etc/apt/sources.list.d/akirad.list'
Resolving repository.akirad.net... 78.47.64.240
Connecting to repository.akirad.net|78.47.64.240|:80... connected.
HTTP request sent, awaiting response... 200 OK
Length: 441 [text/plain]

100%[====================================>] 441           --.--K/s             

14:22:32 (24.68 MB/s) - `/etc/apt/sources.list.d/akirad.list' saved [441/441]

kayvan@kayvan-laptop:~$ wget -q http://repository.akirad.net/dists/akirad.key -O- | sudo apt-key add -
OK

```

So everything seemed alright there - but when I went into my Package Manager, I still could not see Cinelerra. I updated the list like my Package Manager told me to and everything. So I tried to install it from the command line like the guide told me, here are the results:

```
kayvan@kayvan-laptop:~$ apt-get update
E: Could not open lock file /var/lib/apt/lists/lock - open (13 Permission denied)
E: Unable to lock the list directory
kayvan@kayvan-laptop:~$ 
kayvan@kayvan-laptop:~$ apt-get install cinelerra
E: Could not open lock file /var/lib/dpkg/lock - open (13 Permission denied)
E: Unable to lock the administration directory (/var/lib/dpkg/), are you root?

```

Can anyone please help me?

---

### Post by Ryadt on 2008-11-01
Use sudo before apt-get
```
sudo apt-get update
```
```
sudo apt-get install cinelerra
```

---

### Post by FoxTheCave on 2008-11-01
Oh wow, thanks! Worked, its downloading now.

---

### Post by Ryadt on 2008-11-01
Great ;)
Have a look at this guide: 
[https://help.ubuntu.com/community/RootSudo](https://help.ubuntu.com/community/RootSudo)

Plz mark the thread as solved.

---

