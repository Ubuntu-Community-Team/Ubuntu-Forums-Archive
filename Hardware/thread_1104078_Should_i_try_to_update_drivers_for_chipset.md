---
title: "Should i try to update drivers for chipset?"
date: 2009-03-23
forum: Hardware
---

### Post by WOOHOOHOO on 2009-03-23
Hi,

I've been googling around as i dont think my drivers work as well as they did in XP. I (think) Ubuntu used some standard drivers, as when i go into the Admin-Hardwre Drivers, it says i have no drivers.

The main reason i think there is a prob is that 2 games i used to play on XP with no probs really struggle on Linux. I know the games i play were meant for XP, but i see others are managing to play them with lower spec than me.

For example, Delta Force Land Warrior. Ran well on XP, if a little slow between missions. On linux i loaded it up with Wine. It installed and goes through ok until misson starts, then slows my pc to a crawl and virtually crashed it. The graphics are all grey etc, even on the lowest setting. The other example would be Champiuonship Manager 2005, worked great on XP, crawls on Linux.

I'm not too pc-tech wise, but several people asked if i had upgraded my chipset.

I run an old laptop, with SiS 65x graphics chipset, with a Uniwell Computer Corp Device 5100, with Pentium 4 CPU 2.0ghz. I have Ubuntu 8.10.

I read on the SiS folder something about Ubuntu provides some SiS drivers already but i dont understand the tech talk: [http://www.sis.com/support/support_faqs_16.htm](http://www.sis.com/support/support_faqs_16.htm)

what do you think?

---

### Post by cariboo on 2009-03-23
From the looks of it SIS stopped creating drivers for your chipset back when the kernel version was 2.4, we are now at 2.6. Most distributions use the same kernal and drivers, so you may be out of luck.

Jim

---

### Post by TonyFordz on 2009-09-05
[img]http://img32.imageshack.us/img32/1661/dflwlinux1.png[/img]
Playing DFLW single player mode Via WINE

[img]http://img2.imageshack.us/img2/4929/dflwlinux2.png[/img]
Hosting Dedicated Server Via WINE

The best way to install DFLW & have it work best is as follows,

Assuming you have the latest version of WINE installed...

Rather easy to install threw WINE,

Insert your DFLW CD & explore to the folder "dflsetup" then right click on "setup.exe" & chose "open with WINE Windows Program Manager"... Then install the game "Large Size".

After you have installed the game then download the update "1.00.42" which you can get below,
[http://hotfile.com/dl/11601828/1bd9a2e/dflw-Update-.42.zip.html](http://hotfile.com/dl/11601828/1bd9a2e/dflw-Update-.42.zip.html)

You can also download the No CD Patch which also allows you to host up to 8 player Co-Ops,
[http://hotfile.com/dl/11601850/200c10b/dflw-NoCDPatch-.42.zip.html](http://hotfile.com/dl/11601850/200c10b/dflw-NoCDPatch-.42.zip.html)

Run the update which will ask you for the location of your game exe file which
is as follows,

.wine\drive_c\Program Files\NovaLogic\Delta Force Land Warrior

Once you select your DFLW.exe file then let it run the update for you.

Now once you have done this you will need to copy & paste the No CD patch in
that folder also over the old dflw.exe which will now allow for you to play without needing to put your CD in each time to play.

Its that simple!

PS: I have not yet tried the MEDs for making maps on Ubuntu so no idea if those work or not...

---

