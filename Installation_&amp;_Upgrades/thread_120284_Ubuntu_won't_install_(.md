---
title: "Ubuntu won't install :("
date: 2006-01-21
forum: Installation &amp; Upgrades
---

### Post by KSean on 2006-01-21
I've tried installing Ubuntu 5.1, and when it gets to the base install, it freezes at 6%. I also tried 6.04, same problem. I've used both CD-R's and CD-RW's, at different speeds, and again, it still won't work :(

**EDIT:** Ok, I managed to get to the end of the install by typing "linux noapic" at the boot: thing, but at the copying extra files thing (something like that :P) it got around half way then I got an error :\

I skipped that bit after the error and installed GRUB, then after the reboot in the configuration, it froze at 0%

I need some help :S

**EDIT2:** I just tried something else - I tried installing the server (which went well), then using sudo apt-get install ubuntu-desktop.

Whilst doing that I kept getting the following error: Buffer I/O error on device hde, logical block *, where * is a number. =\

**EDIT3:** I also tried with boot: linux no=acpi - stopped at the copying extra packages :(

---

### Post by Mustard on 2006-01-21
I'll go through the standard questions to troubleshoot this commonly asked question. :)

Where did you get the install CD from?

If you downloaded the ISO's did you run an md5sum check on the ISO's to see if they were corrupted during download?

Did you burn the at the lowest speed possible?

Did you verify the media before installation?

If you could describe your system it would be good too.  Are you using a desktop computer or laptop?  Is it an old system or a new one?  What type of hard drive setup have you got?

---

### Post by KSean on 2006-01-21
Where did you get the install CD from?
I got it from [www.ubuntulinux.org](www.ubuntulinux.org)

If you downloaded the ISO's did you run an md5sum check on the ISO's to see if they were corrupted during download?
Yes.

Did you burn the at the lowest speed possible?
Yes, I burnt the CDs at 1x.

Did you verify the media before installation?
Nope :S

My system is:
2.4ghz Intel Celeron
256mb ram
40gig Hard Disk
Desktop with Windows XP
It's around 2 years old.

---

### Post by Elrond on 2006-01-21
Have you tried at speed about 2x or 4x?
I burned mine with 8x speed becouse my nec don't support slower speeds and it worked out fine.

Also try to download iso again...maybe it will work. ;)

---

### Post by KSean on 2006-01-21
[QUOTE=Elrond]Have you tried at speed about 2x or 4x?
I burned mine with 8x speed becouse my nec don't support slower speeds and it worked out fine.

Also try to download iso again...maybe it will work. ;)[/QUOTE]
I've downloaded the iso around 4 times in the last few days, and I burned 3 of them at 1x :S

---

### Post by Mustard on 2006-01-21
Hmm..ok.  Well I suppose we can assume the media is ok.  Which is a pity as the direction to take from here becomes more vague. :)

When you start up the install CD there is a function key option you can press to read about extra install options.  I'm thinking that some of these might be useful in helping the install to proceed.  Options like -noapic -nolapic, I can't recall the exact options.  I'll have a search around on the forums and see if I can find something.  In the meantime someone might come along with some other answers hopefully.

---

### Post by KSean on 2006-01-21
[QUOTE=Mustard]Hmm..ok.  Well I suppose we can assume the media is ok.  Which is a pity as the direction to take from here becomes more vague. :)

When you start up the install CD there is a function key option you can press to read about extra install options.  I'm thinking that some of these might be useful in helping the install to proceed.  Options like -noapic -nolapic, I can't recall the exact options.  I'll have a search around on the forums and see if I can find something.  In the meantime someone might come along with some other answers hopefully.[/QUOTE]
Ok, thanks :P

---

### Post by Mustard on 2006-01-21
What USB devices have you got connected to the computer atm?

Can you check your BIOS settings to see if USB legacy device is disabled? If it isn't can you disable it?

-edit-

