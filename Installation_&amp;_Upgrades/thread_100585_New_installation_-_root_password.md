---
title: "New installation - root password?"
date: 2005-12-07
forum: Installation &amp; Upgrades
---

### Post by ubie_newbie on 2005-12-07
I apologize in advance for the stupidity of this request, but in trying to add some software (Yahoo Messenger), I apparently need to login as 'root', but having only just today completed the install, I recall setting up my user account, but not being asked (or told) what the password for root is.  I tried things I would normally have used if a password was requested, no luck.

Any suggestions (except for "don't be stupid" ... lol) would be appreciated

---

### Post by Digitallysick on 2005-12-07
have you typed in at the command prompt sudo
and then the pass you made up for your username?

---

### Post by aysiu on 2005-12-07
Assuming you downloaded it to your desktop ```
cd Desktop
sudo dpkg -i ymessenger_0.99.17-1_i386.deb
``` Ubuntu doesn't have a root account or a root password. For why, read this: [https://wiki.ubuntu.com/RootSudo](https://wiki.ubuntu.com/RootSudo)

---

### Post by ubie_newbie on 2005-12-07
Yahoo page indicated that install should be done by 'root'.  Tried(unsuccessfully) to login as that user.  Tried the install syntax from a terminal window under my made-up personal user and pwd.  That was when the Yahoo installer told me that I needed to login as a 'superuser' for the unpackaging and installation to proceed.

I should have added that I'm an aging OpenVMS bigot, really have never spent any time on ANY *nix variants, and worst of all, didn't supervise the entire install, so it MIGHT have displayed the root password and I just missed it (was latest build btw -- Breezy Badger)

---

### Post by ubie_newbie on 2005-12-07
While I was submitting the additional (useless) information, the needed answer about sudo was posted, and I DID read it.

Thanks all for the instantaneous assistance.  Guess I better RTFM next time -- hope to get at least a LITTLE smarter.

Sorry for the 'woh-duh' question and thanks again

---

