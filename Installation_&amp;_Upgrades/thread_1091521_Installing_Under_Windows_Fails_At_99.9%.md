---
title: "Installing Under Windows Fails At 99.9%"
date: 2009-03-09
forum: Installation &amp; Upgrades
---

### Post by RRRitchey on 2009-03-09
Hi, 
I have tried everything I can think of to get Ubuntu to install under Windows but it does the same thing every time, the install gets to 99.9% and then says it cannot read the CDROM.  I have cleaned the disk, reburned at a slower speed, downloaded the image a second time and burned a new disk.  I am not sure where to go from here.  Any ideas why its hanging at 99.9%?

---

### Post by Neo_The_User on 2009-03-09
What do you mean install under windows?

---

### Post by avtolle on 2009-03-09
The OP is using Wubi to install Ubuntu as an application, if I may use that term, in Windows. The installation is failing before it totally completes, as I read the initial post.

@RRRitchey, my best thought is to uninstall Ubuntu from your Windows installation; then run a defrag on your HDD (more than once, if using the Windows "native" defrag utitlity) and perhaps run chkdsk -r from Windows, then try a new installation.

---

### Post by Neo_The_User on 2009-03-09
> **avtolle said:**
> The OP is using Wubi to install Ubuntu as an application, if I may use that term, in Windows. The installation is failing before it totally completes, as I read the initial post.

@RRRitchey, my best thought is to uninstall Ubuntu from your Windows installation; then run a defrag on your HDD (more than once, if using the Windows "native" defrag utitlity) and perhaps run chkdsk -r from Windows, then try a new installation.

e2fsck -c from ubuntu live cd works too.

---

### Post by upchucky on 2009-03-09
The answer to this is probably over my head, but I do remember reading somewhere a situation where the cd-rom drive info is not getting passed to the kernel when the kernel is created, so when the bios gives up control of the cd-rom the kernel does not know what to do with it.

If i find where I read this I will post it, but in the meantime i suggest searching here and LinuxQuestions.org as well as google.

---

### Post by RRRitchey on 2009-03-09
Hi, 
I am trying to install under Windows by putting the CD in while Windows is running.  I then click on the "Install Inside Windows" option.  I am doing this because I tried to use the Live CD install and I had my Windows installation trashed last week.  I have a RAID 1 system for my main disk drive that has the boot sector on it.  I think this is why the Ubuntu installation trashed my Windows installation.  When I read how to do raid with Ubuntu it was a lot more work that I have time for right now.  I have run Live CD and it works fine on this computer but I really need the NVidia display drivers and they do not persist under Live CD. I want to try running gEDA is the real reason I am trying to get this installed. Ubuntu is not getting installed at all, it has the CDROM error before it does any installation. The disks have been defraged this weekend and chkdsk does not find any errors.  I am running an Intel i7 965 with an EVGA X58 motherboard. Thanks for any help.

---

### Post by RRRitchey on 2009-03-09
Hi upchucky, 
This sounds like what is happening. I have a new LG DVD writer, number GH20LS10.  Its is a SATA drive. Could it be the kernel does not recognize this DVD drive?  Thanks,

---

