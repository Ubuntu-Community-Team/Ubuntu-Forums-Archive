---
title: "Installing Ubuntu 22.04 from flash drive"
date: 2023-01-31
forum: Hardware
---

### Post by daniell59 on 2023-01-31
My wife's computer has Windows. I am tired of the problem with Malware. I want to install Ubuntu and replace the windows. I am not familiar with the new BIOS. I did not see the flash drive listed in the Boot menu. Please see image. I apologize  for the incorrect orientation of the image.
Any assistance will be appreciated.

---

### Post by oldfred on 2023-01-31
What brand/model system? What video card/chip?
Some require special settings.

If currently only a Windows user, best to dual boot until comfortable with Ubuntu. It is different.
Or at least make full backup of Windows. 
We get a fair number of users who erase Windows, find one application or game that is Windows only and want Windows back.
I have one Windows dual boot just for Turbotax. (My CPA retired and taxes are now less complex).

What tool did you use to create USB flash drive installer?
Some change flash drives, change ports, or change what they use to create flash drive & then it works. 

You may need UEFI settings.
UEFI & Windows Settings for UEFI install  - tea for one 
[https://ubuntuforums.org/showthread.php?t=2467629&p=14061395#post14061395](https://ubuntuforums.org/showthread.php?t=2467629&p=14061395#post14061395)

Some general UEFI install instrucions in link in my signature below.

---

### Post by daniell59 on 2023-01-31
> **oldfred said:**
> What brand/model system? What video card/chip?
Some require special settings.

If currently only a Windows user, best to dual boot until comfortable with Ubuntu. It is different.
Or at least make full backup of Windows. 
We get a fair number of users who erase Windows, find one application or game that is Windows only and want Windows back.
I have one Windows dual boot just for Turbotax. (My CPA retired and taxes are now less complex).

What tool did you use to create USB flash drive installer?
Some change flash drives, change ports, or change what they use to create flash drive & then it works. 

You may need UEFI settings.
UEFI & Windows Settings for UEFI install  - tea for one 
[https://ubuntuforums.org/showthread.php?t=2467629&p=14061395#post14061395](https://ubuntuforums.org/showthread.php?t=2467629&p=14061395#post14061395)

Some general UEFI install instrucions in link in my signature below.

I built this about 5 years ago. It has a Ryzen  APU and Windows 10. I am tired of the numerous times that I had to deal with the spyware. I already used the flash drive to install Ubuntu 22.04 on another old computer.

---

### Post by oldfred on 2023-01-31
Was flash drive created for both UEFI & BIOS?
Older computer may have been BIOS, so BIOS only installer would work.

Check that UEFI settings include allow USB boot or full USB support.
And often easier with UEFI Secure boot off. (Although it should install with it on).

---

### Post by daniell59 on 2023-01-31
> **oldfred said:**
> Was flash drive created for both UEFI & BIOS?
Older computer may have been BIOS, so BIOS only installer would work.

Check that UEFI settings include allow USB boot or full USB support.
And often easier with UEFI Secure boot off. (Although it should install with it on).

The drive was created on a 14 year old computer.

---

### Post by oldfred on 2023-01-31
Ubuntu install guide - multiple ways to create live installer to +flash drive
[https://help.ubuntu.com/community/Installation](https://help.ubuntu.com/community/Installation)
Updates for ISO to USB.
[https://help.ubuntu.com/community/Installation/iso2usb](https://help.ubuntu.com/community/Installation/iso2usb)
Updates -Instructions to make a boot drive, that boots both in UEFI and BIOS mode
[https://help.ubuntu.com/community/Installation/iso2usb/diy](https://help.ubuntu.com/community/Installation/iso2usb/diy)
[https://ubuntuforums.org/showthread.php?t=2299040](https://ubuntuforums.org/showthread.php?t=2299040)

[https://ubuntu.com/tutorials/create-a-usb-stick-on-ubuntu#1-overview](https://ubuntu.com/tutorials/create-a-usb-stick-on-ubuntu#1-overview)
[https://ubuntu.com/tutorials/create-a-usb-stick-on-windows#1-overview](https://ubuntu.com/tutorials/create-a-usb-stick-on-windows#1-overview)

---

### Post by daniell59 on 2023-01-31
> **oldfred said:**
> Ubuntu install guide - multiple ways to create live installer to +flash drive
[https://help.ubuntu.com/community/Installation](https://help.ubuntu.com/community/Installation)
Updates for ISO to USB.
[https://help.ubuntu.com/community/Installation/iso2usb](https://help.ubuntu.com/community/Installation/iso2usb)
Updates -Instructions to make a boot drive, that boots both in UEFI and BIOS mode
[https://help.ubuntu.com/community/Installation/iso2usb/diy](https://help.ubuntu.com/community/Installation/iso2usb/diy)
[https://ubuntuforums.org/showthread.php?t=2299040](https://ubuntuforums.org/showthread.php?t=2299040)

[https://ubuntu.com/tutorials/create-a-usb-stick-on-ubuntu#1-overview](https://ubuntu.com/tutorials/create-a-usb-stick-on-ubuntu#1-overview)
[https://ubuntu.com/tutorials/create-a-usb-stick-on-windows#1-overview](https://ubuntu.com/tutorials/create-a-usb-stick-on-windows#1-overview)

Thanks for the input. I will read it when I am more alert.

---

### Post by C.S.Cameron on 2023-01-31
**Dual boot Ubuntu 22.04 in Legacy BIOS mode**

- Unplug your Windows drive.
 
- Install Ubuntu on the other drive in the same BIOS/UEFI mode Windows uses, (ie Legacy).
 
- Plug in Windows drive.
 
- Set Ubuntu drive as the first HDD in BIOS.
 
- Boot Ubuntu then in Terminal run sudo update-grub , this should add Windows to Ubuntu's boot menu.
 
- When booting the Ubuntu drive you will be given a choice to boot Ubuntu or Windows.

---

### Post by daniell59 on 2023-02-01
> **C.S.Cameron said:**
> **Dual boot Ubuntu 22.04 in Legacy BIOS mode**

- Unplug your Windows drive.
 
- Install Ubuntu on the other drive in the same BIOS/UEFI mode Windows uses, (ie Legacy).
 
- Plug in Windows drive.
 
- Set Ubuntu drive as the first HDD in BIOS.
 
- Boot Ubuntu then in Terminal run sudo update-grub , this should add Windows to Ubuntu's boot menu.
 
- When booting the Ubuntu drive you will be given a choice to boot Ubuntu or Windows.
On the target computer there is only one drive in which Windows 10 is installed.
I was not thinking of dual boot.

---

### Post by daniell59 on 2023-02-01
I just booted into the BIOS with the flash drive plugged in. I did not find the flash drive listed.

---

### Post by yancek on 2023-02-01
If you installed windows 10 yourself, did you install it UEFI or Legacy?  Pre-installed windows 10 systems are almost always UEFI but since you apparently installed yourself, that may not be the case.

When you used the USB to install Ubuntu on the older computer, was it a Legacy install?  Was it on an empty drive, no other OS?  You may need to use a newer computer to create the USB so it is UEFI capable. Do you have multiple USB ports?  Have you tried different ones?

I'd read through the links posted by oldfred. particularly for creating a USB that will boot UEFI/BIOS Legacy mode.

Good luck.

---

### Post by daniell59 on 2023-02-01
> **yancek said:**
> If you installed windows 10 yourself, did you install it UEFI or Legacy?  Pre-installed windows 10 systems are almost always UEFI but since you apparently installed yourself, that may not be the case.

When you used the USB to install Ubuntu on the older computer, was it a Legacy install?  Was it on an empty drive, no other OS?  You may need to use a newer computer to create the USB so it is UEFI capable. Do you have multiple USB ports?  Have you tried different ones?

I'd read through the links posted by oldfred. particularly for creating a USB that will boot UEFI/BIOS Legacy mode.

Good luck.

I am ashamed to say that I don't know whether it was a legacy install.  I installed it over an older version of Ubuntu.
My computers are all old. My wife's computer is 5 years old which has windows. I have two computers. The one I use is about 14 years old. The backup one is quite a bit older. They both reside in Lian Li cases. Both have Ubuntu 22.04 64.
When the mood hits me, I'll build a new computer. I cannot part with the Lian Li cases though they support 80mm fans. It would be like abandoning a sick old dog.

---

### Post by oldfred on 2023-02-01
How you boot install media UEFI or BIOS is then how it installs.
Starting in about 2020 new systems are UEFI only, depending on vendor.
Starting 2012 Microsoft required vendors to install in UEFI boot mode to gpt partitioned drives. But large companies had some older systems and required BIOS install, so that became an option.
Ubuntu will install in UEFI mode or BIOS mode to either gpt or MBR partitioned drives. But really should only install in UEFI mode to gpt drives. And then give a warning if drive is MBR as then it may have a BIOS install of Windows.
I saw the gpt was future, so started using gpt with my 2010 Ubuntu BIOS install, had to totally erase that drive. Windows XP was still on MBR drive. It needed a bios_grub partition for BIOS boot. Then in 2012 started adding both bios_grub and an ESP for future use, if I converted drive to a new UEFI system. 

I reused a case that I liked. But it only had USB2 ports on front, so had to get a cable to connect to USB3 ports. Now Same issue with USB-c as my 2016 build only has that port on motherboard, case is USB3. Also one of my builds had issues with power supplies. I thought it was standard, but did not work with new motherboard. I do not game, so do not add video card. And then like the smaller cases.

---

### Post by sudodus on 2023-02-01
You can find out if your computers are booted in UEFI or BIOS mode (alias CSM alias legacy mode) via the following command line when booted into Ubuntu (or some other Linux distro, installed booted from internal drive or live booted from USB),

```

test -d /sys/firmware/efi && echo efi || echo bios

```

See also the following link

[help.ubuntu.com/community/Installation/FromUSBStick#Test_if_running_in_UEFI_mode](https://help.ubuntu.com/community/Installation/FromUSBStick#Test_if_running_in_UEFI_mode)

---

