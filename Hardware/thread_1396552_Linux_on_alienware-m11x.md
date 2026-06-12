---
title: "Linux on alienware-m11x?"
date: 2010-02-02
forum: Hardware
---

### Post by avilella on 2010-02-02
Has anyone tried the new Alienware M11X on Linux?
Is the nvidia GeForce GT 335M working with nouveau? What about the nvidia closed-source binary drivers?

---

### Post by hyperandy on 2010-02-02
I don't think it officially ships until the beginning of March..I thought about buying one but I ONLY use Ubuntu/ Linux and don't feel like buying something I will be forced to use Windows on until all the drivers are worked out

---

### Post by soleblaze on 2010-02-03
I'm also eyeing this machine, although I would dual boot it.  (Windows for games, Linux for everything else).  I did some research about switchable graphics/gpus.. I think the 335M will run fine, however there's no way of switching between the two in Linux while the machine is running.  If alienware gives a BIOS option (I believe in Windows FN-F6 switches between the two) or the FN-F6 is hardwired via the BIOS then we should be fine.  However, if the only way to switch between the two is in software then it wouldn't make for a very good Linux machine.  I'd say give it awhile and keep an eye on what other people are doing with it once it comes out in March.

---

### Post by soleblaze on 2010-02-03
Hardware Heaven did a review of the M11 [here](http://www.hardwareheaven.com/reviews.php?reviewid=924&pageid=1).  In some of the pictures posted there was one of the [BIOS Screen](http://www.hardwareheaven.com/reviewimages/alienware_m11x/26.jpg).  Looks like the graphics are switchable in the bios, which means the graphics part shouldn't be an issue with Linux.  I'd guess that this laptop will work fine in Linux.

---

### Post by whayong on 2010-02-04
As mentioned, I am eyeing this machine as well but just refuse to use windows as a sole OS. So who's first to test it out??????

---

### Post by tahnok on 2010-02-04
I just ordered this laptop and I am very interested in getting it to run with linux. I think switchable nvidia graphics are simple enough to do. Take a look at the ul30vt and related models from asus. They too have switchable graphics and work fine under ubuntu. I will post more results once I get the machine

---

### Post by hyperandy on 2010-02-04
> **tahnok said:**
> I just ordered this laptop and I am very interested in getting it to run with linux. I think switchable nvidia graphics are simple enough to do. Take a look at the ul30vt and related models from asus. They too have switchable graphics and work fine under ubuntu. I will post more results once I get the machine

Please do! I think this is a great machine just wish it was on the Dells "limited" approved list to be sold with Ubuntu....lol

---

### Post by tahnok on 2010-02-04
I doubt it will ever be officially supported by Dell seeing as it's an alienware and those are for gaming.

---

### Post by hyperandy on 2010-02-04
> **tahnok said:**
> I doubt it will ever be officially supported by Dell seeing as it's an alienware and those are for gaming.

Ya doesn't take a degree to figure that one out. I just wish people would realize that gamers aren't the only ones who want powerful computers. I never have been a gamer and I always buy really nice machines because I can't stand to be slowed down waiting for my machine to "think"

---

### Post by ubudave on 2010-02-23
I just wanted to add that I am very interested in this laptop and will pounce on it as soon as I am sure it will run Ubuntu well.

---

### Post by soleblaze on 2010-02-24
Mine is coming in on Friday, although I might not be there to sign for it.  I'll be testing the latest Ubuntu, Back Track 4, and Gentoo on it.  The main thing I'm worried about is that it might be coming with a broadcom based wireless adapter.  I'll post about it once I mess around with it a bit and I'll also be putting up a hardware page for it on the gentoo wiki.

---

### Post by tahnok on 2010-02-25
Lucky bum, the nice folks at Dell decided that they should cancel and then redo my order thus making sure the arrival date isn't for another 4 weeks.

---

### Post by jebinem1999 on 2010-02-26
I have my m11x, just came in this week. As soon as I got it, I pulled the hard drive and put in a different one so I could test Linux. I was using Linux Mint 8, not Ubuntu. Close enough to the same thing, right?

First off, the graphics card has to be changed back and forth in the BIOS if you want to take advantage of battery life or gaming. I expected this, but was hoping the on the fly function key would still work. No luck.

Sound - didn't work from the get go. It installed a driver, but not the right one. Didn't spend too much time on this, was more interested in getting the lighting controls to work.

Alienware Command Center - one of the main reasons to get an Alienware laptop. I did not have any luck installing this. I used Wine, installing .NET Framework 3.0 first. The installer kept crashing so I wasn't able to fully test this.

So far, no good. I am sticking with the Windows hard drive but I am anxious to see what other people are finding out here. I figure in time, someone will get this rocking like a champ. It would be nice if we could get support from Dell on this. I mean, who wants to be stuck using Windows?

---

### Post by tahnok on 2010-02-26
So you can't switch the graphics on the fly? That's too bad. Which graphics card does it default to?

Do wireless and ethernet work out of the box?

---

### Post by jebinem1999 on 2010-02-26
When you boot the machine, you can get into the BIOS and you have two options: DISCRETE or SWITCHABLE. If you put it on DISCRETE, it will use the on board card. If you put it to SWITCHABLE, then it will use the nVidia card.

In Windows, you just leave it on SWITCHABLE and you can switch on the fly.

Yes, the wireless and ethernet did work.

---

### Post by soleblaze on 2010-02-26
Wattos has created a java program  called [AlienFX Lite](http://ubuntuforums.org/showthread.php?t=1403399) to change the lights.  It doesn't have anything specific for the M11x yet, but I'm sure once he gets input from someone with one it'll have the ability to change the lights within Linux.  

Mine came in this morning, but I won't have a chance to touch it until tomorrow.

---

### Post by raoul1219 on 2010-02-27
I just "fall" on the M11x after searching for a capable light machine. I would buy one in order to have a good gaming system (running windows), but I would'nt dtand this OS in Day to day opperation, then again i could be surprised? I would go for the 250GB SSD and dualboot to Ubuntu. 

The machine seems quite capable, why not run Ubuntu in a VM fullscreen ??

the only no go for me is a UK keyboard since i live in Switzerland and we have a different layout here. is the keyboard 100%size or 98% ?

I am interested in your progress and will follow this post

---

### Post by soleblaze on 2010-02-28
Ok, I have Ubuntu running on it.  It looks like switchable = Intel and discrete = NVIDIA.  If you try to install the nvidia closed source driver and it's set to switchable it will cause a kernel panic.  If you install the driver when it's on discrete it will work fine, but then it will fail to start once you switch it back to switchable.  (The graphics fail to work correctly on the splash screen and it didn't seem to get any farther.  However, it didn't kernel panic on me..when I pressed the alien head it shut down.)  

The wireless card is a Dell 1520, which uses the broadcom BCM4353 chipset.  It works fine with the closed source STA driver, but I'm currently unsure if there's any open source alternatives to this card.

Sound does not work as jebinem1999 mentioned.  

The fan also feels like it spins up a lot more than it does in Windows 7.  Currently it looks like the fan is either off or on, without being throttled in any way.  It can become annoying depending on what you're doing.  I'm hoping this will be fixed in the next bios update.  (The laptop also doesn't overclock correctly, which is supposed to be fixed in the next BIOS revision)

That's about all the testing that I've done on it so far.  I'm guessing the nvidia screws up because it adds the nvidia line to the xorg.conf file.  I'm wondering if X will still pick up on that driver even if it's not in the conf file.  I'll have to test that out when I have more time.

---

### Post by soleblaze on 2010-02-28
[QUOTE=raoul1219;8889633]the only no go for me is a UK keyboard since i live in Switzerland and we have a different layout here. is the keyboard 100%size or 98% ?/QUOTE]

The keyboard is probably more like 95%.  It's a larger chasis than other computers, but they also added the home, page up, page down, and end keys on the rightmost row, causing the other keys to be slightly smaller.  Personally I like the size of the keyboard.

---

### Post by jebinem1999 on 2010-03-01
Soleblaze is correct on the graphics card issue. I experienced the exact same thing when switching the BIOS from DISCRETE to SWITCHABLE. I got the kernel panic as well. I posted a comment to Wattos to see about AlienFX Lite for m11x, as soleblaze mentioned above. Testing continues...

---

### Post by soleblaze on 2010-03-01
Looks like Dave Airlie has been working on creating a way to switch the graphics without rebooting.  He calls this vga_switcheroo, which looks to be merged into the next kernel, 2.6.34.  Looks like it's mostly tested out with the ATI/Intel combination and not NVidia/Intel, however it give us hope that we'll be able to switch without rebooting in the next few months.  It will still require restarting the X server.

---

### Post by ubudave on 2010-03-01
Great to hear all the news on the M11x!  Bummer about the sound not working :(  Keep us up to date with any progress or news you find in that area.  Thanks!!

---

### Post by jebinem1999 on 2010-03-03
Just wanted to add a note:

In this testing, I've wanted to use two hard drives to go back and forth to simplify going from Win7 and Linux. I didn't get the big hard drive or i'd just dual boot. However, the FIRST time I took the bottom panel off, two of the screws will no longer go back in. Very disappointing. I also had found a screw that was just left in the casing from the manufacturer and damaged one of the speakers. That has since been replaced. I'm waiting on my second service call and I've had the thing for just over a week. They have not been helpful at all with my bottom panel problem. I haven't been willing to continue my testing because I'm afraid if I take that panel off again, more of the screws will do the same thing.

This sounds like a post that should be on Alienware's website and not here, I know. The only reason I am mentioning this is to anyone who is interested in getting one and putting Ubuntu on it. If I had to do this over again, I'd wait. In time, I believe the Alien FX lighting, the sound card, and the video card switching will work. Also, (hopefully) the quality of the actual hardware will improve. Very disappointed in that.

Carry on...

---

### Post by ubudave on 2010-03-03
Does anyone know of any laptops that can compete with  the M11x.  13" or smaller. Edit>>> and that run Ubuntu9.10 well.

---

### Post by soleblaze on 2010-03-06
Got the sound working.  Looks like the only working driver at the moment for the ALC665 is on the realtek site [here](http://www.realtek.com.tw/downloads/downloadsCheck.aspx?Langid=1&PNid=14&PFid=24&Level=4&Conn=3&DownTypeID=3&GetDown=false).  Just need to download the Linux driver, extract it and follow the instructions on how to manually install it.  (You'll need to install build-essentials if you don't already have that installed)

---

### Post by ubudave on 2010-03-07
> **soleblaze said:**
> Got the sound working.  Looks like the only working driver at the moment for the ALC665 is on the realtek site [here](http://www.realtek.com.tw/downloads/downloadsCheck.aspx?Langid=1&PNid=14&PFid=24&Level=4&Conn=3&DownTypeID=3&GetDown=false).  Just need to download the Linux driver, extract it and follow the instructions on how to manually install it.  (You'll need to install build-essentials if you don't already have that installed)

Thanks for the info!  Giving some serous thought to ordering one tonight.

---

### Post by jebinem1999 on 2010-03-09
Anyone know anything else about the VGA switching on the fly? Or the Alien FX lite for the lighting controls?

---

### Post by soleblaze on 2010-03-10
got brightness on switchable working:

as root:

edit /etc/default/grub. change GRUB_CMDLINE_LINUX_DEFAULT="quiet splash" to GRUB_CMDLINE_LINUX_DEFAULT="quiet splash nomodeset acpi_backlight=vendor"

Save that then run update-grub. After that and a reboot you should be able to change the brightness just fine.  You have a lot more steps in the brightness than you do in windows.

---

### Post by tahnok on 2010-03-11
> **jebinem1999 said:**
> Anyone know anything else about the VGA switching on the fly? Or the Alien FX lite for the lighting controls?
Ubudave:
You might try checking out some of the ASUS ULVs like the UL30vt. It has a slower graphics card then the m11x, but the screen is larger and the battery lasts longer.

---

### Post by Noxt1109 on 2010-03-15
Been looking at getting the mx11 as well but not sure screen is big enough, then looked at ul30vt which looks great for size and  the switchable graphics are just about sorted now. But have just seen some info today on an update on the ul30vt, the ul30jt same case and screen but i7 CPU and 1gig graphics dedicated memory. No release date yet but the asus guy at the CES said 4-8 weeks so maybe worth a look/wait if anyone after a power full thin and light alternative to mx11.

---

### Post by juanoleso on 2010-03-17
Goona pickup the m11x pretty soon.  Thanks to all for this thread.  Gonna be watching it closely.

---

### Post by insanex on 2010-03-18
Thanks for all the information folks. I ordered my m11x a few days after it was released and have had it for about 2-3 weeks now. I tried Linux Mint 8 and installed the nVidia driver not realizing that the "switchable" mode in BIOS indicated the Intel was default. I got some squished white text at the top of the screen after installing the driver.

Thanks again for the information.

Cheers,
insanex

---

### Post by tahnok on 2010-03-21
I am finding that compared to windows, ubuntu is getting noticeably less battery life. Does anyone have any recommendations for settings I can change to get more battery? Or maybe programs to install?

---

### Post by soleblaze on 2010-03-23
> **tahnok said:**
> I am finding that compared to windows, ubuntu is getting noticeably less battery life. Does anyone have any recommendations for settings I can change to get more battery? Or maybe programs to install?

It's because both the intel and the nvidia graphic card are active.  Until the gpu_switcheroo works for this model we won't get near the same battery life.  I'm sure there's a few tweaks to get some extra time, but this is the major issue.

---

### Post by tahnok on 2010-03-25
> **soleblaze said:**
> It's because both the intel and the nvidia graphic card are active.  Until the gpu_switcheroo works for this model we won't get near the same battery life.  I'm sure there's a few tweaks to get some extra time, but this is the major issue.

Is there no way to manually disable the nvidia card?

---

### Post by norseman-has-a-laptop on 2010-03-25
i hate to be the troll in this one but i dont really like alienware only because i can make a better one for half the price just alot less hassel

---

### Post by tahnok on 2010-03-25
I agree that buying an alienware desktop is probably a waste, but I honestly don't know any way of building an 11" laptop.

---

### Post by norseman-has-a-laptop on 2010-03-25
i was talking about alienware in genral

---

### Post by G0lg0thaZA on 2010-03-26
Dude! 

If you know how to put a laptop like this together, please share...

It does not look too likely that we will get to buy this beauty locally here in Sunny South Africa soon... :-(

---

### Post by aeon.flux on 2010-03-30
as far as i know, alienware doesn't sell they products in my country (Slovakia), but my friend ordered it from from UK and had no problem with Support.

---

### Post by soleblaze on 2010-03-31
> **tahnok said:**
> Is there no way to manually disable the nvidia card?

Not that I've seen.  You can only force the nvidia card to be the main one.

---

### Post by larryfrombarrie on 2010-04-14
should have mine in a week or 2, I upped the hd to the 500 gb and the ram to 8GB which is rediculous, I know but I figured that it will be a while before it becomes 100% ubuntu friendly.  So my plan is to run ubuntu in VB, until it is, instead of dual booting.

Is there anything I should be aware of here?

---

### Post by soleblaze on 2010-04-15
> **larryfrombarrie said:**
> should have mine in a week or 2, I upped the hd to the 500 gb and the ram to 8GB which is rediculous, I know but I figured that it will be a while before it becomes 100% ubuntu friendly.  So my plan is to run ubuntu in VB, until it is, instead of dual booting.

Is there anything I should be aware of here?

Not that I'm aware of.  I'm in the process of getting arch to work and trying to talk to David Arlie about getting the vga switcheroo stuff working for it.  I might end up also virtualizing Linux if I can't turn off the nvidia GPU.

---

### Post by aeon.flux on 2010-04-16
> **larryfrombarrie said:**
> should have mine in a week or 2, I upped the hd to the 500 gb and the ram to 8GB which is rediculous, I know but I figured that it will be a while before it becomes 100% ubuntu friendly.  So my plan is to run ubuntu in VB, until it is, instead of dual booting.

Is there anything I should be aware of here?

i think you should know, that more RAM is pushing battery life down, when i added to my notebook (from 1GB to) 2,5GB the battery life has shorten to the half of time, even if the system was still using only 800MB of it

..and i wanted to ask...
i'm really excited about this model, (i think that alienware is expensive, but i'm going to buy this one), what kind of material is used on the cover? is it metal / colored metal / kind of rubber on metal or what? and is the silver one colored or is it "naked" metal? aluminium?

---

### Post by FFred on 2010-04-17
> **aeon.flux said:**
>  what kind of material is used on the cover? is it metal / colored metal / kind of rubber on metal or what? and is the silver one colored or is it "naked" metal? aluminium?

Don't know about the silver one (mine is black). The black one is of a sturdy rigid metal with a paint that's not too shiny. Looks ok. The Alien head glows white when it's on (it's my first Alienware model). 
All in all an interesting machine although getting it to run Linux is pretty painful, I even managed to kill the Windows partition (Luckily I had a Windows 7 disk lying around, hadn't backed it up, wanted to keep a gaming partition on the thing).

I have to reinstall Grub now.

---

### Post by FFred on 2010-04-17
FYI all, I created a M11X group at :
[http://ubuntuforums.org/group.php?groupid=755](http://ubuntuforums.org/group.php?groupid=755)
Hopefully we can centralise solutions for that machine there to make them easier to find.

---

### Post by tyoc213 on 2010-04-17
Finally, what have you installed on your system?, I mean I want to go to with 10.4 [http://releases.ubuntu.com/releases/10.04/](http://releases.ubuntu.com/releases/10.04/) should I install the netbook? or the 64 bit ubuntu version best? or 32?

---

### Post by FFred on 2010-04-17
> **tyoc213 said:**
> Finally, what have you installed on your system?, I mean I want to go to with 10.4 [http://releases.ubuntu.com/releases/10.04/](http://releases.ubuntu.com/releases/10.04/) should I install the netbook? or the 64 bit ubuntu version best? or 32?

The complete *ubuntu would be more suited to this machine. 64 bit if you have more than 3Gigs of RAM.
I installed Ubuntu desktop 64 bit 10.4 and will be adding kubuntu(which is what I usually use)  as soon as I have a stable system.

---

### Post by larryfrombarrie on 2010-04-18
> **aeon.flux said:**
> i think you should know, that more RAM is pushing battery life down, when i added to my notebook (from 1GB to) 2,5GB the battery life has shorten to the half of time, even if the system was still using only 800MB of it

..and i wanted to ask...
i'm really excited about this model, (i think that alienware is expensive, but i'm going to buy this one), what kind of material is used on the cover? is it metal / colored metal / kind of rubber on metal or what? and is the silver one colored or is it "naked" metal? aluminium?

wow, i never considered that, the ram upgrade is within my budget and my plan is to allocate 4 gb to the virtual machine.  I work on a ship and it is plugged in most of the time, so i should be okay.  maybe if I am traveling I can pop half of the ram out???
Too bad you can't do that on the fly too!!!

Thanks for the tip!

aeon flux is awesome btw...

---

### Post by aeon.flux on 2010-04-19
> **larryfrombarrie said:**
> wow, i never considered that, the ram upgrade is within my budget and my plan is to allocate 4 gb to the virtual machine.  I work on a ship and it is plugged in most of the time, so i should be okay.  maybe if I am traveling I can pop half of the ram out???
Too bad you can't do that on the fly too!!!

if you planing to virtualize, you should now, that 1,3GHz (or even 1,3 dual core) doesn't have to be enouch for running 2 systems. I use ubuntu 9.10 (with win7 in box) and 2,5 GB ram is enough, but my 1,7GHz dual core CPU looks like it's going to explode sometimes.. : (
another thing that nobody talking about is that you can't have base system and the image of virtual machine on same disc (if you have SATA HDD), because the head in disk have to write and read on 2 places at once when you run both and that is slowing both systems and [COLOR="red"]you can break the hardisk[/COLOR] (i was near to that). You should add 20-30GB of data between installing ubuntu and virtual disk. And i wouldn't remove the windows if you want to play games on M11x, because the system in virtual machine has never the same power as the base system whitch means that you can never have the same FPS in virtual machine and without it.
and removing RAM "on the fly" is not good idea, windows does BSOD and you can damage it, so you will not be able to start it again and i think that the same is on ubuntu. unplugging and plugging RAM can also bring some dirt inside the pc, so you can damage it more than you will save the battery
i love aeon flux too and im sory for my gramar :P

---

### Post by FFred on 2010-04-19
> **aeon.flux said:**
> another thing that nobody talking about is that you can't have base system and the image of virtual machine on same disc (if you have SATA HDD), because the head in disk have to write and read on 2 places at once when you run both and that is slowing both systems and [COLOR="red"]you can break the hardisk[/COLOR]

Um ? Wut ? :confused:

While it will certainly slow the system (or both systems) somewhat, it absolutely won't break the disk. The disk will do its operations sequentially, just as it always does. There's absolutely no problem with having the virtual system and the host system on the same disk.

Of course, while a virtualized system is fine for lots of things, it's usually not a very good gaming platform. So if you want to go that way, it's probably better to virtualize Linux than the other way round (plus at one point, MS said that it wouldn't allow the virtualization of Win 7, I don't know what the current status is on that one).

---

### Post by larryfrombarrie on 2010-04-19
> **aeon.flux said:**
> if you planing to virtualize, you should now, that 1,3GHz (or even 1,3 dual core) doesn't have to be enouch for running 2 systems. I use ubuntu 9.10 (with win7 in box) and 2,5 GB ram is enough, but my 1,7GHz dual core CPU looks like it's going to explode sometimes.. : (
another thing that nobody talking about is that you can't have base system and the image of virtual machine on same disc (if you have SATA HDD), because the head in disk have to write and read on 2 places at once when you run both and that is slowing both systems and [COLOR=red]you can break the hardisk[/COLOR] (i was near to that). You should add 20-30GB of data between installing ubuntu and virtual disk. And i wouldn't remove the windows if you want to play games on M11x, because the system in virtual machine has never the same power as the base system whitch means that you can never have the same FPS in virtual machine and without it.
and removing RAM "on the fly" is not good idea, windows does BSOD and you can damage it, so you will not be able to start it again and i think that the same is on ubuntu. unplugging and plugging RAM can also bring some dirt inside the pc, so you can damage it more than you will save the battery
i love aeon flux too and im sory for my gramar :P

Well I guess dual booting is the way to go then if I want to better understand and enjoy linux, and have the alienware gaming experience too.  eh?

---

### Post by aeon.flux on 2010-04-20
> **FFred said:**
> While it will certainly slow the system (or both systems) somewhat, it absolutely won't break the disk. The disk will do its operations sequentially, just as it always does. There's absolutely no problem with having the virtual system and the host system on the same disk.

everybody knows, that HP hard drives are usually overheated(and doesn't have ANY cooling system), you can feel it when you touch pc, the corner where is CPU is never as hot as the hard drive corner.
I don't know anybody whose hard drive on HP survived more than 2 years, many people told me that it can't survive more than 1 year. Actually i'm wondering because my has almost 3 years, i can cook on it every day...

when i was using windows 7 in virtual machine for the first time, it was F**king slow, i was searching and googling whole days, what can cause it and then came my brother and told me that i can't have it on same hard drive. I moved it to external, that is connected via USB 2.0 and is not that fast as my hard drive on notebook and you would wonder, it is much faster, almost like it was base system. i could work especially when i started corel draw and illustrator at once and music and browser in ubuntu

i think that dual-booting is the best way, but i would be carefull with sharing files, it's not good to write into windows (i think NTFS) partition, because ubuntu can cause some problems (I heard that it doesn't close the files). There can be something true about that I think, because last time i was using dual boot, the windows wasn't able to read/write my personal files like music and pictures that i was using in ubuntu..

---

### Post by FFred on 2010-04-20
> **aeon.flux said:**
> i think that dual-booting is the best way, but i would be carefull with sharing files, it's not good to write into windows (i think NTFS) partition, because ubuntu can cause some problems (I heard that it doesn't close the files).
:eek:

Please do not give advice based on *one* *home* machine that you *think* uses some file system. Ubuntu is just *one* of innumerable Linux systems which I have been using for *20* f*ing years and they have been closing their files just fine for all that time.
Sharing files indeed... You don't have any clue what you're talking about.
And to the original poster, mail me if you have questions.

---

### Post by FFred on 2010-04-20
> **tahnok said:**
> I think switchable nvidia graphics are simple enough to do.

That's what you think little grasshopper.

You have much to learn. Go to the well, and fetch some water.

---

### Post by tahnok on 2010-04-21
Virtualization works flawlessly on the default CPU (SU4100) so don't worry about the 1.3 ghz processor being underpowered. Actually I haven't run into anything where the CPU is the bottleneck yet.

@FFred ya... I was hoping it'd be a simple matter of telling the system to jsut power off that piece of hardware but.... no I can't even seem to figure out how to do that!

---

### Post by night reveller on 2010-04-29
Ubuntu via VMware runs great (2048MB mem). 

I'm looking for a way to run (k)ubuntu without virtualization and preserve the long battery life. As far as I can tell, there is no solution yet, am I right?

Will be paying close attention to this thread and the group at [http://ubuntuforums.org/group.php?groupid=755](http://ubuntuforums.org/group.php?groupid=755)

---

### Post by tyoc213 on 2010-04-29
What about wubi way?


I was thinking on virtualizing ubuntu too, but I want the real thing!!... guess I will virtualize 1 for not take time of switch but with little space like 10Gb I guess.


What about the graphics controller, somebody has problems? I have read in the realese notes that because the new alternative system, the driver from nvidia site doesnt work. The default card is the intel one, how do I switch to NVIDIA in ubuntu?

---

### Post by tyoc213 on 2010-04-29
By the way, some one can confirm? under virtualbox try virtualize ubuntu, you can't select the language? hit enter... it seem that the keyboard isn't recognogized inside this virtualizator?

---

### Post by night reveller on 2010-04-30
> **tyoc213 said:**
> What about wubi way?

Installing 10.04 with Wubi works, but there are no network capabilities (both wireless and ethernet). Compiz works and performance navigating the system (menus, launching apps, etc) is noticeably better than running virtualized under VMware.

Anyone an idea on how to enable networking?

---

### Post by night reveller on 2010-04-30
> **tyoc213 said:**
> By the way, some one can confirm? under virtualbox try virtualize ubuntu, you can't select the language? hit enter... it seem that the keyboard isn't recognogized inside this virtualizator?
I had a similar problem using the 'easy install' feature of VMware: no keyboard input on the login screen. 

This worked for me: hit shift while booting, select 'recovery mode' in the GRUB menu, select 'console as root' and run 'dpkg-reconfigure console-setup'. Now reboot. 

More info on the issue: [https://bugs.launchpad.net/ubuntu/+source/xorg-server/+bug/548891](https://bugs.launchpad.net/ubuntu/+source/xorg-server/+bug/548891)

---

### Post by tyoc213 on 2010-05-01
I cant install in wubi way, I get this error [http://pastebin.com/NJAV5zAS](http://pastebin.com/NJAV5zAS) (it expire in a day).

Also I can't install it with an external DVD writer via USB, it just stay in the first purple screen (the one with 2 icons or some like that at the bottom).

Nor in VBox.

So what to do now?

---

### Post by aeon.flux on 2010-05-02
> **tahnok said:**
> Virtualization works flawlessly on the default CPU (SU4100) so don't worry about the 1.3 ghz processor being underpowered. Actually I haven't run into anything where the CPU is the bottleneck yet.

do you think, that CPU in m11x would me useful for rendering 3D models and scenes or at least for modelling, for example in Autodesk Maya 8?

---

### Post by Maquis196 on 2010-05-03
[aeon.flux]("http://ubuntuforums.org/member.php?u=900008") ; if you need raw CPU power you won't want to be using this laptop too much. If bogomips is a good indicator for you then;

```
processor       : 0                                                                                                                                                                                        
vendor_id       : GenuineIntel                                                                                                                                                                             
cpu family      : 6                                                                                                                                                                                        
model           : 23                                                                                                                                                                                       
model name      : Genuine Intel(R) CPU           U7300  @ 1.30GHz                                                                                                                                          
stepping        : 10                                                                                                                                                                                       
cpu MHz         : 1300.000                                                                                                                                                                                 
cache size      : 3072 KB                                                                                                                                                                                  
physical id     : 0                                                                                                                                                                                        
siblings        : 2                                                                                                                                                                                        
core id         : 0                                                                                                                                                                                        
cpu cores       : 2                                                                                                                                                                                        
apicid          : 0                                                                                                                                                                                        
initial apicid  : 0                                                                                                                                                                                        
fpu             : yes                                                                                                                                                                                      
fpu_exception   : yes                                                                                                                                                                                      
cpuid level     : 13                                                                                                                                                                                       
wp              : yes                                                                                                                                                                                      
flags           : fpu vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov pat pse36 clflush dts acpi mmx fxsr sse sse2 ss ht tm pbe syscall nx lm constant_tsc arch_perfmon pebs bts rep_good aperfmperf pni dtes64 monitor ds_cpl vmx est tm2 ssse3 cx16 xtpr pdcm sse4_1 xsave lahf_lm tpr_shadow vnmi flexpriority                                                                                           
bogomips        : 2600.28                                                                                                                                                                                  
clflush size    : 64                                                                                                                                                                                       
cache_alignment : 64                                                                                                                                                                                       
address sizes   : 36 bits physical, 48 bits virtual                                                                                                                                                        
power management:                                                                                                                                                                                          
                                                                                                                                                                                                           
processor       : 1
vendor_id       : GenuineIntel
cpu family      : 6
model           : 23
model name      : Genuine Intel(R) CPU           U7300  @ 1.30GHz
stepping        : 10
cpu MHz         : 1300.000
cache size      : 3072 KB
physical id     : 0
siblings        : 2
core id         : 1
cpu cores       : 2
apicid          : 1
initial apicid  : 1
fpu             : yes
fpu_exception   : yes
cpuid level     : 13
wp              : yes
flags           : fpu vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov pat pse36 clflush dts acpi mmx fxsr sse sse2 ss ht tm pbe syscall nx lm constant_tsc arch_perfmon pebs bts rep_good aperfmperf pni dtes64 monitor ds_cpl vmx est tm2 ssse3 cx16 xtpr pdcm sse4_1 xsave lahf_lm tpr_shadow vnmi flexpriority
bogomips        : 2600.02
clflush size    : 64
cache_alignment : 64
address sizes   : 36 bits physical, 48 bits virtual
power management:
```

---

### Post by Maquis196 on 2010-05-03
Hi all, been the proud owner of said m11x for a couple of months now but I have just the one issue with it;

Basically although I have sound through the headphone socket (or the 2nd one along anyway), I can't get the speakers to work.

Now I've tried a lot of things to get around this; 

I've tried the latest alsa-drivers from git but my kernel was too recent (was running 2.6.33) so I have to try and move back to 2.6.29 but it didn't see my controller properly so Ill have a look at that again.

Ran 10.04 rc2 I think it was and still nothing out the speakers. Alsamixer only reports main and pcm for me.

Does anyone else here use this laptop and the speakers? I only have noise-cancelling earphones so it's not very sociable to use them with people around me :).

Cheers,
Maquis196

---

### Post by tahnok on 2010-05-03
Someone posted a link to [HERE]("http://www.realtek.com.tw/downloads/downloadsCheck.aspx?Langid=1&PNid=14&PFid=24&Level=4&Conn=3&DownTypeID=3&GetDown=false") that lets you download realtec drivers. I just run the install script in there and reboot. My sound works after that!

---

### Post by Maquis196 on 2010-05-03
> **tahnok said:**
> Someone posted a link to [HERE]("http://www.realtek.com.tw/downloads/downloadsCheck.aspx?Langid=1&PNid=14&PFid=24&Level=4&Conn=3&DownTypeID=3&GetDown=false") that lets you download realtec drivers. I just run the install script in there and reboot. My sound works after that!


Ah cheers mate, I've already had a look at those drivers so I guess I'm gonna have to get an older kernel working. Just to confirm... you have sound on the speakers right? I swear I'm the only person on the planet with no speakers in Linux lol 

--Maquis196

---

### Post by vorob on 2010-05-07
Guys looked through this thread, but didn't find any answer. Is it possible to switch between intel and nvidia while in ubuntu? Like if we can do in windows.

---

### Post by Sum Requiem on 2010-05-07
I don't think we can yet. There is a similar technology for switching between ati-intel hybrid graphics, which some people are trying to get working with the m11x's nvidia-intel hybrid graphics but to the best of my knowledge does not work yet. I'm not really in the loop either but thats all i've been able to find.

---

### Post by aeon.flux on 2010-05-11
> **Maquis196 said:**
> if you need raw CPU power you won't want to be using this laptop too much. If bogomips is a good indicator for you then;

but i need a small laptop, because i have to work every day, even if i spend 3/4 of day in train or bus :( m11x has perfect size and price for me

---

### Post by vorob on 2010-05-15
So under ubuntu we have to use nvidia? So we won't see this magic 8 hours of battery life :)

Anyway to control cpu speed? Brightness level?
Maybe there is a way to disable nvidia and use only intel?

Btw, I'm currently playing ubuntu live from usb. And every time i shut it down i have to start all again, any way to save some singe file on my hdd or flashdrive with all changes? I don't want to install ubuntu on hdd, but wanna play around with it.

---

### Post by FFred on 2010-05-16
> **vorob said:**
> So under ubuntu we have to use nvidia? 

You can set it up with intel (I did), works fine. The nvidia driver (binary) is borked with that card at the moment anyway (even in Windows, you have to stick with the Dell tweaked one) and the intel chip is good enough for a laptop.

However the nvidia daughter board is still powered so it draws from the battery even when you don't use it so battery life while not *too* bad isn't great.

---

### Post by warfacegod on 2010-05-16
> **vorob said:**
> So under ubuntu we have to use nvidia? So we won't see this magic 8 hours of battery life :)

Anyway to control cpu speed? Brightness level?
Maybe there is a way to disable nvidia and use only intel?

Btw, I'm currently playing ubuntu live from usb. And every time i shut it down i have to start all again, any way to save some singe file on my hdd or flashdrive with all changes? I don't want to install ubuntu on hdd, but wanna play around with it.

If I were you, I'd boot Live with a CD and then use the USB Startup Disk Creator being sure that Stored in reserved extra space is checked and that the slider is set to the amount of space you want. You'll have to tell it to use the .iso on you HDD if you still have it. If not, download another copy because you won't be able to tell it to use the CD your running on.

---

### Post by vorob on 2010-05-20
Hi, I've got some news on videocard switch, found it on one russian page, sorry for automatic translation:

[http://translate.google.ru/translate?js=y&prev=_t&hl=ru&ie=UTF-8&layout=1&eotf=1&u=http%3A%2F%2Fhabrahabr.ru%2Fblogs%2Fubuntu%2F94032%2F&sl=auto&tl=en](http://translate.google.ru/translate?js=y&prev=_t&hl=ru&ie=UTF-8&layout=1&eotf=1&u=http%3A%2F%2Fhabrahabr.ru%2Fblogs%2Fubuntu%2F94032%2F&sl=auto&tl=en)

Most interesting is part 2:

**Some time ago a new kernel version 2.6.1934 was released, which includes a new cool plugin - vga_switcheroo, which is precisely designed to switch the video card.**

And then we can see a lot of stuff, i'm not good in this thing but maybe it will orient you to make some guide for alienware to have switch option. Thx.

---

### Post by anand00x on 2010-05-22
What is the minimum amount of space recommended for an umbuntu 10.04 partition? I have 14GB left on my SSD windows 7 partition. I can shrink my drive what is the minimum amount of space I can sacrifice while still leaving some space on my windows 7 partition? I was also going to dedicate 1GB to the SWAP partition. Thanks

---

### Post by warfacegod on 2010-05-22
I had 9.10 Karmic and UNR working quite well in a 5 GB partition. 10.04 installs at about the same size as 9.10. Generally an absolute minimum partition size is considered to be 10 GB.

---

### Post by soleblaze on 2010-05-24
> **vorob said:**
> Hi, I've got some news on videocard switch, found it on one russian page, sorry for automatic translation:

[http://translate.google.ru/translate?js=y&prev=_t&hl=ru&ie=UTF-8&layout=1&eotf=1&u=http%3A%2F%2Fhabrahabr.ru%2Fblogs%2Fubuntu%2F94032%2F&sl=auto&tl=en](http://translate.google.ru/translate?js=y&prev=_t&hl=ru&ie=UTF-8&layout=1&eotf=1&u=http%3A%2F%2Fhabrahabr.ru%2Fblogs%2Fubuntu%2F94032%2F&sl=auto&tl=en)

Most interesting is part 2:

**Some time ago a new kernel version 2.6.1934 was released, which includes a new cool plugin - vga_switcheroo, which is precisely designed to switch the video card.**

And then we can see a lot of stuff, i'm not good in this thing but maybe it will orient you to make some guide for alienware to have switch option. Thx.

yeah, I've tried vga-switcheroo.  It doesn't work for nvidia cards yet, just ATI.  The author doesn't have access to an nvidia machine.  I'm guessing the release of optimus will also decrease the amount of time someone would want to spend on it.

---

### Post by night reveller on 2010-05-24
Hi all,

Is anyone also experiencing a big difference in wireless signal strength between Ubuntu and Windows?

The typing lag when connecting to servers via SSH is unworkable when using Ubuntu, while in Windows using PuTTY everything is responsive. Quite a PITA :(

Running Lucid Lynx and the Broadcom 802.11 Linux STA drivers from [http://www.broadcom.com/support/802.11/linux_sta.php](http://www.broadcom.com/support/802.11/linux_sta.php)

Any ideas on how to improve?

Thanks!

---

### Post by juanoleso on 2010-05-25
I've got something that I thought I would ask about, too.  I've got the graphics set to discrete in the bios and I am using the Nvidia drivers from the ubuntu repos.  Is there a way to switch outputs using the fn+F1 key?  Mine doesn't/hasn't worked.

I would like to be able to switch to a TV at 1900x1080 out of the HDMI on the fly.  Volume and brightness both work with the fn+function keys OOTB.  OC it works in windows...

looking forward to any news on VGA_Switcheroo


What are you guys's thoughts on the core i's going into the M11x later this year?  I kind of wish I would've held out a little longer, but then I wonder if I would've ever boughten it.  Also, I don't think the performance increase would be worth price, but its hard to tell.

---

### Post by davidcyber00 on 2010-05-25
how do i get my computer to boot automatically?

---

### Post by moondoggy2 on 2010-05-26
I'm a relative n00b to the Linux world.  I to have an AlienWare m11x, running Karmic Koala.  I installed 9.10, and everything worked perfectly, except the sound.  I dicked around a bit, and got it working.  Then I decided to upgrade to Lucid.  Everything went perfectly, except the sound.  Again, I dicked around, and finally got it weorking,  I finally opted to go back to Karmic, because of the lack of support for the new release, (10.04 LTS).  So, here I am agaion with 9.10, and no audio.  The trouble is, I can't remember what the Hell I did to get the sound working in the first place.  I've been going thru all the step-by-steps, all the tutorials, and forums.  Some of it looks familiar, some of it doesn't.  I've tried everything I can think of, and/or found on here, and am still at a loss.  Any suggestions?

---

### Post by juanoleso on 2010-05-27
> **soleblaze said:**
> Got the sound working.  Looks like the only working driver at the moment for the ALC665 is on the realtek site [here](http://www.realtek.com.tw/downloads/downloadsCheck.aspx?Langid=1&PNid=14&PFid=24&Level=4&Conn=3&DownTypeID=3&GetDown=false).  Just need to download the Linux driver, extract it and follow the instructions on how to manually install it.  (You'll need to install build-essentials if you don't already have that installed)

I got the sound working per the instructions above.

---

### Post by Pollywoggy on 2010-05-27
> **juanoleso said:**
> I got the sound working per the instructions above.

I got one of these a few days ago and did not really intend to install Linux on it though it was something I might try.  This morning, I decided to try it and it worked.  I booted to Ubuntu Lucid but did not really check to be sure everything worked.  I rebooted to Windows 7 and Windows 7 did a filesystem check.  Later, I rebooted and the computer does not work at all, I can't boot anything.  Windows 7 apparently does not like to play nice with other operating systems and I am using the backup disk to reinstall.

This machine is for gaming, so the only big disappointment is that I need to reinstall Windows 7 and all the drivers, etc, from Dell, then my game.

My advice is not to try this if you don't know what you are doing.  I am unable to return the drive space I used for Ubuntu to Windows 7 because none of the disks that have gparted will boot on this machine.  If I want to return the drive space to Windows 7, I will have to buy PartitionMagic.

---

### Post by bendinger on 2010-05-28
Hi,

anyone tried installing CUDA toolkit and SDK? Is it working? 
I am looking for a subnotebook with a decent nvidia card (1.2 cuda at least) to develop cuda programs on the go. Alienware m11x is very interesting machine, but for my needs it is perfect. (72 core instead of 48 (gt330m) and 1GB gddr3)

Thanks!

---

### Post by moondoggy2 on 2010-05-28
> **juanoleso said:**
> I got the sound working per the instructions above.


Thanks.  Everything is working perfectly now!!  :)

---

### Post by juanoleso on 2010-05-28
> **Pollywoggy said:**
> Later, I rebooted and the computer does not work at all, I can't boot anything.

I had similar trouble.  For posterity, I used Super Grub Disk to boot into the existing Ubuntu I had.  Then I uninstalled "grub"(grub 2) and installed "grub-legacy"(grub 1).  Reinstalled the boot member and managed my menu.lst and I was good to go.

> **Pollywoggy said:**
> I am unable to return the drive space I used for Ubuntu to Windows 7 because none of the disks that have gparted will boot on this machine.  If I want to return the drive space to Windows 7, I will have to buy PartitionMagic.

That is strange.  I'm pretty sure that the windows 7 recovery disk can delete and format those partitions.

---

### Post by Sub101 on 2010-05-31
Just to clarify; the main issues are:

1. Speakers require installing Realtek driver
2. Changing the colouring is difficult but can be achieved with AlienFX
3. No switching between Intel and Nvidia graphics.

Is there anything else?

---

### Post by Bushman87 on 2010-06-01
I just uninstalled the dell local safe backup and I havent had issues with grub 2 since. I read somewhere (couldnt remember the google keywords :-)) that certain Windows programs causes grub 2 to become unstable. I think they mentioned the HP laptops that came with a program called angel something (dont own one so stabbing in the dark...) and they uninstalled the program and reinstalled grub 2.

I have had ubuntu for about 5 days now and the grub loader hasnt given me issues since.

Im still a noob ubuntu user, so does anyone have any posts or websites where they set out how to pimp grub 2 for a noob? I googled it but the program they suggest doesnt give me options to do it and the command lines they give make me scared... :P.

---

### Post by Pollywoggy on 2010-06-02
> **juanoleso said:**
> I had similar trouble.  For posterity, I used Super Grub Disk to boot into the existing Ubuntu I had.  Then I uninstalled "grub"(grub 2) and installed "grub-legacy"(grub 1).  Reinstalled the boot member and managed my menu.lst and I was good to go.



That is strange.  I'm pretty sure that the windows 7 recovery disk can delete and format those partitions.


I was able to boot a 32 bit Ubuntu 9.10 CD and then run gparted and delete everything.  I then made an NTFS partition and then reinstall Windows 7.  I won't try putting Linux on this again since I think Windows 7 wants to be the only OS.  

The Windows 7 recovery disk can format the partitions but I did not know it at the time.

---

### Post by night reveller on 2010-06-03
> **night reveller said:**
> Hi all,

Is anyone also experiencing a big difference in wireless signal strength between Ubuntu and Windows?

The typing lag when connecting to servers via SSH is unworkable when using Ubuntu, while in Windows using PuTTY everything is responsive. Quite a PITA :(

Running Lucid Lynx and the Broadcom 802.11 Linux STA drivers from [http://www.broadcom.com/support/802.11/linux_sta.php](http://www.broadcom.com/support/802.11/linux_sta.php)

Any ideas on how to improve?

Thanks!


I decided to replace the Broadcom Wifi chip with an Intel Wireless-N 1000. Price: 15 euros. Just take off the backplate and swap the chip. There is also room for an additional full size chip.

The improvement in signal and speed is remarkable.

---

### Post by night reveller on 2010-06-03
My only problem now with Ubuntu on the m11x is battery time. How can I help to reach a solution in this? What is the status of VGA_switcheroo? Can I help debug/program for this?

---

### Post by tahnok on 2010-06-08
Does anyone know if the inclusion of Optimus will help with the battery situation in linux?

---

### Post by Sub101 on 2010-06-08
> **tahnok said:**
> Does anyone know if the inclusion of Optimus will help with the battery situation in linux?

I would say no, at least not yet. The drivers look like they are all for Windows so far. Of course this may change.

[http://www.nvidia.com/object/optimus_technology.html](http://www.nvidia.com/object/optimus_technology.html)

---

### Post by nasrullahs on 2010-06-10
Im pretty sure i got the nvidia card to turn off...im not completely sure cause i dont know how to measure the power usage, but the temperature drops from ~40 C when the nvidia card is on to ~30 when its off.

I used the code from [http://ubuntuforums.org/showthread.php?t=1366605](http://ubuntuforums.org/showthread.php?t=1366605) thats for asus UL laptops, and changed the 
"status = acpi_get_handle(root_handle, "\\_SB.PCI0.P0P1.VGA._OFF",  &handle);" on line 39
to 
"status = acpi_get_handle(root_handle, "\\_SB.PCI0.P0P2.PEGP._OFF", &handle);"

Also, the instructions on compiling it on the didnt work for me, so i had to follow these instructions:
"ar x *.deb
then
tar xzf data.tar.gz
then go to usr/src/
then 
tar xzf nvidia-*.tar.gz"

then, to change it to work for the m11x, edit dkms_source_tree/nvidia_g210m_acpi.c line 39

then
"make

sudo cp nvidia_g210m_acpi.ko /lib/modules/`uname -r`/kernel/
sudo depmod

To try it out:

sudo modprobe nvidia_g210m_acpi"

If anyone has a way to measure power usage of your m11x, lemme know if this actually works.

UPDATE: fixed copy instruction that said "asus_nvidia.ko" to "nvidia_g210m_acpi.ko"

---

### Post by Sub101 on 2010-06-10
> **nasrullahs said:**
> Im pretty sure i got the nvidia card to turn off...im not completely sure cause i dont know how to measure the power usage, but the temperature drops from ~40 C when the nvidia card is on to ~30 when its off.

I used the code from [http://ubuntuforums.org/showthread.php?t=1366605](http://ubuntuforums.org/showthread.php?t=1366605) thats for asus UL laptops, and changed the 
"status = acpi_get_handle(root_handle, "\\_SB.PCI0.P0P1.VGA._OFF",  &handle);" on line 39
to 
"status = acpi_get_handle(root_handle, "\\_SB.PCI0.P0P2.PEGP._OFF", &handle);"

Also, the instructions on compiling it on the didnt work for me, so i had to follow these instructions:
"ar x *.deb
then
tar xzf data.tar.gz
then go to usr/src/
then 
tar xzf nvidia-*.tar.gz"

then, to change it to work for the m11x, edit dkms_source_tree/nvidia_g210m_acpi.c line 39

then
"make

sudo cp asus_nvidia.ko /lib/modules/`uname -r`/kernel/
sudo depmod

To try it out:

sudo modprobe nvidia_g210m_acpi"

If anyone has a way to measure power usage of your m11x, lemme know if this actually works.

Looks very interesting. I will have a go with it when I get home. 

As I understand it the new vga-switcheroo is out in kernel ending 35. Will havve to wait and see.

---

### Post by Larry Owens on 2010-06-11
@Sub101

I used your post to install the nvidia_g210m_acpi kernel module with line 39 modified per your instructions.  I confirm that power utilization has fallen from approximately 19W to approximately 11W immediately after loading the module.

BTW, I am using Ubuntu Lucid 10.04 LTS, and I am measuring the power drain using the built-in battery indicator applet.  Left click on the battery icon and choose the top menu item "Laptop battery XX minutes left" to display the Power Statistics application.  Choose the "History" notebook tab to show graphs.  For the graph type select "Rate".  It will display a graph of power utilized over time.  Load the kernel module and watch the power utilization fall (graph clearly shows this within about 2 minutes).

Slight correction to the installation directions: copy the "nvidia_g210m_acpi.ko" file into your kernel modules directory.  The directions specified "asus_nvidia.ko".

It is wonderful to get about 6 hours out of the M11X running GNU/Linux with the nvidia chipset turned off.  Excellent work!

---

### Post by nasrullahs on 2010-06-11
> **soleblaze said:**
> got brightness on switchable working:

as root:

edit /etc/default/grub. change GRUB_CMDLINE_LINUX_DEFAULT="quiet splash" to GRUB_CMDLINE_LINUX_DEFAULT="quiet splash nomodeset acpi_backlight=vendor"

Save that then run update-grub. After that and a reboot you should be able to change the brightness just fine.  You have a lot more steps in the brightness than you do in windows.

I tried this and compiz stopped working. Do u know of any way to change brightness and still have compiz work?

---

### Post by greniesa on 2010-06-14
> **nasrullahs said:**
> Im pretty sure i got the nvidia card to turn off...im not completely sure cause i dont know how to measure the power usage, but the temperature drops from ~40 C when the nvidia card is on to ~30 when its off.

I used the code from [http://ubuntuforums.org/showthread.php?t=1366605](http://ubuntuforums.org/showthread.php?t=1366605) thats for asus UL laptops, and changed the 
"status = acpi_get_handle(root_handle, "\\_SB.PCI0.P0P1.VGA._OFF",  &handle);" on line 39
to 
"status = acpi_get_handle(root_handle, "\\_SB.PCI0.P0P2.PEGP._OFF", &handle);"

Also, the instructions on compiling it on the didnt work for me, so i had to follow these instructions:
"ar x *.deb
then
tar xzf data.tar.gz
then go to usr/src/
then 
tar xzf nvidia-*.tar.gz"

then, to change it to work for the m11x, edit dkms_source_tree/nvidia_g210m_acpi.c line 39

then
"make

sudo cp nvidia_g210m_acpi.ko /lib/modules/`uname -r`/kernel/
sudo depmod

To try it out:

sudo modprobe nvidia_g210m_acpi"

If anyone has a way to measure power usage of your m11x, lemme know if this actually works.

UPDATE: fixed copy instruction that said "asus_nvidia.ko" to "nvidia_g210m_acpi.ko"


When I try to compile the module, make return me "nothing to do with Default". (this is a traduction from french). Do you have any idea...

--------------------------------------------------------------------
alienware_nvidia.c
--------------------------------------------------------------------
#include <acpi/acpi.h>
#include <linux/suspend.h>

MODULE_LICENSE("GPL");

static acpi_handle root_handle;

static int kill_nvidia(void)
{
acpi_status status;
// The device handle
acpi_handle handle;
struct acpi_object_list args;
// For the return value
struct acpi_buffer buffer = { ACPI_ALLOCATE_BUFFER, NULL };

status = acpi_get_handle(root_handle, "\\_SB.PCI0.P0P2.PEGP._OFF", &handle);
if (ACPI_FAILURE(status))
{
printk("%s: cannot get ACPI handle: %s\n", __func__, acpi_format_exception(status));
return -ENOSYS;
}

args.count = 0;
args.pointer = NULL;

status = acpi_evaluate_object(handle, NULL, &args, &buffer);
if (ACPI_FAILURE(status))
{
printk("%s: _OFF method call failed: %s\n", __func__, acpi_format_exception(status));
return -ENOSYS;
}
kfree(buffer.pointer);

printk("%s: disabled the discrete graphics card\n",__func__);
return 0;
}

static int power_event(struct notifier_block *this, unsigned long event,
void *ptr)
{
switch (event) {
case PM_POST_HIBERNATION:
kill_nvidia();
return NOTIFY_DONE;
case PM_POST_SUSPEND:
case PM_HIBERNATION_PREPARE:
case PM_SUSPEND_PREPARE:
default:
return NOTIFY_DONE;
}
}

static struct notifier_block power_notifier = {
.notifier_call = power_event,
};

static int __init alienware_nvidia(void)
{
int ret = register_pm_notifier(&power_notifier);
if (ret) return ret;
return kill_nvidia();
}

static void dummy(void)
{
}

module_init(alienware_nvidia);
module_exit(dummy);

-----------------------------------------------------------------
Makefile
-----------------------------------------------------------------

ifneq ($(KERNELRELEASE),)
obj-m := alienware_nvidia.o
else
KERNELDIR ?= /lib/modules/$(shell uname -r)/build
PWD := $(shell pwd)

default:
$(MAKE) -C $(KERNELDIR) M=$(PWD) $(EXTRA_FLAGS) modules

clean:
$(MAKE) -C $(KERNELDIR) M=$(PWD) $(EXTRA_FLAGS) clean

endif

------------------------------------------------------------------

thanks for your help!

---

### Post by greniesa on 2010-06-14
For those like me that try to install the audio driver, here's the working link:

[http://www.realtek.com/Downloads/downloadsCheck.aspx?Langid=1&PNid=14&PFid=24&Level=4&Conn=3&DownTypeID=3&GetDown=false](http://www.realtek.com/Downloads/downloadsCheck.aspx?Langid=1&PNid=14&PFid=24&Level=4&Conn=3&DownTypeID=3&GetDown=false)

---

### Post by nasrullahs on 2010-06-14
@[greniesa]("http://ubuntuforums.org/member.php?u=559502")

Try this makefile:

-----------------------------------------------------------------
Makefile
-----------------------------------------------------------------

ifneq ($(PATCHLEVEL),)
  obj-m    := alienware_nvidia.o
else
  KDIR ?= /lib/modules/$(shell uname -r)/build
  PWD := $(shell pwd)

all:
    $(MAKE) -C $(KDIR) M=$(PWD) modules

install: all
    $(MAKE) -C $(KDIR) M=$(PWD) modules_install
    /sbin/depmod -a

clean:
    rm -rf .*.cmd  *.mod.c *.ko *.o modules.order Module.markers Module.symvers .tmp_versions

endif
 -----------------------------------------------------------------

Also, just noticed, u need a dkms.conf file, I had this in mine:
 -----------------------------------------------------------------
dkms.conf
 -----------------------------------------------------------------
PACKAGE_NAME="alienware-nvidia"
PACKAGE_VERSION="0.1.0"

CLEAN="make clean"
BUILT_MODULE_NAME[0]="alienware_nvidia"
DEST_MODULE_LOCATION[0]="/kernel/drivers/acpi"
MAKE[0]="make"
AUTOINSTALL="yes"
 -----------------------------------------------------------------

---

### Post by greniesa on 2010-06-15
@nasrullahs

First of all, thanks a lot for your help! I really appreciate that.

I have a little progress , now it tell me this:

> make[1]: entrant dans le répertoire « /usr/src/linux-headers-2.6.32-22-generic »
make[1]: *** Pas de règle pour fabriquer la cible « M11X/Turn ». Arrêt.
make[1]: quittant le répertoire « /usr/src/linux-headers-2.6.32-22-generic »
make: *** [all] Erreur 2

traduction:
> 
make[1]: *** There is no rules to make this "target" « M11X/Turn ». Stop.
## sorry about target I don't know if it's the real word in english.


any suggestion?

EDIT: Sorry for that I understand now... This is my path that have space in it... :S... sorry for that.

---

### Post by greniesa on 2010-06-15
Hello community,

I want to know, am I the only one that have an Internet speed problem? When I download my max speeds is 24Ko/sec insted of 350Ko/sec.

So is it a problem with my network or someone else have this problem?

I don't have any idea of what output I can show to help some of you to give a diagnostic, but ask and I will post them.

EDIT: Same speed on Ethernet than WiFi

---

### Post by mcvf on 2010-06-20
> **greniesa said:**
> For those like me that try to install the audio driver, here's the working link:

[http://www.realtek.com/Downloads/downloadsCheck.aspx?Langid=1&PNid=14&PFid=24&Level=4&Conn=3&DownTypeID=3&GetDown=false](http://www.realtek.com/Downloads/downloadsCheck.aspx?Langid=1&PNid=14&PFid=24&Level=4&Conn=3&DownTypeID=3&GetDown=false)

That links always gets me nowhere, maybe Realtek changed something on their site.

Although, I would like to report that new kernel update (2.6.32-23) probably updated also ALSA and now it does sound out of box - more exactly after kernel update.

---

### Post by m1 grant on 2010-06-22
So has anyone tried the optimus refresh of the m11x on ubuntu? Optimus is supposed to make all of the GPU switching decisions via hardware, so that should make it work in linux so long as drivers exist for both GPUs and I believe they do.

---

### Post by patchwerkadams on 2010-06-22
Hey guys, I just picked up my M11X and I'm actually a relatively new Linux user. I managed to install Ubuntu 10.04 however my wireless card isn't working. My lspci says that my wireless adapter is made by Atheros Communications but when I try lsmod there are ath modules loaded at all. Any idea on what could be going on? Any help would be greatly appreciated.

---

### Post by tahnok on 2010-06-22
You probably need to enable restricted (read: proprietary) drivers. It's usually pretty easy. I think it's under System->Administration->Hardware

---

### Post by Sub101 on 2010-06-22
> **patchwerkadams said:**
> Hey guys, I just picked up my M11X and I'm actually a relatively new Linux user. I managed to install Ubuntu 10.04 however my wireless card isn't working. My lspci says that my wireless adapter is made by Atheros Communications but when I try lsmod there are ath modules loaded at all. Any idea on what could be going on? Any help would be greatly appreciated.

Update with an ethernet cable connected and should work fine. It will give the option to install restricted drivers.

---

### Post by patchwerkadams on 2010-06-22
Actually, now I have an even bigger problem. When I go to restart it says that it's unable to locate a module name and tells me to hit any key to continue. When I hit a key it says that there is nothing for Atheros Communications ethernet controller and then restarts...this happens before GRUB even boots so I'm not sure what's going on.

---

### Post by patchwerkadams on 2010-06-23
I managed to resolve my previous problem...I believe it was the Dell backup software that was causing the issue. I removed it from Windows 7 and haven't had a problem with it since.

However, I'm currently using the Intel video card and I'm having issues with the brightness. I managed to get it working using the grub configuration mentioned several pages ago but whenever I unplug the computer the brightness level drops and that becomes the new maximum brightness of the screen. Is anyone else experiencing this? I haven't installed any video card drivers for the Intel card yet...do I need to? Or does Ubuntu install them by default? Bear in mind, I've only been using Linux for a few months now so I'm not sure of the ins an outs quite yet.

As an alternative, I was wondering if there was anyway to force Ubuntu to use the nVidia card when the graphics are set to switchable?

Any help would be greatly appreciated.

---

### Post by datniceguy on 2010-06-24
Just registered. Hopefully using Ubuntu on my m11x will open me up more to the Linux/GNU life. Anyone know how to shut off the keyboard backlights?

---

### Post by portendingennui on 2010-07-02
Hello,

I have recently received an R2 of the M11x and it seems the Bios does not have the Graphics Mode BIOS option.  How do I switch to Discrete to use Compiz, etc, with the new R2?

Once I installed the proprietary Nvidia drivers, I was getting the blackscreen on boot so i had to add the nomodeset to the Grub.

Any help is appreciated

---

### Post by Sub101 on 2010-07-02
> **portendingennui said:**
> Hello,

I have recently received an R2 of the M11x and it seems the Bios does not have the Graphics Mode BIOS option.  How do I switch to Discrete to use Compiz, etc, with the new R2?

Once I installed the proprietary Nvidia drivers, I was getting the blackscreen on boot so i had to add the nomodeset to the Grub.

Any help is appreciated

Doesnt the R2 use Optimus?

If it does then I would be suprised if there was a way to set the card to one or other, as the switch is done based on the load on the hardware. To my knowledge Ubunut cannot switch between graphics cards without at a minimum restarting X.

---

### Post by portendingennui on 2010-07-03
> **Sub101 said:**
> Doesnt the R2 use Optimus?

If it does then I would be suprised if there was a way to set the card to one or other, as the switch is done based on the load on the hardware. To my knowledge Ubunut cannot switch between graphics cards without at a minimum restarting X.

Yep, so I'm SOL for now?  If i go to the NVIDIA X Server Settings it warns "You do not appear to be using the NVIDIA X Driver.  Please edit your X configuration file (just run 'nvidia-xconfig' as root), and restart the X server."

So I perform this step and it says a new configuration file is created and to restart the X server.
So I restart the X server and I'm back to the same problem, solid black screen on boot.

It seems like the option to force discrete mode was removed from the BIOS because of Optimus.  Is there no way at this time to use the Nvidia card/driver?

---

### Post by Sub101 on 2010-07-03
> **portendingennui said:**
> Yep, so I'm SOL for now?  If i go to the NVIDIA X Server Settings it warns "You do not appear to be using the NVIDIA X Driver.  Please edit your X configuration file (just run 'nvidia-xconfig' as root), and restart the X server."

So I perform this step and it says a new configuration file is created and to restart the X server.
So I restart the X server and I'm back to the same problem, solid black screen on boot.

It seems like the option to force discrete mode was removed from the BIOS because of Optimus.  Is there no way at this time to use the Nvidia card/driver?

Id take a look here.

[https://launchpad.net/~hybrid-graphics-linux](https://launchpad.net/~hybrid-graphics-linux)

Optimus is very new so may need to give it time.

---

### Post by corwinspyre on 2010-07-04
> **Sub101 said:**
> Doesnt the R2 use Optimus?

If it does then I would be suprised if there was a way to set the card to one or other, as the switch is done based on the load on the hardware. To my knowledge Ubunut cannot switch between graphics cards without at a minimum restarting X.

What you say is not true.  Optimus does not detect the current load and switch because of it; that is a common misconception.  Optimus has a list of programs, and when any of these programs run, it changes to the higher-powered GPU (335m in the case of the M11X) to render the frames.  This information is from the whitepaper nVidia has on its page on Optimus.

I do agree it will probably be harder to code or will at least involve more than the older generation of hybrid GPUs because it involves a different hardware layout.  With standard hybrid GPUs, whichever GPU is active does both the rendering and displaying while the other is completely powered off.  With Optimus, the system switches which GPU does the rendering, but the IGP always does the displaying.  With the M11X, when the 335m is running, it renders the frames and then passes them to the Intel GPU to send to the screen.  When the IGP is running, it both renders and displays with the 335m completely off.

edit: Just thinking about it some more, perhaps its design will mean it will be easier.  I know in Windows the M11X R1 has to deal with switching between drivers, while the R2 uses only one driver by design.  
And maybe we'll get lucky and nVidia will release a Linux driver supporting Optimus soon.

---

### Post by vorob on 2010-07-04
Any news? Any good way to turn off nvidia and use intel with long battery life?

---

### Post by Rain724 on 2010-07-06
> **vorob said:**
> Any news? Any good way to turn off nvidia and use intel with long battery life?Thats all I would like to do also. I would use Windows for any games I would like to play, but when I am in Ubuntu (or some other flavor of linux) I would not need the Nvidia 335M and would love to be able to just "turn if off" for longer battery life.

---

### Post by fnord0 on 2010-07-07
give this a try: [acpi_call]("http://github.com/mkottman/acpi_call") kernel module, seems to be working here (R1 m11x). this is what I did ::

> [B]git clone [http://github.com/mkottman/acpi_call.git](http://github.com/mkottman/acpi_call.git)
cd acpi_call
make
ln -s acpi_call.ko /lib/modules/`uname -r`/kernel/drivers/acpi/acpi_call.ko
depmod -a
modprobe acpi_call
grep rate /proc/acpi/battery/BAT1/state
echo '\_SB.PCI0.P0P2.PEGP._OFF' > /proc/acpi/call
grep rate /proc/acpi/battery/BAT1/state[/B]

NOTE: run the script '**acpi_call/test_off.sh**' if the above echo call doesn't work on yours.


---

### Post by patchwerkadams on 2010-07-15
Is anyone else having an issue with the brightness on the Core2 Duo model? I can't seem to control the brightness on mine at all. Whenever my laptop is plugged in it's fine but if I boot it up without the power cord the brightness is much lower than what it would normally be and for some reason Ubuntu takes that to be the maximum screen brightness so I can't turn it up any more.

---

### Post by JailHouseRock on 2010-07-16
> **fnord0 said:**
> give this a try: [acpi_call]("http://github.com/mkottman/acpi_call") kernel module, seems to be working here (R1 m11x). this is what I did ::

Didn't seem to work for me, I also have a R1.

I got this spit at me:

```
Initialized empty Git repository in /home/user/git/acpi_call/.git/
remote: Counting objects: 21, done.
remote: Compressing objects: 100% (19/19), done.
remote: Total 21 (delta 6), reused 0 (delta 0)
Unpacking objects: 100% (21/21), done.
make -C /lib/modules/2.6.32-22-generic/build M=/home/user/git/acpi_call modules
make[1]: Entering directory `/usr/src/linux-headers-2.6.32-22-generic'
  CC [M]  /home/user/git/acpi_call/acpi_call.o
  Building modules, stage 2.
  MODPOST 1 modules
  CC      /home/user/git/acpi_call/acpi_call.mod.o
  LD [M]  /home/user/git/acpi_call/acpi_call.ko
make[1]: Leaving directory `/usr/src/linux-headers-2.6.32-22-generic'
ln: accessing `/lib/modules/2.6.32-22-generic/kernel/drivers/acpi/acpi_call.ko': Too many levels of symbolic links
WARNING: Can't read module /lib/modules/2.6.32-22-generic/kernel/drivers/acpi/acpi_call.ko: Too many levels of symbolic links
FATAL: Module acpi_call not found.
present rate:            19402 mW
stuff: 9: cannot create /proc/acpi/call: Directory nonexistent
present rate:            19402 mW
```The "FATAL: Module acpi_call not found." doesn't sound good, am I missing dependencies or something like that?

And after running acpi_call/test_off.sh I got this.
```
The acpi_call module is not loaded
```


edit: I always get things working right after I finally decide to post.

When I did this:
```
git clone [http://github.com/mkottman/acpi_call.git](http://github.com/mkottman/acpi_call.git)
cd acpi_call
make
sudo insmod acpi_call.ko
./test_off.sh
```

And then this:
```
grep rate /proc/acpi/battery/BAT1/state
```

It gave me:
```
present rate:            12256 mW
```

Before it was 19402 mW, as far as I can tell that means it worked.

---

### Post by corwinspyre on 2010-07-19
> **patchwerkadams said:**
> Is anyone else having an issue with the brightness on the Core2 Duo model? I can't seem to control the brightness on mine at all. Whenever my laptop is plugged in it's fine but if I boot it up without the power cord the brightness is much lower than what it would normally be and for some reason Ubuntu takes that to be the maximum screen brightness so I can't turn it up any more.

Did you try the brightness fix via grub boot option listed in this thread?  If that didn't work, there is another fix on Arch distro's wiki to control brightness with the IGP [http://wiki.archlinux.org/index.php/Alienware_M11x#backlight_brightness](http://wiki.archlinux.org/index.php/Alienware_M11x#backlight_brightness)

---

### Post by tyoc213 on 2010-07-28
After not being able to install it in the first place... I come back and have done an USB drive with casper.

The problem is that aparently I cant activate the restricted drivers wireless and NVIDIA card.

Thought I m able to connect now  to the wireless LAN (I think the driver is installed, just that the app doesnt know it is active, I have installed the nvidia drivers from the restricted app but for the moment they dont seem active, lets see in restart?).

I will like to know how many is the aprox penalty for run it from an USB? because updating the stystem after downloading the things has already taked to long... like an our I think perhaps more.

---

### Post by tyoc213 on 2010-07-28
Y also dont have sound... if somebody can help.

---

### Post by Sub101 on 2010-07-28
> **tyoc213 said:**
> Y also dont have sound... if somebody can help.

You need the drivers found here; [http://218.210.127.131/downloads/downloadsView.aspx?Langid=1&PNid=24&PFid=24&Level=4&Conn=3&DownTypeID=3&GetDown=false](http://218.210.127.131/downloads/downloadsView.aspx?Langid=1&PNid=24&PFid=24&Level=4&Conn=3&DownTypeID=3&GetDown=false)

You also need to follow the instructions in the readme, rather than running the install script.

---

### Post by Sub101 on 2010-07-28
> **tyoc213 said:**
> After not being able to install it in the first place... I come back and have done an USB drive with casper.

The problem is that aparently I cant activate the restricted drivers wireless and NVIDIA card.

Thought I m able to connect now  to the wireless LAN (I think the driver is installed, just that the app doesnt know it is active, I have installed the nvidia drivers from the restricted app but for the moment they dont seem active, lets see in restart?).

I will like to know how many is the aprox penalty for run it from an USB? because updating the stystem after downloading the things has already taked to long... like an our I think perhaps more.

Sorry, do you mean you have installed the wireless driver? If not then you need to plug into an ethernet cable to install the restricted driver.

As for the nvidia driver I cant help. I use the intel graphics card rather than the nvidia and have that one turned off to save power.

---

### Post by tyoc213 on 2010-07-28
I think they are installed, because actually Im connected via wireless... (thouth the restricted driver applications dosent show green).

I have sound, thx.


I attach the errors Im geting about the diferent driver installs.

---

### Post by Philip550c on 2010-07-30
> **mcvf said:**
> That links always gets me nowhere, maybe Realtek changed something on their site.

Although, I would like to report that new kernel update (2.6.32-23) probably updated also ALSA and now it does sound out of box - more exactly after kernel update.

Just click the link back one menu item "High Definition Audio Codecs" and work your way forwards.

---

### Post by ElMuggo on 2010-08-01
Hi guys, got a brand new R2 i7 m11x with 8 gigs ram on Friday.
Installed Ubuntu x86 twice (bricked it the first time by accidentally activating nvidia graphics woops!) and noticed a oddity that while it showed 7.5 gigs ram the first time it now only shows 1.9 gigs ram! Yet I haven't noticed any performance change between the two installs... it's still fast as hell and blows Win7 away like nothing!

also with the sound issues it still doesn't work out of the box and while I've done the realtek drivers install, followed the readme and checked everything it all appears fine, is not muted and yet still no volume coming from the speakers (oddly enough output to my tv is fine) 

only other issue so far is that hdmi output seems to be missing the yellow channel, everythings green/purple. I know it's not the lead/tv because Win 7 did output fine... curiouser and curiouser..

---

### Post by patchwerkadams on 2010-08-04
I just did a system update and my touchpad is acting crazy. If I accidentally touch two points on the pad the cursor starts to jump all over the place. Is anyone else having this problem? I was wondering if I have to install different touchpad drivers or something.

---

### Post by tahnok on 2010-08-04
It's always done the touchpad thing for me. Not sure if there is any way to fix it.

---

### Post by ElMuggo on 2010-08-14
> **tahnok said:**
> It's always done the touchpad thing for me. Not sure if there is any way to fix it.

It's probably just set to be too sensitive. 

Try checking System > Mouse and set the Pointer Speed Acceleration and Sensitivity down. 

[GPointing]("http://live.gnome.org/GPointingDeviceSettings") might help out too as it's got settings for palm detection.

---

### Post by kattandpeist on 2010-09-03
I have a m11x-R2 i installed the nvidia driver and when i booted all i had is a blank screen. Is there any way of solve it?

---

### Post by tahnok on 2010-09-03
You may have to go into the bios and set it to always use dedicated graphics. Otherwise it will try and use the intel card

---

### Post by kattandpeist on 2010-09-03
> **tahnok said:**
> You may have to go into the bios and set it to always use dedicated graphics. Otherwise it will try and use the intel card

I can't find that option in the R2 BIOS, is there anybody that found it?

---

### Post by juanoleso on 2010-09-04
I don't have 1, but i've read that that option is not there in the BIOS.  I think you are going to have to wait until Nvidia releases optimus drivers for linux or they get it into the kernel or nouveau or something.

---

### Post by technerd206 on 2010-09-06
> **soleblaze said:**
> 
The fan also feels like it spins up a lot more than it does in Windows 7.  Currently it looks like the fan is either off or on, without being throttled in any way.  It can become annoying depending on what you're doing.  I'm hoping this will be fixed in the next bios update.  (The laptop also doesn't overclock correctly, which is supposed to be fixed in the next BIOS revision)


Is anyone else able to get their fan running? Mine has yet to turn on and acpitool -f doesn't see it.

I have an R1 on Xubuntu running my own 2.6.35 kernel with the A05 BIOS fwiw.

---

### Post by ElMuggo on 2010-09-12
> I can't find that option in the R2 BIOS, is there anybody that found it?

Yeah the R2 doesn't have the option because of Optimus. atm its just a case of living without updated nvidia drivers. 

Mind you, running my R2 I've yet to come across any real problems that the intel graphics can't handle. 

atm my only real remaining niggle is the nightmare sound drivers *sigh seems I must have missed out on the kernal update - wonder if using Wubi might be part of the problem?

---

### Post by nourathar on 2010-09-19
Hi all,

thanks a lot for all the info in this thread, I received my m11x R2 a couple of days ago and now I can double boot into windows7 and Ubuntu 10.04.1. The only difficulty I had was that I had to uninstall the Alienware Respawn support process, because it was eating my GRUB everytime I ran windows. Am I the only one to have run into this problem on a M11x ?

Anyway, my real question is about turning off the NVIdia card, I tried the method mentioned here: [http://ubuntuforums.org/showpost.php?p=9598265&postcount=120](http://ubuntuforums.org/showpost.php?p=9598265&postcount=120) but no success, I get this:

joost@lumiabox:~/acpi_call$ ./test_off.sh 
Trying \_SB.PCI0.P0P1.VGA._OFF: failed
Trying \_SB_.PCI0.OVGA.ATPX: failed
Trying \_SB_.PCI0.OVGA.XTPX: failed
Trying \_SB.PCI0.P0P2.PEGP._OFF: failed
Trying \_SB.PCI0.MXR0.MXM0._OFF: failed
Trying \_SB.PCI0.PEG1.GFX0._OFF: failed
Trying \_SB.PCI0.PEG1.GFX0.DOFF: failed
Trying \_SB.PCI0.XVR0.Z01I.DGOF: failed
Trying \_SB.PCI0.PEGR.GFX0._OFF: failed
Trying \_SB.PCI0.PEG.VID._OFF: failed
Trying \_SB.PCI0.P0P2.DGPU._OFF: failed
Trying \_SB.PCI0.IXVE.IGPU.DGOF: failed
joost@lumiabox:~/acpi_call$ grep rate /proc/acpi/battery/BAT1/state
present rate:            21877 mW

do I perhaps need another version of this for m11x R2 ?
Any suggestions very welcome,

Joost.

---

### Post by JailHouseRock on 2010-09-20
I'm having serious problems with my Wifi, it's been crappy for me in the beginning, then for a while it all went well but now it keeps on disconnecting. 

I would love to replace this broadcom abomination for a decent intel card, but I really don't know which one will fit (it's a half-card?) and whether or not it will be fully ubuntu compatible.

Could someone point me in the right direction?

---

### Post by tahnok on 2010-09-21
Ya, it's a pci half card. I'm pretty sure most intel cards work well with linux. Atheros might also be worth looking at, though they can be a little more tricky.

---

### Post by JailHouseRock on 2010-09-21
I can find these two cards:
Intel Ultimate N WiFi Link 5300
Intel WiFi Link 5100

They both say that they have an "PCI-e Mini Card 1.0" interface, is that the same or compatible with this "half card" thing?

Sorry if I sound stupid, but I'm not that familiar with hardware compatibility.

---

### Post by tahnok on 2010-09-21
I think so, but I'm not sure. You should look at the product manual to see which ones you can use.

---

### Post by JailHouseRock on 2010-09-21
Omg, I think I found one, it actually says 'half card'!
[http://azerty.nl/producten/product_detail/790/282870/intel-wifi-link-5100-netwerkadapter-pci-express-half-mini-card-802-11b-802-11a-802-11g-802-11n-draft-.html](http://azerty.nl/producten/product_detail/790/282870/intel-wifi-link-5100-netwerkadapter-pci-express-half-mini-card-802-11b-802-11a-802-11g-802-11n-draft-.html)

And it looks kinda half too, and in the same shop there is the same card, that is not half:
[http://azerty.nl/producten/product_detail/1038/119008/intel-wifi-link-5100-netwerkadapter-pci-express-mini-card-802-11b-802-11a-802-11g-802-11n-draft-2-0-.html](http://azerty.nl/producten/product_detail/1038/119008/intel-wifi-link-5100-netwerkadapter-pci-express-mini-card-802-11b-802-11a-802-11g-802-11n-draft-2-0-.html)

So I think I'll be buying the first mentioned card. I hope it'll work without problems, I'll report back if I do.

Thanks for the help.

---

### Post by lingenfr on 2010-09-28
Hello all. I just broke my Everun Note and am looking for a replacement. I am pretty interested in the M11x. Is there an advantage today of an R2 over an R1? From having read all of the discussion, it looks like the R1 is actually a bit better with the current state of development. Thanks.

---

### Post by tahnok on 2010-09-28
Yeah, the R1 has pretty good support. It's possible if you follow the instructions in this thread to turn off the nvidia GPU and get a good 6 hours of battery. The R1 also has a VGA port which I find very useful.

---

### Post by juanoleso on 2010-09-28
I have an R1 and I don't feel like i'm missing out on anything the R2 has.

---

### Post by lingenfr on 2010-09-30
Well, my M11x is on the way. I have read all of the threads with information about the M11x. There really is not a single source for information, unfortunately. I found the information on the sound driver. I intend to dual boot Lucid and Win 7 Home Premium. Am I going to need to revert to grub1 or can I just do a normal install and write grub to the MBR? Any other issues that I missed? I have been following the video discussions but am not sure about the current state of affairs. I am not much of a gamer and imagine that I would play my games in Winblows if I did, so my preferance if I can switch video would be to use the integrated video as my default in linux. Thanks.

---

### Post by Sub101 on 2010-09-30
> **lingenfr said:**
> Well, my M11x is on the way. I have read all of the threads with information about the M11x. There really is not a single source for information, unfortunately. I found the information on the sound driver. I intend to dual boot Lucid and Win 7 Home Premium. Am I going to need to revert to grub1 or can I just do a normal install and write grub to the MBR? Any other issues that I missed? I have been following the video discussions but am not sure about the current state of affairs. I am not much of a gamer and imagine that I would play my games in Winblows if I did, so my preferance if I can switch video would be to use the integrated video as my default in linux. Thanks.

Grub2 works fine for me. You may need to remove some of the Windows/Dell backup stuff as it can mess with the MBR.

---

### Post by Sub101 on 2010-10-01
Anyone else finding problems turning off the GPU with the latest kernel?

```
FATAL: Error inserting acpi_call (/lib/modules/2.6.32-25-generic/kernel/drivers/acpi/acpi_call.ko): Invalid module format

```

---

### Post by Mangey on 2010-10-04
> **Sub101 said:**
> Anyone else finding problems turning off the GPU with the latest kernel?

```
FATAL: Error inserting acpi_call (/lib/modules/2.6.32-25-generic/kernel/drivers/acpi/acpi_call.ko): Invalid module format

```

Yep, same exact problem here, not sure what the solution is though.

---

### Post by tahnok on 2010-10-04
You guys need to rebuild and reinstall the acpi_call because the kernel changed.

---

### Post by Mangey on 2010-10-10
> **tahnok said:**
> You guys need to rebuild and reinstall the acpi_call because the kernel changed.

Thanks!

---

### Post by lobo_tuerto on 2010-10-13
*(This links are for Ubuntu 10.04, as Sub101 pointed out, Ubuntu 10.10 might work out of the box with the R2, R1 is working already. I will do a clean install in a few days, will report back ;))*

I bought an Alienware m11x r2 recently, and currently have a dual boot system. I too did read various threads and pages, and found useful to collect the links for future reference:

To solve the problem related to having a dual boot system, that presents after you boot into Windows 7 and then restart the computer and then see:
"No modules found. Press any key to restart.
No operating system found."
**[I used solution 2 [link]]("http://sourceforge.net/apps/mediawiki/bootinfoscript/index.php?title=Boot_Problems:Windows_Writes_To_MBR")**

To get your audio working in Ubuntu on your m11x r2:
**[Linux audio drivers [link]]("http://www.realtek.com.tw/downloads/downloadsView.aspx?Langid=1&PNid=14&PFid=24&Level=4&Conn=3&DownTypeID=3&GetDown=false")**

But what caught my attention was that I read that you can turn off the GPU! how can I do THAT? I'd love to have all those hours "left" I can see when I'm in Windows (5 ~ 6 hrs). In Ubuntu I can only get around 2.5 hrs.

I will update this info if I find anything more related to Ubuntu + m11x r2

---

### Post by Sub101 on 2010-10-13
> **lobo_tuerto said:**
> 
To get your audio working in Ubuntu on your m11x r2:
**[Linux audio drivers [link]]("http://www.realtek.com.tw/downloads/downloadsView.aspx?Langid=1&PNid=14&PFid=24&Level=4&Conn=3&DownTypeID=3&GetDown=false")**


I have the R1 not R2. As of 10.10 the sound works out of the box, so I would suspect its the same for the R2.

---

### Post by tahnok on 2010-10-13
Has anyone done a dist-upgrade from 10.04? Any success?

---

### Post by tyoc213 on 2010-10-13
But after installation I put the NVIDIA propietary driver and the next start it can't log on graphically, only via text, and when doing a startx it says it could not find any devices or some like that... now Im back to windows and reformat a USB for install again desktopx64 via USB.

So there are no improvements? I mean I should use Intel graphic card?


Didn't have the time for see if the other things work (wireless, sound...).

---

### Post by lingenfr on 2010-10-16
This thread has drug on for some time and it appears a lot of changes have occurred. I have my M11x (R1) and am successfully dual booting Win 7 and Ubu 10.10 x64. I have not loaded the nvidia driver and am able to boot fine with the BIOS set to Switchable. Sounds works without installing the driver. I can't adjust the brightness and can't run Compiz without the nvidia driver. Before I make any more changes, I would like to circle back and get some clarification. In [this post]("http://ubuntuforums.org/showpost.php?p=8948066&postcount=28"), it says:
> **soleblaze said:**
> got brightness on switchable working:

as root:

edit /etc/default/grub. change GRUB_CMDLINE_LINUX_DEFAULT="quiet splash" to GRUB_CMDLINE_LINUX_DEFAULT="quiet splash nomodeset acpi_backlight=vendor"

Save that then run update-grub. After that and a reboot you should be able to change the brightness just fine.  You have a lot more steps in the brightness than you do in windows.

There are also references to another method on the [archlinux wiki]("http://wiki.archlinux.org/index.php/Alienware_M11x#backlight_brightness"). Which one works or is best? If it works with 10.10, modifying the grub bootline seems easiest.

Next topic is switching off the nvidia GPU to save power. I have seen at least three methods. Nasrullah provided a script [here]("http://ubuntuforums.org/showpost.php?p=9441266&postcount=94"). The acpi_call script is mentioned here and on the [archlinux wiki]("http://wiki.archlinux.org/index.php/Alienware_M11x#Video") and then the archlinux wiki mentions another method. I seems to me that acpi_call is the easiest, but I would appreciate some feedback. I expect that 99% of the time the Intel GPU will be fine for me and I would rather have the battery life, but I would like to be able to use the nvidia GPU on occasion. Is it safe to load the driver that shows up in restricted drivers? Thanks. I may take the answers and start a new thread specific to the R1 and 10.10 so I can keep the first post current with instructions.

---

### Post by tahnok on 2010-10-17
Yeah, the ACPI call method works well. 

As for enabling the nvidia GPU... I don't know. I've seen lots of mentions of white screens after installing the restricted drivers.

---

### Post by simonhein on 2010-10-21
Hi here's is how I got m11x R1 working on ubuntu 10.10

Works
* Sound
* Disable nvidia - It doesnt work after being in sleep mode, but you can make at shortcut to launch the "nvidia disable" script again
* alienfx
* wifi - active in restricted hardware
* Flash playing in fullscreen (etc. hak5.org, youtube.com ..)

kinda works
* Backlight  - the script is a bit choppy but works.

Doesn't work
* Switchable graphics - I recommend to dual boot into windows for playing games. 

This is what i did. I made a guide for myself, so i easy can reinstall ubuntu, but why not share it with you.

Best regards Simon Hein

================================================================================
Getting started 
================================================================================

Download this zip from [http://thecoder.dk/m11x.zip](http://thecoder.dk/m11x.zip) 

unpack the zip where ever you want

Copy m11x folder to /home/put-your-user-name-here/

================================================================================
Nvidia disable fix
================================================================================

In terminal

cd /home/put-your-user-name-here/m11x/acpi_call/

make

chmod u+x test_off.sh 

echo options nouveau modeset=0 | sudo tee -a /etc/modprobe.d/nouveau-kms.conf 

sudo update-initramfs -u

sudo nautilus
ADD following lines in /etc/rc.local

insmod /home/put-your-user-name-here/m11x/acpi_call/acpi_call.ko
/home/put-your-user-name-here/m11x/acpi_call/test_off.sh

That's it.

To test it 
/home/put-your-user-name-here/m11x/acpi_call/test_off.sh

to check if its working in terminal:
grep rate /proc/acpi/battery/BAT1/state 

The value should drop from around 20000mW to about 11000mW-15000mW
------------------------------------------------------------
|  Warning if you do it wrong i might cause ubuntu to crash. 
|  If that's the problem, start in safe mode, and go to:
|  
|  /etc/rc.local
|  
|  And remove these lines                                  
|  insmod /home/put-your-user-name-here/m11x/acpi_call/acpi_call.ko   
|  /home/put-your-user-name-here/m11x/acpi_call/test_off.s    
|  
|  After that, try the guide again.        
------------------------------------------------------------



================================================================================
Brightness fix
================================================================================
cd /home/put-your-user-name-here/m11x/backlight/
chmod u+x backlight_up
chmod u+x backlight_down

Now go to System > Preferences > Keyboard Shortcuts

Press add

Name:
Backlight up

Command:
/home/put-your-user-name-here/backlight/backlight_up

After that map it to a key combo

Name:
Backlight down

Command:
/home/put-your-user-name-here/backlight/backlight_down

After that map it to a key combo


If you want to make a dedicated key to a specific brighness value use this command.

gksudo "setpci -s 00:02.0 F4.B=42"

gksudo "setpci -s 00:02.0 F4.B=FF"

================================================================================
Alien FX
================================================================================
sudo apt-get install openjdk-6-jre

sudo apt-get install libusb-1.0-0

cd /home/put-your-user-name-here/m11x

Now go to System > Preferences > Keyboard Shortcuts

Add following line to the commandline:
gksudo  "java -jar /home/put-your-user-name-here/m11x/AlienFXLite-0.4b.jar"

map a keyboard shortcut

================================================================================
Making flash play in full screen in ubuntu 10.10
================================================================================
sudo mkdir /etc/adobe 
echo "OverrideGPUValidation=true" >~/mms.cfg 
sudo mv ~/mms.cfg /etc/adobe/

================================================================================

---

### Post by lingenfr on 2010-10-21
Simon,

Thanks very much for this. Progress so far:

Nvidia disable - NOGO. This seems to work when I run it from the command line. I can insert the module. When I run the script it throws off a list of errors, but it does drop the current draw. However, when I put the lines into /etc/rc.local the system won't boot. You didn't say whether to include the 'exit 0' or not. I tried it both ways, still no joy.

AlienFX - GO. Not sure how or if I will use it, but it works.

Backlight - NOGO. The first time I try backlight up or down it asks me for a password, but does nothing. After that, each time I try either, I get a 'Starting administrative...' task but it does not seem to have any effect on the backlight. Running the scripts from the command line also has no effect.

Flash - ? I completed the instructions, but I think this was already working. Will test further.

I am running 10.10 x64 with the latest kernel (2.6.35-22-generic). Help.

---

### Post by Msieur Piero on 2010-10-30
So, If I've understand everything, you can use an acpi_call to turn off the Nvidia card on both version (R1 and R2). I guess for this it's ok. But is the nvidia card usable only by the R1 version (while loading CUDA???), by using the switchable mode or do I have to forget it?
Maybe I haven't understand and you cannot use the nvidia card at all with both version under linux.
Can sombody answers this crappy question? I'm expecting the dell seller's call.

---

### Post by MJalbert on 2010-11-03
Hi,

I've tried to install the sound drivers found here:
[http://www.realtek.com.tw/downloads/downloadsCheck.aspx?Langid=1&PNid=14&PFid=24&Level=4&Conn=3&DownTypeID=3&GetDown=false](http://www.realtek.com.tw/downloads/downloadsCheck.aspx?Langid=1&PNid=14&PFid=24&Level=4&Conn=3&DownTypeID=3&GetDown=false)

I unpack everything and execute the install file (sudo ./install) but during the installation I get an error:
```
rm: cannot remove `/dev/snd': Is a directory
rm: cannot remove `/dev/snd/by-path': Is a directory
rmdir: failed to remove `/dev/snd': Directory not empty
Creating snd/control?...done.
Creating snd/seq...done.
Creating snd/timer...done.
Creating snd/hw??...done.
Creating snd/midi??...done.
Creating snd/pcm??p...done.
Creating snd/pcm??c...done.
Creating aload?...done.
Creating aloadSEQ...done.
Remove Folder.....
./install: 109: Syntax error: "fi" unexpected
```
Anyone has an idea?

Thanks,

---

### Post by lingenfr on 2010-11-06
If you are using 10.10 you don't need the drivers. If you are using a previous version and read this thread, you will see that they recommend you follow the instructions in the readme file and not just run the script.

---

### Post by tejo on 2010-11-16
> **simonhein said:**
> Hi here's is how I got m11x R1 working on ubuntu 10.10

In terminal

cd /home/put-your-user-name-here/m11x/acpi_call/

make

chmod u+x test_off.sh 

echo options nouveau modeset=0 | sudo tee -a /etc/modprobe.d/nouveau-kms.conf 

sudo update-initramfs -u

sudo nautilus
ADD following lines in /etc/rc.local

insmod /home/put-your-user-name-here/m11x/acpi_call/acpi_call.ko
/home/put-your-user-name-here/m11x/acpi_call/test_off.sh

That's it.

To test it 
/home/put-your-user-name-here/m11x/acpi_call/test_off.sh

================================================================================

thanks simonhein

if you want to switch off the gfx card on wake up from suspend you can put rc.local ad 60rc.local in /etc/pm/sleep.d/

---

### Post by lingenfr on 2010-11-17
> **lingenfr said:**
> Simon,

Thanks very much for this. Progress so far:

Nvidia disable - NOGO. This seems to work when I run it from the command line. I can insert the module. When I run the script it throws off a list of errors, but it does drop the current draw. However, when I put the lines into /etc/rc.local the system won't boot. You didn't say whether to include the 'exit 0' or not. I tried it both ways, still no joy.

AlienFX - GO. Not sure how or if I will use it, but it works.

Backlight - NOGO. The first time I try backlight up or down it asks me for a password, but does nothing. After that, each time I try either, I get a 'Starting administrative...' task but it does not seem to have any effect on the backlight. Running the scripts from the command line also has no effect.

Flash - ? I completed the instructions, but I think this was already working. Will test further.

I am running 10.10 x64 with the latest kernel (2.6.35-22-generic). Help.

Has anyone had better luck that mine with 10.10? If so, please post revised instructions as to how you got it working. Thanks.

---

### Post by Sub101 on 2010-11-19
> **lingenfr said:**
> Has anyone had better luck that mine with 10.10? If so, please post revised instructions as to how you got it working. Thanks.


For the R1 the following is the case:

NVidia Disable - working ( I will post instructions when I have more time)

AlienFX - Works and customizable using [http://forum.notebookreview.com/alienware/458528-alienfx-lite-linux-windows-alienfx-tool.html](http://forum.notebookreview.com/alienware/458528-alienfx-lite-linux-windows-alienfx-tool.html)

Backlight - control can be enabled however you lose the ability to use desktop effects (in my case at least) so its down to preference

Flash - works and plently of threads exist with how tos.

---

### Post by strikeoncmputrz on 2010-11-22
Hey all, I've had my R2 for about a week. I've read the entire Thread  and I would like to thank everyone who posted fixes and provided  advice.  I was wondering if someone could post about the current state  of affairs for the R2, similar to Sub101's post above this one. It would be much appreciated. My main concern is successfully turning off the Nvidia card.

---

### Post by lobo_tuerto on 2010-11-23
(This is for the Alienware m11x r2)

[B]BEST SOLUTION SO FAR FOR TURNING OFF THE NVIDIA GPU
IN THE ALIENWARE M11X-R2[/B]
######################################################
Seems like the easiest way to turn the nVidia GPU off is with this:
[peberlein/acpi_call](http://gith*******/peberlein/acpi_call) (ugh, it would scramble my url)
**To get the URL for the github repo google for: github acpi_call peberlein**

git clone it, compile it, insmod it (rmmod it first, if you have been tinkering with this acpi_call stuff)
Then run ./m11xr2.sh off

```

git clone git://the_repo_to_clone
cd acpi_call/
make
sudo insmod acpi_call.ko
./m11xr2.sh off

```

**To get the URL for the github repo google for: github acpi_call peberlein**
######################################################

I just fully charged my laptop's battery and it went up from the usual 2:10hrs (~ 2:30hrs) to 3:15hrs. Not much, compared to what you get in Windows 7 (around 6 hrs?), but 1 hour more when you only have 2, is great!

Energy consumption dropped from 22.6W to 17.4W.

Anyone have any tips for getting better battery life?


(solution found here: [http://linux-hybrid-graphics.blogspot.com/](http://linux-hybrid-graphics.blogspot.com/))

---

### Post by c00lwaterz on 2010-11-30
so, what happen to the fan/cooling system for alienware? did the issue for the fan solved? i haven't heard now about the fan issues. i was watching this thread to have info about cooling system and other issues.

thanks :p

---

### Post by tahnok on 2010-11-30
I haven't had any issues with heat to be honest.

Unrelated: Has anyone successfully gotten the latest intel drivers loaded? I want to get some better video performance so I can run gnome-shell

---

### Post by c00lwaterz on 2010-11-30
> **tahnok said:**
> I haven't had any issues with heat to be honest.

Unrelated: Has anyone successfully gotten the latest intel drivers loaded? I want to get some better video performance so I can run gnome-shell

thanks. do alienware support linux? hardware, linux etc? and other features?

what alienware model you use?

thanks again

---

### Post by tahnok on 2010-11-30
Alienware has no support for linux, but it works anyways.

I have an m11x R1 and it works great

---

### Post by c00lwaterz on 2010-11-30
> **tahnok said:**
> Alienware has no support for linux, but it works anyways.

I have an m11x R1 and it works great

i mean the hardware drivers etc.. do sound works perfectly and fan, lights, gpu etc?

---

### Post by tahnok on 2010-11-30
All of that information is in this thread. There's a summary a few posts back

---

### Post by nesalang on 2010-12-17
> **simonhein said:**
> Hi here's is how I got m11x R1 working on ubuntu 10.10

Works
* Sound
* Disable nvidia - It doesnt work after being in sleep mode, but you can make at shortcut to launch the "nvidia disable" script again
* alienfx
* wifi - active in restricted hardware
* Flash playing in fullscreen (etc. hak5.org, youtube.com ..)

kinda works
* Backlight  - the script is a bit choppy but works.

Doesn't work
* Switchable graphics - I recommend to dual boot into windows for playing games. 

This is what i did. I made a guide for myself, so i easy can reinstall ubuntu, but why not share it with you.

Best regards Simon Hein

================================================================================
Getting started 
================================================================================

Download this zip from [http://thecoder.dk/m11x.zip](http://thecoder.dk/m11x.zip) 

unpack the zip where ever you want

Copy m11x folder to /home/put-your-user-name-here/

================================================================================
Nvidia disable fix
================================================================================

In terminal

cd /home/put-your-user-name-here/m11x/acpi_call/

make

chmod u+x test_off.sh 

echo options nouveau modeset=0 | sudo tee -a /etc/modprobe.d/nouveau-kms.conf 

sudo update-initramfs -u

sudo nautilus
ADD following lines in /etc/rc.local

insmod /home/put-your-user-name-here/m11x/acpi_call/acpi_call.ko
/home/put-your-user-name-here/m11x/acpi_call/test_off.sh

That's it.

To test it 
/home/put-your-user-name-here/m11x/acpi_call/test_off.sh

to check if its working in terminal:
grep rate /proc/acpi/battery/BAT1/state 

The value should drop from around 20000mW to about 11000mW-15000mW
------------------------------------------------------------
|  Warning if you do it wrong i might cause ubuntu to crash. 
|  If that's the problem, start in safe mode, and go to:
|  
|  /etc/rc.local
|  
|  And remove these lines                                  
|  insmod /home/put-your-user-name-here/m11x/acpi_call/acpi_call.ko   
|  /home/put-your-user-name-here/m11x/acpi_call/test_off.s    
|  
|  After that, try the guide again.        
------------------------------------------------------------



================================================================================
Brightness fix
================================================================================
cd /home/put-your-user-name-here/m11x/backlight/
chmod u+x backlight_up
chmod u+x backlight_down

Now go to System > Preferences > Keyboard Shortcuts

Press add

Name:
Backlight up

Command:
/home/put-your-user-name-here/backlight/backlight_up

After that map it to a key combo

Name:
Backlight down

Command:
/home/put-your-user-name-here/backlight/backlight_down

After that map it to a key combo


If you want to make a dedicated key to a specific brighness value use this command.

gksudo "setpci -s 00:02.0 F4.B=42"

gksudo "setpci -s 00:02.0 F4.B=FF"

================================================================================
Alien FX
================================================================================
sudo apt-get install openjdk-6-jre

sudo apt-get install libusb-1.0-0

cd /home/put-your-user-name-here/m11x

Now go to System > Preferences > Keyboard Shortcuts

Add following line to the commandline:
gksudo  "java -jar /home/put-your-user-name-here/m11x/AlienFXLite-0.4b.jar"

map a keyboard shortcut

================================================================================
Making flash play in full screen in ubuntu 10.10
================================================================================
sudo mkdir /etc/adobe 
echo "OverrideGPUValidation=true" >~/mms.cfg 
sudo mv ~/mms.cfg /etc/adobe/

================================================================================

[U]Hi simonhein,

thanks for the help. the nvdia method worked! It was guite cool. One question I have is. How do I turn it back on?

Thanks!


One question, 

Is it possible to use external monitor? 
Thannks!
[/U]

---

### Post by tahnok on 2010-12-17
Yup, I use an external monitor all the time. Sometimes I have to click on Monitors in the System menu in order to get it to work.

---

### Post by c00lwaterz on 2010-12-18
i won't but machine that will not work out of the box on linux. because you buy the machine for it's specification. and if it will not work for you right, then it's a waste of money. if you will use linux then graphics won't work then it's a waste. then you should buy graphics that will work on linux. it's better. (in my opinion) i will buy 100% compatible machine for linux. :D

pls don't get me wrong. :D

---

### Post by Sub101 on 2010-12-19
> **c00lwaterz said:**
> i won't but machine that will not work out of the box on linux. because you buy the machine for it's specification. and if it will not work for you right, then it's a waste of money. if you will use linux then graphics won't work then it's a waste. then you should buy graphics that will work on linux. it's better. (in my opinion) i will buy 100% compatible machine for linux. :D

pls don't get me wrong. :D

You can make both cards work using Arch.

[https://wiki.archlinux.org/index.php/Alienware_M11x#VGA_SWITCHEROO](https://wiki.archlinux.org/index.php/Alienware_M11x#VGA_SWITCHEROO)

And I see no reason why you couldnt make it work in Ubuntu.

---

### Post by c00lwaterz on 2010-12-21
> **Sub101 said:**
> You can make both cards work using Arch.

[https://wiki.archlinux.org/index.php/Alienware_M11x#VGA_SWITCHEROO](https://wiki.archlinux.org/index.php/Alienware_M11x#VGA_SWITCHEROO)

And I see no reason why you couldnt make it work in Ubuntu.

thanks for the info. :D im currently using toshiba m900 but not yet solve the problem about fan control. sorry for the OT. 

so in my opinion "if" i will buy alienware laptop, I will ensure it will work out of the box. it is hard and risky if some hardware is not working.

in my case my toshiba m900 getting really hot because fan is not working on linux even i update the bios. my fan work good on windows only. :frown:

But i really want linux

---

### Post by Pollywoggy on 2010-12-22
> **c00lwaterz said:**
> thanks for the info. :D im currently using toshiba m900 but not yet solve the problem about fan control. sorry for the OT. 

so in my opinion "if" i will buy alienware laptop, I will ensure it will work out of the box. it is hard and risky if some hardware is not working.

in my case my toshiba m900 getting really hot because fan is not working on linux even i update the bios. my fan work good on windows only. :frown:

But i really want linux

You might try a Google search of this forum.  I seem to remember reading that someone wrote instructions for installing Linux on an Alienware laptop, based on how they had succeeded.  IIRC I did it and the only things that did not work were wireless and the enhanced graphics of the laptop.  The worst problem I had (I did not use the information recently posted on this forum about how to install) was that Windows 7 wrote over the Linux boot record.

As for Alienware, Dell's phone tech support is terrible.  If you do have a problem with the hardware as I did, you might need to talk to foreign tech support (if you are a US resident) for 2 hrs or more and play their games before they will schedule a pickup.  Once you have gone through their gauntlet, the rest is fast and you will have your laptop back in one week or less.  I will not know if mine is really fixed until we have warm weather again.  It would shut down immediately after being started during warm weather.  I would not buy anything from Dell unless they fix their tech support for US residents.  I read somewhere that people who live in Europe can deal with tech support in their own countries and that only US tech support is outsourced.  Can someone confirm this?

---

### Post by cjcardinal on 2010-12-23
so recently I decided to finally upgrade to 10.10 as i started having high temperature issues with 10.04 and couldn't find a solution.  Upgrading to 10.10 fixed, or got rid of whatever the problem was.  Problem solved, new problem to deal with...

I am having issues compiling the ALSA drivers (i have done it dozens of times on 10.04 with no issues)

below is the error i receive when i try to "./configure --with-cards=hda-intel"

```
carmen@MADMAX4:~/alsa-driver-1.0.23$ ./configure --with-cards=hda-intel
checking for gcc... gcc
checking for C compiler default output file name... a.out
checking whether the C compiler works... yes
checking whether we are cross compiling... no
checking for suffix of executables... 
checking for suffix of object files... o
checking whether we are using the GNU C compiler... yes
checking whether gcc accepts -g... yes
checking for gcc option to accept ISO C89... none needed
checking for ranlib... ranlib
checking for a BSD-compatible install... /usr/bin/install -c
checking how to run the C preprocessor... gcc -E
checking for grep that handles long lines and -e... /bin/grep
checking for egrep... /bin/grep -E
checking for ANSI C header files... yes
checking for an ANSI C-conforming const... yes
checking for inline... inline
checking whether time.h and sys/time.h may both be included... yes
checking whether gcc needs -traditional... no
checking for current directory... /home/carmen/.local/share/Trash/files/alsa-driver-1.0.23
checking cross compile... 
checking for directory with ALSA kernel sources... ../alsa-kmirror
checking for directory with kernel source... /lib/modules/2.6.35-24-generic/build
checking for directory with kernel build... 
checking for kernel linux/version.h ... linux/version.h
checking for kernel linux/autoconf.h generated/autoconf.h... generated/autoconf.h
checking for kernel linux/utsrelease.h generated/utsrelease.h... generated/utsrelease.h
checking for kernel version... 2.6.35-24-generic
checking for GCC version... Kernel compiler:  Used compiler: gcc (Ubuntu/Linaro 4.4.4-14ubuntu5) 4.4.5

*** NO PREDEFINED KERNEL COMPILER IS DETECTED
*** Assuming the same compiler is used with the current system compiler.

*** Please make sure that the same compiler version was used for building kernel.

checking for built-in ALSA... no
checking for existing ALSA module... yes
checking for Red Hat kernel... auto
checking for Red Hat kernel... no
checking for SUSE kernel... auto
checking for SUSE kernel... no
checking for updating alsa-kernel version.h... yes
checking for CONFIG_EXPERIMENTAL... yes
rm: cannot remove `include/linux/usb/audio.h': Permission denied
checking for directory to store kernel modules... /lib/modules/2.6.35-24-generic/kernel/sound
checking for verbose procfs... on
checking for verbose printk... on
checking for debug level... none
checking for ISA support in kernel... no
checking for processor type... x86_64
checking for ISA DMA API... yes
checking for 32bit compat support... yes
checking for kernel linux/config.h... no
Creating <linux/config.h>...
checking for deprecated linux/config.h... checking to modify of kernel linux/kmod.h... no
checking for kernel linux/utsrelease.h... no
Creating a dummy <linux/utsrelease.h>...
checking for kernel linux/compiler.h... yes
checking for kernel linux/pm.h... yes
checking for kernel linux/spinlock.h... yes
checking for kernel linux/irq.h... yes
checking for kernel linux/threads.h... yes
checking for kernel linux/rwsem.h... yes
checking for kernel linux/gameport.h... yes
checking for kernel media/v4l2-dev.h... yes
checking for kernel linux/devfs_fs_kernel.h... no
Creating a dummy <linux/devfs_fs_kernel.h>...
checking for kernel linux/highmem.h... yes
checking for kernel linux/workqueue.h... yes
checking for kernel linux/dma-mapping.h... yes
checking for kernel asm/hw_irq.h... yes
checking for kernel linux/device.h... yes
checking for kernel linux/platform_device.h... yes
checking for kernel linux/isa.h... yes
checking for kernel linux/jiffies.h... yes
checking for kernel linux/compat.h... yes
checking for kernel linux/log2.h... yes
checking for kernel linux/adb.h... yes
checking for kernel linux/cuda.h... yes
checking for kernel linux/pmu.h... yes
checking for kernel linux/io.h... yes
checking for kernel linux/moduleparam.h... yes
checking for kernel linux/syscalls.h... yes
checking for kernel linux/firmware.h... yes
checking for kernel linux/err.h... yes
checking for kernel linux/bitmap.h... yes
checking for kernel linux/mutex.h... yes
checking for kernel linux/pm_qos_params.h... yes
checking for kernel linux/kthread.h... yes
checking for kernel asm/irq_regs.h... yes
checking for kernel linux/seq_file.h... yes
checking for kernel linux/debugfs.h... yes
checking for kernel linux/gpio.h... yes
checking for kernel linux/bug.h... yes
checking for kernel linux/math64.h... yes
checking for kernel linux/regulator/consumer.h... yes
checking for kernel linux/dmi.h... yes
checking for kernel linux/bitrev.h... yes
checking for kernel linux/hrtimer.h... yes
checking for kernel linux/gcd.h... yes
checking for kernel linux/gfp.h... yes
checking for kernel module symbol versions... yes
checking for has ioport support... yes
checking for PCI support in kernel... yes
checking for I2C driver in kernel... yes
checking for I2C_POWERMAC in kernel... unknown
checking for firmware loader... yes
checking for input subsystem in kernel... yes
checking for pc-speaker platform in kernel... yes
checking for SMP... yes
checking for Video device support in kernel... yes
checking for ISA PnP driver in kernel... yes
checking for PnP driver in kernel... yes
checking for Kernel ISA-PnP support... no
checking for Kernel ISA-PnP module support... no
checking for strlcpy... yes
checking for snprintf... yes
checking for vsnprintf... yes
checking for scnprintf... yes
checking for sscanf... yes
checking for vmalloc_to_page... yes
checking for old kmod... no
checking for PDE... yes
checking for pci_set_consistent_dma_mask... yes
checking for pci_dev_present... yes
checking for msleep... yes
checking for msleep_interrupt... yes
checking for msecs_to_jiffies... yes
checking for tty->count is the atomic type... yes
checking for video_get_drvdata... yes
checking for video_drvdata... yes
checking for V4L1 layer... yes
checking for V4L2 layer... yes
checking for io_remap_pfn_range... yes
checking for kcalloc... yes
checking for kstrdup... yes
checking for kstrndup... yes
checking for kzalloc... yes
checking for create_workqueue with flags... no
checking for pci_ioremap_bar... yes
checking for saved_config_space in pci_dev... yes
checking for new pci_save_state... yes
checking for register_sound_special_device... yes
checking for driver extra-version... 
checking for driver version... 1.0.23
checking for dynamic minor numbers... no
checking for sequencer support... yes
checking for OSS/Free emulation... yes
checking for OSS PCM plugin system inclusion... yes
checking for RTC support... no
checking for HPET support... yes
checking for Procfs support... yes
checking for USB support... yes
checking for kernel linux/usb/audio-v2.h... yes
checking for kernel linux/usb/audio.h... yes
Removing a dummy linux/usb/audio.h.
rm: cannot remove `include/linux/usb/audio.h': Permission denied
checking for valid v1 in linux/usb/audio.h... no
Creating <linux/usb/audio.h>...
./configure: line 13867: include/linux/usb/audio.h: Permission denied
checking for kernel linux/usb/ch9.h... yes
checking for class_simple... no
checking for old driver suspend/resume callbacks... no
checking for removal of page-reservation for nopage/mmap... no
checking for nested class_device... no
checking for new IRQ handler... yes
checking for gfp_t... yes
checking for GFP_DMA32... yes
checking for page_to_pfn... yes
checking for PnP suspend/resume... yes
checking for device_create_drvdata... no
checking for new unlocked/compat_ioctl... yes
checking for builtin _Bool support... yes
checking for x86-compatible PC... no
checking for High-Res timers... yes
checking for kernel PCMCIA
checking for PCMCIA support... yes
checking for PC9800 support in kernel... no
checking for parallel port support... yes
checking for power management... yes
checking for CONFIG_HAS_DMA... yes
checking for cards to compile driver for... hda-intel
checking for additonal options to compile driver for... all
configure: creating ./config.status
config.status: creating version
config.status: creating Makefile.conf
config.status: WARNING:  Makefile.conf.in seems to ignore the --datarootdir setting
config.status: creating snddevices
config.status: creating utils/alsa-driver.spec
config.status: creating utils/buildrpm
config.status: creating toplevel.config
config.status: creating utils/alsasound
config.status: creating utils/alsasound.posix
config.status: creating include/pci_ids_compat.h
config.status: creating include/i2c-id_compat.h
config.status: creating include/config.h
config.status: include/config.h is unchanged
config.status: creating include/config1.h
config.status: include/config1.h is unchanged
config.status: creating include/version.h
config.status: include/version.h is unchanged
config.status: creating include/autoconf-extra.h
config.status: include/autoconf-extra.h is unchanged
Hacking autoconf.h...

```

and obviously since the drivers wouldnt configure properly, this is the "make" result

```
carmen@MADMAX4:~/alsa-driver-1.0.23$ sudo make
[sudo] password for carmen: 
make dep
make[1]: Entering directory `/home/carmen/.local/share/Trash/files/alsa-driver-1.0.23'
make[2]: Entering directory `/home/carmen/.local/share/Trash/files/alsa-driver-1.0.23/include'
make -C sound prepare
make[3]: Entering directory `/home/carmen/.local/share/Trash/files/alsa-driver-1.0.23/include/sound'
make prepare2
make[4]: Entering directory `/home/carmen/.local/share/Trash/files/alsa-driver-1.0.23/include/sound'
make[4]: Nothing to be done for `prepare2'.
make[4]: Leaving directory `/home/carmen/.local/share/Trash/files/alsa-driver-1.0.23/include/sound'
make[3]: Leaving directory `/home/carmen/.local/share/Trash/files/alsa-driver-1.0.23/include/sound'
make[2]: Leaving directory `/home/carmen/.local/share/Trash/files/alsa-driver-1.0.23/include'
make[2]: Entering directory `/home/carmen/.local/share/Trash/files/alsa-driver-1.0.23/acore'
make[3]: Entering directory `/home/carmen/.local/share/Trash/files/alsa-driver-1.0.23/acore/ioctl32'
make[3]: Leaving directory `/home/carmen/.local/share/Trash/files/alsa-driver-1.0.23/acore/ioctl32'
make[3]: Entering directory `/home/carmen/.local/share/Trash/files/alsa-driver-1.0.23/acore/oss'
make[3]: Leaving directory `/home/carmen/.local/share/Trash/files/alsa-driver-1.0.23/acore/oss'
make[3]: Entering directory `/home/carmen/.local/share/Trash/files/alsa-driver-1.0.23/acore/seq'
make[4]: Entering directory `/home/carmen/.local/share/Trash/files/alsa-driver-1.0.23/acore/seq/oss'
make[4]: Leaving directory `/home/carmen/.local/share/Trash/files/alsa-driver-1.0.23/acore/seq/oss'
make[3]: Leaving directory `/home/carmen/.local/share/Trash/files/alsa-driver-1.0.23/acore/seq'
make[2]: Leaving directory `/home/carmen/.local/share/Trash/files/alsa-driver-1.0.23/acore'
make[2]: Entering directory `/home/carmen/.local/share/Trash/files/alsa-driver-1.0.23/i2c'
make[3]: Entering directory `/home/carmen/.local/share/Trash/files/alsa-driver-1.0.23/i2c/l3'
make[3]: Leaving directory `/home/carmen/.local/share/Trash/files/alsa-driver-1.0.23/i2c/l3'
make[3]: Entering directory `/home/carmen/.local/share/Trash/files/alsa-driver-1.0.23/i2c/other'
make[3]: Leaving directory `/home/carmen/.local/share/Trash/files/alsa-driver-1.0.23/i2c/other'
make[2]: Leaving directory `/home/carmen/.local/share/Trash/files/alsa-driver-1.0.23/i2c'
make[2]: Entering directory `/home/carmen/.local/share/Trash/files/alsa-driver-1.0.23/drivers'
make[3]: Entering directory `/home/carmen/.local/share/Trash/files/alsa-driver-1.0.23/drivers/mpu401'
make[3]: Leaving directory `/home/carmen/.local/share/Trash/files/alsa-driver-1.0.23/drivers/mpu401'
make[3]: Entering directory `/home/carmen/.local/share/Trash/files/alsa-driver-1.0.23/drivers/opl3'
make[3]: Leaving directory `/home/carmen/.local/share/Trash/files/alsa-driver-1.0.23/drivers/opl3'
make[3]: Entering directory `/home/carmen/.local/share/Trash/files/alsa-driver-1.0.23/drivers/opl4'
make[3]: Leaving directory `/home/carmen/.local/share/Trash/files/alsa-driver-1.0.23/drivers/opl4'
make[3]: Entering directory `/home/carmen/.local/share/Trash/files/alsa-driver-1.0.23/drivers/pcsp'
make[3]: Leaving directory `/home/carmen/.local/share/Trash/files/alsa-driver-1.0.23/drivers/pcsp'
make[3]: Entering directory `/home/carmen/.local/share/Trash/files/alsa-driver-1.0.23/drivers/vx'
make[3]: Leaving directory `/home/carmen/.local/share/Trash/files/alsa-driver-1.0.23/drivers/vx'
make[2]: Leaving directory `/home/carmen/.local/share/Trash/files/alsa-driver-1.0.23/drivers'
make[2]: Entering directory `/home/carmen/.local/share/Trash/files/alsa-driver-1.0.23/isa'
make[3]: Entering directory `/home/carmen/.local/share/Trash/files/alsa-driver-1.0.23/isa/ad1816a'
make[3]: Leaving directory `/home/carmen/.local/share/Trash/files/alsa-driver-1.0.23/isa/ad1816a'
make[3]: Entering directory `/home/carmen/.local/share/Trash/files/alsa-driver-1.0.23/isa/ad1848'
make[3]: Leaving directory `/home/carmen/.local/share/Trash/files/alsa-driver-1.0.23/isa/ad1848'
make[3]: Entering directory `/home/carmen/.local/share/Trash/files/alsa-driver-1.0.23/isa/cs423x'
make[3]: Leaving directory `/home/carmen/.local/share/Trash/files/alsa-driver-1.0.23/isa/cs423x'
make[3]: Entering directory `/home/carmen/.local/share/Trash/files/alsa-driver-1.0.23/isa/es1688'
make[3]: Leaving directory `/home/carmen/.local/share/Trash/files/alsa-driver-1.0.23/isa/es1688'
make[3]: Entering directory `/home/carmen/.local/share/Trash/files/alsa-driver-1.0.23/isa/gus'
make[3]: Leaving directory `/home/carmen/.local/share/Trash/files/alsa-driver-1.0.23/isa/gus'
make[3]: Entering directory `/home/carmen/.local/share/Trash/files/alsa-driver-1.0.23/isa/msnd'
make[3]: Leaving directory `/home/carmen/.local/share/Trash/files/alsa-driver-1.0.23/isa/msnd'
make[3]: Entering directory `/home/carmen/.local/share/Trash/files/alsa-driver-1.0.23/isa/opti9xx'
make[3]: Leaving directory `/home/carmen/.local/share/Trash/files/alsa-driver-1.0.23/isa/opti9xx'
make[3]: Entering directory `/home/carmen/.local/share/Trash/files/alsa-driver-1.0.23/isa/sb'
make[3]: Leaving directory `/home/carmen/.local/share/Trash/files/alsa-driver-1.0.23/isa/sb'
make[3]: Entering directory `/home/carmen/.local/share/Trash/files/alsa-driver-1.0.23/isa/wavefront'
make[3]: Leaving directory `/home/carmen/.local/share/Trash/files/alsa-driver-1.0.23/isa/wavefront'
make[3]: Entering directory `/home/carmen/.local/share/Trash/files/alsa-driver-1.0.23/isa/wss'
make[3]: Leaving directory `/home/carmen/.local/share/Trash/files/alsa-driver-1.0.23/isa/wss'
make[2]: Leaving directory `/home/carmen/.local/share/Trash/files/alsa-driver-1.0.23/isa'
make[2]: Entering directory `/home/carmen/.local/share/Trash/files/alsa-driver-1.0.23/synth'
make[3]: Entering directory `/home/carmen/.local/share/Trash/files/alsa-driver-1.0.23/synth/emux'
make[3]: Leaving directory `/home/carmen/.local/share/Trash/files/alsa-driver-1.0.23/synth/emux'
make[2]: Leaving directory `/home/carmen/.local/share/Trash/files/alsa-driver-1.0.23/synth'
make[2]: Entering directory `/home/carmen/.local/share/Trash/files/alsa-driver-1.0.23/pci'
make[3]: Entering directory `/home/carmen/.local/share/Trash/files/alsa-driver-1.0.23/pci/ac97'
make[3]: Leaving directory `/home/carmen/.local/share/Trash/files/alsa-driver-1.0.23/pci/ac97'
make[3]: Entering directory `/home/carmen/.local/share/Trash/files/alsa-driver-1.0.23/pci/ali5451'
make[3]: Leaving directory `/home/carmen/.local/share/Trash/files/alsa-driver-1.0.23/pci/ali5451'
make[3]: Entering directory `/home/carmen/.local/share/Trash/files/alsa-driver-1.0.23/pci/asihpi'
make[3]: Leaving directory `/home/carmen/.local/share/Trash/files/alsa-driver-1.0.23/pci/asihpi'
make[3]: Entering directory `/home/carmen/.local/share/Trash/files/alsa-driver-1.0.23/pci/au88x0'
make[3]: Leaving directory `/home/carmen/.local/share/Trash/files/alsa-driver-1.0.23/pci/au88x0'
make[3]: Entering directory `/home/carmen/.local/share/Trash/files/alsa-driver-1.0.23/pci/aw2'
make[3]: Leaving directory `/home/carmen/.local/share/Trash/files/alsa-driver-1.0.23/pci/aw2'
make[3]: Entering directory `/home/carmen/.local/share/Trash/files/alsa-driver-1.0.23/pci/ca0106'
make[3]: Leaving directory `/home/carmen/.local/share/Trash/files/alsa-driver-1.0.23/pci/ca0106'
make[3]: Entering directory `/home/carmen/.local/share/Trash/files/alsa-driver-1.0.23/pci/cs46xx'
make[3]: Leaving directory `/home/carmen/.local/share/Trash/files/alsa-driver-1.0.23/pci/cs46xx'
make[3]: Entering directory `/home/carmen/.local/share/Trash/files/alsa-driver-1.0.23/pci/cs5535audio'
make[3]: Leaving directory `/home/carmen/.local/share/Trash/files/alsa-driver-1.0.23/pci/cs5535audio'
make[3]: Entering directory `/home/carmen/.local/share/Trash/files/alsa-driver-1.0.23/pci/ctxfi'
make[3]: Leaving directory `/home/carmen/.local/share/Trash/files/alsa-driver-1.0.23/pci/ctxfi'
make[3]: Entering directory `/home/carmen/.local/share/Trash/files/alsa-driver-1.0.23/pci/echoaudio'
make[3]: Leaving directory `/home/carmen/.local/share/Trash/files/alsa-driver-1.0.23/pci/echoaudio'
make[3]: Entering directory `/home/carmen/.local/share/Trash/files/alsa-driver-1.0.23/pci/emu10k1'
make[3]: Leaving directory `/home/carmen/.local/share/Trash/files/alsa-driver-1.0.23/pci/emu10k1'
make[3]: Entering directory `/home/carmen/.local/share/Trash/files/alsa-driver-1.0.23/pci/hda'
make[3]: Leaving directory `/home/carmen/.local/share/Trash/files/alsa-driver-1.0.23/pci/hda'
make[3]: Entering directory `/home/carmen/.local/share/Trash/files/alsa-driver-1.0.23/pci/ice1712'
make[3]: Leaving directory `/home/carmen/.local/share/Trash/files/alsa-driver-1.0.23/pci/ice1712'
make[3]: Entering directory `/home/carmen/.local/share/Trash/files/alsa-driver-1.0.23/pci/korg1212'
make[3]: Leaving directory `/home/carmen/.local/share/Trash/files/alsa-driver-1.0.23/pci/korg1212'
make[3]: Entering directory `/home/carmen/.local/share/Trash/files/alsa-driver-1.0.23/pci/lx6464es'
make[3]: Leaving directory `/home/carmen/.local/share/Trash/files/alsa-driver-1.0.23/pci/lx6464es'
make[3]: Entering directory `/home/carmen/.local/share/Trash/files/alsa-driver-1.0.23/pci/mixart'
make[3]: Leaving directory `/home/carmen/.local/share/Trash/files/alsa-driver-1.0.23/pci/mixart'
make[3]: Entering directory `/home/carmen/.local/share/Trash/files/alsa-driver-1.0.23/pci/nm256'
make[3]: Leaving directory `/home/carmen/.local/share/Trash/files/alsa-driver-1.0.23/pci/nm256'
make[3]: Entering directory `/home/carmen/.local/share/Trash/files/alsa-driver-1.0.23/pci/oxygen'
make[3]: Leaving directory `/home/carmen/.local/share/Trash/files/alsa-driver-1.0.23/pci/oxygen'
make[3]: Entering directory `/home/carmen/.local/share/Trash/files/alsa-driver-1.0.23/pci/pcxhr'
make[3]: Leaving directory `/home/carmen/.local/share/Trash/files/alsa-driver-1.0.23/pci/pcxhr'
make[3]: Entering directory `/home/carmen/.local/share/Trash/files/alsa-driver-1.0.23/pci/pdplus'
make[3]: Leaving directory `/home/carmen/.local/share/Trash/files/alsa-driver-1.0.23/pci/pdplus'
make[3]: Entering directory `/home/carmen/.local/share/Trash/files/alsa-driver-1.0.23/pci/riptide'
make[3]: Leaving directory `/home/carmen/.local/share/Trash/files/alsa-driver-1.0.23/pci/riptide'
make[3]: Entering directory `/home/carmen/.local/share/Trash/files/alsa-driver-1.0.23/pci/rme9652'
make[3]: Leaving directory `/home/carmen/.local/share/Trash/files/alsa-driver-1.0.23/pci/rme9652'
make[3]: Entering directory `/home/carmen/.local/share/Trash/files/alsa-driver-1.0.23/pci/trident'
make[3]: Leaving directory `/home/carmen/.local/share/Trash/files/alsa-driver-1.0.23/pci/trident'
make[3]: Entering directory `/home/carmen/.local/share/Trash/files/alsa-driver-1.0.23/pci/vx222'
make[3]: Leaving directory `/home/carmen/.local/share/Trash/files/alsa-driver-1.0.23/pci/vx222'
make[3]: Entering directory `/home/carmen/.local/share/Trash/files/alsa-driver-1.0.23/pci/ymfpci'
make[3]: Leaving directory `/home/carmen/.local/share/Trash/files/alsa-driver-1.0.23/pci/ymfpci'
make[2]: Leaving directory `/home/carmen/.local/share/Trash/files/alsa-driver-1.0.23/pci'
make[2]: Entering directory `/home/carmen/.local/share/Trash/files/alsa-driver-1.0.23/aoa'
make[3]: Entering directory `/home/carmen/.local/share/Trash/files/alsa-driver-1.0.23/aoa/codecs'
make[3]: Leaving directory `/home/carmen/.local/share/Trash/files/alsa-driver-1.0.23/aoa/codecs'
make[3]: Entering directory `/home/carmen/.local/share/Trash/files/alsa-driver-1.0.23/aoa/core'
make[3]: Leaving directory `/home/carmen/.local/share/Trash/files/alsa-driver-1.0.23/aoa/core'
make[3]: Entering directory `/home/carmen/.local/share/Trash/files/alsa-driver-1.0.23/aoa/fabrics'
make[3]: Leaving directory `/home/carmen/.local/share/Trash/files/alsa-driver-1.0.23/aoa/fabrics'
make[3]: Entering directory `/home/carmen/.local/share/Trash/files/alsa-driver-1.0.23/aoa/soundbus'
make[4]: Entering directory `/home/carmen/.local/share/Trash/files/alsa-driver-1.0.23/aoa/soundbus/i2sbus'
make[4]: Leaving directory `/home/carmen/.local/share/Trash/files/alsa-driver-1.0.23/aoa/soundbus/i2sbus'
make[3]: Leaving directory `/home/carmen/.local/share/Trash/files/alsa-driver-1.0.23/aoa/soundbus'
make[2]: Leaving directory `/home/carmen/.local/share/Trash/files/alsa-driver-1.0.23/aoa'
make[2]: Entering directory `/home/carmen/.local/share/Trash/files/alsa-driver-1.0.23/soc'
make[3]: Entering directory `/home/carmen/.local/share/Trash/files/alsa-driver-1.0.23/soc/atmel'
make[3]: Leaving directory `/home/carmen/.local/share/Trash/files/alsa-driver-1.0.23/soc/atmel'
make[3]: Entering directory `/home/carmen/.local/share/Trash/files/alsa-driver-1.0.23/soc/au1x'
make[3]: Leaving directory `/home/carmen/.local/share/Trash/files/alsa-driver-1.0.23/soc/au1x'
make[3]: Entering directory `/home/carmen/.local/share/Trash/files/alsa-driver-1.0.23/soc/blackfin'
make[3]: Leaving directory `/home/carmen/.local/share/Trash/files/alsa-driver-1.0.23/soc/blackfin'
make[3]: Entering directory `/home/carmen/.local/share/Trash/files/alsa-driver-1.0.23/soc/codecs'
make[3]: Leaving directory `/home/carmen/.local/share/Trash/files/alsa-driver-1.0.23/soc/codecs'
make[3]: Entering directory `/home/carmen/.local/share/Trash/files/alsa-driver-1.0.23/soc/davinci'
make[3]: Leaving directory `/home/carmen/.local/share/Trash/files/alsa-driver-1.0.23/soc/davinci'
make[3]: Entering directory `/home/carmen/.local/share/Trash/files/alsa-driver-1.0.23/soc/fsl'
make[3]: Leaving directory `/home/carmen/.local/share/Trash/files/alsa-driver-1.0.23/soc/fsl'
make[3]: Entering directory `/home/carmen/.local/share/Trash/files/alsa-driver-1.0.23/soc/imx'
make[3]: Leaving directory `/home/carmen/.local/share/Trash/files/alsa-driver-1.0.23/soc/imx'
make[3]: Entering directory `/home/carmen/.local/share/Trash/files/alsa-driver-1.0.23/soc/omap'
make[3]: Leaving directory `/home/carmen/.local/share/Trash/files/alsa-driver-1.0.23/soc/omap'
make[3]: Entering directory `/home/carmen/.local/share/Trash/files/alsa-driver-1.0.23/soc/pxa'
make[3]: Leaving directory `/home/carmen/.local/share/Trash/files/alsa-driver-1.0.23/soc/pxa'
make[3]: Entering directory `/home/carmen/.local/share/Trash/files/alsa-driver-1.0.23/soc/s3c24xx'
make[3]: Leaving directory `/home/carmen/.local/share/Trash/files/alsa-driver-1.0.23/soc/s3c24xx'
make[3]: Entering directory `/home/carmen/.local/share/Trash/files/alsa-driver-1.0.23/soc/s6000'
make[3]: Leaving directory `/home/carmen/.local/share/Trash/files/alsa-driver-1.0.23/soc/s6000'
make[3]: Entering directory `/home/carmen/.local/share/Trash/files/alsa-driver-1.0.23/soc/sh'
make[3]: Leaving directory `/home/carmen/.local/share/Trash/files/alsa-driver-1.0.23/soc/sh'
make[3]: Entering directory `/home/carmen/.local/share/Trash/files/alsa-driver-1.0.23/soc/txx9'
make[3]: Leaving directory `/home/carmen/.local/share/Trash/files/alsa-driver-1.0.23/soc/txx9'
make[2]: Leaving directory `/home/carmen/.local/share/Trash/files/alsa-driver-1.0.23/soc'
make[2]: Entering directory `/home/carmen/.local/share/Trash/files/alsa-driver-1.0.23/usb'
make[3]: Entering directory `/home/carmen/.local/share/Trash/files/alsa-driver-1.0.23/usb/caiaq'
make[3]: Leaving directory `/home/carmen/.local/share/Trash/files/alsa-driver-1.0.23/usb/caiaq'
make[3]: Entering directory `/home/carmen/.local/share/Trash/files/alsa-driver-1.0.23/usb/misc'
make[3]: Leaving directory `/home/carmen/.local/share/Trash/files/alsa-driver-1.0.23/usb/misc'
make[3]: Entering directory `/home/carmen/.local/share/Trash/files/alsa-driver-1.0.23/usb/usx2y'
make[3]: Leaving directory `/home/carmen/.local/share/Trash/files/alsa-driver-1.0.23/usb/usx2y'
make[2]: Leaving directory `/home/carmen/.local/share/Trash/files/alsa-driver-1.0.23/usb'
make[2]: Entering directory `/home/carmen/.local/share/Trash/files/alsa-driver-1.0.23/pcmcia'
make[3]: Entering directory `/home/carmen/.local/share/Trash/files/alsa-driver-1.0.23/pcmcia/pdaudiocf'
make[3]: Leaving directory `/home/carmen/.local/share/Trash/files/alsa-driver-1.0.23/pcmcia/pdaudiocf'
make[3]: Entering directory `/home/carmen/.local/share/Trash/files/alsa-driver-1.0.23/pcmcia/vx'
make[3]: Leaving directory `/home/carmen/.local/share/Trash/files/alsa-driver-1.0.23/pcmcia/vx'
make[2]: Leaving directory `/home/carmen/.local/share/Trash/files/alsa-driver-1.0.23/pcmcia'
make[1]: Leaving directory `/home/carmen/.local/share/Trash/files/alsa-driver-1.0.23'
make -C /lib/modules/2.6.35-24-generic/build SUBDIRS=/home/carmen/.local/share/Trash/files/alsa-driver-1.0.23  CPP="gcc -E" CC="gcc" modules
make[1]: Entering directory `/usr/src/linux-headers-2.6.35-24-generic'
  CC [M]  /home/carmen/.local/share/Trash/files/alsa-driver-1.0.23/acore/hwdep.o
In file included from /home/carmen/.local/share/Trash/files/alsa-driver-1.0.23/include/config.h:6,
                 from /home/carmen/.local/share/Trash/files/alsa-driver-1.0.23/include/adriver.h:25,
                 from /home/carmen/.local/share/Trash/files/alsa-driver-1.0.23/acore/hwdep.c:1:
/home/carmen/.local/share/Trash/files/alsa-driver-1.0.23/include/config1.h:175: warning: "CONFIG_SND_HDA_INPUT_BEEP_MODE" redefined
./include/generated/autoconf.h:2099: note: this is the location of the previous definition
In file included from /home/carmen/.local/share/Trash/files/alsa-driver-1.0.23/include/config.h:6,
                 from /home/carmen/.local/share/Trash/files/alsa-driver-1.0.23/include/adriver.h:25,
                 from /home/carmen/.local/share/Trash/files/alsa-driver-1.0.23/acore/hwdep.c:1:
/home/carmen/.local/share/Trash/files/alsa-driver-1.0.23/include/config1.h:175: warning: "CONFIG_SND_HDA_INPUT_BEEP_MODE" redefined
./include/generated/autoconf.h:2099: note: this is the location of the previous definition
  CC [M]  /home/carmen/.local/share/Trash/files/alsa-driver-1.0.23/acore/memory_wrapper.o
In file included from /home/carmen/.local/share/Trash/files/alsa-driver-1.0.23/include/config.h:6,
                 from /home/carmen/.local/share/Trash/files/alsa-driver-1.0.23/include/alsa-autoconf.h:4,
                 from /home/carmen/.local/share/Trash/files/alsa-driver-1.0.23/acore/memory_wrapper.c:1:
/home/carmen/.local/share/Trash/files/alsa-driver-1.0.23/include/config1.h:175: warning: "CONFIG_SND_HDA_INPUT_BEEP_MODE" redefined
./include/generated/autoconf.h:2099: note: this is the location of the previous definition
  CC [M]  /home/carmen/.local/share/Trash/files/alsa-driver-1.0.23/acore/memalloc.o
In file included from /home/carmen/.local/share/Trash/files/alsa-driver-1.0.23/include/config.h:6,
                 from /home/carmen/.local/share/Trash/files/alsa-driver-1.0.23/include/alsa-autoconf.h:4,
                 from /home/carmen/.local/share/Trash/files/alsa-driver-1.0.23/acore/memalloc.inc:1,
                 from /home/carmen/.local/share/Trash/files/alsa-driver-1.0.23/acore/memalloc.c:1:
/home/carmen/.local/share/Trash/files/alsa-driver-1.0.23/include/config1.h:175: warning: "CONFIG_SND_HDA_INPUT_BEEP_MODE" redefined
./include/generated/autoconf.h:2099: note: this is the location of the previous definition
In file included from /home/carmen/.local/share/Trash/files/alsa-driver-1.0.23/include/config.h:6,
                 from /home/carmen/.local/share/Trash/files/alsa-driver-1.0.23/include/alsa-autoconf.h:4,
                 from /home/carmen/.local/share/Trash/files/alsa-driver-1.0.23/acore/memalloc.inc:1,
                 from /home/carmen/.local/share/Trash/files/alsa-driver-1.0.23/acore/memalloc.c:1:
/home/carmen/.local/share/Trash/files/alsa-driver-1.0.23/include/config1.h:175: warning: "CONFIG_SND_HDA_INPUT_BEEP_MODE" redefined
./include/generated/autoconf.h:2099: note: this is the location of the previous definition
  CC [M]  /home/carmen/.local/share/Trash/files/alsa-driver-1.0.23/acore/sgbuf.o
In file included from /home/carmen/.local/share/Trash/files/alsa-driver-1.0.23/include/config.h:6,
                 from /home/carmen/.local/share/Trash/files/alsa-driver-1.0.23/include/alsa-autoconf.h:4,
                 from /home/carmen/.local/share/Trash/files/alsa-driver-1.0.23/acore/sgbuf.c:1:
/home/carmen/.local/share/Trash/files/alsa-driver-1.0.23/include/config1.h:175: warning: "CONFIG_SND_HDA_INPUT_BEEP_MODE" redefined
./include/generated/autoconf.h:2099: note: this is the location of the previous definition
  CC [M]  /home/carmen/.local/share/Trash/files/alsa-driver-1.0.23/acore/pcm.o
In file included from /home/carmen/.local/share/Trash/files/alsa-driver-1.0.23/include/config.h:6,
                 from /home/carmen/.local/share/Trash/files/alsa-driver-1.0.23/include/adriver.h:25,
                 from /home/carmen/.local/share/Trash/files/alsa-driver-1.0.23/acore/pcm.c:1:
/home/carmen/.local/share/Trash/files/alsa-driver-1.0.23/include/config1.h:175: warning: "CONFIG_SND_HDA_INPUT_BEEP_MODE" redefined
./include/generated/autoconf.h:2099: note: this is the location of the previous definition
In file included from /home/carmen/.local/share/Trash/files/alsa-driver-1.0.23/include/config.h:6,
                 from /home/carmen/.local/share/Trash/files/alsa-driver-1.0.23/include/adriver.h:25,
                 from /home/carmen/.local/share/Trash/files/alsa-driver-1.0.23/acore/pcm.c:1:
/home/carmen/.local/share/Trash/files/alsa-driver-1.0.23/include/config1.h:175: warning: "CONFIG_SND_HDA_INPUT_BEEP_MODE" redefined
./include/generated/autoconf.h:2099: note: this is the location of the previous definition
  CC [M]  /home/carmen/.local/share/Trash/files/alsa-driver-1.0.23/acore/pcm_native.o
In file included from /home/carmen/.local/share/Trash/files/alsa-driver-1.0.23/include/config.h:6,
                 from /home/carmen/.local/share/Trash/files/alsa-driver-1.0.23/include/adriver.h:25,
                 from /home/carmen/.local/share/Trash/files/alsa-driver-1.0.23/acore/pcm_native.c:2:
/home/carmen/.local/share/Trash/files/alsa-driver-1.0.23/include/config1.h:175: warning: "CONFIG_SND_HDA_INPUT_BEEP_MODE" redefined
./include/generated/autoconf.h:2099: note: this is the location of the previous definition
/home/carmen/.local/share/Trash/files/alsa-driver-1.0.23/acore/pcm_native.c: In function ‘snd_pcm_hw_params’:
/home/carmen/.local/share/Trash/files/alsa-driver-1.0.23/acore/pcm_native.c:489: error: implicit declaration of function ‘pm_qos_remove_requirement’
/home/carmen/.local/share/Trash/files/alsa-driver-1.0.23/acore/pcm_native.c:492: error: implicit declaration of function ‘pm_qos_add_requirement’
make[3]: *** [/home/carmen/.local/share/Trash/files/alsa-driver-1.0.23/acore/pcm_native.o] Error 1
make[2]: *** [/home/carmen/.local/share/Trash/files/alsa-driver-1.0.23/acore] Error 2
make[1]: *** [_module_/home/carmen/.local/share/Trash/files/alsa-driver-1.0.23] Error 2
make[1]: Leaving directory `/usr/src/linux-headers-2.6.35-24-generic'
make: *** [compile] Error 2

```

any suggestions or ideas?

---

### Post by lingenfr on 2010-12-23
Yes, as mentioned several times in this thread, the drivers are no longer required in 10.10. Sound is supported natively.

---

### Post by cjcardinal on 2010-12-23
> **lingenfr said:**
> Yes, as mentioned several times in this thread, the drivers are no longer required in 10.10. Sound is supported natively.

Yes thanks.  I know it was mentioned "several times." my issue is that they don't work, SO I attempted to re-compile them manually.  So anny suggestions as to how to get my sound working again?

---

### Post by lingenfr on 2010-12-23
When you click on the speaker in the System Tray, click on Sound Preferences and then click on Hardware, what is listed?

---

### Post by cjcardinal on 2010-12-23
> **lingenfr said:**
> When you click on the speaker in the System Tray, click on Sound Preferences and then click on Hardware, what is listed?

Nothingis there...it's kinda weird.  Thats why I thought of recompiling them...and when I reverted back to the latest 10.04 kernel, the sound worked, but AVIs wouldn't have any sound in VLC even after a reinstall of VLC

I'm thinking of just reinstalling 10.10 from scratch

---

### Post by cjcardinal on 2010-12-23
no one has any suggestions?  I decided to revert back to my last kernel that i had while using 10.04, and my sound worked EXCEPT for some reason,, i had no sound when playing AVI's.  all of these issues are brand-new since upgrading to 10.10 from 10.04.

my only issue prior to upgrading was out of the blue i started running at 144 degrees PLUS for both cores and my GPU...now that i have upgraded, i am in the mid 120's and sometimes the 110's depending on what i'm doing (or not doing i guess you could say)

any help with this would be greatly appreciated as currently i am downloding the 10.10 64bit ISO to do a clean install if i cant figure this out

---

### Post by lingenfr on 2010-12-24
Unfortunately, I think that will be the quickest route.

---

### Post by cjcardinal on 2010-12-24
> **lingenfr said:**
> Unfortunately, I think that will be the quickest route.

haha yeah thats what i did last night

thanks for the help though...strange what happened

---

### Post by ianpavlovic on 2011-01-20
Hi can some one help me my wireless on my m11x is not working im a complete noob :D

---

### Post by moondoggy2 on 2011-01-20
> **ianpavlovic said:**
> Hi can some one help me my wireless on my m11x is not working im a complete noob :D

I had the same problem when I made the switch last March.  
First thing, you need to hard wire your laptop.  So, go ahead and plug it into your router.  Then, click SYSTEM>>ADMINISTRATION>>ADDITIONAL DRIVERS

Just a quick FYI: Every time I downloaded the drivers for my nvidia card, things just never worked the same.  Resulting in a couple reformats and clean installs.  

Hope this helps.

---

### Post by Mecasickle on 2011-01-22
I think the NVidia problem should really be fixed for Ubuntu on the Aliewnare m11x.

One of the main reasons I bought this machine was for my Computer Vision and Parallel processing research (with CUDA). I feel that feeling confortable with the intel graphics card is like wasting the money on why someone bought this pricey computer (after social/intelectual status of course) in the first place.

If anyone found the solution please fill us in!

I Think I might write to the guys at NVidia to see if they can help us out!

---

### Post by Mecasickle on 2011-01-22
I just found a solution to this problem here:

[http://linux-hybrid-graphics.blogspot.com/2010/10/howto-allienware-m11x-r2-nvidia-optimus.html](http://linux-hybrid-graphics.blogspot.com/2010/10/howto-allienware-m11x-r2-nvidia-optimus.html)

(To activate the Nvidia driver) ( GO CUDA!)

I'm gonna' test it on Monday, but if anyone tries it before, please comment results!! =D

See you guys!

---

### Post by andamaru on 2011-01-31
> **Mecasickle said:**
> I just found a solution to this problem here:

[http://linux-hybrid-graphics.blogspot.com/2010/10/howto-allienware-m11x-r2-nvidia-optimus.html](http://linux-hybrid-graphics.blogspot.com/2010/10/howto-allienware-m11x-r2-nvidia-optimus.html)

(To activate the Nvidia driver) ( GO CUDA!)

I'm gonna' test it on Monday, but if anyone tries it before, please comment results!! =D

See you guys!

I'm going to be purchasing this machine for a game dev course and I was wondering how your tests went.

---

### Post by callmemister on 2011-02-03
> **Mecasickle said:**
> I just found a solution to this problem here:

[http://linux-hybrid-graphics.blogspot.com/2010/10/howto-allienware-m11x-r2-nvidia-optimus.html](http://linux-hybrid-graphics.blogspot.com/2010/10/howto-allienware-m11x-r2-nvidia-optimus.html)

(To activate the Nvidia driver) ( GO CUDA!)

I'm gonna' test it on Monday, but if anyone tries it before, please comment results!! =D

See you guys!

Did it work ?  I think that every owner of M11x R2 got a bit F*ed in the *** by Nvidia Optimus ! .. i really can't wait when it's gonna work.

---

### Post by Biciclettapc on 2011-02-05
Just received my M11x :)

Planning on dual booting.

Question, which I posted in another forum also:

Which version to install?  Desktop or Netbook?  

I like the idea of larger graphics on the netbook.

Paul

---

### Post by lingenfr on 2011-02-05
Desktop. Netbook is for a netbook, not a laptop.

---

### Post by Biciclettapc on 2011-02-05
Thanks.

Wasnt sure as this sort of falls in the crack?

11" screen to me is more a net book.

---

### Post by tahnok on 2011-02-05
So I've been really bothered by the jumpy cursor when I accidental have two points of input on the trackpad, but I found a way to fix it on the notebook review forums

```
xinput set-int-prop "SynPS/2 Synaptics TouchPad" "Synaptics Jumpy Cursor Threshold" 32 110
```

Hope that helps

---

### Post by jamh on 2011-02-14
I'm expecting to receive my m11x this week.

Is anything special needed for the i7 chip?  I imagine you'd need the 64-bit ubuntu.

Can someone summarize the extra things needed? So far I gathered that sound needs Realtek drivers from their site, and switchable graphics needs a kernel beta hack (or wait).  Anything else?  Thanks.

---

### Post by Biciclettapc on 2011-02-14
I'm core 2 duo cpu.

I had 0 problems.  Installed the restricted drivers for VC and the modem.  

Working very well.... :D

---

### Post by lingenfr on 2011-02-14
> **jamh said:**
> I'm expecting to receive my m11x this week.

Is anything special needed for the i7 chip?  I imagine you'd need the 64-bit ubuntu.


Need no, recommended (by me) yes.

> **jamh said:**
> Can someone summarize the extra things needed?


Someone can and someone has several posts back in the thread.

> **jamh said:**
>  So far I gathered that sound needs Realtek drivers from their site, 

Gathered incorrectly, the Realtek drivers have not been required for quite some time.

> **jamh said:**
> and switchable graphics needs a kernel beta hack (or wait).  Anything else?  Thanks.

Will leave this for someone else. I don't have switchable working, but have been able to switch the nvidia off which is also detailed previously in the thread. Good luck.

---

### Post by DDriver on 2011-02-19
I have R1 and used simonhein's tutorial (thanks!) to make everything work.

Now I am wondering about power consumption. In Windows i've got 7.2-7.8W on idle. With light internet browsing 8.5-9.5W. Under Ubuntu (after using powertop, cpufreq set to powersafe) on idle is 9-10, with browsing around 10-11W. So I am losing more than 1W compare to Windows and I though Windows is what should use energy for nothing. Am I missing something that could be turned off (unnecessary daemons) to not use CPU time?

Thanks in advance

---

### Post by tahnok on 2011-02-19
How are you checking the power consumption in windows?

---

### Post by DDriver on 2011-02-19
> **tahnok said:**
> How are you checking the power consumption in windows?

Using "Battery Bar" and some other hardware monitor (don't remember the name) - report same rates. 

Also forgot to mention - Wifi is on both times. Maybe it's Wifi driver is not working properly. I am using the default Broadcom STA driver. Sometimes wifi looses connection, and bad driver can explain 1W difference in consumption. When I am turning wifi in Ubuntu there is no difference in discharge rate. Are there any better options for Wifi to work?

---

### Post by tahnok on 2011-02-19
really? I notice a 1W drop when I turn off wifi. I'm not sure what else can be done to lower power consumption further. Are all of the LEDs off on the keyboard?

---

### Post by lingenfr on 2011-02-20
I am running 64-bit Maverick. The gnome bluetooth applet has not worked in quite some time to pair a device. To be clear, I have the applet and I have paired my mouse and BT3030, but each time I try to use the applet to add a device it searches forever. Does anyone have a fix?

---

### Post by kvizzel on 2011-02-23
HELP!

Running 64-Bit Maverick on my M11X R1. (BIOS GRAPHICS SET TO DISCRETE. INSTALLED NVIDIA X SERVER.)

I'm able to get HDMI video out, same with VGA. but my HDMI does NOT have sound. The sound stays playing on my M11X.

Anybody know a fix? 

Thanks!!!

---

### Post by juanoleso on 2011-02-23
I have the same problem.  Sound over HDMI does not work in Windows as well if that helps anybody.

---

### Post by kvizzel on 2011-02-23
> **juanoleso said:**
> I have the same problem.  Sound over HDMI does not work in Windows as well if that helps anybody.

Weird. Mine works perfectly fine in Windows 7.

---

### Post by erik.osterholm on 2011-02-25
Can someone tell me what sort of battery life they're seeing on the R2 after having disabled the nVidia graphics?  In hours, preferably? :)

---

### Post by Jeff_1881 on 2011-02-27
I just had my mx11 R2 i5 520um with 4GB memory, 500GB hardisk , Can't live without ubuntu,, I installed 10.10 32bit
Everything seems nice. 

Sound worked fine. (no effort)
Alien FX implemented the Java program posted earlier.


Battery shows 3:30 hours left when full.
Graphic card Nvidia is not working, I tried to install the factory one I ended up with ubuntu stuck in booting screen, I had to uninsulated it. 

The most annoying thing is that Ubuntu is not recognising the 4GB instead 1.9 GB. I paid more money on the memory because I use the Ramdisk to store all the browsers cache.




Anybody over come this problem..

update:

For those who had problem with memory. you need to enable [Physical Address Extension]("http://en.wikipedia.org/wiki/Physical_Address_Extension") 

the following line will install header with PAE,, now I got 3.7 GB ;) better than 1.9GB

sudo apt-get install linux-generic-pae linux-headers-generic-pae


if you want to add cpu temp :

sudo apt-get install lm-sensors
sudo modprobe coretemp
sensors ; will give the reading.
sudo apt-get install sensors-applet

now add the applet (hardware sensor) in the top panel, right click on it to go to preference for cpu selection.

---

### Post by Exakun on 2011-02-28
I recently bought an M11X R2 with an i7. I installed Desktop 10.04 x64 on it and after compiling the audio driver (sound was the only thing not working after installing restricted wireless drivers) I thought everything was working great.

I decided I would try to install the latest nvidia driver from their website. The installation process requires runlevel 5 with gdm stopped, so after downloading the driver I stopped gdm (sudo service gdm stop) in preparation for switching to tty1 (CTRL+ALT+1). I have always installed the nvidia driver on my desktop in the same manner without issue. However, this resulted in a blank screen. The system was not completely unresponsive but I couldn't do anything except reboot the system with ALT+SYSRQ+REISUB.

I then tried to boot into recovery mode and was greeted with a blank screen-- nothing I could do yet again. Rebooting back into a normal startup presented me with the graphical login screen, but I get the frozen image of a glitched graphical login screen every time I navigate away from the graphical login screen.

Obviously, this is disconcerting and I really need to find a solution to this problem. Does anyone know how I can fix this? Thanks in advance for your consideration.

---

### Post by Mecasickle on 2011-03-03
Interested on using CUDA and your NVidia graphics Card on linux ? 

Check out this forum: 

[http://www.nvnews.net/vbulletin/showthread.php?t=144750&highlight=alienware](http://www.nvnews.net/vbulletin/showthread.php?t=144750&highlight=alienware)

---

### Post by oggie on 2011-03-07
Does anyone know if the cooling fan is working correctly on this machine and 10.10? I never hear the fan come on, even when I'm compiling code.

X has restarted on me before as well while in the middle of a build.

I am able to monitor the CPU temps and I see them go up to 53 degrees celsius and still no fan activity at all.

Is there a tool you can use to turn the fans on/off and adjust the thresholds of the fans?

---

### Post by Biciclettapc on 2011-03-07
> **oggie said:**
> does anyone know if the cooling fan is working correctly on this machine and 10.10? I never hear the fan come on, even when i'm compiling code.

X has restarted on me before as well while in the middle of a build.

I am able to monitor the cpu temps and i see them go up to 53 degrees celsius and still no fan activity at all.

Is there a tool you can use to turn the fans on/off and adjust the thresholds of the fans?

+1

---

### Post by darkamikaze on 2011-03-08
Anyone find a good way to do a three finger gesture left/right ? I'm so used to having this on my win7 side using a program.. I was wondering if anyone knows of such? 

I've tried touchegg and it's very skippy mouse wise..

---

### Post by Jeff_1881 on 2011-03-08
> **oggie said:**
> Does anyone know if the cooling fan is working correctly on this machine and 10.10? I never hear the fan come on, even when I'm compiling code.

X has restarted on me before as well while in the middle of a build.

I am able to monitor the CPU temps and I see them go up to 53 degrees celsius and still no fan activity at all.

Is there a tool you can use to turn the fans on/off and adjust the thresholds of the fans?

The fan works when the 54 is reached, as far as it stays below that you are OK..

---

### Post by Jeff_1881 on 2011-03-08
The fan works when the 54 is reached, as far as it stays below that you are OK..

---

### Post by rs3 on 2011-03-11
Just bought the M11x.  Core 2 Duo SU7300, 4GB memory, 320GB drive.  The service tag on the Dell site tells me it's an R3, but I don't think that's right; I figured it was an R1 based on the specifications.

I installed Maverick amd64 last night.  Graphics are set to "discrete" mode and the Restricted Nvidia driver installs/works fine.  Had to also use a restricted Broadcom driver for wifi.  Webcam came up with Cheese.

Only issues I have seen thus far:

* Touchpad is jumpy, but far less so after running updates.
* Battery life is less than stellar (probably about three hours with non-gaming use).  I haven't messed with going Intel/disabling the Nvidia GPU with acpi_call, and I might go that route since the Intel acceleration was plenty fine for Compiz, but I was looking forward to trying a couple games first. ;)
* Occasional artifacts on gnome-panel, which also happened with my last laptop (Intel IGP) when running Compiz.

My to-do list:

* Try the AlienFX app to give my lights a more Ubuntu-fied look.
* Install a demanding 3D game and see how it runs.
* Test HDMI out (I'm told to expect audio to not carry across HDMI, so there might be some work ahead)
* Enable BIOS overclocking and see if it stays up during a heavy compile!

---

### Post by tahnok on 2011-03-11
Overclock that baby already! I've had that setting enabled since I got my machine in September and I don't think it's ever caused my problems.

---

### Post by Philip550c on 2011-03-15
I have an m11xR1 and everything works great, except no sound over HDMI. I have it selected as the output and in alsamixer I switched to the NVIDIA soundcard and unmuted all 4 outputs, but still no sound. Has anyone gotten HDMI audio to work?

---

### Post by rs3 on 2011-03-15
Ditto; I tried HDMI audio out last night.  It is recognized in Sound Preferences as an output device but only produces silence.  

Also, suspend results in an unrecoverable state on wake-up.  Screen backlight turns on but nothing happens, can't get to tty.  Have to hold power button and force shutdown.

Other findings:

[LIST]
[*]I tried a Natty daily build (kernel 2.6.38) and saw that the trackpad was much nicer.
[*]I'm now using the 32-bit build of Maverick as my installed OS and though I'm not 100% certain, battery life estimates look better than they were in 64-bit.
[*]After installing linux-generic-pae, rebooting resulted in a terminal session.  I was previously using the Nvidia binary drivers.  Moving or deleting /etc/X11/xorg.conf and restarting gdm brought me back to the Additional Drivers helper and I was able to re-activate the driver.  Oddly, my wifi failed too, but after fixing the Nvidia driver, the Broadcom driver was restored as well.
[/LIST]

---

### Post by lucasbuck on 2011-03-19
I have an m11x r2 and ubuntu desktop 10.10 installed.

here are a few findings i have found that i thought might be helpful -> most has been intense googling and testing, i did not create most of these hacks (urls are included to sources)


touchpad -> 
this will get 2 finger scrolling working, among other things
source -> [http://forums.linuxmint.com/viewtopic.php?f=49&t=50621&p=314062](http://forums.linuxmint.com/viewtopic.php?f=49&t=50621&p=314062)

this is my script - hacked a little :
------
#!/bin/bash
#
xinput --set-prop --type=int --format=32 "SynPS/2 Synaptics TouchPad" "Synaptics Two-Finger Pressure" 4
xinput --set-prop --type=int --format=32 "SynPS/2 Synaptics TouchPad" "Synaptics Two-Finger Width" 8
xinput --set-prop --type=int --format=8  "SynPS/2 Synaptics TouchPad" "Synaptics Two-Finger Scrolling" 1 1
xinput --set-prop --type=int --format=8  "SynPS/2 Synaptics TouchPad" "Synaptics Edge Scrolling" 0 0 0
xinput --set-prop --type=int --format=32 "SynPS/2 Synaptics TouchPad" "Synaptics Jumpy Cursor Threshold" 250
xinput --set-prop --type=int --format=8  "SynPS/2 Synaptics TouchPad" "Synaptics Tap Action" 0 0 0 0 1 2 3
xinput --set-prop --type=int --format=8  "SynPS/2 Synaptics TouchPad" "Synaptics Palm Detection" 1
synclient TapButton3=2 ##two finger tap for middle-click
synclient TapButton2=3 ##should be 3 finger tap right click but doesn't work

xinput --set-button-map "SynPS/2 Synaptics TouchPad" 1 2 3 4 5 6 7 8 9
exit
-----

chmod it, and run. it will work right away. i have found after any laptop suspend or hibinate it needs to be re-run. I am working on scripting this in to gui startup, but attempts have failed so far, and i dont want to put it in a cron. 
 

Power Saving ->
nvidia gfx card disable (it doesn't work anyway, so lets save power!) -> 

apt-get install acpi
cat /proc/acpi/battery/BAT1/state (this will show your mW draw)
source -> [http://forums.fedoraforum.org/showpost.php?p=1402584&postcount=45](http://forums.fedoraforum.org/showpost.php?p=1402584&postcount=45)
(download the files and make)
insmod m11xr2hack.ko
lsmod | grep m11x (check that its loaded)
then check batt status again

i managed to get my battery draw (with wifi and full screen brightness down from 23000mW (2.2hrs batt) or so to 17500mW (3.2hrs batt), without wifi and lowered screen brightness to about 14000mW (5hrs batt)
i have found this needs to be added after reboot + suspend / hibinate etc -> working on scripts for this.


HDMI Audio ->
tested and working
source -> [http://wiki.foxmediasystems.com/index.php/Ubuntu_Intel_HDMI_Audio](http://wiki.foxmediasystems.com/index.php/Ubuntu_Intel_HDMI_Audio)

on m11x r2 i was using 
# speaker-test -Dplughw:0,3
to test static sound over the hdmi cabled, it also worked with speaker-test -Dplughw:0,7
i was able to just select the vlc output sound device to be hdmi and it has worked very well.


AlienFX lite ->
source -> [http://ubuntuforums.org/showthread.php?t=1403399](http://ubuntuforums.org/showthread.php?t=1403399)


Emapthy msn network connect ->
empathy was having issues connectin to MSN
locate RequestMultipleSecurityTokens.py (should be in SingleSignOn path)
vi /usr/lib/pymodules/python2.6/papyon/service/description/SingleSignOn/RequestMultipleSecurityTokens.py
edit CONTACTS row to : CONTACTS = ("contacts.msn.com", "MBI")
save, exit, reload empathy. msn now connects.


I have a few bits of hacking to do and will add any updates when i make advances

---

### Post by rs3 on 2011-03-19
Good stuff, good finds; I'm looking forward to trying out the touchpad script.  Thanks!

---

### Post by erik.osterholm on 2011-03-19
I changed:
xinput --set-button-map "SynPS/2 Synaptics TouchPad" 1 3 3 4 5 6 7 8 9

to:
xinput --set-button-map "SynPS/2 Synaptics TouchPad" 1 2 3 4 5 6 7 8 9

Because otherwise, I lost the ability to middle-click with both mouse buttons.  Also, do the synclient lines really do anything?  I removed them and noticed no change in behavior.

---

### Post by lucasbuck on 2011-03-19
unknown, i will do some more playing about. it SHOULD support 3 finger taps.

got hdmi audio to work, editing my post above to have solutions all in once place, i will add your change to the touchpad script too.

---

### Post by erik.osterholm on 2011-03-19
Great job!

I'll also add this modification I made to my own r2.  I swapped out the wireless card for this one: [http://www.amazon.com/Intel-802-11n-draft-Wi-Fi-Adapter/dp/B0036BJN12/ref=sr_1_1?ie=UTF8&qid=1300588388&sr=8-1](http://www.amazon.com/Intel-802-11n-draft-Wi-Fi-Adapter/dp/B0036BJN12/ref=sr_1_1?ie=UTF8&qid=1300588388&sr=8-1)

I generally prefer Intel cards for the driver, which I didn't have to download post-install, and which generally works better.  Connecting to my access point was noticeably faster (not that it was that slow before) and the connection has been more stable.

That said, I did have to remove /etc/modpobe.d/intel-5300-iwlagn-disable11n.conf to get 802.11n working.

---

### Post by rs3 on 2011-03-20
> **erik.osterholm said:**
> Great job!

I'll also add this modification I made to my own r2.  I swapped out the wireless card for this one: [http://www.amazon.com/Intel-802-11n-draft-Wi-Fi-Adapter/dp/B0036BJN12/ref=sr_1_1?ie=UTF8&qid=1300588388&sr=8-1](http://www.amazon.com/Intel-802-11n-draft-Wi-Fi-Adapter/dp/B0036BJN12/ref=sr_1_1?ie=UTF8&qid=1300588388&sr=8-1)

I generally prefer Intel cards for the driver, which I didn't have to download post-install, and which generally works better.  Connecting to my access point was noticeably faster (not that it was that slow before) and the connection has been more stable.

That said, I did have to remove /etc/modpobe.d/intel-5300-iwlagn-disable11n.conf to get 802.11n working.

I have noticed at my workplace that I tend to drop frequently from the network.  I was not sure if the Broadcom wireless card was at fault, but I did not have the same problems with my Dell Inspiron 1420 (which uses an Intel card).  I've swapped memory, hard drives, &c on other laptops; is a laptop mini-PCI card significantly more difficult to replace?  I'll check this out and hope for the best.  Thanks!

---

### Post by erik.osterholm on 2011-03-20
It was pretty easy.  Power off the laptop.  8 screws to remove the bottom panel, disconnect the battery (just to be safe--I didn't bother, to be honest), disconnect two wires  to the antenna (remember which ones goes where), unscrew the card and it pops up.  Swap the cards, then put everything back together.

Took me probably 10 minutes from poweroff to poweron.  If you dual-boot Windows, don't forget to grab the Intel drivers from their website.

---

### Post by iRommel on 2011-03-21
Excellent post lucasbuck, very helpful. If you want to automate the nvidia disable then add:

insmod /home/XXX/path_to_file/m11xr2hack.ko

to /etc/rc.local to avoid the whole sudo situation

---

### Post by lucasbuck on 2011-03-21
thanks :) i tried adding it to /etc/init.d and calling it from /etc/rc2.d (my runlevel) but it didn't like that, i'll try this too and add it the post above. 

anything else people want me to look in to?

---

### Post by iRommel on 2011-03-22
i turned off tap-clicking and autorun the script you gave and it stopped my mouse going crazy, its still really sensitive though, i need only hover over it and it goes a bit nuts.. makes clicking things an exciting affair. anyone else experiencing something similar?

---

### Post by erik.osterholm on 2011-03-23
> **iRommel said:**
> i turned off tap-clicking and autorun the script you gave and it stopped my mouse going crazy, its still really sensitive though, i need only hover over it and it goes a bit nuts.. makes clicking things an exciting affair. anyone else experiencing something similar?

I've found that the pointer basically goes nuts if you boot Windows, reboot (rather than shut down) and boot Linux.  If you shut down fully between Windows and Linux, the touchpad is fine.  This is on an R2.

---

### Post by Mecasickle on 2011-04-28
Guys I found out this post on installing CUDA on the Alienware m11x-R2:

[http://forums.nvidia.com/index.php?showtopic=184288](http://forums.nvidia.com/index.php?showtopic=184288)

Check it out, and comment on your results, I'll be busy till the weekend and will post my results by saturday noon.

---

### Post by flyingAnt on 2011-04-28
This sounds like a post that should be on Alienware's website and not  here, I know. The only reason I am mentioning this is to anyone who is  interested in getting one and putting Ubuntu on it. If I had to do this  over again, I'd wait. In time, I believe the Alien FX lighting, the  sound card, and the video card switching will work. Also, (hopefully)  the quality of the actual hardware will improve. Very disappointed in  that.

Carry on...:popcorn:

---

### Post by graups on 2011-04-29
Hi, I have a m11x r2 that I have been running 10.10 on for a while with success. I just upgraded to 11.04 and having an issue with my external monitor connected via HDMI.

When I plug it in both the laptop screen and the external monitor are blank. If I unplug the hdmi port I can see and move my mouse pointer but the laptop display does not refresh. Clicking in areas that should have icons etc on them does not seem to cause any action. At this point, if I reboot the laptop will display properly.

Anyone know what I might try to address this?

Thanks,
scott.

Fixed?: I may have fixed it but I have not had a chance to reboot to see if it sticks. I plugged in the HDMI monitor and, as expected both screens were black. I switched to a virtual shell (ctrl-alt-F1) and ran sudo dpkg-reconfigure xwindows-xorg-video-intel (that name may be wrong, tab complete and you will find it). Then I unplugged the HDMI and plugged it back in. Suddenly I was up and running on my external monitor.

I had to get some work done so I stopped messing with it at that point. I'll update again if it doesn't seem to stick. Further complicating the issues is the fact that I was in and out of the shell reconfiguring various packages and restart X so the steps above may not be all that is required.

---

### Post by lingenfr on 2011-04-29
I have the R1 and have upgraded to 11.04. So far, so good. Not too wild about Unity, but maybe it will grow on me.

---

### Post by Slowpokemon on 2011-05-05
> **JailHouseRock said:**
> When I did this:
```
git clone [http://github.com/mkottman/acpi_call.git](http://github.com/mkottman/acpi_call.git)
cd acpi_call
make
sudo insmod acpi_call.ko
./test_off.sh
```And then this:
```
grep rate /proc/acpi/battery/BAT1/state
```It gave me:
```
present rate:            12256 mW
```Before it was 19402 mW, as far as I can tell that means it worked.

I'm running Natty Narwhal 64-bit edition on my M11x r1. The above method worked for me as well to turn off/disable the Nvidia card; however, I do occasionally encounter a problem with it.

The problem is this: about 50% of the time upon running *test_off.sh*, the script will complete successfully. A few seconds later, the whole computer will freeze. Restarting X doesn't work, so I am forced to hold down the power button until the machine shuts off. On the other hand, the script works flawlessly the other 50% of the time. I'm not sure if it's relevant, but it has never worked when Firefox is open, though it hasn't always worked while Firefox is not running. Even if I run *test_off.sh* just after booting, it is not guaranteed to work. Has anybody else run into this issue? I would greatly appreciate any insight.

The above is mainly an issue because I have to run the following two commands each time I log in:
```
sudo insmod acpi_call.ko
./test_off.sh
```Is there any way to automate this?

** Edit:** I installed the Nvidia driver and now my computer doesn't freeze when I run test_off.sh! lshw works properly now, too. :)

**Edit 2:** I got everything to work automatically! What I had to do was replace my current acpi_call.ko in /lib/modules/2.6.38-8-generic/kernel/drivers/acpi/acpi_call.ko with the new one that I had built per JailHouseRock's instructions. After that, I ran "depmod -a" in terminal and then added test_off.sh to my startup applications. Now when I boot the computer, the correct module is loaded by default, and when I log into my user account, the video card shut down script is run.

---

### Post by tahnok on 2011-05-14
Did you manage to get unity working on the intel card as well?

---

### Post by erik.osterholm on 2011-05-14
> **tahnok said:**
> Did you manage to get unity working on the intel card as well?

Just worked for me. Updated from 10.10 to 11.04.

---

### Post by chikara99 on 2011-05-28
not sure if anyone has installed 11.04 64bit but it gave me problems on m11x. i tried a regular and the alternative version and we ubuntu load i get noting on my screen and then the computer restarts. so i installed 10.04 64bit since i had no display output. Now I'm not getting a sound. I can't find drivers for audio.

Alienware m11x-R2: i7, 8G ram, nvidia gt335m

---

### Post by lingenfr on 2011-05-29
I installed natty 64-bit on my R1 and everything is work OK with the exception of bluetooth. I have to restart and do some other mojo to get it working. The problem is not limited to the M11x.

---

### Post by corte003 on 2011-06-04
Hi all,

I just installed Ubuntu on my M11x-R1, I was wondering if someone can updated me with everything I need to get started?  I'm like a new born baby to ubuntu.  Thanks!

My specs:

U7300 @ 1.30Ghz
4gb RAM
GeForce GT 335M

---

### Post by lingenfr on 2011-06-05
[This]("http://ubuntuforums.org/showpost.php?p=10005704&postcount=159") is still the most current. I doubt you will get more help than that, but maybe. I would suggest that you only use that instructions that you need and don't perform all of them just to do it as they are now a bit dated and could break something now or in the future. Simple adage 'if it ain't broke, don't fix it'. With the current version, my bluetooth is still having problems, but I think it is an error that is affecting many, not just M11x users.

---

### Post by Megan Ashlee on 2011-06-23
Hello All, I currently own the M11x r2 with Ubuntu 11.04 installed on it. Everything that i can tell is working (bluetooth, sound, graphics (i have to manually switch), AlienFX, wifi, et cetera. I just wanted to post this to help some of you out. When i installed Ubuntu it told me that i didn't meet the requirements for Unity (this is because of the hybrid graphics but of course all of you know that) so i went first to the nVidia website to check out if they had any new drivers out for it. They did, but it was also recommended that you stick with the ones included. I have Unity working, this is because i went into the driver manager and stopped the proprietary driver for the card (335m). Before, i would either be told by the system that id have to use 10.04 or have a blank screen completely. So my best advice to get 11.04 to work is just use the drivers that ubuntu comes with and ignore the proprietary drivers (for the graphics). The next order of business i had was to find something that would control the graphics switching: i turned to bumblebee and it worked. To get those programs to run using the nvidia card you just go to terminal type in optirun [insert name here].  Here's the instructions for the process of installing this: NVIDIA hybrid:
[CENTER] 'For nvidia hybrid configurations:
b) try bumblebee for simultaneously using the intel and nvidia cards:
sudo apt-get install git
# type password
git clone [http://github.com/MrMEEE/bumblebee.git](http://github.com/MrMEEE/bumblebee.git)
cd bumblebee/
sudo ./install.sh
optirun glxgears
# check the speed and compare to running:
glxgears
# If you have google-chrome installed, you can try it with/without optirun and report the FPS values on the mailing list:
optirun google-chrome [http://webglsamples.googlecode.com/hg/aquarium/aquarium.html ]("http://webglsamples.googlecode.com/hg/aquarium/aquarium.html")

[LEFT]I copied this verbatim from [https://launchpad.net/~hybrid-graphics-linux]("https://launchpad.net/%7Ehybrid-graphics-linux").
Next for AlienFX theres a small third party made program out there called AlienFX Lite.. i installed this on my computer and it controls the lights perfectly :p GUI isnt as pretty but who cares. 
Heres the link for those instructions which are found elsewhere in this forum: [http://ubuntuforums.org/showthread.php?t=1403399](http://ubuntuforums.org/showthread.php?t=1403399)

I hope this helps someone.. I'm new to using linux distros so if i have an error please pardon my ignorance. 

Anyways, I have had no problems with all of this (except for alienfx where i had to type in a different file name because the one in the instructions is wrong: it is now 0.4b instead of 0.1.

Regards,

Megan

-------
Specs: Alienware M11x R2,  Core i7-U640, 4Gb RAM, 500 GB HDD, nVidia Optimus 335m
[/LEFT]
'
[/CENTER]

---

### Post by Philip550c on 2011-07-05
> **Megan Ashlee said:**
> Hello All, I currently own the M11x r2 with Ubuntu 11.04 installed on it. Everything that i can tell is working (bluetooth, sound, graphics (i have to manually switch), AlienFX, wifi, et cetera. I just wanted to post this to help some of you out. When i installed Ubuntu it told me that i didn't meet the requirements for Unity (this is because of the hybrid graphics but of course all of you know that) so i went first to the nVidia website to check out if they had any new drivers out for it. They did, but it was also recommended that you stick with the ones included. I have Unity working, this is because i went into the driver manager and stopped the proprietary driver for the card (335m). Before, i would either be told by the system that id have to use 10.04 or have a blank screen completely. So my best advice to get 11.04 to work is just use the drivers that ubuntu comes with and ignore the proprietary drivers (for the graphics). The next order of business i had was to find something that would control the graphics switching: i turned to bumblebee and it worked. To get those programs to run using the nvidia card you just go to terminal type in optirun [insert name here].  Here's the instructions for the process of installing this: NVIDIA hybrid:
[CENTER] 'For nvidia hybrid configurations:
b) try bumblebee for simultaneously using the intel and nvidia cards:
sudo apt-get install git
# type password
git clone [http://github.com/MrMEEE/bumblebee.git](http://github.com/MrMEEE/bumblebee.git)
cd bumblebee/
sudo ./install.sh
optirun glxgears
# check the speed and compare to running:
glxgears
# If you have google-chrome installed, you can try it with/without optirun and report the FPS values on the mailing list:
optirun google-chrome [http://webglsamples.googlecode.com/hg/aquarium/aquarium.html ]("http://webglsamples.googlecode.com/hg/aquarium/aquarium.html")

[LEFT]I copied this verbatim from [https://launchpad.net/~hybrid-graphics-linux]("https://launchpad.net/%7Ehybrid-graphics-linux").
Next for AlienFX theres a small third party made program out there called AlienFX Lite.. i installed this on my computer and it controls the lights perfectly :p GUI isnt as pretty but who cares. 
Heres the link for those instructions which are found elsewhere in this forum: [http://ubuntuforums.org/showthread.php?t=1403399](http://ubuntuforums.org/showthread.php?t=1403399)

I hope this helps someone.. I'm new to using linux distros so if i have an error please pardon my ignorance. 

Anyways, I have had no problems with all of this (except for alienfx where i had to type in a different file name because the one in the instructions is wrong: it is now 0.4b instead of 0.1.

Regards,

Megan

-------
Specs: Alienware M11x R2,  Core i7-U640, 4Gb RAM, 500 GB HDD, nVidia Optimus 335m
[/LEFT]
'
[/CENTER]

Is hybrid graphics what the R1 has or is hybrid what R2 (optimus) has?

---

### Post by tahnok on 2011-07-06
I think bumblee is for optimus which is specifically for R2 (and R3 I think). Both are considered to have "hybrid graphics" though

---

### Post by reza_e13 on 2011-07-09
> **lucasbuck said:**
> I have an m11x r2 and ubuntu desktop 10.10 installed.

here are a few findings i have found that i thought might be helpful -> most has been intense googling and testing, i did not create most of these hacks (urls are included to sources)


touchpad -> 
this will get 2 finger scrolling working, among other things
source -> [http://forums.linuxmint.com/viewtopic.php?f=49&t=50621&p=314062](http://forums.linuxmint.com/viewtopic.php?f=49&t=50621&p=314062)

this is my script - hacked a little :
------
#!/bin/bash
#
xinput --set-prop --type=int --format=32 "SynPS/2 Synaptics TouchPad" "Synaptics Two-Finger Pressure" 4
xinput --set-prop --type=int --format=32 "SynPS/2 Synaptics TouchPad" "Synaptics Two-Finger Width" 8
xinput --set-prop --type=int --format=8  "SynPS/2 Synaptics TouchPad" "Synaptics Two-Finger Scrolling" 1 1
xinput --set-prop --type=int --format=8  "SynPS/2 Synaptics TouchPad" "Synaptics Edge Scrolling" 0 0 0
xinput --set-prop --type=int --format=32 "SynPS/2 Synaptics TouchPad" "Synaptics Jumpy Cursor Threshold" 250
xinput --set-prop --type=int --format=8  "SynPS/2 Synaptics TouchPad" "Synaptics Tap Action" 0 0 0 0 1 2 3
xinput --set-prop --type=int --format=8  "SynPS/2 Synaptics TouchPad" "Synaptics Palm Detection" 1
synclient TapButton3=2 ##two finger tap for middle-click
synclient TapButton2=3 ##should be 3 finger tap right click but doesn't work

xinput --set-button-map "SynPS/2 Synaptics TouchPad" 1 2 3 4 5 6 7 8 9
exit
-----

chmod it, and run. it will work right away. i have found after any laptop suspend or hibinate it needs to be re-run. I am working on scripting this in to gui startup, but attempts have failed so far, and i dont want to put it in a cron. 
 

Power Saving ->
nvidia gfx card disable (it doesn't work anyway, so lets save power!) -> 

apt-get install acpi
cat /proc/acpi/battery/BAT1/state (this will show your mW draw)
source -> [http://forums.fedoraforum.org/showpost.php?p=1402584&postcount=45](http://forums.fedoraforum.org/showpost.php?p=1402584&postcount=45)
(download the files and make)
insmod m11xr2hack.ko
lsmod | grep m11x (check that its loaded)
then check batt status again

i managed to get my battery draw (with wifi and full screen brightness down from 23000mW (2.2hrs batt) or so to 17500mW (3.2hrs batt), without wifi and lowered screen brightness to about 14000mW (5hrs batt)
i have found this needs to be added after reboot + suspend / hibinate etc -> working on scripts for this.


HDMI Audio ->
tested and working
source -> [http://wiki.foxmediasystems.com/index.php/Ubuntu_Intel_HDMI_Audio](http://wiki.foxmediasystems.com/index.php/Ubuntu_Intel_HDMI_Audio)

on m11x r2 i was using 
# speaker-test -Dplughw:0,3
to test static sound over the hdmi cabled, it also worked with speaker-test -Dplughw:0,7
i was able to just select the vlc output sound device to be hdmi and it has worked very well.


AlienFX lite ->
source -> [http://ubuntuforums.org/showthread.php?t=1403399](http://ubuntuforums.org/showthread.php?t=1403399)


Emapthy msn network connect ->
empathy was having issues connectin to MSN
locate RequestMultipleSecurityTokens.py (should be in SingleSignOn path)
vi /usr/lib/pymodules/python2.6/papyon/service/description/SingleSignOn/RequestMultipleSecurityTokens.py
edit CONTACTS row to : CONTACTS = ("contacts.msn.com", "MBI")
save, exit, reload empathy. msn now connects.


I have a few bits of hacking to do and will add any updates when i make advances

hi,
sorry because  I am a absolute beginner, where should I put these scripts for two-finger scroll, should I just run them once ? or they should be run in each ubuntu start-up ?
regards

---

### Post by tahnok on 2011-07-09
You can put the script anywhere you like and it should be run at startup each time.

---

### Post by andsoweflow on 2011-07-16
Hello friends, what might I do to fix this black screen (yes, I went ahead and activated the Nvidia proprietary driver *sad face*) if when I enter BIOS, there is no option for graphics to choose switchable or discreet.  I mean, graphics isn't even there :(

---

### Post by thegh0sts on 2011-07-24
hey there,

i am interested in installing ubuntu 11.04 via wubi and wondering about what i am to expect in terms of issues is concerned.

i have the R2 core i7 640um, 8gb RAM, 335m, etc.

---

### Post by tahnok on 2011-10-03
I created a setup guide for those interested in getting things working on an m11x R1

[http://blog.tahnok.me/post/10969464009/setting-up-ubuntu-11-04-on-an-m11x-r1](http://blog.tahnok.me/post/10969464009/setting-up-ubuntu-11-04-on-an-m11x-r1)

Let me know if I missed anything!

---

### Post by juanoleso on 2011-10-28
I might be a slowpoke here, but I was able to get bumblebee working with the M11x R1 on Ubuntu 10.04.
I installed bumblebee and its dependencies from the ppa:

ppa:bumblebee/stable

and restarted but I was getting errors as referenced at this link:

[COLOR="Blue"][URL="https://github.com/Bumblebee-Project/Bumblebee/issues/73"]https://github.com/Bumblebee-Project/Bumblebee/issues/73
[/URL][/COLOR]

I uninstalled nvidia-current and then added this repo:

ppa:ubuntu-x-swat/x-updates

and reinstalled nvidia-current, restarted, but bumblebee still didn't work.
I then uninstalled bumblebee from the ppa and installed Bumblebee from the git @

[COLOR="Blue"][https://github.com/Bumblebee-Project/Bumblebee](https://github.com/Bumblebee-Project/Bumblebee)[/COLOR]

I think I just restarted the bumblebee service and then it worked.  All said and done, I have bumblebee installed from the git source, I have the "virtualgl" package from the bumblebee ppa, and my nvidia driver (looks like 285.05.09) is from the ubuntu-x-swat ppa.  I don't have a way to test this from a fresh install, because my wife will be up and want to use the computer in about an hour and I've actually been working on this for a couple mornings.  I hope this helps someone.

Here are a couple more links I looked at as well:

[COLOR="Blue"][http://forum.notebookreview.com/alienware-m11x/464127-linux-m11x-12.html#post7894582]("http://forum.notebookreview.com/alienware-m11x/464127-linux-m11x-12.html#post7894582")

[https://wiki.archlinux.org/index.php/Alienware_M11x#Alienware_M11x_R1]("https://wiki.archlinux.org/index.php/Alienware_M11x#Alienware_M11x_R1")

[http://forums.nvidia.com/index.php?showtopic=39212]("http://forums.nvidia.com/index.php?showtopic=39212")[/COLOR]

---

### Post by tahnok on 2011-10-28
Bumblebee is for laptops with Optimus graphics switching and the R1 doesn't have the technology for graphics switching...

---

### Post by juanoleso on 2011-10-28
It works.  I have the R1, take a look at the screenshot.  The su7300 is only in the R1's.  I jumped into starcraft this morning with the same framerate I get while in windows.

---

### Post by Sub101 on 2011-11-04
Did anyone else lose sound on the 11.10 upgrade?

---

### Post by Evernoob7 on 2011-11-07
Hey all, I'm still fairly new to linux and I just got an M11x yesterday. I plan to use the original OS in virtualbox to control all those windows only features on the laptop, but I noticed that my 32-bit Linux 11.10 is only recognizing **2.4GB of 4 GB RAM.** I wouldn't mind if it only saw 3.9, but 2.4 is half of what I should have access to! 

Can anyone help me figure out how to access more of my RAM? I'd prefer to stick with 32-bit Ocelot for stability, and also because I've done a TONE of tweaking to this OS and would hate to go through all my changes again (I've got to start documenting the changes I make for reinstalls :/)


**SOLVED:** I found the solution, so for others, here it is... If you are using Linux 9.10 or above, open terminal and input:

$ sudo apt-get install linux-generic-pae linux-headers-generic-pae

Then reboot. Bam, your OS can see as much RAM as a 64 bit OS.

---

### Post by gene simmons on 2011-11-15
hi all,i dont mean to hijack this thread,i just got a screamin deal on a mx11x.i upgraded from a acer one netbook so this is pretty sweet for me haha.i ran all kinds of distros on my acer and to me they all ran as good if not beter than windows.the mx11 is diferent in many ways.i am trying out pinguy 64 11.10 and lininux 11.11 on usb.they both work fine but both run hot,after reading all the pages inthis thread i am still confused on how to switch the gpu to gain battery savings.also is installing juputer any good for this pc.on windows i can get near 7 hours of batter but on both distros i can barely get 3.is there a btter distro for this pc i should try,i prefer linux over windows anyday but u have to admit that windows works well with this pc for its options.again sorry to hijack,any help or tips would be great thanx.

---

### Post by rs3 on 2011-11-16
> **gene simmons said:**
> hi all,i dont mean to hijack this thread,i just got a screamin deal on a mx11x.i upgraded from a acer one netbook so this is pretty sweet for me haha.i ran all kinds of distros on my acer and to me they all ran as good if not beter than windows.the mx11 is diferent in many ways.i am trying out pinguy 64 11.10 and lininux 11.11 on usb.they both work fine but both run hot,after reading all the pages inthis thread i am still confused on how to switch the gpu to gain battery savings.also is installing juputer any good for this pc.on windows i can get near 7 hours of batter but on both distros i can barely get 3.is there a btter distro for this pc i should try,i prefer linux over windows anyday but u have to admit that windows works well with this pc for its options.again sorry to hijack,any help or tips would be great thanx.

I don't think you're going to find a better distro for the m11x.  The battery life issues will persist across all distros and the hardware support for the m11x in 11.04 and 11.10 is about as good as you are going to find.  Sad but true; if you need battery life, you might as well roll with Windows.  If you can deal with the power consumption issues in Ubuntu, it is otherwise going to run quite well.

I can't speak to Jupiter, don't know what it is.  Cheers!

---

### Post by juanoleso on 2011-11-16
if you haven't tried acpi_call to turn off the GPU, you should look into it.  I was able to turn off the GPU in my m11xr1 and it runs cool enough after that that the fan doesn't need to come on.  I'm not sure about battery life, though, as I keep mine plugged in almost all the time.

[http://linux-hybrid-graphics.blogspot.com/]("http://linux-hybrid-graphics.blogspot.com/") for info on The Bumblebee Project and acpi_call.

---

### Post by gene simmons on 2011-11-16
thanx so much for the replys guys,i will look into the acpi call feature.that sounds just what im looking for.i dont play games on the laptop so i dont really need the graphics that much,i am more into batery life.i havent installed a linux distro on the mx11 yet,still running off a usb to try out a few diferent ones.once i install it i will try the acpi call.are u guys that are running linux on the mx11 pretty happy with the setup,do u use windows much at all.thanx for any tips

---

### Post by gene simmons on 2011-11-17
hi guys.again sorfy for hijacking this thread.i am having a prob with the distro i chose for the mx11.i am trying pinguy 64 11.10.all seemed good till it froze up.rebooted and soon froze again.when it freezes u cant do anything.mouse and keys dont respond.i had this issue on my girlftreinds 64 bit intel pc with a few dif ubuntu based distros.what distro are u guys running on ur mx11.have u had any issues and whatcha gettung for battery life with acpi call being used.thanx for any info or tips

---

### Post by romer3r on 2011-12-04
Hi there,

 I am planning to buy a M11x, with I3 2357M 6GMRam & NVIDIA® GeForce® GT540M

 I will install ubutn10.10, Some one test COMPIZ on M11x,  

 I tried compiz with a Intel® HD Graphics 3000 and never work with that.

comment will be apreciated.
Regards

---

### Post by Biciclettapc on 2011-12-04
> **romer3r said:**
> Hi there,

 I am planning to buy a M11x, with I3 2357M 6GMRam & NVIDIA® GeForce® GT540M

 I will install ubutn10.10, Some one test COMPIZ on M11x,  

 I tried compiz with a Intel® HD Graphics 3000 and never work with that.

comment will be apreciated.
Regards

The Nvidia GT540M I am pretty sure has Optimus, which is a real issue (search all the threads on this forum) and will not allow the use of the Nvidia card.

I am sending you a PM in regards to the M11x

Paul

---

### Post by nutsy.ben on 2011-12-30
It is possible to use the Nvidia card through Bumblebee/ or Ironhide (its new name). 

However, I never managed to make this laptop work with an external screen. Any success from a user here ?

---

### Post by tahnok on 2011-12-31
Depends what model you have. I have an R1 and video out on the VGA port works flawlessly. I guess the R2 and R3 don't have a VGA port though.

---

### Post by gene simmons on 2012-03-20
oksorry to dig this thread out of the archives,i am running ubuntu 10,10 macbuntu 64bit and got acpi call to work,battery life is decent now,i followed the intructions and most things seem to work,i cant seem to get hdmi to work though,i know in windows i have to be on nvidia to use hdmi,so in linux do i need to turn the vid card back on?i think i tried that but it still didnt work,the vga port works fine but i would like sound thru my tv,can any one give any sugestions
thanx

---

### Post by sarbull on 2012-04-15
I want a step by step tutorial, for installing Ubuntu 12.04 OR which version do you encourage me to use .. on my Alienware M11x-R1, SU7300 1.3Ghz, 4GB, 500GB, nVidia 335M

---

### Post by FreeRide23 on 2012-04-24
Hello @ all,

i have read this Tread until side 11... now i have quittet reading and just "let it be" like it is.

My Ubuntu is running, but unforgenly i have crashed my Sound.

After i was installing a new driver from the realtek side, there is no more sound.

can some one give me please a working LINK to some driver download side. I dont find a driver download for the AW M11x R2

can some one help me?

A PM or a Email pls! claus.w @ gmx. net

---

### Post by Slowpokemon on 2012-05-04
> **tahnok said:**
> I created a setup guide for those interested in getting things working on an m11x R1

[http://blog.tahnok.me/post/10969464009/setting-up-ubuntu-11-04-on-an-m11x-r1](http://blog.tahnok.me/post/10969464009/setting-up-ubuntu-11-04-on-an-m11x-r1)

Let me know if I missed anything!

I've been using this guide after every reinstall of Ubuntu, but since updating to 12.04 it no longer works for me. I'm not sure if something changed in the git repository or within the kernel, but now everything goes smoothly up until I run the test_off.sh script. At that point it says:

```
Trying \_SB.PCI0.P0P1.VGA._OFF: ./test_off.sh: line 34: /proc/acpi/call: Permission denied
cat: /proc/acpi/call: Permission denied
works!

```It doesn't actually turn off the card, but it says it has worked.
The solution is to run the script as root. The problem with this is that it is necessary to manually execute it upon every login because placing it in startup applications does not grant the script superuser privileges.

After Googling and trying a few different methods of automating it, I still cannot find one that works. Do you have any ideas?

---

### Post by gene simmons on 2012-06-06
i could never get the script to work on startup,i have always ran it in root terminal,i also started with ubuntu 10.10 and now upgraded to 12.04,battery life isnt as good as 10.10,i have read theres new nvidia drivers,for linux i hope they allow users to use hybrid graphics,how do you like your mx11

---

### Post by juanoleso on 2012-06-07
Last word I saw is that nVidia will never support optimus or hybrid switching for linux.  You can just use "The Bumblebee Project" though.  It even works on my r1 for ubuntu 12.04.

[https://launchpad.net/~bumblebee/+archive/stable]("https://launchpad.net/~bumblebee/+archive/stable")

---

### Post by sarbull on 2012-07-15
I am writing this from an Alienware M11x running Ubuntu 12.04

the only problem i had was with the brightness shorcut buttons, and i fixed it below

Repaired FN Brightness
1. sudo vi /etc/default/grub
2. GRUB_CMDLINE_LINUX_DEFAULT=”quiet splash acpi_backlight=vendor“
3. sudo update-grub

Install Bumblebee for nvidia graphics

And other Ubuntu updates ..

It works very well !

---

