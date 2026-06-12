---
title: "Ubuntu 9.04 LiveCD will not go past any options on boot menu:"
date: 2009-04-23
forum: Installation &amp; Upgrades
---

### Post by nbotticelli on 2009-04-23
Hello,

I experience this earlier this week with the Ubuntu 9.04 RC along with the Final that I downloaded today.

On some laptops (I have only tested one desktop with success) I can not get the Ubuntu 9.04 LiveCD to go past any of the boot options even with Safe Graphics mode enabled etc.

I set it to boot off the disc, and then it gives me the language menu choice, I press enter and go to the next step where I have all the options of booting off the live cd or installing etc.

I choose "Boot Ubuntu without making any changes etc" and then the computers will just hang there. I'll hear the cd-rom spin up and down and click and make noises etc but nothing will happen.

I found this odd since previous versions of Ubuntu will boot/install just fine off these same laptops.

So far I have had these results:

Toshiba Portege M400 S3052: 
Jaunty RC: Boot
Jaunty Final: Boot

Rebranded Compal EL81 (Nexlink)
Jaunty RC: Fail
Jaunty Final: Fail

Rebranded Comapl EL80 (Nexlink) (Nvidia Graphics)
Jaunty RC:Fail
Jaunty Final: Unknown

IBM Thinkpad T30
Jaunty RC: Fail
Jaunty Final: Boot after long wait after selecting boot without changes

IBM (Lenovo) Thinkpad R51
Jaunty RC: Unknown
Jaunty Final: Boot

I'm actually quite pleased with the Toshiba tablet so far since most everything works right off the bat even just on a live cd boot. I have bluetooth and tablet functions working which is very nice. Bluetooth never worked before.

The Nexlinks (or Compals) worry me though since they are actually what my computer lab is comprised of, both in my classroom and in my mobile lab. I would like at some point to set these up as dual boots in the nearish future but I'm not sure what to do at this point.

Would it help if I posted lspci for the Compals?

Thank you!

---

### Post by tcfan on 2009-04-23
I had the same problem when I was trying to install using the live CD.  I ended up having to reburn the .iso to a DVD and it worked after that.

---

### Post by stevh0 on 2009-04-23
ill burn it to dvd from the start, thanx for the heads up :)

---

### Post by nbotticelli on 2009-04-23
Odd that a DVD would change things. Any technical reason why this would cause a difference?

I don't have any DVD-r's at the moment but I'll keep looking around to see if there is a reason somewhere.

---

### Post by hesjnet on 2009-04-23
Sometimes the burn isn't all that good. Try to burn the disc with a lower burn speed. That has helped me several times.

You may also want to check that the downloaded iso i not corrupt. A MD5 check is always recommended when installing an OS.:popcorn:

---

### Post by nbotticelli on 2009-04-23
Okay, I will burn at 9x instead of the somewhere around 50x that it normally goes at.

I have always burned at max speed on this tower and never had any issues before but there is always a first time for everything.

---

### Post by nbotticelli on 2009-04-23
Okay, I tried burning a new copy at the slowest possible setting.

I don't believe it is a MD5 issue as it works fine on other computers but I haven't tried so I really don't actually know.

I am trying to "Check disc for defects" but it won't even go there. Just the sound of the optical drive clicking around. Reminds me of an old floppy drive.

Also, I am trying this on multiple of the same model laptop too, so it's not just one with a possible bad drive.

[Edit] 
I also managed to download the final release this morning before most other people starting downloading so I was able to download it very quickly, so I don't think there were many interruptions during download.

---

### Post by netbug2008 on 2009-04-23
I got the same problem when I was trying to install 9.4 to a new VM, I was using the ISO image directly. I think the file is broken even though I can open it in any Virtual Drive or UltraISO software. Can anybody provide a MD5 verify code of a working image file?

---

### Post by Papa.Smurf on 2009-04-23
Glad im not the only one here, iv got the same issue. I guess ill try burning it to DVD.

---

### Post by tcfan on 2009-04-23
Just to chime in since I had success with a DVD instead of a CD.  The checksum was perfect but burning at even 1x for the CD resulted in the freeze at the menu.  Not sure of the exact reason, but I even tried 2 different brands of CDs to see if that would help.  I ended up burning to a blank DVD at 4x and it worked fine.  Not sure why that worked, but it did.

