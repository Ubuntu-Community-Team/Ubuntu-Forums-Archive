---
title: "How can i test or simulate a package installation?"
date: 2009-07-09
forum: Installation &amp; Upgrades
---

### Post by malarie on 2009-07-09
Good day,

I have Hardy LTS installed with subversion 1.4.6.  I would like to use subversion 1.5.2 but i am not sure how to verify all the dependencies..

I have downloaded the  subversion_1.5.4dfsg1-1ubuntu2_i386.deb package, but when i try to:

root@malarie-laptop:~# dpkg -i --dry-run subversion_1.5.4dfsg1-1ubuntu2_i386.deb

i have the following output that does not help me much:

(Reading database ... 245205 files and directories currently installed.)
Preparing to replace subversion 1.5.4dfsg1-1ubuntu2 (using subversion_1.5.4dfsg1-1ubuntu2_i386.deb) ...


I just want to install a new version of subversion on hardy LTS without having to upgrade my disrto to jaunty..

I want to test and verify all dependencies before installing it..

Anybody have a clue?

thanks.

---

### Post by MScapee on 2009-07-09
Disclaimer: Having just recently escaped from M$ prison, I'm an ultra noob so take anything I suggest with a grain of salt (a cup of salt might be better...).  

I'm not sure if this even amounts to much of a clue but assuming that you can boot under a live CD version of Hardy, perhaps you can test your install of subversion under the live CD?  Just a thought...  Good luck!

---

### Post by malarie on 2009-07-09
Thanks for your reply.   It pointed me into a good direction.. I will simply create a jaunty vm anc test it there :)

---

