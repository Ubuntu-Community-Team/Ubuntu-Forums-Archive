---
title: "Unable to install/configure wireless adapter/driver"
date: 2010-03-29
forum: Hardware
---

### Post by jt1990 on 2010-03-29
[FONT=Verdana]Hi all!

I'm brandy new to Ubuntu, so I really have no clue what I'm doing.

[SIZE=1]I'm running Ubuntu 9.1[/SIZE]0 on a Compaq Presario C500, and I can't get the wireless installed right.  At least, I think that's my issue.  I did some hunting, and found the ndisgtk program for installing Windows drivers.  I installed it (I think) properly, and tried to use the INF file for the wireless.  However, when I go to the Windows Wireless Drivers under Administration, I get an error saying "Unable to see if hardware is present."  I click "ok" and the message goes away, and under the list of Currently Installed Windows Drivers, I get "bcmwl6" (which I assume is the network adapter) and it says "Hardware present: Yes".  I click on "Configure Network" and I get an error saying "Could not find a network configuration tool."  

Also, when I click on the network connections icon on the top right hand of the screen, under "Wireless Networks" it says "device not ready."

I CAN get online using a wired connection, but a wireless connection would be a WHOLE lot more convenient.  

I the "lspci" command to get a list of the hardware config, here is what it gave me:

[/FONT]    [FONT=Verdana][SIZE=1]00:00.0 Host bridge: Intel Corporation Mobile 945GM/PM/GMS, 943/940GML and 945GT Express Memory Controller Hub (rev 03)[/SIZE][/FONT]
  [FONT=Verdana][SIZE=1]00:02.0 VGA compatible controller: Intel Corporation Mobile 945GM/GMS, 943/940GML Express Integrated Graphics Controller (rev 03)[/SIZE][/FONT]
  [FONT=Verdana][SIZE=1]00:02.1 Display controller: Intel Corporation Mobile 945GM/GMS/GME, 943/940GML Express Integrated Graphics Controller (rev 03)[/SIZE][/FONT]
  [FONT=Verdana][SIZE=1]00:1b.0 Audio device: Intel Corporation 82801G (ICH7 Family) High Definition Audio Controller (rev 01)[/SIZE][/FONT]
  [FONT=Verdana][SIZE=1]00:1c.0 PCI bridge: Intel Corporation 82801G (ICH7 Family) PCI Express Port 1 (rev 01)[/SIZE][/FONT]
  [FONT=Verdana][SIZE=1]00:1c.2 PCI bridge: Intel Corporation 82801G (ICH7 Family) PCI Express Port 3 (rev 01)[/SIZE][/FONT]
  [FONT=Verdana][SIZE=1]00:1d.0 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #1 (rev 01)[/SIZE][/FONT]
  [FONT=Verdana][SIZE=1]00:1d.1 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #2 (rev 01)[/SIZE][/FONT]
  [FONT=Verdana][SIZE=1]00:1d.2 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #3 (rev 01)[/SIZE][/FONT]
  [FONT=Verdana][SIZE=1]00:1d.7 USB Controller: Intel Corporation 82801G (ICH7 Family) USB2 EHCI Controller (rev 01)[/SIZE][/FONT]
  [FONT=Verdana][SIZE=1]00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev e1)[/SIZE][/FONT]
  [FONT=Verdana][SIZE=1]00:1f.0 ISA bridge: Intel Corporation 82801GBM (ICH7-M) LPC Interface Bridge (rev 01)[/SIZE][/FONT]
  [FONT=Verdana][SIZE=1]00:1f.1 IDE interface: Intel Corporation 82801G (ICH7 Family) IDE Controller (rev 01)[/SIZE][/FONT]
  [FONT=Verdana][SIZE=1]00:1f.2 SATA controller: Intel Corporation 82801GBM/GHM (ICH7 Family) SATA AHCI Controller (rev 01)[/SIZE][/FONT]
  [FONT=Verdana][SIZE=1]00:1f.3 SMBus: Intel Corporation 82801G (ICH7 Family) SMBus Controller (rev 01)[/SIZE][/FONT]
  [FONT=Verdana][SIZE=1]06:00.0 Network controller: Broadcom Corporation BCM4311 802.11b/g WLAN (rev 01)[/SIZE][/FONT]
  [FONT=Verdana][SIZE=1]08:08.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL-8139/8139C/8139C+ (rev 10)[/SIZE][/FONT]
  [FONT=Verdana]
Could anyone please help me with this?
[/FONT]

---

