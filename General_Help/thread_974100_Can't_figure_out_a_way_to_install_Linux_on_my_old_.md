---
title: "Can't figure out a way to install Linux on my old computer..."
date: 2008-11-07
forum: General Help
---

### Post by Qimo on 2008-11-07
Hey,

I want to install linux on my old computer.
Its running on Win98 now, but originally Win95, so i my first question is: What kind of linux should i install? Puppy? DSL?

I got a Toshiba Tecra 500CDT, with 32mb ram and a CD-driver, but no diskette driver (there is some ports on the back of it that i think is for a diskette driver, but then i think i will need a cable and stuff), and it cant boot from CD, so i dont know how to install linux.
So i need the easiest way possible to install. Any suggestions?

---

### Post by beno1990 on 2008-11-07
Try Damn Small Linux if you're not desperate for a super-friendly GUI.

---

### Post by Therion on 2008-11-07
What do you mean it can't boot from a CD?  What happens when you try?  

How are your burning your .iso CD's and have you looked at the system's BIOS settings to make sure the optical drive is the first drive in the boot sequence?

---

### Post by Qimo on 2008-11-07
I cant reach any BIOS settings at all, that may be because im not that good with computers, but on start-up it doesnt say a thing about BIOS settings as it does on my normal computer...

---

### Post by DefineByte on 2008-11-07
Just repeatedly mash (technical term) the delete key from the moment you turn the computer on. :)

---

### Post by Therion on 2008-11-07
On the older Toshiba's you usually need to hit the ESC key during the boot sequence, and then either F1 or F2, to gain access to the BIOS.

---

### Post by Qimo on 2008-11-07
Alright, i found BIOS, thanks :D But then i look at the boot priority and i am able to choose FDD>HDD or HDD>FDD. 
I switched from FDD>HDD to HDD>FDD (the original settings) to see what happens, which was nothing. :(

---

### Post by Therion on 2008-11-07
Okay, that's not good.  

FDD = Floppy Disk Drive and HDD = Hard Disk Drive.  Booting from your optical it appears, is not an option.  

Time for Plan B:

[https://help.ubuntu.com/community/Installation](https://help.ubuntu.com/community/Installation)

See the section **Installation Without a CD**.

---

### Post by Qimo on 2008-11-07
Okay, im trying to install in a way which u need no removable media. Hope it works, i'll write how it went later!

---

### Post by Qimo on 2008-11-07
I tried with a thing called intlux, which u could install linux from Windows (No CD boot-up required). I clicked the .exe file and it starts to load. After 2 min a pop-up appears which says "This is not a Win32 program"(I tried to translate from swedish :P) 
I checked the Netboot program too, which was basically the same thing, but it required Win2000 at least.

*sigh*.... What can i do now? :(

---

### Post by Coreigh on 2008-11-07
This is the really long way around but ...

Linux is somewhat hardware generic. You could remove the hard drive and mount it in another working computer, install linux and replace it in the older machine. I would suspect that there will be some hurdles doing this, the most worry-some being network card driver concerns.

but it is an idea.

---

### Post by Qimo on 2008-11-07
I think it's a rather good idea! Worth a try!
Hope i don't break something :P

---

