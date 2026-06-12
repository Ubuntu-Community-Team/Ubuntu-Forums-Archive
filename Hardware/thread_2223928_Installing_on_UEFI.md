---
title: "Installing on UEFI"
date: 2014-05-13
forum: Hardware
---

### Post by vperaino on 2014-05-13
I've been struggling with trying to set up three ASUS D550MA-DS01 laptops that were ordered for my company. They are insufferable, the worst of which is the UEFI BIOS which I am trying to overtake and install 12.04 over. 

First, I tried the normal "reset Windows to boot into BIOS" thing, which never works. 

Tried navigating the BIOS itself, no mention of boot order. 

Tried looking for a function key that would access a boot menu. Nope. 

Tried wiping the hard drive to see if I could get rid of Windows influence altogether. Now the computer just boots into BIOS every single time I turn it on. 

Tried installing 12.04 on the hard drive and then dropping it into the machine. No dice. 

Here is a shot of the BIOS menu. I'm pretty sure everything is how it's supposed to be for me to attempt to install Linux on a Windows 8 machine with UEFI. The BIOS recognizes that the DVD drive and HDD are there, but will not allow me to use them as boot options - in fact, NOTHING is allowed as a boot option. 

Any ideas? 

[IMG]http://imgur.com/6PKA5rh.jpg[/IMG]

---

