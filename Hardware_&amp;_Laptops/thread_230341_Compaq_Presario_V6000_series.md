---
title: "Compaq Presario V6000 series"
date: 2006-08-05
forum: Hardware &amp; Laptops
---

### Post by Shadwell on 2006-08-05
I've been trying to get Ubuntu 6.06 AMD64 to run on this laptop, so far there have been a few problems, which I expected given that it's a recent model, so I'm hoping that some people here may be able to help.

For the people that have access to it, the HWDB ID is 88805ef8eaf5ae3040edde3b18f23956 - I'll attach lspci to the post.

Initial boot works but only with acpi=off specified.

Here are the problems...

1. The graphics card (NVidia GeForce GO 6150) does not work with the NVidia driver, the screen goes black and stays that way.

2. The graphics card does work with the Vesa driver, but will only display up to 1024x768, the LCD panel is a widescreen 1280x800, I can't see any way to get that resolution.  I've tried several modelines that other people have posted on various forums, but no luck.

3. Wireless ethernet isn't detected, it's a broadcom though, so I expected that given their reputation.

4. The sound card is detected and listed as NVidia HD audio, however it doesn't actually work.  XMMS complains that it can't access the device, and writing directly to /dev/dsp gives a write error.

Any help would be appreciated, especially with the graphics resolution.

---

### Post by tdwester on 2006-08-05
What broadcom series is it?

---

### Post by Shadwell on 2006-08-06
> **tdwester said:**
> What broadcom series is it?

The PCI vendor/product codes are 14e4:4311 - lspci lists it as
"Broadcom Corporation Dell Wireless 1390 WLAN Mini-PCI Card (rev 01)"

I guess Dell used the same chip in one of their laptops.

The webpage for the bcm43xx driver doesn't list that as a supported model,
but I tried it anyway, and it didn't work.

I've not tried ndiswrapper yet, but as soon as I find some XP64bit drivers
for the card I'll give it a go.

---

### Post by boz on 2006-09-12
I have the Compaq V6000z, with the AMD Sempron 32-bit variety.  I've had no luck so far, but I have a few resources at the University I'm attending.  Someone there might be able to figure it out.  It boots up, but then it freezes at certain points and X-server fails to start, even with the Vesa driver.  I haven't tried booting with acpi=off yet, that might help.  And, of course, the Broadcom card is incompatible as always.

If anyone on my end can help with the video and wireless drivers, I'll be sure to document it and post it here.

---

### Post by -TomcaT- on 2006-09-17
Hiya.  Well, I got one of these about a week or two ago...  Here's what I've been able to find thus far (I've been running ubuntu and fedora core on the box):

1) Graphics drivers for this machine are a way off yet.  There's a bug in the current nvidia drivers which won't be fixed until the 1-0.9xx series driver.  This is from a thread in the nv forums, so the bad news is 3D is out until that version is released.  

2) On a positive note though, the xorg nv driver works properly with the machine and you can get proper widescreen support.  Just change the driver line to nv from vesa in the xorg config and you should be fine (this works on fedora, I haven't tested under ubuntu yet, but should be fine).

3) That's about where I got on the wireless.  I opened up the mahcine and wrote down the broadcom chip ID and googled it back to the 1390 as well.

4) I can't get sound working either...  It's detected, but not working.  Grumble...  I'm going to poke around on the nvidia forums some more.


There's several laptop models running around with this hardware configuration, so I'm hoping more attention will be paid to this hardware set in the near future.  Hope the nv driver works out for you at least.

-TomcaT-

Side note:  I'm running the v6000z series (AMD) model.

---

### Post by -TomcaT- on 2006-09-27
Grpahics driver update....  there is a beta release for the gfx drivers from nvidia:  [http://www.nvnews.net/vbulletin/showthread.php?t=77021](http://www.nvnews.net/vbulletin/showthread.php?t=77021)

Install doesn't work properly on fedora, but ubuntu might be fine (FC and nvidia installers never seem to get along well...)

I'm working on ndis wrappers for the wireless, so when I get that working, I'll post here.

-TomcaT-

---

### Post by -TomcaT- on 2006-09-28
Oi...  So, sound, wireless, and other things are now working.  First of all, setting acpi=off on this laptop will prevent a huge amount of things from working right, so find a way aorund it.  Try playing with the various acpi flags (google them).  As a side note, my machine will boot w/o themif rhgb is disabled (again, I'm running fedora, so if you can just get ubuntu to boot in a standard text mode, it might help...)  

These are all running in x86_64 kernel...

So, sound support:  If acpi=off is set, it will not work.  Oterhwise it should be fine.  I think running with acpi=noirq might work with sound ( alot of things started working, like power management, etc), so give this a shot.  My laptop finnally booted w/o the acpi flag set (rhgb turned off), and that's when it finally went up.

Wireless support:  This was done with ndiswrapper (see ndiswrapper on sourceforge).  You will need a (very) recent version of ndiswrapper as well as the correct driver set for your card.  In my case, finding the 64bit driver with support for this thing was a nightmare (4311 broadcom).  In any case, I found a complete driver set that was packaged by compaq.  It was found on [www.station-drivers.com](www.station-drivers.com) (use wine to extract the contents of the exe  look for broadcom-wifi-4.40.exe).  It's a huge DL, but it has support for 64 and 32bit w/ support for a lot of the broadcom cards).  This will not work without acpi support fully up, so you can't use acpi=noirq or the driver will fail to load properly.  Check dmesg output to see if the driver loaded properly.

If you need exact steps spelled out, let me know.  Most of the stuff is worth digging into, so spend a good few hours on google and you'll learn some things.  For those not familiar with wirelss on linux, Use the "iwlist scanning" to harvest network info (that's on FC anyway)...

Folks will want to chime in with distro specific info here though...

-TomcaT-

---

### Post by -TomcaT- on 2006-09-28
Well, the "I can't boot" problem is still present when trying to boot w/o ACPI settings...  Somehow my laptop must have gotten into an odd state where it'd boot properly last night (I rebooted several times so maybe the difference between last night and today is the cold boot...)

In any case, I'll work on figuring out what conditions will allowed the machine to work, but this is the first time I've seen it (or heard of it) up w/ sound and all...

-TomcaT-

---

### Post by -TomcaT- on 2006-09-28
So, today with many attempts, I got the machine to boot successfully once, and only once...  There's some kind of weir race condition that just deadlocks everyhing, and I'm not seeing anyhing in /var/log/messages even when running verbose...  So, it looks like it's a timing issue, although I've no clue how to work around it...  Anyone have an idea about mucking with bios setttings on this machine?  The default menus are, well, devoid of any meaningful options...  Any ideas?

-TomcaT-

---

### Post by -TomcaT- on 2006-09-29
Ok, I can get the machine to boot fairly regularly (i.e. not hang) by doing the following:

- disable the rhgb setting (graphical boot).   Text boot seems to crash less, so it might be worthwhile to see if ubuntu can do the same.

- add the following kernel parameter to grub:  "pci=assign-bus"  I also added "verbose" to see if any errors were being logged that would lend a clue as to what was going on.

- Switch back to vesa drivers for the GFX.  A post on a different forum (nvnews I think) said that for some reason the memory being reserved for the gfx card out of main system mem was being accessed which was a contributing factor of the crashes (which would explain the crashes during X initialization).

Leaving ACPI on, this will usually boot up for me (I do have ndis wrappers installed), so the machine boots up into a wireless ready box.  This is _not_ a solution to the issue, but it is a work around.  I think there's two factors here, one being the nv driver and two either a BIOS or kernel bug contributing to the problem.  I'm not smart enough to track it down though :)  But at least there's a work around...

-TomcaT-

---

