---
title: "CD Player"
date: 2004-12-01
forum: Hardware &amp; Laptops
---

### Post by Infatuated_iPod on 2004-12-01
I love ubuntu but i just have one problem, same problem i had with suse. My speakers wont play the songs on the CD. I have no idea what the problem is, my sound card is intergrated to my motherboard, and all other kind of sound works fine.. it is just the cd rom ... ? Any clues on what the problem could be?

---

### Post by stateq2 on 2004-12-01
you probably need to unmute/raise the cd volume.  you can use a sound mixer like aumix to do it.

---

### Post by bob k on 2004-12-02
[QUOTE=Infatuated_iPod]I love ubuntu but i just have one problem, same problem i had with suse. My speakers wont play the songs on the CD. I have no idea what the problem is, my sound card is intergrated to my motherboard, and all other kind of sound works fine.. it is just the cd rom ... ? Any clues on what the problem could be?[/QUOTE]

I don't know what kind of board you have, but there should be a 3 or 4 wire connector that goes from the cdrom to the cd audio header on your board. The cd audio header is usally discussed in the mb manual and most have a picture of the mb showing where it is at.

If this cable is not connected you will not get analog audio and apps like cd player are using this path for analog audio.

---

### Post by leech on 2004-12-04
I had a similar problem, finally discovered that it was the analog mix (I have an Audigy 2).  I had to turn those up to get any sound, as well as the CD volume.  The other problem I had with gnome-cd (as well as sound-juicer) is that the sg module wasn't loaded.  But that could very well be only a problem if you have a scsi CD-rom (which I do).  Just about every other distro I've used doesn't have that module set by default... why?  If it detects a SCSI card, it should...

Leech

---

