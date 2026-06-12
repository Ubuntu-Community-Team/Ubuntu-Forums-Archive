---
title: "Dual boot help"
date: 2008-10-23
forum: General Help
---

### Post by blootek on 2008-10-23
OK, I have Ubuntu 8.04 install and I want to dual boot with windows XP. 
I tried installing XP over Ubuntu so I could just install Ubuntu again after XP is installed. The main point of this is so I can play games off of XP. I tried using wine but I cant get it to work with WoW properly or with AoC. Other games work decently but I would just rather play them off of XP. When I try to install XP I get a error message saying that the setup cant find my hard drive...I read a forum saying to set my primary boot to my cd drive, I did this nothing different happened. I also looked in to setting my hard drive to Compatibility mode but there is a message on the side saying something like "compatibility mode disable if device with exclamation." this message not really making much sense to me I gave up and now am posting here...I have am fairly frustrated at this point because I have never had this problem before and don't know what to do...any help would be greatly appreciated. I am obviously a noob to Ubuntu, that is why I would like to keep it as dual boot so when im not playing games I can use it and become better acquainted with how it operates. :lolflag:feelin pretty dumb right now...:confused:

---

### Post by logos34 on 2008-10-24
if you have a SATA disk check the bios settings--should be set to IDE legacy mode.  Unlike Vista, XP doesn't have native drivers for Sata EHCI mode, it can only run in pata emulation mode.  Just a guess

---

