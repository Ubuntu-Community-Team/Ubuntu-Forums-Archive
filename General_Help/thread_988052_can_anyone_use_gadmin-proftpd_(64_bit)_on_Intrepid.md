---
title: "can anyone use gadmin-proftpd (64 bit) on Intrepid?"
date: 2008-11-20
forum: General Help
---

### Post by mdurham on 2008-11-20
Here are the last few lines before it dies.
Any suggestions?
Cheers, Mike
> 7f731d774000-7f731d775000 r--s 00000000 08:08 269740                     /var/cache/fontconfig/4794a0821666d79190d59a36cb4f44b5-x86-64.cache-2
7f731d775000-7f731d776000 r--p 00000000 08:08 939927                     /usr/share/locale-langpack/en_AU/LC_MESSAGES/gtk20-properties.mo
7f731d776000-7f731d777000 r--p 00000000 08:08 936779                     /usr/lib/locale/en_AU.utf8/LC_NUMERIC
7f731d777000-7f731d778000 r--p 00000000 08:08 936780                     /usr/lib/locale/en_AU.utf8/LC_TIME
7f731d778000-7f731d779000 r--p 00000000 08:08 938327                     /usr/lib/locale/en_AU.utf8/LC_MONETARY
7f731d779000-7f731d77a000 r--p 00000000 08:08 936784                     /usr/lib/locale/en_AU.utf8/LC_MESSAGES/SYS_LC_MESSAGES
7f731d77a000-7f731d77b000 r--p 00000000 08:08 936785                     /usr/lib/locale/en_AU.utf8/LC_PAPER
7f731d77b000-7f731d77c000 r--p 00000000 08:08 936786                     /usr/lib/locale/en_AU.utf8/LC_NAME
7f731d77c000-7f731d77d000 r--p 00000000 08:08 938328                     /usr/lib/locale/en_AU.utf8/LC_ADDRESS
7f731d77d000-7f731d77e000 r--p 00000000 08:08 938329                     /usr/lib/locale/en_AU.utf8/LC_TELEPHONE
7f731d77e000-7f731d77f000 r--p 00000000 08:08 936789                     /usr/lib/locale/en_AU.utf8/LC_MEASUREMENT
7f731d77f000-7f731d786000 r--s 00000000 08:08 914149                     /usr/lib/gconv/gconv-modules.cache
7f731d786000-7f731d787000 r--p 00000000 08:08 938330                     /usr/lib/locale/en_AU.utf8/LC_IDENTIFICATION
7f731d787000-7f731d78a000 rw-p 7f731d787000 00:00 0 
7f731d78a000-7f731d78b000 r--p 0001e000 08:08 553805                     /lib/ld-2.8.90.so
7f731d78b000-7f731d78c000 rw-p 0001f000 08:08 553805                     /lib/ld-2.8.90.so
7fff25770000-7fff2578c000 rw-p 7ffffffe3000 00:00 0                      [stack]
7fff257ff000-7fff25800000 r-xp 7fff257ff000 00:00 0                      [vdso]
ffffffffff600000-ffffffffff601000 r-xp 00000000 00:00 0                  [vsyscall]


---

### Post by mdurham on 2008-11-21
anyone?

---

### Post by zajc on 2008-12-05
I have similar problem: Segmentation fault :-k

---

### Post by Angelos72 on 2008-12-17
Try this for a solution


The

"Could not launch menu item
Failed to execute child process "su-to-root" (No such file or directory)"

problem is because you do not have the su-to-root application installed. apparently the su-to-root allows you to run an application as super user, similarly to sudo. If you add the -X option it is equivalent to gksudo.

Just install the package "menu" using synaptic and this problem will be solved.

I really do not know we this package is not already installed, or why gksudo is not used in the first place.

I upgraded to Intrepid 32-bit from Hardy (32-bit), may be a clean install would not have the problem.

Now that the su-to-root problem is behind us, the problem remains that the GUI crashes.

It appears that the gadmin-proftpd version that is currently in the repositories has a bug (see also [https://bugs.launchpad.net/ubuntu/+source/gadmin-proftpd/+bug/276181](https://bugs.launchpad.net/ubuntu/+source/gadmin-proftpd/+bug/276181)).

Just install the newer version from here

[http://debian.cs.binghamton.edu/debian/pool/main/g/gadmin-proftpd/](http://debian.cs.binghamton.edu/debian/pool/main/g/gadmin-proftpd/)

and the problem will be solved.

I do not know if it matters, but I completely removed the gproftpd package (which apparently is outdated now), just to be on the safe side.

The package you have to download is:

gadmin-proftpd_0.3.5-2_i386.deb --> for 32-bit systems

or

gadmin-proftpd_0.3.5-2_amd64.deb --> for 64-bit systems

The related bug report os here...
[https://bugs.launchpad.net/ubuntu/+source/gadmin-proftpd/+bug/242067](https://bugs.launchpad.net/ubuntu/+source/gadmin-proftpd/+bug/242067)

---

### Post by flakmoppe on 2009-03-18
> Try this for a solution

You made it sound so easy.. and it was easy!

Thanks man. You really saved me.

---

