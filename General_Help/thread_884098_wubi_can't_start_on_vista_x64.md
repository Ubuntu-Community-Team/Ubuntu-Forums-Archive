---
title: "wubi can't start on vista x64"
date: 2008-08-08
forum: General Help
---

### Post by Jhcho on 2008-08-08
Hi, guys. :KS
I am trying to test ubuntu in windows vista x64,
however, wubi-8.04.1-rev506 doesn't start properly. 
Can anybody help me?

cpu: intel core2 quad
ram: 3GB (<-Wubi log file writes "memory=-1025MB":confused:)
os: window vista x64

p.s. I've checked that wubi runs well in my another
window x86 system.
cpu: intel core2 dual
ram: 2GB
os: window vista x86

---

### Post by FXEF on 2008-08-09
I have posted a message on launchpad to see if wubi-8.04.1-rev506 is compatible with Vista 64bit, but so far no answer. What errors do you get?

---

### Post by Jhcho on 2008-08-11
> **FXEF said:**
> I have posted a message on launchpad to see if wubi-8.04.1-rev506 is compatible with Vista 64bit, but so far no answer. What errors do you get?

I got the message "Windows based Ubuntu Installer has stopped
working...". I don't know why this message comes out and 
why the installer even can't start.

Someone told that this problem "may" be solved by reinstalling
window vista, using new version of wubi, or unactivating the wireless network card, but I think it doesn't fit to my case.

Hmmm...

---

### Post by Jhcho on 2008-08-11
I've finally installed Ubuntu via wubi by changing
vista to use administator and making administator to run wubi.
I don't know why this solves the problem but only glimpse 
that it is related to vista's previlege control.
Anyway, I entered ubuntu's world. :KS

---

### Post by ago on 2008-08-11
Is this confirmed to happen on every Vista 64 bit? If there are other reports I will open a bug report.

---

### Post by Jhcho on 2008-08-11
:(> **Jhcho said:**
> I've finally installed Ubuntu via wubi by changing
vista to use administator and making administator to run wubi.
I don't know why this solves the problem but only glimpse 
that it is related to vista's previlege control.
Anyway, I entered ubuntu's world. :KS

Again, wubi does not work even when it is ran by administator. :(

---

### Post by FXEF on 2008-08-11
> **Jhcho said:**
> :(

Again, wubi does not work even when it is ran by administator. :(


In Vista you _must_ be running with Administrator privileges to install anything... doesn't matter, wubi or whatever. It is just not clear to me if the wubi installer with run under Vista 64 bit. 

Has anyone used wubi to successfully install Ubuntu in Vista 64 bit?

---

### Post by Jhcho on 2008-08-12
> **FXEF said:**
> In Vista you _must_ be running with Administrator privileges to install anything... doesn't matter, wubi or whatever. It is just not clear to me if the wubi installer with run under Vista 64 bit. 

Has anyone used wubi to successfully install Ubuntu in Vista 64 bit?

I gave up to find out why wubi didn't start occasionally.
I tried to turn off each service in vista and test wubi,
it was in vain. Finally, I reinstalled windows vista(x64).
Then, wubi and ubuntu work fine until now.
I will keep watching which services conflict to wubi.

p.s. 

If wubi is ran after ubuntu installed in a drive, say D,
it fails to find "\ubuntu" folder. So, I made a fake
folder "\ubuntu" in another drive, say C, it runs well.
I think it is a kind of bug.

---

### Post by joey-elijah on 2008-08-13
i have before.... =o \

I installed ubuntu via wubi on Vista Premium 64 on an AMD x 2 .... never had a problem... but then i didn't keep it long cos i was fed up of 64bit ubuntu

---

### Post by Akava on 2008-09-02
> **FXEF said:**
> *snip*
Has anyone used wubi to successfully install Ubuntu in Vista 64 bit?

Yes, I have. It installed just fine, no problems at all, worked fine for a while then I messed up the display drivers a little, and decided rather than fixing them I would just re-install.  However I had one HELL of a time trying to get it off.

I have Vista Business 64bit.

---

### Post by ago on 2008-09-03
> **Akava said:**
> However I had one HELL of a time trying to get it off.
[https://wiki.ubuntu.com/WubiGuide#Cannot%20uninstall%20Ubuntu](https://wiki.ubuntu.com/WubiGuide#Cannot%20uninstall%20Ubuntu)

---

### Post by ago on 2008-09-03
So it seems the problem is not specific of vista 64, there are occasional segfaults that are difficult to track but there is a new code base that should address such issues.

---

### Post by m0ar on 2009-08-07
Sup guys.


I've been trying to install Ubuntu via Wubi now, and it doesn't work at all.

I try to start by the icon, the small "wait"-thingie appears for a few seconds then NOTHING at all ;P

I run Vista Ultimate -64.

I had hope in this new technique but it screwed my trust over :c

---