### Post by pdc on 2014-05-13
I guess you have been through such tutorials as these [http://ubuntuforums.org/showthread.php?t=2147295](http://ubuntuforums.org/showthread.php?t=2147295) 

.........old fred seems the expert on these......hopefully he will see your post ...............

---

### Post by vperaino on 2014-05-14
Unfortunately, almost everything in that thread has to do with dual-booting, which I am not interested in.

---

### Post by kc1di on 2014-05-14
what actually happens when you try to run the live DVD /USB stick?

---

### Post by gronne on 2014-05-14
I came in to ask about a related topic. I'm pretty sure your, and my, problem is to do with the bay trail processor. Apparently it can only run 32-bit UEFI and every Linux distro runs 64-bit UEFI. I haven't found any conclusive evidence of how to install a distro. It seems to be possible with some tweaks. If anyone knows how to install Ubuntu on it, please tell.

---

### Post by oldfred on 2014-05-14
Please only attach screen shots, on in line. Some have slower Internet and large graphics lock up their system. 
You can easily attach with Go Advanced editor and use paper clip icon in edit panel at top.

Not dual booting simplifies it as long as you have a system that will boot something other than Windows. Some vendors particularly Sony & HP seem to modify UEFI to only boot Windows.

Do you want UEFI or BIOS boot mode? Either way I suggest including an efi partition in case you want to change later to UEFI and if in BIOS mode you need a bios_grub partition with gpt partitioning.

Is this also a "Bay Trail" system? Similar to one of these. If 32 bit it will not work. If 64 bit you may need 14.04 but the very latest kernel just released that will not be standard in Ubuntu till next version.
 The ASUS "Bay Trail" T100 Is Not Linux Friendly
[http://www.phoronix.com/scan.php?page=news_item&px=MTQ5NzE](http://www.phoronix.com/scan.php?page=news_item&px=MTQ5NzE)
[http://www.phoronix.com/scan.php?page=news_item&px=MTY0OTI](http://www.phoronix.com/scan.php?page=news_item&px=MTY0OTI)

If it will work, then 14.04 would be a much better choice. Intel includes many updates to kernel, support software and video drivers for new hardware and it takes a release or two before those are in the new Linux release.

What is the Intel vitalization setting you have on?

Have you updated UEFI/BIOS to latest version?


  Installation of Ubuntu 14.04 on ASUS N550JV (a Status Report)
[http://ubuntuforums.org/showthread.php?t=2208852](http://ubuntuforums.org/showthread.php?t=2208852)
 ASUS Zenbook Prime UX32VD
[http://www.phoronix.com/scan.php?page=article&item=asus_zenbook_ux301la&num=1](http://www.phoronix.com/scan.php?page=article&item=asus_zenbook_ux301la&num=1)
[http://www.phoronix.com/scan.php?page=article&item=asus_ux32ultrabook_linux&num=1](http://www.phoronix.com/scan.php?page=article&item=asus_ux32ultrabook_linux&num=1)
[https://help.ubuntu.com/community/AsusZenbookPrime](https://help.ubuntu.com/community/AsusZenbookPrime)
 Asus X401U notebook
[http://ubuntuforums.org/showthread.php?t=2169462](http://ubuntuforums.org/showthread.php?t=2169462)
  [SOLVED] Dual Boot on Asus K55vd SX696H - 8 GB (Solved) EFI
[http://ubuntuforums.org/showthread.php?t=2151394](http://ubuntuforums.org/showthread.php?t=2151394)
Asus N56VJ-SH71-CD Shows default Windows partitions Post #25 install instructions
[http://ubuntuforums.org/showthread.php?t=2105622](http://ubuntuforums.org/showthread.php?t=2105622)

---

### Post by olliemonster on 2014-05-14
Im not sure on this but if you have a windows 8 secure boot uefi bios you need to either install 14.04 or switch off secure boot on your pc's uefi bios.

---

### Post by oldfred on 2014-05-14
As far as I know there is not a 32bit distribution.

 New  32 bit UEFI class 3 (no CSM) Only with recompile UEFI/grub/Ubuntu
[http://ubuntuforums.org/showthread.php?t=2189855](http://ubuntuforums.org/showthread.php?t=2189855)
Packard Bell ENME69BMP InsydeH2O  or Gateway LT41P04u
32-bit UEFI Support Proposed For Ubuntu Linux
[http://www.phoronix.com/scan.php?page=news_item&px=MTU1NjE](http://www.phoronix.com/scan.php?page=news_item&px=MTU1NjE)


 Don't ship 32-bit UEFI firmware on x86
[http://mjg59.dreamwidth.org/26734.html](http://mjg59.dreamwidth.org/26734.html)
Some new 64 bit low cost systems with 32 bit UEFI
[http://ubuntuforums.org/showthread.php?t=2189855](http://ubuntuforums.org/showthread.php?t=2189855)

---

### Post by vperaino on 2014-05-14
> **kc1di said:**
> what actually happens when you try to run the live DVD /USB stick?

Literally nothing. It just boots into BIOS with crippled options and no way of creating a new boot path. 

> **oldfred said:**
> 

Do you want UEFI or BIOS boot mode? Either way I suggest including an efi partition in case you want to change later to UEFI and if in BIOS mode you need a bios_grub partition with gpt partitioning.

In this application I will absolutely not need UEFI at all. 

> Is this also a "Bay Trail" system? Similar to one of these. If 32 bit it will not work. If 64 bit you may need 14.04 but the very latest kernel just released that will not be standard in Ubuntu till next version.
 The ASUS "Bay Trail" T100 Is Not Linux Friendly
[http://www.phoronix.com/scan.php?page=news_item&px=MTQ5NzE](http://www.phoronix.com/scan.php?page=news_item&px=MTQ5NzE)
[http://www.phoronix.com/scan.php?page=news_item&px=MTY0OTI](http://www.phoronix.com/scan.php?page=news_item&px=MTY0OTI)

If it will work, then 14.04 would be a much better choice. Intel includes many updates to kernel, support software and video drivers for new hardware and it takes a release or two before those are in the new Linux release.

The processor is listed as a Celeron - I can't seem to find any more information because apparently this is a "black sheep" model that ASUS really doesn't care to provide any specific resources for. 

EDIT: Yes, it is a Bay-Trail. 

> What is the Intel vitalization setting you have on?

I'm assuming you meant "virtualization"? It's disabled. 

> Have you updated UEFI/BIOS to latest version?

I would've, if any of the flashing utilities AMI/Aptio provided actually worked, which they do not.

---

### Post by oldfred on 2014-05-14
It looks like a 64 bit system.
[http://ark.intel.com/products/79051/Intel-Celeron-Processor-N2815-1M-Cache-up-to-2_13-GHz](http://ark.intel.com/products/79051/Intel-Celeron-Processor-N2815-1M-Cache-up-to-2_13-GHz)

A lot of users with very new hardware have installed 14.04 where older versions just did not work.
Some of the older versions even with Intel needed several boot parameters to get it to work like nomodeset, but usually other settings.

       At grub menu you can use e for edit, scroll to linux line and replace quiet splash with nomodeset.
How to set NOMODESET and other kernel boot options in grub2 - both BIOS liveCD & grub first boot ( also UEFI with grub) 
[http://ubuntuforums.org/showthread.php?t=1613132](http://ubuntuforums.org/showthread.php?t=1613132)
Possible boot options suggested by ubfan1
[http://ubuntuforums.org/showthread.php?t=2184839&p=12871710#post12871710](http://ubuntuforums.org/showthread.php?t=2184839&p=12871710#post12871710)
Installer BIOS screens shown
[https://help.ubuntu.com/community/BootOptions](https://help.ubuntu.com/community/BootOptions)

---

### Post by vperaino on 2014-05-14
Son of a mother's lover, GRUB came up with a 14.04 disc. I feel a little bit sheepish now, but my faith in Linux devs has only been strengthened I think. lol 

Thank you for the help. I'll see here in a little while if installations are successful, going to try Ubuntu, Xubuntu, and Mint.

---

### Post by gerberickg on 2014-06-16
> **vperaino said:**
> Son of a mother's lover, GRUB came up with a 14.04 disc. I feel a little bit sheepish now, but my faith in Linux devs has only been strengthened I think. lol 

Thank you for the help. I'll see here in a little while if installations are successful, going to try Ubuntu, Xubuntu, and Mint.

So, did 14.04 successfully install on the ASUS D550MA-DS01 without dual-booting?  Looking at buying this laptop to run stand-alone Ubuntu.

---

### Post by gerberickg on 2014-06-17
For anyone who comes across this thread searching, like I did, I wanted to add some closure:

Ubuntu 14.04 installs onto the Asus ASUS D550MA-DS01 with minimal effort.  As noted in this thread, it doesn't have a BIOS it has UEFI.  I had to press F2 while the machine was booting to enter the UEFI configuration menus.  Here, disable fast boot and secure boot.  You also, for whatever reason, cannot select the DVD drive as a boot option.  To get around this, restart the computer and let it boot into Windows 8.  Restart Windows 8 while holding the shift key, which should bring up the Advanced Startup Options menu.  Select to boot from a removable media device and then select the DVD drive.  This brought me back into the UEFI menus where I was now able to select the DVD drive as my primary boot device.  Restarted once again and I was finally onto my Ubuntu live disk.  I opted to install Ubuntu standalone and wipe out Windows 8.  Everything installed without a hitch and now I have a lovely, and dirt cheap, Linux box for home.

---

