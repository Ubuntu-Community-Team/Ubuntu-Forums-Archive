---
title: "Synaptic and network errors"
date: 2005-12-15
forum: Installation &amp; Upgrades
---

### Post by nimy on 2005-12-15
I recently upgraded from Hoary to Breezy on my laptop and get these errors when I try to check my repositories in the Synaptic package manager:
W: Couldn't stat source package list [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) breezy/main Packages (/var/lib/apt/lists/us.archive.ubuntu.com_ubuntu_dists_breezy_main_binary-i386_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) breezy/restricted Packages (/var/lib/apt/lists/us.archive.ubuntu.com_ubuntu_dists_breezy_restricted_binary-i386_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) breezy-updates/main Packages (/var/lib/apt/lists/us.archive.ubuntu.com_ubuntu_dists_breezy-updates_main_binary-i386_Packages) - stat (2 No such file or directory)

However, the repositories themselves look good in Synaptic's package manager: the CD, Breezy Badger, Updates and Security Updates are listed, matching my other ubuntu client where all is ok, and my packages are up to date.
I checked /etc/apt/sources.list and see no errors - at one point I had added deb-src repositories but those have been commented out.  

I ran sudo apt-get update and had no trouble connecting, 709 kb of info was fetched, but sudo apt-get install checked the packages/dependency tree but installed nothing, so I assume that the synaptic gui already took care of that. 

Another error I have on this laptop client which may be related to this, but I have no idea: /etc/init.d/inetd is missing, plus of course other networking files under /etc/init.d like ssh, and dig of course doesn't work.  I tried reloading dnsutils, no difference.  So I can't run services to connect it to my local network.  What to do?

---

### Post by mlomker on 2005-12-15
I'm not sure.  You're welcome to try [my sources.list]("http://mail3.mpr.org/mlomker/sources.list") if you wish.

---

### Post by mendy on 2005-12-26
Thank you so much.
I read your reply and tried your list, and I don't get any more of the errors.

---

