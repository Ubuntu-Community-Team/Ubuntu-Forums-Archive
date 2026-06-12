---
title: "apt-get remove apache2"
date: 2009-01-30
forum: Installation &amp; Upgrades
---

### Post by fgeorges on 2009-01-30
Hi,

  I've tried to remove the apache2 package from my system with "apt-get remove apache2".  But it let the /etc/apache2 directory, so I removed it with "rm -r /etc/apache2".  When I "apt-get install apache2" again, it does not reinstall the config files.  I tried apt-get purge too.

  How can I remove completely the package (including what is in /etc) and then reinstall it again (including the original files in /etc) ?

  Regards,

-- 
Florent Georges
[http://www.fgeorges.org](http://www.fgeorges.org)

---

### Post by shredder12 on 2009-01-30
why don't you try this one with synaptic.. there you have an option of "complete removal" and when you will apply the changes it will ask for removal for config files..
.. I think this will do the job..

---

### Post by fgeorges on 2009-01-30
Thanks for the response.  AFAIK, synaptic is a graphical interface, and I am running Ubuntu on a server (besides, I am calling apt-get from a script.)

Regards,

-- 
Florent Georges
[http://www.fgeorges.org/](http://www.fgeorges.org/)

---

### Post by shredder12 on 2009-01-30
Okk.. well then you should try this command..
```
sudo apt-get --purge remove <package name> 
```

but this works only when you have that package installed..
suppose you have uninstalled that package and then run this command.. you will get an error..
so,, in order to remove the old configuration files with the package already removed you should probably try this command..
```
sudo dpkg --purge <package name>
```

and as i have already mentioned..this works even when the package is not really installed..

---

### Post by fgeorges on 2009-01-30
Mmh, actually dpkg --purge doesn't work on my system:

dpkg - warning: ignoring request to remove apache2 which isn't installed.

If I use either command when the package is installed, /etc/apache2 is not removed...  And if I remove it by hand, it is not reinstalled by a subsequent install.

I am testing admin scripts; it would be very, very convenient to be able to entirely suppress the apache2 package, and still be able to reinstall a completely clean version.

Maybe did I do something wrong?  Thanks for your help,

-- 
Florent Georges
[http://www.fgeorges.org/](http://www.fgeorges.org/)

---

### Post by cariboo on 2009-01-30
Did you stop apache2 before you tried to remove it? Stop the service and then run:

```
sudo apt-get purge apache2
```

I ran into the same problem a  while back. I use mc as a file manager, ftp client, and more. MC allows you to open a .deb and copy a config file or whatever you need, to any location. I do this when I've forgotten to make a backup of a configuration file before changing it.

MC is available in the repositories.

Jim

---

### Post by fgeorges on 2009-01-30
Thanks, Jim.  Unfortunately, that does not help.  /etc/apache2 is still there after stopping Apache and purging or removing the package, with either apt-get or dpkg.

-- 
Florent Georges
[http://www.fgeorges.org/](http://www.fgeorges.org/)

---

### Post by shredder12 on 2009-01-30
hey, chk this out.. 
i think its the same problem you are facing..
[http://ubuntuforums.org/showthread.php?t=296875](http://ubuntuforums.org/showthread.php?t=296875)

---

### Post by shredder12 on 2009-01-30
for other queries regarding apt-get ..
you can follow this wiki link..
[http://wiki.linuxhelp.net/index.php/Apt-get_Guide](http://wiki.linuxhelp.net/index.php/Apt-get_Guide)

---

### Post by slakkie on 2009-01-30
aptitude purge apache2 should do the trick.

But you could also try to run dpkg-reconfigure apache2, this should in theory reconfigure apache (thus creating new config files).

---

### Post by fgeorges on 2009-02-06
Thanks shredder12, that was indeed the same problem!

-- 
Florent Georges
[http://www.fgeorges.org/](http://www.fgeorges.org/)

---

### Post by iflickle on 2011-04-27
I had the same problem it took me about 20mins to figure it out... 

Solution:

This should not affect your files in /var/www/ as they didnt with mine.
1) sudo apt-get --purge remove  lamp-server^
2) sudo rm -rf /etc/apache2   (i think this is the main thing to do - remove the folder)
3) sudo tasksel    (now lamp server will be de-selected, select it and press enter/ok)

Done!!

iflickle
[http://www.iflickle.com](http://www.iflickle.com)

---

