---
title: "SSD Unrecognized by Unbuntu 18.04.1"
date: 2019-02-08
forum: Hardware
---

### Post by aajax on 2019-02-08
A new Dell Inspiron 3670 computer has 2 drives factory installed. One is a conventional hard drive (HD) the other is a solid state drive (SSD).   It seems that the SSD is completely unrecognized by Ubuntu.  In this case we're talking about having booted the installation disk in "Try Ubuntu" mode and only the HD is present.  This includes as seen by GParted.  The, missing, SSD is connected via PCIe M.2 interface rather than SATA. My suspicion is that this requires a driver that could be missing. However, Dell advertises this computer as being factory supplied with installation option that allows either Ubuntu or Windows 10 to be installed. I haven't tried installing Ubuntu and can't say what might happen then but I would be surprised and seriously disappointed at the idea that I was sold a computer with a drive that an advertised OS cannot use.

How can I get Ubuntu to function on this drive?

---

### Post by oldfred on 2019-02-08
Almost all Dell systems have needed UEFI updates and SSD firmware updates.
Check that you have latest versions.

All Dell seem to use RAID or Intel SRT as drive setting, you need to change to AHCI in UEFI drive settings.
But if dual booting with Windows you need to first install the AHCI driver into Windows or it will not boot. Or you have to switch back & forth.

Issues are common across many models of same brand, bigger differences if Intel or AMD.
       Dell UEFI Dual boot instructions using Something Else
