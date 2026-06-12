---
title: "Problem upgrading Ubuntu Server 7.04 to 8.04 LTS"
date: 2009-05-09
forum: Installation &amp; Upgrades
---

### Post by k31k0 on 2009-05-09
Hi.

I have finally found some time to upgrade my Ubuntu Server 7.04 to LTS version 8.04. I am trying to upgrade trough SSH connection and I'm getting the following warning:

```
root@my_domain:~# do-release-upgrade
Checking for a new ubuntu release
Done Upgrade tool signature
Done Upgrade tool
Done downloading
extracting '/tmp/tmpSdmap8/hardy.tar.gz'
authenticate '/tmp/tmpSdmap8/hardy.tar.gz' against '/tmp/tmpSdmap8/hardy.tar.gz.gpg'

&#268;itam spremnik

Provjeravam upravitelja paketima

Nastaviti rad pod SSHom?

This session appears to be running under ssh. It is not recommended
to perform a upgrade over ssh currently because in case of failure it
is harder to recover.

If you continue, a additional ssh daemon will be started at port
'9004'.
Do you want to continue?

Continue [yN] y

root@my_domain:~#
```

As you can see, my problem is that even when I answer "y" to the "Continue [yN]" question, the script still stops. I don't know why is that happening... Please help.

k3k10

---

### Post by Justcameron on 2009-12-24
I am having this problem also. Gutsy -> Hardy. English though...

Some more details: Ubuntu is a guest inside Windows Server 2008 hyper-v.

I run *sudo apt-get update* and [I]sudo apt-get upgrade
[/I]
This notes that:
[I]The following packages have been kept back:
  linux-headers-generic linux-image-generic linux-restricted-modules-generic
0 upgraded, 0 newly installed, 0 to remove and 3 not upgraded.[/I]

I edited grub's menu.lst to boot into kernel version 2.6.22-14-generic (because of the bug with 2.6.22-15-generic - see [https://help.ubuntu.com/community/HardyUpgrades#Known%20Problems](https://help.ubuntu.com/community/HardyUpgrades#Known%20Problems) )

and then rebooted into 2.6.22-14-generic to run the upgrade. 

and so it just quits on me after I press y and enter as above.

[I]cat /var/log/dist-upgrade/main.log
2009-12-25 00:26:18,622 INFO release-upgrader version '0.87.30' started
2009-12-25 00:26:18,629 DEBUG Using 'DistUpgradeViewText' view
2009-12-25 00:26:18,726 DEBUG enable dpkg --force-overwrite
2009-12-25 00:26:18,804 DEBUG lsb-release: 'gutsy'[/I]

---

### Post by Justcameron on 2009-12-24
I found a bug [https://bugs.launchpad.net/ubuntu/+source/update-manager-core/+bug/389388](https://bugs.launchpad.net/ubuntu/+source/update-manager-core/+bug/389388) which said that this can be worked around by changing your locale to C.

To do so, I edited /etc/environment, removing LANG="en_AU.UTF-8" and adding

LANGUAGE=C
LANG=C

at the start of the file, then restarting.

---

