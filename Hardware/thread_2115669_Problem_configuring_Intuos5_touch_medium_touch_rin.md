---
title: "Problem configuring Intuos5 touch medium touch ring"
date: 2013-02-13
forum: Hardware
---

### Post by bent95kr on 2013-02-13
Hi Ubuntuforums! I can't configure the functions of the touch ring of my Wacom Intuos5 touch medium tablet in the system settings. Dragging my finger around the touch ring clockwise changes the touch ring mode, just like the button inside the touch ring does, and dragging my finger anticlockwise does nothing. And whenever I try to change the functions of the touch ring in the (gnome) system settings, it has no effect. The express keys works though and can be configured as they should though the system settings.
 

 This doesn't happen in windows 7, so I know it's not a hardware issue. Also, all of the tablet's components show up using the “xinput list” command in the terminal.
 

 I use the 64-bit version of Ubuntu 12.10.
Any help would be truly appreciated!

---

### Post by Favux on 2013-02-13
Hi bent95kr,

I believe the default xf86-input-wacom in Quantal is 0.17.  That's the xorg-xserver-input-wacom-0.17 package.  I am reasonably sure some of the commits after it was released fixed issues with the touch ring.

If so what you'd want to do is either download and compile the xf86-input-wacom-0.19 tar or clone the git repository.  See the [BambooPT HOW TO]("http://ubuntuforums.org/showthread.php?t=1515562").  You'd have to update the commands to the correct version or see the updated [BambooPT HOW TO]("http://forums.linuxmint.com/viewtopic.php?f=42&t=110408").

---

### Post by bent95kr on 2013-02-13
Hi, I tried what you suggested, and I hope I got it right... Anyway, I installed it, and now, sometimes when I reboot the computer or reconnect the tablet, it works perfectly, and other times the issue still persists. It seems pretty random when it works and when it doesn't, and I can't see any patterns whatsoever.
 

 I have no clue, but could it be possible that I did something wrong when installing xf86-input-wacom-0.19, and that I now have two drivers (or whatever it is), fighting each others? So that when the tablet is plugged in, whoever gets to the tablet first is activated. It's probably a stupid thought, but I don't know much about these things...

---

### Post by Favux on 2013-02-13
Alright, so the touch ring does work correctly when the tablet is working?

The only conflict would be between xsetwacom binaries if you forgot the correct flag when compiling and ended up with two versions active.  That's described in troubleshooting near the bottom of the HOW TO.

Otherwise I think we're back to your original issue.

---

### Post by bent95kr on 2013-02-13
No, I must have explained myself unclearly, the past issue I had is fixed, and when I said the tablet is not working, I just meant touch ring. The tablet itself is working great at all times now.
 

 I read through the troubleshooting section, but I had problems with understanding the thing about the extra flag and where to look for these duplicates and what to do if I found them. If I understood correctly though, the duplicate (a xsetwacom file) would be found in both usr/local/bin and usr/bin, correct? If so, I don't have a duplicate, as the usr/local/bin folder was empty. Also, the lib64 folder only had one file in it, if that has anything to do with anything.

 

 But the duplicate theory was just an unqualified guess of mine, I just started using linux for the first time a few days ago, and have no idea how any of these things actually works.

---

### Post by Favux on 2013-02-13
Good to hear we're not back to the original issue.

I have no clue why the touch ring would be working intermittently now.  I would have thought the xf86-input-wacom update would have either fixed it or not.  It sounds like your compile was succesful.  You would have seen errors in the terminal output when compiling if something was wrong.

About the only suggestion I have left is since you couldn't reinstall gnome-control-center see if Synaptic Package Manager will let you reinstall the gnome-settings daemon.  I'm bothered that reinstalling the gnome-control-center is grayed out.  That doesn't sound right.  But again something may have changed with Quantal compared to Precise.

---

### Post by bent95kr on 2013-02-13
[FONT=Times New Roman]I tried reinstalling gnome-settings-deamon, even though reinstalling it was possible, it didn't solve the issue. I used git to install xf86-input-wacom, don't know if that works the same as compiling it... And I didn't see any errors anyway.[/FONT]
[FONT=Times New Roman] [/FONT][FONT=Times New Roman]
[/FONT] 
[FONT=Times New Roman] [/FONT][FONT=Times New Roman]Come to think of it I'm not sure I pointed out that when the touch ring is working, it works until I either reboot it or reconnect it, that the issue doesn't start or disappear without doing either of these things.[/FONT][FONT=Times New Roman, serif]
[/FONT]

---