### Post by guyesinho on 2006-09-29
Hi there, I was reading all the thread and it seems to me that you are suffering a lot.
I have a pavillion dv6040us that has the same configuration, and I installed Ubuntu AMD64 painlessly, the only thing you have to do is to boot the live cd with the noapic option, pay attention because it is easy to get confused with this options, acpi is not apic... If you use the noapic funtion, you'll get everything working.
Only a few things I had to tweak around, the information to do it was found completely here in the forums.
For example, the synaptics touchpad was a nightmare, but if you download the xfree68 driver, and instead of installing it you extract it, you cqn replace the xorg driver files with the ones of the xfree86 and it will start to work like a charm. The problem is a issue with the version 0.14.3 and amd64, but if you install xfree86-synaptics-driver, it will uninstall the virtual package ubuntu-desktop, and that is not recommended for future upgrades, but if you do as I wrote, in the future, the xorg-synaptics-driver will naturelly upgrade and so solving the problem without getting out the package management system.

For the wireless, just compile the ndiswrapper stable version, 1.23, following the instruction in the wireless suppot section.

Well, I hope I've been of any help to you and I wish you good luck!!!
P.D. Excese any errors, my english isn't very good, it's not my nature language.

---

### Post by boz on 2006-09-29
Thanks, the noapic boot option worked for me.  I can finally start using a real OS on my laptop.  :-D

---

### Post by cristianm on 2006-11-08
Hello, I have been doing all that you said about ndiswrapper but I can't get it to work.

I get driver and hardware foun but when i type in IWCONFIG none wireless cards appear.

Does anyone have a clue o can someone give me the commands to type.

Thanks

---

### Post by dragonlor20 on 2006-11-27
> **cristianm said:**
> Hello, I have been doing all that you said about ndiswrapper but I can't get it to work.

I get driver and hardware foun but when i type in IWCONFIG none wireless cards appear.

Does anyone have a clue o can someone give me the commands to type.

Thanks

Ok, the BROADCOM drivers suck. Period. On my Compaq V2000 laptop it took me 2 weeks to set up my wireless driver on Edgy. So here is what worked for me and what I am going to recommend to you:

Downgrade to Dapper. This is the easiest way to have a working wireless. In dapper, you need only install ndiswrapper and load up the correct driver and you have wireless...

For Edgy... Compile ndiswrapper from source. This sounds like a terrible solution since the chances of ndiswrapper from source working for you when ndiswrapper is already installed seem to be low. The difference seems to be the difference between wearing a glove and a mitten though... The compilation from source is literally what made it work for me. Im talking the wireless light... everything.

If that doesn't work for you, then try using fwcutter. This will use the native bcm34xx driver and install the firmware for your card... This wont' work 100% in most computers... It will make that wireless light come on and then slowly you will get a feed of internet, but i know that for me it was a start....

---

### Post by jaa6c6 on 2006-12-17
Has anyone had trouble with usb disk drives?  Like flash drives?  I can't get them to work I have a presario v6000 and I'm using the noapic option to get it to boot.

---

### Post by jaa6c6 on 2006-12-17
Hey you might want to see my error.
Also the usb disk I'm using works on my other linux computers running ubuntu edgy.

Heres the pertinent information from when I run dmesg after connecting the device:

[17180947.796000] usb 2-6: new high speed USB device using ehci_hcd and address 2
[17180948.796000] ehci_hcd 0000:00:0b.1: Unlink after no-IRQ?  Controller is probably using the wrong IRQ.
[17180959.340000] usb 2-6: device not accepting address 2, error -110
[17180959.452000] usb 2-6: new high speed USB device using ehci_hcd and address 3
[17180970.996000] usb 2-6: device not accepting address 3, error -110
[17180971.112000] usb 2-6: new high speed USB device using ehci_hcd and address 4
[17180981.540000] usb 2-6: device not accepting address 4, error -110
[17180981.652000] usb 2-6: new high speed USB device using ehci_hcd and address 5
[17180992.076000] usb 2-6: device not accepting address 5, error -110

thanks for any help

---

### Post by jcaveman on 2006-12-18
I have an HP Pavilion dv6119 that had this problem.  Its essentially the same machine as the V6000.  I had to to add  irqpoll noirqdebug in addition to noapic to the kernel parameters to make the usb work correctly.

---

### Post by soapytheclown on 2007-01-05
have there been any developments with support for the v6000 serise, my old man just got me a v6311eu, and whilst the alternate install cd works and about one in twenty times i can acuallly get into the x server the laptop is useless as a linux machine and to be honest whilst im coping with windows i do miss my beryl anf kiba dock etc, i dont partiularly fancy another distro since me my bro and all my "converts" use ubuntu, but i might be forced to at this rate!! 

thanks

---

### Post by jcaveman on 2007-01-05
I dealt with the X-server driver problem by downloading NVidias latest linux driver from their web site and building and installing the new driver.  It works fine.  I had no luck with the proprietary modules included in the repositories.

---

