---
title: "Did Linux Kill My Computer"
date: 2006-04-02
forum: Hardware &amp; Laptops
---

### Post by mafukidze on 2006-04-02
i loaded ubuntu in my compaq deskpro 1600 on a 40GB, 256 Mb. After a few linux short comings or rather my ignorance , i removed it and tried to install windows xp, which failed to boot, tried also win 2003 which failed , i even went to the xtend of trying to load win2000 invain. i get the same message " error loading operating system. i took the harddrive and mounted it on another machine which booted succesfully.

i then tried to load linux ubuntu and it loaded only to give me an error message after rebooting " the error was error 21 ". i think i know my hardware and i think something fishy is happening.

the million dollar question is: what happened. was it coincidental or was it something i can get an explanation for?

dont tell me about reconfiguring the hdd in cmos because compaq does that on its on and besides it has no option of directly accessing cmos . the cmos program is loaded on the harddrive.

:evil:

---

### Post by Buffalo Soldier on 2006-04-02
Did you remember to set the computer to boot to CD?

---

### Post by mafukidze on 2006-04-02
yes it would load win xp make partitions and finish load but will fail to boot

---

### Post by dixonstalbert on 2006-04-02
Hi mafukidze

I could get into BIOS with Compaq computers by pressing F10 during boot up

other suggestion is boot with windows CD and get into Recovery Console and try the Fixmbr command (this is a dangerous command; probably should google Grub and fixmbr first) 

also could use diskpart command in recovery console; type diskpart in recovery console, then type help at diskpart prompt to get a list of commands

you could delete boot partition and rewrite it with diskpart to make sure its clean and ubuntu hasnt left anything in there

good luck

---

### Post by mafukidze on 2006-04-02
before i try that do you think the same error i am getting can not be seen on other computers? i have tried the harddrive on other computers and it worked. what does error 21 mean. i have reloaded linux and it starts loadeing grub and then says error 21

---

### Post by dixonstalbert on 2006-04-02
pasted from googling 'grub error 21' from query on the Debian Forum


I guess you've already seen this from the Grub manual:

21 : Selected disk does not exist
     This error is returned if the device part of a device- or full file
     name refers to a disk or BIOS device that is not present or not
     recognized by the BIOS in the system. 


The thing is, Linux itself will see the drive even if it's not enabled
in the BIOS setup, but GRUB won't because it depends on the BIOS to do
that. That explains why you can see it from Knoppix, and why you could 
install Debian there to begin with.

Seems pretty clear that the drive is there and working as far as Linux
is concerned. Why the BIOS won't recognize it is the question. Does it
get detected if you (temporarily) move it to another position like the
secondary slave?


___________________________________

Did you try hitting F10 during boot up? see what harddrives are set at in BIOS if F10 works for you- another trick to get BIOS back to factory default if F10 does not work is to take flat NiCad battery out of clip on the motherboard, wait half a minute and then put it back in

---

