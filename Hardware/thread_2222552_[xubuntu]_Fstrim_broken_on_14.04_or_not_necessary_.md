---
title: "[xubuntu] Fstrim broken on 14.04 or not necessary anymore?"
date: 2014-05-07
forum: Hardware
---

### Post by dracan_lin on 2014-05-07
Hi everyone,

I have a problem triming my ssd. I know that xubuntu 14.04 is trimming the ssd by default, but when I tried to do it manually I got the following error: fstrim: /: FITRIM ioctl failed: Error inpout/outpout The command I issued is sudo fstrim -v /

My SSD is a OCZ-VERTEX2 80GB. The bios is rather old and has the following options for my ssd: lba mode- supported, block mode-16 sectors, pio mode-4, asynch dma: multiword dma-2, ultra dma-6 S.M.A.R.T supported (enabled). OnChip SATA type is "sata as ide" and not "SATA as raid". I can't enable AHCI on the bios, because it's not an option. I tried another ssd on this old motherboard, same results. Everything worked fine until 12.04, I could manually trim and set up cron! Xubuntu 14.04 failed to trim and so did Debian Jessie (wheezy works fine). Discard is not an option, because it puts some weight on the ssd.

The ssd is only going to hold the operating system (xubuntu 14.04), home folders for 3 users and a very limited set of software. Media and download folders for the users will be on an HDD (probably will move user home folders too), swappiness will be limited to 10% to further take off some weight from the ssd.

My questions:
1. Since I'm not going to install or uninstall software on the ssd and write/move/copy large files on it (videos, mp3, pictures are stored the hdd, is it necessary to trim?
2. Is trim still enabled by default, but gives error when trying to perform manually?

Thank you for your time!
Cheers
Kostas

---

### Post by trag on 2014-05-12
The trim support is limited to Samsung and Intel by default :( , so you will still need to fstrim your drive.
good luck
trag

---

### Post by impliedconsent2 on 2014-07-02
> **trag said:**
> The trim support is limited to Samsung and Intel by default :( , so you will still need to fstrim your drive. good luck trag

"by default..." is the keyword; however, you could try to edit /etc/chron.weekly/fstrim with the last line:  ```
exec fstrim-all --no-model-check
``` I have an OCZ Vertex2 120GB and the only issue I have with my system is that my Haswell-based hardware (legacy or UEFI) will see the Vertex2 every other time on reboot (known OCZ bug - they refuse to fix). I have not had a problem between Ubuntu 14.04 and Vertex2.

---

### Post by santaclaws2 on 2015-03-12
I'm encountering the same problem (error). I have an Intel SSD which supports TRIM function. That's (part of) 'hdparm -I /dev/sda' output:

```

    Model Number:       INTEL SSDSC2xxxxx                   
    Serial Number:      xxxxxxxxxxxxxxxxxxxxxx    
    .....
    device size with M = 1024*1024:       57241 MBytes
    device size with M = 1000*1000:       60022 MBytes (60 GB)
    Nominal Media Rotation Rate: Solid State Device
    .....
Commands/features:
    Enabled    Supported:
    .....
       *    Data Set Management TRIM supported (limit 1 block)
       *    Deterministic read data after TRIM

```

However, when I run 'strace fstrim -v /' I got this file access errors (no need to post the whole command output):

```

open("/usr/share/locale/en_US/LC_MESSAGES/util-linux.mo", O_RDONLY) = -1 ENOENT (No such file or directory)
open("/usr/share/locale/en/LC_MESSAGES/util-linux.mo", O_RDONLY) = -1 ENOENT (No such file or directory)
open("/usr/share/locale-langpack/en_US/LC_MESSAGES/util-linux.mo", O_RDONLY) = -1 ENOENT (No such file or directory)
open("/usr/share/locale-langpack/en/LC_MESSAGES/util-linux.mo", O_RDONLY) = -1 ENOENT (No such file or directory)
write(2, "fstrim: ", 8fstrim: )                 = 8
write(2, "/root: FITRIM ioctl failed", 26/root: FITRIM ioctl failed) = 26
write(2, ": ", 2: )                       = 2
open("/usr/share/locale/en_US/LC_MESSAGES/libc.mo", O_RDONLY) = -1 ENOENT (No such file or directory)
open("/usr/share/locale/en/LC_MESSAGES/libc.mo", O_RDONLY) = -1 ENOENT (No such file or directory)
open("/usr/share/locale-langpack/en_US/LC_MESSAGES/libc.mo", O_RDONLY) = -1 ENOENT (No such file or directory)
open("/usr/share/locale-langpack/en/LC_MESSAGES/libc.mo", O_RDONLY) = -1 ENOENT (No such file or directory)
write(2, "Input/output error\n", 19Input/output error
)    = 19
exit_group(1)                           = ?
+++ exited with 1 +++

```

The error message is the same: **"FITRIM ioctl failed: Input/output error"**.

I've tried to reinstall "util-linux" and "util-linux-locale" packages with no luck. The above files doesn't exist and are not writen by any of these package installation procedure.

The "util-linux" version is 2.20.1-5 (the highest version available for xubuntu 14.04). Anyway, I found a link with the util-linux 2.25.2-1 file list ( [https://www.archlinux.org/packages/core/x86_64/util-linux/files/](https://www.archlinux.org/packages/core/x86_64/util-linux/files/) ) where those missing files are present in that package.

Does anyone knows if I could manually install a higher version of util-linux (2.25.2-1) or I'll get into trouble with other outdated dependencies? Seems like there is a bug with actual version (2.20.1-5). Any help are greatly appreciated.

---

