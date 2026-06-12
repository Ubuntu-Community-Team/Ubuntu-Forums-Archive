---
title: "Intall CD Boot Record Not found"
date: 2006-01-01
forum: Installation &amp; Upgrades
---

### Post by jazee on 2006-01-01
I keep having problems getting my machine to load the boot record from the cd.

I get this error:

Searching for Boot Record from CDROM..Not Found

I have burned 3 diffrent copys of the install cd. Using nero to burn the ISO image to the disc(Not as a Data CD, but as a cd from Image file). All 3 attemps it will not see the boot recored on the cd. I can check the cd in explorer and I see all the files on the disc. I'm using the ubuntu-5.10-intall-i386.iso file for my image and I downloaded it from on official mirror.

The install computer does reconize boot records from other cds. Check using my fedora core 4 cd and windows xp/2003 server cds.

I did do a serch in the forums in hopes that I chould find a solution but no luck.

---

### Post by rjwood on 2006-01-01
you are rebooting after you put the cd in--right??

---

### Post by Omnios on 2006-01-01
How many CDs do you have and which one is set for boot in the biosy, I had a similar prob before where I set the wrong cd. Other than that it may be a bad burn wich can be solved by burning at a lower speed personly I use a large CD-RWable to burn my images on at either 2X or 4X and found higher speeds lead to a lot of bad burns

---

### Post by jazee on 2006-01-01
Yes I'm restarting the machince after inserting the disk.

I have 1 cdrom drive set to be the first boot device fallowed by the Hardrive wich has nothing on it. I'm using 700mb CD-R's and I have tryed burns at 48x and 16x. I'll try one at a 2x and see if that might help but not sure.

---

### Post by jazee on 2006-01-01
So I burned one at 4x the lowest speed I chould do and still nothing.

---

### Post by Some_Body on 2006-01-01
Hm, if you burned the cd properly, your bios should be detecting it. I'll go through the process of entering installation step by step, so you can make sure you've done everything properly.

**Burning**
I'll assume you're using nero since you said you had it.

1)Open nero (obviously)
2)Move your mouse over copy and backup, and click on burn image. Nero should reload, and a file browser will appear.
3)Move to where you can select the file type to browse for, and select "all files".Then, click on the file you installed.
4)Set the writing speed to 4x. 
5)Click on next to burn the cd. It should start the burning process. Hehe, burn. The Roman emperor nero burned people on the stake...I love the creators of nero just for the name :)
6)When the burn process is complete, press next and your cd should eject.

**The Bios**
1)Insert the ubuntu installation disk you have created, and enter the bios (basic input output system) of your computer. How you do it is dependant on which bios/computer brand you have. It is typically done by pressing f10, the delete key (del), or ctrl+alt+esc when the computer first starts up.
2)Change the boot device order. This is usually found under Cmos settings. Set it to boot in this order: Floppy>cd-rom>ide0 (your hard drive). If you can  not configure cmos settings in your bios, then browse around until you find an area where you can change the order in which your computer boots (do not alter anything else). If you still cannot find an area to change the boot device order, then this step was unnecessary, as it does that by default.
3)Restart the computer.
4)Enter installation. Congratulations, you will now get to enjoy a wonderful osx with excellent tech support!

Oh, and if you have a network card, you may have to install the drivers with [ndiswrapper](ndiswrapper.sourceforge.net). If you have trouble with ndiswrapper, look at [the wiki](http://ndiswrapper.sourceforge.net/mediawiki/index.php/Main_Page) for assistance. Hope I've helped :)

---

### Post by jazee on 2006-01-01
Ok I dubble checked your list and I was doing everything right. But I thought for S***s and giggles I would try to burn it on another computer and diffrent program still didn't work. So I thought hey why not try to boot it on another computer and check to see if it was me burning the cd wrong. Well it wasn't the cds burning wrong becuase all 5 of the diffrent copies that I made worked. So now I'm pissed.

So with that said you guys got any ideas why my other computer will not see the boot record on the cd. The bios seems to be set currectly becuase it is checking the cd for a boot record.

---

### Post by jazee on 2006-01-02
Ok It now seems to be working. I went threw and redid all the harware and redid the bios and now it seems to notice the boot record. I thank you guys for all your help and ideas.

---

### Post by digitaltodd on 2006-03-30
I am having the same problem. I have actual Ubuntu Install CD's and I cannot get the system to recognize them. Could you shed some light on what you did to correct this problem. I have been through the BIOS setup several times making changes. I am getting no where. It recognized the disk before I installed Win2000Pro, which I installed first becasue I understand that it needs to be first then Ubuntu gets installed and the Grub Bootloader takes care of the dual boot, at least thats how it worked on the WinXP system I did last month. I am super frustrated now becasue I can't understand what has changed in the BIOS that would not recognize the Ubuntu installer.

---

### Post by jazee on 2006-03-30
i managed to get it to work by reseating everything but the CPU. Don't know why it worked but it did.

---

