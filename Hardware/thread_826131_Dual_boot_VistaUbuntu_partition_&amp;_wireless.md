---
title: "Dual boot Vista/Ubuntu partition &amp; wireless"
date: 2008-06-11
forum: Hardware
---

### Post by jcat1 on 2008-06-11
Hello All,

I'm currently considering switching my system Lenovo t61 to dual boot status with Vista/Ubuntu Hardy 8.04 but there are a couple of questions I have before doing so:

First, I will need to have a shared partition which will contain all of my documents and other files that is accessible from both the Ubuntu and Vista environments.  Should I make this shared partition a FAT32 or NTFS format?  From  what I have read, getting Ubuntu to work with NTFS requires some sort of software workaround whereas FAT32 is supported natively.  What would you  recommend?

Second, when using the LiveCD, I can't see any wireless networks.  It appears that my wireless card is recognized as I can pull up the menu options wireless networking, but there are no networks to select (I have the Intel ABGN version of the wireless card).

Any help/advice you can provide on either or both questions is greatly appreciated.  Thanks in advance!

---

### Post by jimv on 2008-06-11
I would use NTFS.  I'm dual booting with XP (was using Vista for awhile, but got tired of it ;) and I can see the NTFS drive just fine.  The work around used to be installing NTFS-3G to allow Ubuntu to write to an NTFS drive.  I believe that is now built into the latest Ubuntu release.

---

### Post by mokshadaya on 2008-06-11
You're right that NTFS support is now a part of the repository and can be installed using Synaptic.  You'll can also install it through Add/Remove from the default Applications menu.  I would definately use NTFS over FAT32 any day of the week.

Regarding the wireless issue, this is an interesting one that I have seen with other wireless cards.  I see that your card is capable of a/b/g/n connections.  Sounds like this is probably a newer Intel card, however, I could be wrong.  I would bet that the module loaded for this card is not the correct, or best, module to be used.  To discover which module is currently utilized for it do the following:

1.  For future usability install hwinfo (i like this handy little app for many purposes).  From the command line run:  sudo apt-get install hwinfo
2.  <Type> hwinfo
3.  Locate the information for your wireless NIC.  For example purposes mine is pasted here:

56: None 00.0: 10780 Network Interface
  [Created at net.125]
  Unique ID: Yz_m.GSopYcFr9cF
  Parent ID: xFhm.VLFrh6x3TOF
  SysFS ID: /class/net/wifi0
  SysFS Device Link: /devices/pci0000:00/0000:00:1e.0/0000:02:01.1/0000:07:00.0
  Hardware Class: network interface
  Model: "Network Interface"
  Driver: "ath_pci"
  Driver Modules: "ath_pci"
  Device File: wifi0
  HW Address: 00:09:5b:ef:ac:88
  Link detected: yes
  Config Status: cfg=new, avail=yes, need=no, active=unknown
  Attached to: #13 (WLAN controller)

4.  Paste your information in a reply.

This information tells me that I am using the proprietary "ath_pci" module.  What we need to do is see if the module the kernel is using is appropriate for your device.  If not we can select the appropriate module to use.  (Awaiting post.......)

FYI - There's a GUI-style version of this app but I can't recall it's name.  Sorry.

---

### Post by mokshadaya on 2008-06-11
Ah ha.  It's called 'hardinfo'.  You can install it through Synaptic.

---

### Post by phoenix9262 on 2008-06-12
ok, same problem as the person above, so here's my output (thnx for the hardinfo recommendation, I love it)

Name: Atheros Communications Inc. 802.11abgn Wireless PCI Express Adapter
Class: Network Controller
Domain: 0
Bus, device, function: 3, 0, 0
Vendor: Atheros Commuications ([www.atheros.com](www.atheros.com))
OEM Vendor: Atheros Communications Inc Unknown device 0033
IRQ: 11
Bus Master: Yes
Memory: 64kb (non-prefetchable)

---

### Post by mokshadaya on 2008-06-12
Hmmm.  I might be wrong (someone correct me quickly if I am) but I believe we're seeing a driver/module issue here with the newer ABGN cards.

Are either of you familiar with NDISWrapper?  I believe a good next step is to install it through Synaptic and see how the cards perform using the Windows drivers from within NDISWrapper.  If you're not familiar with this, see [http://ndiswrapper.sourceforge.net/joomla/](http://ndiswrapper.sourceforge.net/joomla/) for more information.  They have a good FAQ on the site that gives step by step information.

---

### Post by phoenix9262 on 2008-06-12
I'm using ndis. it says its the right driver and the hardware was found, but the ight still won't come up. I posted in another thread i just found:

[http://ubuntuforums.org/showthread.php?t=814117](http://ubuntuforums.org/showthread.php?t=814117)

I posted some more specs on it too

---

### Post by stchman on 2008-06-12
> **jcat1 said:**
> Hello All,

I'm currently considering switching my system Lenovo t61 to dual boot status with Vista/Ubuntu Hardy 8.04 but there are a couple of questions I have before doing so:

First, I will need to have a shared partition which will contain all of my documents and other files that is accessible from both the Ubuntu and Vista environments.  Should I make this shared partition a FAT32 or NTFS format?  From  what I have read, getting Ubuntu to work with NTFS requires some sort of software workaround whereas FAT32 is supported natively.  What would you  recommend?

Second, when using the LiveCD, I can't see any wireless networks.  It appears that my wireless card is recognized as I can pull up the menu options wireless networking, but there are no networks to select (I have the Intel ABGN version of the wireless card).

Any help/advice you can provide on either or both questions is greatly appreciated.  Thanks in advance!

You can use NTFS as ntfs-3g is installed by default and works very well.  I would not give Ubuntu write permissions to the system drive of Vista.  Use the ro option in fstab.

The 4965 Intel wireless card works OOB with Ubuntu Hardy.  I have one in my laptop.

---

### Post by jcat1 on 2008-06-12
Thank you guys for the quick replies.

It looks like NTFS is the way to go for my shared partition.  Feel free to chime in if you have any other recommendations.

@Phoenix- are you getting wireless internet just fine with ndiswrapper?  Is it just the hardware light that's giving you a problem? If it's just the light, I saw something here about it: [http://www.thinkwiki.org/wiki/Installing_Ubuntu_8.04_%28Hardy_Heron%29_on_a_ThinkPad_T61](http://www.thinkwiki.org/wiki/Installing_Ubuntu_8.04_%28Hardy_Heron%29_on_a_ThinkPad_T61)

I will give ndiswrapper a try later today and let you know what happens.

---

### Post by phoenix9262 on 2008-06-13
yeah, ndis wrapper picks up and installs the driver fine (64 bit driver). but yeah, it doesn't show up under network and the light doesn't come on. stupid thinkpad >.>

also, I was just reading that article; it's like french to me, I'm a bit of a n00b when it comes to actually modifying linux. I can install and use it fine, but programming I'm not good in.

---

### Post by phoenix9262 on 2008-06-14
bump

---

### Post by phoenix9262 on 2008-06-15
bump

---

### Post by phoenix9262 on 2008-06-16
Bump

---

