---
title: "English (UK) locale problem"
date: 2008-07-31
forum: General Help
---

### Post by Wise Ferret on 2008-07-31
On Hardy 32 bit, I am having the following trouble:

My system is set through Administration->Language support to support English and Hebrew, with default language set to English (United Kingdom).
I have some programs that fail to load from terminal. Running ccsm (compiz configuration), for example, returns:> (ccsm:9694): Gtk-WARNING **: Locale not supported by C library.
	Using the fallback 'C' locale.
Traceback (most recent call last):
  File "/usr/bin/ccsm", line 39, in <module>
    import ccm
  File "/usr/lib/python2.5/site-packages/ccm/__init__.py", line 1, in <module>
    from ccm.Conflicts import *
  File "/usr/lib/python2.5/site-packages/ccm/Conflicts.py", line 27, in <module>
    from ccm.Constants import *
  File "/usr/lib/python2.5/site-packages/ccm/Constants.py", line 92, in <module>
    locale.setlocale(locale.LC_ALL, "")
  File "/usr/lib/python2.5/locale.py", line 478, in setlocale
    return _setlocale(category, locale)
locale.Error: unsupported locale setting

I tried re-installing locales package, removing English support, rebooting, returning English support, rebooting, but to no avail.
Output of sudo dpkg-reconfigure locales returns:> perl: warning: Setting locale failed.
perl: warning: Please check that your locale settings:
	LANGUAGE = (unset),
	LC_ALL = "en_UK.UTF-8",
	LANG = "en_UK.UTF-8"
    are supported and installed on your system.
perl: warning: Falling back to the standard locale ("C").
locale: Cannot set LC_CTYPE to default locale: No such file or directory
locale: Cannot set LC_MESSAGES to default locale: No such file or directory
locale: Cannot set LC_ALL to default locale: No such file or directory
Generating locales...
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
  he_IL.UTF-8... up-to-date
Generation complete.

And running locale command returns:> locale: Cannot set LC_CTYPE to default locale: No such file or directory
locale: Cannot set LC_MESSAGES to default locale: No such file or directory
locale: Cannot set LC_ALL to default locale: No such file or directory
LANG=en_UK.UTF-8
LC_CTYPE="en_UK.UTF-8"
LC_NUMERIC="en_UK.UTF-8"
LC_TIME="en_UK.UTF-8"
LC_COLLATE="en_UK.UTF-8"
LC_MONETARY="en_UK.UTF-8"
LC_MESSAGES="en_UK.UTF-8"
LC_PAPER="en_UK.UTF-8"
LC_NAME="en_UK.UTF-8"
LC_ADDRESS="en_UK.UTF-8"
LC_TELEPHONE="en_UK.UTF-8"
LC_MEASUREMENT="en_UK.UTF-8"
LC_IDENTIFICATION="en_UK.UTF-8"
LC_ALL=en_UK.UTF-8

What is going on here? Is there any way to fix this? Can I supply any more data helping toward a solution?

---

### Post by Wise Ferret on 2008-08-01
Bumpity bumpity bump!

---

### Post by Wise Ferret on 2008-08-16
Any ideas? What should I re-instal/re-configure, and how?

---

### Post by Wise Ferret on 2008-09-06
Solved it!

The problem was my .bashrc file, which I edited in order to get English terminal output even when working with different locales.

It contained 

export LC_ALL=en_UK.UTF-8
export LANG=en_UK.UTF-8

Instead of

export LC_ALL=en_GB.UTF-8
export LANG=en_GB.UTF-8

Changing this back to the correct form fixed my problem.

---

