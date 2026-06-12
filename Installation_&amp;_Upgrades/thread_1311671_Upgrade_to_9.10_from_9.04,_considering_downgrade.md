---
title: "Upgrade to 9.10 from 9.04, considering downgrade?"
date: 2009-11-02
forum: Installation &amp; Upgrades
---

### Post by shadowimmage on 2009-11-02
I, like a lot of others here, have hit a few snags with Karmic. I was hoping that the upgrade would go well, but it didn't, and so far I haven't been able to find any solutions, not to mention the fact that a lot of things seem to be less stable.

This is an installation on a Thinkpad T61, Intel integrated graphics.

First thing I noticed:
-Suspend is broken. I used to be able to put my laptop to sleep and wake it up without any issues ever, and furthermore, I could go for weeks without actually shutting it down, and it ran beautifully.
Now, when I tell it to suspend (again I'm not talking about Hibernate), it will go to a black screen and the blinking half moon LED won't stop, and the power never goes off. It just sits there with the backlight on a black screen, and a blinking LED. NOTE: This isn't a resume issue, because I never get that far. I have to hold the power button and restart the system

Second:
-Desktop effects can't be enabled, this happened after the last big upgrade too... I don't understand why I can have "Extra" effects and use the compiz settings manager to tweak everything to how I like it, and then after the upgrade, it's set to "none" and clocking on even "normal" fails. The last time I got it to work was by just sitting there and trying to enable it till it decided that it would work. I don't want to go through all that again, and mostly I just want it to WORK. 

Third:
-this is mostly general, but when running the system, I notice that the crash reporter is constantly reporting various different things crashing. It's reported when managing my installed programs with the new ubuntu software center, and other things that I don't even know how to describe. It seems like background processes are crashing or something like that... but most of the time it doesn't seem to have anything to do with the active application(s). or maybe it does but it's not causing them to crash, just other things?

Fourth:
-Now I have to enter my admin password EVERY time I want to mount ANYTHING, even a USB flash drive, or my secondary bay drive. Also I have the little toolbar applet thing that allows me to monitor my CPU clock speeds (Intel Core2duo) and limit them to "Powersave, performance, ondemand, etc" and every time I want to change those, for each processor core, I have to enter a password! 
This is a MAJOR annoyance to me, as these things weren't password protected before and I don't like having to type in my administrative password on my laptop every five minutes or (more often) LESS.

----

So, I downloaded an ISO of the liveCD and tried that out, the things that are fixed:
-Suspend works fine with the live CD
-Desktop effects are already enabled, and switching from extra to normal and back doesn't hurt anything. But, I can't configure the effects settings anymore because I don't know where to get my Compiz settings manager back that I have installed in Jaunty.

The things that are still broken:
-More crashes of process or programs (none of which are things I'm actively looking at, IE, Firefox doesn't crash and close randomly, but the bug reporter keeps showing up), and that's just while running firefox to do things like read forum posts to see if there's anyone else suffering from these problems.

-the password thing I couldn't really check on the live CD, as there's no different Root password to use on the live CD, and I didn't try mounting anything.

Also, the Live CD doesn't have an option for the middle click scrolling of the trackpoint, which I had to modify some system file to enable before and I don't remember how to fix this... But it's annoying that I can't scroll or middle click with the trackpoint buttons, as I use that 100 times more than the touchpad.

----

What I'm wondering here is, 
Should I clean install 9.10, even if I'm getting crash reports all over the place? What guarantee of stability do I have??
OR
Should I re-Install to 9.04 from my other live CD, as I don't have enough hard drive space these days for a complete disc image elsewhere, and I know that the package manager doesn't support rolling the operating system back (WHICH, is really stupid, as you never know what's going to break when you upgrade, and it'd be nice to have an UNDO button... that isn't a disc image)

Any help that you can render involving any of my problems would be great... Especially the suspend issue as it's a laptop, and a thinkpad at that, and I like it to be able to go everywhere with me, and I like not having to start it up all the time, and then shut it down all the way again. And hibernate is way too slow anyway for these purposes.


THANKS A LOT!
I really love Ubuntu... when it's working... and I don't want to be forced back to Windows...

---

### Post by theozzlives on 2009-11-02
Karmic was released way before it was ready. I'm praying for "fix-it's" to come down the upgrade tube. Beta was a mess, and RC not much better. I guess I should feel lucky that all I'm pulling my hair out over are the Samba issues. Hang in there, I'm sure they'll fix it.

---

### Post by mcooke1 on 2009-11-02
I have been reading the forum and having trouble understanding why people are having problems maybe I am lucky but anyway I had 9.04 installed for 8 weeks and only had minor problems with wireless so I decided to do a clean install of 9.10 it went smoothly almost identical to the install of 9.04 in fact, I again had wireless problems used the forum found a solution and am now enjoying the 9.10 improvements. I belive its faster and the more I use it the more I think they got it right. Try a clean install.

---

### Post by code4pay on 2009-11-03
Make sure that it is actually using the correct kernel,  At the boot menu the choice should mention 9.10 and not 9.04.  I had all sorts of issues with video etc until I fixed this issue.  You need to edit the grub config file to set the latest kernel version.

---

### Post by jgkellt001 on 2009-11-03
How did you edit grub config?

---

### Post by presence1960 on 2009-11-03
I hate to sound like a broken record, and I know it is too late since those having problems with an upgrade to 9.10 can't do anything about whether choosing to do an upgrade or a clean install.

But history has a way of repeating itself. Every time there is a new release there seems to be a lot of posts about upgrades gone awry. This is why I never do an upgrade and do a clean install.

You can save all your settings and packages installed from the repositories can be reinstalled through terminal easily.

First back up your home folder. Then do use this first to back up your installed packages & then after clean install to reinstall your packages:

To replicate your packages selection on another machine (or restore it if re-installing), you can run this:

```
dpkg --get-selections > ~/my-packages
```


This will save a file called my-packages in your home directory. Make a backup of it, install the fresh release, then restore the file "my-packages" to new home partition and run this code in the terminal:

```
sudo dpkg --set-selections < my-packages && sudo apt-get dselect-upgrade
```


It will download and install all the programs for you, except those that you installed manually, if they are not in the new repository. I did this with Jaunty and a lot of packages I installed manually on Hardy were available in the Jaunty repos. So I didn't search for many applications after the fresh install. Did the same with Karmic.

Then restore your backup of /home so all your programs settings will be as they were previously.

---

### Post by jgkellt001 on 2009-11-03
Call me old fashioned, but I still don't see why I or anyone else has to become an expert at saving *this* and *that*, *tweak* the other and *tweek* the same, *stand* on your head and *drink* a pint of beer from the far side of a glass, **just so you can upgrade your Ubuntu 9.04 to 9.10** without any problems.

I just want to use my computer,,,,,not program the damn thing!

---

### Post by shadowimmage on 2009-11-03
Thanks everyone for your replies, I agree that having to learn all this stuff can be a kind of pain in the ****, but at least it can be done. I've been reading what's been happening to the windows 7 people, and I think i'd rather have these probs. At least there's people who can point you in the right direction, etc. 

I checked the kernel numbers, and the grub config on the old install (still haven't clean installed b/c I have no time these days) is set to automatically default to the most recent kernel installed. 

I'll probabaly do a clean install here in the next couple days... but between now and then, I was wondering if anyone could explain how the system sets up drivers for hardware when first installing/booting. To be more clear, I am wondering why in my broken upgraded install, clicking on the advanced desktop effects, it tells me that it couldn't find the right driver, but in the liveCD it just already has it on and running after loading up. 
This has been a murky area of the Ubuntu/linux world for me from the very start - I've never been able to figure out hardware drivers, and only have refered to other posts/guides for modifying anything (like enabling middle-click behavior) without actually understanding anything that I'm doing.

Anyway, I'll post later about the reults of a clean Karmic install, since I already did the /home backup and the dumping of my package selections to the same external HDD.

But I'll also be checking back here if anyone wants to post something pointing me in the "how to figure out (and modify?) your hardware drivers in ubuntu" direction...

Also if anyowants to post a magic "wait you don't have to do that, I have a solution" post... that'd be pretty awesome too.

BONUS question, if I want to have a /home partition, how should I divide up my drive, also, I want to have a sufficient swap partiton, so that'd be helpful too (I have 2gb RAM, current swap is about 4.5gb (is this too much??))

---

### Post by jeggerleg on 2009-11-03
> **jgkellt001 said:**
> Call me old fashioned, but I still don't see why I or anyone else has to become an expert at saving *this* and *that*, *tweak* the other and *tweek* the same, *stand* on your head and *drink* a pint of beer from the far side of a glass, **just so you can upgrade your Ubuntu 9.04 to 9.10** without any problems.

I just want to use my computer,,,,,not program the damn thing!

I agree.  Sadly, because I had time on my hands last Saturday and the upgrade was offered by Update Manager I took the plunge. I'm now on another computer using 9.04 because my wireless connection doesn't always work. Sometimes no problem then it decides to disconnect.  Switch to Vista and I find all is well.

---

### Post by Youresorock on 2009-11-03
My upgrade went poorly like many other people here.  I'll be backing up my home directory and installing 9.04 clean tomorrow.  I'll probably wait for the next LTS release to do another upgrade.  Thank god I didn't upgrade my work computer, or I'd be coming in on Saturday to fix it.  I really don't like the 6 mo cycle.  I think it rushes the developers to release before a product is ready.

Compiz is broken, sound is crunchy, firefox crashes constantly, flash doesn't work, video corruption... It's a mess.

---

### Post by sav2005 on 2009-11-03
I upgraded an installation running inside the Windows partition since 8.10 on a Lenovo, R61 Laptop.

8.10 to 9.04 went well and WEP Enterprise wireless got fixed.

9.04 to 9.10 (Kosmic Kangaroo?) looked good until:

[LIST]
 I tried to use Evolution with Ubuntuone/CouchDB. Broken on laptop, OK on desktop. Message - cannot access Address Book, permission denied. (I have set up Ubuntuone, and can use the folder/remote system from the laptop and other computers)[/LIST]

[LIST]Shutdown and reboot needs manual intervention (Alt+PrtScrn REISUO)[/LIST]

[LIST]Create Bootable USB hangs at "Creating a persistence file - 100%" and makes an unbootable USB. Using the formatting tool in the same program makes an unworkable USB.
[/LIST]
I'm not considering a downgrade, but these are pretty bad,  especially the shutdown/reboot issue.

---

### Post by presence1960 on 2009-11-03
> **jgkellt001 said:**
> Call me old fashioned, but I still don't see why I or anyone else has to become an expert at saving *this* and *that*, *tweak* the other and *tweek* the same, *stand* on your head and *drink* a pint of beer from the far side of a glass, **just so you can upgrade your Ubuntu 9.04 to 9.10** without any problems.

I just want to use my computer,,,,,not program the damn thing!

You will only get out of it what you are willing to put into it. Take your chances with an upgrade rather than a clean install. It only takes a few minutes to do what I suggested, your computer that you insist on using actually does the rest with no input from you. 

If you read my post there is **_no tweaking involved._** Just normal usage of the computer you want so desperately to use. So maybe you should go ahead and use it to it's full potential and let it show you what it is really capable of doing.

---

### Post by tekkidd on 2009-11-03
:lolflag:Had the same problems when I updated from 8.10 to 9.04. Just let this be a lesson dont update to the latest version of ubuntu after its just been relased, let it mature before updating

---

### Post by jgkellt001 on 2009-11-04
In reply to "prescence 1960", I appreciate that you are apparently in the know, and that you've, through either your own self taught experiences or learnings from others, have had the good fortune to ***not ***have experienced the frustrations that others in this thread have experienced in upgrading to 9.10. The link starts off with the quote "Considering a downgrade". This thread is mainly taken up by Ubuntu users who are having problems with the 9.10 upgrade and are scratching around for answers that they've yet to find!

Your advice re, back ups and the terminal procedures, will no doubt be taken up by many, including myself, when 10.04 arrives, but that doesn't solve todays problems.

The frustration is directed at The UBUNTU team not individuals![PHP][/PHP]

---

### Post by arashiko28 on 2009-11-04
As I far as I have gone, the crash repost shows when mounting a partition or any kind of drive to the perpheral ports. I have reported the bug is #467053 and others have reported it too, just do it and then they will know how to fix it, also, try to reproduce it in diffrent situations

---

### Post by presence1960 on 2009-11-04
> **jgkellt001 said:**
> 

Your advice re, back ups and the terminal procedures, will no doubt be taken up by many, including myself, when 10.04 arrives, but that doesn't solve todays problems.

**The frustration is directed at The UBUNTU team not individuals!**[PHP][/PHP]

Sorry if it came at your expense. But as more people consider doing an upgrade rather than a clean install maybe they can be saved from the type of experience you have had. Which is the same type of experience many had with upgrading to Jaunty also. Maybe they will see this post and find an alternative which will allow them to do a clean install preserving their settings and installed software after doing a couple of procedures. I know it works and it is simple too! Everything from my software (except for 2 I installed manually) & my settings are preserved just the way they were by doing a clean install. I have done this with Hardy to Intrepid, Intrepid to Jaunty and now Jaunty to Karmic.

I realize it is already too late for you, but if it can help one person it is worth it. And for those who have already experienced a bad upgrade they have an alternative to consider next time.

---

### Post by vilppu on 2009-11-04
I am considering moving from Studio 8.04 to Studio 9.10 which will no doubt entail a clean install. I would like to know a little bit more about how I can save the various settings and custom applications so that I would not have to download and reinstall them all again. I do know from experience (Mac and Windows) that updates and upgrades can be fraught with bugs and hardware problems.

---

### Post by presence1960 on 2009-11-04
> **vilppu said:**
> I am considering moving from Studio 8.04 to Studio 9.10 which will no doubt entail a clean install. I would like to know a little bit more about how I can save the various settings and custom applications so that I would not have to download and reinstall them all again. I do know from experience (Mac and Windows) that updates and upgrades can be fraught with bugs and hardware problems.

see post #6 from this thread.

---

### Post by s_raiguel on 2009-11-04
Count me among those upgrading, then decided to go back to 9.04 after two days. Most Flash videos would no longer play, nor would DVDs, despite installing restricted codecs. 

Naturally, I first made a backup of my home directory, including a list of installs, and conf files that had been customized, before downgrading. I have a question, though for Presence1960: The default installs always come with several things that I don't need, and get removed. Does the dpkg/my-packages command also take care of software that needs to be removed?

---

### Post by presence1960 on 2009-11-04
> **s_raiguel said:**
> Count me among those upgrading, then decided to go back to 9.04 after two days. Most Flash videos would no longer play, nor would DVDs, despite installing restricted codecs. 

Naturally, I first made a backup of my home directory, including a list of installs, and conf files that had been customized, before downgrading. I have a question, though for Presence1960: The default installs always come with several things that I don't need, and get removed. Does the dpkg/my-packages command also take care of software that needs to be removed?

when you run the first command to make the list of packages installed it only records packages actually installed on your current setup. When you place a copy of the file created by the first command into the home directory after installation and run the second command it installs every package in that file that is in the repositories.

Removing unwanted packages will still have to be done by you.

---

### Post by s_raiguel on 2009-11-04
Quoting presence1960: when you run the first command to make the list of packages installed it only records packages actually installed on your current setup...

Are you *sure* about that? When I run dpkg -get, a portion of the my-packages file reads: 

.
.
bogofilter-common				install
brasero						install
brltty						deinstall
brltty-x11					deinstall
bsd-mailx					deinstall
bsdmainutils					install
.
.

It certainly *lists* packages that have been removed, but whether or not the -set command makes appropriate use of that information is another question.

---

### Post by Tut Morris on 2009-11-04
I upgraded two machines: my old Dell Inspiron 3800 laptop and an Athlon-based home built. The laptop upgrade went without a hitch and it runs fine. The desktop, on the other hand, was a total cluster-f***.

As soon as I try to open any app other than some of the system utilities, the machine freezes. Even trying to run from the command line causes the system to freeze. Cycling power or hitting reset is the only way to free it up. I did a clean install from the Live CD and I get the same results. This machine ran flawlessly under 9.04 so I'm wiping the drive and doing a clean install of 9.04.

9.10 is definitely not ready for prime time, at least for the one machine.

---

### Post by azador1606 on 2009-11-05
Yeah, I think I jumped on too early. I only very recently upgraded to 9.04 from 7.04, and the experience of that upgrade was so positive that when I saw 9.10 I did not wait.

TV tuner - down
Secondary Hard Drives - read-only
webcam - down
security - weird stuff happening, need to get permission to log out
second display - need to log in twice
web browsers - Opera and Firefox running painfully slow
and a bunch of small stuff

Now I believe that it will all be fixed *someday*.
However, if the hard drive issue isn't fixed by the weekend then I will attempt to go back to 9.04 - even knowing I could be worse off.

Windows 7 by comparison (on another box) was faster, and only drew one complication (although a major one that required new hardware) - in time and money and purely from the effort\cost of upgrade compared to benefits -- this time Windows was the winner. (and that's hard to swallow)

---

### Post by jeggerleg on 2009-11-08
Before upgrading I had a dual-boot Ubuntu and Vista laptop.  Now I have the same but can't use Ubuntu because the wireless doesn't work. How do I do a clean install? 
I haven't the remotest idea how I managed to setup the dual-boot system in the first place, probably more by luck than management.
I can't risk having just a Linux machine because as this latest balls up has shown I wouldn't have a working machine. Nor are there Linux equivalents of some of the programs I need to use.

---

### Post by PRR on 2009-11-08
Even if you do a clean install you may not get wireless, especially if you use a
  dongle.

---

### Post by JCK-longhair on 2009-11-10
I've just moved from Windows XP to Ubuntu on my ThinkPad X41 tablet. So far I'm pretty happy (there are still some details to iron out). I did an upgrade as part of a fresh install (just to confuse you!) because I had a disc of 9.04 burned but immediately upgraded to 9.10 before doing anything else. Most things work perfectly.

Thanks presence1960 for post #6, that's useful for me as a newbie to have some idea of what needs backing up in case of ever needing to reinstall. I wonder though if anyone has thought to put that into a little semi-automated GUI app? I imagine there are a lot of people who are not so comfortable with command line/ terminal typing.

---

### Post by optimus2861 on 2009-11-10
My first Karmic impressions aren't great. Postgresql is outright broken for me (was acting as my amarok-1.4 backend, so that's hosed too); flash performance has taken a big hit (flash games like Bejeweled and Gemcraft now have awful video stuttering, very hard on the eyes); the wireless didn't want to work until I reset my router; and KDE looks worse than ever, not that it ever looks good in Ubuntu.

I'm willing to work with it for a while to see if I can get the kinks out, but if not, it's clean install time.

I may also free up some hard drive space and check out Mandriva's new release this weekend.

---

### Post by michaelzap on 2009-11-10
Before you downgrade, try the 2.6.32-RC6 kernel linked here:
[http://ubuntuforums.org/showpost.php?p=8263419&postcount=135](http://ubuntuforums.org/showpost.php?p=8263419&postcount=135)

My Lenovo Y530 was completely unusable with Karmic (and yes I did a clean install), but it's much better with that kernel. I still don't have suspend, hibernate, or surround sound working, but it runs fine otherwise. I could probably grow to like Karmic a lot once those bugs are fixed.

---

### Post by jnorthr on 2009-11-10
Hello JCK - welcome aboard  ;)  Howz maidstone tonite ?
if you need a nice ubuntu guide, see below my sig. line, though it's not been updated to reflect 9.10 changes.

---

### Post by KPDXHAM on 2009-11-10
](*,)Just another newbie that's been using ubuntu on and off for a few months now. I had tried 9.10 beta and had some problems with it. So removed and did a wubi to install 9.04 back onto my hdd. I have xp on primary hdd and ubuntu on slave. Last night I saw a pop-up notice when using 9.04 that I could upgrade to 9.10 and figured that the bugs must be gone! ;)
Like with the beta, it hung-up on the first re-boot. When I booted again it began loading for a few seconds in black screen with ubuntu logo and froze. The cap lock and scroll lock lights were flashing. So, I re-boot again. Graphic is missing on firefox desktop icon.(no big deal, I can replace that) BUT, then it locked-up again on next re-boot.
Guess what:?:

I'm removing 9.10 and will do clean install like someone else mentioned and hope it works out better [-o<, otherwise I'll just go back to 9.04.

---

### Post by mudguts on 2009-11-10
quick and silly question.   
You install 64 bit? or 32 bit?

i had a t60 running 9.10, everything seems to work well EXCEPT suspend.

but then again, I only had 9.10 installed for about a week before I sold it.

---

### Post by donaldt on 2009-11-10
Greetings,

I am trying to recover to a Linux system on an external hard drive.  Had a great experience for 8 months using 9.04.  With the BIOS set to boot the USB hard disk drive first, I could always access Ubuntu by just plugging in the USB hard disk drive.  With the USB unplugged, the computer booted Vista.  No problems.  Great way to keep the programs separated.  (I thought?)

Did an on line upgrade to 9.10 on day one.  (Big Mistake!)  Went back and forth between using a live cd to get Ubuntu 9.10 working and a USB mini windows program (USB stick) to restore the MBR in the Vista computer.  Could never get both working at the same time.  If one worked, the other would not and vice versa.

Eventually destroyed my Vista portable (the host computer) system.  Error 21 prior to any boot capability, so no way to access either drive.  Spent lots of money to get it re-loaded and working again.  Don't want to repeat that experience.  Very shy now about using Ubuntu on an external drive and Vista on my host computer.  The Vista system runs my business.

Heard about Super Grub Disk.  Downloaded unetbootin for windows.  Downloaded Super Grub Disk usb_0.9799.tar.gz.  Formatted a USB thumb drive to NTFS file system.  Used Unetbootin to load SGD to thumb drive.  Everything worked as expected.  Said I should re-boot.  Did a re-boot, but extracted the thumb drive prior to re-start.  

Plugged the thumb drive into small Fujitsu notebook computer.  Notebook runs Windows XP.  Set the notebook bios to boot the USB thumb drive first.  Re start computer.  Received error message "BOOT MANAGER IS MISSING  Press control alternate delete to re-boot".  

Is there some way I can recover the missing boot manager or must I begin all over?  Is it possible to use SGD to boot a dead Linux system?  

I re-loaded 9.04 on the external hard drive and it worked fine, but when I shut it down I had to restore the MBR on the notebook and after that, then the Unbuntu system was error 17...and I stopped.  If I get access to one system the other one goes dead.  Never able to get both going at the same time.  Never able to get either computer to boot Ubuntu 9.04 on the USB hard disk drive.  Error 17, go back in with a live CD, restore the Ubuntu system.  Shut down and try XP.  Doesn't work.  Use the mini windows program to restore the MBR in XP.  Try Ubuntu 9.04.  Error 17 again.   ...and thus it has gone for the past week.  

I just gave up and signed up for Canonical paid software support.  Haven't heard from them yet, but it will be interesting to hear the party line.

My personal opinion of Linux is now in the dumpster.  How can anyone expect the average computer user to go through all of this grief to be able to use a system just because it is free?  It is worth a few hundred dollars to keep using an inferior system that is backed by support and has none of these problems.  Sorry, Canonical.  Your software is not ready for prime time.

donaldt

---

### Post by Ubuteric on 2009-11-10
So how do unistall 9.10?? I was using 9.04 with no issues now after installing 9.10 I cant access the net and I'm sick of it.
Do I have to format the disk? I dont want to do that as I dual boot with windows and I have stuff on the windows side I'd rather not disturb.
Any help on how to go back to 9.04 would be greatly appreciated.

---

### Post by jimbo99 on 2009-11-10
I have so many Linux machines that prior to the official release I chose one box to try an update on.  It failed with some oddities.  That first machine ended up with a wipe and a reinstall of 9.10 (which went very well).  I then attempted a second machine as a test and it had exactly the same problem as the first, only this one couldn't be wiped in order to start over.  I'd spent too much time over the years customizing it and actually using it -- hehe, and it isn't my primary machine.  I use Linux folks, really use it.

This machine's problem were the same so I began to investigate. I posted a thread with my problem and what I did to resolve it.  That resolution followed me onto every other Linux machine I have as I was cautious that each one would have the same problem.  Needless to say I took a proactive approach to those other machines.  Every one of the remaining machines so far has gone very well once I found that fix--it was to alter the xorg.conf file and replace the driver reference from "nvidia" to "nv", then do the upgrade and reboot.  Afterwards I did a reinstall of the video drivers.  I see there's a sticky thread where they were working this out.  I sort of wish they'd read my thread first as they wouldn't have had to reinvent the wheel like they did.

Today I am updating another laptop. I did a switch to the layout of my work area and had to put a smaller form factor laptop in place of a larger HP wide screen.  I did the "nvidia"/"nv" thing first.

Luckily I haven't had any issues with grub or otherwise, but I also haven't tried, on any of my machines to convert my partitions to ext4.  So far, all of my wireless issues have been resolved by Karmic and all of my audio issues have been resolved.

Oh, and there was one machine where I was able to resolve the first boot issue but once I began using the system the sound was totally screwed up.  I chose at that time to back up, wipe and reinstall.  I chose ext4 as the file system and all my sound issues completely disappeared.

Only issue I have currently on EVERY machine is that there's no shutdown option off the desktop.  I have to log out first then shut down, which is ridiculous and costs me time.  Maybe it is some screwball bug (or screwball programmer) that's causing it.

Anyway, I'm amazed at the number of issues people are having and the type.  I really miffed that so many people had some really oddball problems.

Edit:  The install went as planned.  Nothing unusual.  But I have to comment that I did forget that on all my upgraded systems the icon for Firefox is missing.  I have to say that it is pretty messy of the Canonical folks, especially for them not to have seen this.

---

### Post by jfl on 2009-11-10
> **jimbo99 said:**
> I have so many Linux machines that prior to the official release I chose one box to try an update on.  It failed with some oddities.  That first machine ended up with a wipe and a reinstall of 9.10 (which went very well).  I then attempted a second machine as a test and it had exactly the same problem as the first, only this one couldn't be wiped in order to start over.  I'd spent too much time over the years customizing it and actually using it -- hehe, and it isn't my primary machine.  I use Linux folks, really use it.

This machine's problem were the same so I began to investigate. I posted a thread with my problem and what I did to resolve it.  That resolution followed me onto every other Linux machine I have as I was cautious that each one would have the same problem.  Needless to say I took a proactive approach to those other machines.  Every one of the remaining machines so far has gone very well once I found that fix--it was to alter the xorg.conf file and replace the driver reference from "nvidia" to "nv", then do the upgrade and reboot.  Afterwards I did a reinstall of the video drivers.  I see there's a sticky thread where they were working this out.  I sort of wish they'd read my thread first as they wouldn't have had to reinvent the wheel like they did.

Today I am updating another laptop. I did a switch to the layout of my work area and had to put a smaller form factor laptop in place of a larger HP wide screen.  I did the "nvidia"/"nv" thing first.

Luckily I haven't had any issues with grub or otherwise, but I also haven't tried, on any of my machines to convert my partitions to ext4.  So far, all of my wireless issues have been resolved by Karmic and all of my audio issues have been resolved.

Oh, and there was one machine where I was able to resolve the first boot issue but once I began using the system the sound was totally screwed up.  I chose at that time to back up, wipe and reinstall.  I chose ext4 as the file system and all my sound issues completely disappeared.

**Only issue I have currently on EVERY machine is that there's no shutdown option off the desktop.  I have to log out first then shut down, which is ridiculous and costs me time.  Maybe it is some screwball bug (or screwball programmer) that's causing it.**

Anyway, I'm amazed at the number of issues people are having and the type.  I really miffed that so many people had some really oddball problems.

The "shut-down" button was replaced with the "log-out" :rolleyes:
Right click on the panel, choose "ad to panel" scroll down to the shut-off option and add it.
You can remove the log-out icon if you want.

---

### Post by Ubuteric on 2009-11-10
so any ideas on how to get rid of 9.10 and reinstalling 9.04???

---

### Post by michaelzap on 2009-11-10
> **Ubuteric said:**
> so any ideas on how to get rid of 9.10 and reinstalling 9.04???
A clean install is always worth the extra effort.

---

### Post by Ubuteric on 2009-11-10
> **michaelzap said:**
> A clean install is always worth the extra effort.
 
So that means I have to format and reinstall?

---

### Post by michaelzap on 2009-11-10
Well, personally I would try the RC6 kernel that I posted a link to above before downgrading (if you haven't already). It turned my completely useless Karmic installation into something close to a thing of beauty. But if you decide to downgrade, then yes back up your files and reinstall (deleting and recreating the partition or reformatting the disk as you do).

---

### Post by Ubuteric on 2009-11-10
> **michaelzap said:**
> Well, personally I would try the RC6 kernel that I posted a link to above before downgrading (if you haven't already). It turned my completely useless Karmic installation into something close to a thing of beauty. But if you decide to downgrade, then yes back up your files and reinstall (deleting and recreating the partition or reformatting the disk as you do).
 
 
cool thanks

---

### Post by robtg on 2009-11-10
> **jgkellt001 said:**
> Call me old fashioned, but I still don't see why I or anyone else has to become an expert at saving *this* and *that*, *tweak* the other and *tweek* the same, *stand* on your head and *drink* a pint of beer from the far side of a glass, **just so you can upgrade your Ubuntu 9.04 to 9.10** without any problems.

I just want to use my computer,,,,,not program the damn thing!

I couldn't agree with you more.  I backed-up my data and then did a clean install of 9.10.  The install went fine but the results had enough issues that my clean install of 9.10 was followed by a clean install of 9.04.  Having things that previously worked in 9.04 be broken in 9.10 was especially annoying.

You can't really complain about free software, but Canonical took this out of the oven way too soon.

---

### Post by jeggerleg on 2009-11-11
> **PRR said:**
> Even if you do a clean install you may not get wireless, especially if you use a
  dongle.

I have now managed to reinstall an earlier version of Ubuntu I have on disc.  I also have a dual boot system again.
Can anyone suggest why in Ubuntu my touchpad doesn't work, or a USB mouse when connected?
Thank God for Vista

---

### Post by jimbo99 on 2009-11-11
> **jfl said:**
> The "shut-down" button was replaced with the "log-out" :rolleyes:
Right click on the panel, choose "ad to panel" scroll down to the shut-off option and add it.
You can remove the log-out icon if you want.

Heh, that's silly.  They added time to the shutdown when they claimed they were cutting down on the time to shut down.

We asked them to reduce the start up time.  We all know this.  It makes no sense to reduce the start up time if they don't reduce the shutdown time also.  There's a lot of services that start up that don't need to be shutdown when we quit.  Those services apparently were also optimized so that the chain of links in shutdown events was minimized.

To force us to go to logout first is ridiculous because it adds to the shutdown time (in a serious way).  Shutdown should shutdown from the desktop.  Every OS has that, gnome and kde used to as well.

---

### Post by jgkellt001 on 2009-11-12
> **robtg said:**
> I couldn't agree with you more.  I backed-up my data and then did a clean install of 9.10.  The install went fine but the results had enough issues that my clean install of 9.10 was followed by a clean install of 9.04.  Having things that previously worked in 9.04 be broken in 9.10 was especially annoying.

You can't really complain about free software, but Canonical took this out of the oven way too soon.

I've eventually backed all my data up and did a clean install of 9.10. A bit of a pain reinstalling Flash 10, printer drivers,medibuntu & various other bits, but the sound now works and the overall performance is very neat and tidy. I'm now happy again in respect of Ubuntu on my computer. However, when Ubuntu 10.04 comes out, I think I'll hold fire for a while and see what happens before i even think of an upgrade!

Regards

jgkellt001

---

### Post by jeggerleg on 2009-11-13
Managed at last to return my machine to the way it was two weeks ago. The update manager is informing me version 9.10 is available.  I don't think so.

---

### Post by cornholder on 2009-11-14
I did the update from 9.04 to 9.10 through the Update Manager, in the hopes it would solve my problems customizing the usplash and GDM login screens. Facepalm.jpg; after trying and failing even harder, I read around here and found out that they took away a lot of the options we had to play with those screens in the effort to reduce boot and shutdown times. 

When I first updated, it had my old usplash but it was all squashed into the middle of the screen at a smaller resolution. After changing the usplash to a different one, it decided I was only going to get the verbose text of the processes starting up. So currently on startup I get that in tiny font on a black screen, then somehow it gave me a Mythbuntu GDM theme that looks like grey corduroy, then it switches to my desktop wallpaper with an ugly Windows95-grey login box, then after login it switches back to the Mythbuntu corduroy while it plays my login sound and then a few seconds after that, I'm in. Synaptic says to remove the Mythbuntu package, it will also have to remove xsplash and ubuntu-desktop, which doesn't sound like what I want. Total login time is around 30-35 seconds, probably 10 seconds longer than Jaunty took. Shutdown is definitely a few seconds faster, however.

I am currently backing up all my movies and junk - which is taking 15-20 minutes per movie because the update to 9.10 didn't magically install the usb2 drivers that I lost last time I reinstalled 9.04 a few months ago - because I bring my laptop all over to show friends stuff, and I think it'd be cool to turn it on and have it say something like "HEATING PRIMARY REACTION CHAMBER" or "SATURATING PLASMA FIELD" while a status bar builds. That in itself is worth doing a clean install of 9.04 to me.

---

### Post by singercs on 2009-11-14
I also upgraded from 9.04 to 9.10 and man, I had to after three frustrating days of reinstalling and formatting reinstall Xp to get the computer to boot and last evening tried an older version 8.04.3 and lo and behold, works like a charm, everything works like new and I am keeping this older version.
When 9.10 was first installed, it was very slow to boot,hung on every step and could not find my drives, also after I did the update it wouldn't boot without the disc in.
I can't be bothered to fool with issues like this all the time, I would rather pay the 100.00 for my XP, anyway, after I installed the older OS, everything works like it should.

---