---

### Post by netbug2008 on 2009-04-23
it just does not make any sense.....

---

### Post by sbooder on 2009-04-23
I noticed that the ISO only burned 519mb of the 689mb, this could be that a cd at 700mb may not be large enough, hence the need for a DVD.

---

### Post by netbug2008 on 2009-04-23
I've tried a DVD, not working still, just like using the ISO file. I check the DVD size, it is 698M. This is weird.

---

### Post by kingofpain on 2009-04-23
> **sbooder said:**
> I noticed that the ISO only burned 519mb of the 689mb, this could be that a cd at 700mb may not be large enough, hence the need for a DVD.

If the iso would be too large to fit on the CD, the burning tool would tell you that it cannot burn it.
Plus, why the Ubuntu team would release an iso that doesn't fit on a CD and stil tell you to burn it on a CD?! :lolflag:

---

### Post by netbug2008 on 2009-04-23
I am downloading the image from another source. wish me luck.

---

### Post by Xir on 2009-04-23
I downloaded the iso from two separate sources and mounted them directly into VMware (which is how I had installed Ubuntu in the past) and was unable to get either image to do ANYTHING after I hit "install". Both files were the same size and had the same MD5 hash. No idea what happened.

---

### Post by theducks on 2009-04-23
made 2 coasters using Ubuntu 8.10 (dufault) burning tool, speed was set to lowest (IMHO way 2 fast, would not allow <10x). Data error at END of burn.
copied ISO to pendrive and moved to Windows XP, Nero burnd with no problem.
 :/


Still hangs after menu on Toshiba 1135.
Same CD Boots fine on a Dell D4600

---

### Post by netbug2008 on 2009-04-23
it is ISO file problem. I downloaded a new one with a file size 732,909,568 byes (comparing to the file that was not working, the file size is 726,274,048 byes). It is working now.

---

### Post by jimbob on 2009-04-23
Try running an md5sum on both CD's and see what it comes up with:

mount /dev/scd0 /cdrom     
cd /cdrom
md5sum -c md5sum.txt | grep -v 'OK$'

---

### Post by quotidion on 2009-04-23
I also hung up at the same screen: run without change, install, check cdrom, etc., regardless of what I chose.

But I hadn't been able to find the MD5 hash to check my ISO image before. I finally found the hash for ubuntu-9.04-desktop-i386.iso at 

[https://help.ubuntu.com/community/UbuntuHashes](https://help.ubuntu.com/community/UbuntuHashes)

It is 66fa77789c7b8ff63130e5d5a272d67b but it doesn't match the md5 hash of the download. (Checked using winMd5Sum.)

I don't know if it's newly posted. Right after the download, I got to a page suggesting I check the hash, and giving two pages to get it. Neither page had it.

Seems like a lot of us got defective downloads. At least I hope it's not a defective ISO image that's been posted.

---

### Post by Ort on 2009-04-24
Acer Aspire 5100
AMD Turion 64 MK-36 2.0GHz
4gb mem

7.10 live cd pass
8.04 live cd pass
8.10 live cd pass 32 and 64
9.04 live cd fail 32 and 64: dl 3 dif locations, md5 ck, disk ck, isoburn with all versions, locks up after language.

---

### Post by fallenshadow on 2009-04-24
I am also having this problem... its really annoying. I don't know whats wrong as the iso works fine in virtualbox. Disk burning errors has to be the source of this problem. :(

---

### Post by mohtasham1983 on 2009-04-24
I just downloaded the ISO file from bittorrent. Checked the md5 checksum and it's identical to that of ubuntu website. 

Burned the ISO file on a CD using the following command:

[PHP]wodim -v dev=/dev/cdrw ubuntu-9.04-desktop-i386.iso[/PHP]

After selecting the language it froze as you mentioned.

Tried to burn it on a Flash drive using the following command:
[PHP] dd bs=8M if=ubuntu-9.04-desktop-i386.iso of=/dev/sdb1 [/PHP]

After booting the computer from USB drive got the Error 17 from grub. 

I don't have another blank CD or a DVD right now. I'm downloading another ISO from some Russian server to see if that one works. 

This is a huge drawback for ubuntu, if it's targeting new users.

---

### Post by mohtasham1983 on 2009-04-24
Basically, I tried to open my CD using the package manager on Ubuntu 8.10 and synaptic gave me the following error:

```

W: Skipping non-exisiting file /media/cdrom0/dists/jaunty/main/binary-i386/Packages
W: Hash mismatch for: main/binary-i386/Packages.gz
W: Skipping non-exisiting file /media/cdrom0/dists/jaunty/restricted/binary-i386/Packages

```

I can simply upgrade my computer, but I want to format my entire hard disk to ext4. I know it's possible to format your ext3 partition to ext4 without formatting it, but you need to unmount that volume before formatting it. I don't know how to unmount my root partition on my laptop.

Anyways, I'm trying to get xubuntu now. Maybe it's a better OS for my 5 years old laptop.

---

### Post by elizar on 2009-04-24
I managed to get past this on my Toshiba Satellite 1135) by hitting F6 at the live CD home screen; from the options menu that pops up select the first entry for APCI OFF. For me the boot up into the Live CD continues on until it can't detect my Intel integrated 82852 graphics properly and goes into some low-resolution mode. Not looking like Jaunty is in my future. :(

