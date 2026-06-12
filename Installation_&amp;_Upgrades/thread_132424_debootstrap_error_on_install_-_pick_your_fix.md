---
title: "debootstrap error on install - pick your fix"
date: 2006-02-18
forum: Installation &amp; Upgrades
---

### Post by najevi on 2006-02-18
The symptoms of this install error have been posted by several people at this forum, just search for "debootstrap error" or "bootstrap.log"

Also bug reports have been filed at **Launchpad**
[https://launchpad.net/distros/ubuntu]("https://launchpad.net/distros/ubuntu")
Just search using keyword "debootstrap"

I grew frustrated looking for a fix so took the time to collate as many suggestions as I could find and post these along with my own learning. So at the risk of the proverbial "*blind leading the blind*" ...

If not for this error I would never have learned about the 4 virtual consoles that are accessible during the install process. Select from among these four consoles by pressing ALT+F1, ALT+F2, etc.

**SYMPTOMS:**
***Console 1: **(ALT+F1)*
[I][FONT=Courier New] The debootstrap program exited with an error (return value 1)
 check target/var/log/bootstrap.log for the details[/FONT]

** Console 2:**[/I] (ALT+F2)
[I](disabled shell - not applicable)

** Console 3:**[/I] (ALT+F3)
[I](varied)
[FONT=Courier New][COLOR=Red]**chroot**[/COLOR]: cannot execute dpkg: No such file or directory
[/FONT][FONT=Courier New][FONT=Verdana]OR[/FONT][/FONT][/I][I][FONT=Courier New]
[/FONT][/I][FONT=Courier New]*[COLOR=Red]** tar**[/COLOR]: ./usr/share/man/man3/Locale ::gettext.3pm.gz :Invalid argument*[/FONT]
[I]OR
[/I][FONT=Courier New][COLOR=Red]**cp**[/COLOR]: read error: Input/output [/FONT][FONT=Courier New]error[/FONT]

* ** Console 4:*** (ALT+F4)
[I](varied)
[FONT=Courier New]base-installer: info: Running /usr/lib/base-installer.d/[COLOR=SeaGreen]**40netcfg**[/COLOR]
init:
[/FONT]
**SEEMINGLY UNRELATED FACTORS:**
partition plan
Install CD - pressed or burned (so long as it passes the integrity check below)


**SUGGESTIONS:**
[/I] At these forums I have read several (and tried just two) suggestions:[LIST=1]
[*][http://www.ubuntuforums.org/showpost.php?p=440481&postcount=16]("http://www.ubuntuforums.org/showpost.php?p=440481&postcount=16")
[quote=Samuli]I had the same debootstrap problem with Kubuntu Breezy when I used finnish language options and keyboard layout.. I got over base-install by **using english language and keyboard**.[/quote]
[*][http://ubuntuforums.org/showpost.php?p=446620&postcount=10]("http://ubuntuforums.org/showpost.php?p=446620&postcount=10")
[quote=taygan]**try enabling dma on your dvd drive** (you can do it from the expert install.. when it gets to **cdrom parameters** type in **-d1** or, get to the console (alt-f3?) during the beginning of the regular setup and type sudo **hdparm -d1 /dev/**hdb (or whatever /dev your dvd drive is.)[/quote]
[*][http://ubuntuforums.org/showpost.php?p=683809&postcount=4]("http://ubuntuforums.org/showpost.php?p=683809&postcount=4")
[quote=rikard_grankvist]... I was trying to install with FAT32 as the file-system on my root partition. Got the same exact error message. I **solved it by using EXT3** instead.[/quote]
[*][http://ubuntuforums.org/showpost.php?p=620606&postcount=3]("http://ubuntuforums.org/showpost.php?p=620606&postcount=3")
[quote=Todd50]I had the same issue... numerous times!!!! 
Finally in desparation ... I used a program called "KILLDISK" and from floppy **overwrote the entire disk using DoD standards** and the install finally went without a hitch. If needed you can get the program from Killdisk.com.[/quote]
[*]and finally there is everyone's favourite piece of advice:
    [I]try reburning your install CD at <some slower> speed! 
[/I] Mind you one individual did take the time to explain *how to verify your CD*:[I]
[http://ubuntuforums.org/showpost.php?p=548266&postcount=2]("http://ubuntuforums.org/showpost.php?p=548266&postcount=2")
    [/I][quote=amohanty]... when you install Ubuntu at the install prompt type:
    [FONT=Courier New]expert[/FONT]
It will offer you a menu. Scroll down to verify install cd (or something to that effect) and do that. Then reboot and install normally.[/quote]
    *The menu item is *"**Check the CD-ROM(s) integrity**"
[*][http://ubuntuforums.org/showpost.php?p=497818&postcount=13]("http://ubuntuforums.org/showpost.php?p=497818&postcount=13")
[quote=Thunderguy]... I had the same problems you did and figured out exactly what is causing them. Our systems have a thing called USB Mouse support, what this really seems to do, is detect USB peripherals and set them up for PS/2. When you turn on the system that numlock state is lit, and something messes up when configuring the keyboard, I believe this is just a simple mis-understanding between the kernel keyboard drivers and the Bios, there is a way you can fix this ... Go into your **BIOS**, it may be under advanced options.. I'm not quite sure,     **Disable** your **USB Mouse support**.
               
 Afterwards you should find the kernel detects the keyboard just fine...[/quote]
I assume this refers to the "Legacy USB Support" BIOS setting. If so then I can't imagine the connection - but it seems to have worked in one case.
[*]any **other **ideas to share?[/LIST]I know that the pressed CD that I am using is good because I successfully installed ubuntu-breezy 7 days ago on the same machine, using the same partition plan. (... yeah! don't ask why.) Also it passed the CD check described at (5) above.

Of the suggestions above the one that seems to have fixed my particular problem was (2) the DMA enable via the 'Expert' option at boot from the install disk. I am not 100% certain that this is the only thing I did to fix it, Now that it 'aint broke' I have no desire to figure out how to break it again and verify the fix.

I *suspect* that there may be some fail-safe hdparm tweaks (*other than, or in addition to* **-d1**) for the cdrom device that will ensure stability of reading data from the CDrom drive during install but that is beyond me to figure out. *FYI*:  [http://www.linux-sxs.org/housekeeping/hdparm.html](http://www.linux-sxs.org/housekeeping/hdparm.html) describes some hdparm options available and the effect they have. *Caution is advised.*


enjoy!

---

### Post by SteveHoffmanUK on 2006-03-06
Nice summary -- thanks for pulling these threads together.

I overcame the problem by using "everyone's favorite piece of advice" -- reburned my Breezy Badger 5.1 install CD after a fresh download.

I did the fresh download because I first tried to just reburn my existing download, but my Nero burning software flagged up an error to do with record lengths (?), so I figured it was safer to redownload. Then I burned the new download at the slowest speed (4x), and all the problems disappeared, including missing libraries and the debootstrap error message. :) :) \\:D/

So I'm up and running and am very impressed by unbuntu. Keep up the good work, guys!

---

### Post by Mustard on 2006-03-22
Nice thread.  I'd love to see more people answering. :)

---

### Post by kinson7 on 2006-04-09
I've just experienced the exact same problem, and my situation has been rather different..well, stupid as well, if you may :P

I tried burning the cd again, I had already checked the md5 of the image file, but I didn't know how to check the CD md5 (yeah, I sound stupid, hahah :P ), so I followed one of the suggestions above and used the installer to check (selecting "expert" mode). I noted that both the cd's failed the integrity check. Since the second CD was burn't at about 8x, I didn't think it was the burning process, so I swtiched to another CD-ROM, and voila ! it worked ! I've just logged in, and hope to start learning about linux soon :)

(I should have noted sooner I suppose, cause that CD had given me problems in the past).

I hope this helps others out there who are having the same problems :)

Btw, hello all, haha!

Kinson.

---

