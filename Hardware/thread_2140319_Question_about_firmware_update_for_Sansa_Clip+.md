---
title: "Question about firmware update for Sansa Clip+"
date: 2013-04-29
forum: Hardware
---

### Post by Buntu Bunny on 2013-04-29
My husband can no longer access the music folder on his Sansa Clip+ mp3 player. The first step seems to be to update the firmware, for which there is indeed a newer version. I found information on the Sansa Firmware Updater [here]("http://forums.sandisk.com/t5/Sansa-Clip-Sansa-Clip/Sansa-Clip-Firmware-Update-01-02-18/td-p/280756"), with directions for Linux. To update the firmware manually, I am to drag the downloaded firmware file to the device's root directory.

My question is, where do I find the root directory? There is nothing labelled as such in the Sansa Clip+ folder when it's plugged into my computer, nor in my file system. The user manual doesn't cover this. Would it have another name, or be located where I'm not thinking to look?

---

### Post by Buntu Bunny on 2013-04-29
OK, found it. There isn't an actual folder named root, it is simply the main directory for the device.

---

### Post by tgalati4 on 2013-04-29
*root* is a generic name for the top-level directory of a file system tree.  Many linux systems also have a directory called /root where some administrative configuration files are kept.  The root directory of a device (for example a cell phone or mp3 player) would be the top-level directory of that device.  Once mounted, they can be found in /media/username/devicename or /media/devicename.  On some systems they are located at /mnt.

---

### Post by Buntu Bunny on 2013-04-29
> **tgalati4 said:**
> ....  Once mounted, they can be found in /media/username/devicename or /media/devicename.  On some systems they are located at /mnt.

Tgalati4, once again, thank you. I did not know this but it is obviously helpful information for the future.

I have to add that, unfortunately, updating the firmware didn't solve the problem. Next on my list will be to further research that.

---

