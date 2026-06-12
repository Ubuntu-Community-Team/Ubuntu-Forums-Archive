---
title: "Wd elements no longer opens."
date: 2012-05-06
forum: Hardware
---

### Post by Filthy Stockings on 2012-05-06
Have been using a WD ELEMENTS 1 TB EXTERNAL HD for over 10 months and a WD ELEMENTS 2 TB EXTERNAL HD for 4 months; only plugging in weekly to backup data.

ALL whilst using U 11.04 OS.

BUT one week ago, as backing up items to 2TB unit, the COPY TO process suddenly stopped and noticed the EXTERNAL HD icon on the DASH had vanished and then seemed to intermittently re-appear...then not re-appear so had to disconnect without SAFELY REMOVE option.

Then tried same USB CABLE/POWER UNIT for the 1TB to try and back up to that; since needed some space on the PC....but same problem occurred as copying data and had to remove without SAFELY REMOVE option.

When tried to start the 1TB up again got the following alert on screen;

                                  [SIZE=3]Error mounting: mount exited with exit code 13: $MFTMirr does not match $MFT (record 0).[/SIZE]
 [SIZE=3]Failed to mount '/dev/sdb1': Input/output error[/SIZE]
 [SIZE=3]NTFS is either inconsistent, or there is a hardware fault, or it's a[/SIZE]
 [SIZE=3]SoftRAID/FakeRAID hardware. In the first case run chkdsk /f on Windows[/SIZE]
 [SIZE=3]then reboot into Windows twice. The usage of the /f parameter is very[/SIZE]
 [SIZE=3]important! If the device is a SoftRAID/FakeRAID then first activate[/SIZE]
 [SIZE=3]it and mount a different device under the /dev/mapper/ directory, (e.g.[/SIZE]
 [SIZE=3]/dev/mapper/nvidia_eahaabcc1). Please see the 'dmraid' documentation[/SIZE]
 [SIZE=3]for more details.[/SIZE]
  
As a technical novice am ignorant as to what the above means but as installing the 2TB also produced the same alert, and after swapping the USB and POWER UNITS; am now stuck with 2 apparently unusable EXTERNALS with over 2TB data between them; which I now fear might have been lost.

I copied the alert and sent it to WD SUPPORT but they only replied stating that if I had used a LINUX system then they would not help as the products were designed for WINDOWS OS; even though the retailers informed me they would work on LINUX systems and that proved to be correct, without any REFORMATING needed, just plug in and use, and FOR NEARLY A YEAR for the 1TB.

Can anyone advise me what to do next please?

---

### Post by ahallubuntu on 2012-05-06
The fact that both of them do the same thing probably indicates either some corruption in your system or some problem on your system that has corrupted both filesystems.  OR, you have a hardware problem with your computer and the USB ports are no longer working.

The way to figure this out is to change different things and see if you are able to access the drives.

First, do you have any other computer you can plug these drives into?  Obviously if your drives work OK on another computer, then the drives themselves are fine.

If you don't have another computer, do you have an original Ubuntu live CD you can boot on this computer?  If you can boot that, see if the drives work there.  If they do, then again there's something corrupt in your Ubuntu installation.

