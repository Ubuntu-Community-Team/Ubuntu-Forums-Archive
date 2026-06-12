---
title: "Having a Difficult Time Trying to Upgrade to 9.04"
date: 2009-05-16
forum: Installation &amp; Upgrades
---

### Post by HorseSnot on 2009-05-16
When attempting to upgrade from 8.04 to 9.04, I get this error message:

E: dpkg was interrupted, you must manually run 'dpkg --configure -a' to correct the problem. 
E: _cache->open() failed, please report.

Okies, so I attempt via command line and it asks for superuser privileges, for some reason I'm getting authentication failure. Is there a way to reset the superuser passwd or should I just blow the whole OS away and reinstall? I'm not terribly concerned with any extraneous software I've downloaded, so it's no great loss if I have to do that.

Can someone offer some advice?

Thanks very much in advance!

---

### Post by taurus on 2009-05-16
You did include the sudo in front of the command, right?

```
**sudo** dpkg --configure -a
```
On the other hand, not sure if it's wise to skip a release, jumping from 8.04 to 9.04, by-passing 8.10.

8.04 -> 8.10 -> 9.04

---

### Post by sailthesea on 2009-05-16
> **HorseSnot said:**
> When attempting to upgrade from 8.04 to 9.04, I get this error message:

E: dpkg was interrupted, you must manually run 'dpkg --configure -a' to correct the problem. 
E: _cache->open() failed, please report.

Okies, so I attempt via command line and it asks for superuser privileges, for some reason I'm getting authentication failure. Is there a way to reset the superuser passwd or should I just blow the whole OS away and reinstall? I'm not terribly concerned with any extraneous software I've downloaded, so it's no great loss if I have to do that.

Can someone offer some advice?

Thanks very much in advance!
 
If you put sudo dpkg --configure -a in the CLI and it refused your password you gotta  get the right one or reinstall Check your Cap Lock!

---

### Post by HorseSnot on 2009-05-16
Ok. It was an operator error: me! I did not include sudo before the command! Arf! Heck, just a newb! 

Thanks so much!:KS

---

