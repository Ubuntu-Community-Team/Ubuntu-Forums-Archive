---
title: "How to check hard drive from live CD"
date: 2009-06-09
forum: Installation &amp; Upgrades
---

### Post by raymondvillain on 2009-06-09
Trying to install Jaunty 9.04 from the live CD and having problems.

If I open a terminal window (while booted to the live CD) is there a way I can have it "see" the partitions and files on the hard drive?

I already had Jaunty (upgraded from Intrepid) on my machine but was having lots of problems

Now while I'm running from the live CD I cannot get Nautilus to work.  If I click on "places" a tab appears on the bottom taskbar and says "opening Ubuntu" and after a while it goes away.  Nautilus never appears.  A message box pops up that says "Sorry, the program "nautilus" closed unexpectedly

Your computer does not have enough free memory to automatically analyze the problem and send a report to the developers."

Any and all suggestions would be greatly appreciated.

---

### Post by Therion on 2009-06-09
I'm assuming this is available via the LiveCD...

System/Administration "Partition Editor"

Further, do you know the basic specs of the PC you're trying to install Ubuntu on?  How much memory, graphics, hard drive size, CPU... That sort of thing?  Or make and model if it's an off the shelf system?

---

### Post by yaroto98 on 2009-06-09
alt+F2 type "gparted"
or in a terminal type "df"

---

### Post by yaroto98 on 2009-06-09
"not enough memory"? how much RAM does your computer have?

---

### Post by blackxored on 2009-06-09
Switch to a virtual console. 

```
fdisk
```

That should be all.

---

### Post by raymondvillain on 2009-06-09
Thanks, folks, for all the help.

If I do alt+F2 and choose "gparted" I get the same partition editor as when I select System>Administration>partition editor.  I can see the partitions but not the files.  Is there a way to check files from within partition editor?

If I open a terminal window and type "df" It shows me the Ubuntu live CD partitions, not the ones on my hard drive.

The machine is a 4 year old HP desktop with a pentium 4 and 3 Gig of memory.  Dual boot, windows XP and Ubuntu.  The Ubuntu partitions are on a separate 250G hard drive.

I originally installed Hardy and all was well.  Upgraded to Intrepid and had a few rough spots getting bluetooth to work but finally things were pretty smooth.  Then I upgraded to Jaunty and had lots of problems (could not launch a terminal window, etc.) so I'm trying to install Jaunty on top of itself from the live CD.

---

### Post by raymondvillain on 2009-06-09
I'm pretty green with Ubuntu and Linux.  What is a virtual console?  How does one "switch to a virtual console"?

---

### Post by blackxored on 2009-06-09
Ok, your linux handbook will tell you. 
A virtual console, is a virtual terminal used by your machine, from which usually the 7th is the GUI (what you're used to). From a GUI you could press CTRL+ALT+[F1-F6] for "switching to the virtual console 1-6". Usually tty8 is for logging. You could return to the GUI by skipping the Control and pressing ALT+F7. Hope it helps.

---

### Post by raymondvillain on 2009-06-09
Thanks, blackxored!

I can indeed use fdisk to see the partitions on the hard drive that has ubuntu.

I would like to open (or copy) the /boot/grub/menu.lst file that is on the hard drive (/dev/sdc in my case).  From a virtual terminal, how does one do that?

If I'm in a virtual terminal and I type ls -l I get the files and directories used by the live CD, not the ones on the hard drive.  Is there a way around this?

Thanks for your help.

---

