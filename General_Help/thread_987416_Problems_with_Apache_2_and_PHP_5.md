---
title: "Problems with Apache 2 and PHP 5"
date: 2008-11-19
forum: General Help
---

### Post by Musicalmidget on 2008-11-19
Hi all.

Continuing in my quest to make Ubuntu my full time operating system I'm working on setting up an apache server with php.  I've done this several times before on various different operating systems including Ubuntu, yet for some reason I'm having problems doing so on Ubuntu 8.10.

I firstly installed apache2 and when I went to localhost in my browser the default apache index.html file was there displaying "It works!".

Next, I installed php5 (which also installed libapache2-mod-php5).  I restarted apache for good measure and created a test file in /var/www to display PHP information.  I also setup DirectoryIndex in apache2.conf to look firstly for index.php before then looking for .html or .htm files.  After restarting the apache server however, none of these changes seem to have taken effect.  Visiting localhost still defaults to index.html instead of index.php.  Also, when I manually navigate to index.php Firefox attempts to download or open the file rather than display it.

The PHP error seems to suggest that the apache config file wasn't updated correctly by the PHP installer, but reinstalling the package hasn't solved the problem.  Similarly, removing and then reinstalling apache also results in the same effect.  As for the DirectoryIndex problem, I've no idea about that one.

I've searched around for similar problems and seen some posts which suggest checking that PHP is enabled in apache by running a2enmod php5, but when I tried this I was told that PHP was indeed already enabled.

This is really the only thing remaining that absolutely *must* be fixed if I'm going to be able to make the full switch to Ubuntu, therefore advice as always would be most appreciated.

Thanks.

---

### Post by Musicalmidget on 2008-11-19
Typically, I seem to have managed to solve these problems myself since posting this thread.  I'll post the solutions here for reference if anyone else finds themselves experiencing the same problems.  As expected, there were small things that were overlooked during setup which resulted in the problems I was experiencing.

Firstly for the PHP problem, when I investigated further I found that the package php5-cgi had been missed from the installation.  Simply installing this package allowed PHP and Apache to work together and I can now run PHP scripts locally from my browser.

Secondly, the DirectoryIndex problem was also simple.  The DirectoryIndex instructions I was placing in /etc/apache2/apache2.conf were being overwritten by another set of instructions in /etc/apache2/mods-available/dir.conf.  Removing my changes from apache.conf and instead making my changes in mods-available/dir.conf was the solution.

Hopefully this thread may prove useful for someone else in the future.  If not, I've at least learnt more myself about setting up Apache/PHP on Ubuntu. :)

---

