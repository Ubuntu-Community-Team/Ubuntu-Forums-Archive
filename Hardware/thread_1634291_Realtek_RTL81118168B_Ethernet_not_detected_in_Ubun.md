---
title: "Realtek RTL8111/8168B Ethernet not detected in Ubuntu 10.10(64bit)"
date: 2010-11-30
forum: Hardware
---

### Post by sanjayav on 2010-11-30
I have a HP DV6 3122TX Laptop. I installed Ubuntu 10.10 64 bit version. Right after installation the ethernet card worked properly, detecting the ADSL connection. After installing updates, I rebooted the machine. After that the internet connection was not detected.  

OS Details:
> 2.6.35-22-generic x86_64 GNU/LinuxNetwork Card:
> Ethernet controller: Realtek Semiconductor Co., Ltd. RTL8111/8168B PCI Express Gigabit Ethernet controller (rev 03)Any help on solving this issue is greatly appreciated. I tried re-installing Ubuntu but the issue is still there. Please note that I have no way of connecting the the internet from this laptop as it has issues with the wireless adapter as well.

---

### Post by mickhill on 2010-12-27
[B]_This worked for me!_
[/B]

**This is how you fix it.**


[LIST]
[*]First, remove the r8169 module from the linux kernel.
[/LIST]
[INDENT]# rmmod r8169
[/INDENT]
[LIST]
[*]Download the official realtek driver from [here]("http://www.realtek.com/downloads/downloadsView.aspx?Langid=1&PNid=5&PFid=5&Level=5&Conn=4&DownTypeID=3&GetDown=false#RTL8111B/RTL8168B/RTL8111/RTL8168%3Cbr%3ERTL8111C/RTL8111CP/RTL8111D%28L%29%3Cbr%3ERTL8168C/RTL8111DP")
[*]Unpack  the download and install the driver as per the readme instructions  included with the driver. Here’s the relevant part of the readme file;  well, the “Quick Install” anyway:
[/LIST]
[INDENT]<Quick install with proper kernel settings>
Unpack the tarball :
# tar vjxf r8168-8.aaa.bb.tar.bz2
Change to the directory:
# cd r8168-8.aaa.bb
If you are running the target kernel, then you should be able to do :
# ./autorun.sh	(as root or with sudo)
You can check whether the driver is loaded by using following commands.
# lsmod | grep r8168
# ifconfig -a
If there is a device name, ethX, shown on the monitor, the linux
driver is loaded. Then, you can use the following command to activate
the ethX.
# ifconfig ethX up
[/INDENT]
[LIST]
[*]Finally, blacklist the r8169 driver add the following to /etc/modprobe.d/blacklist.conf:
[/LIST]

[INDENT]#blacklist r8169 driver
blacklist r8169


