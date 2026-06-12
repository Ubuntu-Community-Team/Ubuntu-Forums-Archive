---
title: "Sun Virtual Box display problem, after upgrade to 9.04"
date: 2009-04-26
forum: Installation &amp; Upgrades
---

### Post by vewert on 2009-04-26
After upgrading from Ubuntu 8.10 to 9.04 the display on the Sun Virtual Box management screen has gone all wonky... all the text is blurred out. (See screen shot).  Note: only the text seems affected, images are fine.

I tried upgrading to latest version of Sun Virtual Box (2.2.0), but no luck.  I have also tried change application fonts, screen resolution, visual effects, but nothing seems to help.  I have a feeling it may be graphics card/driver related, but so far that is the only application that show this problem.

I'm relatively new to Linux, and would appreciate any help.

Thanks.

Screen Shot:

[IMG]http://www.ewert-technologies.ca/assets/misc/images/Screenshot-Sun_VirtualBox-1.png[/IMG]

---

### Post by vewert on 2009-04-26
I have solved the problem (sort of).  I had been using the Nimbus theme.  I tried switching to a different theme and then problem went away.  The strange thing is, is that I switched back to Nimbus theme, and now Virtual Box still works fine.  Not sure what's going on here, but at least it working for me now.

---

### Post by vewert on 2009-05-08
Hmmm, so now the VirualBox GUI is working for me, but whenever I try to run a Guest, the display of the guest machine goes funny... it kind of has a transparent/faded look.  Is anyone else having any similar problems?

----------------------
Victor Ewert
[http://www.ewert-technologies.ca]("http://www.ewert-technologies.ca/")

---

### Post by vewert on 2009-08-17
In case anyone is interested, it looks like this problem has been resolved in Sun VirtualBox 3.0.4:

From 3.0.4 ChangeLog:

Linux hosts: fixed problems leading to wrong colors or transparency in host windows with some graphics drivers (bug [#3095]("http://www.virtualbox.org/ticket/3095"))

---

