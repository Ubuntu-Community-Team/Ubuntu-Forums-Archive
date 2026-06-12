---
title: "Ubuntu on Old PC"
date: 2005-09-06
forum: Hardware &amp; Laptops
---

### Post by cas194 on 2005-09-06
I installed ubuntu in a couple of spare partitions on a relatively modern notebook wthout any difficulty. However, I have been trying for days to get it to install on an old Intel Pentium I with an AMIBIOS dated 1996. (I've tried to update the BIOS, but the version is not recognised by the on-line update routine.)

SmartBootManager fails to recognise the CD-ROM drive, so I turned to Loadlin. This leads to:

"Uncompressing Linux.." followed immediately by "invalid compressed format (err=2)"
"System halted_"

Can anyone offer any suggestions?

CAS

---

### Post by mcduck on 2005-09-06
I'd say that your wasting your time..
No Pentium 1 would not be fast enough for ubuntu.. Even if you'd succeed with install I doubt that it would be usable. For hardware that old you'd need some _very_ light distro..

---

### Post by cas194 on 2005-09-08
[QUOTE=mcduck]I'd say that your wasting your time..
No Pentium 1 would not be fast enough for ubuntu.. Even if you'd succeed with install I doubt that it would be usable. For hardware that old you'd need some _very_ light distro..[/QUOTE]

Weeell, this same machine has, for a long time, been running a whole series of other distributions perfectly satisfactorily (Red Hat, Caldera, Mandrake, etc.) so I'd be interested to learn exactly  why you believe that Ubuntu should have a problem. 

For me, part of the appeal of Linux has been the much-publicised ability  to get satisfactory performance from older equipment. I'm not sure why this should have changed so suddenly.

Any more helpful suggestions? 

CAS

---

### Post by az on 2005-09-08
Loadlin can use a bzipped kernel, I think.  What version of loadlin are you using?

---

### Post by chantal on 2005-09-08
Hi CAS 194,
I ran first Warty then Hoary OK on a Pentium 133MHz (Sys Bus 66MHz) with 128MB of RAM from April 'til July this summer. I needed to write the Smart Boot Manager floppy image from the Ubuntu install cd with rawrite under DOS, and then booting from it, I could select the Install CD. The install took many hours. Afterwards the pc took 5 minutes to boot once all was installed, the time to make a cup of tea!
Perhaps you could change your cd rom drive to a more modern one just for the install. I used a 32x to accelerate the install a bit.

---

### Post by cas194 on 2005-09-09
[QUOTE=azz]Loadlin can use a bzipped kernel, I think.  What version of loadlin are you using?[/QUOTE]

v.1.6 It's a mystery to me how loadlin applied to the same image which installed satisfactorily on another machine should return this bizarre "invalid format" message

CAS

---

### Post by cas194 on 2005-09-09
[QUOTE=chantal]Hi CAS 194,
I ran first Warty then Hoary OK on a Pentium 133MHz (Sys Bus 66MHz) with 128MB of RAM from April 'til July this summer. I needed to write the Smart Boot Manager floppy image from the Ubuntu install cd with rawrite under DOS, and then booting from it, I could select the Install CD. The install took many hours. Afterwards the pc took 5 minutes to boot once all was installed, the time to make a cup of tea!
Perhaps you could change your cd rom drive to a more modern one just for the install. I used a 32x to accelerate the install a bit.[/QUOTE]

Thanks for that. Unfortunately, having used rawrite under DOS to create a boot floppy, the CD was not recognised, so I couldn't boot from it. As you suggest, I shall next try substituting more recent  CD drives from my other machines.

I've tried everything I could think of, but so far I can get Ubuntu to run only on fairly modern equipment. A pity, since it seems to be an excellent distro, and I've always relied on Linux to extend the life of my older machines.

Ho, hum. I shall just have to try something else.... 

CAS

---

### Post by cas194 on 2005-09-09
[QUOTE=mcduck]I'd say that your wasting your time..
No Pentium 1 would not be fast enough for ubuntu.. Even if you'd succeed with install I doubt that it would be usable. For hardware that old you'd need some _very_ light distro..[/QUOTE]

Since I started working on UNIX machines around 1984, I've lost track of the number of times I've been told that I'm "wasting my time". Somehow, it has never seemed that way to me.....

CAS

---

### Post by riktzvet on 2006-01-26
I have just gotten this error "Uncompressing Linux.. invalid compressed format (err=2) System halted_" on a machine that has been running Breezy just fine for quite awhile. It has been rebooted several times since the latest updates with no problem.

Any ideas?

---

### Post by Thulemanden on 2006-01-26
Well, you know, the world moves on. We can't stop the development because 0,001% runs antique equipment.

Ubuntu for punchcards?

---

### Post by riktzvet on 2006-01-27
It's responses like yours thulemanden that cause dissent on forums and discourage new members from posting. I need help with a problem not an off comment.

I am running Ubuntu on a PIII 550 with 512 ram. Not really that old is it?

---

### Post by chantal on 2006-01-28
I discovered Ubuntu Hoary by trying first on a Pentium 1 133MHz (66MHz system bus) with 128MB ram (~70MB was used just for the desktop) , and now I've been using it for six months on a Dell 400 Pentium 2 333MHz (66MHz bus) with 400MB ram. The Ubuntu forums have been a great help getting everything to work in both cases.
At present on the Dell I have the vsftpd daemon acting as a FTP server, (only with password logon), and I'm working on  PHP 4 with Apache2 and MySQL4.0. With the Epiphany browser, Firestarter and the server daemons running, I'm using 140MB of ram.
This post is to encourage those with an older pc.

---