[]("http://www.rvdavid.net/how-to-get-gigabit-speeds-from-rtl81118168b-pci-express-gigabit-ethernet-controller-on-ubuntu-linux/")[http://www.rvdavid.net/how-to-get-gigabit-speeds-from-rtl81118168b-pci-express-gigabit-ethernet-controller-on-ubuntu-linux/](http://www.rvdavid.net/how-to-get-gigabit-speeds-from-rtl81118168b-pci-express-gigabit-ethernet-controller-on-ubuntu-linux/)




[/INDENT]

---

### Post by Junge on 2010-12-28
This didn't work for me at all...

At first the r8169 kept loading, even when I blacklisted it. I found out that it was in initrd.img, so I removed it there. 

Now the big problem is that it loads the r8168 module, and not the r8169 module anymore, but that the thing still doesn't work. It's especially frustrating since I it used to work like a charm and that probably some update messed the whole thing up.

Anything like sudo ifconfigh eth0 up simultaneously brings eth0 down en gives the following message in my syslog.

r8168: eth0: link down
ADDRCONF(NETDEV_UP): eth0: link is not ready

I even changed the cable and that didn't solve the problem either.


Does anyone have any hints or could point me in the right direction?

---

### Post by radicalyffe on 2011-02-13
Hiya,

I'm a bit of a newbie, muddling along as best I can - been having some trouble with my network connection though.

I am running Ubuntu 10.10 (64bit) with the same ethernet card as Junge. I've had some trouble with it from the beginning - but over the last couple of days it stopped detecting the ethernet cable at all. I thought maybe it was the hardware itself that was faulty, and decided to google the name to find the manufacturers website to check the warranty, which is what brought me to this page.

I tried the fix posted by mickhill to see whether it might help, and installed the latest driver from the realtek website - version r8168-8.021.00.tar.bz2

That seemed to go fine, and the 'Additional Drivers' app from the System menu reports that the driver is installed, but when I plugged in the ethernet cable and tried to connect it still wasn't detecting the cable.

I rebooted my machine to see if that would help, and my screen resolution has changed, and I can no longer use the highest resolution for my monitor. I'm confused about how uninstalling and reinstalling a driver for my ethernet card might effect my computers screen resolution.

Does anyone know? Is there any information I could provide that would assist you in answering my question?

Also, any assistance you can provide in helping me resolve the initial problem (computer not detecting ethernet cable plugged into realtek card), or the new problem (screen resolution cannot be set higher than 1440x900) would be most appreciated.

Cheers
-Ryan

Additional Details that might be handy:

Kernel version: Linux 2.6.35.25-generic
Monitor: LG W2442PA
Video driver: ATI/AMD proprietary FGLRX graphics driver

---

### Post by radicalyffe on 2011-02-16
So a bit of an update.

I turned off my computer and unplugged it from the powerpoint, and then turned it on again and have my ethernet connection back now.

I'm very pleased about this.

However, my graphics are still messed up. I can no longer run two monitors, and my screen resolution is still really low.

Anyone got any ideas how this might have happened?

Ryan

---

### Post by Cean on 2011-03-10
I have a very similar problem, as posted [here]("http://ubuntuforums.org/showthread.php?t=1701561"). My computer isn't a laptop, but I have a Realtek RTL8111DL. I've tried installing the r8168 drivers and done a number of other 'weird fixes' that seem to work for other people. I still haven't been able to find a solution that works for me.

---

### Post by radicalyffe on 2011-03-10
Have you tried unplugging it from the powerpoint leaving it for a bit, and then turning it back on again?

I'm still having intermittant ethernet trouble, but that seems to work. Turning it off without unplugging the powerpoint doesn't work though.

---

### Post by kubilay@xanadu on 2011-03-11
Hi there

I had the same problem with my Lenovo Thinkpad SL510 and Ubuntu 10.10 64 bit. It seems like the Wireless hardware is not recognised. I have contacted Realtek and gave them the output of my 'lspci' command and they have recommended me to download **RTL8188CE** driver for Linu[FONT=Times New Roman][SIZE=2][COLOR=black]x kernel 2.6.x [COLOR=black][/COLOR][/COLOR][/SIZE][/FONT]from their site and install it. I have seen others in this forum have done the same and got their wireless adapter working. I will try the driver they told me to use tonight and keep you updated. 

This is the Realtek email you write to: **wlanfae@realtek.com**

I hope this helps

Kubilay

---

### Post by Cean on 2011-03-11
Try installing WICD. It worked for me.

---

### Post by UltimateCat on 2011-12-23
> **kubilay@xanadu said:**
> Hi there

I had the same problem with my Lenovo Thinkpad SL510 and Ubuntu 10.10 64 bit. It seems like the Wireless hardware is not recognised. I have contacted Realtek and gave them the output of my 'lspci' command and they have recommended me to download **RTL8188CE** driver for Linu[FONT=Times New Roman][SIZE=2][COLOR=black]x kernel 2.6.x [/COLOR][/SIZE][/FONT]from their site and install it. I have seen others in this forum have done the same and got their wireless adapter working. I will try the driver they told me to use tonight and keep you updated. 

This is the Realtek email you write to: **wlanfae@realtek.com**

I hope this helps

Kubilay
I have the ( pretty much ) the same problem ; only have the RTL8111/8168B-

Found that other members have similar problems/symptoms but I haven't found the solution yet-

If you find a solution to the diagnosis please post it.   I have not been able to (for going on 4-5 weeks now) get my Linux/Ubuntu; UE 2.7 online.

Being a newbie is extremely challenging at times.

Wish you the best

---

### Post by UltimateCat on 2011-12-28
:)Hi!
I too have had this problem with this RTL8111.....etc.

Does anyone know; does it matter that I have 10.04?

I am wondering because I'D like to follow the instructions that a member posted for his 10.10-...
Sincerely,
UltimateCat

---

