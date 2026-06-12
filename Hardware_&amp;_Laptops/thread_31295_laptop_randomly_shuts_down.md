---
title: "laptop randomly shuts down"
date: 2005-05-02
forum: Hardware &amp; Laptops
---

### Post by aaarg on 2005-05-02
first off i am a newb to linux so keep that in mind. 

after trying several distros i tried ubuntu on my averatec 5400......it was the first one that everything worked (except wireless and i got that working) so great work ubuntu!

 my laptop works great while i am using it, but if i leave for a while the screen saver comes on...sometimes for 10 mins sometimes 2 hours then the computer will just turn off. One time it stayed on over night, but just that one time.  i am extremely happy with ubuntu but i am "lost in the sauce" on what to do to fix this...any help would be greaty appreciated. thx

---

### Post by ssam on 2005-05-02
posibly a hardware issue.

faulty powerbutton or power controller?

does this only happen in linux or ubuntu?

maybe a bios setting?

maybe an apci problem.

---

### Post by Xerampelinae on 2005-05-02
Your laptop may have heat issues.  Try turning the screensaver to simply blank screen so the processor isn't working on screensaver stuff.

---

### Post by aaarg on 2005-05-02
i seriously doubt it is a hardware issue.....never happens when i am physically using it, even for hours of continuous use. also, the machine came with win xp which i ran for 7 months with no problems what so ever. i ran xandros 3.0/red hat 9 (i think it was 9)/suse 9.2 and  9.3 and didnt experience this problem (just a ton of others.)

i think it might be the apci problem, but i dont really know what to do.......i will test the blank screensaver suggestion

---

### Post by alastair on 2005-05-02
I've seen a machine lockup with an OpenGL screensaver and a proprietary X driver (think it was "nvidia").

---

### Post by aaarg on 2005-05-02
aight i turned off the screensaver and let it run for a few hours and it hasnt shut down.....could this be stemming from my video card? i have read a little about the card....via unichrome pro and others seem to be having problems with theirs. think this could be my problem? that card is the only thing i havent gotten set up completely yet ( i have only 1 resolution option and the refresh is stuck at 0). any suggestions?

---

### Post by airhead on 2005-05-03
I wonder if you maybe have a similar problem to me? [http://ubuntuforums.org/showthread.php?t=30713](http://ubuntuforums.org/showthread.php?t=30713)

Similar thing in that it never dies when I'm using it. Wierd (and yes, I disabled xscreensaver long ago, thinking that was the problem).

---

### Post by aaarg on 2005-05-03
i honestly dont know what it is....its not the same problem exactly as airheads (no battery discharge) and when i run on the battery i get my battery meter with approximate time like it should.  my initial leanings were towards the acpi, but now i almost think its my video card.....with the screen saver off the laptop stayed on over night for the first time, so maybe thats a little progress.....a little.

airhead you still having the same problem i assume?

---

### Post by airhead on 2005-05-05
Yes, still having these issues.

---

### Post by punkass on 2005-05-07
A friend of mines laptop (Dell 5150 with ATI, i believe) just emailed me and asked about the same thing. He says he leaves his laptop for awhile the screensaver comes on then awhile later it shutsdown.

I am curious if anyone has solved the problem, or at least narrowed it down some more.

---

### Post by airhead on 2005-05-08
Okay, interesting. Glad to know someone else is having the same issues :) I have an nvidia chip in my 5150, so it must not be chip specific. I've taken another stab in the dark and I think it could have something to do with the power management in xscreensaver (which would explain why the shutdown was delayed).

Go to System -> Preferences -> Screensaver and click the "Advanced" tab. Disable power management. I did this yesterday and my laptop hasn't died yet, however I haven't been trying to kill it. I'd be interested if anyone else continues to have these issues after disabling the display power management. If this solves the problem, it kinda sucks that my display will be on all the time  ](*,)

---

### Post by cmilhaus on 2005-05-12
Interesting, I have an Older P3-450 Desktop and I am getting random shutdowns as well, but spread out over a period of days, or maybe even weeks. Just had one yesterday evening, clear weather so that was not a factor. Did not exeprience this issue with "Warty", and there have been no hardware changes or strange software installed.
Before this, Warty has been rock solid, as had Fedora Core and SuSE 9.1
It's not a major issue with me just adding my 2 cents in to let these other folks know it's not just laptop units.

---

### Post by R Audano on 2005-06-23
I am querious to see if anyone as resolved these shutdown problems!
I have an APC ups hooked up via serial cable but dont have it configured to shutdown  yet. Also I am running a Nvidia Video card! Please e-mail me if anyone has solved this issue yet!

Thanks

---

### Post by Frogger on 2005-06-27
[QUOTE=R Audano]I am querious to see if anyone as resolved these shutdown problems!
I have an APC ups hooked up via serial cable but dont have it configured to shutdown  yet. Also I am running a Nvidia Video card! Please e-mail me if anyone has solved this issue yet!

Thanks[/QUOTE]
 Try disabling ACPI, I was having a similar problem with my laptop (Pentium 266/32Mb/Intel Graphics) but mine happened in the installer, much quicker.  I go the error message "Critical Tempature Error, shutting down" but my computer was not hot. 
Quick, someone who knows more than I, is there a way they can read any error message the computer gave before it shut down, a log somewhere perhaps?

---

### Post by aaarg on 2005-06-29
after my shutdown problem got worse i attempted a fresh install. the laptop would shutdown randomly during the install, sometimes at the beginning....sometimes right before it finished (no heat related errors though). i even tested different distros with the same result....acpi?

