---
title: "ATI and Intel hybrid graphics problem on 15.10"
date: 2015-12-10
forum: Hardware
---

### Post by redguy41 on 2015-12-10
Hi everyone,

I could not find this post anywhere so I'm posting it now.

I'm using a Lenovo z51-70 IdeaPad with hybrid graphics as listed:

Display controller: Advanced Micro Devices, Inc. [AMD/ATI] Venus XTX [Radeon HD 8890M / R9 M275X/M375X] (rev 81)and
VGA controller: Intel Corporation Broadwell-U Integrated Graphics [8086:1616] (rev 09) (prog-if 00 [VGA controller])

The graphics in use is intel as per lspci -vnnn | perl -lne 'print if /^\d+\:.+(\[\S+\:\S+\])/' | grep VGA.


For office tasks, everything works fine with the open source default driver and my system is using the Intel graphics. When I try to change to AMD closed source driver in "Additional drivers" tab (see attached), the system boots but the graphics lags, scrolling as well.

[ATTACH=CONFIG]266070[/ATTACH]

Furthermore, I **have tried to install the fglrx driver and updates, **and the panel as well, but I couldn't switch to the AMD. It never offered a switching action. 
After isntalling the driver and rebooting, the graphics fail and instruct me to return to the open source graphics (Try using Ubuntu in low graphics mode).

Although everything works fine, I would like to be able to use this AMD graphics especially if I wish to play games.

THank you and my appologizes if this has been posted before.

Gaj

---

### Post by mastablasta on 2015-12-10
fglrx has a problem in 15.10: [https://bugs.launchpad.net/ubuntu/+source/fglrx-installer/+bug/1493888](https://bugs.launchpad.net/ubuntu/+source/fglrx-installer/+bug/1493888)

also with hybrid you need to initialise the driver after install. Item 6 under 3.1.  - [https://help.ubuntu.com/community/BinaryDriverHowto/AMD](https://help.ubuntu.com/community/BinaryDriverHowto/AMD)

---

### Post by redguy41 on 2015-12-10
OK thanks for the heads up.
Will try the tutorial, and check the bugs.

---

### Post by niai on 2015-12-10
I had a lot of trouble with the drivers in the end the best thing was 15.10 installed with these commands 

> **Install the driver:**

        sudo apt-get install fglrx-updates gcc-4.9 g++-4.9

**Create links to gcc:**

        sudo rm -f /usr/bin/gcc

        sudo rm -f /usr/bin/g++

        sudo ln -s /usr/bin/gcc-4.9 /usr/bin/gcc

        sudo ln -s /usr/bin/g++-4.9 /usr/bin/g++

**Rebuild the driver module.:**

        sudo apt-get --reinstall install fglrx-updates-core



---

### Post by redguy41 on 2015-12-10
Thanks.
Do you happen to know if this bug is consistent with LTS 14.10? I might downgrade.

---

### Post by QIII on 2015-12-10
Hello!

14.10 is not an LTS release -- and it is no longer supported.

14.04 is an LTS release.  It is likely that the problem would not exist in 14.04.  However, I cannot guarantee that using 14.04 would offer a solution to the issue.

---

### Post by redguy41 on 2015-12-10
Thanks! Maybe I'll just wait for the 16.04.

---

### Post by mastablasta on 2015-12-11
if 14.04.3 LTS doesn't work and you don't want to mess with repositories then -wait for 16.04 or for the bug to be solved in 15.10.

I would try the LTS first. or another distro. OpenSUSE maybe?!

---

### Post by redguy41 on 2015-12-23
So what I did was downgrade to 14.04 LTS, which made the whole thing work a bit better, but only a bit. FGLRX drivers got installed successfully, however, screen tearing appeared and lagging, especially during watching movies whether on Youtube or VLC. I could easily switch between the power-saving INTEL GPU and Gaming High Performance AMD GPU in the ATI Catalyst Control Center in Unity.

I also tried to mess around with Compiz, as per tutorials on the web, but nothing helped. I also tried to install the fglrx driver updates, from the AMD website which failed my boot, so I had to purge the drivers and start over again.

Eventually I got sick of it, so I'm now using the Intel on board graphics, since I'm not playing games, for now. Really frustrated about this, I had hoped to buy a decent hardware but AMD just doesn't rhyme with Ubuntu.

I guess I'll wait for the 16.04 release in hope that they will have figured out this problem.
Any suggestions are welcome.

Thanks!

---

