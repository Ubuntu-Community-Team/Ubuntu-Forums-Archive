---
title: "Dell Laditude E6420 18.04.1 Does not boot after install"
date: 2018-10-15
forum: Hardware
---

### Post by jason.jackal on 2018-10-15
Laptop: Dell Laditude E6420

Was able to install 18.04.1 with no issues; however, machine is just at a blinking courser after BIOS screen. Machine runs through POST and makes it past BIOS; however, hangs at a black screen when it goes to boot the OS, and I do not even get the loading Kernel screen or option boot screen.

Does anyone have issues like this with E6420? If so what can I check?

---

### Post by jason.jackal on 2018-10-15
###UPDATE###
I had to go into the BIOS and select UEFI; however, I am not at all familiar with this method. I had to change FROM Legacy TO UEFI.

Does anyone have details as to why this is the case?

---

### Post by oldfred on 2018-10-15
Microsoft required all Windows installs from vendor with Windows 8 or later to be UEFI with gpt partition. And UEFI Secure boot is on, but user can turn it off.
But UEFI really has 3 boot mode, UEFI with Secure Boot, UEFI, and CSM.
        CSM - UEFI Compatibility Support Module (CSM), which emulates a BIOS mode  
Many vendors call the new UEFI as BIOS since users know that, but all new hardware in about last 5 years is UEFI.

But then when installing a new system you have to boot install media in boot mode you want install to be. And that may not be the default setting of system, once installed. If you install in UEFI mode and have system set to boot in UEFI mode everything works. But mixing in BIOS, or UEFI secure boot complicates it.

      
 Dell UEFI Dual boot instructions using Something Else
[https://www.dell.com/support/article/us/en/19/SLN301754/how-to-install-ubuntu-and-a-recent-windows-operating-system-as-a-dual-boot-on-your-dell-pc?lang=EN](https://www.dell.com/support/article/us/en/19/SLN301754/how-to-install-ubuntu-and-a-recent-windows-operating-system-as-a-dual-boot-on-your-dell-pc?lang=EN)
[https://www.dell.com/support/article/us/en/19/sln142679/how-to-enable-boot-from-dvd-option-with-uefi-boot-mode-enabled--windows-8--81--10-?lang=en](https://www.dell.com/support/article/us/en/19/sln142679/how-to-enable-boot-from-dvd-option-with-uefi-boot-mode-enabled--windows-8--81--10-?lang=en)

Lots of UEFI info & links to more UEFI info in link below in my signature.

---

### Post by jason.jackal on 2018-10-16
> **oldfred said:**
>  If you install in UEFI mode and have system set to boot in UEFI mode everything works. But mixing in BIOS, or UEFI secure boot complicates it.

To be honest, I am not sure what I selected during install. The DVD just booted, and I went with the flow. \o/

This is NEW hardware to/for me, so that could be the issue. Also, I am use to older hardware, and as you point out - most hardware I have is roughly 10< years old. This is the newest machine I have.

Thank you for the links... will read up on it.

---

