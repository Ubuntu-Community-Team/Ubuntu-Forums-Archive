---
title: "ubuntu 10.10 32bit :  &quot;free -m&quot; says I have 8gb"
date: 2011-04-16
forum: Hardware
---

### Post by Bachelier on 2011-04-16
Hi folks,

I am confused...

I installed Ubuntu 10.10 32 bit on my Asus g73sw with 8gb RAM (installing the 64 bit version didn't work, unfortunately -- any ideas why?)

On the command line"free -m" yields
                   total       used       free     shared    buffers     cached
Mem:          8049        605       7443          0         37        269

Now, computer illiterate as I may be, why does 32 bit Ubuntu recognize more than 4gb RAM ?

---

### Post by SeijiSensei on 2011-04-16
What does the command "uname -a" show?  If you're using a [-pae kernel]("https://help.ubuntu.com/community/EnablingPAE"), it includes some "tricks" to see > 3GB on 32-bit machines.

---

### Post by Bachelier on 2011-04-18
Hi SeijiSensei,  the link you added to your reply contained the solution:  PAE seems to be enabled with the installers with versions > 10.04.   Thanks for pointing me in the right direction! Bachelier

---

