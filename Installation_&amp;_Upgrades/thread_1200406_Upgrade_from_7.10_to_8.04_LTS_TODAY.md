---
title: "Upgrade from 7.10 to 8.04 LTS TODAY"
date: 2009-06-30
forum: Installation &amp; Upgrades
---

### Post by Poleh on 2009-06-30
Hi folks

seems a silly question and I did some digging on the forums but couldn't find anything to help. It was kind of odd, as I always go no results when searching for terms like "Upgrade from 7.10 to 8.04" etc. Even when clicking the "Check if already posted" button here, it gave me no results ...

I currently have 7.10 installed on a server, and want to upgrade it to 8.04 LTS to continue maintaining a secure and up-to-date server.

Obviously now there are releases beyond 8.04, so my question is, will performing the steps as recommended here:
[https://help.ubuntu.com/community/HardyUpgrades#Network](https://help.ubuntu.com/community/HardyUpgrades#Network) Upgrade from 7.10 for Ubuntu Servers (Recommended)

By doing this:
sudo apt-get install update-manager-core
sudo do-release-upgrade

upgrade me to 8.04, or will it suck down the latest release? If it gets the latest, is my only option to do an offline update with an ISO image?

Thanks in advance, 2 years on from my Windows server and loving it in Unbuntu land ...


[edit]
So I took a punt, changed all the "Gutsy" instances in the sources list to "Hardy" and performed the sudo do-release-upgrade and it all worked perfectly and only took 12 minutes. Linux is so awesome!

---

### Post by mikewhatever on 2009-06-30
Can you post the output of **cat /etc/lsb-release**. I really doubt an upgrade can be completed in as little as 12 minutes.

---

### Post by Poleh on 2009-06-30
```
duncan@web1:~$ cat /etc/lsb-release
DISTRIB_ID=Ubuntu
DISTRIB_RELEASE=8.04
DISTRIB_CODENAME=hardy
DISTRIB_DESCRIPTION="Ubuntu 8.04.2"
```


:) To be fair I should state it's a Dual Xeon 3.2GHz, 4GB RAM box with a 10Mb connection to a local mirror ...

---

### Post by mscoxoh on 2009-07-19
> **Poleh said:**
> 
:) To be fair I should state it's a Dual Xeon 3.2GHz, 4GB RAM box with a 10Mb connection to a local mirror ...

Thanks for the tip. I just did the same process from a Core 2 Duo 2.20GHz with 1gb RAM and a (typically) 7-8mbps Time Warner cable connection to the internet and it took maybe 20 minutes. Pretty flippin' sweet!

---