### Post by soapytheclown on 2007-01-05
nothing on getting it to install and boot up properly with most things working yet?? or a i going to have to wait for fiesty :( worst thing is all the computers ive switched to ubuntu have gone flawlessly except the ones i own!! LOL nevermind good learning experience i suppose!!

---

### Post by keflavich on 2007-01-12
Thanks TomcaT and others for posting up all that helpful stuff.... my laptop would be a paperweight by now without your help.

I'm also running Fedora Core 5 on the Presario V6000, and can't get useful resolution, any wireless, or proper sound control (though I believe there's another forum with a lot more help on sound... [http://ubuntuforums.org/showthread.php?t=322817)](http://ubuntuforums.org/showthread.php?t=322817)).

For screen resolution stuff, the NVidia proprietary drivers failed miserably, so I guess I just have to wait?  

For the wireless, ndiswrapper gives me this output (after following TomcaT's instructions):
ndiswrapper -l
installed drivers:
b44win          driver installed (alternate driver: b44)

Which I gather means the hardware was not detected?  How can I use fwcutter?  I have some drivers I downloaded a while ago... bcmwl5.sys from the archive R140746.EXE, I can't remember where I got it... but no luck:
bcm43xx-fwcutter bcmwl5.sys
Sorry, the input file is either wrong or not supported by bcm43xx-fwcutter.
I can't find the MD5sum b89bcf0a25aeb3b47030ac83287f894a :(
Does that mean I'm mis-using fwcutter or just that the file is useless?

I'm also not very familiar with the commands I should be using to find out what/where my hardware is.  
iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

sit0      no wireless extensions.

and of course, that means ifconfig -a only shows me things that don't work.... what can I do to convince my computer to detect my wireless hardware?

As for sound, my sound works, but for some reason "Master" controls the headphone jack and PCM controls everything, but that means I can't have just the headphone jack on and not the speakers, which kind of defeats the purpose.  This is just a minor annoyance, but any ideas?

Last small issue - when I first installed FC5, running gnome, those volume control/mute buttons worked fine, but they don't any more.  I can still map them in the key mapping preferences, but they no longer do anything besides beep annoyingly.  What did I do to kill them?

Thanks,
Adam

---

### Post by soapytheclown on 2007-01-16
hey keflavich,

the guide ive followed for my broadcom card uses ndiswrapper but there are a few extra steps involved in the setup which may be why your ndiswrapper so far hasnt worked,  the howto i followed was this one:-
[https://help.ubuntu.com/community/WifiDocs/Device/Broadcom_BCM4311_rev_01_%28ndiswrapper%29?highlight=%28broadcom%29%7C%284311%29](https://help.ubuntu.com/community/WifiDocs/Device/Broadcom_BCM4311_rev_01_%28ndiswrapper%29?highlight=%28broadcom%29%7C%284311%29)
just to make a note, i tried with the ndiswrapper off the edgy cd and it didn't work, compiled version 1.28 (1.29 didn't work) and it worked great!!

the only version of linux ive had any luck with as far as graphics went was openSuse 10.2 only problem was every few mins wireless would randomly switch off  with the only solution being a reboot oh and beryl worked except emerald didnt which was pretty useles. i tried FC6 which i hated and also had no luck with bar the wireless, i tried mandriva which again i had no luck couldnt even get to boot up, i suppose i should have tried the noapic flag but after installing several versions of linux in a day with no working version i was thoroughly pissed off and couldnt be arsed lol.

Let me know how you guys get on i NEED my laptop as a Linux (pref ubuntu) windows is doing my head in worrying about problems security etc!! :D

---

### Post by keflavich on 2007-01-16
soapy - thanks, it looks like you've tried everything.  I saw that guide, and it's great, except I'm running FC5  and "Step 3 - Prepare the Linux build environment" isn't so easy - in fact, no matter what I do, I can't get ndiswrapper, alsa, or nvidia installers to recognize my kernel source/headers.  Someone elsewhere told me I was downloading kernel-`uname -r`.src.rpm instead of kernel-source-`uname-r`.rpm.  I suppose the best solution would be to switch to ubuntu, but I'm pretty well dug in to FC5 with applications and data I can't remove.

btw, if anyone wants to post a review/more info about the v6000, I think this is a good place: [http://www.linuxquestions.org/hcl/showproduct.php/product/3732](http://www.linuxquestions.org/hcl/showproduct.php/product/3732)

---

### Post by soapytheclown on 2007-01-16
would it not be such a problem to upgrade to fc6 i had no problem with ndiswrapper on fc6 everything as far as wireless went was fine??

---

### Post by keflavich on 2007-01-17
as it turns out, upgrading to FC6 was the solution, and it wasn't as difficult as I'd expected.  Once I did that, everything clicked... though I still haven't figured out the step of connecting my wireless card to the network.  That shouldn't be too tough.  

Thanks for the help,
Adam

---

### Post by vivichrist on 2007-02-08
feisty think is now ready, 2.6.20 kernel seems to work a treat. no kernel parameters necessary after you install nvidia-glx (9631). also bios upgrade to F.27 really worked out well me thinks ... suport for acpi 2.0 and parts of 3.0, still get crashes on wake. this is my only complaint. ndiswrapper, sound etc. all seem to work

compaq presario v60001au

---

### Post by soobash on 2007-02-09
I had tried FC 6 on a compaq presario V6182 ea. It was quite buggy with the screen, wireless, sound etc. I have since installed opensuse 10.2 and all the hardware work fine.

---

### Post by zergberg on 2007-02-11
So is there any consensus on whether or not this laptop works or not with Ubuntu? I'm seeing all sorts of stuff from FC6 to Feisty (I'm willing to use the beta if it works) to works on Edgy to works on Dapper but not Edgy.

Thread is quite confusing.

---

### Post by keflavich on 2007-02-11
it definitely works with FC6 and Edgy, but you have to tweak the GRUB settings with noacpi, and some features (graphics, microphone, network card) are a little difficult to deal with.

---

### Post by vivichrist on 2007-02-12
With my hp compaq presario v6001au, it doesn't seem to like the vesafb module (driver).

um ... yeah i guess it is a bit confusing ... I think its time related alot of the bugs you hear about get fixed in different and newer versions of the kernel and also the kernel more than the distro has more to do with whether this hardware will work or not or kind of ...bla

---

### Post by vivichrist on 2007-02-13
sorry let me expand on my first statement.
whenever ubuntu is in a console (non-X-window/terminal) it seems to have a random chance
of crashing (no responce somtimes text and background change to weird colors ...?). Every time upon booting if the splash screen goes away and you get fsck messages (aka console) disk check gets to ruffly 70% sometimes less and freezes. In this case subsequent boot will retry to fsck ... endless freezing. so then noapic is nessary. To me this is a minor inconvenience. but freezing on resume from sleep, which quite recently stopped happening, was a major pain:( ... I blame a yet to be configured ndiswrapper.

I have a resonably stable system currently. :)

---

### Post by alexohara1 on 2007-02-16
im having difficulties running ubuntu 6.10 on my compaq presario v6000 ive installed it along side windows xp using grub as the loader.... the main ubuntu loader displays and that bar goes left to right a few times then the screen goes blank and nothing happens...any idea on whats going on here...
regards alex

---

### Post by vivichrist on 2007-02-16
I mission was to install nvidia-glx or (if you don't need opengl) nv. but ,and heres the catch, nvidia driver and libs must be 1.0.9xxx to work and in feisty nvidia-glx is version 1.0.9631 which seem to work quite perfectly, even wakes from suspend, but unfortunately not with beryl. so I guess use noapic or if that doesnt work acpi=off kernel parameter (grub ... select type e for edit) in recovery mode to get to a prompt and once you're in startup dselect =>[s]elect  (type / to search + to install _ to remove) etc.

or maybe, at a prompt instead of the above, type:
sudo apt-get install nvidia-glx

required for both:
sudo dpkg-reconfigure xserver-xorg

edgys nvidia-glx is 1.0.8xxx and didn't work for me ... not without a hiccups anyway.

---

### Post by tomwsmf on 2007-02-19
I picked up the v6133cl version of this and had the following

1) installed edgy from iso (32bit ) and got nada on X
2) read these forums and freaked a bit
3) turn off acpi and then installed automatix and bleeder
4) got the latest nvidia drivers (yea so I get -5 stallman points, ill buy him a cheese sandwich as contrition)
5) rebooted without accpi=off .. all grfx worked like a charm, even got beryl going (oi vey enough with the eye candy already)
6) followed the ndiswrapper instructions, worked like a charm
7) still beating head over sound issues...particularly
    a) I can play sounds and all that, but nothing will record or capture thru
        i) mics on the lid
        ii) mic jack
    b)the headphone and mic jacks are dead, nothing works from or to them

both the sound options (HDA NVidia or Generic 14f1 ID 5045)  are equaly helpless in making this work. Audacity cant read any working deivce nor does Sound Recorder capture stuff playing through those apps that do work (sipie, firefox, vlc, etc etc)

Any help on this would garner many karma points 

Danke
-tomhiggins

---

### Post by vivichrist on 2007-02-20
OK sometime soon I shall test this with feisty (alsa 1.0.13)
but I have a hunch it may have somthing to do with edgy having a lesser version of alsa drivers ...

---

### Post by soapytheclown on 2007-02-21
> **vivichrist said:**
> OK sometime soon I shall test this with feisty (alsa 1.0.13)
but I have a hunch it may have somthing to do with edgy having a lesser version of alsa drivers ...

let us know how this goes i tried the first 2 herds and had no luck. 

on another note for those more advanced sabayon linux worked perfectly (almost) out of the box, only needed to do ndiswrapper, beryl etc working straight away, only one issue with the sound, which was the sound on startup would default out of the headphones regardless of if there was anything plugged in, so id have to change the levels everytime i started up. only thing it is gentoo based which is a bloody pain in the arse for the average user as far as i can tell whilst it was fantasically quick and smooth looked great etc doing anything without reading a 1000 page wiki wasn't my idea of ease to use, so i removed it after a week or so.

but yeah with the release of herd 4 i hope things are starting to look up for us, windows is seriously annoying me, luckily i have my desktop in all its glory a few meters away for when its too much :D

---

### Post by vivichrist on 2007-02-22
yep same here.
I wonder if ... well ... conexant HDA vs. intel HDA ...
wonder what the difference is?

---

### Post by ToyBoit on 2007-02-24
Hey Everyone. 

Ive spent a good deal of time getting everything to work on this V6000 and I must say that when its all configured, it runs real smooth. So smooth I just obliterated Vista off the hard drive.  I also learned that different versions of the v6000 come with slightly different versions of the broadcom43xx based card.  On my version after running this command:

"#lspci -v | grep Broadcom"

I learned my card was a different distributor than what all the guids and faqs point to for using with NDIS Wrapper.  This is what it turned out to be: 

"Broadcom Corporation Dell Wireless 1390 WLAN Mini-PCI Card (rev 01)"

