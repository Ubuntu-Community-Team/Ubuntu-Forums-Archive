---
title: "Help!"
date: 2008-09-15
forum: General Help
---

### Post by GrumpyGrenade on 2008-09-15
I'm a complete noob. I've installed and reinstalled Ubuntu about 4 times now. I've created about 3 live CDs. I followed all the instructions and yet I still get errors. When I make changes that require a restart, like enabling restricted drivers, and I restart that is when the problems start. It gets as far as the loading screen with the orange bar. After that is finished the screen just turns black. And if I run the Ubuntu in recovery mode it just throws up a fancy smorgasborg then leaves it to me to sort it out, and if I press ctrl+alt+del it goes to a wierd login screen that looks like grub. The last time these things happened a did a memtest (whatever that is) and that cleared things up. Unfortunately it takes about 28 hours. I do not want to spend all my time doing memtests. Please help!  ](*,)

edit: even when I try to boot from the live cd it still does not work.

---

### Post by Crayboff on 2008-09-15
Are you trying to partition your harddrive or move completely to Ubuntu. Also what OS are you using currently? Have you tested your Live CD for defects using the function on the CD itself? Also, what version of Ubuntu are you attempting to install?

---

### Post by GrumpyGrenade on 2008-09-15
I am trying to move completely to Ubuntu. I used to use XP but it was wiped when I was fooling around while partitioning. Now that I have discovered Ubuntu I'm going to stick with it for now. Yes, I have tested it for defects. It says it is fine. And I was trying to install ubuntu hardy heron.

---

### Post by overdrank on 2008-09-15
> **GrumpyGrenade said:**
> I'm a complete noob. I've installed and reinstalled Ubuntu about 4 times now. I've created about 3 live CDs. I followed all the instructions and yet I still get errors. When I make changes that require a restart, like enabling restricted drivers, and I restart that is when the problems start. It gets as far as the loading screen with the orange bar. After that is finished the screen just turns black. And if I run the Ubuntu in recovery mode it just throws up a fancy smorgasborg then leaves it to me to sort it out, and if I press ctrl+alt+del it goes to a wierd login screen that looks like grub. The last time these things happened a did a memtest (whatever that is) and that cleared things up. Unfortunately it takes about 28 hours. I do not want to spend all my time doing memtests. Please help!  ](*,)

edit: even when I try to boot from the live cd it still does not work.

Hi and welcome, could you give us some system specs? You may try and boot into recovery mode which is usually the second choice from the grub. Then use the xfix option and hopefully this will correct the graphics.

---

### Post by paydaydaddy on 2008-09-15
If you are getting errors when you run memtest then you probably have a bad stick of ram. If you are running more than one stick of ram try testing them individually.

---

### Post by GrumpyGrenade on 2008-09-17
Sorry for taking so long to post. Anyway my computer is a Compaq Presario SR1000 with a Radeon X1600 graphics card. It has an AMD Athlon XP 3000   ( 2.16 GHz) proccesor. It has 512 mb of RAM and a 160 gb hard drive.

---

### Post by EmanresuusernamE on 2008-09-17
> **GrumpyGrenade said:**
> edit: even when I try to boot from the live cd it still does not work.
Sounds like you need a different version of Ubuntu then.  Have you tried a different flavor of Ubuntu such as Kubuntu, Xubuntu or perhaps a downgraded version of Ubuntu?

---

### Post by GrumpyGrenade on 2008-09-17
> **EmanresuusernamE said:**
> Sounds like you need a different version of Ubuntu then.  Have you tried a different flavor of Ubuntu such as Kubuntu, Xubuntu or perhaps a downgraded version of Ubuntu?

No I have not. Why couldn't I use Hardy Heron?

---

### Post by EmanresuusernamE on 2008-09-17
Hardware compatibility issues.  Give one of the other flavors a try, see if they allow you to use Ubuntu.

---

### Post by GrumpyGrenade on 2008-09-17
> **EmanresuusernamE said:**
> Hardware compatibility issues.  Give one of the other flavors a try, see if they allow you to use Ubuntu.

Unfortunately I can't do that right now. Memtest is **still[B]**[/B] running. So far it has been running for 47 some hours. Last time it only took about 28....

---

### Post by EmanresuusernamE on 2008-09-18
Hit Escape and cancel it.  You don't have to go through the entire memtest if you don't want to.  Once you've run a memtest, it's kinda pointless to run it over and over again.  That'll only decrease the lifespan of your RAM.

The memtest is a VERY thorough tester, and personally, I don't test more than 5% of my RAM when I do my tests.

---