### Post by avtolle on 2009-03-09
The SATA DVD writera could be a problem. This was common, as I recall, with 8.04. The fix there for many was to use the following boot option: all_generic_ide (see [https://help.ubuntu.com/community/BootOptions](https://help.ubuntu.com/community/BootOptions) for an overview of using boot options). HTH.

Alternatively, I'd recommend giving the alternate CD a whirl to get installed, especially if the above doesn't help.

---

### Post by RRRitchey on 2009-03-09
Hi, 
At this point I am scared to death of installing Ubuntu in any way except as a application under Windows.  I cannot afford to loose my XP installation again and I think that I will because of my RAID 1 drives and the fact the boot loader cannot handle a boot sector on a RAID 1 drive.  I can't use any boot options when installing under Windows so I don't think this is a good option.  I also found that the Alternate CD has to be a stand alone installation so that scared me off it. If you have any ideas how I can do a stand alone install but use the Windows boot loader let me know.  I need the RAID 1 security but it seems to be really messing up my ability to load Ubuntu. Thanks,

---

### Post by avtolle on 2009-03-09
I've never done a RAID installation before, but have read the various "how-tos" out there, and agree that this install isn't something to do unless there is plenty of time available and little to no other pressures on the person installing.

Yes, the alternate install is a "stand-alone" in that it cannot be accomplished using Wubi within Windows. One may dual boot with Windows once the installation has completed. 

On using the Windows bootloader; there is some application available (something BCD: sorry, don't have it written down any where, and memory isn't what it used to be) to use the Windows bootloader with Ubuntu. Perhaps a google search? Open BCD rings a faint bell. Good luck.

---

### Post by avtolle on 2009-03-09
BTW, is Raid1 a "hardware" RAID; a "fake RAID"; or just what? IIRC, Wubi won't successfully install Ubuntu in a software or fake RAID environment. Again, from memory, when reading the Wubi site.

EDIT: I see things have changed a bit; [https://wiki.ubuntu.com/WubiGuide#Software%20raid%20arrays](https://wiki.ubuntu.com/WubiGuide#Software%20raid%20arrays) says that installation on a RAID1 will be supported in the Wubi 8.10 release.

---

### Post by RRRitchey on 2009-03-09
Hi, 
I am sure its a fake RAID.  Its built into the Intel chipset on the motherboard but requires a software driver that I had to slipstream into the Windows install CD.  I wish that Ubuntu had something like the slipstream program I used on the Windows CD (nLite - its great).  I have a 5th drive that is not in any RAID and I wanted to install Ubuntu on it.  But when I tried this the first time stand alone, the Windows boot screen would come up after Ubuntu had been installed but then it would crash (a window came up that must have had information but it rebooted so fast I could not catch it with PAUSE) and reboot immediately and every time no matter what safe mode I used. Strange thing was I never saw a screen that would allow me to pick Ubuntu or Windows.  Frustrating.  Thanks for your input.

---

### Post by bob hughes on 2009-03-09
This is not an uncommon thread. As a newbie I posted "ubuntu 8.1 in windows XP3 install problem" Sunday GMT
No firm suggestions as to a fix .Is this something to do with raid discs or a HPT 374 raid controller?
I have tried on an old ABIT KT7-MAX2 and my new ABit IP35 PRo with a Jmicron JMB 36x Controller.
Basic error is could not access CD when near end.
Done integrity checks, download checks ... burnt at 4X
Await enlightenment from old hands.
Worrying that this could be putting people off UBUNTU?
Bob Hughes

---

### Post by RRRitchey on 2009-03-09
Hi, 
I know I am getting frustrated.  I have two computers I cannot install Ubuntu on.  This computer I just put together (i7 965, EVGA X58 mb, 2 RAID 1 drives, 6GB) and the old one I replaced (AMD 64-bit, ASUS mb, 2GB).  Both hang on me.  The old one will load Ubuntu but gets to checking battery and hangs.  I have not found a way around that.  This one seems to hang when it gets done loading Ubuntu onto the hard drive and wants to switch to the kernel to finish installation.  I would think I could get this to load on one of these machines but no luck.

---

### Post by upchucky on 2009-03-09
Ok, the first install you tried did not trash windows, everything was still there, it just needed the master bootloader repaired. this involved setting up the chainloader for windows and the boot stages containing drive info for grub. this information is located in the menu.lst file of grub.

with that said, you can use use ntfsclone (which is provided free on the knoppix live cd), to make a image of the existing windows install and be able to restore windows and all installed programs within about 20 minutes.

to install windows and ubuntu as a dual boot, you should have a utility called advanced super grub disk, it will repair windows and linux bootloaders, and the above mentioned knoppix cd will also let you edit any windows or linux files to get either system working again.

there are many key words i have in this post that a quick search of this forum will get you hundreds of replies that have fixes for any linux/windows install problems.

Of course the above assumes you have solved the hang at 99% problem which is a different problem than dual booting or fixing windows/linux installs.

I will keep looking for the post about kernel problems when reading some cdrom info, just a thought, are you using third party drive overlay interpreter software for windows to talk to the cdrom, if so this may be the problem. as this workaround for crappy cdroms is not supported in linux.

---

### Post by RRRitchey on 2009-03-10
Hi upchucky, 
Thank you for all the information, its very helpful.  The DVD writer is recognized by Windows and does not require any third-party driver.  It uses the Windows standard driver. Still have not been able to get around the 99.9% problem. I thought it might have corrupted Windows because the Windows boot screen with the progress bar came up but then it seemed to fail when it tried exit the boot screen, there is always a "glitch" in the progress bar and then it transfers to the login screen. Windows rebooted about where the glitch should have been. I will look into all the solutions you have given me. 

Maybe you can give me some insight on my other machine I cannot get 8.10 to install on either.  I did an install under Windows of the AMD 64 build.  This went fine.  When I boot I get a Windows boot menu with Windows and Ubuntu.  When I start Ubuntu it goes fine until I get to Starting Ubiquity.  This seems to time out and then it tells me setting 640x480 mode failed.  The motherboard is an ASUS with Nvidia video built in. I then get a command prompt.  Any idea how I can proceed to get the UI up?  

Thanks again.

---

### Post by upchucky on 2009-03-10
the second pc is choking on the monitor settings or lack of the proper settings in the xorg.conf file
you are gonna have to search for similar problems here and find out how to get the proper settings for your display type.

a common method is trying to find a post that has the same sys you have, chances are the proper settings are in the replies to their post.
asking how to discover display, monitor type, resolution, should produce many posts of information and hints.

almost every display on different systems are set up with different settings, its trial and error to get it right.

one way to find the right or close settings is to boot using the live cd and if it has an acceptable display setting then edit the xorg.conf file of the ubuntu install to match the xorg display settings that the live cd is using. it is important that you understand how this is done so read carefully how to edit and set up displays.
after u get a reasonable display working and save it as a generic setting, you are gonna need to search for nvidia set-up for your sys, that is a whole other task with 8.10, so one step at a time.

---

### Post by RRRitchey on 2009-03-10
Hi upchucky, 
Again, thank you for your input.  The live CD hangs at "Checking Battery State" which I find strange because this is a desktop.  Any idea why its doing that.  I really prefer to install on this older machine but I have not found a way to do it there either.

---

### Post by Twitch6000 on 2009-03-10
> **RRRitchey said:**
> Hi upchucky, 
Again, thank you for your input.  The live CD hangs at "Checking Battery State" which I find strange because this is a desktop.  Any idea why its doing that.  I really prefer to install on this older machine but I have not found a way to do it there either.

Humm older machine.

Might I ask what the specs are for this older machine?

If they are below 512mb ram and 1.6ghz cpu ubuntu will not install (well it didn't for me atleast)

You would need a lightweight version of ubuntu or even a different distro all together .

---

### Post by RRRitchey on 2009-03-10
Hi Twitch, 
Oh, no its not that old. Its an AMD 64 processor running a 2.2GHz, 2GB of RAM and an ASUS motherboard with integreated Nvidia graphics that is about 2 years old.  When I canceled the Live CD boot, it again told me that it could not initialize the video at 640x480.

---

### Post by RRRitchey on 2009-03-10
Hi Twitchy, 
Also, the built in video is an Nvidia GeForce 6150 GPU. For some reason this is giving 8.10 fits.  Thanks,

---

### Post by avtolle on 2009-03-10
Re: second computer. Try running the Live CD in safe graphics mode (F4 at the initial screen will give you some options, select Safe Graphics) then select "Try...." and see if that gets you anywhere. If it does (i.e., you get to the desktop), and you want to try to install again from it, then go to System>Preferences>Appearance, go to the Visual Effects tab, select None, then close and click on the install folder. If this gets you installed, then you will need to get the driver (from Hardware Drivers) for the graphics installed. Personally, I get all the updates downloaded and installed before trying to install the driver, as I've never had any issues doing it that way, but you can try the driver out before updates (there will be at least one kernel update after installation) to see if it works. Hopefully, this won't give you any trouble.

But first, let's see if you can install in "Safe Graphics" mode with visual effects turned off.

---

### Post by Neo_The_User on 2009-03-10
> **avtolle said:**
> Re: second computer. Try running the Live CD in safe graphics mode (F4 at the initial screen will give you some options, select Safe Graphics) then select "Try...." and see if that gets you anywhere. If it does (i.e., you get to the desktop), and you want to try to install again from it, then go to System>Preferences>Appearance, go to the Visual Effects tab, select None, then close and click on the install folder. If this gets you installed, then you will need to get the driver (from Hardware Drivers) for the graphics installed. Personally, I get all the updates downloaded and installed before trying to install the driver, as I've never had any issues doing it that way, but you can try the driver out before updates (there will be at least one kernel update after installation) to see if it works. Hopefully, this won't give you any trouble.

But first, let's see if you can install in "Safe Graphics" mode with visual effects turned off.

Yeah, sometimes Compiz can mess things up.

---

### Post by RRRitchey on 2009-03-10
Hi avtolle, 
On the second machine I never get an Ubuntu screen.  It always comes up with "boot:".  It does this whether I run the 32-bt or 64-bit Live CD. To do Live CD I have been typing in "live".  Is there a switch to boot live in safe mode?  Thanks,

---

### Post by Neo_The_User on 2009-03-10
You know right after the language selection, you can choose try ubuntu... install... etc? well at the bottom there are F keys and tells you what they do. Hit the one for "More options" or "Driver" and select safe graphics mode. You'll find it. ;)

---

### Post by avtolle on 2009-03-10
> **RRRitchey said:**
> Hi avtolle, 
On the second machine I never get an Ubuntu screen.  It always comes up with "boot:".  It does this whether I run the 32-bt or 64-bit Live CD. To do Live CD I have been typing in "live".  Is there a switch to boot live in safe mode?  Thanks,
I know this isn't your situation, but when reading this I was beginning to think you had a pre-intel Mac there with yaboot (that's a bootloader for ppc chips), as what you describe fits the yaboot screen to a "T". If it was yaboot, yes, there is a switch to boot in safe mode. I don't recall what it is, however, but it would be displayed if the Tab key was pressed at the boot: prompt (along with a number of other options).

I'll give this some thought; off the top of my head, I've no answer to your question.

---

### Post by RRRitchey on 2009-03-10
Hi Neo_The_User, 
Well, if I let "boot:" time out a get a small blue graphic at the bottom of the screen that has 7 options.  "Try without change" "install" etc and "Advanced Options" but when I choose Advanced there are no options, only "Back".  None of the F keys do anything at this point.

---

### Post by Neo_The_User on 2009-03-10
> **RRRitchey said:**
> Hi Neo_The_User, 
Well, if I let "boot:" time out a get a small blue graphic at the bottom of the screen that has 7 options.  "Try without change" "install" etc and "Advanced Options" but when I choose Advanced there are no options, only "Back".  None of the F keys do anything at this point.

I'm going to pop in my Ubuntu CD to be of further assistance.

PLEASE NOTE: OLD BIOSES BY DEFAULT DO NOT SUPPORT USB ON EARLY START-UP

edit: It's F4. Use up down arrows to select safe grapics. F6 to turn off quiet splash.

---

### Post by avtolle on 2009-03-10
> **RRRitchey said:**
> Hi Neo_The_User, 
Well, if I let "boot:" time out a get a small blue graphic at the bottom of the screen that has 7 options.  "Try without change" "install" etc and "Advanced Options" but when I choose Advanced there are no options, only "Back".  None of the F keys do anything at this point.
Hmm, that's remarkably different from anything anyone else has posted that I've read on the Forums. What are the other options that appear after letting "boot:" time out (other than "Try without change" "install" and "Advanced Options"?

---

### Post by Neo_The_User on 2009-03-10
Might be a bad iso or burned wrong. It's supposed to have all those other things. :(

---

### Post by RRRitchey on 2009-03-10
Hi Neo_The_User, 
I have downloaded and burned twice.  Everyone says its a bad ISO but I get the same thing on both downloads and burns.

---

### Post by Neo_The_User on 2009-03-10
> **RRRitchey said:**
> Hi Neo_The_User, 
I have downloaded and burned twice.  Everyone says its a bad ISO but I get the same thing on both downloads and burns.

Well maybe its a crummy CD-ROM drive. If its a bad burner, no matter how many times you re-burn it, it probably won't work. Try burning the iso on a new machine (if you have one available) or swap the CD-ROM drive out. Those old PATA CD-ROM drives I've always had problems with. If you have a SATA CD-ROM drive lying around somewhere, try that.

---

### Post by RRRitchey on 2009-03-10
Oh, and also, it happens with both the 32-bit and 64-bit versions, exactly the same. Same CD on my i7 machine boots into the Ubuntu graphic screen for Live CD.  I can't see how it can be a bad CD. I have burned the CD on both machines and swapped them between both machines. Same results.  I have tried to be thorough.

---

### Post by Neo_The_User on 2009-03-10
> **RRRitchey said:**
> Oh, and also, it happens with both the 32-bit and 64-bit versions, exactly the same. Same CD on my i7 machine boots into the Ubuntu graphic screen for Live CD.  I can't see how it can be a bad CD. I have burned the CD on both machines and swapped them between both machines. Same results.  I have tried to be thorough.

...No idea my friend. avtolle might be of further assistance. One of the Ubuntu forum staff or admins might be able to help you too. They've seen and heard pretty much everything.

---

### Post by avtolle on 2009-03-10
Not that this necessarily a guarantee; have you tried to boot another computer with the cd you burned from the download? 

I'm sure you've read/heard the standard advice on this many times, but I'll give it another iteration: after downloading the iso, check the iso's md5sum to be sure it is the same as that provided for the iso on the official Ubuntu site; burn the iso as an image to CD-R using a slow speed (4x to 8x); and then check the CD for defects on boot. The last step is, of course, from the initial menu that you aren't getting to, although it might be an option at the bottom of the screen in the blue graphic you posted about earlier.

EDIT: just saw the post you made as I was composing the above. It seems to me that there's a problem with the cd on the "older" machine, and it's likely related to the on-board graphics, assuming (as it appears) there were no problems with the iso and burn.

---

### Post by avtolle on 2009-03-10
Forgot to ask the essential question: when you type "Live" at "boot:", what does that give you? You've likely already posted that, and I missed it or don't recall what you posted.

---

### Post by Neo_The_User on 2009-03-10
Don't forget about the edit button, avtolle. ;)

---

### Post by RRRitchey on 2009-03-10
Hi, 
To reply to the last couple message.  My 32-bit CD will boot on my new machine in Live CD mode just perfectly. I get graphics, sound, everything. My issue on this machine is that when I try to install under Windows the CD hangs at 99.9% and says it cannot read the CD.  I get the screens you are talking about, the Ubuntu splash screen, the language screen, all the F-key options.  Same CD in my older machine comes up with "boot:".  When it times out I get the blue box, the screen is still in text mode, no graphics.  This does not look anything like what I get on my new machine.  I have to believe the CD is OK. When I type "live" at "boot:" I start getting a lot of text saying what is loading.  It gets down to "checking battery" and hangs.  When I hit ctl-alt-del it starts shutting down and then tells me it cannot initialze the display controller in 640x480 mode.  From all the reading I have done I thought the 32-bit CD should load just fine in my AMD machine, but I get the same results using the AMD 64-bit CD anyway.

---

### Post by avtolle on 2009-03-10
Thank you RRRitchey. This is a bug ([https://bugs.launchpad.net/ubuntu/+bug/277587](https://bugs.launchpad.net/ubuntu/+bug/277587)) that has been reported many times. While the initiator of the bug report linked had ATI graphics, this seems to not be related to any particular graphics card/chip, but affects some (looking through the report, ATI, nvidia, and Intel were all involved). 

One poster was able to overcome the hang by pressing the enter key when it occurred; this didn't work for others. I note that the last post indicated this was not an issue once an upgrade to the latest 8.10 kernel (2.6.27.13, IIRC) occurred.

What I suggest is that when you type "live" at "boot:", try hitting the enter key; alternatively, press the power key once (this might work for you, I have to do it on an installed 8.10 on a Compaq laptop to get past a boot hang) to see if boot continues. There is a boot option that has been posted, which I don't recall at the moment, which will reportedly get one past the hang. I'll take a look around and see if I can find it, and if I do, will post it along with a link to a help piece on how to use boot options.

---

### Post by RRRitchey on 2009-03-10
Hi avtolle, 
Thank you for all your help.  I will try these suggestions.  I guess this all still does not get me past my problem of the fact both computers hang at 99.9% when I try to install under Windows.  I have LG DVD drives on both of them so this is probably the issue but they work with the standard Windows drivers and they work on the new machine to boot into Live CD.

---

### Post by avtolle on 2009-03-10
RRRitchey, you should try hitting the Enter key or press the power button at the point it hangs; just reread my earlier post, and it was far from clear on this.

The boot option I recalled is "acpi=off"; not sure how you would do this given the situation you are in. I would try "Live acpi=off" at "boot:" if the above suggestions don't work for you (this is how it would be done on a ppc machine at the similar yaboot prompt, and I'm trying to come up with a working analogy to that process). 

Back to the problem with the 99.9% install failure, I've not come upon anything else than that which I first posted. It does seem that there is a problem with passing control to the kernel too fast, as nearly as I can tell. I'll ponder on this some more, and post back with anything that I find/think of that might be of use.

---

### Post by RRRitchey on 2009-03-10
Hi, 
I have tried acpi=off already.  I did a lot of reading before I started posting.  I have tried it with and without quotes around acpi=off, neither seems to make any difference.  Hitting enter when its hung at checking battery stated does not do anything either.  Thanks for all your research. And I thought Ubuntu was suppose to be the easy linux to use!  I guess I just have weird hardware.

---

### Post by avtolle on 2009-03-10
RRRitchey, thanks for the update. Found another option to try: "nolapic_timer"; you likely have seen this, too, as it was mentioned along with acpi=off in one of several threads on the topic. 

On the LG DVD writer drive; the only other suggestion I have is to check to see if there has been any firmware updates for the drive. As you still have Windows, if there has been such an update, it would be simple to download and install the same. 

Othewise, I'm about to surrender to the vagaries of hardware compatibility issues one sometimes runs into when dealing with Linux and Windows "specific" hardware. I'll keep thinking, and if something else occurs to me, I'll be back. While we've not been successful, it has been a pleasure working on this with you.

---

### Post by RRRitchey on 2009-03-10
Hi avtolle, 
I really do appreciate all the time you took to help.  I have an automatic firmware updater that LG provides for Windows and no firmware has been updated for this drive at this time.

---

### Post by upchucky on 2009-03-10
I have been known to be wrong before, but since a live cd boot does work on the machine, it is possible to make it work when actually installed? Plus could he look at the logs of a good live cd boot to try to find a hint where the hang is?

On the battery hang issue,i have seen batteries that have extra contacts to tell the software that the battery is indeed actually installed, and contacts to provide battery temperature and charge state. clean the battery contacts with a pencil eraser, make sure the bat is not loose in the holder, and is a good battery, if it is partially defective it could cause a hang because the pc is getting bad battery info.

---

### Post by sandlidl on 2009-03-11
Maybe this sounds really stupid and basic, but I had some similar problems with several computers I was installing Ubuntu on. 

Turns out there was a bad ram module everytime. I had about every error in the book and then tested the ram and voila, there was the problem. Changed out the ram and it installed perfectly after that.

Put in the live cd and run the memory test.

Hope I'm not wasting your time. Cheers!

---

### Post by hochae on 2009-03-11
I got a same problem with version 8.10.
Please try again with version 8.042.

---

### Post by RRRitchey on 2009-03-11
Hi upchucky,
The machine Ubuntu Live boots on is the one that has the RAID drives.  Last time I tried to install it trashed my bootloader and I had to reload Windows because I did not know how to backup and replace the bootloader if it gets trashed.  The real problem is my boot sector is on one of the RAIDs and its seems this messes up bootloaders except for the Windows one.  Don't ask me why.  I will check RAM but I think I did that already. I will check the battery contacts, I did not realize the software could check the BIOS battery voltage. I guess I could also try 8.042.  Thanks for all your help.

---

### Post by RRRitchey on 2009-03-11
Hi upchucky, 
I was thinking about using virtualization to load Unbutu.  Something like Sun's Virtual Box.  Do you know anything about this? Thanks.

---

### Post by upchucky on 2009-03-11
the other posts here have gone further than i could have, and I am sorry we have not been able to get your current problems solved so far. however i did read that 8.10 when it was released was incompatible with nvidia, so I am still running 8.04. I also read later that there are work arounds to get 8.10 working with nvidia. but i have not tested this.

I have only worked with debian, ubuntu, knoppix and gentoo. In my honest opinion, anything ubuntu is ready for the world, and the others I have worked with are for challenging the daring spirit in me, they have provided many hours of beard growing, To be clear on this I love them for the challenge and experiments.

If you do go to 8.04, the following is the way to set up a nvidia card properly, there are others that use envy, but it is a work around, not a true install for the card. only do the card after you get a generic display working.

Set up Nvidia driver

Print out this guide, you will be in pure CLI for part of the install.

1)  Download the driver for your Nvidia Card from [http://www.nvidia.com/Download/index.aspx?lang=en-us](http://www.nvidia.com/Download/index.aspx?lang=en-us)
	1.a) Make sure its in your home directory, this will make it so we don't have to change directories later when were in terminal.

2) Open a terminal: Applications--> Accessories--> Terminal

3) sudo apt-get install build-essential

4) gksudo gedit /etc/modules
	4.a) Add "nvidia" without quotes to the list.
	4.b) Save and Exit

