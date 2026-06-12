---
title: "wireless and monitor not working thinkpad T30"
date: 2007-03-22
forum: Hardware &amp; Laptops
---

### Post by downest on 2007-03-22
I have an older IBM Thinkpad T30 I've had since 2002.  I've been running Gentoo successfully for two years with no problems (once I got everything working :P ).  Last night my roommate convinced me to switch to Ubuntu.  It's definitely a better system for me, I'm not very computer savvy, so Gentoo was harder to use and mostly wasted on me.  I was really happy to see ALMOST everything work when I first loaded Ubuntu after the amazingly short install off the liveCD.  Anyway, I have two issues I need to fix...

1. Wireless does not work.  I've read some different things to try, but nothing works.  I'm trying to connect to a wireless LAN in my apartment with an encryption key, which of course I do have.  I tried the built-in GUI but it doesn't work, iwconfig returns this:

> 
eth1      IEEE 802.11b  ESSID:"rocknroll"  Nickname:"Prism  I"
          Mode:Managed  Frequency:2.412 GHz  Access Point: 00:11:F5:14:73:04   
          Bit Rate:11 Mb/s   Sensitivity:1/3  
          Retry min limit:8   RTS thr:off   Fragment thr:off
          Power Management:off
          Link Quality=80/92  Signal level=-9 dBm  Noise level=-143 dBm
          Rx invalid nwid:0  Rx invalid crypt:265  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0


but doesn't work.

2. I keep the thinkpad on a port replicator on my desk 90% of the time, connected to a USB keyboard, mouse etc (the IBM keyboard is losing keys every day) and to a CRT monitor connected to the VGA port on the replicator.  I cannot get both the laptop screen and the CRT to display at the same time, as Gentoo did for me no problem.  If I boot with the monitor plugged in and the laptop on the PR, only the monitor comes up with something, and it's way too big and I can't see the whole thing.  The laptop is blank, even if I then remove it from the replicator.  If I boot off the PR the laptop screen shows everything perfectly.  When I put it on the PR, nothing changes.  The card I have is an ATI Radeon Mobility 7500, I've read that there are many problems with it.  My friend who is pretty savvy with FreeBSD and Mac OS tried to help me, but we couldn't really make any progress.  He got both screens to display, but it hangs somewhere checking the Radeon drivers (or something, keep in mind I don't understand very well).  We reloaded the backed up xorg.conf file, and it still hung!  then we booted to the liveCD and copied the xorg.conf file there to my USB drive, intending to copy it over.  After a reboot, Ubuntu loaded X perfectly fine as it has been!  I compared the backed-up xorg.conf file to the one from the liveCD and there is no difference... it seems to be ok now and I have no clue what to do.  

here's the output of llspci, I was told it will help to know what hardware is there.
> 
downest@thinkpad:~$ lspci
00:00.0 Host bridge: Intel Corporation 82845 845 (Brookdale) Chipset Host Bridge (rev 04)
00:01.0 PCI bridge: Intel Corporation 82845 845 (Brookdale) Chipset AGP Bridge (rev 04)
00:1d.0 USB Controller: Intel Corporation 82801CA/CAM USB (Hub #1) (rev 02)
00:1d.1 USB Controller: Intel Corporation 82801CA/CAM USB (Hub #2) (rev 02)
00:1d.2 USB Controller: Intel Corporation 82801CA/CAM USB (Hub #3) (rev 02)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev 42)
00:1f.0 ISA bridge: Intel Corporation 82801CAM ISA Bridge (LPC) (rev 02)
00:1f.1 IDE interface: Intel Corporation 82801CAM IDE U100 (rev 02)
00:1f.3 SMBus: Intel Corporation 82801CA/CAM SMBus Controller (rev 02)
00:1f.5 Multimedia audio controller: Intel Corporation 82801CA/CAM AC'97 Audio Controller (rev 02)
00:1f.6 Modem: Intel Corporation 82801CA/CAM AC'97 Modem Controller (rev 02)
01:00.0 VGA compatible controller: ATI Technologies Inc Radeon Mobility M7 LW [Radeon Mobility 7500]
02:00.0 CardBus bridge: Texas Instruments PCI1520 PC card Cardbus Controller (rev 01)
02:00.1 CardBus bridge: Texas Instruments PCI1520 PC card Cardbus Controller (rev 01)
02:02.0 Network controller: Intersil Corporation Prism 2.5 Wavelan chipset (rev 01)
02:08.0 Ethernet controller: Intel Corporation 82801CAM (ICH3) PRO/100 VE (LOM) Ethernet Controller (rev 42)
downest@thinkpad:~$ 



thanks in advance!

TD

---

### Post by id10t on 2007-03-22
My wireless problem also occured on an Intersil prism 2.5 based card. :(   Did your problem occur after you installed the updates?

---

### Post by downest on 2007-03-22
Guess I spent too much time on Gentoo... I found the built-in GUI and set it up... wireless is fine now.  I really want to get the monitor working now.

I installed Network Manager earlier at someone's suggestion, I think that made the GUI available, either that or I just overlooked it before.  For the GUI (Gnome), go to System > Administration > Network Manager and you can manually enter what you need.  I'm still not able to scan.  I've been told the card won't support scanning, but when I originally got the computer from my school (RPI) it was running XP and scanned fine.  I was confused because I'm used to Gentoo, which keeps a wireless config file in /etc/conf.d/ which doesn't exist in Ubuntu.

---

### Post by downest on 2007-03-22
Scratch that... I had to do updates and now it doesn't work.  Network Manager is now called "Network Tools" and displays 2 wired connections.

Edit: Maybe the name didn't change, and it's just not there now?  I got an error message that Network Tools was missing resources.

---

### Post by teryan2006 on 2007-03-22
Network Manager and Network Tools are different GUI utilities that perform the same function. Network Tool is the default GUI that comes with GNOME. Network-Manager is a newer tool which automatically switch between wired, wireless and access points w/o user intervention.

---

### Post by downest on 2007-03-22
Ok, but how do I get NM to run again?

---

### Post by id10t on 2007-03-23
Never mind it being a prism 2.5 its is a prism 1.  Makes me feel like my computer is ancient.

---

### Post by downest on 2007-03-23
Ok, got wireless back.  This may work for you too... try it.  I looked around and Network Manager's site mentions that the Prism cards have a conflict with 2 drivers: [here](http://live.gnome.org/NetworkManagerHardware).  I had some trouble disabling the driver at first, thinking it was the orinoco driver, it was telling me it's in use.  I looked around again and found that I had to blacklist the prism driver:

```
lsmod | grep prism
```

will return the name of the prism thing, in my case prism2_pci.

Then open up /etc/modprobe.d/blacklist and add 

```
blacklist prism2_pci
```

or whatever your thing returned.  Reboot and it's good to go.  Hope that helps you, the older Prism cards aren't mentioned in the NM list.

---

