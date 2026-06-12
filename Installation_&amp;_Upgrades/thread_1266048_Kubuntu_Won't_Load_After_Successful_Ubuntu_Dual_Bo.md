---
title: "Kubuntu Won't Load After Successful Ubuntu Dual Boot"
date: 2009-09-14
forum: Installation &amp; Upgrades
---

### Post by rhardie on 2009-09-14
I have made numerous attempts to load Kubuntu 9.04 64 bit onto my system with no success.  I had Ubuntu 9.04 loaded in dual boot environment when I decided I wanted totally Linux machine.

System:

AMD Athlon 64 single core
3GB RAM
HDD1 120GB IDE Primary
HDD2 200GB IDE Secondary
HDD3 300GB SATA External

Had dual boot successful with Windows on HDD1 and Ubuntu 9.04 on HDD2.

Preference would be Linux only on HDD3 and not dual boot.

Procedure followed:

Download ISO
Checksum verified
Burned as bootable and verified
Sucessful live CD load on another Ubuntu system at work
Re-load Windows XP on HHD1
Re-format HDD2 and HDD3 from Windows
Attempt install reults up until fail as follows:
English language - OK
Time Zone - OK
Keyboard Configuration - OK
System scans disk - OK
Detecting file sys (120GB, 200GB, 300GB found) - OK
Who Are You? - entered name & pw - OK
Ready to Install - OK
Detect file System - OK (chose 300GB HDD3)
Format Part#1 SCSI1 (0,0,0), sda
    CD drive spins up and reads files
    Screen goes blank after about 15 seconds of loading
    "X" as a cursor is on screen - mouse moves cursor
    No CD read activity indicated, spins down
    No hard drive activity detected for over 1 minute

Previous attempts that also ended in failure to load were:

1. Remove all but 120GB HHD1 and attempt to load
2. Remove all but 200GB HHD2 and attempt to load
3. Remove all but 300GB HDD3 and attempt to load (SATA)
4. Attempted to load Kubuntu on another similarly configured system at home that had Windows loaded and screen died

Any ideas or help would be appreciated.

rhardie

---

### Post by Partyboi2 on 2009-09-14
Have you tried installing in safe graphics mode? At the main menu of the live cd press F4.
If that does not work you could always try installing using the alternate cd which is a text base installer

---

### Post by rhardie on 2009-09-14
Answer to reply above (Thank you, by the way):  No, I will attempt the safe mode.

Now:  Since my first post, above, I attempted to load as a live CD.

Result:

CD reads, then stops with no hard drive activity
Screen locked up with the Kubuntu boot screen (blue scanning left to right)

Reboot system

Now can not load Kubuntu onto system

Result:

Load from CD
Install Ubuntu page
CD spins up and reads
CD spins down, video screen dark
Reboot to Windows XP

rhardie

---

### Post by Partyboi2 on 2009-09-14
At the main menu of the live cd press F6 and remove the word "splash' from the line and press enter. Hopefully this might provide further infomation.

---

### Post by rhardie on 2009-09-14
I began to think that the RAM was a common denominator.  Ran Memtest 86.

Results:

Fail Test 2 (address area 000abfd63a0
Fail Test 3 (address areas 000abe56b70...000abfd6360)
Still running test 4 with no failures

I'll re-seat the RAM sticks and re-run memtewst 86 (note added later: reseated RAM but continue to get memory test failures in same address range.  Will swap memory card locations or replace memory)

Posted from my GF's Dell Mini 10 with Ubuntu 8.04

rhardie

---

### Post by rhardie on 2009-09-14
SUCCESS!

I pulled the memory stick from DIMM3 slot, re-ran the failing memory tests without failures.

Attempted live CD install with successful load.  :)
Full install progressing well.

My guess is that Ubuntu goes to the highest addresses of the RAM to load files and uses the lower addresses for installation and operation, therefore, all of memory must be operational for a successful install.  Microsoft loaded OK so it must have different requirements of memory.  Again, my guess as I am not a software or hardware expert.

LESSON LEARNED:

Utilize diagnostic capabilities on Ubuntu more quickly when having installation issues.  Memory is good one moment, bad the next.

The diagnostic will help identify the bad memollry module based upon the failing addresses.

rhardie

How do I mark this as "solved"?

---

### Post by Partyboi2 on 2009-09-14
Good to see you got it all sorted. :)
To mark a thread solved click on 'Thread Tools' at the top right of the thread and choose "mark this thread solved".

---

