---
title: "No wireless on Asus Eee PC 1005 HA"
date: 2009-09-30
forum: Hardware
---

### Post by Joe420 on 2009-09-30
Hello,

I've had this computer for about a month and modified it to dual boot originally in Zenwalk along with Windows, but couldn't get the ethernet to work in Zen.  When researching this problem, I came across this website:

[http://www.jfwhome.com/2009/08/06/perfect-ubuntu-jaunty-on-the-asus-eeepc-1005ha-and-1008ha/comment-page-1/](http://www.jfwhome.com/2009/08/06/perfect-ubuntu-jaunty-on-the-asus-eeepc-1005ha-and-1008ha/comment-page-1/)

and decided to try it, so I wiped Zen off the hard drive and installed jaunty.  I made it all the way to the wireless connection (ethernet works - yay!) but there is no sign of life on the wireless side.  I installed the jaunty backports like it says on the website and when I check on the synaptic package manager, there are green boxes next to:

linux-backports-modules-jaunty /the installed version is 2.6.28.15.20, which is also the latest version.

Also installed is:

linux-backports-modules-jaunty-generic /the installed version is  the same as above which is also the latest.

There are no bars on the wireless and when I right click on the network manager,  wireless is enabled along with networking.  When I go to edit connections and click on the wireless tab, there is no list of available networks even though I have my router next to the computer and ther e are about 9 other networks seen when I run windows (or when I used to run zenwalk).

Ironically, Zenwalk's network manager could see the networks with a straight out of the box installation (but no ethernet).

I'm not sure what to do.  I tried to click on "add" and give my network name and other pertinent facts but that just killed my ethernet and I had to reinstall everything to get it working again.  So I'm being more patient and cautious this time.  I need to know where to start.  I would like to try to get wireless going so that I have both ethernet and wireless.  If I can't, I'll have to go back to Zen because I need the wireless more than I need the ethernet.  Of course, without both, I still have to use windows from time to time and I'm trying to move away from that so, it would be nice to get a linux installation where both will work.  Any ideas are welcome and thanks in advance.

---

### Post by Laux on 2009-10-20
Bump! Me too! Minus the Zen part...

---

### Post by Dark_Stang on 2009-10-20
So what kind of wireless card is it? Go ahead and run...
```
lspci | grep -i "wlan"
lsusb
```
And post the output. The first command will list all PCI devices that have "wlan" in them, and the second will list all usb devices.

---

### Post by thesheff17 on 2009-11-05
I'm trying to get my ubuntu 9.10 netbook installed with this wireless device:
02:00.0 Network controller: Atheros Communications Inc. AR9285 Wireless Network Adapter (PCI-Express) (rev 01)

The backports do not work with karmic and also the kernel stuff fails to build here:
[http://ubuntuforums.org/showthread.php?t=1286503](http://ubuntuforums.org/showthread.php?t=1286503)

Even though I have both of these installed:
linux-headers-`uname -r` build-essential

I don't get why this wireless would work with ubuntu 9.04 backports but not with 9.10 backports.  Any ideas?

My Kernel version is: 2.6.31-14-generic

---

### Post by fungiblename on 2009-11-24
I followed the instructions at

[http://ubuntuforums.org/showthread.php?t=1286503](http://ubuntuforums.org/showthread.php?t=1286503)

with the following exceptions: 

1) I downloaded the "bleeding edge" drivers, available from [http://linuxwireless.org/en/users/Download#Where_to_download_bleeding_edge](http://linuxwireless.org/en/users/Download#Where_to_download_bleeding_edge). I had previously used the "stable" drivers or the Jaunty backports, but I was getting horrendously unstable wireless (signal would drop/reconnect all the time; I would get 70% signal sitting 3 feet from a router/AP)

2) After unzipping, I changed to the driver directory and selected the ath9k module using the driver-selection script. 

```
./scripts/driver-select ath9k
```This can save a lot of compile time on the 1005ha. 

3) Ensure you have all your relevant kernel headers in the right places, then run the following, in succession

```
make
sudo make unload
sudo make install
```

4) At the end of the process, I did not need to reboot; just 

```
sudo modprobe ath9k
```

Now I'm up and running, and my machine is truly mobile - I felt like I was on a cell phone in 1998 before - twisting and turning, hunting around for a seat right next to where I thought the router would be. I would also get bumped off the network when people with certain wireless cards would sit near me. I now have no interference problems, rock-solid stability (for me, at least, YMMV), and full signal strength. I can see "100%" in my signal strength in the network manager for the first time. 

