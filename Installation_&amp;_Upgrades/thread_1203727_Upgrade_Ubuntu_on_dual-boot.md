---
title: "Upgrade Ubuntu on dual-boot"
date: 2009-07-03
forum: Installation &amp; Upgrades
---

### Post by jichun on 2009-07-03
I have a laptop with dual boot of Windows XP and Ubuntu 8.0.4.. I'd like to upgrade to Ubuntu 9.0.4 without affecting the Windows XP.

What is the easiest way to achieve that?

Thanks.

---

### Post by Sub101 on 2009-07-03
You can either upgrade using the update manager.

Or you can do a fresh install after downloading 9.04 to a disc. So long as you manually select the partitions you want to use when installing you shouldnt have a problem. In general it is best to do a fresh install however it will delete files from the partitions you select to use.

---

### Post by Hobgoblin on 2009-07-03
You have 2 options.

Upgrade to 8.10 then upgrade again to 9.04 (via the update manager) this will keep all your files and settings from your Ubuntu install but upgrading can cause problems in some cases.

Since you are on the LTS version of Ubuntu you'll need to change the "show new distribution releases" option (under the updates tab of software sources) to "normal releases".

Or

Make a fresh install of Ubuntu 9.04, selecting the manual partitioning option and telling it to use your current Ubuntu partition, with the mount point of / and check the format box.

---

### Post by raymondh on 2009-07-03
[https://help.ubuntu.com/community/UpgradeNotes](https://help.ubuntu.com/community/UpgradeNotes)
[https://help.ubuntu.com/community/IntrepidUpgrades](https://help.ubuntu.com/community/IntrepidUpgrades)
[http://www.ubuntu.com/getubuntu/releasenotes/904](http://www.ubuntu.com/getubuntu/releasenotes/904)
[http://www.ubuntu.com/getubuntu/upgrading](http://www.ubuntu.com/getubuntu/upgrading)

Upgrading versions from 8.04 to 8.10 (as well as updating 8.10) and then upgrading to 9.04 does take time.

I prefer to do a fresh install (as other have mentioned).... Making sure I format the appropriate partition. And since I have a /home, I make sure to use it but NOT FORMAT it (/home).

Before upgrading (either thru the network or thru a clean install).....

1. **Back up your files**.  There are no guarantees.
2. **Burn a liveCD of 9.04 and test it out**, checking how it reacts/relates to your system specs.  It is, after all, a good indicator of things to come.

Good luck.

---

### Post by jichun on 2009-07-04
Thank you all for the replies.

I personally don't mind a clean reinstall. My concern is what is going to happen to the 8.0.4. After the re-installation of 9.0.4 in the partition where 8.0.4 currently occupies, and when the computer boots up, is the selection of 8.0.4 going to go away?

---

### Post by earthpigg on 2009-07-04
yes, if you install 9.04 over the 8.04 partition then you will lose 8.04.

you can make _**another**_ partition, if you really want to, and install ubuntu there.

boot from live ubuntu cd -> applications -> accessories -> terminal and run 'gparted'

resize an existing partition and create another wherever you have the space to do so... then you can have windows, 8.04, and 9.04 all at once.

---

### Post by earthpigg on 2009-07-04
(not editing my existing post to make sure you see this)

ensure you backup _**anything you care about**_ before you do **_anything_** with partitions.

---

