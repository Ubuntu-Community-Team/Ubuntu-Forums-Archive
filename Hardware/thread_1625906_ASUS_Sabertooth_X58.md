---
title: "ASUS Sabertooth X58"
date: 2010-11-19
forum: Hardware
---

### Post by carolinason on 2010-11-19
Not sure if this is off thread. Anyone using the ASUS Sabertooth X58 and Ubuntu? I've searched for ASUS Sabertooth X58 + Linux, but haven't found anything???? Just wondering. I am going to buy one, but I thought I'd search the HCLs. Old well.

---

### Post by carolinason on 2010-11-19
seems all is fine

---

### Post by cascade9 on 2010-11-20
You could have issues with some of the SATA controllers. Theres a jmicron jmb 362 (runnign eSATA) and a marvel 9128 (2 x SATA III ports). Either of which might work under linux distros, or they might not.

---

### Post by carolinason on 2010-11-20
i'll post results soon, i couldn't help it, i had to order it.

---

### Post by RaSTaBLub on 2010-12-15
Hey,

Is the some news about the support of that mobo on ubuntu ???

Did you received it ? 
Is there some major issue ?

:oops:

---

### Post by cascade9 on 2010-12-15
Someone on a different thread had problems with the marvel 9128 (SATAIII) controller, but aside from that I dont know of any issues.

---

### Post by Migrus on 2010-12-15
I recently upgraded my Linux computer to this motherboard. Seems to be working just fine.

Have not been using the eSATA or SATAIII ports so can't comment on those.

The only Linux related problem I have noticed is that hibernating would not work because of XHCI (I like hibernate even on a desktop machine). This is a known issue and something I guess you will get on any USB 3.0 motherboard. 

This is solved by adding to /etc/pm/config.d/unload_modules this line:
SUSPEND_MODULES="xhci-hcd xhci_hcd"
(different pages had different ideas on the module name so I added both, xhci_hcd seems to be the module name my current kernel has)


I also noticed that my memory is being detected/used at 1066MHz instead of 1600MHz, but that is some BIOS configuration that isn't correct and not correctly autodetected.

---

### Post by cascade9 on 2010-12-15
> **Migrus said:**
> The only Linux related problem I have noticed is that hibernating would not work because of XHCI (I like hibernate even on a desktop machine). This is a known issue and something I guess you will get on any USB 3.0 motherboard. 

I also noticed that my memory is being detected/used at 1066MHz instead of 1600MHz, but that is some BIOS configuration that isn't correct and not correctly autodetected.

I just tried hibernation on my system, with an onboard USB 3.0 controller. Seemed to work no problems. Probably best if I say I'm not using ubuntu on that system, its running aptosid (AMD 64 KDE version). 

As for the memory, some of the 1600+ memory modules will always default to 1066. Not really an issue, but its yet another reason for people to get to know the BIOS in the system they are running.

---

### Post by carolinason on 2010-12-26
same here about 1066. i just set the speed to 1600 in the bios. for some reason maybe i fat fingered something not sure, but the dimm voltage got set too high @ 1.7 for about a day - set it back to auto and all is fine. i noticed that my cpu was running around 130F idle and it runs around 108F otherwise. 

for some reason in 64 bit, doesn't happen in 32 bit, either in ubuntu or windows my hdd led will show activity and then the system is either sluggish or not responding. the mouse works and some things work like system monitors, but most anything else waits. because when the system is back then anything i did with the mouse while unresponsive, will happen. like moving a window or selecting a menu. like it is irq related. get this though, running iotop in ubuntu showed there was no i/o activity going on... twilight zone man!

then this morning while working in shotwell, ubuntu's photo manager, the partition table on my data drive blew up! never had that happen while just working. all of a sudden dialog boxes had no text, the system was really nuts. i've had windows blow up a part table when formatting a partition in windows, but this was pretty weird.

sysrescd - testdisk - found the part table and put it back together, but that's the kind of mess i hate.

