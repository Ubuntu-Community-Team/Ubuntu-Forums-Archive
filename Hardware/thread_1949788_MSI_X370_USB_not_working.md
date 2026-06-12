---
title: "MSI X370 USB not working"
date: 2012-03-30
forum: Hardware
---

### Post by algebralives on 2012-03-30
*****BASICS*****
Installed Lubuntu on new MSI laptop. Everything works great except USB flash drives or external DVD drives. The USB hardware is fine. I know it's OS related. Effected: Ubuntu, Lubuntu, Mint (11.10, 12.04 Beta)


*****SPECS*****
MSI X370 Laptop
AMD E-450 1.65GHz
AMD Radeon HD6320 Graphics Card
4 GB SSD
500 GB HDD


*****THE STORY*****
Used unetbootin to attempt to install the following on the laptop/netbook but failed while copying files during installation: Lubuntu 11.10 (32 and 64), Ubuntu 11.10 (32 and 64), Mint 12 (32), Mint LXDE 12 (32), Lubuntu 12.04 Beta (64). This is the reason I filed this under Ubuntu because I believe it's a systemic issue.

However, after installing elementary Jupiter, I was successful. Because Jupiter is based on 11.04, I installed Lubuntu 11.04 (32). Installation was flawless. I used the upgrade feature to upgrade to Lubuntu 11.10. No problems except for my USB drives again.
 
Now my USB has limited functionality. Printer works great. However, I can only copy about 100-20 MB worth of stuff with a flash drive before it crashes. After it crashes, I can't use any flash drive until I reboot. Not only will it not mount, it doesn't even recognize the drive is there. External DVD (hooked into USB) spins up to speed, looks promising, and then crashes.


*****IT'S NOT THE USB PORT*****
Please don't suggest this as an option. I copied 40GB of music from an external hard drive while I was still in Lubuntu 11.04. Worked great. I know this is an Ubuntu 11.10+ issue...


Help? Thanks!! :)

---

### Post by mhrpinca on 2012-04-26
Similar problem here... i cant tether my phone for more than a minute before i lose my internet conection and if i conect an external drive it recognizes it, connects to it than imediatly disconects.....pissing me off.

---

### Post by algebralives on 2012-04-26
Ironically, I'm posting this running the brand new 12.04 off a USB stick. It seems to work fine. Maybe there was a kernel fix. I'll post again if the upgrade solves it...

Good luck with your tethering!

---

### Post by dumaron on 2012-04-28
You can find a temporary solution in this topic: [http://ubuntuforums.org/showthread.php?p=11882892](http://ubuntuforums.org/showthread.php?p=11882892)

---

### Post by algebralives on 2012-04-28
Thanks, Dumaron. I'm going to repost the solution below. Upgrading to 12.04 did not help, but this did. Although it is claimed to be a temp fix, I'm marking this solved.

In terminal:
```
 sudo gedit /etc/modprobe.d/blacklist.conf
```

Add the following line, save, and reboot:
```
 blacklist rts5139
```

---

### Post by iyas120 on 2013-01-11
With new kernel on ubuntu 12.04.1 and above.. this problem is solved by default. Thanks to kernel team...

---