5) gksudo gedit /etc/default/linux-restricted-modules-common
	5.a) Add "nv" without quotes to the restricted list. It should look exactly like this: DISABLED_MODULES="nv"
	5.b) Save and Exit

6) sudo cp /etc/X11/xorg.conf ./xorg.conf.backup

7) sudo rm /etc/X11/xorg.conf
	7.a) Were just deleting your old xorg.conf file, we backed it up in step 6 just in case we ever need it back again.
	7.b) Getting rid of old drivers, use one or more of the sections that apply to you:
		-------------------------------------------------------------------------------------------------------
		If you used Envy to attempt a previous nvidia install please run this command now before you go on:

               sudo envy --uninstall-all 
		sudo dpkg -P envy 

		-------------------------------------------------------------------------------------------------------
		If you have some old Ubuntu repository/restricted driver manager attempts installed please run this command before you go on:

		sudo apt-get remove --purge nvidia*
                sudo rm /lib/restricted-modules/.nvidia*

		-------------------------------------------------------------------------------------------------------
		If you have a failed NVIDIA*.run (drivers from the nvidia.com site) run this command before you go on:

		sudo nvidia-installer --uninstall

		-------------------------------------------------------------------------------------------------------
####################################################################################
##................................................................................##
## Alright Now Assuming That You are starting with a clean slate lets move forward##
##................................................................................##
####################################################################################

