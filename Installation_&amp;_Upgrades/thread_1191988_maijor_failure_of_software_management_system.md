---
title: "maijor failure of software management system"
date: 2009-06-19
forum: Installation &amp; Upgrades
---

### Post by devananda on 2009-06-19
IN JAUNTY,EEE PC 1000H 

I AM UNABLE TO USE THE PACKAGE MANAGER,UPDATE MANAGER AND ALSO ADD/REMOVE APPLICATION.

I GOT THIS MESSAGE!!!

Failed to check for installed and available applications

This is a major failure of your software management system. Please check for broken packages with synaptic, check the file permissions and correctness of the file '/etc/apt/sources.list' and reload the software information with: 'sudo apt-get update' and 'sudo apt-get install -f'


CAN SOMEONE EXPLAIN ME HOW TO ACCESS THE FILE  THAT IS INDICATED

THANK YOU

---

### Post by devananda on 2009-06-19
> **devananda said:**
> in jaunty,eee pc 1000h 

i am unable to use the package manager,update manager and also add/remove application.

I got this message!!!

Failed to check for installed and available applications

this is a major failure of your software management system. Please check for broken packages with synaptic, check the file permissions and correctness of the file '/etc/apt/sources.list' and reload the software information with: 'sudo apt-get update' and 'sudo apt-get install -f'


can someone explain me how to access the file  that is indicated ,,,i cant a

thank you
i cant access the package manager!!!!!!!!!!!!!!!!!!!!!

---

### Post by blackxored on 2009-06-19
Easy man.

Ok, try to give a little more info and we'll be happy to help.

Please tell us if you installed something recently that failed, if you have edited /etc/apt/sources.list or any of the files in /etc/apt/sources.list.d if applicable.

I think the message is pretty clear. Review sources.list, find broken packages, etc.

Sincerely.

---

### Post by devananda on 2009-06-19
thanks for your help,,,i cant remember i failed to install something,,

anyway when  i try to access the update manager or package manager i am rejected with the message

E: Encountered a section with no Package: header
E: Problem with MergeList /var/lib/apt/lists/us.archive.ubuntu.com_ubuntu_dists_intrepid-backports_restricted_binary-i386_Packages
E: The package lists or status file could not be parsed or opened.
E: _cache->open() failed, please report.

i am quiet new in ubuntu,,,so i really dont know what to do:?

---

### Post by DGortze380 on 2009-06-19
Please slow down, open a terminal (Accessories -> Terminal) and post the output of 

```

cat /etc/apt/sources.list

```

please also post the output of

```

ls -al /etc/apt | grep sources

```

---

### Post by devananda on 2009-06-19
ok here is the outcome :

ryeknow@ryeknow-mini:~$ cat /etc/apt/sources.list
# deb cdrom:[Ubuntu 8.10 _Intrepid Ibex_ - Release i386 (20081029.5)]/ intrepid main restricted
# See [http://help.ubuntu.com/community/UpgradeNotes](http://help.ubuntu.com/community/UpgradeNotes) for how to upgrade to
# newer versions of the distribution.

