---
title: "Trying to Install 2nd Hard Drive, stops ubuntu from loading"
date: 2009-05-09
forum: Hardware
---

### Post by grimdeath on 2009-05-09
I have an older compaq system I have been running Ubuntu 9.04 on but it only had a 30gb hard drive. I decided to pull a IDE 120gb Western Digital drive out of my main system and add it to my ubuntu system but when I have tried this I am having problems.

First problem, it would boot but came to a weird error message and just sat there (didnt write down the error, sorry) but checking the bios it appeared the new drive was showing up first as the primary drive. So I shut down, unplugged and swapped the cable the other way around.

Turned it on, and now it just goes to a black screen. Trying to go to the bios doesnt work, black screen as well. So I shut down and unplugged the power to the new drive. Turned it on and it boot right to grub just like normal. Its as if no matter what I do it wants to boot into the new drive instead.

Any idea what is holding it up with the new drive? The new drive has had the partition deleted when I was reinstalling Windows on my main machine but I did not reformat it. I checked the jumpers and the existing 30gb drive is set to master, the new drive is missing the jumper and I dont have one to replace it...it always worked fine in my main system that way :/

The computer will not boot into the live cd, I guess its too much for it to handle (acts like its booting the desktop, plays music etc, then goes to a black screen) so if you need me to edit anything I will need to know how to do it from the terminal or with the new drive unplugged.

I searched around and did not see anyone else with this exact error but please forward me if there is. Thanks for any help.

---

### Post by logos34 on 2009-05-09
either the Bios is defaulting to the new drive as boot device as soon as it is detected, and/or you need the jumper to make it slave or cable select. (I know my maxtor does not need a jumper for master, but it does for the other two). Not sure, though, why it would work that way in your main system.

Check the hard disk boot priority menu in the Bios (if you can enter it after connecting the drive) and check the sticker on the hdd for jumper diagram (or find the docs for your model at West digital website)

---

### Post by dsmithhfx on 2009-05-09
> the new drive is missing the jumper and I dont have one to replace it...it always worked fine in my main system that way :

I suspect the missing jumper is the critical issue here, however:

Is the original 30G boot drive on ide channel 1?

Did you add the 'new' (120G) drive to the same channel by plugging the middle connector of the ide ribbon cable to it (the slave position)?

Did you try it on channel 2 (the other ide connector on your mb)? The recommended route is to have hdd's on separate channels, with the second hdd as slave to the optical drive.

Did you try to reformat the 120G drive by booting up a Western Digital "Data Lifeguard" cd or floppy (this will also have jumpering info, you can check drive health etc)?

---

### Post by oomagoolies on 2009-05-09
I had a similar problem and what did it for me was re-installing ubuntu after i put my second hard drive in my machine, like you it seemed to boot from the new drive and after messing with the bios till I was totally pissed off I just installed onto the two drives.

---

### Post by grimdeath on 2009-05-09
thanks for the quick replies guys.

the bios is not very robust in this system, not a ton of options and no way to swap priority between the two that ive seen from the bios alone.

I am using both on the same ribbon cable, I will try using the other cable next though, didnt think of that.

the drive should be fine, I was using it yesterday even. all I did was delete the partition and such off it before shutting down and moving it over. I figure its just a issue with either the jumper or cable setup like others were saying on here.

ill report back later tonight when I try that.

---

### Post by grimdeath on 2009-05-10
ok I didnt get to try the two cable method until today but again no luck. this time it just sits at the boot screen that says compaq and has the various options to load into the bios, pick boot device, etc...clicking any of them just goes to a screen with the name of computer model and just sits there.

I guess if I get desperate I will just pull out the 30gb drive and reinstall on the larger one. I would like to figure out the issue though because I plan to insert another drive at some point since I want to use this as a file/media server.

*edit*
because 30gb is not a major loss ive decided to just reinstall on my larger new drive. if anyone else has any other ideas just let me know. guess ill just have to get a new jumper or drive to try again :)

thanks for the help anyways.

---

