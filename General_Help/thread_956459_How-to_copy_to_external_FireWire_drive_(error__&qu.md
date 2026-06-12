---
title: "How-to copy to external FireWire drive? (error:  &quot;read-only&quot;) and unmount correctly?"
date: 2008-10-23
forum: General Help
---

### Post by indiworks on 2008-10-23
i) I can't figure out how-to copy files to my external FireWire disc (250 GB). "The destination is read-only." and "The permissions of "Untitled" could not be determined." It was formatted under OS X (10.3.9) and I could (before formatting it) copy files to my Ubuntu PC (but never managed to copy anything onto this disc under Ubuntu).

Someone told me you have get access to the drive as root (or something like that?), but I can't reconstruct the details.

I want to use the disc for back-ups and for video editing.

ii) The other problem I have with it: when unmounting the disc it keeps working (drive keeps spinning etc.) and I have to turn it off in a rather brutal way with the on/off switch. (Not good for the disc!) When I eject the disc on my Mac it also spins down as it should. How can I get this to work under Ubuntu?

Thanks!

---

### Post by MobyTurbo on 2008-10-23
> **indiworks said:**
> i) I can't figure out how-to copy files to my external FireWire disc (250 GB). "The destination is read-only." and "The permissions of "Untitled" could not be determined." It was formatted under OS X (10.3.9) and I could (before formatting it) copy files to my Ubuntu PC (but never managed to copy anything onto this disc under Ubuntu).

HFS+, the format you made it in, is read-only and not reliable in Linux. Format it FAT32, though you'll need multiple partitions, if you want it read-writable in Linux, Windows, and OS X. Or maybe as NTFS and use NTFS3g with Linux FUSE or with OS X MacFUSE, and of course with Windows without assistance.

---

### Post by indiworks on 2008-10-24
> **MobyTurbo said:**
> HFS+, the format you made it in, is read-only and not reliable in Linux. Format it FAT32, though you'll need multiple partitions, if you want it read-writable in Linux, Windows, and OS X. Or maybe as NTFS and use NTFS3g with Linux FUSE or with OS X MacFUSE, and of course with Windows without assistance.

I see, thanks. Since I'm switching from my old iMac I think I can live without having the external drive OS X compatible... So I now installed GParted, but I don't know how to format the external FireWire drive under Linux. It seems that it is locked (permission problems?), please see the attached screenshot.

How can I format the drive for and under Ubuntu? Thanks!

---

