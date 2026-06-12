---
title: "No ethernet after installing 2.6.27-11"
date: 2008-12-20
forum: Installation &amp; Upgrades
---

### Post by schimschone on 2008-12-20
I have discovered that I have no ethernet support under the new kernel (2.6.27-11), however it works fine under the previous version. I have restarted several times, and I have tried reinstalling the new kernel.. still nothing.

Here's my chipset:

Broadcom Corporation BCM4312 802.11b/g (rev 01)
Realtek Semiconductor Co., Ltd. RTL8101E/RTL8102E PCI Express Fast Ethernet controller (rev ff)

and I'm on a Dell Mini 9, running x86 version of 8.10, if that helps.

At this point I've simply reedited GRUB to run the old kernel on startup. 

I'm open to any suggestions.. even the possibility that I missed something.

Thanks ahead a time, btw.

schim

---

### Post by abn91c on 2008-12-20
what happens if you do sudo dhclient eth0 in a terminal?

---

### Post by schimschone on 2008-12-20
Here ya go:

"Listening on LPF/eth0/00:21:70:d0:e6:98
Sending on   LPF/eth0/00:21:70:d0:e6:98
Sending on   Socket/fallback
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 8
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 7
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 9
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 9
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 14
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 14
No DHCPOFFERS received.
No working leases in persistent database - sleeping."

I have no idea what all this means though.. while I'm not a n00b I would probobly count as a n0b.. but I'm learning.

schim

---

### Post by abn91c on 2008-12-21
when you right click on the network icon top of the screen does it say manual configuration? If that is the case you may need to reset the network configuration file

---

### Post by abn91c on 2008-12-21
If you want to configure DHCP address you need to edit the /etc/network/interfaces and you need to enter the following lines replace eth0 with your network interface card

sudo vi /etc/network/interfaces

# The primary network interface - use DHCP to find our address
auto eth0
iface eth0 inet dhcp

---

### Post by Schulf on 2008-12-21
I can confirm the problem on a LG X110 Netbook. 

Setting dhcp in /etc/network/interfaces doesn't help.

I doubt it's an configuration error because the same configuration works with kernel 2.6.27-10-generic.

---

### Post by schimschone on 2008-12-21
Unfortunately it isn't even seeing that an ethernet cable is attached, thus there is no 'manual connect' prompt, and 'Auto eth0' just searches for the etehrnet connection without finding it .. at this point I think I'm sticking with 2.6.27-10 until these issues are ironed out, but I'm still open to any ideas.

schim

---

### Post by schimschone on 2008-12-26
Well as of the last time I checked.. about an hour ago, this problem has not been resolved through update. Now while I appreciate that we live in a wireless world, it seems fairly significant that ethernet support has been lost by at least a few in the community. 

Any ideas would be appreciated, and while I am n00b-ish, I am willing to learn. So again I holler into the electrical press and say "help".

schim

---

### Post by Schulf on 2008-12-28
Maybe it helps if i give some extra information about what i was able to find out so far.

It seems that the interface looses the ability to sense a cable.

The kernel sees the interface as always up although no connection to the switch exists.

once again i'll post the hardware information and kernel logs.

> 01:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL8101E/RTL8102E PCI Express Fast Ethernet controller (rev 02)

Working Kernel 2.6.27-10
> [    4.252365] r8169 Gigabit Ethernet driver 2.3LK-NAPI loaded
[    4.252405] r8169 0000:01:00.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[    4.252435] r8169 0000:01:00.0: setting latency timer to 64
[    4.252456] r8169 0000:01:00.0: unknown MAC (37a00000)
[    4.253373] eth0: RTL8169 at 0xf8838000, 00:21:85:dc:f0:b4, XID 34a00000 IRQ 221

> [   35.601150] r8169: eth2: link down

Not working Kernel 2.6.27-11
> [    4.689292] r8169 Gigabit Ethernet driver 2.3LK-NAPI loaded
[    4.689330] r8169 0000:01:00.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[    4.689358] r8169 0000:01:00.0: setting latency timer to 64
[    4.689378] r8169 0000:01:00.0: unknown MAC (37a00000)
[    4.690220] eth0: RTL8169 at 0xf884a000, 00:21:85:dc:f0:b4, XID 34a00000 IRQ 221

> [   36.621050] r8169: eth2: link up

The only difference i could find was this strange link up during boot without a cable connected. 

Thats it from me. Maybe im just not seeing the simple solution, but i dont have the time right now to search for the problem myself.

Schulf

---

