---
title: "ubuntu 18.04 strange boot issue"
date: 2019-05-16
forum: Hardware
---

### Post by jb8ker on 2019-05-16
Okay, so I'm so lost as to what happened to my OS. Came home today, turned on my PC and I am greeted with a "lubuntu" boot screen not the usual Ubuntu boot screen. Then it just stays on that lubuntu loading page. I can press ctrl+alt+F1, or F2, ...etc, and get to the Ubuntu command line login, and login, but that's as close as I can get to my Ubuntu OS just the black command line interface. Do note that I have never downloaded or installed lubuntu on my PC and everything was running completely normal last night when I shut it down before bed. I've been running Ubuntu for a little over a year now, so I'm new to the OS but not a total beginner. Any suggestions/ideas/thoughts on what could have happened or how to correct this issue?

---

### Post by Rubi1200 on 2019-05-17
Hi and welcome to the forums :-)

Is Ubuntu the only operating system on the computer? Do see the GRUB menu when booting?

I would try and get to the GRUB menu by pressing Shift as the computer starts then choose advanced options.

First try dpkg to repair any broken packages.

If that does not help then start again and try fsck which will attempt to fix any file system errors.

Report back here if anything helped.

If not, we will try more steps.

Thanks.

---

