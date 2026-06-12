---
title: "3rd install still no wireless connection"
date: 2008-08-12
forum: Hardware
---

### Post by rach3773 on 2008-08-12
Hello!
I could really use some help. I have tried everything that is posted including: How to: Broadcom Wireless cards without Ndiswrapper for Dapper and Edgy by nickm. I understand that it is out dated but anything will do. I am so frustrated at this point.

Is there anyone who has had trouble and then figured it out?
I have Ubuntu 8.04

Thanks,
Rach3773:confused:

---

### Post by SpaceMaster on 2008-08-12
The ndiswrapper set of instructions got mine working.  That is, it worked for two different Broadcom cards on two different machines.

[This is the thread]("http://ubuntuforums.org/showthread.php?t=766560")with the instructions I followed.  It also seems to have the best overall success rate.

Also, you may want to take a look at Ubuntu's online help documentation for this process, [here]("https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx/Feisty_No-Fluff#head-bc33832c0547766a33c3a84f13f971ca757b2851").  There are, of course, other models of Broadcom wireless adapters.  I used the BCM4306 steps for my BCM4309, for example.

  The ftp servers at HP and Compaq are iffy, so I'd suggest replacing step 2 with:
```

wget http://myspamb8.googlepages.com/WPC5...826-pruned.zip
unzip WPC54Gv2_40826-pruned.zip
```

Other than that, just follow the instructions either in the thread or on the help page to the letter, and they'll lead you to gold.

Hope this all helped.

---

### Post by rach3773 on 2008-08-12
Please tell me what I did wrong????


