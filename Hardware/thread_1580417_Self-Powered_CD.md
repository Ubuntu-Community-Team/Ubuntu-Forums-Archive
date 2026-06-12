---
title: "Self-Powered CD"
date: 2010-09-23
forum: Hardware
---

### Post by John Peschken on 2010-09-23
I'm having a small problem with little USB powered CD Drive and my ASUS eeePC 704HA.  
 
I put a disk in the drive, there is some activity, but ultimately the drive does not mount.  
 
This drive did work on the same machine running Windows XP. so apparently Ubuntu is having trouble mounting this thing for some reason.  This same drive, plugged into my Dell Latitude D600 running XP complains that the USB port does not have enough power to runt hte thing, so apparently it's something of a power hog.  Any ideas about what I might do to get this to work?

---

### Post by IcarusR on 2010-09-23
You can try a usb 'y' cable like the one here...

[http://www.bixnet.com/5vps2powercord.html]("http://www.bixnet.com/5vps2powercord.html")

Or if possible with an external power supply.

As far as I'm aware there is no way to increase usb power.

---

### Post by John Peschken on 2010-09-23
It seems to me like the cableyou suggest might help the Dell Windows machine, since that's the one complaining it does not have enough power to run the drive. However, since that machine only has two closely stacked USB ports I suspect that they might share the same power.  If that is the case, it does not seem like using a "Y" cable to tap the power of both USB ports would help.  
 
The ASUS/Ubuntu machine is the one I am most concerned with, though.  The same drive works perfectly with Windows XP as the OS on that machine.  So, it seems logical that it must be an Ubuntu problem rather than a power shortage.

---

### Post by IcarusR on 2010-09-23
Do any cds work in the drive ??
My cd/dvd drive does not like some makes of media. When it does not like media the drive 'thrashes'.

Is there anything about the drive in the logs ?

Unplug, wait 10 secs re-plug in & in a terminal type 
> dmesg

---

### Post by John Peschken on 2010-09-23
I did discover that data CD's work. It is only music CD's that fail.  I'm talking about factory made audio CD's.  A disk of MP3 and OGG files will mount normally.  The Ubuntu live CD mounts normally. 

Here is what I _think_ is the relevant part of the log file.  It is pretty long.  Hope I got the right part.

[ 1956.011431] sr0: scsi3-mmc drive: 24x/24x cd/rw xa/form2 cdda tray
[ 1956.012776] sr 4:0:0:0: Attached scsi CD-ROM sr0
[ 1956.016329] sr 4:0:0:0: Attached scsi generic sg2 type 5
[ 1956.402637] sr 4:0:0:0: [sr0] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE
[ 1956.402650] sr 4:0:0:0: [sr0] Sense Key : Illegal Request [current] 
[ 1956.402660] Info fld=0x0, ILI
[ 1956.402665] sr 4:0:0:0: [sr0] Add. Sense: Illegal mode for this track
[ 1956.402676] sr 4:0:0:0: [sr0] CDB: Read(10): 28 00 00 00 00 00 00 00 02 00
[ 1956.402695] end_request: I/O error, dev sr0, sector 0
[ 1956.402704] __ratelimit: 8 callbacks suppressed
[ 1956.402710] Buffer I/O error on device sr0, logical block 0
[ 1956.705502] sr 4:0:0:0: [sr0] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE
[ 1956.705524] sr 4:0:0:0: [sr0] Sense Key : Illegal Request [current] 
[ 1956.705545] Info fld=0x0, ILI
[ 1956.705553] sr 4:0:0:0: [sr0] Add. Sense: Illegal mode for this track
[ 1956.705575] sr 4:0:0:0: [sr0] CDB: Read(10): 28 00 00 00 00 00 00 00 02 00
[ 1956.705611] end_request: I/O error, dev sr0, sector 0
[ 1956.705627] Buffer I/O error on device sr0, logical block 0

It is repetitive after this with only the leading number in the brackets [   ]  changing.

Clearly, it's reporting an error, yet WinXP on this same computer is perfectly happy with it.

---

