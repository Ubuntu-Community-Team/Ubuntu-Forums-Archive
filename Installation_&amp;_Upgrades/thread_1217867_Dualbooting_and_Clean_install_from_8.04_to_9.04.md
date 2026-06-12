---
title: "Dualbooting and Clean install from 8.04 to 9.04"
date: 2009-07-20
forum: Installation &amp; Upgrades
---

### Post by scotcella on 2009-07-20
Hi All,

I'm a little stuck with a few things, so here I am asking for advice.

Background:
Currently I have Windows Vista and Ubuntu 8.04 installed on my laptop. I would like to do a clean install from 8.04 to 9.04.

What I have checked out so far, (googled, forum searches etc), most of the posts don't show what the poster actually did to resolve their issues.

As far as I understand, when I get to the partitioning bit of the installer, I need to select the manual partitiong.  I can identify the Windows partioning 

```
/dev/sda2 NTFS
```

and I can see the ubuntu partions, which are:

```
/dev/sda3 Extended
/dev/sda5 ext3
/dev/sda6 Linux-swap
```

Question: Which partition am I supposed to select to do a clean install of 9.04?

Many thanks in advance

---

### Post by .nedberg on 2009-07-20
Sda5. Use sda6 as swap

---

### Post by presence1960 on 2009-07-20
**don't forget the most important thing you can do prior to any partitioning/install procedure: BACK UP ALL data!**

---