If you find out the drives are corrupted (because they don't work on another computer) either, running Windows chkdsk /f as the message describes might be a good idea.  Having access to a Windows computer would help.  You may also be able to download/burn a Western Digital diagnostic disk from their website and see if you can boot it and use it to test out the drives.

A final thought: what kind of power are the drives plugged into?  A power strip?  Can you try a different power plug, just for fun?  It's possible I guess that the power supplies have failed or got zapped by a power surge (were both plugged in all the time even if the drives were not on?).  There are a lot of possibilities with your issue, of course!

---

### Post by Filthy Stockings on 2012-05-06
Thanks for reply.

The USB ports work for other external devices so they must be ok.

As I stated, I ended up using the same WD supplied power supply cable and USB cable with BOTH HDs so if there was a fault with one of them, then that must have caused the failure to, I think it is referred to as UNSAFE UNMOUNTING when removed both HDs from the PC.

Swapped the power and USB cables to re-try both of the WD ELEMENTS and they still gave the same ALERT....so maybe the damage already done and only way to tackle it is to perform another operation; as the ALERT stated [tho, I do not understand its terminology; hence request here for some definition of the words/procedures described]

Have read on other threads with similar ALERTS received that there is the option you quote re using a WINDOWS PC to plug them into and to then do the chkdsk /f but have not been able to locate another PC just yet [hopefully tomorrow]

BUT they also suggest the other option, which is to 

[I]" Code: sudo apt-get install ntfsprogs 

This package has a nice collection of tool for ntfs drives. To fix your problem let's say your drive is /dev/sda2
[/I][I]
[/I][I]Code: sudo ntfsfix /dev/sda2 
[/I]
*This should fix the disk. Reboot after this."*


Have  got as far as installing the ntfsprogs but, excuse me for being dim,  but do I have to then MOUNT THE WD ELEMENTS and THEN input the next line  of code? 



Just want to be sure am not adding any greater risk to losing the 2TB data on the disks.


*Also as my own ALERT refers to *[SIZE=3]'/dev/sdb1' [SIZE=2]do you think I input the code;[/SIZE][/SIZE]


[SIZE=3]sudo ntfsfix /dev/sdb1      ?[/SIZE]


[SIZE=2]Any further advice gratefully appreciated.[/SIZE]
[SIZE=2]
[/SIZE]
[SIZE=3][SIZE=2]Thanks[/SIZE][/SIZE]

---

### Post by ahallubuntu on 2012-05-06
You would need to attach the drive before running ntfsfix but DO NOT try to mount it (the tool would hopefully warn you against doing that).  I personally have never used that tool - I would prefer using Windows own chkdsk tool for fixing NTFS disks, but if that's all you have I guess you can try it.

Yes,
```
sudo ntfsfix /dev/sdb1

```

would indeed be the correct command if your Windows partition (on the external drive) is /dev/sdb1 .

FYI, in the future, if you aren't planning to use your WD drives with Windows computers, you can reformat them as ext4 and then you can use native Linux tools to try to fix issues.  Of course, you'll have to copy all data off the drive first before reformatting it as ext4 - something to consider for the future.

---

### Post by Filthy Stockings on 2012-05-09
BELATED THANKS....haven't been able to get online til now.

Still confused as to how I can "ATTACH" the external drive without it being "MOUNTED"....is it not the same procedure ie plug the external into the PC?

Please excuse my ignorance on the matter.

As originally just plugged in BOTH externals and without having to reformat them from WINDOWS to EXT4; have never found any problem with using them.

It is likely that this problem only arose because the USB/POWER UNIT, supplied by WESTERN DIGITAL failed and caused the SAFELY UNMOUNT operation to be thwarted....though that is my technical novice assumption.....perhaps someone else could diagnose the cause otherwise.

Thanks again

---

### Post by Filthy Stockings on 2012-05-10
Managed to get WINDOWS PC to try the

"chkdsk /f"

 solution to the failure of the WD ELEMENTS EXTERNAL HDD. 

A 5 minute process was completed and was able to SAFELY REMOVE the device.

Then connected to UBUNTU OS PC and found the previous ERROR MESSAGE [see first posting] did not occur and seemed like all data still present BUT it is now READ ONLY!!

Cannot delete anything, cannot copy anything to it so now have frozen 1TB EXTERNAL HDD with 115G FREE but apparently now unusable.

CAN ANYONE HELP ME PLEASE?

Thanks in advance.

SA

The ONLY PROCEDURE I DID NOT USE was to "REBOOT TWICE" after the "chkdsk /f" operation as I was not sure if that REBOOTING would be considered a UNSAFE UNMOUNT and cause the same problem to be caused......could THAT have caused the failure for READ/WRITE on the UBUNTU system?

---

### Post by misterblobby on 2012-05-10
You could try pulling the drive out of the case and plugging it into a welland dock. I have has 2 of these drives fail, but taking out the electronics between the drive and the USB cord and using a dock fixed the problem.

---

### Post by Filthy Stockings on 2012-05-10
Thanks for advice but am a tech novice and opening up the units has to be seen as a last resort for me as would surely cancel any 3 year warranty on the products.

Could there not be other options?

As stated, I have found that using a WINDOWS PC to do the "chkdsk /f" seemed to at least allow the EXTERNAL to be connected to my UBUNTU PC and be READ which is ONE POSITIVE since the ERROR MESSAGES received days ago.

Perhaps I need to follow the ERROR REPORT advice re the "REBOOT TWICE"?

Would that allow WRITE on the UBUNTU OS?

---

### Post by Filthy Stockings on 2012-05-14
FINALLY found a cure to restore my WD EXTERNAL HDD to READ/WRITE by  constant searching these forums, so thanks to the more recent poster who  sought out the result in the thread below...he attracted the advice I  never received.

  	 	 	 	 	 	    [COLOR=#000000][SIZE=3][http://ubuntuforums.org/showthread.php?t=1979516](http://ubuntuforums.org/showthread.php?t=1979516)[/SIZE][/COLOR]


and below is his posted link to the SOLUTION which is NOT from these forums...til now
 

  [COLOR=#000000][SIZE=3][http://www.noobslab.com/2011/12/inst...-tool-and.html](http://www.noobslab.com/2011/12/inst...-tool-and.html)[/SIZE][/COLOR]
  

  WESTERN DIGITAL SUPPORT were HOPELESS!

---