i bought this board for stability and it is stable in 32 bit, wish now i bought 3@1GB dimms instead of 2@GB. 

so i was thinking about loading debian, but i might have to go old school and stick a new kernel in it. good way to see the cpu pump out a kernel in no time flat.

but as far as windows goes it's 'okay' in 64 bit and handles w7 32bit quite well.

---

### Post by carolinason on 2010-12-26
one other thing, there were kernel panics with flash

upgraded to 11.04 with 2.6.37-11-generic. i can't see anything in the changelogs, but the hey

---

### Post by carolinason on 2010-12-28
i wonder if it's AHCI?

/* enabled ahci instead of ide compatibility... reinstalling

---

### Post by carolinason on 2010-12-29
enabled ahci in bios and reinstalled windows and linux, problem solved.

---

### Post by cascade9 on 2010-12-29
> **carolinason said:**
> same here about 1066. i just set the speed to 1600 in the bios. for some reason maybe i fat fingered something not sure, but the dimm voltage got set too high @ 1.7 for about a day - set it back to auto and all is fine. i noticed that my cpu was running around 130F idle and it runs around 108F otherwise. 

Its possible that you have 1.7v DDR3 RAM sticks, they do exist. 

130F at idle sounds  bit high to me. Not dangerous, but higher than it should be IMO.

---

### Post by wiebeest on 2011-01-04
> **carolinason said:**
> Not sure if this is off thread. Anyone using the ASUS Sabertooth X58 and Ubuntu? I've searched for ASUS Sabertooth X58 + Linux.

Having happily made the quite progressive jump from my 4 years old AMD Athlon64 3500+ 
with 1GB memory and vanilla geforce 6600 (256mb) with Ubuntu 32bit OS to my new system as specified below.

CPU: core i7 950 
Cooler: Scythe Mugen 2 rev b. SCMG-2100
Mainboard: **Asus Sabertooth x58**, 
Memory: Corsair XMS3 6GB, 
GPU: Gigabyte nVidia Geforce GTX 460 SOC
2 SATA HD's in RAID1 (mirror): WD Caviar Black WD1002FAEX 1 TB, both with Zalman Heathpipe HDD cooler ZM-2HC2
PSU: Cooler Master Silent PRO M 700W
Case: Thermaltake Soprano Black  

And moving from 1GB of memory to 6GB, there off course was a definately urging need to go for the 64bit version this time around, since I wanted to be able to use the full 6GB size, besides of the other obvious benefits of a 64-bit OS with such new components that can make use of such an OS. 

So I downloaded the **Ubuntu 10.10 64-bit** .iso, burned it on a CD-R and tested the live-cd enviroment which seemed to work perfectly. Sound, LAN, etc. all being recognised out of the box (or better said: from the live CD).

Then, alas, onward to actually installing the Ubuntu OS presented a completly different and I might add less smooth scenario.

The installer did seem to startup just fine, but after the partitioning page in the installer, the progress-bar just never appeared, which at first I thought was just a quirk. 

So, I thought, no problem, this will probably be just a simple matter of *lather, rinse and repeating* which will probably remedy that. 

So I rebooted from the live-cd again, clicking the install-icon on the desktop, but same the problem presented itself...after setting up the partition through the installer, again the progressbar did not appear on the horizon. Disk utility did properly recognise my 2 unformatted SATA HD' s though.

But since the problem repeatedly appeared after partioning during the installer, I thought I narrowed it down too something going awkward with Ubuntu detecting that new SATA Harddisk, or it's configuration in the BIOS of my Sabertooth.

So again having rebooted, I now tried fiddling with the settings in my Sabertooth' s BIOS, then booting from the live cd...to no avail, and after consulting dr. Google on this matter, I figured that perhaps the current version of Ubuntu couldn't be happily married yet to that new *marvel 9128 (SATAIII) controller *. 

So I tried remedy that by switching my SATA HD' s from the marvel SATAIII controller to the SATA2 connectors on the mainboard, only to be confronted with the same problem again, and again...for an estimated 80 (...!) flawed attempts, before finally concluding that installing Ubuntu 10.10 64-bit with the live cd really wouldn't work for my new setup.

Thus I downloaded the 10.10 64-bit alternative .iso, in the live-cd enviroment made a bootable usbstick with that on it and *lo and behold* installing this time around worked flawlessly.

Everything now seems to work, my LAN, the sound, installing the proprietary graphics driver for the nVidia GPU, testing that intensely by playing some Windows-titles (trough Wine) without lockups, the whole she-bang. So I'm a happy camper in the end. 
 
And yes, I can solemnly confirm that Ubuntu actually does play very nice with the **Asus Sabertooth**, and can be installed running flawlessly in a 64-bit enviroment, as long as you wisely choose the alternative cd to install on the first attempt (instead of, like me, innitially waisting about 80 faulty installs in three days with the default live cd). :-( 

Worth mentioning though is one little quirk that happens to me every time while booting up the OS... 

After *grub* and before the *loginscreen* appears, I see a warning message mentioning ***"Too many connections"***. 
Now, I have no idea what in the blazes this message reffers to, nor have I so far been able to find an explanation googling it. But the system seems to run mighty fine. 

Still I wonder what this warning could reffer too? 
*Too many connections*? Of *what*? 
I only have one *internet connection*, so that couldn't be "too many". 
And there also couldn't be too many *devices* connected to my mainboard,
since there are so many connectors unused on both the mainboard and my modular PSU. So I'm clueless here. 

So if any of you guys could elude me on this matter, I would appriciate that very much.
Besides that, again Ubuntu 10.10 aka "Maverick Meercat" works great with the Asus Sabertooth x58, even (or perhaps should be especially?) in 64-bit.

---

### Post by carolinason on 2011-01-06
this board runs exceptional with just two bios settings. one) set ram to it's speed in my case 1600 and two) if you have all sata enable ahci, a must.

---

### Post by carolinason on 2011-01-06
> **cascade9 said:**
> Its possible that you have 1.7v DDR3 RAM sticks, they do exist. 

130F at idle sounds  bit high to me. Not dangerous, but higher than it should be IMO.

i'm running standard crucial 1600 ram. idle temp is 108-111F ambient temp depending. [COLOR="Red"]handbrake can push the cpu to 190F[/COLOR] and then i had to pull the handbrake so to say. so the stock cooler on the i7-950 is not a performance fan.

---

### Post by carolinason on 2011-01-06
> Originally Posted by **wiebeest** * Too many connections? Of what?* 

this error is a digital audio message and can be found here [http://ubuntu-virginia.ubuntuforums.org/showthread.php?t=1635278&page=2](http://ubuntu-virginia.ubuntuforums.org/showthread.php?t=1635278&page=2)
i still have not connected my optical connection to my receiver to see if this works. i've noticed some programs use the hd audio and analog is used by others. 

if you desire, set disk controller in bios to ahci to see if this corrects progress bar issue. but you would have to reinstall the system, which you've already done, so... as i have said in this and other posts it caused me great confusion in system waits until i set the ahci feature in the bios.

marvel driver is an issue. waiting on the kernel to catch up to this board[COLOR="Blue"]'s sata III controller[/COLOR]

---

### Post by cascade9 on 2011-01-07
> **carolinason said:**
> i'm running standard crucial 1600 ram. idle temp is 108-111F ambient temp depending. [COLOR=Red]handbrake can push the cpu to 190F[/COLOR] and then i had to pull the handbrake so to say. so the stock cooler on the i7-950 is not a performance fan.

'Standard' crucial RAAM? Not really a model number. From what I can see, crucial DD3 with heatsinks is 1.65v, without heatsinks is 1.5v. 

I'd guess that either your case has no/very poor airflow, the heatsink isnt fitted properly, or you've got to mcuh heatisnk paste. It shouldnt be doing 55C in idle. Hitting 88C at full load is really bad, better to keep things under 70C.

---

### Post by wiebeest on 2011-01-07
> **carolinason said:**
> this error is a digital audio message and can be found here [http://ubuntu-virginia.ubuntuforums.org/showthread.php?t=1635278&page=2](http://ubuntu-virginia.ubuntuforums.org/showthread.php?t=1635278&page=2)
i still have not connected my optical connection to my receiver to see if this works. i've noticed some programs use the hd audio and analog is used by others.

Thank for the tip. I will check it out. 

> **carolinason said:**
> if you desire, set disk controller in bios to ahci to see if this corrects progress bar issue. but you would have to reinstall the system, which you've already done, so... as i have said in this and other posts it caused me great confusion in system waits until i set the ahci feature in the bios.

I've tried both AHCI and IDE during my long unsuccesfull trial and error process described lengthly in my earlier post before I swapped the default 10.10 64-version for the *alternative 64-bit .iso*, which installed succesfully on the first attempt.  Neither settings made the progress bar appear on default 10.10 64-bit version. But AHCI indeed is enabled on current install.

> **carolinason said:**
> marvel driver is an issue. waiting on the kernel to catch up to this board[COLOR="Blue"]'s sata III controller[/COLOR]

Yup, think it's an current support issue which will be solved in the upcoming version. 
But I can live with SATA2 for now, because for what've read on this matter thus far the improvements of SATA3 ATM are not really noticable, only in benchmarks and SATA2 feels quite fast allready compared to my former IDE HD system. :-)

---

### Post by cascade9 on 2011-01-07
> **wiebeest said:**
> Yup, think it's an current support issue which will be solved in the upcoming version. 
But I can live with SATA2 for now, because for what've read on this matter thus far the improvements of SATA3 ATM are not really noticable, only in benchmarks and SATA2 feels quite fast allready compared to my former IDE HD system. :-)

I think you are beign very hopeful. Who knows if, or when marvel 9128 will get proper support (BTW, IIRC there is, or was, a hack to get that controller working properly) 

As for the WD1002FAEX/SATAIII....not really much piont in goign to SATAIII. Sure, if its easy an avaible, go for it, but the only real difference is going to be burst speed. FAEX is still well below SATAII speeds for sustained transfers.

---

### Post by wiebeest on 2011-01-07
> **wiebeest said:**
> 
Originally Posted by carolinason  
this error is a digital audio message and can be found here [http://ubuntu-virginia.ubuntuforums....1635278&page=2](http://ubuntu-virginia.ubuntuforums....1635278&page=2)
i still have not connected my optical connection to my receiver to see if this works. i've noticed some programs use the hd audio and analog is used by others.
Thank for the tip. I will check it out. 

Hmmz. Actually that didn't really help. Totally disabling HD Audio disables sound completely. Setting it to *AC'97* instead of the default *HD audio* does work, but also keeps the " *Too many connections* error.

---

### Post by carolinason on 2011-02-04
Core I7 T.L.B. bug

says there might be hangs! this information is 3 years old. i just stumbled on it.

---

### Post by BobJoe1803 on 2011-02-12
Hey:
I'm new to the site and basicly new to Linux. I have pretty much the same system as you do with the i7 950 chip, nvidia gtx 460, 6gig corsair ram and the sabertooth. Did you have to hunt down drivers to get everything to work together? My internet is run from my desktop, into my laptop which is just a middle connection that connects wirelessly to our router. Linux says the cable is not connected and I dont know enough to fix this at the moment. I also couldnt find drivers for the Realtek adapter.

---

### Post by carolinason on 2011-02-27
solved cpu temp with refitting the heatsink and using a good thermal grease and not the factory stuff. 

i had an issue with system hangs - it was bad hdd controller. disconnected the drive an all is hunky dory.

board is awesome!

---

