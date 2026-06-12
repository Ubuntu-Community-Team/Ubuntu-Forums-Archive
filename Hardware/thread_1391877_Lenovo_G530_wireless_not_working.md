---
title: "Lenovo G530 wireless not working"
date: 2010-01-27
forum: Hardware
---

### Post by b1lancer on 2010-01-27
Hello,

[LEFT]I've just installed Ubuntu 9.10 on my girlfriend's computer, but (embarrassingly after singing praise of Ubuntu) the wireless is not working. I've had this problem before in a Dell after a fresh install. Any suggestions?? (She's glaring at me!!) #-o
[/LEFT]

Thanks!!

---

### Post by mörgæs on 2010-01-28
[https://help.ubuntu.com/community/WifiDocs/WirelessTroubleShootingGuide](https://help.ubuntu.com/community/WifiDocs/WirelessTroubleShootingGuide)

Let us know if she gives you a proper reward :-)

---

### Post by b1lancer on 2010-01-30
Ok. I really need some help here.

I went to the broadcom website. I found that they have a file that using the terminal, can install drivers and activate the wireless networking.

It worked. But when I restart the machine, it goes away!! I tried doing the process again, but this time placing the drivers inside /usr/lib/ directory, thinking that it won't be affected. The files are still there... but the wireless is still not recognized!

After following broadcom's instructions, the wireless WAS WORKING perfectly. As soon as I restarted, it went away! 

Please, I've been trying to find a resolution for this now for a couple days. The laptop is using a Broadcom 4312 wireless chip.

---

### Post by Idefix82 on 2010-01-30
What is the name of the driver? Maybe the driver is not loaded at startup. To test it, do
```
sudo modprobe drivername
```
substituting the correct name for the module with the driver. If wireless starts working after that, then you can make it permanent By typing in
```
echo "drivername" | sudo tee -a /etc/modules
```,
again replacing drivername by the correct name (but leaving the inverted comas).

---

