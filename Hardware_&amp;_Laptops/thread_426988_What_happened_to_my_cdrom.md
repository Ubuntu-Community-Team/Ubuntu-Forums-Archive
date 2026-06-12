---
title: "What happened to my cdrom?"
date: 2007-04-29
forum: Hardware &amp; Laptops
---

### Post by llanitedave on 2007-04-29
I upgraded to Feisty, but I really don't know if this issue is related or coincidental.

I have a homebuilt AMD64 with pretty standard components, including a Memorex 16x DVDRW player/burner.  I put it together about 18 months ago, and have had no major issues before.

Tonight I inserted an audio cd into the player -- and nothing happened.  I know the cd works because I had already played it on my Apple ppc iBook running Edgy.

I opened up Amarok, hit "Play Audio CD", and got the message "Could not read AudioCD".

Hmmmm...

I opened up System Settings, and looked at "Disk and Filesystems".  The first line's data was:

Name:  Burner Memorex DVD etc...
Mount Point:  <mount point>    
Type: auto       
Device:  /dev/hda    
Enabled: disabled

So the device is disabled.  I entered Administrator mode and pressed the "Enable" button.  An error dialog popped up that said "The system reported:  mount:  no medium found"

With an error code of 32.

I thought maybe <mount point> wasn't a valid one, so I went into modify and changed it to /media/cdrom0

Still, I got the same error when I tried to enable it.

So, what gives?  How do I enable my cdrom device?

---

### Post by llanitedave on 2007-04-29
Update:  Choosing iso9660 as the type instead of Auto allows me to enable the device when a data disk is in the drive, but not an audio disk.  But it doesn't allow me to eject the disk until I disable it.

Hints?

---

### Post by PRAEst76 on 2007-06-05
I'm not sure you can mount an audiocd per se. i may be wrong. I think this is related to the way amarok is handling audiocds. I'm having the same problem and I'm not finding any solution.
[B]
Update:[/B] Actually I've noticed that audiocd: plays fine if amarok is run as root, so this must be a permissions problem.

Could also be related to the playback engine. I'm using Xine, perhaps xine doesn't use the audiocd:/ device?

**A Further Update:** Actually, it seems Xine doesn't use audiocd:/ If you set the engine to use /dev/cdrom instead it works. Or at least it does here.

---

