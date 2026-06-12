---
title: "&quot;Unable to mount location&quot; - External hard drive issue"
date: 2016-05-01
forum: Hardware
---

### Post by talkingpie2 on 2016-05-01
Hello,

I'm a newbie to using ubuntu and data recovery and was using a BootMed created CD with the program PhotoRec on it recover a hard drive.  Everything seemed to go well until I logged out and shut down and tried to use the external hard drive that had the files that I recently recovered and transferred to. I was given the message :

> Error mounting: mount exited with exit code 13: The disk contains an unclean file system (0, 0). The file system wasn't safely closed on Windows. Fixing. 
ntfs_attr_pread_i: ntfs_pread failed: Input/output error 
Failed to read NTFS $Bitmap: Input/output error 
NTFS is either inconsistent, or there is a hardware fault, or it's a 
SoftRAID/FakeRAID hardware. In the first case run chkdsk /f on Windows 
then reboot into Windows twice. The usage of the /f parameter is very 
important! If the device is a SoftRAID/FakeRAID then first activate 
it and mount a different device under the /dev/mapper/ directory, (e.g. 
/dev/mapper/nvidia_eahaabcc1). Please see the 'dmraid' documentation 
for more details. 

I've tried googling similar problems/solutions and seems I need to enter the command "ntfsfix" but I wanted confirmation and perhaps a bit more guidance since this seems to be somewhat serious. 

I spent all weekend trying to find solutions to recover my drive and now have run into this silly issue.  It's been very frustrating. Your help is very much appreciated.  Thanks!

---

### Post by weatherman2 on 2016-05-01
We can only guess the state of your external drive, how you used it, etc.

When you were done, did you eject the external drive before unplugging it?  Or did you leave it plugged in until after complete shutdown?  if not - if you unplugged before shutdown without ejecting it - could be the files weren't completely written yet and/or you corrupted the NTFS filesystem on the external hard drive.

I usually recommend using Windows to check/fix NTFS volumes if you have issues with them.  Do you have a Windows disc of any type that you can boot with this external drive plugged in?  I recently booted a Windows 7 disc and was able to run chkdsk on an external drive successfully; older flavors of Windows may not have the USB driver for the external drive.

You might also want to check the health of your external hard drive.  Any hard drive can fail without warning.  I use GSmartControl in Linux to check the S.M.A.R.T. health.  Let's hope your external drive isn't failing too!  I'd probably check this first before doing anything else - because if it's failing too, you may need to get yet another (healthy) drive to recover to.  Look at the S.M.A.R.T. Attributes to see if any are highlighted red/pink in GSmartControl.  (Which you'll have to install in Ubuntu.)  You might also dig up the 2013 version of Parted Magic - the last free version (try MajorGeeks) - and boot that, I still use that version regularly on older hardware.  It has GSmartControl already installed (as "Disk Health" on the desktop) and may detect your external USB drive.  Sometimes it's tricky to get S.M.A.R.T. info out of an external drive and you have to add some extra parameters to the smartctl command...

---

### Post by Bucky Ball on 2016-05-02
Plug it into a Windows box, let it fix what it has to, right click and safely remove it. Looks like you yanked it out while it was still mounted in Windows.

---

### Post by talkingpie2 on 2016-05-02
Thanks for the help guys.

In my mind I saw myself logging out and shutting down Ubuntu before ejecting my external hard drive.  However, I do recall clicking on a file in its folder and not waiting for it to fully load before exiting…


I have Windows Vista, but the original problem was that it wasn’t booting properly and now I keep getting the Restore Factory Settings Option at start.  Therefore, I can’t hook up my external hard drive to it and have Windows fix it.


I have another computer with Windows 10 on it and it doesn’t recognize the hard drive when I plug it in and says the message, “USB Device Not Recognized.”  I tried chkdsk F: /F through command prompt and it says, “Cannot open volume for direct access.”

---

