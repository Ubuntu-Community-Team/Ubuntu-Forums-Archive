---
title: "wubi installer quits without displaying anything"
date: 2009-07-14
forum: Installation &amp; Upgrades
---

### Post by jtniehof on 2009-07-14
I double-click on the wubi exe, the cursor changes to hourglass and the hard drive cranks for a bit, and wubi.exe shows up in task manager. After a few seconds the cursor changes back to an arrow, the hard drive activity stops, and wubi.exe disappears from task manager. At no point does the installer display anything nor appear to actually do anything.

Thinkpad T43 running XP, same results using the "Download now" link from the wubi homepage, rev129 from SourceForge, or rev 134RC from the thread in this forum. Antivirus disabled for the installation.

---

### Post by riyanm on 2009-07-14
hi there jtniehof,
 
I don't have a solution for you but perhaps a clue.  I have a Thinkpad X40 and my system does the same thing.  I have GRUB in my MBR.  Do you have the original IBM MBR, or have you modified it?
 
My guess is that this problem happens to IBM Thinkpads.  Mine is three years old, and seems like yours is newer.

---

### Post by jtniehof on 2009-07-16
Thanks for the suggestion. The T43's a few years old, probably about the same vintage as yours. It's the original MBR, nothing funky done to it.

I'd find it really bizarre if something in the MBR kept a Windows app from even starting (since, after all, that's all the installer is at that point.)

---

### Post by MadmanMike83 on 2009-07-31
I have the same problem on old IBM thinkcentre desktop running Windows XP SP3.  wubi.exe pops up in the task manager for a second or two then disappears. without any visible effect.

---

### Post by MadmanMike83 on 2009-07-31
Oddly enough the 8.10 wubi installer loads up fine, but I don't really want Ubuntu 8.10.

---

### Post by jtniehof on 2009-09-02
I checked in %TEMP% for the wubi log file...there is none there, just a pyl82.tmp.exe with the wubi logo.

---

### Post by ropeladder on 2009-09-16
I am having the same problem with the installer on my old homebuilt Windows98SE machine. Some processes start running (which you notice if you hit ctrl-alt-delete right away) and then everything disappears.

-ben

---

### Post by arnige on 2009-09-17
Exactly the same problem here on a Dell Precision M65 running XP SP3.

---

### Post by compo80 on 2009-11-02
I have [SIZE=1]the same problem on an old desktop:[/SIZE]
[FONT=Times New Roman][SIZE=4][FONT=Times New Roman][SIZE=4][FONT=Verdana][SIZE=1]MS-6368 Micro-ATX Mainboard[/SIZE][/FONT]
[FONT=Verdana][SIZE=1]504Mb Ram[/SIZE][/FONT]
[FONT=Verdana][SIZE=1]Intel Celeron 1066MHz [x86 Family 6 Model 11 Stepping 1][/SIZE][/FONT]
[FONT=Verdana][SIZE=1]Windows 98SE.[/SIZE][/FONT]
[FONT=Verdana][SIZE=1][/SIZE][/FONT] 
[FONT=Verdana][/FONT]
[FONT=Verdana][SIZE=1]I have already tryed a lot of thing to get ubuntu -including clean the cd drive lens and try unetbootin- but no one work.[/SIZE][/FONT]
[FONT=Verdana][SIZE=1][/SIZE][/FONT] 
[FONT=Verdana][SIZE=1]Please help[/SIZE][/FONT]
[FONT=Verdana][SIZE=1]Thank you in advice.[/SIZE][/FONT]
[/SIZE][/FONT][/SIZE][/FONT]

---

### Post by Bernie9119 on 2009-11-10
Same problem here on an old Acer laptop with XP. The log file says that the write to registry for the uninstaller failed with "access denied". The account has no admin rights.

---

### Post by tracybejj on 2011-01-15
> **jtniehof said:**
> I double-click on the wubi exe, the cursor changes to hourglass and the hard drive cranks for a bit, and wubi.exe shows up in task manager. After a few seconds the cursor changes back to an arrow, the hard drive activity stops, and wubi.exe disappears from task manager. At no point does the installer display anything nor appear to actually do anything.Thinkpad T43 running XP, same results using the "Download now" link from the wubi homepage, rev129 from SourceForge, or rev 134RC from the thread in this forum. Antivirus disabled for the [[COLOR=#000000]installation[/COLOR]](http://www.software-to-convert.com/asf-conversion-software/index.html).It's helpful to me, It's very detailed, Thanks for your effort!

---

