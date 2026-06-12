---
title: "Power failure during CUPS update install"
date: 2008-10-19
forum: General Help
---

### Post by yoozrname on 2008-10-19
After downloading some updates via Update Manager, specifically:

cupsys Version 1.3.7-1ubuntu3.1
cupsys-bsd Version 1.3.7-1ubuntu3.1
cupsys-client Version 1.3.7-1ubuntu3.1
cupsys-common Version 1.3.7-1ubuntu3.1
libcupsimage2 Version 1.3.7-1ubuntu3.1
libcupsys2 Version 1.3.7-1ubuntu3.1

the installer went about doing it's thing, during which there was a sudden power outage. This is when my pc shut off leaving everything in an unknown state.

After successfully rebooting to the desktop and launching Update Manager I made an attempt to continue the installs, after which I received an error message as follows:

E: dpkg was interrupted, you must manually run 'dpkg --configure -a' to correct the problem. 
E: _cache->open() failed, please report.

So I SUDO'd "dpkg --configure -a" only to get an error message as follows:

dpkg: parse error, in file `/var/lib/dpkg/updates/0001' near line 1:
 newline in field name `padding'

Now I didn't understand the second part of the first error message so I just left that alone. As for the second error message, I have no idea what that is implying.

I have no idea which, if any of these installs went through successfully or not prior to the power outage as I am relatively new to Linux and command line stuff.

Basically, I wish to get this sorted out so as to have Update Manager be able to finish dealing with this and continue to detecting the next available ones. But as it is, I get the same error message every time I click "Install".

Any help I could get involving delving into the depths of the system to correct things to the way they should be in a concise, noob kind of way will be much appreciated.

Any specific additional info can be made available.

Thanks

---

