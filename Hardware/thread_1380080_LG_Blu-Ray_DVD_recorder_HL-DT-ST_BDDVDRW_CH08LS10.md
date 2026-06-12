---
title: "LG Blu-Ray DVD recorder HL-DT-ST BDDVDRW CH08LS10"
date: 2010-01-13
forum: Hardware
---

### Post by bhobw on 2010-01-13
Bought the above model LG. Trying to record CD or DVD and I'm getting fails.

From reading another thread, just about the only app supporting recording is Nero Linux. I've got v4 of this and tried to record with same error - see below:

I've tried launching the app as root - same error. I'm now out of ideas.

K3B didnt work either.

Drive reads discs fine - although I havent even started messing with the Blu-Ray side of it yet! More pain to come no doubt. For the time being I'd just like the writer working.

Im running 9.10.

BHOBW

11:59:06        #26 Text 0 File Cdrdrv.cpp, Line 1273
        11:59:06 - HL-DT-ST BDDVDRW CH08LS10 (H:2 T:0) : Queue again later

11:59:20        #27 SCSI -1064 File SCSIInterface.cpp, Line 624
        SCSI Exec, HA 2, TA 0, LUN 0, buffer 0x0xb6a1c480
        Status:     0x04 (0x01, SCSI_ERR)
        HA-Status   0x00 (0x00, OK)
        TA-Status   0x05 (0x0B, SCSI_TASTATUS_FAILED)
        Sense Key:  0x05 (KEY_ILLEGAL_REQUEST)
        Sense Code: 0x21
        Sense Qual: 0x00
        CDB Data:   0x2A 0x00 0xFF 0xFF 0xFF 0x6A 0x00 0x00 0x20 0x00 0x00 0x00
        Sense Data: 0x70 0x00 0x05 0x00 0x00 0x00 0x00 0x0A
                    0x2A 0x20 0x03 0x80 0x21 0x00

11:59:20        #28 CDR -1064 File Writer.cpp, Line 306
        Invalid block address
        HL-DT-ST BDDVDRW CH08LS10 (H:2 T:0)

11:59:20        #29 Text 0 File DVDPlusDualLayer.cpp, Line 1455
        SetDriveCaps: Set LAST LBA of layer 1 to 0

11:59:20        #30 Phase 34 File ExtendedProgress.cpp, Line 537

---

### Post by bhobw on 2010-01-13
:confused:

Anyone?

---

### Post by Cathhsmom on 2010-01-13
I am a newbie when it comes to Ubuntu, but I can tell you what I have found while getting familiar with Boxee.  I read on the forum for Boxee that Blue Ray does not work in Linux.  That might be your failure.

---

### Post by bhobw on 2010-01-13
Thanks Cathhsmom

Not really what I wanted to hear though..... :-)


Anyone else?

BHOBW

---

### Post by bhobw on 2010-02-05
I was using karmic initially.

I wiped the system and downgraded to 9.04. It worked! I could write successfully.

I upgraded the system to karmic again .... and it stopped working!! Grrrrrrrrr.


Looks like this is a karmic problem somehow. I'm now about to wipe again and go back to 9.04.

BHOBW

---

### Post by markbuntu on 2010-02-05
Be sure to file a bug report at launchpad so the devs know there is a problem.

---

### Post by anothergene on 2010-07-18
> **bhobw said:**
> I was using karmic initially.

I wiped the system and downgraded to 9.04. It worked! I could write successfully.

I upgraded the system to karmic again .... and it stopped working!! Grrrrrrrrr.


Looks like this is a karmic problem somehow. I'm now about to wipe again and go back to 9.04.

BHOBW

I concure, I am having the same issue with 9.10 and the same drive.  I'm not in a position to be able to downgrade to 9.04 though.  I'm going to try and find some time to try it with a newer kernel.  If a bug has not been filed I am willing to give it a go.  I noticed the LG has a newer version of firmware available too.  2.0 as opposed to the 1.0 that I have on mine.  unfortunately they only have the updater for windows.  I'll see if I can some how get it hooked up to or booted of of a win disk.

---

