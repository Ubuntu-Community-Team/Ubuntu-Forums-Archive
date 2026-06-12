---
title: "Computer failed entirely. HDD problem? Trying to rec. with LiveCd/ubuntu"
date: 2008-11-30
forum: General Help
---

### Post by kidwithshirt on 2008-11-30
Alright sorry if I posted in the wrong spot, thanks for reading

-

I have a dell XPS m1530 laptop, with 8600mGT

I use vista mostly (sorry), recently I tried to upgrade my graphics driver. I probably didn't properly uninstall the previous drivers, but I tried several drivers including a custom (dox) one. I was pretty tired but I just wanted to get them to work.

Anyway after the 2nd driver or so the temp of my graphics driver became unbearably hot (85C on idle!). I didnt mind so I watched a movie and went to sleep. 

After I tried to reboot it in the morning, it was pretty slow so I terminated the process in the boot screen (where a small status bar rolls across the long bar). I called up dell techies and they gave me this series of tests. The first one failed during some part, where the computer just shut off and I didnt notice where it was. After I booted on the next time into the diagnostic thing, then a HDD failure showed and I gave the error code to the dell guy and he arranged a fix.

I am glad they are fixing it, but I needed my data! I used livecd and booted into it and tried to copy the files onto my USB drive. It showed all my NTFS drives correctly, I had to use "mount .... -o force" to get it to work. I was able to access the disk, but it always hangs so I wasnt able to get the file at all. It copied about 100mb of a file then just hung, i had to shut it off.

I then used the LiveCd to delete the nv* driver files in system32, did all that, didnt help. Couldnt boot into windows safe mode.

I tried my ubuntu partition. It couldnt finish booting and gave me this:

```
[ 24.658587] sda:<4>Driver 'sr' needs updating - please use bus_type methods
[ 24.666883] ata1.00: exception Emask 0x0 SAct 0x0 SErr 0x0 action 0x2
[ 24.666887] ata1.00: BMDMA stat 0x24
[ 24.666893] ata1.00: cmd c8/00:08:00:00:00/00:00:00:00:00/e0 tag 0 dma 4096 in
[ 24.666894] res 51/84:00:07:00:00/00:00:00:00:00/e0 Emask 0x10 (ATA bus error)
[ 24.666897] ata1.00: status: { DRDY ERR }
[ 24.666900] ata1.00: error: { ICRC ABRT }
[ 24.666923] ata1: soft resetting link
[ 24.847974] ata1.00: configured for UDMA/100
[ 24.847982] ata1: EH complete
[ 24.849775] ata1.00: exception Emask 0x0 SAct 0x0 SErr 0x0 action 0x2
[ 24.849778] ata1.00: BMDMA stat 0x24
[ 24.849783] ata1.00: cmd c8/00:08:00:00:00/00:00:00:00:00/e0 tag 0 dma 4096 in
[ 24.849785] res 51/84:00:07:00:00/00:00:00:00:00/e0 Emask 0x10 (ATA bus error)
[ 24.849788] ata1.00: status: { DRDY ERR }
```

This was pretty similar to what I got. I found this on the net and i couldnt get mine out of the computer since I couldnt even access anything. 

I checked out some posts and fixing partition table might help? I am not too understanding of computers, but I can try it if I get some directions.

All I am trying to is get my music/doc/vids out. Any ideas? Sorry that was a mouthful. I would gladly appreciate it because I believe my HDD is still functional since I can get to it in LiveCD. I just think the dell diagnostic broke it or something =\

I would be deeply obliged to you if you can help me out since I treasure my 200GB of files and programs :)

---

### Post by /////// on 2008-11-30
Try getting the harddrive out of the computer and mounting it in another computer where it is not the primary drive. Then boot in with Ubuntu and try to copy the files again

---

### Post by ajcham on 2008-11-30
> **/////// said:**
> Try getting the harddrive out of the computer and mounting it in another computer where it is not the primary drive. Then boot in with Ubuntu and try to copy the files again

Might not be as simple as that with a laptop.

Kidwithshirt, could you try copying the files again, but do it from a command line to see if it gives any errors that might shed light on the problem.

[SIZE="3"]**[FONT="Courier New"]cp -r ~/music/doc/vids *PATH_TO_USB_DRIVE*[/FONT]**[/SIZE]

---

### Post by lotacus on 2008-11-30
sounds like baaad sectors. Did you drop your laptop? muahaha. I dropped my laptop being silly once and had heck of a time using windows. I ended up returning the laptop to the manufacture to get a new HD, but of course, I didn't tell them I had dropped it. :)

I would boot from a windows installation cd, run recovery console and do a chkdsk /? command and then find the switch to correct errors and then run that command

ie: chkdsk /s (note the s is just an example not the actual switch)

It may take days for it to complete though I left mine for a day and it still hasn't completed, that's when I just returned the laptop. But essentially what that will do is scan for physical errors, and try to recover data and move them to a location on the drive that isnt' damaged, then you should be able to move yoru files out if your lucky.

---

