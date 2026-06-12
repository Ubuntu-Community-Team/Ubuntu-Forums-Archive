---
title: "[SOLVED] change default paper size"
date: 2008-08-13
forum: Hardware
---

### Post by roel46 on 2008-08-13
Hoi allemaal,

I setup my system with US defaults. Therefor my default paper size is US letter. My printer (hp photosmart d5160) uses paper size a4 so I want to adapt the system default paper size. I failed: applications (e.g. firefox) seem not to listen to my actions. Here is the list of unsuccessful atttempts to change the default paper size:

[LIST=1]
[*]System > Administration > Printing > Printer Options: Media Size: A4 (replacing Letter).
[*]at the login screen: choose a language where the environment has a4 as a default e.g. English (UK)
[*]add the following lines to "/etc/environment" and reboot afterwards:
> 
LANG="en_GB.UTF-8"
LC_PAPER="en_GB.UTF-8"

[*]edit /etc/papersize and replace "letter" by "a4" and reboot 
[/LIST]

After being so unsuccessful I asked my system some questions:
[LIST]
[*]from a terminal (shell):
> 
$ grep DefaultPageSize /etc/cups/ppd/*.ppd
/etc/cups/ppd/PDF.ppd:*DefaultPageSize: A4
/etc/cups/ppd/Photosmart_D5100_series.ppd:*DefaultPageSize: A4

[*]install and run PrintingBugInfoScript (from the UbuntuPrintingTeam?) as described at [https://wiki.ubuntu.com/PrintingBugInfoScript](https://wiki.ubuntu.com/PrintingBugInfoScript)
[*]note: some interesting output lines of that script:
```

CupsConfiguredPPDs:
 PDF: Generic PDF file generator
 Photosmart_D5100_series: HP PhotoSmart D5100 Foomatic/hpijs, hpijs 2.8.2
Date: Wed Aug 13 23:46:36 2008
DesktopEnvironment: GNOME
DistroRelease: Ubuntu 8.04
EtcPapersize: a4
Locale: LANG=en_GB.UTF-8, LC_CTYPE=en_GB.UTF-8, LC_PAPER=en_GB.UTF-8
Uname: Linux elro 2.6.24-19-generic #1 SMP Fri Jul 11 23:41:49 UTC 2008 i686 GNU/Linux

```
[/LIST]

My question: how can I change the system wide paper size to a4?

Thank you for reading this long story, groeten, Roel.

---

### Post by roel46 on 2008-08-15
solution for my problem found on Dutch forum:
[LIST=1]
[*]system wide default page size was well set as described before
[*]firefox doesn't listen to the system wide default page, it listens to its own settings. These can be viewed and changed via "about:config":
[LIST]
[*]search line "print.postscript.paper_size"
[*]and set to "a4" (via right click > modify)
[/LIST]
[/LIST]
thanks for all contributions, roel.

---

### Post by jarondl on 2010-12-27
Thanks!
Finally.. Goodbye "Letter"!

---

### Post by rpremuz on 2012-12-26
This issue also exists on Ubuntu 12.04 with Mozilla Firefox 17 and Thunderbird 17.

As already mentioned a workaround is to change the value of **print.postscript.paper_size** setting.

[LIST]
[*]In **Firefox**:
[LIST]
[*]open [about:config]("about:config") in the address bar
[/LIST]
while in **Thunderbird**:
[LIST]
[*]go to Edit -> Preferences -> Advanced -> General tab -> Config Editor
[/LIST]
[*]Search for **print.postscript.paper_size**
[*]Doubleclick the preference to change its value and enter **iso_a4** (which defines that default paper size is A4 as defined by [ISO 216 standard]("https://en.wikipedia.org/wiki/ISO_216")).
[/LIST]

**For advanced users:**

The user preferences are saved in the following plain text files:
[LIST]
[*]For Firefox:
~/.mozilla/firefox/Profiles/*profileID*.default/prefs.js
[*]For Thunderbird:
~/.thunderbird/*profileID*.default/prefs.js
[/LIST]

I was also able to set this setting system wide by adding the following line in **/etc/firefox/syspref.js** (for Firefox) and in **/etc/thunderbird/syspref.js** (for Thunderbird):

pref("print.postscript.paper_size", "iso_a4");

Note that if a setting is set both in the system wide configuration and user preferences, the later prevails.

---

