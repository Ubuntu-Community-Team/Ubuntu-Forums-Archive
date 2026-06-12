---
title: "Acer Aspire AXC-703G-UW52 boot ubuntu from live usb settings? HELP!!!"
date: 2016-10-09
forum: Hardware
---

### Post by primitive1 on 2016-10-09
If anyone knows about this model or even Acer desktops, etc.,  i am having a problem accessing bios settings from post when computer is first turned on!

I have to go through the windows recovery of windows 8 all the way to the efi settings to get to BIOS settings because neither F2 or F12 comes up for bios or boot modes!

Please explain to me what settings i need to make as far as legacy mode, secure boot, signature, etc. because i am trying to boot with usb 3.0 port with a usb stick that is 3.0.

When customizing secure boot mode it says something about variables being loaded or you can go with standard secure boot.  Also acer manual says there will be a splash screen to hit the F2 or F12 screen and that never happens no matter how i set the computer's bios settings.

I bought the machine recertified and there are no service passwords set and my cable being used to the monitor is hdmi instead of the small vga connector.  Don't really think that makes a difference but someone in another site's post said it did.

Please help as i have had numerous lenovos, dells, gateway, toshiba netbooks, laptops and desktops be able to boot linux from live usb stick and this one just refuses to do so.  THANKS!

---

### Post by Bucky Ball on 2016-10-09
Try the DEL or escape key. If you have a look online you will find the manual for the machine/model and the key will be in there somewhere. 

Which do want to boot in? Legacy or EFI? Whatever Windows is in, that's what you'll be installing Ubuntu in.

Not much point diddling with fast start or secureboot. Both should be OFF when you are installing Ubuntu in either mode. Likewise hibernation in Windows if you are dual-booting. If that is not off you won't get anywhere. Windows in hibernation locks the drive.

---

### Post by oldfred on 2016-10-09
All Acer UEFI require you to set a supervisory password and enable trust from UEFI on the grub/ubuntu .efi boot files in the ESP - efi system partition.
Some Acer threads may suggest downgrading UEFI, but newer ones say newest UEFI works. Make sure you have newest UEFI from Acer.
 Acer Very latest UEFI/BIOS works, downgrade not required:
