---
title: "install Cinelerra"
date: 2009-09-03
forum: Installation &amp; Upgrades
---

### Post by red33m on 2009-09-03
I tried to install Cinelerra and it gave me this error....
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.
The following information may help to resolve the situation:

The following packages have unmet dependencies:
  cinelerra: Depends: liblame0 (>= 3.97) but it is not installable
             Depends: libmjpegtools0c2a (>= 1:1.8.0) but it is not installable
             Depends: libopenexr2ldbl (>= 1.2.2) but it is not installable
             Depends: libquicktimehv (= 1:2.1.0-2svn20082807ubuntuubuntu1) but it is not going to be installed
E: Broken packages

What do I do?

---

### Post by Partyboi2 on 2009-09-03
Hi, what repo did you add to install it?
You can fix the broken packages with
```
sudo apt-get -f install
```

---

### Post by red33m on 2009-09-03
> **Partyboi2 said:**
> Hi, what repo did you add to install it?
You can fix the broken packages with
```
sudo apt-get -f install
```

well I am a noob so repo stands for repositories.... I did what you said and it said that:
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages were automatically installed and are no longer required:
  libquicktime-dev libnettle2 libquicktime-doc liboop4 x11proto-kb-dev
  libcvaux1 lsh-server mesa-common-dev libx11-xcb1 libxdmcp-dev
  libkrb5-25-heimdal libhx509-3-heimdal xtrans-dev ttf-liberation
  x11proto-core-dev libgavl1 nettle-bin zlib1g-dev x11proto-input-dev
  libroken18-heimdal libcv1 libpthread-stubs0-dev libxau-dev libpthread-stubs0
  libhighgui1 libgl1-mesa-dev lsh-utils libx11-dev libwind0-heimdal winbind
  libxcb1-dev libasn1-8-heimdal
Use 'apt-get autoremove' to remove them.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.

what about now?

repositories I installed:
 #ubuntu edgy
