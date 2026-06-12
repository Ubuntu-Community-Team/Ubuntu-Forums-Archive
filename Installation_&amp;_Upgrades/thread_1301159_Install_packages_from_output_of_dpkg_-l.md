---
title: "Install packages from output of dpkg -l ?"
date: 2009-10-25
forum: Installation &amp; Upgrades
---

### Post by capsid on 2009-10-25
Hey guys.  I was wondering if there's an easy way to install all of your favorite packages on a fresh install, without manually keeping a list.  

What I'm going to try is making a script to parse the output from *dpkg -l *on a fully configured computer, then use that to compose a very long* apt-get install *command.  

Is there a more elegant way to do this?

---

### Post by sgosnell on 2009-10-25
```
dpkg --get-selections > ~/my-packages
```

puts the list of installed packages into a file named my-packages in your home directory.  Copy it elsewhere for safety if you feel the need, especially if your /home is not on a separate partition.

```
sudo dpkg --set-selections < my-packages && sudo apt-get dselect-upgrade
``` installs all the packages listed in my-packages.

---

### Post by capsid on 2009-10-25
Nice, this is perfect.  Googling the command you mentioned yielded a slightly longer article on the topic.
[http://kevin.vanzonneveld.net/techblog/article/restore_packages_using_dselectupgrade/](http://kevin.vanzonneveld.net/techblog/article/restore_packages_using_dselectupgrade/)

Thanks a lot!

---

### Post by sgosnell on 2009-10-25
You're welcome.  And if you want a more durable solution, install aptoncd from the repositories.  It burns you a CD of the packages, which you can use as a local repository, instead of having to download everything.

---

