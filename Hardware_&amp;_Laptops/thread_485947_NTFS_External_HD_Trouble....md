---
title: "NTFS External HD Trouble..."
date: 2007-06-27
forum: Hardware &amp; Laptops
---

### Post by Haxish420 on 2007-06-27
Ok, so here is the synopsis:

I was running a dual boot with Feisty and Xp SP 2.

I wanted to try Ubuntu Studio and didn't want to upset anything on the laptop's internal hd, so I used the Studio installer to re-size my External Usb HD (formated with ntfs) and installed Ubuntu studio into the empty space I had created.  I couldn't get it to boot, so I deleted my windows partition and installed it on the internal hd.

For a while, I could still access the ntfs partition on the usb drive fine, then I had to force it because it wouldn't mount, and then it stopped letting me mount the ntfs partition at all so I tried using ntfsfix 1.13.1 to check the disk and it said everything went fine, but I still couldn't mount it.

I decided to switch back to dual booting windows to try and fix the hd and because I had no real use for Ubuntu studio and decided to dual boot vista.  I used gparted to delete the Ubuntu studio partitions on both the internal and external hd's, as well as the swap partitions that each install had created.

Everything went fine reinstalling vista and reinstalling grub via the live cd to overwrite vista's mbr, but the external hd doesn't work at all in vista.  If it is on and plugged in when I boot into vista, it will just hang and not load, and if I plug it in and turn it on after booting, vista gets extremely sluggish and absolutely nothing will work.

I need to save the info on the ntfs partition at all costs, so simply reformatting is not an option for me.  Any help would be greatly appreciated.  Thanks.

---

### Post by Tsen on 2007-06-27
Mine did something similar in XP, unfortunately, it was physically damaged and I could only recover some of the data.
For now, just try checking it with Window's chkdsk command.  Since it's causing the computer to hang, I left the external drive off until after the computer had booted.  Then open up a command prompt in Windows (Run->CMD in XP, I'd assume Vista is similar).  The syntax for the command requires that you know the drive letter though.  Due to a flaw in the way Windows handles these things, the drive letter won't show in explorer (at least not in my case), but the computer HAS assigned it a drive letter.  I can't help you much here--mine was F:, but you'll have to figure that out.  It should be the next unassigned letter after your other drives...
Anyway, after that, the command should be:
```
chkdsk F: /r /x
```
Replace F: with your drive's letter.  /r tells it to recover readable information from damaged sectors, and /x tells it to unmount the drive if necessary, then checks for errors on the disk.
Hope it helps, having an external drive go down can be hell.

---

### Post by Haxish420 on 2007-06-27
The thing is that if the HD is on in windows, I can't do anything in windows.  As soon as I turn on the HD, vista recognizes it and then the whole computer slows down to the point that nothing works at all.  I can't safely remove the hard drive, I can't open my computer, I can't even shut down the computer at all.

In Ubuntu It at least shows up but if I try to mount it I get an error about the drive being not shutdown properly and to run ntfsfix, so I did, and then I get the error that the drive needs to be booted into windows twice or forced using the force command, but then the force command doesn't work.

---

### Post by Tsen on 2007-06-28
Dang.  That's what happened with my external, but at least when I turned it on *after* booting up Windows, it wouldn't slow down the system unless I tried to view the Device Manager.  
If you can boot in recovery mode with command prompt, do so and try running chkdsk.  Unfortunately, the disk is probably damaged, and you may have lost some, if not all, of your data.  
Check to see if the manufacturers have a data recovery option.  Some allow you to send them the disk and they'll salvage whatever they can from it for you.

---

