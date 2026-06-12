---
title: "HP PSC 1315 Blank pages only."
date: 2007-03-06
forum: Hardware &amp; Laptops
---

### Post by P4VV37 on 2007-03-06
I've got Ubuntu 6.10 and hp psc 1315 printer. I've already installed drivers from hp but printer doesn't print anything. When i press "print" printer only gives me blank page, without any ink on it. What's wrong and how can i repare it? Printer is printing on MS Windows.

Sorry for my eanglish, I don't speak it very well. If i've done any mistakes in the text please corret me.

---

### Post by P4VV37 on 2007-03-08
Can anyone help me?

---

### Post by Jeffrey Barnes on 2007-03-15
I had that problem also.... It happens when you reinstalled the driver for that printer. If you dont have important files in your PC try to format your harddisk and install your printer, remember that you should not connect the USB printer until the installer prompt you to do so. Correct me if im wrong guys... but I did that in my PC and it works

---

### Post by ramjet_1953 on 2007-03-16
I have a psc 1350 and all I did was this:

Click:   System>Administration>Printing

A window opens. Double click on add new printer.

If your printer is plugged into your PC and is powered-up, it should auto detect it.

Then just choose all of the default options. You do not need to download, or install any drivers, it will do it automatically and also install HPLIP, which has the driver needed and gives you good control over the printer, even indicating ink levels.

Regards,
Roger :cool:

---

### Post by P4VV37 on 2007-03-17
I've allready fix this problem. I've found this: [http://ubuntuforums.org/showthread.php?p=1264009I've allready fix this problem. I've found]("http://http://ubuntuforums.org/showthread.php?p=1264009I've allready fix this problem. I've found")

---

### Post by protasio on 2007-06-16
hi,

i've a psc 1315 and have the same problem, tried to change to the latest drivers, reinstalled ubuntu, but always the same...

I install the printer, all well detected and correct, but when i try to print something only comes white pages... in Windows it prints fine, so it's not the lack of ink ;)

you said you found the solution but our link is not very good, even after i fixed it ot leads to something nothing to do with printer issues... so can you or someone else help me?

---

### Post by BruisedQuasar07 on 2007-07-23
I had the same problem with my HP PSC 1315 all-in-one printer. The Unbuntu installed CUPS program recommended 1310 series setup. The 1315 is 1310 series but no matter what I tried, I got only light 
yellow printing. I finally guessed that the printer USB being plugged into a USB hub may be the
problem. It was. 

I went to System > Administration > Printing , after I rebooted with my printer connected DIRECTLY to a PC USB port. I "removed" the 1310 icon and clicked "new printer". I kept all the CUPS recommended settings. I now have black printing. I do not know yet if I will get color printing. The HP psc1310 series driver in CUPS is inadequate for the 1315 models but you can get good black printing. 

BRUISED

---

### Post by itsbradman on 2007-07-28
I am having the same problem with an HP 3740.  Ubuntu recognizes it immediately.  The printer head moves and all, but only a blank page comes out.  The printer works fine in windows.  Help!!

---

### Post by BruisedQuasar07 on 2007-08-14
I know it may sound weird but shifting to Linux reminds me of the earlier days of the personal or desk computer when there was competition in O/S and software and hardware. 

Radio Shack and a few medium main frame computing companies were major players then. IBM PCs and IBM clones were business PCs, so I stuck with Commodore C-64, then C-128D. Back then, when a PC booted and was ready to go users saw only a cursor. If you had a menu, you probably made it yourself.

There was no MAC or Windows desktop and hardware had dipswitches that had to be set just so for them to work in your IBM clone. 

There were no books and the magazines offered little practical information. They were mostly thinly disguised cheer leaders for their top advertisers. Hard as this may be to believe today, the top four magazines had people bamboozeled into thinking Gateway was the best PC there was. Gateway was forever getting magazine BEST awards. I actually was threatened by fish eyed Gateway enthusiasts for pointing out that Dell and Tandy PCs were much better than any Gateway. 

We had to do a lot of trial and error and group projects figuring out how 
to get a mere Sound Blaster card to work in any specific PC! The problem was the dip switches and the IRQs. Although many companies had good technical support, they often could not help. PC hardware & software were in a revolution stage and the tech just moved to fast for techs and enthusiasts.
A lot of MS-DOS software worked out of the box on few PCs, each program cam with a huge manual. 

I tried several live distros but not one identified or installed my Linksys mini USB Ethernet card. I installed Ubuntu and for some reason Ubuntu auto ID and ran the card, connecting me to cable broadband. Afterwards any and all
distros identified and setup my card and broadband connection! 

It was a dual boot with Windows XP. I found installed the linksys Windows driver and connected with the card with XP. Afterward, all Linux distros could operate the card! I looked forward to the headache of losing whatever
in Windows might be cluing in Linux, eventhough I could not figure how a
live distro CD Linux could find and connect with my Linux driver.

My Grub Boot collapsed. I decided to just re-install Ubuntu on the drive. I still have my Linksys card connection! Go figure.

I had to trial and error get my all-in-one HP printer printing in black and grey scale. Using the HP 1315 serie driver clone, gave me printing in very light yellow. I finally hit gold with one distro, now it prints fine in all distros. 
Again, go figure. Now all of them get it right.  

Linux reminds me of the control I had over my little Commodore Computers and my MS-DOS PCs, The head aches of moving to Linux is well worth it.
For a few months, there will be head scratching and call for trial and error but I already see it is well worth the effort. 

O.K. only after serious effort  can we run most of the clips Win Media Player runs (automatically and in rather high quality) but do we really need the clips? Getting that all-in-one to full function takes work, trial and error but it is impressive how light the resource pull is in Linux. 

My HP driver and software package runs at an acceptable clip only on my dual core, high speed bus gaming machine. I have no registry to maintain or crash my system, no file fragmentation to waste time on defragging (you would think very rich Microsoft would have taken care of this by now!). Doesn't crap like that remind some of you of the American made car that has the same defects year, after year, after year? Consider the Le Sabre, long one of America's best. 15 years and three body makeovers and the trunck lid still leaks rain water inside the trunk when it is lifted up. Duh. 15 years production and the driver side auto lock still fails after about three years. And overpriced MS Word still has that goofy glitch, after five versions, where suddenly the first letter of every line is capitalized.  

I can't wait to master the terminal line. It will take me back to my MS-DOS batch file days when I made up my own menus and scripts, except the Linux shell is vastly more powerful.
--Bruised

---

### Post by Ryo964 on 2008-01-03
Hey All, 
    I had the same problem, printing blank pages from Gutsy to an HP PSC 1315xi. I tried several of these solutions, but here's what worked for me. A caveat: I really only use black printing, so that's what I was shooting for.

System-->Administration-->Printing

delete your printer under Local Printers and click "New Printer"
choose all the default settings
then go to "Printer Options" tab and change Normal Color to Normal Grayscale
Apply settings

For me, this got me good black printing. If that's all you need, try it.

---

