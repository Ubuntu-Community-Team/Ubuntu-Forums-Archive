---
title: "quick question"
date: 2006-01-02
forum: Installation &amp; Upgrades
---

### Post by cordless on 2006-01-02
I got on old pc, it got zapped and i want to run pure lynx, is there a away to run ubuntu purely with no windows? and i need info on how to install it.

---

### Post by cordless on 2006-01-02
also i had windows 98 wipped out, its an hp, gots about 10 gigs, enuf?

---

### Post by Sef on 2006-01-03
10 gb is more than enough.   

At install screen, type server and then hit enter.

---

### Post by cordless on 2006-01-03
it wont pop up, just says no OS installed.

---

### Post by r4ik on 2006-01-03
Did you set youre bootorder to make it start from cd?

---

### Post by cordless on 2006-01-03
i got 0 knowledge ont this mumbo jumbo, all i got is this pc. and my spare, i need full info, it has 0 OS on it, and only a cd rom, not dvd, need info to install from zip.
again its old windows 98, about 10 gigs, no dvd rom, just cd+floppy.

---

### Post by dickohead on 2006-01-03
when the computer starts, it will usually mention: "Press delete to enter setup" - press delete and under the section for boot priority (can be named other things), change the order of your devices so that the CD drive is first, then restart the machine with the install disc in the drive. Once the first screen comes up, you can then type "server" to install the basic Linux packages.

---

### Post by r4ik on 2006-01-04
Shift Esc or F2 are also options to try.
Get to bootorder by using the arrows on our keyboard search fot your first boot device and change it to cd by hitting enter and change it using the left-right arrow or + -
Set the second boot device to hdd and our flop third.
Hit F10 to save the settings it will ask you y/n chose
y and hit enter again then reboot and you will be able to boot from cd.
Fingers crossed :)

---

### Post by Sef on 2006-01-04
Usually the page where you change the boot loader is a few pages back.  There should be some directions how to change pages and how to change the boot order.

---

### Post by r4ik on 2006-01-04
We are talking Bios here arent we?
To me that is only one page in wich one can hop from one section to another.
As for the instructions they are in the right hand window thanks for marking that.

---

### Post by cordless on 2006-01-06
ok, this is the situation, i only got a cd rom on the pc, no OS, my windows 98 SE was destroyed, i want to get ubuntu onto it, i need to know the process to install it right from the cs, or how to make a disc to boot from a cd, my computer has no dvd rom, and when it boots up the screen is black with white words saying "no os found" if i press anything it makes a sound of reading a floppy and the white words copy themselves one place down.

---

### Post by kook44 on 2006-01-06
The reason you are getting "No OS found" is that when you turn on the computer, its looking to boot from hard drive, which, like you said, has no OS on it.  You have to tell it to boot from the CD-ROM drive.  When you first turn on the computer, you will see a quick splash screen that will say somewhere "Press del to enter setup" or "Press F2 to enter setup"  somehting like that.  you have to press that key, whoch will take you into the BIOS setup utility.  Within that utility, you have to change the boot sequence to check the CD-ROM before the hard drive.  Save your changes, put the ubuntu install disk in the drive, and reboot.

---

### Post by benco on 2006-01-06
Just to be sure : do you have an Ubuntu CD ?

---

### Post by cordless on 2006-01-07
ok so i got into the bois, im guessing i burnt my live cs wrong, what files should go on the cd?

---

### Post by noigeaR on 2006-01-07
you have to burn the ubuntu iso file as an image. don't burn the iso file as data onto a cd. what recording software do you use? nero?

---

### Post by cordless on 2006-01-08
i got it to work, but now im getting a no root error.

---

### Post by cordless on 2006-01-08
its at the partioning portion of the install, i got to create new md, nothing, keeps looping back to a menu i cant figure out what to do next.

---

### Post by cordless on 2006-01-09
arg need some help!

---

### Post by Installer36 on 2006-01-09
If you dont care about any of the stuff on your hard drive ...when you get to the options for partioning I always select the top one "erase entire disk" something like that then it will give another prompt asking something like are you sure ..YES ... from there just follow the prompts..And just a word of advice slowwww down, and start to read all the helpfull posts here then ask the questions if you cant find the anserws

---

