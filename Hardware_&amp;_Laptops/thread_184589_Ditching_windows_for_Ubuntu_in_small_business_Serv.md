---
title: "Ditching windows for Ubuntu in small business Servers (Checking new Hardware)"
date: 2006-05-30
forum: Hardware &amp; Laptops
---

### Post by Sapphiron on 2006-05-30
Hi All

Please bear with me on this long post, as i believe in complicated questions with simple awnsers.

I've been in the small business IT sector for about 3 years now working as a private consultant looking to grow a business.  My biggest problem during this time has been inflexible microsoft licencing and horrible price scaling.

All is fine and happy as long as the business has less than 10 PC's.  All you need to do is run a Windows XP server and all is love and happyness.

once you have more than that, Microsoft becomes enourmously expensive.  Effectively you are paying 3 times more per PC than with sub-10 PC networks (because of all the CAL's).

i'm looking to get away from that expensive mess.

I am aware of the limitations of Linux , in that it can't do everything on anything (or at least not yet).  I am not looking for that.  I need a disto that can do basic server and desktop stuff.  Email, Internet, Office, thats it.  NO 3D, No Games, no Multimedia (maybe MP3's).  Basically, I want a Car with power steering and aircon.  No sattelite navigation, no radar guided cruise control or massaging seats.

I am using linux on a gateway server level already for internet, VPN and firewalling services.  I use a disto called Clarkconnect.  I have found it to be excellent, but getting the right hardware to run it on is a problem.  it is ok, because a gateway server is like an appliance, you set it up once on a very light PC and it runs almost forever.

What I am looking for is for Linux to replace my windows XP and 2003 based Servers. and eventually replace my windows XP desktops in some cases, but not all.

From the info I have gathered from the Web, my peers and personal experience, I have found most free linux distro to be a disaster as replacement Servers.  The biggest problem is incompatible hardware.  Especially on Semi-Server Desktop Hardware. Most of the Servers I build for clients are Athlon64 or Athlon64 X2 based hardware (usually using Nvidia chipsets).  

They have been running no problem on Windows, but when I try to load a free linux distro on them, most of the critical hardware is not detected.  Partucularly Software RAID controllers, Network adapters and graphics chipsets.  

The Graphics chipset problems are easily resolved by switching to VESA.  But in in future when I start to use Linux as a Small Business Desktop, I want that running too.

I know that Software SATA RAID controllers are not supported by Linux yet.  To get around that I want to install Hardware RAID controllers.

Network adapters are usually ok, as long as the manufacturer includes a linux driver, but I would prefer it if it worked out of the box.  Untill I tried Fedora Core 5, no Linux distro I tried (Red Hat, SUSE, Mandriva, Debian, Ubuntu 5.x) could give me that.  but Fedora Core 5 is too unstable for production use.  

I am hoping that the new Ubuntu 6.06 would have similar hardware support as it uses a very new Kernel.  

OK HERE COMES MY QUESTION FINALLY
From the info I got it seems that hardware support is determed by what the distro creators include in their boxed kernel.  How can I check if the hardware I am planning to use has the Kernel module uncluded in Ubuntu.  Particularly Critical Components like Hardware SATA RAID Controllers (mainly PCI and PCI-Express adapters from Promise) and network adapters.  Or is there a way of installing these RAID drivers at Boot installation from stiffy, Flashdrive or CD like with Windows XP and Vista.

Typical System would look like this:
Antec desktop Chassis (like the new NSK6500) with 430W PSU
AMD Athlon64 X2 3800+
1-2GB of DDR400 (moving to DDR2 within next 6 months)
ASUS Nforce4 discrete or Nforce430 onboard graphics chipse based boards
2x 320GB SATA HDD on Hardware RAID controller (RAID 1 mirror setup) Also looking at RAID 5 setups with up to 4 drives
2x External USB backup drives
DVD reader drive

How would I start to check if the hardware is compatible.  Keep in mind that I want to stay with the new technology as soon as it is beneficial.

Thank you all in advance.  Hope the forum lives up to it's reputation.

---

### Post by glotz on 2006-05-30
Download a liveCD and give your hw a test spin.

---

### Post by Sapphiron on 2006-05-30
duplicate delete

---

### Post by Sapphiron on 2006-05-30
duplicate deleted

---

### Post by Sapphiron on 2006-05-30
[QUOTE=glotz]Download a liveCD and give your hw a test spin.[/QUOTE]


The idea is to know with reasonable certainty **before** I buy.

I am starting the download now and I will give it a try for the existing servers, but how does that help me check if the hardware is picked up at install time?

---

### Post by glotz on 2006-05-30
Buy? You can download it for free from [http://www.ubuntu.com](http://www.ubuntu.com)

The hw detection is the same for the liveCD and the installer version as far as I know. I think that's one of the points of having a liveCD available. Or then I've misunderstood the question somehow.

---

### Post by Lord Illidan on 2006-05-30
[quote=glotz]Buy? You can download it for free from [http://www.ubuntu.com]("http://www.ubuntu.com")

The hw detection is the same for the liveCD and the installer version as far as I know. I think that's one of the points of having a liveCD available. Or then I've misunderstood the question somehow.[/quote]

I think he is talking about the cost of the hardware, not the software. Is there any reason why you want to use Nforce mobos? I hear that they are incompatible with Linux, why not try something else.

Also, use Nvidia cards. But usually the provided nv drivers suck... You have to get the nvidia-glx packages.
Other than that, Ubuntu should suit you.

BTW, nice noticing that you like Frozen Throne, hehe!

---

### Post by Sapphiron on 2006-05-30
> I think he is talking about the cost of the hardware, not the software. Is there any reason why you want to use Nforce mobos? I hear that they are incompatible with Linux, why not try something else.

Not really, found them better than VIA for windows platforms.  A recent expericence with linux and a new VIA chipset went very bad.  it did not even detect the southbridge, no sound, no network, not even PCI slots (no the board was not faulty).

>  Also, use Nvidia cards. But usually the provided nv drivers suck... You have to get the nvidia-glx packages.
Other than that, Ubuntu should suit you.

usually i go for the onboard nforce410/430.  i just switch everything to VESA.  The only reason I use the GUI as a conveniance on linux servers.  With Fedora 5 the only problem i had was invisible pointer.

[quote=Lord Illidan]BTW, nice noticing that you like Frozen Throne, hehe![/quote]

took me a while to figure that one out.:-k  I acually got the name from my girlfriend 8 years ago.  The game was cool though, just don't like it multiplayer.  it does not "work" for me.  I'm waiting for Total Annihilation's successor Supreme Commander.  That is my type of multiplayer game.  Far too complex and large scale to be as predictable as WC3.

---

