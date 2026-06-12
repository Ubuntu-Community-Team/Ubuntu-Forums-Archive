---
title: "Intel M.2 SSD 660p not detected in ubuntu"
date: 2019-09-09
forum: Hardware
---

### Post by vincent-tremblay on 2019-09-09
Hi everyone, 

I bought a new laptop, Acer Nitro 5 (AN515-54-58YY). I added a M.2 SSD PCIe of 512GB and can't make Ubuntu recognize/detect it.
BIOS detect it, Windows 10 and Windows 10 setup, detect it, but ubuntu live CD, installer, gparted, lsblk (or any other command), can't detect it. I tried Ubuntu 18.04, 19.04, 19.10 Daily build. 
My windows FASTBOOT is disabled. Inside BIOS, I tried desabling FASTBOOT and SECUREBOOT options. Nothing work.
I can't change any option for AHCI or RAID option (I've done a lot of research on the web before asking here...)
Tried boot option nvme_load=YES, nvme_core.default+ps_max_latency_us=200 ... 
BIOS is up to date, and firmware of SSD too.

The SSD is an Intel SSD 6 (660p) SSDPEKNW512G8XT. 

Can it be incompatible with Ubuntu for any reason ?

Help me please !

Thanks !

---

### Post by oldfred on 2019-09-09
Have you updated UEFI and SSD firmware? Even if new.
Almost all Acer will need "trust" setting in UEFI after install.

       [SOLVED]Acer Nitro 5 (with Ryzen 7 2700U, RX 560X) Ubuntu 18.10  
