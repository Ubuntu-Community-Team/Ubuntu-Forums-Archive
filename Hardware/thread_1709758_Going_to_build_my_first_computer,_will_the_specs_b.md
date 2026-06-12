---
title: "Going to build my first computer, will the specs be able to run ubuntu nicely?"
date: 2011-03-18
forum: Hardware
---

### Post by adityaparikh1 on 2011-03-18
Hello everyone! 

I'm going to be building my first computer. The computer is low budget but my needs aren't very high either.

The computer will be used for general usage. By general usage I mean, web browsing (running up to 5 tabs at once), watching YouTube videos, listening to Pandora, using OpenOffice.org, using email, playing an occasional Flash-based game, and Skype. 

I am buying the computer parts from CircuitCity.com with a "barebones kit". The kit can be found here: [http://www.circuitcity.com/applications/SearchTools/item-details.asp?EdpNo=89742&SRCCODE=CCDAFFL&cm_mmc_o=-ddCjC7BBTkw%2A%2A%20%2A%2AzuubkbzfwlCjC-d2CjC-uu&id=k54384&sessionid=gan_1300002152]("http://www.circuitcity.com/applications/SearchTools/item-details.asp?EdpNo=89742&SRCCODE=CCDAFFL&cm_mmc_o=-ddCjC7BBTkw%2A%2A%20%2A%2AzuubkbzfwlCjC-d2CjC-uu&id=k54384&sessionid=gan_1300002152")

The specifications of the parts are:
Biostar N68S+ Motherboard
AMD Phenom X4 9100e 1.8GHz AM2+ OEM Quad Core CPU
Masscool Socket 939, 940, AM2 CPU Cooling Fan
Lite-On Internal 24X DVD Writer
Centon 2048MB DDR2 at 800MHz
Seagate Barracuda 7200RPM 500GB Hard Drive
DiabloTek PSDA400 Power Supply
Diablotek CPA-9611B ATX Mid-Tower Case

Will the computer be good enough to run Ubuntu with the uses I need? Also if you are familiar with computer building, can you please tell me if these parts are good, fast, reliable, etc?

Thank you.

---

### Post by Tanker Bob on 2011-03-18
Looks like you should be OK. Ubuntu is compatible with most newer hardware. Usually the major concern is with video cards and 3D driver support. Your Biostar MB has NVidia video support built in, and NVidia works hard to keep their 3D drivers up to date for Ubuntu. 

The specs themselves look more than sufficient to run Ubuntu. Ubuntu will run well on boxes that would choke on other, non-Linux operating systems.

---

### Post by Toafan on 2011-03-18
Hello adityaparikh1, welcome to Ubuntu!

I can't think of any problem with your hardware, it looks to me like you might even be able to run Windows 7 (sure, you'd use up half your RAM just SITING THERE, but it'd run - if I'm right) -- not that I'd recommend it. (the list of things I --dislike-- dis-prefer about win7...)

The thing I'd worry about is *software*. On my Ubuntu machine, for example, YouTube will *skip*. It will also sometimes go mute in the middle of a video. On the other hand, this machine only has 512 Megs RAM, so YMMV. The other thing about Flash etc. is that you may need to install the codecs 'the hard way' - it's not already done for you and the website won't help (I don't think...).
I've used OpenOffice and web browsers on this and slower machines before, no problems. I haven't gotten around to setting up email on it, but I can't imagine a problem. No idea about the others, though (sorry).

