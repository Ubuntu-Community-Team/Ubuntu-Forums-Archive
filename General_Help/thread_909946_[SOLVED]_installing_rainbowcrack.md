---
title: "[SOLVED] installing rainbowcrack"
date: 2008-09-04
forum: General Help
---

### Post by chex_m8 on 2008-09-04
will someone walk me through installing rainbowcrack, i already have the src file downloaded. i did the make -f makefile.linux command already. now what?

---

### Post by Rhubarb on 2008-09-04
Could you please post a link to the rainbowcrack site you're referring to?
As I haven't heard of the software myself.

Please post the link, as I'm curious about the software, and have experience with compiling ophcrack (which uses rainbow tables too) for ubuntu 8.04.

---

### Post by chex_m8 on 2008-09-05
[http://www.antsight.com/zsl/rainbowcrack/](http://www.antsight.com/zsl/rainbowcrack/)    this is where i downloaded it.

---

### Post by Crafty Kisses on 2008-09-05
> **chex_m8 said:**
> [http://www.antsight.com/zsl/rainbowcrack/](http://www.antsight.com/zsl/rainbowcrack/)    this is where i downloaded it.

Do you have build essentials installed?

---

### Post by Rhubarb on 2008-09-05
Ok, the good news is that it is easy to compile.
You may want to look at [ophcrack]("http://ophcrack.sourceforge.net/"), it's really easy to use, the live cd is even easier to use.


If you want to compile rainbowcrack youself, then read on:

You'll need a few packages first, grab:
```
sudo aptitude install build-essential openssl libssl-dev
```

Download rainbowcrack-1.2-src.zip, and un-zip it to your home folder.
(and unzip rainbowcrack-1.2-src-algorithmpatch.zip to ~/rainbowcrack-1.2-src/src if you want use of md5 and other hashing stuff).

Open up a terminal, and change to the ~/rainbowcrack-1.2-src/src directory:
```
cd ~/rainbowcrack-1.2-src/src
```

Now to compile it:
```
make -f makefile.linux
```

That generates a few files for you, the important ones you need are:
[I]charset.txt
list.txt
random_lm_alpha#1-7.hash
random_lm_alpha#1-7.plain
random_md5_loweralpha#1-7.hash
random_md5_loweralpha#1-7.plain
random_sha1_loweralpha#1-7.hash
random_sha1_loweralpha#1-7.plain
rcrack
rtdump
rtgen
rtsort[/I]

So if you like, copy those files to a new directory.
Then to use it, an example would be:
```
./rtgen lm alpha 1 7 0 2100 8000000 all
```

A good tutorial for it is [here]("http://www.antsight.com/zsl/rainbowcrack/rcracktutorial.htm").
This program worked for me for a simple 3 character xp password I created myself solely as a test for the program.


Again, if you're wanting to use this for windows passwords, use ophcrack, it's much easier to use.

---

### Post by Crafty Kisses on 2008-09-05
> **Rhubarb said:**
> Ok, the good news is that it is easy to compile.
You may want to look at [ophcrack]("http://ophcrack.sourceforge.net/"), it's really easy to use, the live cd is even easier to use.


If you want to compile rainbowcrack youself, then read on:

You'll need a few packages first, grab:
```
sudo aptitude install build-essential openssl libssl-dev
```

Download rainbowcrack-1.2-src.zip, and un-zip it to your home folder.
(and unzip rainbowcrack-1.2-src-algorithmpatch.zip to ~/rainbowcrack-1.2-src/src if you want use of md5 and other hashing stuff).

Open up a terminal, and change to the ~/rainbowcrack-1.2-src/src directory:
```
cd ~/rainbowcrack-1.2-src/src
```

Now to compile it:
```
make -f makefile.linux
```

That generates a few files for you, the important ones you need are:
[I]charset.txt
list.txt
random_lm_alpha#1-7.hash
random_lm_alpha#1-7.plain
random_md5_loweralpha#1-7.hash
random_md5_loweralpha#1-7.plain
random_sha1_loweralpha#1-7.hash
random_sha1_loweralpha#1-7.plain
rcrack
rtdump
rtgen
rtsort[/I]

So if you like, copy those files to a new directory.
Then to use it, an example would be:
```
./rtgen lm alpha 1 7 0 2100 8000000 all
```

A good tutorial for it is [here]("http://www.antsight.com/zsl/rainbowcrack/rcracktutorial.htm").
This program worked for me for a simple 3 character xp password I created myself solely as a test for the program.


Again, if you're wanting to use this for windows passwords, use ophcrack, it's much easier to use.
Nicely written, follow that tutorial, and try to re-build and you should be successful.

---

### Post by slipdipper on 2008-11-30
Updated installation howto:

[http://ubuntuforums.org/showthread.php?p=6279688](http://ubuntuforums.org/showthread.php?p=6279688)

---