Though it is broadcom, the correct driver that was needed for this particular built-in card was the 64 bit driver for the 1390 from Dell.com. So if you get the same kind of card as I did, then you need to surf over to Dell.com and go into their support module to find the 32bit or 64bit drivers for the Dell 1390.  Install and compile the latest version of ndiswrapper and plug in the driver. You'll see the blue light fire up with much joy. Case in point, not all bcmwl5.inf files are the same as they can be particular to a different distributor (in this case, Dell)

Likewise, if you use the same command and get a different distributor like Gateway or Asus. Then browse on over to their support site and get the driver from there.  Again, pop it in with the latest compiled ndiswrapper and you're good to go.

As for nVidia. It works very well if you install your kernel-source from apt-get and run the driver installer downloaded from nvidias site.  Manually change "nv" in xorg.conf to "nvidia", restart.  Very smooth.

Hope it helps.

---

### Post by keflavich on 2007-02-24
As far as I know, all the v6000's do come with the same Broadcom 4311, but if you've updated your pciids it will show up as the Dell 1390, if you haven't, it's Broadcom unknown or something along those lines.

If you don't want to go searching for the drivers, look here: [http://ndiswrapper.sourceforge.net/mediawiki/index.php/List](http://ndiswrapper.sourceforge.net/mediawiki/index.php/List)
or try either of: 
[ftp://ftp.hp.com/pub/softpaq/sp34001-34500/sp34152.exe](ftp://ftp.hp.com/pub/softpaq/sp34001-34500/sp34152.exe)
[http://ftp.us.dell.com/network/R115321.EXE](http://ftp.us.dell.com/network/R115321.EXE)

I'm curious, though, which driver did you have such success with?  Was it the R115321 or sp34152?  I've had varying success with both, and as far as I can tell the only difference is that R115321 comes with a lot of extra crap in the download (50MB vs 5MB).

Adam

---

### Post by ToyBoit on 2007-02-24
I had success with this driver: R140747.EXE

It can be found at this location (64 bit):  

[http://support.us.dell.com/support/downloads/download.aspx?c=us&cs=19&l=en&s=dhs&releaseid=R140747&formatcnt=1&libid=0&fileid=187881](http://support.us.dell.com/support/downloads/download.aspx?c=us&cs=19&l=en&s=dhs&releaseid=R140747&formatcnt=1&libid=0&fileid=187881)

---

### Post by PsychoKlown on 2007-02-26
Hey TomcaT I was wondering if you could be a little more specific on how to get the wireless to work.

I installed Ubuntu within a few hours of getting my laptop. The main issue I'm having is getting my wireless to work. Maybe getting widescreen support, but thats not a biggie.

If you wanna point me towards some place, I don't mind learning on my own, but I'm at a loss as to how to get started.

---

### Post by Hashi on 2007-02-27
Hi, everyone. I'd like to thank everyone for their input re the V6000. Needless to say, I am having the same problems, and still haven't solved them. There seems to be a whole lot of good ideas in this thread, which individually fix a subset of the main problem, that is getting edgy (or feisty) to run on this machine.
  I'm a relative n00b, although I have edgy running perfectly on the desktop machine I am writing this on. I will never, never, go back to windows, I see no reason. I _really_ want to flick windows on the laptop too.
  Anyway, what I was wondering was, is there anyone out there who could write a coherent 'how-to' detailing all of the steps necessary to get edgy running on the V6000? I mean completely, wireless, gfx, sound, touchpad etc. I personally don't have enough know how to get all this stuff going. I know it's a big ask, but I (and a lot of other people by the looks of it) would be eternally grateful.
  Many thanks.
Hashi

---

### Post by vivichrist on 2007-02-27
mmmmm ... good idea but this will change with development of the kernel. I usto have alot of problems but those have now mostly gone (my major problem was with suspend and powersaving. although this could still get better). I think the most essential info was just the kernel parameters i.e. noapic acpi=off etc. although pointing people to resources that perhaps explain things like the linux boot process. loading of modules, x-window-system configuration etc. the problem with this also is that info becomes obsolete very quickly with linux, bugs get fixed very fast, especially when you send detailed bug reports.
 just being able to get to a prompt or gui and then from there I just used general linux know-how ... and I'm no expert. as I solve One problem it gives me understanding to solve others.
linux is becoming simpler to use ... that in its self can be confusing. because most of the oldskoolers do things the hard way, but hard way, I find, is more educational. but my typing ain't that great and I'm lazy so I tend to look to easier less taxing solutions. linux is definitely a less taxing solution. once you get stuff to work it just keep working.

---

### Post by Hashi on 2007-02-28
I understand what you are getting at. However, I would sacrifice my firstborn (joking, joking) to get past GO and collect $200. For instance, I have just spent 4 hours mucking around, just to get nvidia drivers working. No luck, BTW, running feisty herd 4. See, it wants to download kernel sources, and guess what, my wireless doesn't work, as many here have found. I have not been able to get that going, so I can't download sources, so...... well, you get the picture. 
I'm kinda stuck, and tired, so I'm going to bed to cry a lot. :(

---

### Post by soapytheclown on 2007-02-28
has anyone else had power management issues, like the battery indicator thing saying you have about 35 hours of batery life lef one second then the next saying the battery is in a critical condition and needs a power outlet etc??

---

### Post by vivichrist on 2007-03-01
Ok yes I got ndiswrapper to work with the sp33008.exe drivers from the hp website ... got the  blue light and started picking up DHCP from random networks in the neighbourhood ... which was a bit annoying so I use ethernet now ... just followed the instructions pointed to earlier in this forum and hay presto.

and yes I have had weired messages from the battery icon from what I have read this is a common problem.

---

### Post by Hashi on 2007-03-02
Hi again
  I am running kubuntu feisty herd 4 amd64, impressed with speed and general operation. Should mention, running edgy on my desktop (this is my laptop) for ages, full on beryl, absolutely fantastic, hence wanting to ditch windows on the laptop. BUT, and it's a big BUT, I can't get some things working, and believe me, I have tried. As with most of the posts here, I can't get full res on my screen, even though I have installed latest nvidia drivers. Also wireless, but that can wait.
  What is the deal please, if anyone knows, when I have installed nVidia driver, and it is in xorg.conf, and the max resolution is set to 1280x800, WHY, WHY, does the resolution not go higher than 1024x768? This is so annoying, and I can't find any reason? Do I have to sacrifice a virgin to the great god nvidia or what? Does anybody know how to get max res?
Thanks,
Hashi

---

### Post by vivichrist on 2007-03-02
have you tried:

sudo dpkg-reconfigure xserver-xorg

and ... exacty what have you tried :confused:

---

### Post by Hashi on 2007-03-02
Vivichrist,
  Sorry to get all 'tired and emotional', it just seems that I've tried everything, with no luck. Here is what I've tried:
  1) Used the Beryl 123 setup script, haven't got the URL handy, but it is in the Beryl forums. Reason for doing this, it also installs nvidia driver. All went well. I get the groovy nvidia splash when I boot up, so I thought all was OK. Went to System Settings -> Monitor and Display (kbuntu), max res is 1024x768, which is wrong. Hardware tab shows me that the driver is nv. This makes no sense. I checked xorg.conf. Made sure that driver was nvidia, and that 1280x800 was the first res in each selection. I can post the relevant part if required. What I don't get is how the applet thinks I'm using nv?? Where does it get that info from? I would have thought xorg.conf, but hey, it can't be.
  2) Wireless, arrrgghhh! I followed a how to pointed to in this forum, word for word. As with the video, everything went well, using ndiswrapper and the appropriate hp driver. Blue light comes on! Fantastic! F me, the thing doesn't work. Don't know why (obviously), all indications are that it IS working, except for the slight problem that it is not. Again, I can post relevant bits of config files if required.
Any help greatly appreciated.
Hashi

---

### Post by vivichrist on 2007-03-03
Ok my setup is running 1280x800 50Hz. In your xorg.conf if the vertical and horizontal sync rates are wrong for that resolution  then x will reject it ... possibility number one.
if your frame buffer is to small ...
if ... bla bla (check your /var/log/xorg.0.log or system=>administration=>system log ... gnome) then perhaps x is reverting to nv as a backup plan.

please give me more info ... you're not helping people to help you.:KS

---

### Post by Hashi on 2007-03-03
Right, I get the drift. I am really trying to get this stuff working, and if I haven't been clear I sincerely apologise. I have a fair idea of what I'm doing. I have run linux on various computers for, oh\, about 5 years. I have not had many problems.
This laptop is different. Nothing seems to work as expected. I blame the laptop, not ubuntu. 
Anyway, here is what I've done. Installed nvidia driver (many times, via various methods). According to all logic, it should be working. I get the nvida splash when I logon. My xorg.conf follows -
----------------------------------------------------------------------------------------------------------------------------
Section "Device"
	Identifier	"Generic Video Card"
	Driver		"nvidia"
	BusID		"PCI:0:5:0"
	Option		"UseFBDev"		"true"
EndSection


Section "Screen"
	Identifier	"Default Screen"
	Device		"Generic Video Card"
	Monitor		"Generic Monitor"
	DefaultDepth	24
	SubSection "Display"
		Depth		1
		Modes		"1280x800" "1024x768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		4
		Modes		"1280x800" "1024x768" "800x600" "640x480"
	EndSubSection

	SubSection "Display"
		Depth		8
		Modes		"1280x800" "1024x768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		15
		Modes		"1280x800" "1024x768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		16
		Modes		"1280x800" "1024x768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		24
		Modes		"1280x800" "1024x768" "800x600" "640x480"
	EndSubSection
EndSection

Section "ServerLayout"
	Identifier	"Default Layout"
	Screen		"Default Screen"
	InputDevice	"Generic Keyboard"
	InputDevice	"Configured Mouse"
	InputDevice     "stylus" "SendCoreEvents"
	InputDevice     "cursor" "SendCoreEvents"
	InputDevice     "eraser" "SendCoreEvents"
	InputDevice	"Synaptics Touchpad"
EndSection

Section "DRI"
	Mode	0666
EndSection

------------------------------------------------------------------------------------------------------

It seems OK to me, but I could be missing something? The thing that gets me is that the screen setting applet only allows me to go to 1024x768, AND.... the driver is specified as nv, not nvidia! I really don't get it, if xorg.conf shows nvidia, and when I boot the nvidia splash comes up, why, oh why, can;t I use the full resolution?
Ta
Hashi

PS still got wireless issues (doesn't work) but I'll treat this separately.

---

### Post by Hashi on 2007-03-03
Sorry, forgot this bit of xorg.conf:


Section "Monitor"
	Identifier	"Generic Monitor"
	Option		 "DPMS"
	HorizSync	28-
50
	VertRefresh	43-75
EndSection


Don't know if it's important, seems OK to me.
Hashi

---

### Post by vivichrist on 2007-03-03
Ok what about Xorg.0.log thats the biggy

oh and my sync rates are H 28-64 V 43-60

also 

      Option "UseFBDev" "true" 

is instead:

       VideoRam 65536

I don't use kernel frame buffer its slow and chunky
although this set video ram to 64MB you coud use 128MB
1024 * 128 ... bla

---

### Post by Hashi on 2007-03-03
OK, it's working now. I didn't actually change anything, well, there was a line break in the refresh rate line, I fixed that, ctrl+alt+backspace and all's well. I can't see that what I did could have any effect, but there you go.  Thanks for the help everyone, I couldn't have done this without this forum! Beryl works, but any minimised app cannot be brought back, ie it is stuck at minimised. I understand that this is common for my combination of hardware+op system+software, so I'm going to let it go for now.

Now, wireless. This is my LAST problem, I promise! I mentioned previously I had installed the driver via ndiswrapper? Well, heres the thing. The blue light is on (yay), iwconfig shows wlan0 is set up correctly, with the correct ESSID, but it doesn't actually work. Do I have to do something to tell ubuntu I'm using the wireless instead of eth0? I guess that is the issue, but I don't know enough about networking to guess where to go.
Thanks again, Hashi.

---

### Post by vivichrist on 2007-03-03
yay:)   ... I always assumed white space was ignored ... so maybe not in that context.
I know that with some config files you need to leave a line-break before EOF, but thats a new one on me.

from your posts it is hard to tell what level you are on.
I'm sorry if a sounded patronising.

---

### Post by Znix on 2007-03-05
Did you try :
dhcpclient wlan0

or dhcpclient (whatever your wireless card id became)
after setting the card with iwconfig, if you need dhcp use that, if not
use ifconfig.

Hope that helps.

Znix

---

### Post by -TomcaT- on 2007-03-05
Sorry, it's been a long while since I last checked here...  I'm running FC5 (x86_64), current kernel version is 2.6.18-1.2257.fc5.  

Some notes:  With some kernel updates, I've seen the odd behavior with USB disks (not mounting properly), although the issues are resolved with later updates from Fedora, so chances are a small bug somewhere that was introduced by an update and corrected later (I'm currently not having any problems with USB drives).

As noted previously, nv drivers prior to the 9625 release will not work with this laptop, or others with a simialr hardware configuration.  I suggest getting the latest from nvidia and performing the install from there if you have one of these.

For wireless, I'm currently running ndiswrapper 1.23 which will allow wireless access.  Note that if you update the kernel, you will need to re-install the ndiswrapper kernel module (although you won't need to re-install the windows driver using the ndiswrapper utilities), similar to reinstalling nvidia drivers on each update (thus the problem with using closed drivers).  I'll applolgize now in that I don't rememebr the exact location of the driver download for the card, although there are links to the HP driver packages in this thread IIRC.  The driver name is bcmwl5.  After installing ndiswapper and installing the windows driver, you should be able to do "ndiswapper -l":

