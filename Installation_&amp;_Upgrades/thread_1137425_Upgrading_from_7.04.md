---
title: "Upgrading from 7.04"
date: 2009-04-25
forum: Installation &amp; Upgrades
---

### Post by LinuxNewb56 on 2009-04-25
Hello all
 
So Im pretty new to linux, I understand the basic commands and I have to upgrade my servers to 8.04. I have 1 and 7.04 and 1 and 7.10. Im trying to upgrade the one at 7.04 and I was able to download and update all of the old updates from the old repositories. I was then able to install the update-manager-core.
 
However when I try to run the command do-release-upgrade i get the following errors.
 
# do-release-upgrade
Checking for a new ubuntu release
Failed Upgrade tool signature
Failed Upgrade tool
Done downloading
extracting '/tmp/tmpQPspbm/gutsy.tar.gz'
Traceback (most recent call last):
File "/usr/bin/do-release-upgrade", line 45, in <module>
fetcher.run()
File "/usr/lib/python2.5/site-packages/UpdateManager/Core/DistUpgradeFetcherCore.py", line 160, in run
if not self.extractDistUpgrader():
File "/usr/lib/python2.5/site-packages/UpdateManager/Core/DistUpgradeFetcherCore.py", line 98, in extractDistUpgrader
tar = tarfile.open(self.tmpdir+"/"+os.path.basename(self.uri),"r")
File "/usr/lib/python2.5/tarfile.py", line 1139, in open
return func(name, "r", fileobj)
File "/usr/lib/python2.5/tarfile.py", line 1200, in gzopen
fileobj = file(name, mode + "b")
IOError: [Errno 2] No such file or directory: '/tmp/tmpQPspbm/gutsy.tar.gz'
 
 
Can anyone help please?

---

### Post by LinuxNewb56 on 2009-04-27
Its been a couple of days and I was wondering if anyone out there had any ideas on this please?

---

