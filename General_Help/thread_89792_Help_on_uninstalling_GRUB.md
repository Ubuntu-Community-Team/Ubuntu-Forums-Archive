---
title: "Help on uninstalling GRUB"
date: 2005-11-13
forum: General Help
---

### Post by edo_e on 2005-11-13
Hello there. I'm still new to Linux.

I have 3 hard disk. I installed WinXP on the first disk and Red Hat on the third disk. Used GRUB. Everything runs perfect.

Later, I wanted to replace my Red Hat with Ubuntu. I thought that Ubuntu's GRUB installer will just overwrite it. The installer asked me to remove the CD and the installer will restart the system.

My PC restarts and stops at:
"GRUB Loading stage 1.5."

"GRUB Loading, please wait..."
"Error 22"

Now, I can't boot to Windows or Ubuntu. Everytime I restart my PC, i will stuck there. Tried to run the Ubuntu installation again but same result. Tried again but I choose LILO. Same results.

I dun have floppy drive and my WinXP CD dun have the recovery console. I dunno why my WinXP CD dun have the recovery console.

What I wanted to do now is, reset my MBR so I can boot to my WinXP and install Ubuntu later like how I install Red Hat.

Can I reset my MBR with the Ubuntu installer CD? What other methods than 'fdisk' can I use? I've been googling around but I can't find the answer that can help me.

Please help me. Thank you.

---

### Post by aysiu on 2005-11-13
One of these two links should help:

[http://ubuntuforums.org/showthread.php?t=24113](http://ubuntuforums.org/showthread.php?t=24113)
[http://www.microsoft.com/resources/documentation/Windows/XP/all/reskit/en-us/Default.asp?url=/resources/documentation/Windows/XP/all/reskit/en-us/prkd_tro_ldau.asp](http://www.microsoft.com/resources/documentation/Windows/XP/all/reskit/en-us/Default.asp?url=/resources/documentation/Windows/XP/all/reskit/en-us/prkd_tro_ldau.asp)

---

### Post by CompleteNewb on 2005-11-13
Ok, so i am also extremely new, but when i first installed ubuntu i was getting the same grub error, so what i did was went to bios and reset to default settings, after that i jsut went back into the cmos setting and set priomary boot to ide1 and grub loaded up and everything was alright, i hope that helps.

---

### Post by edo_e on 2005-11-13
Thanks for the links..

but the first technique can't be done with Breezy Badger installer. The manual partition option is not there. I can download the Live CD but with my internet connection speed, I would take days to finish the download.

Is there any other way to fix the mbr with the Breezy Badger installer?

I will still try to download the Live CD on my friend's PC.

---

