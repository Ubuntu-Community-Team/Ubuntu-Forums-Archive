---
title: "problem with code blocks"
date: 2009-04-07
forum: Installation &amp; Upgrades
---

### Post by ubun_tut on 2009-04-07
hi,

i downloaded code::blocks and installed it using 

sudo apt-get install build-essential gdb libwxgtk2.6-0 libwxgtk2.6-dev wx2.6-headers wx-common

as stated on [http://wiki.codeblocks.org/index.php?title=Installing_Code::Blocks_nightly_build_on_Ubuntu](http://wiki.codeblocks.org/index.php?title=Installing_Code::Blocks_nightly_build_on_Ubuntu). then i get the following message


Reading package lists... Done
Building dependency tree       
Reading state information... Done
build-essential is already the newest version.
gdb is already the newest version.
libwxgtk2.6-0 is already the newest version.
libwxgtk2.6-dev is already the newest version.
wx2.6-headers is already the newest version.
wx-common is already the newest version.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.

which probably means the installation is successful (i think i may have installed it before, hence the message). but how do i run code::blocks? i cant seem to find any new additions to the 'applications' bar. or must i initiate it from the command line?

thx

---

### Post by Doopydoo22 on 2009-04-07
Code::Blocks isn't in that list of packages you gave to apt-get.

From the looks of things, you were hoping to build it from source.  That shouldn't be necessary unless their nightly build is what you absolutely want.

Ubuntu has Code::Blocks in their universe repositories, just run:

```
sudo apt-get install codeblocks
```

That should do it for ya.  It should pop up under Applications > Programming.

---

### Post by ubun_tut on 2009-04-07
i tried what you suggested, but i get the following message

Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Couldn't find package codeblocks

I have checked to make sure that the universe repository is checked under software sources...what seems to be the problem?

---

### Post by ubun_tut on 2009-04-08
hi, anymore suggestions on how to install code::blocks on ubuntu?

---

