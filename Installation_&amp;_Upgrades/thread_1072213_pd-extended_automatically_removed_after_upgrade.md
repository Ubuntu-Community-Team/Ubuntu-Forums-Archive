---
title: "pd-extended automatically removed after upgrade"
date: 2009-02-17
forum: Installation &amp; Upgrades
---

### Post by Jamesss on 2009-02-17
I just upgraded Ubuntu via Update Manager the other day and it automatically removed pd-extended. I re-installed pd-extended ([http://downloads.sourceforge.net/pure-data/Pd-0.40.3-extended-ubuntu-hardy-i386.deb](http://downloads.sourceforge.net/pure-data/Pd-0.40.3-extended-ubuntu-hardy-i386.deb)) afterwards and it installs and runs ok, but I get a message after installation that tells me to run "sudo apt-get install -f" which removes it again! I could ignore this command, but then I can't use Synaptic Package Manager or Update Manager! Is there some conflict with the latest Ubuntu distro and pd-extended? For now I installed pd (basic version) through Synaptic, but would really like to get pd-extended back. 

I am running:

kernel 2.6.24-23
Ubuntu 8.04 (Hardy)
Gnome 2.22.3
AMD Athlon XP 2400+
500MB ram

James

---

### Post by Jamesss on 2009-02-17
Ok well I figured I'd try upgrading to 8.10 and that seems to have fixed it. I can install pd-extended fine now

---

