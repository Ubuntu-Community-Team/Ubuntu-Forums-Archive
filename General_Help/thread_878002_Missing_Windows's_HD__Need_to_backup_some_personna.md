---
title: "Missing Windows's HD ? Need to backup some personnal XP files before reformatting"
date: 2008-08-02
forum: General Help
---

### Post by Browser_ice on 2008-08-02
I am having a problem with my current Dual boot.  Since yesterday, my Windows XP reboots itself after 1-5 min once logged on. I did a system restore prior to an update I had 2 weeks ago that was causing it to reboot (back then). But that didn't work. I tried to do a Windows Repair but it fails with a Blue Screen of death with the reason : Stop:0x0000007f

If I boot in my Ubuntu all the non Linux HD are not there on my desktop anymore.  I am beginning to suspect a HD problem.

What I want from the community to help me is 2 things :

1) how to gain back XP's HDs access through my Ubuntu so I can at least take a backup of MyDocuments folder.

2) Can I through Ubuntu do somekind of HD check/repair on all those XP HD ? I have no rescue Floppys. I have a Maxtor diagnostic tool but it is on a non booting CD.


Today or Wednesday at the most, I am planning on changing my whole configuration to have Ubuntu my main O/S and Windows to be have the minimal  install for the stuffs I can't run under Ubuntu.  But I DO need to take a backup of some XP Partitions for personnal files.

---

### Post by prshah on 2008-08-02
> **Browser_ice said:**
> 
1) how to gain back XP's HDs access through my Ubuntu so I can at least take a backup of MyDocuments folder.

2) Can I through Ubuntu do somekind of HD check/repair on all those XP HD ? I have no rescue Floppys. I have a Maxtor diagnostic tool but it is on a non booting CD

You have to approach this in reverse; I think you are right in suspecting a HDD problem. 

You should _first_ try to boot into "Safe mode with command prompt" and use chkdsk to check the HDD. _Before_ the windows splash screen comes up (immediately _after_ the bios screen display), keep tapping F8 to get a boot menu. In that, select "Safe Mode with Command Prompt". When the welcome screen appears, login as Administrator, and run ```
chkdsk c: /f
``` When it's done, shutdown cleanly and return to ubuntu to gain access to your ntfs partitions.

If the safe mode is a no-go/non-starter:
Unluckily, ubuntu's own fsck (fsck.ntfs) is not yet available; but you can use the following command to check your ntfs partition```
sudo ntfsresize -fib /dev/sda1
``` Though it says resize, it will not perform anything of that sort. Replace /dev/sda1 with the actual device of your ntfs partition.

If you don't have ntfsresize, you may need to install the ntfsprogs package```
sudo apt-get install ntfsprogs
```

Note that this is highly experimental. I suggest that you instead boot off a Windows CD (beg, borrow, or st---), switch to recovery console, and run chkdsk.```
chkdsk /f
```

As for mounting your NTFS partitions, linux will not automatically mount them if it detects an unclean shutdown. If you cannot perform a chkdsk, there are a couple of options available to you:

a) ```
sudo ntfsfix /dev/sda1
``` will tell windows to run a check on the drive on the next boot. Give this command, let windows attempt to run the check, then shutdown immediately, and boot back into ubuntu.

If for any reason this does not work, you can use the "force" parameter with the mount command to force-mount unclean drives. This carries a risk warning, but I've never yet screwed up any data using this option; YMMV.
```
sudo ntfs-3g /dev/sda1 /mnt -o force,ro
``` after this command, your ntfs partition will be accessible at "/mnt" directory, readonly, to prevent any (further) damage.

All of this is potentially hazardous to your data. I would like to make an additional suggestion; try to get a Windows Live CD. Search Google for BartPE.

---

### Post by Browser_ice on 2008-08-02
I will try those.

Before suspecting an HD problem, I thought it was a virus so I booted into safe mode and started a command line anti-virus scan but I don't think it went through because after 15 min, I went to get a cofee and I heard it reboot.

I also tried to do a Windows Repair with the Windows XP CD but I got a blue screen with a "Stop: 0x0000007f ...." message.

I' come back in 15 min or so with the results. Thx

---

### Post by Browser_ice on 2008-08-02
Hummm, that went a bit too fast.

I originally booted into safe mode with command line and did a chkdsk c: /f but when I rebooted it went right into windows (after selecting it from the Dualboot menu). So I did not even see any Checkdisk nor Scandisk windows.

So I logged on to my usual XP id. I took a chance and copied my "My Documents" to another drive. It went through without rebooting. I was relieved. But then I did a properties on my C drive and selected a full Scandisk with repair. I rebooted and when going back into Windows I saw the Checkdisk screen but it said right away it did not find any problems and printed a dozen '.' for progress but the whole checkdisk session lasted less then 5 seconds then it went into windows.

I did checkdisk before and they always lasted longer then that. So what gives ?

Anyway, I manged in Ubuntu to go pick my backed up "My Documents" (all XP drives were now accessible) and copied it into my Ubuntu's desktop.

So I should be fine now to re-install everything. I just have to make DVD backups from Ubuntu and go ahead.

I just do not understand what happen vs Checkdisk reporting nothing !!!!

---

### Post by Browser_ice on 2008-08-02
Hummm, 10 min ago I was able to log on to my Windows XP  without problem but now as I rebooted (did a shutdown but then remembered to do something in it) it went into the same problem I am having for the past 2 days:it reboots for no reasons without any warning nor messages once I am in my Windows ID and within 2-5 min.  I do not have that problem when I am in my Ubuntu (Dual boot) and that Ubuntu is on a 2nd partition of the same HD.

I am beginning to wonder if it is a permanent HD problem now.

---

### Post by prshah on 2008-08-02
> **Browser_ice said:**
> 
I just do not understand what happen vs Checkdisk reporting nothing !!!!

If you boot back into Windows, you can study the event viewer to see what (if anything) chkdsk has done. Click on Start-Run, give the command ```
eventvwr.msc
``` then check in the "Applications" (or is it in "System") section for an entry from "Winlogon". There will be multiple entries at about the time chkdsk was finished; look through them all to find out what chkdsk has done. You can post back the results here if you like.

> **Browser_ice said:**
> it reboots for no reasons without any warning nor messages once I am in my Windows ID and within 2-5 min.

Maybe your CPU is overheating? Thermal? No, that _should_ affect Ubuntu as well... OK, we can rule out HDD physical damage as below:

Open a terminal (Applications-Accessories-Terminal), then give the below commands ```
sudo umount /dev/sda1
sudo badblocks -v /dev/sda1

``` This will run a (read-only) physical test on your c: drive. Depending on the size of your drive, it will run a fair while.

---