---

### Post by hippyjim on 2005-08-08
I'm also having a similar problem, but mine happens while I'm using it too.

It's not a heat thing, I can literally have just one firefox tab open, and it'll suddenly go to text mode, then shut down - mid keystroke!

This is starting to be a problem as I was hoping to switch, but I'll never convinve my wife to switch from Windoze XP if the darned thing won't stay on!

Anyone got any ideas - english only please, I'm a total newb.

---

### Post by hippyjim on 2005-08-10
Ok, I've done a bit more digging, and found a way to check the current temperature (I think). Now I know that I've got a reasonable fan and heatsink, but I can't quite believe this:

jim@bigbertha:~$ cat /proc/acpi/thermal_zone/THRM/temperature
temperature:             -265 C

So even though the temperature control bit of ACPI is presumably not active, I still get shut down due to the processor overheating?

Anyone got any ideas where to go with this - I'd rather not remove ACPI because (as i understand it) it allows me to shut down the power from the "log out" options.

---

### Post by edemark on 2005-08-11
Hi all 

I just wanted to indicate that i also have some strange switch off issues. Though I think i am a bit more lucky than some of you as i only get this problem in vvin emulation (qemu and cedega) 
Whenever i try to play games (cedega) and sometimes when i run vvin in qemu.  suppose that this is (at least in my case) a heat issue 
I am using an HP compaq nx9010
and I would like to resolv this problem as well.
Just one more thing, it never happened while i was using suse but i like more Ubuntu so i will keep on sufering (is to say not playing games)
I hope it helps

---

### Post by Majidah on 2005-12-06
I've been getting a related problem to this, the inspiron 5150 suddenly shuts down for no apparent reason.  To the naked ear I get the impression that it has had a power interuption (fan spins up, hard drive spins up, everything suddenly quiets down), but it could be a temperature problem too.  

Funny thing is I usually only get it when I'm installing packages, esp. font packages (mstffonts are the worst).  

All through the install I just had to keep dpkg ing  over and over getting a little further each time before it packed it in... very odd indeed, anyone got any advice?

---

### Post by notanatheist on 2006-02-09
This has cropped up for the first time to me. Dell 700M, up to date Dapper, Gnome desktop. Sometimes a couple programs open, other times just a term. CPU meter says my Pentium M 1600 is staying at 600 since there's no heavy load. Mine just starting the shutdown problem today after doing updates. I've had minor issues with this machine before where it would occasionally just lock up and need to be rebooted (keyboard stopped responding but hitting, not holding, the power button would bring it down). Since this was the third time today I came searching here. Anyone experiencing the same issues with another desktop? Could it be a Gnome bug? What log files should I be looking for?

---

### Post by notanatheist on 2006-02-10
I'll add this from syslog:

Feb  9 16:26:26 laptop shutdown[6120]: shutting down for system halt
Feb  9 16:26:26 laptop init: Switching to runlevel: 0
Feb  9 16:26:27 laptop gconfd (mro-4596): Received signal 15, shutting down cleanly
Feb  9 16:26:27 laptop gconfd (mro-4596): Exiting
Feb  9 16:26:31 laptop gconfd (root-4735): GConf server is not in use, shutting
down.
Feb  9 16:26:31 laptop gconfd (root-4735): Exiting
Feb  9 16:26:32 laptop kernel: [4297796.458000] apm: BIOS version 1.2 Flags 0x03 (Driver version 1.16ac)
Feb  9 16:26:32 laptop kernel: [4297796.458000] apm: disabled on user request.
Feb  9 16:26:36 laptop sdpd[4416]: terminating...
Feb  9 16:26:36 laptop hcid[4411]: Exit.
Feb  9 16:26:36 laptop kernel: Kernel logging (proc) stopped.
Feb  9 16:26:36 laptop kernel: Kernel log daemon terminating.
Feb  9 16:26:36 laptop exiting on signal 15


Feb  9 20:11:07 laptop shutdown[10443]: shutting down for system halt
Feb  9 20:11:09 laptop init: Switching to runlevel: 0
Feb  9 20:11:10 laptop gconfd (mro-4598): Received signal 15, shutting down cleanly
Feb  9 20:11:10 laptop gconfd (mro-4598): Exiting
Feb  9 20:11:16 laptop kernel: [4307946.881000] apm: BIOS version 1.2 Flags 0x03 (Driver version 1.16ac)
Feb  9 20:11:16 laptop kernel: [4307946.882000] apm: disabled on user request.
Feb  9 20:11:19 laptop sdpd[4418]: terminating...
Feb  9 20:11:19 laptop hcid[4413]: Exit.
Feb  9 20:11:20 laptop kernel: Kernel logging (proc) stopped.
Feb  9 20:11:20 laptop kernel: Kernel log daemon terminating.
Feb  9 20:11:20 laptop exiting on signal 15

That's two of the three instances from today. Hope that can help in sleuthing.

---

### Post by SMDBIOS on 2006-05-04
Hello, 

The Dell 5150 suffers from a motherboard problem that results in an unexpected shutdown condition at any given time. Please see: 

[http://www.aqstech.com/5150.html](http://www.aqstech.com/5150.html)

---

### Post by notanatheist on 2008-02-17
That's because the 5150 is a piece of crap with a Pentium 4. Any laptop with a full blown desktop Pentium 4 needs to be taken out and shot if it isn't dead already. Seriously, as a partner in a PC shop I've seen more cooked laptops with P4 and AMD procs than any combination of Pentium M, Celeron M, PII, PIII, and anything else combined.

---

