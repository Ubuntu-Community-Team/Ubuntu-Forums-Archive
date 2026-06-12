---
title: "Concerned About HD Space"
date: 2009-07-16
forum: Installation &amp; Upgrades
---

### Post by mju4t on 2009-07-16
Hello

I recently installed Ubuntu and I am concerned I did not allocate enough space for my / partition.  I gave 13 GB to /, and 46 GB to /home and 3 GB to swap.  Can I install programs in my /home directory?  What about when I download packages? All this partitioning makes my head spin!

Alex

---

### Post by drs305 on 2009-07-16
13GB is normally sufficient, especially with a separate /home, but of course it depends on the user. For now, I would continue to allow apps to install in the default locations until your / partition starts getting near full. 

Packages (.debs) are downloaded and stored in /var/cache/apt/archive. Note these are the program packages, not the installed application files. You can periodically remove them as they accumulate with the command: "sudo apt-get clean".  Once an app is installed you don't need the package any longer - you can download them again if needed from the repositories.

---

### Post by mju4t on 2009-07-16
Thanks for the quick response!  What about installing programs that aren't in a repository?  I want to install MATLAB, and I have all the files necessary...can I install it to /home? Do I just make a directory called programs to install all my "non repository" programs?

---

