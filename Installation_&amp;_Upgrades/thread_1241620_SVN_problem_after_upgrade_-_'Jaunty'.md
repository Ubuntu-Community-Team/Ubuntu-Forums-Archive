---
title: "SVN problem after upgrade - 'Jaunty'"
date: 2009-08-16
forum: Installation &amp; Upgrades
---

### Post by Milossh on 2009-08-16
Hello all,

For a week now I was getting an notice that I need to upgrade some packages, but that it cannot be done regularly, and that I need to partially upgrade them. I clicked partially upgrade, and it automatically removed my Subversion.

Now, when I try to install Subversion from repos, I get following errors:

```
abnormal@Eniac:/opt/www/amo$ sudo apt-get install subversion
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.
The following information may help to resolve the situation:

The following packages have unmet dependencies:
  subversion: Depends: libsvn1 (= 1.5.4dfsg1-1ubuntu2) but 1.5.4dfsg1-1ubuntu2.1 is to be installed
E: Broken packages

```What should I do?

P.S. Sorry for my bad English.

---

### Post by Partyboi2 on 2009-08-16
Hi, are you able to downgrade the libsvn1 package? You can do this by opening Synaptic (System>Admin>Synaptic) and searching for [FONT=monospace]'[/FONT]libsvn1' then highlighting it and go to Package>Force Version and see if you can downgrade to [FONT=monospace]'[/FONT]1.5.4dfsg1-1ubuntu2'

---

### Post by Milossh on 2009-08-16
Thanks man, this was pretty fast and accurate :)

Problem solved.

---

