---
title: "Upgrade from 7.10 to 8.04 LTS"
date: 2009-08-25
forum: Installation &amp; Upgrades
---

### Post by Pierrot Lafouine on 2009-08-25
Hi Can I use Synaptic to upgrade now from 7.10 to 8.04 ?
(7.10 repository have been removed)

Or can I use ISO file I downloaded to upgrade ?
I guess so, but I had bad experience once with Windowz overwrote registry.

Thanks


Pierre

---

### Post by mikewhatever on 2009-08-25
Yes, it's about time to. The guide below also covers upgrading from cd. 
[https://help.ubuntu.com/community/HardyUpgrades](https://help.ubuntu.com/community/HardyUpgrades)

---

### Post by Pierrot Lafouine on 2009-08-26
How can I start update-manager, I don't have this menu (I don't know why, it used to be there, now it disappear)

---

### Post by Pierrot Lafouine on 2009-08-26
How can I start update-manager, I don't have this menu (I don't know why, it used to be there, now it disappear)

---

### Post by modorf on 2009-08-26
you can manually change your /etc/apt/sources.list file to point to hardy repository.  Then do an apt-get update, apt-get upgade, apt-get dist-upgrade.
This is the old debian way of doing upgrades.

Alternatively you can find the gutsy repositories at:
[http://old-releases.ubuntu.com/ubuntu/](http://old-releases.ubuntu.com/ubuntu/)

Update your /etc/apt/sources.list file to use the old-releases repository. And then follow the instruction sheet.

---

### Post by Pierrot Lafouine on 2009-08-26
> **modorf said:**
> you can manually change your /etc/apt/sources.list file to point to hardy repository.  Then do an apt-get update, apt-get upgade, apt-get dist-upgrade.
This is the old debian way of doing upgrades.

Alternatively you can find the gutsy repositories at:
[http://old-releases.ubuntu.com/ubuntu/](http://old-releases.ubuntu.com/ubuntu/)

Update your /etc/apt/sources.list file to use the old-releases repository. And then follow the instruction sheet.

Thanks for the hint,
Where is Hardy repo ?
This is what I have now in sources.list:

deb [http://ca.archive.ubuntu.com/ubuntu/](http://ca.archive.ubuntu.com/ubuntu/) gutsy-updates main restricted
etc...

---

### Post by Pierrot Lafouine on 2009-08-26
I made a find and replace, from gutsy to hardy, in source.list file
Then tried apt-get update
Didn't work... lol
Sorry, I will need more details
Thanks

---

### Post by Pierrot Lafouine on 2009-08-26
I just tried Alternate CD Downloaded here : [http://releases.ubuntu.com/hardy/ubuntu-8.04.3-alternate-i386.iso](http://releases.ubuntu.com/hardy/ubuntu-8.04.3-alternate-i386.iso))
During setup, it tells me that all data will be erased.
So it looks to me it's not an upgrade ISO file I downloaded.
Were can I find an update ISO file for 8.04 LTS ?

Thanks

---

### Post by Pierrot Lafouine on 2009-08-27
ok, my source.list file point to old-release.
I was able to install a SDL package I needed, but apt-get update generates error 404

How do I fix that to udate/upgrade to Hardy ?
Thanks

---

### Post by ptn107 on 2009-08-27
You need to put in the 8.04 alternate disk while ubuntu is running.  Don't boot from it.  A box will come up saying 'Upgrade volume detected: Would you like to try to upgrade from it automatically?'  Click the 'Run Upgrade' button and follow the prompts.

---

### Post by Pierrot Lafouine on 2009-08-28
Ok thanks, I'll give a try this week-end

---

