---
title: "Adept file manager problem"
date: 2005-11-18
forum: General Help
---

### Post by phil66 on 2005-11-18
Installation :
Kubuntu Breezy 5.1.0
KDE 3.4

Started install of Libmagick++6-dev I left the computer during the install when I returned a file was running in the preconfigure screen.
The file was scrolling and would pause for a few seconds.
It was asking for a number coresponding to a greophical area. I am unable to input a number or to move the cursor to any location. The file will auto start scrolling and pausing on its own for how ever amount of time you allow it to do so.
In the preview changes area the file Libc6-I686 (Gnu c Library) exist with the status Broken ( upgradable) Action Break ( keep)
Removed libc6 this did not effect preconfigure file it continues to scroll

Cannot install or upgrade any other files as the script continues to scroll until a command to kill or another command is given.

Adept manager has error message commit is not complete because of broken file.

Tried recovery mode but no sucess

How do I get rid of this file that is not completing the preconfigure process.

Thanks
Ray

---

### Post by mlomker on 2005-11-18
lib6c is a critical package that almost everything on the system depends upon.  Have you installed any DEB packages outside of Adept?  I usually only see that problem if someone tries to install DEBS that weren't designed for Ubuntu.

Perhaps you could to an **sudo apt-get update** and **sudo apt-get -f upgrade** at a terminal prompt and post the results.

---

### Post by phil66 on 2005-11-18
Miomker

Sudo apt-get update worked and corrected problem.

It downloaded 13000 +- files then suggest I run

dpkg -- configure -a  this brought up the problem program and alow me to put the needed entries

Libc6 now shows to be install in adept file manager

I was able to upgrade a file using adept

Before using apt-get update dpkg --configure -a would not run

Thanks for the help

Have a good Thanksgiving
Ray

---

