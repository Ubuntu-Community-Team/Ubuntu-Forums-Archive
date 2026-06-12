---
title: "Errno 5 Input/Output error"
date: 2009-04-28
forum: Installation &amp; Upgrades
---

### Post by screaminj3sus on 2009-04-28
Ok, I get this Errno5 error EVERY time I've tried to install the 9.04 final. I had previously used the beta and it installed fine. I burned 2 cds with 2 different isos (redownloaded them) and even redownloaded it AGAIN and used a live USB, BUT EVERY DAMN TIME ERRNO5. same spot. without fail.

---

### Post by screaminj3sus on 2009-04-28
WTF downlaoded it again via bittorrent this time so I know the hash matches. Installed via usb with a differtn drive and usb slot STILL THE SAME DAMN ERROR.

THIS IS RETARDED

---

### Post by Psyphre on 2009-04-30
Same issue. Its 23% every single time. I had this issue with hardy. All other ubuntu versions from edgy to intrepid worked perfectly. HArdy and Jaunty have this issue for me.
I'm desperately look for a solution.

---

### Post by vobadm on 2009-04-30
I had the same problems. 
Checked Hard drive - no problems
Checked MD5checksum - no problem
reformated harddrive - no success
reburned cd at low speed - no success
burned on DVD - no success

at one point I pulled out my CD-ROM Drive from my LAPTOP and put it back in - success. Worked like a charm.

I read in other threads that some people removed some RAM bars which helped them.... a miracle.

So it seems it is always somewhat hardware related...

just my 50 cent

---

### Post by Psyphre on 2009-04-30
the ram one is new to me. Will try that and post results.

---

### Post by Psyphre on 2009-04-30
it worked!! thanks alot for the advice. The original poster should try it too.

---

### Post by paulita on 2009-05-03
Mmmm the ram thing didn't work for me... I thought maybe it could be something to do with my TV card, so I took it away but didn't work either.
I tried burning more than one cd image at different speeds and didn't work. Tried booting from a memory stick and the same error appears after a 44% of the installation as it always does.
This is making me sick! 
Please, I need some help...
Thanks

---

### Post by Abilnet on 2009-05-05
**Solved for me!**

