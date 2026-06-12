---
title: "Grub loads before boot CD"
date: 2007-08-04
forum: Hardware &amp; Laptops
---

### Post by jsorc on 2007-08-04
Hello,

I have had ubuntu up and running fine on my Toshiba laptop for a while (model M45-s165) but recently, i have attempted to boot from a kubuntu live cd to try out KDE. However, when i try to boot from cd, grub is loaded before the cd has a chance to boot. I have adjusted the boot priority correctly in BIOS and have tried pressing F12 and selecting boot from cd but it still will not work. The cd boots fine in my other pc but i cant get any cd to boot on the laptop (i have tried several including a legitimate windows disc) -- it just goes straight to grub. In addition, i have tried to use SBM but get the "Disk error! 0xAA"... Has anyone else had this problem or have any suggestions? I dont mind if i have to wipe the entire drive -- i just want to be able to use my laptop! Thanks!

---

### Post by buzzmandt on 2007-08-04
sounds like a bad burn... have you tried this cd on another computer?
and did you burn it at the slowest speed available?

---

### Post by jsorc on 2007-08-04
yes, I have tried the disc on my other pc and it works just fine. I even tried using a pressed windows disc in it with the same result. I have no clue why it would be doing this. It boots from the cd just fine if i take the hard drive out but that wont solve anything ;)

---

### Post by lisati on 2007-08-04
> **jsorc said:**
> yes, I have tried the disc on my other pc and it works just fine. 

Some PCs seem to have more trouble with CDs than others - my old WIN98SE machine doesn't like the Ubuntu disks but is happy with most of the other CDs I have.

You might want to select the "Check CD integrity" option from your other PC, and let us know how you get on.

---

### Post by jsorc on 2007-08-04
I have checked the integrity and checked the md5 sum and they seem to match up just fine. I suspect it is a hardware issue but I do not know what it could be. The laptop will not boot ANY cd so I do not think it is the ubuntu disc in particular. It just seems like grub loads up before the cd drive gets a chance...

---

### Post by phidia on 2007-08-04
Never mind all of the paragraphs below this one-You need to make sure that in your bios the cd-rom is _the first boot device_ if you place it after the HD in boot order the computer always boots the hard drive-if there is no disc in the cd-rom drive then it boots the HD.

Except for the fact you have ubuntu on the laptop i would have asked if it even supports booting from cd-rom. What happens when you are booted into ubuntu and you insert a cd or any type (data,music, install) into the drive? I'm thinking that the drive may have gone bad.

> It boots from the cd just fine if i take the hard drive out but that wont solve anything

This is a clue it seems-sorry I missed that on my first read through. Something is going on in bios I believe you need to try adjusting your boot parameters again. Does the bios show the cd-rom as a boot device when it is also recognizing the hard drive?

---

### Post by jsorc on 2007-08-06
> What happens when you are booted into ubuntu and you insert a cd or any type (data,music, install) into the drive? 
The drive seems to work fine when im booted into ubuntu so I dont know that it is an issue with the drive itself. 

> Does the bios show the cd-rom as a boot device when it is also recognizing the hard drive?
In the bios I set it as the first boot device. I have it set to CD Drive, Removable, Realtek Boot Manager, HDD in that order but it still seems to jump straight to grub... 

The laptop unfortunately does not show much info during POST... just a toshiba splash screen with a progress bar and then goes right to grub (or the ubuntu live cd bootup process if the HD is out). I cant seem to find any way to get a verbose POST. I'm pretty sure i have the most recent bios but ill check that next and post back

---

### Post by jsorc on 2007-08-07
Ugh... Well I think i found the problem... It appears that the previous owner of the laptop (it is a hand-me-down) updated the bios to the wrong version. It is supposed to be phoenix bios 1.50 but it has 1.60 installed. I am pretty sure this is what is causing my grief. If I attempt to "downgrade" back to 1.50 with the bios I downloaded from toshibas site I get a "version mismatch" error and have to quit the flashing app.

Is there any way to downgrade the bios? or am i stuck with taking out the drive and working with it from a different computer?

---

### Post by gibbsnich on 2007-10-11
Hey everybody,

I do have the same problem* and wanted to know if you found any way - other than removing the harddisk and putting it in another pc - to boot from cd. 
What's really strange is that obviously it worked just fine the other day when I installed Ubuntu... I did not change anything on that laptop - no bios update, no hardware changes. I don't know enough about how a BIOS works but I'm sure it shouldn't depend on having the Windows XP bootloader in MBR to boot a cd, should or even could it? So having grub installed shouldn't be the problem, but it's the only thing I changed.. You see I'm really lost :-(

Thanks in advance for any reply!

Yours, Michael


* Toshiba A 100-512, Phoenix BIOS *v1.5*, which had Windows XP installed but which I removed and installed Ubuntu 7.04 on. Now I cannot boot from any DVD/CD (althought they seem to play nice with other pcs), even though I changed the BIOS-settings (F2) to boot from CD-ROM drive first. Selecting the CD-ROM drive from the "Boot Menu" (which you can enter with pressing F12) changes nothing: The laptop still boots grub from the first harddisk.. Obviously it worked just fine the other day when I installed Ubuntu...

---

### Post by gibbsnich on 2007-10-11
So I searched the Internet and suprise, suprise: Changing the boot order (via F2) or directly selecting the boot device (via F12) is supposed *not* to work. The correct way to boot from cdrom/dvd is to press the 'C'-key directly after turning on power ;-) Who would have guessed!?
See: [http://www.csd.toshiba.com/cgi-bin/tais/su/su_sc_dtlView.jsp?soid=403623&moid=1073769771](http://www.csd.toshiba.com/cgi-bin/tais/su/su_sc_dtlView.jsp?soid=403623&moid=1073769771)

HTH!

Michael

---

