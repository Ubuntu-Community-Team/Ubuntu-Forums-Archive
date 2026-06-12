---
title: "Brasero seems to lockup ans stuck in a loop"
date: 2008-08-24
forum: General Help
---

### Post by yamawho on 2008-08-24
I was using Brasero in Mint 4 but since I switched to Hardy, it is slow and if I try to burn a dvd compilation, it just hangs and doesn't burn. I am able to create a dvd when I right click but I wonder is my Brasero broken ?

---

### Post by TenPlus1 on 2008-08-24
Try downloading and installing the latest version of Brasero from [www.getdeb.net](www.getdeb.net) and see if that's any better...

---

### Post by yamawho on 2008-08-24
Thanks for the link.
I did the dl of the current version but when I tried to install I got a message that this version was already installed.

I installed K3b and got the following message on startup;

System locale charset is ANSI_X3.4-1968
Your system's locale charset (i.e. the charset used to encode filenames) is set to ANSI_X3.4-1968. It is highly unlikely that this has been done intentionally. Most likely the locale is not set at all. An invalid setting will result in problems when creating data projects.
Solution: To properly set the locale charset make sure the LC_* environment variables are set. Normally the distribution setup tools take care of this.

Could this be the root of my issue ?

How do I fix it ?

---

### Post by yamawho on 2008-08-24
I looked in etc/default/local and found this;

LANG="C"

---

### Post by yamawho on 2008-08-27
Anyone ...

---

### Post by Artemis3 on 2008-08-30
I just had this problem after upgrading brasero 0.8.0 to 0.8.1... First it crashes, then it claims it can't lock the drive -_-

What i did was rm ~/.config/brasero and ~/.gconf/apps/brasero rebooted and it worked again.

---

### Post by exploder on 2008-08-30
I have problems burning DVD iso files, it produces an error nearly every time. Burning a CD iso does not produce an error. Even though burning a DVD iso gives me an error, the burned disk is fine!

I have installed Brasero 0.8.1 and the problem is still present. I think the issue is gvfs related somehow.

---

