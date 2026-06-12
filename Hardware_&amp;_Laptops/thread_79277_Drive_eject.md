---
title: "Drive eject"
date: 2005-10-19
forum: Hardware &amp; Laptops
---

### Post by philt80 on 2005-10-19
Might be a real noob question but how do I get my DVD drive to eject on hardware button press instead of software eject?

---

### Post by wellery on 2005-10-19
As far as I know, you can't. The reason the drive is locked is to stop you ejecting it while it's in use. When you eject using the OS it then makes sure that it can safely be ejected.

---

### Post by jdtanner on 2005-10-20
I've noticed that this is a symptom to bug #17607. If I start my laptop up with a cd/dvd in the drive, then I am unable to mount it using the Computer Nautilus interface and I am unable to eject it until I have issued a mount/umount at the command line.

I hate to say it, but I've gone back to Hoary until these little problems are sorted. I'd love to be able to hack about and help out, but I really haven't got a clue when it comes to interfacing with hardware on a driver level :-(

---

### Post by az on 2005-10-20
[QUOTE=philt80]Might be a real noob question but how do I get my DVD drive to eject on hardware button press instead of software eject?[/QUOTE]


Here at work, I can make this Windows2000 (it is up to date) workstation crash by browsing a cd and eject it at the same time.  Data loss, blue screen, freeze, you name it.  

I never push that button unless I am booting and forgot to eject the disk previously.

---

### Post by neighborlee on 2005-10-20
[QUOTE=philt80]Might be a real noob question but how do I get my DVD drive to eject on hardware button press instead of software eject?[/QUOTE]
-----
Yes it can be done.  I will find the link and paste it here in a moment..

EDIT EDIT: The answer is at the bottom of : [http://bugzilla.ubuntu.com/show_bug.cgi?id=11480](http://bugzilla.ubuntu.com/show_bug.cgi?id=11480) 

have fun ;-)

cheers
nl

---

### Post by neighborlee on 2005-10-20
[QUOTE=neighborlee]-----
Yes it can be done.  I will find the link and paste it here in a moment..

EDIT EDIT: The answer is at the bottom of : [http://bugzilla.ubuntu.com/show_bug.cgi?id=11480](http://bugzilla.ubuntu.com/show_bug.cgi?id=11480) 

have fun ;-)

cheers
nl[/QUOTE]

or not..well doesn't that just bite..thats what I get for taking the word of someone on a bug list LOL

OH WELL..im  sure it will get ironed out ;-)

if suse, mandrake, xandros and linspire can do it you'd think the almight debian team could too ?

cheers
nl

---

### Post by neighborlee on 2005-10-20
[QUOTE=neighborlee]or not..well doesn't that just bite..thats what I get for taking the word of someone on a bug list LOL

OH WELL..im  sure it will get ironed out ;-)

if suse, mandrake, xandros and linspire can do it you'd think the almight debian team could too ?

cheers
nl[/QUOTE]

WELL the dain board system is borked it seems and wont let me 'edit' my message atm...keeps complaining that I n eed to edit message with 'one' more character..

anyway it DOES work afterall..one just must reboot sysetm ( Ctrl-alt-backspace  is not enough)..

;-)
cheers
nl

---