deb [http://giss.tv/~vale/ubuntu32](http://giss.tv/~vale/ubuntu32) ./
deb-src [http://giss.tv/~vale/ubuntu32](http://giss.tv/~vale/ubuntu32) ./

---

### Post by Partyboi2 on 2009-09-03
Yes sorry repo= repositories, I take it you are using Jaunty? If you are then remove the 
```
deb [http://giss.tv/~vale/ubuntu32]("http://giss.tv/%7Evale/ubuntu32") ./
deb-src [http://giss.tv/~vale/ubuntu32]("http://giss.tv/%7Evale/ubuntu32") ./     
``` by going to Software Sources (System>Admin>Software Sources) and under the 3rd party software tab remove those 2 repositories. Then try adding these if you are using Jaunty, open a terminal (Applications>Accessories>Terminal) and type
```
echo deb http://akirad.cinelerra.org akirad-jaunty main | sudo tee /etc/apt/sources.list.d/akirad.list && wget -q http://akirad.cinelerra.org/dists/akirad.key -O- | sudo apt-key add - && sudo apt-get update
``````
sudo apt-get install cinelerracv
```[http://cinelerra.org/getting_cinelerra.php#ubuntu](http://cinelerra.org/getting_cinelerra.php#ubuntu)

---

### Post by red33m on 2009-09-03
It says that and it does nothing...what do I do wrong?

red33m@red33m-desktop:~$ sudo tee /etc/apt/sources.list.d/akirad.list && wget -q [http://akirad.cinelerra.org/dists/akirad.key](http://akirad.cinelerra.org/dists/akirad.key) -O-
sudo apt-key add -
sudo apt-key add -
sudo apt-key add -sudo apt-key add - && sudo apt-get update
sudo apt-key add -sudo apt-key add - && sudo apt-get update
sudo apt-get install cinelerracv
sudo apt-get install cinelerracv

---

### Post by red33m on 2009-09-03
Pal even worse problem got me...serious....every time I try to install something via terminal it says 

red33m@red33m-desktop:~$ sudo apt-get install amsn
E: Type 'sudo' is not known on line 1 in source list /etc/apt/sources.list.d/akirad.list
E: The list of sources could not be read.
red33m@red33m-desktop:~$ 

what the hell is wrong now?

---

### Post by Partyboi2 on 2009-09-03
You need to fix up line 1 of your sources.list, open a terminal and post the output to
```
 cat /etc/apt/sources.list
```

---

### Post by red33m on 2009-09-03
I just want to break the PC when nothing seems to work....again the same error thing my friend....

---

### Post by Partyboi2 on 2009-09-03
> **red33m said:**
> I just want to break the PC when nothing seems to work....again the same error thing my friend....
The command I gave (cat /etc/apt/sources.list) should not have given the same error, it should have  shown the contents of your sources.list, which I need to see to be able to help you fix it. :)

---

### Post by red33m on 2009-09-03
Oh right my noobness is tremendous, I know.... :)

It gave me this:

# deb cdrom:[Ubuntu 9.04 _Jaunty Jackalope_ - Release i386 (20090420.1)]/ jaunty main restricted
# See [http://help.ubuntu.com/community/UpgradeNotes](http://help.ubuntu.com/community/UpgradeNotes) for how to upgrade to
# newer versions of the distribution.

deb [http://gr.archive.ubuntu.com/ubuntu/](http://gr.archive.ubuntu.com/ubuntu/) jaunty main restricted
deb-src [http://gr.archive.ubuntu.com/ubuntu/](http://gr.archive.ubuntu.com/ubuntu/) jaunty main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb [http://gr.archive.ubuntu.com/ubuntu/](http://gr.archive.ubuntu.com/ubuntu/) jaunty-updates main restricted
deb-src [http://gr.archive.ubuntu.com/ubuntu/](http://gr.archive.ubuntu.com/ubuntu/) jaunty-updates main restricted

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team. Also, please note that software in universe WILL NOT receive any
## review or updates from the Ubuntu security team.
deb [http://gr.archive.ubuntu.com/ubuntu/](http://gr.archive.ubuntu.com/ubuntu/) jaunty universe
deb-src [http://gr.archive.ubuntu.com/ubuntu/](http://gr.archive.ubuntu.com/ubuntu/) jaunty universe
deb [http://gr.archive.ubuntu.com/ubuntu/](http://gr.archive.ubuntu.com/ubuntu/) jaunty-updates universe
deb-src [http://gr.archive.ubuntu.com/ubuntu/](http://gr.archive.ubuntu.com/ubuntu/) jaunty-updates universe

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
## team, and may not be under a free licence. Please satisfy yourself as to 
## your rights to use the software. Also, please note that software in 
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
deb [http://gr.archive.ubuntu.com/ubuntu/](http://gr.archive.ubuntu.com/ubuntu/) jaunty multiverse
deb-src [http://gr.archive.ubuntu.com/ubuntu/](http://gr.archive.ubuntu.com/ubuntu/) jaunty multiverse
deb [http://gr.archive.ubuntu.com/ubuntu/](http://gr.archive.ubuntu.com/ubuntu/) jaunty-updates multiverse
deb-src [http://gr.archive.ubuntu.com/ubuntu/](http://gr.archive.ubuntu.com/ubuntu/) jaunty-updates multiverse

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
# deb [http://gr.archive.ubuntu.com/ubuntu/](http://gr.archive.ubuntu.com/ubuntu/) jaunty-backports main restricted universe multiverse
# deb-src [http://gr.archive.ubuntu.com/ubuntu/](http://gr.archive.ubuntu.com/ubuntu/) jaunty-backports main restricted universe multiverse

## Uncomment the following two lines to add software from Canonical's
## 'partner' repository.
## This software is not part of Ubuntu, but is offered by Canonical and the
## respective vendors as a service to Ubuntu users.
# deb [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) jaunty partner
# deb-src [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) jaunty partner

deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) jaunty-security main restricted
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) jaunty-security main restricted
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) jaunty-security universe
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) jaunty-security universe
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) jaunty-security multiverse
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) jaunty-security multiverse
deb [http://ppa.launchpad.net/do-testers/ppa/ubuntu](http://ppa.launchpad.net/do-testers/ppa/ubuntu) intrepid main
deb-src [http://ppa.launchpad.net/do-testers/ppa/ubuntu](http://ppa.launchpad.net/do-testers/ppa/ubuntu) intrepid main
red33m@red33m-desktop:~$ cat/etc/apt/sources.list
bash: cat/etc/apt/sources.list: No such file or directory
red33m@red33m-desktop:~$ sudo gedit /etc/apt/sources.list
red33m@red33m-desktop:~$ sudo apt-get update
E: Type 'sudo' is not known on line 1 in source list /etc/apt/sources.list.d/akirad.list
red33m@red33m-desktop:~$ cat /etc/apt/sources.list
#deb cdrom:[Ubuntu 9.04 _Jaunty Jackalope_ - Release i386 (20090420.1)]/ jaunty main restricted
# See [http://help.ubuntu.com/community/UpgradeNotes](http://help.ubuntu.com/community/UpgradeNotes) for how to upgrade to
# newer versions of the distribution.

deb [http://gr.archive.ubuntu.com/ubuntu/](http://gr.archive.ubuntu.com/ubuntu/) jaunty main restricted
deb-src [http://gr.archive.ubuntu.com/ubuntu/](http://gr.archive.ubuntu.com/ubuntu/) jaunty main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb [http://gr.archive.ubuntu.com/ubuntu/](http://gr.archive.ubuntu.com/ubuntu/) jaunty-updates main restricted
deb-src [http://gr.archive.ubuntu.com/ubuntu/](http://gr.archive.ubuntu.com/ubuntu/) jaunty-updates main restricted

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team. Also, please note that software in universe WILL NOT receive any
## review or updates from the Ubuntu security team.
deb [http://gr.archive.ubuntu.com/ubuntu/](http://gr.archive.ubuntu.com/ubuntu/) jaunty universe
deb-src [http://gr.archive.ubuntu.com/ubuntu/](http://gr.archive.ubuntu.com/ubuntu/) jaunty universe
deb [http://gr.archive.ubuntu.com/ubuntu/](http://gr.archive.ubuntu.com/ubuntu/) jaunty-updates universe
deb-src [http://gr.archive.ubuntu.com/ubuntu/](http://gr.archive.ubuntu.com/ubuntu/) jaunty-updates universe

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
## team, and may not be under a free licence. Please satisfy yourself as to 
## your rights to use the software. Also, please note that software in 
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
deb [http://gr.archive.ubuntu.com/ubuntu/](http://gr.archive.ubuntu.com/ubuntu/) jaunty multiverse
deb-src [http://gr.archive.ubuntu.com/ubuntu/](http://gr.archive.ubuntu.com/ubuntu/) jaunty multiverse
deb [http://gr.archive.ubuntu.com/ubuntu/](http://gr.archive.ubuntu.com/ubuntu/) jaunty-updates multiverse
deb-src [http://gr.archive.ubuntu.com/ubuntu/](http://gr.archive.ubuntu.com/ubuntu/) jaunty-updates multiverse

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
# deb [http://gr.archive.ubuntu.com/ubuntu/](http://gr.archive.ubuntu.com/ubuntu/) jaunty-backports main restricted universe multiverse
# deb-src [http://gr.archive.ubuntu.com/ubuntu/](http://gr.archive.ubuntu.com/ubuntu/) jaunty-backports main restricted universe multiverse

## Uncomment the following two lines to add software from Canonical's
## 'partner' repository.
## This software is not part of Ubuntu, but is offered by Canonical and the
## respective vendors as a service to Ubuntu users.
# deb [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) jaunty partner
# deb-src [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) jaunty partner

deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) jaunty-security main restricted
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) jaunty-security main restricted
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) jaunty-security universe
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) jaunty-security universe
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) jaunty-security multiverse
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) jaunty-security multiverse
deb [http://ppa.launchpad.net/do-testers/ppa/ubuntu](http://ppa.launchpad.net/do-testers/ppa/ubuntu) intrepid main
deb-src [http://ppa.launchpad.net/do-testers/ppa/ubuntu](http://ppa.launchpad.net/do-testers/ppa/ubuntu) intrepid main

Dude by the time you can understand all these lines you really know about ubuntu...!

---

### Post by Partyboi2 on 2009-09-03
I gave the wrong command (its been a long day)  it was meant to be
```
cat  /etc/apt/sources.list.d/akirad.list
```

---

### Post by red33m on 2009-09-03
No problem by the time you are helping me on this one I really appreciate it..!

It gave me this:
red33m@red33m-desktop:~$ cat  /etc/apt/sources.list.d/akirad.list
sudo apt-key add - && sudo apt-get update
red33m@red33m-desktop:~$

---

### Post by Partyboi2 on 2009-09-03
Remove the file and start again, so[FONT=monospace]
[/FONT]```
[FONT=monospace]sudo rm /etc/apt/sources.list.d/akirad.list[/FONT]
```[FONT=monospace]
then add the repo with[/FONT]
```
echo deb http://akirad.cinelerra.org akirad-jaunty main | sudo tee /etc/apt/sources.list.d/akirad.list
```Then add the key for the repo
```
wget -q http://akirad.cinelerra.org/dists/akirad.key -O- | sudo apt-key add - && sudo apt-get update
```

---

### Post by red33m on 2009-09-03
I did the first one....OK till here..i added this to the repo, I saved it and then I opened a terminal and I added the whole last thing you wrote...but then it does nothing.....let me be more specific

echo deb [http://akirad.cinelerra.org](http://akirad.cinelerra.org) akirad-jaunty main | sudo tee /etc/apt/sources.list.d/akirad.list
I saved it and then I opened a terminal and I added the whole last thing you wrote...but then it does nothing.....let me be more specific:

red33m@red33m-desktop:~$ sudo rm /etc/apt/sources.list.d/akirad.list
[sudo] password for red33m: 
red33m@red33m-desktop:~$ sudo gedit /etc/apt/sources.list
red33m@red33m-desktop:~$ wget -q [http://akirad.cinelerra.org/dists/akirad.key](http://akirad.cinelerra.org/dists/akirad.key) -O- | sudo apt-key add - && sudo apt-get update

all the time the cursor flashes and when I try to close the terminal it says that If I do I will kill it...

what it it?

---

### Post by red33m on 2009-09-03
I am the happiest man in the world...! I did it with your help of course...!  I killed the terminal and then I opened a terminal I gave a simple command (sudo apt-get update) and it said tha a problem wah faced at line 56 so I opened the repo and I deleted the line saved it and it worked like a charm...First time I solved a problem with help( I wouldn't have managed without your help)  

Thanks and it is time to eat now lol!!!!!!

I am damn happy...appreciate the help again pal!!!

see ya in another thread..!

---

### Post by Partyboi2 on 2009-09-03
Adding the repo is done from the terminal and you do not need to use
'sudo gedit /etc/apt/sources.list' so in the terminal it is[FONT=monospace]
[/FONT]```
echo deb http://akirad.cinelerra.org akirad-jaunty main | sudo tee /etc/apt/sources.list.d/akirad.list

``` to add the repo.

Edit: did not see you last post, glad you got it working :)

---

### Post by red33m on 2009-09-04
Godd morning Party boy...

I just wanted to let you know that I followed your instructions and I managed to fix the broken packages..after that I logged in the server (akirad) again- it was overloaded when I was trying- and I downloaded a deb package installed it and then installed cinellerracv...and it works just fine...

Thanks man..!---I am marking the thread as solved---

---

### Post by Partyboi2 on 2009-09-04
Happy to have helped :)

---

