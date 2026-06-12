---
title: "Dynagen not Working"
date: 2009-05-01
forum: Installation &amp; Upgrades
---

### Post by vinupete on 2009-05-01
Hi i am vey new to ubuntu domain.... i recently upgradd my OS to 9.04 n suddenly my Dynagen stopped working ?
the error message i get is,

vinu@vinu-desktop:~$ dynagen /home/vinu/dynamips/LAB3/sp.net
Traceback (most recent call last):
  File "/usr/bin/dynagen", line 28, in <module>
    from console import Console
  File "/var/lib/python-support/python2.6/console.py", line 34, in <module>
    from confConsole import AbstractConsole, confHypervisorConsole, confConsole
ImportError: No module named confConsole

 how do i fix this one... please help

---

### Post by drake77 on 2009-05-13
> **vinupete said:**
> Hi i am vey new to ubuntu domain.... i recently upgradd my OS to 9.04 n suddenly my Dynagen stopped working ?
the error message i get is,

vinu@vinu-desktop:~$ dynagen /home/vinu/dynamips/LAB3/sp.net
Traceback (most recent call last):
  File "/usr/bin/dynagen", line 28, in <module>
    from console import Console
  File "/var/lib/python-support/python2.6/console.py", line 34, in <module>
    from confConsole import AbstractConsole, confHypervisorConsole, confConsole
ImportError: No module named confConsole

 how do i fix this one... please help

I have the same problem!! :(

---

### Post by nguoimotthoi on 2009-05-23
File "/usr/bin/dynagen", line 28, in <module>
    from console import Console
  File "/var/lib/python-support/python2.6/console.py", line 34, in <module>
    from confConsole import AbstractConsole, confHypervisorConsole, confConsole
ImportError: No module named confConsole

---

### Post by tigerplug on 2009-06-12
Smae here guys... just can't get it working :(

Any updates?


Tigerplug

---

### Post by po11ution on 2009-06-24
I'm also having this issue.
Apparently the way to solve it is to use synaptics to remove dynagen, then download the dynagen tar ball and extract it manually. I did this, but can't get dynagen to run now - probably need to create a symbolic link (which i'm unsure of)

Guys mention moving dynagen into /usr/local/bin directory - but i'm also unsure why.

---

