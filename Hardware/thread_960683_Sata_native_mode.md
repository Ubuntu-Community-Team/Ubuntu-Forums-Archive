---
title: "Sata native mode"
date: 2008-10-27
forum: Hardware
---

### Post by francisc1701 on 2008-10-27
Hello, everyone!

Because I didn't want to integrate the Sata drivers into my windows installation cd I disabled "Sata native mode" from my bios before I installed windows and I left it that way until today. In the meantime I installed Kubuntu. Today, out of curiosity (will Kubuntu boot? windows doesn't) I enabled "Sata native mode" in the bios. Kubuntu did boot without any problems, but I get this message on every boot: ```
[   31.502491] ata1: exception Emask 0x10 SAct 0x0 SErr 0x0 action 0x9 t4
[   31.502494] ata1: irq_stat 0x00400040, connection status changed
``` Is that something I should be worried about? What's causing this?

Another thing about "Sata native mode": I read somewhere that it needs to be enabled in order to take full advantage of the drive's speed. However, I did not notice any improvement since I enabled that option. Before, resuming from hibernation went at about 26 MB/s. After, it still goes at about 26 MB/s. Is that simply the top speed of my hard drive? ```
# hdparm -tT /dev/sda
``` says ```
/dev/sda:
 Timing cached reads:   2124 MB in  2.00 seconds = 1062.37 MB/sec
 Timing buffered disk reads:  158 MB in  3.00 seconds =  52.63 MB/sec
feri@acasa-laptop:~$ sudo hdparm -tT /dev/sda

/dev/sda:
 Timing cached reads:   2076 MB in  2.00 seconds = 1038.07 MB/sec
 Timing buffered disk reads:  162 MB in  3.02 seconds =  53.69 MB/sec
feri@acasa-laptop:~$ sudo hdparm -tT /dev/sda

/dev/sda:
 Timing cached reads:   2084 MB in  2.00 seconds = 1042.77 MB/sec
 Timing buffered disk reads:  162 MB in  3.02 seconds =  53.69 MB/sec
feri@acasa-laptop:~$ sudo hdparm -tT /dev/sda

/dev/sda:
 Timing cached reads:   2046 MB in  2.00 seconds = 1023.93 MB/sec
 Timing buffered disk reads:  164 MB in  3.00 seconds =  54.60 MB/sec

```
If hdparm can read that fast why can't resume? (I mean the buffered reads)

Thanks for taking the time to read my little rant.

---

