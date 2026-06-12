---
title: "Peer-to-peer network problem"
date: 2006-04-07
forum: Hardware &amp; Laptops
---

### Post by slash_schizoid on 2006-04-07
Well, I'm kind of a newbie, I used FC distro for a while and now changed to Ubuntu.
Now my problem. As I said before, I used FC on my laptop so, for me going Ubuntu, I had to make a backup in my WinXP PC. I set up the network very nicely, static IPs 192.168.1.1 & 192.168.1.2 subnetmask 255.255.255.0 then used samba to move the files from my laptop to my PC.
Now that I have configured this new distro I wanted to get my files back, so I set this network again, same IPs and devices, but, my great trouble is: I CAN'T EVEN PING MY PCs INTERFACE! I tested the crossover cable, and it was OK, but I can't ping with my laptop the PC.
Sometimes the output of the ping command on the PC shows about 4 Request timed out and 1 Reply from.... And, on the laptop, shows all replies but with times of 10 seconds or something like that... DOES ANYONE KNOWS WHAT IS WRONG???!!! ](*,) 
BTW, I don't have a router or hub, just crossover cable.
I really hope someone can help me, thanx a lot

---

### Post by ranf on 2006-04-08
Have a look at this:
[http://ubuntuforums.org/showthread.php?t=87643](http://ubuntuforums.org/showthread.php?t=87643)

---

### Post by hajk on 2006-04-08
Show us the output of the following commands:

sudo ifconfig
sudo route

and the contents of the /etc/network/interface file.

---

