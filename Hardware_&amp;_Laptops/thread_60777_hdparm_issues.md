---
title: "hdparm issues"
date: 2005-08-29
forum: Hardware &amp; Laptops
---

### Post by oliwood on 2005-08-29
Hey gang,
Whilest trying to ijmprove the speed of read of my cdrom drive, I appear to have managed to break it in a new and interesting way.  When I put in an audio cd, it spins up, finds the track listing using cddb, but then refuses to play!

sudo hdparm /dev/hdc gives:
/dev/hdc:
 IO_support   =  0 (default 16-bit)
 unmaskirq    =  0 (off)
 using_dma    =  0 (off)
 keepsettings =  0 (off)
 readonly     =  0 (off)
 readahead    = 256 (on)
 HDIO_GETGEO failed: Invalid argument


dmesg has the following at it's tail:
end_request: I/O error, dev hdc, sector 737520
hdc: command error: status=0x51 { DriveReady SeekComplete Error }
hdc: command error: error=0x51
ide: failed opcode was 100


Anybody got any clue what I've managed to do?  the command I was used (off the top of my head - its not in my history) was

hdparm -d /dev/hdc

Many thanks,
Oli(idiot)

---

### Post by essexman on 2005-08-29
[QUOTE=oliwood]Hey gang,



dmesg has the following at it's tail:
end_request: I/O error, dev hdc, sector 737520
hdc: command error: status=0x51 { DriveReady SeekComplete Error }
hdc: command error: error=0x51
ide: failed opcode was 100


Anybody got any clue what I've managed to do?  the command I was used (off the top of my head - its not in my history) was

hdparm -d /dev/hdc

Many thanks,
Oli(idiot)[/QUOTE]
You can try ```
hdparm -d1 /dev/hdc
``` as this toggles the command command for dma.

But I'm not sure if this would stop the track from playing.  This may not be a hdparm issue.

Can you run```
 sudo hdparm -tT /dev/hdc
``` and post the read out?

---

### Post by oliwood on 2005-08-29
stranger and stranger. I got the following:

/dev/hdc:
read() failed: Input/output error
 Timing buffered disk reads:  read() failed: Input/output error


That kindsa smells to me like the cd drive isn't connected - but its built in to the lappy.  Ill have a quick ccheck of connections are post again.

thanks for the help thus far,

oli

---

### Post by oliwood on 2005-08-29
[QUOTE=oliwood]stranger and stranger. I got the following:

/dev/hdc:
read() failed: Input/output error
 Timing buffered disk reads:  read() failed: Input/output error


That kindsa smells to me like the cd drive isn't connected - but its built in to the lappy.  Ill have a quick ccheck of connections are post again.

thanks for the help thus far,

oli[/QUOTE]
 Update: looks like it was my drive in the process of dieing.  Its not not even opening up when i press the eject button on the outside.

Oh well - i trip to PC World then :(

---

