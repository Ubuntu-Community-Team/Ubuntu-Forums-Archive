---
title: "LiveCD Failure"
date: 2005-11-05
forum: General Help
---

### Post by Mizutsuki on 2005-11-05
I think this is an issue related to my motherboard, so I'll just start by telling you it's an Asus P5WD2 and I've got a P4 640 on there with 2x512 Corsair ValueRAM.
Anyway, when I try to boot from the liveCD on this particular machine (I'm using BB 64-bit livecd, not the DVD, and I'm unwilling to test by installing) it says it can't install the CD drivers, so I should install them using a floppy.  Now that's a little strange, I tried both of the drives, one is a plain old DVD-ROM drive, and the other is a DVD_+RW drive, both are normal internal IDE drives.  I think it may be related to the IDE chipset, but I don't really know enough to say that.
I'm not using any SATA drives.
Also, I tried using other liveCDs including KANOTIX, DSL, and KNOPPIX and they all came up with the same error:

Can't find KNOPPIX filesystem, sorry.
Dropping you to a (very limited) shell.
Press reset button to quit.

Any idea if all that's related?  Any other thoughts or help?  I just want to check linux out on this machine... any help would be appreciated.
Thank you.

---

### Post by Mizutsuki on 2005-11-06
Ok, I think I've discovered the source of my chagrin.  It turns out that both programs I've been using to burn the CDs have been truncating the filenames to 64 characters.  Now I just have to figure out a way around the limitation.
Who the hell decided on names longer than 64 characters? ~_~

---

### Post by nightfly on 2005-11-06
> It turns out that both programs I've been using to burn the CDs have been truncating the filenames to 64 characters.

This is not likely true. If you were burning the CDs from a .iso file, then the CD block are burned block for block and filenames should not get changed by anyhow.

You may want to verify the integrity of the disc after burning.
Mount the CDROM disc. Open a Terminal window and type
```
sudo md5sum -c /media/cdrom/md5sum.txt
```

---

### Post by Mizutsuki on 2005-11-06
[QUOTE=nightfly]This is not likely true. If you were burning the CDs from a .iso file, then the CD block are burned block for block and filenames should not get changed by anyhow.

You may want to verify the integrity of the disc after burning.
Mount the CDROM disc. Open a Terminal window and type
```
sudo md5sum -c /media/cdrom/md5sum.txt
```[/QUOTE]

Turns out you're right, it wasn't that at all.  I'm using windows (so I couldn't use your tip) and somehow windows can't *read* filenames over 64 characters in length, so when I checked it out on my laptop (that uses Ubuntu) it showed full filenames and told me that that was not the issue.
It turns out I was right, it was my controller.  My motherboard (P5WD2) apparently has 3 controllers, one for SATA, one for for UDMA 133 (with support for 2x2 HDDs) and one for DMA 100 (with support for 2 drives) and I had my DVD drives hooked up to the UDMA controller, which didn't work to well for whatever reason.  When I switched them both over to the DMA controller it worked it all loaded up fine (though I had a seperate slew of issues upon reaching the desktop that I highly doubt are at all related.)
I just wanted to make sure I got this down so if anyone else is having similar difficulty they might google this up.
[Hmm, let see, google search terms: P5WD2, Linux, KNOPPIX, KANOTIX, Ubuntu, LiveCD, IDE, controller... I don't even know if google will read these :D ]

---

### Post by nightfly on 2005-11-07
I am glad you have figured it out.

By the way, Linux should have detected the DVD drive even when it was connected through a UDMA controller as in your case. This is probably a bug in the kernel that will hopefully be resolved.

---

