---
title: "Need help...have already done 50+ reboots"
date: 2005-08-19
forum: Hardware &amp; Laptops
---

### Post by nasar2k2000 on 2005-08-19
i am stumped...

I have a presario 2570 laptop. Last nite when i booted it up a strange sound came from my speakers and now my laptop does not boot up at all.

It just displays my initial vendor screen and that is it...
the HDD activity light stays lit, and i can even feel the drive working, but apparently nothing is being read from it. There is no noise as well.

I tried to run my rescue mode and tried to mount the drive but when i do the same thing happens. The drive just keeps spinning and nothing happens.

i also tried the redhat9 rescue mode...
but when the time comes for checking the HDD partitions the error it gives me is something about "dma-timer timing out"...

PLEASE HELP...I am dead tired and VERY cranky...i dont wannt to replace my HDD...there does not seem to be any physical damage because i hear a physically damaged HDD makes noise.](*,)

---

### Post by heimo on 2005-08-19
[QUOTE=nasar2k2000].there does not seem to be any physical damage because i hear a physically damaged HDD makes noise.](*,)[/QUOTE]

Not neccessarily. :(

Did you make any BIOS changes? Can you go to BIOS, does it normally list your hard disk? Try autodetection. If that's not working, there's nothing you can do with operating system / install CDs. Sorry to say this, but according what you're telling us, it sure looks like hardware failure.

---

### Post by nasar2k2000 on 2005-08-19
[QUOTE=heimo]Not neccessarily. :(

Did you make any BIOS changes? Can you go to BIOS, does it normally list your hard disk? Try autodetection. If that's not working, there's nothing you can do with operating system / install CDs. Sorry to say this, but according what you're telling us, it sure looks like hardware failure.[/QUOTE]

yeah....

it is a TOSHIBA HDD and the bios sez just that...

when the problem first arose i used Partion Magic and it did not even read the FAT table...

but then i used the redhat9 rescue mode to write a new FAT table and it did that because when i tried Partion Magic after that it read it and showed me one unformated primary space and the resat of the unpartitioned logical space...?????:roll:

@#$% is going on!!!!

---

### Post by heimo on 2005-08-19
Laptop bioses are limited, but if it has setting for hard disk access mode, try changing it. :-/ Or try resetting BIOS to default / factory settings.

---

### Post by nasar2k2000 on 2005-08-19
[QUOTE=heimo]Laptop bioses are limited, but if it has setting for hard disk access mode, try changing it. :-/ Or try resetting BIOS to default / factory settings.[/QUOTE]

hmmmm....

i did use the reset button under my laptop...

you think that would have reset my bios as well???

---

### Post by heimo on 2005-08-19
[QUOTE=nasar2k2000]
you think that would have reset my bios as well???[/QUOTE]

Probably, but to be sure check user manual. And check if you have that access mode setting in BIOS. This is very faint idea, but something that I'd try anyway. It doesn't sound too promising.

---

### Post by nasar2k2000 on 2005-08-19
[QUOTE=heimo]Probably, but to be sure check user manual. And check if you have that access mode setting in BIOS. This is very faint idea, but something that I'd try anyway. It doesn't sound too promising.[/QUOTE]

yes i have the access mode....the PI/O and the DMA

by resetting you mean i should turn them off??

because PI/O can be turned off but not the DMA and like i said earlier the error during the rescue mode was off the DMA timer timing out.

---

### Post by heimo on 2005-08-19
[QUOTE=nasar2k2000]yes i have the access mode....the PI/O and the DMA

by resetting you mean i should turn them off??

because PI/O can be turned off but not the DMA and like i said earlier the error during the rescue mode was off the DMA timer timing out.[/QUOTE]

I meant trying it in some other than automatic mode, some of those old, slow PIO modes, I believe that turns off DMA too. Error message about DMA timeout is quite probably just a secondary error, not the root cause. :-/ :-\

---

### Post by nasar2k2000 on 2005-08-19
[QUOTE=heimo]I meant trying it in some other than automatic mode, some of those old, slow PIO modes, I believe that turns off DMA too. Error message about DMA timeout is quite probably just a secondary error, not the root cause. :-/ :-\[/QUOTE]

cant say that i have done that...

but yes i could try that out...

but can you tell me if there is ne way i can recover or 'isolate' a bad boot sector...prolly the very first sector of my harddrive...

---

### Post by heimo on 2005-08-19
[QUOTE=nasar2k2000]cant say that i have done that...

but yes i could try that out...

but can you tell me if there is ne way i can recover or 'isolate' a bad boot sector...prolly the very first sector of my harddrive...[/QUOTE]

To me, it doesn't look like just a bad master boot record. :( It looks like some kind of hardware problem, but can't be even 100% sure that it's the hard disk. If it is, I'd be just happy that it wasn't motherboard (which would mean you would buy a new laptop instead of relatively inexpensive (and easily replacable) hard disk.

---

### Post by nasar2k2000 on 2005-08-22
[QUOTE=heimo]To me, it doesn't look like just a bad master boot record. :( It looks like some kind of hardware problem, but can't be even 100% sure that it's the hard disk. If it is, I'd be just happy that it wasn't motherboard (which would mean you would buy a new laptop instead of relatively inexpensive (and easily replacable) hard disk.[/QUOTE]

:groan:
:roll:

---

### Post by heimo on 2005-08-22
Any news? No luck? :(

---

### Post by nasar2k2000 on 2005-08-23
[QUOTE=heimo]Any news? No luck? :([/QUOTE]
 
yeah man...
 
no luck...none at all

---