8) CTRL-ALT-F1
	8.a) Okay were in Command Line only now, we have a little left to do in here.
	8.b)login:
	8.c)Password:

9) sudo /etc/init.d/gdm stop
	9.a) This step shuts down the x-server and gnome desktop manager

10) sudo chmod a+x ./NVIDIA*.run
	10.a) We made the nvidia installer executable.

11) sudo ./NVIDIA*.run
	11.a) Answer to the affirmative for all questions.
	11.b) Be sure to specifically say you DO WANT it to write a new xorg.conf
	11.c) If you somehow answered incorrectly on the last question in the installer then:
		c.I) sudo nvidia-xconfig #this will write a new or attempt repair of
                     an xorg.conf file for you.

12) sudo /etc/init.d/gdm start
	12.a) You should see an Nvidia Logo, and then be put at your login screen, 
              you should also be able to enable desktop effects.

Optional But recommended:
13) To get the driver to update itself when a new kernel is installed from the update
    manager be sure to follow the guide in this link:
     [http://ubuntuforums.org/showpost.php?p=5227704&postcount=1](http://ubuntuforums.org/showpost.php?p=5227704&postcount=1)

---

### Post by RRRitchey on 2009-03-12
Hi upchucky, 
I don't know how I can thank you for all this work.  So 8.04 might work out of the box?  I may try that.  I may not get to this till this weekend, I have some work to catch up on.  Again, you have gone out of your way for me, thank you very much.

---

### Post by RRRitchey on 2009-03-12
Hi upchucky, 
Just for fun I installed Virtual PC 2007 and found a website than had instructions for installing under Virtual PC.  It worked! This is a good solution for me since I won't be using it for everyday work and I don't have to reboot to run Ubuntu.

---

### Post by ago on 2009-03-13
This is a known problem with some CD drives when extracting the ISO: see [https://wiki.ubuntu.com/WubiGuide#Cannot%20access%20the%20CD](https://wiki.ubuntu.com/WubiGuide#Cannot%20access%20the%20CD)

In short, use the ISO file directly by placing wubi.exe and the ISO in the same folder and running wubi.exe

---

### Post by RRRitchey on 2009-03-13
Thanks ago, I will give it a shot.

---

