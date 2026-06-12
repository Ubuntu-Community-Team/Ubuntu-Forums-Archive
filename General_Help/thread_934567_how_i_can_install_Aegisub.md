---
title: "how i can install Aegisub"
date: 2008-09-30
forum: General Help
---

### Post by THE BLUE DRAGON on 2008-09-30
hi guys 
i need help how i can install Aegisub on ubuntu ??:(:(

plz help

---

### Post by THE BLUE DRAGON on 2008-09-30
i try download deb file 
root@dhruae4host:/home/dragon# apt-get install aegisub_2.1-dev-r2207_i386
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Couldn't find package aegisub_2.1-dev-r2207_i386

the file in /home/dragon
but how i can install it correct plz help

---

### Post by THE BLUE DRAGON on 2008-09-30
i try download deb file 
root@dhruae4host:/home/dragon# apt-get install aegisub_2.1-dev-r2207_i386
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Couldn't find package aegisub_2.1-dev-r2207_i386

the file in /home/dragon
but how i can install it correct plz help

---

### Post by cyberdork33 on 2008-09-30
It is not in the Ubuntu Software Repositories.
According to the website, you can get deb files here:
[http://lulzicon.com/?page_id=10](http://lulzicon.com/?page_id=10)

---

### Post by jpeddicord on 2008-09-30
Moved to General Help.

---

### Post by x6ronn9x on 2008-09-30
Do a little search on any searching site engine and go to a downloading website.

---

### Post by THE BLUE DRAGON on 2008-10-01
thanks now i can use it

---

### Post by unf4b1x on 2008-12-12
hey I have followed one of the instructions on how to install aegisub, but when I reloaded synaptic package, the package cannot be found!!! you said it worked fine with you.. May I know did you do it? I also want to install aegisub, although, I got wine, I wanted to install using the linux side.

---

### Post by shirilover on 2008-12-12
> **THE BLUE DRAGON said:**
> i try download deb file 
root@dhruae4host:/home/dragon# apt-get install aegisub_2.1-dev-r2207_i386
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Couldn't find package aegisub_2.1-dev-r2207_i386

the file in /home/dragon
but how i can install it correct plz help

You should probably try
```

sudo dpkg -i aegisub_2.1-dev-r2207_i386.deb

```

---

### Post by majormar on 2009-09-04
In case anyone stubles across this and is looking for newly maintained packages for Aegisub you can find them here ...

[http://www.teufansub.uni.cc/aegiubuntu/](http://www.teufansub.uni.cc/aegiubuntu/)

---

### Post by Poytu on 2009-12-23
**majormar**many many thanks
making aegisub with my own hands drive me crazy

---

### Post by nivosh on 2010-01-18
Can't install the deb...

The installer ends with error...

Any help?

---

### Post by Found on 2010-03-23
> **nivosh said:**
> Can't install the deb...

The installer ends with error...

Any help?

What's the error? I'm compiling mine from [http://www.aegisub.org/](http://www.aegisub.org/)
Goes well so far. The only thing I installed was wxWidgets from repos.

---

