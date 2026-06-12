---
title: "What can be used besides wine to install windows programs?"
date: 2008-11-11
forum: General Help
---

### Post by Rubicon421 on 2008-11-11
Microsoft encarta is one of the only programs that I really want to keep and I can't get it to work with wine. It installed without error but will not run. I tried the wine setting to run in WinXP mode. What other methods are out there to install windows programs?/

---

### Post by pikabuntu on 2008-11-11
There's Crossover, but you have to pay for it...

---

### Post by mc4man on 2008-11-11
i don't have encarta around (may have a copy in a box somewhere - will look)

I'd focus on seeing if adding these 2 .dlls to wine has any effect. First in the system32 folder, possibly in the encarta or system folder. Other variables would be to set a dll overide in winecfg for them and trying win nt 4.0 vs. xp (I'd set up a separate profile up for encarta 

shrpnl10.dll
shrl30.dll

They should be available (according to MS) from the encarta cd in \Aref\Compnts   (or aref/compnts


MS info page
[http://support.microsoft.com/kb/249629](http://support.microsoft.com/kb/249629)

---

### Post by crazyness003 on 2008-11-11
Quick question: why encarta? If you have Internet access, encarta is obsolete (due to interwebs: [www.wikipedia.org](www.wikipedia.org), [http://www.encyclopedia.com](http://www.encyclopedia.com), and even [http://encarta.msn.com](http://encarta.msn.com) [encarta on the web])

So why install it?

---

### Post by ichi@YUKI on 2008-11-11
maybe you should try some virtualization and just run windows from a virtual drive.

---

### Post by Rubicon421 on 2008-11-12
> **crazyness003 said:**
> Quick question: why encarta? If you have Internet access, encarta is obsolete (due to interwebs: [www.wikipedia.org](www.wikipedia.org), [http://www.encyclopedia.com](http://www.encyclopedia.com), and even [http://encarta.msn.com](http://encarta.msn.com) [encarta on the web])

So why install it?
I agree, it is obsolete but my son uses the encarta kids explorer all the time. It's got great pics & videos with every result written on a level he can read and no results that I have to worry about filtering before he sees them. It's really great for kids who want to just type in a keyword and start learning, and it has a bunch of educational games.

---

### Post by Rubicon421 on 2008-11-12
> **mc4man said:**
> i don't have encarta around (may have a copy in a box somewhere - will look)

I'd focus on seeing if adding these 2 .dlls to wine has any effect. First in the system32 folder, possibly in the encarta or system folder. Other variables would be to set a dll overide in winecfg for them and trying win nt 4.0 vs. xp (I'd set up a separate profile up for encarta 

shrpnl10.dll
shrl30.dll

They should be available (according to MS) from the encarta cd in \Aref\Compnts   (or aref/compnts


MS info page
[http://support.microsoft.com/kb/249629](http://support.microsoft.com/kb/249629)
Thanks. So if I understand you right, when MS encarta tried to run in ubuntu it can't find dlls that should have been unloaded during the install, and I need to copy them to the right spot- right? And exactly where do I put the new dlls? 

Thanks again

UPDATE: I went to the folder on the disk that you mentioned and those dlls aren't there.

---

### Post by Rubicon421 on 2008-11-12
> **ichi@YUKI said:**
> maybe you should try some virtualization and just run windows from a virtual drive.
I messes around with it a little bit, but I would rather find something more like wine that just aids in installing it to run in ubuntu. I don't want to have to create a VM and load it every time, just to use one program. I thought I heard of something else a while ago that was like wine but I can't remember the name. I think it was something like cerana??

---

### Post by crazyness003 on 2008-11-12
> **Kill Vista said:**
> I messes around with it a little bit, but I would rather find something more like wine that just aids in installing it to run in ubuntu. I don't want to have to create a VM and load it every time, just to use one program. I thought I heard of something else a while ago that was like wine but I can't remember the name. I think it was something like cerana??

i think it was called credenza (or something like that). It was replaced by CrossOver from Codeweavers (same people of WINE). Only with CrossOver you get tech support(I think).

Sorry man, but some things are microsoft windows only....kinda like microsoft encarta, and windows live messenger (basically most of ms's products).

Keep experimenting with WINE. Report to [http://appdb.winehq.net](http://appdb.winehq.net) for assistance and what you're findings are. Maybe someone already went thru this and has an answer.
If all else fails...sorry to say this but windows is the answere. no one can deny that. it was designed to run in that os.

keep us posted on your findings

---

### Post by Rubicon421 on 2008-11-12
I udgraded to wine 1.1.8 to see if that would help. It still didn't work so I tried to run the install of encarta again. All it did was a repair and didn't give me an option to do a full install/uninstall. Then I found the uninstall windows programs option in wine but the icon for uninstalling encarta had a red X through it and I guess there is a problem with that feature. How else can I do a complete uninstall of encarta to try it from scratch with the new version of wine?

---

### Post by crazyness003 on 2008-11-12
> **Kill Vista said:**
> I udgraded to wine 1.1.8 to see if that would help. It still didn't work so I tried to run the install of encarta again. All it did was a repair and didn't give me an option to do a full install/uninstall. Then I found the uninstall windows programs option in wine but the icon for uninstalling encarta had a red X through it and I guess there is a problem with that feature. How else can I do a complete uninstall of encarta to try it from scratch with the new version of wine?

I've personally found wine to be a pain. Its almost not worth it. The 'uninstall' utility doesnt always work. I had a version of skype stay on there till i decided to clean the entire Ubuntu partition. You have to edit the registry that comes with wine somehow, and delete the program from the 'program files' directory (like real windows. probably why its so buggy)

EDIT: you can access the WINE registry by going to WINE's C:windows (/home/*<your_user_name>*/.wine/dosdevices/c:/windows) and rightclicking on 'regedit.exe' and select 'Wine Windows Program Loader'

And if you're farmiliar with the registry, id be extremely careful not to damage it since its one of the many places that can damage the entire Wine system (not Ubuntu)

---

### Post by starcannon on 2008-11-12
+1 to virtualization, I like Virtual Box for that sort of thing:
[http://www.virtualbox.org/](http://www.virtualbox.org/)

That said, and while I'm not a wine officianado, I have had decent success using wine-doors to install the occasional piece of software; your mileage may vary.
[http://www.wine-doors.org/wordpress/](http://www.wine-doors.org/wordpress/)

GL and have fun.

---

### Post by Rubicon421 on 2008-11-12
How do you install virtual box? I downloaded the deb and it said it installed but I don't see it in the applications or system menu.

---

### Post by starcannon on 2008-11-12
Applications>System Tools>Virtual Box

I have noted sometimes the menu's don't update immediately. If it still isn't showing up then restart x with Ctrl+Alt+Backspace or reboot the machine, it should then show up in its appropriate menu location.

GL have fun and keep us posted on how your progressing :)

---

### Post by Rubicon421 on 2008-11-12
> **starcannon said:**
> Applications>System Tools>Virtual Box

I have noted sometimes the menu's don't update immediately. If it still isn't showing up then restart x with Ctrl+Alt+Backspace or reboot the machine, it should then show up in its appropriate menu location.

GL have fun and keep us posted on how your progressing :)
OK, I have it installed but I can't get the VM to boot. If I do it w/o a disc it says
  FATAL: could not read from the boot medium
And with a XP install disc in, it boots and tries to start doing a restore on the VM (the window that looks like ur computer booting up starts displaying options to do a restore)

EDIT: The help file says I need qt 4.3.0 or higher and sdl 1.2.7 installed. I have a few files installed that look like they might be the right ones but I found several others in synaptic. Should the right ones be installed by default or is that something you would normally have to add?

---

### Post by starcannon on 2008-11-12
I've never had to manually add anything, the package manager has always taken care of that for me.

I have found that its more reliable to install from an iso than from a cd.

so with the cd in the drive, 

[LIST]
[*]right click its icon on the desktop
[*]choose "copy disk"
[*]Copy disc to: "File Image" from drop down menu
[*]Choose a location that you can easily find.
[*]Click OK
[/LIST]
Now instead of mounting the cd rom with Virtual Box, mount the ISO you just created instead.

I've gotta go for now, but the documentation is pretty good for Vbox, and if you get stuck someone here will help, or I'll help later when I'm back.

GL and keep it fun.

---

### Post by Rubicon421 on 2008-11-12
Cool, thanks for all the help man.
Peace

---

### Post by Rubicon421 on 2008-11-12
Wait, did you mean reattempt installing Encarta with the disc as an iso, or install XP from the VM window with the XP disc as an iso?

---

### Post by starcannon on 2008-11-12
I'm back for a bit.
Reading your last post I think I got lost so first things first, bring me up to speed.

You installed Virtual Box:
Did you successfully install XP to Vbox?
[INDENT]if so then I assume you must be now trying to install Encarta?
[/INDENT]if your trying to install Encarta then please redescribe the problem.

---

### Post by Rubicon421 on 2008-11-12
I have Vbox installed. Then I created a VM for XP (or at least set up the initial settings for it) without using a CD or ISO. When I tried to start the VM it said something about 'could not read from boot medium'. So I changed the settings to boot from CD instead of HD and put in an XP install disc. Then when I started the VM it showed the window of a computer booting up and went into installing windows. I stopped there because I wasn't sure if I was suppose to install another version of XP while inside the VM. I already have a dual boot and have XP taking up HD space on this computer already. I didn't want to install it again as a VM and have two footprints wasting space. I know since I still have XP that I can just keep using encarta in XP but I'm trying to get rid of windows all together and my son really likes this program. It's about the only reason I haven't wiped out windows yet.

---

### Post by crazyness003 on 2008-11-12
> **Kill Vista said:**
> I have Vbox installed. Then I created a VM for XP (or at least set up the initial settings for it) without using a CD or ISO. When I tried to start the VM it said something about 'could not read from boot medium'. So I changed the settings to boot from CD instead of HD and put in an XP install disc. Then when I started the VM it showed the window of a computer booting up and went into installing windows. I stopped there because I wasn't sure if I was suppose to install another version of XP while inside the VM. I already have a dual boot and have XP taking up HD space on this computer already. I didn't want to install it again as a VM and have two footprints wasting space. I know since I still have XP that I can just keep using encarta in XP but I'm trying to get rid of windows all together and my son really likes this program. It's about the only reason I haven't wiped out windows yet.

You can (in theory) use your existing XP partiton in the VM, BUT: There are a lot of hoops, hardware profiles, and weird fstab changes that you have to do. When i tried to do that (see this thread: [http://ubuntuforums.org/showthread.php?t=943103](http://ubuntuforums.org/showthread.php?t=943103)), nothing worked for me (plus i didnt really take it THAT seriously). So, if i were you, and VM was my last chance, just install a new XP in the VM and use that. Rarely will you need to boot back into native XP anyway.
So once the VM XP is installed, you're gonna have no real use for booting XP, unless you're a HardCore gamer.
Then jsut have Ubuntu take over THE WORLD. MWahahaha-ahem. I mean, the HDD.

peace.

PS: VirtualBox OSE (open source edition) does not have support for mounting USB.
VirtualBox PUEL (cant remember what it ment) does, but its not OSS.

---

### Post by starcannon on 2008-11-12
Ah-ha-ah

VM lets you run MS windows in a window on a linux desktop. 
Now that I more fully understand you (sorry you have so much time into this), I would like to point out some bonus features.

I know I grazed an article on how to use a virtual machine with an existing install of windows, I'll dig around, I think this would be the best solution for your situation. As for leaving windows all together, weeeell kinda hard to do if theres some killer app that keeps you stuck there, in this case Encarta. If you want Windows to have a smaller footprint you could quit dual booting, and just install windows to a 10gb VM (can even go down to 8gb for XP I believe). Anyway, I'ma go dig up that article for you.

---

### Post by starcannon on 2008-11-12
Oh sorry Crazyness003, I'll try your post first, see how that link works out.

Here it is! woot!
[http://blarts.wordpress.com/2007/12/06/how-to-run-virtualbox-using-a-physical-partition-using-ubuntu-feisty-fawn/](http://blarts.wordpress.com/2007/12/06/how-to-run-virtualbox-using-a-physical-partition-using-ubuntu-feisty-fawn/)
Okay its written for feisty, but should work the same here on Hardy or Intrepid either one.
I'm curious so I'm gonna try it myself, I'll pop in and let you now how it went or is going.

---

### Post by starcannon on 2008-11-12
Okay I'm making progress, the post that is getting me there is this one:
[http://ph.ubuntuforums.com/showthread.php?t=769883](http://ph.ubuntuforums.com/showthread.php?t=769883)

I don't have it working yet, but shouldn't be long.

---

### Post by Rubicon421 on 2008-11-12
This forum needs more guys like you. Would you be willing to provide a DNA sample for cloning?

---

### Post by Rubicon421 on 2008-11-12
I just read that page you linked. I kinda understand it but it's still more than I am comfortable doing- especially with the warning about damaging you existing Windows OS and only being able to boot it through VM afterwards. Maybe I should just install the VM like normal and once I get the bugs worked out I will delete the old native version of windows.

---

### Post by starcannon on 2008-11-12
I think booting VM in a normal fashion is your best option, even with a bunch of "just because I could" programs I have never filled up a 10gb Virtual Machine. And like you said, once your at home (Virtual Box will speed that process up exponentially) you can quit dual booting.

I have finally gotten my windows partition to boot, but so far not happy with the performance; though I have a feeling I'll fix that, just needs some tuning.

Anyway if you do a standard Vbox setup the only "geeky" thing you'll have to do is set up usb ports, and I'll help you with that, its a nice intro for you to the command line and a couple configuration files.

---

### Post by Rubicon421 on 2008-11-12
OK, so then do I need to continue from where I stopped earlier by mounting the iso as the boot device for the VM and when it starts up, use the VM window to do a 'normal' installation of XP in that window? And will I need a CD key? I have one but the computer I'm doing it on doesn't come with an OEM copy, it's the HP restore disc. The disc I was going to use is OEM but it has a different key, so which disc and which key should I use?

---

### Post by starcannon on 2008-11-13
I'll be back tomorrow 11-13 I can help you set up a standard vm np. Talk to you then, I see you found me on skype.

---

### Post by lykwydchykyn on 2008-11-13
I know you've moved on past using WINE, but I wanted to point out the other WINE alternative that nobody could remember is Cedega.  It's a fork of WINE and is still in active development.  It's not free or open source, though; and it's mostly focussed on gaming.  Website is [www.transgaming.com](www.transgaming.com).

Crossover Office is basically a nice GUI on top of WINE.  I don't know that you really get much more reliable performance out of Crossover than you do from WINE.  Still, Codeweavers employs a lot of WINE developers, so buying their product helps keep WINE development going.

The most reliable results are definitely using a VM.

---

