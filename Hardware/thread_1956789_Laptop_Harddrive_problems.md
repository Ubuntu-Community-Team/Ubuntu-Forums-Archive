---
title: "Laptop Harddrive problems"
date: 2012-04-11
forum: Hardware
---

### Post by deokisu on 2012-04-11
Hello guys, I hope that you will be able to help me. The problem is this: while using my Windows 7, at some point blue screen appeared and since then I am not able to turn my laptop under Windows os. The thing is that I have Ubuntu as well. However, I am not able even to mount harddrive on it. I would delete that stupid Windows and forget about it, but I have some important files out there as well. Please, help me to restore it. If there is no way to restore windows, may you please advise me how to restore my files at least. Here is information that I am able to provide. Just tell me, if you need anything else.

The message I get, when I am trying to mount harddrive on Ubuntu:

```
"Error mounting: mount exited with exit code 13: The disk contains an unclean file system (0, 0).
The file system wasn't safely closed on Windows. Fixing.
ntfs_attr_pread_i: ntfs_pread failed: Input/output error
Failed to read NTFS $Bitmap: Input/output error
NTFS is either inconsistent, or there is a hardware fault, or it's a
SoftRAID/FakeRAID hardware. In the first case run chkdsk /f on Windows
then reboot into Windows twice. The usage of the /f parameter is very
important! If the device is a SoftRAID/FakeRAID then first activate
it and mount a different device under the /dev/mapper/ directory, (e.g.
/dev/mapper/nvidia_eahaabcc1). Please see the 'dmraid' documentation
for more details."
```Result of fdisk -l

```
"Disk /dev/sda: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders, total 976773168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x00082197

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *        2048      206847      102400    7  HPFS/NTFS/exFAT
/dev/sda2          206848   872323071   436058112    7  HPFS/NTFS/exFAT
/dev/sda3       872325118   974100479    50887681    5  Extended
/dev/sda4       974100480   976773119     1336320   82  Linux swap / Solaris
/dev/sda5       872325120   967817215    47746048   83  Linux
/dev/sda6       967819264   974100479     3140608   82  Linux swap / Solaris
"
```Hope you will be able to help me. Thank you in advance.

---

### Post by Ms. Daisy on 2012-04-12
Did you run chkdisk /f like it said?

---

### Post by deokisu on 2012-04-12
I am not able to run Windows. I tried using installation disk, but it takes me straight to the installation process and I am not able to access command prompt.

---

### Post by Ms. Daisy on 2012-04-12
What about safe mode? Hold down F8 while it's booting (after you chose windows in your grub menu that is).

Do you have a windows recovery partition?

---

### Post by deokisu on 2012-04-12
Safe mode does not even start. What I see is that it loads some files, but at some point it stops (harddrive starts making periodic signals), then laptop reboots. 

And no, I don't have recovery partition.

---

### Post by Mark Phelps on 2012-04-12
Since the hard drive, is as you say, making strange noises, that is an indication that is is failing, or has already failed.

In tht case, you are unlikely to be able to boot any OS on the drive due to filesystem corrutions.

Your best bet, at this point, is to boot the PC from an Ubuntu Desktop CD, choose Try Ubuntu, plug in an external drive -- and drag the files you want to save to the external drive.

You will want those files to be able to restore them after you replace the hard drive.

---

### Post by deokisu on 2012-04-12
I am able to run Ubuntu, so probably there is a problem with bad sectors on the hard drive. It doesn't make some weird scratching noises, it sounds like it starts loading for a sec, but then stops. However, I think you should not pay much attention to noises. 

Right now I am typing to you from my laptop, thus I conclude that harddrive is partly alive. I am not able to mount the partition with Windows, which is on the same harddrive.

---

### Post by Ms. Daisy on 2012-04-12
Disk Utility is an application in Ubuntu. It can check the windows partition for errors.  I know that Mark Phelps has much more experience with it so I'm hoping he can add his thoughts.

