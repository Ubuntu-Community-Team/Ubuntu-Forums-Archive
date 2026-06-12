---
title: "/bin/csh: bad interpreter: No such file or directory"
date: 2009-06-09
forum: Installation &amp; Upgrades
---

### Post by debojyoti on 2009-06-09
Dear user, I am new to this ubuntu linux world and having some problem when I am trying to install a software. When I am giving a script 

./expand_lapw 

in the terminal I am getting an error which reads:

bash: ./expand_lapw: /bin/csh: bad interpreter: No such file or directory

Could anyone please help me in sorting out the problem without using the heavy technical jargon.

Debojyoti

---

### Post by Lampi on 2009-06-09
you are missing the C-Shell (csh):

sudo apt-get install csh

---

### Post by riopiedra on 2012-03-10
Thank you!

---

### Post by oldos2er on 2012-03-10
Closed, necromancy.

---