[http://ubuntuforums.org/showthread.php?t=2298380&p=13419141#post13419141](http://ubuntuforums.org/showthread.php?t=2298380&p=13419141#post13419141) 

      
 Acer Aspire E15 will not dual boot, many details Trust settings in step 35
[URL="http://askubuntu.com/questions/627416/acer-aspire-e15-will-not-dual-boot"]http://askubuntu.com/questions/627416/acer-aspire-e15-will-not-dual-boot
      [/URL]
 Acer Cloudbook shows screen for selecting trust
[http://bernaerts.dyndns.org/linux/74-ubuntu/340-ubuntu-install-acer-aspire-cloudbook-431](http://bernaerts.dyndns.org/linux/74-ubuntu/340-ubuntu-install-acer-aspire-cloudbook-431)
[http://community.acer.com/t5/Predator-Laptops/Dual-Boot-Ubuntu-Win10-Step-by-step-guide/m-p/430392#U430392](http://community.acer.com/t5/Predator-Laptops/Dual-Boot-Ubuntu-Win10-Step-by-step-guide/m-p/430392#U430392) 

 Is your Celeron a Bay  Trail? That may also be an issue.
      
 Ubuntu 14.04 intel_idle.max_cstate=1 required on baytrail to prevent crashes
[URL="https://bugzilla.kernel.org/show_bug.cgi?id=109051"]https://bugzilla.kernel.org/show_bug.cgi?id=109051
[/URL]
 Boot Parameter required
[http://askubuntu.com/questions/695805/acer-aspire-es1-311-freezes-regularly-on-ubuntu-gnome-15-10](http://askubuntu.com/questions/695805/acer-aspire-es1-311-freezes-regularly-on-ubuntu-gnome-15-10)
Acer E3-112-C0MQ - Bay Trail Issue Boot Parameter required
[http://ubuntuforums.org/showthread.php?t=2326162](http://ubuntuforums.org/showthread.php?t=2326162) 

Many Intel Bay Trail Devices Have Been Borked On Linux For The Past Year - Mar 2016
[http://www.phoronix.com/scan.php?page=news_item&px=Intel-Linux-Bay-Trail-Fail](http://www.phoronix.com/scan.php?page=news_item&px=Intel-Linux-Bay-Trail-Fail) 
    [URL="https://bugzilla.kernel.org/show_bug.cgi?id=109051"]
[/URL]

---

### Post by primitive1 on 2016-10-09
> **oldfred said:**
> All Acer UEFI require you to set a supervisory password and enable trust from UEFI on the grub/ubuntu .efi boot files in the ESP - efi system partition.
Some Acer threads may suggest downgrading UEFI, but newer ones say newest UEFI works. Make sure you have newest UEFI from Acer.
 Acer Very latest UEFI/BIOS works, downgrade not required:
[http://ubuntuforums.org/showthread.php?t=2298380&p=13419141#post13419141](http://ubuntuforums.org/showthread.php?t=2298380&p=13419141#post13419141) 

      
 Acer Aspire E15 will not dual boot, many details Trust settings in step 35
[URL="http://askubuntu.com/questions/627416/acer-aspire-e15-will-not-dual-boot"]http://askubuntu.com/questions/627416/acer-aspire-e15-will-not-dual-boot
      [/URL]
 Acer Cloudbook shows screen for selecting trust
[http://bernaerts.dyndns.org/linux/74-ubuntu/340-ubuntu-install-acer-aspire-cloudbook-431](http://bernaerts.dyndns.org/linux/74-ubuntu/340-ubuntu-install-acer-aspire-cloudbook-431)
[http://community.acer.com/t5/Predator-Laptops/Dual-Boot-Ubuntu-Win10-Step-by-step-guide/m-p/430392#U430392](http://community.acer.com/t5/Predator-Laptops/Dual-Boot-Ubuntu-Win10-Step-by-step-guide/m-p/430392#U430392) 

 Is your Celeron a Bay  Trail? That may also be an issue.
      
 Ubuntu 14.04 intel_idle.max_cstate=1 required on baytrail to prevent crashes
[URL="https://bugzilla.kernel.org/show_bug.cgi?id=109051"]https://bugzilla.kernel.org/show_bug.cgi?id=109051
[/URL]
 Boot Parameter required
[http://askubuntu.com/questions/695805/acer-aspire-es1-311-freezes-regularly-on-ubuntu-gnome-15-10](http://askubuntu.com/questions/695805/acer-aspire-es1-311-freezes-regularly-on-ubuntu-gnome-15-10)
Acer E3-112-C0MQ - Bay Trail Issue Boot Parameter required
[http://ubuntuforums.org/showthread.php?t=2326162](http://ubuntuforums.org/showthread.php?t=2326162) 

Many Intel Bay Trail Devices Have Been Borked On Linux For The Past Year - Mar 2016
[http://www.phoronix.com/scan.php?page=news_item&px=Intel-Linux-Bay-Trail-Fail](http://www.phoronix.com/scan.php?page=news_item&px=Intel-Linux-Bay-Trail-Fail) 
    [URL="https://bugzilla.kernel.org/show_bug.cgi?id=109051"]
[/URL]

How can i tell if my processor is an Intel Bay Device?  Are you saying either way about bios version i still have to get a password for UEFI?

---

### Post by howefield on 2016-10-09
> **primitive1 said:**
> How can i tell if my processor is an Intel Bay Device?  Are you saying either way about bios version i still have to get a password for UEFI?

What's the output of 

```
cat /proc/cpuinfo  | grep 'name'| uniq
```

---

