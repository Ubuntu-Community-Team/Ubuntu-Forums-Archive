---
title: "RPM Package and Subpackage"
date: 2009-10-16
forum: Installation &amp; Upgrades
---

### Post by Beavis111 on 2009-10-16
I'm trying to install an RPM package that contains subpackages.

I converted the .rpm package to a .deb package using Alien.
I installed the .deb package successfully.

After investigation it was found that the installation only installed the master package. None of the subpackages were installed. (ex: The .h files that were supposed to be installed by one of the subpackages do not exist on the system).

Do I have to install every one of the subpackages manually?

Your help is appreciated, thanks in advance..

---

### Post by Mark Phelps on 2009-10-17
I have personally found the alien convert-rpm-to-deb function to be of limited use. This is made harder because the .deb packaged library components sometimes have different names than the .rpm-packaged components.

So basically, the answer is yes -- you'll have to work through the dependency resolution yourself.

---

