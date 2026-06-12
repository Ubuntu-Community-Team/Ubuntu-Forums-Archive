---
title: "Problems on installing GRUB"
date: 2005-03-27
forum: Hardware &amp; Laptops
---

### Post by Firli on 2005-03-27
Hi, I'm trying to install ubuntu at a friend's computer, but it always seems to crash during GRUB installation at 50%.
Don't know if it could have anything to do with the fact it for some reason recognises the HDD as sda instead of hda during partitioning. Because the GRUB crashes while: 'installing on hd0'. I've already tried to select the option during partitioning where it says it will install the GRUB on the partition instead of in the master boot record. It still tries to install on hd0 and crashes.
Any suggestions?

---

### Post by clb137 on 2005-03-27
HI,

Can you give me more info on the specs of the PC your trying to install the software on?  Also have you any other operating systems installed

thanks


clinton

---

### Post by tjz on 2005-04-11
I have the exact same problem, when installing warty or hoary. Funny enough I was able to install ubuntu on the exact same pc some months ago. 

I want to go back to ubuntu, so some help would be great!!!

---

### Post by Firli on 2005-04-11
Whoops sorry for the late reply, but it was kind of a hassle getting the specs (I don't see the friend every day and worse, I can't open up the pc). Screenshots of device lists :P.
[http://gmail.google.com/gmail?view=att&disp=inline&attid=0.1&th=1032b86d6602fa89](http://gmail.google.com/gmail?view=att&disp=inline&attid=0.1&th=1032b86d6602fa89)
[http://gmail.google.com/gmail?view=att&disp=inline&attid=0.2&th=1032b86d6602fa89](http://gmail.google.com/gmail?view=att&disp=inline&attid=0.2&th=1032b86d6602fa89)
[http://gmail.google.com/gmail?view=att&disp=inline&attid=0.3&th=1032b86d6602fa89](http://gmail.google.com/gmail?view=att&disp=inline&attid=0.3&th=1032b86d6602fa89)
(if these links don't work, please tell me so :)).

Anyway, other weird thingie of the pc. It seems they have some weird system of hdd's. All normal maxtor hdd's, but completely seperated through hardware, I mean, to get to another hdd, they have to shut down the pc, and turn a switch (switch cannot be turned while pc is on). Don't know how this works on the inside as I'm not allowed to open it up. Anyway, installing windows on seems to give no problems, actually, it's only the GRUB that gives problems (I'm guessing it has trouble detecting the hdd properly). Anyway, just to stay ahead :P, this is not a raid-system or anything... it's erm.. a hand-made system by their uncle :roll:.

Now, I could try out some stuff, but I don't know how to configure the GRUB during install (it just starts automatically, I want to point to where to install myself :P).

About other operating systems... windows for the time being, pc needs to work :P.

---

### Post by clb137 on 2005-05-25
[QUOTE=Firli]Whoops sorry for the late reply, but it was kind of a hassle getting the specs (I don't see the friend every day and worse, I can't open up the pc). Screenshots of device lists :P.
[http://gmail.google.com/gmail?view=att&disp=inline&attid=0.1&th=1032b86d6602fa89](http://gmail.google.com/gmail?view=att&disp=inline&attid=0.1&th=1032b86d6602fa89)
[http://gmail.google.com/gmail?view=att&disp=inline&attid=0.2&th=1032b86d6602fa89](http://gmail.google.com/gmail?view=att&disp=inline&attid=0.2&th=1032b86d6602fa89)
[http://gmail.google.com/gmail?view=att&disp=inline&attid=0.3&th=1032b86d6602fa89](http://gmail.google.com/gmail?view=att&disp=inline&attid=0.3&th=1032b86d6602fa89)
(if these links don't work, please tell me so :)).

Anyway, other weird thingie of the pc. It seems they have some weird system of hdd's. All normal maxtor hdd's, but completely seperated through hardware, I mean, to get to another hdd, they have to shut down the pc, and turn a switch (switch cannot be turned while pc is on). Don't know how this works on the inside as I'm not allowed to open it up. Anyway, installing windows on seems to give no problems, actually, it's only the GRUB that gives problems (I'm guessing it has trouble detecting the hdd properly). Anyway, just to stay ahead :P, this is not a raid-system or anything... it's erm.. a hand-made system by their uncle :roll:.

Now, I could try out some stuff, but I don't know how to configure the GRUB during install (it just starts automatically, I want to point to where to install myself :P).

About other operating systems... windows for the time being, pc needs to work :P.[/QUOTE]

1. I cannot see you file i do not have a googl account,

2. u said install grub on HDD,    Grub HAS to be installed on HDA it does not matter which operating system resides on HDA, but in order to boot 'Grub' MUST be installed there.  

3. The drive where linux is loaded MUST be 'startable' / Bootable ( you can set these options during the install



clinton

---

### Post by Firli on 2005-07-02
Sorry for being unclear. I meant hdd as hard-disk-drive. The problem is, the installer crashes when installing the GRUB. I've also noticed during formatting, that he only seems to find a harddisk named sda, as if it's an usb-disk. It doesn't get detected as hda (though there is only one accessible disk present.

Sorry for the pics, here they are again :)
[[IMG]http://img244.imageshack.us/img244/286/screenshot11kh.th.jpg[/IMG]](http://img244.imageshack.us/my.php?image=screenshot11kh.jpg)

[[IMG]http://img244.imageshack.us/img244/472/screenshot20rw.th.jpg[/IMG]](http://img244.imageshack.us/my.php?image=screenshot20rw.jpg)

[[IMG]http://img244.imageshack.us/img244/3482/screenshot37tx.th.jpg[/IMG]](http://img244.imageshack.us/my.php?image=screenshot37tx.jpg)

---

### Post by Fluffy, the jolly sheep on 2005-07-02
It seems the hard drive gets correctly recognized. A /dev/sda drive isn't necessarily a usb drive, it can also be a S-ATA or SCSI drive. GRUB normally uses hd0 for the primary drive regardless of whether it's a /dev/hd* or /dev/sd* one. The problem seems to be something else. Probably those damn squirrels again. Always jumping around in trees and causing problems. I blame them! :mad: 
Maybe someone in here knows about a way to get a more detailed error report of the grub installation?

---

