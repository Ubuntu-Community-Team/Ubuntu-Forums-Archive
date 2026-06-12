---
title: "Slow internet surfing &amp; performace"
date: 2005-11-17
forum: General Help
---

### Post by t2kburl on 2005-11-17
I've been using Breezy for a while now and I have noticed that it takes ~50 seconds for Firefox to start up and load my home page. The same process takes 7 seconds when I boot to XP. Why is this happening?
I have also noticed, when I use top, that xorg is frequently up to 10-20% CPU usage! I'm running a 2.66 p4! xorg.conf is using the proper nvidia drivers.
Overall I think the system performace I'm getting with Breezy is poor. 
Any ideas or suggestions?

---

### Post by kairu0 on 2005-11-18
Can you estimate how much of that 50 seconds is program loading versus the network side (DNS resolution, proxy (?), page loading)? A breakdown would be helpful.

---

### Post by Sirin on 2005-11-19
[QUOTE=t2kburl]I've been using Breezy for a while now and I have noticed that it takes ~50 seconds for Firefox to start up and load my home page. The same process takes 7 seconds when I boot to XP. Why is this happening?
I have also noticed, when I use top, that xorg is frequently up to 10-20% CPU usage! I'm running a 2.66 p4! xorg.conf is using the proper nvidia drivers.
Overall I think the system performace I'm getting with Breezy is poor. 
Any ideas or suggestions?[/QUOTE]

Have you tried Konqueror also to see if it is your system or is it just the program?

---

### Post by t2kburl on 2005-11-20
found out (by testing Arch Linux and coming up with the same problem) (nice distro, btw) that it had to do with DNS name resolution.

see this thread for the Ubuntu specific fix:

[http://ubuntuforums.org/showpost.php?p=482412&postcount=14](http://ubuntuforums.org/showpost.php?p=482412&postcount=14)

I just needed to change my nameserver in /etc/resolv.conf to the IP given by my ISP instead of letting DHCP assign it as the router's IP

Now I'm flying around the net :)

---

### Post by t2kburl on 2005-11-20
I have also removed several packages I had installed to experiment with, and now xorg runs as it should ( 1% or less)

---