[https://www.dell.com/support/article/us/en/19/SLN301754/how-to-install-ubuntu-and-a-recent-windows-operating-system-as-a-dual-boot-on-your-dell-pc?lang=EN](https://www.dell.com/support/article/us/en/19/SLN301754/how-to-install-ubuntu-and-a-recent-windows-operating-system-as-a-dual-boot-on-your-dell-pc?lang=EN)
[https://www.dell.com/support/article/us/en/19/sln142679/how-to-enable-boot-from-dvd-option-with-uefi-boot-mode-enabled--windows-8--81--10-?lang=en](https://www.dell.com/support/article/us/en/19/sln142679/how-to-enable-boot-from-dvd-option-with-uefi-boot-mode-enabled--windows-8--81--10-?lang=en) 
    
       Dell update UEFI/BIOS from Linux
[https://www.dell.com/support/article/us/en/19/sln171755/updating-the-dell-bios-in-linux-and-ubuntu-environments?lang=en](https://www.dell.com/support/article/us/en/19/sln171755/updating-the-dell-bios-in-linux-and-ubuntu-environments?lang=en) 
    
See link in my signature below for general UEFI install instructions. Do not skip the backup.

---

### Post by awdelft on 2019-02-08
Hi oldfred et al:)
I just received my very fresh dell aurora i9 9900k with nvme only. My ict department put W10 on it and I asked to free half the nvme ssd for a ubuntu partition. 
I tried to install ubuntu 1804 but live does not see the m2 nvme at all. 
Then I found online that this is something I might have checked before...
The disk is already in ahci according to bios.
I looked at the dell articles but still did not succeed. Of course this machine is not in the tested list yet.
Could you please point me in the right direction, things to try and do?
Actually, since it is a fresh system, I could not care less to damage W10. Maybe that helps?
Eventually I would like to dual boot...

---

### Post by oldfred on 2019-02-08
Are UEFI & SSD firmware  updated?

Post this:
sudo parted -l

Need to confirm that Windows was correctly installed in UEFI boot mode. Often when users install it, they use the 35 year old BIOS/MBR configuration. Some still like it, but Windows has used as default UEFI since Windows 8 released in 2012.

---

### Post by aajax on 2019-02-09
Very nice!  Looks to be spot on.

I ended up both upgrading firmware & then changing SATA setting from "Raid On" to "AHCI" before booting Ubuntu which then worked fine at least with respect to recognizing both disk drives.  Therefore, I don't know if both were required but the Dell supplied information indicted that there was what they called an "urgent" need to upgrade the firmware version that was on the machine.

I also verified that System Rescue CD, which was suffering from the same problem, could find the drives. It also suffered from the same problem and is something that I find to be a very nice/useful tool when needed.

Many thanks for the help!

---

### Post by oldfred on 2019-02-09
If it is now working you can change to [Solved].

---

### Post by skoles on 2020-02-08
I have this same issue ATM...The AHCI driver.....How does one identify the correct driver ? My assumption is once I successfully install the AHCI driver in WINDOWS 10, I would be able to change from RAID to AHCI and there would be no issues booting back into WINDOWS 10 correct ? :-)

> **oldfred said:**
> Almost all Dell systems have needed UEFI updates and SSD firmware updates.
Check that you have latest versions.

All Dell seem to use RAID or Intel SRT as drive setting, you need to change to AHCI in UEFI drive settings.
But if dual booting with Windows you need to first install the AHCI driver into Windows or it will not boot. Or you have to switch back & forth.

Issues are common across many models of same brand, bigger differences if Intel or AMD.
       Dell UEFI Dual boot instructions using Something Else
[https://www.dell.com/support/article/us/en/19/SLN301754/how-to-install-ubuntu-and-a-recent-windows-operating-system-as-a-dual-boot-on-your-dell-pc?lang=EN](https://www.dell.com/support/article/us/en/19/SLN301754/how-to-install-ubuntu-and-a-recent-windows-operating-system-as-a-dual-boot-on-your-dell-pc?lang=EN)
[https://www.dell.com/support/article/us/en/19/sln142679/how-to-enable-boot-from-dvd-option-with-uefi-boot-mode-enabled--windows-8--81--10-?lang=en](https://www.dell.com/support/article/us/en/19/sln142679/how-to-enable-boot-from-dvd-option-with-uefi-boot-mode-enabled--windows-8--81--10-?lang=en) 
    
       Dell update UEFI/BIOS from Linux
[https://www.dell.com/support/article/us/en/19/sln171755/updating-the-dell-bios-in-linux-and-ubuntu-environments?lang=en](https://www.dell.com/support/article/us/en/19/sln171755/updating-the-dell-bios-in-linux-and-ubuntu-environments?lang=en) 
    
See link in my signature below for general UEFI install instructions. Do not skip the backup.

---

### Post by oldfred on 2020-02-08
Several sets of instructions on AHCI in Windows.

Windows AHCI instructions - some have found safeboot method better
[https://www.dell.com/community/Laptops-General-Read-Only/Dell-M-2-FAQ-regarding-AHCI-vs-RAID-ON-Storage-Drivers-M-2-Lanes/td-p/5072571](https://www.dell.com/community/Laptops-General-Read-Only/Dell-M-2-FAQ-regarding-AHCI-vs-RAID-ON-Storage-Drivers-M-2-Lanes/td-p/5072571)
[https://askubuntu.com/questions/1148120/ubuntu-18-0x-not-detecting-windows-ssd-during-installation](https://askubuntu.com/questions/1148120/ubuntu-18-0x-not-detecting-windows-ssd-during-installation) & 
[https://askubuntu.com/questions/963087/install-dual-boot-ubuntu-with-windows-10-and-raid-on#963100](https://askubuntu.com/questions/963087/install-dual-boot-ubuntu-with-windows-10-and-raid-on#963100)
[https://samnicholls.net/2016/01/14/how-to-switch-sata-raid-to-ahci-windows-10-xps-13/](https://samnicholls.net/2016/01/14/how-to-switch-sata-raid-to-ahci-windows-10-xps-13/)
AHCI enable - May have to unlock bitlocker if used
[https://www.tenforums.com/drivers-hardware/15006-attn-ssd-owners-enabling-ahci-mode-after-windows-10-installation.html#post332243](https://www.tenforums.com/drivers-hardware/15006-attn-ssd-owners-enabling-ahci-mode-after-windows-10-installation.html#post332243)

---

### Post by skoles on 2020-02-08
Awesome, I will peruse these. Thanks for the quick reply :-)

---

### Post by skoles on 2020-02-08
Ok, I have read through the majority of these articles/methods.....

Some of the methods allude to installing a driver but make no mention of the actual driver sought as in Sam's super easy guide....The only driver downloads mentioned are the so called DELL "UNSUPPORTED" drivers for the SSDs.  In my case I have the TOSHIBA SSD.

Of course assumptions can be made but I am still not comfortable making an assumption here. 

[h=2]"Sam&#8217;s super easy guide to switching your SATA Controller from RAID to AHCI without destroying your Windows 10 disk[/h] 
[LIST]
[*]Boot to Windows with your current SATA controller configuration
[*]Open *Device Manager*
[*]Expand *Storage Controllers* and identify the *Intel SATA RAID Controller*
[*]View properties of the identified controller
[*]On the *Driver* tab, click the *Update driver&#8230;* button
[*]_***Browse my computer&#8230;*, *Let me pick&#8230;---->>>>>>Pick what ?***_
[*]Uncheck *Show compatible hardware*
[*]Select *Microsoft* as manufacturer
[*]Select *Microsoft Storage Spaces Controller* as model[SUP][3]("https://samnicholls.net/2016/01/14/how-to-switch-sata-raid-to-ahci-windows-10-xps-13/#fn-513-3")[/SUP]
[*]Accept that Windows cannot confirm that this driver is compatible
[*]Save changes, reboot to BIOS and change RAID SATA Controller to AHCI
[*]Save changes and reboot normally, hopefully to Windows"
[/LIST]

---

### Post by oldfred on 2020-02-08
Did you look at the others?
Some even show the exact Windows drivers.
But it looks like if you reboot into safe mode, after changing UEFI to AHCI, Windows will just install the correct driver.

---

### Post by skoles on 2020-02-15
Well, After thoroughly researching this topic, asking an IT guy at work and finding DELL of little help, I chose OPTION #2 using the BCDEDIT commands and safe mode. IT WORKED PERFECTLY !!!!!! YEA !!!!!!!!!!!!!!!!!

---

