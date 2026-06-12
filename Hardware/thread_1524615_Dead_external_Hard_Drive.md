---
title: "Dead external Hard Drive"
date: 2010-07-05
forum: Hardware
---

### Post by pranesh on 2010-07-05
Hi,
   I have a 500 GB seagate external hard drive, that is most probably dead. I have tried to use it on multiple computers with both windows and Linux (ubuntu and OpenSUSE). No avail. The company has asked me to send the drive to them and get a replacement for free. Is there any chance of recovering the data in the drive? And any chances of getting the old drive to work?

Regards
Pranesh

---

### Post by Jay Car on 2010-07-05
> **pranesh said:**
> Hi,
   I have a 500 GB seagate external hard drive, that is most probably dead. I have tried to use it on multiple computers with both windows and Linux (ubuntu and OpenSUSE). No avail. The company has asked me to send the drive to them and get a replacement for free. Is there any chance of recovering the data in the drive? And any chances of getting the old drive to work?

Regards
Pranesh

Hi Pranesh,

What happens when you try the ext. drive on those computers?  Is there an error message?  Do they just not see it at all? Does the ext. have an on/off switch?  Do any of the lights show on the ext. when it's plugged in? (several of mine have lights that blink when they are being accessed).  If you can give a bit more information it might help others to help you.

---

### Post by pranesh on 2010-07-06
Hi Jay,
    Sorry for not being more detailed. There is a LED kind of light that glows up. IT still does, but none of the computers recognize the drive. The windows alone recognizes that some kind of USB device is attached, as the drive comes up in "Safely remove hardware". I can still hear a spinning sound from inside. There is no on off switch.

---

### Post by CannibalZerg on 2010-07-06
I periodically have the similar problem with Seagate FreeAgent 320Gb. If your HDD enclosure has a eSATA port, try to connect it with eSATA cable (I recommend to power down the computer before attaching eSATA HDD, because some of eSATA controllers/drivers has a hotplug-related bugs). In my case it helps, and after this procedure HDD becomes available through its USB interface. 
If HDD didn't recognized via eSATA, well, maybe it's really dead. Try to get the drive itself from enclosure (warranty may be void) and connect it to SATA port. If it works fine, try to put it back and connect via USB.

---

### Post by efflandt on 2010-07-06
What partition types are on the drive?

Does **sudo fdisk -l** (small L) show anything for the drive?  I have been able to do that even when an old laptop drive in a USB enclosure could not be mounted by Linux or Windows due to bad sectors.  Although, after I let it sit for a few weeks, I was able to mount it in Linux and copy some files from it.

Another time when laptop a drive had bad sectors it would show up in Windows in USB enclosure, but could not be accessed.  In that case **chkdsk /f** for that drive letter in Windows fixed it enough to be able to boot.  Although, WD diagnostics still showed the bad sectors, so I got a warranty replacement.  I could not clone that drive with clonezilla, which would fail due to the bad sectors.  But the WD version or Acronis (not sector by sector) worked to make an image for the replacement drive.

Seagate also has their free version of Acronis which I used to back up a drive at work before attempting a Windows fix that did not work.  I had to put the drive in a different PC to restore it, but it was completely restored.

I have not had any trouble with WD Passport drives, except one old PC that will not boot Linux from the far end of a 500 GB drive probably due to some BIOS limitation.  Linux from that PC auto mounts it fine, and the drive boots on other PC's.

---

