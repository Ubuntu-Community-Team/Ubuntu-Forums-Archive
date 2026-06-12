---
title: "Terrible Hardware performance problems/&quot;Error Requestiong Region 4300.../Error prob.."
date: 2008-04-19
forum: Hardware &amp; Laptops
---

### Post by funkster on 2008-04-19
Hi there,
first of all, sory for the lengthy post, hope you don't mind.
it's been almost a year now that I switched to some flavor of *nix (tried a few diff. distros) for my daily tasks (internet, office, some graphics work etc) and so far I'm pleased enough to keep it that way. 
Still, I'd like to use linux completely, but I have specific needs, which are mainly audio related (multitracking of MIDI & Audio, softsynths, etc.)
Now it seems that whatever I do, I can't get any decent performance figures from ANY distro I've tried. My hardware is not of the newest variant, but it's no slouch either. Under Windows XP it is flying away (though a very streamlined/nLite'd install is used there, not the standard run of the mill installation). Obviously, I've spent quite some time to find out through trial & error, what I need to tweak on windows to make it that fast. 

Now after almost 1 year of linux experience, I thought I should be able to get at least decent figures out of my system, but it seems not.
The thing I don't understand is, through the modularity of linux systems it should seemingly be possible to strip a system to the bare essential of what a user needs. I have tried all the specialist Linux-Audio distros I could find (Ubuntu Studio, JackLab JAD, GNU/Musix, Agnula/DeMuDi, 64 Studio, you name it...).
First having graphics/xserver related problems with an old ATI 7000/VE 64 MB, not willing to operate like I wanted in a dual monitor setup. Solved that by buying a Matrox G550 Millenium. At least now I have my 2 screens in their best resolution working. Than I had a mobo failure, changed that too. But since I couldn't afford a complete platform change/CPU upgrade, I had to find one that still worked with the rest of my HW. (system listing at the end of this thread). Most of the problems I had could be resolved with the help of google and some nice and knowledgeable people on forums like this and/or through mailing lists/IRC. But the one problem that really prevents the use of my system as an audio workstation, persists.
Namely, performance. Whatever I do, whichever app I run, it works (sort of) and even when the CPU pegs at a full 100%, the system keeps stable and all, very nice. But my performance limit is reached very fast. I open up qjackctl, the connections window & Freewheeling, I record/play back 2 loops and I shoot my CPU already over 50 %, steadily.  When I close all windows/GUI's, I regain around 20 % CPU. But even a steady 30 % still seems a lot to me for playing back a few loops in freewhelling through jackd. I don't even talk about MuSE or Rosegarden, let alone Ardour. Rosegarden, with only ONE friggin MIDI track, routed to outboard synth, pegs at FULL on 100 % CPU use. Holy ****. How am I to ever write/record a complete piece of music with these figures? The system just never 'feels' right. Everything just feels so sluggish, pasty, GUI's take way more than a second or so to operate/open, and all this accumulates to the end of the day, making efficient work a 'no go'. 

Now the ONLY variable I see coming back through ALL distros I've tried, is an error message at boot time. I don't know if this is the root of all evil or if it can be ignored or what, but it's the only common denominator I can see for the time being. Here it is:
```

Error requesting Region 4300 .. 433F for SMB2
nforce2_smbus_0000:00:01.1: Error probing SMB2
```
Anybody in the know/able to give me a helping hand (and be it only for telling me that this HW will never do what I want it to do under linux) to my rescue please. 
What's yet more puzzling, I keep reading reports from people using PC's way less performant than mine, and they manage to get a stable low latencey, medium to high track count recording system. WTH? HW specs will be in my sig and if you need anything like log files or whatever, just let me know. I'll happily provide you whatever I can.

Many TIA for your consideration and patience with an old dude trying to make the impossible a reality maybe?

Raphael ;)

