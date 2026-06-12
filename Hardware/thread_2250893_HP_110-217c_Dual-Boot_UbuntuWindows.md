---
title: "HP 110-217c Dual-Boot Ubuntu/Windows"
date: 2014-10-31
forum: Hardware
---

### Post by WanderingAlbatross on 2014-10-31
Dear friends,

Just to let others know of a challenge with this install.  I did everything according to [https://help.ubuntu.com/community/UEFI](https://help.ubuntu.com/community/UEFI).  It would boot into the new grub menu then boot either Ubuntu or Windows 8.  The strange part was that once Windows booted, it would boot straight to Windows on successive boots.  Each time I could fix it by interrupting boot, going back into BIOS and moving Ubuntu to the top of the UEFI boot menu again.  I knew this would be very inconvenient for my grandfather, who owns the computer.  I had to find the reason Windows kept changing the boot order in the BIOS.

Eventually I had to open Windows and type in an administrator's command line:
```
 bcdedit /set {bootmgr} path \EFI\ubuntu\grubx64.efi
```

As per: [http://askubuntu.com/questions/221835/installing-ubuntu-on-a-pre-installed-windows-8-64-bit-system-uefi-supported](http://askubuntu.com/questions/221835/installing-ubuntu-on-a-pre-installed-windows-8-64-bit-system-uefi-supported)

This caused Windows to lay off the monopolizing, and Grub became the bootloader.  I just don't like the idea of Windows having ultimate control over my booting to Gnu/Linux.

---

