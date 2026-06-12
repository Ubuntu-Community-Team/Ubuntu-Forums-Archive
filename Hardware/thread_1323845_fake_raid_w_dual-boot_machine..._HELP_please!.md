---
title: "fake raid w/ dual-boot machine... HELP please!"
date: 2009-11-12
forum: Hardware
---

### Post by Perturbed Penguin on 2009-11-12
Hey I am just looking to set up my family's new computer over this holiday season and I am curious if anyone has some advice on how to setup a firmware/driver raid (raid using the integrated 'raid' feature of a motherboard) to work with both Ubuntu and Windows on a dual-boot machine. I am currently planning on dual-booting Ubuntu 9.10 and Win7 but the Windows version can change if that happens to make things easier in any way. I would like my two WD Caviar Black TB drives to show up as a single raid1 drive in both OSs. I read up on this last year a bit and it sounded like a pain but if anyone has any suggestions it would be greatly appreciated!!

---

### Post by Perturbed Penguin on 2009-11-13
bump

---

### Post by viper250 on 2009-11-13
settting up raid using the mobo feature is done thru the bios program 
usually on boot you should see the raid configuration program prompt message. For example for a scsi raid card the message would be press ctrl, m to configure raid
my guess your drives are sata drives so the procedure would be in bios. The type of raid configuration you are looking for should be called a mega raid.
This would show the drives as 1 massive drive,
this is an actual raid configuration. the other option would be to use a software raid (fake raid) program to configure your raid. this process in effect uses a config file that fools the OS into thinking it has just one big drive.
This information can be found in the mobo manual or on the manufacturers web site 
If your mobo has a raid feature it is an actual hardware raid and although it may be a little more dificult to set up, it far more reliable than a software raid. 30 years in computer repair and a coffee cup the size of a swimming pool!!:shock:  hope this helps:)

---

### Post by Perturbed Penguin on 2009-11-13
Hmm, interesting. I setup a raid system recently with a Gigabyte board(I have the same mobo model for the new comp) for Win XP and had to install(with floppies I might add ](*,)) a raid driver during th OS setup. My understanding is that these drivers are supposed to tell the OS to view the two drives as a single raid1 drive. If this is the case it would mean that the OS has to do something to to setup the raid system - aka the bios don't report the two drives as a single drive as you suggest. I really wish the bios worked that way, it would make things a LOT easier but as far as I am aware that is unfortunately not the case at least not on my machine. Btw I understand that A true hardware raid system would be a better choice for many reasons but it is MUCH more expensive to buy a raid card than to just use the integrated mobo 'raid' feature whatever that is called. Like you said though I DON'T want to use software raid if at all possible.

Also just to clarify I am looking to use raid1 for backup NOT striped. A quick look at Wikipedia also suggests that what I am describing is firmware/driver raid and not hardware or 'fake'(software) raid as I had referred to it as earlier... I have gone back and changed that in the first post now as well as mentioned raid1 just to clarify what I meant.

Thank you very much for your reply! Do you have any other ideas or are you familiar with Gigabytes' mobo raid implementation?

[http://en.wikipedia.org/wiki/RAID](http://en.wikipedia.org/wiki/RAID)

---

### Post by Perturbed Penguin on 2009-11-15
Bump

---

### Post by Perturbed Penguin on 2009-11-17
Hey, is there anyone out there who has ANY idea as to what I can do?

---

### Post by Ahadiel on 2009-11-17
I also have a Gigabyte board and am using RAID0 happily.

IIRC, you should not need to install any raid drivers if you have a hardware raid since your raid card/mobo takes care of all the raid stuff.

I just went into my BIOS, changed SATA to RAID, setup my drives via the provided interface, and voila.

---

### Post by dawnlove on 2009-11-17
I use suse 11 on my false raid box. It a hard row to hoe in debian although I do believe It can be done if you google it.

---

### Post by Perturbed Penguin on 2009-11-18
Ok, that has been my impression... that it is possible but not at all easy. Looks like I just have a lot of web searching to do! Although I doubt it is quite what I am looking for I will look into that raid setting in the bios and see if that could work Ahadiel. Thanks guys. Btw, 'thanks' button? If there is one on this forum I wouldn't mind knowing where it is! Thanks again! ;)

---

### Post by Perturbed Penguin on 2009-12-13
Alright I will resurrect this thread once more just to be certain there is no easy way to get raid working in Ubuntu before I go ahead and begin setting up the new comp. ...BUMP ;)

On a side note does anyone know, if I were to use openSuse instead, if I set it up w/ Gnome instead of KDE this will not affect its raid/networking abilities will it? Just logically speaking, if not, then is there any reason I can't install the same packages on Ubuntu using a non .deb format and make Ubuntu work just as well as Suse seems to work for this purpose?

---

### Post by Perturbed Penguin on 2010-01-07
Just an update: Unfortunately I have not been able to find any solution to this problem. I could probably get it to work if I were to use a different distro such as Suse but since it is not necessary for me to have Linux on this machine I decided to go with only Windows this time 'round. I would love it if the Ubuntu devs would add easy to access support for motherboard raid systems, perhaps have it as an option in the initial install? Anyways, thanks for the replies! ;)

---

### Post by Perturbed Penguin on 2010-01-10
For anyone who stumbles upon this thread it appears as though there is an option to set up a software raid using the alternate install disk - I am unsure how easy it is, what you have to do or how well this software raid works but the option is in the alternate install disk so if you are looking to use raid on Ubuntu I would start there.

---

