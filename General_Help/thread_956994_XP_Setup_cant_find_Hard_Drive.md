---
title: "XP Setup cant find Hard Drive?"
date: 2008-10-23
forum: General Help
---

### Post by blootek on 2008-10-23
OK, I have Ubuntu 8.04 install and I want to dual boot with windows XP.
I tried installing XP over Ubuntu so I could just install Ubuntu again after XP is installed. The main point of this is so I can play games off of XP. I tried using wine but I cant get it to work with WoW properly or with AoC. Other games work decently but I would just rather play them off of XP. When I try to install XP I get a error message saying that the setup cant find my hard drive...I read a forum saying to set my primary boot to my cd drive, I did this nothing different happened. I also looked in to setting my hard drive to Compatibility mode but there is a message on the side saying something like "compatibility mode disable if device with exclamation." this message not really making much sense to me I gave up and now am posting here...I have am fairly frustrated at this point because I have never had this problem before and don't know what to do...any help would be greatly appreciated. I am obviously a noob to Ubuntu, that is why I would like to keep it as dual boot so when im not playing games I can use it and become better acquainted with how it operates. feelin pretty dumb right now...

---

### Post by jerome1232 on 2008-10-23
Is your drive a Sata disk? If so then XP doesn't have the Sata drivers built into it, and as you've already found on another forum one work around is to set your drive to 'ide' or 'compatibility' mode. Another workaround is to download the driver from you motherboard's or Sata Controller's manufactures website, put it on a floppy disk and hit 'f6' when the installer asks if you have any additional drivers you need (it's flashes on the bottom of the screen during the initial start up sequence for the XP installation)

---

### Post by blootek on 2008-10-23
Alright, I will work on this...thanks for the reply was starting to think no body was going to lol. This is the second time you have helped me, props to you sir.

---

### Post by jerome1232 on 2008-10-23
Glad to help, I don't know if your aware of this, when but you do get XP installed it's going to nuke grub out of existence making Windows the only bootable OS (don't worry there's an easy fix to get it dual booting)

It's outlined here at the top of the page [https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows](https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows)

good luck (The only reason I know about the sata thing is I have to do this for xp on all of my computers)

---