Here is a how-to describing options in disk utility.
[http://www.howtogeek.com/howto/37659/the-beginners-guide-to-linux-disk-utilities/](http://www.howtogeek.com/howto/37659/the-beginners-guide-to-linux-disk-utilities/)

Be careful with Disk Utility. It's a powerful program- one wrong click and you can delete your entire hard drive.
Here's a screen shot of what you're likely to see. The windows partition is probably NTFS.

---

### Post by deokisu on 2012-04-12
After using    	 	 	 	 	 	   ```
sudo badblocks -v /dev/sda1
```
I get such result:
```
Checking blocks 0 to 102399
Checking for bad blocks (read-only test): done                                
Pass completed, 0 bad blocks found.

```
Now I am really confused.

---

### Post by DWade on 2012-04-12
It would appear you have lost your mbr boot.

but here is thread that may help you [http://ubuntuforums.org/showthread.php?t=1769482]("http://ubuntuforums.org/showthread.php?t=1769482")

once restore mbr you should be able to load both windows and Ubuntu.

go to Parted Magic down load the ISO and use clonezilla to copy bot images and save them.

---

### Post by deokisu on 2012-04-12
Once again: I am able to load Ubuntu. Windows is the one causing problems.

Here is the [log of Boot Repair.]("http://paste.ubuntu.com/926945/")

---

### Post by deokisu on 2012-04-12
If it was unclear before: I have 2 operating systems on my laptop (Windows 7 and Ubuntu). At some point Windows crashed and now during the boot, after few seconds of windows logo I experience sudden blue screen and immediate reboot. At the same time Ubuntu is working perfectly well, but I cannot mount the partition on which I have Windows. Windows did not start in safe mode (it crashes on loading ATI driver and shows the same blue screen).

If there is no way you can help me to save the previous state of windows, just help me to save some important documents from that partition.

---

### Post by Ms. Daisy on 2012-04-12
This is a link to show how to repair windows from ubuntu

[http://www.makeuseof.com/tag/fix-corrupted-windows-ntfs-filesystem-ubuntu/](http://www.makeuseof.com/tag/fix-corrupted-windows-ntfs-filesystem-ubuntu/)

I haven't tried it so I can't vouch for it though.

---

### Post by ahallubuntu on 2012-04-13
Your #1 goal at this point should be recovering data from what you assume is a failing hard drive.  That means: STOP USING THE HARD DRIVE, even to boot Ubuntu.  Instead, you will want to boot CDs that use the drive only when necessary.  Even using the "good sectors" on the Ubuntu side could put more stress on the whole drive and make things worse.  If the surface of the drive is failing, you want to STOP using it unnecessarily.

First thing, if you can, is to see if your drive really is failing.  Try checking S.M.A.R.T.   I do this with a handy little Linux distro called Parted Magic (google for it).  You can burn this to a blank disc (like burning a Ubuntu disc) and boot it on your laptop to check out the state of your hard drive.  (S.M.A.R.T. is some self-testing/self-monitoring stuff built into every hard drive and very useful if you know how to use it.)

Once you boot, click on "SmartControl" and look for the S.M.A.R.T. Attributes tab.  Look for rows highlighted in red.  These are the real errors you've had so far.  (Pending sectors for example are really bad.)  If there are no rows highlighted, maybe your drive isn't failing after all.

If you have some real problems showing up in S.M.A.R.T., I'd probably just replace your hard drive ASAP.  Then, if you wish to attempt to rescue your Windows partition (and save those files), CLONE old drive to a new one with something like ddrescue that will not exit if it tries to copy bad sectors.  Then, you can attempt file system repair with chkdsk (obtaining a Windows disc that lets you do command prompt) or ntfs-3g as noted above.  But you'd do this on the COPY you made, not the original.

If no S.M.A.R.T. errors show up, maybe your original hard drive isn't failing at all and just had the Windows partition corrupted.  Then you need to run chkdsk on the filesystem.  If you are able to get to the point where you can try to enter safe mode, look for a "Repair" menu item instead.  This may offer you a Command Prompt option.

Otherwise, download and create your own Windows 7 disc to boot and run chkdsk.  There are legal ways to do this - I have - to create your own bootable Windows 7 disc.  Here for example:

[http://forum.notebookreview.com/windows-os-software/428068-legal-windows-7-download-links-just-like-vista-before.html](http://forum.notebookreview.com/windows-os-software/428068-legal-windows-7-download-links-just-like-vista-before.html)

---

### Post by deokisu on 2012-04-13
Unfortunately I found that "Current Pending Sector Count" section is highlighted. Currently I am trying to rescue some data. Is there any way to rescue specific data or do I have to copy the whole drive and then deal with it?

---

### Post by deokisu on 2012-04-17
I am really getting close to what I want to achieve. I was able to create an image of a hard drive with ddrescue tool. Now I am experiencing difficulties to mount this image properly. Here is what I've got.

I have mounted the created image to /mnt folder. However, I cannot access the data. I get the message "The folder contents could not be displayed. You do not have the permissions necessary to view the contents of "mnt"." I tried to unlock the image, using [this information]("http://voices.yahoo.com/changing-permissions-locked-folders-ubuntu-linux-2927907.html"), but it does not seem to work. Please, help me on this last step of restoring my info.

---

