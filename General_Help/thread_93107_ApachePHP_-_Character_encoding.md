---
title: "Apache/PHP - Character encoding"
date: 2005-11-21
forum: General Help
---

### Post by Paperjam on 2005-11-21
Hi

I have installed Apache 2 and PHP 4. My system is set to use the ISO8859-1 - encoding (I did this with *sudo dpkg-reconfigure locales*), because I am working with a lot of ISO8859-1-encoded text files.
The problem I have is that whenever I use PHP to write to a file or read from a file, characters like ö, ä, ü, ... are messed up. In fact, this probably is a problem with the *locale* of the system, but I am sure that it should somehow be possible to make it work.

I hope someone has a solution for this.

Thanks,
paperjam

---

### Post by mgor on 2005-11-21
not sure if it will help, but try setting the default charset in /etc/php4*/apache2/php.ini
```
default_charset = "iso-8859-1"
```

and reload apache.

---

### Post by Paperjam on 2005-11-21
[QUOTE=mgor]not sure if it will help, but try setting the default charset in /etc/php4*/apache2/php.ini
and reload apache.[/QUOTE]

Thanks for your help. Unfortunately it didn't work, but I found the solution myself. I had to edit the file */etc/apache2/conf.d/charset* and that did the trick...

---

