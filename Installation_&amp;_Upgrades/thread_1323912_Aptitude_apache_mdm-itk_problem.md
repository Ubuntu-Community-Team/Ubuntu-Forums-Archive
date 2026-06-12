---
title: "Aptitude apache mdm-itk problem"
date: 2009-11-12
forum: Installation &amp; Upgrades
---

### Post by Lord_Garfield on 2009-11-12
Hi all,

One day I decided to install apache by using
aptitude install apache2

Ok fine. But after installing some stuff to enable webdav I totaly screwed up apaches config. So I decided to startover.

I do 
aptitude purge apache2

What I find out is that all files are still there. services are still running etc..

So then I do it totaly wrong i suppose.
I rm -f everything in /etc/apache2
/var/log/apache2
/usr/bin/apache2
/etc/init.r2/apache2
etc/init.d/apache2
etc...

great I think. Lets do aptitude install apache again.
Seems to work fine but there is no /etc/apache2 anymore..
Hmmm. Looked it up and it seemed that this is created by apache-common but that one is still installed. (in fact I removed it manualy but aptitude thinks it is still installed.)
Ok first remove apache again
aptitude purge apache2
then common
aptitude purge apache2.2-common.
A lot will go wrong now.
Especialy with something called apache2-mdm-itk

when I do aptitude search apache
I still have the folowing lines that I probably need to get removed:

id  apache2-mpm-itk
ipA apache2.2-common

I tried to aptitude purge them both but it fails. reinstall fails
aptitude -f remove fails
 How can I fix this so I can do 
aptitude install apache2 again like when I had a fresh install?

thanks in advance.

kind regards.

---

### Post by Lord_Garfield on 2009-11-13
Is this a major problem that can't be fixed? Or did I not explain my question in the right form? Please ask for more details if needed.

---

