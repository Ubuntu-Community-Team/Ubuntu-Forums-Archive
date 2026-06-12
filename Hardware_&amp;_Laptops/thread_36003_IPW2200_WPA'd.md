---
title: "IPW2200 WPA'd"
date: 2005-05-21
forum: Hardware &amp; Laptops
---

### Post by Stealth on 2005-05-21
I got the new drivers and firmware installed, set up wpa_supplicant, and everything should work but it doesn't. I'm running Kubuntu so I'm mainly using Kwifimanager. Now, my WPA network isn't detected at first. But with some command that I'm suppose to put after the wpa_supplicant is installed its detected, its just I can't seem to find a way to connect to it...anyone got an idea as it seems WPA and the new IPW2200 drivers are working?

---

### Post by luca_linux on 2005-05-21
I'm running Ubuntu...have you followed this howto: [http://www.ubuntuforums.org/showthread.php?t=26623?](http://www.ubuntuforums.org/showthread.php?t=26623?)

---

### Post by Stealth on 2005-05-23
Yea, that was the thing I followed...kinda ^_^

I was getting errors on one of the tar things, but I found deb packages for the 2 things and installed them with dpkg. I searched and found them in the folders they were suppose to be (the ones you have to cp to). 

Hmmm...looing through the thread I missed that section about KMISC...I'll check that out...

The command: "sudo wpa_supplicant -B -i eth1 -c /etc/wpa_supplicant.conf -D ipw -w -dd" is what I mentioned before. Before I can't see the network, after using that command, *then* I can see the WPA network. It just won't connect (maybe I suck at Kwifi? :P Any other programs I can use?)

And I missed that start up thing too... ](*,)

---

### Post by Stealth on 2005-05-24
I ALMOST GOT IT!

I set up everything all over again, installed gcc, build essentials, etc. etc., installed headers and sources, etc. Started from top, installed 2.3 firmware, drivers, copied and fixed whatever was wrong with em and now dmesg will show me that I'm running the latest version. AND Kwifi shows I'm connected to my network, and everything seems to be working, I can even browse my network! Yea...everything works but the internet... ](*,) What is it? I can see I have the right IP (I got a static IP and followed ur interfaces thing) so isn't that all I should need?

---

### Post by luca_linux on 2005-05-24
Are you sure you've set the right DNS?

---

### Post by Stealth on 2005-05-25
All right yea, the DNS was the problem...but here's the weird stuff. KDE's Control Center is very weird Kubuntu, I was able to add my router as the DNS and that worked, but for some reason, now my default gateway, which is also my router must be added manually everytime I boot, because KDE won't save the setting. Also, I can't even changes any Network settings unless I go into Konsole and use "sudo kcontrol" to launch it. Sooo, atm, I'm using a sudo route gateway ip" command, or something like it, and am wondering if there's a way to fix this, or a way to run this command on start up?

---

