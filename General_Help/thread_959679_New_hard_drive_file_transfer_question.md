---
title: "New hard drive file transfer question"
date: 2008-10-26
forum: General Help
---

### Post by sdswingr on 2008-10-26
I am running a laptop with ubuntu, and have been successfully for about 18 months now..
My puny 20g hard drive is finally not enough space for me..so I am upgrading to somethign like a 200g, or whatever.
But I don't want to have to reinstall anthing, I would like to just make a direct mirror of my current hard drive on the new. What is the easiest way to do this? 
all the file transfer kits that I have seen are only win/mac compatible.
A friend of mine recommended GNU Parted. Does anyone have experience with this? [http://www.gnu.org/software/parted/index.shtml]("http://www.gnu.org/software/parted/index.shtml")

I am still a relative newbie...so please help thanks in advance.
-Tim

---

### Post by geirha on 2008-10-26
What means do you have to transfer files between the hard drives? Are you able to connect both hard drives to the laptop simultaneously?

---

### Post by dracayr on 2008-10-26
Well, actually you don't need a kit or program to copy files :). Just make sure the new (220GB) drive is formatted as ext3 or ext2 (you can use gparted to format), then use ```
cp -a source destination
``` at the command line to copy. the reason why you have to use the command line and cp -a instead of cp, is that cp -a preserves ownerships etc. (I don't know if the normal File browser does this)

dracayr

---

