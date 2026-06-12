---
title: "Dell Inspiron 7567"
date: 2017-09-16
forum: Hardware
---

### Post by pepevi83 on 2017-09-16
Hi all,

I just bought a Dell Inspiron 7567 and I am trying to install Ubuntu 14.04, 16.04, 17.04, ...

I've disabled secure boot, added nomodeset, disconnected and connected USB as haraldviste commented,....  but nothing works. Sometimes it crushes even before Ubuntu Live loads, others once it's loaded and I cannot do anything but reboot and start over again. It's getting kind of frustrating/disappointing, I start thinking that I will have to stay with Windows until there is a new version that does not have all this problems :(

Has anyone succeeded in installing Ubuntu in this same model? Could you please help me?

Any help/advise will be much appreciated :)

Regards

---

### Post by mörgæs on 2017-09-17
Hi, welcome to the fora.

Have you tried 17.10 (beta)?

---

### Post by oldfred on 2017-09-17
Often issue is the needed change from RAID (even if one drive) to AHCI.

[https://ubuntuforums.org/showthread.php?t=2353195](https://ubuntuforums.org/showthread.php?t=2353195)

       Dell UEFI Dual boot instructions using Something Else
[https://www.dell.com/support/article/us/en/19/SLN301754/how-to-install-ubuntu-and-a-recent-windows-operating-system-as-a-dual-boot-on-your-dell-pc?lang=EN](https://www.dell.com/support/article/us/en/19/SLN301754/how-to-install-ubuntu-and-a-recent-windows-operating-system-as-a-dual-boot-on-your-dell-pc?lang=EN)
[URL="https://www.dell.com/support/article/us/en/19/sln142679/how-to-enable-boot-from-dvd-option-with-uefi-boot-mode-enabled--windows-8--81--10-?lang=en"]https://www.dell.com/support/article/us/en/19/sln142679/how-to-enable-boot-from-dvd-option-with-uefi-boot-mode-enabled--windows-8--81--10-?lang=en
[/URL]
 Dell XPS 8920 & Nvidia GTX 1060 & PCIe M2 drive Raid change to AHCI
[https://ubuntuforums.org/showthread.php?t=2360929](https://ubuntuforums.org/showthread.php?t=2360929) 

Other Dell threads on similar models mention that UEFI and NVMe firmware both must be updated.

Ubuntu 16 on the DELL XPS15 9550 Tutorial
[https://ubuntuforums.org/showthread.php?t=2345444](https://ubuntuforums.org/showthread.php?t=2345444) 




[URL="https://www.dell.com/support/article/us/en/19/sln142679/how-to-enable-boot-from-dvd-option-with-uefi-boot-mode-enabled--windows-8--81--10-?lang=en"]
[/URL]

---

### Post by linux4me on 2017-11-21
I had a lot of trouble getting Linux running on the Dell 7567 (mostly because I didn't know what I was doing), but it is possible, and once I figured out the steps required, it went pretty smoothly. Once I set the SATA mode in the BIOS to AHCI (the option is only available in later versions of the BIOS, so update to the latest version of the BIOS first), Ubuntu Mate 16.04.3 worked out-of-the-box. 

I had some issues getting Ubuntu 17.10 and Ubuntu Mate 17.10 to work because they would give me a black screen on first boot if I didn't select the option to update software during the install, or hang at the desktop manager when I did select that option, but once I figured out the issue was resolved by installing the nvidia-384 driver as [described here]("https://ubuntuforums.org/showthread.php?t=2375916&p=13713749#post13713749"), both seem to be working just fine.

---

