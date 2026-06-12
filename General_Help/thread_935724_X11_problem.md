---
title: "X11 problem"
date: 2008-10-02
forum: General Help
---

### Post by joacorapela on 2008-10-02
Greetings,

I am running Ubuntu 8.04 with all the latest updates and Gnome 2.22.3 on my laptop. I ssh -X to a server running SUSE, I type xdvi, xdvi appears briefly and then crashes with the following message

Warning: locale not supported by Xlib, locale set to C
Warning: Unable to load any usable fontset
Error: Aborting: no fontset found

If I type xterm (or xclock or xcalc) it works fine, but I get the following warning

Warning: locale not supported by Xlib, locale set to C

But if I ssh to the same server from another computer (running Red Hat) everything work well with no warning. So I guess there must be a problem in the configuration of my Ubuntu laptop. Or could this be a problem in the SUSE server?

I would greatly appreciate any help. Some diagnosis follow. 

Thanks in advance, Joaquin

The output of locale is:

LANG=en_SG.UTF-8
LC_CTYPE="en_SG.UTF-8"
LC_NUMERIC="en_SG.UTF-8"
LC_TIME="en_SG.UTF-8"
LC_COLLATE="en_SG.UTF-8"
LC_MONETARY="en_SG.UTF-8"
LC_MESSAGES="en_SG.UTF-8"
LC_PAPER="en_SG.UTF-8"
LC_NAME="en_SG.UTF-8"
LC_ADDRESS="en_SG.UTF-8"
LC_TELEPHONE="en_SG.UTF-8"
LC_MEASUREMENT="en_SG.UTF-8"
LC_IDENTIFICATION="en_SG.UTF-8"
LC_ALL=

I run dpkg-reconfigure locales and get the following

  en_AU.UTF-8... up-to-date
  en_BW.UTF-8... up-to-date
  en_CA.UTF-8... up-to-date
  en_DK.UTF-8... up-to-date
  en_GB.UTF-8... up-to-date
  en_HK.UTF-8... up-to-date
  en_IE.UTF-8... up-to-date
  en_IN.UTF-8... up-to-date
  en_NZ.UTF-8... up-to-date
  en_PH.UTF-8... up-to-date
  en_SG.UTF-8... up-to-date
  en_US.UTF-8... up-to-date
  en_ZA.UTF-8... up-to-date
  en_ZW.UTF-8... up-to-date
  es_AR.UTF-8... up-to-date
  es_BO.UTF-8... up-to-date
  es_CL.UTF-8... up-to-date
  es_CO.UTF-8... up-to-date
  es_CR.UTF-8... up-to-date
  es_DO.UTF-8... up-to-date
  es_EC.UTF-8... up-to-date
  es_ES.UTF-8... up-to-date
  es_GT.UTF-8... up-to-date
  es_HN.UTF-8... up-to-date
  es_MX.UTF-8... up-to-date
  es_NI.UTF-8... up-to-date
  es_PA.UTF-8... up-to-date
  es_PE.UTF-8... up-to-date
  es_PR.UTF-8... up-to-date
  es_PY.UTF-8... up-to-date
  es_SV.UTF-8... up-to-date
  es_US.UTF-8... up-to-date
  es_UY.UTF-8... up-to-date
  es_VE.UTF-8... up-to-date
Generation complete.

The output of apt-get install locales

Reading package lists... Done
Building dependency tree       
Reading state information... Done
locales is already the newest version.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.

---

### Post by adult swim on 2008-10-02
you seem to be more knowledgeable about the matter than me, but to forward X in ssh aren't you supposed to use ssh -Y ?

---

### Post by iponeverything on 2008-10-02
take a look at update-locale

here is the output of my locale -a

root@foo-laptop:/etc/modprobe.d# locale -a
C
en_AU.utf8
en_BW.utf8
en_CA.utf8
en_DK.utf8
en_GB.utf8
en_HK.utf8
en_IE.utf8
en_IN
en_NZ.utf8
en_PH.utf8
en_SG.utf8
en_US.utf8
en_ZA.utf8
en_ZW.utf8
POSIX

---

### Post by joacorapela on 2008-10-03
Thanks for your replies iponeverything and adult swim. 

The problem was not on my Ubuntu laptop but on the SUSE server. I just changed the locale in the server to the POSIX locale (by typing "export LANG=C") and I can run xdvi perfectly.

Cordially, Joaquin

---

