---
title: "What's the best format to format an external drive to?"
date: 2009-08-11
forum: Hardware
---

### Post by tomreid on 2009-08-11
Hi

I just bought a 1TB external drive, it is unformatted.

I use Ubuntu 9.04 as my main OS, but still occasionally use Mac. 

Partition Manager seems to have an option to format the drive to EXT2, but my Mac won't read the data from an EXT 2 formatted drive. 

I thought of formatting it to NTFS which I think both Mac and Linux can read, but I don't see that option. 

FAT 32 I thought was only suitable for small drives.

Does anyone have any suggestions?

cheers

---

### Post by Bartender on 2009-08-11
Yeah.
Go to GPartedLiveCD website, download the latest stable version, burn it to a CD as an .iso.  Boot from the resulting CD with the external drive plugged in and spinning.  After you click thru the beginning part and get the partition map, look up in the right hand corner to see which drives it recognizes.  GPLCD gives you the option of formatting as NTFS.  That's what I did with a Seagate 1TB drive in a Vantec NextStar dock using GPLCD.  I wanted to format it in ext3 or 4, but I connect the dock to a couple of Windows PC's.  Since Windows doesn't want to cooperate with Linux file systems but the Linux PC's can deal with NTFS, NTFS made the most sense.
I don't know what the best option is for a Mac, but if you want NTFS use GPLCD.  It's the handiest single tool I've discovered since venturing into the Linux world.

---

### Post by tomreid on 2009-08-14
Thanks, that worked!

---

