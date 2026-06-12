---
title: "What versions of packages to use?(aiming for stability)"
date: 2008-10-02
forum: General Help
---

### Post by Serguei_89 on 2008-10-02
Hello

Here is my story:
I installed Debian the other day, and saw that many packages are from several years ago and 10 version numbers back. I thought that's wonderful because these packages have obviously been tested for a long time.

I unfortunately went back to Linux Mint(which is basically Ubuntu) because I rely on proprietary wireless driver, which I couldn't easily figure out in Debian.

But my question is this: How to take this kind of Debian Approach in Ubuntu? Like for example tell Ubuntu to only use packages that Debian repositories consider stable? 

I like how Linux Mint introduced levels of stability to updates and you can choose to only update things approved by Mint developers. Ubuntu uses a lot of cutting edge stuff I don't necessarily need.

What should I do to choose stable packages?

---

### Post by whizbaby on 2008-10-02
> **Serguei_89 said:**
> 
What should I do to choose stable packages?
Stick with the LTS releases. If hardy is changing too fast for you use dapper until its expired(06/2009 for the Desktop I believe), hardy should have 'stabilized' by then. All non-lts releases are not supported for a long time (18 month) and therefore not appropriate if you dont want much changes on a regular basis in your system.

---

### Post by drs305 on 2008-10-02
> **Serguei_89 said:**
> 
What should I do to choose stable packages?


The ubuntu repositories have the ability to do what you want in a bit of a roundabout method. Open synaptic and click on Settings, Repositories. In the 'Ubuntu Software' section are tick boxes for packages officially supported by the ubuntu maintainers. The packages in this section should have a good deal of stability and have been extensively tested before being placed in the official repositories.

In the Updates section,  hardy-security should definitely be checked, as these updates deal directly with security issues. The hardy-updates are generally also 'safe' bets in that they have been tested by the ubuntu maintainers and found to be compatible with the current release.

Hardy-proposed are still being evaluated and have not yet received the 'official' seal of approval. It doesn't mean they won't work well - in many cases they will. However there may still be integration or other issues which the ubuntu team has not yet resolved or have yet to investigate. Think of these as versions the ubuntu team considers 'beta' in that they haven't fully committed to the packages. This is not to say the packages themselves are beta - they are often the package's latest stable release *in the opinion of the developer*. The developer may not have tested the package in ubuntu.

The hardy-backports repositories are unsupported future versions of packages which have not yet received extensive testing.

If you are happy with what you have, only receive the security updates. For normal users, you should be safe accepting the recommended (remember, they are listed as '*recommended*') packages..

Anyone asking the questions you have been asking should probably stay away from the 'proposed' and 'backports' updates.

---

### Post by Serguei_89 on 2008-10-02
Thanks for the replies. 2 Follow up things:

What if a fresh install of Ubuntu, which as I understand is only ubuntu-supported applications, is unstable at times on my hardware or for some packages.

And second thing is, does your advice about the ubuntu-supported repos apply to the universe and multiverse packages? Like say I want to install amarok or vlc. Some versions of those are more stable than others? How to work around that?

---

### Post by drs305 on 2008-10-02
> **Serguei_89 said:**
> Thanks for the replies. 2 Follow up things:

What if a fresh install of Ubuntu, which as I understand is only ubuntu-supported applications, is unstable at times on my hardware or for some packages.

And second thing is, does your advice about the ubuntu-supported repos apply to the universe and multiverse packages? Like say I want to install amarok or vlc. Some versions of those are more stable than others? How to work around that?

The synaptic repositories display only one version of a package.  If you find one that is unstable on your system, you can open synaptic, highlight the package and then from the menu select 'Package', 'Force Version'. If synaptic is aware of other (older) versions, you can select an older version. 

You can also do an internet search for an older (or newer) deb package which you think will do better. If you install it properly (say with Gdebi) it will be registered and you can 'lock' the version in synaptic so the version won't be updated. Highlight the package and then in the menu select "Package", "Lock Version" so that the package won't be updated via automatic updates. If you don't do that, you can also choose not to upgrade a package by unchecking it when the Update Manager shows the packages about to be downloaded and updated.

Lots of users update things like gimp, googleearth or vlc to newer versions not in the repositories. Do a search to see if people are having problems with a newer version before installing an external deb package.  If it's newer and it shows up in the synaptic list once you have installed it by other means, synaptic won't try to overwrite it with an older version.

---