---

### Post by nbotticelli on 2009-04-24
Wow, this is a real drag. I do have 9.04 installed on my Toshiba Portege M400 and am definitely liking it there but basically this means that the majority of my machines won't be able to run this. 

I'm waiting another month and then plan to install Jaunty on my friend's new Thinkpad T400 as Intrepid at this point doesn't run the best on it. I'm really hoping they fix this upstream somehow.

---

### Post by tchalvakspam on 2009-04-24
Yeah, you definately gotta check the checksum at the end, especially with bittorrent downloaded isos, cause sometimes one little bit of data somewhere is trashed.

---

### Post by nbotticelli on 2009-04-24
Just seems strange that this would only happen on certain hardware. I am currently still using it on my Toshiba Portege M400 S3052 (running two days now) and everything seems fine. But still no luck with that same cd on other machines.

I'll have to wait another week when things cool down and try downloading again and actually do the MD5 check for once.

Is that generally what people are agreeing on that is causing this?

Can anyone else verify that it won't go past boot on the same hardware that we've mentioned here? Or, can another person says that it does work on the same computer as one mentioned here that doesn't work for us?

---

### Post by betete on 2009-04-24
Hello, I have a different hardware, Pentium 4 HT 3GHz and Ati Radeon 9200, and have the same problem. I thought it could be my graphic card, which gave me troubles with other versions of Ubuntu, but I'm not sure.

Now I have Hardy installed and works fine, but want to try Jaunty.

Actually I had no problem installing it on a Pavilion. So I don't think the iso is corrupted.

Suggestions?

---

### Post by quotidion on 2009-04-25
> **quotidion said:**
> 
Seems like a lot of us got defective downloads. At least I hope it's not a defective ISO image that's been posted.

I downloaded the ISO again. This time the MD5 hash checked ok.  Install went fine.

Lesson: first thing, check your hash.

---

### Post by jsonder on 2009-04-25
I've had no problems with the last couple of alphas and the betas.  Now, the live desktop cd fails to load with a checksum error.  The md5 numbers match before burning the cd.

I've burned using two different machines, with k3b and brasero, and get the same result on most of the machines at the computer club that I tried to boot with the live cd.

It seemed that brasero still might have had a tad to write but the cd was full.

Has anyone else run into this?

---

### Post by mxpert on 2009-04-26
> **elizar said:**
> I managed to get past this on my Toshiba Satellite 1135) by hitting F6 at the live CD home screen; from the options menu that pops up select the first entry for APCI OFF. For me the boot up into the Live CD continues on until it can't detect my Intel integrated 82852 graphics properly and goes into some low-resolution mode. Not looking like Jaunty is in my future. :(

that worked for me ! :)

Thanks !

---

### Post by nbotticelli on 2009-04-27
Okay, I downloed the iso over again. MD5 hash checked fine.

Reburnt it to disc, same problem. Tried F6 and used different combinations of shutting acpi off with other things. Still no luck.


I'm blanking a DVD-RW right now and will try burning it to dvd and see if that works.

