---
title: "Upgrade Error From Ubuntu Server 8.10 to 9.04"
date: 2009-04-24
forum: Installation &amp; Upgrades
---

### Post by mlbarnes on 2009-04-24
I installed the update-manager-core package and installed the new version using do-release-upgrade. The install went off without any errors or inputting anything in the log files. It successfully finished and asked to reboot. When it rebooted I was no longer able to ssh in to the server. I went the server locally and noticed that not many of the processes started. SSHd started but I was not able to get a connection. I looked through the log files and found this error:

Apr 23 19:46:36 cora kernel: Cannot find map file.
Apr 23 19:46:36 cora kernel: No module symbols loaded - kernel modules not enabled. 

I have searched the web and found a few postings saying this was a known bug but it appeared to be for older versions of Ubuntu. I would appreciate any help with this. If you need any further information please feel free to ask. Thanks in advance.

---

### Post by mlbarnes on 2009-04-27
Nobody else has had this error? I would appreciate any help

---

