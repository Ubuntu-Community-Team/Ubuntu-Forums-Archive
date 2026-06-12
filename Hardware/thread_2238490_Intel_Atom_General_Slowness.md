---
title: "Intel Atom: General Slowness"
date: 2014-08-08
forum: Hardware
---

### Post by steve_l on 2014-08-08
I feel silly writing this.  I've been using Linux since 1995 and have never really payed much attention to the generic X86 hardware I've owned.  Each machine was faster than the last, moore's law worked, and all was right with the world.

For the last two years I've owned a computer which is not just slow - but seems so unreasonably slow compared to everything else I've owned and is so close to unusable that I think something must be wrong. 

I am currently running Xubuntu 14.04, though the same - possible - symptom applies to all *untu releases from mid 2012 when this computer was purchased to current, as well as Crunchbang.

The computer is a Gateway LT4004U, with 1GB ram.  Intel GMA-3600 graphics, dual-core N2600 Atom @ 1.6Ghz.

Performance is abysmal,  but for no obvious reason that I understand.  To give you an idea of what I'm talking about:

Web Browsing: I use Palemoon browser and can't think about opening more than nine or ten active tabs at once (even using noscript plugin to block all unnecessary scripts).  Though I can stream videos online (with frequent interruptions with a frozen screen and sound stuck in a repeated loop for up to a minute at a time before slowly recovering if I'm foolish enough to be doing anything on the system at all while a video is playing, like reading text in another browser window), and loading a page with a number of embedded videos on it will bring browser and system to a halt - as in waiting several seconds to half a minute for the mouse to move again.  I have to keep a terminal window open and ready to switch to at all times so I can quickly type "killall palemoon"

Calibre Ebook Manager: Takes minutes to launch, loading a library of around 4,800 ebooks. Searches in the library take probably twenty seconds or so. An Epub to Epub conversion on a book of say 250k takes a few minutes.

Offline Video: Unless a video is very low resolution, like 480 wide or so, I can't watch in fullscreen with VLC/Xine/etc. Attempting to switch to full screen will cause video to freeze completely and it will take many many minutes of dealing with lags and waits for response to alt-tab to the terminal and kill VLC. 

Unity: Hah.. I installed Ubuntu desktop a couple releases ago and it was absolutely impossible to use - I could only open a tab or two in Firefox and if one of them was something particularly demanding like Facebook, I'd already have stalling and lags even with nothing else running.

