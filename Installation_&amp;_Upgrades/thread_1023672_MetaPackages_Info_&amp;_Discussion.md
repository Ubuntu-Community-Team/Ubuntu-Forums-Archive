---
title: "MetaPackages Info &amp; Discussion"
date: 2008-12-28
forum: Installation &amp; Upgrades
---

### Post by jerremy-tamlin on 2008-12-28
I have started this thread in response to the Wiki article [_[COLOR="DarkRed"]MetaPackages[/COLOR]_]("https://help.ubuntu.com/community/MetaPackages") where there was some contention regarding these packages being "recommended not to be removed"

Here is my two cents...

I like Aptitudes ability to mark packages as being either Manually or Automatically installed. In a previous install earlier this year I lost track of what programs/applications I had installed and was certain there must have been many that I didn't use but that weren't in my Applications menu. So now having reinstalled (Kubuntu this time) using the alternate-CD I wanted to use aptitude to keep track of what I had installed...

However, I quickly ran into a problem. Many of my packages were already marked Manually installed including certain linux-headers-2.6.24-19 & linux-headers-2.6.24-19-generic which had already been replaced by linux-headers-2.6.24-22 & linux-headers-2.6.24-22-generic but not removed. I can only assume this was because they were marked Manually Installed.

So commenced a process of trial and error discovering which meta-packages I could mark as manual that would enable everything else to be kept. This was an almost clean install, having only been using it for about two weeks.

**_Here are my results:_**
_linux-generic_        *You need a linux kernal!*
_ubuntu-standard_ & _ubuntu-minimal_        *I Needed Both*
_kubuntu-desktop_ & _kdebase_        *I Needed Both*
_language-pack-en_        *Replace en with your language if not english*
_language-pack-kde-en_        *If you use kde you need this too, probably something similar for gnome.*
_openoffice.org_        *Unless you don't want it*
_firefox-2_        *Or other browser you want. If you use konqueror thats included in both the kubuntu packages*
_installation-report_        *This keeps a log of your installation and can help when sending bug reports.*
_kubuntu-restricted-extras_        *If you want them*

Marking all other packages as Auto made aptitude automatically remove linux-headers-2.6.24-19 & linux-headers-2.6.24-19-generic and allowed all my other programs to remain based on the dependency of these meta-packages.

Now if I install anything else it will be marked as manual and I'll be able to do a simple search ```
aptitude search '!~M~i'
``` and see what programs I have installed. :D


Regarding the "recommended not to be removed" question. I think this is most likely because when distributions are upgraded the maintainers can easily change the dependency of these meta-packages to the new distribution and your system will know that there is a new distribution that it can be upgraded to. Not at all sure if this is how it actually happens though it's just my speculation.

Have a great day and I hope this info is useful.
Please add to it.
Cheers :P

---

### Post by stderr on 2008-12-28
Interesting info; I may have a play around later myself to see what I can simplify :) Cheers for posting.

---

### Post by Murene on 2009-11-14
[https://help.ubuntu.com/community/MetaPackages](https://help.ubuntu.com/community/MetaPackages) referred me to this page to discuss, so I'm sorry to reply to such an old thread.

I've searched google to find the difference between "linux-generic" and "linux-image-generic" and couldn't find a satisfying answer.

[quote=[https://help.ubuntu.com/community/MetaPackages](https://help.ubuntu.com/community/MetaPackages)]
**Kernel Metapackages**

 These metapackages install the latest linux kernel and modules through a series of dependencies. These make upgrading the kernel much easier, and safer, since they ensure that all required modules and headers are also installed. 

[LIST]
[*]**linux-generic**: Always depends on the latest generic Linux kernel available.
[*]**linux-headers-generic**: This package always depends on the latest generic kernel headers available.
[*]**linux-image-generic**: This package always depends on the latest generic kernel image available.
[*]**linux-restricted-modules-generic**: This package always depends on the latest restricted modules available for generic kernels.
[/LIST]
[/quote]
It might make sense to add the real difference between "linux-generic" and "linux-image-generic" so people know what to choose when using the mini installer (netinst). 

What's the difference between "generic kernel image" and "generic linux kernel"? Is one preferred over the other?

---

### Post by chienpo on 2010-08-16
I've got a question about the following point made on the MetaPackages page: [https://help.ubuntu.com/community/MetaPackages](https://help.ubuntu.com/community/MetaPackages)

> A metapackage, such as **ubuntu-minimal** or **ubuntu-desktop**,  can have a long list of dependencies.  So, when a metapackage is  automatically removed by the removal or purging of any one, or more, of  its underlying dependencies, all of the other packages that were in the  metapackage's depends list are still installed on the system.  If at a  later time, there is an upgrade to the metapackage, the upgrade cannot  occur, because the metapackage to be upgraded is no longer installed on  the system.So, say I remove the **ubuntu-minimal** meta-package by purging one of its dependencies from my system:

```

$ sudo apt-get purge ntpdate
Reading package lists... Done
Building dependency tree
Reading state information... Done
The following packages will be REMOVED:
  ntpdate* ubuntu-minimal*
0 upgraded, 0 newly installed, 2 to removed and 2 not upgraded.
After this operation, 311kB disk space will be freed.
Do you want to continue [Y/n]? y
(Reading database ... 30032 files and directories currently installed.)
Removing ubuntu-minimal ...
Removing ntpdate ...
Purging configuration files for ntpdate ...

```Now I'll no longer get ugrades to the **ubuntu-minimal** package. That much is clear. However, just to clarify, I **will** still get upgrades to the other packages that were "part of" (dependencies of) the ubuntu-minimal meta-package (such as *sudo*, for instance) so long as they remain on my system, yes?

I've got a JeOS-based virtual machine running Ubuntu Server 10.04. The virtual host runs ntpd to keep the system clock up to date. As such, the virtual guests have no need to ever attempt to update the clock. However, my JeOS-based virtual guest unnecessarily includes ntpdate as it is part of the ubuntu-minimal meta-package. The ntpdate package installs /etc/network/if-up.d/ntpdate which tries to update the clock whenever the network is brought up.

This isn't a big deal but I want to nuke ntpdate on the VM guest image to be leaner, cleaner and correcter (yes, you may call me a worventor: a word inventor). This removes the ubuntu-minimal meta-package. I just want to be sure the other individual packages still installed (sudo, vim-tiny, rsyslog, python, etc) will get their individual security updates.

**Note:** I'm not worried about updates to the ubuntu-minimal package as a whole as I assume that updates to the meta-package simply includes changes to its meta-information such as its dependency list. This, in turn (still assuming) results in installation and removal (perhaps replacement) of other packages when "upgrading" the meta-package. I don't care about having such packages added or removed. I have no intent to upgrade this VM guest image off of 10.04. When 12.04 and/or 14.04 come out I'll just be re-creating a new, base VM guest image from scratch anyway. I don't see myself caring if someone decides package X should also be part of ubuntu-minimal on 10.04. If I don't need package X now, I won't need it later (and if I do I'll add it manually).

Anyhow, I'm interested in any correction, confirmation, and/or clarification anyone has to offer on this subject.

Thanks.

---

