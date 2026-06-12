---
title: "DVD Burning Problem"
date: 2005-03-22
forum: Hardware &amp; Laptops
---

### Post by silent82 on 2005-03-22
While I was burning a dvd I got this:
```

3765207040/4681428992 (80.4%) @0.0x, remaining 4:43
3765207040/4681428992 (80.4%) @0.0x, remaining 4:43
3765207040/4681428992 (80.4%) @0.0x, remaining 4:44
:-? the LUN appears to be stuck writing LBA=1c0d90h, retry in 141ms
3765207040/4681428992 (80.4%) @0.0x, remaining 4:45
3765207040/4681428992 (80.4%) @0.0x, remaining 4:46
:-[ WRITE@LBA=1c0d90h failed with SK=3h/ASC=0Ch/ACQ=00h]: Input/output error
builtin_dd: 1838480*2KB out @ average 2.3x1385KBps
:-( write failed: Input/output error
/dev/hdc: flushing cache
/dev/hdc: updating RMA
/dev/hdc: closing disc
/dev/hdc: reloading tray

```

dmesg gave me:
```

cdrom: This disc doesn't have any tracks I recognize!
cdrom: This disc doesn't have any tracks I recognize!
spurious 8259A interrupt: IRQ7.
cdrom: This disc doesn't have any tracks I recognize!
cdrom: This disc doesn't have any tracks I recognize!
hdc: packet command error: status=0x51 { DriveReady SeekComplete Error }
hdc: packet command error: error=0x40 { LastFailedSense=0x04 }
ide: failed opcode was: unknown
ATAPI device hdc:
  Deferred Error: Hardware error -- (Sense key=0x04)
  Internal CD/DVD logical unit failure -- (asc=0x44, ascq=0x00)
  The failed "Read Cd/Dvd Capacity" packet command was:
  "25 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 "

```

the command was:
```

growisofs -dvd-compat -Z /dev/hdc=file.iso

```

Can anyone help me? I burned 4 dvds... with no luck :-(

---

### Post by adun on 2005-03-22
Was your iso bigger than 4 GB?

---

### Post by silent82 on 2005-03-22
-rwxrwxrwx   1 silent82 silent82 4681428992 2005-03-22 00:01 file.iso

---

### Post by silent82 on 2005-03-22
I'm using kernel 2.6.11

---

### Post by ArcticChicken on 2005-05-14
Humor me.

Enter this command...

ps aux | grep k[s]cd

...and post if turns up anything.

---

### Post by ArcticChicken on 2005-05-14
Darn.  Wrong discussion.  I *am* a newb.

---

### Post by osde.info on 2005-07-12
>> -rwxrwxrwx 1 silent82 silent82 4681428992 2005-03-22 00:01 file.iso

DVD's labelled 4.7 Gigabytes (4,700,000,000) only actually hold 4.37 Gibibytes (4617089843) ! your iso of 4681428992 may be too close to 4692251770

See also

[http://www.dvddemystified.com/dvdfaq.html#3.3](http://www.dvddemystified.com/dvdfaq.html#3.3)
[http://www.brainyencyclopedia.com/encyclopedia/g/gi/gibibyte.html](http://www.brainyencyclopedia.com/encyclopedia/g/gi/gibibyte.html)

---

