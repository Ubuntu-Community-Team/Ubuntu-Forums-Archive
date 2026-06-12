---
title: "Issues with de-selecting updates"
date: 2009-06-12
forum: Installation &amp; Upgrades
---

### Post by Sambo_ on 2009-06-12
*System: Ubuntu 8.04 running under a VMWare Server v2 Virtual Machine.*

Hi,

When I run the Update Manager I get the following message:

'Not all updates can be installed.' 'Run a partial upgrade to install as many updates as possible' and the options to 'Partial Upgrade' or 'Close'.

I tried a 'Partial Upgrade' but it installed everything (I guess), including the latest version of Dan's Guardian which I don't want to install right now for various reasons.  So I recovered from backups (virtual disk) and tried 'Close' so that I could de-select the DG update and install the others.  However when I click 'Close', the updates are ghosted / greyed out and I can't unselect DG (or anything else for that matter).

Anyone have any ideas how I can get around this issue?  Any assistance would be greatly appreciated.

Cheers,

Sam.

---

### Post by Sambo_ on 2009-07-13
Anyone?  Any suggestions welcome!

---

### Post by ptn107 on 2009-07-13
Verify that your /etc/apt/sources.list file looks like this one (get rid of any non-official repositories):

_[http://ubuntu.pastebin.com/m56464172](http://ubuntu.pastebin.com/m56464172)_

and try again:
```
sudo aptitude update && sudo aptitude full-upgrade
```

---

### Post by Sambo_ on 2009-10-28
> **ptn107 said:**
> Verify that your /etc/apt/sources.list file looks like this one (get rid of any non-official repositories):

_[http://ubuntu.pastebin.com/m56464172](http://ubuntu.pastebin.com/m56464172)_
Is anyone able to re-post this information?  It seems to have expired or something and is no longer available.

Thanks :)

In any case, here are the un-commented lines of my sources.list file:
```
deb http://nz.archive.ubuntu.com/ubuntu/ hardy main restricted
deb http://nz.archive.ubuntu.com/ubuntu/ hardy-updates main restricted
deb http://nz.archive.ubuntu.com/ubuntu/ hardy universe
deb http://nz.archive.ubuntu.com/ubuntu/ hardy-updates universe
deb http://nz.archive.ubuntu.com/ubuntu/ hardy multiverse
deb http://nz.archive.ubuntu.com/ubuntu/ hardy-updates multiverse
deb http://security.ubuntu.com/ubuntu hardy-security main restricted
deb http://security.ubuntu.com/ubuntu hardy-security universe
deb http://security.ubuntu.com/ubuntu hardy-security multiverse
```
To my (untrained) eye, this all looks pretty standard to me...

---