---

### Post by nbotticelli on 2009-04-27
So I blanked the DVD-RW, burned the iso to it, and now it works! This is totally bizarre. What would cause this to happen?

What would be the different between the cd-r and dvd-r(w) in terms of being able to boot past the menu?

Seems like something rather serious that ought to be taken care of relatively soon!

---

### Post by Ort on 2009-04-27
Just dl'd newest release. Wasted another cd (7 now). Tried a blank dvd and it WORKS giving live cd of 9.04. So basically the cd burn issue as of 04/27/09 is still open.

---

### Post by kruzztee on 2009-04-27
I've downloaded Ubuntu 9.04 Jaunty 64bit, I burned the image to a CD-RW... I booted, but when I choose to try without installing and install ubuntu it showed "CD Error" message. I checked the MD5 and it matched.

Finally, I managed to install the iso using UNETBOOTIN utility to make my 2GB USB flash drive as a Ubuntu install device.

What is the main problem with the ISO? Luckily I used CD-RW to burn.

---

### Post by jimbob on 2009-04-28
I downloaded and burned the CD and all hashes matched and I had no problem with the install.

I did watch the byte count in the iso file in a terminal window as it progressed and at the end it showed 732+ MB !! Quite a bit for a CD only rated to hold 700 Mb max but not very much for a DVD.

Wonder if this could be (part of) the problem?

---

### Post by don.clark on 2009-04-28
I have the same problem on my Dell Inspiron 1545 and 1505.  I installed 8.10 then upgraded to 9.04 and that worked great.   I finally got my kids to use Ubuntu and would hate for a problem like this to discourage them. I would still like to be able to boot the live cd, I guess I'll try burning to a DVD to see what happens.

---

### Post by Graf Zahl on 2009-04-28
Hey guys, I got the same problem here, with the alternate CD. After choosing 'install ubuntu', the next menu 'choose a language' is frozen.
But guess what? It's because all the USB ports are deactivated. When I use an adapter to connect my USB-keyboard to that old round keybord connector, I can continue with the installation.

But that's not much help, for example my USB WLAN stick doesn't work.

I didn't have any of these problems when I installed 9.04 beta a couple of weeks ago.

---

### Post by gohanssjn on 2009-04-28
> **Graf Zahl said:**
> Hey guys, I got the same problem here, with the alternate CD. After choosing 'install ubuntu', the next menu 'choose a language' is frozen.
But guess what? It's because all the USB ports are deactivated. When I use an adapter to connect my USB-keyboard to that old round keybord connector, I can continue with the installation.

But that's not much help, for example my USB WLAN stick doesn't work.

I didn't have any of these problems when I installed 9.04 beta a couple of weeks ago.

Hmm, I wonder if that is why my LiveCD won't ever boot, my tablet uses a USB CD-ROM...

WELL I'LL BE.

Once I start the LiveCD, the CD-ROM shuts down.  This is a HUGE issue...

---

### Post by nbotticelli on 2009-04-29
How do we search for it if it is considered a bug in launchpad?

---

### Post by rebski on 2009-04-30
This concurs with my experience on my Dell M2010. 

I have been trying to boot up from the live CD/DVD of Ubuntu, Kubuntu and Xubuntu and get the freeze a moment after I select ‘Try Without any changes to your computer’. And yes I also tried putting the CD images on DVD disks.

The error code given is:-
Unknown interrupt or fault at EIP 00000097 00000098 0000bd80

This is a common problem on many Linux distros and has been around for several  years now. Google it and see what I mean.

In fact I have found it to be so with all the Alpha, Beta and RC versions of 8.04, 8.10 and 9.04. The only difference being that it was fixed in the final version of 8.04 and 8.10 but not, sadly, 9.04.

The md5sum on the CD/DVD has been checked and is correct. In any event the same disks works fine on my Clevo laptop and Shuttle desktop. 

The Clevo Elantech touchpad is still not recognised just as before and neither is the Logitech Bluetooth keyboard and mouse on my Shuttle, though that did work with 8.10 as I recall.

It is a shame that Canonical can’t devote a bit of time to dealing with these well known and documented bugs. But then again not everyone is affected by them. 

