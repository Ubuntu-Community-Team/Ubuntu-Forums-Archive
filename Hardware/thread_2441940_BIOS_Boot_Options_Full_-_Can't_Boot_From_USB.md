---
title: "BIOS Boot Options Full - Can't Boot From USB"
date: 2020-04-28
forum: Hardware
---

### Post by arst06d on 2020-04-28
Hi

I need to decrease the size of my Xubuntu partition to grant more space to my Windows partition, so trying to boot from a LiveCD.  Done this no problem in the past when installing the Windows OS.

However, as you can see from the image, I only have 4 possible options for boot devices - all of which are taken!  I cannot therefore boot from USB CD or USB stick.

I see the there are two PXE devices.  as I understand these would allow me to boot from a network image.  This is a home laptop so this is not something I will ever do.  I can disable these in BIOS but not remove.  When I reboot, they are active again.

How do I go about removing the PXE devices from the boot options altogether which will allow the BIOS to recognise the attached USB CD?

Alternatively - is there another way of safely shrinking and growing partitions which does not require booting from LiveCD?

Thanks in advance.

---

### Post by ajgreeny on 2020-04-28
Can you confirm that the USB was attached and that you know it is a bootable  device: have you tried it on another computer?

How did you create the USB boot device?

---

### Post by arst06d on 2020-04-28
Hi
Yes it was attached, I created the LiveCD by downloading the image and burning it.  Yes, I have used it on this laptop previously as stated - to create the Windows partition originally.
Thanks

---

### Post by ajgreeny on 2020-04-28
You appear to have the same BIOS or UEFI settings as I have on my laptop. Occasionally my USBs do not show immediately and I have to boot to my existing OS Xubuntu 18.04 and attach the USB to mount it, and with it still mounted, restart the system.

The USB then will appear in the list, which incidentally, I do not think is ever limited in number but depends solely on detection of the devices as a boot device.

---

### Post by arst06d on 2020-04-28
That doesn't work.  
Tried inserting a music CD and attaching the USB disk - doesn't mount.

Came at this a different way.

In gparted I deleted the entire Windows partition and ran sudo update-grub.
However it still finds the boot record for Windows from somewhere and I need to get rid of it because it still shows in the BIOS list and it still shows in GRUB menu.

When I run update-grub I get 

> Found Windows Boot Manager on /dev/nvme0n1p1@/EFI/Microsoft/Boot/bootmgfw.efi

How do I delete this reference so the system forgets it?



Getting desperate!

---

### Post by CelticWarrior on 2020-04-28
First of all, not BIOS, it's clearly UEFI. Keeping this in mind avoids confusion and promotes the use of correct terminology. Also makes you look for the correct information for managing you dual-boot, something that you're asking right now, something easily searchable in Google. BIOS and UEFI do the same job but in very different ways and with very different requirements.  

Secondly, **you don't need to remove that Windows bootloader**. By itself it does nothing in the absence of the Windows OS system partition. And it's just a few Kb in a partition that ISN'T user accessible. So there's that, you can leave it alone. But if you want to remove it there are some ways to do it. Many UEFIs allow that management from the firmware settings but alternatively there are software for all OS families to deal with it. In Ubuntu we typically use [efibootmgr]("http://manpages.ubuntu.com/manpages/trusty/man8/efibootmgr.8.html").  

Ina nutshell, in Terminal, just run
```
efibootmgr
```
to obtain the list of all bootloaders and assigned numbers.
Note down the number of the option you want to delete. Then
```
sudo efibootmgr -b <bootnum> -B
```
where <bootnum> is the number found in the previous command. 
Be very careful or you may end up with an unbootable system, reason why users like you that aren't familiar with UEFI yet, almost always should leave the bootloaders alone.

---

### Post by ajgreeny on 2020-04-28
I think you will need to use ***sudo efibootmgr*** to see first what that shows as available and copy it back here and someone other than me will be able to assist you further in more detail than I safely can, never having used it.

See also ***man efibootmgr*** for all the details of using it.

EDIT:
There you are CW was writing at the same time as I was, so I'll now leave you with him.

---

### Post by CelticWarrior on 2020-04-28
> I think you will need to use ***sudo efibootmgr*** 

The command alone can run without privileges, it just lists the bootloaders. Then, to make changes it needs 'sudo'.

---

### Post by oldfred on 2020-04-28
Grub2's os-prober is finding the /EFI/Microsoft folder in the ESP - efi system partition.
Deleting Windows does not delete either the UEFI boot entry nor the folder in the ESP for Windows. You need ESP partition to boot Ubuntu, so do not delete that partition. You can delete the /EFI/Microsoft folder.
You may not have permission from inside your install to see /boot/efi/EFI folders. You can use live installer and mount that partition.

---

### Post by arst06d on 2020-04-29
Thanks all.

I managed to get past this by sudo -i nautilus and deleting the Microsoft folder in /mount, then updating grub.  Didn't affect the entry in the Boot order though, although I take your points above that it doesn't matter.

Managed to unblock the USB boot by plugging a different bootable USB stick - recognised, then plugging in the USB CD with LiveCD and rebooting.  Accessing the boot order Icould see the new entry, altered order, rebooted, resized and made new partion for Windows.

Now all working no problem.

Thanks very much.

---