I didn't expect great performance from a netbook, but what I don't understand is that I replaced a previous netbook that had just died with this thing and it was great.  Can't remember brand or model at all because it - like every generic x86 PC, desktop or laptop that I've purchased for the past 20 years ran Linux just fine after initial configuration difficulties were worked out (though I don't recall any such difficulties even popping up). It was faster than the computer it replaced that I had purchased years before, and that was just how things worked.  Until I bought this particular laptop and moore's law took a dump on me. 

It really seems that this thing is unreasonably slow in a way that just can't be right - I mean it is two years old (or at least two years since I bought it at Best Buy), and not only has much poorer performance than the machine it replaced (probably purchased in 2008 or 2009), but I'm discovering now after comparing notes in another forum about Calibre (start time, number of books) and basic web browsing (how many tabs can you open before you no longer have a functioning machine) that I have a far more limited machine than Celeron desktops from 2003 or so.

That can't actually be right, can it?  Is this machine just THAT underpowered, or does it seem perfectly reasonable that someone with an Atom netbook running a lightweight distro like Crunchbang, Lubuntu, or Xubuntu should have THIS bad of performance?

Now I know that this graphics card is poorly supported in Linux in general - but I've never had a system with video acceleration before, and have pretty much always wound up using the Vesa driver in X before, so I don't see how that could be having an effect.

I don't know how the Atom N2600 ranks in the pantheon of processor power because I've never payed attention to any of that before - I just knew that if I bought a new x86 machine it would be way faster than the x86 machine it replaced from five years or so earlier, but I'm discovering that Calibre takes folks running Pentium-M and Celeron machines around 40 seconds and it takes me 5 minutes or so.

Comparing anecdotal descriptions of Firefox performance between these guys (again ten year old intel machines versus my two-year old one, with them running full desktops like Cinnamon or Mate while I'm running Xfce...) are similarly absurd - I'm in trouble with single digits of tabs open in Palemoon, these guys say they have no problems with thirty tabs left open in Firefox on these MUCH older machines.

Is there anything that I might want to investigate that explains such horrible performance for this machine running Linux, or am I just the owner of a Gateway LT4004U, manufactured in 2012 running exactly as I should expect it to?

---

### Post by mikewhatever on 2014-08-08
Pretty sure you run out of RAM with 10 browser tabs and a 4800 book library. Run <free -m> to verify when it gets slow.
IMHO, Intel's Atom brand is a hokes. It compromises too much on performance, but does not provide major power savings or better battery life. Intel's Atoms also require active cooling - spinning fans attached to them, and Intel graphics is probably even worse.
While some of the stuff you've reported is a bit extream, having looked at reviews and ebay listings, I'd say you've got what you payed for.

---

### Post by tgalati4 on 2014-08-08
Atom processors are good for headless servers.  Low power and low performance.  They are just too annoying to use for a hands-on computer.

Read the reviews:

[http://cpuboss.com/cpu/Intel-Atom-N2600](http://cpuboss.com/cpu/Intel-Atom-N2600)

[http://www.tomshardware.com/forum/350768-28-good-atom-n2600-powervr](http://www.tomshardware.com/forum/350768-28-good-atom-n2600-powervr)

---

### Post by steve_l on 2014-08-08
Really?  I mean it makes the most sense that this machine just sucks - but it seems extreme that a task which takes 29 seconds on a ten year old Celeron would take over 7 minutes on this thing. I mean it just seems absurd and impossible that intel would produce a processor which, all other things being equal is outperformed more than 14 times over by their own commodity hardware from ten years ago.  It really never occurred to me that something might be wrong until I started comparing notes and discovered this

---

### Post by steve_l on 2014-08-08
I mean should a 1.6 Ghz dual core Atom be ONE FOURTEENTH the speed of a 1.4 Ghz single core Celeron?

---

### Post by steve_l on 2014-08-08
Also, regarding running out of memory - this is with 1gb of ram. I should have mentioned when I described performance above that none of these tasks are ever engaged in at the same time, thus "with 10 tabs and 4,800 books" doesn't apply.  I could not possibly think about running Calibre and browser like Firefox or Palemoon at the same time! What I was describing is the performance of a web browser running alone (except for a terminal window needed to kill said browser from when things get TOOOO slow).  When launching Calibre, nothing else more significant than a terminal and file manager window or two could possibly be running!

Also, strangely, I've had top running many times while the system was bogged down to a completely unusable state and I'm seeing not only plenty of free memory, but no task even using significant cpu resources (like I'll be dealing with a machine so slow that the mouse takes more than a second to respond to attempts to move it, and the head of the list for top will be my browser using like 6% cpu time.... wtf?)

---

### Post by tgalati4 on 2014-08-08
What are the SMART parameters of the hard disk?

```
sudo smartctl -a /dev/sda
```

---

### Post by steve_l on 2014-08-08
> **tgalati4 said:**
> What are the SMART parameters of the hard disk?

```
sudo smartctl -a /dev/sda
```

smartctl 6.2 2013-07-26 r3841 [x86_64-linux-3.13.0-23-generic] (local build)
Copyright (C) 2002-13, Bruce Allen, Christian Franke, [www.smartmontools.org](www.smartmontools.org)

=== START OF INFORMATION SECTION ===
Model Family:     Western Digital Scorpio Blue Serial ATA (AF)
Device Model:     WDC WD3200BPVT-22JJ5T0
Serial Number:    WD-WX71C1245713
LU WWN Device Id: 5 0014ee 206b0e272
Firmware Version: 01.01A01
User Capacity:    320,072,933,376 bytes [320 GB]
Sector Sizes:     512 bytes logical, 4096 bytes physical
Rotation Rate:    5400 rpm
Device is:        In smartctl database [for details use: -P show]
ATA Version is:   ATA8-ACS (minor revision not indicated)
SATA Version is:  SATA 2.6, 3.0 Gb/s
Local Time is:    Fri Aug  8 16:08:35 2014 EDT
SMART support is: Available - device has SMART capability.
SMART support is: Enabled

=== START OF READ SMART DATA SECTION ===
SMART overall-health self-assessment test result: PASSED

General SMART Values:
Offline data collection status:  (0x00)	Offline data collection activity
					was never started.
					Auto Offline Data Collection: Disabled.
Self-test execution status:      (   0)	The previous self-test routine completed
					without error or no self-test has ever 
					been run.
Total time to complete Offline 
data collection: 		( 8100) seconds.
Offline data collection
capabilities: 			 (0x7b) SMART execute Offline immediate.
					Auto Offline data collection on/off support.
					Suspend Offline collection upon new
					command.
					Offline surface scan supported.
					Self-test supported.
					Conveyance Self-test supported.
					Selective Self-test supported.
SMART capabilities:            (0x0003)	Saves SMART data before entering
					power-saving mode.
					Supports SMART auto save timer.
Error logging capability:        (0x01)	Error logging supported.
					General Purpose Logging supported.
Short self-test routine 
recommended polling time: 	 (   2) minutes.
Extended self-test routine
recommended polling time: 	 (  82) minutes.
Conveyance self-test routine
recommended polling time: 	 (   5) minutes.
SCT capabilities: 	       (0x7035)	SCT Status supported.
					SCT Feature Control supported.
					SCT Data Table supported.

SMART Attributes Data Structure revision number: 16
Vendor Specific SMART Attributes with Thresholds:
ID# ATTRIBUTE_NAME          FLAG     VALUE WORST THRESH TYPE      UPDATED  WHEN_FAILED RAW_VALUE
  1 Raw_Read_Error_Rate     0x002f   200   200   051    Pre-fail  Always       -       0
  3 Spin_Up_Time            0x0027   144   135   021    Pre-fail  Always       -       1791
  4 Start_Stop_Count        0x0032   097   097   000    Old_age   Always       -       3187
  5 Reallocated_Sector_Ct   0x0033   200   200   140    Pre-fail  Always       -       0
  7 Seek_Error_Rate         0x002e   200   200   000    Old_age   Always       -       0
  9 Power_On_Hours          0x0032   078   078   000    Old_age   Always       -       16263
 10 Spin_Retry_Count        0x0032   100   100   000    Old_age   Always       -       0
 11 Calibration_Retry_Count 0x0032   100   100   000    Old_age   Always       -       0
 12 Power_Cycle_Count       0x0032   100   100   000    Old_age   Always       -       838
191 G-Sense_Error_Rate      0x0032   001   001   000    Old_age   Always       -       3124
192 Power-Off_Retract_Count 0x0032   200   200   000    Old_age   Always       -       208
193 Load_Cycle_Count        0x0032   047   047   000    Old_age   Always       -       461517
194 Temperature_Celsius     0x0022   102   081   000    Old_age   Always       -       41
196 Reallocated_Event_Count 0x0032   200   200   000    Old_age   Always       -       0
197 Current_Pending_Sector  0x0032   200   200   000    Old_age   Always       -       0
198 Offline_Uncorrectable   0x0030   100   253   000    Old_age   Offline      -       0
199 UDMA_CRC_Error_Count    0x0032   200   200   000    Old_age   Always       -       0
200 Multi_Zone_Error_Rate   0x0008   100   253   000    Old_age   Offline      -       0

SMART Error Log Version: 1
No Errors Logged

SMART Self-test log structure revision number 1
No self-tests have been logged.  [To run self-tests, use: smartctl -t]


SMART Selective self-test log data structure revision number 1
 SPAN  MIN_LBA  MAX_LBA  CURRENT_TEST_STATUS
    1        0        0  Not_testing
    2        0        0  Not_testing
    3        0        0  Not_testing
    4        0        0  Not_testing
    5        0        0  Not_testing
Selective self-test flags (0x0):
  After scanning selected spans, do NOT read-scan remainder of disk.
If Selective self-test is pending on power-up, resume after 0 minute delay.

---

### Post by MartyBuntu on 2014-08-08
> **steve_l said:**
> ...or am I just the owner of a Gateway LT4004U, manufactured in 2012 running exactly as I should expect it to?

Yeah...pretty much.

I too own a netbook (Linux Mint 13 LTS installed).

I don't throw anything other than light browsing, text editing and file management at it. It is what it is.

---

### Post by steve_l on 2014-08-08
> **MartyBuntu said:**
> Yeah...pretty much.

I too own a netbook (Linux Mint 13 LTS installed).

I don't throw anything other than light browsing, text editing and file management at it. It is what it is.

If true, that's just amazing. I just discovered in another forum that a 1.4Ghz Celeron M from around 2003, single core, 1GB ram will load a similar sized Calibre library in 26 seconds (better than his original estimate of around 40 seconds). I timed launching my Calibre library while leaving three browser tabs running and it came out to 7 minutes, 6 seconds by the time it had actually launched and I was able to select a book.

That means it takes 17.15 times as long for my 2012 Atom netbook to perform the same task as a 2003 Celeron-M desktop.

And Calibre is only an easy ersatz benchmark to use - everything else I try to do on the system is just as bad.  Every time  I try to describe how bad using a web browser is on this thing, people start telling me "Oh it must be your flash, you need to... bla...bla..." and I have to try to get them to understand that this isn't just a flash issue, but an everything issue.

If it is just slow, that's what I had been thinking all along -- until I discovered just how slow it was compared to such significantly older hardware.  Now it just seems like there has to be something wrong.

Consider, for instance, that I have nothing but a browser and terminal open now, with five tabs open in the browser including an NPR streaming page.  Attempting to type this post while leaving the audio stream playing (32kbps mp3) means that audio has stalled several times while I have been typing this, repeating the same fraction of a second loop for some time until it finally recovers and the last several words that I typed finally catch up and I can use the keyboard again.

If that is just normal and expected for an Atom netbook with a gig of ram then I'm just baffled - I haven't ever payed attention to all these different lines of processors because, like I said, newer generic x86 has always been faster than older for every purchase I've made for 20 years -- until now when Moore's law has taken a very very dramatic reversal leaving me with the kind of processing power I had somewhere in the 1990's.

---

### Post by kostkon on 2014-08-08
> **steve_l said:**
> Consider, for instance, that I have nothing but a browser and terminal open now, with five tabs open in the browser including an NPR streaming page.  Attempting to type this post while leaving the audio stream playing (32kbps mp3) means that audio has stalled several times while I have been typing this, repeating the same fraction of a second loop for some time until it finally recovers and the last several words that I typed finally catch up and I can use the keyboard again.

If that is just normal and expected for an Atom netbook with a gig of ram then I'm just baffled - I haven't ever payed attention to all these different lines of processors because, like I said, newer generic x86 has always been faster than older for every purchase I've made for 20 years -- until now when Moore's law has taken a very very dramatic reversal leaving me with the kind of processing power I had somewhere in the 1990's.
Yeah, that's not normal at all. You should be able to multi-task just fine. And you are running Xubuntu, not even Ubuntu.

I'm blaming your PowerVR-based GMA3600.

Or even something like bad RAM?

My netbook, N455 1.6GHz, GMA3150 with 2GB RAM (upgraded from 1GB), running 12.04 (with Unity and all) and the performance is more than decent. It ran fine even with 1GB RAM (but with increased swap usage, obviously.)

Definitely, something is wrong.

---

### Post by SeijiSensei on 2014-08-08
How much swap do you have allocated?

Adding another GB of memory to the machine would probably make a great deal of difference.

---

### Post by awo3it on 2015-02-12
If you are still interested...the problem is the video card driver (cedarview), not working properly(and there is no good solution, no way for hd videos full screen!)...try ubuntu 12.04 without unity(like i did, i completely removed unity for openbox+pcmanfm). Maybe mint (not sure of lubuntu or xubuntu, for they could be less adjourned).

---

### Post by kerry_s on 2015-02-12
> **awo3it said:**
> If you are still interested...the problem is the video card driver (cedarview), not working properly(and there is no good solution, no way for hd videos full screen!)...try ubuntu 12.04 without unity(like i did, i completely removed unity for openbox+pcmanfm). Maybe mint (not sure of lubuntu or xubuntu, for they could be less adjourned).

install -> intel-microcode : sudo apt-get install intel-microcode
no setup needed just reboot, this will take care of firmware issues.

create a xorg.conf file -> gksudo mousepad /etc/X11/xorg.conf
(i'm just assuming your text editor, replace with what your actually using, i prefer mousepad)

put:

```
Section "Device"
	Identifier "Intel Graphics"
	Driver "intel"
	Option "AccelMethod" "uxa"
EndSection
```

that will take care of intel graphics issues.

make sure you use "dvmt" in your bios for video if that is a option on your board. it will allocate up to 256mb of your ram on the fly(as needed) instead of fixed. that way you have all your ram(-8mb) available all the time.


invest in maxing out your ram, i also switched to a ssd drive. prior to this board i had the atom 230 board, dual 1.6ghz, 1gb ram, so i do remember the challenge.
my current board is a atom 330 1.6ghz x 4, 2gb ram(max).

i use debian testing, i've found it to be a lot faster than *ubuntu's. i use standard gnome 3, cause it gets the most love from developers.
i use the debian net installer, which lets you select whatever desktop you want installed.

---

### Post by steve_l on 2015-02-25
> **kerry_s said:**
> install -> intel-microcode : sudo apt-get install intel-microcode
no setup needed just reboot, this will take care of firmware issues.

create a xorg.conf file -> gksudo mousepad /etc/X11/xorg.conf
(i'm just assuming your text editor, replace with what your actually using, i prefer mousepad)

put:

```
Section "Device"
	Identifier "Intel Graphics"
	Driver "intel"
	Option "AccelMethod" "uxa"
EndSection
```

that will take care of intel graphics issues.

make sure you use "dvmt" in your bios for video if that is a option on your board. it will allocate up to 256mb of your ram on the fly(as needed) instead of fixed. that way you have all your ram(-8mb) available all the time.


invest in maxing out your ram, i also switched to a ssd drive. prior to this board i had the atom 230 board, dual 1.6ghz, 1gb ram, so i do remember the challenge.
my current board is a atom 330 1.6ghz x 4, 2gb ram(max).

i use debian testing, i've found it to be a lot faster than *ubuntu's. i use standard gnome 3, cause it gets the most love from developers.
i use the debian net installer, which lets you select whatever desktop you want installed.

Well, I honestly have no idea what intel-microcode provided or fixed, but it seems to have improved things greatly. Flash video at full screen has a noticeably higher frame rate and looks much better. No video BIOS options, and no noticeable change from the xorg.conf. 

Meanwhile, I finally added memory last month. I now have the maximum 3 gig (all that is recognized of a 4gb stick). HUGE difference - that seven minute launch for Calibre is now about 1.5 minutes. Still more than twice the time for a desktop machine a few years older, but MUCH better than what I'd been dealing with before.

Also, regarding the 32/64 bit bit, I'm running 64 bit Lubuntu 14.04 at the moment. 

On Debian versus Ubuntu, I've not been able to throw Debian on this thing because its wifi adapter only works out of the box under Ubuntu and my Internet access is wireless only, no access to a router to plug into directly. I haven't tried Mint yet and am considering Mint Debian Edition in hopes that my driver is there.

---

### Post by steve_l on 2015-02-25
Again, I don't know what installing "intel-microcode" did, but it definitely did something. The system is much more responsive, flash video much, much, *much* better.

Yesterday, I had been playing around with cloud.mathsage.com and used ipython to do a quick comparison between their VMs and my poor brain damaged machine. 

%timeit math.factorial(2**14):

mathsage cloud: 10 loops, best of 3: 113 ms per loop
atom pre-intel-microcode: 1 loops, best of 3: 735 ms per loop
atom with intel-microcode: 1 loops, best of 3: 670 ms per loop

---

### Post by steve_l on 2015-02-25
I know that isn't a very scientific benchmark, but it is surprisingly consistent.

Running the same code several times on mathsage cloud came back with 113ms all but once when it returned 114ms.  Running several dozen times on the LT4004U (with intel-microcode) returns a bit more range, with the best at 663 and worst at 674, and while I only ran it a few times before the intel-microcode package was installed, all the results were 730 or worse at the time. There is definitely a statistically significant improvement.

---

### Post by mattharris4 on 2015-02-25
Steve, I am perplexed as well but I haven't ever used a computer with a Atom processor.  I am typing this on an approximately eight year old 32 bit HP with a Pentium 4 3.0GHz processsor running Edubuntu and my programs usually come up quite quickly.  The only issue I have really had is after a major update and SF Gate (San Francisco Chronicle) revamping their site I started to use all of my then 2GB RAM and up to 900GB of swap. Every time my computer started using swap it slowed to a crawl.  Upgrading RAM to 3.5GB took care of that issue.  I usually open 6-8 tabs on SF Gate and use about 2.2-2.5GB of RAM.  I tested Lubuntu (using a USB stick with a Lubuntu ISO on it) with the same site on the same computer and used about 1.3GB.  I haven't really messed with Xubuntu but it is supposed to be lighter than Ubuntu/Edubuntu but more feature rich than Lubuntu (although pretty much anything that you need and is in the software repository that will run on Ubuntu will run on the lighter versions if you download the program). 

 I also have a new 15" Toshiba laptop with an AMD E1-2100 1.0GHz processor 64 bit with 4GB of RAM (purchased in May 2014, it is known as a crappy processor and AMD's answer to the Atom) that I played with a bit using a USB Lubuntu ISO and it worked fine, probably better than the Windows 8.1 that came with it.  It certainly works much better than your netbook does.  After the warranty expires I might dual-boot Windows 8.1 and Lubuntu on it.  On all of my computers I have Flash disabled by default and manually turn it on when I want to watch a video so that embedded videos (common on newspaper sites, an example is the Marin Independent Journal site) don't interfere with my browsing pleasure and take up precious RAM.  This computer does not allow for more than a few tabs and a You Tube video open because of the slow processor using Win 8.1 (I can tell through a performance monitor that it is the processor and not the RAM maxing out) but I get 5-6 hours of battery life with an extended battery option to extend that to 8-9 hours so this computer works fine for what I use it for (and it will probably work better with a lighter OS like Lubuntu but I don't dare install it until the warranty expires).  Either way, with my experience on this computer and it having the competitor's version of what you have as a processor I am sure you have some issue with your computer.  

Now I have some suggestions:

1.  Replace the RAM sticks (a netbook usually has two, with 1GB of RAM you probably have two 512MB sticks currently) with 1GB (or even 2GB if available) sticks.  If the sticks are sottered in place skip this step and plan on replacing the computer.  Otherwise this is notoriously simple but many videos on You Tube will walk you through it.  Since you have a netbook it is likely a 32 bit machine which cannot use more than 3.5GB of RAM but you can install four GB and the computer should still work fine just only recognizing the 3.2-3.5GB it is capable of using.  Make sure the sticks are the same speed and chip, the specifications should tell you what speed RAM sticks you need (example PC2-4200 533MHz non ECC, this is likely not what your computer takes but that is the way it will be written).  RAM sticks for a recent computer aren't that expensive, I ordered mine from Amazon (I am assuming you are in the US or Canada, if you are in the UK you will likely need to visit your local computer shop -- customs duties for a UK resident are known to be horrendous ordering from a US site).  After installing the new RAM, test the machine on a RAM hog site, [www.sfgate.com](www.sfgate.com) is the hoggiest I use, open 10-12 tabs with different articles on the computer, attempt to read and scroll through a few and see if it still bogs down.

2.  If you are still having this issue do the following: 

A.  Save all documents onto a external hard drive or USB stick
B.  Once you have done this, verify the documents are on the external stick or drive
C.  Make a list of all programs you have installed on your computer so you can reinstall them from the software repository later 
D.  Make sure you have a Lubuntu 14.04 ISO on a stick or CD
E.  Format the hard drive
F.  Reinstall Lubuntu, download the third party driver package
G.  Download updates (preferably you have an internet connection, an ethernet cord and your computer has an ethernet plug available so you can select the option to do so while installing)
H.  Reinstall all of your programs
I.   Test computer thoroughly.  Load the computer to the gills -- open 10-12 tabs on SFGate's site if you don't know of a RAM hog site to use.

If you still have a problem it is either the processor, motherboard or the hard drive.  You could try replacing the hard drive with a new one (2.5 inch drives are standard in laptops -- in this new of a laptop it is likely a SATA plug drive, in the US they are about $50-$75 for 500GB) if this computer is worth that much to you.  An SSD would speed things up massively (assuming the rest of your computer is working correctly) but you need at least a 240GB drive and that costs over $120.  To match what you probably already have (500GB) you would spend $250 plus on an SSD.  Again, the replacement is simple and installing Lubuntu on the new drive will be harder than installing the HD in its proper bay.  If a hard drive replacement does not work, replace the computer -- processors and motheboards are notoriously expensive to repair/replace.

---

### Post by steve_l on 2015-02-25
Well, I'm maxed out at 3 gb (what is supported and used of the 4 gb stick filling the single slot - nothing to do with 32/64 bit, it is an x86-64 processor currently running Lubuntu 14.10 64-bit). And an SSD would cost FAR more than a significantly more powerful used machine (like a five+ year old Thinkpad or something). If I had the option of spending that kind of cash I wouldn't have to worry about it - I'd have pitched or given away this particular machine long ago ;-)

---

### Post by kerry_s on 2015-02-25
here's what is says in synaptic for intel-microcode:
This package contains updated system processor microcode for
Intel i686 and Intel X86-64 processors.  Intel releases microcode
updates to correct processor behavior as documented in the
respective processor specification updates.

---

### Post by mattharris4 on 2015-02-25
^  It sounds like you may have reached the limit of this machine to do what you need it to do.  As I said you could try replacing the hard drive but I suspect we are at the end of what this machine is worth.  My next question is do you absolutely need a laptop?  Since cash is tight if you can use a desktop and you happen to have an old VGA based computer monitor lying around (if not a new monitor is less than $100 or you can probably hit up the local resale stores and get one for less than $25) you can buy a refurb desktop for less than $125, Tiger Direct and Newegg both sell them starting at $70 but I would go $30-$40 more and get one with a larger HD and a DVD-RW.  They would come with Windows 7, you could do a dual-install with Lubuntu once you know the computer functions properly (I bought one that didn't, after three tries at repair I determined the motherboard was the likely culprit and the computer was exchanged for another by the refurbisher).  Make sure you get one with a one-year warranty included, a couple of refurbishers only give three months warranty.  I bought mine from Tiger Direct four years ago (it was $200 but the price on something equivalent has dropped drastically since then) and it was refurbed by Joy Systems.  Tiger and Newegg sell refurbs from several different refurbishers so make sure you get one with the one year warranty.  Certainly this is cheaper than a new computer (although new base-model computers from Acer and HP run about $250 on Amazon with Win 8.1).

I wish I could help more.  Good luck whatever you decide to do.

---

### Post by tessk2 on 2015-02-25
No suggestions on how to fix it, but I used a similar netbook, the Samsung NC10, with 2GB RAM under Windows 7 for years without a hitch, in fact it was my primary computer for quite a while. You could even play some light Steam games on it, like AudioSurf. Definitely something wrong, not just weak hardware.

---

### Post by tushar3 on 2015-07-10
I know this is an old thread. But I am a dino usng netbook with 1.6Ghz Intel Atom processor. This is a single core processor complemented by a 1GB Ram. I am running LUBUNTU 14.04 on it and my friend steve_l this thing sucks big time. I have made this one my exclusive machine for programming and playing around. I have pretty much the same issues that you mentioned. 
The Win XP that came with was decent though. Those days are long gone now!
I was about to install crunchbang on this puppy but after reading your review I am gonna stick to it. 
I am planning on installing Debian and then add the packages that i need over a very basic build. Hope that makes it worthy of something. And for casual programming this thing works just fine. I have all the fancy IDEs installed Eclipse/Geany/Rstudio and else. All of them work fine after the initial lag in loading.
Browsing with firefox is a sure death on this one.

eBay can help find you an old machine with decent specs that runs better than this.

---

### Post by matthew82 on 2015-07-11
> **tushar3 said:**
> I know this is an old thread. But I am a dino usng netbook with 1.6Ghz Intel Atom processor. This is a single core processor complemented by a 1GB Ram. I am running LUBUNTU 14.04 on it and my friend steve_l this thing sucks big time. I have made this one my exclusive machine for programming and playing around. I have pretty much the same issues that you mentioned. 
The Win XP that came with was decent though. Those days are long gone now!
I was about to install crunchbang on this puppy but after reading your review I am gonna stick to it. 
I am planning on installing Debian and then add the packages that i need over a very basic build. Hope that makes it worthy of something. And for casual programming this thing works just fine. I have all the fancy IDEs installed Eclipse/Geany/Rstudio and else. All of them work fine after the initial lag in loading.
Browsing with firefox is a sure death on this one.

eBay can help find you an old machine with decent specs that runs better than this.
[http://www.ebay.com/itm/2GB-HP-Compaq-Mini-311-Series-DDR3-NetBook-Memory-/110635721589?pt=LH_DefaultDomain_0&hash=item19c2672375](http://www.ebay.com/itm/2GB-HP-Compaq-Mini-311-Series-DDR3-NetBook-Memory-/110635721589?pt=LH_DefaultDomain_0&hash=item19c2672375)

Throw some cash at it with the above. This is what I have in my HP mini 311 with the Atom N270. Mine is OC'ed to 2.3ghz which makes it noticeably snappier than leaving it at the stock 1.66ghz.

---

### Post by eightbits2010 on 2015-10-03
I am using the Atom (Intel) processor that is hardwired to this circuit board
 [http://www.intel.com/products/motherboard/D510MO/index.htm](http://www.intel.com/products/motherboard/D510MO/index.htm) 

 
 
 It has 2 G Ram and seems to run at reasonable speed. I recently installed Xubuntu 14.04 (clean install)
 and I did experience better performance. Prior to the Xubuntu install it was Ubuntu 14.10 and I did
 notice it was painfully slow prior to installing Xubuntu.

 
 
 The Atom processor (soldered in) is a four core processor at 1.66 GHZ speed/core.
 The multicore may make a difference in your setup, I don't know.

This PC is also a nettop machine.

 
 
 The Xubuntu was not as easy to use as Ubuntu and took a lot of tweaking and I was using nemo as the desktop and I think there was some speed minor slow up after changing those things.
 
 
 I can only offer the above link for a Atom processor.

---

