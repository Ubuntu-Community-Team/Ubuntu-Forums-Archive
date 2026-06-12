---
title: "New HP Envy 17 inch with Haswell Graphics, display de-activated?"
date: 2013-09-25
forum: Hardware
---

### Post by ken-zwn on 2013-09-25
I am having a very weird issue with a new computer (HP Envy 17th, intel 4700MQ, 4600 HD graphics)

This model does have UEFI. I am booting with secureboot disabled, and the compatibility module loaded.)

If I boot with nomodeset in grub... I get access to the laptop display. If I exclude nomodeset (also deleted "quiet splash"), and I have an external display attached, the external display works and I am able to login... but nothing on the laptop display itself.

If I boot with nomodeset, the laptop display works, but I have no monitor showing as attached via the HDMI cable (it is attached) in the display manager.

Running 13.04.

Any insight?

---

### Post by Yellow Pasque on 2013-09-26
Try a Xubuntu 13.10 LiveUSB. (I recommend Xubuntu so you don't have to deal with XMir).
[http://cdimage.ubuntu.com/xubuntu/releases/saucy/beta-1/](http://cdimage.ubuntu.com/xubuntu/releases/saucy/beta-1/)

---

### Post by oldfred on 2013-09-26
I agree with Temüjin on 13.10 even though still beta. Your hardware is so new, you need the latest kernel and related drivers. 

These were Toshiba's but I think the issues & solutions were more related to the new Haswell configuration.

 Toshiba Satellite P50 model number: P50-A-01E Haswell processor
[http://ubuntuforums.org/showthread.php?t=2163854](http://ubuntuforums.org/showthread.php?t=2163854)
Turned NIC (Integrated Network Interface Controller) off and then booted off of USB. Was NOT an issue with any Linux distro just a quirk of the laptop.
 Am now running 13.10 daily and everything works. Also had to stick with EFI boot ON, Secure Boot disabled. Wouldn't boot off of any media or HDD when mode set to CSM.
Toshiba Satellite P75 intel hd 4600 needed acpi_osi=Linux acpi_backlight=vendor
[http://ubuntuforums.org/showthread.php?t=2161204](http://ubuntuforums.org/showthread.php?t=2161204)

---

### Post by ken-zwn on 2013-09-26
I have booted with a pre-release copy of 13.10 (reg ol Ubuntu) on a USB stick and the system boots with nomodeset. Still blackscreens with just "quiet splash --" in grub. Got rid of the issue of compliing the realtek WiFi driver (apparently included in 13.10). I did not get a chance to try troubleshooting the extended display issue again... which is the major deal breaker for me.

But... some other features on the laptop are going to have me troubleshooting for an extended period (Beats speakers for one thing). So... it will be going back to Costco. (for future troubleshooters the Envy model # is C8U17AV).

I am ending up getting a 15" Gazelle from System76. :-)

---

