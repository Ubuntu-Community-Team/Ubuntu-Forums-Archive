---
title: "How to delete old version"
date: 2009-10-02
forum: Installation &amp; Upgrades
---

### Post by mgmyers on 2009-10-02
I recently upgraded to a newer Ubuntu and chose to install the new version without deleting the old one just yet.  It seems a partition was created.  I really like the newer version:P, except that my documents etc were not transferred from the old one as promised.:(  

After retrieving those documents, I would like to delete the old version and regain the harddrive space.  As it is, with the old version taking up space, there is no room for me to download updates for the newer version.

How do I get the old version out and only have the one OS installed?  BTW, I can manually choose on install which version to boot.  Unfortunately I'm given eight or ten choices instead of the expected two.

Thanks for any help.

---

### Post by tuahaa on 2009-10-02
You need to format the old version (I think)

What you do is open Gparted in your new version, and then select the partition which contains your old version and unmount (if not already done) and then format it.

I just got rid of my old Linux Mint partition a few minutes ago like this. 

Good luck. And don't get rid of the partition unless you know  it contains your old version. Then you can resize your current partition ising a live CD of Gparted, or you can just use a LiveCD of any other distro

---