### Post by 2hot6ft2 on 2010-03-29
> **jt1990 said:**
> 
  [FONT=Verdana][SIZE=1]06:00.0 Network controller: **Broadcom** Corporation **BCM4311** 802.11b/g WLAN (rev 01)[/SIZE][/FONT]

There's a guide for your adapter here:
[The Definitive 9.10 Broadcom Solution Guide]("http://ubuntuforums.org/showthread.php?t=1368699") 
And welcome to the forum and ubuntu.

---

### Post by coffeecat on 2010-03-29
Your wireless card is:

> **jt1990 said:**
> [FONT=Verdana][SIZE=1]06:00.0 Network controller: Broadcom Corporation BCM4311 802.11b/g WLAN (rev 01)[/SIZE][/FONT]

According to this page:

[https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx](https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx)

... your wireless chipset (BCM4311) doesn't need ndiswrapper/ndisgtk, so you can save yourself a few tears with that. :)

That link is a bit badly laid out, imo. What you need to do, as far as I can see, is to go down to "CDROM/DVD". To clarify, boot into your intalled Ubuntu, insert the live CD into the optical drive, open System > Administration > Synaptic, and then:

> 
**Step 1.** Install the bcmwl-kernel-source package using the Synaptic Package Manager. First select **Add CD-ROM** from the edit menu to enable the install media as a package repository, then click on **Reload** to refresh the available packages list, ignore any internet/download errors. Now search for the bcmwl-kernel-source package and install. 
**Step 2:** Under the desktop menu **System > Administration > Hardware Drivers**, the drivers can be activated for use. 
**Note:** A computer restart may be required before using the wifi card. FYI - there are licensing issues with the Broadcom firmware which is why you have to go through these contortions.

---

### Post by jt1990 on 2010-03-29
OK.... I did that, and the device now shows up in Hardware Drivers saying "This driver is activated but not currently in use."

When I run "sudo lshw -c network" in the terminal, it tells me that the network adapter is unclaimed.  The help section (which I've been all over) says that this means that there's no driver for the card.  What is going on here?  I'm rather confused...

EDIT:  Thank you both very much for your quick responses! :-)

---

### Post by Naggobot on 2010-03-29
Proprietary drivers are activated from 
system -> administration -> hardware drivers

If the driver is not visible then select search

If the driver is still not visible, then hook up wire to internet. All of the broadcom drivers are not distributed with the Ubuntu. At least I have understood that there are some lisence issues. I my self ended up installing 9.10 twice when I did not realize this little detail at the time.

Please everyone, feel free to correct me if I am wrong.

---

### Post by coffeecat on 2010-03-29
> **jt1990 said:**
> OK.... I did that, and the device now shows up in Hardware Drivers saying "This driver is activated but not currently in use."

I think you need to reboot.

---

### Post by jt1990 on 2010-03-29
> **coffeecat said:**
> I think you need to reboot.

I already tried that, but I'm trying it again...

---

### Post by jt1990 on 2010-03-29
> **Naggobot said:**
> Proprietary drivers are activated from 
system -> administration -> hardware drivers

If the driver is not visible then select search


The driver is showing up in Hardware Drivers, but it's "not currently in use"

I just finished restarting again, still no luck.  Is there some command or something that I need to run to tell the card to use the driver?:-?

---

### Post by Naggobot on 2010-03-29
This may sound really obvious but have you tried clicking it with both right and left mouse buttons to see if you can get it working. 

There should be no extra commands required, Coffeecat may know better, I am just a noob. 

I have on both of my occasions managed to get broadcom wireless working just be updating the system from 

system -> administration -> update manager

and 

system -> administration -> hardware drivers. 

Granted, I did redo my second laptop installation with wired connection so that the installer used b43-fwcutter tool to download correct proprietary drivers from Internet, but to my understanding reinstallation was unnecessary. 

I hesitate to comment more so that I won't mess up anything. Coffeecat can give more definite advise.

---

### Post by coffeecat on 2010-03-29
I wonder if the ndiswrapper windows driver is conflicting with the Linux Broadcom driver that you've installed. Sorry - have no experience of ndiswrapper/ndisgtk so I wouldn't know how to uninstall the Windows driver.

---

### Post by jt1990 on 2010-03-30
Thank you all for your assistance! :)  I've just finished reinstalling Ubuntu, and I'm going to try installing the card using the above method - we'll see if that works.  

Thanks!

---

### Post by jt1990 on 2010-03-30
It worked!  Excellent!  Thank you all very much!  I'll definitely be back here... :D

---

