---
title: "GPG Error when I'm updating"
date: 2009-01-14
forum: Installation &amp; Upgrades
---

### Post by ElCrackdel83 on 2009-01-14
Hi!

A week ago I found a problem updating my Intrepid Ibex. As I oftenly do, I executed %>sudo aptitude update in a terminal. After several lines, at the end the output is the one showed in the following paragraph:

Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) intrepid-security/restricted Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) intrepid-security/universe Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) intrepid-security/multiverse Packages
Fetched 366kB in 4s (89.9kB/s)                         
Reading package lists... Done
W: GPG error: [http://archive.ubuntu.com](http://archive.ubuntu.com) intrepid Release: The following signatures were invalid: BADSIG 40976EAF437D05B5 Ubuntu Archive Automatic Signing Key <ftpmaster@ubuntu.com>
W: You may want to run apt-get update to correct these problems

I've tried so many things, and I don't know what to do to fix it. Please, if some one has a clue, I'd appreciate it a lot. I have no idea what's wrong with my Ubuntu. 

Thank u very much in advance.

Regards.

---

### Post by Pumalite on 2009-01-14
```
sudo apt-get update
```

---

### Post by ElCrackdel83 on 2009-01-14
> **Pumalite said:**
> ```
sudo apt-get update
```

Thanks for your answer.

That's the first thing I tried, and the result is exactly the same one that I get after executing sudo aptitude update.

---

