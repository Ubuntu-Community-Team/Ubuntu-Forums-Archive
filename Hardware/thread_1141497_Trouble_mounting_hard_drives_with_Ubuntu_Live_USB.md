---
title: "Trouble mounting hard drives with Ubuntu Live USB"
date: 2009-04-28
forum: Hardware
---

### Post by dpblank on 2009-04-28
I have a netbook running XP with a corrupt boot. I've given up trying to repair the system, I just want to recover the files before I reinstall XP completely. 

I used my Jaunty 9.04 desktop machine to create a USB boot stick of an Intrepid 8.10 .iso, which I boot on the netbook live. 

The objective is to transfer about 6GB of files from netbook's internal HDD (FAT32) to an external HD (Mac OS Journaled). 

The problems that I am running into are: 

1) The netbook's internal HDD will mount **only** on the first boot with the live USB stick. If I reboot the netbook with the live USB system, its internal HDD will no longer mount. I get the error *dev/sdb0/ is already mounted*.
 
2) The external HD will mount, but is read only. (It read-writes on my 9.04 desktop, however; or at least I can't remember ever  altering the permissions.) 

I assume it is problems with either the formatting or permissions, but I can't save fstab or mtab on the live USB boot. 

Any suggestions/thoughts?

---

### Post by shatterblast on 2009-04-28
SDB0 refers to a USB hard drive I believe while SDA whatever should point to an internal hard drive.

To edit fstab or mtab, you will need to begin the line probably with "sudo gedit".  For instance:

sudo gedit /etc/fstab

The password might be "admin" on the live CD.  I think you have to edit something occasionally to get a USB drive to reboot in some cases.  I think this holds true especially if you expose it to a Windows environment.  Otherwise, I can only say to recreate the live image on the USB bootable for the sake of simplicity.

Please skip this particular section of advice if you aren't familiar with editing your BIOS.  Until you can properly copy your data from your Netbook, I would suggest disabling your hard drive from being bootable inside the BIOS.  This can be accomplished by pressing F2, Delete or whatever right as the system activates.  On some systems, you can hear a beep from a speaker or the stutter of the screen restarting as this occurs. If you ask yourself something like "What is this?" or "What does that mean?", please disregard.

Keep the external USB hard drive disconnected until you can boot into your Netbook correctly.  Once you see a mouse cursor show up and you are logged in while able to see desktop icons, plug in the external USB hard drive and wait about 5 seconds or a little longer.  You should see some message display about the external hard drive.  In this fashion, you can tell if the external hard drive will be properly recognized or not.  The whole point is to search for an error message and determine the next step of direction.

---

### Post by dpblank on 2009-04-28
It very well could have been dev/sda instead of sdb0, I was writing from memory. But now that I think about it, I never used gedit to write to fstab or mtab...I just navigated to the file itself in the filesystem for some reason. 

I'm not near my machines at the moment, but supposing this were the case and I can properly edit/save fstab, what line(s) would I have to add to get the USB live disk system to be able to write to the external (Mac OS Journaled) disk? 

Thanks for the advice :)

---

### Post by shatterblast on 2009-04-28
You shouldn't have to I think.  I'm not sure if the format of your hard drive is recognized properly by Ubuntu, though I believe software can be added that allows it to do so.  If true, going that path would lead to experimental software.  Similar to EXT4, it wasn't absolutely stable.

If you just boot Ubuntu and then plug in the USB drive after logging in, it should still recognize the hardware itself just fine.  It may provide an error message on whether the Mac Journalized FS will be compatible for what you want.  In a worst case scenario, there may arise the need to reformat your USB drive with some other kind of file system.  I'm not sure if EXT3 is recognized properly by Mac OS X and 10.5 though.  FAT32 might work, but I prefer to avoid it altogether.  Just be aware that reformatting will cause loss of all data.

I might be making this seem complex.  All you should have to do is go to:

Places -> Computer

Assuming all drives and their formats are compatible, just simply copy and paste from one drive to another.  In the event of a permissions issue, you could try to custom make your own Live CD with Remastersys.

---

### Post by dpblank on 2009-04-28
I was able to disable journaling on my external HD and transfer the files successfully.

If anyone reading this has a similar problem, you may use this terminal command to disable journaling on your Mas OS formatted HD:

diskutil disableJournal /Volumes/TheVolumeName

You can always re-enable journaling in OSX's DiskUtility.

---