I got thr same "(Errno 5)input/output error" all the time (at 56% mark of the install) what ever I did. Then I tried to flash Netbook Remix -version to my USB -stick. That made the trick and installation succeed! (maybe there's some bug in the ISO writing to USB stick, but flashing the IMG works?)

So, one possible solution is to install Netbook Remix -version of Ubuntu 9.04

Good luck from Sunny Spain!

---

### Post by paulita on 2009-05-08
Finally i decided to install ubuntu 8.04 from de cd (everything went perfect) and upgrated to 8.10 and then to 9.04. Ubuntu Jaunty is working perfectly (except that i have no audio on tvtime... but that's other issue).
Thanks anyway

---

### Post by tmarshall57 on 2009-05-17
I had the same error repeatedly. As a last resort I put the Ubuntu CD in the Toshiba DVD-ROM drive on my PC instead of the Sony DVD-RW drive. It loaded perfectly.

I had previously burned an additional copy of the CD at 4x speed, cleaned the CD etc - all to no avail.

---

### Post by TheTechFan on 2009-05-17
I had this error repeatedly when I tried to install after selecting the "Try Ubuntu without installing" option on the live CD. Everything worked fine after selecting the "Install now" option instead on the same CD.
Give it a try.

---

### Post by HarleyJoel on 2009-05-25
I'm trying to install Ubuntu Netbook Remix from a usb and I'm getting this error each time. Tried another download and same exact problem. Each fresh install I do on other machines seem to go well. The problem seems to be when I try to reinstall over an existing version. Can't remove ram and I don't have a CD/DVD drive.

Update: I downloaded the image via torrent and it installed without any problems.

---

### Post by jabrwoky on 2009-06-10
Just wanted to report success at installing 9.04 after trying many different things.
Tried burning CD as slower speed. Tried removing one of my memory chips, tried burning on a different machine. Finally yanked my CD drive and put in a spare, worked first time. The drive I pulled was a Toshiba TS-H552L DVD R/RW. The one I put in was a Phillips DVD-ROM drive (just a reader).
Hope this helps.

---

### Post by SteveDee on 2009-06-24
I've installed 9.04 on 3 systems from the same disk (a CD).

I recently removed the hard drive from one of them and replaced it with a small, 40GB laptop drive. When I try to install 9.04 I get the input/output error with the install progress bar at 15%.

Tried all sorts of things including deleting the disk partition, creating a new partition & so on.

Eventually I tried to install Puppy Linux 4.12. The only problem I had was getting GRUB to work, but this was fixed with SuperGrub and now Puppy runs fine. So there must be something flakey with Ubuntu install that makes it intolerant of certain hardware configs.

---

### Post by garymax on 2009-08-18
It seems to be a very suspicious coincidence that all of these people who have had problems reportedly had to remove hardware that, otherwise, worked with earlier versions of Ubuntu.

I think it is something flakey with Ubuntu's installer.

I got the same error every time @ 22%. Then I would put a Slackware DVD in the drive and each and every time Slackware would parition, format and install to the hard drive without no errors whatsoever.

I think your solution is to either wait for a better Ubuntu release that has a better installer or switch to Slackware which runs perfectly on most all hardware.

Remember: if another distro works on the same hardware that you are having Ubuntu issues with, it isn't your hardware, it's Ubuntu.

And, really, why would you have to remove RAM just to install your favorite distribution????

---

### Post by Mazlaghan on 2009-09-01
hi there,

errno 5 error here too. never had any problems with installs before. i used a usb stick as well as i do not have a cd/dvd rom drive on my dell d400. i downgraded the iso to 8.04 and swoosh it worked. the only thing is that i found out at the end of the day so i have to wait till tomorrow to get my ubuntu machine back :(. 

this issue seems to be quite a major one. would be good if somebody could make a fix for it. not sure whether it's got to do with the media or the actual hardware your using. it was a bit annoying because i had to take the ram out (i have 1.25gb in my machine) so very slooooooooooow install on 256mb...

---

### Post by garymax on 2009-09-01
I must really like Ubuntu because I removed both optical drives in my 6+ yr old computer and replaced them with relatively new drives.

Ubuntu 9.04 installed without incident. Was it my hardware? Possibly. Or it could be a certain algorithm within the installer which causes it to be flakey with respect to hardware.

It's almost as if one has to really hope an install works and then they can breathe easy for 18 months until the next time.

I hope Canonical finds the cause and fixes this issue.

---

### Post by presence1960 on 2009-09-01
[http://ubuntuforums.org/showthread.php?t=1207755&page=2](http://ubuntuforums.org/showthread.php?t=1207755&page=2)  see post #20

please take note of a mispelling of the command in #4 of post 20

it should read:```
 ubiquity --no-migration-assistant
```

This worked for me on a client's rig when I kept getting the errno 5 error on install.

---

### Post by halsboss2 on 2009-09-19
Returning to ubuntu after a long break and was looking forward to it.  

So much for 9.04.  Load of crap, it won't install with downloaded WUBI.

Don't give me any crap about bad CDs and drives etc etc, they work PERFECTLY under windows and have done for a couple of YEARS !!!  

I've downloaded desktop version twice from the main site and burned it to 2 different CDs in slow mode and tried to install it from 2 different sata CD drives and get the same error.

Googled, and people dribble on about bad CDs and drives etc.  All rubbish.  If the drives work PERFECTLY EVERY TIME under Windows and the CDs check out OK but Ubuntu hates them ... what does that tell you about this install kit ?  Once guess.  

I'd like to try it out again, but no luck so far.  Anyone know of a REAL solution ?

---

### Post by scr9268 on 2009-09-28
Had to reload Ubuntu over the weekend when it's hard drive started acting up. (Being a telecom weenie, I maintain a slew of backups so I didn't lose anything I couldn't replace easily.)

Replaced the drive and figured I'd load 9.04.  Experienced the same errno 5 a number of times and tried as many different options as I could think of, incl a fresh Live CD, starting from the main live menu. No go.

Dropped back to 7.10 and it went right into the new drive. Tried 9.04 again. No go.

Loaded 8.04 onto the same drive, worked like a charm.

Tried 9.04 again from the main menu, went straight in without error.

Perhaps it's the fact that it's sunny out now.  Glad it's finally in; confused to no end as to an actual root cause.

I appreciate the heck out of all the guidance provided in this thread.

bl

---

### Post by pantone186 on 2009-09-28
What chip set are you using?

---

### Post by scr9268 on 2009-09-28
> What chip set are you using?

The other side of this is that I'm running Ubuntu on a Seagate external hard drive.  The host machine is a Dell PC with an Intel P4, 2.5gb of ram, runs Windows XP when not running Ubuntu.

Wasn't sure what exactly you were looking for, so here's the entire output from lspci -v. My apologies.

bill@bills-desktop:~$ lspci -v
00:00.0 Host bridge: Intel Corporation 82945G/GZ/P/PL Memory Controller Hub (rev 02)
	Subsystem: Dell Device 01d2
	Flags: bus master, fast devsel, latency 0
	Capabilities: <access denied>
	Kernel modules: intel-agp

00:01.0 PCI bridge: Intel Corporation 82945G/GZ/P/PL PCI Express Root Port (rev 02)
	Flags: bus master, fast devsel, latency 0
	Bus: primary=00, secondary=01, subordinate=01, sec-latency=0
	I/O behind bridge: 0000d000-0000dfff
	Memory behind bridge: efd00000-efefffff
	Prefetchable memory behind bridge: 00000000ec000000-00000000edffffff
	Capabilities: <access denied>
	Kernel driver in use: pcieport-driver
	Kernel modules: shpchp

00:1c.0 PCI bridge: Intel Corporation 82801G (ICH7 Family) PCI Express Port 1 (rev 01)
	Flags: bus master, fast devsel, latency 0
	Bus: primary=00, secondary=02, subordinate=02, sec-latency=0
	Memory behind bridge: efc00000-efcfffff
	Capabilities: <access denied>
	Kernel driver in use: pcieport-driver
	Kernel modules: shpchp

00:1d.0 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #1 (rev 01)
	Subsystem: Dell Device 01d2
	Flags: bus master, medium devsel, latency 0, IRQ 21
	I/O ports at ff80 [size=32]
	Kernel driver in use: uhci_hcd

00:1d.1 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #2 (rev 01)
	Subsystem: Dell Device 01d2
	Flags: bus master, medium devsel, latency 0, IRQ 22
	I/O ports at ff60 [size=32]
	Kernel driver in use: uhci_hcd

00:1d.2 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #3 (rev 01)
	Subsystem: Dell Device 01d2
	Flags: bus master, medium devsel, latency 0, IRQ 18
	I/O ports at ff40 [size=32]
	Kernel driver in use: uhci_hcd

00:1d.3 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #4 (rev 01)
	Subsystem: Dell Device 01d2
	Flags: bus master, medium devsel, latency 0, IRQ 23
	I/O ports at ff20 [size=32]
	Kernel driver in use: uhci_hcd

00:1d.7 USB Controller: Intel Corporation 82801G (ICH7 Family) USB2 EHCI Controller (rev 01) (prog-if 20)
	Subsystem: Dell Device 01d2
	Flags: bus master, medium devsel, latency 0, IRQ 21
	Memory at ffa80800 (32-bit, non-prefetchable) [size=1K]
	Capabilities: <access denied>
	Kernel driver in use: ehci_hcd

00:1e.0 PCI bridge: Intel Corporation 82801 PCI Bridge (rev e1) (prog-if 01)
	Flags: bus master, fast devsel, latency 0
	Bus: primary=00, secondary=03, subordinate=03, sec-latency=32
	I/O behind bridge: 0000c000-0000cfff
	Memory behind bridge: efb00000-efbfffff
	Capabilities: <access denied>

00:1f.0 ISA bridge: Intel Corporation 82801GB/GR (ICH7 Family) LPC Interface Bridge (rev 01)
	Flags: bus master, medium devsel, latency 0
	Capabilities: <access denied>
	Kernel modules: iTCO_wdt, intel-rng

00:1f.1 IDE interface: Intel Corporation 82801G (ICH7 Family) IDE Controller (rev 01) (prog-if 8a [Master SecP PriP])
	Subsystem: Dell Device 01d2
	Flags: bus master, medium devsel, latency 0, IRQ 16
	I/O ports at 01f0 [size=8]
	I/O ports at 03f4 [size=1]
	I/O ports at 0170 [size=8]
	I/O ports at 0374 [size=1]
	I/O ports at ffa0 [size=16]
	Kernel driver in use: ata_piix

00:1f.2 IDE interface: Intel Corporation 82801GB/GR/GH (ICH7 Family) SATA IDE Controller (rev 01) (prog-if 8f [Master SecP SecO PriP PriO])
	Subsystem: Dell Device 01d2
	Flags: bus master, 66MHz, medium devsel, latency 0, IRQ 20
	I/O ports at fe00 [size=8]
	I/O ports at fe10 [size=4]
	I/O ports at fe20 [size=8]
	I/O ports at fe30 [size=4]
	I/O ports at fea0 [size=16]
	Memory at a8000000 (32-bit, non-prefetchable) [size=1K]
	Capabilities: <access denied>
	Kernel driver in use: ata_piix

00:1f.3 SMBus: Intel Corporation 82801G (ICH7 Family) SMBus Controller (rev 01)
	Subsystem: Dell Device 01d2
	Flags: medium devsel, IRQ 9
	I/O ports at ece0 [size=32]
	Kernel modules: i2c-i801

01:00.0 VGA compatible controller: ATI Technologies Inc RV370 5B60 [Radeon X300 (PCIE)]
	Subsystem: ATI Technologies Inc Device 0602
	Flags: bus master, fast devsel, latency 0, IRQ 16
	Memory at ec000000 (64-bit, prefetchable) [size=32M]
	Memory at efde0000 (64-bit, non-prefetchable) [size=64K]
	I/O ports at dc00 [size=256]
	Expansion ROM at efe00000 [disabled] [size=128K]
	Capabilities: <access denied>
	Kernel modules: radeonfb

01:00.1 Display controller: ATI Technologies Inc RV370 [Radeon X300SE]
	Subsystem: ATI Technologies Inc Device 0603
	Flags: bus master, fast devsel, latency 0
	Memory at efdf0000 (64-bit, non-prefetchable) [size=64K]
	Capabilities: <access denied>

03:02.0 Modem: Intel Corporation FA82537EP 56K V.92 Data/Fax Modem PCI (rev 04)
	Subsystem: Dell Device 1000
	Flags: bus master, stepping, medium devsel, latency 64, IRQ 18
	Memory at efbfe000 (32-bit, non-prefetchable) [size=4K]
	I/O ports at cc00 [size=256]
	Capabilities: <access denied>
	Kernel driver in use: serial

03:03.0 Multimedia audio controller: Creative Labs CA0106 Soundblaster
	Subsystem: Creative Labs Device 1007
	Flags: bus master, medium devsel, latency 64, IRQ 19
	I/O ports at c8a0 [size=32]
	Capabilities: <access denied>
	Kernel driver in use: CA0106
	Kernel modules: snd-ca0106

03:08.0 Ethernet controller: Intel Corporation 82801G (ICH7 Family) LAN Controller (rev 01)
	Subsystem: Dell Device 01ab
	Flags: bus master, medium devsel, latency 64, IRQ 20
	Memory at efbff000 (32-bit, non-prefetchable) [size=4K]
	I/O ports at c8c0 [size=64]
	Capabilities: <access denied>
	Kernel driver in use: e100
	Kernel modules: e100


bl

---

### Post by Scouseal on 2009-10-05
Hello everyone I'm new here so be gentle!!
 
Over the past 24 hours I have been trying to install 9.04 over 8.04 and kept on getting this error. I searched on the web and found the following suggestions:
 
Burn ISO CD at a Slower rate
Replace/reduce/increase memory
DiskCheck
Memory Test
Faulty cd/dvd drive
 
I tried the following and all were unsuccessful:
 
Burnt same ISO on to a CD at 16x - Installation Failed
Replaced/reduced/increased memory - tried all 3 - Installation Failed
Disk Check - found 1 error repaired - installation failed
Memory Test - Passed - Installation failed
Used different cd/dvd drive - Installation failed
 
I then decided to download from a different mirror and burnt the ISO onto CD at a speed of 1x (it took some 1.5 hours to complete the burn) attempted installation again and it worked fine.
 
Therefore I can only assume that there was either something wrong with the original ISO I downloaded or that you have to burn the CD at a Very Slow speed.
 
The Mirror I used for the second download was the Virgin Media server in the UK (where I'm from).
 
Hope this helps those suffering this problem.

---

### Post by presence1960 on 2009-10-05
> **Scouseal said:**
> Hello everyone I'm new here so be gentle!!
 
Over the past 24 hours I have been trying to install 9.04 over 8.04 and kept on getting this error. I searched on the web and found the following suggestions:
 
Burn ISO CD at a Slower rate
Replace/reduce/increase memory
DiskCheck
Memory Test
Faulty cd/dvd drive
 
I tried the following and all were unsuccessful:
 
Burnt same ISO on to a CD at 16x - Installation Failed
Replaced/reduced/increased memory - tried all 3 - Installation Failed
Disk Check - found 1 error repaired - installation failed
Memory Test - Passed - Installation failed
Used different cd/dvd drive - Installation failed
 
I then decided to download from a different mirror and burnt the ISO onto CD at a speed of 1x (it took some 1.5 hours to complete the burn) attempted installation again and it worked fine.
 
Therefore I can only assume that there was either something wrong with the original ISO I downloaded or that you have to burn the CD at a Very Slow speed.
 
The Mirror I used for the second download was the Virgin Media server in the UK (where I'm from).
 
Hope this helps those suffering this problem.

You should always [MD5SUM]("https://help.ubuntu.com/community/HowToMD5SUM") the iso before burning it to CD. The hashes must match exactly or the iso is corrupted.

---

### Post by halsboss2 on 2009-10-06
> **presence1960 said:**
> You should always [MD5SUM]("https://help.ubuntu.com/community/HowToMD5SUM") the iso before burning it to CD. The hashes must match exactly or the iso is corrupted.

I also got frustrated and tried the MD5 and to my surprise 2 (yes TWO) separate downloads from 2 separate mirrors had incorrect MD5s.  Both downloaded with firefox native download.  **[COLOR=Red]Something odd is going on with the mirrors ![/COLOR]**    Downloaded from a 3rd mirror and that turned out to MD5 correctly - burned it and it self-checked nicely when booted from the live CD.

NOW I get the dreaded no-solution-available "PERMISSION DENIED" error trying to install via WUBI.

---

### Post by Muskegman on 2009-10-24
Hello all,
I have been using ubuntu 8.10 and 9.04 on my HP quad core without a problem for over a year now. I got an Acer 4520 laptop the other day and of course wiped out vista and tried to install 9.04 and 8.10 on it and i keep getting the same [Errno5] input/output error. Now i do know that both copies of ubuntu including the copy of kubuntu 9.04 all work fine, I got them shipped to me via shippit directly from Canonical. 

I have also tried the suggestion of removing a stick of RAM with no luck at all. I have also used the same ubuntu CD's to install on other computers with no problems. 

Ive been trying to install ubuntu and or kubuntu now for 3 days and im starting to get fed up. Any ideas anybody?

---

### Post by halsboss2 on 2009-10-24
> **Muskegman said:**
> i keep getting the same [Errno5] input/output error. Now i do know that both copies of ubuntu including the copy of kubuntu 9.04 all work fine, [B]I got them shipped to me via shippit directly from Canonical. 
[/B] 
I have also tried the suggestion of **removing a stick of RAM** with no luck at all. I have also used the same ubuntu CD's to install on other computers with no problems. 

Any ideas anybody? Await a version that actually works ?

All that crap about removing RAM etc etc is simply utter crap spread by "hackers" who don't want to blame the real culprit - UBUNTU installation.  Others blame the CD to their little hearts' content and repeat that mantra until the cows come home, in spite of evidence like yours (why would anyone ever bother with something mystically said to be so fussy and flakey about something so ubiquitous as industry-standards data CDs ??) - again, fantasy from those who want to deny the truth of UBUNTU's pith poor installation record. 

Other o/s work perfectly, win98, XP, etc and yet UBUNTU doesn't.  Look at the wealth of undeniable evidence, just do some googling on the error !

As they used to say on Sesame Street, can you pick the one that's not the same ?

---

### Post by SteveDee on 2009-10-25
> **Muskegman said:**
> Hello all,
I have been using ubuntu 8.10 and 9.04 on my HP quad core without a problem for over a year now. I got an Acer 4520 laptop the other day and of course wiped out vista and tried to install 9.04 and 8.10 on it and i keep getting the same [Errno5] input/output error. Now i do know that both copies of ubuntu including the copy of kubuntu 9.04 all work fine, I got them shipped to me via shippit directly from Canonical. 

I have also tried the suggestion of removing a stick of RAM with no luck at all. I have also used the same ubuntu CD's to install on other computers with no problems. 

Ive been trying to install ubuntu and or kubuntu now for 3 days and im starting to get fed up. Any ideas anybody?

Have you tried this:-

> If you experience problems with installer stopping at xx% then try running Ubuntu from the liveCD, open a terminal and type:-
ubiquity --no-migration-assistant

---

### Post by Muskegman on 2009-10-25
Ran the live cd and opened a terminal and typed in what was suggested started installing and at 30% i got the same thing.

I just dont get it, my copy of 8.10 and 9.04 both installed flawlessly on my HP quad core and on several other PC's. The Acer laptop is new and all the hardware is working fine. Does ubuntu not like laptops for some strange reason?

---

### Post by Muskegman on 2009-10-28
Also created a bootable USB flash drive and tried to install with that  .......got as far as installing to 62% this time but then ........got the same message again:(
Did a mem test and it passed
removed and swapped 1gig ram sticks.. same thing
checked cd"s for defects , all 3 of them , kubuntu 9.04 ubuntu 9.04  intrepid 8.10 , all passed ok

Well i am out of ideas now 

I am trying to install all these on an AMD 64 Acer aspire 4520 laptop, i wonder if trying to install 32 bit versions of ubuntu on a AMD 64 could be an issue?

Ive read every forum i could find and read everything in google i could possibly find to come up with an answer and now im left scratching my head. There must be an answer somewhere out there, other people have been having the same problems

---

### Post by WSmart on 2010-04-22
Check the disc.

Run the disc check utility from the disc startup menu.  I have a disc that checks without errors in one drive and with errors in another drive.  My install kept failing as noted above which you would expect if the drive can't properly read the disc.

---

### Post by FriendMarmot on 2010-04-25
9.10 gave me the same error yesterday. When I heard about the RAM stick solution I tried that and wouldn't you know it, it worked. I have two 1Gig Kingston sticks and another Gigastick of some other brand, so I figured the "other" stick should be removed. After the installation I popped it back in (with the computer off, of course) and it tells me I'm operation with all 3GB of RAM. Whew!
 
*Btw, I had my first experience with the terminal trying to install Flash for youtube videos. There's gotta be a way to move files by giving yourself temporary write-access via GUI. Oh well though, it was a learning experience. *:rolleyes:

---

### Post by Hectic on 2011-11-04
I feel horrible for the poor people this is happening to. I too, have received Errno 5.

I tried re-downloading the ISO, still no go.
I tried burning at slower speeds, still no go.
I tried using a USB drive, still no go.

I decided to try the ram module pull thing (I was desperate!), I opened the side of my PC and... Decided I was too lazy and went to boot the live cd version. When the dialog that says Try or Install appeared, I thought to myself try it one more time and so I did.

The damn thing installed without a hitch!

WTF, so I guess another "solution" is to try is: open your PC, look at it, and close back up. :confused:

---

### Post by oldos2er on 2011-11-04
Closed. Please don't bump old threads.

---

