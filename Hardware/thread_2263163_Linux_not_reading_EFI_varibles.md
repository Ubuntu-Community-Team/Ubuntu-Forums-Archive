---
title: "Linux not reading EFI varibles"
date: 2015-01-29
forum: Hardware
---

### Post by LostFarmer on 2015-01-29
```
&#9178; [dad:/home/dad] $ sudo efibootmgr -v
[sudo] password for dad: 
&#9178; [dad:/home/dad] $

``` no output from above command.

Grub.cfg does not have a efi-firware entire.

```
&#9178; [dad:/home/dad] 3s $ ls /sys/firmware/efi/vars
AcpiGlobalVariable-c020489e-6db2-4ef2-9aa5-ca06fc11d36a
ASUSSetupDefault-f1920447-7a78-4c0d-a028-ba9d003985e8
del_var
EfiTime-9d0da369-540b-46f8-85a0-2b5f2c301e15
FPDT_Variable-01368881-c4ad-4b1d-b631-d57a8ec8db6b
HobRomImage-dde1bc72-d45e-4209-ab85-14462d2f5074
MonotonicCounter-01368881-c4ad-4b1d-b631-d57a8ec8db6b
new_var
PchInit-e6c2f70a-b604-4877-85ba-deec89e117eb
PCI_COMMON-aca9f304-21e2-4852-9875-7ff4881d67a5
Setup-ec87d643-eba4-4bb5-a1e5-3f3e36b20da9
StdDefaults-4599d26f-1a11-49b8-b91f-858745cff824
USBCHARGE_VAR-ec87d643-eba4-4bb5-a1e5-3f3e36b20da9

``` The above I think shoud have at least 50 EFI firmware entires.  There are no entires for BOOTxxx, the reason efibootmgr -v has no output, no tables to read.

Have a ASUS X551MA preinstalled with win8.1 with Mint,PinGuy,Ubuntu (14.04LTS),Mageia, and Ubuntu (14.10) installed. All have the same problem. It is GPT with EFI boot.

Due to the problem is also in Mageia , would say the bug is upstream from Ubuntu, mabe in package 'linux-firmware' (?).

I think the above problem caused a dead comp, ASUS did repair with a new motherboard.

Question, where should the problem be reported and what information might be needed ?  This would be all new to  me.

Thanks for any help.

---

### Post by oldfred on 2015-01-30
Probably best to just see configuration. Post link to summary report.

 Boot Repair -Also handles LVM, GPT, separate /boot and UEFI dual boot.:
Precise, Trusty, Vivid, & Utopic all should work now with current ppa
[https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair)

---

### Post by LostFarmer on 2015-01-30
I can boot with no problems, that is not the failure.
link for boot-repair [http://paste.ubuntu.com/9962489/](http://paste.ubuntu.com/9962489/)

at line# 2976 efibootmgr -v   no output  (see my OP)
on my grub.cfg's no entire for "BEGIN /etc/grub.d/30_uefi-firmware"

The reason is kernel is NOT reading the EFI tables, they should be in "/sys/firmware/efi/vars".
  'efibootmgr' will write a boot entire to the EFI firmware, but it does so blindly and can corrupt the EFI table and leave my Comp dead after sometime doing so.  (Did read that on a old efi bug, do not remember where)



I also do not know what other EFI tables it is not reading and may cause problems down the road.

Was thinking about running "fwts" but have never done so, would have no idea of its output.

---

### Post by oldfred on 2015-01-30
Does it have the newest UEFI version from Asus?

If in BIOS mode, there is no efibootmgr, but have not seen issues with efibootmgr not working. But I think some of the outputs from Boot-Repair have not shown the output like yours. I assumed it was an issue with Boot-Repair or user was in BIOS mode.

---

### Post by LostFarmer on 2015-01-30
> Does it have the newest UEFI version from Asus? Yes

Comp is booted in EFI mode or else it would not have /sys/firmware/efi.

Booted into my son's Dell with live usb stick:

/sys/firmware/efi/vars:  (did not copy the complete file name, left off the uuid # nor all of the entires.
```
Boot0000-***
Boot0001-***
Boot0002-***
Boot0006-***
Boot0007-***
BootCurrent-***
BootOrder-***
```

```
ubuntu@ubuntu:~$ sudo efibootmgr -v
BootCurrent: 0006
Timeout: 1 seconds
BootOrder: 0000,0001,0002,0006,0007
Boot0000* P0: ST1000DM003-1ER162            BIOS(11,0,00)
Boot0001* SanDisk SanDisk Ultra PMAP    BIOS(12,0,00)
Boot0002* P1: TSSTcorp DVD+/-RW SH-216DB    BIOS(13,0,00)
Boot0006* UEFI: SanDisk SanDisk Ultra PMAP    ACPI(a0341d0,0)PCI(1d,0)USB(1,0)USB(3,0)HD(1,800,1ae7800,0000025d)..BO
Boot0007* UEFI: SanDisk SanDisk Ultra PMAP    ACPI(a0341d0,0)PCI(1d,0)USB(1,0)USB(3,0)HD(2,1ae8000,fa000,0000025d)..BO

```

My ASUS does not have the efi boot items in /sys/firmware/efi/vars/ (see first post) so 'efibootmgr -v' has no data to read out.  The vars are not being loaded by the kernel.  'efibootmgr -v' does not read its data from the motherboards efi tables but from the tables read in by the kernel to /sys/***/vars.


Would say [http://ubuntuforums.org/showthread.php?t=2260864](http://ubuntuforums.org/showthread.php?t=2260864)  has the same problem with a different ASUS. [http://paste.ubuntu.com/9752816/](http://paste.ubuntu.com/9752816/) line #137
```
 efibootmgr -v show_boot_order(): No such file or directory
```   The "ls  /sys/firmware/efi/vars" command a coupe line before, also does not list any 'boot***' entires.

---

### Post by oldfred on 2015-01-30
I have not used modprobe, but there was a post where you should do that first?

 modprobe efivars
sudo efibootmgr -v

---

### Post by LostFarmer on 2015-01-30
modprobe efivars
sudo efibootmgr -v 				

still does not give any output.  

It would seem that first command is no loger needed, it is part of the kernel. [http://askubuntu.com/questions/232364/module-efivars-does-not-exist](http://askubuntu.com/questions/232364/module-efivars-does-not-exist)

---

### Post by oldfred on 2015-01-31
Thanks for the updated info on modprobe.

I think then Asus is not following the UEFI standard or writing it differently and kernel cannot then find all the efi data. But if system works, the essential data must be there.

---

### Post by adgmonk2 on 2015-04-27
> **oldfred said:**
> I think then Asus is not following the UEFI standard or writing it differently and kernel cannot then find all the efi data.

Yes indeed, but Asus has fixed it now.  After updating UEFI firmware to version 514 (latest as of April 2015) from Asus site for my X551MA / X551MAV laptops (same firmware), the problem got solved:  efibootmgr now shows the EFI variables.

(I should note that the updated Asus UEFI firmware (version 514) still has plenty of bugs:  Adding a boot entry via the firmware setup menu may not work when you have multiple EFI system partitions (it lists files to select from a wrong partition); morever, the Asus UEFI firmware may, at its own whim, modify/add boot entries added by grub or efibootmgr.)

This thread can now be marked SOLVED and closed.

---

### Post by LostFarmer on 2015-04-27
The latest UEFI firmware does indeed seems to have fix this problem. One also needs to update the efibootmgr to version 0.7.0

Thanks adgmonk2

---