[https://ubuntuforums.org/showthread.php?t=2413504](https://ubuntuforums.org/showthread.php?t=2413504) &
[https://ubuntuforums.org/showthread.php?t=2412117](https://ubuntuforums.org/showthread.php?t=2412117) &
[https://community.acer.com/en/discussion/555251/unable-to-install-ubuntu-in-my-nitro-an512-42](https://community.acer.com/en/discussion/555251/unable-to-install-ubuntu-in-my-nitro-an512-42)
Acer Very latest UEFI/BIOS works, downgrade not required if no trust screens, you must now upgrade:
[http://ubuntuforums.org/showthread.php?t=2298380&p=13419141#post13419141](http://ubuntuforums.org/showthread.php?t=2298380&p=13419141#post13419141) 
    
       Acer Trust Settings - details, some now report that then secure boot has to be on to set trust:
[https://ubuntuforums.org/showthread.php?t=2297947&p=13369742#post13369742](https://ubuntuforums.org/showthread.php?t=2297947&p=13369742#post13369742) & 
[https://ubuntuforums.org/showthread.php?t=2297947](https://ubuntuforums.org/showthread.php?t=2297947) & 
[https://ubuntuforums.org/showthread.php?t=2358003](https://ubuntuforums.org/showthread.php?t=2358003)

---

### Post by vincent-tremblay on 2019-09-09
Hi oldfred, and thanks for helping me !
Yes Bios(UEFI) and firmware of my SSD is up to date.

I can't configure my trust settings, because I can't even install my ubuntu, because I can't figure out how to make Ubuntu detect it (my SSD PCIe). 

All post you share me is revelant only if I could install Ubuntu. 

Thanks for your help !

---

### Post by oldfred on 2019-09-09
I was hoping that firmware update was all that was required.
And sometimes those with same/similar system post additional info on issues, but I am not familiar with Acer other than lots of posts on "trust" issues.

You should have AHCI setting on drives somewhere. It may be currently RAID or Intel RST.
It may be under an advanced or IDE settings. (Which may seem backwards).

My Asus motherboard has UEFI settings all under the BIOS/CSM settings. Since CSM is an emulation mode in UEFI, it also seems backwards. CSM/BIOS settings should be under a UEFI tab or setting.

---

### Post by vincent-tremblay on 2019-09-09
It is "RST Premium with Optane" in SATA Mode and I can not change it. It is in the "Information" page, and no other options on that in the others tabs ...
And under Boot Mode, I only got UEFI, no legacy, ahci, raid or nothing else ...

I really think I can't do anything !

Is windows 10 could make Uubntu installer not detecting SDD ?
I tried with GParted Live USB, and it do not detect my M2 SSD ...

Thanks

---

### Post by oldfred on 2019-09-09
Microsoft requires vendor to let uses turn UEFI Secure Boot on and off. Probably for those with Windows 7 as it did not support UEFI Secure Boot.

Others have posted with Acer that you have to set a password in UEFI to open up additional settings. Do not lose password, or reset later to blank when done reconfiguring system.

---

### Post by vincent-tremblay on 2019-09-10
In my unfortunate research, "Intel RST with optane" isn't supported in Linux. Since I can't disable it (nor change SATA mode) in BIOS, I'm stuck right there. Hope in the future, Linux will add support for it. Or Acer will add option to change it in a Bios update.
I will install win10 on m.2 and linux on slow hdd (disappointing). I will use F12 boot option to switch from one to the other at boot time ...

---

### Post by oldfred on 2019-09-10
I have yet to see a system that cannot be changed. Some UEFI setting somewhere will open up those changes.

HP with Optane:
[https://askubuntu.com/questions/1134503/cant-boot-ubuntu-because-windows-10-rewrites-entire-efi-partition-solved](https://askubuntu.com/questions/1134503/cant-boot-ubuntu-because-windows-10-rewrites-entire-efi-partition-solved)
       Intel Optane - See Intel response that no performance difference between RAID & AHCI.
[https://communities.intel.com/thread/121155](https://communities.intel.com/thread/121155)

---

### Post by Dennis N on 2019-09-10
> In my unfortunate research, "Intel RST with optane" isn't supported in Linux.
Yes, but that doesn't mean the drive doesn't work in Linux. Phoronix tested Intel 660p m.2 NVMe SSDs using Ubuntu 18.04 about a year ago. Read here:

[Phoronix Test]("https://www.phoronix.com/scan.php?page=article&item=intel-ssd-660p&num=1")

---

### Post by vincent-tremblay on 2019-09-10
Yes, I know that the SSD work with Linux, but as I said, I can't change "RST" to AHCI ou whatever options for SATA in Bios. So I need Linux be able to handle Intel RST (because it can't detect SDD nor controller), or Acer to modify their Bios to let people change that option ... I'm really surprise to not find any solution to my problem. I searched solutions for more than 50 hours in the couple of past days with no luck. People will have this kind of problem more often and maybe someday will have solution, hack or evolution !

---

### Post by oldfred on 2019-09-10
This has several links into Acer, but you have to log into Acer to see them.

[https://community.acer.com/en/discussion/551111/nitro-an515-52-recover-my-hdd-after-intel-rst-made-it-a-recovery-drive](https://community.acer.com/en/discussion/551111/nitro-an515-52-recover-my-hdd-after-intel-rst-made-it-a-recovery-drive)

---

### Post by Dennis N on 2019-09-11
Does UEFI bios have a section for managing PCIe devices? That may have options to change the mode of the m.2 device connector. Could be set to 'Auto' (automatically detect from device) but maybe it's set otherwise by Acer; possibly you need to make manual setting instead of Auto.

NVMe devices don't use AHCI. But SATA devices (like the HDD or SATA SSDs) do.

---

### Post by Yellow Pasque on 2019-09-11
Does lscpi see it? Any mention in dmesg?
```
sudo update-pciids
lspci
dmesg | grep -i nvm
```

It should look like:
```
07:00.0 Non-Volatile memory controller: Intel Corporation SSDPEKNW020T8 [660p, 2TB] (rev 03)
```

---

### Post by vincent-tremblay on 2019-09-21
> **Dennis N said:**
> Does UEFI bios have a section for managing PCIe devices? That may have options to change the mode of the m.2 device connector. Could be set to 'Auto' (automatically detect from device) but maybe it's set otherwise by Acer; possibly you need to make manual setting instead of Auto.

NVMe devices don't use AHCI. But SATA devices (like the HDD or SATA SSDs) do.


I can't change anything in the BIOS, I'm stuck in RST mode, in "SATA mode" section. No other section regarding PCIs devices. My BIOS detect correctly my m.2 drive.

---

### Post by vincent-tremblay on 2019-09-21
> **Yellow Pasque said:**
> Does lscpi see it? Any mention in dmesg?
```
sudo update-pciids
lspci
dmesg | grep -i nvm
```

It should look like:
```
07:00.0 Non-Volatile memory controller: Intel Corporation SSDPEKNW020T8 [660p, 2TB] (rev 03)
```


Here result of lspci after update-pciids :  

lspci
00:00.0 Host bridge: Intel Corporation 8th Gen Core 4-core Processor Host Bridge/DRAM Registers [Coffee Lake H] (rev 07)
00:01.0 PCI bridge: Intel Corporation Xeon E3-1200 v5/E3-1500 v5/6th Gen Core Processor PCIe Controller (x16) (rev 07)
00:02.0 VGA compatible controller: Intel Corporation UHD Graphics 630 (Mobile)
00:08.0 System peripheral: Intel Corporation Xeon E3-1200 v5/v6 / E3-1500 v5 / 6th/7th/8th Gen Core Processor Gaussian Mixture Model
00:12.0 Signal processing controller: Intel Corporation Cannon Lake PCH Thermal Controller (rev 10)
00:14.0 USB controller: Intel Corporation Cannon Lake PCH USB 3.1 xHCI Host Controller (rev 10)
00:14.2 RAM memory: Intel Corporation Cannon Lake PCH Shared SRAM (rev 10)
00:14.3 Network controller: Intel Corporation Wireless-AC 9560 [Jefferson Peak] (rev 10)
00:15.0 Serial bus controller [0c80]: Intel Corporation Cannon Lake PCH Serial IO I2C Controller #0 (rev 10)
00:15.1 Serial bus controller [0c80]: Intel Corporation Cannon Lake PCH Serial IO I2C Controller #1 (rev 10)
00:16.0 Communication controller: Intel Corporation Cannon Lake PCH HECI Controller (rev 10)
00:17.0 RAID bus controller: Intel Corporation 82801 Mobile SATA Controller [RAID mode] (rev 10)
00:1d.0 PCI bridge: Intel Corporation Cannon Lake PCH PCI Express Root Port #14 (rev f0)
00:1e.0 Communication controller: Intel Corporation Device a328 (rev 10)
00:1f.0 ISA bridge: Intel Corporation Device a30d (rev 10)
00:1f.3 Audio device: Intel Corporation Cannon Lake PCH cAVS (rev 10)
00:1f.4 SMBus: Intel Corporation Cannon Lake PCH SMBus Controller (rev 10)
00:1f.5 Serial bus controller [0c80]: Intel Corporation Cannon Lake PCH SPI Controller (rev 10)
01:00.0 VGA compatible controller: NVIDIA Corporation GP107M [GeForce GTX 1050 3 GB Max-Q] (rev a1)
01:00.1 Audio device: NVIDIA Corporation GP107GL High Definition Audio Controller (rev a1)
06:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL8111/8168/8411 PCI Express Gigabit Ethernet Controller (rev 25)

and result for grep NVM
[    1.434908] ahci 0000:00:17.0: Found 1 remapped NVMe devices.

Is that help someone ?

Thanks guys !

---

### Post by oldfred on 2019-09-21
After you update UEFI & SSD firmware, you have to turn on UEFI Secure Boot and login to UEFI. Never forget that password.
Then you should have more settings available to change.
If UEFI updated, it often reverts settings to defaults, so you may have to redo some you did before.

---

### Post by vincent-tremblay on 2019-09-21
Did not work oldfred, I already tried that.

---

### Post by Yellow Pasque on 2019-09-21
```
[ 1.434908] ahci 0000:00:17.0: Found 1 remapped NVMe devices.
```
It sounds like you may have one of those hardcoded RAID systems the dev refers to in the third paragraph:

> Some Intel ahci implementations have a completely broken remapping mode
where they hide one or more NVMe devices behind the bar of an AHCI device.

Intel refuses to let the OS reprogram the BIOS to switch out of this
mode at runtime, and so far we're not come up with another good way
to undo the mess that the Chipset people created.  So for now the only
thing we can do is to alert users about this situation and switch to the
faster and much saner so called "AHCI" mode insted of the RAID mode in
the BIOS so that the BIOS does not hide the NVMe devices from us.

The situation is even worse as at least one vendor (thanks a lot Lenovo..)
has started hardcoding their BIOS into the "RAID" mode even for laptops
that don't use AHCI _at all_ and just have a single NVMe device.  For now
there is an unspported Linux-only BIOS that undoes this braindamage,
but we'll have to see if things are getting better or worse from here.
[https://www.spinics.net/lists/linux-ide/msg53505.html](https://www.spinics.net/lists/linux-ide/msg53505.html)

---

### Post by Yellow Pasque on 2019-09-21
Wow. The manual really lacks info on the BIOS/EFI screen options. That's part of why I would never recommend Acer to anyone who is a "power" or Linux user.

---

### Post by vincent-tremblay on 2019-09-22
That's my exact problem ! Thanks for that info Yellow Pasque. I now know that i'm not the only one ;-)
I'm stuck in RAID mode ... But I don't understand why is that a problem with Linux system ?

---

### Post by Yellow Pasque on 2019-09-23
I guess this is the relevant report: [https://bugs.launchpad.net/ubuntu/+source/linux/+bug/1808842](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/1808842)

> But I don't understand why is that a problem with Linux system?

I'm not sure, but the bottom line is that you need to switch to AHCI SATA mode in the BIOS. I see other Nitro 5 users reporting they can switch, ( [https://community.acer.com/en/discussion/558380/acer-nitro-5-an515-52-wont-boot-in-ahci-mode](https://community.acer.com/en/discussion/558380/acer-nitro-5-an515-52-wont-boot-in-ahci-mode) ), so you should be able to as well. The only thing I can think of is that your BIOS detects the Windows install operating in RST/Optane and won't let you because it would break Windows. Maybe you should ask Acer..


EDIT: You are using F5 or F6 keys in BIOS to try and change the value, correct?

---

### Post by Dennis N on 2019-10-26
> **vincent-tremblay said:**
> I can't change anything in the BIOS, I'm stuck in RST mode, in "SATA mode" section. No other section regarding PCIs devices. My BIOS detect correctly my m.2 drive.
A similar problem thread appeared for Acer Nitro. The solution given there might apply to you?
[https://ubuntuforums.org/showthread.php?t=2429951&p=13900969#post13900969](https://ubuntuforums.org/showthread.php?t=2429951&p=13900969#post13900969)

---

### Post by wowbaggerbr on 2019-11-03
I recently bought a Samsung laptop that has the same design: the UEFI simply won't let you chance none of the NVME drives to AHCI, the setting isn't there.

---

### Post by oldfred on 2019-11-03
Samsung typically needs UEFI Secure Boot /password  on to have more settings.
But many SSDs need firmware updates to be correctly seen by Linux.

---

### Post by THEKINGDOM on 2019-11-09
I'm experiencing the same issue with the Intel M.2 SSD **660P **on Ubuntu 18.04 --  Not detected in bios or the system at all. 
Even the Intel SSD firmware updater can't detect it in bios boot environment with linux kernel loaded. 

Interestingly, the Intel** 600P M.2 SSD **has no issues being detected and that's currently the M.2 SSD that my Ubuntu OS resides. 
The 600P is 128GB

---

### Post by Yellow Pasque on 2019-11-09
> **THEKINGDOM said:**
> I'm experiencing the same issue with the Intel M.2 SSD **660P **on Ubuntu 18.04 --  Not detected in bios or the system at all. 

What kind of system or motherboard do you have? I have a 660P running/booting Linux without issue.

---

### Post by THEKINGDOM on 2019-11-09
> **Yellow Pasque said:**
> What kind of system or motherboard do you have? I have a 660P running/booting Linux without issue.

MSI Z390 MPG Gaming Edge AC - motherboard
i7-9700k CPU
Ubuntu 18.04
660P Drive size 512GB - what size is your drive ?

---

### Post by Yellow Pasque on 2019-11-11
> **THEKINGDOM said:**
> 660P Drive size 512GB - what size is your drive ?

I have the 1TB variant of the 660P, but it shouldn't matter. If you cannot see the drive in the BIOS, then your situation seems unrelated to the OP's, other than having the same model of SSD.
My guess is that you (in order of probability):
1) Need to alter a BIOS setting
2) Need to update your BIOS
3) Installed the drive incorrectly
4) Have a defective drive

For this type of issue, I think you would have better luck asking on a general hardware support forum or the MSI site.

---

### Post by THEKINGDOM on 2019-11-11
Hi guys, update here: 
the drive was faulty, had it tested at the retail outlet..so my case is not valid to this thread. Sorry for the confusion.

Thanks

---

### Post by vincent-tremblay on 2020-05-12
Hello everyone. 

Several months past since my problem. I decided to check for new BIOS update, and I saw a lot of versions ! I did de lastest hoping that I would be grant the choice of "SATA Mode" in my BIOS. 
Unfortunately, no !

I did couple of researches on the Internet again, to find another post, with this kind of problem. And I found a solution that has worked for me !! 

Here what I did.

Update my BIOS (Acer) to version 1.29 (lastest as may 11, 2020)
In BIOS, go to "Main" section. Press "CTRL + S".
An hidden section called "Sata mode" will  be available !
I change from "RST Premium with Octane" to AHCI.

There I go, Linux (Mint and Ubuntu) now detect my M2 drive !

Prior of doing that,**_ if you have dual-boot with Windows_**,  have Windows ready to boot in Safe mode at first boot-up. It will install needed drivers for proper boot-up next normal boot. If you didn't do that first, Windows will hang at boot with blue screen. If that so, don't worry, just go back in BIOS and put "SATA mode" back to RST, and prepare Windows to boot in safe mode. and do it again !

Thanks for your time guys and hope people with this problem can have this solution worked for them !

---

### Post by Yellow Pasque on 2020-05-12
Ugh. I hate when vendors hide settings behind strange key combos, especially when they don't tell you about them in the manual.

---