To put this into perspective I also have these issues with the latest OpenSuse 11.2. Though OpenSuse 11.1 worked fine on my Dell M2010 – at least the final version, the betas gave the same problems.

Frustratingly, over the years sometimes the problems appear to have been fixed, but then they come back, then they get fixed again and at the moment they remain broken once more.

I bought an 8gb USB Memory Stick to try and install from that to my Dell M2010.  But that method is fraught with difficulty too.  This is possibly to do with FAT32 being the required format and having a theoretical limit of 4gb. Ubuntu requires 4.24gb.

I have developed a stoical resignation to all of this, after all I have only been trying to get a satisfactory Linux system on my computers for the past 13 years. 

Perhaps 9.10 will come through for us - but I wouldn’t bet money on it.

---

### Post by kruzztee on 2009-04-30
> **nbotticelli said:**
> How do we search for it if it is considered a bug in launchpad?

Since all posts here lead to one same problem, I agree with you to considered this as bug in launchpad.

---

### Post by nbotticelli on 2009-05-01
I guess I don't want to try to submit a bug if it is already in there, but I am somewhat confused on how to properly search for this in Launchpad. I have tried a few things and have not found anything yet but am not convinced yet.

---

### Post by frutavana on 2009-05-01
I'm not sure if I'm having the same problem you have guys. I downloaded the Jaunty ISO from the Ubuntu site, checked the hashes and burnt it with the Ubuntu "default" CD/DVD writer: didn't work, couldn't get it to boot, goes straight into GRUB, as if there were no CD in the drive. That is, I don't even get to the language selection screen.

Anyway, I tried with a new CD, now using Brasero, same result. I tried a third, rewritable CD, still no luck. In all cases, I wrote the CD at the lowest possible speed.

My CD/DVD drive has been dying for the last couple of years (I normally use an external drive), but I tried booting the Intrepid CD to see if that was the problem, and it booted flawlessly.

Any clues? Never heard of an ISO being bootable in some computers but not in others.

Plus, my laptop cannot boot from USB, so using my external drive or a flash stick is pretty much ruled out. I'm still reading into how to make a clean install from the HDD.

---

### Post by brianwjackson on 2009-05-02
I have been through 10 CDr's and 15 DVDr's, now I am completely out of media. I think you will notice if you look at the back of the disk, there is hardly any data there. It wont work because there is no data, even though it acts like there is. I wonder if there is anywhere to actually get a real copy of this software, it doesnt seem like the ubuntu team wants us to have it....or maybe I should just stick with windows.

---

### Post by jimbob on 2009-05-03
I too have noticed that apparent lack of data on the back of the CD and attributed it to my  recorder??  Interesting.

---

### Post by Hawkeye25 on 2009-05-03
I got Kubuntu 9.04 a week or so ago and formatted my D drive with Ext3 and it loaded and worked. It was an ISO dl'd burned to a CD. I rdered a few new components for the computer and installed them. Nothing really big - kybd, mouse, CPU fan, Sata HD. Then dl'd Ubuntu 9.04 and tried to load it to the SATA - no good, same lockup as others are talking about at language selection. Then tried the Kubuntu that had worked. No deal. By a lucky accident I had connected the new kybd with an adapter to the old round port, but even an operational kybd is of no use with this bug. I ordered a copy of Ubuntu 8.10 from an Ebay vendor in New York - works fine. Tried everything with Kubuntu 9.04 and Ubuntu 9.04. So far, no dice. I will format the SATA drive with Ext3 and remove the IDE drive cable prior to reboot and try again, but I'm not hopeful. Too bad. This release was supposed to be good.
 
BTW, I can't do the 'Hardy' and 'Jaunty' or 'Laurel' and 'Hardy' or any other of that fluffy stuff. Why can't it just be called 'I', 'H' and 'J'? I suppose you can get used to the odd names, but I can't say them in public. I shudder to think about when Kissy Kitty and Lacey Lady and Mincy Missy get released.

---

### Post by nbotticelli on 2009-05-03
Or you can just call the different releases 8.04, 8.10 and 9.04?

---

### Post by MichaelNoyce on 2009-05-04
I've also experienced this problem today when trying to install Jaunty on my Dell 8600c laptop from the Live CD.

