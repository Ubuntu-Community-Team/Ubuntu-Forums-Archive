---
title: "MP3 encoding lame help please!"
date: 2005-12-06
forum: General Help
---

### Post by bananaman on 2005-12-06
Okey... It's been three hours and Im very tired and frustrated but I refuse to go to bed if it doesnt work...

I cant encode mp3s!

Im trying to use grip...but apparently lame isnt installed...
So I searched for answers and went for the obvious:
sudo apt-get install lame
and
sudo apt-get install gstreamer8.0-lame

they dont work! it says the packages dont exist... i have all the repositories i know that... and i really dont want to get into compiling lame (im still a noob and have had horrible experiences with compiling)...

so the question is: what the hell is going on? please help me! or if you are an experiencied ubuntu breezy user then please give me instructions to compile and install lame... 

please! someone! anyone!...thanks in advance...

---

### Post by Liam on 2005-12-06
Have you got **multiverse** enabled, in addition to universe? That's where it's at.

---

### Post by bananaman on 2005-12-06
um...i dont know... i believe i enabled all of them...heres my sources.list

is it?

------------------------------------------------------------------------------------------------
deb cdrom:[Ubuntu 5.10 _Breezy Badger_ - Release i386 (20051012)]/ breezy main restricted


deb [http://mx.archive.ubuntu.com/ubuntu](http://mx.archive.ubuntu.com/ubuntu) breezy main restricted
deb-src [http://mx.archive.ubuntu.com/ubuntu](http://mx.archive.ubuntu.com/ubuntu) breezy main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb [http://mx.archive.ubuntu.com/ubuntu](http://mx.archive.ubuntu.com/ubuntu) breezy-updates main restricted
deb-src [http://mx.archive.ubuntu.com/ubuntu](http://mx.archive.ubuntu.com/ubuntu) breezy-updates main restricted

## Uncomment the following two lines to add software from the 'universe'
## repository.
## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
 deb [http://mx.archive.ubuntu.com/ubuntu](http://mx.archive.ubuntu.com/ubuntu) breezy universe
 deb-src [http://mx.archive.ubuntu.com/ubuntu](http://mx.archive.ubuntu.com/ubuntu) breezy universe

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
 deb [http://mx.archive.ubuntu.com/ubuntu](http://mx.archive.ubuntu.com/ubuntu) breezy-backports main restricted universe multiverse
 deb-src [http://mx.archive.ubuntu.com/ubuntu](http://mx.archive.ubuntu.com/ubuntu) breezy-backports main restricted universe multiverse

deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) breezy-security main restricted
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) breezy-security main restricted

 deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) breezy-security universe
 deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) breezy-security universe
-----------------------------------------------------------------------------------------------

---

### Post by daller on 2005-12-06
Change these lines:

```

deb http://dk.archive.ubuntu.com/ubuntu breezy universe
deb-src http://dk.archive.ubuntu.com/ubuntu breezy universe

```

into: (append multiverse at the end!)

```

deb http://dk.archive.ubuntu.com/ubuntu breezy universe multiverse
deb-src http://dk.archive.ubuntu.com/ubuntu breezy universe multiverse

```

And run:

```

sudo apt-get update

```

then:

```

apt-get install gstreamer0.8-lame

```

---

### Post by bananaman on 2005-12-06
IT WORKS...

I got confused with the mx/dk things...i got it right now...
sorry for the confusion, thank you very much may tux bless you :)
thanks again!

---

### Post by Liam on 2005-12-06
Can you do just the basic lame package?

$ sudo apt-get install lame

You shouldn't need the gstreamer plugin if you're using Grip.

---

### Post by kosmic on 2005-12-06
YEs you need to activate multiverse in the breezy repositories, you only have multiverse in the backports
 
 
Ups, take to long to asnwer, sorry

---