Well the search function on the forum has gone fubar on me atm, so I can't search for anything.  I can't do much about that atm unfortunately. :)

---

### Post by KSean on 2006-01-21
I currently do not have any USB Devices connected.

Also, where in the BIOS settings would I check if USB legacy is disabled?

---

### Post by Mustard on 2006-01-21
[QUOTE=KSean]I currently do not have any USB Devices connected.

Also, where in the BIOS settings would I check if USB legacy is disabled?[/QUOTE]

I wouldn't worry about it if you haven't got any USB devices going. Atm the only thing I can say is to keep trying, and try a few of the special install parameters.  There is never any one cause for this problem.  It varies from case to case.  It could be bad blocks on your hard drive, a problem with the CD drive, or any other number of vague and obscure reasons. :)

Some people have gone through the process many times over and then all of sudden it starts working.

Keep swapping the disks around that you use maybe, since you seen to have a whole collection of them now. :)  I think there is a 'verify' option or 'check media' option somewhere in the function key options too.  You could try that on all the disks you have.

---

### Post by KSean on 2006-01-21
[QUOTE=Mustard]I wouldn't worry about it if you haven't got any USB devices going. Atm the only thing I can say is to keep trying, and try a few of the special install parameters.  There is never any one cause for this problem.  It varies from case to case.  It could be bad blocks on your hard drive, a problem with the CD drive, or any other number of vague and obscure reasons. :)

Some people have gone through the process many times over and then all of sudden it starts working.

Keep swapping the disks around that you use maybe, since you seen to have a whole collection of them now. :)  I think there is a 'verify' option or 'check media' option somewhere in the function key options too.  You could try that on all the disks you have.[/QUOTE]
Ok, I'll try that now, be right back.

EDIT: I erased all of the CD-RWs after they wouldn't work :s

---

### Post by stuglass on 2006-01-21
i get a similar problem, during the last phase after it reboots where it installs the packages it stops at 44%('gstreamer0.8-jpeg'). ive also tried reburning, downloading the iso again and still no pie! ive got the same setup mentioned but i havnt tried the function. 
does it matter if i do not have an ethernet adapter???

---

### Post by Mustard on 2006-01-21
[QUOTE=stuglass]i get a similar problem, during the last phase after it reboots where it installs the packages it stops at 44%('gstreamer0.8-jpeg'). ive also tried reburning, downloading the iso again and still no pie! ive got the same setup mentioned but i havnt tried the function. 
does it matter if i do not have an ethernet adapter???[/QUOTE]

It shouldn't matter, I got the 'no ethernet adapter' part come up for me everytime I installed, as I have a dialup connection.

I think your problem is slightly different in that you have gone well past the base installation process, and have reached the stage of applications installing and configuring themselves after the reboot.  If you have trouble at this stage, it may be possible to finish the installation via the command line (if you get a command line at all).

---

### Post by KSean on 2006-01-21
Does anyone have any more ideas on how I could fix this? :S

EDIT: Also is it possible to install Ubuntu from another partiton? For example, if I put the iso onto a seperate FAT32 partition, could I boot from it?

---

### Post by KSean on 2006-01-21
Ok, I managed to get to the end of the install by typing "linux noapic" at the boot: thing, but at the copying extra files thing (something like that :P) it got around half way then I got an error :\

I skipped that bit after the error and installed GRUB, then after the reboot in the configuration, it froze at 0% :(

I need some help :S

---

### Post by KSean on 2006-01-21
I just tried something else - I tried installing the server (which went well), then using sudo apt-get install ubuntu-desktop.

Whilst doing that I kept getting the following error: Buffer I/O error on device hde, logical block *, where * is a number. =\

---

### Post by Ocxic on 2006-01-21
try doing a zero fill of your drive, it may solve you i/o error, worked for me.

---

### Post by KSean on 2006-01-21
[QUOTE=Ocxic]try doing a zero fill of your drive, it may solve you i/o error, worked for me.[/QUOTE]
How would I do a "zero fill"?

---

