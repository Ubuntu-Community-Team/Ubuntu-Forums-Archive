---
title: "errod csh required"
date: 2005-04-12
forum: Hardware &amp; Laptops
---

### Post by rbarth on 2005-04-12
While trying to run the command "dpkg -i --force-overwrite cupswrappermfc210c_1.0.0-1_i386.deb" I get this:

> (Reading database ... 58056 files and directories currently installed.)
Preparing to replace cupswrappermfc210c 1.0.0-1 (using cupswrappermfc210c_1.0.0-1_i386.deb) ...
Unpacking replacement cupswrappermfc210c ...
Setting up cupswrappermfc210c (1.0.0-1) ...

 ****** ERROR: csh is required. ******


Does anyone know what this is telling me, and what do I need to do to fix it. Really new at this.

Thank You

Bob

---

### Post by rbarth on 2005-04-12
ok... turns out that this was no big thing, csh stands for the "C" shell and it is needed to compile or whatever it is doing. Used Synaptic to download the file "tcsh" and everthing now works fine.

Bob

---

