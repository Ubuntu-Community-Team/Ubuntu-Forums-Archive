---
title: "How to upgrade from 8.04 to 9.04"
date: 2009-08-11
forum: Installation &amp; Upgrades
---

### Post by deBALZAC on 2009-08-11
The Update Manager only says my sys is already up to date.

Also I've tried the following command lines:
```

update-manager -c
``````
 
sudo aptitude update && sudo aptitude -s safe-upgrade
  
sudo aptitude -y safe-upgrade
  
sudo aptitude install update-manager-core
sudo do-release-upgrade
```But still all I got are messages telling me my sys is Already up to date, so I was wondering what do I have to do so my update manager will recognize the new sys 9.04 version?

---

### Post by overdrank on 2009-08-11
[JauntyUpgrades]("https://help.ubuntu.com/community/JauntyUpgrades")
> You can only directly upgrade to Ubuntu 9.04 from Ubuntu 8.10

---

### Post by Cope57 on 2009-08-11
8.04 is a Long Term Support distribution (LTS) and will be supported until April 2011. Upgrading is not ideal for some people and they may require a more stable system. In April 2010, another LTS distribution will become available. This will be the Ubuntu 10.04 LTS version.
I am sure in April 2010, there will be a tutorial for upgrading 8.04 to 10.04.

If you would like to be in the every 6 month upgrade process, install a non LTS version.

---

### Post by deBALZAC on 2009-08-11
> **Cope57 said:**
> 8.04 is a Long Term Support distribution (LTS) and will be supported until April 2011. Upgrading is not ideal for some people and they may require a more stable system. In April 2010, another LTS distribution will become available. This will be the Ubuntu 10.04 LTS version.
I am sure in April 2010, there will be a tutorial for upgrading 8.04 to 10.04.

If you would like to be in the every 6 month upgrade process, install a non LTS version.

So it means I don't need to upgrade to 9.04 only for security purposes? Is my PC secure with an 8.04 totally up to date?

---

### Post by p2bc on 2009-08-11
Yes your system is secure, as for right now, until the long term support lasts.

**No need to upgrade for security reasons**. 

Now, you **don't have to upgrade** to 9.04 **unless you want the new features** that 9.04 offers, that would be the only reason right now you would have to upgrade to 9.04

---

### Post by raymondh on 2009-08-11
> **deBALZAC said:**
> So it means I don't need to upgrade to 9.04 only for security purposes? Is my PC secure with an 8.04 totally up to date?

Unless you have any need/desire to try out a non-LTS version, Hardy is a good version with support.   Even if you want to test out the new versions, you could always try its' liveCD or, even virtualize them within Hardy.

Yes, you are up-to-date, it seems.

---

