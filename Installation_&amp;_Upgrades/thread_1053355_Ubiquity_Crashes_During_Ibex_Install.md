---
title: "Ubiquity Crashes During Ibex Install"
date: 2009-01-28
forum: Installation &amp; Upgrades
---

### Post by UltraAnders on 2009-01-28
Hi all,

Been trying to install Ibex from CD. I've verified the download and the burnt CD, plus tried installing a few times.

I reported the crash ([319351]("http://bugs.launchpad.net/bugs/319351")), and it was flagged as a duplicated of [298509]("https://bugs.launchpad.net/bugs/298509"). So I thought "great, lets see what they did" ... except I don't have permission to view this bug, and I can't seem to find it when I search for it? 

I'm hoping someone can give me a steer on the way forward, since I'm not even sure what error message to search on. Cheers!
```
ProblemType: Crash
Architecture: i386
DistroRelease: Ubuntu 8.10
ExecutablePath: /usr/lib/ubiquity/bin/ubiquity
InterpreterPath: /usr/bin/python2.5
Package: ubiquity 1.10.10
ProcAttrCurrent: unconfined
ProcCmdline: /usr/bin/python /usr/lib/ubiquity/bin/ubiquity gtk_ui
ProcEnviron: Error: [Errno 13] Permission denied: '/proc/8339/environ'
PythonArgs: ['/usr/lib/ubiquity/bin/ubiquity', 'gtk_ui']
SourcePackage: ubiquity
Title: ubiquity crashed with ValueError in command()
Uname: Linux 2.6.27-7-generic i686
```

---

### Post by utnubuuser on 2009-01-28
The only thing that comes to mind is to check your Bios.  In particular, look for HDD compatiblilty settings.
Not all machines have this, but some do, and I've read posts about crashing during the installation due to an incorrect BIOS setting.

---

### Post by UltraAnders on 2009-01-28
Thanks for the reply. I tried the text based alternate CD installer and to my surprise it worked! I'm writing this from my new Ibex install :)

---

