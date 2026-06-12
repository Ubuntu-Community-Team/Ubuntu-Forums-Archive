---
title: "Feisty upgrade not working?"
date: 2009-06-11
forum: Installation &amp; Upgrades
---

### Post by dannyboy79 on 2009-06-11
I am way behind on upgrading. I am now trying to upgrade my Feisty install to  the next release and then the next release and so on until I get to Hardy Heron (the LTS release). Update-manager is giving me this error in a little window. Can anyone please help?

Could not find the release notes
The server may be overloaded. 

[[IMG]http://img3.imageshack.us/img3/9573/screenshotjxw.th.png[/IMG]](http://img3.imageshack.us/i/screenshotjxw.png/)

---

### Post by Partyboi2 on 2009-06-11
Hi, you will probably find it easier to backup your important stuff and do a clean install of a later version. Or you could have a look at
[https://help.ubuntu.com/community/EOLUpgrades](https://help.ubuntu.com/community/EOLUpgrades) but there is no guarantee that it would work.

---

### Post by Sef on 2009-06-11
**Back up** your **data** and do a clean install.   That would be the best way.

---

### Post by dannyboy79 on 2009-06-11
i don't want to have to reconfigure all my programs. like samba, ssh, ftp, mythtv etc etc. which is why I want to upgrade instead of install fresh. i'll check the above link. thank you.

---

### Post by dannyboy79 on 2009-06-11
> **Partyboi2 said:**
> Hi, you will probably find it easier to backup your important stuff and do a clean install of a later version. Or you could have a look at
[https://help.ubuntu.com/community/EOLUpgrades](https://help.ubuntu.com/community/EOLUpgrades) but there is no guarantee that it would work.

i am trying it and I already get an error. it states:
IOError: [Errno 2] No such file or directory: '/tmp/tmp6b8Ixq/gutsy.tar.gz'

any help please?

---

### Post by Therion on 2009-06-11
Is Feisty even supported any more?  Either way, doing that many dist-upgrades is just *begging* for problems.  

Dude, seriously... Suck it up and do a clean install.

---

### Post by drs305 on 2009-06-11
> **dannyboy79 said:**
> i don't want to have to reconfigure all my programs. like samba, ssh, ftp, mythtv etc etc. which is why I want to upgrade instead of install fresh. i'll check the above link. thank you.

You can make a separate /home partition then do the upgrade to keep most of your current configuration settings. You would need to make a separate partition, move your /home over to it, and then designate that partition as your /home during the clean install, making sure to select it as your /home and also NOT to format it during the partitioning portion of the install. 

Here is a link on making/moving to a separate /home:
[https://help.ubuntu.com/community/Partitioning/Home/Moving]("https://help.ubuntu.com/community/Partitioning/Home/Moving")

---

### Post by dannyboy79 on 2009-06-11
samba.conf, sshhd.conf and other config files aren't kept in your home directory. i'll just back up /etc/. i'll figure it out.

---

