---
title: "error booting vista after updating ubuntu"
date: 2009-06-16
forum: Installation &amp; Upgrades
---

### Post by amenezes13 on 2009-06-16
I installed ubuntu alongside Vista just fine (apparently not, but stay with me for a second).  I shrunk the windows partition in vista (using vista), and I used the ubuntu cd to install.  I allocated the free space as follows: 3gb to swap, 20gb to ext3.  Finally, I installed and everything seemed to work.  The grub boot loader started up and I selected vista to ensure that it still worked.  Vista booted up fine but gave me prompts saying that I needed to install a driver...I ignored these prompts (I am kicking myself for this now).  Finally, I restarted from Vista, and the grub boot loader came up again, naturally.

I fired up ubuntu, and I installed only the updated that my friend told me to (he has dual boot with vista and ubuntu working fine).  These updates included vlc, flash plugins, etc.  I restarted ubuntu after these updates installed, and I tried to load vista again from grub.  I got a blue screen error.  I tried repairing vista using various methods, and the only information i acertained was the following: winlogon.exe fails because it cannot find msimg32.dll.  As a result, I searched the directories containing the winlogon.exe file and the msimg32.dll file (aided by my friend, who searched his vista computer at the same time).  Both files were intact, but I overwrote them, just in case.  I restarted, and I continue to get the same error.  I have no idea what could be wrong, and I apologize for the long summary.  I really hope someone can help me, so I won't have to reinstall vista.

---

### Post by o0splitpaw0o on 2009-06-17
Found your problem. Should be able to get into safemode. But you are not going to like it. 

[http://forums.techguy.org/malware-removal-hijackthis-logs/817580-winlogon-exe-error-despite-loads.html](http://forums.techguy.org/malware-removal-hijackthis-logs/817580-winlogon-exe-error-despite-loads.html)

---

### Post by amenezes13 on 2009-06-17
I had it working that one time after the installation though.  Also, windows was running fine prior to installing ubuntu.  Furthermore, my error messages are different from the person in the aforementioned thread.  If I use the "Dell Factory Image Recovery" option, will that be able to restore vista even though the OS partition has been shrunk?  I've asked everyone for help on this, and that seems to be my only option at this point.

---

### Post by amenezes13 on 2009-06-17
bump. any ideas? I don't want to have to go through Dell's crappy "Factory Restore" option since I will lose all of my settings/programs and have to install linux again, I think?

---

### Post by Mark Phelps on 2009-06-17
My guess is that Vista said it needed to install a driver because, presuming you installed in dual-boot mode, it detected new partitions on the drive.

As to the current problem, if you have a Vista DVD, you can boot into it, open a command prompt, and run "sfc /scannow" to get it to scan the system files, look for file corruption, and replace them.

You could also try rebooting from a Vista DVD and running Startup Repair a few times.

If you don't have a Vista DVD, you can download an burn a repair CD image from the NeoSmart forums.

If none of those work, you would need to boot into a non-MS OS, attach an external drive for backing off your files, and use the Dell facility to reload the factory image and, yes, my guess is that it will completely reformat your drive, removing the Ubuntu stuff.

---

### Post by amenezes13 on 2009-06-17
factory restore didnt take off ubuntu...everything works now after using that tool...musta been the stupid driver install.  i had all my data backed up anyway, and i dont intend on using vista much.  thanks for the help.

---

### Post by amenezes13 on 2009-06-17
going to give a quick dual boot install guide for people here so that they can hopefully avoid any trouble:
1. Disable system restore and page file system (unmovable files that make defragging a pain) - Right click My Computer and go to "Properties"...then click "System Protection" for system restore...page file system will be an option labeled with "virtual memory" in another tab.
2. Defrag windows vista using a tool that can defrag while offline (i.e. before windows boots) like Perfect Disk
3. Shrink the vista main OS volume the amount of space that you want to use for ubuntu (after right clicking My Computer and going to "manage").  I used 23 GB total for ubuntu - 3 swap, 20 file system.
4. Re-enable System Restore and the Page File system at this point if you want them back.  I recommend keeping system restore.
5. Restart windows and boot from the ubuntu CD.
6. In the partitioning section, choose the "use largest unallocated free space" option.  Do NOT accept the default option to use the entire hard drive.
7. Assign the appropriate amount of space for a swap partition
8. Repeat for a file system partition and choose ext3 (more stable from what i've heard).
9. Choose mount point (i.e. "/").
10. Let the install process do the rest.
11. Boot into vista from the Grub boot loader.
12. Allow windows to install drivers for the newly detected partition (if you skip or ignore this step, you will probably get screwed over when trying to boot vista again).
13. Restart.
14. Let ubuntu load automatically from the Grub boot loader, and enjoy your new system.

---

