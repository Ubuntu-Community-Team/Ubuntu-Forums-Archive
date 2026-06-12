---
title: "[SOLVED] Sansa Clip MP3 player now useless?"
date: 2008-10-16
forum: Hardware
---

### Post by xscd on 2008-10-16
Hello all-- I recently bought a tiny and cute Sansa Clip "MP3 player." It had some problems mounting in Linux (had old firmware), and after consulting various online forums here and at AnythingButiPod.com and SanDisk's own support forum, I read numerous reports that said the same thing: update the firmware, or if all else fails, reformat the Clip.

I downloaded SanDisk's "Sansa Updater" application and tried to run the Windows-only program under Wine. No luck. Then before I discovered that one could manually update the firmware, I reformatted the flash memory of the drive using gparted. This was before I learned that "reformat" at the forums meant "use the Clip's own 'Format' command."

So, the Clip was then useless, a cute little plastic brick beside the computer. I contacted SanDisk tech support (still haven't heard from them, a few days later) and wrote messages on all the forums pleading for help.

As is the case many times, I ended up helping myself. I did some more research and tried lots of ideas. One of them worked. The solution is in two parts.


Before trying the steps below, if your Sansa Clip has not been completely rendered useless yet, you may be able to use its own Settings--> Format command to reformat the Clip. That is easier and better, and then you can update the firmware manually (check the SanDisk forums or AnythingButiPod.com forums for firmware versions).

**[COLOR="Green"]How to get a useless Sansa Clip working again[/COLOR]**

[LIST=1]
[*]Reformat the Sansa Clip's flash memory and install a FAT32 filesystem. You can reformat it in Linux using Gparted, but the Clip still won't work because the Clip wants the exact settings that Windows uses when it formats a blank disk. However, reformatting the Clip in Gparted will serve the purpose of ensuring that it absolutely won't work nor be recognized by a Windows machine. So go ahead and do that once if you like. Then plug the Sansa Clip's USB2 connector into a machine running Windows or Vista. Then use Windows file manager (Windows Explorer) to try to open the drive letter of the Windows-detected USB device. Windows will give an error message saying the drive is unformatted, and offer to format it for you. Choose FAT32 filesystem and UN-check "Quick format." Then let Windows format the Sansa Clip's flash memory.
[*]After the Clip is formatted in Windows, remove it ("safely remove hardware" icon in system tray, followed by disconnecting the USB cable). Then go to SanDisk.com and download the "Sansa Updater." This application is for updating the firmware of already working Sansa Clips, but believe it or not, it can also completely restore the firmware and directory-structure and files that the Clip needs to run. After downloading and running or installing the Sansa Updater, close the program. Then plug the Clip back into Windows. It should be recognized and the Sansa Updater program may automatically launch. If not, then find the Sansa Updater in the Start menu, launch it and follow its directions. It will search for your Sansa Clip, then download the latest firmware, then restore your used-to-be-useless Sansa Clip to a pristine, factory-approved, completely updated state that works great with Ubuntu Hardy Heron and **even** now supports OGG and FLAC!
[/LIST]

Best wishes all. Hope this helps other Sansa Clip users. :-P

---