---------------------------------------------------Terminal---------
rachelle@Runbox:~$ echo 'blacklist bcm43xx' | sudo tee -a /etc/modprobe.d/blacklist
blacklist bcm43xx
rachelle@Runbox:~$ sudo apt-get install ndiswrapper-utils-1.9
Reading package lists... Done
Building dependency tree       
Reading state information... Done
ndiswrapper-utils-1.9 is already the newest version.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
rachelle@Runbox:~$ mkdir ~/bcm43xx; cd ~/bcm43xx
rachelle@Runbox:~/bcm43xx$ 
rachelle@Runbox:~/bcm43xx$ 
rachelle@Runbox:~/bcm43xx$ sudo apt-get install cabextract
Reading package lists... Done
Building dependency tree       
Reading state information... Done
cabextract is already the newest version.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
rachelle@Runbox:~/bcm43xx$ wget [ftp://ftp.compaq.com/pub/softpaq/sp34001-34500/sp34152.exe](ftp://ftp.compaq.com/pub/softpaq/sp34001-34500/sp34152.exe)
--18:09:23--  [ftp://ftp.compaq.com/pub/softpaq/sp34001-34500/sp34152.exe](ftp://ftp.compaq.com/pub/softpaq/sp34001-34500/sp34152.exe)
           => `sp34152.exe'
Resolving ftp.compaq.com... 161.114.23.171
Connecting to ftp.compaq.com|161.114.23.171|:21... connected.
Logging in as anonymous ... Logged in!
==> SYST ... done.    ==> PWD ... done.
==> TYPE I ... done.  ==> CWD /pub/softpaq/sp34001-34500 ... done.
==> PASV ... done.    ==> RETR sp34152.exe ... done.

    [                      <=>            ] 4,494,456      1.26M/s             

18:09:28 (978.66 KB/s) - `sp34152.exe' saved [4494456]

rachelle@Runbox:~/bcm43xx$ cabextract sp34152.exe
Extracting cabinet: sp34152.exe
  extracting bcm1xsup.dll
  extracting bcm43xx.cat
  extracting bcm43xx64.cat
  extracting Bcmnpf64.sys
  extracting bcmwl5.inf
  extracting bcmwl5.sys
  extracting bcmwl564.sys
  extracting bcmwliss.dll
  extracting bcmwlnpf.sys
  extracting bcmwlpkt.dll
  extracting bcmwls.ini
  extracting bcmwls32.exe
  extracting bcmwls64.exe
  extracting bcmwlu00.exe
  extracting data1.cab
  extracting data1.hdr
  extracting data2.cab
  extracting ikernel.ex_
  extracting is.exe
  extracting launcher.ini
  extracting layout.bin
  extracting setup.exe
  extracting Setup.ini
  extracting setup.inx
  extracting setup.iss
  extracting sp34152.cva

All done, no errors.
rachelle@Runbox:~/bcm43xx$ sudo ndiswrapper -i bcmwl5.inf
driver bcmwl5 is already installed
rachelle@Runbox:~/bcm43xx$ ndiswrapper -l
bcmwl5 : driver installed
	device (14E4:4311) present (alternate driver: bcm43xx)
rachelle@Runbox:~/bcm43xx$ sudo depmod -a
rachelle@Runbox:~/bcm43xx$ sudo modprobe ndiswrapper
rachelle@Runbox:~/bcm43xx$ sudo cp /etc/network/interfaces /etc/network/interfaces.orig
rachelle@Runbox:~/bcm43xx$ echo -e 'auto lo\niface lo inet loopback\n' | sudo tee /etc/network/interfaces
auto lo
iface lo inet loopback

rachelle@Runbox:~/bcm43xx$ sudo ndiswrapper -m
module configuration already contains alias directive

rachelle@Runbox:~/bcm43xx$ echo 'ndiswrapper' | sudo tee -a /etc/modules
ndiswrapper
rachelle@Runbox:~/bcm43xx$ echo 'ENABLED=0' | sudo tee -a /etc/default/wpasupplicantENABLED=0
rachelle@Runbox:~/bcm43xx$ sudo rmmod b43
ERROR: Module b43 does not exist in /proc/modules
rachelle@Runbox:~/bcm43xx$ 
---------------------------------------------------------Terminal----------
Any clues??

---

### Post by Ayuthia on 2008-08-12
> **rach3773 said:**
> Please tell me what I did wrong????


---------------------------------------------------Terminal---------
rachelle@Runbox:~$ echo 'blacklist bcm43xx' | sudo tee -a /etc/modprobe.d/blacklist
blacklist bcm43xx
rachelle@Runbox:~$ sudo apt-get install ndiswrapper-utils-1.9
Reading package lists... Done
Building dependency tree       
Reading state information... Done
ndiswrapper-utils-1.9 is already the newest version.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
rachelle@Runbox:~$ mkdir ~/bcm43xx; cd ~/bcm43xx
rachelle@Runbox:~/bcm43xx$ 
rachelle@Runbox:~/bcm43xx$ 
rachelle@Runbox:~/bcm43xx$ sudo apt-get install cabextract
Reading package lists... Done
Building dependency tree       
Reading state information... Done
cabextract is already the newest version.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
rachelle@Runbox:~/bcm43xx$ wget [ftp://ftp.compaq.com/pub/softpaq/sp34001-34500/sp34152.exe](ftp://ftp.compaq.com/pub/softpaq/sp34001-34500/sp34152.exe)
--18:09:23--  [ftp://ftp.compaq.com/pub/softpaq/sp34001-34500/sp34152.exe](ftp://ftp.compaq.com/pub/softpaq/sp34001-34500/sp34152.exe)
           => `sp34152.exe'
Resolving ftp.compaq.com... 161.114.23.171
Connecting to ftp.compaq.com|161.114.23.171|:21... connected.
Logging in as anonymous ... Logged in!
==> SYST ... done.    ==> PWD ... done.
==> TYPE I ... done.  ==> CWD /pub/softpaq/sp34001-34500 ... done.
==> PASV ... done.    ==> RETR sp34152.exe ... done.

    [                      <=>            ] 4,494,456      1.26M/s             

18:09:28 (978.66 KB/s) - `sp34152.exe' saved [4494456]

rachelle@Runbox:~/bcm43xx$ cabextract sp34152.exe
Extracting cabinet: sp34152.exe
  extracting bcm1xsup.dll
  extracting bcm43xx.cat
  extracting bcm43xx64.cat
  extracting Bcmnpf64.sys
  extracting bcmwl5.inf
  extracting bcmwl5.sys
  extracting bcmwl564.sys
  extracting bcmwliss.dll
  extracting bcmwlnpf.sys
  extracting bcmwlpkt.dll
  extracting bcmwls.ini
  extracting bcmwls32.exe
  extracting bcmwls64.exe
  extracting bcmwlu00.exe
  extracting data1.cab
  extracting data1.hdr
  extracting data2.cab
  extracting ikernel.ex_
  extracting is.exe
  extracting launcher.ini
  extracting layout.bin
  extracting setup.exe
  extracting Setup.ini
  extracting setup.inx
  extracting setup.iss
  extracting sp34152.cva

All done, no errors.
rachelle@Runbox:~/bcm43xx$ sudo ndiswrapper -i bcmwl5.inf
driver bcmwl5 is already installed
rachelle@Runbox:~/bcm43xx$ ndiswrapper -l
bcmwl5 : driver installed
	device (14E4:4311) present (alternate driver: bcm43xx)
rachelle@Runbox:~/bcm43xx$ sudo depmod -a
rachelle@Runbox:~/bcm43xx$ sudo modprobe ndiswrapper
rachelle@Runbox:~/bcm43xx$ sudo cp /etc/network/interfaces /etc/network/interfaces.orig
rachelle@Runbox:~/bcm43xx$ echo -e 'auto lo\niface lo inet loopback\n' | sudo tee /etc/network/interfaces
auto lo
iface lo inet loopback

rachelle@Runbox:~/bcm43xx$ sudo ndiswrapper -m
module configuration already contains alias directive

rachelle@Runbox:~/bcm43xx$ echo 'ndiswrapper' | sudo tee -a /etc/modules
ndiswrapper
rachelle@Runbox:~/bcm43xx$ echo 'ENABLED=0' | sudo tee -a /etc/default/wpasupplicantENABLED=0
rachelle@Runbox:~/bcm43xx$ sudo rmmod b43
ERROR: Module b43 does not exist in /proc/modules
rachelle@Runbox:~/bcm43xx$ 
---------------------------------------------------------Terminal----------
Any clues??

So far, it does not look like anything is wrong.  The message about b43 not existing just means that the module was not loaded which is not a big deal because you are trying to remove it.

---

### Post by rach3773 on 2008-08-12
I still have no wireless connection.???

---

### Post by Slug71 on 2008-08-12
Rach make sure the Proprietary driver is enabled. System - Admin - Hardware Drivers. Mine was lo think. Thats what i did anyways and it worked fine. Also had Hardy and have the BCM4310.

---

### Post by Ayuthia on 2008-08-12
> **Slug71 said:**
> Rach make sure the Proprietary driver is enabled. System - Admin - Hardware Drivers. Mine was lo think. Thats what i did anyways and it worked fine. Also had Hardy and have the BCM4310.

If you are using ndiswrapper, I don't think that you want to have the Hardware Drivers enabled or else ndiswrapper will not work.

Can you post the results of:
```
lshw -C network
lsmod|grep -i -e bcm43xx -e b43 -e ssb -e b44 -e ndiswrapper -e wl
uname -a
```
The first command will let us see what driver your wireless is trying to use, the second will show what drivers are loaded for your wireless, and the last one is to see what kernel version and bit version you are using (32 or 64).

---

### Post by rach3773 on 2008-08-12
That worked!!!

Do you know how to make it perminate?? (excuses the spelling)
:)


Thanks,
Rach3773

---

### Post by Slug71 on 2008-08-13
What worked, the proprietary driver? 
If you enabled it, it should be enabled permanently. And if you right click on NM at the top right corner of the screen(next to the little speaker i think) there should be a little check box or something that will make it connect automatically.

---

### Post by Ayuthia on 2008-08-13
> **Slug71 said:**
> What worked, the proprietary driver? 
If you enabled it, it should be enabled permanently. And if you right click on NM at the top right corner of the screen(next to the little speaker i think) there should be a little check box or something that will make it connect automatically.
You will also want to either blacklist ndiswrapper or uninstall it so that it will not interfere.

---

