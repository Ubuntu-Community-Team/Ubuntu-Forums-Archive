---
title: "Tip:  Boot Fail From USB Solution"
date: 2009-01-06
forum: Installation &amp; Upgrades
---

### Post by NorgeFortuna on 2009-01-06
If you are having trouble loading Ubuntu from a live CD to a USB memory stick, this may help.

SITUATION:  You run Windows, but you are playing with Ubuntu using the live CD, and you want to install Ubuntu onto a bootable USB memory stick using the menu option on the live CD so you can preserve settings between sessions while you learn the program.  The process appears to work fine, but when you try to boot from the memory stick, the computer ignores it and boots into Windows instead.  

SOLUTION:  Here are three ideas to try:  Check for an updated BIOS from your manufacturer, start with a completely blank USB memory stick, and, if you know EXACTLY what you are doing, format the USB drive using Ubuntu and the live CD.  (WARNING: If you don't know EXACTLY what you are doing, don't try the last suggestion--you might accidentally select your hard drive to format instead and lose all your data.)

DISCUSSION:  I was using a 3-year old Toshiba laptop and had never updated the BIOS.  I'm guessing that was the real problem.  I mention the other two actions only to be complete because I also did those things and didn't check in between to see what actually solved the problem.  Also, to erase everything on the memory stick from SanDisk with U3 programs installed, I started the U3 program and removed it using it's own de-install option.  Again, probably no difference, just FYI. 

RESULTS:  I used memory sticks from SanDisk, Toshiba, and two no-name generics.  Before, only one of the generics worked. After, the computer booted successfully into Ubuntu from all four.  I'm new to Ubuntu and new to the forum, so I apologize if it's already widely known, but I didn't see it mentioned on various installation guides I checked on the web.  I thought it might be useful.

---