P.S.: The sig. length limit won't allow me to paste extended sysInfo, so here it is (yet longer this post :D):
ASRock K7NF2-RAID-AMD Athlon XP 2200+|2 GB Dual-channel DDR400 Corsair (2x1024)|PCI Network Adapter Realtek 8139|Matrox Mill. G550 DH (2x19" CRT)|M-Audio Delta 1010LT|SB!Live Platinum 5.1|Behringer BCR2000|Logitech Cordless iTouch KB & Cordless Mouseman Wheel|MS SideWinder Dual Strike USB (used as an advanced MIDI Controller)|IDE 1=80 GB WD Caviar 7200/8 MB (Master)/LG DVDRAM GSA-4163B|IDE 2=80 GB Samsung SP0812N 7200/8 MB (Master)/80 GB &#8206;WD800JB 7200/8 MB (Slave)/2x160GB Samsung HD 161HJ SATA|Epson D88 Printer|Artec Ultima 2000 Scanner|Onboard NIC, Serial, Parallel and Audio/MIDI devices are all disabled

---

### Post by pietjanjaap on 2008-04-19
smbus is were the motherboard send info over temperatur and fan speed (and more things),
so something is checking something on the smbus.
But things like this with boot is normal, a lot of things get checked and some fail(different hardware).
Is there a problem with this smbus.
Search google with smbus.

For speed you need to tweak your pc, get the good drivers installed.
Like if you do't have the good grafic driver then there is no speed and high cpu%.
example:
Verifying if install is ok

Run the following command to check its output to ensure the fglrx driver is installed properly:

$ fglrxinfo
display: :0.0  screen: 0
OpenGL vendor string: ATI Technologies Inc.
OpenGL renderer string: ATI Radeon Xpress Series
OpenGL version string: 2.1.7412 Release

The OpenGL vendor string should read ATI and not Mesa.

If it still says Mesa and not ATI, even after re-enabling the driver from the Restricted-manager: 


Disable services in the background,
get enough cpu power, memory, etc.
search more on forums.
Get different linux like xubuntu, fluxbuntu xfce, these run faster.

---

### Post by funkster on 2008-04-19
Cheers pietjanjaap,
all good advice and so on, but I fear I have done already all this. 
I'm running a Matrox Video card actually with the provided mga drivers. There's nothing else for this card anyway. And yes, I do run Mint-XFCE Edition for a lighter wm with a 2.6.22-14-rt kernel .I have no visible services running in the background except what's absolutely needed (dbus, atd, anacron, sysklogd,klogd and gdm) .
As for CPU power and memory, I should have enough to run way more than what is actually possible. 2 GB Dual channel DDR400 from Corsair should be plenty. And my AMD 2200+ can run at least 40 Audio tracks and a few dozen MIDI tracks routed to outboard gear under windows (I'm dual-booting). Reading forums, mailing lists and googling around is all I still do under linux for the moment.  I'm using 5 HD's i.e. 3 IDE & 2 SATA. The OS is getting it's own HD, the home directory gets it's own HD, the page/swap file as well. And the 2 SATA drives are for samples and audio recording respectively.  All those drives are plenty fast with 8MB caches etc. It's not that I'm a complete noob when it comes to optimising my PC for the tasks I need it to do. 
Maybe I should just leave it at that, run linux for what it actually does, that is office apps, internet/mail, some graphic tinkering, and relate to windows for my audio needs. I dunno. I'm tired and fed up of trying and failing and want to enjoy making music again. 

Thanks for stopping by and trying to give me some good advice at least mate, much appreciated.

Raphael ;)

---

### Post by funkster on 2008-04-21
Come on guys, nobody got some other/better ideas? Any hint at what direction I should take? Any tweaks to try? Damn, I would so much like to use this system as my single goto productive machine.

Cheers
Raphael ;)

---

### Post by ububug on 2008-05-11
i fear you have landed in the wrong forum ... speaking from my experience, knowledge of the average ubuntu-user regarding linux or the OS in general does not run very deep (nor does it have to, according to what ubuntu aims to be).

anyway, i cannot think of any advice you may not already have heeded in your - obviously - thorough quest. from what i know of a friend of mine, a musician as well, it was hard to find the right hardware even for the microsoft windows platform ... it took him a long while to find the right configuration and the thing is quite brittle, thus better left untouched (safe for working of course ;)
what he did was researching in internet fora specialised in audio, looking for like-minded people. there you may find someone who already got over the hurdle you are encountering now.

now, audio people on linux are probably in the camp of exotics, so i do want to wish you luck. on the other hand, you can be sure if you find your kind, it will be a small circle of people and it may be safe to assume that they keep up good relations among each other :)

i don't think my post is of any help to you, but i am convinced that you will get something useful out of this forum with utter luck only.

---

