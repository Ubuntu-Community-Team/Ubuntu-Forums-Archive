---
title: "HELP:NVME Sanitize Unexpected Outcome"
date: 2024-04-27
forum: Hardware
---

### Post by ddoubleuc on 2024-04-27
Hi Gang,

Not that I knew what to expect in any form, given I’m jube when it comes to using command- line to operate PCs … 

So - using Try Ubuntu and nvme-cli on USB flash drive plugged into my laptop, I ran ‘sudo nvme sanitize -a 4 /dev/nvme0’ (ie crypto erase) then I ran  ‘sudo nvme sanitize -a 2 /dev/nvme0’ (ie block erase) just to be sure. Both operations ran in the blink of an eye. Log command returned success ie the laptop’s internal NVMe PCIe SSD was sanitized.

What I understood was nvme-cli sanitize command was supposed to only sanitize ‘user data’, however on then trying to clean install Windows 11 on the SSD, Windows is unable to locate signed driver device - thus inSTALL.

Casting aside Windows OS humour, any ideas where I went wrong? eg did sanitise go beyond user data coz I selected nvme0 vs nvme0n1?

Thanks for considering

---

### Post by oldfred on 2024-04-27
Signed driver is UEFI Secure boot.
Windows may need a driver for NVMe drives  with secure boot.

Google found this:
> During the Windows 11 installation, **on  the screen to select the storage device, select "Load drivers" >  Browse > Select the Drivers folder on the USB storage > Select the  driver > Next**. If the procedure worked correctly, you should be able to see your NVME drive now.

---

### Post by ddoubleuc on 2024-04-29
Thanx oldFred … loading IRST certainly rectified the driver issue … I’m hoping to understand whether the sanitize operation can still be performed without erasing storage drivers … thoughts?

---

### Post by oldfred on 2024-04-29
Drivers would not be on a drive, but on the installer, or would need to be added to the installer.

You should also make sure you have latest firmware for both UEFI & NVMe drives.

I have never totally erased a drive nor sanitized a NVMe drive.
I know data may still be on drive, but formatting & reusing has been enough for me.

With trim active which is standard, now, deleted data is erased with trim. Makes recovery of data more difficult from SSD/NVMe drives, so backup even more important.

---

### Post by ddoubleuc on 2024-04-30
Thanx again oldfred ...

---