### Post by rfaull on 2008-12-28
I can confirm same problem on an Acer Aspire One running 8.10. Kernel 2.6.27-10 work, 2.6.27-11 no Ethernet, wireless ok.:(

---

### Post by SylverRat on 2008-12-28
same here, msi wind.
back to 2.6.27-9.

---

### Post by schimschone on 2008-12-30
Well it was suggested from someone here: 

[http://groups.google.com/group/UbuntuMini/browse_thread/thread/7dc4e9314301e7b6?hl=en](http://groups.google.com/group/UbuntuMini/browse_thread/thread/7dc4e9314301e7b6?hl=en)

.. That a fresh install cleans up this issue.

However I will mention that this is not an upgrade, and is purely related to the new kernel (2.6.27-11) on 8.10, and happened after the fix of the wifi after an incomplete package install. 

The best guess I've heard is that there is a hardware driver that's as corrupt as an Illinois governor.. however one difference I've noted is that I get no ethernet even when booting with the cable installed.

So next the sledgehammer.. I will do a fresh install come this weekend, but I don't really consider this a solution any more than I would consider our economic collapse a solution to our dependence on oil.

---

### Post by rfaull on 2009-01-01
Sometimes, just sometimes (maybe twice), my AA1 running 2.6.27-11 has loaded the Ethernet module and eth1 is active, displaying in Network Manager as 'greyed' but will connect if a cable is connected. The module always loads using 2.6.27-10. Strange! Anyone else experience is?

---

### Post by davidself1001 on 2009-01-02
Just completed the 8.10 upgrade from 8.04 and have the same problem.  I have a gnome-netstatus applet and a network manager applet in the systray. The gnome-netstatus applet shows eth0 but the netmanager applet shows no eth0.  Also note that I don't have a net configuration item showing up in the system preferences either.  I have access to the internet but no way to setup network config for my local lan, etc.

---

### Post by Mr_Mirsal on 2009-01-04
Same here, MSI Wind U100X, is there a LP entry for this bug ?

---

### Post by rfaull on 2009-01-04
Bug reported today at [https://bugs.launchpad.net/ubuntu/+bug/313866](https://bugs.launchpad.net/ubuntu/+bug/313866)

---

### Post by powdermaniaDE on 2009-01-08
I can confirm the problem on a Lenovo Thinkpad T61

Setting dhcp in /etc/network/interfaces doesn't help.

I doubt it's an configuration error because the same configuration works with kernel 2.6.27-10-generic.

---

### Post by powdermaniaDE on 2009-01-08
Problem solved. 
But it had nothing to do with the kernel update...our institutional dhcp server was producing the error. I didn't get a valid ip adress on reboot. Static ip works.

---

### Post by Schulf on 2009-01-11
Fixed. Latest Kernel Update fixed the problem - at least for me.

---

### Post by jeperezd on 2009-01-12
I still have the issue on my MSI Wind. I tried to compile the driver I downloaded from Realtek and worked only during the first reboot. I also tried to add NOAPIC parameter to the kernel and only worked the first reboot as well. 
With the Live CD it works fine, so it's not hardware problem. My intrepid is full up to date.

---

### Post by zero_gravity on 2009-01-20
I also have this problem with the current intrepid kernel on my dell mini 9. 2.6.27-7 works fine, though.

---

### Post by ge0rdie on 2009-01-29
Same prob here MSI U100
Aditionally, if I plug in my Belkin USB 10/100 dongle, the NetworkManager picks it up no probs at all, so the prob is directly related to the card and not just the kernel.

---

### Post by ge0rdie on 2009-01-29
FYI: after plugging in my Belkin 10/100 dongle, I checked for updates, there was a new kernel,  I downloaded it and it has fixed the problem for me.  (2.6.27-11.27 I think)


If you are into Linux, I recommend you get a usb 10/100 dongle, it has saved me soooo many times.  When you have trouble with dodgy NIC's you can plug it in to download updates, drivers, compilers etc to fix your problems.

---

### Post by dave_i on 2009-01-31
Anyone had any luck fixing this yet? I noticed exactly the same thing - the ethernet on my Acer Aspire One didn't work after the 2.6.27-11 kernel upgrade. I'm using 2.6.27-9 at the moment and it's working fine. My system is up to date (as of 5 minutes ago), and the wireless is fine.

The lights on the ethernet port aren't coming on when I plug in the cable in 2.6.27-11, but it's fine in 2.6.27-9.

---

### Post by DimitrisC on 2009-01-31
I installed the kernel 2.6.27.11 on my msi wind last night using the ethernet.  When I rebooted after the update the ethernet was still working.  However this morning when I plugged in my pc to the wired network I realised that the ethernet was dead.  I tried booting with the ethernet cable plugged in but still haven't been able to get it to work.  I also booted using up the 2.6.27.9 kernel but the ethernet is not working?  Any ideas?  Other people say that booting a previous kernel solves the issue but that hasn't worked for me.  Is there any config files that I should delete that may cause the problem to occur even with the 2.6.27.9 kernel? Thanx.

---

### Post by schwal on 2009-01-31
It seems to work after it is disabled and then re-enabled, for example by plugging in an external wifi device. you probably have to do this after every reboot, so it's not a permanent solution.

---

### Post by infraction on 2009-02-01
And here's a wrinkle.  Installed 2.6.27-11 on Ubuntu running under Wubi.  Now boot into WIN XP and ethernet is broken there as well.  Apparently the Ethernet card is somehow being quite disabled, regardless of OS.

Guess I need to back up to kernel -9 and hope that fixes the problem for both OS's.

Nice work, Debian!!!!!!!!!!!!!!!!

---

### Post by Mike DrGK on 2009-02-02
+1

My MSI Wind U100 cannot connect any more after installing the 2.6.27-11 Kernel using the eth0 connection.

My wireless connection works fine.

---

### Post by Mike DrGK on 2009-02-02
After disabling auto settings and setting manual settings to eth0, it looks that it is connected.

But it is no possible to communicate with any other network device (the router eg).

---

### Post by ericle77 on 2009-02-02
i have a acer one install update 2.6.27.11 and lost the network
connection but still working in 2.6.27.7

---

### Post by xircon on 2009-02-02
Me too Advent 4211 Netbook (MSI Wind clone), wireless fine no ethernet.

[http://forums.msiwind.net/viewtopic.php?f=7&t=8216&sid=cbe6c6784fce8b750e934e5ec65bfc04](http://forums.msiwind.net/viewtopic.php?f=7&t=8216&sid=cbe6c6784fce8b750e934e5ec65bfc04)

Thread about the problem from the wind forum.

---

### Post by em4r1z on 2009-02-02
My problem is related: I can connect through Ethernet but it's not handled by the Network Manager (the option is grayed out.) The Network Manager detects the wireless connections. It worked flawlessly with the previous kernel.

AMD64 Mobile, Ubuntu 8.10 64-bit, NVIDIA chipset, kernel 2.26.27-11.

---

### Post by dxd_2009 on 2009-02-06
My First post



I fix it !!!!!!!!

go to Bios 


1


[http://www.freeimagehosting.net/uploads/c5b365b1ba.jpg](http://www.freeimagehosting.net/uploads/c5b365b1ba.jpg)





2


[http://www.freeimagehosting.net/uploads/a618cee753.jpg](http://www.freeimagehosting.net/uploads/a618cee753.jpg)


Not all Bios are same     :)

---

### Post by gian on 2009-02-06
same here, mean no eth0 on Acer One after kernel upgrade

---

### Post by optimisteo on 2009-02-06
Same issue here with 8.10 64bits on a Thinkpad T61
Intel Corporation 82566MM Gigabit Network Connection (rev 03)
 
kernels 2.6.27.8  2.6.27.10   2.6.27.11

did not test with 2.6.27.7 ...

had to revert to 2.6.24.21 for eth0 to start working again.

eth0 doesn't work (doesnt react when eth cable plugged), yet appears in ifconfig and lspci


I can see that from the very early stages of bootup the two eth leds light, become still and hang up in that state.


Regards,

---

### Post by Hermes87 on 2009-02-09
I am experiencing the same problem on a Dell Mini 9 running 8.10 with kernel 2.6.27-11 generic. A recent round of updates (incl. kernel updates) did not resolve the problem

---

### Post by geroad on 2009-02-09
> **schimschone said:**
> Unfortunately it isn't even seeing that an ethernet cable is attached, thus there is no 'manual connect' prompt, and 'Auto eth0' just searches for the etehrnet connection without finding it .. at this point I think I'm sticking with 2.6.27-10 until these issues are ironed out, but I'm still open to any ideas.

schim
I had the same problem with my wireless not being recognized. This is my info...
Ethernet controller [0200]: Atheros Communications Inc. Atheros AR5001X+ Wireless Network Adapter [168c:0013] (rev 01)
I stumbled on this when reading another post about a freezing problem.........

Verify you don't have Intel 4965 wireless chipsets

If so follow the release notes for 8.10 and install linux-backports-modules-intrepid
run this code in your terminal......
********************
Code:

sudo apt-get install linux-backports-modules-intrepid

***************


this fixed the wireless problem.

---

### Post by odium1 on 2009-02-11
well i downloaded **kernelcheck** and let it find the latest kernel and install it (2.6.28-4) and it cleared up my ethernet problem. i had read somewhere that jaunty used the newest kernel and that people who were using that kernel weren't experiencing this problem, so i gave it a shot.. my first idea was to install jaunty alpha 4 but after a little research i found kernelcheck. going about it that way probably saved me a boatload of time heh..

---

### Post by Hermes87 on 2009-02-15
I also used kernelcheck to upgrade the kernel to 2.6.28.5, I was able to restore the ethernet. However this broke the wireless- had to reload the driver but now its working.

---

### Post by slamelov on 2009-02-16
Same problem here, Acer Spire One
[http://ubuntuforums.org/showthread.php?t=1070062](http://ubuntuforums.org/showthread.php?t=1070062)

---

### Post by seventhfire on 2009-02-16
I have the same/similar  problem with a U120 MSI
If I boot with 2.6.27-7 I both wired and wireless work
If I boot with 2.6.27-11 I wired will no longer work but wireless does.
If I knew how to display the chipset I'd do so but new to ubuntu

---

### Post by dave_i on 2009-02-19
Upgrading to 2.6.28.6-ultimate fixed the problem on my Acer Aspire One.

---

### Post by bod on 2009-02-21
> **dave_i said:**
> Upgrading to 2.6.28.6-ultimate fixed the problem on my Acer Aspire One.

Great.
Or it would be if I had a clue where to find 2.6.28.6-ultimate! Googling it returns one result - this thread :-|

---

### Post by bod on 2009-02-22
Went with the sickboy/kuki kernel in the end, has brought my ethernet back at least. Will see how it goes under normal usage this week.

[http://www.aspireonekernel.com/](http://www.aspireonekernel.com/)

---

### Post by gazzatav on 2009-02-23
I have no ethernet on my pc.  The network-admin applet has a greyed out 'unlock' button.  I use a fixed IP.

---

### Post by namerandom on 2009-02-28
Ditto the last post.

After I install 8.10 it insists on doing updates or the package install tool will not find any other packages (emacs, g++, etc.).  After the update the ethernet stops working so one can not install any new packages then either.  

The update after install lists many things that don't look like updates but rather things left out of base.  

In any case I went through the long list and unchecked everything that could be related to breaking ethernet.  After 30 minutes the update tool kindly updated the update list and rechecked everything I had just unchecked. Am I going to spend another 30 minutes ... guess I can't as the cafe is closing.  

Absolutely madenning!!!  Updates break the networking, the package manager refuses to find packages until updates are run, and the update tool insists on changing my selections for updating so I can't get around the problem!  Yes, the original problem is bad but the madenning part is that it is impossible to get around it because of what appear to be human chosen "features" in Ubuntu.  I.e. one should be able to run the system without running updates,  one should be able to install more packages without running updates.  One should be able to leave the update list on the screen without fighting the Ubuntu over what is check marked for days or however long it takes.  

I could see a message perhaps that says more updates available, but not a system that fights the user as if saying, no no you must check this, and this, and this.  Why? Because it is an imperfect world.  In a perfect world these "features" would make sense.  But in our world sometimes things go wrong and the administrator installing the system needs to be able to get around them when they do.

---

### Post by iKevin on 2009-03-01
I am having the same problem with the Little Falls MoBo.  It has the same Realtek chipset that most in this thread have.  When investigating, I found a ubuntu bug report and it is apparently fixed in the next kernel release.  

Here is the bug report:

[https://bugs.launchpad.net/ubuntu/intrepid/+source/linux/+bug/326891](https://bugs.launchpad.net/ubuntu/intrepid/+source/linux/+bug/326891)

---

### Post by RTrev on 2009-03-18
Reading the above bug report suggests that a -13 kernel has been found, in the last week or so, to fix the no-wired-ethernet problem.  I'd guess we should be seeing this as an available update in the near future?

---

### Post by fonsi2099 on 2009-03-20
The same problem, no eth0 is working and wireless network with laptop is working well.
(the ethernet stops working so one can not install any new packages then either).

:( Fonsi

---

### Post by Pedro P. Caro on 2009-03-22
As it's proposed in many of these posts, my opinion is that the problem comes from the kernel 2.6.27-11. However, anyone of you might be interesting in the following observation: if you boot with an old kernel (my case 2.6.27-7), you connect to Internet by cable, and afterward you reboot with the kernel 2.6.27-11; then the cable connection works. Unfortunately, when you boot your computer in the next day this connection won't work any more.

Does it give you any clue about the problem comes from?

---

### Post by RTrev on 2009-03-22
> **Pedro P. Caro said:**
> As it's proposed in many of these posts, my opinion is that the problem comes from the kernel 2.6.27-11. However, anyone of you might be interesting in the following observation: if you boot with an old kernel (my case 2.6.27-7), you connect to Internet by cable, and afterward you reboot with the kernel 2.6.27-11; then the cable connection works. Unfortunately, when you boot your computer in the next day this connection won't work any more.

Does it give you any clue about the problem comes from?

Hmm.  I'm unable to duplicate this.  2.6.27-7 works fine, but the restart into 2.6.27-11 still fails to connect with a wired connection.

This is on a Dell Mini-9 if that's pertinent.

---

### Post by dunbrokin on 2009-03-22
> **rfaull said:**
> Sometimes, just sometimes (maybe twice), my AA1 running 2.6.27-11 has loaded the Ethernet module and eth1 is active, displaying in Network Manager as 'greyed' but will connect if a cable is connected. The module always loads using 2.6.27-10. Strange! Anyone else experience is?

I have the same problem, I can access the net using the cable but not the wireless - the wireless is greyed out. However, I cannot access the net using wireless with either 2.6.27.10 nor if I try and use 8.10 live disk.

---

### Post by fonsi2099 on 2009-03-23
The reinstall does work well for me! I reinstall the same Jaunty again (release downloaded am 15.03.09)  and the wired network eth0 is working, every thing is working well.
After installing I did: sudo apt-get update, and sudo apt-get upgrade and it works after rebooting too. This is the way to save time many, many time. I don't why the first time it doesn't work correctly.

---

### Post by herbie_popnecker on 2009-03-26
Glad to know I'm not the only one with the problem... I will hold off until next month's release and see if that fixes the problem. I don't want to reinstall all my damned other goodies...

---

### Post by verlyn13 on 2010-05-07
I am having the same problem after installing 10.04.  (It has now been officially released).  It detects my wireless adapters, but no eth0 available.  

My wired connections has worked fine for all previous Ubuntu installations over the last 2 years. This seems more like a step backwards than a step forwards.

Perhaps I overlooked it, but was there a clear solution to this problem in this thread?

---

### Post by pirron on 2010-06-16
I have the same problem with Ubuntu 10.04. Wireless is working but I don't have ethernet.
 
Here is my lspci

00:00.0 Host bridge: Intel Corporation Mobile PM965/GM965/GL960 Memory Controller Hub (rev 0c)
00:02.0 VGA compatible controller: Intel Corporation Mobile GM965/GL960 Integrated Graphics Controller (rev 0c)
00:02.1 Display controller: Intel Corporation Mobile GM965/GL960 Integrated Graphics Controller (rev 0c)
00:1a.0 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #4 (rev 03)
00:1a.1 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #5 (rev 03)
00:1a.7 USB Controller: Intel Corporation 82801H (ICH8 Family) USB2 EHCI Controller #2 (rev 03)
00:1b.0 Audio device: Intel Corporation 82801H (ICH8 Family) HD Audio Controller (rev 03)
00:1c.0 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 1 (rev 03)
00:1c.1 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 2 (rev 03)
00:1c.2 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 3 (rev 03)
00:1d.0 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #1 (rev 03)
00:1d.1 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #2 (rev 03)
00:1d.2 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #3 (rev 03)
00:1d.7 USB Controller: Intel Corporation 82801H (ICH8 Family) USB2 EHCI Controller #1 (rev 03)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev f3)
00:1f.0 ISA bridge: Intel Corporation 82801HEM (ICH8M) LPC Interface Controller (rev 03)
00:1f.2 IDE interface: Intel Corporation 82801HBM/HEM (ICH8M/ICH8M-E) SATA IDE Controller (rev 03)
00:1f.3 SMBus: Intel Corporation 82801H (ICH8 Family) SMBus Controller (rev 03)
02:00.0 Network controller: Intel Corporation PRO/Wireless 4965 AG or AGN [Kedron] Network Connection (rev 61)
06:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL8101E/RTL8102E PCI Express Fast Ethernet controller (rev 01)
08:07.0 CardBus bridge: Texas Instruments PCIxx12 Cardbus Controller
08:07.1 FireWire (IEEE 1394): Texas Instruments PCIxx12 OHCI Compliant IEEE 1394 Host Controller
08:07.2 Mass storage controller: Texas Instruments 5-in-1 Multimedia Card Reader (SD/MMC/MS/MS PRO/xD)

And I also tried "ethtool -i eth0" and here is the output
driver: r8169
version: 2.3LK-NAPI
firmware-version: 
bus-info: 0000:06:00.0

---

### Post by pirron on 2010-08-17
I found a way to make ethernet work. I just disable the wireless network (Right-click at Network Manager icon) and I am back online.

---

