---
title: "preseeding installation 8.10 - how to preseed &quot;encrypted directory&quot; prompt?"
date: 2009-02-18
forum: Installation &amp; Upgrades
---

### Post by chakoshi on 2009-02-18
Hi
I'm trying to preseed the installation for 8.10; but it seems there's no debian installer (d-i) variable to preseed the "encrypted private directory" prompt to fully automate the installation. I found it reported on launchpad [https://bugs.launchpad.net/ubuntu/+bug/285722](https://bugs.launchpad.net/ubuntu/+bug/285722) as a bug, so what should I do then? does it mean there's no way to skip this question during installation?
does any one know where can I found a full list of d-i variables,(may be in source codes?which files?)
thanks in advance

---

### Post by chakoshi on 2009-02-18
Oh! no one answered me:(
but I found the solution, hope to be useful for others;)

add this line to your preseed file:
**user-setup-udeb user-setup/encrypted-private boolean false**

I found this by the following set of commands, from ubuntu community documentations:
"[I]If you can't find the option you're looking for you can generate a comprehensive preseed file based on your own install time choices by using debconf-get-selections 

debconf-get-selections usage:

[B]sudo apt-get install debconf-utils    # It is part of the debconf-utils package.
debconf-get-selections --installer > somefile.txt
debconf-get-selections >> somefile.txt[/B] [/I]"

---

### Post by gregsheu on 2009-02-20
> **chakoshi said:**
> Oh! no one answered me:(
but I found the solution, hope to be useful for others;)

add this line to your preseed file:
**user-setup-udeb user-setup/encrypted-private boolean false**

I found this by the following set of commands, from ubuntu community documentations:
"[I]If you can't find the option you're looking for you can generate a comprehensive preseed file based on your own install time choices by using debconf-get-selections 

debconf-get-selections usage:

[B]sudo apt-get install debconf-utils    # It is part of the debconf-utils package.
debconf-get-selections --installer > somefile.txt
debconf-get-selections >> somefile.txt[/B] [/I]"

Thanks a lot. I am looking for how to disable this prompt in the preseed file as well.

---

### Post by guvnr on 2010-05-05
if you get error:-

debconf: DbDriver "di_questions": could not open ...........

try:-

debconf-get-selections > debconf
nano debconf

---

