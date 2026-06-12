---
title: "project?"
date: 2005-11-22
forum: General Help
---

### Post by theOrange on 2005-11-22
I can't install project (formally mr project) - there seems to be a conflict with libgda.

1) is this something that just needs a backport?

2) if so, what is the status on that

3) anything i can do - i really need something like this for work right now - this is all i need to report a successfull trial to my boss!

---

### Post by Xian on 2005-11-22
[QUOTE=theOrange]I can't install project (formally mr project) - there seems to be a conflict with libgda.[/QUOTE]
Can you post the error output in the terminal?

---

### Post by kennethb on 2005-11-22
Try using the Synaptic Package Manger and search for "planner". Have you used the Synaptic Package Manger before?

---

### Post by theOrange on 2005-11-23
Wow - either nobody read my post or there was miscommunication.

I found project via synaptic - that wasn't the prob.

The problem is with lib dependencies...

It depends on libgda2-3 BUT Breezy uses libgda0.

If i try to upgrade to libgda2 it ask to uninstall not only the lidbga0 stuff but also libgnomedb0 stuff - is this OK?

I don't want to mess anything up with side effects. 

If it is ok to upgrade to libgda2-3 than why wasn't this the default lib for Breezy?

Arghhh!

---

### Post by aschlapsi on 2005-11-23
Try to update the package list. Have you added other repositories (other than the Ubuntu ones - main, restricted, universe and multiverse) to your repository list?

---

### Post by Xian on 2005-11-23
I'm not getting that dep issue when installing the same package so I would advise checking your sources.list and ask perhaps if you have installed any software that is not in the official Ubuntu mirrors? This can indeed cause some problems.

```
$ sudo apt-get install mrproject
Reading package lists... Done
Building dependency tree... Done
The following extra packages will be installed:
  planner
Recommended packages:
  gda2-postgres
The following NEW packages will be installed:
  mrproject planner
0 upgraded, 2 newly installed, 0 to remove and 0 not upgraded.
Need to get 1751kB of archives.
After unpacking 4899kB of additional disk space will be used.
Do you want to continue [Y/n]?
```

---

### Post by kennethb on 2005-11-23
[QUOTE=theOrange]Wow - either nobody read my post or there was miscommunication.

I found project via synaptic - that wasn't the prob.

The problem is with lib dependencies...

It depends on libgda2-3 BUT Breezy uses libgda0.

If i try to upgrade to libgda2 it ask to uninstall not only the lidbga0 stuff but also libgnomedb0 stuff - is this OK?

I don't want to mess anything up with side effects. 

If it is ok to upgrade to libgda2-3 than why wasn't this the default lib for Breezy?

Arghhh![/QUOTE]

Ooops! Sorry from misreading your question (see above quote). I have not come across this problem and I'm using Breezy (5.10). I'm using "Planner" (aka Mr Project) fairly regularly for my work. I'll stayed subscribed to this thread and contribute if I start to experience this problem and or come up with a solution.

---

### Post by theOrange on 2005-11-23
Thanks for all your replies.

So  I might have installed other software that caused this dependency issue? I'll go ahead and post my sources.list and what packages i have installed locally. Maybe you guys will notice something??? 

If not, should i just start uninstalling non-official stuff and try reinstalling project until i've isolated the dependency issues? Is there a way to search what dependecies installed packages have so i could find out what is using libgda2-3?


SOURCES.LIST
## official 5.10
deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) breezy main multiverse restricted universe 
deb-src [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) breezy main multiverse restricted universe

## official 5.10 updates
deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) breezy-updates main restricted 
deb-src [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) breezy-updates main  restricted 

