---
title: "Wireless IPN2220 driver with XUbuntu 8.04"
date: 2008-06-05
forum: Hardware
---

### Post by narcisgarcia on 2008-06-05
I'm writing the wiki page:
[https://wiki.ubuntu.com/LaptopTestingTeam/AcerAspire1363WLMi](https://wiki.ubuntu.com/LaptopTestingTeam/AcerAspire1363WLMi)
for that laptop, and I've tried the procedures described in:
[http://users.skynet.be/ostaquet/aceraspire1360/](http://users.skynet.be/ostaquet/aceraspire1360/)
and:
[https://help.ubuntu.com/community/WifiDocs/Device/ipn2220](https://help.ubuntu.com/community/WifiDocs/Device/ipn2220)

(tested both Winxp and Win2k drivers)

...but everytime the result is the same: the Network-Manager shows entries about Wireless networks but doesn't detect anyone. I've already tested successfully the first procedure (from Olivier Staquet) on another partition with UbuntuStudio 7.10, but now this doesn't work with XUbuntu GNU/Linux 8.04 (Hardy Heron).

What fails? How can I diagnose/find the problem?

---

### Post by prshah on 2008-06-05
> **narcisgarcia said:**
> 
...but everytime the result is the same: the Network-Manager shows entries about Wireless networks but doesn't detect anyone.

What fails? How can I diagnose/find the problem?

Why not try my step-by-step guide (with expected outputs) ([http://ubuntuforums.org/showthread.php?t=756260](http://ubuntuforums.org/showthread.php?t=756260)) to set up the wireless network card? 

Since it is with expected outputs, you can see exactly where things are getting messed up.

---

### Post by narcisgarcia on 2008-06-06
Oh thanks!
I've reached the connection with only the command:
> sudo iwconfig wlan0 essid MYNETNAME
Then the "network manager applet" shows the wireless networks available and could select mine with the mouse.

But what happens when you don't know the access point ESSID?

---

