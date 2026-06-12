---
title: "Cloning my current ubuntu installation."
date: 2009-07-19
forum: Installation &amp; Upgrades
---

### Post by CynicalPsycho on 2009-07-19
So how would I go about cloning my current installation of ubuntu? like... have an exact clone of my current setup on another hard drive?

currently my computer is partitioned into:
/:15 GB
/home/:273 GB
/boot/:91.1 MB
Swap: 8 GB (i know... I never use that much but yeah anyway)

I was thinking about using clonezilla, but I know very little about it. Is it doable? does anyone have any have any prior experience or knowledge they could send my way?

---

### Post by cariboo on 2009-07-19
There are several tools you can use to clone your hard drive:

[list]
[*] dd - installed by default, type man dd for info.
[*] partimage - it is in the repositories.
[*] [remastersys]("http://www.geekconnection.org/remastersys/remastersystool.html") - I just been playing with this, it allows you to create a custom disttribution or backup up your current version.
[*] clonezilla - I haven't tried this yet.
[*] rsync - installed by default man rsync for more.
[/list]

---

### Post by ruehara on 2009-07-19
I've been using rsync to backup my entire installation onto an eSata drive each day.

Recently I allowed the Update Manager to install some bug & security fixes which resulted in my PC (Dell XPS 430 & Jaunty) to become unstable and Skype to inherit a 5 - 6 second delay.

I tried to restore my system by copying the entire rsync tree from the eSata drive which rendered my PC totally useless - wouldn't boot up at all.

The only way I could get back into operation was to make a clean installation from the live CD and then try to remember everything I had set up in the system.

Any suggestion as to where I went wrong?

---

### Post by stlsaint on 2009-07-19
just a thought but cloning a partition that has more than one internal partition may take a lil more than what you are used to like when you used windows. look for something like a sys backup in the reposit.
there are many tools there and most will complete the backup the way you are used to doin and when you try and restore ensure that you have formatted your partition completely so as to not conflict!

---

