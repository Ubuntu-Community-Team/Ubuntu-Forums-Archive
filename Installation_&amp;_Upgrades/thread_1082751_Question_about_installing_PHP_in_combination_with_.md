---
title: "Question about installing PHP in combination with Mysql (im noob)"
date: 2009-02-28
forum: Installation &amp; Upgrades
---

### Post by BramWillemsen on 2009-02-28
Hello everyone. 

A few days ago i purchased a laptop. I directly installed ubuntu, but i'm not that good with Linux yet. I have been reading a book about php and mysql for some time, and i'd like to test some of my newly acquired skills. The specific book that I use gives a guide to install mysql and php with apache and such in Linux. Yesterday i tried to install mysql 5.1 but i ran into some trouble because 5.0.6 was already installed on my computer.S This messed up mysql completely so i removed all mysql and used the apt-get install feature to get 5.0.6 back. MySQL works now perfectly (when i know more about linux ill try to boost it to 5.1), but i do have problems when i want to install php.

The specific book I'm using (Luke Welling, Laura Thomson ->"PHP and MYSQL Web Development") told install php in the following way.

Download the php tar.gz  file. Go with the terminal to the directory where you untarred it. Then use the following command: 

./configure --prefix=/your/path/to/php \
            --with-mysqli=/your/path/to/mysql_config \
            --with blabla \
            --with blabla

**The problem is that i don't have a mysql_config file on my computer to link to. I guess i really need this for the mysqli feature.** How did you guys install php on your computer? I'm using the 8.10 desktop 64 bit edition btw. Do i have to uninstall mysql 5.0.6 again to install 5.1 in some way ? Or is there something that i forget ? I'm totally new to Linux so i may have made some mistake. Thanks a lot for the help.

kind regards,

Bram Willemsen

---

