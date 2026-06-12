---
title: "Problem burning with new Pioneer DVR-115D"
date: 2008-02-01
forum: Hardware &amp; Laptops
---

### Post by Rizlaw on 2008-02-01
I am running Ubuntu 7.10. I had been using both a Pioneer DVR-110D and 111D on my system with no trouble. I always got perfectly burned CDs and DVDs with both burners. After my Asus A8N-SLI Deluxe motherboard literally flamed out ( a few capacitors went up in flames and smoke) I decided to upgrade my burner to a new Pioneer DVR-115D (IDE type). Asus repaired my motherboard and when I got it back, I reinstalled Ubuntu 7.10 along with the new 115D burner which had version 1.06 Pioneer firmware. I had a whole bunch of reading and writing problems with this drive and returned it to NewEgg for a replacement. While waiting for the replacement drive, I learned that Pioneer had issued a firmware update [1.18].

I use removable drives to boot the various Linux and Windows OSs I have. I don't dual boot, each removable drive has only one bootable OS.

When I received the replacement drive, I immediately flashed it, under Windows XP, to the new Pioneer 1.18 firmware. I burned an ISO of Kubuntu using Nero 7 under WinXP. The burn went fine and the Kubuntu LiveCD booted without problems.

I then installed my main Ubuntu 7.10 hard disc and booted into Linux. The new drive is detected OK (/dev/hda) and I can read from it, but I can't write to it. The new firmware seems to have fixed the reading problems I had with the first 115D in Linux. However, I've created several coasters (CDs and DVDs) using Verbatim DVD-R media and TDK CD media. All of the media used have given me perfect burns with the 110D and 111D burners, so I know it's not a batch of bad media.

I'm at a loss to explain why this drive works OK in Windows and not in Linux. I've also tried Gnomebaker, and it, too, gives me the same write errors.

The cost of the drive, $30, doesn't make it worth spending another $10 to return it to NewEgg a second time. Also, I can't honestly say the drive is defective since it works under WinXP.

Does anyone have any ideas what could be going on in Ubuntu to cause this drive not to write properly?

---

### Post by spookie_dookie on 2008-02-19
similar problem with pioneer 111D drive. Makes great coasters, but i dont need a burner for that.....

BTW, DMA is enabled, banshee, nero and nautilus all fail but nero gets the closest (when it gets to 90%, it looks like the buffer just dissapears then it spits it out)

---

### Post by spookie_dookie on 2008-03-10
hey mate i think i cracked it, go to my thread and look at the website i posted, it downgrades the drive firmware to a linux acceptable version. i downgraded my 111D from 1.29 to 1.19 and its working much better.

[Forum Thread]("http://ubuntuforums.org/showthread.php?p=4488328#post4488328")

---

### Post by spookie_dookie on 2008-03-10
oh btw, look at the source website link for your 115 its the last link in the posts

---

### Post by SuprNoodles on 2008-03-15
I believe I'm having the same problem as you. I have a brand new Pioneer 115D. Everything works fine on Windows, though on Ubuntu, files on DVD-R's appear 'corrupted' and I can't burn them either. Watching DVD's is also impossible.

How can it be that all of this works fine on Windows, though not on Linux?

---

