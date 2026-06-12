---
title: "Amarok install woes"
date: 2005-11-14
forum: General Help
---

### Post by robenroute on 2005-11-14
Hi there, I'm trying to install amarok through apt-get (synaptic) but there are 2 files that can't be found/downloaded. I've been trying for a few days now, but it's just not working. The files in question are:
- netpbm
- libarts1c2

Universe and multiverse (and all the other selectable repositories) are all checked. Am I missing something?

Thanks in advance,

Rob

---

### Post by kperkins on 2005-11-14
They _are_ in the Breezy repositories.  I don't know why you can't find them.

---

### Post by aaron_ on 2005-11-14
hi.. 

you need:

amarok
amarok-engines

to modify the amarok face you need:

qt3-qtconfig

bye
aaron

---

### Post by robenroute on 2005-11-14
[QUOTE=aaron_]hi.. 

you need:

amarok
amarok-engines

to modify the amarok face you need:

qt3-qtconfig

bye
aaron[/QUOTE]


Well, those are exactly the packages I selected. Synaptic told me it also wanted to install a few more packages (16 in total) and when I gave the go-ahead, it all went tits up because it couldn't find the 2 packages mentioned in my first post. I know, these packages SHOULD be there, but why can 14 packages be found and downloaded, but just those 2 can't? I just beats me... I'm rather puzzled.

Any ideas on how to proceed? Are these packages downloadable from some other place?

Thanks a lot. Rob

---

### Post by Pablo_Escobar on 2005-11-14
Can You post Your /etc/apt/sources.list here ?
Maybe there is something wrong in Your repo list.
We'll have more insight when You post it.

---

### Post by robenroute on 2005-11-14
[QUOTE=Pablo_Escobar]Can You post Your /etc/apt/sources.list here ?
Maybe there is something wrong in Your repo list.
We'll have more insight when You post it.[/QUOTE]

Okay:

#deb cdrom:[Ubuntu 5.10 _Breezy Badger_ - Preview i386 (20050923)]/ breezy main restricted


## Uncomment the following two lines to fetch updated software from the network
deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) breezy main restricted
deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) breezy main restricted

## Uncomment the following two lines to fetch major bug fix updates produced
## after the final release of the distribution.
deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) breezy-updates main restricted
deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) breezy-updates main restricted

## Uncomment the following two lines to add software from the 'universe'
## repository.
## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) breezy universe
deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) breezy universe

deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) breezy-security main restricted
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) breezy-security main restricted

deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) breezy-security universe
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) breezy-security universe

deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) breezy multiverse
deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) breezy multiverse

deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) breezy-backports main restricted universe multiverse

----

Hope this helps. Thanks again.

---

### Post by Pablo_Escobar on 2005-11-14
Heck it seems You've install You Breezy from preview CD. It shouldn't be a problem. I have amarok work great and Your sources list looks good. 
I hve no idea what can be a problem :(

---

### Post by robenroute on 2005-11-14
Hell, I also have no clue as to what is going on. Synaptic gave me the following error message:

-----
W: Failed to fetch [http://archive.ubuntu.com/ubuntu/pool/main/a/arts/libarts1c2_1.4.3-0ubuntu1_i386.deb](http://archive.ubuntu.com/ubuntu/pool/main/a/arts/libarts1c2_1.4.3-0ubuntu1_i386.deb)
  Bad header line [IP: 82.211.81.182 80]


W: Failed to fetch [http://security.ubuntu.com/ubuntu/pool/main/n/netpbm-free/netpbm_10.0-8ubuntu1.1_i386.deb](http://security.ubuntu.com/ubuntu/pool/main/n/netpbm-free/netpbm_10.0-8ubuntu1.1_i386.deb)
  Bad header line
-----

Now, I don't really understand what the bad header line thing means. Anyone?

Thanks,
Rob

---

### Post by robenroute on 2005-11-28
Okay, the netpbm package is found and downloaded. However, the libarts1c2 file still can't be found. Weird....

Well, so much for the weirdness or inexplicability of things, how about a tip for getting things (amaroK!) to work. I've been using Beep Media Player so far, but amaroK is still my favourite (i.e. on linux; the -in my opinion- only music player worthy of my mouse clicks is foobar2000.) I'm digressing, amarok is very usable and I would just like to have it on my Ubuntu Box.

Anyone?

---

