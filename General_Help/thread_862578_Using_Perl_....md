---
title: "Using Perl ..."
date: 2008-07-17
forum: General Help
---

### Post by root-x on 2008-07-17
I had a look if i had Perl on my terminal and it looks like i have but how do i know what version is on and what is the directory of the (Perl) folder e.g C:\Perl in windows i need to know the directory of the C:\Perl\bin folder cause i need to add .pl scripts inside the folder to run .. how do i do that. I needed Active Perl 5.8.8 installing ..

sorry for the n00byish questions ...


and if i do try installing it it says ...

E: Could not open lock file /var/lib/dpkg/lock - open (13 Permission denied)
E: Unable to lock the administration directory (/var/lib/dpkg/), are you root?

i have full rights and I'm in the root user group.

and if i use the tracert command it says only for super users how do i become a super user ?

---

### Post by root-x on 2008-07-18
any ideas ??

---

### Post by danwood76 on 2008-07-18
Running
```

perl -v

```
Will tell you the version and patchlevel of perl.

Perl scripts are just executed by doing ./*****.pl, you dont need to add the perl scripts anywhere to make them run.
If you need more perl modules they can generally be installed through CPAN quite easily.

BTW when you run programs like apt-get you need to run them as root user using sudo.

---

### Post by Chokkan on 2008-07-18
Hi, you can type perl -v at the prompt to see your version.

EDIT: Ouch beat'd :)

---

### Post by root-x on 2008-07-21
k cheers ... all sorted now ..

---

