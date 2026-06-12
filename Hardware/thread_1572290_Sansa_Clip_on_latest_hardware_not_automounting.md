---
title: "Sansa Clip on latest hardware not automounting"
date: 2010-09-10
forum: Hardware
---

### Post by asterix404 on 2010-09-10
So I was messed with something that was working because I wanted to upgrade my Sansa Clip's firmware. I did it successfully on windows. I now have it working with rhythmbox but the weird thing is that it won't mount now just by plugging it in like it did before. lsusb displays the device correctly. 

sudo mtpfs -o allow_other mtp

works fine but then it will hang when I try to cd mtp and or give me the error: "mtp: Transport endpoint is not connected". 

This was working perfectly before I updated the firmware. Any ideas what I can do?

---

### Post by asterix404 on 2010-09-10
Ahh, it turns out that the USB mode is not MTP after the firmware update and ubuntu was confused. Anyway, once it is set to MTP on the player itself it worked even better than before. Well... hopefully this will help someone else out.

---

### Post by billstei on 2011-02-24
Thanks for this post.  Just bought a Sansa Clip+ 2GB and the USB mode in the player was set to Auto out of the box, and Ubuntu Maverick was not recognizing/mounting it.  Set this to MTP in the player and now it is working, although in Nuatilus it does not have the Eject / Safely Remove Drive options.  Tried setting player to MSC and now I have Eject and Safely Remove Drive available in Nautilus.

---

### Post by Chronon on 2011-02-24
I always use MSC because then I can use my audio player as a storage device for other files, not just files a jukebox app agrees to send to it.  It's also virtually guaranteed to work with any system that has USB ports since pretty much any USB host has drivers for UMS devices.

---

### Post by billstei on 2011-02-27
After playing some music I discovered that there are 6 demo songs on the player that were put there by Sansa.  The player shows that there is a folder called MTP somewhere, but using MSC and Nautilus I cannot locate the folder (and it is not a .hidden folder).  Switching the USB mode to MTP allowed me to see the songs in RhythmBox (but not Nautilus) and after backing them up, I deleted them, and then right-clicked the device as listed in RhythmBox and selected Eject.  The player said "Writing" and then both RhythmBox and the Clip+ completely froze.  I did a Force-Quit on RhythmBox, and then I had to hold down the power button on the Clip+ for 15 seconds (see User's Manual) and the player shutdown.  The songs were gone as expected, but after putting the player back to MSC mode, I was surprised to find that the approximate 25 MB of memory the songs were using (theoretically) was not added/recovered.  I unmounted the drive and did an fsck on it using Disk Utility (in Gnome, System->Administration->Disk Utility)  and it checked OK (it uses the FAT file system).

Update: I found the missing memory... There were over 30 FSCKxxxx files located at the root of the drive, which I assume fsck put there even though it said that things were "OK".  I deleted them and gained 22 Meg.

---