Once past the boot menu the CD/DVD drive makes some very odd mechanical noises, like the head is constantly trying to read the disc in the drive. I've never heard noises like that from the CD/DVD drive before and my initial thought was that the drive head had physically failed in some way.

I've had no problems using the Jaunty release candidate Live CD on the same laptop.

I checked the ISO md5sum and that was okay. I checked the CD contents md5sums and they were all okay. I was able to boot from the Live CD on a Dell 640m laptop without any problems.

As suggested in this thread, I then burnt the ISO to a DVD and that seems to work on my Dell 8600c laptop without any problems. Very vexing...

---

### Post by pomalin on 2009-05-04
Hi, I haven't read all messages, but, if somebody feels concerned, and if somebody have the same bug, please look at my bugreport, and perhaps the devs will move.

[https://bugs.launchpad.net/ubuntu/+source/linux/+bug/343268]("https://bugs.launchpad.net/ubuntu/+source/linux/+bug/343268")

---

### Post by brianwjackson on 2009-05-04
Is everyone here with problems using IE to download the ISO? I think this might be the problem.....

---

### Post by nbotticelli on 2009-05-04
> **brianwjackson said:**
> Is everyone here with problems using IE to download the ISO? I think this might be the problem.....

I've used Firefox on Ubuntu 8.10 every time.

---

### Post by rebski on 2009-05-05
> if somebody have the same bug, please look at my bugreport, and perhaps the devs will move.
pomalin, thanks for doing that and also for the link. Now that I know where to go I shall post my information.

---

### Post by JonDubya on 2009-05-18
I have a Dell Inspiron 1100 and have the same problem.  Tried the F6 trick and that didn't work either.  Unfortunately for me, the lapper doesn't have a DVD-ROM so I can't even try that option...wtf ubuntu? Verified MD5s as well in k3b.

PS.  I tried Kubuntu beforehand and it got further, all the way past the KDE splash screen, but after that I just got a blank screen w/ a mouse cursor.

*sigh*

I may just install 8.10 and upgrade if this continues to be a problem.

---

### Post by jimbob on 2009-05-19
Hope I'm not reiterating something already suggested above but I have had great success in using the Ubuntu alternate CD in many cases where laptop installations have shown this problem.

---

### Post by JonDubya on 2009-05-20
So I got Kubuntu 9.04 installed using the regular cd but not using the Live Boot option.  However, once I installed it and login, all I get is the default background and a moveable mouse.  I can Alt+F2 for krunner and ctrl+esc for system activity, but that's about it.  Suggestions?

---

### Post by binneypl on 2009-05-29
I have similar problems on Compaq AP500 and Toshiba Portege 7200.
I've downloaded the .iso from several places - all with identical images and same checksum, as per Ubuntu website.

On both the 8.04 live CD works fine.

So, I can only assume either
a) the .iso is corrupt in some way that only affects older PC's, or
b) support for older PC's has been removed

Shame!

-------- more, later

I've now given up, after trying endless combinations of **all_generic_ide**, **nousb**, **acpi=off**, **noapic** and **nolapic** as well as various BIOS modfications.

I also got the official Ubuntu CD (since so many posts suggest that the burning of the CD was at fault), but that made no difference.

I managed to get the CD to load a couple of times, but each time
was unable to repeat the process using identical options.

Errors include,

[FONT="Courier New"]Segmentation fault[/FONT]

[FONT="Courier New"]IO APIC resources could not be allocated[/FONT]

[FONT="Courier New"]'/sbin/modprobe -b pci:00001250...' ... abnormal exit[/FONT]

[FONT="Courier New"][ 3521.NNNNNN] end_request: I/O error, dev sr0, sector MMMMMM[/FONT]

[FONT="Courier New"]rm: cannot remove '/tmp/.clean': Read-only file system
Segmentation fault
Segmentation fault
mkdir: cannot create directory '/tmp/.X11-unix': Read-only file system
init: rc-default main process (1572) terminated with status 139[/FONT]

[FONT="Courier New"]udevd-event [931]: '/sbin/modprobe -b pci:v00001179d000...' ... abnormal exit
udevd-event [937]: '/sbin/modprobe -b pci:v0000125Dd000...' ... abnormal exit[/FONT]


