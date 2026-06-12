---
title: "Any Incompatibilities w/ Clevo M570U?"
date: 2006-11-14
forum: Hardware &amp; Laptops
---

### Post by jcq on 2006-11-14
Are there any known incompatibilities with the Clevo M570U notebook (or the Sager 5760 or Hypersonic CX7, which are based on it)?  

Any problems with the touch pad, sound, network, card reader, or built-in web cam?

Thanks in advance...

---

### Post by vakont on 2006-12-03
Generally it works nicely, minus a few things that need fixing.
From the Device manager I see that the Chipset Bridge is not recognized, and it does not recognize the NVidia 9750. The graphics card runs smoothly though with the driver from the Synaptics Pakage Manager (and the according Kernel Module) giving over 22500fps on the glxgears.

The one thing that does not work at all is the DVD-RW, the LG that the M570U natively has installed. It is connected under the SATA protocol and whatever I have done to date hasn't been able to resolve the problem. The scd0 seems to be not present under the /dev folder and if I try the MAKEDEV scd0 command, it will put the scd0-9 in the /dev/.static/dev folder.

So, when I try to point /etc/fstab to the new scd0 device (or any scd or hd for that matter) the response I get it "not a valid block device".

That is the major incompatibility I have with my M570U.

My M570U laptop has:

