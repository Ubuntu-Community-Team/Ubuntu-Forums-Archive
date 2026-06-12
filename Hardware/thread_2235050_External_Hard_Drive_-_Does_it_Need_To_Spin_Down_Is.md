---
title: "External Hard Drive - Does it Need To Spin Down? Is &quot;Safely Remove&quot; Enough?"
date: 2014-07-18
forum: Hardware
---

### Post by johnsmoke on 2014-07-18
So I recently bought a 2 TB WD My Passport drive to use with my Ubuntu (14.04) machine. I plan on formatting to ext4 as well as encrypting with TrueCrypt. Anyway, I plugged it in just to see if Ubuntu would recognize it, and it did... spun right up, mounted etc... Now I went to properly remove the drive by right clicking it in the dashboard, and it unmounts it (drive disappears from launcher on left). However, still hear the drive spinning and there is still power to the drive.... My question is - does the drive need to completely spin down/power off prior to removing it? Or does a "safely remove" suffice? Another big reason that I ask is because once I encrypt the drive and format to ext4, I know that ext4 is a tad more sensitive to dismounting properly, and could cause corruption of data if not ejected/dismounted properly.

---

### Post by grahammechanical on 2014-07-18
Does the OS give you a message that the drive can now be safely removed or something like that?
> Before disconnecting devices, you must unmount them  first.  This is similar to "Safely Remove" in Windows in that the device  won't unmount until data is finished being written to the device, or  until other programs are finished using it.  This applies to all types  of storage devices, including flash drives, flash cards, external hard  drives, ipods and other media players, and even remote storage like  Samba or NFS shares. 

**Failure to unmount before disconnecting the device can result in loss of data and/or a corrupted file system.**  There are no exceptions to this rule.  Be safe - unmount your drives before disconnecting them! 

