---
title: "Wont Install anything"
date: 2009-03-24
forum: Installation &amp; Upgrades
---

### Post by webbut on 2009-03-24
I just installed an old Ubuntu disk i had on my computer(7.04) and im connected to the internet but i can go to the add/remove software thing to get updates and install new things. when i get to the "Downloading package information". It says at 1% and then a pop up says it couldnt download and it lists all the files. I try again and look at the download information and it just skips each thing without downloading a single kb

---

### Post by mhgsys on 2009-03-24
open up a terminal . 

typ 

```

sudo dpkg --configure -a

```

after that try to update with 
```

sudo apt-get update

```

then try again

edit<;do they actually still support it??

---

### Post by stchman on 2009-03-24
> **webbut said:**
> I just installed an old Ubuntu disk i had on my computer(7.04) and im connected to the internet but i can go to the add/remove software thing to get updates and install new things. when i get to the "Downloading package information". It says at 1% and then a pop up says it couldnt download and it lists all the files. I try again and look at the download information and it just skips each thing without downloading a single kb

That is because the Feisty Fawn repositories are now closed.  You will need to use Dapper(6.06 LTS) Gutsy(7.10), Hardy(8.04 LTS), or Intrepid(8.10).

---