Also, I am not sure if this is relevant for your situation, but I have also installed fewt's excellent eeepc-tray and related scripts. It was formerly available on statux.org, and all my hotkeys work perfectly under Jaunty. I'm not even sure where to get it any more (I believe you can find eeepc-tray on SourceForge now), and it will not install through Synaptic anymore (fewt has taken down the repository). Cycling wireless on/off with Fn+F2 and reconnecting fixes almost all my wireless problems. Again, YMMV, but I'm finally starting to get happier with this machine (now all I need is something to spin down the hard drive - I'm jealous of Windows users' reported 9+ hour battery life...)

---

### Post by fewt on 2009-11-24
> **fungiblename said:**
> I followed the instructions at

[http://ubuntuforums.org/showthread.php?t=1286503](http://ubuntuforums.org/showthread.php?t=1286503)

with the following exceptions: 

1) I downloaded the "bleeding edge" drivers, available from [http://linuxwireless.org/en/users/Download#Where_to_download_bleeding_edge](http://linuxwireless.org/en/users/Download#Where_to_download_bleeding_edge). I had previously used the "stable" drivers or the Jaunty backports, but I was getting horrendously unstable wireless (signal would drop/reconnect all the time; I would get 70% signal sitting 3 feet from a router/AP)

2) After unzipping, I changed to the driver directory and selected the ath9k module using the driver-selection script. 

```
./scripts/driver-select ath9k
```This can save a lot of compile time on the 1005ha. 

3) Ensure you have all your relevant kernel headers in the right places, then run the following, in succession

```
make
sudo make unload
sudo make install
```

4) At the end of the process, I did not need to reboot; just 

```
sudo modprobe ath9k
```

Now I'm up and running, and my machine is truly mobile - I felt like I was on a cell phone in 1998 before - twisting and turning, hunting around for a seat right next to where I thought the router would be. I would also get bumped off the network when people with certain wireless cards would sit near me. I now have no interference problems, rock-solid stability (for me, at least, YMMV), and full signal strength. I can see "100%" in my signal strength in the network manager for the first time. 

Also, I am not sure if this is relevant for your situation, but I have also installed fewt's excellent eeepc-tray and related scripts. It was formerly available on statux.org, and all my hotkeys work perfectly under Jaunty. I'm not even sure where to get it any more (I believe you can find eeepc-tray on SourceForge now), and it will not install through Synaptic anymore (fewt has taken down the repository). Cycling wireless on/off with Fn+F2 and reconnecting fixes almost all my wireless problems. Again, YMMV, but I'm finally starting to get happier with this machine (now all I need is something to spin down the hard drive - I'm jealous of Windows users' reported 9+ hour battery life...)

I get 10 hours on my HE with the stock battery so i know it is possible.  When you disconnected power I set laptop mode to 5 which should have spun down your hard drive after a period of inactivity.

I went for over 9 hours watching movies on my HE so it may have been a kernel driver problem for you if you didn't see HDD spin down or long battery life.

---

### Post by jmalone767 on 2009-11-29
FungibleName you are a genius I give all credit to you, and the bleeding edge.

---

### Post by phazed on 2009-12-23
This worked Great for me! Funny thing is Karmic Koala Worked perfectly out of the box.. it wasn't until I attempted to get smb shares to work that I had problems.

If the Atheros chipset was off and turned on (FN+F2... or restart, wake up from sleep.. etc.) I could connect to one wireless network. If I disconnected and tried to reconnect it wouldnt work. I would have to cycle wireless on/off. Bleeding Edge Drivers worked a Treat! 

Getting better signal too! 

Thanks!
phaZed

---

### Post by romkebomke on 2010-07-12
Hello. I have an Asus EEE 1008ha netbook. Had Ubuntu Remix 9.10  installed and had wired and wireless working fine. I have upgraded to  10.04 and have lost wireless connections. I can coax wireless to work  for one reboot after having used a live USB version of 9.10, but with  the next reboot it's gone again. None of the advice given here about  older versions of Ubuntu seems to fit. Any suggestions?
Btw, I posted this thread elsewhere on Ubuntuforums, but I fear that thread might be outdated: it only concerns Jaunty.

---

### Post by thesheff17 on 2010-09-02
all wireless works on ubuntu 10.04.

---

### Post by breeky5 on 2010-09-19
I also have the same problem with my asus 1008HA. I'm using ubuntu netbook 10 and my wireless is not working. Help anybody?

---

### Post by romkebomke on 2010-09-21
I discovered what my problem was with my 1008HA and Ubuntu 10.4: The Bios. Onboard WLAN was disabled by default. I could enable it for one session, but upon rebooting, it reverted back to disabled. For some reason or other it now appears to consistantly work, and I have no idea what improved it.

---

