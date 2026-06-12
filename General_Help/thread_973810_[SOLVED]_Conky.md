---
title: "[SOLVED] Conky?"
date: 2008-11-07
forum: General Help
---

### Post by Yezinki on 2008-11-07
Hi there,

I am learning desktop customization for the first time on Ubuntu 8.10.

Am unable to install Conky.

Any help would be appreciated,

Regards,

Yezinki.

---

### Post by Yezinki on 2008-11-07
[B]ubuntu@ubuntu-laptop:~$ sudo apt-get install conky
[sudo] password for ubuntu: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
conky is already the newest version.
The following packages were automatically installed and are no longer required:
  libsvga1 libglide2 libggi-target-x libggi2 libgii1 libgii1-target-x
Use 'apt-get autoremove' to remove them.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
ubuntu@ubuntu-laptop:~$ apt-get autoremove
E: Could not open lock file /var/lib/dpkg/lock - open (13 Permission denied)
E: Unable to lock the administration directory (/var/lib/dpkg/), are you root?
ubuntu@ubuntu-laptop:~$ 

[/B]

---

### Post by Yezinki on 2008-11-07
What do I do now??

---

### Post by slinkey1981 on 2008-11-07
> **Yezinki said:**
> [B]ubuntu@ubuntu-laptop:~$ sudo apt-get install conky

conky is already the newest version.

ubuntu@ubuntu-laptop:~$ apt-get autoremove
E: Could not open lock file /var/lib/dpkg/lock - open (13 Permission denied)
E: Unable to lock the administration directory (/var/lib/dpkg/), are you root?
[/B]

It says you installed conky previously.
It's saying you can't do 

```
apt-get autoremove
``` 

and it told you aren't root....  Cause you didn't use

```
sudo apt-get autoremove
```

Hope this helps some.

---

### Post by Yezinki on 2008-11-07
Thanks alot slinkey1981 you are one smart man,

Sorry about that, am a newbie in the world of Ubuntu after 15 years with windows.

Regards,

Yezinki.

[B]
ubuntu@ubuntu-laptop:~$ sudo apt-get install conky
[sudo] password for ubuntu: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
conky is already the newest version.
The following packages were automatically installed and are no longer required:
  libsvga1 libglide2 libggi-target-x libggi2 libgii1 libgii1-target-x
Use 'apt-get autoremove' to remove them.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
ubuntu@ubuntu-laptop:~$ sudo apt-get autoremove
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages were automatically installed and are no longer required:
  libsvga1 libglide2 libggi-target-x libggi2 libgii1 libgii1-target-x
The following packages will be REMOVED:
  libggi-target-x libggi2 libgii1 libgii1-target-x libglide2 libsvga1
0 [/B]upgraded, 0 newly installed, 6 to remove and 0 not upgraded.
After this operation, 4456kB disk space will be freed.
Do you want to continue [Y/n]? y
(Reading database ... 116012 files and directories currently installed.)
Removing libggi-target-x ...
Removing libggi2 ...
Removing libgii1-target-x ...
Removing libgii1 ...
Removing libglide2 ...
Removing libsvga1 ...
Processing triggers for man-db ...
Processing triggers for libc6 ...
ldconfig deferred processing now taking place
ubuntu@ubuntu-laptop:~$

---

### Post by Yezinki on 2008-11-07
Why this now


[B]ubuntu@ubuntu-laptop:~$ sudo apt-get install conky
Reading package lists... Done
Building dependency tree       
Reading state information... Done
conky is already the newest version.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
ubuntu@ubuntu-laptop:~$ zcat /usr/share/doc/conky/examples/conkyrc.sample.gz > ~/.conkyrc
gzip: /usr/share/doc/conky/examples/conkyrc.sample.gz: **No such file or directory**
ubuntu@ubuntu-laptop:~$ 




[/B]

---

### Post by slinkey1981 on 2008-11-07
Doesn't Conky install to;    **./etc/conky/**

What happens if you Alt-f2 and run conky?
I'm not exactly sure what it is that you are trying to do, so I don't know how much help I can be.
I am basically a Ubuntu n00b as well...

---

### Post by Yezinki on 2008-11-07
Thanks

 Its not what matters whether one is geek or a noob like me.......

What really matters is the willingness to help.

Regards,

Yezinki.

---

### Post by Thanoulis on 2008-11-07
Try to open a terminal and type *conky*
(Beware the caps lock.Linux is a case sensitive OS)
Also, you can type *man conky* in order to read the manual.
Hope that helps. :)

---

