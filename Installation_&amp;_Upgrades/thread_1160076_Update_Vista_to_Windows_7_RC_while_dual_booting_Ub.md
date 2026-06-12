---
title: "Update Vista to Windows 7 RC while dual booting Ubuntu"
date: 2009-05-15
forum: Installation &amp; Upgrades
---

### Post by blackriven on 2009-05-15
Has anyone tried installing Windows 7 RC by upgrading Vista, as opposed to uninstalling it and installing Windows 7? I'm currently dual booting Vista Home with Ubuntu 9.04, and would like to give the Release Candidate of Windows 7 a try using its upgrade option, but I'm worried that there might be problems due to Grub being the boot loader. Has anyone tried this? Does it work?

---

### Post by coffeecat on 2009-05-15
Yes, I have. Yes, it does. Yes, you will have to reinstall Grub. :)

On my Sony laptop, first time round I imaged my Vista install and tried a fresh install of W7. It went well, but even after I downloaded some of the Sony Vaio firmware and software for my model I couldn't get all the special laptop hardware working. Even though everything worked out of the box with Jaunty! :lol: I could see that among the downloaded Sony stuff were a couple of registry hacks, so I restored Vista from my image, and did an upgrade install. For this you have to boot into Vista, insert the W7 install DVD and let it autorun. It saves (most of*) your settings and installed software, but takes about twice as long as a fresh install. There's a few rough patches but it's working quite well.

But, just to emphasise, the mbr **will** be overwritten with the Windows mbr, meaning that temporarily you won't be able to boot into Ubuntu, but otherwise your Linux partitions will be untouched. It's easy enough getting grub reinstalled to the mbr. There are plenty of guides around, but the easiest way is with [SuperGrubDisk]("http://www.supergrubdisk.org/") which, by the way, is also the easiest and quickest way of restoring the Windows mbr for anyone wanting to 'uninstall' Ubuntu.

Good luck!

* **Edit**: forgot to add - all my software installations were retained with the exception of AVG Free for some obscure reason. But I soon had that re-installed.

---

### Post by blackriven on 2009-05-15
Awesome! Thanks for the quick reply. 

Can you tell me how to image my Vista install?

---

### Post by coffeecat on 2009-05-15
In theory you could use Partimage or Clonezilla (I'll let you do the googling :wink: ) but I lost patience with Partimage when it refused to recognise my USB drive. Clonezilla is said to be good but its interface is a bit - um - basic. What I used was [the free version of Macrium Reflect]("http://www.macrium.com/reflectfree.asp"). I've done successful restores of both Vista and W7 images made with Macrium, so it does do what it says on the tin. The downside is that it is proprietary, but the free version does everything I want. The upside is that the boot CD for doing a restore is Linux-powered. :)

Before you do something irreversible I do suggest you try restoring a Macrium image onto a spare drive **and** boot up from this, just to reassure yourself that it does work. It does have a few foibles, one of which is that it won't restore to a partition smaller than the one it imaged even if the restored OS will easily fit into the new partition. There's probably a perfectly good reason for this, but some of its rivals don't have this limitation.

---

