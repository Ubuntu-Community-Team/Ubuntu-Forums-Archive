---
title: "Ubuntu 22.04 on Lenovo servers with UEFI"
date: 2022-11-26
forum: Hardware
---

### Post by Alex_Filonov on 2022-11-26
Getting "Error 1962 No Operating System Found" on Lenovo computers after Linux install?

Spend many hours trying to make work 20.04 on Lenovo Thinkserver M82. Was mad at Lenovo, now mad at Ubuntu as well.
The problem: BIOS checks if your boot partition is Windows or Red Hat partition (many crude words come to mind).
Fix: make fictional Windows partition. Using the following procedure:

Login from CD or USB live linux distribution, open terminal as a root and do the following:

mkdir /mnt1
mount -t msdos /dev/sda1 /mnt 1 # You disk might have different id, replace sda1 with it)
cd /mnt

Check if you have fake Windows partition:

efibootmgr

You'll get output like this:
 
[sudo] password for alex: 
BootCurrent: 0000
Timeout: 5 seconds
BootOrder: 0000,0001,0002
Boot0000* Windows Boot Manager
Boot0001* PLDS DVD-RW DH16ACSH
Boot0002* ubuntu
Boot0003* CT500MX500SSD1
Boot0004* IBA GE Slot 00C8 v1381
Boot0005* ubuntu
Boot0006* Generic Usb Device
Boot0008* Generic Usb Device
Boot000A* CT500MX500SSD1
Boot000B* ubuntu
Boot000C* SanDisk Ultra 2.01
Boot000D* UEFI: SanDisk Ultra 2.01


If you have a line  Boot0000* Windows Boot Manager, and BootOrder has 0000 as the first, everything is OK. If not:

Create fake Windows partition

efibootmgr -c -L "Windows Boot Manager" -l efi/boot/BOOTx64.efi

Check the Windows partition number. Change boot order so Windows partition is first. On my system, Windows partition is Boot0000, so in boot order 0000 should be first.
If it's not, make it first, and include your Ubuntu partition in the boot order.

efibootmgr -o 0,1,2

And this fix helped me for a year. Now, updating your system, at least if you update grub or kernel related packages, updates EFI boot order as well. It's true for 20.04 and 22.04 as well. So, after kernel update, you get boot order in which Ubuntu partition is first. Well, if you try to reboot, you get error 1962. So you need to change boot order after each update. Luckily, Ubuntu mounts EFI partition and has efibootmgr installed. So, all you need to do:

sudo efibootmgr

Check boot order in the output

If your fake Windows partition is not first, do:

sudo efibootmgr -o 0,1,2

your order can be different if fake Windows partition has different number (not 0).

I am going to create automated script to fix boot order and put it on cron, just in case I forget to check boot order before restart.

---

### Post by oldfred on 2022-11-26
Some vendor's UEFI expect to boot Windows, by description. It does not check actual boot file.You can just create an UEFI boot entry that says Windows, but boots Ubuntu.If Description has to be Windows then change UEFI description. Assumes ESP is sda1. See man efibootmgr for added parameters for other partitions.	
sudo efibootmgr -c -L "Windows Boot Manager" -l "\EFI\ubuntu\shimx64.efi"
sudo efibootmgr -v

[https://ubuntuforums.org/showthread.php?t=2243715&page=3](https://ubuntuforums.org/showthread.php?t=2243715&page=3)

---

### Post by Alex_Filonov on 2022-11-28
If you do it this way, Ubuntu will change partition name on the next grub update.

---

### Post by Alex_Filonov on 2022-11-28
[COLOR=#000000]If you do it this way, Ubuntu will change partition name on the next grub update.[/COLOR]

---

### Post by Alex_Filonov on 2022-11-28
[COLOR=#000000]Wouldn't Ubuntu change partition name on the next grub update?[/COLOR]

---

### Post by oldfred on 2022-11-28
Ubuntu does not really know you created new entry.
And you are still booting shimx64.efi.

But every Windows or Ubuntu update reset UEFI boot order to have that system first. 
So if question is boot order, yes major grub update will change boot order.
Minor updates that do not do a full reinstall of grub, do not update UEFI entries.

You then can use efibootmgr to change boot order.
see also 
man efibootmgr
To see current order:
sudo efibootmgr -v
To change order, as an example:
Change boot order with efibootmgr, some require all 4 hex char others 1 is ok.
 sudo efibootmgr -o 0,1,2

---

### Post by Alex_Filonov on 2022-11-28
That's what original post is about. How to fix efi boot and change boot order.

---

### Post by Alex_Filonov on 2022-12-01
More info. Found out that 22.04 changes EFI boot order at each reboot (and each kernel update as well). So I created a script which runs every 5 minutes on cron and updates boot order if needed. Code below, you would need to change it if your fake Windows partition is not number 0:

 #!/bin/bash#
# Check and fix, if needed, EFI entries and boot order
#


# get current boot order


first=$(efibootmgr | grep BootOrder | awk '{print $2}' | awk -F "," '{print $1}')


if [[ $first != "0000" ]]; then
	echo "Boot change, current order is $first"
	efibootmgr -o 0,1,2
fi


exit 0

---