### Post by GrumpyGrenade on 2008-09-18
Is there any way I could fix this issue without uninstalling ubuntu **again?** Anyone?

---

### Post by GrumpyGrenade on 2008-09-18
is it possible that I downloaded the ISO from a bad mirror?

---

### Post by jp73107 on 2008-09-18
Any number of things could have gone wrong. The CD Drive you're installing with could have a problem, (I've had this occur before. While installing windows vista on one drive, it would error out and cancel install, but after switching to a new drive, it went just fine.. same disk). The burning software you used might have had a problem and not reported it. The ISO itself might have been bad. Try these steps below to see if it helps any.

1. Choose a different download mirror. I use the OSU Open Source Lab mirror myself (ftp.osusl.org)
2. Download the MD5SUMS file from the mirror you are downloading from ([http://ubuntu.osuosl.org/releases/hardy/MD5SUMS](http://ubuntu.osuosl.org/releases/hardy/MD5SUMS)) and do this:
On linux, open a terminal and type md5sum -c nameof.iso and compare it to the MD5SUMS file.
On Windows, download WinMD5 ([http://www.blisstonia.com/software/WinMD5/](http://www.blisstonia.com/software/WinMD5/)) and compare the result to the MD5SUMS file.

If the MD5SUM and results from your md5 match, the iso is good.
3. Try installing Ubuntu with a different CD drive. You can purchase a new one pretty cheaply these days, from 20$ and up.

Edit: Also download isorecorder from [www.alexfeinman.com](www.alexfeinman.com) to burn iso files on windows. Its free and i've never had a problem burning images to cds with it. It doesn't let you edit the ISO or use it as a compilation program (i.e. nero burning rom) All it does is burn images to the disk.

Hope you get your issue fixed soon :)


New Edit: I'm not sure about being able to repair it without reinstalling ubuntu again. If you continue to have problems with the livecd, try the alternate installation cd. Its a text mode installer. the Ubuntu livecd requires 384 MB of ram minimum to use, i believe.

---

### Post by GrumpyGrenade on 2008-09-20
> **EmanresuusernamE said:**
> Hit Escape and cancel it.  You don't have to go through the entire memtest if you don't want to.  Once you've run a memtest, it's kinda pointless to run it over and over again.  That'll only decrease the lifespan of your RAM.

The memtest is a VERY thorough tester, and personally, I don't test more than 5% of my RAM when I do my tests.

so if i x out it wont "untest" it?

---

### Post by Sef on 2008-09-20
> so if i x out it wont "untest" it?

Read [memtest86]("http://memtest86.com")'s website to know how to find the results.

---

### Post by EmanresuusernamE on 2008-09-22
> **GrumpyGrenade said:**
> so if i x out it wont "untest" it?
The test is just to see if your RAM has any defects.  All it does is test it thoroughly over and over again with different sets of data.  AFAIK there is no way to untest anything like that.

In a nutshell, it just looks to see if your RAM has problems and tells you about them, and where the problems are.  I've never seen (more like never looked) for an option to see if it would save any of the results it gets.

---

### Post by GrumpyGrenade on 2008-09-22
OK gotcha. So... any idea on why it gets all messed up every time it asks me to restart? And maybe how to fix it?](*,)

edit: I X'ed out like EmanresuusernamE said but to no avail (nothing was fixed)6 days of worthless memtesting. sigh*

---

### Post by EmanresuusernamE on 2008-09-23
Memtest is not a repair utility, it's a **Mem**ory **Test**.  When you boot up your linux, choose the Failsafe boot option, (second boot option on a default installation).  When it boots up, choose the Repair X Server option, then Boot normally.

---

### Post by GrumpyGrenade on 2008-09-23
> **EmanresuusernamE said:**
> Memtest is not a repair utility, it's a **Mem**ory **Test**.  When you boot up your linux, choose the Failsafe boot option, (second boot option on a default installation).  When it boots up, choose the Repair X Server option, then Boot normally.

there is no fail-safe option. i know there is one on the login screen but as I have already said, I can't even get to the login screen. And about the Repair X Server option. I've already tries that many many times.

---

### Post by GrumpyGrenade on 2008-09-23
> **jp73107 said:**
> Any number of things could have gone wrong. The CD Drive you're installing with could have a problem, (I've had this occur before. While installing windows vista on one drive, it would error out and cancel install, but after switching to a new drive, it went just fine.. same disk). The burning software you used might have had a problem and not reported it. The ISO itself might have been bad. Try these steps below to see if it helps any.

1. Choose a different download mirror. I use the OSU Open Source Lab mirror myself (ftp.osusl.org)
2. Download the MD5SUMS file from the mirror you are downloading from ([http://ubuntu.osuosl.org/releases/hardy/MD5SUMS](http://ubuntu.osuosl.org/releases/hardy/MD5SUMS)) and do this:
On linux, open a terminal and type md5sum -c nameof.iso and compare it to the MD5SUMS file.
On Windows, download WinMD5 ([http://www.blisstonia.com/software/WinMD5/](http://www.blisstonia.com/software/WinMD5/)) and compare the result to the MD5SUMS file.

If the MD5SUM and results from your md5 match, the iso is good.
3. Try installing Ubuntu with a different CD drive. You can purchase a new one pretty cheaply these days, from 20$ and up.

Edit: Also download isorecorder from [www.alexfeinman.com](www.alexfeinman.com) to burn iso files on windows. Its free and i've never had a problem burning images to cds with it. It doesn't let you edit the ISO or use it as a compilation program (i.e. nero burning rom) All it does is burn images to the disk.

Hope you get your issue fixed soon :)


New Edit: I'm not sure about being able to repair it without reinstalling ubuntu again. If you continue to have problems with the livecd, try the alternate installation cd. Its a text mode installer. the Ubuntu livecd requires 384 MB of ram minimum to use, i believe.

so far i have been having problems with ISOrecorder so I am using InfraRecorder. For some reason when I select the burn speed to 1x during the burn session it says: Writing Track one of one at 18xspeed or 40xspeed. Any idea whats going on?

---

### Post by EmanresuusernamE on 2008-09-24
Try using Free Easy CD DVD Burner from Koyote Soft.  It burn the live CDs ver well, and I've never had a problem with it.  It's free too. :)

[http://www.koyotesoft.com/indexEn.html](http://www.koyotesoft.com/indexEn.html)

---

### Post by GrumpyGrenade on 2008-09-24
ok. how do i format the drive to get rid of all the other ubuntus? i have about 3 ubuntus on my computer now....:(

---

### Post by EmanresuusernamE on 2008-09-26
> **GrumpyGrenade said:**
> ok. how do i format the drive to get rid of all the other ubuntus? i have about 3 ubuntus on my computer now....:(
Well, if you tell it to use the entire disk, that will get rid of all other installations, BUT this will ALSO remove any windows installation as well.

Quickest way to remove an Ubuntu installation, just delete the partitions, and then tell the installer that you want to use all of the unpartitioned space.

---

### Post by GrumpyGrenade on 2008-09-27
hmmmm....I made a new disk and so far it has worked fine, although I think that problems will arise again soon. When I installed ubuntu I told it to use the whole disk but when I restarted there were still all the other installations.:(

---

### Post by EmanresuusernamE on 2008-09-27
Hmmm, since you want to use the whole disk, load up Gparted and then manually remove all of the partitions that you don't want, then expand your main partition, or create a whole new partition.

If I where booting windows, I'd say just create a new data partition.  When my OS would die, I'd just reinstall it on the main partition and all of my other data would still be fine.

---

### Post by GrumpyGrenade on 2008-09-28
Gparted??? When I start up the Add/Remove thing the closest thing to that is GPar2....\\:D/

---

### Post by EmanresuusernamE on 2008-09-29
Look under System > Administration.  There should be an item called Partition  Editor.  If you can't find it, open up a terminal, and type in gparted.

---

### Post by GrumpyGrenade on 2008-09-29
When I select the partition I want to get rid of the option to delete isn't there.....:(

---

### Post by EmanresuusernamE on 2008-09-29
Could you post a screen shot of your Partition Editor?  So that we can see what all is going on.

---

### Post by GrumpyGrenade on 2008-10-01
Here.

---

### Post by GrumpyGrenade on 2008-10-01
Whoops. Srry for bumping but just so you know the one I highlighted is the one I'd like to delete.

---

### Post by GrumpyGrenade on 2008-10-05
Hello? :confused:

---

### Post by EmanresuusernamE on 2008-10-06
Sorry for the delay, sometimes life will actually come up and bite me in the rear, and I'll have to mess with the vista os and feel like ripping my own/customer's hair out.

It looks like that partition you don't want, can't be removed because the Linux Swap partition is in it.  For systems with low amounts of RAM, you need a swap partition, for systems with more RAM, it's more of a tossup if you want to use it or not.  Personally, I see it as only using a gig of space, so it'd be no big deal to me and I'd just leave it.

However if you want to remove it, you'd have to edit your fstab file to stop it from being used, restart your system, then remove it with gparted and finally resize your main partition and restart again to make the changes take effect.  A bit more work that what it's worth to me.

---

### Post by GrumpyGrenade on 2008-10-06
oh...thanks for all your help. But getting back to my real issue: why is ubuntu getting messed up every time I enable the drivers for my graphics card?

---

### Post by EmanresuusernamE on 2008-10-07
If you're using the free drivers that came with Ubuntu, that can happen since there's little documentation about the propriatary hardware in use by your video card.  If you use the drivers that come from your manufacturer, then you may have better luck using it, and better graphics acceleration.

---

### Post by GrumpyGrenade on 2008-10-09
Yes, but I've already looked for the latest drivers but when I downloaded it all it said was: There is no application installed for this filetype,

---

### Post by EmanresuusernamE on 2008-10-09
If you have an ATI or nvidia graphics card, load up Add/Remove or Synaptic, and install Envy.  Then have it install the graphics drivers for your system.

The description should talk about installing ATI and nvidia drivers for you.

---

### Post by GrumpyGrenade on 2008-10-09
I did what you said and everything is fine. My computer survived the restart so that is a good sign...just in case, is there anyway to back up all my setting and files?

---

### Post by EmanresuusernamE on 2008-10-12
The file xorg.conf in like: /etc/X11 (I think.......... I really should learn to no hit these forums while I'm forced to use a windows box) would be a start.  That's your video configuration file.  And for the most part, your setting should all be in your home folder along with pretty much everything else you've downloaded most likely.

---

### Post by GrumpyGrenade on 2008-10-14
ok....now i got everything backed up. i then enabled the drivers and when i restarted the whole thing blew up in my face. It said it was going to run Ubuntu in low-graphics mode or something like that. I installed ubuntu **again** and so far everythings been peachy keen (ha!). I have everything I backed up in the little harddrive on my desktop (in my computer). Question is: how do I take all of it's contents and apply everything to ubuntu like it never went kaplut?

---

### Post by GrumpyGrenade on 2008-10-15
i know the cd was good because I requested it...but yet when I enabled the hardware drivers and restarted things got messy again. The booting up was fine. The logging in was fine. But after i logged in the whole screen went white. Same thing in recovery mode. The only reason I'm not staring a white screen right no is that I used the fail-safe GNOME option. Any tips?

---

### Post by EmanresuusernamE on 2008-10-18
Hmmm, it would seem that Ubuntu is not compatible with your hardware for some reason.  What type of graphics card do you have? Is it embedded into your motherboard?  If it is, have you gone into your motherboards settings and change the BIOS to give it more VRAM, or more AGP Aperture space?

---

### Post by GrumpyGrenade on 2008-10-19
It is a Radeon X1600 graphics card. It is not embedded in my motherboard.

---

### Post by EmanresuusernamE on 2008-10-20
What are you using to enable your graphics drivers?  Are you going under, System > Admin and then enabling the drivers that way, or are you using the drivers from the manufacturer?  Also, have you tried using Envy to install the graphics drivers?

---

### Post by GrumpyGrenade on 2008-10-21
So far I've been trying to enable the drives through the System/Admin wasy, but in the last installation I tried out Envy...wich didn't work either. I'll try it again for this one...

---

### Post by GrumpyGrenade on 2008-10-21
No it did not work. The Envy installation seemed to have worked perfectly but when I restarted I still got the same result: When doing a regular boot I get a black screen (and didn't even get to the login) and when doing recovery mode and choosing last session I got a white screen with a mouse.

---

### Post by EmanresuusernamE on 2008-10-21
Hmmm, while looking this up, I found an interesting website:
[https://help.ubuntu.com/community/BinaryDriverHowto/ATI]("https://help.ubuntu.com/community/BinaryDriverHowto/ATI")
Thanks to:
[http://ubuntuforums.org/showthread.php?t=310189&page=2]("http://ubuntuforums.org/showthread.php?t=310189&page=2")

If that top one doesn't help, you might want to try using a different version of Ubuntu.  (I knew there was a page like that out there, I just could not find it to save my life).

---

### Post by GrumpyGrenade on 2008-10-25
Well...I tried it once and when I restarted and went to the Hardware Drivers section it had a green light saying :"In Use" but the enable box was unchecked. So I checked it, restarted and all I got was lines and and offer to use Ubuntu in lowgraphics mode... When I next restarted I got the red light again....   Yes I'm thinking of getting a nother version...but question is what version should I get? Should wait for Intrepid or should I get an older version? I'm thinking I should wait for Ibex and then request it for free...  ](*,)

---

### Post by GrumpyGrenade on 2008-10-31
Ok, so I've upgraded to Intrepid and so far things are great. I enabled the hardware drivers and restarted and nothing went wrong. But after the drivers were upgraded some things weren't functional anymore. Some screen savers became blank etc. Any explantion for this?

---

