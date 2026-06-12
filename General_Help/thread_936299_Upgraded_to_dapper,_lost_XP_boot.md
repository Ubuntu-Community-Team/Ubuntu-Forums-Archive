---
title: "Upgraded to dapper, lost XP boot"
date: 2008-10-02
forum: General Help
---

### Post by JediSange on 2008-10-02
Hey, I recently built my own computer and have been dual-booting Windows XP Pro and Ubuntu.  I recently decided to start using Ubunut to do my JAVA Programming in with eclipse.  So I'm coding away and realize the JAVA5 that Ubuntu comes with doesn't have the scanner class, so I go to update to Java6.

I google around and find these sites:

[http://ubuntuforums.org/showthread.php?t=317000](http://ubuntuforums.org/showthread.php?t=317000)
[http://ubuntuguide.org/wiki/Dapper#How_to_upgrade_from_Hoary_Hedgehog_-.3E_Breezy_Badger_-.3E_Dapper_Drake](http://ubuntuguide.org/wiki/Dapper#How_to_upgrade_from_Hoary_Hedgehog_-.3E_Breezy_Badger_-.3E_Dapper_Drake)

So anyways I follow the instructions on the second page and upgrade to dapper.  My friends had told me to do that anyways.  I then reboot my PC and notice that my XP boot is gone.  How can this be fixed?  Thanks.

---

### Post by JediSange on 2008-10-02
These forums move fast, so sorry to bump =\  I could really use some help with this.

---

### Post by Surkow on 2008-10-02
I assume the partition is still there? Then you only need to add a boot option for Windows XP to grub (to /boot/grub/menu.lst). The menu.lst file contains information what to add to be able to boot Windows.

---

### Post by Ryadt on 2008-10-02
You won't get anything to work properly in Dapper cause it is no longer supported. You will have to upgrade to Hardy.

---

### Post by JediSange on 2008-10-02
haha... that's funny... I had Hardy.  My friends are idiots.

---

### Post by Ryadt on 2008-10-02
How did you upgrade to dapper???:confused::confused::confused:
Can you post the output of ```
lsb_release -a
```

---

### Post by JediSange on 2008-10-02
Well thankfully I saved a copy of my hardy sources.list (referring to below)

/etc/apt/sources.list

As far as what I did to "downgrade" I guess to dapper I just followed the directions in my second link  ([http://ubuntuguide.org/wiki/Dapper#How_to_upgrade_from_Hoary_Hedgehog_-.3E_Breezy_Badger_-.3E_Dapper_Drake](http://ubuntuguide.org/wiki/Dapper#How_to_upgrade_from_Hoary_Hedgehog_-.3E_Breezy_Badger_-.3E_Dapper_Drake)) then ran the update/upgrade/dist-upgrade.

Anyways, I replaced the sources.list with the hardy one and ran them again.  I think I have fixed the problems that were there.  As far as the output of lsb_release -a it looks like this:

No LSB modules are available.
Distributor ID:	Ubuntu
Description:	Ubuntu 8.04.1
Release:	8.04
Codename:	hardy

---

### Post by Ryadt on 2008-10-02
You could not have downgraded to Dapper. It's impossible.
You can't downgrade to any version.

---

### Post by JediSange on 2008-10-02
Well I literally followed the instructions in my second link, and ran update... and it messed up my PC.  I don't know exactly what happened, but I think I fixed it... so I'm good haha.  Thanks for the help, just needed the boot loader.

---

