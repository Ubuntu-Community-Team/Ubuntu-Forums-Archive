---
title: "NVIDIA e-GeForce 8600GT Driver Install - Successful"
date: 2007-10-19
forum: Hardware &amp; Laptops
---

### Post by harsh2209 on 2007-10-19
Newly installed Ubuntu 7.10 Desktop edition.
Wanted to install Nvidia 2-GeForce 8600 GT Drivers.
Downloaded driver from:  [http://www.nvidia.com/object/linux_display_ia32_100.14.19.html](http://www.nvidia.com/object/linux_display_ia32_100.14.19.html)
Solution that worked out for me.
1.	Log-in as normal user.
2.	Then go to Terminal and type ‘apt-get install build-essential’.
3.	Wait until it returns the prompt and no errors displayed.
4.	Then press (without quotes) ‘Ctrl+Alt+F1’.
5.	Screen will flicker and you will see command line.
6.	Log-in as root.
7.	Stop X-Server by ‘sudo /etc/init.d/gdm stop’.
8.	Now cd to the location where the Nvidia driver is.
9.	And run it as ‘sh driver-name’
10.	It will ask to accept. Accept it.
11.	Then it will say that no precompiled kernel found etc. and would you like it to download from ‘ftp…’
12.	Say yes… and it should successfully begin the installation.
13.	When finished type on the prompt ‘sudo /etc/init.d/gdm restart’.
14.	For a moment you should see nvidia logo. It means you are successful.

---

### Post by zen2000 on 2007-10-27
Thank you! I had been struggling to get my nvidia 8600gt to work a week. I tried Envy, but it didn't work.
Your method worked.

---

### Post by jay019 on 2008-07-17
Big thumbs up for this dude! My 7.10 wouldnt start GDM after installing the nvidia card, followed your instructions on a virtual terminal and bingo all working. Cheers.

---

