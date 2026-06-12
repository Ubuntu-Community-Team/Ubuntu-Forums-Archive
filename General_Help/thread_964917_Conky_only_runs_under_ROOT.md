---
title: "Conky only runs under ROOT????"
date: 2008-10-31
forum: General Help
---

### Post by w1av on 2008-10-31
My newly installed Conky will only start from terminal if I do:

sudo su
then becomes root and when I type "conky&" it runs fine. If I don't do this as regular user I get errors. Could it be a permission problem??? Not sure where or what to look at for solution. Since this is the case, I cannot have conky in my startup because of the needed command to run it as ROOT!!!!  I installed conky.conf in /etc/conky  It is a copy of someone else I found on here that looks perfect on my desktop.Thanks:confused:

---

### Post by malleus74 on 2008-11-07
I'm still pretty much a newbie, but the way I installed conky was:

sudo apt-get install conky

Then you can edit the .conkyrc file in your home directory, if you're a single user... copy in the file you have from the net, and make sure you have all the addons for what you're trying to do.

This thread [http://ubuntuforums.org/showthread.php?t=281865](http://ubuntuforums.org/showthread.php?t=281865) has quite a lot of customized .conkyrc files posted to it.

---

