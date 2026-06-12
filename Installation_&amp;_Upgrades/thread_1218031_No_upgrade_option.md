---
title: "No upgrade option"
date: 2009-07-20
forum: Installation &amp; Upgrades
---

### Post by lesmorton on 2009-07-20
I am running Ubuntu 8.04 on my Toshiba NB100, I would like to upgrade to 9.04 and understand that I need to upgrade to 8.10 first.  I would like to upgrade online using the Update Manager but I don't get offered an upgrade to 8.10.  I have launched Software Sources but only have three tabs - Updates, Third Party Software and Authentication.  No Upgrade tab.

I have searched the forums and Googled my problem but can't seem to find a solution - can anyone out there assist please?:confused:

Many thanks.

---

### Post by kostkon on 2009-07-20
Check [this]("http://www.ubuntugeek.com/upgrade-ubuntu-804-hardy-heron-to-ubuntu-810-intrepid-ibix.html").

---

### Post by wojox on 2009-07-20
When your in software sources look under automatic updates and Release upgrade show Normal Releases then close.

Hit Alt+F2 for run application and enter:

update-manager -c -d

Click Run

Click the Check update button to check for new updates you should see something letting you know there is a new distribution release.

---

### Post by lesmorton on 2009-07-20
The tutorial shows an Upgrade tab in Software Sources - that's what I don't get on my system.

---

### Post by lesmorton on 2009-07-20
> **wojox said:**
> When your in software sources look under automatic updates and Release upgrade show Normal Releases then close.

Hit Alt+F2 for run application and enter:

update-manager -c -d

Click Run

Click the Check update button to check for new updates you should see something letting you know there is a new distribution release.

In Software Sources, under Automatic updates I don't get a Release upgrade option.  Al I have is Check for updates (with a drop down showing daily, Every two days, etc.), a radio button next to Download all updates in the background, and a radio button (which is highlighted) next to Only notify about available updates.

I've run the Update Manager is suggested above, but again nothing about Ugrade or new distribution release.  

My 8.04 system is bang up to date with all updates done.

---

### Post by wojox on 2009-07-20
> **lesmorton said:**
> In Software Sources, under Automatic updates I don't get a Release upgrade option.  Al I have is Check for updates (with a drop down showing daily, Every two days, etc.), a radio button next to Download all updates in the background, and a radio button (which is highlighted) next to Only notify about available updates.


Under that you don't have a

 Release upgrade

  Show new distribution releases

That weird maybe its because your using an LTS.

---

### Post by lesmorton on 2009-07-20
I'm using the Ubuntu that was pre-installed on the netbook when I bought it.

---

### Post by wojox on 2009-07-20
Here's the link I found:

[https://help.ubuntu.com/community/IntrepidUpgrades](https://help.ubuntu.com/community/IntrepidUpgrades)

---

### Post by lesmorton on 2009-07-20
In step 2 (Software Sources) it's the Updates tab that's different.  I only have Check for updates (with a drop down showing daily, Every two days, etc.), a radio button next to Download all updates in the background, and a radio button (which is highlighted) next to Only notify about available updates.  I don't have all the other options which relate to security updates and release upgrades.

---

### Post by lesmorton on 2009-07-20
If I download and install 9.04 Netbook Remix using a Flash drive I assume it will overwrite 8.04?  If I backup my home directory first can I assume I can reload it from a back copy on another flash drive to bring back all my previous settings into 9.04?

---

