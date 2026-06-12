---
title: "windows boot issue...07 07 07 07"
date: 2008-09-07
forum: General Help
---

### Post by badboy165 on 2008-09-07
Right...

Ive got a major issue at the moment and I need urgent help...I installed BT3 on my usb stick and tried to upgrade the kernel version (because of the intel 4965 issues) so...everything was going fine until I edited the lilo.conf...I think I set the /dev/..to the wrong drive (my HDD)...I rebooted the laptop and now I cant boot into vista (installed on the HDD) or BT3 (on the usb)...When I let the laptop boot it just comes up with "07 07 07 07 07 07....." 

I tried restoring the startup with the vista install cd but that didnt do anything...The absolute final thing I want to do is format the HDD...Can somebody please help me fix this problem...Help is much appreciated

I have a dell with 3 partitions I think (1st is the vista main partion, 2nd is just a small back up and I think the 3rd is dell utils that I cant see in vista but I can in BT3)

SOLVED: I installed a fresh copy of vista on the backup partition and that sorted out the boot problem...I then uninstalled the new vista installation...Now I need to figure out how to boot straight into windows because I get a dual boot screen which allows me to boot into two versions on vista but I only have one...any ideas?

---

### Post by Solvingyournoobishproblem on 2008-10-20
To anyone reading this... the solution the above poster used was definitely the WRONG one. There is a much easier fix for a damaged master boot record (MBR).

Put in your Vista Recovery/Installation CD. Let it load, and choose your language. Choose the "repair" option.

Click to open a console.

type bootrec.exe

View the available options. For now, type this:

bootrec.exe /FixMbr

Restart, and enjoy your repaired MBR.

---

