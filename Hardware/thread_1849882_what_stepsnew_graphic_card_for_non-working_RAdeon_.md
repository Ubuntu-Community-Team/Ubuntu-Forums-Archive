---
title: "what steps/new graphic card for non-working RAdeon 9200SE"
date: 2011-09-25
forum: Hardware
---

### Post by andymids on 2011-09-25
Hi - installed Ubuntu which seemed to work OK, but when at end of install the system rebooted, the monitor warning indicated 1289x1024 resolution 60hz required - and monitor remained blank (however it shoed all the Ubuntu backgrounds ec during the install.

At Boot I have option of Windows XP Pro or Ubuntu - monitor works fine with XP Pro, and monitor Philips 170C set to the desired resolution as above.

I've spent some time s\earching and reading about this, and think it would be beyond me to get the ATI Radeon 9200SE card to work with Ubuntu. I'm not knowledgeable enough.

I had loaded ATI CATALYSTcontrol center for Radeon 9200SE on XP with updated drivers.

I was wondering, there's a catalyst control centre version for Linux. For now I want to try UBUNTU and keep the option of XP open. Can the Catalyst control centre for Linux & Radeon 9200SE be installed alongside the XP version? Probably not possible I guess.

What graphics card might easily work with XP and Ubuntu?

Helpful comments welcome on this, however I don't think I would be able to enact most of the work-arounds I've read about in the last few hours.

---

### Post by hreichgott on 2011-09-25
Hi,
If your system is dual-boot, then all the windows stuff lives on one part of your hard drive, and all your ubuntu stuff lives on another part. There will not be any conflict with Catalyst or any other software that you use in both.
ATI makes a Catalyst driver that runs natively on Linux, so no need to try to install it from the Windows CD using Wine or anything. Just go to the ATI/AMD website and follow the prompts to download the right driver for your card. It comes with an installer, which is great for new users who just want things to work :)
There are also open-source drivers available for Radeon but I have not been able to get them to work on mine (Radeon 9802). Others may be of more help here.

---

### Post by .... on 2011-09-25
Try booting without KMS (add radeon.modeset=0 to the boot line).

> ATI makes a Catalyst driver that runs natively on Linux
..except it dropped support for the card in question years ago. Please don't tell people to install fglrx/Catalyst on anything older than RadeonHD. It will screw up their system. See big red warning here: [http://wiki.cchtml.com/index.php/Ubuntu_Natty_Installation_Guide#Installing_Proprietary_Drivers_a.k.a._Catalyst.2Ffglrx](http://wiki.cchtml.com/index.php/Ubuntu_Natty_Installation_Guide#Installing_Proprietary_Drivers_a.k.a._Catalyst.2Ffglrx)

---

### Post by hreichgott on 2011-09-25
By the way, if you have a completely blank screen (no graphics at all) you may need to boot into Windows, download the driver installer onto a USB stick or something, then boot into text-only Ubuntu (if it isn't an option on boot, hold down shift while booting, and it should come up as an option) and run the driver installer manually.
Your USB stick will probably be under /media/.
If you need help navigating around the directory structure and running programs in text-only mode, don't be embarrassed to ask forhelp. Or you can look at the tutorials on tuxfiles.org, they're pretty good for beginners.

---

### Post by hreichgott on 2011-09-25
Sorry, did not realize 9200SE was older than RadeonHD. My card is RadeonHD and has a very similar model number. Was speaking from experience on own hardware. Please disregard earlier advice.

---

### Post by .... on 2011-09-25
9802 is not the model number for your chip; it's the PCI device ID. Your GPU is actually a RadeonHD 6310. If it shows as a 9802 with lspci, then you probably need to update your PCI ID list:
```
sudo update-pciids
```

---

### Post by andymids on 2011-09-26
Thanks hreichgott and ...    for your efforts

I think very few people have managed to get 9200Se working.

I have a friend with nVidia GeForceMX440 AGP graphics card working and taken from his rebuild.

There seem to be comments suggesting this card is more likely to work OK with Ubuntu/Linux.

My friend thinks he just put this card, expensive at the time, in his AGP slot, and off he went.

I have one AGP slot (4 old PCI slots).

I think replace the Radeon with the nVidia card and see if it works on XP.
If so, BOOT in Ubuntu and see.

Any better suggestions of how to approach this ~ get it working on XP with 'latest' drivers if possible? Be ready for......?

[Investigating my C drive, and having used wubi installer for Ubuntu, I didn't realise I would lose my boot.ini file which I had written myself - or I can't locate it now in C root - to be replaced by wubildr.mbr and  wubldr, so I am struggling to see how to add 'radeon.modeset=0' to the boot line. On boot up, the menu looks good as before, only with Ubuntu added as should be]
Oh Dear - complicated.

It will be a few days til I get hold of the nVidia card.
Thanks - Andrew

---

