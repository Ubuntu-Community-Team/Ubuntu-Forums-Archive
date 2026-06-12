---
title: "SATA detection"
date: 2004-11-18
forum: Hardware &amp; Laptops
---

### Post by Hagoromo on 2004-11-18
Hello,

I recently purchased an AMD64 3500+ with
an Asrock K8 Combo-Z motherboard (ULi M1689
chipset).

The installation of 4.10 does not detect my S-ATA
disk (Maxtor 160 Gb).

Any idea?

Thanks in advance,

Hg

---

### Post by Tutur on 2005-08-06
Hello,

I am french and I have bougth exactly the same PC: Atlhon 3500 with a K8 Combo-z motherboard... I have the same problem and for the moment all the message I have posted in France didn't get the solution...  :???: 
I hope we will find the issue here... 
Thank's in advance for the advices.

---

### Post by sto6ma9ch on 2005-08-28
Same thing here.

[INDENT]AMD Athlon 64 3500+ processor
MSI RS480M2-IL microATX motherboard
2GB DDR RAM
2 Western Digital Raptor 74GB 10,000 RPM SATA drives[/INDENT]

Windows XP installed without incident on the first drive. I'd like to install Ubuntu on the second SATA drive, but the installer fails when loading the partitioning utility. This is the error message:

***"No partitionable media was found. Please check that your hard drives are connected."***

I think from what I've Googled, it's down to two causes:

[list]The motherboard's BIOS is not labeling the SATA drives correctly[/list]
[list]The Ubuntu 5.04 installer is loading a kernel without module(s) for SATA support[/list]

A colleague of mine has dual SATA drives and was able to install Ubuntu 5.04 successfully, so I'm inclined to go with the first cause. In either case, I have a support e-mail into MSI, and I'm downloading Breezy Badger - Colony 3.

Anybody been successful installing 5.04 to SATA drives?

---

### Post by sto6ma9ch on 2005-08-28
**UPDATE** 

I just installed Breezy Badger successfully onto my second SATA drive! Both drives were detected by the Ubuntu installer.

For other users with issues installing to these types of drives, try using the ISO's at this link

[http://cdimage.ubuntu.com/releases/breezy/colony-3/](http://cdimage.ubuntu.com/releases/breezy/colony-3/)

---

### Post by JoP on 2005-08-29
Hi!
Same here, I tried Warty with no luck, and Breezy installed smooth as a breeze ( :-# soo easy...), but didn't detect properly my Realtek 8205 based network card, included in Asrock board. Don't know how to make it work (maybe a bit off topic, sorry).

BTW, for Breezy (and other distros) to detect SATA drives I needed to set up SATA RAID in BIOS, even if I had just one drive.

(when you (sto6ma9ch) say WinXP installed without incident you mean it did after passing it Sata drivers from a floppy disquette, don't you? Since I don't have a floppy drive, I can't install XP that way...  ](*,) )

---

### Post by Amol_Karmarkar on 2005-08-29
Hi All,
         I too have the same problem.I have a 64 AMD athlon with ASUS K8Mx mobo and the SATA HDD is not detected. Infact the bios shows my CDROM as primary master.Also, I booted using live CD only to find that my Realtek n/w card is not detected.I installed XP by addind drivers thru floppy disk.Will something similar have to be done here ? Please help.

Thank you,
Amol Karmarkar

---

### Post by sto6ma9ch on 2005-08-29
JoP,

[INDENT]When installing XP, I just took all of the components out of the box (building your own computer is always a learning experience), put the computer together, popped in the XP Media Center Edition 2005 disk, and off it went. I didn't even go into the BIOS before installing XP. To answer your question, nope. I didn't have or need a floppy with SATA drivers.[/INDENT]

Amol_Karmarkar,

[INDENT]My DVD-RW drive shows up as the first IDE device, too. I think it's because my motherboard's BIOS lumps all of the IDE devices together.

Have you tried installing Ubuntu via the "Breezy" install CD? There's one available specifically for AMD64 processors.  :D  sweet. That's what I had to do to get Ubuntu installed on SATA drives. I posted the Colony 3 download link in my earlier post.

Let us know what happens.[/INDENT]

---

### Post by JoP on 2005-08-30
[QUOTE=sto6ma9ch]JoP,

[INDENT]When installing XP, I just took all of the components out of the box (building your own computer is always a learning experience), put the computer together, popped in the XP Media Center Edition 2005 disk, and off it went. I didn't even go into the BIOS before installing XP. To answer your question, nope. I didn't have or need a floppy with SATA drivers.[/INDENT]
[/QUOTE]

Yeah, so XP Media Center works with SATA... that's something good to know, thanks. XP Professional and Home ed. don't. They need the disquette with sata drivers (I'd like to know why they don''t let you choose the cd player as driver storage  :? )

Anyway, since I can't buy Media Center here (in spanish, I mean) until it is realeased, I can't test it.
BTW, I built my computer too (and many others, I've got a comp. store... ;-) ), it is actually a Media Center computer, so I'm trying to get everything working in Ubuntu, and I rather use Hoary, since I wouldn't like to sell a Pc with Breezy beta installed (not that it doesn't work nice, it does, but it's still a beta... I'm testing it too, anyway).
Breezy 64 works great with my Athlon 64.

---

### Post by JoP on 2005-08-30
[QUOTE=Amol_Karmarkar]Hi All,
         I too have the same problem.I have a 64 AMD athlon with ASUS K8Mx mobo and the SATA HDD is not detected. Infact the bios shows my CDROM as primary master.Also, I booted using live CD only to find that my Realtek n/w card is not detected.I installed XP by addind drivers thru floppy disk.Will something similar have to be done here ? Please help.
[/QUOTE]

Did you activate SATA Raid in BIOS? That way it worked for me, with every distro, but Hoary  :? . Breezy worked too. I still haven't found a way to get Hoary detect SATA, but I recall having read it worked on some mobos. Is that possible?
Which chip is your realtek net card using?

---

### Post by trunkd on 2005-09-09
I had the same issue on a Dell SX280 with a partitioned SATA drive.  In the BIOS on this machine, there is an option under "Drives" where you can set the SATA to either "Normal" or "Combination".  Choose "Normal" for the Hoary distro.
Hope this helps.

---

### Post by netneo on 2005-09-17
Hi everyone

Even i seem to facing the same problem with SATA drive

My system is:
Processor---->AMD Athlon A64 3000+ having Socket 939
Motherboard----->MSI RS480 with ATI x300 Onboard gfx
Ram------>512 Mb DDR
Hard Disk----->Samsung 80 Gb SATA

I had installed WinXp with NTFS and 3 partitions of sizes 29.2,29.2 and 15.9 gb respectively

Has anyone tried out what Trunkd has suggested?

Will it work for our systems as well?

If u dont mind Trunkd..could u guide me as to what i should be doing without my WinXP getting affected?

This wont affect the GRUB loader will it?

Did u face any problems with Hoary 5.04 after that?

Thank you

---

