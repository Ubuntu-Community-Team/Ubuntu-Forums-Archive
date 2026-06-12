---
title: "Installing MediaWiki"
date: 2005-11-15
forum: General Help
---

### Post by aliB on 2005-11-15
First I succesfully installed MediaWiki based on [this]("http://meta.wikimedia.org/wiki/Help:Running_MediaWiki_on_Debian_GNU/Linux") description.

But then I got aware that Ubuntu has a mediawiki package in its repository, so I thought why not try this one.
The advantage would be, that I easily can upgrade my mediawiki using **aptitude upgrade**

```
Warning: main(./LocalSettings.php): failed to open stream: Permission denied in /usr/share/mediawiki/index.php on line 25
But all I get to see from my new wiki is this message in the browser:
Fatal error: main(): Failed opening required './LocalSettings.php' (include_path='.:/usr/share/php:/usr/share/pear') in /usr/share/mediawiki/index.php on line 25
```

In short, this is what I've already done:
Installing ubuntu 5.10 Breez (hostname wikipc)
- sudo bash
- uncommented breeze universe repository
- aptitude update && aptitude install mediawiki

-setting the mysql psw
>> mysqladmin -u root password xxxx

- created Dir:
>>  /etc/mediawiki/wikis
- cp -a /var/lib/mediawiki /etc/mediawiki/wikis/_mywiki

configure apache2:
- cp /etc/apache2/sites-available/default /etc/apache2/sites-available/_mywiki
- setting the DocumentRoot and the Directory to /etc/mediawiki/wikis/_mywiki/
- creating a symlink in /etc/apache2/sites-enabled/
>> ln -s /etc/apache2/sites-available/_mywiki 000-mywiki
- removing 000-defualt symlink (otherwise it doesn't work (I don't know why))

configure /etc/php4/apache2/php.ini
- memory_limit = 20M
- extension=mysql.so
- extension=gd.so

- apache2ctl restart

Now you can configure the wiki under [http://wikipc/config](http://wikipc/config)

- copy /var/lib/mediawiki/config/LocalSettings.php /etc/mediawiki/
- chmod 600 /etc/mediawiki/config/LocalSettings.php

Now the wiki page should theoretically work but all I see is the error posted already above.
I hope somebody can help.

---

### Post by aliB on 2005-11-15
Sorry, forgot to say that I installed Ubuntu for server.
Maybe this is important.

---

### Post by aliB on 2005-11-15
> First I succesfully installed MediaWiki based on this description.
This was of course (as said in the description of mediawiki) on a debian sarge system.
On ubuntu this description doesn't work too.

Sorry for the inconvenience.

Has anybody already installed mediawiki successfully on ubuntu 10.5?

---

### Post by [2]BoxingFiend on 2005-11-15
took me a while to get mine up and running.

breezy base install

[LIST]
[*]add [http://packages.dotdeb.org](http://packages.dotdeb.org) stable all
[*]install mysql5
[*]compile eaccelerator
[*]install graphviz for flow charts
[*]install ploticus for timeline
[*]compile lilypond 2.6.x version, breezy and debian version is classifed as ancient
[*]install gnuplot, working on an extention atm, must have my 3d graphs
[*]download and configure geshi
[/LIST]

base install before i start putting up my articles again

[http://ferin.homelinux.org](http://ferin.homelinux.org)


TODO list
[LIST]
[*]get a comment area up and running, i like to lock down my wiki
[*]redo lilypond hooks to "autocrop" music
[/LIST]

---

### Post by aliB on 2005-11-15
Hi BoxingFiend, thanks for answering,
I've still some question:
> add [http://packages.dotdeb.org](http://packages.dotdeb.org) stable all
This is a backport right? Why do you need this?
Isn't everything you need also available in the universe repository?

> install mysql5
is also installed when **aptitude install mediawiki**
(I don't know if it's also Version 5 but I think so)

> compile eaccelerator
> install graphviz for flow charts
> install ploticus for timeline
> compile lilypond 2.6.x version, breezy and debian version is classifed as ancient
> install gnuplot, working on an extention atm, must have my 3d graphs
> download and configure geshi

are these packages really necessary? under debian sarge I didn't need to install these packages to get my wiki working.
I thought with ubuntu the installation of a wiki would be easear because of the mediawiki package in the repository :confused::confused:

---

### Post by [2]BoxingFiend on 2005-11-15
at the core all you need is apache, mod_php, php, mysql

with those, you can literally, download the tar, untar it into /srv/www.  rename it to your liking

and then http://localhost/{name of wiki dir}/config

i chose to install the other packages just because i wanted to have this wiki on ubuntu have stuffs that was on my old server

---

### Post by aliB on 2005-11-17
Finaly I got a solution on [www.ubuntuusers.de](www.ubuntuusers.de).
My mistake was, that I didn't change the owner and group of LocalSettings.php
>> chown www-data:www-data LocalSettings.php
and everything is working!

Since I've described the installation very detailed this thread could also be used as a tutorial for other users.

---

### Post by Mortuis on 2007-08-08
I'm glad you posted this aliB, it was really helpful to me just now.

---

### Post by Sureseven on 2007-09-20
Changing the group / ownership of LocalSettings.php solved it for me, too.

We should post this information more prominently somewhere.

---

