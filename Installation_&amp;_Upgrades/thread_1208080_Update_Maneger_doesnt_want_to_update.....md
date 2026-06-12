---
title: "Update Maneger doesnt want to update...."
date: 2009-07-08
forum: Installation &amp; Upgrades
---

### Post by kibster on 2009-07-08
this is the error I receive. 

Failed to fetch cdrom://Ubuntu 8.10 _Intrepid Ibex_ - Release i386 (20081030)/dists/intrepid/main/binary-i386/Packages  Please use apt-cdrom to make this CD-ROM recognized by APT. apt-get update cannot be used to add new CD-ROMs
Failed to fetch cdrom://Ubuntu 8.10 _Intrepid Ibex_ - Release i386 (20081030)/dists/intrepid/restricted/binary-i386/Packages  Please use apt-cdrom to make this CD-ROM recognized by APT. apt-get update cannot be used to add new CD-ROMs
Some index files failed to download, they have been ignored, or old ones used instead.

What does it need ...What a noob i am  .

---

### Post by earthpigg on 2009-07-08
your computer is trying to pull the updates from an ubuntu cd, not from the ubuntu software repository servers.


system -> administration -> software sources

'download from:' dropdown -> 'other' -> select best server

work?

:D

---

### Post by hansdown on 2009-07-08
Hi kibster.

Click system> administration> software sources> ubuntu software.

Enter password.

Make sure the first four boxes are checked.

Make sure the "install from CD-ROM/DVD" box is unchecked.

If you want the medibuntu repository, click third party software and
check the medibuntu box.

Also as earthpigg said, you can choose where to download from. Mine is set for the server from Canada. Choose which works best for you.

---

### Post by kibster on 2009-07-08
Well I tried and the same thing happened...Says the repository is out of date/

---

### Post by Soul-Sing on 2009-07-09
Then post your sources.list here.

---

### Post by kibster on 2009-07-09
God I feel like an idot...  I cant copy the list. it won't let me

---

### Post by kibster on 2009-07-09
earthpigg said

your computer is trying to pull the updates from an ubuntu cd, not from the ubuntu software repository servers.


Yes... It won't let me change the location...

---

### Post by earthpigg on 2009-07-09
please post the output of:

```
cat /etc/apt/sources.list
```

---

### Post by kibster on 2009-08-23
I guesss I'm a little slow


# deb cdrom:[Ubuntu-Server 8.04 _Hardy Heron_ - Alpha i386 (20080225)]/ hardy restricted main
deb [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) hardy partner
deb-src [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) hardy partner
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) hardy-security restricted main multiverse universe
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) hardy-security restricted main multiverse universe
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) hardy restricted main multiverse universe
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) hardy restricted main multiverse universe
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) hardy-backports main restricted universe multiverse
# deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) hardy-backports main restricted universe multiverse
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) hardy-updates restricted main multiverse universe
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) hardy-updates restricted main multiverse universe
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) jaunty-security multiverse

---

### Post by Partyboi2 on 2009-08-23
> **kibster said:**
> Well I tried and the same thing happened...Says the repository is out of date/
From the terminal you can update the package list with
```
sudo apt-get update
```
But before that you need to remove the Jaunty repo from your sources.list as this will cause breakages. To do this in a terminal type or paste
```
gksu gedit /etc/apt/sources.list
```
Then when gedit has opened look for this line and remove it
```
 deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) jaunty-security multiverse 	
```
Then save the changes and close gedit and back in the terminal
```
sudo apt-get update
```

---

### Post by kibster on 2009-08-23
Thanks a lot....that will fix it... New to linux. Didnt know how to write the command line stuff...  Which takes a bit of getting use to it.

---

### Post by Windy Peaks on 2009-11-08
Just Used your info and it worked prefectly.

Thanks

Windy





> **earthpigg said:**
> your computer is trying to pull the updates from an ubuntu cd, not from the ubuntu software repository servers.


system -> administration -> software sources

'download from:' dropdown -> 'other' -> select best server

work?

:D

****

---

