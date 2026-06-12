---
title: "Install windows XP"
date: 2009-02-22
forum: Installation &amp; Upgrades
---

### Post by Asday on 2009-02-22
I know, I know, really weird thread title.

[SIZE="5"]_Background._[/SIZE]

I have recently build a b*tching awesome PC, but the motherboard seems to only have 1 IDE slot.  I don't own any SATA HDDs.

I plugged my HDD into IDE, (which is partitioned (windows/(ubuntu/ubuntu home/swap)) ), and tried to boot Ubuntu.  It worked.  Yay me.  I tried to boot windows.  GRUB:  "Disk not found."  Aah.  It appears it had been finding a windows on a different HDD upon installation (makes sense, honest.)

So, I plugged a borrowed CD drive into the same IDE (neither of my optical drives work :() and stuck my XP installation disc in.  It got to the "Setup is starting Windows..." bit, before it comes up with all the formatting and partitioning options, and it BSoD'd.  Yeah, I got a BSoD without even having windows installed.  Joy.  Session_initialization_failure3 or something.  0x000000cf.  Plenty on google about it, and I've decided that it was due to being on the same IDE ribbon as the (or any) HDD.  (I tried two different XP install discs, both failed for the same reason.)

[SIZE="5"]_Goal._[/SIZE]

So.  I want to install windows.  Before anyone comes back with "nyurr, why, Linux does everything windows does, nyurr" in the snooty manner in which I've been told you adopt, I know.  That's why I have Ubuntu installed.

The two things Ubuntu can't do, are [this]("http://www.steinberg.net/en/home.html"), and [this]("http://www.eveonline.com/download/windows.asp").  The second being more important.  (Also, I've been told it has trouble with ATI, and I have a 4870.  I'm not giving it up.  Or letting it down, or running around and deserting it.)

I also don't have enough money for anything.  Seriously.  Today's my own mother's birthday, and instead of getting her anything (even a card) I cleaned the bathroom, and tried to cook her breakfast.  I have £0.57.  (Reason being, the government sucks and won't effing pay me my effing EMA.)

