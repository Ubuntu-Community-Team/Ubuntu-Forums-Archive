---
title: "installation problem in oracle 11 g plz help me out"
date: 2009-07-31
forum: Installation &amp; Upgrades
---

### Post by faizan_comsian on 2009-07-31
i follow the steps according to this link:[http://www.pythian.com/news/968/installing-oracle-11g-on-ubuntu-804-lts-hardy-heron](http://www.pythian.com/news/968/installing-oracle-11g-on-ubuntu-804-lts-hardy-heron)

but i am fail at step 9: by doing this... plz help me out

oracle@faizan-desktop:~/database$ ./runInstaller -ignoreSysPrereqs
Starting Oracle Universal Installer...

Checking Temp space: must be greater than 80 MB.   Actual 16890 MB    Passed
Checking swap space: must be greater than 150 MB.   Actual 1168 MB    Passed
Checking monitor: must be configured to display at least 256 colors
    >>> Could not execute auto check for display colors using command /usr/X11R6/bin/xdpyinfo. Check if the DISPLAY variable is set.    Failed <<<<

>>> Ignoring required pre-requisite failures. Continuing...

Preparing to launch Oracle Universal Installer from /tmp/OraInstall2009-07-31_04-24-41PM. Please wait ...[../stage/Components/oracle.jdk/1.5.0.1.1/1/DataFiles/jre.jar]
  End-of-central-directory signature not found.  Either this file is not
  a zipfile, or it constitutes one disk of a multi-part archive.  In the
  latter case the central directory and zipfile comment will be found on
  the last disk(s) of this archive.
note:  ../stage/Components/oracle.jdk/1.5.0.1.1/1/DataFiles/jre.jar may be a plain executable, not an archive
/tmp/OraInstall2009-07-31_04-24-41PM/jdk/lib/tools.jar  bad CRC 63b7f85f  (should be 8466ce83)

---

### Post by faizan_comsian on 2009-08-04
I got the solution of DISPLAY variable from this site [http://www.unix.com/unix-advanced-expert-users/69370-display-variable-erroring-when-installing-oracle-10g.html](http://www.unix.com/unix-advanced-expert-users/69370-display-variable-erroring-when-installing-oracle-10g.html)
and by the way CRC error is just because of crept  download

I JUST MADE THIS POST TO FOR OTHERS SO THEY MADE HABIT IF THEY GOT SOLUTIONS BY THERE OWN SO THEY POST HERE FOR OTHERS

---

