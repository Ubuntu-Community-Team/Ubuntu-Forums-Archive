---
title: "Laptop with dead CD, external via USB"
date: 2009-05-12
forum: Hardware
---

### Post by wanderingarticfox on 2009-05-12
[FONT="Arial"][SIZE="3"]First off I'm a noob with Ubuntu and somewhat to computers in general. I'll try to keep this short but here is the issue: I have an old Compaq 1200 laptop that has an internal CD/RW that is dead/kaput. I can get as far as selecting the language and the initial part of the instal before the CD craps out and I have to use the paperclip to open the drive.  I do have full access to the CD via an external CD/RW connected by USB.  The problem is multifold here: 1]I've tried all combinations to enter BIOS and the WinMe/Compaq OEM will not let me in, 2] I'm looking the Ubuntu 810 i386 in the external drive but have no idea how to get windows to let me 'command' prompt for an instal.. I really would like to shove Ubuntu into this machine and say good bye to the MS ME for once and all.  I'm writing on my desktop ,in XP-Home; but I'm dual  boot with  Ubuntu 8.10 and learning and my music is still there.   I also have the capability to link my desktop to the laptop via USB if anyone knows how to walk me through the ISO transfer.  I really would not post here because I'm a noob but I need some experienced eyes, and some patience and obviously a lot of HELP](*,) The folders I'm looking at on the laptop are   .disk  casper  dists   install  isolinux  pics  pool  preseed  umenu.exe   the wubi and readme stuff.  I just do not know what to tell windows to open this stuff with. I know Linux sees windows but I've learned about windows being blind to Linux.   Oh, one last thing, I have a 4 Gb jump drive I could use also. I think my trouble lies in not being able to reboot via USB and rebooting by internal CD is only going to get me a language and install selection,  after the bar goes back and forth , when things are starting to 'load' the internal cd drops dead. It does this with two Ubuntu 8.10 CD's and music and any other CD's so it is kaput:( Can not even use a 'restore' disc to fix windows-not that I want to:o Thanks for taking the time to read and all help is appreciated. Gonna scatch my head a wait now:confused:](*,):biggrin:](*,)[/SIZE][/FONT]

---

### Post by Skripka on 2009-05-12
Odds are, the normal LiveCD installer will NOT work with hardware this old and lowend.  Specs I grabbed from here:

[http://www.amazon.com/Compaq-Presario-Notebook-700-MHz-Pentium/dp/B00005O03A](http://www.amazon.com/Compaq-Presario-Notebook-700-MHz-Pentium/dp/B00005O03A)

You can try the alternate install instead as alluded to here:

[https://help.ubuntu.com/community/Installation/SystemRequirements](https://help.ubuntu.com/community/Installation/SystemRequirements)

---

### Post by wanderingarticfox on 2009-05-12
](*,)](*,)[FONT="Arial"][SIZE="3"]Yea, that's the old beastie. I poped a 256K of Ram up the back but I'm stuck with the 6Gb HDD. I've never opened a laptop but really just want to convert to make it a portable pdf file reader for study and stuff. Therefore the more reason to kick micro off.  I'll look at the alternate and see if I can learn there:o[/SIZE][/FONT]

---

### Post by wanderingarticfox on 2009-05-12
[FONT="Arial"][SIZE="3"]Is it possible to run the instal from the CD in an external/USB connect mode without rebooting?:confused:[/SIZE][/FONT]

---

### Post by Skripka on 2009-05-12
> **wanderingarticfox said:**
> [FONT="Arial"][SIZE="3"]Is it possible to run the instal from the CD in an external/USB connect mode without rebooting?:confused:[/SIZE][/FONT]

There are other ways of getting *buntu onto a system inside of Windows...but unfortunately those only work with a much larger hard disk.

Reading your original post, if your machine does have a broken CD drive you may be SOL.  With how old your machine is, there's a chance that it won't let you boot from USB...in which case you may be sunk.

If you have not gotten into your BIOS yet-odds are the keystoke (right after boot) should be one of the following: F11 or F12 or Delete.  Those are the most common I have seen...a long time ago I think I might have seen F2 also.  Once you get in there you need to find a listing of devices to boot from-and hope your USB is listed.

---

### Post by wanderingarticfox on 2009-05-13
yeah, I've tried all the F-key entries  and all I get is audible noise that I think is OEM but may be a sign of doa for the system.  I'll keep trying to get into BIOS. I was just hoping there was a way to tell windows to open the data on the CD, it ask what I want to use to open it and I'm looking at the folders on the desktop CD and just hoping someone might know. I know the small drive is an issue but that's why I'm trying for a clean install to wipe windows out completely.](*,)](*,)
 and 13 comes before 14 and after 12 :)

---

### Post by lisati on 2009-05-13
Don't know if this will help: one of my machines is a Compaq desktop. The key for selecting the boot device is "Esc" while the Compaq logo is being displayed.

---

