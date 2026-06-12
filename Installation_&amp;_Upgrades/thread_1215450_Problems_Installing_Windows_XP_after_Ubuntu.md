---
title: "Problems Installing Windows XP after Ubuntu"
date: 2009-07-17
forum: Installation &amp; Upgrades
---

### Post by andy0550 on 2009-07-17
Hey everyone,

  I had a problem with Ubuntu, and now everytime I try to boot my computer, the screen goes black with wierd colored vertical lines on the screen after the Ubuntu Boot Screen. In other words, Ubuntu just doesn't work anymore :( Anyway, due to this program, I decided to reinstall my Windows XP on my computer instead, but the problem is, everytime I try to install XP, a message shows up saying "Windows can't be installed, no Harddrive found".

Does anyone have a solution to this problem? In advance, thank you!

---

### Post by bodyharvester on 2009-07-17
> **andy0550 said:**
> "Windows can't be installed, no Harddrive found".

Does anyone have a solution to this problem? In advance, thank you!

when i had a problem similar to this my hard drive had to be replaced because the os (XP) could not be found :(

but if you still get the ubuntu screen then the harddrive must be working fine, have you tried re-installing ubuntu?

---

### Post by andy0550 on 2009-07-17
No I haven't... But it's a wierd thing really, because it worked fine before, and then suddenly this black screen with lines started appearing :( Perhaps I should try reinstalling Ubuntu as you say :) But the problem is I currently don't have access to the Installation CD, so I was hoping that I could find a solution here online, so that I can directly install windows.

---

### Post by bodyharvester on 2009-07-17
> **andy0550 said:**
> No I haven't... But it's a wierd thing really, because it worked fine before, and then suddenly this black screen with lines started appearing :( Perhaps I should try reinstalling Ubuntu as you say :) But the problem is I currently don't have access to the Installation CD, so I was hoping that I could find a solution here online, so that I can directly install windows.

you can download ubuntu 9.04 from the main site, then burn to a disk

if your COMPUTER (after, say, Dell screen with loading bar before your OS with loading bar) cant access the drive then the drive is likely bust :( sorry if thats the case, you are in warranty right?

good luck, ill wait around to see how it goes

mine went like this...DELL with loading bar then a black screen with words at the top saying it could not boot coz C:\windows could not be found and inserting install xp cd the harddrive could not be found. dell took laptop away and when it returned it had a new harddrive

---

### Post by andy0550 on 2009-07-17
Well it is different in my case, because I get past the computer boot, and into the ubuntu boot, but then the problem occurs, so perhaps the windows xp install cd is misunderstanding an error? And with the burning CDs, I know you can download it from the site, but I currently don'thave access to a PC with a cd burner, and my own computer, is as said, having problems, so can't do it there either, so some time might pass before I get my hands on a ubuntu cd :(

---

### Post by bodyharvester on 2009-07-17
> **andy0550 said:**
> Well it is different in my case, because I get past the computer boot, and into the ubuntu boot, but then the problem occurs, so perhaps the windows xp install cd is misunderstanding an error? And with the burning CDs, I know you can download it from the site, but I currently don'thave access to a PC with a cd burner, and my own computer, is as said, having problems, so can't do it there either, so some time might pass before I get my hands on a ubuntu cd :(


go to [https://shipit.ubuntu.com](https://shipit.ubuntu.com) to request a cd, mine took a week to arrive but its better to have a copy lying around

as for ubuntu boot is the xp installation cd in the drive when you restart?

---

### Post by bodyharvester on 2009-07-17
oh, just to be sure make certain that in the BIOS you have chosen boot option CD/DVD or whatever it says

---

### Post by prshah on 2009-07-17
> **andy0550 said:**
> everytime I try to install XP, a message shows up saying "Windows can't be installed, no Harddrive found".

If you are using a version of Windows prior to SP2, and a SATA hard disk drive, you can get this problem. 

This is because WinXP SP2 and below do not have driver support for SATA.

You can get around this by 

a) "Slipstreaming" the SATA drivers / SP3 into your existing Windows Installation files.

b) Checking if you have a "compatibility" option in your BIOS to allow SATA to be seen as IDE. Sorry, I can't be more specific, each BIOS has it's own setting.

c) Get a Windows with SP3 integrated install disk.

---

