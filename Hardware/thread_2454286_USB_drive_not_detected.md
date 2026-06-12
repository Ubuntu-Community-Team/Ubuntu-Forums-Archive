---
title: "USB drive not detected"
date: 2020-11-26
forum: Hardware
---

### Post by kramerica-industries-k on 2020-11-26
I am brand new to Linux, I tried it briefly once a long time ago and haven't touched in years since.  I have a version of Lubuntu as I'm trying it out on an old laptop that struggles to run Win 7.  I have a Seagate 1TB external hard drive that I am attempting to format but I cannot get either windows or linux operating systems to work properly.  Firstly, the hard drive works, the cable is good and the usb ports work.  The hard drive was hooked up to my satellite receiver and I was using it for pvr purposes and I had no issues with it.  I no longer subscribe to the satellite service so I hooked up the hard drive to a digital converter box that picks up over the air tv stations, again to be used for pvr purposes.  When I first hooked it up, it worked but the converter box was only showing a capacity of about 100MB.  I had my laptop with Lubuntu closest to the hard drive at the time so I reformatted the drive in Lubuntu, I can't remember for sure but I think I choose NTFS format.  I had to google how to do it as Im basically brand new to linux.  All went well, I hooked it up to the converter box and configured it and it recognized the full 1TB capacity.  About a week or two later, I brought the converter box with me up into my attic to adjust my antenna that is in the attic better so I could see what kind of reception I was getting.  When I hooked the converter box back up to the tv in my bedroom it was having the same problem as when I first plugged in the hard drive for the very first time where it only showed about 100MB of capacity.  This time I had windows on the laptop and I was going to try to reformat it again.  I plugged the hard drive into the laptop and it was taking for ever to load the drivers, it must have been going for over 5 minutes so I figured it was frozen and unplugged the hard drive and attempted to start over.  Since then, I cannot get the drive to work properly.  When I hook it up to the converter box, the box freezes until I unplug the hard drive.  When I hook it up to my laptop with lubuntu, the drive doesn't get read at all.  I tried googling the issue and tried many different things I read, but the drive isn't getting recognized at all.  When I hook the drive up to my laptop with Windows, it recognizes the drive but it fails to install the drivers so its as if its not even plugged it.  It doesn't show up in disk management and its in device manager with a yellow exclamation point next to it.  I don't know if it makes more sense to try to format this drive in windows or linux but if anyone has and suggestions I would greatly appreciate it.

---

### Post by CelticWarrior on 2020-11-26
Welcome.

If you want to format as NTFS then it makes a lot more sense to do it in Windows.
That said, I'm afraid you already ruined that drive so it really doesn't matter.

---

### Post by kramerica-industries-k on 2020-11-27
I fear you are correct and that this drive may in fact be ruined.  I attempted taking it out of the enclosure and hooking it up to my desktop via a sata cable but the computer wont boot at all when the drive is plugged in.
What is your best guess as to what I did that ruined it?

---

### Post by tea for one on 2020-11-28
> **kramerica-industries-k said:**
> What is your best guess as to what I did that ruined it?

From your original post [COLOR="#FF0000"]I plugged the hard drive into the laptop and it was taking for ever to load the drivers, it must have been going for over 5 minutes so I figured it was frozen and unplugged the hard drive and attempted to start over[/COLOR]

Assuming that there is no data to retrieve, why not try **gparted** and see if you can create a new partition table and subsequently a partition?

---

### Post by ajgreeny on 2020-11-28
With the external disk attached show us the output of ```
sudo fdisk -l
``` which may give us a bit more information.

---

### Post by DuckHook on 2020-11-28
I suspect your drive is toast, or you should treat it as such anyway.

Given its previous use, this would not be surprising. PVR use is really hard on a HDD. It's on 24/7 and is constantly writing huge data streams and large files. NTFS is especially bad because its horrific fragmentation (mis)management means tons of head movement and mechanical wear. Your description is symptomatic of large sectors of bad substrate.

The following advice is practical, not technical:

It makes no sense to continue using this drive or trying to salvage it. Presumably, your HDD is something that you use to store important data. So even if you get the drive working, it is suspect. In fact, it is so suspect that I would consider it to be completely unreliable. That's simply a bad recipe for important data.

The one component on a machine that you shouldn't take chances with is the HDD. If it were me, I wouldn't waste any more time trying to chase this one down. 1 TB HDDs are absurdly cheap these days&#8212;my local shop sells one for $35. It's unwise to entrust critical data to a demonstrably wonky drive for want of $35.

