---
title: "Ubuntu installation left an unusual HD problem on dual boot machine"
date: 2010-11-15
forum: Hardware
---

### Post by oserdavid on 2010-11-15
I have a Tosh Satellite Pro P200 with two internal ATA 160gb hard drives - one is Hitachi and one is Toshiba. Before installing Ubuntu 10.10 it was (and still is) running Vista Business SP2. Originally configured as C:\ (OS and some programs) and E:\ (Data and other programs) on the Hitachi and D:\ (spare - almost empty) on the Toshiba drive.

I installed Ubuntu onto D: as 'alongside other OS' and configured it to use half of the D drive's capacity. The first attempt at installation failed - possibly due to a corrupt DVD disk. The second installation attempt appeared to 'take' perfectly. Except I was surprised not to be confronted with grub on normal bootup, the machine booted straight into Windows. It's a simple matter on this machine to select boot source options (F12 does it) - so I find that when I select boot from the Tosh disk, Ubuntu fires up very nicely and works perfectly. That's OK by me since selecting boot source is no greater hardship than just selecting OS. Though I'm puzzled as to why this happened.

However, my main problem is that on default boot, Windows cannot find its drive D any more. I can get it back very temporarily by using a Windows system restore - but it disappears again quickly. The intended windows sector shows up under 'Manage' in right-click 'Computer' under Windows - but without a drive letter. 'Deleting' it and setting as Simple Volume with NTSF and the appropriate size doesn't work. At the same time Windows insists on looking for drivers for 'unknown device' and not finding them (or sometimes finding an unspecified driver, but not making any difference when it does). It seems to be looking for drivers for the Ubuntu sectors as well as the NTFS sector.

I know this is a Windows issue - but I wondered if anyone here has had any experience of a similar issue - or recognises the problem and can come up with a solution.

Would I be advised to reformat the whole Drive again, make sure it is permanently recognised by Windows (assuming it does) and then trying to reinstall Ubuntu again in the hope of getting a normal grub type option on default restart?

Ho hum...

---

### Post by Quackers on 2010-11-15
I suspect that grub was only installed to the mbr of your second HDD. If you set the second HDD as first boot device and when your Ubuntu desktop loads, open a terminal and type ```
sudo update-grub
```
then watch as grub.cfg is configured. Does the Windows loader appear? If it does then you should now be able to select which OS to boot from when the grub menu appears at boot.

---

### Post by oserdavid on 2010-11-15
Thanks Quackers. Windows Loader does not appear. I have reformatted the drive and will install Ubuntu again once I have solved the problem of Windows only intermittently recognising the offending drive (and then forgetting it again on next reboot). For that, I guess I need another forum more appropriate for a Windows issue.
Best

---

