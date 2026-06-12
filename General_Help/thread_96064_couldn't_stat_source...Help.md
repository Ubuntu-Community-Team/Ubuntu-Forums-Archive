---
title: "couldn't stat source...Help"
date: 2005-11-28
forum: General Help
---

### Post by kmorsch on 2005-11-28
Everytime I try to install something or use apt-get update I get this message at the end:

W: Couldn't stat source package list [http://ubuntu-backports.mirrormax.net](http://ubuntu-backports.mirrormax.net) hoary-backports/universe Packages (/var/lib/apt/lists/ubuntu-backports.mirrormax.net_dists_hoary-backports_universe_binary-i386_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list [http://ubuntu-backports.mirrormax.net](http://ubuntu-backports.mirrormax.net) hoary-backports/multiverse Packages (/var/lib/apt/lists/ubuntu-backports.mirrormax.net_dists_hoary-backports_multiverse_binary-i386_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list [http://ubuntu-backports.mirrormax.net](http://ubuntu-backports.mirrormax.net) hoary-backports/restricted Packages (/var/lib/apt/lists/ubuntu-backports.mirrormax.net_dists_hoary-backports_restricted_binary-i386_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list [http://ubuntu-backports.mirrormax.net](http://ubuntu-backports.mirrormax.net) hoary-extras/restrict Packages (/var/lib/apt/lists/ubuntu-backports.mirrormax.net_dists_hoary-extras_restrict_binary-i386_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list [http://ubuntu-backports.mirrormax.net](http://ubuntu-backports.mirrormax.net) hoary-backports/main Packages (/var/lib/apt/lists/ubuntu-backports.mirrormax.net_dists_hoary-backports_main_binary-i386_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list [http://ubuntu-backports.mirrormax.net](http://ubuntu-backports.mirrormax.net) hoary-backports/universe Packages (/var/lib/apt/lists/ubuntu-backports.mirrormax.net_dists_hoary-backports_universe_binary-i386_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list [http://ubuntu-backports.mirrormax.net](http://ubuntu-backports.mirrormax.net) hoary-backports/multiverse Packages (/var/lib/apt/lists/ubuntu-backports.mirrormax.net_dists_hoary-backports_multiverse_binary-i386_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list [http://ubuntu-backports.mirrormax.net](http://ubuntu-backports.mirrormax.net) hoary-backports/restricted Packages (/var/lib/apt/lists/ubuntu-backports.mirrormax.net_dists_hoary-backports_restricted_binary-i386_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list [http://ubuntu-backports.mirrormax.net](http://ubuntu-backports.mirrormax.net) hoary-extras/restrict Packages (/var/lib/apt/lists/ubuntu-backports.mirrormax.net_dists_hoary-extras_restrict_binary-i386_Packages) - stat (2 No such file or directory)
W: You may want to run apt-get update to correct these problems
E: Some index files failed to download, they have been ignored, or old ones used instead.
root@c-24-22-98-143:~ #

what is wrong? How can I fix this?

---

### Post by wanger123 on 2005-11-28
There is obviously a problem with those backport repositories. If you just want to get rid of the error messages, you need to go to /etc/apt/sources.list and comment them out. Then save file and do apt-get update.

[EDIT] Are you sure that the url's are correct? There doesn't seem to be any packages in them. Maybe they are just focussing on Breezy now?

Cheers

wanger

---

### Post by Xian on 2005-11-28
Yeah, afaik the hoary backports are no longer supported.
Remove them from your sources list.

---

### Post by kmorsch on 2005-11-28
How do you remove them? I am new to Linux, like last week.

---

### Post by aysiu on 2005-11-28
See the first link in my sig.

---

### Post by marvlus on 2005-12-03
aysiu. 
  Thanks for this post.  You're a lifesaver!!

---

