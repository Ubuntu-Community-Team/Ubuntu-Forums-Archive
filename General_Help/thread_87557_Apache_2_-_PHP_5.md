---
title: "Apache 2 - PHP 5"
date: 2005-11-08
forum: General Help
---

### Post by ivanp on 2005-11-08
Hello everybody.

I need to install Apache 2, PHP 5 and MySQL 4.1.x. I guess the normal way should be just to go trough every site downloading rpm's or .tar.gz's and follow the instructions, but, I it ocurrs to me that this **Synaptic** thing may be helpful. Any clues?

Thank in advance

Ivan

---

### Post by paddyg on 2005-11-08
in terminal just type

```
sudo apt-get install apache2
sudo apt-get install php5
```

---

### Post by ivanp on 2005-11-08
Thanks a lot paddyg, dou you mind help me with **MySql 4.1**.x too

---

### Post by Stereotypical Rage on 2005-11-08
[QUOTE=ivanp]Hello everybody.

I need to install Apache 2, PHP 5 and MySQL 4.1.x. I guess the normal way should be just to go trough every site downloading rpm's or .tar.gz's and follow the instructions, but, I it ocurrs to me that this **Synaptic** thing may be helpful. Any clues?

Thank in advance

Ivan[/QUOTE]Enable the extra repositories in your /etc/apt/sources.list file. Mainly the Universe one.

You, then want mySQL client and server 4.1.x and php5-mySQL, libapache2-mod-php5.

Do a name search for "mySQL" and "php5", you'll find what you need there.
Installing phpmyadmin is nice too.

I currently have PHP5, mySQL 4.0.x (DOH) and Apache2 on my local machine.

---

### Post by paddyg on 2005-11-08
also, this link may help you (it's for Hoary, but most things are ok with Breezy as well)
[http://www.ubuntuguide.org](http://www.ubuntuguide.org)

---

### Post by ivanp on 2005-11-10
Thanks. Just one thing, I don't understand what you mean with **Hoary** and **Breeze.** Are they just **flavors** for ubuntu distribution?

---

### Post by ivanp on 2005-11-10
Yes, is a flavor

---

### Post by valmy on 2005-11-10
[QUOTE=ivanp]Thanks. Just one thing, I don't understand what you mean with **Hoary** and **Breeze.** Are they just **flavors** for ubuntu distribution?[/QUOTE]

Breezy is the new edition that was released October 2005, while Hoary is the previous one that was released in March 2005.

---

### Post by ivanp on 2005-11-10
How do I make sure I'm using breezy?

---

### Post by Joh_ on 2005-11-10
If you've got the ubuntu logo showing while it's starting up (before the graphical interface), with a progress bar and lots of text scrolling below, you're using Breezy.

---

### Post by paddyg on 2005-11-10
[QUOTE=ivanp]How do I make sure I'm using breezy?[/QUOTE]

in terminal
```
cat /etc/lsb-release
```
or
```
head /etc/lsb-release
```

---

