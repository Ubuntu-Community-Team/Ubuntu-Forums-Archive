---
title: "love ubuntu now how do i get onto laptop?"
date: 2009-01-28
forum: Installation &amp; Upgrades
---

### Post by irpayne on 2009-01-28
Flush with success after installing Ubuntu onto my old (wifes) HP laptop and getting everyting running nicely so far inc wifi card, mail, movies pics etc I have decided to pu it onto my newer laptop which has windows xp on.
I would love to get rid of XP but can't 'cos I use some windows programs for work.
Dual boot I thought, no such luck!
Will not boot from hard drive or cd.
Can get a cursor when using the ACPI getaround choice on boot but don't now what to do with it!
Help menu is coming up but what do I do now?
I dont have a floppy which I think is giving an error message.
I do have built in wifi and a sd card slot.
Any ideas? would loce to run both systems but don't know linux commands to do anything with the cursor that I can get up!!!
Cheers 
Ian

---

### Post by abn91c on 2009-01-28
give wubi a try [http://wubi-installer.org/](http://wubi-installer.org/)

---

### Post by Tomatz on 2009-01-28
> **irpayne said:**
> Flush with success after installing Ubuntu onto my old (wifes) HP laptop and getting everyting running nicely so far inc wifi card, mail, movies pics etc I have decided to pu it onto my newer laptop which has windows xp on.
I would love to get rid of XP but can't 'cos I use some windows programs for work.
Dual boot I thought, no such luck!
Will not boot from hard drive or cd.
Can get a cursor when using the ACPI getaround choice on boot but don't now what to do with it!
Help menu is coming up but what do I do now?
I dont have a floppy which I think is giving an error message.
I do have built in wifi and a sd card slot.
Any ideas? would loce to run both systems but don't know linux commands to do anything with the cursor that I can get up!!!
Cheers 
Ian

Enter the BIOS and set your cd/dvd drive to "first boot device".

---

### Post by irpayne on 2009-01-28
Sorry, did not make myself clear!

I have installed wubi and got the dual boot menu ok
Windows still boots ok, but ubuntu starts to load but then then hangs.
This is the same as if boot from cd disc.
On the ubuntu boot menu I have tried the various modes ie, verbose , vga, acpi work around etc,
no joy.
When doin acpi workaround choice i have had a cusor appear which allows me to get into help menu and enter commands but thats where I am gettin lost as I dont know what the linux commands are or mean.

May be I should try a different version of ubuntu?
Thanks

---

### Post by abn91c on 2009-01-28
try removing compiz, at the prompt do```
sudo apt-get remove compiz
sudo apt-get remove compiz core
metacity --replace
startx
```

---

### Post by irpayne on 2009-01-29
Thanx, will try that.

In the mean time I also tried an older version of ubuntu and also elive without joy.
Theres something about my hardware i think that linux does not like.

---

