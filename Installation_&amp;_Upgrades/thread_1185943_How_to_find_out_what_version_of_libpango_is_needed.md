---
title: "How to find out what version of libpango is needed by flash"
date: 2009-06-12
forum: Installation &amp; Upgrades
---

### Post by ninetails on 2009-06-12
I'm trying to install the newest version of flash.  I downloaded the .deb file from adobe's website, but when I run it, I get the following:

Error: Dependency is not satisfiable: libpango1.0-0

I checked in Synaptic Package Manager, and it says I have 1.20.1-1 installed, and it says that this is the latest version.  However, this might not be correct, since I'm getting the dependency error.  There might be a newer version that is required.  How do I find out which version exactly this package requires?

---

### Post by mc4man on 2009-06-12
From the control file for adobe flash
>  libpango1.0-0 (>= 1.20.[COLOR="Red"]5)[/COLOR]

What version of ubuntu are you using? (1.20.1-1 is fairly old, gutsy or before or a rc of hardy

> pango1.0 (1.20.1-1) unstable; urgency=low

  * New upstream bugfix release.

 -- Sebastian Dröge <slomo@debian.org> [COLOR="Blue"] Wed, 09 Apr 2008[/COLOR] 07:43:17 +0200


---

### Post by ninetails on 2009-06-13
How do you look at the control file? I'm using Ubuntu 8.04, Hardy Heron.

---

### Post by mc4man on 2009-06-13
If you have 8.04 then you haven't updated it to any extent (if at all) since you installed or more likely upgraded to it.

If you wish to install flash or even keep 8.04  I'd do so,  (System -> Admin. -> Software Sources -> Updates and enable the first 2 (security and updates), then close and reload

I'd also ck. here to see if non hardy sources are still enabled

```
 cat /etc/apt/sources.list
```

> How do you look at the control file


In this case i downloaded the adobe installer .deb (save rather than install) and opened it with the archive manager (right click) and 'browsed' to the control file and opened in a text editor.
(just a series of d. left clicks


Edit; just saw your other post, if you intend to upgrade to 9.04 I'd update 8.04 fully first

---

