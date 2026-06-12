---
title: "Parallel Zip 250 drive isn't working through parallel in 12.04"
date: 2013-11-30
forum: Hardware
---

### Post by BlackMaxPhoto on 2013-11-30
HELP!


I'm trying to access a Zip 250 Parallel in UBS 12.04, does ANYBODY know a method that WORKS?

I've consulted the Wizard of Google and tried three variations, so far, none of them have worked.

Either the system locks up or I get, "special device sd4 not found"


:confused:

---

### Post by rackit on 2013-11-30
If it is an old zip drive, which it would be, does it work on other machines? It may just be bad,. I've had several fail over the years.

---

### Post by BlackMaxPhoto on 2013-11-30
It doesn't show up in the file manager

---

### Post by rackit on 2013-11-30
Here is an old article using gnome - adapt to unity and see what happens. [https://help.ubuntu.com/community/IomegaZIPDrive](https://help.ubuntu.com/community/IomegaZIPDrive)

---

### Post by BlackMaxPhoto on 2013-11-30
UBS runs xfce ... not Unity

Tried that one already, the command:

#  cat /proc/scsi/scsi 

... yields NO listing of the drive, that one was written to work under Ubuntu 6.06, so it was unlikey to still work under 12.04.

:popcorn:

:cool:

---

### Post by rackit on 2013-11-30
I understand. Sometimes we can glean bits of the right trail to take from the older stuff. Sorry for wasting your time. :(

---

### Post by BlackMaxPhoto on 2013-12-04
No time wasted, I had  tried the old page prior to posting here ... still seeking a working solution.

Tried the 'jazip' package from the repository as well, no luck there either

---

### Post by tgalati4 on 2013-12-05
Find an old machine with a parallel port and put Dapper Drake (6.06) on it.  I was able to access some old zip drives that I had with Dapper.  Newer kernels dropped support for ISA bus and other legacy hardware, so it's no surprise that you are having problems.

---

### Post by BlackMaxPhoto on 2013-12-06
Thanx

:popcorn:

---