deb [http://es.archive.ubuntu.com/ubuntu/](http://es.archive.ubuntu.com/ubuntu/) jaunty main restricted multiverse
deb-src [http://es.archive.ubuntu.com/ubuntu/](http://es.archive.ubuntu.com/ubuntu/) jaunty restricted main multiverse universe #Added by software-properties

## Major bug fix updates produced after the final release of the
## distribution.

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team. Also, please note that software in universe WILL NOT receive any
## review or updates from the Ubuntu security team.
deb [http://es.archive.ubuntu.com/ubuntu/](http://es.archive.ubuntu.com/ubuntu/) jaunty universe

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
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) intrepid-backports main restricted universe multiverse
# deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) intrepid-backports main restricted universe multiverse

## Uncomment the following two lines to add software from Canonical's
## 'partner' repository. This software is not part of Ubuntu, but is
## offered by Canonical and the respective vendors as a service to Ubuntu
## users.
deb [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) intrepid partner
deb-src [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) intrepid partner
deb [http://security.ubuntu.com/ubuntu/](http://security.ubuntu.com/ubuntu/) jaunty-security universe main restricted multiverse
deb-src [http://security.ubuntu.com/ubuntu/](http://security.ubuntu.com/ubuntu/) jaunty-security universe main restricted multiverse #Added by software-properties
deb [http://es.archive.ubuntu.com/ubuntu/](http://es.archive.ubuntu.com/ubuntu/) jaunty-updates universe main restricted multiverse
deb-src [http://es.archive.ubuntu.com/ubuntu/](http://es.archive.ubuntu.com/ubuntu/) jaunty-updates universe main restricted multiverse #Added by software-properties

ryeknow@ryeknow-mini:~$ ls -al /etc/apt | grep sources
-rw-r--r--   1 root root  2460 2009-06-19 21:56 sources.list
drwxr-xr-x   2 root root  4096 2009-06-19 14:53 sources.list.d
-rw-r--r--   1 root root  3017 2009-05-15 21:04 sources.list.distUpgrade
-rw-r--r--   1 root root  2381 2009-06-19 21:56 sources.list.save

thanks again for your help

---

### Post by devananda on 2009-06-19
> **devananda said:**
> ok here is the outcome :

ryeknow@ryeknow-mini:~$ cat /etc/apt/sources.list
# deb cdrom:[Ubuntu 8.10 _Intrepid Ibex_ - Release i386 (20081029.5)]/ intrepid main restricted
# See [http://help.ubuntu.com/community/UpgradeNotes](http://help.ubuntu.com/community/UpgradeNotes) for how to upgrade to
# newer versions of the distribution.

deb [http://es.archive.ubuntu.com/ubuntu/](http://es.archive.ubuntu.com/ubuntu/) jaunty main restricted multiverse
deb-src [http://es.archive.ubuntu.com/ubuntu/](http://es.archive.ubuntu.com/ubuntu/) jaunty restricted main multiverse universe #Added by software-properties

## Major bug fix updates produced after the final release of the
## distribution.

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team. Also, please note that software in universe WILL NOT receive any
## review or updates from the Ubuntu security team.
deb [http://es.archive.ubuntu.com/ubuntu/](http://es.archive.ubuntu.com/ubuntu/) jaunty universe

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
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) intrepid-backports main restricted universe multiverse
# deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) intrepid-backports main restricted universe multiverse

## Uncomment the following two lines to add software from Canonical's
## 'partner' repository. This software is not part of Ubuntu, but is
## offered by Canonical and the respective vendors as a service to Ubuntu
## users.
deb [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) intrepid partner
deb-src [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) intrepid partner
deb [http://security.ubuntu.com/ubuntu/](http://security.ubuntu.com/ubuntu/) jaunty-security universe main restricted multiverse
deb-src [http://security.ubuntu.com/ubuntu/](http://security.ubuntu.com/ubuntu/) jaunty-security universe main restricted multiverse #Added by software-properties
deb [http://es.archive.ubuntu.com/ubuntu/](http://es.archive.ubuntu.com/ubuntu/) jaunty-updates universe main restricted multiverse
deb-src [http://es.archive.ubuntu.com/ubuntu/](http://es.archive.ubuntu.com/ubuntu/) jaunty-updates universe main restricted multiverse #Added by software-properties

ryeknow@ryeknow-mini:~$ ls -al /etc/apt | grep sources
-rw-r--r--   1 root root  2460 2009-06-19 21:56 sources.list
drwxr-xr-x   2 root root  4096 2009-06-19 14:53 sources.list.d
-rw-r--r--   1 root root  3017 2009-05-15 21:04 sources.list.distUpgrade
-rw-r--r--   1 root root  2381 2009-06-19 21:56 sources.list.save

thanks again for your help
what should i do now:-k

---

### Post by tgalati4 on 2009-06-19
From your listing, did you perform a distribution upgrade from Intrepid to Jaunty on May 15 at 9 pm?

You have a mixture of Intrepid and Jaunty repositories.  Which version of Ubuntu do you want to run?  If it's Jaunty, then comment all instances of Intrepid with ##.

sudo apt-get clean
sudo apt-get update
sudo apt-get upgrade

---

### Post by raymondh on 2009-06-19
> **tgalati4 said:**
> From your listing, did you perform a distribution upgrade from Intrepid to Jaunty on May 15 at 9 pm?

You have a mixture of Intrepid and Jaunty repositories.  Which version of Ubuntu do you want to run?  If it's Jaunty, then comment all instances of Intrepid with ##.

sudo apt-get clean
sudo apt-get update
sudo apt-get upgrade

Good catch tgalati4.

---

### Post by devananda on 2009-06-20
):Pthank you,,,now everything seems to work again.

i send you peace light

---

### Post by raymondh on 2009-06-20
> **devananda said:**
> ):Pthank you,,,now everything seems to work again.

i send you peace light

Congratulations  :)

If you want to .... as it will help others who may experience the same issue and are searching for solutions, you may want to mark your thread SOLVED.  On both threads, go to the first post you made > edit > advanced > type SOLVED in front of your thread title > save.

Also, if you have not done so, go to launchpad and send them a note that your bug report is solved.

Once again, peace to you as well.

---

### Post by techrascal on 2009-06-20
exactly the same problem with me.....
how am i suposed to comment the jaunty part.....in the terminal where the result came??
plz help...m not too good with terminal interface

---

### Post by raymondh on 2009-06-20
> **techrascal said:**
> exactly the same problem with me.....
how am i suposed to comment the jaunty part.....in the terminal where the result came??
plz help...m not too good with terminal interface

Hello techrascal,

Put a ## in front of the line.  That way, your sytem will not read it.

- Open a terminal (applications > accessories).
- Type or copy/paste this command

```
cat /etc/apt/sources.list
```

That will bring up your sources list.
- Go through the list and comment those you wish to leave out.  As mentioned above, put a ## sign in front of the line you don't want
- Save and exit
- Then (in terminal)

```
sudo apt-get update
```

If you are not sure or if you still receive errors ..... kindly make a new thread either asking for more clarification or if with errors, explaning what you have done so far and the errors involved. 

Thanks and good luck.

---

### Post by DGortze380 on 2009-06-20
> **raymondhenson said:**
> Hello techrascal,

Put a ## in front of the line.  That way, your sytem will not read it.

- Open a terminal (applications > accessories).
- Type or copy/paste this command

```
cat /etc/apt/sources.list
```

That will bring up your sources list.
- Go through the list and comment those you wish to leave out.  As mentioned above, put a ## sign in front of the line you don't want
- Save and exit
- Then (in terminal)

```
sudo apt-get update
```



This will not work...

use either

```

gksudo gedit /etc/apt/sources.list

```

or

```

sudo nano /etc/apt/sources.list

```

---

### Post by raymondh on 2009-06-20
> **DGortze380 said:**
> 

```

gksudo gedit /etc/apt/sources.list

```

or

```

sudo nano /etc/apt/sources.list

```

you are right, i forgot the editor. thank you.

---

### Post by techrascal on 2009-07-04
thanx..
that gedit thing worked..
i didnt know of this kind of editor in linux..

---

### Post by jomigo on 2009-07-07
Hi, thought I would jump on to this as I am having the exact problem.
My first time on this forum and am not to sure of the process.
 
Tried to install Java and it froze half way through.
 
Did what was suggested in this thread and no luck.
 
Any assistance would be greatly appreciated.
 
Just dont know where to start looking for the problem as I am very new to ubuntu.
 
J

---

### Post by richardh9936 on 2009-08-18
Dear tgalati4,
My eee-pc also had a reference to INTREPID in sources.list  It was one of the security libraries, too.

Source manager didn't have ticks in the boxes; adding them seemed to fix  the offending line, then all worked fine.

Many thanks.

---

### Post by altog33k on 2009-08-25
**I'm having the same issue, same error message. Please someone help**


altog33k@altog33k-desk:~$ cat /etc/apt/sources.list

deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) edgy main restricted universe multiverse
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) edgy main restricted universe multiverse

## Major bug fix updates produced after the final release of the
## distribution.
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) edgy-updates main restricted universe multiverse
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) edgy-updates main restricted universe multiverse

## Uncomment the following two lines to add software from the 'universe'
## repository.
## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
# deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) edgy universe
# deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) edgy universe

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
# deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) edgy-backports main restricted universe multiverse
# deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) edgy-backports main restricted universe multiverse

deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) edgy-security main restricted universe multiverse
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) edgy-security main restricted universe multiverse
# deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) edgy-security universe
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) edgy-proposed restricted main universe multiverse
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) edgy-proposed restricted main universe multiverse
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) edgy-backports restricted main universe multiverse
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) edgy-backports restricted main universe multiverse
# deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) edgy-security universe
deb [ftp://archive.ubuntu.com/ubuntu/](ftp://archive.ubuntu.com/ubuntu/) hoary
altog33k@altog33k-desk:~$ ls -al /etc/apt | grep sources
-rw-r--r--   1 root root 2297 2009-08-25 10:55 sources.list
drwxr-xr-x   2 root root 4096 2006-09-27 18:44 sources.list.d
-rw-r--r--   1 root root 2187 2009-08-25 10:55 sources.list.save
altog33k@altog33k-desk:~$

---

### Post by slakkie on 2009-08-25
you are running edgy? Although I see hoary repo's as well.

run lsb_release -a

If you have either:

Edgy 6.10
Feisty 7.04
Gutsy 7.10

Then please following the followin guide:
[https://help.ubuntu.com/community/EOLUpgrades](https://help.ubuntu.com/community/EOLUpgrades)

Or reinstall a supported version, eg Hardy (8.04)/Intrepid (8.10)/Jaunty (9.04)

If you run any of the above, please let us know.

---

