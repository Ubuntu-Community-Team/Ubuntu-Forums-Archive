---
title: "Does Ubuntu 64-bit have the same compatibility for Linux programs as Ubuntu 32-bit?"
date: 2008-08-25
forum: General Help
---

### Post by Hellraizer51 on 2008-08-25
There's no 32-bit Folding@Home SMP client so that's leading me to go with 64-bit...

---

### Post by Mgiacchetti on 2008-08-25
> **Hellraizer51 said:**
> There's no 32-bit Folding@Home SMP client so that's leading me to go with 64-bit...
Well the same problem that leads you to 64 led me to 32 if that tells you anything.

---

### Post by Hellraizer51 on 2008-08-26
So you mean there's a 32-bit F@H SPM client? If so, where can I get it?

---

### Post by phidia on 2008-08-26
To get 32 bit compatibility with 64 bit debian/ubuntu you just need to install the [ia32-lib package]("http://packages.ubuntu.com/gutsy/amd64/ia32-libs/download"). If you have any problems after that use [get-libs]("http://ubuntuforums.org/showthread.php?t=474790"). 
I've been using 64 bit for years without any real issues. You can run 32 bit programs in x86_64 Linux.

---

### Post by Joeb454 on 2008-08-26
I'm using 64 bit. The only thing that I've found so far that doesn't have a 64 bit release is flash.

Though as of 8.04 that installs using nspluginwrapper by default. So you can get flash easy on 64 bit installs :)

---

### Post by bollix47 on 2008-08-26
> **Hellraizer51 said:**
> So you mean there's a 32-bit F@H SPM client? If so, where can I get it?

There is no 32-bit F@H SMP client for Linux.  If that's the client you want to run then you must have 64-bit installed.  As already mentioned you need the ia32-libs installed in order to run the client as the actual client is 32-bit but the folding core is 64-bit.

---

### Post by Hellraizer51 on 2008-08-26
Ok, so just to get this straight, with the ia32-libs installed on Ubuntu 64-bit it will run every single 32-bit program correct?

---

### Post by phidia on 2008-08-26
> **Hellraizer51 said:**
> Ok, so just to get this straight, with the ia32-libs installed on Ubuntu 64-bit it will run every single 32-bit program correct?

There might be exceptions. That's why get-libs is useful. But do you need "every single 32 bit program" that's out there? Just try it with what you want.

---

### Post by Hellraizer51 on 2008-08-26
Ok then, thanks.

---

