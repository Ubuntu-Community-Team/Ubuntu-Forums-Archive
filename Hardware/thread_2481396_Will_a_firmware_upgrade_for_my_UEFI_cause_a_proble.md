---
title: "Will a firmware upgrade for my UEFI cause a problem?"
date: 2022-11-28
forum: Hardware
---

### Post by dbbslc on 2022-11-28
When logging in today on my ASUS TUF Gaming F17 FX706HCB_TUF706HCB laptop running Ubuntu 22.04.1 LTS (GNU/Linux 5.15.0-52-generic x86_64) I see the following message which has caused me to wonder if I should do the upgrade. I don't want this Microsoft pushed firmware update to break my UEFI due to some supposed security issue with grub.
Has anyone seen this and know for sure one way or the other whether this upgrade should be done?

---------------------------------------- Message being seen when logging in and executing the 'fwupdmgr get-upgrades' command -------------------------------
```
Welcome to Ubuntu 22.04.1 LTS (GNU/Linux 5.15.0-52-generic x86_64)


 * Documentation:  [https://help.ubuntu.com](https://help.ubuntu.com)
 * Management:     [https://landscape.canonical.com](https://landscape.canonical.com)
 * Support:        [https://ubuntu.com/advantage](https://ubuntu.com/advantage)


1 device has a firmware upgrade available.
Run `fwupdmgr get-upgrades` for more information.




6 updates can be applied immediately.
To see these additional updates run: apt list --upgradable


*** System restart required ***


1 device has a firmware upgrade available.
Run `fwupdmgr get-upgrades` for more information.


Last login: Mon Nov 14 10:41:04 2022 from 192.168.<XXX.YYY>
dbb@dbb-laptop:~$ fwupdmgr get-upgrades
Devices with no available firmware updates: 
 &#8226; ELAN1203:00 04F3:307A
 &#8226; SanDisk Ultra 3D NVMe
 &#8226; System Firmware
 &#8226; UEFI Device Firmware
 &#8226; UEFI Device Firmware
ASUS TUF Gaming F17 FX706HCB_TUF706HCB
&#9474;
&#9492;&#9472;UEFI dbx:
  &#9474;   Device ID:          362301da643102b9f38477387e2193e57abaa590
  &#9474;   Summary:            UEFI revocation database
  &#9474;   Current version:    83
  &#9474;   Minimum Version:    83
  &#9474;   Vendor:             UEFI:Linux Foundation
  &#9474;   Install Duration:   1 second
  &#9474;   GUIDs:              6c9777b8-19f2-5e2c-9210-66ef3691a9f3
  &#9474;                       c8749f7f-439b-5c3c-a2ea-3baacf663a5a
  &#9474;                       c6682ade-b5ec-57c4-b687-676351208742
  &#9474;                       f8ba2887-9411-5c36-9cee-88995bb39731
  &#9474;                       7d5759e5-9aa0-5f0c-abd6-7439bb11b9f6
  &#9474;                       0c7691e1-b6f2-5d71-bc9c-aabee364c916
  &#9474;   Device Flags:       &#8226; Internal device
  &#9474;                       &#8226; Updatable
  &#9474;                       &#8226; Supported on remote server
  &#9474;                       &#8226; Needs a reboot after installation
  &#9474;                       &#8226; Only version upgrades are allowed
  &#9474;                       &#8226; Signed Payload
  &#9474; 
  &#9500;&#9472;Secure Boot dbx:
  &#9474;     New version:      217
  &#9474;     Remote ID:        lvfs
  &#9474;     Release ID:       15179
  &#9474;     Summary:          UEFI Secure Boot Forbidden Signature Database
  &#9474;     Variant:          x64
  &#9474;     License:          Proprietary
  &#9474;     Size:             13.8 kB
  &#9474;     Created:          2020-07-29
  &#9474;     Urgency:          High
  &#9474;     Vendor:           Linux Foundation
  &#9474;     Duration:         1 second
  &#9474;     Release Flags:    &#8226; Is upgrade
  &#9474;     Description:      
  &#9474;     This updates the dbx to the latest release from Microsoft which adds insecure versions of grub and shim to the list of forbidden signatures due to multiple discovered security updates.
  &#9474;     
  &#9474;     Before installing the update, fwupd will check for any affected executables in the ESP and will refuse to update if it finds any boot binaries signed with any of the forbidden signatures. If the installation fails, you will need to update shim and grub packages before the update can be deployed.
  &#9474;     
  &#9474;     Once you have installed this dbx update, any DVD or USB installer images signed with the old signatures may not work correctly. You may have to temporarily turn off secure boot when using recovery or installation media, if new images have not been made available by your distribution.
  &#9474;   
  &#9500;&#9472;Secure Boot dbx:
  &#9474;     New version:      211
  &#9474;     Remote ID:        lvfs
  &#9474;     Release ID:       15178
  &#9474;     Summary:          UEFI Secure Boot Forbidden Signature Database
  &#9474;     Variant:          x64
  &#9474;     License:          Proprietary
  &#9474;     Size:             13.5 kB
  &#9474;     Created:          2021-04-29
  &#9474;     Urgency:          High
  &#9474;     Vendor:           Linux Foundation
  &#9474;     Duration:         1 second
  &#9474;     Release Flags:    &#8226; Is upgrade
  &#9474;     Description:      
  &#9474;     This updates the dbx to the latest release from Microsoft which adds insecure versions of grub and shim to the list of forbidden signatures due to multiple discovered security updates.
  &#9474;   
  &#9492;&#9472;Secure Boot dbx:
        New version:      190
        Remote ID:        lvfs
        Release ID:       6104
        Summary:          UEFI Secure Boot Forbidden Signature Database
        Variant:          x64
        License:          Proprietary
        Size:             14.4 kB
        Created:          2020-07-29
        Urgency:          High
        Vendor:           Linux Foundation
        Duration:         1 second
        Release Flags:    &#8226; Is upgrade
        Description:      
        This updates the dbx to the latest release from Microsoft which adds insecure versions of grub and shim to the list of forbidden signatures due to multiple discovered security updates.
--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------
```

---

### Post by TheFu on 2022-11-30
Every change to a computer is a risk for problems.

If you trust the update, there really isn't much choice, but to install it. It would be smart to backup everything you don't want to lose.  
This applies to every patch for every software.  Assuming you patch your Ubuntu system weekly, there is risk with those updates too.  Always have a backup for anything you don't want to lose. Always. And have a way planned to restore the system or the single file, should something bad happen.

"Hope is not a plan."
Daily backups, with validation they worked AND can be recovered is a plan.  Until you actually test a partial and full system restore, you don't really know if the backups will work or not. Testing is part of risk management, which we all need to be doing.

Or perhaps the data and the system aren't important enough to validate a solid restore plan actually works?  That's fine, if it is a clear choice.

---

