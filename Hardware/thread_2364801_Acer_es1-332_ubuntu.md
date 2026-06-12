---
title: "Acer es1-332 ubuntu"
date: 2017-06-28
forum: Hardware
---

### Post by alanedwards72 on 2017-06-28
Hello,
im thinking about buying this small laptop to use for travelling and portable use and just want to be sure ubuntu works ok on it fully and ask if anyone knows if this is capable of playing 1080p movies via hdmi to a tv. Also is it possible to just turn of the uefi stuff and just use legacy boot to save the hassle and is there any issues I may encounter with it having an eMMC drive instead of a standard hard drive.
i will be removing windows 10 as I've no use for it.
Thanks for any help in advance for any answers to these questions.
[http://www.ebay.co.uk/itm/Acer-Aspire-ES-13-3-Inch-Celeron-4GB-32GB-Laptop-Red-Official-Argos-Store-/332144983639](http://www.ebay.co.uk/itm/Acer-Aspire-ES-13-3-Inch-Celeron-4GB-32GB-Laptop-Red-Official-Argos-Store-/332144983639)
Alan

---

### Post by oldfred on 2017-06-28
Other threads discussing the issues they had with similar Acer ES1.

 Acer Aspire ES1-132 cannot able to install kubuntu UEFI missing options, rEFInd
[https://ubuntuforums.org/showthread.php?t=2348269](https://ubuntuforums.org/showthread.php?t=2348269) 
Acer ES1-331 laptops Strange differences at new installations
[https://ubuntuforums.org/showthread.php?t=2362511](https://ubuntuforums.org/showthread.php?t=2362511) 
Aspire E1-522 InsydeH20 Bios unlock -  7 min video
[https://www.youtube.com/watch?v=7SkBFkzOW0A](https://www.youtube.com/watch?v=7SkBFkzOW0A)
Acer E1-531 UEFI menus.
[http://www.tomshardware.com/forum/65627-63-body](http://www.tomshardware.com/forum/65627-63-body) 
           Acer Aspire ES1-512-C39M Details on supervisor password and settings to enable trust on ubuntu entries Also R14 model same fix
[http://ubuntuforums.org/showthread.php?t=2256083&p=13203044#post13203044](http://ubuntuforums.org/showthread.php?t=2256083&p=13203044#post13203044)
[http://acer--uk.custhelp.com/app/answers/detail/a_id/27071/~/how-to-enable-or-disable-secure-boot](http://acer--uk.custhelp.com/app/answers/detail/a_id/27071/~/how-to-enable-or-disable-secure-boot)
[http://acer.custhelp.com/app/answers/detail/a_id/29349/](http://acer.custhelp.com/app/answers/detail/a_id/29349/)
[http://ubuntuforums.org/showthread.php?t=2290594](http://ubuntuforums.org/showthread.php?t=2290594)

---

### Post by RobGoss on 2017-06-28
Hello and welcome to the forums, As you can see from the response Acer is a bit more difficult to install Linux, there's a few other manufacturers that make installing Ubuntu much eaisier, Dell is one of the ones I would recommend but that's just my opinion

I'm not saying Acer is not a good buy but for some new user it can be problematic and might  discourage your new experience with linux

---

### Post by alanedwards72 on 2017-06-28
Thanks robgoss and oldfred for your responses. I've already got an acer v3-571 laptop that was bought just after windows 8 and Uefi came out. On that I turned the uefi of and use The legacy drive option and I've had no issues using and installing ubuntu ever since. I was hoping I could just do the same on the newer acer but wasn't sure if that option is available nowadays. I only plan on using one partition on the drive and to be honest I don't know what I'd gain from using uefi. I did consider a dell but this option for £120 seems very good value if I can install ubuntu ok.

---

### Post by RobGoss on 2017-06-28
You should be able to install Ubuntu on the new machine, you have to shuffle a few things around in the BIOS but it's still doable

As far as UEFI I don't think it's does much besides lock down the BIOS to prevent installing other systems

---

### Post by oldfred on 2017-06-28
I still prefer to use the newer gpt partitioning even if using BIOS boot.
Normally gpt is used with UEFI and Windows only boots with UEFI from gpt.

But Ubuntu can use either UEFI or BIOS to boot from gpt if correct supporting partitions are used.
With UEFI you have to have the ESP - efi system partition (FAT32), and with BIOS you have to have a bios_grub partition which is unformatted.

I started to switch to gpt back in 2010 on my old BIOS system. Cannot say I noticed any difference, but also no issues. The gpt(GUID) is newer and has a backup partition table and better internal structures to avoid issues.

I also use gpt on my larger flash drives with a full install of Ubuntu.I used to use BIOS with gpt, but new systems are UEFI, so I now only use UEFI with gpt.

 GPT Advantages (older 2010 but still valid)  see post#2 by srs5694:
[http://ubuntuforums.org/showthread.php?t=1457901](http://ubuntuforums.org/showthread.php?t=1457901)
[https://wiki.archlinux.org/index.php/GUID_Partition_Table#Advantages_of_GPT](https://wiki.archlinux.org/index.php/GUID_Partition_Table#Advantages_of_GPT)
[http://en.wikipedia.org/wiki/Unified_Extensible_Firmware_Interface](http://en.wikipedia.org/wiki/Unified_Extensible_Firmware_Interface)
[http://askubuntu.com/questions/629470/gpt-vs-mbr-why-not-mbr](http://askubuntu.com/questions/629470/gpt-vs-mbr-why-not-mbr)
UEFI Advantages
[http://askubuntu.com/questions/647303/uefi-or-legacy-which-is-advised-and-why/647604#647604](http://askubuntu.com/questions/647303/uefi-or-legacy-which-is-advised-and-why/647604#647604)
[http://askubuntu.com/questions/446968/legacy-vs-uefi-help](http://askubuntu.com/questions/446968/legacy-vs-uefi-help)

---

