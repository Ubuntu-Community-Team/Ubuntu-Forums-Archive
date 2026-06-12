---
title: "I upgraded to Intrepid and now Bash + some KDE is in French?"
date: 2008-11-06
forum: General Help
---

### Post by DWRZ on 2008-11-06
So on Hardy I had English US as my main language, but also had Italian, French, and Chinese available. Upon upgrading to Ibex, bash started going in French as well as a few KDE things (apt, some notifications). What gives and how do I fix this? I checked /etc/environment and the locale seems right there. :(

---

### Post by DWRZ on 2008-11-07
Help, please? I still haven't been able to figure this out.

---

### Post by DWRZ on 2008-11-12
I've tried everything I can in system settings. 

Locale command produces the following:
LANG=en_US.UTF-8
LANGUAGE=fr
LC_CTYPE="en_US.UTF-8"
LC_NUMERIC="en_US.UTF-8"
LC_TIME="en_US.UTF-8"
LC_COLLATE="en_US.UTF-8"
LC_MONETARY="en_US.UTF-8"
LC_MESSAGES="en_US.UTF-8"
LC_PAPER="en_US.UTF-8"
LC_NAME="en_US.UTF-8"
LC_ADDRESS="en_US.UTF-8"
LC_TELEPHONE="en_US.UTF-8"
LC_MEASUREMENT="en_US.UTF-8"
LC_IDENTIFICATION="en_US.UTF-8"
LC_ALL=

Yet /etc/environment is:
PATH="/usr/local/sbin:/usr/local/bin:/usr/sbin:/usr/bin:/sbin:/bin:/usr/games"
LANGUAGE="en_US:en"
LANG="en_US.UTF-8"

Any ideas? I really need help.

---