SO.  My equipment is:
[list][*]a LAN cable (might be crossover, I have no idea.  The XBox 360 can connect to another 360 and play games with it, and I can share my Laptop's vista internet with Ubuntu.)
[*]a Laptop.  HP 530, internet connection, windows vista installed.
[*]a PC.  Yay.
[*]a partitioned HDD.  (blank/(linux/linux home/swap))
[*]an IDE to USB cable.[/list]

I mention the cable because it might be possible to do this all with my laptop, but I don't know, and I REALLY don't want to mess up the boot drive again.

I was thinking of either:

[list][*]Installing XP over LAN.  If possible.  Google hasn't helped me on this.  OR:
[*]Installing XP in ubuntu, by using a VM.  This is what I thought of:[/list]

Open up SUN microsystem's VMware thingy, or whatever else.  Create a teenytiny .vdi on the blank partition of the HDD.  Install windows to it, with the VM.  Close the VM, and unpack the .vdi to the HDD, then add it to GRUB's boot menu.

[SIZE="5"]_Conclusion._[/SIZE]

Halp plox.

---

### Post by Dj TweeX on 2009-02-23
first off ubuntu can run those programs with an app called Crossover
[http://www.codeweavers.com/products/cxlinux/](http://www.codeweavers.com/products/cxlinux/)
i use crossover pro & it can run any windows program.

second. you should be able to have the hdd & the cd drive on the same ribbon.
the master should be the cd drive & the slave the hdd
you may also look in to a SATA to IDE converter that plugs into the back of an IDE drive & converts it to SATA

third, installing it with vm can work but may not.
i dont know to much about vm but i know it has its troubles

i would try putting the drives on one ribbon & installing again.
if that doesnt work. just use the IDE to USB plug it into your laptop & boot the XP install disk & install it to the drive that way

Good Luck!
~~Gabe~~

---

### Post by Asday on 2009-02-23
I can nigh on guarantee that crossover won't make the EVE online premium client run 100% correctly, at nearly full speed, taking advantage of the ATI 4870.  Cubase is another matter.

As for buying an adapter, I don't have the money.

On the same ribbon, XP install crashes.  I'll try fiddling around with the master/slave settings, and post back here.

Also, the install via laptop option I like.  I hadn't thought of it.  It does worry me slightly, though, as it may or may not try to mess with my notebook HDD.  You know what windows' like.

Thank you.

---

### Post by Mark Phelps on 2009-02-23
Sorry to tell you this, but the TRUTH is, that Wine (and Crossover) are NOT able to run ANY windows programs.  

Codeweavers has a database of Windows program execution results, rating programs from worst (garbage) to best (platinum).  If they were able to run ANY Windows programs, they wouldn't need a rating system!

Suggest that before you purchase Crossover or install Wine, you check their database to see the ratings of your Windows programs.  Unless they are Gold or better, you're wasting your time.

---

### Post by Dj TweeX on 2009-02-23
> **Asday said:**
> I can nigh on guarantee that crossover won't make the EVE online premium client run 100% correctly, at nearly full speed, taking advantage of the ATI 4870.  Cubase is another matter.

As for buying an adapter, I don't have the money.

On the same ribbon, XP install crashes.  I'll try fiddling around with the master/slave settings, and post back here.

Also, the install via laptop option I like.  I hadn't thought of it.  It does worry me slightly, though, as it may or may not try to mess with my notebook HDD.  You know what windows' like.

Thank you.

if you are worried about accidentally formatting your laptops hdd then name it something unique like "Vista" or "Windows" the xp installer will show the names of the drives & avoid even selecting it. it actually would be absolutly best if you took the laptop hdd out of the laptop before the install. the installer might try to install boot files fr xp on your root (C:\) drive.

the master/slave selections are very important if you would like to try that route. the cd drive MUST be master & the hdd MUST be slave.
do not select the Cable Select (CS) mode as its not guaranteed to work.

good luck!

---

### Post by Dj TweeX on 2009-02-23
> **Mark Phelps said:**
> Sorry to tell you this, but the TRUTH is, that Wine (and Crossover) are NOT able to run ANY windows programs.  

Codeweavers has a database of Windows program execution results, rating programs from worst (garbage) to best (platinum).  If they were able to run ANY Windows programs, they wouldn't need a rating system!

Suggest that before you purchase Crossover or install Wine, you check their database to see the ratings of your Windows programs.  Unless they are Gold or better, you're wasting your time.

you need to do your research & actually use the program. i have crossover pro & all i have to do is create custom bottles for any program i want to run. every single program i have needed to run i have been able to run in crossover.

---

### Post by Asday on 2009-02-23
I didn't realise that the optical drive had to be master, and HDD slave.  I actually thought vice versa.

I'm just going to go and choke down a bowl of cereal, and I'll mess around with the MA/SL settings.

Also, if it came to installing it via my laptop, I would certainly be removing my HDD.

EDIT:  Alright, I got it to stop BSoDing, but upon choosing the partition to install to, install told me:  "[however, this disk does not contain a windows XP compatible partition]("http://www.google.co.uk/search?hl=en&q=however%2C+this+disk+does+not+contain+a+windows+XP+compatible+partition&btnG=Google+Search&meta=")".  Yay.

I'm thinking it's time to mess around with partitions.  Now, where's my liveCD...?

EDIT2:  Ok, after much kerfuffle, the XP install files are on the hard drive, and I'm attempting to boot from it, to complete the installation, and I get exactly what's described [here]("http://www.computing.net/answers/hardware/invalid-system-diskbios-boot-order/49550.html").

Thing is, their be all and end all is to install vista, which is both something I've not the money for, and also am avoiding like the plague.

So.  Any recommendations on where to go for help on this?  Google isn't being much help.

(I'm using a LanParty DK M2RSH, 790 FX B chipset, DFI motherboard.  Fairly new thing.  Apparently XP has troubles with new boards.)

---

### Post by Asday on 2009-02-24
[SIZE="1"]And a dirty doublepost, because editing doesn't bump the thread.  >=|[/SIZE]

---

### Post by Mark Phelps on 2009-02-24
> **Dj TweeX said:**
> you need to do your research & actually use the program. i have crossover pro & all i have to do is create custom bottles for any program i want to run. every single program i have needed to run i have been able to run in crossover.

OK, so you lucked out and the few Windows programs you installed worked.  Hurray!! I did my research, and of the half-dozen different Windows apps I installed, NOTHING worked -- that's right, NOTHING!

I'm not saying that SOME Windows programs won't work in Crossover; I've read enough posts by folks who have been successful to know that SOME programs do work.  However, unless you have installed and tested EVERY Windows program, you can't make the claim (as you did) that EVERY Windows program will work.  All you know for sure is the ones you tested and others have tested do work. 

Since the Pro version costs money, it's worth investigating if a particular program WILL work before spending the money.

---

### Post by Dj TweeX on 2009-02-24
> **Mark Phelps said:**
> OK, so you lucked out and the few Windows programs you installed worked.  Hurray!! I did my research, and of the half-dozen different Windows apps I installed, NOTHING worked -- that's right, NOTHING!

I'm not saying that SOME Windows programs won't work in Crossover; I've read enough posts by folks who have been successful to know that SOME programs do work.  However, unless you have installed and tested EVERY Windows program, you can't make the claim (as you did) that EVERY Windows program will work.  All you know for sure is the ones you tested and others have tested do work. 

Since the Pro version costs money, it's worth investigating if a particular program WILL work before spending the money.

seeing how you are not adding to the thread whatsoever im going to have to ask you to stop posting unless you can help this man.

and i have 143 programs installed with crossover. i have never had a problem with installing anything. even programs on their garbage list.


as for the original poster,

your best chance it just to create a new partition map. id say back up your /home directory then reinstall completely.
i know it sounds troublesome. but its your best chance at an almost guaranteed a good outcome

---

### Post by redroad55 on 2009-02-24
now that you have the installation files in place what happens if you change the jumper to "cs" ? Post back with any results and or questions..

---

### Post by Mark Phelps on 2009-02-24
> **Dj TweeX said:**
> seeing how you are not adding to the thread whatsoever im going to have to ask you to stop posting unless you can help this man.

and i have 143 programs installed with crossover. i have never had a problem with installing anything. even programs on their garbage list.


Ok, I'll concede --  everything you tried worked.  Given that level of success, it's probably a good idea for me to look at Crossover again.  Perhaps I'll be more successful this time.

---

### Post by Dj TweeX on 2009-02-24
ok so now your computer is trying to start up from a diffrent drive just hit whatever button your system needs to goto the boot menue, then boot from your hdd. it will boot & go through setup.
access your bios & change your device boot order & it will be permanent.

---

### Post by Asday on 2009-02-24
I believe you're misunderstanding my progress.

I plugged the HDD into my laptop (with and IDE <-> USB cable) and ran the installer, up to the point where it's finished copying all the files.  I then took the HDD, and placed it back in my PC, and, when trying to boot from it, I get 0x0000007B.  There is a split second in which I can hammer F8 and get the boot options menu, but Safe Mode has the same problem, and I don't see any others helping me.

The HDD is being detected, and successfully booted from, and windows is not fully installed yet.

---

### Post by Dj TweeX on 2009-02-24
> **Asday said:**
> I believe you're misunderstanding my progress.

I plugged the HDD into my laptop (with and IDE <-> USB cable) and ran the installer, up to the point where it's finished copying all the files.  I then took the HDD, and placed it back in my PC, and, when trying to boot from it, I get 0x0000007B.  There is a split second in which I can hammer F8 and get the boot options menu, but Safe Mode has the same problem, and I don't see any others helping me.

The HDD is being detected, and successfully booted from, and windows is not fully installed yet.

i was talking about the boot menu where you choose which device to boot from not the boot options menue lol. but if its readding the drive thats a good thing. um.....try installing it on with your laptop again & leave it plugged into your laptop & run the setup from there. are there ANY other storage devices on your laptop that han=ve not been removed??

---

### Post by Slim Odds on 2009-02-24
> **Asday said:**
> I didn't realise that the optical drive had to be master, and HDD slave.  I actually thought vice versa.

It should work just fine either way.....

---

### Post by Dj TweeX on 2009-02-24
> **Slim Odds said:**
> It should work just fine either way.....

it makes life easier. so you dont have to edit your bios to boot from an install cd

---

### Post by Slim Odds on 2009-02-24
> **Dj TweeX said:**
> it makes life easier. so you dont have to edit your bios to boot from an install cd

The BIOS usually has a boot order like that is not dependent on master/slave.

It's usually something like: CDROM, then USB, then HD

or something like that.

---

### Post by Dj TweeX on 2009-02-24
> **Slim Odds said:**
> The BIOS usually has a boot order like that is not dependent on master/slave.

It's usually something like: CDROM, then USB, then HD

or something like that.

yes but it jut uses those names for the IDE controllers. not the devices themselves. newer systems can differentiate the devices but not his board.

---

### Post by TimDaniels on 2009-02-24
> **Asday said:**
> 
[.....] I tried to boot windows.  GRUB:  "Disk not found."  Aah.  It appears it had been finding a windows on a different HDD upon installation (makes sense, honest.)

[SIZE="5"]_Goal._[/SIZE]

So.  I want to install windows.

You shoulkd consult a Windows XP newsgroup.  I strongly suggest microsoft.public.windowsxp.setup_deployment .  There are more experts there on WinXP than there are here.

*TimDaniels*

---

### Post by Dj TweeX on 2009-02-24
> **TimDaniels said:**
> You shoulkd consult a Windows XP newsgroup.  I strongly suggest microsoft.public.windowsxp.setup_deployment .  There are more experts there on WinXP than there are here.

*TimDaniels*

ive been tri-booting with Ubuntu & windows for years. all they will say is "Why are you useing linux?!?" its happend to me.

---

### Post by Asday on 2009-02-24
To whoever said run the full install on the laptop, I don't particularly want to, as I believe it will then install according to the hardware, which will then change vastly upon it's first boot, and it'll be all like:  "Heeeey, this wasn't were I was installed...  Where's my mommyyy!?  Baaaawwwwwww!"  Which will be a pain in the behind.

Also, what's to say that the fully installed version won't just 0x0000007B on me in the same way?

Oh yeah, noobish question, how do I...  Use (?) newsgroups?

---

### Post by Dj TweeX on 2009-02-24
> **Asday said:**
> To whoever said run the full install on the laptop, I don't particularly want to, as I believe it will then install according to the hardware, which will then change vastly upon it's first boot, and it'll be all like:  "Heeeey, this wasn't were I was installed...  Where's my mommyyy!?  Baaaawwwwwww!"  Which will be a pain in the behind.

Also, what's to say that the fully installed version won't just 0x0000007B on me in the same way?

Oh yeah, noobish question, how do I...  Use (?) newsgroups?

it doesn't install based on hardware thats one thing you can always rely on windows to be, inferior

---

### Post by Dj TweeX on 2009-02-24
> **Asday said:**
> 
0x0000007B

protip
 just say 0x7B
you dont need all the zero's

---

### Post by Asday on 2009-02-24
> **Dj TweeX said:**
> it doesn't install based on hardware thats one thing you can always rely on windows to be, inferior

First, let's please not bring superiority or inferiority into this.  All present are fully aware of the pros and cons of each platform.

I know it doesn't install based on hardware, *but* I believe it gets annoyed of you change any hardware significantly, such as replacing a motherboard and/or processor.  Hence my worries.

> protip
just say 0x7B
you dont need all the zero's 

Thanks.

---

### Post by Hobgoblin on 2009-02-24
> **Asday said:**
> It got to the "Setup is starting Windows..." bit, before it comes up with all the formatting and partitioning options, and it BSoD'd.  Yeah, I got a BSoD without even having windows installed.  Joy.  

I've seen that several times and it has always been due to faulty memory.  Run memtest (from the Ubuntu CD, or from the grub menu) for a couple of hours.

If it errors and you can take one memory stick out then try with one at a time to find the faulty one.

As for the order of the drives.  The CD should be slave to the HDD, the best way is to set them both at cable select and have the HDD on the end connector.

---

### Post by Asday on 2009-02-25
Although it's feasable, I believe it's more likely that the motherboard (or more appropriately, windows failing) that's the problem.  Nevertheless, I shall run the test.

---

### Post by Hobgoblin on 2009-02-27
I think the test has had enough time.  If there were no errors by now you can safely say your memory is OK.:P

---

### Post by Asday on 2009-02-27
Oh right, ok, yeah memory's fine.

Still getting the stop error, and after some mucking around on the laptop, I've come up against an error that suggests my CMOS drive-type settings are wrong, and that it's unable to access the boot partition.

---

### Post by Asday on 2009-03-07
[SIZE="1"]Nasty doublepost.[/SIZE]

It was either both of the install discs, or that I tried to install using USB.

Occam's Razor plays here, so I was right about USB and windows being a b*tch.

---

