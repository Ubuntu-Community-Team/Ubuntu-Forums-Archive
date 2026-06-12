---
title: "[SOLVED] Programs are outdated on aptitude"
date: 2008-08-26
forum: General Help
---

### Post by Firehalk on 2008-08-26
I'm currently kind of newbie when it's about Linux, so please, can anyone say to me how often the **aptitude** lists are updated?

I'm asking that because pidgin is already on the 2.5 version, and through aptitude it shows always only 2.4.1. 

When i type:

```
sudo aptitude install pidgin
```

It doesn't get anything too. It says 0kb downloaded, which means it thinks the current version is 2.4.1, right?

I tried to get Pidgin 2.5 tar.gz2 from Pidgin's website, but for me it's a nightmare to compile anything under Linux. 

It just never works. When I finally find some library that was missing, and I run** ./configure** again, then it shows another thing that is missing... And so it goes forever.

Well, my point with this post, is ask any suggestion of how to keep softwares up-to-date when it's about Ubuntu/Linux.

I tried many things already, some people even said to me that I just need to update the lists and do everything through terminal... But the fact is, that shows outdated too, whe running **sudo aptitude update**

If it's not possible other way then compiling the newer versions, then please any tips about compiling would be useful. 

I already did read the official docs btw: [https://help.ubuntu.com/community/CompilingEasyHowTo](https://help.ubuntu.com/community/CompilingEasyHowTo)

Thanks.

---

### Post by gaussian on 2008-08-26
One thing which often works really well is when you are trying to compile a newer version of something that exists within Ubuntu is to do (example emacs):

```

sudo apt-get build-dep emacs

```

This installs all the required libraries to compile the version in Ubuntu. If you are lucky, the new version will compile with the same versions of libraries. If the new version needs newer libraries things can start looking messy really soon.

---

### Post by phidia on 2008-08-26
Compiling can be a nightmare that's why apt and derivatives exist. Does the pidgin site have links to any .deb packages? Sometimes someone will create a .deb package based on a more up-to-date release. Also if the latest release is available as an rpm you could use alien (search that) to convert to a deb and install that.
A package manager is a trade off you get a fairly stable system and programs to install, but not necessarily the latest version of everything out there.

---

### Post by oldos2er on 2008-08-26
Usually, except for security updates, programs in Ubuntu's repositories are updated once every six months to coincide with OS releases. As you've seen, if you want to update to the latest versions you have to do it yourself, compiling, etc.

 "[B]sudo aptitude update" only updates the list of programs available from the repos.

 Dealing with compiling source code, you should read README and INSTALL files included with the source. These usually explain any needed dependencies.

[/B]

---

### Post by tuxxy on 2008-08-26
You dont need to compile it from source, the package in the repos is outdated I beleive, as it hasnt been updated to the correct version yet you will have to download the .deb package here

[http://www.getdeb.net/app/Pidgin](http://www.getdeb.net/app/Pidgin)

Once downloaded right click and select install :)

---

### Post by Hells_Dark on 2008-08-26
And there are also some ppa or others repositories.

---

### Post by AusIV4 on 2008-08-26
I generally recommend against installing versions out of sync with what's in the repositories. They may not have the absolute latest features, but progrmas from the repositories are generally well tested and reliable, and get automatic security updates.

If you have to have the latest version, I'd recommend looking at [getdeb.net]("http://www.getdeb.net/") to see if anyone has built a package yet.

---

### Post by Joeb454 on 2008-08-26
The repositories aren't updated that often. It's possible that Ubuntu 8.10 will include pidgin 2.5.

Some programs also receive updates through the -backports repository, so you may want to enable that.

Alternatively, you could compile your favourite programs from source, which would then allow you to update it as and when you want :)

---

### Post by aysiu on 2008-08-26
The software is updated every six months with a new Ubuntu release.

---

### Post by Firehalk on 2008-08-26
**tuxxy**, what a nice link! :D

Lots of cool apps there, all as deb! Damn, too perfect.

I installed through there, and it works.

Much better.

Thanks a lot folks.

---

