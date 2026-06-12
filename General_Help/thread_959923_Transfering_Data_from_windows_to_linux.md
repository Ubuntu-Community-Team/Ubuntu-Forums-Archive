---
title: "Transfering Data from windows to linux"
date: 2008-10-26
forum: General Help
---

### Post by mdh426 on 2008-10-26
I recently purchased a laptop (which i run ubuntu on) and want to transfer data from my old desktop( that runs windows xp). I know a few ways to transfer data. Any suggestions on what the most efficient way would be? 
Thank you.

---

### Post by Yashiro on 2008-10-26
Crossover cable if you have one.

1.) Assign IP addresses. Both computers require a unique IP address.
sudo ifconfig eth0 10.0.1.1 netmask 255.255.255.252
ip of 10.0.1.1 for the first computer and subnet 255.255.255.252

10.0.1.2 for the second computer. 
sudo ifconfig eth0 10.0.1.2 netmask 255.255.255.252
ip of 10.0.1.2 for the second computer and subnet 255.255.255.252

2.) Enable file sharing (windows file sharing / linux samba) - You can find more information on how to do this on the net. 

3.) Share the folders you are interested in accessing - You can usually share a folder by right clicking on it while browsing your files. In the menu, you'll get an option to share. This varies for each OS.

4) Copy files. Use their IP addresses to access them, smb://10.0.1.1 or whatever the windows syntax is.


* If you have a home network set up start at step 2 and don't bother changing ip's.


* or buy a cheap USB drive and do it that way.

---

