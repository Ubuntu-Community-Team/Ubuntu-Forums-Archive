---
title: "I/O ERROR when copying 80gig file from ubuntu ibex"
date: 2009-04-24
forum: Installation &amp; Upgrades
---

### Post by BlazeXI on 2009-04-24
Hello...

I am experiencing an i/o Error when coying a 80gig file from the local drive to an external storage (usb) on ubuntu ibex...

I have tried a normal copy past from nautilus and i have also tried from the terminal using  the commad "cp" .

I have noticed that the copy always falls over at about 24 - 28 gig completed.

could anyone please assist with this :confused:

thanking you in advance.

---

### Post by Slim Odds on 2009-04-24
try ddrescue

---

### Post by BlazeXI on 2009-04-24
ok ..will try this just now ...jusy doing a apt-get install ddrescue ...lol

---

### Post by BlazeXI on 2009-04-24
i dont think ddrescue is going to help me as i dont have to recovery any data ...the data i want to cpy is fine (80gig WORTH) all i want to do is copy the data to another location...when doing this i experiance an I/O error .. ???

---

### Post by BlazeXI on 2009-05-29
Hello ...

i resolved this ....I pulled out my harddrive from my laptop and connected it to a sata to mini usb casing and connected the hard drive to my bro's fedora machine ...

yips and guess what on fedora we managed to copy the 80-gig file to his local machine no problems ......then i ripped open my 1 year old seagate freeagent drive took the harddrive put it into my laptop...reinstalled ubuntu 9.04 ....recovered all apps and stuff.... then copied 80 gig file to my laptop.


all done ...all cool ;)

get you thinking hey ....:-$

---

### Post by orange-wedge on 2009-05-29
is the usb drive formatted for fat?  b/c fat can't handle files over 4GB...

---

### Post by Mark Phelps on 2009-05-29
> **orange-wedge said:**
> is the usb drive formatted for fat?  b/c fat can't handle files over 4GB...

Did you even READ the OP post?  He said it fails in the 24-28GB range (of a single 80GB file) --  so obiously, he's copied over 4GB alread!

---

