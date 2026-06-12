---
title: "apt-get install recommended &amp; suggested"
date: 2005-12-05
forum: General Help
---

### Post by Randy Sparks on 2005-12-05
Is there any way to use apt-get to install the recommended and/or suggested packages? 

According to one site I read, I should be able to type

apt-get install-rs packagename

But this doesn't work. Neither does add an -rs command option.

---

### Post by LaMpiR on 2005-12-05
I think that you need to uncomment all sorces from /etc/apt/sources.list i beleive that it is the file. Then you can find file by using command
sudo apt-cache search packagename or you can try to search it true Synaptic package menager...

---

### Post by flopsy on 2005-12-05
aptitude has --with-recommends and --with-suggests. You can use it on the command line in a similar way to apt-get, e.g. aptitude update, aptitude --with-suggests --with-recommends install packagename, etc.

aptitude also has an ncurses interface, which you use by running aptitude without options. Give it a try; it's much more powerful than Synaptic.

---

