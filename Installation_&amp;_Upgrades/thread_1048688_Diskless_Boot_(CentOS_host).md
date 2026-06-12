---
title: "Diskless Boot (CentOS host)"
date: 2009-01-23
forum: Installation &amp; Upgrades
---

### Post by mitchell2345 on 2009-01-23
Hi,

I would like to try out ubuntu on my diskless frontend for MythTV.  Currently I have CentOS set up as diskless boot and works great.  I have heard good things about ubuntu and also want to use Boxee Alpha.

I have rsynced over my entire install (expcept /proc and /sys. 

When i run system-config-netboot as root I get this error:

/bin/cp: cannot stat `/tmp/tv/video/diskless/i386/ubuntu/root/etc/rc.d/functions': no such file or directory.

When looking int /etc/ I dont have a rc.d folder:
[myth@mythtv etc]$ ls |grep rc
bash.bashrc
inputrc
nanorc
rc0.d
rc1.d
rc2.d
rc3.d
rc4.d
rc5.d
rc6.d
rc.local
rc.readonly
rcS.d
screenrc
wgetrc
[myth@mythtv etc]$ 

I assume this is a diff between deb and RH.  Is there some folder i can sym link to so the RH netboot script works?

Thanks,
Mitchell

---

### Post by mitchell2345 on 2009-01-24
well i have made some progress.  I gave up on the system-config-netboot and started manually configuring as per this guide:

[https://help.ubuntu.com/community/DisklessUbuntuHowto](https://help.ubuntu.com/community/DisklessUbuntuHowto)

I get my PXE to start loading but get the attached error on my test vm and actual client.

Any ideas?

Thanks,
Mitchell

---

