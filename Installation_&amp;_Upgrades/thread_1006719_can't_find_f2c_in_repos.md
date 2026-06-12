---
title: "can't find f2c in repos"
date: 2008-12-09
forum: Installation &amp; Upgrades
---

### Post by r.stiltskin on 2008-12-09
On my laptop running Kubuntu Feisty - as far as I can tell I have main restricted universe and multiverse enabled, but apt-get gives:
Couldn't find package - f2c
and of course it's not listed by Adept or Synaptic.

I had no trouble finding and installing it from repositories on my Ubuntu Gutsy desktop, and according to [http://packages.ubuntu.com/feisty/f2c](http://packages.ubuntu.com/feisty/f2c) it should be in Feisty also.

Did the Kubuntu people take it out?

---

### Post by Partyboi2 on 2008-12-09
Maybe double check that you have the universe repos enabled. You could manually download the package and install it as another option.

---

### Post by jenkinbr on 2008-12-09
Feisty went End Of life not long ago, and there has been discussion in ubuntu-devel mailing list about pulling feisty archives, but let's see...

I checked out this page ( [http://packages.ubuntu.com/feisty/i386/f2c/download](http://packages.ubuntu.com/feisty/i386/f2c/download) )
Some of the links work, some of them don't.

Could you post the output of ```
cat /etc/apt/sources.list
```

Chances are that you are using a repository mirror that is no longer availible.

---

### Post by r.stiltskin on 2008-12-09
Do you see anything wrong with this:


```
deb http://archive.ubuntu.com/ubuntu/ feisty main restricted 
deb-src http://archive.ubuntu.com/ubuntu/ feisty main restricted 

## Major bug fix updates produced after the final release of the
## distribution.
deb http://archive.ubuntu.com/ubuntu/ feisty-updates main restricted 
deb-src http://archive.ubuntu.com/ubuntu/ feisty-updates main restricted 

##deb http://us.archive.ubuntu.com/ubuntu/ feisty-proposed main restricted universe multiverse
##deb-src http://us.archive.ubuntu.com/ubuntu/ feisty-proposed main restricted universe multiverse

## Uncomment the following two lines to add software from the 'universe'
## repository.
## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
deb http://archive.ubuntu.com/ubuntu/ feisty universe multiverse 
deb-src http://archive.ubuntu.com/ubuntu/ feisty universe multiverse 

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
# deb http://us.archive.ubuntu.com/ubuntu/ edgy-backports main restricted universe multiverse 
# deb-src http://us.archive.ubuntu.com/ubuntu/ edgy-backports main restricted universe multiverse 

deb http://archive.ubuntu.com/ubuntu/ feisty-security main restricted 
deb-src http://archive.ubuntu.com/ubuntu/ feisty-security main restricted 
deb http://archive.ubuntu.com/ubuntu/ feisty-security universe 
deb-src http://archive.ubuntu.com/ubuntu/ feisty-security universe 

## the following needed to satisfy codeblocks dependencies
deb http://apt.wxwidgets.org/ feisty-wx main 




```

---

### Post by jenkinbr on 2008-12-09
Try this instead.  First, back up your sources.list file using ```
sudo cp /etc/apt/sources.list /etc/apt/sources.list.bak
```

Now run this command: ```
kdesudo kedit /etc/apt/sources.list
```

Select everything in the file and delete it.

Now, copy and paste the code below:
```
deb http://mirrors.cs.wmich.edu/ubuntu/ feisty main restricted 
deb-src http://mirrors.cs.wmich.edu/ubuntu/ feisty main restricted 

## Major bug fix updates produced after the final release of the
## distribution.
deb http://mirrors.cs.wmich.edu/ubuntu/ feisty-updates main restricted 
deb-src http://mirrors.cs.wmich.edu/ubuntu/ feisty-updates main restricted 

##deb http://us.archive.ubuntu.com/ubuntu/ feisty-proposed main restricted universe multiverse
##deb-src http://us.archive.ubuntu.com/ubuntu/ feisty-proposed main restricted universe multiverse

## Uncomment the following two lines to add software from the 'universe'
## repository.
## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
deb http://mirrors.cs.wmich.edu/ubuntu/ feisty universe multiverse 
deb-src http://mirrors.cs.wmich.edu/ubuntu/ feisty universe multiverse 

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
# deb http://us.archive.ubuntu.com/ubuntu/ edgy-backports main restricted universe multiverse 
# deb-src http://us.archive.ubuntu.com/ubuntu/ edgy-backports main restricted universe multiverse 

deb http://mirrors.cs.wmich.edu/ubuntu/ feisty-security main restricted 
deb-src http://mirrors.cs.wmich.edu/ubuntu/ feisty-security main restricted 
deb http://mirrors.cs.wmich.edu/ubuntu/ feisty-security universe 
deb-src http://mirrors.cs.wmich.edu/ubuntu/ feisty-security universe 

## the following needed to satisfy codeblocks dependencies
deb http://apt.wxwidgets.org/ feisty-wx main 




```

What I did in the code above is replace all active occurences of the string 'archive.ubuntu.com/' with 'mirrors.cs.wmich.edu/', a mirror that still has the feisty archives intact.

Now run ```
sudo apt-get update
```

and try to install the software.

edit: if you have a different mirror you would like to try, go ahead and replace mirrors.cs.wmich.edu/ubuntu with that mirror instead.  mirrors.cs.wmich.edu/ubuntu is a nice fast mirror that I use, but your speed may very depending on how far away you live.

---

### Post by r.stiltskin on 2008-12-09
Thanks, you did a bit more work than was necessary -- Kubuntu includes Adept which has a drop-down menu to change mirrors automatically. In addition to changing the mirror, I also enabled feisty-backports.  Unfortunately it didn't help anyway.  f2c is still not there.

Anyway, I solved my immediate problem.  I realized all I really need right now is the header file so I went to the netlib.org repository, grabbed a copy of f2c.h & put it in /usr/local/include so I can compile my code.

The longer-term solution will be to do a dist-upgrade in the near future.

---

### Post by jenkinbr on 2008-12-09
When you do a dist-upgrade, be sure to go to hardy first.  I've heard that the direct upgrade path to intrepid doesn't work.

Also, I don't use KDE, so I don't know for sure how all the applications worked.  I installed adept once, but that was only to see if it supported exporting a download script, which it didn't.

---

