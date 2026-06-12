---
title: "Sansa View"
date: 2007-12-26
forum: Hardware &amp; Laptops
---

### Post by Super TWiT on 2007-12-26
_[CENTER]Getting the Sansa View to Work in Ubuntu[/CENTER]_

This is a tutorial about how to get the Sansa View to work in Ubuntu.  I haven't tried this in any other Ubuntu versions except Gutsy, but this should still work.

Step 1: Turn your Sansa on and switch it to hold by pushing the switch on the side up.

Step 2: While in hold mode, hold down the left part of the directional pad.  Do this, until the ring lights up.  (Note that this is dependent upon the firmware.  On the latest firmware the ring is already light up and will stay light up, so don't worry if this happens.)  Then connect it to your computer.

Step 3: Boot into dare I say it windows (note you should also be able to do this step using Gparted, however I haven't tried that, so if anyone has done this using Gparted let me know.)

Step 4: Your Sansa should show up as a usb device.  I found out how to get it into usb mode by reading: [http://forums.sandisk.com/sansa/board/message?board.id=view&message.id=1617]("http://forums.sandisk.com/sansa/board/message?board.id=view&message.id=1617").  I figured out that Ubuntu doesn't like the volume label, so go to my computer and click format.  Make sure in the format options to remove the disk label.  **Formatting will destroy all data on the drive, so make sure there isn't anything you want on it!**

Step 5: Once this is completed, the Sansa should be able to mount in Ubuntu.  However, every time you want to mount it you have to repeat step 1 and step 2.  This puts the Sansa into usb mass storage mode, and there is no way that I know of to put it in mass storage mode by default.  This way Ubuntu will recognize it.  Please again let me know if this is possible to do in Gparted as I want to take windows out of this tutorial if possible.  Please if there are any problems with this tutorial let me know.  Hope this tutorial helps you out.

---

### Post by K.Mandla on 2007-12-26
Moved to Hardware and Laptops.

---

