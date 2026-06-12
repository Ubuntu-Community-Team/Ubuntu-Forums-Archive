---
title: "Sony Vaio WiF Problems"
date: 2007-10-28
forum: Hardware &amp; Laptops
---

### Post by daz4126 on 2007-10-28
I've managed to get a live CD working on my new Sony vaio, but Ubuntu doesn't pick up the wifi. It is using
Integrated Wireless LAN IEEE 802.11b/g
But when I click on the network button in the menu the only options are wired network (greyed out) or manual configuration. An older Toshiba laptop picked the wireless network up straight away, so I think the problem is with the vaio's hardware, although my searches on google seem to suggest that the Integrated Wireless LAN above is supported.

Anybody got any ideas?

Thanks,

DAZ

---

### Post by derick on 2007-10-28
I had the same issue with mine.   the command "lspci" told me it was a -

06:00.0 Network controller: Intel Corporation PRO/Wireless 4965 AG or AGN Network Connection (rev 61)

Reading through the forums, its not really supported well on 7.04.  The drivers for it are included in the 7.10 release, which is what I installed.  Working fine.

---

### Post by daz4126 on 2007-10-28
Thanks derick. I'm using 7.10 already, so do you think that my wireless controller will be supported eventually?

---

### Post by spier on 2007-10-28
> **daz4126 said:**
> But when I click on the network button in the menu the only options are wired network (greyed out) or manual configuration.

DAZ

I had the same issue after upgrading to Gutsy.
 First, tried to re-install NM from Synaptic. Then in the Manual config, selected Wireless connection's properties and checked Enabling roaming mode. These actions somehow corrected my wireless and it works now like in Feisty.

---

### Post by daz4126 on 2007-10-28
Using 'lspci', I found that it is actually:

Atheros Communications Inc, AR5006EG 802.11 b/g Wireless PCI Express Adapter

Will do some searching to find out more about its support. I don't want to wait for Hardy to be released before I can dump Vista for Ubuntu!

---

### Post by daz4126 on 2007-10-29
I´ve just checked the Restricted Drivers and there is just one entry:
Atheros Hardware Access Layer (HAL) which says that it is enabled and in use.
I am assuming that this is the Wifi card mentioned above, but it is definitely not working!

Help!!!!!

---

### Post by miwaypet on 2007-10-29
I am new to the Ubuntu experience. I have a one year old Sony vaio vgn fs980. When I first checked out 7.10 with live cd I also had no wireless. When I tried again with same cd, I had wireless. Decided to install. Blew out MS and installed 7.10. I had to run it in manuel mode. It picked up my router but no bars showed on desktop. WTF! Got in a jam like all good newbies and had to uninstall and reinstall. Guess what? Thats right, picked the wireless straight up. No probs since.  As a side note. have wpc54gx4 pc card. Used synaptic to install 'windws wireless drivers' manager. Put pc card disk in optical drive. Drag folders onto desktop and they are read instantly. Start the windows wireless driver apt and drag correct .inf file to open window. Picks up my pc card without a hitch. Have the best wirless now. Network manager in 7.10 picks up all wieless AP's within range. Best Ububtu experience yet. Thanx.

---

### Post by daz4126 on 2007-11-06
It turns out that my wifi card is being reported incorrectly and is in fact the Atheros AR5007 rather than the older AR5006. The drivers have not yet been ported over to madwifi yet, but should be soon. This means I need to use ndiswrapper to use the Windows drivers. Somebody kindly gave me the following instructions:

> Chipset: Atheros AR5007EG (rev 01)
PCI ID: 168c:001c

Download the windows 32-bit(or 64bit if you need) Wireless_Atheros ZIP drivers from here.

Download and install the last version of ndiswrapper (it works from 1.45 version), installation

Try to remove the module ath_pci to let ndiswrapper to use the wifi.
     "sudo rmmod ath_pci" or "sudo modprobe -r ath_pci"

also try put that module in the blacklist of modprobe to avoid his
loading on the startup:

          sudo nano /etc/modprobe.d/blacklist-common

Insert this line:
        blacklist ath_pci

Then restart.
When u will boot again.
Load the windows driver it from the uncompress folder:
       #ndiswrapper -i net5211.inf
 then install to modprobe
       #ndiswrapper -m

I had to install the latest version of ndiswrapper (the one in the repos is too old) and then followed the instructions. 

Still no wifi!

But....if I run 
```
ndiswrapper -l
```, I get
net5211 : driver installed
        device (168C:001C) present (alternate driver: ath_pci)

If I run
```
iwconfig[
```, I get
lo        no wireless extensions.

eth0      no wireless extensions.

If I have the drivers installed, does anybody know how I get Ubuntu to notice my wifi card and get connected????

cheers

---

### Post by arranmc182 on 2007-11-19
ndiswrapper will work or you can try going to [http://linuxwireless.org/](http://linuxwireless.org/) and downloading the Linux wirless drivers from there they worked 100% for me and works a lot better than ndiswrapper as it puts the drivers right in to the mian kernel and its all verry simple to install.

here is just some of the drivers u will get

b43/b43legacy (Broadcom chips)
ath5k (Atheros devices)
adm8211 (ADMtek devices)
madwifi (Atheros devices)
p54 (Intersil chips)

and there are even more drivers built in all you have to do us install it and linux will detect what driver is needed if you have compatable hardware

---

### Post by daz4126 on 2007-12-01
I tried this and it didn't work with my device, so I'm still with ndiswrapper.

Hopefully my device will be supported soon - I'll keep trying and hope that it is supported natively in hardy.

Thanks,

DAZ

---

### Post by chalewa on 2007-12-01
what sony are you trying to get this up and running with?

[http://ubuntuforums.org/showpost.php?p=3868406&postcount=48](http://ubuntuforums.org/showpost.php?p=3868406&postcount=48)


try to follow that.

---

