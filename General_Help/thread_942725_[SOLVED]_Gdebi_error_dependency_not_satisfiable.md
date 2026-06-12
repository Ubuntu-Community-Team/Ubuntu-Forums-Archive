---
title: "[SOLVED] Gdebi error: dependency not satisfiable"
date: 2008-10-09
forum: General Help
---

### Post by timzak on 2008-10-09
I'm having an issue in Debian Etch-XFCE with installing Asunder (an audio ripper/encoder) from a .deb package.  

Seeing as this is a minimal XFCE install, I've been manually installing all packages as I need them.  I did not have gdebi installed, so I did install it first from Synaptic.  Then I downloaded the Asunder .deb file and double-clicked it.  It started to unpack the file before stopping with the message:

```
Error: Dependency is not satisfiable: libatk1.0-0
```

So I assumed libatk1.0-0 was not installed.  When I went into Synaptic to check, it shows that it is already installed in my system.

Any ideas on how to get Asunder installed?

Thank you.

---

### Post by timzak on 2008-11-05
Hi, I'm still having this same issue.  I recently tried installing Flash 10 .deb on this computer and got the same dependency error (libatk1.0-0).  So it's not just Asunder, it appears to be any .deb file I try to install will give me this dependency error.  As I said, I checked that libatk1.0 was installed, and according to Synaptic it is.  Any ideas why this is occuring?  The only thing I can think of is that since this is a minimal "ground up" install, there may be some other dependency issue that is being mis-reported as libatk1.0-0?

Any ideas greatly appreciated.

---

### Post by WelshChris on 2008-11-05
Tried to reinstall libatk using synaptic?  Which version libatk do you have?
Asunder requires >=1.2.0

---

### Post by timzak on 2008-11-06
> **WelshChris said:**
> Tried to reinstall libatk using synaptic?  Which version libatk do you have?
Asunder requires >=1.2.0

Hmmm...might Flash 10 also require >=1.2.0?

This system uses Debian Etch, and 1.0-0 is the highest version in Etch.

Is there a way to upgrade libatk without upgrading the whole system to Lenny?

Thank you.

---

### Post by timzak on 2008-11-11
I marked as solved since there doesn't appear to be any solution.  As I was scolded in the Debian forums for not knowing any better (so much for "the only dumb question is the one not asked"), Etch is by default a stable release, so upgrading or installing apps via gdebi is inconsistent with the whole concept of Etch.

---

### Post by xiongnu on 2010-11-18
> **timzak said:**
> I marked as solved since there doesn't appear to be any solution.  As I was scolded in the Debian forums for not knowing any better (so much for "the only dumb question is the one not asked"), Etch is by default a stable release, so upgrading or installing apps via gdebi is inconsistent with the whole concept of Etch.

i'm having the same problem as well.  just installed latest firefox web browser but couldn't play any youtube clips. Went ahead and Downloaded the latest adobe flash plugins but got this error msg.

any suggestions?

---

