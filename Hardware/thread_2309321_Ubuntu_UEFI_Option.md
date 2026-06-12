---
title: "Ubuntu UEFI Option"
date: 2016-01-09
forum: Hardware
---

### Post by enc on 2016-01-09
I attempted a Ubuntu barebones install recently, and immediately ran into hardware compatibility issues. I didn’t want to deal with it, so I deleted Ubuntu and decided to use Debian instead. 

However, Ubuntu / grub is apparently writing a UEFI option to the boot menu for UEFI mode now. I don’t want to use Ubuntu, and I can’t get rid of the option. 

I’ve tried EasyUEFI, I’ve tried disabling fast boot from Windows, I've reset CMOS and restored from defaults, and I’ve tried deleting the option from the ‘BIOS’ and I can’t get rid of the thing. EasyUEFI just deletes it until the computer is restarted. I’ve searched the forums, and haven’t found a solution. I've tried everything I can think of but can't get rid of this thing. I've never had serious issues with Ubuntu until now...

---

### Post by Dennis N on 2016-01-09
I understand Debian names it's EFI system partition folder 'debian' (right?), so it's safe to remove the folder (named 'ubuntu') left by Ubuntu on the EFI system partition. You should be able to do this from the Debian Installation and browse to that location ( /boot/efi/EFI/ubuntu). On reboot, the UEFI firmware should no longer detect it and remove it from the UEFI boot manager list.

---

### Post by oldfred on 2016-01-09
Not sure if after deleting /EFI/ubuntu if UEFI deletes its entry or not.
But you can delete it with efibootmgr.

 Check entry is there.
sudo efibootmgr -v 

   Delete entry change XXXX to correct entries. Some UEFI require all 4 HEX char, other just need 1 or 2 significant char.
sudo efibootmgr -b XXXX -B
Delete Ubuntu
[http://ubuntuforums.org/showthread.php?t=2289179&p=13331743#post13331743](http://ubuntuforums.org/showthread.php?t=2289179&p=13331743#post13331743)

---

### Post by Dennis N on 2016-01-10
> Not sure if after deleting /EFI/ubuntu if UEFI deletes its entry or not.
On this computer I remember it did (or at least it was not displayed to the user) when the EFI system partition was reformatted, but you are right in that it might not on other systems.

---

