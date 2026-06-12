---
title: "Skype installation"
date: 2006-02-05
forum: Installation &amp; Upgrades
---

### Post by Rajan Varadarajan on 2006-02-05
I downloaded the latest version of Skype from skype.com. They have several binaries but I got the one clearly marked "Debian" package and the web site mentioned "for Debian distributions like ubuntu.." So I believe I got the right package. But I have a hard time installing it. 

Also, in the mean time, I read several posts saying that Skype kills the sound card. I am not sure why that is the case.

Questions:
1. What is the correct syntax for installing the Skype Debian package?
2. Does anyone have experience installing Skype and making it work with ubuntu?
3. I have an old Gateway Penitum 266MHz (320 MB RAM) running ubuntu. It runs pretty fine. The sound card I have is an old sound blaster (dating back to 1999 or earlier). I play music all the time on this system without any trouble and I don't want to kill my sound card with Skype.

Thanks in advance for your help.

---

### Post by frodon on 2006-02-06
1- To install a . deb run use this command : ```
sudo dpkg -i package_name
```
2- No problem with skype for me, i got it working in 1 min installing [this .deb]("http://www.ubuntuforums.org/showthread.php?t=81831&highlight=skype+deb") package, and it works really well on my ubuntu box.
3- I have an old sound blaster too and i never got this kind of problems and i also listen music all the time ;)

I think you shouldn't get any problems except if you're really unlucky.

Happy skyping ;)

---

### Post by Rajan Varadarajan on 2006-02-07
I found in another thread about the dependency problems introduced by the Debian Skype package. The dependency was from Qt library (version 3). The author suggested using the RPM package instead of the Debian package. The RPM package is converted to the Debian package by using the Alien conversion tool. That solution worked perfectly and I was able to install Skype on my Gateway PC. It even refreshed my contacts list. I just have to hook up my microphone and give it a ride.

Thanks for all the help.

---

