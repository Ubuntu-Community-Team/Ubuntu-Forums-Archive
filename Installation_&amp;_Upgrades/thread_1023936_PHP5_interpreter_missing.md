---
title: "PHP5 interpreter missing"
date: 2008-12-28
forum: Installation &amp; Upgrades
---

### Post by Vordreller on 2008-12-28
Greetings. Two days ago, I installed Ubuntu 8.10 using Wubi.

Before that day, I'd never worked with anything but Windows.
Now, with the help of google, most things weren't hard to figure out. I had the system checked for updates, I installed Java, I installed netbeans for PHP and then I followed these 3 articles to be able to debug PHP:

[http://blogs.sun.com/netbeansphp/entry/ubuntu_php_netbeans](http://blogs.sun.com/netbeansphp/entry/ubuntu_php_netbeans)
[http://blogs.sun.com/netbeansphp/entry/ubuntu_php_netbeans_part_ii](http://blogs.sun.com/netbeansphp/entry/ubuntu_php_netbeans_part_ii)
[http://blogs.sun.com/netbeansphp/entry/ubuntu_php_netbeans_part_iii](http://blogs.sun.com/netbeansphp/entry/ubuntu_php_netbeans_part_iii)

I got the phpinfo() page to run and all, so that's a succeS.

Now I'm trying to get Netbeans to debug my files, but for some reason, there's no PHP interpreter found.

I went to /usr/bin/ to check for PHP but it wasn't there.

I tried the terminal: whereis php
but that returned nothing.

So since I don't have a php interpreter, I can't debug my php projects.

It's kinda weird, since the pages render perfectly, but I just can't find the interpreter...

does anybody know what might be causing this and/or what I can do to make things work?

---

### Post by npm1 on 2009-07-02
no i don't that is exactly what i'm also looking for netbeans 

their is easy eclipse and it comes with everything pre installed all u do is open the package in the folder and walla it opens with no installation required @ all

---

### Post by npm1 on 2009-07-02
i'll try it out as well and let u know how it works out for me

---

### Post by bowens44 on 2009-07-02
try this:
sudo apt-get install php5-cli

---

### Post by npm1 on 2009-07-02
yes its working thank u very much mate

---

### Post by npm1 on 2009-07-02
now their is no need for any other ide

---

### Post by tatacarrera on 2010-06-22
sudo apt-get install php5-cli
worked for me!!
thanks

---

