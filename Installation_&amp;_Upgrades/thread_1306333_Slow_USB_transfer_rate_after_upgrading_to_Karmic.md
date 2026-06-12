---
title: "Slow USB transfer rate after upgrading to Karmic"
date: 2009-10-30
forum: Installation &amp; Upgrades
---

### Post by skotos on 2009-10-30
After upgrading to Karmic, copying files to and from a USB drive has become a problem.
I think this is a regression bug.

The transfer rate that previously was around 12-19 Mb/s and over is now down at 1.1-1.2 Mb/s: as if it were recognized as a USB 1.x, but this is not the case.

Any idea? I have found a now closed message of a user experiencing the same problem in the beta release - [http://ubuntuforums.org/showthread.php?t=1297106](http://ubuntuforums.org/showthread.php?t=1297106) - and after digging up a bit more this info, too:

[LIST]
[*][https://bugs.launchpad.net/ubuntu/+source/nautilus/+bug/457768](https://bugs.launchpad.net/ubuntu/+source/nautilus/+bug/457768)
[*][https://bugs.launchpad.net/ubuntu/+source/gvfs/+bug/197762](https://bugs.launchpad.net/ubuntu/+source/gvfs/+bug/197762)
[*]....
[/LIST]

---

### Post by phillw on 2009-10-30
> **skotos said:**
> After upgrading to Karmic, copying files to and from a USB drive has become a problem.
I think this is a regression bug.

The transfer rate that previously was around 12-19 Mb/s and over is now down at 1.1-1.2 Mb/s: as if it were recognized as a USB 1.x, but this is not the case.

Any idea? I have found a now closed message of a user experiencing the same problem in the beta release - [http://ubuntuforums.org/showthread.php?t=1297106](http://ubuntuforums.org/showthread.php?t=1297106) - and after digging up a bit more this info, too:

[LIST]
[*][https://bugs.launchpad.net/ubuntu/+source/nautilus/+bug/457768](https://bugs.launchpad.net/ubuntu/+source/nautilus/+bug/457768)
[*][https://bugs.launchpad.net/ubuntu/+source/gvfs/+bug/197762](https://bugs.launchpad.net/ubuntu/+source/gvfs/+bug/197762)
[*]....
[/LIST]


Can you post what your system says about its usb interface, etc...

[http://ubuntuforums.org/showthread.php?t=320202](http://ubuntuforums.org/showthread.php?t=320202)

would be a good start for someone to help you with.

Cheers,

Phill.

---

### Post by yunone on 2009-10-31
i have similar slow speeds with Ubuntu....WIN32 i see greater speeds, i just write it off as something with ubuntu.


example.... large file...1.2 GB to my USB thumb drive average transfer speeds of 7-9 MB

same file in Win 32.... 20-26 MB

makes no sense, not sure what to look for in Ubuntu....just kinda crappy

---

### Post by Azraele on 2009-11-01
> **yunone said:**
> i have similar slow speeds with Ubuntu....WIN32 i see greater speeds, i just write it off as something with ubuntu.


example.... large file...1.2 GB to my USB thumb drive average transfer speeds of 7-9 MB

same file in Win 32.... 20-26 MB

makes no sense, not sure what to look for in Ubuntu....just kinda crappy

yeah man this is a problem for me too. And searching up a little bit i found out that this problem is amongst us at least since 7.0..
It is unbelievable that during all this time nothing has been achieved.
How is supposed ubuntu to stand up as an alternative to windows?
Everybody who has an external HD is forced to dump this os!!
Yet we've not talked about the crappy flashplayer, and all the troubles getting a decent xorg set up with almost any ATI graphic card.

However i've got a pentium 4 3.0 Ghz, mounted on Intel 865PE mobo, 2 gigs Ram DDr 400, Ati radeon 4670 agp, Western digital 160 Gb Hd.

I've tested hard disk and usb speed with the command sudo hdparm -tT and this is the outcome:

/dev/sda:
 Timing cached reads:   1814 MB in  2.00 seconds = 906.61 MB/sec
 Timing buffered disk reads:  150 MB in  3.01 seconds =  49.84 MB/sec
alexandros@alexandros-desktop:~$ sudo hdparm -tT /dev/sdc

/dev/sdc:
 Timing cached reads:   1724 MB in  2.00 seconds = 862.10 MB/sec
 Timing buffered disk reads:   60 MB in  3.02 seconds =  19.88 MB/sec

here's info got with hdparm -i about the HD:

/dev/sda:

 Model=WDC, FwRev=15.05R15, SerialNo=WD-WMAEK2296128
 Config={ HardSect NotMFM HdSw>15uSec SpinMotCtl Fixed DTR>5Mbs FmtGapReq }
 RawCHS=16383/16/63, TrkSize=57600, SectSize=600, ECCbytes=74
 BuffType=DualPortCache, BuffSize=2048kB, MaxMultSect=16, MultSect=16
 CurCHS=16383/16/63, CurSects=16514064, LBA=yes, LBAsects=312581808
 IORDY=on/off, tPIO={min:120,w/IORDY:120}, tDMA={min:120,rec:120}
 PIO modes:  pio0 pio1 pio2 pio3 pio4 
 DMA modes:  mdma0 mdma1 mdma2 
 UDMA modes: udma0 udma1 udma2 udma3 udma4 *udma5 
 AdvancedPM=no WriteCache=enabled
 Drive conforms to: Unspecified:  ATA/ATAPI-1,2,3,4,5,6


Yet when moving data from hd to usbstick (Kingston 4 Gigs) the transfer rate starts from 10 Mb/s then drops gradually to 3 Mb/s, sometimes even 1 Mb/s, which goes without saying makes the usb unusable.

If some other info are needed just ask.

Thanks for the patience

---

### Post by Azraele on 2009-11-02
Sooooo Fellas

I've made further investigation about this crazy usb problem and found out some other shocking details:
googling up a little bit i found out that this problem was everything but new to ubuntu, and that the misfunctioning of the usb was due to the wrong kernel modules loaded during the startup; the damn modules were 
ohci_hcd : the usb 1.0 module file
ehci_hcd : the usb 2.0 module file
uhci_hcd : the usb hi-speed module file

In the previous ubuntu releases the problem existed because of a wrong startup module file (/etc/module) which loaded ohci_hcd instead of the other two modules needed for our beloved usb 2.0.

So i decided to check out with dmesg | less if during the ubuntu boot our modules where misloaded, but sadly the modules were loaded fine.

Funny thing is, if you check out the /etc/modules files there NONE usb modules are loaded!!

More interesting if you check out the /lib/modules/2.6.31-14-generic/kernel/drivers/usb/host/ where the usb modules are stored you'll found out that the ehci and uhci do not exist!!!

I think that this is the core of the problem here, but as you'll already know i am knew to linux and i have no skills to deal with an issue like this one.

Good news is a found out that loading in the file /etc/modules the
usb 3.0 module my usb speeds up a little bit, making it better but surely leaving its performances to a very very poor level.

So if you want to give it a shot open /etc/modules as root with the termial:

sudo vi /etc/modules

and then insert the line:
xhci.ko (or if it doesn't work)xhci
 
but only if lines like ehci_hcd or uhci_hci are not already present.

This is not a solution. I hope that someone with skills tries to solve this problem too or we will end up with ubuntu without usb.

---

### Post by beeema on 2009-11-02
Yeah that's strange. I also can't acces my 3G-USB-modem properly and my mouse takes a looong time to run. In 9.04 everything was OK. I hobe someone can solve this. I'm not really an IT-expert :(

---

### Post by skotos on 2009-11-03
> **phillw said:**
> Can you post what your system says about its usb interface, etc...

[http://ubuntuforums.org/showthread.php?t=320202](http://ubuntuforums.org/showthread.php?t=320202)

would be a good start for someone to help you with.

Cheers,

Phill.
Thank you phillw.

In the meantime I have discovered that the Avermedia firmware download that worked up to Jaunty is now causing me lots of small/big problems.

After renaming /lib/firmware/xc3028-v27.fw, in fact, the USB ports start working at full speed again and Cheese once again recognizes the internal webcam.

Thus, I think I have now to look for an xc3028-v27.fw update/solution.

---

### Post by skotos on 2009-11-03
@yunone
@beeema
@Azraele

Well guys, my problems seem related (as in my answer to phillw) to another non USB misconfiguration: when booting, in fact, the kernel asks for a firmware file needed to initialize my internal DVB board, but providing the requested file as I have done in the past is today causing these USB problems.

From this experience of mine, I would suggest you to do the same and look at the errors that can be reported in the log files, in particular inside **/var/log/messages**.

This file is in fact written at boot time and the first and most important errors are generally reported inside it. Taking these errors away can generally solve the others.

HTH

---

### Post by Azraele on 2009-11-03
> **skotos said:**
> @yunone
@beeema
@Azraele

Well guys, my problems seem related (as in my answer to phillw) to another non USB misconfiguration: when booting, in fact, the kernel asks for a firmware file needed to initialize my internal DVB board, but providing the requested file as I have done in the past is today causing these USB problems.

From this experience of mine, I would suggest you to do the same and look at the errors that can be reported in the log files, in particular inside **/var/log/messages**.

This file is in fact written at boot time and the first and most important errors are generally reported inside it. Taking these errors away can generally solve the others.

HTH

Well i've checked it twice, but i don't see any kind of error, nor usb-related neither any other kind of 'em.

however the starting transfer speed usually are fine, but there's a drastic drop of the transfer rate after some seconds since the beginning of the operation, which fast reaches a bottom of 3 - 1 Megs per second.

As i've already said i see no errors in the boot up log file, but i think that the core of our issue is in the kernel too. 
Could be the fact that wrong usb-kernel modules are loaded, at least that seemed to be the problem in the previous version of ubuntu, easily solved by inserting the right ones in the kernel modules files, but since the usb 2.0 modules seems to be disappeared in the 9.10 i don't really know what to do.

We should have a good diagnosis before trying to solve this problem, and as far as i can see we don't have one. ;)

I repeat, my system doesn't give me any kind of error outputs, which means that for his protocol everything is fine, but we all can see that it ain't.

---

### Post by angelus13 on 2009-11-04
Howzit all,

At first I thought that it was my laptop, since its like ancient, was not compatible with koala, but it seems you are also having the usb problems. If there is a solution, please can someone help us out. Its quite annoying having to wait for copying 500gb. Why did they try to fix something that wasn't broke.

Its all awesome that I can now load the windows software that was builtin on my 3g usb dongle, but that doesn't help me really. 

Any solutions for this slow tx rate pls..

---

### Post by angelus13 on 2009-11-04
Howzit guys, 
I just realized something, because I use my externals as direct download locations.

When more than 1 program is trying to access the drive, everything else is stalling, whether its ftp, or download (torrent and http) its crazy.....and driving me insane. I have to go and reroute all my downloads now....this sucks.....I hope that there is a fix for this sooon.....

---

### Post by skotos on 2009-11-04
> **Azraele said:**
> Well i've checked it twice, but i don't see any kind of error, nor usb-related neither any other kind of 'em.
(Well, solving the errors shown in the logs is a prerequisite) 
I do not get any USB related message too.

It seems as if the *event of a newly attached device* is not sent to the kernel (*libnotify, udev*, ...?)

 (My USB HP printer gets now recognized by the horrible HP all-in-one extension only: no way to see its usb uri otherwise)

> **angelus13 said:**
> ...it seems you are also having the usb problems...
Yes, I am.

> **Azraele said:**
> ... i think that the core of our issue is in the kernel too.

I definitely agree with you: a kernel problem concerning the USB ports

---

### Post by Azraele on 2009-11-04
Still I have no idea what it is, we know were to search now but the fact that the system log file does not suggests anything isn't helping out..

Bright new ideas are  welcome!!! :D

---

### Post by baltetsch on 2009-11-05
> **angelus13 said:**
> Howzit guys, 
When more than 1 program is trying to access the drive, everything else is stalling, 

I am experiencing the same issue, I tried to transfer a couple of videos onto my phone, first of all the transfer speed was extremely slow (much slower then when I had 8.4, 8.10 or 9.4 installed) and then when I tried to copy a second file at the same time it just about killed the system.  If there is a fix I would love to hear about it.

---

### Post by smdeep on 2009-11-06
Hi
I have the same issue as angelus13. Suppose I am downloading a biggish file in firefox and at the same time I decide to copy something to a pendrive. The whole system (checked on an old laptop and an old desktop) comes to a crawl and even the mouse pointer does not move!

I sincerely hope there is some solution to this.

---

### Post by Azraele on 2009-11-08
> **smdeep said:**
> Hi
I have the same issue as angelus13. Suppose I am downloading a biggish file in firefox and at the same time I decide to copy something to a pendrive. The whole system (checked on an old laptop and an old desktop) comes to a crawl and even the mouse pointer does not move!

I sincerely hope there is some solution to this.

I don't wanna be a pessimist, but i'm starting thinking that this problem has become somekind of a tradition :p

i'm considering re-switching to windoze ):P

---

### Post by ballin on 2009-11-08
I'm getting exactly the same problem since 9.10

---

### Post by shushek on 2009-11-10
Hello there, sorry but me too is experiencing the same "SLOW DATA TRANSFER ISSUE" with my 9.10. It was there in 8.04 as well, but this time is a bit worse. As am a newbie to this so can't be able to provide my investigation details as it was primarily based on the posts provided by you people.

Just waiting for some miracle to happen,and AM NOT THINKING OF GOING BACK TO WINDOWS.. not in this life!!:popcorn:

---

### Post by potam on 2009-11-10
Same problem here.

---

### Post by Hevydani on 2009-11-12
This is CACK, Same problem. Problem, Problem, Problem. Seems all I have with Ubuntu,
Am starting to regret my switch from Win....

---

### Post by gyaneshwar on 2009-11-13
> **Azraele said:**
> Sooooo Fellas
So if you want to give it a shot open /etc/modules as root with the termial:

sudo vi /etc/modules

and then insert the line:
xhci.ko (or if it doesn't work)xhci
 
but only if lines like ehci_hcd or uhci_hci are not already present.

This is not a solution. I hope that someone with skills tries to solve this problem too or we will end up with ubuntu without usb.


Thanks a million, it works for me. :popcorn:

---

### Post by skotos on 2009-11-13
I have currently - better partially - solved my USB problems by installing the ***2.6.31-15.28*** kernel from the proposed updates.
Please, beware of the proposed updates: they should not be run on production workstations/servers...
I am not suggesting them as a regular practice: this time they might be considered a necessary exception and a solution to some of us.

---

### Post by skotos on 2009-11-13
OK. IT **_WAS_** PARTIALLY SOLVED.

[COLOR=Red]Upgrading to the latest proposed kernel **2.6.31-15.50** made things go worse and worse.[/COLOR]
For USB is still day one. Nothing works again.
The USB hard drives worked under **2.6.31-15.28**.

---

### Post by tractor on 2009-11-14
Same problem here. I wanted a clean install of 9.10, so I backed up all of my data to a portable hard drive. I had fast transfer speeds transferring the data out. After installing 9.10, when trying to copy the data back to 9.10, I'll get from 10% to 30% of the data copied at good speeds, then the transfer almost stops dead. Tonight at one point I just left it sit there, and after two or three minute period of time, the speed picked back up to what it should have been the entire time and the transfer completed.

---

### Post by skotos on 2009-11-18
I still haven't checked the transfer rate, but it seems something interesting has been released: for the first time after upgrading/switching to Karmic, **USB devices are once again automatically recognized!**
In three of four computers no reboot was necessary to make them work the first time!

These are the positively updated packages:

[LIST=1]
[*]initscripts 2.87dsf-4ubuntu12
[*]system-tools-backends 2.8.2-1ubuntu1
[*]sysv-rc 2.87dsf-4ubuntu12
[*]sysvinit-utils 2.87dsf-4ubuntu12
[/LIST]
FYI
These packages come from the **official repositories** and do not require any *proposed updat*e: thus to have them correctly installed simply run Synaptic, refresh, mark all the upgrades, apply and you are done!

I am now going to further check!
:D :popcorn:

---

### Post by Azraele on 2009-11-18
Not to bother but this is a solution to a problem you created for yourself.

Still no sight of as solution for the damn USB.

---

### Post by Azraele on 2009-11-18
Not to bother but this is a solution to a problem you created all by yourself.

Still no sight of as solution for the damn USB.

---

### Post by FabioBraso on 2009-11-19
Hello all,

I have a similar problem. In my desktop with Karmic Koala; there are 4 usb 1.1 port in motherboard and 5 usb 2.0 port in additional PCI card.

The speed rate to read from a usb memory  is:

140 KB/s from usb 1 ports and 450KB/s from USB 2 ports.

Can someone give me an hint?

thank you

Fabio

---

### Post by Azraele on 2009-11-19
I suggest it's a kernel problem, since the module loaded should be the right ones, nobody has the furthest idea of what to do. I suggest looking my previous post about the kernel modules since it seems that has helped someone, for me thou it didn't worked out well.

You can always try adding in /boot/grub/menu.lst the option pci=routeirq to the line of the kernel you're actually using.

All this tips are FAR AWAY from a solution. I think it's a MAJOR KERNEL BUG

---

### Post by Azraele on 2009-11-19
I suggest it's a kernel problem, since the module loaded should be the right ones, nobody has the furthest idea of what to do. I suggest looking my previous post about the kernel modules since it seems that it has helped someone, for me it didn't worked out well.

You can always try adding in /boot/grub/menu.lst the option pci=routeirq to the line of the kernel you're actually using, this has improved my USB stats, but they're still too poor for USB 2.0 standards.

All this tips are FAR AWAY from a solution. I think it's a MAJOR KERNEL BUG which can be only solved by linux programmers. But since nobody seems to care i think i'm switching to Fedora. I suggest you do the same thing, because it seems that it has not these kind of issues. ;)

---

### Post by skotos on 2009-11-21
> **Azraele said:**
> Not to bother but this is a solution to a problem you created for yourself.
YES if upgrading means "creating for myself", _NO_ otherwise.

I think that the heavy changes in the boot process that are taking  us far from the original and historical init scripts are creating this kind of problems.
**Upstart** is a big change, but [I]probably the 6 months cycle is too short for it to be successfully applied with no general issue.
[/I] 
As soon as these scripts have been updated, my HP all-in-one printer has been once again able to scan and print as in the past, and every my USB key/hard disk has been read and written as it was before upgrading.

No more proposed Kernel update, just a few scripts updates.
I think that, having solved this, those who is/are responsible for the upstart migration is/are going to start working on speed/transfer rates.

This is - at least - what I would do: I would first solve the problems that do not let me access the hardware, then I would work on optimization.

The developer is/are supposed to be working like this. What is wrong is simply the 6 months cycle: immediate upgrade after a new release is still too dangerous.
We are probably considered a sort of beta testers and this is not good at all. I do not feel like a beta tester and I do not want to be treated like this.
If I wanted to be a beta tester I would be running the next generation and I would not wait up to October 29th...

I hope - at least - that -  on its release date - 10.04 will not be at an alpha stage any more.

Audio problems can be frustrating, but display and USB problems can be too heavy for computers on which end users are working on a regular basis.

Up to now, in fact, immediate upgrade might transform a victory in a desperately lost war.

I know that Mark and Canonical have done lots to GNU/Linux, but users expectations are dangerous as well.

It is sad reading things like this:[quote=Azraele]..But since nobody seems to care i think i'm switching to Fedora...[/quote]isn't it?

Next year, it would be probably better installing a fully working 10.0**6** or 10.0**8** than a broken 10.0**4**.
On a release date we simply would like to run the software and not feel frustrated.

---

### Post by Azraele on 2009-11-24
> **skotos said:**
> YES if upgrading means "creating for myself", _NO_ otherwise.

I think that the heavy changes in the boot process that are taking  us far from the original and historical init scripts are creating this kind of problems.
**Upstart** is a big change, but [I]probably the 6 months cycle is too short for it to be successfully applied with no general issue.
[/I] 
As soon as these scripts have been updated, my HP all-in-one printer has been once again able to scan and print as in the past, and every my USB key/hard disk has been read and written as it was before upgrading.

No more proposed Kernel update, just a few scripts updates.
I think that, having solved this, those who is/are responsible for the upstart migration is/are going to start working on speed/transfer rates.

This is - at least - what I would do: I would first solve the problems that do not let me access the hardware, then I would work on optimization.

The developer is/are supposed to be working like this. What is wrong is simply the 6 months cycle: immediate upgrade after a new release is still too dangerous.
We are probably considered a sort of beta testers and this is not good at all. I do not feel like a beta tester and I do not want to be treated like this.
If I wanted to be a beta tester I would be running the next generation and I would not wait up to October 29th...

I hope - at least - that -  on its release date - 10.04 will not be at an alpha stage any more.

Audio problems can be frustrating, but display and USB problems can be too heavy for computers on which end users are working on a regular basis.

Up to now, in fact, immediate upgrade might transform a victory in a desperately lost war.

I know that Mark and Canonical have done lots to GNU/Linux, but users expectations are dangerous as well.

It is sad reading things like this:isn't it?

Next year, it would be probably better installing a fully working 10.0**6** or 10.0**8** than a broken 10.0**4**.
On a release date we simply would like to run the software and not feel frustrated.

I know my buddy that it's sad, but:

Point one: the 9.10 release isn't a beta, or at least isn't considered that since the beta period of one month expired the day the release was official.

Point two: This is not a little bug or something easy solvable, since i found docs proving the existence of this problem for more than 3 years from now, and i'm starting thinking either programmers don't care or they don't know what to do, and in both cases i can't use an os without usb.

I'm sorry but that's the situation here.

---

### Post by yunone on 2009-11-24
updated to show no change in speed

---

### Post by potam on 2009-11-25
> **yunone said:**
> updated to show no change in speed

Same here. Speed decrease is not so radical as before, but still exists.

---

### Post by tedsign on 2009-11-25
In my case, beside the slow transfer (after 80 MB transfered), also mouse response becomes slow too. Even when the transfer indicates already 100%, I have to wait for some time for the progress bar to disappear. 

It seems there is no solution for this issue (like package updating or whatever). I have migrated about 40+ computers to Ubuntu in my office. And now I am thinking of give other distros a try.

---

### Post by MrPotter on 2009-11-25
> **tedsign said:**
> In my case, beside the slow transfer (after 80 MB transfered), also mouse response becomes slow too.
You are not alone. I'm having the same problem since Karmic. Also for me it is not possible to cancel a running file transfer. After I clicked the red x-Button the system ignores my action and proceeds the transfer.
Last time I tried to copy a large file (~1GB) to my iPod. I canceled the process, because the transfer rate only was ~450kb/s. Then the system behaved like having a kernel panic - I wasn't able to move the mouse. Only an emergency shutdown helped me .-.

 Is a kernel/distro downgrade possible?!

---

### Post by Azraele on 2009-11-25
> **MrPotter said:**
> 

 Is a kernel/distro downgrade possible?!

It probably wouldn't help a thing. As I've already said this issue is old.

However our friend dcstars seems to have an explanation for the usb slowdowns. Check this out:

[http://ubuntuforums.org/showthread.php?t=366205](http://ubuntuforums.org/showthread.php?t=366205)

Too bad if that's the problem it's unsolvable.

---

### Post by slumbergod on 2009-11-25
This has always been the case for me, ever since I started using Gutsy. The speed goes all over the place. I can transfer two files one after the other to a USB 2.0 flash drive. One will transfer as fast as it would under windows...the other will transfer so slow I thing it has hung and stopped.

USB flash drives have never given me performance on par with USB 2.0. It's been the same in every very of Ubuntu and across three different laptops (the latest being a brand new system).

I've also just put it down to being some weird Ubuntu issue that doesn't affect everyone and will probably never be fixed. I've just learned to live with it.

---

### Post by w0rds on 2009-11-25
did anybody file a bug report of this problem?

---

### Post by potam on 2009-11-26
> **w0rds said:**
> did anybody file a bug report of this problem?

I saw several bug reports regarding to this problem. No soultion yet, but it is a major kernel bug.

---

### Post by aditya_g8 on 2009-11-26
Updateted today 26/11/2009 still very slow copy to internal and external hdd

---

### Post by MrPotter on 2009-11-26
> **Azraele said:**
> It probably wouldn't help a thing. As I've already said this issue is old.

But I never had this problem before. All file transfers in Ubuntu < Karmic worked perfectly. Of course there were older kernel versions, but without this bug.   Also the thread itself indicates, that there is something different to the old kernel bug. "Slow USB transfer rate **after upgrading** **to Karmic**".

---

### Post by sbec67 on 2009-11-27
Hi,
I faced also the Problem with very slow USB....
what i found out is, that it devers from what kind of unit you attach.

Example: i have aa USB External HD - Formatted EXT3 - Transfer Rate 17-20 MB/Sec

i have a USB MP3 Player ( also readable under Windows ;-) ) Transfer rate 400 KB/Sec ( Kilo !! :-( )

Could it be possibe that USB is OK, but with some Formats Karmic has a Problem ?

---

### Post by potam on 2009-11-28
> **sbec67 said:**
> Hi,
Could it be possibe that USB is OK, but with some Formats Karmic has a Problem ?

Confirmed, this is a partition-type problem. With ext3 I got 28 MB/s speed, with fat32 only 0.5-1 MB/s.
Edit: this is for external hdd, flash drives still slow like hell.

---

### Post by skotos on 2009-11-28
> **potam said:**
> Confirmed, this is a partition-type problem. With ext3 I got 28 MB/s speed, with fat32 only 0.5-1 MB/s.
Edit: this is for external hdd, flash drives still slow like hell.
NICE! This sounds... interesting!
Humm..
At least we might find a way to survive by formatting a few hard disks..

In the meantime I can confirm that performances heavily go down even on NFSv4 operations.
 
And... oh.. I have been forced to run Fedora 12 in order to have full USB support and functionalities.
This is some enlightening info from Fedora bugs page [http://fedoraproject.org/wiki/Bugs/Common](http://fedoraproject.org/wiki/Bugs/Common): 
```
Some manufacturers ship systems with a BIOS whose handling of [IOMMU]("http://en.wikipedia.org/wiki/IOMMU") hardware is incorrect. 
The BIOS is supposed to tell the operating system where in memory to find the IOMMU hardware,
but some BIOSes do not do so correctly, providing a garbage location or a location which is
valid but is not actually where the device is located.
The kernel attempts to handle these cases, but some are still not fully handled in the
Fedora 12 kernel. 
[B]If you have a system affected by this problem, the most common symptom is that the USB
subsystem will fail to work (no USB peripherals will work), but other symptoms have included
systems that completely fail to boot, and non-functional network adapters.[/B]
```This might at least explain what is currently happening...

---

### Post by Ivo_Wever on 2009-11-29
> **potam said:**
> Confirmed, this is a partition-type problem. With ext3 I got 28 MB/s speed, with fat32 only 0.5-1 MB/s.
Edit: this is for external hdd, flash drives still slow like hell.

Disconfirmed: I have an external hdd and a flash drive that are both formatted as fat32. The hdd performs as expected, while the flashdrive shows lousy performance. I have verified that it must be this Karmic machine, as another machine can write to the flashdrive at high speed.

---

### Post by Azraele on 2009-11-29
I found out a way that improves my transfer speeds, check it out than let me know:

IRQ stands for Interrupt ReQuest. When the computer is doing something, rather than always be on the lookout for other devices and processes that need its attention, it uses these interrupts or IRQ's to allow the device to say "Hey look at me -- I want to tell you something". It's a bit like a string tied to the PC so the device can tug on it for attention.

I think the slowdowns are due to the fact that after sometime the usb has difficulties to call up the attention of the motherboard, therefore the stopping of the transfer which increases the transfer timings.

To turn off the IRQ you have to add the option 

pci=acpi

to the booting kernel options. So open the file

/boot/grub/grub.cfg 

and edit the option line of the kernel you use to boot adding the command i've previously shown. Be careful not to add to all the kernels this option, because in case of screw ups you can boot the other ones and modify what's gone wrong.

In case you don't recognise the option line, usually it's the one which terms with quiet or bootsplash (which are other booting options of course).

Let me know if it worked. ;)  

I've got to say, if my usb keeps going this fast, I can say problem solved for me.

---

### Post by potam on 2009-11-30
> **Azraele said:**
> 
To turn off the IRQ you have to add the option 
pci=acpi

No difference for me :(

---

### Post by R33D3M33R on 2009-11-30
Hi, same problem for me here. The speed is 1-2MB/s on a USB 2.0 drive. In Hardy, the speed was fine.

---

### Post by imwithid on 2009-12-01
About 45 minutes ago, I started copying a 950MB file to my USB key and it is still transferring. I tried using the "Send To" application to see if this would make a difference from a manual transfer and it seems to be worse.

I generally run mprime (and Prime 95 in Windows - both distributive computer programs) and I find it impossible to do anything in Karmic, especially after the last update yesterday (I'm not sure if there was a kernel update). Even now as I type, I get a lag at times. and switching between tabs using Opera takes about 5 seconds to process.

Generally, I must close all programs for transfers to a USB drive to transfer at higher speeds. This generally improves my situation but renders the computer unusable during that period. This is by no means a solution, but saves me from getting a hammer and fixing the computer for good.

---

### Post by imwithid on 2009-12-01
After over 50 minutes of waiting, it had to be done. After having closed the application, everything seems to be running normally again (Internet speed back to normal). Although it does not show in the System Monitor, transferring files to a USB key seems to take up quite a bit of the resources.

---

### Post by MrPotter on 2009-12-01
> **Azraele said:**
> 
[...]
pci=acpi
[...]
/boot/grub/grub.cfg 


It worked! 

 I added the option to the kernel image line in the menu.lst - file. The system don't freeze anymore and the transfer rate seems to be normal!

Thank you!!

---

### Post by roozbeh on 2009-12-02
it didnt work for me and i still have very slow performance on my usb disks.
i saw this.
not the prefect solution but maybe would help some peaple

[http://en.opensuse.org/SDB:Automounting_without_the_sync_Option](http://en.opensuse.org/SDB:Automounting_without_the_sync_Option)

PS. is this bug reported?

---

### Post by Azraele on 2009-12-03
> **roozbeh said:**
> it didnt work for me and i still have very slow performance on my usb disks.
i saw this.
not the prefect solution but maybe would help some peaple

[http://en.opensuse.org/SDB:Automounting_without_the_sync_Option](http://en.opensuse.org/SDB:Automounting_without_the_sync_Option)

PS. is this bug reported?

I had transfer speed from ext4 to NTFS of approx. 25 meg/sec.

I checked after the grub tweak and now my transfer speed to Windoze partitions are 40 Megs per second :D:D

---

### Post by roozbeh on 2009-12-04
> **Azraele said:**
> I had transfer speed from ext4 to NTFS of approx. 25 meg/sec.

I checked after the grub tweak and now my transfer speed to Windoze partitions are 40 Megs per second :D:D

whats the twaeak?

---

### Post by potam on 2009-12-05
I guess [this]("http://ubuntuforums.org/showpost.php?p=8409097&postcount=47"), it did not work for me. Let us know if it works for you.

---

### Post by Azraele on 2009-12-05
> **roozbeh said:**
> it didnt work for me and i still have very slow performance on my usb disks.
i saw this.
not the prefect solution but maybe would help some peaple

[http://en.opensuse.org/SDB:Automounting_without_the_sync_Option](http://en.opensuse.org/SDB:Automounting_without_the_sync_Option)

PS. is this bug reported?


The first time  tried it I had no improvements because the same day there was a kernel upgrade, and anytime one gets a new kernel the grub.cfg is written back up, so all the changes one makes to the file are lost. 

To those whom had improvement with my solution remember always to put the option back again after a kernel update!! :popcorn::popcorn:

---

### Post by potam on 2009-12-06
No improvement in 2.6.31-16 kernel. Transfer starts at 11 MB/s, and drops to 600 kB/s. Test file was 700 MB.

---

### Post by Joshua Lückers on 2009-12-06
I have the same issue when writing files to a USB stick.

---

### Post by sbec67 on 2009-12-07
i added into /boot/grup/menu.lst pci=acpi
```

title		Ubuntu 9.10, kernel 2.6.31-15-generic
uuid		96f8feb3-e65b-4696-b8f5-c32638cde861
kernel		/boot/vmlinuz-2.6.31-15-generic root=UUID=96f8feb3-e65b-4696-b8f
5-c32638cde861 ro quiet splash pci=acpi
initrd		/boot/initrd.img-2.6.31-15-generic
quiet

```
no change.. still extremely slow, to transfer Data to FS-type msdos :-(

also the recent kernel update didn't change anything :-(

any news on this ?

---

### Post by Sico2 on 2009-12-07
Have the same since at least 7.10. I can remember, some distribution had allowed me to transfer with 25-30 Mbp/s. Since I swapped to karmic koala, the transfer is almost always about 3Mbp/s. It doesn't matter if it's movie transfer to my MP4 player or my external SATA or USB stick.

Any ideas, how can we move it faster around? Any phone number for Ubuntu people? London, Edinburgh? :)

---

### Post by BkKen on 2009-12-08
Hi all,

  I'm new to Ubuntu and all, but I've recently just turned to Ubuntu, and it seems my major problem is the same as you guys here. I've around 5mb/s transfer rate on a fast day, and less than 1 mb/s on any "bad hair day". Now I've tried updating my bios, changing the distro version, backing to an older version of the Ubuntu, and none seems to work. Would really appreciate any help here, cos I'm on the verge of giving up and heading back to the lousy old Win.


Thanks,

BkKen

---

### Post by MCunha on 2009-12-08
[COLOR=black][FONT=Verdana]Hi,[/FONT][/COLOR]
[COLOR=black][FONT=Verdana] [/FONT][/COLOR]
[COLOR=black][FONT=Verdana]Can anybody try remount an USB device and see if the speed get normal?[/FONT][/COLOR]
[COLOR=black][FONT=Verdana]This solves this problem to me in 9.04. Copy a 3gb file to a Voyager GT takes almost 2 hours in sync mode and only 4 minutes in async mode:[/FONT][/COLOR]
[COLOR=black][FONT=Verdana] [/FONT][/COLOR]
[COLOR=black][FONT=Verdana]```
sudo mount -o remount,async /path_where_is/mounted
```[/FONT][/COLOR]
[COLOR=black][FONT=Verdana] [/FONT][/COLOR]
[COLOR=black][FONT=Verdana]Let me know if this changes anything.[/FONT][/COLOR]
[COLOR=black][FONT=Verdana] [/FONT][/COLOR]
[COLOR=black][FONT=Verdana]Good luck![/FONT][/COLOR]

---

### Post by BkKen on 2009-12-09
> **MCunha said:**
> [COLOR=black][FONT=Verdana]Hi,[/FONT][/COLOR]

[COLOR=black][FONT=Verdana]Can anybody try remount an USB device and see if the speed get normal?[/FONT][/COLOR]
[COLOR=black][FONT=Verdana]This solves this problem to me in 9.04. Copy a 3gb file to a Voyager GT takes almost 2 hours in sync mode and only 4 minutes in async mode:[/FONT][/COLOR]

[COLOR=black][FONT=Verdana]```
sudo mount -o remount,async /path_where_is/mounted
```[/FONT][/COLOR]

[COLOR=black][FONT=Verdana]Let me know if this changes anything.[/FONT][/COLOR]

[COLOR=black][FONT=Verdana]Good luck![/FONT][/COLOR]
Hi, sorry but I'm very fresh with Linux, could you please guide me as to how this is done? I tried opening the Terminal and typed as instructed (having the USB connected) changing the "/path_where_is/mounted" to "/media/HDD_name" but the returned response was "mount: you must specify the filesystem type"


Thanks

---

### Post by potam on 2009-12-09
> **MCunha said:**
> [COLOR=black][FONT=Verdana]Hi,[/FONT][/COLOR]
[COLOR=black][FONT=Verdana] [/FONT][/COLOR]
[COLOR=black][FONT=Verdana]Can anybody try remount an USB device and see if the speed get normal?[/FONT][/COLOR]
[COLOR=black][FONT=Verdana]This solves this problem to me in 9.04. Copy a 3gb file to a Voyager GT takes almost 2 hours in sync mode and only 4 minutes in async mode:[/FONT][/COLOR]
[COLOR=black][FONT=Verdana] [/FONT][/COLOR]
[COLOR=black][FONT=Verdana]```
sudo mount -o remount,async /path_where_is/mounted
```[/FONT][/COLOR]
[COLOR=black][FONT=Verdana] [/FONT][/COLOR]
[COLOR=black][FONT=Verdana]Let me know if this changes anything.[/FONT][/COLOR]
[COLOR=black][FONT=Verdana] [/FONT][/COLOR]
[COLOR=black][FONT=Verdana]Good luck![/FONT][/COLOR]

No difference for me.

---

### Post by imwithid on 2009-12-12
I'm sick of this problem. It's been like this for me since 9.04. The only way that speeds increase is when I close all applications, run System Monitor and change the nice level of nautilus to <-10.


I'm taking a chance with 10.04 Alpha-1. I'll write back in the next day or two as to what happens. It's too late and I'm too tired to mess around with this silly problem. It's clearly a bug and I feel like I'm wandering about a large building blindfolded with hundreds of others trying to find the exit while the building is on fire. I'm angrier than Rambo in First Blood: II when he gets back to say that he's finished his mission.

---

### Post by Azraele on 2009-12-12
The only way of solving this is filing a bug report to the official channel. But it will be hard. I'm already doing this for another problem and even gettin' the programmers to look at it is difficult: 
file a bug report and then everybody has to quote the problem. Making it the official way is the only solution. Obviously you'll have to feed them information daily to make their work possible and to obtain solutions. Everybody has to collaborate.

---

### Post by BkKen on 2009-12-13
> **Azraele said:**
> The only way of solving this is filing a bug report to the official channel. But it will be hard. I'm already doing this for another problem and even gettin' the programmers to look at it is difficult: 
file a bug report and then everybody has to quote the problem. Making it the official way is the only solution. Obviously you'll have to feed them information daily to make their work possible and to obtain solutions. Everybody has to collaborate.
Yes pls, I would love to do that if it helps this community. Would you mind guiding me how I could make that happen? 

One funny observation I had lately is this (not sure if everyone shares the same). I tried Mint on a Live USB, and it gives me a transfer rate at around 12mb/s (unstable rate). But when I had it installed in my machine, its back to a lousy 2 mb/s. 

Also, another observation is that, if I have a file created from Ubuntu, (eg. The downloaded Opensuse .ISO) and I transfer those files onto the same media on USB, the write speed can be as fast as 2X mb/s. ^^"

---

### Post by Azraele on 2009-12-13
> **BkKen said:**
> Yes pls, I would love to do that if it helps this community. Would you mind guiding me how I could make that happen? 

One funny observation I had lately is this (not sure if everyone shares the same). I tried Mint on a Live USB, and it gives me a transfer rate at around 12mb/s (unstable rate). But when I had it installed in my machine, its back to a lousy 2 mb/s. 

Also, another observation is that, if I have a file created from Ubuntu, (eg. The downloaded Opensuse .ISO) and I transfer those files onto the same media on USB, the write speed can be as fast as 2X mb/s. ^^"

You go to this site and do what you have to. People better than me will help you through the process.  

[https://bugs.launchpad.net/](https://bugs.launchpad.net/)

but as you can see they're already working on it :

[https://bugs.launchpad.net/ubuntu/+source/linux/+bug/197762](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/197762)
 
But still they don't seem to have any solution. :D

---

### Post by rom85 on 2009-12-14
> **Azraele said:**
> The only way of solving this is filing a bug report to the official channel. But it will be hard. I'm already doing this for another problem and even gettin' the programmers to look at it is difficult: 
file a bug report and then everybody has to quote the problem. Making it the official way is the only solution. Obviously you'll have to feed them information daily to make their work possible and to obtain solutions. Everybody has to collaborate.

there are by now so many bug reports that they are hardly answered. people, including me, have this very boring problem and ubuntu developers pay no attention at its presence. so what's the meaning of those lauchpads when no one reads.
it gets very inconvenient to use ubuntu because of this GREAT problem

---

### Post by Azraele on 2009-12-14
What can I say man? There are hundreds of os, choose one and install it: I'm sure not all the linux distros have this issue.
I have even installed windows 7, I use it for games, since gaming support on linux is shitty, it's pretty smooth, truly another planet from (s)vista. :popcorn:

(for those who are not italian and can't get the joke: 
in italian svista means mistake :D :D :D

truly the fate has sense of humor)

---

### Post by JoeSolo on 2009-12-14
I also experience a drastic slowdown in transfer rates when using a thumb drive.  But my transfer rates are normal when using an externally powered USB harddrive or a hardrive that takes power from one USB port and transfers data on another.

---

### Post by nomiz on 2009-12-14
My solution is to edit **/etc/initramfs-tools/module** to change the load order of the usb related modules:

**/etc/initramfs-tools/module**:
[FONT="Courier New"]# List of modules that you want to include in your initramfs.
#
# Syntax:  module_name [args ...]
#
# You must run update-initramfs(8) to effect this change.
#
# Examples:
#
# raid1
# sd_mod
 
ehci_hcd
uhci_hcd[/FONT]

This solved all my problems!

---

### Post by syborfical on 2009-12-15
that seemed to have improved performance a little bit its still faster for me to put one usb drive on my ubuntu 9.10 box formatted on EXT4

Then use a windows PC and connect my other external up.

With both drives plugged into my ubuntu box i get 11mb Woot !
Over the network about 10-30mb.

2 drives plugged into my windows machine 30-70mb.

before i did the fix above my USB drive would go on holidays some where :P id have to remount it or some times reboot!!!!

---

### Post by BkKen on 2009-12-16
Hi,

To [Azraele]("http://ubuntuforums.org/member.php?u=940892"): Thanks for the link, I'll go fiddle with it. :)

To nomiz: Would you mind guiding me a bit more about your solutions? I'm new to Linux commands. 


Thanks.

---

### Post by zimari on 2009-12-16
:lolflag:
I also have this problem and Like he say.

I would be nice with an copy and past "guide" for the terminal.

---

### Post by yavoh on 2009-12-21
Thanks for all of your investigation, everyone.  I've been chasing a slow printing problem since I moved from Win7 to Karmic (I'm a long-time *nix user, though I've never run Ubuntu specifically on my primary machine before now).

Basically, if I try to print any file above some size (I'm not sure what), my printer times out before it starts printing and the document never prints.  Could this be related to the USB speed issue, do you think?

I've been searching all the threads I can find and a lot of people are having slow printing problems in Ubuntu in general, but this is one route I haven't investigated.

---

### Post by potam on 2009-12-22
> **yavoh said:**
> Could this be related to the USB speed issue, do you think?

My printer has USB 1.1 port, so no notable slowdown. When my printer won't print is always because the cable.

---

### Post by R33D3M33R on 2009-12-22
[Azraele's solution]("http://ubuntuforums.org/showpost.php?p=8409097&postcount=47") worked for me, it improved the speed. I made a test and transfered a ~6,1GB file in 17 min 13 seconds, that means 6,03 MB/s average. That's good enough for me :)

But beware! You must manually add pci=acpi to grub.cfg after every kernel upgrade.

---

### Post by slumbergod on 2009-12-22
I think I tried every solution offered in the forums and online during hardy and jaunty. I just set up a dual boot Karmic - XP system and have discovered the same slow USB flash drive problem that plagues my system.

My feeling is that it is a kernel bug and it hasn't been fixed simply because it hasn't affected the people who work on the kernel. In three releases the bug has not been addressed. 

This is why I consistently wish that the existing issues get resolved BEFORE the devs rush off and introduce new features (and new bugs). I love Xubuntu and I have no intention of changing but when my fellow IT workers see how slow USB file transfers are in Linux they put another nail in the lid of Linux's coffin. In other words, this issue is enough of a problem to inhibit adoption of Linux as a serious alternative in this office environment. 

I would love to be able to contribute but my programming skills are so basic compared to the talents of the kernel guys.

---

### Post by Azraele on 2009-12-23
> **slumbergod said:**
> 
My feeling is that it is a kernel bug and it hasn't been fixed simply because it hasn't affected the people who work on the kernel. In three releases the bug has not been addressed. 


Exactly man, that's the point. 

Free software = no paying for a software which sucks the ****!!!

The programmers aren't paid, so they don't work on the software issues, and no one can blame 'em because food is not for free. That makes a buch of lazy and already fatigued men responsible for the developing of the software. This is not working for me.

---

### Post by sbec67 on 2009-12-24
i just love my ubuntu ;-)

i have reported a new Bug report (#500069) , with all debug informations.
Please also take some time to debug you issue, and open a report.

description of how to get debug informations you fine here:
[https://help.ubuntu.com/community/DiskPerformance]("https://help.ubuntu.com/community/DiskPerformance")

Regards
Sbec

---

### Post by MrPotter on 2009-12-25
I noticed something with the activated PCI IRQ routing option in the menu.lst (pci=acpi). My USB device is connected during the boot procedure to my pc. After the system is started completely, I'm able to copy files with full speed to the mass storage. But, after I unmount the device and mount it again, the transferrate is very slow (~500kbit/s).
Can somebody confirm that?

---

### Post by Azraele on 2009-12-26
> **sbec67 said:**
> 
Please also take some time to debug you issue, and open a report.

description of how to get debug informations you fine here:
[https://help.ubuntu.com/community/DiskPerformance]("https://help.ubuntu.com/community/DiskPerformance")

Regards
Sbec

I'm already on a nautilus bug, confirmed and filed the necessary infos, still nobody gives a ****.

---

### Post by potam on 2010-01-02
Three months since Karmic released, and this major bug still exists. Come on!

---

### Post by sbec67 on 2010-01-02
go to the Bug 
( [https://bugs.launchpad.net/ubuntu/+source/linux/+bug/500069]("https://bugs.launchpad.net/ubuntu/+source/linux/+bug/500069") )
and click, that it also affects you also.

The More People it affects, the faster the will work on it ( i guess ;-) )

---

### Post by imwithid on 2010-01-03
> **MrPotter said:**
> I noticed something with the activated PCI IRQ routing option in the menu.lst (pci=acpi). My USB device is connected during the boot procedure to my pc. After the system is started completely, I'm able to copy files with full speed to the mass storage. But, after I unmount the device and mount it again, the transferrate is very slow (~500kbit/s).
Can somebody confirm that?

That is interesting. I think I'll go ahead and test that hypothesis tomorrow when I reboot my system. I do recall that sometimes my USB flash drive show's a generic drive name and at others a XXXX-XXXX name. Maybe I'm wrong. I want to test this to retain some sanity and perhaps pay greater attention to these little things in hopes of helping solve these problems.

I'll end up staying with 9.10 for a couple more weeks until the next alpha of 10.04. I'll give this problem another go and see if it's just a simple problem blown out of proportion.

---

### Post by imwithid on 2010-01-06
I've tried several ways of using my USB key. I've left it in when I power on the computer, I plugged it in after boot up, demounting and mounting the device and so far the only thing that causes problems is that if I have been running applications for some time (greater than an hour perhaps or using more than half of the memory resources at a time), the transfer rate comes crashing down.

However, if it is the first device that I access after boot, no matter what applications I open (so far tested - I've opened up Opera which as of late has been a memory hog and mprime which heavily relies on CPU usage), it seems that the transfer rates remain steadily high. I will leave the system running for the next couple of hours to run a few more tests noting which applications I use and their duration.

---

### Post by MrPotter on 2010-01-07
> **imwithid said:**
> However, if it is the first device that I access after boot, no matter what applications I open (so far tested - I've opened up Opera which as of late has been a memory hog and mprime which heavily relies on CPU usage), it seems that the transfer rates remain steadily high. I will leave the system running for the next couple of hours to run a few more tests noting which applications I use and their duration.

Don't know what's happened, but now I have exactly the same behaviour. After boot, I'm able to copy, dismount, mount with almost always full speed. The first transfer-process is the fastest (~12MB/s). The second and the following have a speed up to 3-4 MB/s.
But if I start a file-transfer with some open programs (browser, video player, etc.), the speed declines to the well-known few bytes per second. 

I started another file-transfer as the RAM percentage usage was between 55%-60%. Result: mouse dropouts, slow transfer-rate. Then I closed all open programs and I was able to see how the transfer rate slowly speed up. More transfer tests confirms that there really is a malfunction with the RAM usage. Can you also confirm that on your machine?

I think its better to run memtest to exclude possible hardware problems.

---

### Post by R33D3M33R on 2010-01-07
I just installed the 2.6.32.3 kernel (get it here: [http://kernel.ubuntu.com/~kernel-ppa/mainline/v2.6.32.3/](http://kernel.ubuntu.com/~kernel-ppa/mainline/v2.6.32.3/)) and the speed greatly improved: 10 MB/s average. There are no hacks needed anymore.

To install download the correct packages for your architecture (AMD64 or i386) to a folder, open up a terminal window in the folder and run:

```
sudo dpkg -i *
```

After that, don't forget to reboot!

---

### Post by imwithid on 2010-01-07
> **MrPotter said:**
> Don't know what's happened, but now I have exactly the same behaviour. After boot, I'm able to copy, dismount, mount with almost always full speed. The first transfer-process is the fastest (~12MB/s). The second and the following have a speed up to 3-4 MB/s.
But if I start a file-transfer with some open programs (browser, video player, etc.), the speed declines to the well-known few bytes per second. 

I started another file-transfer as the RAM percentage usage was between 55%-60%. Result: mouse dropouts, slow transfer-rate. Then I closed all open programs and I was able to see how the transfer rate slowly speed up. More transfer tests confirms that there really is a malfunction with the RAM usage. Can you also confirm that on your machine?

I think its better to run memtest to exclude possible hardware problems.


This is in line with my experience. As soon as the memory usage reaches some point(>50%), my transfer rates crash down to a few kb/s. Upon closing all applications, the transfer rates resume to their normal (approx. 6MB/s long run) speed.

I would attempt to install a new kernel as stated by r33d3m33r, however, could this cause other unintended problems?

---

### Post by MrPotter on 2010-01-08
> **imwithid said:**
> 
I would attempt to install a new kernel as stated by r33d3m33r, however, could this cause other unintended problems?

This kernel version is a [MainlineBuild]("https://wiki.ubuntu.com/KernelTeam/MainlineBuilds"). It might be possible that you get some driver conflicts. 

But you don't need to bother. I installed that Kernel Version and I have the same problems. By the way, memtest found no memory errors ...

---

### Post by imwithid on 2010-01-22
> **MrPotter said:**
> This kernel version is a [MainlineBuild]("https://wiki.ubuntu.com/KernelTeam/MainlineBuilds"). It might be possible that you get some driver conflicts. 

But you don't need to bother. I installed that Kernel Version and I have the same problems. By the way, memtest found no memory errors ...



I've run memtest86+ as well as a full torture test by prime95 (mprime in linux) with no errors.

It's an interesting point you bring up with mainline kernels. I had no idea. Either way, I don't really bother with them anymore since the xorg fiasco a couple of Ubuntu releases back was more or less fixed.

---

### Post by yunone on 2010-01-23
bought a faster usb drive... Patriot XT 8 GB, the red stripe one... NTFS format, 4k block size

win 7 test 32 Bit
3.6 GB from Win7 HD to USB stick=lowest speed recorded 16 MB/S

Ubuntu 9.10
3.6 GB from Karmic to USB stick=lowest speed recorded 9 MB/s

same file
same usb stick= 200x <30 MB/s>


the speeds i am posting represent the lowest speed recorded and typically the speed that was recorded at time of file transfer completion

---

### Post by Catscrash on 2010-01-28
same problem here, drops from 30mb/s down to 5-6mb/s in ubuntu, not so in windows...

does that only happen with ntfs, or also with usb-ext3/4 drives?

---

### Post by 64bitguy on 2010-01-28
Hi folks

Well, I'm in the same situation.  My speed times for USB Transfers on my 16GB Kingston stick under Windows XP are about 22MB/s; whereas under a clean version of Ubuntu 9.10 on the same computer (I pull the primary 80GB, 5400RPM 2.5" IDE XP boot drive from the laptop and replace it with a 7200RPM 2.5" IDE Boot Drive with Ubuntu Karmic using EXT4) and the tranfer rates on the same stick drops to about 2MB/s  That's a huge performance drop folks!  I've tried changing the stick partition to every known format and get basically the same performance (FAT, EXT3, EXT4 makes little if any difference).

Sooooo... After reading posts on this subject going back... well.. over a year (in about 100 different threads here alone!), I'm befuddled as what to do (after trying like 20 different things including bug report suggestions)..  I must ponder, is anyone taking this issue seriously?  Given the "Medium" level of the various bug reports, I must wonder.  I mean, I can't really use Linux (Ubuntu) with these kinds of transfer USB rates and I suspect that I'm not alone.  **I think a 90% degradation in USB I/O and File System performance is a serious core OS issue that someone should be looking at! ** But that's just my Two cents.  With that in mind, it would be great if someone (somewhere) were interested in at least escalating the existing bug reports to "Serious".  

:)

---

### Post by abowyer1540 on 2010-01-28
I'm also getting slow usb transfer rates, approximately 880 KB/sec.

Ignore, I found this pc has USB1.1.  On a separate PC I'm up to 13 MB/s

---

### Post by no2498 on 2010-01-28
its in the unmount of some thing dont ask how i just found it

---

### Post by no2498 on 2010-01-28
you do not see it the day you do it

---

### Post by Niksko on 2010-02-22
I'm probably a bit late to the party, but Azraele's method of adding pci=acpi to the boot options list worked like a charm.

Thanks, and hopefully 10.04 is more stable and well rounded, as 9.10 has proved a massive pain for me.

-Nik

---

### Post by jahja on 2010-02-22
I also get this problem, 

usually levels out at about 1mb/sec. 

I noticed it today (I haven't used the USB stick before) and I installed about 2 weeks ago. 

I tried upgrading to the latest kernel - 2.6.32 - to see if that would beat it...seems to have made my wireless smoother and a couple of other things, but no difference to the speed of the USB.

I'm sure some kind person is dedicating some time to sorting this somewhere, so all praise - for me, this is no-where NEAR enough of an annoyance to switch back to winblows as some people would suggest :) Plan those overnight file transfers lol...

E2A: This is true for me with a 16gb kingston stick, or a 2gb generic cheapie. Processor use to 100% and memory also at 100%, although the system doesn't run at all slow, the transfers are ridiculous, settling at about 1.5mb second to usb. All the rest of my system seems sweet enough....any ideas  anyone??

---

### Post by pepa_u on 2010-03-06
I have the same trouble with 500GB SATA  to USB drive (Ubuntu 9.10, kernel 2.6.31-20-generic). In case that all is fine, dmesg reports:

[43362.890185] usb 2-1: new high speed USB device using ehci_hcd and address 43
[43363.044422] usb 2-1: configuration #1 chosen from 1 choice
[43363.060674] scsi20 : SCSI emulation for USB Mass Storage devices
[43363.060958] usb-storage: device found at 43
[43363.060963] usb-storage: waiting for device to settle before scanning
[43368.060349] usb-storage: device scan complete
[43368.063812] scsi 20:0:0:0: Direct-Access     WDC WD50 00AACS-00ZUB0         PQ: 0 ANSI: 2
[43368.064672] sd 20:0:0:0: Attached scsi generic sg2 type 0
[43368.084131] sd 20:0:0:0: [sdb] 976773168 512-byte logical blocks: (500 GB/465 GiB)
[43368.087006] sd 20:0:0:0: [sdb] Write Protect is off
[43368.087008] sd 20:0:0:0: [sdb] Mode Sense: 38 00 00 00
[43368.087011] sd 20:0:0:0: [sdb] Assuming drive cache: write through
[43368.091546] sd 20:0:0:0: [sdb] Assuming drive cache: write through
[43368.091550]  sdb:
[43369.950303] usb 2-1: reset high speed USB device using ehci_hcd and address 43
[43375.140088] usb 2-1: reset high speed USB device using ehci_hcd and address 43
[43379.991567]  sdb1
[43380.004579] sd 20:0:0:0: [sdb] Assuming drive cache: write through
[43380.004592] sd 20:0:0:0: [sdb] Attached SCSI disk

However, it sometimes connects OK like, but then during data transfer happens (dmesg report again):

[43469.830206] sd 20:0:0:0: [sdb] Unhandled error code
[43469.830216] sd 20:0:0:0: [sdb] Result: hostbyte=DID_ERROR driverbyte=DRIVER_OK
[43469.830226] end_request: I/O error, dev sdb, sector 138382152
[43469.830238] Buffer I/O error on device sdb1, logical block 17297513
[43469.830250] Buffer I/O error on device sdb1, logical block 17297514
[43469.830257] Buffer I/O error on device sdb1, logical block 17297515
[43469.830265] Buffer I/O error on device sdb1, logical block 17297516
[43469.830272] Buffer I/O error on device sdb1, logical block 17297517
[43469.830279] Buffer I/O error on device sdb1, logical block 17297518
[43469.830286] Buffer I/O error on device sdb1, logical block 17297519
[43469.830294] Buffer I/O error on device sdb1, logical block 17297520
[43469.830301] Buffer I/O error on device sdb1, logical block 17297521
[43469.830308] Buffer I/O error on device sdb1, logical block 17297522
[43469.830432] sd 20:0:0:0: [sdb] Unhandled error code
[43469.830437] sd 20:0:0:0: [sdb] Result: hostbyte=DID_ERROR driverbyte=DRIVER_OK
[43469.830445] end_request: I/O error, dev sdb, sector 138382392
[43469.830527] sd 20:0:0:0: [sdb] Unhandled error code
[43469.830533] sd 20:0:0:0: [sdb] Result: hostbyte=DID_ERROR driverbyte=DRIVER_OK
[43469.830540] end_request: I/O error, dev sdb, sector 138382408
[43469.830650] sd 20:0:0:0: [sdb] Unhandled error code
[43469.830655] sd 20:0:0:0: [sdb] Result: hostbyte=DID_ERROR driverbyte=DRIVER_OK
[43469.830663] end_request: I/O error, dev sdb, sector 138382648
[43469.830698] usb 2-1: USB disconnect, address 43
[43470.050041] usb 5-1: new full speed USB device using uhci_hcd and address 7
[43470.181270] usb 5-1: device descriptor read/64, error -71
[43470.422901] usb 5-1: device descriptor read/64, error -71
[43470.650394] usb 5-1: new full speed USB device using uhci_hcd and address 8
[43470.780100] usb 5-1: device descriptor read/64, error -71
[43471.020096] usb 5-1: device descriptor read/64, error -71
[43471.250276] usb 5-1: new full speed USB device using uhci_hcd and address 9
[43471.670137] usb 5-1: device not accepting address 9, error -71
[43471.792613] usb 5-1: new full speed USB device using uhci_hcd and address 10
[43472.210104] usb 5-1: device not accepting address 10, error -71
[43472.210143] hub 5-0:1.0: unable to enumerate USB device on port 1

And the drive is lost. Often, it does not connect as a high speed USB from the beginning:

[42234.062632] usb 5-1: new full speed USB device using uhci_hcd and address 5
[42239.209478] usb 5-1: not running at top speed; connect to a high speed hub

I am little bit suspicious that also hardware takes part in this, though. I am using HP Pavilion dv2637tx and Windows (vista) had troubles to connect external USB drives on the full speed too sometimes.

---

### Post by HeadHunter00 on 2010-03-20
the problem is not only in ubuntu, but also arch linux. i figured that it's nautilus that has been slowing speed down. instead of directly copying files and folders using nautilus, either use thunar or the cp command. i get a constant write speed of about 17 mb/s using the cp command and 11 mb/s using thunar.

---

### Post by sensory on 2010-03-26
This is still a major problem for a lot of people, including me.

---

### Post by potam on 2010-03-28
> **sensory said:**
> This is still a major problem for a lot of people, including me.

That's why I had to uninstall Ubuntu. I copy files frequently to flash drives. It is unacceptable for me to wait 20 minutes for one 700 MB file, instead of 1 minute.

---

### Post by elclanrs on 2010-03-29
These needs to be fixed I just noticed today cuz I never trasfered a large file to my pen, but it took like 20 min to copy a 600mb file. On Windows I transfered the same file in 4 min.

---

### Post by togume on 2010-04-01
Confirming this issue. I've experienced this for a long time. I just tried copying a 1.4GB file to a cruizer micro. It transfered 350ish MB in a couple seconds, then slowly coasted down to 800KB/s.

---

### Post by Ryanmt on 2010-04-11
Another bump, can this please be fixed. its a real headache!

---

### Post by NKK on 2010-04-16
I see same problem only with VFAT filesystem, but not with usb stick formatted to NTFS/ext3/ext4

---

### Post by airplus on 2010-04-24
Same problem here.

I am in 9.10, I am copying a 3.5GB file to a Western Digital external HD.

One hour and it is still 60% at 844k/s. 

This can't be good... :(

EDIT: this is too much, almost two hours and still not copied??? I need to go to sleep!!

I had to restart, boot into XP and copy the file in TWO MINUTES!!!! 

[IMG]http://img408.imageshack.us/img408/4681/usbxp.jpg[/IMG]

Well, I have to keep updating the old trusty XP... :shock:  Ubuntu is not ready yet for the prime time it seems :( :-k

---

### Post by kmrdeva on 2010-04-25
I have a PC running Mint 8 64bit and a laptop running Ubuntu 10.04 RC 64bit - both seem to have the same USB2 transfer problem.

Have recently upgraded to the 2.6.33 kernel (2.6.34 is only RC5 at present) on both computers. USB2 transfers seem to be ok but I will need more time to monitor this.

Got my kernels from [http://kernel.ubuntu.com/~kernel-ppa/mainline/](http://kernel.ubuntu.com/~kernel-ppa/mainline/)

---

### Post by darkshines87 on 2010-04-25
Hi!

I can confirm that this is an issue for me, too. I tried that one solution with adding scheduler options to the kernel boot, but none did any good.

```

uname -a
Linux p-ubuntu 2.6.31-20-generic #58-Ubuntu SMP Fri Mar 12 04:38:19 UTC 2010 x86_64 GNU/Linux

```

---

### Post by philodice on 2010-04-25
Just to weigh in, not sure if this will help, but I'm running Karmic netbook remix and haven't noticed slow usb, slow mouse, or slow data transfer of any kind.  Perhaps it is related to some machine + distro compatibility.  The Acer seems made for Ubuntu.

---

### Post by skogs on 2010-05-02
Another vote of no confidence.  Running 10.04, still no change in default usb configuration.  Pushing ~9Gigs of data from an ntfs USB drive over the network to samba share yields 2MB transfer speed.  
This has been an issue only with ubuntu for many years now.  I can't believe that there isn't somebody with brains involved that periodically transfers decent amounts of data around.  Really...if I had the brains I'd fix it because it drives me up the wall.  Exact same hardware, rebooted into XP or Vista runs 12MB/s over the network...exactly where it should be for a 100Mb line.  God forbid I try to run it at gig speed.  
I have heard this blamed on:

[LIST]
[*]mounting with on access file update turned on/off in fstab
[*]gnome's vfs system
[*]samba server
[*]windows server
[*]RAM/swap
[*]kernel modules
[*]acpi
[*]IRQ / pcirouteirq
[*]slow flash drives
[*]slow hard drives
[*]hardware drivers
[*]and probably a few I don't remember
[/LIST]
Now that I've finally got ATI drivers that work fully (or at least appear to), this is the ONLY major problem I can find.  Except maybe the default min/max/close on the left hand side.  :)

---

### Post by wesman83 on 2010-05-08
is ANYBODY working to fix this? its the most frustrating bug 	:-x

---

### Post by Badcam on 2010-05-08
I too have this problem.

```

lsusb
Bus 009 Device 002: ID 046d:c016 Logitech, Inc. M-UV69a/HP M-UV96 Optical Wheel Mouse
Bus 009 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 011 Device 002: ID 0951:1625 Kingston Technology 
Bus 011 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 010 Device 004: ID 0781:7435 SanDisk Corp. 
Bus 010 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 008 Device 003: ID 0556:0001 Asahi Kasei Microsystems Co., Ltd AK5370 I/F A/D Converter
Bus 008 Device 002: ID 046d:08c5 Logitech, Inc. QuickCam Pro 5000
Bus 008 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 005 Device 002: ID 0518:0001 EzKEY Corp. USB to PS2 Adaptor v1.09
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 006 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 007 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
badcam@badcam-desktopblack ~ $ sudo modprobe -r ehci_hcd
[sudo] password for badcam: 
FATAL: Module ehci_hcd not found.
badcam@badcam-desktopblack ~ $ sudo modprobe -a ehci_hcd
WARNING: Module ehci_hcd not found.
badcam@badcam-desktopblack ~ $ sudo dmesg | grep echi_hcdIf
badcam@badcam-desktopblack ~ $ sudo dmesg | grep usb
[    0.131115] usbcore: registered new interface driver usbfs
[    0.131132] usbcore: registered new interface driver hub
[    0.131164] usbcore: registered new device driver usb
[    0.828109] usb usb1: configuration #1 chosen from 1 choice
[    0.840080] usb usb2: configuration #1 chosen from 1 choice
[    0.852081] usb usb3: configuration #1 chosen from 1 choice
[    0.852412] usb usb4: configuration #1 chosen from 1 choice
[    0.852665] usb usb5: configuration #1 chosen from 1 choice
[    0.852909] usb usb6: configuration #1 chosen from 1 choice
[    0.853147] usb usb7: configuration #1 chosen from 1 choice
[    0.853402] usb usb8: configuration #1 chosen from 1 choice
[    0.853659] usb usb9: configuration #1 chosen from 1 choice
[    0.853901] usb usb10: configuration #1 chosen from 1 choice
[    0.854156] usb usb11: configuration #1 chosen from 1 choice
[    2.608014] usb 5-1: new low speed USB device using uhci_hcd and address 2
[    2.817563] usb 5-1: configuration #1 chosen from 1 choice
[    2.831114] usbcore: registered new interface driver hiddev
[    2.846492] input: Plus More Enterprise LTD. USB-compliant keyboard as /devices/pci0000:00/0000:00:1d.1/usb5/5-1/5-1:1.0/input/input3
[    2.846588] generic-usb 0003:0518:0001.0001: input,hidraw0: USB HID v1.10 Keyboard [Plus More Enterprise LTD. USB-compliant keyboard] on usb-0000:00:1d.1-1/input0
[    2.865519] input: Plus More Enterprise LTD. USB-compliant keyboard as /devices/pci0000:00/0000:00:1d.1/usb5/5-1/5-1:1.1/input/input4
[    2.865615] generic-usb 0003:0518:0001.0002: input,hidraw1: USB HID v1.10 Mouse [Plus More Enterprise LTD. USB-compliant keyboard] on usb-0000:00:1d.1-1/input1
[    2.865637] usbcore: registered new interface driver usbhid
[    2.865641] usbhid: v2.6:USB HID core driver
[    3.068019] usb 8-1: new full speed USB device using uhci_hcd and address 2
[    3.222341] usb 8-1: not running at top speed; connect to a high speed hub
[    3.384458] usb 8-1: configuration #1 chosen from 1 choice
[    3.624065] usb 8-2: new full speed USB device using uhci_hcd and address 3
[    3.807451] usb 8-2: configuration #1 chosen from 1 choice
[    4.052025] usb 9-2: new low speed USB device using uhci_hcd and address 2
[    4.227699] usb 9-2: configuration #1 chosen from 1 choice
[    4.243852] input: Logitech Optical USB Mouse as /devices/pci0000:00/0000:00:1e.0/0000:02:01.1/usb9/9-2/9-2:1.0/input/input5
[    4.243950] generic-usb 0003:046D:C016.0003: input,hidraw2: USB HID v1.10 Mouse [Logitech Optical USB Mouse] on usb-0000:02:01.1-2/input0
[    4.484024] usb 11-1: new full speed USB device using uhci_hcd and address 2
[    4.629153] usb 11-1: not running at top speed; connect to a high speed hub
[    4.663277] usb 11-1: configuration #1 chosen from 1 choice
[    4.904022] usb 11-2: new full speed USB device using uhci_hcd and address 3
[    5.062269] usb 11-2: configuration #1 chosen from 1 choice
[   17.674365] usbcore: registered new interface driver usb-storage
[   17.694956] usb-storage: device found at 2
[   17.694961] usb-storage: waiting for device to settle before scanning
[   17.768406] usbcore: registered new interface driver sonixj
[   17.802341] input: UVC Camera (046d:08c5) as /devices/pci0000:00/0000:00:1e.0/0000:02:01.0/usb8/8-1/8-1:1.0/input/input6
[   17.802421] usbcore: registered new interface driver uvcvideo
[   17.944726] usbcore: registered new interface driver snd-usb-audio
[   22.774395] usb-storage: device scan complete
[148279.860024] usb 10-2: new full speed USB device using uhci_hcd and address 2
[148280.010054] usb 10-2: not running at top speed; connect to a high speed hub
[148280.050201] usb 10-2: configuration #1 chosen from 1 choice
[148280.060318] usb-storage: device found at 2
[148280.060320] usb-storage: waiting for device to settle before scanning
[148285.068890] usb-storage: device scan complete
[150618.256060] usb 10-2: USB disconnect, address 2
[151772.452056] usb 10-2: new full speed USB device using uhci_hcd and address 3
[151772.605684] usb 10-2: not running at top speed; connect to a high speed hub
[151772.643973] usb 10-2: configuration #1 chosen from 1 choice
[151772.656843] usb-storage: device found at 3
[151772.656846] usb-storage: waiting for device to settle before scanning
[151777.665103] usb-storage: device scan complete
[153839.528091] usb 10-2: USB disconnect, address 3
[154044.135598] usb 10-2: new full speed USB device using uhci_hcd and address 4
[154044.294090] usb 10-2: not running at top speed; connect to a high speed hub
[154044.332212] usb 10-2: configuration #1 chosen from 1 choice
[154044.347598] usb-storage: device found at 4
[154044.347603] usb-storage: waiting for device to settle before scanning
[154049.346206] usb-storage: device scan complete
[154993.720086] usb 11-2: USB disconnect, address 3
[155818.128081] usb 10-2: USB disconnect, address 4
[156037.796028] usb 10-2: new full speed USB device using uhci_hcd and address 5
[156037.941105] usb 10-2: not running at top speed; connect to a high speed hub
[156037.979263] usb 10-2: configuration #1 chosen from 1 choice
[156038.008829] usb-storage: device found at 5
[156038.008834] usb-storage: waiting for device to settle before scanning
[156043.010963] usb-storage: device scan complete
[156200.984072] usb 10-2: USB disconnect, address 5
[156269.920024] usb 10-2: new full speed USB device using uhci_hcd and address 6
[156270.071149] usb 10-2: not running at top speed; connect to a high speed hub
[156270.107776] usb 10-2: configuration #1 chosen from 1 choice
[156270.146849] usb-storage: device found at 6
[156270.146853] usb-storage: waiting for device to settle before scanning
[156275.156321] usb-storage: device scan complete
[156447.000078] usb 10-2: USB disconnect, address 6
badcam@badcam-desktopblack ~ $ sudo dmesg | grep ehci_hcdIf
badcam@badcam-desktopblack ~ $ sudo modprobe -r ehci_hcd
FATAL: Module ehci_hcd not found.
badcam@badcam-desktopblack ~ $ uname -a
Linux badcam-desktopblack 2.6.31-21-generic #59-Ubuntu SMP Wed Mar 24 07:28:56 UTC 2010 i686 GNU/Linux

```

---

### Post by nuzeb on 2010-05-13
I have the same annoying problem here with Ubuntu 10.4 on a Samsung NC10. DMESG says plugged in 2.0 devices are high speed usb using ehci_hcd. Which seems to be correct. But transfer rates (e.g. HDD) are between 2.0MB/s and a seldom maximum of 6MB/s.

I've tried everything hinted in all the forum posts and bug reports I found regarding to this matter. But nothing helped.

I often have to handle a lot of data and there seem to be no way to get around this problem. So I sadly have to use Windows now, which I don't like but doesn't have this specific issue.

It would be great, if someone could hint another possible solution or any hopeful words. Please let me know, if I can provide any further information to help solving this.

---

### Post by sanketmedhi on 2010-05-23
I have been using Ubuntu for AT LEAST 6 years and I don't remember a time when my USB drives have worked well, at least on my desktops/laptops. The argument that my hardware is old is not the answer, fact is that if my USB drives perform well on other OSs on the same hardware, they are expected to perform the same way on Ubuntu. I have been waiting for a fix for so many years, but never actually got something that could fix this. Its sad that such a popular and awesome OS like Ubuntu would have such a primitive problem for so long. I still hope a fix is released for this bug soon.

---

### Post by webbyone on 2010-07-15
Yea, same here try moving couple hundred gigs, it craps out completely. You would think with TB drive so readily available this problem would get a little more attention.

---

### Post by Dolfhin01 on 2010-08-03
This is very unacceptable, I have the same problem on 2 PC's!

After all this time we need a fix.

---

### Post by TwistedPriest on 2010-08-10
Pepa, make sure you let the drive spin up fully before plugging it in. I used to have the same problem for a while, but if I wait for the drive to get up to speed and do all of its self-tests it's recognized as full speed.

---

### Post by remerson on 2010-08-16
I have this issue too with Xubuntu 9.10 (2.6.31-22 generic); FAT32 device recognised as "full speed" according to /var/log/syslog.

I'm waiting many minutes for transfers that should take only a few seconds.

It seems there's some buffering issue; the first 20-50Mb or so is fast (> 20Mb/sec), but then slows to total crawl (< 1Mb/sec).

Can anyone recommend a distro where USB actually works properly, please?

---

### Post by ivanovnegro on 2010-11-22
So guys, I have the same problem and found this thread here, so Im not the only one, I posted another about this [here]("http://ubuntuforums.org/showthread.php?t=1628052") as I did not find this.
Its the first annoying thing that is really bad and Im seriously thinking about to switch to Windows to have the possibility to use my external USB device without problems as I need it. 
Before I did not notice the problem really as I had all my data on the notebook but some months ago I transferred it to the USB device because of space and now have this really weird experience. In general I noticed a slow down while transferring data but I could live  with it as I only made backups but now Im using my whole music library from the USB device and I have huge performance problems. When I want to transfer an amount of data the system slows dramatically down.
I love Linux and Ubuntu and now I have no idea what to do, I need a fix and for god sake I dont want to switch to Windows.

Edit: Im on 10.10

---

### Post by jatinps on 2010-12-24
I am having this issue on multiple laptops when copying to usb flash drives and sd cards. Starts out at 10mbps or so and then slows down to a few 100kbps - this leaves me waiting an hour or more for a measly 1-2gb data transfer!

---

### Post by simonedge on 2011-03-03
Time for a bump, I think. (it's... disconcerting that such an issue should be unresolved for so long)

Ubuntu Netbook Edition 10.10, kernel 2.6.35-27-generic

initial speeds of about 13mb/s for about fifty percent of the file (650mb video), dropping to about 3mb/s thereafter. Not to mention that wait when the transfer is reported as complete.

The above was with a bog-standard FAT pendrive.
Formatting the drive to EXT4 and transferring the same file again yielded an initial speed boost (closer to 20mb/s) until, again, about 50% of the file had been transferred. Te speed then tailed off slowly to about 7mb/s, but I wasn't left waiting when the transfer had finished.

---

### Post by imwithid on 2011-06-01
> **simonedge said:**
> Time for a bump, I think. (it's... disconcerting that such an issue should be unresolved for so long)

Ubuntu Netbook Edition 10.10, kernel 2.6.35-27-generic

initial speeds of about 13mb/s for about fifty percent of the file (650mb video), dropping to about 3mb/s thereafter. Not to mention that wait when the transfer is reported as complete.

The above was with a bog-standard FAT pendrive.
Formatting the drive to EXT4 and transferring the same file again yielded an initial speed boost (closer to 20mb/s) until, again, about 50% of the file had been transferred. Te speed then tailed off slowly to about 7mb/s, but I wasn't left waiting when the transfer had finished.

I think your problem may require a separate thread. I think this thread, by definition, is dead as this was primarily a Karmic issue. It was resolved in Lucid, as far as I remember.

---

### Post by santiagorf on 2011-07-15
same problem here, my usb ends up transferring at <1Mb/s, really annoying. I'm using Linux Mint Helena (Ubuntu Karmic).

---

### Post by pommie on 2011-07-15
I have had this problem since Hoary, two laptops and four desktops later still not fixed, not holding my breath,

usb3 transfer speeds of 3MBps:confused:

Cheers David

---

### Post by potam on 2011-07-16
I can't believe this issue was still not fixed. That's why I had to switch back to Windows. Unbelievable that this problem still exists...

---

### Post by ajarmoniuk on 2011-10-21
I've just saw a bug report marked as Wont-Fix because it was reported against Karmic and the support for it has ended :D

Anyway, have a look at this:

[http://mailman.archlinux.org/pipermail/arch-general/2010-June/014470.html](http://mailman.archlinux.org/pipermail/arch-general/2010-June/014470.html)

---

### Post by Digital_Man on 2012-05-06
Well, it may be better for me to start my own thread on this subject, but my issue is exactly the same as the initial poster of this thread, only on Precise as opposed to Karmic.

I ran 32bit Ubuntu for years without any problems but now with my upgrade to 64bit Precise, everything is running smoothly except this infuriating USB speed transfer issue. Any suggestions? Has there been any firm resolution to this issue on Ubuntu yet?

**_UPDATE_**
Strange - I struggle with the problem all evening, and no sooner do I post about it that I think I've found somewhat of a solution....

The answer lies in the formatting/partitioning of the USB sticks. The sticks I had been using were formatted to NTFS, but using the Ubuntu Disk Utility, I could see that partition type of the volume was "w95 FAT32 (0x0b)." Disk Utility will allow you to edit the partition, but that didn't seem to work for me. I unmounted the USB, deleted the partition, and then formatted the stick with Disk Utility and selected "Don't Partition" as the scheme. I've tried formatting it with both FAT (32bit) and NTFS and both seem to work well on my Ubuntu 12.04 64bit.... and the FAT versions seemed to transfer particularly fast.

The moral of my story? Format your USB drives without partitions and you should be alright. There may better answers out there, but that's what seems to work for me. On the downside, problems may arise if you receive a USB from someone that has a partioned volume, but formatting the drives without a partition will serve the majority of my own needs. I can live with that.

---

### Post by techvish81 on 2012-07-12
i did everything from adding pci=acpi to formatting the usb in all possible ways and nothing is working, and the strange part of the story is, it works when it wants to but not everytime we copy. sometimes it works as if there is no problem while sometimes it just crawls and hangs and all that described earlier. i don't know what is this happening and think that this is a LTS , so 12.04.1 may solve the problem.

if anyone has found any solution that works on precise 64 , please share it here.

---

### Post by oldos2er on 2012-07-12
Old thread closed. Please start a new thread for your question.

---

