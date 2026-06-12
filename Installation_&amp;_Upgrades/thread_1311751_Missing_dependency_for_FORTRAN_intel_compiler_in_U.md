---
title: "Missing dependency for FORTRAN intel compiler in Ubuntu 9.10"
date: 2009-11-02
forum: Installation &amp; Upgrades
---

### Post by profeta81 on 2009-11-02
The intel fortran compiler needs libstrc++5 installed on the system, which doesn't seems to be supported in the main rep of ubuntu anymore. I solved the problem by downloading and installing the debain package from

[http://packages.debian.org/lenny/libstdc++5](http://packages.debian.org/lenny/libstdc++5)

this seemed to solve the problem although it isn't neat. Anybody has a better solution?

regards
Lorenzo Trojan


p.s. ifort is the only fortran compiler I'm using. I don't know if other intell products are not working

p.p.s. refer to thread on the intel forums:

[http://software.intel.com/en-us/forums/intel-fortran-compiler-for-linux-and-mac-os-x/topic/69247/](http://software.intel.com/en-us/forums/intel-fortran-compiler-for-linux-and-mac-os-x/topic/69247/)

---

### Post by profeta81 on 2009-11-05
just thought of bumping up this thread...

This may be an issue to all Intel products users...

regards

---

### Post by inato_uzumaki on 2010-01-22
Step no: 4 of 7 | Installation configuration - Missing Optional Pre-requisite
--------------------------------------------------------------------------------
There is one or more optional unresolved issues. It is highly recommended to fix
it all before you continue the installation. You can fix it without exiting from
the installation and re-check. Or you can quit from the installation, fix it and
run the installation again.
--------------------------------------------------------------------------------
Missing optional pre-requisite
-- operating system type is not supported.
-- system glibc or kernel version not supported or not detectable
-- binutils version not supported or not detectable
--------------------------------------------------------------------------------
    1. Skip missing optional pre-requisites [default]
    2. Show the detailed info about issue(s)
    3. Re-check the pre-requisites

    h. Help
    b. Back to the previous menu
    q. Quit
--------------------------------------------------------------------------------
Please type a selection or press "Enter" to accept default choice [1]:


[COLOR=DarkOrange]**what should I do? please help me?**[/COLOR]

---

