---
title: "Can't edit symbolic link"
date: 2008-09-10
forum: General Help
---

### Post by bossy22 on 2008-09-10
hi, 

I have a problem with a symbolic link in my system..

The Task is to link from a file in the sites-enabled Folder in /etc/apache2/

to a Folder in my Home Directory..

The Prompt: 

```

root@tatooine-desktop:/etc/apache2/sites-enabled# ln -s /etc/apache2/sites-enabled/100-myfootballteam /home/hendrik/work/myfootballteam/www/conf/vhost.conf 
ln: Erzeuge symbolische Verknüpfung „/home/hendrik/work/myfootballteam/www/conf/vhost.conf“: File exists

```

Of course the file exists, because I want to link from /etc/apache2/sites-enabled/100-myfootballteam 


to

/home/hendrik/work/myfootballteam/www/conf/vhost.conf 


Any help?


regards bossy

---

### Post by hyper_ch on 2008-09-10
you don't have the syntax right:

ln -s /PATH/TO/WHERE/THE/SYMLINK/SHALL/GO /PATH/TO/WHERE/THE/SYMLINK/SHALL/BE

---

### Post by bossy22 on 2008-09-10
thanx a lot. It went forward, but still a problem: 

Prompt: 

> 
root@tatooine-desktop:/etc/apache2/sites-enabled# /etc/init.d/apache2 start
 * Starting web server   apache2                                                 
 apache2: Syntax error on line 298 of /etc/apache2/apache2.conf: Could not open configuration file /etc/apache2/sites-enabled/100-myfootballteam: Too many levels of symbolic links


---

### Post by Sycron on 2008-09-10
Remove the symlink you've done and then create it again.

---

### Post by bossy22 on 2008-09-11
did it..

rm symlink
then 
ln -s to relink it..

still the same error message

```
lrwxrwxrwx 1 root root   36 2008-09-09 13:29 000-default -> /etc/apache2/sites-available/default
root@tatooine-desktop:/etc/apache2/sites-enabled# ln -s /home/hendrik/work/myfootballteam/www/conf/vhost.conf /etc/apache2/sites-enabled/100-myfootballteam 
root@tatooine-desktop:/etc/apache2/sites-enabled# ls -al
insgesamt 8
drwxr-xr-x 2 root root 4096 2008-09-11 10:51 .
drwxr-xr-x 7 root root 4096 2008-09-09 13:29 ..
lrwxrwxrwx 1 root root   36 2008-09-09 13:29 000-default -> /etc/apache2/sites-available/default
lrwxrwxrwx 1 root root   53 2008-09-11 10:51 100-myfootballteam -> /home/hendrik/work/myfootballteam/www/conf/vhost.conf
root@tatooine-desktop:/etc/apache2/sites-enabled# /etc/init.d/apache2 start
 * Starting web server apache2                                                  apache2: Syntax error on line 298 of /etc/apache2/apache2.conf: Could not open configuration file /etc/apache2/sites-enabled/100-myfootballteam: Too many levels of symbolic links

```


when I type ls -al it
says "insgesamt 8" which means "all in all 8" does that refer to the amount of symlinks??

regards

bossy

---

### Post by hyper_ch on 2008-09-11
do you have a symlink that refers back again and hence you have an endless loop?

---

### Post by bossy22 on 2008-09-11
yes I did!!

thanx for the tip...

Everything works now..

thanx a lot


bossy

---

### Post by Sycron on 2008-09-11
I'm glad it works :D .

---

