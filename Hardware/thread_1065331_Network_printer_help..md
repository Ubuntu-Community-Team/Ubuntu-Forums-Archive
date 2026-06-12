---
title: "Network printer help."
date: 2009-02-09
forum: Hardware
---

### Post by GARoss on 2009-02-09
I am new to Ubuntu. For about 1 week I, with a great deal of help from this forum, have a dual boot Ubuntu/Xp working and I can network my Ubuntu 8.10-64bit to 2 other XPs, both 32bit, on a hub. For my printer I had to install TurboPrint in my Ubuntu to get my Canon i950 to work. It works perfectly when plugged into Ubuntu's USB port.
But, now I would like to move the i950 back to the 32bit XP it was originally plugged into (this is how we had the network when all 3 were XPs & all could print fine). So far, I'm unable to do this from the Ubuntu. I don't know if it matters that my Ubuntu is 64bit & the XP is 32bit. I figure I've got to use the 64bit drive in Ubuntu, right?
Opening *System/Administration/Printers* then *Properties* to add i950 printer as a network. Here's Printer Properties:
 
[http://i92.photobucket.com/albums/l10/queenofshines/maries%20tidbit%20trays/Screenshot-PrinterProperties-Canon_.png](http://i92.photobucket.com/albums/l10/queenofshines/maries%20tidbit%20trays/Screenshot-PrinterProperties-Canon_.png)


Description- is the tag I put on the network printer from The Ubuntu.
Location- Marie is the name of the XP.
Device URI- smb://192.168.0.4/print$/ points to the network shared print folder.
Make & Model- the TurboPrint drive
Printer State- denied results

Am I on track or not; what am I doing wrong.
George

---

### Post by GARoss on 2009-02-10
Bump-
Anyone?

---

### Post by GARoss on 2009-02-10
It seems to be a driver issue; different systems-Xp & Ubuntu. I reversed & got a warning on the XP to that affect. See;
[http://ubuntuforums.org/showthread.php?t=1065671](http://ubuntuforums.org/showthread.php?t=1065671)
George

---

