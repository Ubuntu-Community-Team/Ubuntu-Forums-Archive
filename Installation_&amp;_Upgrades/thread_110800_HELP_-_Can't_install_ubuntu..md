---
title: "HELP - Can't install ubuntu."
date: 2005-12-31
forum: Installation &amp; Upgrades
---

### Post by makba018 on 2005-12-31
Hello, I can not install ubuntu. I have just got a new computer which only has DOS on it and a copy of windows 98 which has not been installed. I tried installing ubuntu but can not get it going. I burned the ISO file on a disc and put the disc in my CD/DVD drive. When I load up my computer, DOS appears with the C:/> and i press "enter" but nothing happens. How do i install ubuntu? Please send me a message to my email @ [email]mokhtar_akbari@yahoo.ca[/email].

Thank you

---

### Post by Jeff12088 on 2005-12-31
You need to go to your BIOS and set it so the CD drive boots **before** the hardrive.

---

### Post by makba018 on 2005-12-31
Thank you Jeff
How do i get to BIOS?

Mokhtar

---

### Post by Norberg on 2005-12-31
Depending on what bios you have its diffrent but presing delete under boot up work in most case sometimes its F2.

---

### Post by makba018 on 2005-12-31
I got into BIOS and went to boot device priority. I changed the 1st, 2nd, and 3rd boot device to CD-ROM. I restarted the computer. The message was
BOOT DISK FAILURE - INSERT BOOT DISK AND PRESS ENTER.

I guess it is not reading the boot disk.

Any suggestions of changes i can make in BIOS?

Mokhtar

---

### Post by Jeff12088 on 2005-12-31
1st boot device should be Floopy, second boot device should be CDROM, and thrid boot device should be hardrive or C drive.
Make sure you have "no" disks in your floopy drive and make sure the CD is in the drive.
Post any errors that come up.

Also, your CD needs to be burned as an ISO image for it to work. See more: [https://wiki.ubuntu.com/BurningIsoHowto](https://wiki.ubuntu.com/BurningIsoHowto)

---

### Post by makba018 on 2005-12-31
I have done what you have suggested in my BIOS and saved the changes. There is no disk in floppy A: and the priority is set.
1. Floppy A:
2. CD-ROM
3. Hard disk

DOS keeps coming up when i boot with this line: 
C:/>

Any other suggestions?

---

### Post by Jeff12088 on 2005-12-31
I don't know what might be the problem if you have it set like that.
Does the bootup detect your CD drive?
If the boot up can't read the CD, it'll skip it. So make sure you burned your CDs the right way. As said in my previous post, your CD needs to be burned as an ISO image for it to work. See more: [https://wiki.ubuntu.com/BurningIsoHowto](https://wiki.ubuntu.com/BurningIsoHowto)

---

### Post by opensourcerocks on 2005-12-31
Look at files on the cd.
If you only see an iso file on it 
you have burned it wrong.
I have wrecked so many discs without realizing that 
the burning program has to open up the iso file.

---

