---
title: "powerware ups"
date: 2007-05-11
forum: Hardware &amp; Laptops
---

### Post by spur on 2007-05-11
I downloaded the driver for my 64bit system and it seemed to install, but nothing is happening and the config file is empty. The last step on the install was the creation of a sym link which it says did not work.
Has any one got one of these  to work? If so how? Mine is the 5110.
This what it tried to sym link I think "/etc/init.d/ls.init" Which is why its not working,  I think.:confused:

---

### Post by spur on 2007-05-12
If no -one has one then does someone have an idea where the sym link should link to? I'm runnig Feisty.

---

### Post by Spartan.II.117 on 2007-05-12
did you try installing nut? that's what i use on my minuiteman ups

---

### Post by spur on 2007-07-18
I finally got around to this again after moving to kubuntu for a while. Kubuntuhas a graphical interface for managing ups that is a dream and I can't get it to install on my ubuntu.
Anyway i followed the directions from this site [http://opensource.mgeups.com/howto.htm]("http://opensource.mgeups.com/howto.htm") and am getting > Error: Connection failure: Connection refused.When I run > upsc ups1@localhost 
I also note that when I run the command to start it it looks ok but only says half of what it should.
Start command > invoke-rc.d nut start
result > Starting Network UPS Tools thrn it should say > :upsd upsmon and it doesn't.

---

### Post by spur on 2007-07-18
I found the glitch. The upsd.conf file was in the wrong place from installation it should have been in /etc/nut/ but was in /usr/. Once I fixed this things began to work.

---

