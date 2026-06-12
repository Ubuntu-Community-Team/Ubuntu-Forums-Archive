---
title: "Install Plustek 9636T scanner"
date: 2005-12-26
forum: Hardware &amp; Laptops
---

### Post by getglenn on 2005-12-26
i'm trying to install the above scanner but need some help as follows:...

[INDENT][/INDENT]i have downloaded/extracted the file: plustek-pp-0.43-8.tar.gz

as i understand the man info, i have to...

[LIST=1]
[*]create a .conf file
[*]move that file to the correct location
[/LIST]

i am assuming the correct location to be

[INDENT]/usr/local/etc/sane.d/ [as per man page][/INDENT]

but am not certain... there are many other files in the extracted folders, too, but i can find no explanation what they are for???

i'm also unclear as to how to activate the scanner once the file is in place... the man pages seems to assume the user has a level of expertise i don't have, despite reading the relevant SANE and plustek driver web pages...

regards glenn

---

### Post by getglenn on 2006-01-20
c'mon guys, please!!
some one else must use this scanner with Ubuntu/Linux...

i have read and re read the man pages and any other relevant info i could find...

and I still don't get it!!

i know i could buy a newer usb scanner, BUT this one still works well, even in Windows XP

this has become a real challenge, now, as i cannot believe

a) that it should be so difficult
b) i am that stupid, i can't follow explicit instructions

---

### Post by blueskye on 2006-01-21
Hi, getglenn ... I am brand new to Ubuntu also ... just loaded it this morning. And I am also trying to learn how to get my Visioneer 9420 scanner working. If I was sitting in your chair, I would try moving the file specified to the folder specified and leave all the other stuff where it is for the moment. Then I would look for a program that used scanners ... I don't even know if I have anything that uses scanners ... but would try to get it to scan for the scanner. If it didn't find it, I would then move the other files into the folder where I moved the specified file and see if that worked. But what do I know ... absolutely nothing!!

I am out here in the dark right along with you ... good luck to us both!!

... blueskye ...

---

### Post by sebauribe on 2006-07-31
I'm ussing Dapper.
(in root mode or with sudo)
1) chmod 666 /dev/parport0
2) edit the file: /etc/sane.d/dll.conf
Uncomment the line "plustek_pp"
3) run xsane

---

