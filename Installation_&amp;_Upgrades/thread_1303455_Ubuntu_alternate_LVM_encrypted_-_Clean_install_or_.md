---
title: "Ubuntu alternate LVM encrypted - Clean install or upgrade"
date: 2009-10-28
forum: Installation &amp; Upgrades
---

### Post by tellapu on 2009-10-28
Hi there!
I read through a lot of interesting threads about clean install or upgrade, but haven't read yet about this specific question:

I have installed Ubuntu alternate LVM encrypted 09.04 Jaunty on my computer. What would be the best way to go?
Clean install or upgrade?

To add some more specific question: ;)
Clean install: Is a harddisk-formating and whole new installation required/recommended (loosing all the LVM partitioning and more) or can a clean install be done/recommended within the encrypted LVM?
Would it be worth to wait till 10.04 LTS and then do a clean install from scratch? Or would be an upgrade then easier (with a clean install of 09.10) as ext4 and GRUB2 are already introduced in Karmic 09.10?

Thanks for your insight in advance. :popcorn:

---

### Post by tellapu on 2009-10-29
Any thought or even personal experience already would be appreciated. :roll:

---

### Post by Nather on 2009-10-30
Hiya tellapu,

there's a bug preventing Koala to detect encrypted harddisks, if they were created with an older version of cryptsetup than 1.0.7. Jaunty uses version 1.0.6, which does not remove old filesystem signatures from the superblock upon creation of the encrypted partition.

Since you've used the Jaunty to encrypt your partitions, you are most likely to be affected by this. And if you've got your root-partition encrypted, you will most likely not  be able to boot after upgrading to Koala.  

This [link]("https://bugs.launchpad.net/ubuntu/+source/cryptsetup/+bug/428435") has a more precise description of the bug.

If you've already upgraded to Koala and got hit by the bug, then there is a solution described in message [#32]("https://bugs.launchpad.net/ubuntu/+source/cryptsetup/+bug/428435/comments/32") and [#24]("https://bugs.launchpad.net/ubuntu/+source/cryptsetup/+bug/428435/comments/24"). But be warned. You will have to run a script to fix the superblocks of your partitions and  will have to choose which signature to keep. Choosing the wrong one will most likely result in a complete dataloss of the partition. So, if possible, backup your data before running the script.


Concerning ext4: There is possibly a bug that can corrupt large files. Here's a [link]("http://www.ubuntu.com/getubuntu/releasenotes/910#Possible%20corruption%20of%20large%20files%20with%20ext4%20filesystem").

So altogether I'd say, do a backup if you want to risk the upgrade and do a backup even if you don't. ;) And to stay away from ext4 until the corruption-issue is cleared. 


Hope this helps. :)


Addendum: Looks like the signature-issue got fixed.

---

### Post by tellapu on 2009-10-31
Hey Nather, you deserved your first bean. :-({|=

The possible bug that can corrupt large files is quiet critical for me as well. So probably I wait a bit and see what happens. Perhaps only make an upgrade first.

Thanks!

---

### Post by Nather on 2009-11-01
If your filesystems are ext3 and you do the upgrade to Karmic, then they will still be ext3. So it should be safe to do the upgrade... Unless Murphy strikes and the updater crashes, leaving the system in a semi-configured state (like it did for me -.-). Luckily I had a backup. ^^

---

### Post by tellapu on 2009-11-01
Thanks for that! Good you had a backup!! What sort of backup did you make? Using which program(s)?

---

