---
title: "Peer Guardian/MoBlock"
date: 2009-05-18
forum: Installation &amp; Upgrades
---

### Post by khaos28 on 2009-05-18
So i went to the DL page for Peer Guardian and got and installed the PG .DEB version ([http://sourceforge.net/project/downloading.php?group_id=131687&filename=peerguardnf-1.5beta.i386.deb&a=90811190](http://sourceforge.net/project/downloading.php?group_id=131687&filename=peerguardnf-1.5beta.i386.deb&a=90811190)) and I'm not really sure where to go from there...is there a GUI i can interact with? update the IP lists? i'm kind of new to this, so any help would be greatly appreciated. 

Also if MoBlock is better then PG in your opinion please explain why?

Thanks.
Jake

Edit: Like how do i use it and get it to open?

Is there a sudo code that i can add into my terminal to make it Dl and Install better? when i Dl'ed the original time, i had some pre-installed app come up and do it for me, but idk what that all did.

---

### Post by jre on 2009-05-19
PG Linux isn't developed since 4 years. It has some bugs, so don't use it.

Use
moblock+blockcontrol+mobloquer or
nfblock+blockcontrol or
iplist

Basically they all do the same. If you installed blockcontrol read /usr/share/doc/blockcontrol/README.blocklists.gz to learn more about the blocklists. (You can use those from bluetack or TBG. Also habe a look at iblocklist.com which is a provider for all known blocklists. In blockcontrol I use TBG lists from iblocklist per default - but you can change them if you wish.

> **khaos28 said:**
> when i Dl'ed the original time, i had some pre-installed app come up and do it for me, but idk what that all did.

During the blockcontrol installation you were prompted some debconf questions. If you gave non-default answers then the changes are saved to /etc/blockcotnrol/blockcontrol.conf (except the selected blocklists which are saved in /etc/blockcotnrol/blocklists.list)

---

