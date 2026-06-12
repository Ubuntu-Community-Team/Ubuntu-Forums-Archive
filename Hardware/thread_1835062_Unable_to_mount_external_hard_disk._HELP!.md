---
title: "Unable to mount external hard disk. HELP!"
date: 2011-08-28
forum: Hardware
---

### Post by davy jones on 2011-08-28
I have a western digital 2 TB external hard drive. It was working fine and suddenly in the middle of a file transfer I got the following error message
[B]
Error mounting: mount exited with exit code 13: $MFTMirr does not match $MFT (record 0).
Failed to mount '/dev/sdb1': Input/output error
NTFS is either inconsistent, or there is a hardware fault, or it's a
SoftRAID/FakeRAID hardware. In the first case run chkdsk /f on Windows
then reboot into Windows twice. The usage of the /f parameter is very
important! If the device is a SoftRAID/FakeRAID then first activate
it and mount a different device under the /dev/mapper/ directory, (e.g.
/dev/mapper/nvidia_eahaabcc1). Please see the 'dmraid' documentation
for more details.[/B]

After this, the drive refused to be mounted. This has happened to me before so I did what I had done the last time, i.e, run chkdsk /f on windows and reboot twice. This had solved the problem the last time but this time it didn't. The second part of the error message (about softRAID/fakeRAID) makes no sense to me whatsoever but I'm guessing that's not relevant to my hard disk since the problem got solved the last time by just doing the run chkdsk /f on windows.
[B]
Some things (if relevant) which are different this time from the last time I faced this problem are these -[/B]
1. The hard disk has been formatted since then but the partition system is the same (NTFS).
2. Last time after rebooting windows twice when I tried to 'safely remove' the drive it showed an error message saying that the hard disk was in use. After rebooting it the third time I was easily able to safely remove the hard disk. This time the same error message showed up after the second reboot but it did not go away even after the third and the fourth reboots and I just had to shut the system down, turn off the drive and take out the usb cable. 

_**I REALLY REALLY need help with this as I need to transfer data onto this hard disk. I would seriously owe anyone who helps me solve this.**_

---

### Post by alarme on 2011-08-28
hi

Linux can't mount an NTFS partition if is marked as dirty.
If you cannot safely unmount it on windoze, maybe you have a virus (autorun.inf or some other) writing your USB and avoiding safe eject.

From console, try:

cd /home/yourusername
mkdir mnt

# in the next line, replace sda5 for the correct device as your USB hard disk

ntfs-3g /dev/sda5 /home/user/mnt -o ro

This would mount it as read-only
Then, you can copy the files to your PC
After, you can reformat the USB hard disk and copy your files back to it.
---

Or, take another windoze PC
Disable autorun BEFORE plugin your USB hard disk (search for tweakUI or security policies)
In explorer, enable "show hidden files"
Plug the USB
If you find autorun.inf, delete it
Search for suspicious .exe on the root of the disk
After this, proceed with chkdsk /f for this disk letter

Good luck

---

### Post by BitJunkie on 2011-08-29
I have the same problem when copying large amounts of data to a 1 TB Seagate USB external drive. If you find a solution, please post it!

---

### Post by davy jones on 2011-08-29
Ok so I haven't tried the first solution because I want to keep formatting the drive as the last option. But about the second solution - the autorun.inf file on this hard disk was deleted when I formatted it earlier so that cannot be the problem. I also looked for any hidden files on the hard disk and there was no .exe (is that what you meant by root of the hard disk?). The drive only and only has the files and folders that I put there and nothing else whatsoever. 
Trying chkdsk /f on another windows PC failed. The PC just wouldn't boot with the hard disk connected when I restarted it after running chkdsk /f. I checked the BIOS so that's not the problem. This could actually just be a problem in this particular PC. I'm gonna try it in the windows laptop I tried it on earlier but I'm not very hopeful.
If there are any other solutions, please let me know. Thank you.

---

### Post by davy jones on 2011-09-02
So I finally decided to format the drive because nothing else seemed to be working. Its working fine now but if anyone knows a long term solution to prevent this from happening again, please let me know. Thank you

---

### Post by davy jones on 2011-09-22
Ok I'm posting this on the same thread because its relevant. Very often I get strange errors while transferring files onto my external hard disk like "Error splicing file". And sometimes certain files and folders refused to be deleted and they give errors like "Cannot delete file/directory - Input/Output error". I tried to delete those files/folders in windows but that didn't work either. I am really tired of having to format the drive every time something like this happens. I've done it thrice already and it takes ages to transfer all my data back into it. So can someone PLEASE tell me a less weary solution to this??

---

### Post by mentalcic on 2012-01-15
As it turns out according to the searches from various forums this is a common problem and is related with file copying/moving from one location to another. My scenario was booting latest live Xubuntu from USB Flash drive on a HP Compaq nx9020 in attempt to save files from both hdd partitions (unknown/broken and NTFS) and copy them on external USB WD My Book (NTFS).

So to eliminate some things:
1. USB Flash drive is tested and it works perfectly on HP Compaq nx9020, Toshiba Satellite A210-19j and on ASUS EeePC 4G Surf.
2. Computers are virus free, no autoruns, unwanted executables or malicious software, checked it more than once.
3. Could accept that internal hdd is broken but since it was clearly mounded and allows access to data I would go with broken MBR or broken WindowsXP (Error is BSOD while starting up with message UNMOUNTABLE_BOOT_VOLUME)

Symptoms:

It seems that both internal hard drive and external USB hdd get unmounted in the process at the moment it gets "stuck" on a file copy and error is presented:
Error splicing file.
Input/output error.
Do you want to skip it?
[Cancel] [Retry] [Yes to all] [Yes]
Retry does not help. Partially copied file is being replaced and it gets stuck on the same spot again and again.

Wish someone could get into this issue since I believe it is related to all versions of Ubuntu and not to specific version/release.

I don't know how to "monitor the system" in order to determine what happened at the certain point when it gets "stuck" and would appreciate some advice/help on this in order to provide more information.

UPDATE:
While I was typing the above on Toshiba, got spammed thrown to the console on HP laptop and XFCE session was killed in the middle of retrying to copy a 400Mb file.

---

