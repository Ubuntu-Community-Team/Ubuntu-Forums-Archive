---
title: "Ubuntu 9.10 on Dell Vostro 1000 (No Wireless)"
date: 2009-10-29
forum: Hardware
---

### Post by dyous87 on 2009-10-29
I have a Dell Vostro 1000 laptop that I was running with Ubuntu 9.04 and everything including wireless was working perfectly. Today I formatted it and did a clean install of Ubuntu 9.10 but I cannot get wireless working. 

When I run a "lspci" I get this line in the output:

```
05:00.0 Network controller: Broadcom Corporation BCM4312 802.11b/g (rev 01)
```I don't understand why wireless was working out of the box on 9.04 but now I cannot get it to work at all. Any help would be greatly appreciated.

David

---

### Post by dyous87 on 2009-10-29
bump

---

### Post by dyous87 on 2009-10-30
I was able to fix the issue by instaling the bcmwl-kernel-source:

```
apt-get install bcmwl-kernel-source
```

I hope this can help anyone who needs it.

David

---

### Post by empeg9000 on 2009-10-30
I have the same laptop. Did everything else work right out of the box? How about graphics and sound?

---

### Post by dyous87 on 2009-10-30
Everything else worked flawlessly out of the box. The wireless was the only thing I had to install the above package to get to work.

David

---

### Post by x2wdtoyotax on 2009-10-30
I have an HP Mini 1030nr with the same wireless card in it.  I tried the code listed above... couldn't find that package? I've been researching this issue and found out that the Broadcom cards require firmware to work correctly. I downloaded the firmware at:

[https://launchpad.net/ubuntu/karmic/i386/b43-fwcutter/1:012-1](https://launchpad.net/ubuntu/karmic/i386/b43-fwcutter/1:012-1)

When I try to activate the proprietary drivers I receive:

SystemError: installArchives() failed

I am very new to the Ubuntu/linux world. Any help would be greatly appreciated.

---

### Post by dyous87 on 2009-10-30
You shouldn't have to install b43-fwcutter. Before you try installing the package that worked for me, click on System>Administration>Software Sources

The make sure that you have Main, Universe, Restricted and Mutliverse checked off. 

Close that. Now open a terminal and run the following commands.

```
sudo apt-get update
sudo apt-get install bcmwl-kernel-source
```

It should now find the package. After a restart you should have working wireless.

David

---

### Post by x2wdtoyotax on 2009-10-30
So... I tried the steps you listed in the second fix.  I can't access the Internet at all on my netbook ( :( no Ethernet port due to the small form factor.) I'm using a second computer to access the Internet right now. When I tried to update it failed, obviously. Is there any way to download that package manually?  I'll do some more research also.  Thanks for your help. 

More info:
Ubuntu Netbook Remix 9.10
Broadcom BCM4312 802.11b/g (rev 01)
HP Mini 1030nr Netbook

---

### Post by x2wdtoyotax on 2009-10-30
OK... I think I found it. After a quick google...

[http://packages.ubuntu.com/da/karmic/bcmwl-kernel-source](http://packages.ubuntu.com/da/karmic/bcmwl-kernel-source)

I found builds for both the i386 and amd64 architectures. I am going to install and see what happens.

---

### Post by x2wdtoyotax on 2009-10-30
Now I've got a new problem! When I open the package to install it. I receive the following error message:
[B]
Error: Dependency is not satisfiable: dkms[/B]

The package installer will not let me continue? Any suggestions?

---

### Post by x2wdtoyotax on 2009-10-30
OK.... after another quick google. I found a DKMS package at 

[http://packages.ubuntu.com/da/karmic/dkms](http://packages.ubuntu.com/da/karmic/dkms)

That installed fine and allowed me to install the driver package with no issues. After a reboot... the wireless was still not working.  I tried to enable driver via System> Administration> Hardware Drivers with no luck. It goes through all the motions with no errors yet never actually activates the driver? I feel like I'm so close! Any suggestions?

---

### Post by Summitt Dweller on 2009-10-30
Same issue here with my 1120nr.  Followed the same steps and got the same outcome...no apparent errors but no wireless after reboot either. :(

Subscribing

---

### Post by RRNovaes on 2009-10-30
I have a HP Mini 5101 and I've had the same problem.

The first solution worked for me:
sudo apt-get install bcmwl-kernel-source

(I downloaded it through my cell phone connection, since I had no Ethernet available.)

BUT I'm puzzled by the fact that wireless *did work* on live mode, even with no other Internet connection, and then failed *after* install.

That's very disappointing, even for moderately advanced user such as myself. Let alone for beginners.

---

### Post by wprime on 2009-10-31
> **x2wdtoyotax said:**
> OK.... after another quick google. I found a DKMS package at 

[http://packages.ubuntu.com/da/karmic/dkms](http://packages.ubuntu.com/da/karmic/dkms)

That installed fine and allowed me to install the driver package with no issues. After a reboot... the wireless was still not working.  I tried to enable driver via System> Administration> Hardware Drivers with no luck. It goes through all the motions with no errors yet never actually activates the driver? I feel like I'm so close! Any suggestions?

Hi,

You'll need to connect that system to the internet.

Completely remove DKMS

sudo apt-get remove dkms

Then reinstall the driver

sudo apt-get install bcmwl-kernel-source

---

### Post by Haythayt on 2009-10-31
This worked for me.. at least until i rebooted:

[http://ubuntuforums.org/showpost.php?p=8209076&postcount=6](http://ubuntuforums.org/showpost.php?p=8209076&postcount=6)

---

### Post by rainserpent on 2009-11-07
Thank you so much dyous87 for this tip:

sudo apt-get update
sudo apt-get install bcmwl-kernel-source

It worked like a charm!

-Paul

---

### Post by y2ken on 2009-11-13
Thanks! 
The below fix worked for me on my HP DV6000 series laptop.  :D

sudo apt-get update
sudo apt-get install bcmwl-kernel-source

Although I was very disappointed that wireless with Ubuntu 9.10 didn't work 'out-of-box' like it did with 9.04  :(

---

### Post by jesusprice on 2009-12-08
okay this fi worked on my inspiron 1504 i just had to restart

---

### Post by spogue on 2009-12-14
Well, I was hoping all this would work for me as well.  I have a HP Mini 1030nr and have installed Ubuntu Moblin Remix 2.1 which is 9.10 based.  Wired works fine though initially I had to boot with the ethernet cable connected.  However, I can't get wireless working.  I tried doing it through > sudo apt-get install bcmwl-kernel-source and also through Hardware Drivers.  Reboot and still no wireless.  If I rerun apt-get it tells me that bcmwl-kernel-source is up-to-date.  If I go to Hardware Drivers, it shows it in the list but not activated.  When I try to activate it, it never flips to activated. Is there a next level of PD I can do here?

---

### Post by humantarget on 2010-03-09
This worked perfectly for my Vostro 1000. (After a reboot)

---

### Post by m4r4g4t0 on 2010-03-25
Hi, people!

I have a Dell Vostro 1000 running 9.04, but my 3D is slow.

Please let me know if 3D runs fast on 9.10 for you (Neverball is a good test) so I can decide to do the upgrade. Thanks, guys!

YES, IT DOES!! (just installed 9.10 and after a few initial updates, everything is working, including Wi-Fi and 3D acceleration)

---

