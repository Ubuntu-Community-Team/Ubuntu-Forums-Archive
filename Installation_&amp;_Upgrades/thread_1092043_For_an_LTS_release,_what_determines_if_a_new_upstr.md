---
title: "For an LTS release, what determines if a new upstream package will be made available?"
date: 2009-03-10
forum: Installation &amp; Upgrades
---

### Post by oryan_dunn on 2009-03-10
I am in the middle of trying to rebuild a package that has had many new upstream releases since 8.04, but hasn't been updated in the 8.04 repos yet ([http://ubuntuforums.org/showthread.php?t=1086634](http://ubuntuforums.org/showthread.php?t=1086634)).  The package in question is the nspluginwrapper.  However, I'm also interested in another upstream package, xsane.
[https://launchpad.net/ubuntu/hardy/+source/xsane/+changelog](https://launchpad.net/ubuntu/hardy/+source/xsane/+changelog)
[https://launchpad.net/ubuntu/hardy/+source/nspluginwrapper/+changelog](https://launchpad.net/ubuntu/hardy/+source/nspluginwrapper/+changelog)

Both list the new upstream releases, but I'd like them to be available for 8.04 as both fix several very annoying bugs (nspluginwrapper fixes the keyboard not being available in a plugin such as adobe reader, and xsane fixes the post scan window being forced into full screen when using compiz).

Would it be possible to just use the packages for intrepid or jaunty? I'm about 90% the way through rebuilding the nspluginwrapper to the same spec as the original 8.04 release, but it is quite time consuming.

---

### Post by Neo_The_User on 2009-03-10
The package maintainers choose. UGH! If Ubuntu was only a rolling distro...

---

### Post by oryan_dunn on 2009-03-10
> **Neo_The_User said:**
> The package maintainers choose. UGH! If Ubuntu was only a rolling distro...

I get it.  I could update, but everything else works just fine.  Why would I want to upgrade my entire system to fix a couple minor bugs, and bring on all the extra pain that involves?  It is just annoying when bug fix upstream updates are not included in the LTS release.

---

### Post by Neo_The_User on 2009-03-10
Have you tried arch linux?

---

### Post by oryan_dunn on 2009-03-10
> **Neo_The_User said:**
> Have you tried arch linux?


No, because 99.99% of my system is working perfectly with Ubuntu 8.04.  Again, why would I go to all the trouble of upgrading my entire OS just for a couple bug fixes?  I was under the impression that an LTS release would be supported with bug & security fixes for 3 years.  Perhaps I was misled?  When I'm done with my packages for nspluginwrapper and xsane, I'll figure out somewhere to host them so others (few though they may be) can easily update to a later package.

If you know of someone else who has already done this, I'll be glad to reuse their hard work.

---

### Post by Neo_The_User on 2009-03-10
Oh sorry. 8.04 only gets old crummy updates now. Its all old legacy stuff. I think 8.04 still uses Mesa 7.0.4 heh.

---

