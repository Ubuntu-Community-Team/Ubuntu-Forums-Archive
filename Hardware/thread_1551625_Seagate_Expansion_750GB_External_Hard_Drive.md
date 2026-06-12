---
title: "Seagate Expansion 750GB External Hard Drive"
date: 2010-08-12
forum: Hardware
---

### Post by MugenDraco on 2010-08-12
I just bought a Seagate Expansion 750GB external hard drive.  The reviews claimed you just plug it in via USB, and it recognizes it as just a storage drive where you can drag and drop files.  Simple as that.  I got it, and not only does Linux not recognize it, Windows doesn't either.  When I use sudo -fdisk -l it doesn't even come up.

Disk /dev/sda: 320.1 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xd0f4738c

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1       12158    97659103+   7  HPFS/NTFS
/dev/sda2   *       12159       12766     4883760   83  Linux
/dev/sda3           12767       38913   210025777+  83  Linux

As you can see, it only shows my Home, Root, and Windows partitions on my internal hard drive.  I've also tried all the ntfs-3g advice I can find, and it still won't recognize it.  Does anyone have any more advice that might help?  I'm running Ubuntu 9.10 Karmic Koala on a Dell Inspiron 1520.

---

### Post by dabl on 2010-08-12
I'd start my investigation in the BIOS.  Is it the latest version?  With the external disk plugged in, boot the computer, press whatever needs pressed to access BIOS, and take a look at the "boot device sequence" item -- do you see that disk there?

If neither Windows nor Linux sees it when it's connected, that indicates that the computer itself (the BIOS and USB controller) aren't seeing it either.  Do other USB storage devices (USB stick, external CD ROM, or whatever) work on that computer?

---

### Post by MugenDraco on 2010-08-12
I saw USB storage device listed, but it's listed under boot sequence no matter if there's one present or not.  And yes, all other USB devices I've ever plugged into my laptop have worked.  This is a first.  If the BIOS is not current, how would I know, and how would I go about updating it?

---

### Post by ajgreeny on 2010-08-12
Can you get a friend to try the disk on another computer, as it sounds as if it could be a faulty disk, particularly as your computer finds all other usb devices.

I think the BIOS update palaver is probably a bit of a red herring, and I would not rush into doing anything about that at the moment.

---

### Post by MugenDraco on 2010-08-12
OMG I don't know how this happened, but I was in Windows, and I thought maybe the USB cord might be faulty.  So I found another one and plugged it in.  It recognized it!  Thought for sure it was the cord, but just to make sure, I plugged it in once again with the cord it came with.  It worked!  It's working in Linux right now too.  Dunno.  Maybe the cord wasn't all the way in the first time, so it just registered a charge but no mounting took place.  Who knows?  Weird.

---

### Post by Bruce S on 2010-11-15
Hope this is helpful to you.

I intend getting an external drive, and from my reading about it, maybe you need to mount it before it will be recognised.

---

