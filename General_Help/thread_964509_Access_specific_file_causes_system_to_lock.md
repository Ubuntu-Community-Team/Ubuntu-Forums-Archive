---
title: "Access specific file causes system to lock"
date: 2008-10-31
forum: General Help
---

### Post by unc0nn3ct3d on 2008-10-31
So I am trying to convert a .wav to a .mp3 with Audacity and SoundKonverter and no matter the program the entire system freezes when whatever program gets to a specific point with importing the file..  
 At first I thought it might have soemthing to do with the progs as I have had pretty **** luck with Audacity this week but then when I tried to move the file to another hard drive the entire sytem freezes indefinitely when I get to 170.1mb out of 342.5 .  Same place everytime system just locks and I have to do a cold boot.

The drive is a 750GB SATA2 drive formated as NTFS.  I was having problems with it booting at all today until I turned ACPI off in my bios and now it loads fine.  Although strange enough when I put 'acpi=off' in GRUB after turning ACPI off in bios my mouse and keyboard don't work.

So what I want to know is if there is a way for me to find out what is going on/causing the entire system to lock and if anyone has any ideas on how to fix this?

Many thanks

---

### Post by unc0nn3ct3d on 2008-11-01
So this is now happening with another file in another location on the same hard drive.  I had some mp3's in a directory that I went to add to my playlist.. As soon as the directory in question was touched the entire system froze, had to powerdown and powerup.  Tried this a few times to make sure I could replicate the results.  To test if it was the files or the spot on the disk I took the .rar file they can in and unrar'd them into another directory.  When that was complete I was able to add this second dir to my playlist and start planing no problem.
  Am I right in assuming that this could probably be a physical error on the disk itself?  If so is there a way to scan/fit/isolate the problem area telling linux not to wriet on it?

thanks in advance for your help!!

---