You don't have to use Ubuntu (:gasp: ). [http://www.zegeniestudios.net/ldc/](http://www.zegeniestudios.net/ldc/) has a nice 'quiz' to help figure out what Linux distro fits you best. I also recomend finding a good source for tutorials for whatever --version-- distro you go with. For Ubuntu, I personally like Psycocats' ([http://psychocats.net/ubuntu/index.php](http://psychocats.net/ubuntu/index.php)).

Good luck with your machine, whatever you go with.

(and at the end) looks like someone beat me to the reply, so this may now be irrelevant. Oh well.

---

### Post by adityaparikh1 on 2011-03-18
The test did say that Ubuntu was a 100% match for me which is good, I want to know how stable Ubuntu is? I've been running Windows PC's for 12 years now, and haven't had any problems that weren't caused by me.

---

### Post by Tanker Bob on 2011-03-18
BTW, welcome to the forums. I find the building your own machine is the only way to get exactly what you want at a price you're willing to pay. Plus, you appreciate it more when your blood is on the pins and connectors.

I've been running Ubuntu exclusively for over 4 years with no stability issues that I didn't cause. It runs flawlessly on my wife's laptop, otherwise I'd hear about it. :) I ran WinXP since the day it came out, and I find Ubuntu faster, more stable, and more secure. I built this computer from scratch specifically with Ubuntu compatibility in mind and have updated parts (MB, memory, HD array, BIOS) since then without complain from Ubuntu. If I change MB, BIOS, etc. in WinXP, it would complain about authentication.

Come on in, the water's fine!

---

### Post by adityaparikh1 on 2011-03-18
How do I know if I need 64bit or 32bit Ubuntu?

---

### Post by Tanker Bob on 2011-03-18
You have a 64-bit CPU, so you can run either one. 32-bit is generally recommended if you don't have more than about 4 GB of RAM, which you don't. That's what I'd recommend for starting out.

I also recommend that you make 3 partitions for Linux on intial installation. Make a 15 GB root partition, a 1 GB swap, and use the rest of the available space your /home partition. That way, you can upgrade to future versions, go to 64-bit later, or even change distributions w/o affecting your data. 

If you will dual boot to WinXP, install WinXP first in its own partition, then install Ubuntu. That's the easist way to go. Don't let Windows have the entire drive. Give it one partition of whatever size you need, but be sure to leave enough hard drive space for your data under Ubuntu.

---

### Post by adityaparikh1 on 2011-03-18
I don't have a Windows license and I don't want to pay money to buy one, so Ubuntu will be the only OS on the system. I don't understand why I need 3 partitions...I just want to run a simple computer that is stable and is a one-time setup.

Also, how does the update system work on Ubuntu. I know that they make a major release every 6 months, so after I make a CD of 10.10 to install on the computer that I will build, do I have to make another CD and install it every time a new version of Ubuntu comes out?

Also, do you know if these parts are reliable?

---

### Post by adityaparikh1 on 2011-03-19
How does security work in Ubuntu?

---

### Post by racie on 2011-03-19
> **adityaparikh1 said:**
> I don't have a Windows license and I don't want to pay money to buy one, so Ubuntu will be the only OS on the system. I don't understand why I need 3 partitions...I just want to run a simple computer that is stable and is a one-time setup.
Well, you really only need two partitions (the third is optional, but recommended), but let me explain...  You need one main partition, preferably formatted as ext4 (or ext3 if you like), to actually run the operating system.  Your second partition, the swap partition, is needed for hibernation and running multiple programs at once.  Swap is kind of like adding more RAM to your computer.  The third, but optional partition (formatted as ext4 or ext3 again) is used for basically all of your music, videos, documents, downloads, etc.  It is recommended so you don't have to back up all of your files before installing a new OS.

Of course, you don't have to worry about all of this unless you want to.  Letting Ubuntu automatically partition your hard drive during installation works just fine.  The only issue is you won't have the third partition.  (You really don't need it anyway, although I personally have one.)

> Also, how does the update system work on Ubuntu. I know that they make a major release every 6 months, so after I make a CD of 10.10 to install on the computer that I will build, do I have to make another CD and install it every time a new version of Ubuntu comes out?
Ehh... seems to me like it's a bit of a waste of CD's.  I prefer to make USB installs with [Unetbootin](http://unetbootin.sourceforge.net/).  It's a great tool and I really recommend checking it out. :)  You can also just update to the next release through Ubuntu's Update Manager, but it is recommended to do a clean install to make sure everything goes smoothly.  If you have that third partition that was mentioned and you install Ubuntu from a USB every time, it's really quite simple and hassle free.
> Also, do you know if these parts are reliable?
Sorry, I don't know much about hardware in general.  :/

Anyway, good luck with your new desktop!

*edit* Oh... if you need help with formatting, I can walk you through it or refer you to a guide!


Security, eh?  Well you won't have to worry about that too much.  There do exist firewalls and such out there for Ubuntu, but it's really not necessary.  Just be smart in what you install and what you accidentally make changes to or delete. ;)  Yeah, I've accidentally messed up my system before, but it was due to my carelessness and accidentally screwing up system files, not because of any sort of virus. :)

---

### Post by adityaparikh1 on 2011-03-19
> **racie said:**
> You can also just update to the next release through Ubuntu's Update Manager, but it is recommended to do a clean install to make sure everything goes smoothly.

Why, is the Ubuntu Update Manager not trustable? How does security work in Ubuntu?

---

### Post by racie on 2011-03-19
> **adityaparikh1 said:**
> Why, is the Ubuntu Update Manager not trustable? How does security work in Ubuntu?

Oh no, the Update Manager works perfect.  I receive updates daily for my packages.  But installing a NEW RELEASE this way can occasionally leave you with undesired results.  I can't really explain why... I'm not THAT great with computers.  :P

(I edited my other post with some more details btw)

As far as security goes, you really don't have much to worry about.

---

### Post by adityaparikh1 on 2011-03-19
What do you mean by unexpected results when installing new releases? Sorry, I don't mean to be really picky but I just need to know everything before I go through with Ubuntu, because I've had Linux crash on me a lot, when I was testing some old releases on my old computer. 

My plan was to build this computer, put in the Linux 10.10 CD I made from the ISO and then just follow the on screen instructions. Wouldn't that work out okay?

---

### Post by racie on 2011-03-19
> **adityaparikh1 said:**
> What do you mean by unexpected results when installing new releases? Sorry, I don't mean to be really picky but I just need to know everything before I go through with Ubuntu, because I've had Linux crash on me a lot, when I was testing some old releases on my old computer.
Well, it's very difficult to say exactly what would happen.  It's different for everyone.  For some people, everything works great, while others may receive errors and bugs.  Maybe [this thread](http://ubuntuforums.org/showthread.php?t=1595311) will give you a better idea of what I'm talking about.  Note the people who voted in the "upgrade" part of the poll.  Although the results are a bit skewed towards people who have issues with installation/upgrading.  Most people with no issues don't even look at that thread.

> My plan was to build this computer, put in the Linux 10.10 CD I made from the ISO and then just follow the on screen instructions. Wouldn't that work out okay?
Haha, I don't see why it wouldn't!  Just go for it.  :)

---

### Post by adityaparikh1 on 2011-03-19
All right then, since this computer will primarily be used as an internet-based device, it won't really have any personal files on it. So if anything goes wrong when upgrading, worst-case scenario, I have to reinstall Ubuntu.

---

### Post by racie on 2011-03-19
> **adityaparikh1 said:**
> All right then, since this computer will primarily be used as an internet-based device, it won't really have any personal files on it. So if anything goes wrong when upgrading, worst-case scenario, I have to reinstall Ubuntu.

Yeah, basically.  It would probably be wise to backup any of the files you want to make sure you have before you upgrade to any new release.

---

### Post by Tanker Bob on 2011-03-19
Looks like racie handled most of the questions. You can install from the CD and accept the default installation to let Ubuntu set itself up, especially if you don't care abou the data on it later. A dedicated /home partition preserves you data though the six-month upgrades.

The daily update manager works great in Ubuntu. No need to give it a second thought.

The six-month upgrades can either be installed from CD or using the upgrade manager. I've seen arguments both ways, for installing clean (hence the dedicated /home partition) and using the upgrade manager. I usually use the upgrade manager and have never had a problem. The only issue is that the setup files from stuff no longer installed tend to accumulate over time, wasting disk space.

Security is designed into the very nature of Linux. Based on Unix, it was designed from the beginning as a multi-user system with broader access, so has lots of safeguards built in. Windows has been and apparently ever will be primarily designed as a single-user, home system. Very different approaches, and Windows is still trying to catch up. In Linux, you don't have to worry about virii, trojans, worms, etc., so you don't need anti-virus software.

Hope that covers your questions. Bottom line: just plug in and boot the Live CD, double-click on the Install Ubuntu icon, and enjoy the freedom!

---

