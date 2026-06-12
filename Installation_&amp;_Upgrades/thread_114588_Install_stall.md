---
title: "Install stall"
date: 2006-01-08
forum: Installation &amp; Upgrades
---

### Post by s3rial_number on 2006-01-08
hello, this is my second linux install, first was Mandrake, i get just past the base configuration and then it stalls out at 25% while its configuring the step after that, (i don't remember what the step is called)

im using winXP as a main OS but im putting ubuntu on its own HDD 
the hdd is a 80gig SATA.

please help

---

### Post by bikeboy on 2006-01-09
Did you check the md5sum of your iso before burning it to cd?
Another common fix is to try reburning the cd at a slower speed. CD-RW's are good for this as you don't want to waste CD-R's.

---

### Post by s3rial_number on 2006-01-09
[QUOTE=bikeboy]Did you check the md5sum of your iso before burning it to cd?
Another common fix is to try reburning the cd at a slower speed. CD-RW's are good for this as you don't want to waste CD-R's.[/QUOTE]


whats a "md5sum" ?

also will having a serial ATA hdd cause a conflict with the install, my instructor at my tech school seems to think it will in ubuntu.. but since the install doesnt ask for a 3rd party driver, i don't know how i would fix this... aside from switching over to my 200 gig ATA drive..

---

### Post by bikeboy on 2006-01-09
As far as the serial ATA is concerned I believe most people have had no trouble installing to them. I haven't tried it myself but I think if you have an ide hard drive as well the installer can get confused and want to use the ide by default.

An md5sum is a way of checking if two files are identical, therefore verifying that the download of ubuntu worked 100% correctly.
Check this wiki entry, the comments have something on checksums in windows.
[https://wiki.ubuntu.com/BurningIsoHowto](https://wiki.ubuntu.com/BurningIsoHowto)

Hopefully a more experienced user will see your thread and help some more with the multiple hard disk part as I really don't know about that part.

See how you go with checking the md5sum anyway and post back after that.

edit: different link

---

### Post by s3rial_number on 2006-01-10
theres seems to be about 15 files that cant be found in the MD5sum file.. and one that cant be opened.. should i try to re-download it? perhaps from a different source?

i suppose i could just order the cd's and wait like a normal person.

---

### Post by bikeboy on 2006-01-10
Ah yes if it failed the check then you should re-download if that is a viable option for you. Another mirror might be a good idea, then again it might have just been bad luck and the mirror is fine.

Nothing wrong with ordering pressed cd's if you don't mind the wait. 6+ weeks in Australia from what I've been told. A new version of Ubuntu will be released in April too, so you might like to try now with download and order the new one when it is released.

---

### Post by s3rial_number on 2006-01-10
where is the ubuntu offices? im stateside.. so i don't know how long it will take 
to ship them. i might try re-downloading the file later this week, i have broadband at the moment so it shouldn't take very long to get again. thanks for helping!

---

### Post by bikeboy on 2006-01-11
[QUOTE=s3rial_number]where is the ubuntu offices?[/QUOTE]
Sorry I have no idea. Expect it to take at least a couple of weeks though.

>  thanks for helping!
No worries. I'm a fairly new user too so I'm glad to have these forums.

---

### Post by s3rial_number on 2006-01-12
re-downloaded and im using it as i type. this is a beautiful system and it just feels clean. and untouched.. the only problem im having now is my screen resolution is only 1024X768 and i want it up some more.. is there a way to do it?

:confused: :confused:

---

### Post by bikeboy on 2006-01-12
Glad you got it going!

Most likely there is a way to increase resolution but I would need some extra info.
What type of monitor are you using (crt, lcd) and what's its max resolution or the res you normally used before.
Also, what type of video card do you have?

Sounds simple but I must also ask, have you gone to System > Preferences > Screen Resolution? I'm sure you have but there are other ways to fix screen problems if we need to.

---

### Post by s3rial_number on 2006-01-12
my resolution that i used to use was 1280 X 960 or 1280 X 1024 depending on what i was doing.. i have a geforce 6800 PCI-E and i've tried the "screen resolution" option but its capped at 1024 X 768 .. im thinking it could be a driver problem.. but i cant figure out how to decompress the files from nvidia.. (its a .run file) theres still alot i have to learn i guess!

---

### Post by bikeboy on 2006-01-13
This might be what you're after.

[https://wiki.ubuntu.com/BinaryDriverHowto/Nvidia](https://wiki.ubuntu.com/BinaryDriverHowto/Nvidia)

Otherwise a search of these forums will no doubt unveil the nvidia howto.

---