[root@v6000z ~]# ndiswrapper -l
Installed drivers:
bcmwl5          driver installed, hardware present

If all is working right (hardware present), you can then use the network device settings to get the card configured (wireless network name, encryption settings, etc).

Cliffs:
- This machine needs the "noapic" kernel option set.  
- Suspend works fine usually with the kernel listed.
- ndiswrapper is needed for wireless (make sure you get the correct version of the windows driver for this card!)
- I have not done any bios updates to the machine.

---

### Post by -TomcaT- on 2007-03-08
Quick update:

- Sound:  headphone jack works properly on the 2.6.19-1.2288.2.1.fc5 kernel, so the alsa patch shouldn't be needed.

- Latest stable ndiswrapper works with this kernel for wireless support.  Driver file to look for is the HP support package.  The support file should be something along the lines of: SP33011A if you look for the file on HP's support site for this laptop (make sure you get the correct driver version for 64bit or 32bit).

Good luck all :)

-TomcaT-

---

### Post by Hashi on 2007-03-08
Hi again,
  A quick one. What _real_ advantage is there in running the 64 bit kernel as opposed to 32 bit on this machine?
  I mean, I know it's groovy and all, but I think I would have a lot less trouble getting everything to work with the 32 bit version, not to mention that not all apps are available as 64 bit.
  Any opinions greatly appreciated.

---

### Post by Levitation on 2007-03-09
Hey I want to thank you guys! 

I just got a Compaq v6210us as a replacement from HP. At first I was seduced by the Vista flash, but after Windows Media Player failed to start (an HP support could not help after 3 attempts) AND I got the dreaded "Blue Screen (Insufficient memory-Shutdown)"...

Well I tried: Ubuntu 6.06 (64-bit), 5.10 and Kubuntu 6.06 (64-bit) but like you it hung up midway. 

So now I will try the "noapic nolapic" and wend my way through the other fixes. I am pretty much a newbie (installed Ubuntu on my old P2 Toshiba laptop and managed to get the wifi working), so I am sure I'll be back with Q's.

Peace to you,
Lev

---

