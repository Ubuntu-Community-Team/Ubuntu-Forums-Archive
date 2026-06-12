---
title: "nvidia problem?"
date: 2012-11-04
forum: Hardware
---

### Post by unibroker on 2012-11-04
I just did a fresh install of 12.04 64bit checking both boxes, updates and 3rd party drivers, during the process.  I get the customary mouse freezes on initial boot up and some error having to do with ```
usr/bin/jockey
```.  In my research this morning they seem to be related to my nvidia graphics card ```
VGA compatible controller: NVIDIA Corporation GT218 [GeForce 210] (rev a2)

```.  I have read previously that there is an ongoing problem with nvidia.  Some have gone so far as to recommend going with another card.  Another thing, Displays under System Settings has my display as Goldstar 22" which it is not.  However the resolution is correct.

Just wanted to see what the brain trust here recommends before I proceed.

---

### Post by grahammechanical on 2012-11-04
By ticking install third party software you also installed the Nvidia proprietary driver. This is the default arrangement from 12.04 onwards. This means that the Displays utility is not effective. It works best with the Nouveau open source driver. You should have a Nvidia settings utility. See what that says about your set up.

Regards.

---

### Post by BicyclerBoy on 2012-11-04
LG is Goldstar as much as they would like to deny it!

---

### Post by unibroker on 2012-11-04
> **BicyclerBoy said:**
> LG is Goldstar as much as they would like to deny it!

You are correct BB!  LG was formed from a late 90's merger of two Korean companies; Lucky and Goldstar.  I do have a LG monitor.

---

### Post by unibroker on 2012-11-05
> **grahammechanical said:**
> By ticking install third party software you also installed the Nvidia proprietary driver. This is the default arrangement from 12.04 onwards. This means that the Displays utility is not effective. It works best with the Nouveau open source driver. You should have a Nvidia settings utility. See what that says about your set up.

Regards.

Interesting that the Nouveau driver is the one that I have activated on my system even after ticking the install 3rd party software.  I wonder if installing the "recommended" nvidia drivers will clear up my video issues.  FWIW, I reverted to version 29 (from version 32) of the kernel and had no kernel panics this morning.

---

### Post by BicyclerBoy on 2012-11-05
nVidia driver install has a dependency on the current kernel headers package..

Some people seem to have nvidia troubles lately with missing headers dependency or broken something..
You could try:
sudo apt-get install linux-headers-generic
- this package always points to the match headers for your kernel..

---

