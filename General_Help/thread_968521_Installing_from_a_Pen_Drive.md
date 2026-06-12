---
title: "Installing from a Pen Drive"
date: 2008-11-02
forum: General Help
---

### Post by Slrman on 2008-11-02
I have down loaded Ubuntu onto my desktop system but I want to install it on my laptop.  Can I extract the winrar file to a flash drive and load it from a USB port on my laptop?  That seems like pretty much the same thing as burning a CD and faster and easier, I think.

Thanks for any help.  :)

---

### Post by mdurham on 2008-11-02
The short answer is, no. How did you get it in a rar file anyway?. It's usually in .iso form.

---

### Post by Axis on 2008-11-02
Are you certain of that? As of 8.10 Ubuntu offers a feature to make a USB Startup Disk, if you have Ubuntu already this may be an option.
To get to this feature go to System -> Administration -> Make a USB Startup Disk

Solutions exist to this problem if you are already on windows. However one of the only things I could suggest would be to maybe install Ubuntu using Wubi (When you place the CD into your Windows PC, select the third option "Install Ubuntu Inside of Windows"), and then once inside of ubuntu you could create the live CD for you USB device with Ubuntu.

Another (longer) solution should you not have a CD, would be to mount the .iso file with Daemon Tools, or a similar program. Then select the third option again and continue from there.

Hope it helped, asked questions if anything was unclear.

---

### Post by Slingshot on 2008-11-02
Try this [http://ochsenhirt.org/2008/05/23/install-ubuntu-804-lts-from-usb-howto/]("http://ochsenhirt.org/2008/05/23/install-ubuntu-804-lts-from-usb-howto/"). Might give you some useful info on how.

---

### Post by C.S.Cameron on 2008-11-02
You can load the iso to USB flash drive using either unibootin, (work from windows also), or usb-creator, located on the 8.10 Live CD.
This flash disk will install Ubuntu to other computers just like the Live CD.

---

### Post by Slrman on 2008-11-03
I downloaded Ubuntu from a server in Germany and it came through as a WINRAR file.  I extracted the WINRAR to a folder I named Ubuntu (clever, yes?) And it looks like the attachment shown.

I haven't seen a thing about an ISO file.  Do I need to download this again?  If so from where?

Thanks for all the replies.

---

### Post by Axis on 2008-11-03
The WINRAR file you recieved, was most likely the .iso file. WINRAR is capable of opening .iso files.

---

### Post by Slrman on 2008-11-03
Yes, there is a folder named isolinux in the extracted files.  I don't know how I missed seeing it before.  

I see I should have added the following information.  The laptop already has Win XP installed, but something has gone south with XP  (when did that ever happen?) and it will only start in safe mode.  Someone supposedly more knowledgeable than I am said the only solution was to re-install XP, thereby formatting the disk.  As far as data goes, that isn't a problem as everything is backed up very well.  I would lose many applications, though and some o those were downloaded and have no back-ups. 

I have been thinking about going to Ubuntu anyway, so this seems like a good time to try.  So my thought is to install it from the USB pen drive and give it a go.  

I think what I may do, if no one has any direct suggestions, is to fire it up, try it and see what happens.  The worst that can be is I end up doing the XP re-install and wiping the drive.  So what do I have to lose but some time?  :confused:

---

