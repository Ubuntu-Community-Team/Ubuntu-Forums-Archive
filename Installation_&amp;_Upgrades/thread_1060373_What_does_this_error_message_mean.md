---
title: "What does this error message mean?"
date: 2009-02-04
forum: Installation &amp; Upgrades
---

### Post by frankwakeman on 2009-02-04
When I run Update Manager, after it has seemed to look at, currently, 52 packages I get this message:

W: GPG error: [http://ppa.launchpad.net](http://ppa.launchpad.net) intrepid Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 60D11217247D1CFF


What does that mean, and how do I put it right?

Thanks.

---

### Post by Merovius on 2009-02-04
I've had the same for a week or two. What gives?

---

### Post by pauwl on 2009-02-05
You don't have the required keys installed to 'trust' the source.

If you trust the source:

Run from the terminal:
```

gpg --keyserver keyserver.ubuntu.com --recv-keys 60D11217247D1CFF

```
then
```

gpg --export --armor 60D11217247D1CFF | sudo apt-key add -

```

then happy camping.

---

### Post by frankwakeman on 2009-02-05
So it turns out that this is the people we got Open Office 3 from.  But after I'd downloaded OOo 3 I deleted this unofficial key, so it's a bit annoying trace has remained.

---

### Post by forger on 2009-02-06
[http://ubuntuforums.org/showthread.php?t=1056099](http://ubuntuforums.org/showthread.php?t=1056099)

---