### Post by Levitation on 2007-03-09
Try this link:
[http://www.linux-on-laptops.com/compaq.html](http://www.linux-on-laptops.com/compaq.html)

Find your model and there is a step by step setup guide. There was an impressive list of every make and model.

It may not be with Ubuntu...it may be Debian, etc.

---

### Post by vivichrist on 2007-03-15
Ok there is a new kernel 2.6.20-10.6 first it says something about bios bug on the very first screen, before the ubuntu logo and bar, and then just stops when loading mannul drivers and kernel modules even with noapic so ... have to use 2.6.20-9.6 for now ... any clues?

---

### Post by vivichrist on 2007-03-18
however 2.6.20-11 kernel works fine?

---

### Post by salocinbake on 2007-03-23
Hi, I used a different way to get my wireless working.

Maybe easier for someone newer to  Ubuntu.  [This method]("http://www.ubuntuforums.org/showthread.php?t=185174") worked for me. 
I have a presario V6000 (V6110ca to be exact) Turion 64. I have a Broadcom 4311.

It works at 11mbps, enough for me.  

For newby out there, make sure to navigate to your desktop, before following the instruction.    > cd /home/*user*/Destop    *user* being your name for log in.

Good luck

Salo

---

### Post by Hashi on 2007-03-24
Hi. I've read all of this thread, and got most things going. There is one thing remaining, however. Has _anybody_ got Beryl working yet? I can install it, and it seems OK, but it does not actually work. I think it might be video memory but I'm really not sure. Anybody had any success? Running feisty alpha 5, v6000au. 
One other thing, wireless seems to work, but it seems to be related to the phase of the moon, or maybe sunspot activity, but it's certainly not reliable. ie, sometimes it just works fine, other times, forget it, no matter what I do. Anybody have similarexperiences?
Thanks, Hashi

---

### Post by vivichrist on 2007-03-27
yes I've had beryl working, some of the settings I had to force or beryl would give me black boxes instead of window's.
but now the current version that I have just bombs a kumara:popcorn:

---

### Post by Hashi on 2007-03-28
Vivichrist,
When you say "force" some of the settings in beryl, do you mean via the beryl manager? 'Cause that's where I change my settings, but they don't work. See, I have another PC running edgy and beryl, and it works beautifully. If I open the emerald theme manager and click on a theme, the changes show up instantly. On this godforsaken laptop, however, clicking on a theme has no effect whatsoever.
I have a plan. I have been using feisty alpha, I just downloaded the beta, so I'll just reinstall everything from scratch I think. Maybe with all the failed attempts to get stuff working I've irretrievably buggered something up.
Hashi
PS What's a kumara?

---

### Post by vivichrist on 2007-03-30
yeah ... the beryl-manager, options like force Nvidia or use COW or whatever.
my beryl just stops responding when loading. I added a third party repository to my software sources and previous versions worked with a liottle tweeking, but now ...:( 
I find it takes up alot of processing resources so I'm not to fussed.

kumara (maori) = sweet potato

---

### Post by Hashi on 2007-03-30
Right. Installed Feisty beta (clean install), installed nvidia drivers, installed beryl. It now sort of works, except all windows are black on black, ie can't really use it. The windows decorations in each theme work correctly, so I don't know what's going on. I'm going to pass on this for now, it may be fixed in the final feisty release, or not, or maybe the beryl team will change something, don't know. I'll just wait until it gets better,
Anyway, thanks for all the help you guys and girls, I have learned a LOT by going through all of this.
Hashi

---

### Post by washu on 2007-03-30
Hello Gnu fans, this will be my very first post to fellow linux users. I started using debian back in 2002 or 2003. Then mandrake & then xandros & then ubuntu. I was planning to use freebsd for programming and for making cartoon with. But the multimedia is to weak at the moment so I paid $70 for mandriva 2007 linux, and paid about $900.+ plus for a v6000z notebook that I ordered from hp web site. Now I really don't want to spend time working on the infrastructure of a unix system but instand work on the Application programming side like with gimp+python blander+python and goom+C , now this link will give a pretty good bit of info on the notebook that I got today, any suggenteds or comment and even complaits are welcomed. 

And thank alot,:guitar: 

[http://www.geocities.com/feglawx75/compaq_presario_v6000z_series.html](http://www.geocities.com/feglawx75/compaq_presario_v6000z_series.html)

---

### Post by washu on 2007-03-31
Well this is a funny moment for me. The mandriva x86_64 with the boot flag apic=off, with no luck. But the free 32-bit mandriva works fine with normal boot...? Weird... 

Am going to start collage again on April 2, and all I want is to have a 64-bit os that can be used for creating 2-d & 3-d cartoons...  I wish that things could be easier so I can get my work done:confused: 

I hear dell might sell linux friendly laptops one day.:popcorn: for now its a wait and see thing.

Man this is alot of work.

But I know that what will be gained well help me have a better future for myself and for my one day business. So I have some :KS  hope.

---

### Post by soapytheclown on 2007-04-03
> **Hashi said:**
> Right. Installed Feisty beta (clean install), installed nvidia drivers, installed beryl. It now sort of works, except all windows are black on black, ie can't really use it. The windows decorations in each theme work correctly, so I don't know what's going on. I'm going to pass on this for now, it may be fixed in the final feisty release, or not, or maybe the beryl team will change something, don't know. I'll just wait until it gets better,
Anyway, thanks for all the help you guys and girls, I have learned a LOT by going through all of this.
Hashi

okay right now im using sabayon linux the latest version 3.3 mini edition and evertihng works stright out of the box, im talking 1280x800 resolution, broadcom 43xx with knetwork manager, touchpad, usb's , nvidia drivers with beryl installed by default, basically everything we all want on our ubuntu boxes. The black on black thing was something that pissed me off alot cause i could only open about 5 windows before it started happening, its basically something to do with the video sharing on the go 6150 and the nvidian drivers, 2 methods to fix:-

1. use xgl
2. in beryl manager, force aigxl and force cow.

up to you which every you like, i used the first for a while before i learnt about the second. i just want to be able to remove everything off my lappy-t and have a pure ubuntu one :( but in the meantime if u cant be arsed to fanny about with all the configureing on ubuntu give the sabayon linux live mini ed a try id definatley recommend its latest release.

---

### Post by vivichrist on 2007-04-18
the latest version of beryl works 
I found out how to stop beryl crashing:
      beryl-manager --no-force-window-manager
then make the only option not auto in beryl-manager menu:
      /advanced beryl options/rendering path/copy

---

### Post by vivichrist on 2007-05-15
Ok I think the way to fix suspend/resume problems is uswsusp package
and forcing the unloading of nvidia module /etc/default/acpi-support

[http://blog.paulbetts.org/index.php/2007/02/11/fixing-software-suspend-hibernate-with-uswsusp-in-ubuntu-feisty-and-edgy/]("http://blog.paulbetts.org/index.php/2007/02/11/fixing-software-suspend-hibernate-with-uswsusp-in-ubuntu-feisty-and-edgy/")

also altered /etc/hibernate/common.conf
     alwaysforce yes
     alwaykill        yes

sounds serious : |

---

### Post by talkout on 2007-05-28
This might be useful. It worked for my BCM4310 UART (rev 01), on my Compaq Presario V6211 AU.
This page lists drivers for a whole lot of other Broadcom chips. [https://help.ubuntu.com/community/HardwareSupportComponentsWirelessNetworkCardsBroadcom?highlight=%28Broadcom%29](https://help.ubuntu.com/community/HardwareSupportComponentsWirelessNetworkCardsBroadcom?highlight=%28Broadcom%29)

NiMaL
---
[www.talkout.tk](www.talkout.tk)

---

### Post by ToNiuSKaS on 2007-07-09
> **vivichrist said:**
> Ok I think the way to fix suspend/resume problems is uswsusp package
and forcing the unloading of nvidia module /etc/default/acpi-support

[http://blog.paulbetts.org/index.php/2007/02/11/fixing-software-suspend-hibernate-with-uswsusp-in-ubuntu-feisty-and-edgy/]("http://blog.paulbetts.org/index.php/2007/02/11/fixing-software-suspend-hibernate-with-uswsusp-in-ubuntu-feisty-and-edgy/")

also altered /etc/hibernate/common.conf
     alwaysforce yes
     alwaykill        yes

sounds serious : |
I've tried it and it doesn't work very well.

---

### Post by vivichrist on 2007-07-09
I'm currently having problems with the new kernel freezing on resume because of some hardware not responding (the ricoh stuff)

I'm going to reverse the previously mentioned and see what happens.

---

### Post by vivichrist on 2007-07-12
Ok my findings are that you need to insure pm-utils package is installed.

find /usr/share/hal/fdi/information/10freedesktop/20-video-quirk-pm-hp.fdi

and add:
...
      <match key="system.hardware.product" contains="V6000">
        <merge key="power_management.quirk.vbemode_restore" type="bool">true</merge>
        <merge key="power_management.quirk.no_fb" type="bool">true</merge>
      </match>
...

that is ... inbetween maybe um "nx6150" and say ... "nc6230"

---

### Post by vivichrist on 2007-07-25
ok maybe its more like this?
...
<match key="system.hardware.product" contains="V6000">
        <merge key="power_management.quirk.s3_bios" type="bool">true</merge>
        <merge key="power_management.quirk.s3_mode" type="bool">true</merge>
        <merge key="power_management.quirk.vbemode_restore" type="bool">true</merge>
        <merge key="power_management.quirk.no_fb" type="bool">true</merge>
</match>
...

---

### Post by keflavich on 2007-08-07
Kernel and Feisty questions for those of you who have stuck with the v6000:

What kernels have you found work with sound and wireless?  I'm running 2.6.17-11-386 on Edgy, but when I upgraded to 2.6.17-12-386 both failed.  I don't think I had to reinstall ndiswrapper the last time I upgraded my kernel, do I have to do that?

How does Feisty perform?  Does it improve performance in any way for this particular machine, i.e. does it allow the headphone jack to function or boot more reliably?

I've been using Edgy on this machine fairly reliably for about 6 months now.  The only persistent problems I've had I've learned to deal with.  They are:
1. Headphone jack doesn't work
2. On boot, often freezes with "PCI: Ignoring BAR0-3 of IDE controller" or similar errors
3. Sometimes the wireless fails and simply requires a reboot.  This usually happens after restoring the computer from a hibernate and trying to switch access points, but it's very rare

Thanks,
Adam

---

### Post by dpw2atox on 2007-08-08
my laptop which is a compaq v6107 actually works fine in general under Feisty as long as i boot with noapic the first time. After that if i install the binary nvidia drivers then i no longer need to use noapic.

I do use my wireless with ndiswrapper and it works pretty well.

My issues are suspend/resume doesnt work properly and i am unable boot in gutsy at all. It hangs on the reading startup files section. So currently i am using gutsy with the feisty kernel.

Anyone have any luck on this?

---

### Post by vivichrist on 2007-08-08
my two previous posts work with gutsy and feisty would appreciate feedback as to whether this works on other v6000's.

this completely fixs suspend resume problems for me although personally I now have feisty amd64 and have to boot noapic and turn off "sync to VBlank" in nvidia-settings and compiz.

the bcm43xx kernel driver with the firmware cutter pkg (downloaded firmware) now work poifectly ... for my v6000 anyway.

viv:)

---

### Post by vivichrist on 2007-08-29
I don't recommend upgrading to gutsy its still really buggy, left over config from thunderbird 1.5 destroy's 2.0.0.6. I can't get suspend/resume happening like in feisty and I had to go back to using noapic boot every time ... and its almost release time

---

### Post by vivichrist on 2007-09-10
Ok all is good now. gutsy will make this particular series of hp compaq laptop quite funtional I believe. still have to use noapic to stop USB spurious irq 7 bug killing my system at boot with amd64 distro. but a small price to pay really.

---

### Post by worldgnat on 2007-10-26
Yes, but have you gotten ACPI working under Gutsy? I just installed it and got it working great with ndiswrapper, noapic and the nvidia drivers, but I can't get it to resume. I tried the xml you posted earlier, but to no avail. It worked once right after I did this: [http://blog.paulbetts.org/index.php/2007/02/11/fixing-software-suspend-hibernate-with-uswsusp-in-ubuntu-feisty-and-edgy/](http://blog.paulbetts.org/index.php/2007/02/11/fixing-software-suspend-hibernate-with-uswsusp-in-ubuntu-feisty-and-edgy/), and then never again.

Edit: Ok, I was dumb. It turns out that the software suspend that comes with the gutsy kernel works just fine on the v6000, and I was trying to get it to run s2ram. Tried pmi action suspend force, and it suspended and resumed right up when told. The scripts on that site change the order of the suspend software (if s2ram exists, use that instead of pmi), so I just changed it. I wouldn't even try the instructions on that site on gutsy, they don't appear to be needed.

---

### Post by worldgnat on 2007-10-27
I was wrong... while it does suspend and resume up to a point, if It's suspended for around an hour, it won't resume. I have to hard reboot, at which point it turns, on, doesn't load any OS, turns off, and then boots normally. I don't understand it at all. What does it mean?

---

### Post by vivichrist on 2007-11-03
I think I had that very same problem for a while but is ok now on either F.38 | F.3A bios.
Updates kept removing my modification but doesn't seem to matter now. I just have the default settings and poifect sus/resume function. but I would say persevere and try different combinations of quirks.

---

### Post by msaelectronics on 2007-11-16
does anyone knows which linux version is compatible with compaq v6000
series of laptops?kindly post a reply soon?

---

### Post by alexohara1 on 2007-11-18
yes if you find out i would be keen too.... i am also having a hell of a problem getting linux to work on this laptop i think it is a nvidia problem and even if i put "apci=off" at start up it still has problems booting and if it does manage to boot it locks on shut down... any help id like to get ubuntu on this laptop

---

### Post by msaelectronics on 2007-11-18
searching for linux version but couldn't find any?please find sth ?

---

### Post by vivichrist on 2007-11-21
No I take it all back gutsy is now (since fresh install) hanging on resume about every 1 in 3 times i've installed pm-utils package, added lines to 20-video-quirk-pm-hp.fdi, switched of sync to vblank. but trying /etc/default/acpi-support POST-VIDEO=false.

by the way I did this all in reverse order from the feisty days, one of these, a combination or all of the above will work ... maybe.

---

### Post by vivichrist on 2007-11-22
Ok it works, if I make a tutorial will people come to the party. as in if this actually works on most hp comcrap v6000's

---

### Post by alexohara1 on 2007-11-29
yes ... im a newbie and a tutorial to do this would be assume

---

### Post by vivichrist on 2007-11-29
note: step 1,2 & 3 are nvidia specific and are also documented [here.]("https://help.ubuntu.com/community/NvidiaLaptopBinaryDriverSuspend")

1. change ACPI configuration 
 In the same terminal type:
```
sudo gedit /etc/default/acpi-support
```
 move the cursor to line 23 or where you find SAVE_VBE_STATE=...
 change ```
SAVE_VBE_STATE=true
``` to ```
SAVE_VBE_STATE=false
```

 then move the cursor to line 29 or where you find POST_VIDEO=...
 change ```
POST_VIDEO=true
``` to ```
POST_VIDEO=false
```

and save.

2. change NVidia settings
 In the same terminal type:
```
nvidia-settings
```
using the interface navigate to X Screen 0 > X Server XVideo 
and untick Sync to VBlank
also navigate to X Screen 0 > OpenGL Settings
and untick the same option.

and quit.

3. change Xorg device settings
 In the same terminal type:
```
sudo gedit /etc/X11/xorg.conf
```

find the device section and insert the line:
```
	Option		"NvAGP"		"1"
```

so as to look something like this:
```
Section "Device"
	Identifier	"nVidia Corporation C51 [Geforce 6150 Go]"
	Driver		"nvidia"
	Busid		"PCI:0:5:0"
	Option		"AddARGBVisuals"	"True"
	Option		"AddARGBGLXVisuals"	"True"
	Option		"NvAGP"		"1"
	Option		"NoLogo"	"True"
EndSection
```

this is my own device section out of my xorg.conf file and is only useful as an ruff example.

4. Install pm-utils
 open a xterminal and type:
```
sudo apt-get install pm-utils
```

5. Add quirks to your Hardware Information
 In the same terminal type:
```
sudo gedit /usr/share/hal/fdi/information/10freedesktop/20-video-quirk-pm--hp.fdi
```
 move the cursor to the start of line 29, or there abouts, just make sure there is a </match> on the line above and a <match ... > on the line with you cursor.
 press enter so as to create a empty line between </match> and <match ... >

 then cut and paste these lines:
```
      <match key="system.hardware.product" contains="V6000">
        <merge key="power_management.quirk.vbemode_restore" type="bool">true</merge>
        <merge key="power_management.quirk.no_fb" type="bool">true</merge>
        <merge key="power_management.quirk.s3_bios" type="bool">true</merge>
        <merge key="power_management.quirk.s3_mode" type="bool">true</merge>
      </match>
```
and save.

note: this will differ with other versions of ubuntu in both where the file is and where you would insert the xml code.

possible other steps are installing xserver-xgl and black listing bcm43xx driver

---

### Post by worldgnat on 2007-12-12
Awesome, it works perfectly. I've only suspended once, but it resumed after around 20 minutes, so it looks like it's going to work. Thanks for taking the time to write that.

---

### Post by Doublec5 on 2007-12-15
Hi, I've got a bit of a weird problem with my Presario, running Feisty. I've also been afflicted with the black screen on boot issue..the strange part is, Ubuntu runs just fine if I use the "startx" command in recovery mode. I'm using the "nv" generic driver. I'm really new to Linux, and although I've tried ideas on this thread and others, I've had no success. Is there some information I can provide to help with a further diagnosis of the problem? Thanks in advance for any help I receive.

---

### Post by vivichrist on 2007-12-18
please explain in more detail

---

### Post by Doublec5 on 2007-12-18
Actually, I've solved it. 
[http://ubuntuforums.org/showthread.php?t=458164](http://ubuntuforums.org/showthread.php?t=458164)
This post in the forums helped immensely, for anybody running into similar problems.

---

### Post by martinquested on 2007-12-30
vivichrist,
your solution has fixed my suspend/hibernate problems - **thank you!**

The reason I stumbled on it at all was that I did the BIOS flash update which HP sent me an "urgent email" telling me to do - and suddenly I got a zero brightness screen when the power mode changed!  After a panicked support call to HP resulting in them offering to take the machine in to fix it, I researched and found what you had written, and somehow that fixed things.  I still don't understand exactly what changed when the BIOS got flashed.  Anyway, it's nice that the power manager now seems to work correctly, and the hibernate and suspend too.

The only **problem** is that the **fn+F7** and **fn+F8** keyboard brightness controls no longer work.  Is this something that the BIOS update has altered, or is it a result of implementing your solution?  Or both?  Or neither?

Sorry for asking a nooby question, when I really ought not to be a noob any more.

All help very gratefully received! :)

Martin

---

### Post by vivichrist on 2007-12-30
um yeah you are right, I don't really use those controls and didn't notice. I think gnome has taken over that functionality and maybe has it's own shortcut keys.

---

### Post by martinquested on 2007-12-31
I see.  I'm using Kubuntu, actually, but it's probably the same thing.

What is weird is that I seem to have lost this capacity (but gained the ability to alter my screen brightness right down to zero) not with a Kubuntu update, but with a new BIOS (or possibly, by fixing the hibernate/suspend modes).

Anyone else have any tips?  If there is a key combo I can use to instantly adjust the screen brightness that would be good too!

---

### Post by wvstephens on 2008-01-17
I need help I have 7.10 running great, full res everything.
The only issue I am having is I do not have any sound.

 I have a compaq presario v6205NR
AMD Turion 64
Conexant audio device

If someone can point me in the right direction I would appreciate it. right now I have alsa and I have tried every tutorial I could find with no luck. 

Thanks in advance.

---

### Post by vivichrist on 2008-02-05
sudo modprobe snd-hda-intel

?

---

### Post by MOkAONE on 2008-03-14
im running into 1 problem (so far). i cant seem to connect to my wireless network. i can connect to it wired, but not wireless. any suggestions?

i also tried using my neighbors "linksys" network, since its not WEP encrypted and still nothing.

---

### Post by martinquested on 2008-03-14
Wireless is a headache on this machine, unfortunately.

I have finally got a decent level of stability by using wicd (google it and then add it to your repositories) instead of network manager.  But there are still ways to break it completely, which I don't fully understand...  (Sometimes it just fails to register using dhcp - in these instances it's best just to force an IP address and use global DNS servers like 208.67.222.222 and 208.67.220.220.)

One little foible that it has is that if you have a WEP passphrase you should try entering it as both a hex and an ascii key, whatever you think it is.  (Or maybe that's my own stupidity - either way, it made things work very suddenly.)

Hope that helps you.

---

### Post by Davros7 on 2008-06-01
Compac Presario V6000 Running Ubuntu Heron

**Problem**
I had heaps of trouble setting connecting to my wive's wireless network at home. 

**Symptoms**
Wireless network not seen.  
Wireless network seen but unable to connect regardless of network key combination entered Hex/ASCII.  

**Solution**
Install Heron.
Connect to Internet (wired) to get all the latest updates.
But I installed WICD and it worked immediately, as per the instructions above. I entered the network key as Hex. 

**Findings**
You can spend a lot of time trying various combinations of network phrases and security settings using the other network tools.  Obviously there are many red-herrings here.  These can be doubly annoying if you are connecting to an Apple wireless network.

---

### Post by Davros7 on 2008-06-01
Apple OS X Leopard Apple Network Using Airport Hex WEP Network Password

**Problem**
Finding the WEP Hex network key for Apple Airports.  To use for any none-apple computer to connect to an apple network.

**Solution**
Browse to your [Airport Utility] with Finder.
Select the appropriate Airport.
In the main menu bar select the Base Station drop down menu.
Select Equivalent Network Password.
A Dialog box will appear, on this dialog a 10 Hex digit code will appear.
This ten digit hex code is what you need to connect to your apple network with none-apple computers.

**Findings**
You can spend quite sometime searching the Internet to find this setting.  It is not in any of the Apple help systems.  But if you know the concept Equivalent Network Password it makes it really easy to find!

Hopefully, this is useful for someone.

---

### Post by Zulu-Zeffir on 2008-06-25
A good post for the Wireless problems you may be having.
[http://ubuntuforums.org/showthread.php?t=475963]("http://ubuntuforums.org/showthread.php?t=475963")

Works great!

---

### Post by randy013 on 2008-06-30
Howdy Y'all,
I have a AMD Turion 64X2 Compaq V6000au.  Gutsy worked well although the Boadcom pci wlan refused to work.  I had installed the restricted drivers but this was the firmware only.  I got around this by using a Netgear dongle as I ha the driver disk and used the Windows Wireless wrapper to install them.  After downloading the broadcom drivers, Hardy however has found the internal wireless so, all good.  I used the RutilT WLAN Manager to scan for the access point get the SSID and create a profile then the panel based Network Selector to connect to the network .  It was very much trial and error and which action of mine worked I am still not sure.  One piece of advice I can give is that you must give the network tools time to diagnose and work.  Assuming an app has locked can be premature as some take up to 2 mins to return information.  Patience truly is a virtue.  As for the screen resolution, I am currently baffled as the restricted drivers are installed and working(compiz is fully functional) yet the screen resolution screen doesn't give me the correct options (1024x768 max).  This is my mission for today.

---

### Post by randy013 on 2008-06-30
P.S. Even though I am on a 64-bit system a wrapped 32-bit windows driver still works.

---