[https://help.ubuntu.com/community/Mount/USB](https://help.ubuntu.com/community/Mount/USB)

I would guess that unmounting does not switch off power to the device. Just as plugging the device in brings power to the device so unplugging it would remove power. In the mean time the drive's platters will still be spining. Otherwise, powering down would slow down data transfer if the device need to power up before it could be written to.

Regards,

---

### Post by slickymaster on 2014-07-18
You can safely unmount and spin-down an external hard disk from the terminal most easily by using the command-line functionality of **udisks**```
udisks --unmount /dev/sdb# <- '#' being the drive in question
```
Then to safely remove (i.e. spindown- you will hear it click and spin-down), use only sdb, for example:```
udisks --detach /dev/sdb
```
It is of crucial importance here that you use sdb or sdc without a partition number when using the detach option; i.e. sdb1 or sdc1 will not work. The partition must be unmounted first and then the disk itself spun down.

See [https://help.ubuntu.com/community/AutomaticallyMountPartitions](https://help.ubuntu.com/community/AutomaticallyMountPartitions) for reference.

---

### Post by johnsmoke on 2014-07-18
Thanks for the replies. So just clicking "safely remove" isn't sufficient? A spin down is definitely necessary to ensure data is not corrupted? I read that most drives now "auto park" the heads when powering down anyway... I just want to be sure that I properly remove the drive, unmount etc. prior to removing the USB cable and disconnecting from my system.

---

### Post by Mark Phelps on 2014-07-18
I've found that the USB interface makes the difference in that, when I unmount a USB 3 drive, it powers off; but when I unmount a USB 2 drive, it does not.  In the latter case, I turn it off and wait until it stops spinning before I move it.

---

### Post by ajgreeny on 2014-07-19
> **Mark Phelps said:**
> I've found that the USB interface makes the difference in that, when I unmount a USB 3 drive, it powers off; but when I unmount a USB 2 drive, it does not.  In the latter case, I turn it off and wait until it stops spinning before I move it.
Turn off what?

If you have a portable, USB powered disk you have the choice only to turn off the computer OS which is hardly convenient.

---

### Post by Mark Phelps on 2014-07-19
> Turn off what?

The external USB cases that I have with my disks have a power switch on the front.  I am able to turn them off that way.

---

### Post by johnsmoke on 2014-07-19
So should you spin the drive down and power it off before unplugging? My drive is usb powered - when I "safely remove" it looks like it unmounts (disappears from the launcher on the left side) - but the drive is still on and the disk is still spinning.... Is there any way that I can properly power this down prior to unplugging from the machine? I just want to be sure I do this correctly so that my data does not get corrupted.

---

### Post by Dennis N on 2014-07-19
If it is powered from the USB port, I just eject or safely remove the drive and then unplug the USB cable. So far (several years) no data has ever been lost.

There is the **hdparm** utility which has a command option to make a drive spin down to standby. You have to try and see if your drive responds. In the terminal, read **man hdparm** for information.

---

### Post by johnsmoke on 2014-07-21
So what is the general consensus on the USB-powered drives? Is doing a "safely remove" sufficient enough to be able to pull the cord even though the drive is still spinning? I'm willing to do that if it's safe... I just don't want to load up this drive with tons of stuff, then mess it up by not ejecting it properly.

Dennis, thanks for the info on hdparm... I'm a bit confused by it though. Seems like you can set intervals for the spin down... maybe those settings are saved for good for the drive... not sure if a one time immediate spin down is possible... or if needed based on my above comments.

---

### Post by Dennis N on 2014-07-21
> not sure if a one time immediate spin down is possible...
Best way to find out is to try a few commands and see. On mine, the immediate standby doesn't work:

WD 1 TB usb drive, Immediate spin-down:
```
dmn@Roxanne:~$ sudo hdparm -y /dev/sdc
/dev/sdc:
 issuing standby command
 HDIO_DRIVE_CMD(standby) failed: Invalid argument

```

Get information on the drive and what is supported:
```
dmn@Roxanne:~$ sudo hdparm -I /dev/sdc
```

I think the manufacturer expects you to just unplug the drive when you are finished with it after eject. What else can you do? If there was some risk, seems they would warn you.

---

### Post by johnsmoke on 2014-07-21
I hear you. The more I research this, the more I am convinced that a "safely remove" to unmount the drive should be sufficient enough to unplug the drive, so I may not seek further into the whole spindown thing.... The only reason I am kind of freaking out about this is because recently I had a 16 GB USB flash drive, and I clicked "safely remove" but yank the drive out before it unmounted, resulting in the drive being corrupted and losing all of the data on it... but like I said, I yanked it before it unmounted/disappeared from the launcher there on the side, so that was my own mistake on it.

Only reason I am really trying to research this in depth is because I have a 2 TB hard drive I plan on using, so once that's loaded up it would be much worse having THAT drive corrupted rather than just the 16 GB flash (I had the data for that b/u elsewhere and easily reformatted and added all the data back onto the drive.

---

### Post by Mark Phelps on 2014-07-21
One thing you can consider is doing what I did -- purchasing external drive cases that have power switches on them.  My 2.5 inch USB drive cases all have a little power toggle switch on the case.  After I Unmount the drive, I push the switch to the side and the drive powers off.

---

### Post by Dennis N on 2014-07-21
Is your WD 2TB usb powered? The WD 1TB I was using for the little test has an external power adapter, and once you unmount AND disconnect the usb cable, it powers itself off without unplugging the power. Lubuntu 14.04 (which I am using) shows no eject or safely remove option for that drive - only unmount. Flash drives do show an eject option, however.

---

### Post by johnsmoke on 2014-07-21
> **Dennis N said:**
> Is your WD 2TB usb powered? The WD 1TB I was using for the little test has an external power adapter, and once you unmount AND disconnect the usb cable, it powers itself off without unplugging the power. Lubuntu 14.04 (which I am using) shows no eject or safely remove option for that drive - only unmount. Flash drives do show an eject option, however.

The WD 2TB is a small portable drive (My Passport) and it is usb powered. When I originally tested it the day I got it I just did the "Safely Remove" option (I'm using Ubuntu 14.04), then once it disappeared from the launcher, I disconnected the cabled and it powered off. So this is sufficient you believe in my case?

---

### Post by david253 on 2014-07-21
Safely remove is usually enough in windows7, I am new to ubuntu, good to know this is requred extra so I dont break anything!

---

### Post by J_Me on 2014-07-21
Maybe spinning down was useful back in the day like screen savers were for crt monitors, people are just leaving everything on and plugged in now a days.
A couple of things I do for my externally powered drive are, I always wait for the light(on the drive itself) to stop blinking before I unplug the usb cable, even if the desktop says it's safe to remove and I run checksums against important files. Probably being over caution but I had some horror stories.

---

### Post by Dennis N on 2014-07-21
> **johnsmoke said:**
> The WD 2TB is a small portable drive (My Passport) and it is usb powered. When I originally tested it the day I got it I just did the "Safely Remove" option (I'm using Ubuntu 14.04), then once it disappeared from the launcher, I disconnected the cabled and it powered off. So this is sufficient you believe in my case?

Yes I think so. Same with the flash drives. If the device icon disappears (on your launcher, or desktop, if another DE) its safe to unplug the usb cable. Also there is a notification bubble that it is safe to remove the drive on Xubuntu (but not Lubuntu or Ubuntu 12.04). I also have a couple of usb HDs that are usb powered like yours and that is what I do with those. Never lost any data.

And I always check the drive light too!

---

### Post by ajgreeny on 2014-07-21
> **Mark Phelps said:**
> One thing you can consider is doing what I did -- purchasing external drive cases that have power switches on them.  My 2.5 inch USB drive cases all have a little power toggle switch on the case.  After I Unmount the drive, I push the switch to the side and the drive powers off.
I do not see any real difference between doing that and just unplugging the usb cable that is powering a drive; Once it is unmounted the cable becomes nothing more than the power supply so unplug = power-off, surely?

---

### Post by johnsmoke on 2014-07-22
> **Dennis N said:**
> Yes I think so. Same with the flash drives. If the device icon disappears (on your launcher, or desktop, if another DE) its safe to unplug the usb cable. Also there is a notification bubble that it is safe to remove the drive on Xubuntu (but not Lubuntu or Ubuntu 12.04). I also have a couple of usb HDs that are usb powered like yours and that is what I do with those. Never lost any data.

And I always check the drive light too!


Thanks a lot for the information, appreciate it. I just wanted to be sure of everything before loading up tons of data on the thing. And I hear you on the drive light, when I click "safely remove" the light flashes, and in researching this it sounds like with that it's "caching" or "flushing" the buffers or something to unmount it.... so once it's unmounted and flashing of the LED light is complete, I should feel safe in removing the usb cord.

Thanks much for your comments!

---

### Post by johnsmoke on 2014-07-22
> **ajgreeny said:**
> I do not see any real difference between doing that and just unplugging the usb cable that is powering a drive; Once it is unmounted the cable becomes nothing more than the power supply so unplug = power-off, surely?

I agree, it's USB-powered in this case for my drive, so essentially the USB is the power.

---

### Post by Mark Phelps on 2014-07-22
> ...Once it is unmounted the cable becomes nothing more than the power supply so unplug = power-off, surely? 

I don't disagree -- just saying that I've never had a filesystem corruption problem with these external drives and I attribute that to powering off the drive before I move it.  Pulling the USB cord does the same, obviously, you should just not physically move the drive until it spins down.

---

### Post by ajgreeny on 2014-07-23
> **Mark Phelps said:**
> I don't disagree -- just saying that I've never had a filesystem corruption problem with these external drives and I attribute that to powering off the drive before I move it.  Pulling the USB cord does the same, obviously, you should just not physically move the drive until it spins down.
Yes agreed.  I misunderstood your meaning.  Thanks for the clarification; it's useful for those of us with USB powered drives.

---

### Post by johnsmoke on 2014-07-24
FYI - when this drive was formatted with Ext4 it did spin down and go into an idle state after "safely remove."

---