---

### Post by kramerica-industries-k on 2020-11-28
The thing that is strange to me is that I was able to format it just fine the first time then when I hooked it up to my digital converter box it worked fine.  All I really did was unplug the hard drive for a few hours, then when I plugged it back in, it no longer recognized the full capacity of the drive.  To me, that doesn't make any sense.

Can unplugging a usb device while windows is attempting to install drivers for it really ruin it?

I just tried gparted, it's been "scanning all devices" for the last 10 mins or so. I'll check on it again in a couple of hours and see if anything has changed.

These are the sudo fdisk results:
Disk /dev/sda: 569.17 Gib, 640135028736 bytes, 1250263728 sectors
Disk model: WDC WD6400BPVT-2
Units: sectors 1 * 512=512 bytes
Sector size (logical/physical): 512/4096 bytes
I/O size (minimum/optimal): 4096 bytes/4096 bytes
Disklabel type: dos
Disk identifier: 0X1FB8C47C

Device          Boot Start     End                Sectors              Size           Id     Type
/dev/sda1     *       2048    1250258624    1250256577      596.2G      83    Linux

That is my internal hard drive, it doesn't recognize the external drive at all.

As my intention is to use this drive solely for pvr purposes, I'm not super concerned if the drive fails and I lose my data.  I have already spent more time on this than I would have liked so I'm nearing the end of my willingness to try to troubleshoot, but I'm willing to try a few more things before giving up.  Would FAT32 be a better option than NTFS? It needs to be one of those for the digital converter box.

---

### Post by kramerica-industries-k on 2020-11-30
Gparted is still scanning, going on 24 hours now, so I think it's safe to say that it's not going to recognize the hard drive

---

### Post by tea for one on 2020-11-30
> **kramerica-industries-k said:**
> Gparted is still scanning, going on 24 hours now, so I think it's safe to say that it's not going to recognize the hard drive

Yes, that seems to be a fair assumption.

As a last resort, see what happens with any of the options in gnome-disks [https://wiki.gnome.org/Apps/Disks](https://wiki.gnome.org/Apps/Disks)

Probably fruitless, but worth a shot.......

---

### Post by kramerica-industries-k on 2020-12-01
I can't figure out how to install gnome-disks but thank you for the suggestion

---

### Post by CelticWarrior on 2020-12-01
Disks should be installed already.

---

### Post by tea for one on 2020-12-01
> **kramerica-industries-k said:**
> I can't figure out how to install gnome-disks but thank you for the suggestion

I've just noticed that you are using Lubuntu, which may not contain gnome-disks as a default application.

Try to add it via the terminal with:-
```
sudo apt install gnome-disk-utility
```

---

### Post by kramerica-industries-k on 2020-12-01
The drive doesn't show up in Disks either.

I contacted Seagate, they offered to replace the drive for me.  I was expecting them to tell me the drive is garbage so that was a pleasant surprise.  It's nice to know there are still some companies out there that care about customer service

---

### Post by tea for one on 2020-12-01
> **kramerica-industries-k said:**
> I contacted Seagate, they offered to replace the drive for me. 

Well, that's a pleasant surprise. I somehow got the impression that the drive was quite old. 

Do you remember when you purchased it?

---

### Post by kramerica-industries-k on 2020-12-01
It is old. Pretty sure I bought it 10 years ago

---

### Post by kramerica-industries-k on 2020-12-01
So I have two of these identical drives. Each was hooked up to a different satellite receiver for pvr purposes.
I tried the second one earlier today. Windows read it fine, I formatted the drive in ntfs. I then plugged it into my Linux laptop and it read it fine and it appeared to be working. I had either gparted or disks open and it said there were 5 bad sectors on the hard drive. I had the Seagate tools software installed on my windows laptop already so I thought I would scan the drive and attempt to fix the bad sectors. I tried a quick test, and it completed without any errors. There was a "fix all" option that I tried. It said it could take a few hours so I walked away from the laptop. When I went back to see the progress the test had failed. I noticed the drive was no longer being recognized by Windows. It's basically in the same state as the other drive now. When I plug it in, windows fails to install the drivers for it so it appears to be garbage as well. 
Does this appear to be coincidental that they both seem to have failed shortly after they were reformatted? I don't think I did anything wrong so maybe they both just happened to fail at roughly the same time? They were both purchased and setup for pvr use within a month or two of each other

---

