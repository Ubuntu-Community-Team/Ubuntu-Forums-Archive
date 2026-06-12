---
title: "Synaptic package manager"
date: 2008-12-23
forum: Installation &amp; Upgrades
---

### Post by DarkKnight445 on 2008-12-23
ok when I start the package manager press reload it starts downloading the updates and this pops up what do I do and this is UbuntuGEU



W: A error occurred during the signature verification. The repository is not updated and the previous index files will be used.GPG error: [http://greenie.sk](http://greenie.sk) hardy Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 6B2226D9969C86CA

W: Failed to fetch [http://greenie.sk/ubuntu/dists/hardy/Release](http://greenie.sk/ubuntu/dists/hardy/Release)  

W: Some index files failed to download, they have been ignored, or old ones used instead.

---

### Post by xjcannonx on 2008-12-23
I would try switching the server from where you download.

In SPM go to setting-->repositories and change it the main server.

See if this helps

---

### Post by clyde9999 on 2009-02-06
I am having the same problem with openGEU 8.04.1. It just has a missing key. Can anyone tell us how to obtain that missing key?

clyde9999

---

### Post by clyde9999 on 2009-02-06
> **clyde9999 said:**
> I am having the same problem with openGEU 8.04.1. It just has a missing key. Can anyone tell us how to obtain that missing key?

clyde9999

I found it.

[http://forum.intilinux.com/index.php?topic=728.0;wap2]("http://forum.intilinux.com/index.php?topic=728.0;wap2")

works fine! lasts long time!

clyde9999

---

### Post by dburnett77 on 2009-02-06
You imported from a previous install.  When you were running greenie, this site verified.  When the other install copied these settings, they don't recognize the system as valid.

In Synaptic, select "Settings...Repositories..." and make the appropriate changes.  Or, search for sources.list files and correct all of them.

Terminal command 'sudo apt-get update  ' with the right arguments will also correct this.  Run "man apt-get " for the list of parameters.

---

