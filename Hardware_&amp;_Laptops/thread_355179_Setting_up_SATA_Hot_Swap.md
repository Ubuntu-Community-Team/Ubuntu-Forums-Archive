---
title: "Setting up SATA Hot Swap"
date: 2007-02-06
forum: Hardware &amp; Laptops
---

### Post by oxygen on 2007-02-06
Hey guys,

Does any one now I can go about automatically mounting a SATA drive when it's connected?

Additionally, I will have 2 drives, but only ever connect one at a time - so regardless of which drive it is, I want it to mount in the same place.

Thanks in advance!

---

### Post by oxygen on 2007-02-11
No one knows?

After a kernel upgrade to 2.6.20 and a separate SATA RAID card I have UDEV registering the two drives as sda and sdb.

I have add the drives UUID to fstab and given them their own mount points - however they are not mounting when I plug them in.

Does anyone know what step I'm missing? Is this something to do with UDEV or HAL?

Thanks in advance!

---

### Post by pirothezero on 2007-05-28
bump I could use the same information now that feisty came out with the 2.6.20 kernel.

Thanks in advance.

---

### Post by JeffH.other on 2007-06-03
*BUMP*

I have essentially the same question...

[URL="http://ubuntuforums.org/showthread.php?t=440443"]
issues with mounting ATA/IDE disk in modular bay - ubuntu 6.10 Edgy[/URL]
[http://ubuntuforums.org/showthread.php?t=440443](http://ubuntuforums.org/showthread.php?t=440443)

Does the 2.6.17-11-generic kernel support hot swapping/plugging of  disks?  Or is there some new magic in the 2.6.20 kernel as alluded to in this thread?

I noted that i can put my disk in the modular bay, insert it into powered-off computer, power-on & boot, and it is recognized as /dev/sdb, and then I can pmount it to where I want it. But I'd like to be able to stick it into a powered-on system and have it recognized and mounted in the same fashion as a USB-based drive. 

Anyone know how?

thanks,

=JeffH

---

### Post by =JeffH on 2007-06-08
*bump*

Does the 2.6.17-11-generic kernel support hot swapping/plugging of disks? Or is there some new magic in the 2.6.20 kernel as alluded to in this thread?

I noted that i can put my disk in the modular bay, insert it into powered-off computer, power-on & boot, and it is recognized as /dev/sdb, and then I can pmount it to where I want it. But I'd like to be able to stick it into a powered-on system and have it recognized and mounted in the same fashion as a USB-based drive.

Anyone know how?

thanks,

=JeffH

---

### Post by EnglishRob on 2007-06-30
One way I found to get round this with USB drives was to use AutoFS and UDEV.  I had UDEV setup to recognise the manufacturer and model number of the drive and then assign them to device IDs usbhd*.

I think in the UDEV rules I created I got it to run a script, so in theory you could run a script to mount the drive?

I ended up using AutoFS to mount the drive as and when it's needed.

I used [this](http://www.reactivated.net/writing_udev_rules.html) page to work out the UDEV rules for the USB drive.  It tells you in there how to find out the strings to match and how to run scripts/external programs when the device is detected.

I suppose another thing to do is check that hot swapping is supported for your configuration.  There is a list of controllers and drivers that do support hot swapping [url=http://linux-ata.org/driver-status.html]here[/].

Hope this helps.

It would be interesting to see if you can get it working.  I'm looking to implement some sort of hot swapping for backing up to external eSATA hard drives on a server with shed loads of storage.  Some sort of hot swapping like this would be really useful (over the slightly slower USB2 that I'm currently using).

Rob

---

### Post by =JeffH on 2007-07-02
thanks for the hints EnglishRob -- I'll check 'em out, but it'll be a while (lotsa work to get done before off traveling for a while)

wrt usb-mounted drives, they are automagically recognized for me in Edgy (6.10), Linux 2.6.17-11-generic. I just plug 'em into the usb port and poof, i get a dialog asking whether I want to open a konquerer window for them. If I reply "yes", then they're mounted and available. 

HTH,

=JeffH

---

### Post by BitHosts on 2007-08-30
*BUMP*

I am too looking for this info, there doesn't appear to be very much around on the subject either here on Ubuntu forums or from "our friend Google".  I did find this thread but in all honesty I couldn't work out if this means theres a solution or not - it didnt look very promising.

[http://kerneltrap.org/node/5632]("http://kerneltrap.org/node/5632")

Thanks in advance!

---

### Post by bricktop on 2007-11-21
hi guys,

Has anyone come up with any solutions on this topic, I have the same issue?

---

### Post by oxygen on 2007-11-26
Yes I actually got this working using UDEV and autofs.

We have two separate SATA drives. Our backup script basically checks whether the UUID of disc is found - then if so it runs backup to those drives. If you need more info I'll post the config files and scripts.

---

### Post by AnObfuscator on 2007-12-14
> **oxygen said:**
> Yes I actually got this working using UDEV and autofs.

We have two separate SATA drives. Our backup script basically checks whether the UUID of disc is found - then if so it runs backup to those drives. If you need more info I'll post the config files and scripts.

I would really like to see those, if you don't mind. I have the same problem (although I'm running Fedora right now) -- I have an eSATA enclosure and a removable SATA bay, and I've been trying to figure out how to hotplug them for quite a while.

---

### Post by phantom42 on 2008-01-25
I was able to hot-swap my esata drive by using a command-line tool called scsiadd. What I did is I booted the system with the drive plugged in and ran 'scsiadd -p' which prints out info on all the drives. The one i wanted to hotswap was a Hitachi 1TB drive which showed up like this:

 Host: scsi3 Channel: 00 Id: 00 Lun: 00
  Vendor: ATA      Model: Hitachi HDS72101 Rev: GKAO
  Type:   Direct-Access                    ANSI  SCSI revision: 05

I unmounted it and ran 'scsiadd -r 3 0 0 0' (host channel id lun) and shut off the drive. I checked /dev just to make sure, and sure enough /dev/sdb didn't exist anymore. I proceeded to start the drive back up, and I'm pretty sure /dev/sdb was there again but not /dev/sdb1, so I wouldn't be able to mount it. Then I ran 'scsiadd -a 3 0 0 0' followed by 'scsiadd -s' and I was able to mount the drive. Hope this helps.

---

