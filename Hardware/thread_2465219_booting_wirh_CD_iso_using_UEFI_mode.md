---
title: "booting wirh CD iso using UEFI mode"
date: 2021-07-26
forum: Hardware
---

### Post by angel mike on 2021-07-26
Using a Dell Inspiron 3670 and setting boot mode to UEFI there is an option to add a boot mode which I want to use for an external CD drive containing a Ubuntu  20.04 iso.
How do I specify the File Path required. Connecting the drive does not show up a file  path

---

### Post by oldfred on 2021-07-26
The boot mode setting is for your installed system.
You normally get two boot options with Ubuntu ISO, one clearly UEFI and one not, which is the old BIOS boot.
But you have to have created DVD correctly, often better to use flash drives. Back when I still used CDs/DVDs, I made a lot of coasters(bad burns).
Flash drives are reuseable and offer more flexibility.

Dell  Inspiron 3670 UEFI update & AHCI worked
[https://ubuntuforums.org/showthread.php?t=2412152](https://ubuntuforums.org/showthread.php?t=2412152)

Dell typically needs UEFI update, if SSD also SSD firmware update.
It needs UEFI setting for drives changed to AHCI, not Intel RST nor RAID. But if dual booting with Windows you must first install AHCI drivers into Windows or Windows will not boot.
Often better to have UEFI Secure boot off. And UEFI fast boot off, as that assumes no system changes & you are changing system.
Newer systems need legacy off to boot in UEFI mode.
And in Windows you need Windows fast start up off as that sets hibernation flag and then Linux NTFS driver cannot see the NTFS partitions. Note that Windows updates may turn fast start up back on.

See also general install steps in my link below.

Lots of info on USB boot for installing
[https://help.ubuntu.com/community/Installation/iso2usb](https://help.ubuntu.com/community/Installation/iso2usb) & 
[https://help.ubuntu.com/community/Installation/FromUSBStick](https://help.ubuntu.com/community/Installation/FromUSBStick)

---

### Post by angel mike on 2021-07-27
Thanks for the response. I have found the cause of my problem - I  was using a CD setup for Legacy. Once I downloaded UEFI version onto a  USB it showed up in the BIOS. Beware if buying online ! Will mark as  solved

---

