---
title: "ata*: exception Emask 0x10 Sact Serr 0x406000"
date: 2009-02-24
forum: Hardware
---

### Post by sadohert on 2009-02-24
I have no idea what to.  This sequence of messages is pouring into my logs at a sporadic rate (1 a second to 1 a minute) and I can't seem to find any information that relates to my situation.  I'm not even sure what I can call/invoke to probe things to get more info.

Anyone have any pointers?  To start I'd like to know what "ata8" is?  I have 3 harddrives and a DVD burner... 

Thanks

Feb 24 20:29:33 mule kernel: [ 3143.133175] ata8: exception Emask 0x10 SAct 0x0 SErr 0x4060000 action 0x2 frozen
Feb 24 20:29:33 mule kernel: [ 3143.133180] ata8: (irq_stat 0x00000040, connection status changed)
Feb 24 20:29:34 mule kernel: [ 3143.847411] ata8: soft resetting port
Feb 24 20:29:34 mule kernel: [ 3143.847423] ata8: SATA link down (SStatus 0 SControl 300)
Feb 24 20:29:34 mule kernel: [ 3143.847432] ata8: EH complete

---

### Post by sadohert on 2009-02-24
I just found this thread:

[http://ubuntuforums.org/showthread.php?t=616274](http://ubuntuforums.org/showthread.php?t=616274)

And it sounds like those users were having almost the exact same issue.  I followed the instruction to turn off the JMicron motherboard feature, and the stream of messages has disappeared.  I haven't done anything different to my system since Sunday (when I see the messages started to appear in my logwatch output).  I don't even remember any updates over the last few days.  The only system change I've made was to do some downloading, and building from source, of the Barry Project (for Blackberry sync).

The JMicron chip does IDE/PATA stuff.  I don't use any IDE devices, thankfully, but this coudl be annoying if I needed to throw one in.

Stu

---

### Post by sadohert on 2009-02-24
And this bug report seems to have more people commenting on the issues.

[https://bugs.launchpad.net/ubuntu/+source/linux/+bug/198871/](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/198871/)

---