Intel Pentium Core Duo 2 T7400, 2.16GHz
2GB RAM
nVidia Geforce 7950 512MB DDR3 VRAM
SATA Western Digital HD 120GB (works nicely)
HL-DT-ST DVDRAM (SATA DVD-RW, doesn't work at all, but I installed ubuntu from it!)

I run on Ubuntu Edgy Eft (6.10) as the only OS on my laptop, with all the updates I could get.

---

### Post by jcq on 2006-12-05
Thank you very much for the reply!

I just ordered a Sager 5760 (Clevo M570u) yesterday, and eagerly anticipate trying out ubuntu on it.   So, if I understand you correctly, the DVD drive is recognized enough to do the install, but not thereafter?  That'll be really annoying...  I can get around it by connecting to my desktop I suppose, but still...  Anybody else encounter this and maybe have some idea on a fix?

Also, I'm going to be dual-booting Ubuntu and Windows MCE (switching that to Vista when it comes out)...   Any suggestions on partition size?  I'm getting a 100gig drive, and want to make sure I allow sufficient space for each OS before I allot the rest for miscellaneous storage.  What's a good size for an Ubuntu install?  I will likely want to try at least a couple of games using Wine or Cedega, including WoW.   Is there a decent way to do this having just one install?  It's been some time since I've messed with Linux...  is there smooth NTFS support yet?

Thanks again...

---

### Post by vakont on 2006-12-06
You're very welcome!

> So, if I understand you correctly, the DVD drive is recognized enough to do the install, but not thereafter?
That is correct. I have tried multiple workarounds but I haven't been able to detect a solution. Keep in mind though that your brand of DVD might fall in the supported group.

As for the sizes regarding the dual boot system, that is not too hard if you consider what your primary OS will be. Personally I have only Ubuntu on my laptop, because I am simply sick of Windows. I have a pretty decent Desktop computer where I can play a game or two or do some other work (Pentium D 3.2GHz, 2GB RAM, ATI X1900XT 512MB VRAM, 1 TerraByte Hard drive space). Over there I have WinXP Pro.
I use my laptop for presentations, some graphics, writing and internet applications. Besides, I deeply enjoy the clean, secure and reliable structure of Ubuntu and for now I don't mind this inconvenience (I can always port data with my USB hard drives) or through my local network. I also have it working with Beryl, thus making windows drones drool! As it comes to use Cedega, then yes, a working DVD is required.

As for the NTFS, by default it is read only. If you want to be able to write in NTFS partitions, then you will have to install the required libraries, some of which are in the Ubuntu repositories. I haven't tested them extensively though. There is also the commercial project NTFS-Linux, which allows you to treat those partitions as native ones.

Wine works nicely so far with what little I have tested it with. My more demanding applications though still have a few bugs to work around.

---

### Post by iptechno on 2006-12-27
I have been eyeing one of these myself.  Here is someone who claims to have found the problem with the DVD drive: [http://www.brianparsons.net/]("http://www.brianparsons.net/")
Check out the other links on the site.  There is a lot of info there.

---

### Post by jcq on 2007-01-04
I only just now saw that reply, but thanks, I'll definitely give that a shot!    I did finally get my Clevo m570u, and after some problems with my Windows MCE install (reinstalled twice, finally gave up and installed XP Pro), I'm preparing to put Ubuntu back on there (had it on, but wiped it during my Windows reinstalls).   It was a shame to not have access to the CD drive, and so here's hoping that fix works.

On a separate issue, what's the best way to get Beryl up and running on this machine?   Last time I tried the nvidia beta driver, but seemed to have some graphic anomalies and OS instability.   Should I have gone the AIGLX route instead?

Thanks again...

---

### Post by jcq on 2007-01-04
> **iptechno said:**
> I have been eying one of these myself.  Here is someone who claims to have found the problem with the DVD drive: [http://www.brianparsons.net/]("http://www.brianparsons.net/")
Check out the other links on the site.  There is a lot of info there.

Oh my...   I wish I had seen this before.  I knew (from this thread) that I might have some issues w/ accessing the drive in linux, but had no idea that this also was most likely the cause of the problem I had in MCE as well.    Inexplicably (seemingly...  I forgot that it was right after installing ubuntu) I lost access to my CD/DVD drive in Windows as well.    Sigh.   Well, it's good to finally have an probably explanation, even if after a complete wipe/reinstall.  :)

So now I just need to make sure that reinstalling Ubuntu doesn't end up hosing it in Windows again.   If I understand it correctly, as long as Grub isn't doing the loading and causing the problem, things should work just fine...  it doesn't actually corrupt anything in the OS.  Sound correct?

---

### Post by jcq on 2007-01-04
OK, so what's the best way to approach this?   I'm dual-booting Windows, so should I use that as the main boot loader?

If I install Grub on the linux partition and add it to the Windows loader, that should avoid any problems in Windows, yes?   However, am I to assume by that other thread that I would still have issues in Linux?   How do I switch it to LILO?   I don't remember -- is that an option during the initial Ubuntu install?   The last time I used LILO it was back in the days when it was the only option.  :)

---

### Post by pferraro on 2007-06-14
I have a Clevo M570U as well and had the same problems with Ubuntu not recognizing the CD/DVDRW under Feisty, even after successfully installing it via the LiveCD.  After trying every suggestion under the sun, I finally enabled RAID in the BIOS - even though I only have 1 hard drive.  That did it!  CD/DVD is now recognized and works perfectly.  YMMV.

---

### Post by esme on 2007-06-23
so has anyone managed to get the webcam working under fiesty fawn ?

---

### Post by Spydax on 2007-06-27
pferraro thank you so much!  

esme I'm with you on the webcam issue.  I haven't even started to look into that one.

---

### Post by jcq on 2007-06-30
The CD/DVD drive issue is fixed by using LILO instead of Grub (that's what I had been doing), but if just enabling RAID solves the issue, that's probably the best way to go.   No arcane LILO setup then.  :P

This then brings me to my much more pressing (and annoying) issue w/ Ubuntu on this machine.   Anybody else have problems getting accelerated NVIDIA drivers working?  I have the GeForce Go 7950GTX, and every time I have tried to install the accelerated drivers (through the new Feisty tool, through Automatix, whatever), I end up with instability, lockups, and some graphical corruption upon rebooting.   Anybody who has this working, could you please describe the steps you took?  Dumb it way down for me, since after so many unsuccessful attempts to get this working, I certainly feel that way.  :P

---

### Post by addiakogiannis on 2007-07-18
I installed ubuntu desktop alternate and fixed the resolution from there. After booting I used the experimental driver and nvidia works like a charm!!!!!

I will try the raid solution for the cd-rom now.

By the way, has anyone made web cam work?

---

### Post by jcq on 2007-07-18
Ah, so the alternate install CD allows for some other config with regards to the graphics?   You altered something *prior* to installing the accelerated driver?

Oh, and though the RAID method seemed to remedy the issue with the CD drive not being accessible when I tried it during my last install, it made my Vista installation unbootable because of the drive configuration change.  I'm fairly certain that I could have gotten that to work, but since I needed to use the computer for other stuff right away (and more importantly, since I had the errors w/ the accelerated driver in Ubuntu), I just let Vista redo the boot sector and wipe out Grub.

I'd be willing to give the Ubuntu install another try with the Alternate Install CD if that might help...    I mean, for all I know the problems that I'm having are due to some sort of graphics setting (res, refresh, something...?), but I never get a chance to actually change anything because I start to get lockups as soon as I reboot after installing the driver.  :(

---

