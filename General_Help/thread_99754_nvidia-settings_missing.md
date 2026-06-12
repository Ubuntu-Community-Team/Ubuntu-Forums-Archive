---
title: "nvidia-settings missing?"
date: 2005-12-06
forum: General Help
---

### Post by Thunk on 2005-12-06
I tried to install nvidia-settings through apt-get but it gives me this error messege:

Package nvidia-settings is not available, but is referred to by another package.
This may mean that the package is missing, has been obsoleted, or
is only available from another source

How else can I get it? What other sources are there?

---

### Post by frodon on 2005-12-06
Maybe you have a problem with your source.list, look here to see if you have a missing repository : [http://www.ubuntuforums.org/showthread.php?t=92672](http://www.ubuntuforums.org/showthread.php?t=92672)

---

### Post by daller on 2005-12-06
What repos are you using?

I get this:

daniel@ubuntu:~$ sudo apt-get install nvidia-settings
Password:
Indlæser pakkelisterne... Færdig
Opbygger afhængighedstræ... Færdig
Følgende NYE pakker vil blive installeret:
  nvidia-settings
0 opgraderes, 1 nyinstalleres, 0 afinstalleres og 0 opgraderes ikke.
504kB skal hentes fra arkiverne.
Efter udpakning vil 1020kB yderligere diskplads være brugt.
Henter:1 **[http://dk.archive.ubuntu.com](http://dk.archive.ubuntu.com) breezy/restricted nvidia-settings 1.0-3ubuntu6** [504kB]
Hentede 504kB på 3s (136kB/s)

---

### Post by Thunk on 2005-12-06
[QUOTE=frodon]Maybe you have a problem with your source.list, look here to see if you have a missing repository [/QUOTE]

It was the sources list. Thanks!

---

