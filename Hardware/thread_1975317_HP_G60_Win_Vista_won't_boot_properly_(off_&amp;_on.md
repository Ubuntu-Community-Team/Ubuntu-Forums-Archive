---
title: "HP G60 Win Vista won't boot properly (off &amp; on)"
date: 2012-05-07
forum: Hardware
---

### Post by RememberWhenItRained on 2012-05-07
Hello friends:

 Here's the situation: I currently have a friend's laptop (HP G60 with 32 bit Windows Vista) that I am trying to diagnose/troubleshoot. As mentioned in this thread ([http://ubuntuforums.org/showthread.php?t=1961591](http://ubuntuforums.org/showthread.php?t=1961591) ; same machine) it had some hard drive errors (bad sectors and temp. control) that I found running several scans (badblocks, GSmartMon, fsck, etc.) After cloning as image with Clonezilla & then wiping the disc (zeroed with DBAN), I restored the image to the original internal drive and ran all the tests again which came back clean. As mentioned in the linked thread, there was a continuous BIOS beep while Windows freezes on a black screen with white text reading "Windows is loading files" with loading bar. The beep persists and the loading makes no progress.

The "newly" wiped machine worked for her for about a week, and then occurred again. I have run the aforementioned testes again and the disk comes back clean. Which makes me wonder. I had thought the BIOS beep was a hard drive error; but upon looking it up ([http://www.computerhope.com/beep.htm](http://www.computerhope.com/beep.htm)) perhaps it's loose RAM? Though I have run both Memory (RAM) and HDD tests which came back clean. A google query of "hp vista stuck at windows is loading files beeps" yielded a site which suggested to reseat the drive. Since it passed all aforementioned tests, wouldn't it have to be connected properly though?

 My next instinct was that it was possibly a boot-sector virus. Downloaded avast! for linux 32 bit on a live USB and ran. Found 10-something viruses (with Java in the file path name, which I thought odd.) I deleted those and set a restore point. (Oh, also, windows restore/recovery which should supposedly "automatically fix boot errors" usually fails to work.) I also reimaged the drive and am currently wiping the internal HDD. (Which, now that i think about it, is dumb; I originally thought that perhaps the viruses infected other areas, so wiping the disc might help, even after deleted the files avast! detected. But imaging a disc would still transfer the current state of the system (including possible viruses) when you reloaded it, wouldn't it?)

I'm not really sure how to proceed. Viewing the system Diagnostics Logs (pressed Esc to access boot menu then chose diagnostics.) showed an error code of 0603. Not sure if this is Windows' or HP's code. From what little i could find on it, some suggested it might be HDD related. But again, HDD passed all tests. (I'm supposed to be an IT/Information Systems major in college; this seems somewhat pathetic. Oh well, i guess IT guys do plenty of Google-ing as well.)

The warranty is long expired so i could open it up and try reseating the HDD and RAM if that would help. However, sometimes it does seem to boot fine (occasionally.) So i'm not sure if i could see if that actually solved the problem. For instance, last time I gave it back to her, it worked for a week before acting up again.

I have Ubuntu and Ultimate Boot CD (with PartedMagic) on live USBs, but am unable to pinpoint the specific problem(s) yet. 

Suggestions?

Thanks in advance and sorry for the length. You all are a wonderful community.

---

### Post by RememberWhenItRained on 2012-05-07
reseated the HDD. can't quite get the RAM out yet.

---

### Post by RememberWhenItRained on 2012-05-08
reseated RAM and HDD. now getting error winload.exe is missing or corrupt. No install or recovery disc yet to speak of. Trying restoring image again though i'm doubtful it'll help. I'm thinking it was a boot sector virus (?)

I almost forgot why i hated Windows sometimes...

---

### Post by RememberWhenItRained on 2012-05-08
restored image from external to local HDD. Got it to boot properly. Now running Secunia & Avira. Still not sure what HP error code 0603 was, or what the problem was and if it is fixed..

---