[FONT="Courier New"]... relay_hotcpu_callback+0x6d/0xbd
... __kmalloc_track_caller+0x61/0xf0
init: rc-default main process () terminated with status 139[/FONT]

[FONT="Courier New"]Setting kernel variables (/etc/sysctl.conf)... Segmentation fault
Setting kernel variables (/etc/sysctl.d/10-console-messages.conf)... Segmentation fault
Setting kernel variables (/etc/sysctl.d/10-network-security.conf)... Segmentation fault[/FONT]

---

### Post by R@pt0r on 2009-06-11
Hello everybody,


 I am also currently experiencing problems with Ubuntu 9.04 on my desktop PC.
 

My PC configuration is as follows:[INDENT]  *Motherboard:* Asus P5VD2-MX
*CPU:* Pentium D 820 2.8 GHz
*RAM:* 2 x 1GB Kingmax (not dual-channel, MB does not support it)
*Video:* GeForce 9600GT
*HDD:* 1 WD 250GB P-ATA (IDE) & 1 Seagate 320GB S-ATA (My Ubuntu OS is installed on WD)
*DVD writer:* Samsung SH-S182D
[/INDENT]In november 2007 I installed Ubuntu 7.10. Since then, I have been upgrading with every new stable release of Ubuntu. Currently I am running the latest (Ubuntu 9.04), but I am not able to boot from GRUB the new kernel version 2.6.28. It just hangs saying "Loading, please wait...". I can boot Ubuntu 9.04 using the old kernel version left behind from Ubuntu 8.10 (2.6.27-11-generic).
 

-------------------------------------------------------------------
 

I also downloaded the ISO of Ubuntu 9.04 from ubuntu.com. MD5 turned out OK. I put the ISO on my 4GB USB memory stick using Unetbootin. When I boot from it, after selecting "Try Ubuntu without ony change to your computer" from the menu, it also hangs saying "Loading, please wait..."
 

-------------------------------------------------------------------
 

Today, I received in my mailbox the Ubuntu 9.04 CD I ordered from ShipIt. I put it in my DVD writer, boot from it, and this too also hangs after selecting "Try Ubuntu without ony change to your computer" from the menu.




 From the behaviors described above, I can only conclude that there must be some kind of incompatibility between my hardware and the new kernel (2.6.28 ) in Ubuntu 9.04.

---

### Post by vinboy on 2009-09-21
Same here. Burnt to CD but couldn't boot on my Compaq laptop.
Burnt to DVD and it works.

what a weirdo.

---

### Post by fairlane32 on 2010-01-24
Wow,
     I'm glad I found this thread. I'm new to the whole linux thing and have been brushing up. I'm an avid listener to SecurityNow!, a podcast done by Steve Gibson and Leo Laporte, and in their last episode they talked about using a LiveCD to boot from to do online banking securely. Well, I thought I'd dive in and have successfully created versions of Puppy Linux and Slax from a cd and usb stick and they seemed to work on a few Dell Optiplexes (745 and 755) at my job, but my custom box at home just spews out hate whenever I put a cd of ubuntu (or any of the other distros mentioned) into my drive to boot from. Same exact behavior as the rest on the thread. The disc boots into the gui menu, accepts my language, but every alternative boot option to try to proceed results in a blank screen with a blinking cursor. I downloaded 9.10 straight from the ubuntu download page, and burned the .iso using ImgBurn on the slowest speed. Didn't try a dvd yet, but I'm thinking, why should I even bother? It shouldn't be this difficult!! What a shame for everyone here to have to deal with these issues, and its just a Live CD!!

Makes me want to find Linus Torvalds and beat him senseless....:D

Linus, if you're listening, YOU OWE ME A STACK OF CD-R'S   muahhaha

Fairlane


Just in case anyone cares,
Asus A8N-SLI Premium mobo
AMD Opteron 180
3Gb Corsair RAM
GeForce 8800GTX x2 SLI mode
Lite-On CD rewritable
SONY DVD rewritable (both masters)
Two WD Raptor drives in RAID0 128 Stripe size
PS/2 keyboard
Microsoft Intellimouse Explorer 3.0

ViewSonic V922 19' monitor

If anyone sees any obvious problems, and has any solutions, feel free......

---

