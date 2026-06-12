---
title: "software manger problem"
date: 2009-09-01
forum: Installation &amp; Upgrades
---

### Post by bubsy100 on 2009-09-01
hello all 

i am newbi in ububtu  
when i try to open and software manger ( add/remove , syna packed manger or update manger i found this message 

--
**This is a major failure of your software management system. Please check for broken packages with synaptic, check the file permissions and correctness of the file '/etc/apt/sources.list' and reload the software information with: 'sudo apt-get update' and 'sudo apt-get install -f**

plz can anybody help me to fix this problem and explain me what is wrong ?

plz because i can not add or remove any application from my system ( ubuntu Hardy 8.04 )

---

### Post by oldos2er on 2009-09-01
Did you run the commands suggested? Here are the correct permissions you can check: -rw-r--r-- 1 root root 3564 2009-08-30 15:33 /etc/apt/sources.list

---

### Post by bubsy100 on 2009-09-01
plzz explain all steps

---

### Post by raymondh on 2009-09-01
EDIT : same as Ann's suggestion

Access synaptic (system > admnistration > synaptic package manager (type in password) > edit > fix broken packages)

Then reload or... close synaptic and access a terminal (applications > accessories) and type

sudo apt-get update

If you still get errors, check permissions.

---

### Post by bubsy100 on 2009-09-01
plz be noted that 

syna packed manger can not be opened at all and give me error problem

---

### Post by shredder12 on 2009-09-01
Okk. then lets do everything from command line.
go to application->accessories-> terminal

type the following commands
```
sudo chmod 644 /etc/apt/sources.list
```

this will set appropriate file permissions

then fix the broken packages 
```
sudo apt-get install -f
```

and now update
```
sudo apt-get update
```

then try opening synaptic or update manager..
hope this helps..

---

### Post by bubsy100 on 2009-09-01
thank u 
but its still not work , the same error is appeared 

plz tell me how can run it in permission mode because when i try enter root passwored in terminal

---

### Post by shredder12 on 2009-09-01
please open the terminal again and post the output of 

ls -l /etc/apt/sources.list

so that we may know what are the permissions set for this file..

---

### Post by bubsy100 on 2009-09-01
thanks  
i tried to do what you advised me but this error appeard in terminal 

plz help me , tell me in steps to understand 

sudo apt-get install -f

E: Type 'e' is not known on line 51 in source list /etc/apt/sources.list
E: The list of sources could not be read.

---

### Post by shredder12 on 2009-09-02
There is some error in the sources.list file..
so post the content of  that file..
do
```
gedit /etc/apt/sources.list
``` 

and post it..

---

### Post by raymondh on 2009-09-02
> **shredder12 said:**
> There is some error in the sources.list file..
so post the content of  that file..
do
```
gedit /etc/apt/sources.list
``` 

and post it..
.

---

### Post by bubsy100 on 2009-09-02
thanks 

here your advised command result 

---------
# deb cdrom:[Ubuntu 8.04 _Hardy Heron_ - Release i386 (20080423)]/ hardy main restricted
# See [http://help.ubuntu.com/community/UpgradeNotes](http://help.ubuntu.com/community/UpgradeNotes) for how to upgrade to
# newer versions of the distribution.


## Major bug fix updates produced after the final release of the
## distribution.

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
## team, and may not be under a free licence. Please satisfy yourself as to 
## your rights to use the software. Also, please note that software in 
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
# deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) hardy-backports main restricted universe multiverse

## Uncomment the following two lines to add software from Canonical's
## 'partner' repository. This software is not part of Ubuntu, but is
## offered by Canonical and the respective vendors as a service to Ubuntu
## users.
deb [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) hardy partner
deb-src [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) hardy partner

# Line commented out by installer because it failed to verify:
# deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) hardy-security main restricted
# Line commented out by installer because it failed to verify:
# deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) hardy-security main restricted
# Line commented out by installer because it failed to verify:
# deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) hardy-security universe
# Line commented out by installer because it failed to verify:
# deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) hardy-security universe
# Line commented out by installer because it failed to verify:
# deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) hardy-security multiverse
# Line commented out by installer because it failed to verify:
# deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) hardy-security multiverse

deb [http://download.skype.com/linux/repos/debian/](http://download.skype.com/linux/repos/debian/) stable non-free
e

deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) hardy main restricted
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) hardy restricted main #Added by software-properties

----------------------------------------------
what can i do now ???

---

### Post by drs305 on 2009-09-02
> **bubsy100 said:**
> 
deb [http://download.skype.com/linux/repos/debian/](http://download.skype.com/linux/repos/debian/) stable non-free
**[COLOR="Red"]e[/COLOR]**

deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) hardy main restricted
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) hardy restricted main #Added by software-properties

----------------------------------------------
what can i do now ???

The "e" on a separate line is your problem. All lines in sources.list should begin with "deb" or a "#" symbol.
Open sources.list for editing and remove that line. The "+51" should make gedit open on the line in error:
```

gksudo gedit +51 /etc/apt/sources.list

```

Save the file, then:
```

sudo apt-get update
sudo apt-get upgrade

```

---

### Post by bubsy100 on 2009-09-02
Dear [drs305]("http://ubuntuforums.org/member.php?u=223945")  

Thank u very much  because your help to solve my problem 

thank u again  

problem solved

---

