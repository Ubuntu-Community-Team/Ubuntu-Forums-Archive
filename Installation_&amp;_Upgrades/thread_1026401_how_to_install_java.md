---
title: "how to install java?"
date: 2008-12-31
forum: Installation &amp; Upgrades
---

### Post by m.balakrishnan on 2008-12-31
how do i install java on ubuntu?

---

### Post by TerryArnott on 2008-12-31
I'm new to Ubuntu (and linux in general) but love it so far, only prob is I too can not install Java.  I'm probably going about it all wrong so if someone could point me in the right direction it would be a big help.

TIA

T

---

### Post by namdung on 2008-12-31
System-->Admin-->Synaptic Package Manager

JRE - run java applications
JDK - develop java applications

Therefore select either of the following according to ur need
[INDENT][I]sun-jave6-jdk
sun-java6-jre[/I][/INDENT]

---

### Post by TerryArnott on 2008-12-31
> **namdung said:**
> System-->Admin-->Synaptic Package Manager

JRE - run java applications
JDK - develop java applications

Therefore select either of the following according to ur need
[INDENT][I]sun-jave6-jdk
sun-java6-jre[/I][/INDENT]

Hi and thanks for the pointers, but its not working for me.

I go into the package manager and tick 'sun-java6-jre' then it thinks for a sec and comes up with an error.

Could not mark all packages for installation or upgrade
sun-java6-jre:
   Depends: java-common (>=0.24) but it is not installable
   Depends: sun-java6-bin but it is not going to be installed or
       ia32-sun-java6-bin (=6-10-0ubuntu2) but it is not installable

   Recommends: gsfonts-x11 but it is not installable

All this means to me is that there is some problem.... lol
Where do i go from here?

TIA again

T

---

### Post by TerryArnott on 2009-01-08
I have figured this one out.

It appears that the country specific servers are not necessarily fully stocked with all the packages and files.

I switched to use the main server instead of the Australian local server and it now finds and installed all the packages.

Hope this helps anyone else with this same problem.

T

---