## official 5.10 security patches
deb [http://security.ubuntu.com/ubuntu/](http://security.ubuntu.com/ubuntu/) breezy-security main restricted
deb-src [http://security.ubuntu.com/ubuntu/](http://security.ubuntu.com/ubuntu/) breezy-security main  restricted 

## 5.10 backports
deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) breezy-backports main restricted universe multiverse
deb-src [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) breezy-backports main restricted universe multiverse

################################################################################

## latest breezy wine
deb [http://wine.sourceforge.net/apt/](http://wine.sourceforge.net/apt/) binary/

## latest breezy BPMx
deb [http://eros.vlo.gda.pl/~szuwarek/files/linux/bmpx/](http://eros.vlo.gda.pl/~szuwarek/files/linux/bmpx/) ./

## breezy free and non-free repo
deb [http://antesis.freecontrib.org/mirrors/ubuntu/plf/](http://antesis.freecontrib.org/mirrors/ubuntu/plf/) breezy free non-free
deb-src [http://antesis.freecontrib.org/mirrors/ubuntu/plf/](http://antesis.freecontrib.org/mirrors/ubuntu/plf/) breezy free non-free
##deb [http://public.planetmirror.com/pub/plf/ubuntu/plf/](http://public.planetmirror.com/pub/plf/ubuntu/plf/) breezy free non-free
##deb-src [http://public.planetmirror.com/pub/plf/ubuntu/plf/](http://public.planetmirror.com/pub/plf/ubuntu/plf/) breezy free non-free

## breezy extras
deb [http://seveas.ubuntulinux.nl/](http://seveas.ubuntulinux.nl/) breezy-seveas breezy-extras
deb-src [http://seveas.ubuntulinux.nl/](http://seveas.ubuntulinux.nl/) breezy-seveas breezy-extras


LOCALLY INSTALLED
azureus 2.3.0.4-3
gsynaptics 0.9.3-0ubuntu2
laptop-mode-tools 1.11-1
retroclient 7.0.0-2
sharpmusique 1.0-1
ymessenger 1.0.4_1

---

### Post by Xian on 2005-11-23
[QUOTE=theOrange]So  I might have installed other software that caused this dependency issue? I'll go ahead and post my sources.list and what packages i have installed locally. Maybe you guys will notice something??? [/QUOTE]
Since I can install the pkg with no dep conflicts and you can not, the problem has to either be with your source list or with a locally installed package that is not from the official Ubuntu mirrors. Some output from a terminal might shed light on what the exact issue is on your system.

In the meantime start eliminating possible fail points. The first is your source list. You have a number of repos in there that are not pulling from official Ubuntu mirrors, and this might be part of the trouble. Comment out everything except what is listed below, then run your 'apt-get update' and 'apt-get install' session again. If there are more errors then post the output of both.

```
SOURCES.LIST
## official 5.10
deb http://archive.ubuntu.com/ubuntu/ breezy main multiverse restricted universe 
deb-src http://archive.ubuntu.com/ubuntu/ breezy main multiverse restricted universe

## official 5.10 updates
deb http://archive.ubuntu.com/ubuntu/ breezy-updates main restricted 
deb-src http://archive.ubuntu.com/ubuntu/ breezy-updates main restricted 

## official 5.10 security patches
deb http://security.ubuntu.com/ubuntu/ breezy-security main restricted
deb-src http://security.ubuntu.com/ubuntu/ breezy-security main restricted 

## 5.10 backports
deb http://archive.ubuntu.com/ubuntu/ breezy-backports main restricted universe multiverse
deb-src http://archive.ubuntu.com/ubuntu/ breezy-backports main restricted universe multiverse
```

```
$ sudo apt-get update
$ sudo apt-get install mrproject
```

---

### Post by theOrange on 2005-11-23
[QUOTE=Xian]Since I can install the pkg with no dep conflicts and you can not, the problem has to either be with your source list or with a locally installed package that is not from the official Ubuntu mirrors. Some output from a terminal might shed light on what the exact issue is on your system.

In the meantime start eliminating possible fail points. The first is your source list. You have a number of repos in there that are not pulling from official Ubuntu mirrors, and this might be part of the trouble. Comment out everything except what is listed below, then run your 'apt-get update' and 'apt-get install' session again. If there are more errors then post the output of both.

```
SOURCES.LIST
## official 5.10
deb http://archive.ubuntu.com/ubuntu/ breezy main multiverse restricted universe 
deb-src http://archive.ubuntu.com/ubuntu/ breezy main multiverse restricted universe

## official 5.10 updates
deb http://archive.ubuntu.com/ubuntu/ breezy-updates main restricted 
deb-src http://archive.ubuntu.com/ubuntu/ breezy-updates main restricted 

## official 5.10 security patches
deb http://security.ubuntu.com/ubuntu/ breezy-security main restricted
deb-src http://security.ubuntu.com/ubuntu/ breezy-security main restricted 

## 5.10 backports
deb http://archive.ubuntu.com/ubuntu/ breezy-backports main restricted universe multiverse
deb-src http://archive.ubuntu.com/ubuntu/ breezy-backports main restricted universe multiverse
```

```
$ sudo apt-get update
$ sudo apt-get install mrproject
```[/QUOTE]


I did that and the problem seems to be:

The following packages have unmet dependencies:
  planner: Depends: libgda2-3 but it is not going to be installed
E: Broken packages

I guess my question is why don't i have libgda2-3? Instead i have libgda0?
This was a freash Breezy install - is libgda2-3 the default lib for Breezy? If yes, what app did i install that reverted me back?

So, i seem to have a understand the problem. I guess my main issues is if there is an easy way to find what installed package uses libgda? Selecting and then clicking "Properties" and checking the "Dependencies" tab is slow and a major PITA.

Thanks...

---

### Post by Xian on 2005-11-24
[QUOTE=theOrange]I guess my question is why don't i have libgda2-3? Instead i have libgda0?[/QUOTE]
This is not possible to answer for certain, but the most likely reason would be that you installed an application that was dependent upon libgda0 and it simply got installed automagically. When apt gives you the message "Depends: libgda2-3 but it is not going to be installed", that generally means either one of two things: (1) You have some broken packages on your system that need to be fixed before further installations can take place, or (2) Installing the package means removing other libraries which would require your approval.

You can check for both instances with the commands below:

```
$ sudo apt-get -f install
$ sudo apt-get install libgda2-3
```

---

### Post by gmmazlum on 2006-07-13
Do a search in package.ubuntu.com for your library requested and distribution
download it then dpkg -i It should work

---

