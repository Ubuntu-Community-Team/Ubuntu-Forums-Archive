---
title: "Acer Aspire 5672WLMI"
date: 2006-01-24
forum: Hardware &amp; Laptops
---

### Post by gmc on 2006-01-24
Hi Folks,

Here's sad story about a guy with BIG eye's. I recently asked about Ubuntu's compatibility issues with the Acer 5002WLMI. Well I was planning to get one but when I got to the store, they didn't have any 5002's in stock.

Well I spotted an brand spanking new **Intel based Core Due** (Dual Centrino 1.66Ghz) [Acer 5672WLMI]("http://www.notebookdepot.com/product.asp?productid=453054685&categoryid=1"). It was a little more than I really wanted to spend, but hell who am I kidding... the bragging rights on one of these puppies, was more than I could stand. *So I bought it*.

Unfortunately, this machine is based on the ICH7 chipsets and though I knew I might have problems with the wireless end of the machine, I didn't expect the built-in ethernet port to be a problem.

This port is based on the Broadcom BCM5789 chipset and even though the Tigon3 driver (tg3.ko) loads, it just won't communicate with my router. 

As a result, the default installed kernel with Breezy is not up to date enough to support that ethernet chipset, and I cannot get network access either wireless nor wired.

Is there anywhere I can download a more up to date kernel (preferably deb format), that I can install one my Breezy Install. At this point, the install does not have all the tools to compile my own kernel.

And so, let this be a lesson to you boys and girls, if you buy really new hardware, you're supported hardware problems will be multiplied.

G.

---

### Post by spd106 on 2006-01-24
You could try Dapper. Although it's not offically released yet, most of the milestone development releases are quite stable. The latest one (Flight 3) came out last week. As a bonus you get to join the [laptop testing team]("https://wiki.ubuntu.com/LaptopTestingTeam")

However, I wouldn't suggest using it as your main base. Either dual boot, or use the live cd.

---

### Post by gmc on 2006-01-24
[QUOTE=spd106]You could try Dapper. Although it's not offically released yet, most of the milestone development releases are quite stable. The latest one (Flight 3) came out last week. As a bonus you get to join the [laptop testing team]("https://wiki.ubuntu.com/LaptopTestingTeam")

However, I wouldn't suggest using it as your main base. Either dual boot, or use the live cd.[/QUOTE]

At this point, I really don't have anything to lose. I'll give that a shot on the weekend and see. Thanks

G.

---

### Post by gmc on 2006-01-25
Good News Folks. I took spd106's advice and tried installing the current daily snapshot of Dapper. I now have ethernet access in linux, which supports my research.. 2.6.12+ kernel does support the chipsets in this computer. The only devices not recognized are the ATI X1400 (no suprise there), the Texas Instruments Firewire port and I belive the Blue tooth port.

There were a few hitchs during the install. 

1). No matter what I did, the disk partitioning software and partition assigning process refused to continue until I assigned mounting points for the WinXP partition and the hidden recovery partition. Even after assigning it refused to continue. I had to manually tell it not to return to the partitioning/assignment questions.

2) There appears to be a dependancy problem with the pop up notification program . Though it's not show stopper.

3) No xorg.conf was created and there's no xf86cfg program to create one, but I may still be missing stuff from the xorg subsection. 

There is a fourth problem that I'm looking into, regarding my external usb harddrive and dvdrom. I'm not sure if the usb ports are completely working. When I plug either drive in, I get a read error on the usb driver.

Things are definately taking a turn for the right :-)

G.

Update: 

With the 2.6.15 Kernel, lspci shows the following:

0000:00:00.0 Host bridge: Intel Corporation Mobile Memory Controller Hub (rev 03)
0000:00:01.0 PCI bridge: Intel Corporation Mobile PCI Express Graphics Port (rev 03)
0000:00:1b.0 0403: Intel Corporation 82801G (ICH7 Family) High Definition Audio Controller (rev 02)
0000:00:1c.0 PCI bridge: Intel Corporation 82801G (ICH7 Family) PCI Express Port 1 (rev 02)
0000:00:1c.1 PCI bridge: Intel Corporation 82801G (ICH7 Family) PCI Express Port 2 (rev 02)
0000:00:1c.2 PCI bridge: Intel Corporation 82801G (ICH7 Family) PCI Express Port 3 (rev 02)
0000:00:1c.3 PCI bridge: Intel Corporation 82801G (ICH7 Family) PCI Express Port 4 (rev 02)
0000:00:1d.0 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI #1 (rev 02)
0000:00:1d.1 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI #2 (rev 02)
0000:00:1d.2 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI #3 (rev 02)
0000:00:1d.3 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI #4 (rev 02)
0000:00:1d.7 USB Controller: Intel Corporation 82801G (ICH7 Family) USB2 EHCI Controller (rev 02)
0000:00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev e2)
0000:00:1f.0 ISA bridge: Intel Corporation 82801GBM (ICH7-M) LPC Interface Bridge (rev 02)
0000:00:1f.2 IDE interface: Intel Corporation 82801GBM/GHM (ICH7 Family) Serial ATA Storage Controllers cc=IDE (rev 02)
0000:00:1f.3 SMBus: Intel Corporation 82801G (ICH7 Family) SMBus Controller (rev 02)
0000:01:00.0 VGA compatible controller: ATI Technologies Inc: Unknown device 7145
0000:03:00.0 Network controller: Intel Corporation: Unknown device 4222 (rev 02)
0000:04:00.0 Ethernet controller: Broadcom Corporation NetLink BCM5789 Gigabit Ethernet PCI Express (rev 21)
0000:0a:09.0 CardBus bridge: Texas Instruments: Unknown device 8039
0000:0a:09.1 FireWire (IEEE 1394): Texas Instruments: Unknown device 803a
0000:0a:09.2 Mass storage controller: Texas Instruments: Unknown device 803b

The USB Chipset is identified but does not work. I'm also not having much luck with the ATI x1400, though I did find the vesa driver works in xorg @ 1024x768.

G.

---

### Post by soc on 2006-02-05
hi!
i consider buying a Acer Aspire 5672WLMI and installing dapper on it.
i would be really happy if you could provide me with additional information.
- cardbus and firewire aren't really interesting to me, but what about
- usb? could you get it working?
- processore features? do things like hibernate or the different sleep states work? does it change the processore frequency and the fan speed correctly? 
- special keys? work they out-of-the-box or did you some manual work?
- what about the x1400? hardware acceleration won't work because ati hasn't released a working binary for xorg7. could you set your screen to 1280x800 with the vesa drivers?
- does the sound work?
- did you test the integrated webcam? (although i won't need it as far as i expect)
thx!
ps: if we could get more information togehter, we could provide these information to the laptop testing team as spd160 mentioned.

---

### Post by gmc on 2006-02-09
Hi Soc,

Sorry for the long delay in relpying. Work and other threads have been keeping my pretty busy.

[QUOTE=soc]
- cardbus and firewire aren't really interesting to me, but what about
- usb? could you get it working?
[/QUOTE]

Yes, I do have USB working, and according to a friend of mine (Anna in Hawaii) the bluetooth port works too. I don't have any firewire devices to test on the machine so that's unknown at this time. The USB problem that I was having turned out to be caused by the USB hub I was using. My old laptop only had 2 USB v1.1 ports, so I needed the hub to connect my USB mouse, USB external harddrive and USB externel dvdram drive. Since this machine has 4 USB ports built-in, I no longer need the hub.

[QUOTE=soc]
- processore features? do things like hibernate or the different sleep states work? does it change the processore frequency and the fan speed correctly?
[/QUOTE]

After installing the "linux-686-smp" meta-package, both processors are recognized and used. Hibernation/Sleep appear to need some tweaking, but the FN-F4 key does cause the machine to sleep but reboots upon waking it up. The CPU speed stepping and fan both work flawlessly. Interestingly enough, dual CPU's don't generate nearly as much heat as I expected. My old Toshiba Satellite Pro 4600 get's hotter than this machine.

[QUOTE=soc]
- special keys? work they out-of-the-box or did you some manual work?
[/QUOTE]

This is still a work in progress, however the key combinations to adjust the screen brightness and audio volume control work out of the box (in Dapper).

[QUOTE=soc]
- what about the x1400? hardware acceleration won't work because ati hasn't released a working binary for xorg7. could you set your screen to 1280x800 with the vesa drivers?
[/QUOTE]

The Radeon Mobility X1400 is the one sore spot. Yes, I do have the vesa driver displaying 1280x800x24 but text and images are stretched horizontally. I have been tweaking the kernel boot option "video=" and dpi settings in Xorg/Gnome and it's not as bad as it was when I originally installed Dapper. I'm looking forward to trying ATI's drivers when they arrive.

[QUOTE=soc]
- does the sound work?
[/QUOTE]

Yes, sound does work, but is full of static. The Ubuntu startup audio is the worst, Frozen-Bubble seems to be ok. Once again this is a work in progress.

[QUOTE=soc]
- did you test the integrated webcam? (although i won't need it as far as i expect)
[/QUOTE]

I've not played with that yet. Under WinXP it's pretty good, I played with Acer's software for it and was quite impressed with the quality of the images and features.

[QUOTE=soc]
PS: if we could get more information together, we could provide these information to the laptop testing team as spd160 mentioned.[/QUOTE]

I would point out that the battery monitor (acpi) does not work at this time, I know I need to play with the dsdt support but it looks pretty complicated, so I'll leave that for the time being. I'm working on a webpage to post on "Linux on Laptops" and "TuxMobile". Overall, Dapper in it's current state is doing a fantastic job with this machine. I'm so looking forward to wiping WinXP off of it and dedicating it to Ubuntu.

G.

---

### Post by Clint. on 2006-02-10
To Whom It May Concern of the ubuntu Community:


   I know what you all are going through with Acer Notebooks.  October 2005, I got an Acer Aspire 3613 WLCi notebook from my College.  I have been using linux for over a year now.  However, I became more involved teaching myself line commands, and navigating around the file system.  Yes people wonder; will I be able to use my nice wireless at college? How about the cafe you like to go to, or even a local pub, and any place that provides wireless?  Ubuntu I have to say, is the best hardware detection I have found for my new laptop.  It's just time and patience for us laptop users with new hardware.  Furthermore, if we study & research the information it will take to fix the issues, open source will prevail. In conclusion, I gave myself a motive.  "The sky is not the limit, if we traveled to the moon"  ~Clint~

---

### Post by Kenotic on 2006-02-11
I also have an aspire 5670. I will be watching this thread closly to see your progress.

---

### Post by ccf on 2006-02-11
> October 2005, I got an Acer Aspire 3613 WLCi notebook from my College. 

aptitude install linux-restricted-modules
modprobe ath_pci

The 3610 series I believe uses Atheros chipsets, despite the Broadcomm label on the underside of the laptop (lspci -vv is your friend).  If you frequent several different wireless networks, you might want to put nm-applet on your panel somewhere.

What I need to figure out is frequency scaling etc. (which currently my lappy claims "is not supported", which I know to be a lie). 90 minute battery life is not acceptable.

---

### Post by dyous87 on 2006-02-17
i recently go my new aspire 5672wlmi and i don't know what to do to get ubuntu to work. as of now i'm stuck using windows it's horrible :cry:

---

### Post by gmc on 2006-02-21
Hi dyous87,

You could do what I did. Download the current release of Dapper and installing that.

The biggest problem is the 2.6.11/12 kernel that is currently used in Breezy doesn't recognize any of the pci hardware (especially the ethernet port and thus no working network access). You shouldn't have any problems downloading and burning the Dapper .iso using the NCI CD/DVD maker that's included with the system.

Under Dapper, you *must* to use the Xorg vesa video driver as our ATI X1400 is not supported yet. (Don't bother trying the ATI native drivers, they don't work). You most probably will want to install the linux-686-smp metapackage to enable Dapper to make use of both your processors. Other than that, Dapper is quite usable on the 5672. though be warned, if you aren't comfortable with command line tweaking, you might want to suffer with XP for the time being and wait for the stable release of Dapper. 

In my travels, I've read in several places that ATI is expected to release X1xxx native drivers sometime this spring and although there is support for the internal wireless network adapter, it requires a custom kernel with an additional patch, that apparently is not compatible with kernels with smp support. 

So until that problem is resolved, it's a trade off, wireless connectivity or smp support, I chose smp support.

G.

---

### Post by drgreborn on 2006-02-25
I'm looking at getting this laptop so I'll be keeping aclose eye on this thread. So in general the only thing not working properly is the X1400 card?

---

### Post by gmc on 2006-02-25
Hi DrGreborn,

[QUOTE=drgreborn]I'm looking at getting this laptop so I'll be keeping aclose eye on this thread. So in general the only thing not working properly is the X1400 card?[/QUOTE]

Correct. The X1400 is the one part of the system that will have to wait until ATI developers release drivers for it. On the whole, I'm pretty impressed with the over all speed and features of this laptop. :-)

G.

---

### Post by drgreborn on 2006-02-25
its been what 5 months since x series came out? should there be linux driver out by now? the nvidia ppl were rather timely with theirs.

---

### Post by niv on 2006-02-25
These are the first laptops to have the Mobility X1xxx cards, and many of them are still on pre-order...

I'm looking forward to any progress you make, gmc (especially with the Intel 3945ABG wireless), since I have the same model laptop. My Windows XP Home installation decided to FUBAR itself, and none of the Windows XP setup CDs will load (they get to the Windows is starting Setup message and then die). I figure it's about time for me to make my transition to *nix, and since this isn't my primary computer and is portable (so I can bring it over to a friend's for help) I would be willing to take a risk with it. Good luck.

---

### Post by gmc on 2006-02-26
Hi drgreborn,

[QUOTE=drgreborn]its been what 5 months since x series came out? should there be linux driver out by now? the nvidia ppl were rather timely with theirs.[/QUOTE]

You would think so, but I guess we'll just have to wait. Hopefully we'll have something to play with in the next month or two.

G.

---

### Post by skychris on 2006-02-26
Hi everybody,

I also just bought an Acer 5672. As I am just starting with Linux, I installed it on a new partition, keeping Windows (for now). After reading the previous topics here, I realize that it's gonna be quite an adventure to install linux on a machine like this. 
After having installed the latest Dapper, I am still stuck with an non working wifi and no graphic card found either. And here's my question.
After the system tells me that it can't install X-window, I end up with a prompt. At this time, do I have all the command available under linux ? ( apt-get, sudo, mount etc...) or is it kinda stuck halfway through the installation. 
and what's the difference or relation between X-window, Xfree, Xorg. I am sorry if it is too trivial, but I've been on the windows dark side too long and all those new terms confuse me.

best regards

Chris

---

### Post by gmc on 2006-02-26
Hi skychris,

[QUOTE=skychris]Hi everybody,

I also just bought an Acer 5672. As I am just starting with Linux, I installed it on a new partition, keeping Windows (for now). After reading the previous topics here, I realize that it's gonna be quite an adventure to install linux on a machine like this. 
After having installed the latest Dapper, I am still stuck with an non working wifi and no graphic card found either. And here's my question.
After the system tells me that it can't install X-window, I end up with a prompt. At this time, do I have all the command available under linux ? ( apt-get, sudo, mount etc...) or is it kinda stuck halfway through the installation. 
and what's the difference or relation between X-window, Xfree, Xorg. I am sorry if it is too trivial, but I've been on the windows dark side too long and all those new terms confuse me.

Chris[/QUOTE]


Welcome to the club. If you 'sudo dpkg-reconfigure xserver-xorg' and choose the vesa video driver. Currently only vesa drivers work with the X1400 chipset. This should at least get you up and running in Xorg. As for the wireless, unless you're comfortable patching and recompiling the kernel, I'd leave that alone for a bit, at least until Dapper becomes stable.

G.

---

### Post by gmc on 2006-02-27
Thought anyone following this thread might be interested in reading this blog that I found on
digg,com. [Driver Heaven]("http://www.driverheaven.net/%7Epete/article5.htm") has an interesting article for us currently unsupported ATI X1xxx video cards.

Looks like it's going to be a while before we see linux drivers.

G.

---

### Post by niv on 2006-02-27
A word of warning to whoever wants to remove their service partition but still wants to use Windows for the timebeing--make sure to disable the boot option first. 

Unlike an IBM in different [thread]("http://ubuntuforums.org/showthread.php?t=136293"), my Acer decided that it was appropriate to create a 1 byte-length service partition starting at cylinder 0 because it was missing and Acer's engineers figured that would have been the correct response...for whatever reason why (or ignored that possibility). Because of that, Ubuntu (until after a few tries), MEPIS, and of course, Windows, didn't boot. Knoppix 4.0.2 miraculously did (using nopcmcia), and I managed to erase that partition with the help of a professor at my college. 

So there you go. Off to call Acer to tell them to cancel the pickup of my laptop... [-(

---

### Post by gmc on 2006-02-27
Hi niv,

[QUOTE=niv]A word of warning to whoever wants to remove their service partition but still wants to use Windows for the timebeing--make sure to disable the boot option first. 
[/QUOTE]

Are you referring to the 4gig hidden partition? or are you saying your recovery dvd damaged your hidden partition? Just trying to clarify a problem that I had when I first installed Ubuntu.

G.

---

### Post by drgreborn on 2006-02-28
[QUOTE=gmc]Thought anyone following this thread might be interested in reading this blog that I found on
digg,com. [Driver Heaven]("http://www.driverheaven.net/%7Epete/article5.htm") has an interesting article for us currently unsupported ATI X1xxx video cards.

Looks like it's going to be a while before we see linux drivers.

G.[/QUOTE]
5 months close to half a year. Unacceptable. But ATi been known to consolidate all bugs and then realease a large patch or what not. But the fact remains there wasn't even a driver to patch in the first place.

---

### Post by niv on 2006-02-28
gmc, I was referring to the recovery partition. The recovery disc won't work anyway, it was complaining about the number of partitions and then promptly died... :rolleyes:

---

### Post by dyous87 on 2006-02-28
ok so in that case as soon as i go home tonight i will download and install dapper drake.  i was just wondering if maybe that didn't work either because when i tried the dapper live cd i had a whole bunch of error messages that were coming up. 

as far as the 4 gig restoration partition...i could keep that on my system in case anything goes wrong right? just encase i run into problem one day and need to reinstall xp (even though i really don't see what could possess me to want to do that). what about those restoration cd's acer makes you burn when you first start up your computer. do those disks allow you to reformat the hdd and reinstall xp?

lastly you had said that if i install the package that allows for dual processor support then i cannot use the native wireless drivers. that being said, i should still be able to use the windows drivers with ndiswrapper to get wireless running shouldn't i?

thanks for your help in advance! :)

---

### Post by niv on 2006-03-01
That disc is rather useless...it complained about my # of partitions and then decided that it would just exit. You only have two options after booting that disc--1. Language, 2. Factory Reset. The factory reset doesn't seem to work when you really need it... \\:D/

---

### Post by dyous87 on 2006-03-01
ok well i created a new partition and got dapper installed. everything seemed to go smoothly but then when i went to boot into ubuntu the first time i got a few error messgaes and a blank screen. ok i restarted and this time was able to get into the command line. configured xserver with the vesa drivers and started x. everything seems to be runnign smoothly so far. the resolution is wierd...lol has anyone been able to run this at the native resolution? also has anyone been able to fix the sound issue...

...well anyway i'm gona play around with it now to see what i can do. i'll be keeping an eye on this thread and posting any progress that i make

thanks -- dave

edit: ok i was able to get the smp package installed, now linux should taking advantage of the dual processors. is there anyway to be sure of this?

also does anyone have any idea how i could get wireless working with smp, it's very important that i have wireless since this is my tavelling computer which i take to school with me and i have no ethernet jack where i work from at my house...

other then that things seem to be going great...now if only we could find a way to get it running with native resolution that would be great!

---

### Post by gmc on 2006-03-01
[QUOTE=dyous87]
edit: ok i was able to get the smp package installed, now linux should taking advantage of the dual processors. is there anyway to be sure of this?

also does anyone have any idea how i could get wireless working with smp, it's very important that i have wireless since this is my tavelling computer which i take to school with me and i have no ethernet jack where i work from at my house...

other then that things seem to be going great...now if only we could find a way to get it running with native resolution that would be great![/QUOTE]

If you're still struggling with Xorg, you'll want to 'sudo dpkg-reconfigure xserver-xorg' and select the vesa driver. To check if both cpu's are working, try 'cat /proc/cpuinfo'. If both processors should be listed. As for wireless, I have a page that talks about what to try, though I should warn you, the author reports that he could not get wireless working on an smp enabled kernel.

Unfortunately I'm just on my way to work, so I'll dig out that page and post it here in the morning.

G.

Edited: Here's that [website]("http://ndiswrapper.sourceforge.net/mediawiki/index.php?title=List&printable=yes") that I found information on patching the kernel to get the Intel Pro/Wireless 3945ABG. Just search (ctrl-f) for 3945 will take you to the information and has a link to the patch (though I've not tried it at all)

G.

---

### Post by gmc on 2006-03-02
Hi niv,

[QUOTE=niv]gmc, I was referring to the recovery partition. The recovery disc won't work anyway, it was complaining about the number of partitions and then promptly died... :rolleyes:[/QUOTE]

Ouch! Ok that's not the same problem I had. I guess it might be advisable to leave that partition alone. If you wish I can make an .iso of the recovery dvd and post it online for you to download if that helps. We can make arrangements privately if you wish.

I had reason to use mine the day I installed Breezy on this machine and ended up with a non bootable system. Scared the hell out of me, but Dapper saved the day.

G.

---

### Post by niv on 2006-03-02
Oh, don't put any effort into it. Everything's working fine now--just disable that BIOS option and it's all good.

Mind you, I did have a copy of that disc. It just doesn't work. I frankly don't need the headaches and space wasted (both physically and digitally).

---

### Post by gmc on 2006-03-02
Hi Niv,

[QUOTE=niv]Oh, don't put any effort into it. Everything's working fine now--just disable that BIOS option and it's all good.

Mind you, I did have a copy of that disc. It just doesn't work. I frankly don't need the headaches and space wasted (both physically and digitally).[/QUOTE]

I hear that. I'm so thankful that Dapper is at least stable enough to keep me from using Windows. I'm looking forward to dedicating this machine to Linux and formatting those nasty partitions :-)

G.

---

### Post by dyous87 on 2006-03-02
so i have to patch my kernel to use 16 stacks instead of 8. the site isn't really clear though. how would i go about doing that? :confused:

---

### Post by gmc on 2006-03-03
Hi Dyous87,

[QUOTE=dyous87]so i have to patch my kernel to use 16 stacks instead of 8. the site isn't really clear though. how would i go about doing that? :confused:[/QUOTE]

A lot of prayer :-) .. seriously, I've been planning to try patching my kernel, but since Dapper is still dynamic as far as packages coming down the pipe. I've been delaying it. The basic procedure is to download the Dapper kernel source code and Ubuntu specific patchs. Apply those patchs so the kernel you are building is identical the the binary only version. Then apply the wireless patch, compile and pray that it works.

As the note on that page says, the guy could not get it working with smp enabled kernels, so you have to understand that you *may* have wireless or you *can* have the kernel use both cpu's, it's one or the other.

Anyhow, if you want to try, search these forums for information on building a custom kernel and pay particular attention to any info on applying Ubuntu specific patchs. By the time you've worked your way through that, you'll know what to do to add the wireless patch.

If you've never built a custom kernel, it's a fun experiance and I recommend it to anyone who like to delve that deep into the guts of Linux, but if you're not comfortable with the idea. Don't do it, it's easy to screw up your system and cause a lot of headaches.

G.

EDITED: I found [this link]("http://support.intel.com/support/notebook/sb/cs-006408.htm") (search 3945). Looks like Intel is committed to releasing native drivers for our beloved 3945 chipset. This being the case, I would if you can, recommend waiting until then to seriously try to get wireless working. Now of only ATI would do the same, I'd be a happy camper

EDITED: While browsing the laptop forum, I found [this link]("http://ipw3945.sourceforge.net/") which also looks promising for drivers for our 3945 :-)

---

### Post by gmc on 2006-03-08
Hi Folks,

Since a number of people said they were going to be following this thread or are owners
of the above laptop. I thought you'd be interested in the following support ftp site:

[ftp://ftp.support.acer-euro.com/notebook/aspire_5670/]("ftp://ftp.support.acer-euro.com/notebook/aspire_5670/")

Since sourceforge has opened a page for driver support for the 3945ABG chipset. I'm in the process of trying to apply the appropriate patchs and compile a custom kernel.

I'll post my results in a few days or so...

G.

---

### Post by bwanab on 2006-03-15
This thread has been a huge help for me getting my 5672 going. Other than the ATI x1400 problem (which given my use isn't a huge problem - just the general ugliness of appearance), my system is working nicely. 

One question. I tried to use ndiswrapper with the windows driver for wireless. When I installed the driver through ndiswrapper, it said the hardware was there, but when I try to configure it with iwconfig, no wireless is found. This is my first time trying this, so I easily could have done something wrong. Is there any reason to think that this approach will or won't work? Not a huge issue, but it would be convenient to have wireless until the intel 3945 drivers are ready.

EDIT: This guy [http://www.novaglobal.com.sg/?q=Acer_5672WLMi]("http://www.novaglobal.com.sg/?q=Acer_5672WLMi") claim's to have gotten the intel drivers to work. No details, though.

---

### Post by gmc on 2006-03-15
Hi bwanab

[QUOTE=bwanab]This thread has been a huge help for me getting my 5672 going. Other than the ATI x1400 problem (which given my use isn't a huge problem - just the general ugliness of appearance), my system is working nicely. 

One question. I tried to use ndiswrapper with the windows driver for wireless. When I installed the driver through ndiswrapper, it said the hardware was there, but when I try to configure it with iwconfig, no wireless is found. This is my first time trying this, so I easily could have done something wrong. Is there any reason to think that this approach will or won't work? Not a huge issue, but it would be convenient to have wireless until the intel 3945 drivers are ready.[/QUOTE]

You're further along that am I, in getting wireless working on the 3945 than I am. I've been trying to patch my kernel but for some reason, I'm not having any luck what's so ever. Have tried following the instructions [here]("http://ipw3945.sourceforge.net/"). This is a native driver but it's pretty complicated to get working.

If you try it and get any success, please let me know. 

Frustrated.
G.

---

### Post by dyous87 on 2006-03-15
I've also attempted using ndiswrapper and have been unsuccessful.  In order to get the wireless working you need to create a custom kernel that uses 16 stacks instead of the default 8.  This isn't something I've tried yet as I have no idea how to even go about doing it so for now I'm stuck using xp most of he time which is really annoying :rolleyes: btw I've read somewhere that a MEPIS default install has the graphics working at native resolution. If anyone knows any more on this like how they got it to work right or what drivers they used it would be a big help...

---

### Post by gmc on 2006-03-17
Hi dyous87,

[QUOTE=dyous87]I've also attempted using ndiswrapper and have been unsuccessful.  In order to get the wireless working you need to create a custom kernel that uses 16 stacks instead of the default 8.  This isn't something I've tried yet as I have no idea how to even go about doing it so for now I'm stuck using xp most of he time which is really annoying :rolleyes: btw I've read somewhere that a MEPIS default install has the graphics working at native resolution. If anyone knows any more on this like how they got it to work right or what drivers they used it would be a big help...[/QUOTE]

Mepis is also limited to using the vesa driver under xorg, and so is also limited to 1024x768 mode. I did find a lot of interesting information (mostly for WindowsXP) ... [here]("http://forum.notebookreview.com/forumdisplay.php?f=22").

Until ATI releases native linux drivers for our X1400, 1024x768 is the best you'll be able to get.

G.

---

### Post by dyous87 on 2006-03-17
[QUOTE=gmc]Hi dyous87,



Mepis is also limited to using the vesa driver under xorg, and so is also limited to 1024x768 mode. I did find a lot of interesting information (mostly for WindowsXP) ... [here]("http://forum.notebookreview.com/forumdisplay.php?f=22").

Until ATI releases native linux drivers for our X1400, 1024x768 is the best you'll be able to get.

G.[/QUOTE]

I figured so but i was wondering if maybe they used a different driver to get it working because on [this forum]("http://forum.notebookreview.com/showthread.php?t=37507") someone had stated that mepis had no trouble displaying at native resolution:

-------------------------------------------------------------------------
[SIZE="1"]Quote:
[I]Originally Posted by chuckey
Sweet! Does MEPIS display properly at the native resolution (1280X800)? If so, I've gotta give it a shot[/I]

Yes, no problems in display whatsoever. I had some problems booting up today, it used to just hang in the process. But used the 'noauto' option in the boot command (from [http://www.mepis.org/node/1386](http://www.mepis.org/node/1386)) and it works now.

Display, Audio, USB mouse, ethernet working till now. Tried wireless with ndiswrapper (with w39n51.inf), but it didnt load.[/SIZE]
----------------------------------------------------------------------------
....but anyay they could have just been mistaken. The resolution is the least of my concerns for now...back to trying to get wirelss running lol :-k

---

### Post by kingsidy on 2006-03-17
i have a travelmate 4202. the specs are similar to the aspire 5672 as far as wireless chipsets. I also have been trying to get it work with no success. If anybody does get it work please post I am trying to follow the intruction on the ipw.3945 sourceforce project but still no luck. I hope that it gets supported with dapper upon the final release.

---

### Post by justhamade on 2006-03-18
I have a Acer TravelMate 4202 which uses the same wireless driver as your laptop.  I just posted some detailed instruction on using the [ipw3945 driver from sourceforge]("http://ipw3945.sourceforge.net/#requirements") in another thread [http://www.ubuntuforums.org/showthread.php?p=837922#post837922]("http://www.ubuntuforums.org/showthread.php?p=837922#post837922")

Hope that helps you guys. 

Justin

---

### Post by gmc on 2006-03-19
Hi Justin,

[QUOTE=justhamade]I have a Acer TravelMate 4202 which uses the same wireless driver as your laptop.  I just posted some detailed instruction on using the [ipw3945 driver from sourceforge]("http://ipw3945.sourceforge.net/#requirements") in another thread [http://www.ubuntuforums.org/showthread.php?p=837922#post837922]("http://www.ubuntuforums.org/showthread.php?p=837922#post837922")

Hope that helps you guys. 

Justin[/QUOTE]

E-X-C-E-L-L-E-N-T !! As soon as I get a couple of hours sleep, I'll give it another go. You know, this is exactly why Ubuntu is so popular.. user to user help! 

Thanks
G.

Edited: Success... go to [this thread]("http://www.ubuntuforums.org/showthread.php?t=140085&highlight=gmc") for detailed instructions on how to get the 3945 working :-)

G.

---

### Post by bwanab on 2006-03-20
posted by gmc:

> Edited: Success... go to this thread for detailed instructions on how to get the 3945 working


gmc, did you solve the problem of getting it to load a boot time?

---

### Post by bwanab on 2006-03-20
[QUOTE=bwanab]posted by gmc:



gmc, did you solve the problem of getting it to load a boot time?[/QUOTE]

Edit: Well, it looked good at first :cry:  When I first went through the procedure, everything built ok, then I did the sudo ./load and it found the wireless card. I did iwconfig eth1 and it identified it correctly. Then I tried to configure it and it hung. I rebooted, and now every time I try to do the sudo ./load, it just hangs. Any ideas?

---

### Post by gmc on 2006-03-21
[QUOTE=bwanab]Edit: Well, it looked good at first :cry:  When I first went through the procedure, everything built ok, then I did the sudo ./load and it found the wireless card. I did iwconfig eth1 and it identified it correctly. Then I tried to configure it and it hung. I rebooted, and now every time I try to do the sudo ./load, it just hangs. Any ideas?[/QUOTE]

Are you loading the ipw3945 driver? Edit /etc/modules and add "ipw3945" to the end. As for automatically loading, yes but I cheated. I created a symbolic link to the "load" script in /etc/rc2.d by doing a 'ln -s /usr/src/ipw3945/load /etc/rc2.d/S99wireless'. It seems to work. Unfortunately I've broken something by trying to add wpa/wpa2. Back to the drawing board. You may also want to install NetworkManager, though I'm not sure that I actually need it.

G.

Edited: Ok, I've got things working again. I managed to get WEP working, but no luck with WPA. I suppect the problem with that is me. The best I was able to get was a message from NM (NetworkManager) saying, my hardware doesn't support the encryption.

---

### Post by bwanab on 2006-03-23
[QUOTE=gmc]Are you loading the ipw3945 driver? Edit /etc/modules and add "ipw3945" to the end. As for automatically loading, yes but I cheated. I created a symbolic link to the "load" script in /etc/rc2.d by doing a 'ln -s /usr/src/ipw3945/load /etc/rc2.d/S99wireless'. It seems to work. Unfortunately I've broken something by trying to add wpa/wpa2. Back to the drawing board. You may also want to install NetworkManager, though I'm not sure that I actually need it.

[/QUOTE]

I added ipw3945 to /etc/modules, but found that "sudo ./load" was still hanging. I traced through the load script using debug messages and found that it is hanging trying to unload the modules which doesn't make sense to me. Why is load unloading first? At any rate, it seems that what load does is unload all the modules with rmmod, then load the modules again with depmod, then runs the daemon. I tried just running the daemon by hand and this reported that it successfully found the interface and ipwconfig eth1 reports that everything looks ok. However, when I try to configure the network, it hangs. Is there any debug that I can do at this point to figure out what is wrong?

---

### Post by gmc on 2006-03-24
Hi bwabab,

[QUOTE=bwanab]I added ipw3945 to /etc/modules, but found that "sudo ./load" was still hanging. I traced through the load script using debug messages and found that it is hanging trying to unload the modules which doesn't make sense to me. Why is load unloading first? At any rate, it seems that what load does is unload all the modules with rmmod, then load the modules again with depmod, then runs the daemon. I tried just running the daemon by hand and this reported that it successfully found the interface and ipwconfig eth1 reports that everything looks ok. However, when I try to configure the network, it hangs. Is there any debug that I can do at this point to figure out what is wrong?[/QUOTE]

This is weird. Can you post a copy of 'lspci -vv' (thats 2 v's, not a w). I'm wondering if you have a different version of the 3945 chip. Either that, or (and I hate to suggest it) try re-installing Dapper from scratch and try following the instructions again.

G.

---

### Post by tonitonitoni on 2006-04-04
I had the same problem with my laptop.
I've modified the official driver (8.23.7) to recognise the X1400 card, but that's just a workaround. At least I can use the native resolution now (1280x800).
Visit [http://toni.to/ati.html]("http://toni.to/ati.html") for details.

Toni

---

### Post by bwanab on 2006-04-04
[QUOTE=tonitonitoni]I had the same problem with my laptop.
I've modified the official driver (8.23.7) to recognise the X1400 card, but that's just a workaround. At least I can use the native resolution now (1280x800).
Visit [http://toni.to/ati.html]("http://toni.to/ati.html") for details.

Toni[/QUOTE]
Well, I tried. Lord knows I don't know what I'm doing, but it looks like your fix works for xorg 6.8, but dapper has moved on to 7.0. I'm probably way off base here, but when I installed the 8.23.7 from ati, the file that you mentioned (/usr/X11R6/lib/modules/drivers/fglrx_drv.o) was there, but when I replaced it and configured xorg.conf for fglrx no driver was found. It is looking for fglrx_drv.so in /usr/lib/xorg/modules/drivers. Just for fun, I put your fglrx_drv.o into that directory and it seemed to read it, but then it complained that it was looking for 7.0, but found 6.8.
I tried using beav on the supplied fglrx_drv.so (with the latest dapper stuff), but I found too many references to 4f 5e to pin it down. Alas, one more failure at workarounds for me ](*,) Back to vesa.

---

### Post by tonitonitoni on 2006-04-05
Hi,

The official ATI driver is for X.Org 6.8 only.
Since my workaround isn't working for you, I hope ATI won't wait too long to release the new driver. Hopefully with the native support for X1xxx.

Or you could try to pin down the rigth reference to 4f 5e with my help ;-)
You should be looking for the table of known IDs. The following IDs should be very close to each other:
4a 5e
4b 5e
4c 5e
4d 5e
4f 5e
(those are the IDs of the X700 card).
Just replace any of those IDs with the ID of your graphics card.
Note the reversed byte order: if the ID of your card is 71 45, replace one of the above IDs with 45 71.

That should work for any X1xxx card, but don't expect any advanced features to work.

What's the exact size of your driver?

Toni

---

### Post by bwanab on 2006-04-05
[QUOTE=tonitonitoni]Hi,

The official ATI driver is for X.Org 6.8 only.
Since my workaround isn't working for you, I hope ATI won't wait too long to release the new driver. Hopefully with the native support for X1xxx.

Or you could try to pin down the rigth reference to 4f 5e with my help ;-)
You should be looking for the table of known IDs. The following IDs should be very close to each other:
4a 5e
4b 5e
4c 5e
4d 5e
4f 5e
(those are the IDs of the X700 card).
Just replace any of those IDs with the ID of your graphics card.
Note the reversed byte order: if the ID of your card is 71 45, replace one of the above IDs with 45 71.

That should work for any X1xxx card, but don't expect any advanced features to work.

What's the exact size of your driver?

Toni[/QUOTE]

It worked! I sure wouldn't have found it without your help. Thanks. This is such a huge improvement. I've put my doctored version of fglrx_drv.so [here]("http://juraview.com/fglrx_drv.so")

---

### Post by tonitonitoni on 2006-04-06
[QUOTE=bwanab]It worked! I sure wouldn't have found it without your help. Thanks. This is such a huge improvement. I've put my doctored version of fglrx_drv.so [here]("http://juraview.com/fglrx_drv.so")[/QUOTE]

I'm glad I could help :KS 

Cheers,
Toni

---

### Post by sharedagroove on 2006-04-07
I just used the driver that Bwanab posted and it worked great

Thanks guys


Edit:

Resolution is working great but cannot play videos

---

### Post by qpad on 2006-04-07
Hello,

First of all thanks for the x1400 video tips ! It's much better with native resolution !

Now is anyone able to watch dvd with this Aspire 5672 ??

I'v tried different players : vlc, mplayer and xine... none of them worked for some dvd I could read on other computers...

here are the kind of error I get :

```

*** Zero check failed in ifo_read.c:662
    for pgc->pg_playback_mode = 0x08

*** libdvdread: CHECK_VALUE failed in ifo_read.c:664 ***
*** for pgc->cell_playback_offset == 0 ***

```

Any idea of what I could try ??

Thanks !

---

### Post by echoderek on 2006-04-08
> Originally Posted by tonitonitoni
Hi,

The official ATI driver is for X.Org 6.8 only.
Since my workaround isn't working for you, I hope ATI won't wait too long to release the new driver. Hopefully with the native support for X1xxx.

Or you could try to pin down the rigth reference to 4f 5e with my help
You should be looking for the table of known IDs. The following IDs should be very close to each other:
4a 5e
4b 5e
4c 5e
4d 5e
4f 5e
(those are the IDs of the X700 card).
Just replace any of those IDs with the ID of your graphics card.
Note the reversed byte order: if the ID of your card is 71 45, replace one of the above IDs with 45 71.

That should work for any X1xxx card, but don't expect any advanced features to work.

What's the exact size of your driver?

Toni

It worked! I sure wouldn't have found it without your help. Thanks. This is such a huge improvement. I've put my doctored version of fglrx_drv.so here

hey guys  when i install the fglrx driver from synaptic I didn't find the file fglrx_drv.o in this path "usr/X11R6/lib/modules/drivers/" actually I don't have the dr "modules"
I don't know why..
Then i use the fglrx_drv.so from bwanab and put it in "usr/lib/xorg/modules/drivers"
I can get ino Xwin but the system become very very slow.
By the way my laptop is Acer travelmate 3282 also x1400 but only got 128MB dedicated memory I think this is different from 5672 
So what should I do?    Thanks for helping!:-D

---

### Post by qpad on 2006-04-08
[QUOTE=echoderek]hey guys  when i install the fglrx driver from synaptic I didn't find the file fglrx_drv.o in this path "usr/X11R6/lib/modules/drivers/" actually I don't have the dr "modules"
[/QUOTE]

Just to be sure : the actual place is /usr/X11R6/... and not usr/X11R6/...

Anyway the one that worked for me is at : 

/usr/lib/xorg/modules/drivers/fglrx_drv.so

---

### Post by tonitonitoni on 2006-04-08
[QUOTE=qpad]Hello,

First of all thanks for the x1400 video tips ! It's much better with native resolution !

Now is anyone able to watch dvd with this Aspire 5672 ??

I'v tried different players : vlc, mplayer and xine... none of them worked for some dvd I could read on other computers...

here are the kind of error I get :

```

*** Zero check failed in ifo_read.c:662
    for pgc->pg_playback_mode = 0x08

*** libdvdread: CHECK_VALUE failed in ifo_read.c:664 ***
*** for pgc->cell_playback_offset == 0 ***

```

Any idea of what I could try ??

Thanks ![/QUOTE]

Sorry, I didn't try to watch any DVDs. And I have SuSE Linux installed. What we've done here is just a quick and dirty workaround, I wouldn't expect too much.
I guess you'll just have to sit tight and pray to the ATi god. As we all should...

It wouldn't hurt to send feedback to ATi:
[http://support.ati.com/ics/survey/survey.asp?deptID=894&surveyID=491&type=web]("http://support.ati.com/ics/survey/survey.asp?deptID=894&surveyID=491&type=web")

Cheers,
Toni

---

### Post by tonitonitoni on 2006-04-08
[QUOTE=qpad]Just to be sure : the actual place is /usr/X11R6/... and not usr/X11R6/...

Anyway the one that worked for me is at : 

/usr/lib/xorg/modules/drivers/fglrx_drv.so[/QUOTE]

Thanks, I didn't know Ubuntu uses a different directory. I have SuSE installed...

Cheers,
Toni

---

### Post by gmc on 2006-04-10
Just wanted to say thanks to Toni for introducing the patched fglrx idea to this thread. As such we now have working wireless networking and *real* 1280x800 mode on the 5672, though since it's a hack (or patch, your choice of terms) it does tend to be a bit unstable. I've hard locked my machine while playing with Xscreensaver.

Hopefully ATI will release real support soon.

Thanks
G.

---

### Post by qpad on 2006-04-10
Hello,

Just to ask if anyone tried to get the Orbicam webcam working ?

Ekiga doesn't detect it and camE complains because it didn't find /dev/video ...

Any idea concerning what we can try ?

---

### Post by bwanab on 2006-04-10
[QUOTE=qpad]Hello,

First of all thanks for the x1400 video tips ! It's much better with native resolution !

Now is anyone able to watch dvd with this Aspire 5672 ??

I'v tried different players : vlc, mplayer and xine... none of them worked for some dvd I could read on other computers...

here are the kind of error I get :

```

*** Zero check failed in ifo_read.c:662
    for pgc->pg_playback_mode = 0x08

*** libdvdread: CHECK_VALUE failed in ifo_read.c:664 ***
*** for pgc->cell_playback_offset == 0 ***

```

Any idea of what I could try ??

Thanks ![/QUOTE]

Yes, you can watch dvds with the Aspire 5672. Totem which uses gstreamer for the back end should work. Make sure that you get the gstreamer0.8plugins module through synaptic or apt-get install. I'm not sure if that installs libdvdcss which may or may not be illegal where you live.

---

### Post by qpad on 2006-04-10
[QUOTE=bwanab]Yes, you can watch dvds with the Aspire 5672. Totem which uses gstreamer for the back end should work. Make sure that you get the gstreamer0.8plugins module through synaptic or apt-get install. I'm not sure if that installs libdvdcss which may or may not be illegal where you live.[/QUOTE]

Hey, thanks for your answer.

In fact, after updating a pack of software (most relevant were libstdc++ or gcc, I guess) and a reboot every thing got working...

---

### Post by echoderek on 2006-04-11
Thank you!!  tonitonitoni
You have upgrade you web and put the new patched fglrx_drv.so on it. I used it and success. Just wanna to say thank you:)
By the way, does the vedio card have the 3D firniture? I mean whether I can use xgl with this X1400 driver.

---

### Post by tonitonitoni on 2006-04-11
[QUOTE=gmc]Just wanted to say thanks to Toni for introducing the patched fglrx idea to this thread.[/QUOTE]
[QUOTE=echoderek]Thank you!!  tonitonitoni
You have upgrade you web and put the new patched fglrx_drv.so on it. I used it and success. Just wanna to say thank you:) [/QUOTE]

You're all wellcome :D 
I've put a link to bwanab's fix for xorg 7 along with a detailed instruction of what we've done to fix the problem on [my homepage]("http://toni.to/ati.html"). That instruction should work for all ATI X1xxx video cards.

[QUOTE=gmc]Hopefully ATI will release real support soon.[/QUOTE]

We should keep our fingers crossed, a miracle could still happen... :(
In the meantime, why don't you all give ATI a push?
[http://support.ati.com/ics/survey/survey.asp?deptID=894&surveyID=491&type=web]("http://support.ati.com/ics/survey/survey.asp?deptID=894&surveyID=491&type=web")
Notice that the OS choice of the form doesn't list Linux at all...

[QUOTE=echoderek]By the way, does the vedio card have the 3D firniture? I mean whether I can use xgl with this X1400 driver.[/QUOTE]

I'm using my laptop at work only, so I don't need 3D support. I sincerely don't know if that would work.
But you could try it out and give us feedback on that subject ;) 

Cheers,
Toni

---

### Post by EstevaoSoares on 2006-04-11
[QUOTE=tonitonitoni]I had the same problem with my laptop.
I've modified the official driver (8.23.7) to recognise the X1400 card, but that's just a workaround. At least I can use the native resolution now (1280x800).
Visit [http://toni.to/ati.html]("http://toni.to/ati.html") for details.

Toni[/QUOTE]

Hi toni,

I just would like to thank you (A LOT!) for the Help... 

I just placed the .so file and execute the first aticonfig command a voila, everything works beautiful! 
You're responsable for my hapiness, so... thanks from Brazil ;)

---

### Post by pavlik on 2006-04-12
Today ATI has finally released new version of of Linux drivers ( 8.24.8 ) that supports Mobility Radeon X1800, X1600, X1400, X1300 and others. Hope that XGL and other features works properly now. Let me know cause I'm going to buy  Acer 5672 next month.

---

### Post by bwanab on 2006-04-13
[QUOTE=pavlik]Today ATI has finally released new version of of Linux drivers ( 8.24.8 ) that supports Mobility Radeon X1800, X1600, X1400, X1300 and others. Hope that XGL and other features works properly now. Let me know cause I'm going to buy  Acer 5672 next month.[/QUOTE]

I doubt that this is going to work OOTB for the Acer 5672 running ubuntu. Anybody running ubuntu with the 5672 is running Dapper which is up to xorg7.0. The ATI drivers are for xorg6.8. That said, it seems clear to me that there are clever people at ubuntu who know how to package these drivers to work since they have a package with the old (8.23.7) ATI driver (which was also targetted to xorg6.8), working with 7.0. I suspect we'll have to wait a few more days until they do their magic. I'd love to be proven (or prove myself) wrong on this.

---

### Post by bwanab on 2006-04-13
[QUOTE=tonitonitoni]You're all wellcome :D 
I've put a link to bwanab's fix for xorg 7 along with a detailed instruction of what we've done to fix the problem on [my homepage]("http://toni.to/ati.html"). That instruction should work for all ATI X1xxx video cards.
[/QUOTE]

Toni, one correction to your site. For xorg 7, you need to put fglrx_drv.so into /usr/lib/xorg/modules/drivers.

Thanks again for your help on this.

---

### Post by MrFredo on 2006-04-13
[QUOTE=pavlik]Today ATI has finally released new version of of Linux drivers ( 8.24.8 ) that supports Mobility Radeon X1800, X1600, X1400, X1300 and others. Hope that XGL and other features works properly now. Let me know cause I'm going to buy  Acer 5672 next month.[/QUOTE]
I tried to install the 8.24.8 while forcing the installer to think my xorg is a 6.9 (by doing)
> export X_VERSION=x690
doesn't work out, on my shiny dapper... I think i'll have to wait a little bit more.

edit: by the way ATI's web site claims that 8.24.8 works out with Xorg 7.0

---

### Post by b3b0p on 2006-04-13
I don't see the V5200 Fire GL card listed that is in the Thinkpad T60P. Anyone able to tell me if it will work or not? Is the V5200 based off of one of the other ATI cards?

---

### Post by cville on 2006-04-14
Any news about the orbit cam ?

I saw a logitech model Orbit too maybe its the same driver ?

---

### Post by gmc on 2006-04-19
[QUOTE=cville]Any news about the orbit cam ?

I saw a logitech model Orbit too maybe its the same driver ?[/QUOTE]

Unfortunately, I have a bad feeling about the Orbicam on the 5672. As root "lshw" doesn't even show that the cam exists and there's very little information on it from Google. What we need to do is identify what chip the cam is based on and then look for a workable driver. I did try the Logitech Color Quickcam driver, but no luck there.

---

### Post by adamvt on 2006-04-19
[QUOTE=pavlik]Today ATI has finally released new version of of Linux drivers ( 8.24.8 ) that supports Mobility Radeon X1800, X1600, X1400, X1300 and others. Hope that XGL and other features works properly now. Let me know cause I'm going to buy  Acer 5672 next month.[/QUOTE]

I recently bought an Acer Aspire 5672 with the ATI Mobility X1400.   I thought I might pass the following link on.  I simply followed all the instructions at

[http://wiki.cchtml.com/index.php/Ubuntu_Breezy_Installation_Guide]("http://wiki.cchtml.com/index.php/Ubuntu_Breezy_Installation_Guide")

which explained how to get new 8.24.8 Linux drivers working.  
Everything now looks great in the 1280 x 800 resolution!

---

### Post by MrFredo on 2006-04-19
[http://wiki.cchtml.com/index.php/Ubuntu_Breezy_Installation_Guide](http://wiki.cchtml.com/index.php/Ubuntu_Breezy_Installation_Guide)

works fine, only for the 386 kernel though, the 686 won't  work...
Anyway had anyone succeeded in getting the sound working? or am I just dumb ? (this is a pure rethorical question). Anyhow if the sound works great at yours place, could you let me know? 

Have fun

---

### Post by gmc on 2006-04-20
[QUOTE=MrFredo][http://wiki.cchtml.com/index.php/Ubuntu_Breezy_Installation_Guide](http://wiki.cchtml.com/index.php/Ubuntu_Breezy_Installation_Guide)

works fine, only for the 386 kernel though, the 686 won't  work...
Anyway had anyone succeeded in getting the sound working? or am I just dumb ? (this is a pure rethorical question). Anyhow if the sound works great at yours place, could you let me know? 

Have fun[/QUOTE]

I'm using the 686SMP kernel and got the new ATI driver working quite painlessly using method 2. As for sound, it worked out of the box (with a little static but some recent update has cleared that up now).

Edited: I stand corrected. I just did a complete re-install of Dapper Beta and you are correct, there is no sound. Once I'm finished the install, I'll look into it. **BTW my 5672 is now completely WindowsXP-less (tm) **:-)

---

### Post by itamar on 2006-04-21
[QUOTE=MrFredo][http://wiki.cchtml.com/index.php/Ubuntu_Breezy_Installation_Guide](http://wiki.cchtml.com/index.php/Ubuntu_Breezy_Installation_Guide)

works fine, only for the 386 kernel though, the 686 won't  work...
Anyway had anyone succeeded in getting the sound working? or am I just dumb ? (this is a pure rethorical question). Anyhow if the sound works great at yours place, could you let me know? 

Have fun[/QUOTE]

Shalom all,

using the 5672, I have sound but it is very weak, I wonder if anyone knows how to make the speaker louder?

Also, any one used the mic? I wish to skype using this laptop.

Thanks all, Itamar

---

### Post by jdong on 2006-04-21
Do battery  readouts work?

ACPI: does poweroff at least work? Have you tried suspend/hibernate yet?

(hmm, 3 signs jdong is planning to purchase a core duo... ;) )

EDIT:

The switches for bluetooth and wifi on the front (more importantly wifi), how do they work with Linux? I really don't care if I can't use them to shut off the radio (I can use ifconfig, thank you very much), but I'd be ticked if they prevent the radio from running :)

---

### Post by jamesl on 2006-04-21
Does the camera show up in lsusb? (ive heard that it is indeed a usb device) I too am curious about ACPI.

I am getting one in a couple days (i'm so excited!!)

---

### Post by gmc on 2006-04-21
[QUOTE=jdong]Do battery readouts work?

ACPI: does poweroff at least work? Have you tried suspend/hibernate yet?

(hmm, 3 signs jdong is planning to purchase a core duo... ;) )

EDIT:

The switches for bluetooth and wifi on the front (more importantly wifi), how do they work with Linux? I really don't care if I can't use them to shut off the radio (I can use ifconfig, thank you very much), but I'd be ticked if they prevent the radio from running :)[/QUOTE]

**Battery Monitor**: Yes, though I'm not sure about the reported battery life timer. It reports 2h 15m for a full charge.

**Hibernate/Suspend**: Closing the lid, turns off the backlight but hibernate/suspend thought I've not looked into those yet.

Edited:  :-) AH! I just tested Hibernate and other than a little screen corruption that self-corrects when you move the mouse, it works! -- I'll add the "resume=/dev/hdxx" and test suspend next time I have to reboot, and let you know how it fairs. Edited again: No, suspend does not work and I noticed bad screen corruption during shutdown after having the machine in hibernate mode. I should note that there were no problems with the shutdown though.

**WiFi/Bluetooth Switchs**: Yes, Both enable/disable the appropriate function. I don't have any bluetooth devices, so I can't say if bluetooth actually works.

Gord

---

### Post by gmc on 2006-04-21
[QUOTE=jamesl]Does the camera show up in lsusb? (ive heard that it is indeed a usb device) I too am curious about ACPI.

I am getting one in a couple days (i'm so excited!!)[/QUOTE]

No, the built-in Orbicam doesn't appear with lsusb/lshw/lspci, unfortunately. I spent sometime earlier this week trying to find out what chip this cam uses but have had no luck yet. I'll keep my eyes open and report here if I find any useful information.

Gord

---

### Post by echoderek on 2006-04-22
the new 8.24.8 driver is ok, but got some problems with xgl. I don't know it's casued by our x1400 or the new driver because someone said this newser driver can work with xgl on some old vedio card

---

### Post by jdong on 2006-04-22
Just to say, out-of-the-box support for the X1xxxx and the ipw3945abg have been uploaded to Dapper yesterday. :)

---

### Post by jdong on 2006-04-22
How about the card reader? It seems to be a _PCI_ device rather than traditionally the typical USB mass storage adapter.

Can you post lsusb output just for kicks?

---

### Post by jdong on 2006-04-22
```

[Logitech]

%PID_0892_DD%=PID_0892,USB\VID_046D&PID_0892            ; OrbiCam



[Logitech.NT]

%PID_0892_DD%=PID_0892.XP,USB\VID

1=%DISK_NAME%,,,

_046D&PID_0892		    ; OrbiCam

```

From the Windows drivers for the Orbicam, it seems to be a Logitech USB camera of some sort. Are you **positive** it's not in lsusb??

---

### Post by jdong on 2006-04-22
[http://linux-uvc.berlios.de/#download](http://linux-uvc.berlios.de/#download)

It seems like drivers for these cameras are currently under development. Things look promising :)

---

### Post by gmc on 2006-04-22
[QUOTE=jdong]How about the card reader? It seems to be a _PCI_ device rather than traditionally the typical USB mass storage adapter.

Can you post lsusb output just for kicks?[/QUOTE]

Sure can. I've attached a tar.gz with listing for lspci, lsusb, lshw. Enjoy.

Gord

---

### Post by gmc on 2006-04-22
[QUOTE=jdong][http://linux-uvc.berlios.de/#download](http://linux-uvc.berlios.de/#download)

It seems like drivers for these cameras are currently under development. Things look promising :)[/QUOTE]

Maybe I was wrong! I assumed the double Logitech entry was being caused by my Logitech Marble Mouse (that was a symtom with the mouse on my old Toshiba 4600Pro). However after looking at the above site, I realised that the '0892' entry is actually the Orbitcam ](*,) . Unfortunately that device ID is not listed on the above page... but at least it's a step in the right direction.

```

[SIZE="5"]_**lsusb**_[/SIZE]

Bus 005 Device 003: ID 04b4:6830 Cypress Semiconductor Corp. USB-2.0 IDE Adapter
Bus 005 Device 004: ID 046d:0892 Logitech, Inc.
Bus 005 Device 001: ID 0000:0000
Bus 003 Device 001: ID 0000:0000
Bus 004 Device 001: ID 0000:0000
Bus 001 Device 001: ID 0000:0000
Bus 002 Device 003: ID 046d:c408 Logitech, Inc. Marble Mouse (4-button)
Bus 002 Device 001: ID 0000:0000

```

Gord

Edited: I've posted the above information on the developers list in the hopes that support can be added to the driver for the Orbitcam.

---

### Post by marianoi on 2006-04-24
Hello guys,

I installed the latest fglrx driver and the Kernel yesterday night (I am a Dapper guy). My ACER Aspire 5672 is working nicely running the new ATI driver.

However...I followed the instructions for setting up compiz and xgl and when rebooting X won't start. NO error message, nothing. It was just trying to load GDM for more than 10 min when I decided to re-configure to the original state. Did anyone have the same problem?

Wireless is not working with this kernel either. I tried ndiswrapper but did not work. Does anyone know if the WiFi will work with Dapper before the final release?

THANKS ! 

Mariano

---

### Post by gmc on 2006-04-24
[QUOTE=marianoi]Hello guys,

I installed the latest fglrx driver and the Kernel yesterday night (I am a Dapper guy). My ACER Aspire 5672 is working nicely running the new ATI driver.

However...I followed the instructions for setting up compiz and xgl and when rebooting X won't start. NO error message, nothing. It was just trying to load GDM for more than 10 min when I decided to re-configure to the original state. Did anyone have the same problem?

Wireless is not working with this kernel either. I tried ndiswrapper but did not work. Does anyone know if the WiFi will work with Dapper before the final release?

THANKS ! 
Mariano[/QUOTE]

Yes, there is a driver for the ipw3945. Check [this thread]("http://www.ubuntuforums.org/showthread.php?t=140085&highlight=3945"), for instructions on how to get it working (without ndiswrapper).  If you are using NetworkManager to manage your network connections, you should configure everything for WEP, as WPA/WPA2 do not appear to work (yet).

As for XGL, I get the same results, though the instructions on how to get XGL working do state 
that they do not work with the mobile version of the ATI X1400. Hold off in playing with XGL for a bit.

Gord

---

### Post by marianoi on 2006-04-24
Thanks Gord,

I knew Mobility X1400 was no supported...I was hopping that the new driver would do the trick...

Thanks for the help.

Cheers

Mariano

---

### Post by cwood06 on 2006-04-24
Hello, Im new to linux and i was wondering if you fine people could help me out i got this laptop that you guisy are talking about and i cant Suse or Gentoo to install on my laptop it doesnt see my windows partition at all and changes it to a  EFI GPT partition and i cant boot into windows ; ;. Im New to linux and i was wondering if i am doing something wrong to dual boto between windows and some distro of linux. Ill install a 20 gig unallocated disc on the begiing of my windows partition using aprtition magic then il ltry to install a distro and it get that. it also says i dont have access to my disc. So what am i doingwrong here please hlpe me out many thanks

---

### Post by gmc on 2006-04-25
Hi cwood,

[QUOTE=cwood06]Hello, Im new to linux and i was wondering if you fine people could help me out i got this laptop that you guisy are talking about and i cant Suse or Gentoo to install on my laptop it doesnt see my windows partition at all and changes it to a  EFI GPT partition and i cant boot into windows ; ;. Im New to linux and i was wondering if i am doing something wrong to dual boto between windows and some distro of linux. Ill install a 20 gig unallocated disc on the begiing of my windows partition using aprtition magic then il ltry to install a distro and it get that. it also says i dont have access to my disc. So what am i doingwrong here please hlpe me out many thanks[/QUOTE]

What type of partition is you Windows on? FAT32 or NTFS? I'm a little concerned that either Suse/Gentoo (and I assume Ubuntu) are seeing your Windows partition as a "EFI GPT" formatted partition.

Gord

---

### Post by cwood06 on 2006-04-25
[QUOTE=gmc]Hi cwood,



What type of partition is you Windows on? FAT32 or NTFS? I'm a little concerned that either Suse/Gentoo (and I assume Ubuntu) are seeing your Windows partition as a "EFI GPT" formatted partition.

Gord[/QUOTE]


yea thats what its doing when i did suse it wouldng change it tell i got to the partitioning sections and the same for gentoo and maybe ubuntu im gunan dl it today while i mat school and try it when i get back. My Windows is on a Fat32 patition a bit 111 patition

So how do i make it so it doesnt change it to a efi gpt?

---

### Post by jdong on 2006-04-25
whoa... EFI GPT... that sounds like something out of MacBook land... are you sure we're speaking of the same laptop? Does Ubuntu also call it EFI GPT?

---

### Post by cwood06 on 2006-04-25
I dont remebr i tryed to install Ubuntu and i sitll think it wanted to earase my whole harddisc. But when i went to the manual way it siad ther are files on thsi parition and formating will delte all these files. So im guessing it saw it was a Fat32 partition

---

### Post by jamesl on 2006-04-25
Every time I run the espresso installer in dapper beta it stops after keyboard layout... and "espresso noui" from the command line doesnt seem to do anything, either.

EDIT: after several attempts, it just worked...

---

### Post by YourDoom123 on 2006-04-26
dapper just plain refuses to install for me... every time it gets to grub, it gives me an error saying unable to install grub (hd0). i've done everything i can think of, including manually fdisking the drive to create bootable flags, and installing grub manually (i can't, because grub refuses to recognize my drives, which is odd, because grub installed just fine on here from the gentoo livecd... i'm gonna reinstall gentoo, and think about ubuntu later...

---

### Post by jamesl on 2006-04-28
I got it to install, (it just worked eventually, not sure why) but it failed to install the boot loader. I managed to install grub manually though.

---

### Post by cjbchachacha on 2006-04-28
[QUOTE=gmc]Unfortunately, I have a bad feeling about the Orbicam on the 5672. As root "lshw" doesn't even show that the cam exists and there's very little information on it from Google. What we need to do is identify what chip the cam is based on and then look for a workable driver. I did try the Logitech Color Quickcam driver, but no luck there.[/QUOTE]
Try this link...its to the Australian Support site...worked FANTASTIC for me...my orbicam NOW works perfectly as it is supposed to:
[http://support.acer.com.au/support_acer.nsf/approvedbyheading/55D398B9AC2672F2CA25710800223EA0?OpenDocument](http://support.acer.com.au/support_acer.nsf/approvedbyheading/55D398B9AC2672F2CA25710800223EA0?OpenDocument)

Once your orbicam is working, you MUST take advantage of the really cool VisageON effects (Avatars and Face Accessories) which can be found here:
[http://www.logitech.com/index.cfm/products/videoeffects/videoeffectlisting/US/EN,CRID=2365,camera=10561,effecttype=10346,company=0](http://www.logitech.com/index.cfm/products/videoeffects/videoeffectlisting/US/EN,CRID=2365,camera=10561,effecttype=10346,company=0)
:D

---

### Post by gmc on 2006-04-29
[QUOTE=cjbchachacha]Try this link...its to the Australian Support site...worked FANTASTIC for me...my orbicam NOW works perfectly as it is supposed to:
[http://support.acer.com.au/support_acer.nsf/approvedbyheading/55D398B9AC2672F2CA25710800223EA0?OpenDocument](http://support.acer.com.au/support_acer.nsf/approvedbyheading/55D398B9AC2672F2CA25710800223EA0?OpenDocument)

Once your orbicam is working, you MUST take advantage of the really cool VisageON effects (Avatars and Face Accessories) which can be found here:
[http://www.logitech.com/index.cfm/products/videoeffects/videoeffectlisting/US/EN,CRID=2365,camera=10561,effecttype=10346,company=0](http://www.logitech.com/index.cfm/products/videoeffects/videoeffectlisting/US/EN,CRID=2365,camera=10561,effecttype=10346,company=0)
:D[/QUOTE]

These are great links for Windows, but we were talking about getting the Orbitcam working under Linux. Thanks for the information though.

Gord

---

### Post by jamesl on 2006-04-29
i downloaded the source for the uvcvideo driver, compiled it and loaded it. it loads fine but does not work. I even modified it (so that it would recognize the camera by its usb id) but same thing.

---

### Post by mbeach on 2006-05-01
Wow - guys thank you a bunch - am in the market for a new laptop - stumbled on the 5672WLMi at CDW and thought - sounds good - checked here and you fellas have done so much work.  I feel your pain in some of this - had some similar troubles with new hardware a long time ago with a Vaio - I've learned my lesson about doing my research first and stopping the impulse buy with the thought, "Hey I'm sure I can get it to work."  Seriously, this is one of the reasons I love the Ubuntu forums - just friendly with quotes like, "those are for XP, thanks though".  

Part of my draw to the unit was the cam - might hold on purchase or find another with built in cam - any suggestions in this $ range?  I've also read that the keyboard on this particular model is 'mushy' - any thoughts?

---

### Post by jdong on 2006-05-02
I've just received mine, and spent the past two days setting up Kubuntu/Ubuntu on it. Currently, I have almost everything working. Unless I mention otherwise, it probably works flawlessly.

Overview:
The laptop is extremely usable, and installed fairly well out-of-the-box. Needed some tweaking afterwards, but nothing huge. Some hardware still doesn't work.


Notable Points:

* **SMP Kernel**: Just a reminder, to utilize the 2nd core, you must install a SMP capable kernel, such as linux-686
* **High-pitch noises during idle**: If you allow your system to become very idle on battery power, you may get high-pitched noises coming from underneath the touchpad area (CPU)! It is very distracting. The underlying cause is that somehow when the Core Duo enters C3 (low power CPU sleep) in both cores, somehow it generates a human-audible frequency. This is not a Linux or an Acer problem, but has been reported on Core Duos everywhere, from Macbooks to Dell Inspirons. It happens most under Linux and OSX, where under Windows a USB2 bug keeps CPU's from entering sleep modes. To resolve the issue (work around), you must lock your CPU out of C3. Create a /etc/rcS.d/S02acpi.sh file, with the following contents:

```

echo 2 > /sys/module/processor/parameters/max_cstate

```

Then, reboot. Some say that recompiling a kernel with CONFIG_HZ helps, but I'm too lazy to play with it.

* **Webcam**: No Linux support yet. It's a Vivicro vc0321 chipset, which should be USB Video Class compliant but not, and should be hackable to work with both the pwc and spca5xx drivers, but I've yet to have any success. It's a very new Logitech device, so I would just give it some time for now :). The specs seem to be quite open, so I'm sure it'll get some attention in the future :)

* **Cardreader**: Unable to get it working yet. TI chipset, connected to PCI Express. Gentoo users report that applying a hackjob kernel patch will get it working to some degree (only Memory Stick?), but I've yet have time to try.

* **Frequency Scaling**: powernowd has a known issue with SMP processors, where the 2nd CPU will not scale at all. Use powersaved+kpowersave (requires configuration) or your other favorite CPU frequency controller instead. The kernel has built-in ones, too (performance, ondemand, etc) which is what powersaved uses.

* **ATI:** Working, 3D acceleration, basically out of the box. Needed fglrx drivers installed via apt-get, just like any other ATI, otherwise 1280x800 is not a supported mode. The new ATI driver is a bit unstable when switching between VT's, especially when not done with a keyboard (i.e. shutdown zapping X server, chvt commands, etc); ATI acknowledges the issue in the release notes, so hopefully a future update will fix it. A hint about battery life: aticonfig --lsp, aticonfig --set-powerstate # --effective=now, these commands can be used to throttle the video card. VERY benefitial to battery life (+30 minutes, maybe even more)

* **Wireless**: Works out of the box with latest kernel, no configuration. Make sure you use a daily CD build to install; beta2 CD's have unresolved symbols.

---

### Post by gmc on 2006-05-03
Hi jdong,

    Welcome to the club :-) Some good/useful information there. Great catch on the Webcam. Where'd you find that out? Google didn't provide any useful information when I last checked.

Gord

---

### Post by jdong on 2006-05-03
[QUOTE=gmc]Hi jdong,

    Welcome to the club :-) Some good/useful information there. Great catch on the Webcam. Where'd you find that out? Google didn't provide any useful information when I last checked.

Gord[/QUOTE]

Thanks for the warm welcome. This laptop is great, and I'm very happy with my purchase decision. At $1100, I don't think there's a better laptop suitable towards my work than this.

As far as the camera, I started by looking at the Windows driver for it, which uses "lv321.sys". A quick search at similar logitech devices showed that they used lv301. Most of those are supported by the spca5xx driver, so I headed over to their mailing lists and snooped for lv321 info. There was one thread on someone trying to hack a driver for that chipset, and that it supports UVC and is similar to the 301. With that info, I went to vivicro's site, and requested spec sheets for the camera.

This summer, if there is no progress on it yet, I will definitely play around with the drivers and see if I can write something up for it.

---

### Post by gmc on 2006-05-04
[QUOTE=jdong]Thanks for the warm welcome. This laptop is great, and I'm very happy with my purchase decision. At $1100, I don't think there's a better laptop suitable towards my work than this.
[/QUOTE]

OUCH! that smarts. I payed double that back in January. Oh well, live and learn.

> 
As far as the camera, I started by looking at the Windows driver for it, which uses "lv321.sys". A quick search at similar logitech devices showed that they used lv301. Most of those are supported by the spca5xx driver, so I headed over to their mailing lists and snooped for lv321 info. There was one thread on someone trying to hack a driver for that chipset, and that it supports UVC and is similar to the 301. With that info, I went to vivicro's site, and requested spec sheets for the camera.

This summer, if there is no progress on it yet, I will definitely play around with the drivers and see if I can write something up for it.

DOH! Now why didn't I think of that when I had Windows installed here. I'll have to keep an eye over there for further developements. If it should become a project of your's please be sure to let me know and I'll be happy to help with testing.

Thanks
Gord

---

### Post by gmc on 2006-05-04
Hi Folks,

Has anyone noticed a clock problem? Recently I began toting my 5672 to work and home. During this time the machine is powered down. When I arrive at my destination and power it up, I find the time has advanced forward by an hour (noting that my travel time is about 30 minutes).

I only noticed this problem in the last day or two, so I'm not sure if the last kernel upgrade introduced it or if some other update has.

Currently I'm using the standard 2.6.15-21-686 Ubuntu kernel. I'm going to test the "no_timer_check" kernel option and see if that helps/solves the problem.

Gord

---

### Post by MrFredo on 2006-05-04
Just to let you know gmc, the same clock problem happened to me a week ago, I havn't gone inside it deeply because I'm deep inside broken packages (I think it comes from my installing fglrx out of the distro, why didn't I wait!!!).

---

### Post by gmc on 2006-05-04
Hi Folks,

[Computer Temprature Monitor]("http://computertemp.berlios.de/index.php")

If you use Gnome as your desktop, this is definately an applet that you'll want to install. Boy has it come a long way since I last played with it.

Gord

---

### Post by jdong on 2006-05-04
[QUOTE=MrFredo]Just to let you know gmc, the same clock problem happened to me a week ago, I havn't gone inside it deeply because I'm deep inside broken packages (I think it comes from my installing fglrx out of the distro, why didn't I wait!!!).[/QUOTE]

I've seen it happen once in a while (huge drifts) when I am playing with getting S3/S4 sleep to work, but none other time.

---

### Post by jamesl on 2006-05-06
I have the same issue with time, its really annoying.

---

### Post by jdong on 2006-05-06
Yeah, I'm getting time jumps between reboots... investigating that right now...

---

### Post by Circleback on 2006-05-07
Hi have any of you guys on the Acer 5672 gotten the hotkey and FN keys to work? I have a different Acer model (5502) but its pretty new and has a similar hotkey setup. Here is what works and doesnt work in Kubuntu Dapper:

Works:
Fn+ Volume up, Volume down, Mute
Fn+ Screen brightness
Fn+ Black screen
Fn+ touchpad off/on
Wifi and Bluetooth led buttons
Fn + number lock

Doesn't work:
Fn+F5 switch out to crt (for external monitor or projector)
Fn+F2, F1,F2,F3,F4
Fn+Multimedia controls
4-way navigation on touchpad
Mail, Web, e-manager, and P hotkeys.

Any help would be appreciated.

---

### Post by nolongerlivecd on 2006-05-07
Hey, I'm using 5504, and I can certify that acerhk does not work either.

---

### Post by scifan on 2006-05-07
Question

Now that I've taken the time to read through this entire  thread, I wonder if one or more of you who have had varying degre's of success would create a wiki for this book?

GMC - what version of dapper are you running right now? (I downloaded Flight 7 today...)

I'm expecting my 5672 to be delivered tomorrow... 

and for what it's worth, I paid $1k for it @ buy.com

This should be a VERY decent notebook for the cost.

and Thanks for your extensive efforts.

---

### Post by jamesl on 2006-05-07
I have Xgl and compiz running like wonderfully though ;-)

---

### Post by jdong on 2006-05-07
As far as clock skew, I've made the following change and since then, I've yet to see any skew:

/etc/init.d/hwclock.sh:
```

# Set this to any options you might need to give to hwclock, such
# as machine hardware clock type for Alphas.
- HWCLOCKPARS=
+ HWCLOCKPARS="--directisa"

```

---

### Post by bwanab on 2006-05-08
Here's a question. I spend a lot of time these days on the train with my 5672 plugged into the wall socket. Every 10 minutes or so, the train loses power and most of the time it's a non-event for me since battery kicks in and I see a report that this has happened. Occasionally, once an hour or so, when power goes off, the report states that battery is critically low with only 4 minutes left. This occurs when I know that the battery has a full or almost full charge. Since I know that the battery has plenty of juice, I've just ignored it as a bad message, but yesterday it really bit me because after a minute or so, it saved state and shut down. I ended up losing several minutes of work. Is this a bug in ubuntu or is the computer reporting bad information?

---

### Post by gmc on 2006-05-08
Hi scifan,

[QUOTE=scifan]Question

Now that I've taken the time to read through this entire  thread, I wonder if one or more of you who have had varying degre's of success would create a wiki for this book?

GMC - what version of dapper are you running right now? (I downloaded Flight 7 today...)

I'm expecting my 5672 to be delivered tomorrow... 
and for what it's worth, I paid $1k for it @ buy.com

This should be a VERY decent notebook for the cost.
and Thanks for your extensive efforts.[/QUOTE]

I'm using Dapper Beta CD, with daily updates, so the pretty much equals Flight 7.
With all the headway we've made in this thread and the 3945 thread, I think your really going to enjoy your new Toy.

Just for the record, I formatted the WinXP partition and now am completely Windows free here. Ubuntu is doing very nicely...

Gord

---

### Post by jdong on 2006-05-08
[QUOTE=bwanab]Here's a question. I spend a lot of time these days on the train with my 5672 plugged into the wall socket. Every 10 minutes or so, the train loses power and most of the time it's a non-event for me since battery kicks in and I see a report that this has happened. Occasionally, once an hour or so, when power goes off, the report states that battery is critically low with only 4 minutes left. This occurs when I know that the battery has a full or almost full charge. Since I know that the battery has plenty of juice, I've just ignored it as a bad message, but yesterday it really bit me because after a minute or so, it saved state and shut down. I ended up losing several minutes of work. Is this a bug in ubuntu or is the computer reporting bad information?[/QUOTE]

I have seen this happen once on my system. I think it's just a hardware fluke, but it's never lasted long enough for me to pull up a terminal and look at /proc/acpi's information about battery charge state. It is unfortunate that it reports 4%, a critical value, that could trigger a shutdown.

---

### Post by jdong on 2006-05-08
[QUOTE=scifan]Question

Now that I've taken the time to read through this entire  thread, I wonder if one or more of you who have had varying degre's of success would create a wiki for this book?
[/quote]
Sure, Let's organize a few of us to create a wiki page for this laptop. I'd be more than happy to contribute to it. 

> 
GMC - what version of dapper are you running right now? (I downloaded Flight 7 today...)

We are typically running the latest Dapper release, though I believe a few are still on Breezy. It's certainly going to be easier to set up on Dapper than on Breezy, due to the great work of the Ubuntu Laptop / Kernel folks.

This thread should already contain most of the info to get everything working, and it's extremely smooth, especially taken into account how new this laptop is!

As far as outstanding issues you may still encounter (somewhat updated from the previous time I posted this list):

(1) ipw3945 unresolved symbols: Depending on if the latest kernel uploaded some time last night hit Flight 7, ipw3945 may complain about missing symbols out of the box. However, wired networking works perfectly, so you may have to dist-upgrade once.

(2) fglrx: Fglrx takes the typical configure (apt-get install, edit xorg.conf) to work. There are still some quirks with this release of fglrx, especially dealing with console switching (sometimes causes a hang, though rare) and TV-OUT (I'm not sure if it works yet), but these should be resolved in future ATI driver updates (which you probably will have to manually install).

(3) ACPI Lid: Some of you may want to help me confirm this, but when the lid is closed while power is on, ACPI will repeatedly generate LID events (when it should only generate 2: open and close). This will lead to high (50%) CPU usage as the lid script is rapidly respawned. A quick workaround is to disable the lid script by adding an "exit 0" to the top of /etc/acpi/lid.sh. A bug report with the kernel has been filed ([http://bugzilla.kernel.org/show_bug.cgi?id=5853)](http://bugzilla.kernel.org/show_bug.cgi?id=5853)), so hopefully we see some resolution).

(4) Camera: No drivers have been discovered for the built-in webcam/camera yet. It's an extremely new logitech USB, and we've identified the chipset and requested spec sheets from the manufacturer, so we'll probably see some progress into that.

(5) Card Reader: No drivers have been discovered for the card reader yet. There are talks of patches or sdhci (2.6.17) support here and there, but nothing concrete or out-of-the-box...

(6) Suspend-to-{RAM,DISK}: Pretty spotty. I have been able to successfully do it on my system, with just tweaking acpi-support's little hacks here and there, but whether or not a particular suspend resumes properly is a lottery, so I'm personally not messing with it. With a fairly low current draw while idle and excellent Dapper boot-up times, I'm not really missing out on much.

(7) Intermittent high-pitched noises: This laptop does experience the infamous Core Duo whining noise issue that has been getting some press coverage in the Apple MacBook community. Basically, when both cores enter the C3 (deep sleep idle) states, the laptop will emit a whining noise. Since this is a pretty random event that both cores enter, you'll get this noise intermittently. The fix is to lock the CPU out of C3 sleep, which I've provided some hints at in previous posts. Another "fix" is to bump CONFIG_HZ from 1000 to 100. On my laptop, it reduces it to a low buzzing noise, much more tolerable. I've launchpadded a request for this to be one of the default kernel configs ([https://launchpad.net/distros/ubuntu/+source/linux-source-2.6.15/+bug/43281)](https://launchpad.net/distros/ubuntu/+source/linux-source-2.6.15/+bug/43281)), so we'll see how that goes. Consequences of disabling C3 sleep are reduced battery life during pure idling, but I cannot really confirm that. The most I've seen is a 10 minute life difference, which may just be natural variation from my usage patterns... The core duo already has such a low power draw, even under load, that C3 savings are vastly outshadowed by HD or screen or video card consumption!

(8) Powernowd does not scale 2nd processor core: Powernowd 0.97 has been uploaded into Dapper today, which should fix the problem for good, no workarounds required. Don't you love how fast/recently these problems are being fixed?

Other than these, the laptop should work great with Linux.  As I've said before, considering that this is bleeding edge new hardware, it's quite impressive how well this thing works out of the box. The list of issues is really quite a small one, not to mention most are also pretty minor :)

> 
I'm expecting my 5672 to be delivered tomorrow... 

and for what it's worth, I paid $1k for it @ buy.com

This should be a VERY decent notebook for the cost.

and Thanks for your extensive efforts.
This is one spectacular notebook for its price (I paid $1100 at NewEgg), and everything it's hyped up to be. Spectacular performance (outshadows my Athlon64 3000+ even in single-threaded programs; each core packs a great punch), cool and quiet, nothing short of amazing. I'm very happy with my purchase and I'm sure you will be too :)

P.S. The wifi antenna is amazing. My friend has a Dell Core Duo, and this thing picks up networks at a much greater range, not to mention with spectacular stability even compared to other ipw3945's. I have very weak wi-fi in my room (too far from my cheap AP), so weak that my Atheros (one of the top chipsets) drops in and out on bad days, but this laptop maintains a constant 2MB/s throughput regardless of where I am in the room when the Atheros needs to have its antenna precisely positioned for 200KB/s.

---

### Post by scifan on 2006-05-08
Thanks!!!

I'm psyched - though my wife wasn't home to actually get my book from Fedex... ( ](*,) Signature required) so I'm stuck waiting until tomorrow to start playing with this little badboy.

Glad to hear that you're books are reasonably cool... I'd read elsewhere that there were some  heat isue's... the system I looked at at compusa seemed reasonble temp wise, but it's always reassuring to hear that others think so as well... it's sounding like alot of the stuff talked about in this column and others that directly relate are being incorporated into the default dapper cofiguration - which is great!

hopefully I will be testing  my system tomorrow  a this time.

I've read some on the  whine/heat issue's on the mac book pro's... 
sounds like they have some issue's with improper thermal  grease installation.

at least  one guy's reporting a 15c reduction in temperature after taking his book apart and redoing the thermal grease implementation...

---

### Post by jdong on 2006-05-08
[QUOTE=scifan]Thanks!!!

I'm psyched - though my wife wasn't home to actually get my book from Fedex... ( ](*,) Signature required) so I'm stuck waiting until tomorrow to start playing with this little badboy.

Glad to hear that you're books are reasonably cool... I'd read elsewhere that there were some  heat isue's... the system I looked at at compusa seemed reasonble temp wise, but it's always reassuring to hear that others think so as well... it's sounding like alot of the stuff talked about in this column and others that directly relate are being incorporated into the default dapper cofiguration - which is great!
[/quote]
90% of the issues brought up here have been fixed in default Dapper by now :). It's actually comical how many "it's uploaded to Dapper two hours ago" posts I've made by now :)

As far as heat, it's not terrible at all. I've been keeping both cores at quite a load recently (poor laptop, feel wrath of jdong's workload) and I'm really impressed at how cool it remains. The most heat is generated on the top side near the touchpad area, where you rest your palms while typing. The area does get noticeably warm, but never uncomfortably so (even under load). I actually appreciate the heat a bit, as my hands tend to get pretty cold after a while of computer use.

As far as underside heat, you'll be happy to know that this laptop remains comfortable to place on your lap... Something my Celeron and P3-m couldn't do!

As far as the noise (whine) issue, it's not caused by thermal paste or anything of that nature. It's when power usage falls within a certain range (i.e. C3 sleep), a different set of transistors/capacitors on the PSU will be servicing the CPU than before. This particular set will resonate when being charged/discharged. Since when idle the only thing that goes on is timer interrupts (which happen at 1000Hz by default), it creates a human-audible whine as the capacitors charge/discharge. The fixes are either to bump power consumption so that a quieter capacitor services the CPU load (i.e. C2 instead of C3) or to lower the timer frequency to take it out of human range (i.e. CONFIG_HZ to 100)
hopefully I will be testing  my system tomorrow  a this time.

I've read some on the  whine/heat issue's on the mac book pro's... 
sounds like they have some issue's with improper thermal  grease installation.

at least  one guy's reporting a 15c reduction in temperature after taking his book apart and redoing the thermal grease implementation...[/QUOTE]

---

### Post by jdong on 2006-05-08
[QUOTE=scifan]Thanks!!!

I'm psyched - though my wife wasn't home to actually get my book from Fedex... ( ](*,) Signature required) so I'm stuck waiting until tomorrow to start playing with this little badboy.

Glad to hear that you're books are reasonably cool... I'd read elsewhere that there were some  heat isue's... the system I looked at at compusa seemed reasonble temp wise, but it's always reassuring to hear that others think so as well... it's sounding like alot of the stuff talked about in this column and others that directly relate are being incorporated into the default dapper cofiguration - which is great!
[/quote]
90% of the issues brought up here have been fixed in default Dapper by now :). It's actually comical how many "it's uploaded to Dapper two hours ago" posts I've made by now :)

As far as heat, it's not terrible at all. I've been keeping both cores at quite a load recently (poor laptop, feel wrath of jdong's workload) and I'm really impressed at how cool it remains. The most heat is generated on the top side near the touchpad area, where you rest your palms while typing. The area does get noticeably warm, but never uncomfortably so (even under load). I actually appreciate the heat a bit, as my hands tend to get pretty cold after a while of computer use.

As far as underside heat, you'll be happy to know that this laptop remains comfortable to place on your lap... Something my Celeron and P3-m couldn't do!

As far as the noise (whine) issue, it's not caused by thermal paste or anything of that nature. It's when power usage falls within a certain range (i.e. C3 sleep), a different set of transistors/capacitors on the PSU will be servicing the CPU than before. This particular set will resonate when being charged/discharged. Since when idle the only thing that goes on is timer interrupts (which happen at 1000Hz by default), it creates a human-audible whine as the capacitors charge/discharge. The fixes are either to bump power consumption so that a quieter capacitor services the CPU load (i.e. C2 instead of C3) or to lower the timer frequency to take it out of human range (i.e. CONFIG_HZ to 100)
hopefully I will be testing  my system tomorrow  a this time.

---

### Post by gmc on 2006-05-09
Hi jdong,

[QUOTE=jdong]
(6) Suspend-to-{RAM,DISK}: Pretty spotty. I have been able to successfully do it on my system, with just tweaking acpi-support's little hacks here and there, but whether or not a particular suspend resumes properly is a lottery, so I'm personally not messing with it. With a fairly low current draw while idle and excellent Dapper boot-up times, I'm not really missing out on much.

(8) Powernowd does not scale 2nd processor core: Powernowd 0.97 has been uploaded into Dapper today, which should fix the problem for good, no workarounds required. Don't you love how fast/recently these problems are being fixed?
[/QUOTE]

I found a blog by [DiCianno]("http://www.dicianno.org/acer-aspire-5670-v-gentoo/") that reports success with suspend2 kernel patch. Unfortunately I had a bad experiance with Suspend2 on a Toshiba Satellite Pro4600 and I'm in no hurry to repeate that.

Actually there's a lot of good information there though it's somewhat Gentoo specific.

As for the powernowd, I'm running two copies of Gnome CPU Freq applet (one set for each processor) and I see both processors clocking up and down when set to "ondemand" and that's been working here for weeks now. I just wish the applet would handle both processors, rather than having to run two copies.

Gord

---

### Post by angel12 on 2006-05-09
When I tried flight 6 a few weeks ago, i remember that the volume keys didnt change the right volume, they changed PCM, and not the FRONT channel. Is this fixed yet? and awesome news about the camera, i had thought about trying to hack into the acer drivers for linux (if there are any, never really looked into it). Thanks guys!

---

### Post by jamesl on 2006-05-09
I am using suspend2 successfully. There are issues with ati's binary drivers though, and it doesn't work when I have a lot of applications running (which is pretty much most of the time).

EDIT: actually, i just did suspend to ram (with acpi) and it worked fine!
as root:```
echo mem > /sys/power/state
```

---

### Post by jdong on 2006-05-09
Unfortunately, the audio front/pcm issue is not fixed yet; KDE allows you to choose a primary channel (which you can set as FRONT), but perhaps alsa has one also that needs to be set properly.

As far as suspend, S3/S4 both work here ,but regardless upon resume all virtual consoles are corrupted (X comes back fine). Once in a while, I'll get a case where the screen stays black and it does not resume, but that's very rare.

---

### Post by scifan on 2006-05-09
Well, I'm in "testing" mode... trying to figure out what to try next since my touchpad seems to not work at all... :(  ](*,) 

This is kind of frustrating...

and you were talking about how your book is pretty temperate, etc... but mine's fairly hot... I wonder if Acer has an issue with inconsistant thermal grease installation as has been reported on the apple power book pro's?!

---

### Post by jdong on 2006-05-09
[QUOTE=scifan]Well, I'm in "testing" mode... trying to figure out what to try next since my touchpad seems to not work at all... :(  ](*,) 
[/quote]
Dumb suggestion: Is the touchpad on? There's an fn key that toggles touchpad power, did you press that by accident?

> 
and you were talking about how your book is pretty temperate, etc... but mine's fairly hot... I wonder if Acer has an issue with inconsistant thermal grease installation as has been reported on the apple power book pro's?!
Interesting... where does it get hot?

---

### Post by scifan on 2006-05-09
good guess, but I hadn't turned it off... and I tried toggling it... I'm thinking that there's something fubar there... :(

it gets pretty hot under the touch pad... and to the right of the touch pad... touch pad gets hotter than most notebooks I've worked with... even after I turned the cpu power down to medium to see if that would help... 

not sure... seems like a nice enough notebook... but this sucks :(

I'll figure out something... maybe step up the warranty to on-site... actually, might do the 2 yr for $121... what ever the case, I want to resolve this before putzing with linux on it...

---

### Post by jdong on 2006-05-10
The heat on mine is also concentrated in the touchpad and right of it, but it's very tolerable and never uncomfortably hot, even for extended use under load...

The touchpad in your case may be defective; probably best to send it back than to open it up yourself...

---

### Post by scifan on 2006-05-10
It's headed out tomorrow...

and it runs alot cooler if I have it on a  desk rather than on my lap...

---

### Post by angel12 on 2006-05-10
yeah, one thing i have found is that its more of a notebook than a laptop, meant to be on a flat surface where air can get to it. Does anyone else have problems with the camera in windows? it seems that when i turn the camera around, i hear the chime that windows has found a new device. But when i try to use the camera in any application, it says that the camera is busy... maybe i should send it in...

---

### Post by marianoi on 2006-05-10
Hello everyone,

I got this excellent PC about 3 weeks ago. It has an amazing performance under both Win and Dapper. Dapper outperforms windows by quite a bit...for me at least.

My questions for you:

1) I read someone had Xgl/ compiz working with this ATI card. However, I could not get it done. ...X-server crashes. So, if you have it running what threat did you follow? any suggestions? ](*,) 

2) I have my touch pad working nicelly but I cannot scroll with it, does anyone have this issue? How could it be solved?

Thank you very much!

Cheers

Mariano

---

### Post by jdong on 2006-05-10
[QUOTE=marianoi]
2) I have my touch pad working nicelly but I cannot scroll with it, does anyone have this issue? How could it be solved?[/QUOTE]

The default scroll margins are really tight... I've widened them on my system. This is my touchpad configuration in my xorg.conf:

```


Section "InputDevice"
	Identifier  "Synaptics Touchpad"
	Driver      "synaptics"
	Option	    "SendCoreEvents" "true"
	Option	    "Device" "/dev/psaux"
	Option	    "Protocol" "auto-dev"
	Option	    "LeftEdge" "1700"
	Option	    "RightEdge" "4800"
	Option	    "TopEdge" "1700"
	Option	    "BottomEdge" "4200"
	Option	    "FingerLow" "25"
	Option	    "FingerHigh" "30"
	Option	    "MaxTapTime" "180"
	Option	    "MaxTapMove" "220"
	Option	    "VertScrollDelta" "100"
	Option	    "MinSpeed" "0.09"
	Option	    "MaxSpeed" "0.18"
	Option	    "AccelFactor" "0.0015"
EndSection

```

RightEdge is the most significant; it determines at what "touchpad pixel" count it starts considering it the right edge. Default is like 5800, but for me 4800 works great.

---

### Post by gmc on 2006-05-11
Hi Folks,

[SIZE="5"]**XGL/Compiz WORKS**[/SIZE]

Just thought I'd let everyone know that I have had success with getting XGL/Compiz working on our favorite little laptop. I've been using the 2nd HOWTO listed **[here]("http://www.compiz.net/viewtopic.php?id=389").**

One gotcha is libGL.so.1.2 is located in /usr/share/fglrx/diversions on my system (keeping in mind that I manually installed the ATI fgrlx driver).

Attached below are the various scripts and configuration files needed to get it working.

Enjoy
Gord

---

### Post by jdong on 2006-05-11
Attached is my /etc/acpi directory; I've made the following tweaks to it:

(1) ACPI sleep kind of works with built-in scripts now; I added the "new X11" hack stolen from suspend2's hibernate script. This helps resolve the "dead display after resume" issues.

(2) No need for powernowd anymore. Just apt-get remove and say goodbye to it. When AC is unplugged, it will send CPU's into "powersave" (1GHz) mode and also enable PowerPlay on the lowest frequency. When AC is plugged in, it sends CPUs into "ondemand" (dynamic) mode and put video card into highest clock speed.

---

### Post by gmc on 2006-05-11
Hi jdong,

[QUOTE=jdong]Attached is my /etc/acpi directory[/QUOTE]

Boy, You are a busy little beaver :-) - Good job and Thanks.

Gord

---

### Post by jdong on 2006-05-11
Yep; trying to get the best I can outta this laptop :)

---

### Post by gmc on 2006-05-11
Hi jdong,

[QUOTE=jdong]Yep; trying to get the best I can outta this laptop :)[/QUOTE]

Are you sure the processor(s) are put in ondemand mode while on AC and powersave on battery?

I've replaced my /etc/acpi files with your's and uninstalled powernowd. When I check /sys/devices/system/cpu/cpu# there's no references to freq* or govenor* files. I'm pretty sure powernowd doesn't create them and the only modules the kernel loaded are cpufreq_userspace and freq_table.

I see in fglrx-powermode.sh is the only reference to cpufreq, and I don't have a program called cpufreq-set.

Gord

---

### Post by jdong on 2006-05-11
I'm sorry; I forgot to tell you that you need **cpufrequtils**

---

### Post by gmc on 2006-05-11
Hi jdong,

[QUOTE=jdong]Yep; trying to get the best I can outta this laptop :)[/QUOTE]

Are you sure the processor(s) are put in ondemand mode while on AC and powersave on battery?

I've replaced my /etc/acpi files with your's and uninstalled powernowd. When I check /sys/devices/system/cpu/cpu# there's no references to freq* or govenor* files. The only modules the kernel loaded are cpufreq_userspace and freq_table, the CPU frequency scaling monitor applet reports. (see attached gif)

I see in fglrx-powermode.sh is the only reference to cpufreq, and I don't have a program called cpufreq-set.

Gord

---

### Post by jdong on 2006-05-11
I forgot to mention that you need **cpufrequtils** installed... Sorry :)

---

### Post by gmc on 2006-05-11
Hi jdong,

[QUOTE=jdong]I forgot to mention that you need **cpufrequtils** installed... Sorry :)[/QUOTE]

Nope, replaced powernowd with cpufrequtils and same problem as before. Seems the kernel is not loading the appropriate drivers.  lsmod is reporting:

```

cpufreq_userspace       6496  0
freq_table              4928  0

```

as opposed to:

```

speedstep_centrino      8752  1 
cpufreq_userspace       6496  2 
cpufreq_stats           6688  0 
freq_table              4928  2 speedstep_centrino,cpufreq_stats
cpufreq_powersave       1920  0 
cpufreq_ondemand        7752  0 
cpufreq_conservative     9000  0 

```

Gord

---

### Post by jdong on 2006-05-11
Try executing "sudo /etc/acpi/power.sh" by hand. Any errors?

the fglrx script should be modprobing the modules you've listed... they do here... *scratches head*

---

### Post by gmc on 2006-05-11
[QUOTE=jdong]Try executing "sudo /etc/acpi/power.sh" by hand. Any errors?

the fglrx script should be modprobing the modules you've listed... they do here... *scratches head*[/QUOTE]

Nope, no errors and not working either. Actually the only reason that cpufreq_userspace and freq_table modules were being loaded was because they were in my /etc/modules file (I added them sometime back when I was testing something). I've removed them and rebooted. Now no freq/govenor related modules are being loaded. Me thinks something is wrong in Dodge.

```

# /etc/modules: kernel modules to load at boot time.
#
# This file contains the names of kernel modules that should be loaded
# at boot time, one per line. Lines beginning with "#" are ignored.

lp
psmouse
sbp2

fglrx
ipw3945

```

Gord

---

### Post by jdong on 2006-05-11
From fglrx-powermode.sh:
```

modprobe speedstep-centrino
modprobe cpufreq-powersave
modprobe cpufreq-ondemand
if [ ${on_dc} -eq 1 ]; then
        echo "On DC; going into powersave"
        cpufreq-set -c 0 -g powersave
        cpufreq-set -c 1 -g powersave

        iwpriv eth1 set_power 5
else
        echo "On AC; going into dynamic"
        cpufreq-set -c 0 -g ondemand
        cpufreq-set -c 1 -g ondemand
        iwpriv eth1 set_power 0
fi

```

It certainly does try to insert the required modules... Interesting that it's not loading for you. 

Try to issue the three modprobe statements by hand. Do they work and populate /sys?

Also try adding those modules to your /etc/modules file and see if that does you any good...

---

### Post by gmc on 2006-05-11
Hi jdong,

[QUOTE=jdong]From fglrx-powermode.sh:
```

modprobe speedstep-centrino
modprobe cpufreq-powersave
modprobe cpufreq-ondemand
if [ ${on_dc} -eq 1 ]; then
        echo "On DC; going into powersave"
        cpufreq-set -c 0 -g powersave
        cpufreq-set -c 1 -g powersave

        iwpriv eth1 set_power 5
else
        echo "On AC; going into dynamic"
        cpufreq-set -c 0 -g ondemand
        cpufreq-set -c 1 -g ondemand
        iwpriv eth1 set_power 0
fi

```

It certainly does try to insert the required modules... Interesting that it's not loading for you. 

Try to issue the three modprobe statements by hand. Do they work and populate /sys?

Also try adding those modules to your /etc/modules file and see if that does you any good...[/QUOTE]

The modules load correctly via /etc/modules (now that I've added them) and /sys is populated properly but yanking the AC, the CPU govenor's remain in ondemand mode. It looks like fglrx-powermode.sh isn't being executed. Very weird.

I'll be back in a bit, going to watch Buffalo knock off the Senators :-)

Gord

---

### Post by jdong on 2006-05-11
LOL

Well, first thing to try is to invoke both the fglrx and power.sh scripts by hand (with sudo) and see if you get any meaningful output from them. Adding strategically placed 'echo' statements will help you track execution progress, too...

---

### Post by jdong on 2006-05-12
**UPDATE:** I take back what I said before about C3 not saving power. My god does the Core Duo have some little surprises :)

Enabling C3 allowed me to easily tread into the 3:30+ battery life range during **normal use**. I have recompiled my kernels to be CONFIG_HZ 100, which in effect turns that annoying high-pitched beeping into a very low buzz that blends in with the hard drive and fan.

I am currently working on cleaner ways of generating these HZ=100 kernels; currently it's a terribly unholy hackjob on our beloved linux-source-2.6.15 package and linux-restricted-modules package.

Also, if you guys can go in and voice interest in [https://launchpad.net/distros/ubuntu/+source/linux-source-2.6.15/+bug/43281](https://launchpad.net/distros/ubuntu/+source/linux-source-2.6.15/+bug/43281),  that would get some more attention, too.

---

### Post by jdong on 2006-05-12
I'm going to start rolling my own kernel for this laptop; there's lots I'd like to experiment with on the kernel side...

Currently I'm just seeding a set of patches against the vanilla kernel, so it's not very useful, but as soon as it becomes useful, I'll publish a bzr (Bazaar-NG) branch of my kernel(s) for everyone here to use.

In the meantime, I'll have to figure out a hosting location for this... I need SFTP or FTP (preferably SFTP/SSH with public keys support) and a few hundred MB's of storage speed, and an upload pipeline that isn't afraid to take a person or two trying to retrieve the code. My ISP pipeline is out of the question... I'll consider using the Backports server first.


I'm not going to use Git because it's not very intuitive to me... I'm going to be more productive in bzr than Git, and it's going to be easier for you guys to follow bzr than git.

---

### Post by samir85 on 2006-05-13
Hi,

just want know if somebody here's experiencing the following issue with intel 3945 wireless drivers, since the new updates for Dapper yesterday ...

[https://launchpad.net/distros/ubuntu/+source/linux-source-2.6.15/+bug/44601](https://launchpad.net/distros/ubuntu/+source/linux-source-2.6.15/+bug/44601)

---

### Post by gmc on 2006-05-14
Hi Samir,

I can't say that I've noticed any problems with the 3945 driver (1.0.3) through out any of the updates over the last few days.

Gord

---

### Post by jdong on 2006-05-14
ipw3945 works fine for me....

I've started work on a "-duo" kernel for the acers... Currently, it just sets CONFIG_HZ to 100, but will do more in the future.

I've stored it in bzr branches at [http://ubuntubackports.org/jdong/kernels/](http://ubuntubackports.org/jdong/kernels/)

coreduo.dev, coreduo.stable, and linux-restricted-modules-coreduo are the interesting branches. Stable is currently unusable (I only have dev set up properly), while dev appears to work fine.

To retrieve the kernels, use something like this:
[code]
bzr init-repo --trees kernels
cd kernels
bzr get http://ubuntubackports.org/jdong/kernels/coreduo.dev/
bzr get http://ubuntubackports.org/jdong/kernels/coreduo.stable/
etc etc etc
[/coe]

To keep branches up to date, go into each folder (i.e. coreduo.dev) and run "bzr pull"

For more info on working with bazaar, see http://bazaar-vcs.org/



To build these kernels, they are regular old Debian packages, so dpkg-buildpackage works. First build the kernel (coreduo.dev) and install the resulting .deb's. Then, build linux-restricted-modules, as it needs installed kernel headers.

---

### Post by jdong on 2006-05-14
ipw3945 works fine for me....

I've started work on a "-duo" kernel for the acers... Currently, it just sets CONFIG_HZ to 100, but will do more in the future.

I've stored it in bzr branches at [http://ubuntubackports.org/jdong/kernels/](http://ubuntubackports.org/jdong/kernels/)

coreduo.dev, coreduo.stable, and linux-restricted-modules-coreduo are the interesting branches. Stable is currently unusable (I only have dev set up properly), while dev appears to work fine.

To retrieve the kernels, use something like this:
```

bzr init-repo --trees kernels
cd kernels
bzr get http://ubuntubackports.org/jdong/kernels/coreduo.dev/
bzr get http://ubuntubackports.org/jdong/kernels/coreduo.stable/
etc etc etc

```

To keep branches up to date, go into each folder (i.e. coreduo.dev) and run "bzr pull"

For more info on working with bazaar, see [http://bazaar-vcs.org/](http://bazaar-vcs.org/)



To build these kernels, they are regular old Debian packages, so dpkg-buildpackage works. First build the kernel (coreduo.dev) and install the resulting .deb's. Then, build linux-restricted-modules, as it needs installed kernel headers.

---

### Post by marianoi on 2006-05-15
Hello everyone,

I just followed the instructions for installing Xgl and Compiz. I created a new Xgl session. When loaded compiz seemed to work fine (cube rotated, etc). However, the system was pretty SLOW! Very slow. And after a few minutes I lost the windows decorations...

Has anyone had this problem? I do not know how to get the window decorations back...I tried several tips but nothing worked.

Help is welcomed!

Cheers :) 

Marianoi

EDIT: I found the problem and now **Compiz is working** pretty much ok. The dock plug-in somehow caused the issues I mentioned. I just removed it from the list and restarted the system. After that I had no problems (well, except that opacity plug-in is not working)

---

### Post by lir on 2006-05-15
hey guess what?

i just got my acer aspire 5562wxmi and it rocks!
i got ubuntu dapper flight 7 installed and from there xgl and fglrx where
a breeze.

though im with the stock 2.6.15-22-386 kernel and i see there is a 
linux-686-smp package. if i install it would i have to re-install fglrx/xgl?
cause that would suck...

---

### Post by jdong on 2006-05-15
[QUOTE=lir]hey guess what?

i just got my acer aspire 5562wxmi and it rocks!
i got ubuntu dapper flight 7 installed and from there xgl and fglrx where
a breeze.

though im with the stock 2.6.15-22-386 kernel and i see there is a 
linux-686-smp package. if i install it would i have to re-install fglrx/xgl?
cause that would suck...[/QUOTE]
If you are using the -386 kernel, you will not be using the 2nd core, which will be quite a performance hit, upwards of half your potential speed.

Install the linux-686 package (-smp is not required; the Dapper 686 kernel is already SMP) for using both cores. You will not have to reinstall fglrx nor will you have to reconfigure xgl.

---

### Post by lir on 2006-05-16
[QUOTE=jdong]If you are using the -386 kernel, you will not be using the 2nd core, which will be quite a performance hit, upwards of half your potential speed.

Install the linux-686 package (-smp is not required; the Dapper 686 kernel is already SMP) for using both cores. You will not have to reinstall fglrx nor will you have to reconfigure xgl.[/QUOTE]

ahh ok, thanks jdong.
im so happy to have found this thread as i got my new acer 5562wxmi
(basically the same as the 5672 just 14.1" wide screen) and im installing
linux on it.

have you found support for the wireless with the ipw3495 website?
is it necessary to install it from source only or is there a package ready
in dapper?


thanks.

---

### Post by jdong on 2006-05-16
Thee ipw3945 should already be detected as eth1 and working out of the box.

---

### Post by jdong on 2006-05-16
Regarding the webcam: I found this post on the uvc-video list ([https://lists.berlios.de/pipermail/linux-uvc-devel/2006-May/000501.html](https://lists.berlios.de/pipermail/linux-uvc-devel/2006-May/000501.html))

> 
The camera you're talking about does not support UVC and will therefore  
not work with the Linux
UVC driver.

However, Michel Xhaard, the author of the SPCA5xx driver  
([http://mxhaard.free.fr/spca5xx.html](http://mxhaard.free.fr/spca5xx.html)) is
currently looking into adding support for this type of camera. So with a  
little bit of luck and
Michel's great work you should be able to use it in the not too far future.

Cheers,
Martin


So, that limits our search down to spca5xx... Maybe one of us should send off a polite inquiry to the spca50x list, and offer our help.

---

### Post by jdong on 2006-05-16
UPDATES:

*  New BIOS patch: [ftp://ftp.acer-euro.com/notebook/aspire_5620_5670/bios](ftp://ftp.acer-euro.com/notebook/aspire_5620_5670/bios)

3224.zip; requires either Windows (if you still have it lying around) or a DOS environment (which you can produce on a CD or bootable USB stick) to flash.

Not too much new with the BIOS update, except a lot of Video BIOS work, which seems to make resume-from-{disk,RAM} much more reliable. Now, my virtual terminals do not get clobbered on resume :)


UPDATE: 

Yes, this update does do miracles for suspend support. I have flawless suspend to disk and suspend to RAM right now!

---

### Post by lir on 2006-05-17
Just wondering how are the Fn-Up and Down arrow keys working for you?
(those for the sound) because they aren't working for me on 5562 (latest dapper flight 7). I can't even see their keycodes in console as 'unknown key kbd' or something...

Also, would you say your linux is pretty much un-consuming with the battery?
Cause I can get on a fully charged battery (brand new laptop) not more than
1:45 hours. I've made sure I'm runing frequency scaling.


Thanks.

---

### Post by jdong on 2006-05-17
[QUOTE=lir]Just wondering how are the Fn-Up and Down arrow keys working for you?
(those for the sound) because they aren't working for me on 5562 (latest dapper flight 7). I can't even see their keycodes in console as 'unknown key kbd' or something...
[/quote]
The fn-up/down works the same as the Vol+/Vol- keys for me, under GNOME. Under KDE, you have to configure it as a KMix Global Shortcut. Make sure you use a keyboard model that supports volume keys, like:
```

        Option      "XkbModel" "microsoftpro"

```

> 
Also, would you say your linux is pretty much un-consuming with the battery?
Cause I can get on a fully charged battery (brand new laptop) not more than
1:45 hours. I've made sure I'm runing frequency scaling.


No; not over here... Linux is pretty much on par with Windows over here... 3 hr 10 minutes Linux, 3 hr 20 min Windows...

Make sure that CPU frequency and video card frequency scaling are both working. Look at my attached acpi.tar.gz for more information on frequency scaling setup.

---

### Post by gmc on 2006-05-17
Hi jdong,

[QUOTE=jdong]UPDATES:

*  New BIOS patch: [ftp://ftp.acer-euro.com/notebook/aspire_5620_5670/bios](ftp://ftp.acer-euro.com/notebook/aspire_5620_5670/bios)

3224.zip; requires either Windows (if you still have it lying around) or a DOS environment (which you can produce on a CD or bootable USB stick) to flash.

Not too much new with the BIOS update, except a lot of Video BIOS work, which seems to make resume-from-{disk,RAM} much more reliable. Now, my virtual terminals do not get clobbered on resume :)

UPDATE: 

Yes, this update does do miracles for suspend support. I have flawless suspend to disk and suspend to RAM right now![/QUOTE]

Now it sucks to be me then. I removed WindowsXP, looks like I'm going to have to try and make a bootable USBdrive or fork out for a USB floppy drive.

Gord

---

### Post by angel12 on 2006-05-17
so any luck on the volume keys in gnome with front/pcm? thats my main reason for stickin in windows. pretty crummy reason but still.

---

### Post by jdong on 2006-05-17
[QUOTE=angel12]so any luck on the volume keys in gnome with front/pcm? thats my main reason for stickin in windows. pretty crummy reason but still.[/QUOTE]
As I said, make sure in your xorg.conf you're using the "microsoftpro" keyboard model. It works fine here.

---

### Post by lir on 2006-05-17
[QUOTE=jdong]The fn-up/down works the same as the Vol+/Vol- keys for me, under GNOME. Under KDE, you have to configure it as a KMix Global Shortcut. Make sure you use a keyboard model that supports volume keys, like:
```

        Option      "XkbModel" "microsoftpro"

```



No; not over here... Linux is pretty much on par with Windows over here... 3 hr 10 minutes Linux, 3 hr 20 min Windows...

Make sure that CPU frequency and video card frequency scaling are both working. Look at my attached acpi.tar.gz for more information on frequency scaling setup.[/QUOTE]



1. About the Fn-keys - thanks for the tip I'll try xorg with that option
2. About the acpi/battery time - thats a hell of a great time but there is 
    a bit of difference since I'm using the acer 5562 wxmi (ati 1400) and your
    using the 5672, they're pretty much same configuration but still im sure
    there are differences.

    never-the-less, i just noticed that im getting 1h and about 30-40 minutes
    top on linux with battery fully charged and about 2h and 30-40 on  
    windows. i've taken a look at your acpi tar which is full of scripts that
    i dont know what to do with :)

    i know about cpu frequency scaling - i've installed the -686 kernel as you
    suggested and now i see 2 cpus and i also see with the gnome cpu 
    indicator that its showing sometimes the speed on 1gh and times on 1.66
    whats video frequency scaling though? never heard of that.

    also- are you getting those 3h battery life with everything turned on?
    i mean there are so many things- bluetooth, wireless, irda... 
    maybe i should also take a try at minimizing gnome's start-up items
    or remove unneeded services and such.


    id like to have your opinion over the battery life thing, its the most
    important to me. 
    thanks.


  lir

---

### Post by angel12 on 2006-05-17
jdong, so flight 7 fixed the front/pcm issue with the volume keys? in gnome in flight 7 if i would use the vol+ / vol- keys it would change the PCM volume, not the FRONT volume...

---

### Post by jdong on 2006-05-17
My 3 hours of battery life is a genuine 3 hours of usage: word processing web browsing, and light programming. I typically have bluetooth off, wireless on, and I'm unsure about the IR.

The greatest factors contributing to battery life (ordered from most important down) are:

(1) Video card clock speed. By default, the ATI card operates at the fastest clock speed. Lowering this to the lowest setting while on battery yields an extra hour of life!

(2)  Display brightness. Use the lowest brightness setting that's comfortable to your eyes. I typically operate on a notch or two above minimum while indoors. This also makes a huge difference on battery life (30 minutes potentially, I'd say)

(3) CPU frequency scaling. I find that with the Core Duo processors, the CPU does not have that great a drain on battery power. For example, there is only about a 20% difference in battery life between letting the laptop sit idle at the lowest frequency and performing a large batch of MP3 encoding utilizing both cores at full speed. Nonetheless, CPU frequency scaling does get you 15 minutes or so of additional life in average use.


Less important factors include:
* Hard disk spindowns: I find the HD doesn't really use much power. Having it spin up and down every few minutes does not make any difference for me.
* CPU C-states: As I've noted before, C3 must be disabled on most of these laptops to prevent an annoying high pitched noise. This costs about 5-10 minutes of life at most; as the high C-states are only entered when the system is _completely_ idle. A little animation on the screen or a move of your mouse immediately disengages CPU sleep.
=======

As far as my ACPI scripts, you can simply replace the contents of your /etc/acpi with my files. You will also need to install **cpufreq-utils**, which my script uses to effect CPU frequency changes, and uninstall powernowd. My ACPI tweaks perform the following:

* CPU frequency scaling:
   * On AC power, use dynamic frequency scaling
   * On battery power, lock into lowest frequency (1GHz)
* GPU scaling:
   * On AC power, use highest GPU speed
   * On battery, use lowest GPU speed
* Suspend tweaks
   * Do not mess with framebuffer enabling/disabling with suspend; our laptops don't need it and it clouds potentially useful debug messages.

Most of my changes are centered in "power.sh" and "fglrx-powermode.sh", so just copying those two will likely suffice.

---

### Post by jdong on 2006-05-17
[QUOTE=angel12]jdong, so flight 7 fixed the front/pcm issue with the volume keys? in gnome in flight 7 if i would use the vol+ / vol- keys it would change the PCM volume, not the FRONT volume...[/QUOTE]

No, that issue has not changed... PCM is still controlled instead of Front. I have filed a bug on that ([https://launchpad.net/distros/ubuntu/+source/linux-source-2.6.15/+bug/45167)](https://launchpad.net/distros/ubuntu/+source/linux-source-2.6.15/+bug/45167)), so I'm awaiting results on that.

If you guys can go and voice confirmation, that'd help, too!

---

### Post by ubiqquitous on 2006-05-18
Wow, guys, jdong and gmc, great great work...

I just ordered another Acer notebook and I am going to attempt something similar to your efforts:

[http://ubuntuforums.org/showthread.php?t=178564](http://ubuntuforums.org/showthread.php?t=178564)

As I said in that thread, it would be nice to have a set of reference platforms. That way, anyone could buy one of the reference platforms and get Ubuntu running without having to do things the OS should handle.

Acer notebooks are good candidates for this because they offer good power/value ratios.
Actually, we should probably contact Acer and get their support for this. Clearly, this makes their notebooks more appealing.

---

### Post by lir on 2006-05-18
[QUOTE=jdong]My 3 hours of battery life is a genuine 3 hours of usage: word processing web browsing, and light programming. I typically have bluetooth off, wireless on, and I'm unsure about the IR.

The greatest factors contributing to battery life (ordered from most important down) are:

(1) Video card clock speed. By default, the ATI card operates at the fastest clock speed. Lowering this to the lowest setting while on battery yields an extra hour of life!

(2)  Display brightness. Use the lowest brightness setting that's comfortable to your eyes. I typically operate on a notch or two above minimum while indoors. This also makes a huge difference on battery life (30 minutes potentially, I'd say)

(3) CPU frequency scaling. I find that with the Core Duo processors, the CPU does not have that great a drain on battery power. For example, there is only about a 20% difference in battery life between letting the laptop sit idle at the lowest frequency and performing a large batch of MP3 encoding utilizing both cores at full speed. Nonetheless, CPU frequency scaling does get you 15 minutes or so of additional life in average use.


Less important factors include:
* Hard disk spindowns: I find the HD doesn't really use much power. Having it spin up and down every few minutes does not make any difference for me.
* CPU C-states: As I've noted before, C3 must be disabled on most of these laptops to prevent an annoying high pitched noise. This costs about 5-10 minutes of life at most; as the high C-states are only entered when the system is _completely_ idle. A little animation on the screen or a move of your mouse immediately disengages CPU sleep.
=======

As far as my ACPI scripts, you can simply replace the contents of your /etc/acpi with my files. You will also need to install **cpufreq-utils**, which my script uses to effect CPU frequency changes, and uninstall powernowd. My ACPI tweaks perform the following:

* CPU frequency scaling:
   * On AC power, use dynamic frequency scaling
   * On battery power, lock into lowest frequency (1GHz)
* GPU scaling:
   * On AC power, use highest GPU speed
   * On battery, use lowest GPU speed
* Suspend tweaks
   * Do not mess with framebuffer enabling/disabling with suspend; our laptops don't need it and it clouds potentially useful debug messages.

Most of my changes are centered in "power.sh" and "fglrx-powermode.sh", so just copying those two will likely suffice.[/QUOTE]


Thanks for the great reply.
I have to ask some more questions as I'm new to this power saving thing.

So I'm currently doing (2) and (3) and I doubt (1) (video clock speed) is enabled
on my setup by default.

So to get things straight:
I'm currently runing powernowd to manage all the frequency scaling stuff?
Once I unpack your acpi tar to /etc/acpi how do i start making them work?
I mean, does linux now automatically that on AC to run 1 script and on battery
to run others? 

If I remove powernowd should I install an alternative package to manage
the power saving thing? 

Sorry for all the questions - its a first to handle power saving issues.

---

### Post by jdong on 2006-05-18
[QUOTE=lir]Thanks for the great reply.
I have to ask some more questions as I'm new to this power saving thing.

So I'm currently doing (2) and (3) and I doubt (1) (video clock speed) is enabled
on my setup by default.

So to get things straight:
I'm currently runing powernowd to manage all the frequency scaling stuff?
Once I unpack your acpi tar to /etc/acpi how do i start making them work?
I mean, does linux now automatically that on AC to run 1 script and on battery
to run others? 
[/quote]
They will begin working automagically. Specifically, /etc/acpi/power.sh is run by acpid every time the power state changes on the system.

> 
If I remove powernowd should I install an alternative package to manage
the power saving thing? 

Sorry for all the questions - its a first to handle power saving issues.
Nope; I use the kernel governors "cpufreq-ondemand" to provide dynamic scaling and "cpufreq-powersave" to provide lowest frequency. This functionality is built into the kernel with no need for userspace agents.

---

### Post by gmc on 2006-05-18
Hi Folks,

Ok, I jumped the gun a little while back removed Windows XP (Bye Bill). This had the unfortunate side effect of not allowing me to upgrade my bios (easily). And here was me all proud to be Windows free.

I did a little searching on Google and noted that HP created a utility to format and create a bootable USB drive some time back. Unfortunately, HP removed the utility and it's pretty hard to find. I did eventually find it. You'll need to find someone with a Windows machine in order to help you create your bootable USB drive, but once created, you don't need anything more to do with Windows.

Search google for the following **sp27213.exe** and **hpusbfw_bootfiles.zip**. You shouldn't have too much trouble finding them.

The good news is that I created my bootable USB drive and have successfully flashed my bios up to 3224 version :-)

Gord

---

### Post by sharedagroove on 2006-05-18
When I got my 5672 I kept the recovery partition and the XP partiton, and installed dapper on a third primary partition using grub as the bootloader.  

I was wondering if anyone would have a suggestion for removing dapper and grub so I could get back to the way my machine was when I started.

---

### Post by Clint. on 2006-05-18
No not ness, Bud,  get ahold of me on msn, gaim, etc,,   [email]clintsnet@hotmail.com[/email]

:-)

---

### Post by lir on 2006-05-18
[QUOTE=jdong]They will begin working automagically. Specifically, /etc/acpi/power.sh is run by acpid every time the power state changes on the system.


Nope; I use the kernel governors "cpufreq-ondemand" to provide dynamic scaling and "cpufreq-powersave" to provide lowest frequency. This functionality is built into the kernel with no need for userspace agents.[/QUOTE]


Well I've removed powernowd like you told me and did 
'apt-get install cpufrequtils' though no I see that my cpu is alwayson 1.66, 
full power and even if i add the applet for gnome to monitor the cpu
it tells me "CPU frequency scaling unsupported: you will not be able to modify the frequency of your machine....".

I removed the /etc/acpi dir and untarred your gz file to /etc/acpi...

One more thing - I dont know if you compiled your own custome kernel
but I havent. im working with vanilla, kernel stock 2.6.15-22-686 from
ubuntu dapper flight 7.


your help please, thanks.

an update:

i also took a look at /etc/acpi a bit and try runing ./power.sh for example
which exited with error about /etc/default/fglrx which doesnt exist and i saw 
you were trying to load some modules so i've loaded them too....
the cpufreq-powersave, -ondemand and speedstep-centrino.
still no change.

thanks in advance.

---

### Post by jdong on 2006-05-18
Oops, totally forgot about /etc/default/fglrx!

Create that file, and put:

```

FGLRX_ACPI_SWITCH_POWERSTATES=true

```

in there.

---

### Post by jdong on 2006-05-18
Here's a new acpi.tar.gz:

> 
------------------------------------------------------------
revno: 32
committer: root <root@jdong-laptop>
branch nick: etc
timestamp: Thu 2006-05-18 18:19:39 -0400
message:
  Remove dependency on /etc/default/fglrx
------------------------------------------------------------
revno: 31
committer: root <root@jdong-laptop>
branch nick: etc
timestamp: Thu 2006-05-18 18:18:12 -0400
message:
  * ACPI: Make console switch delayed; seems to help with nasty bug that hangs suspends.
------------------------------------------------------------


---

### Post by lir on 2006-05-18
[QUOTE=jdong]Oops, totally forgot about /etc/default/fglrx!

Create that file, and put:

```

FGLRX_ACPI_SWITCH_POWERSTATES=true

```

in there.[/QUOTE]


still things are kind of odds.
like seems like POWERplay is not installed cause if i manually run
aticonfig --lsp im getting
"Error: Unable to obtain POWERplay information" - any ideas?

i've re-ran /etc/acpi/power.sh and now i do see that it detects im on
AC and goes into dynamic mode.

---

### Post by jdong on 2006-05-18
You mean, if you run "aticonfig --lsp" **inside an X session**, you get an error?


I get:
```
  core/mem      [flags]
---------------
1: 135/135 MHz  [low voltage]
2: 392/252 MHz
3: 446/342 MHz  [default state]

```

---

### Post by lir on 2006-05-18
[QUOTE=jdong]You mean, if you run "aticonfig --lsp" **inside an X session**, you get an error?


I get:
```
  core/mem      [flags]
---------------
1: 135/135 MHz  [low voltage]
2: 392/252 MHz
3: 446/342 MHz  [default state]

```[/QUOTE]


right, inside an  X session ofcourse.
are you runing xgl?

cause i've been doing some reading for a little while and i see that it
requries the radeon or ati driver or something like that where as the 
if i use xgl i must configure the fglrx driver in xorg.conf

ummm, do you have any ideas on that?

EDIT---
actually its not fglrx i think because according to this website:
[http://www.thinkwiki.org/wiki/How_to_make_use_of_Graphics_Chips_Power_Management_features](http://www.thinkwiki.org/wiki/How_to_make_use_of_Graphics_Chips_Power_Management_features)
"Versions 8.19.10 and higher of the ATI fglrx driver support "PowerPlay", which "allows for the user to switch between power consumption modes".

---

### Post by jdong on 2006-05-18
Hmm, no, I'm not running Xgl. That's probably the difference. aticonfig is likely trying to interface with Xgl to do the powerstate transition when Xgl of course has no idea what the heck that command is :)

I'm not sure how well Xgl will run with the card clocked all the way down. Stuff like that is video card intensive, and that may also explain some of your battery drain.

---

### Post by YourDoom123 on 2006-05-18
I managed to get flight 7 installed on my 5672 (flight 6 refused to install because of a bug /w the installer), but my wifi doesn't work, nor can i install the new 686 kernel. I'm stuck using the 386 one cause the linux-restricted-modules-686 is broken... anyone else run into this?

---

### Post by lir on 2006-05-18
[QUOTE=jdong]Hmm, no, I'm not running Xgl. That's probably the difference. aticonfig is likely trying to interface with Xgl to do the powerstate transition when Xgl of course has no idea what the heck that command is :)

I'm not sure how well Xgl will run with the card clocked all the way down. Stuff like that is video card intensive, and that may also explain some of your battery drain.[/QUOTE]


ofcourse.
ok then hold up, im testing this without xgl :)

EDIT--

alright, i'm seeing great improvements.
first of all aticonfig --lsp does return the expected results so cool :)

and i'm seeing great improvements so xgl is a killer it seems :)
i had about 1h and 40 minutes before with xgl and im looking now at 2h and 41m 
when the battery is on 96%

so thanks for all the help and i guess those scripts are doing their thing :P

---

### Post by jdong on 2006-05-18
Excellent; glad to hear they're working out for you... And sorry you don't have shiny eyecandy anymore ;)


So I can stop posting tarballs every other reply, I have versioned my ACPI folder with bzr and published a branch at [http://ubuntubackports.org/jdong/acpi-coreduo/](http://ubuntubackports.org/jdong/acpi-coreduo/)


In a previous post about kernels, I've already explained how to use bzr. A web browser is not sufficient to see stuff; it'll just show a blank folder.

I don't see myself doing much more ACPI hacking; everything looks decent to me right now. So, if you just unpacked a tarball of mine, you're probably not missing much compared to the bzr branch.


One known bug: The GPU is likely at the fastest speed when you boot. I'm still figuring out how to effect aticonfig at startup... The closest I've gotten is linking /etc/acpi/power.sh to /etc/X11/Xsession.d/01power, which effects a powerstate check at login. That means that while GDM is sitting there, it'll be under full GPU speed. Don't let GDM sit too long while under battery.

This bug only happens when you boot up on battery. If you boot up on AC then unplug, power states correctly transition.

If anyone has ideas as to fixing this, please let me know.

---

### Post by jdong on 2006-05-18
Just to say, you'd be surprised how much power video cards draw! When this mobility radeon is in full force, it has a bigger battery hit than fully loading both processor cores.

---

### Post by YourDoom123 on 2006-05-18
odd... i reinstalled using the daily build and my wifi worked... i let it update everything, and the wifi was no longer recognized... i'm gonna reinstall once more, but not "update" anything until I know whats going on.

---

### Post by gmc on 2006-05-19
Hi Folks,

Just a heads up. The new 2.6.15-23 kernel comes with version 1.0.3 ipw3945 driver, so WPA wireless should be good to go out of the box. Keep in mind that the restricted modules for this version of the kernel are not yet available so currently there is no fglrx driver and will break Xorg.

Boy Dapper is making leaps and strides...

Gord

Edited: ...and 10 minutes after the original post, the restricted modules arrives... :-)
Edited (again): Woohoo, no more having to manually compile the ipw3945 driver. I'm back to using WPA on my wireless connection.

---

### Post by lir on 2006-05-19
> **jdong]Excellent said:**
> http://ubuntubackports.org/jdong/acpi-coreduo/[/url]


In a previous post about kernels, I've already explained how to use bzr. A web browser is not sufficient to see stuff; it'll just show a blank folder.

I don't see myself doing much more ACPI hacking; everything looks decent to me right now. So, if you just unpacked a tarball of mine, you're probably not missing much compared to the bzr branch.


One known bug: The GPU is likely at the fastest speed when you boot. I'm still figuring out how to effect aticonfig at startup... The closest I've gotten is linking /etc/acpi/power.sh to /etc/X11/Xsession.d/01power, which effects a powerstate check at login. That means that while GDM is sitting there, it'll be under full GPU speed. Don't let GDM sit too long while under battery.

This bug only happens when you boot up on battery. If you boot up on AC then unplug, power states correctly transition.

If anyone has ideas as to fixing this, please let me know.

I still have my eyecandy :)
I just login with a different session to gnome in gdm everytime so its
actually very much comfortable and I can enjoy xgl when I'm not in a
need for long work time.

And thanks again about that 2nd fixed tarball post.
About the power settings its a very good idea then to indeed link it to
/etc/init.d/01power.sh so that right on the bootup process it changes
the power saving stuff...


_YourDoom123:_ 
I know what bug you're talking about, the way to solve it
(with flight 7 at least) is just to keep on trying to re-partition (delete and
then re-create, and format) at around the 3rd time it installs just fine.

I've had no problems installing 686 or the restricted modules. Everything
works fine, even wifi works out of the box (because ipw3945 is already
in the kernel and available as a module).


_gmc & YourDoom123:_
so is it safe to run apt-get update && apt-get upgrade ?
everything is working so well and supported that i wouldn't want to break
things with un-ncessesary upgrades :)

---

### Post by gmc on 2006-05-19
[QUOTE=lir]I still have my eyecandy :)
_gmc & YourDoom123:_
so is it safe to run apt-get update && apt-get upgrade ?
everything is working so well and supported that i wouldn't want to break
things with un-ncessesary upgrades :)[/QUOTE]

Sure is. Let 'er rip, and Enjoy :D 

Gord

---

### Post by gmc on 2006-05-19
Hi jdong,

[QUOTE=jdong]
One known bug: The GPU is likely at the fastest speed when you boot. I'm still figuring out how to effect aticonfig at startup... The closest I've gotten is linking /etc/acpi/power.sh to /etc/X11/Xsession.d/01power, which effects a powerstate check at login. That means that while GDM is sitting there, it'll be under full GPU speed. Don't let GDM sit too long while under battery.

This bug only happens when you boot up on battery. If you boot up on AC then unplug, power states correctly transition.

If anyone has ideas as to fixing this, please let me know.[/QUOTE]

How about putting the following in /etc/rc.local

```

[ ! -f /usr/bin/aticonfig ] || /usr/bin/aticonfig --set-powerstate 1 --effective=now

```

It's a kludge fix but it should work.

Gord

---

### Post by jdong on 2006-05-19
(1) It's safe to dist-upgrade. I've just done so, and it's working beautifully.

(2) I was actually considering one of the gdm shellscripts. Aticonfig only works when it assumes the identity and DISPLAY of the active X user. Somehow, it doesn't look like GDM responds to aticonfig at all, even if the power.sh is invoked after gdm pops up. Perhaps the gdm user is restricted in some fashion...

---

### Post by Dralt on 2006-05-19
Guys, fascinating thread indeed!

I have the following hardware:

- Genuine Intel(R) CPU T2500 @ 2.00GHz
- ATI Mobility Radeon X1400
- Realtek High Definition Audio
- TOSHIBA MK1234GSX HDD
- HL-DT-ST DVDRAM GSA-4082N DVD drive
- Intel(R) PRO/Wireless 3945ABG

How can I burn an ISO that would include the latest stuff?
Apparently, Flight 7 is not going to be enough, right?

---

### Post by jdong on 2006-05-19
[http://cdimages.ubuntu.com/daily/current/](http://cdimages.ubuntu.com/daily/current/)
[http://cdimages.ubuntu.com/daily-live/current/](http://cdimages.ubuntu.com/daily-live/current/)

These are the install and live-install CD's that are built automatically every night. I personally still recommend the text-mode installer for those who are ept enough to deal with it as opposed to the live installer, because the last time I tried the live instaler (about a month ago, so it might be solved by now), custom partitioning was very shaky.

---

### Post by Dralt on 2006-05-19
[QUOTE=jdong][http://cdimages.ubuntu.com/daily/current/](http://cdimages.ubuntu.com/daily/current/)
[http://cdimages.ubuntu.com/daily-live/current/](http://cdimages.ubuntu.com/daily-live/current/)

These are the install and live-install CD's that are built automatically every night. I personally still recommend the text-mode installer for those who are ept enough to deal with it as opposed to the live installer, because the last time I tried the live instaler (about a month ago, so it might be solved by now), custom partitioning was very shaky.[/QUOTE]

Thanks!

I tried a Live install on another system with Flight 7 and I had problems as well. Basically, it could not adjust the partitions to make some room for Ubuntu.

Thanks again for your great help!

---

### Post by Dralt on 2006-05-19
[QUOTE=jdong][http://cdimages.ubuntu.com/daily/current/](http://cdimages.ubuntu.com/daily/current/)
[http://cdimages.ubuntu.com/daily-live/current/](http://cdimages.ubuntu.com/daily-live/current/)

These are the install and live-install CD's that are built automatically every night. I personally still recommend the text-mode installer for those who are ept enough to deal with it as opposed to the live installer, because the last time I tried the live instaler (about a month ago, so it might be solved by now), custom partitioning was very shaky.[/QUOTE]

Forgot a question...

If I install one of the daily builds, will I be able to update to the release version of Ubuntu 6.06 LTS?

Since the official release is supposed to come at the end of the month, I suppose daily builds must be very close to the final release at this point.

---

### Post by jdong on 2006-05-19
Yes. Once any snapshot/release of Dapper is installed, the upgrader will bring you up-to-date with the latest Dapper updates. There is never a need to reinstall Dapper when it is released or when a new beta comes out: if you update, you'll already be running it :)

The beta/flight releases just provide a convenient location for new users to hop on. Typically, extra care is taken to make sure there are no installer bugs in the snapshot releases, as opposed to the daily builds which are just machine-done with no human review :)

---

### Post by Dralt on 2006-05-19
[QUOTE=jdong]Yes. Once any snapshot/release of Dapper is installed, the upgrader will bring you up-to-date with the latest Dapper updates. There is never a need to reinstall Dapper when it is released or when a new beta comes out: if you update, you'll already be running it :)

The beta/flight releases just provide a convenient location for new users to hop on. Typically, extra care is taken to make sure there are no installer bugs in the snapshot releases, as opposed to the daily builds which are just machine-done with no human review :)[/QUOTE]

Really, really cool.
I must say Ubuntu is turning out to be the best Linux distribution ever.

I tend to prefer KDE versus Gnome. (hope I don't hurt any feelings)
Do the daily builds include the Kubuntu packages?

---

### Post by jdong on 2006-05-19
[QUOTE=Dralt]Really, really cool.
I must say Ubuntu is turning out to be the best Linux distribution ever.

I tend to prefer KDE versus Gnome. (hope I don't hurt any feelings)
Do the daily builds include the Kubuntu packages?[/QUOTE]
Linux is all about choice :). I myself switch from KDE to GNOME and back to KDE comically often (at one point, nearly daily).

There are Kubuntu images on the same server, but in a kubuntu subfolder. They are also built nightly in live and textmode flavors.

Just to say, the suspend tweaks I've done are GNOME specific... i.e. currently only gnome-power-manager seems to work with it. The two times I've tried with KDE's laptop daemon, I've hung the system on resume. I'm sure if I actually try harder to tweak the system, it will suspend from KDE fine, but right now I simply don't have the resources or (more importantly) incentive to do so.

If someone wants to take a stab at it, it involves getting the powersaved suspend/resume scripts to call Ubuntu's /etc/acpi/sleep.sh force or /etc/acpi/hibernate.sh force.

---

### Post by Dralt on 2006-05-19
[QUOTE=jdong]Linux is all about choice :). I myself switch from KDE to GNOME and back to KDE comically often (at one point, nearly daily).

There are Kubuntu images on the same server, but in a kubuntu subfolder. They are also built nightly in live and textmode flavors.

Just to say, the suspend tweaks I've done are GNOME specific... i.e. currently only gnome-power-manager seems to work with it. The two times I've tried with KDE's laptop daemon, I've hung the system on resume. I'm sure if I actually try harder to tweak the system, it will suspend from KDE fine, but right now I simply don't have the resources or (more importantly) incentive to do so.

If someone wants to take a stab at it, it involves getting the powersaved suspend/resume scripts to call Ubuntu's /etc/acpi/sleep.sh force or /etc/acpi/hibernate.sh force.[/QUOTE]

I can stick with Gnome, for a while...it's not that it's bad...the latest KDE gets closer Mac OS X, though...you know, I'm vain and I like nice high-resolution icons...

Is there any traps and pitfalls while using the text-mode installer?
How much does it differ, functionally, from the GUI installer?

---

### Post by jdong on 2006-05-19
[QUOTE=Dralt]I can stick with Gnome, for a while...it's not that it's bad...the latest KDE gets closer Mac OS X, though...you know, I'm vain and I like nice high-resolution icons...
[/quote]
KDE rocks for visual appeal, yes... but in my experience (not to go on a desktop environment rant) KDE works much less out-of-the-box compared to GNOME... I have simplistic needs.. I don't stare all day at icons complaining about their resolution :)

> 
Is there any traps and pitfalls while using the text-mode installer?
How much does it differ, functionally, from the GUI installer?
The textmode installer will not have a functioning GUI (duh) during install, so the system will basically be unusable during the install procedure. With the LiveCD, you can still browse the web and do other stuff while installing. The text installer, however, is much more mature (age and widespread usage) than the GUI installer.


The text mode installer uses a simple, keyboard-driven interface rather than the GUI's mouse-driven interface. Both are basically identical in functionality, except the text-mode interface can expose more expert options if you so desire.

---

### Post by Dralt on 2006-05-19
[QUOTE=jdong]KDE rocks for visual appeal, yes... but in my experience (not to go on a desktop environment rant) KDE works much less out-of-the-box compared to GNOME... I have simplistic needs.. I don't stare all day at icons complaining about their resolution :)[/QUOTE]

I understand perfectly. I am all about functionality. Yet, I don't think high-resolution icons would hurt anything either. In other words, functionality and performance come first. After that, if a system is graphically appealing, it's icing on the cake.

:)

Thanks for all the tips.
I am going to get to that this weekend.

---

### Post by gmc on 2006-05-19
Hi Folks,

Is any one finding that the ipw3945 driver that's included with the 2.6.15-23 kernel works for a while then loses connection with the router and refuses to connect again. I'm not sure if it's actually the driver or if it's dhclient that's refusing to reconnect with the router but the only solution for me is to reboot the system. Back when we had to manually compile the 3945 driver, I never had this problem.

Gord

---

### Post by jdong on 2006-05-19
I've been noticing that at times this new ipw3945 will associate but not transmit packets... Some weird combination of waiting, flipping the frequency switch, and performing rain dances seems to resolve it... Like right now I can't reproduce it.

EDIT: [https://launchpad.net/distros/ubuntu/+source/linux-source-2.6.15/+bug/45676](https://launchpad.net/distros/ubuntu/+source/linux-source-2.6.15/+bug/45676) LP ticket opened.

---

### Post by YourDoom123 on 2006-05-19
hmm the wireless is working fine for me. Haven't had any problems with it. the 686-smp kernel installed today, so today is looking good :-P

one question though... is there a better touchpad driver then the default? i'd really like vertical and horizontal scrolling. everything else is a bonus, but those two are a must.

and i also gotta figure out how to turn the refresh rate up... i'm used to it fairly high.

---

### Post by angel12 on 2006-05-19
edit xorg mouse drivers to use the synaptics, that i think will do the trick, be sure to back up xorg.conf just in case

EDIT: edit the file /etc/X11/xorg.conf, once again, be sure to back it up

---

### Post by YourDoom123 on 2006-05-19
yea, thts what i was trying when u posted tht, lol. I'm confused tho as to what to change it to, because the way its set up right now, is the same way i would set it up for a normal mouse.

---

### Post by jdong on 2006-05-19
Attached is my xorg.conf. It is configured with a good set of touchpad parameters for our particular pads (the edge values have to be tuned).


A few touchpad tricks that not everyone knows:

* The corners are special. Tapping the bottom right corner  generates a right-click, and tapping the top right corner generates a middle-click.
* You can tap and drag files. Tap, release, then immediately tap, then HOLD (i.e. double-tap, but do not release the 2nd tap). Now, when you move your mouse, you will drag whatever's underneath it. When you move into an edge, the cursor will continue cruising in that direction, so you don't run out of dragging room :)

* Multi-finger tapping also works. Tapping with two fingers generates a middle click. Tapping with 3 fingers generates a right click.

---

### Post by gmc on 2006-05-19
Hi YourDoom123,

[QUOTE=YourDoom123]hmm the wireless is working fine for me. Haven't had any problems with it. the 686-smp kernel installed today, so today is looking good :-P

one question though... is there a better touchpad driver then the default? i'd really like vertical and horizontal scrolling. everything else is a bonus, but those two are a must.

and i also gotta figure out how to turn the refresh rate up... i'm used to it fairly high.[/QUOTE]

Thanks for the conformation, I'll have to play with it some more.

I'm not sure if this will help, but here's the xorg.conf that I'm using. I found it [here]("http://www.dicianno.org/files/acer5670/xorg.conf"), though I've modified it a bit (see below). Note the **bold** section seemed to make the touchpad a lot easier to work with, though for the most part I use a Logitech marble mouse.

```

Section "Files"
        FontPath        "/usr/share/X11/fonts/misc"
        FontPath        "/usr/share/X11/fonts/cyrillic"
        FontPath        "/usr/share/X11/fonts/100dpi/:unscaled"
        FontPath        "/usr/share/X11/fonts/75dpi/:unscaled"
        FontPath        "/usr/share/X11/fonts/Type1"
        FontPath        "/usr/share/X11/fonts/100dpi"
        FontPath        "/usr/share/X11/fonts/75dpi"
        # path to defoma fonts
        FontPath        "/var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType"
EndSection

Section "Module"
        Load    "i2c"
        Load    "bitmap"
        Load    "ddc"
        Load    "dri"
        Load    "extmod"
        Load    "freetype"
        Load    "glx"
        Load    "int10"
        Load    "type1"
        Load    "vbe"
EndSection

Section "InputDevice"
	Identifier  "Keyboard1"
	Driver      "kbd"
	Option	    "XkbRules" "xorg"
	Option	    "XkbModel" "pc104"
	Option	    "XkbLayout" "us"
EndSection

Section "InputDevice"
	Identifier  "Mouse1"
	Driver      "mouse"
	Option	    "Protocol" "auto"
	Option	    "Device" "/dev/input/mice"
	Option	    "ZAxisMapping" "4 5 6 7"
	Option	    "Emulate3Buttons"
EndSection

[B]Section "InputDevice"
	Identifier  "Mouse0"
	Driver      "synaptics"
	Option	    "Device"	"/dev/psaux"
	Option	    "Protocol"	"auto-dev"
	Option	    "LeftEdge"	 "1350"
	Option	    "RightEdge"	 "5500" # allow scrollon on the right edge, so this is within the physical border
	Option	    "TopEdge"	 "1400"	# above the physical top
	Option      "BottomEdge" "5000" # below the physical top
	Option	    "FingerLow"  "35"
	Option	    "FingerHigh" "58" # these setting should allow clicks -- use synclient to turn off tap when typing
	Option	    "VertScrollDelta" "100"
	Option	    "MinSpeed" 	      "0.02"
	Option	    "MaxSpeed" 	      "0.09"
	Option	    "AccelFactor"     "0.0010"
	Option	    "SHMConfig" "on" # we need this for synclient to work
	Option	    "Emulate3Buttons" "yes" # what should be the middle button is a rocker, 4-way, not 5-way (no press)
EndSection[/B]

Section "Monitor"
	Identifier   "monitor"
	HorizSync    31.5 - 90.0
	VertRefresh  45.0 - 110.0
	ModeLine     "1280x800" 123.4 1280 1368 1504 1728 800 801 804 840
	Option	     "DPMS"
EndSection

Section "Device"
	Identifier  "tvideo"
	Driver      "fglrx"
        VideoRam        131072   # Video corruption if set higher that 128M
        Option          "KernelModuleParm" "agplock=0" # Need this for XGL/Compiz
        Option          "VideoOverlay"          "on"
        Option          "OpenGLOverlay"         "off"
        Option          "UseInternalAGPGART"    "yes"
        BusID           "PCI:1:0:0"
EndSection

Section "Screen"
	Identifier "Screen 1"
	Device     "tvideo"
	Monitor    "monitor"
	DefaultDepth     24

	SubSection "Display"
		Depth     24
		Modes    "1280x800" "1024x768" "800x600" "640x480"
	EndSubSection
EndSection

Section "DRI"
	Mode         0666
EndSection

Section "ServerLayout"
	Identifier     "Simple Layout"
	Screen         "Screen 1"	0 0
	InputDevice    "Mouse0"	   	"CorePointer"
	InputDevice    "Keyboard1" 	"CoreKeyboard"
EndSection

```

Gord

---

### Post by YourDoom123 on 2006-05-20
jdong, ur touchpad set up works perfectly for me... Thanks! I started work on setting up Xgl/Compiz... This is my first time using them, and I'm sure something is not working right, because every time i load into it, i get a different screen... sometimes, its a standard gnome login, except only one desktop works, and everything is slower... much slower. and other times, the top and bottom taskbars just don't show up... just the icons. So the only way to restart the comp safely is to pull the plug, and wait for it to power down... i'd do a hard restart, but i crashed the entire system once like that already, so i'm not too keen on tht. Since then, I've not gone back into xgl. i followed the guides exactly, so i'm not sure whats wrong... any ideas?

---

### Post by Dralt on 2006-05-20
[QUOTE=jdong]I've been noticing that at times this new ipw3945 will associate but not transmit packets... Some weird combination of waiting, flipping the frequency switch, and performing rain dances seems to resolve it... Like right now I can't reproduce it.

EDIT: [https://launchpad.net/distros/ubuntu/+source/linux-source-2.6.15/+bug/45676](https://launchpad.net/distros/ubuntu/+source/linux-source-2.6.15/+bug/45676) LP ticket opened.[/QUOTE]

I hope someone can fix this, I really love my wireless. :)

Also, after working on my new hardware, I realized the following: The TravelMate 4670 series is the same hardware as the Aspire 5670 series, without Bluetooth, without the Web cam, but with the 2.0 GHz version of the Core Duo, 2 GB of RAM, and a 120 GB HDD.

This is great in my book, since I didn't care for the Web cam or Bluetooth, but  I can always use a faster CPU and more RAM. :-D

---

### Post by jdong on 2006-05-20
The wireless issue is really weird; I can't get it to happen now...

---

### Post by Dralt on 2006-05-20
[QUOTE=jdong]The wireless issue is really weird; I can't get it to happen now...[/QUOTE]

Hey, the Core Duo kernel you made take care of the whine issue right?

Will I be able to upgrade to that kernel after I install today's daily?

---

### Post by angel12 on 2006-05-20
[QUOTE=Dralt]I hope someone can fix this, I really love my wireless. :)

Also, after working on my new hardware, I realized the following: The TravelMate 4670 series is the same hardware as the Aspire 5670 series, without Bluetooth, without the Web cam, but with the 2.0 GHz version of the Core Duo, 2 GB of RAM, and a 120 GB HDD.

This is great in my book, since I didn't care for the Web cam or Bluetooth, but  I can always use a faster CPU and more RAM. :-D[/QUOTE]


My 5270 came with 2gigs of ram, and im planning on upgrading the cpu, it seems to be pretty easy, and pretty cheap, i can get the 2.16ghz off ebay for around $500, and then i will just sell the chip i have now if everything works. And bluetooth is nice with all the new phones that are coming out with bluetooth. theres my two cents

---

### Post by jdong on 2006-05-20
[QUOTE=Dralt]Hey, the Core Duo kernel you made take care of the whine issue right?

Will I be able to upgrade to that kernel after I install today's daily?[/QUOTE]

I have to rebase my kernel to the new Ubuntu release, though... and it does not completely solve the whine. A correct combination of activated USB devices will bring the whine back in its full glory.


The better workaround is to set max_cstate=2 from rcS.d, which I've outlined earlier in this thread. This costs around 10 minutes in battery life, and completely eliminates the noise.

---

### Post by Dralt on 2006-05-20
[QUOTE=jdong]I have to rebase my kernel to the new Ubuntu release, though... and it does not completely solve the whine. A correct combination of activated USB devices will bring the whine back in its full glory.


The better workaround is to set max_cstate=2 from rcS.d, which I've outlined earlier in this thread. This costs around 10 minutes in battery life, and completely eliminates the noise.[/QUOTE]

I am posting this from my fresh Ubuntu install! :)

So, doh, the network adapter was recognized. I also have video, although the x1400 was not recognized and the current resolution is 1024x768.

So, first order of business: Fix the video stuff.

UPDATE: Oops...wrong...need to get both cores to be recognized....

---

### Post by Dralt on 2006-05-20
Do you guys use kernel framebuffers with fglrx?

---

### Post by jdong on 2006-05-20
We do use kernel framebuffers.


To get both cores recognized, install 'linux-686'. For video, follow standard Ubuntu procedures for installing fglrx from the repositories.

---

### Post by Dralt on 2006-05-20
[QUOTE=jdong]We do use kernel framebuffers.


To get both cores recognized, install 'linux-686'. For video, follow standard Ubuntu procedures for installing fglrx from the repositories.[/QUOTE]

When I configured X, I said no to kernel framebuffers. It seems to work, but the Screen Resolution applet does not show 1280x800 as an option.
I'm going to refer to your copy of xorg.conf.

UPDATE: I don't think you are using kernel framebuffers with flgrx, otherwise you would have this line in your xorg.conf file:

Option		"UseFBDev"		"true"

UPDATE 2: OK, 1280x800 is working and hardware acceleration is also working. Not sure why it didn't take it the first time around.

---

### Post by Dralt on 2006-05-20
Wow! I just fell on my rear end.
Here is why: I installed Network Manager. 2 minutes later, I connected to my wireless network using WPA. Flawlessly, I just had to type in my passphrase, obviously.

I have never experienced such ease before with a Linux distribution.

This is solid gold.

Now, I have a question, though.

Network Manager and the "Network Settings" applet don't seem to talk to each other. Indeed, Network Manager did all the work and I am connected, but the "Network Settings" applet still believes the wireless interface is not configured and not activated.

Is there a way to sync these 2?

Network Manager had an easy time because I set up my AP to run a DHCP server.
Now, however, I would like the wireless interface to use a static IP address, etc.
How do I change that? Is it done via the "Network Settings" applet?

The Network Settings applet does not know anything about WPA, so I am concerned that if I attempt to configure the wireless interface using it, it will mess up the magical job Network Manager did.

---

### Post by jdong on 2006-05-20
Network Manager and Network Settings are mutually exclusive. Only one can manager your networking settings. Network Manager specifically does not support static IP's because it's not a goal of the project...

So, either set up DHCP (or static DHCP leases) or set up wpa-supplicant the old-fashioned way.... I'd go with DHCP :)

---

### Post by Dralt on 2006-05-21
[QUOTE=jdong]Network Manager and Network Settings are mutually exclusive. Only one can manager your networking settings. Network Manager specifically does not support static IP's because it's not a goal of the project...

So, either set up DHCP (or static DHCP leases) or set up wpa-supplicant the old-fashioned way.... I'd go with DHCP :)[/QUOTE]


I worked with wpa_supplicant before and my love for DHCP has just increased by a mile or two. :)

---

### Post by gmc on 2006-05-21
Hi Folks,

I had a major fright a few minutes ago. I've just completed an apt-get upgrade and now during the period from entering my password on the gdm screen to the point I enter my keyring password, the fan on my machine sounds like a jet. The air flow out the side vent is enough to blow out a cigarette lighter 6 inches way.
The fan then returns to normal cooling speed and seems to stay that way from that point on.

I realize this might be a hardware problem but on the off chance, has anyone else noticed this problem?

Gord :(

---

### Post by Dralt on 2006-05-21
With the 5/20 daily, I don't see the ACPI Lid event flood problem. Did they fix or am I just lucky?

gmc, isn't that normal? I thought it was normal Core Duo handling. It sometimes happen with Windows as well.

---

### Post by lir on 2006-05-21
[QUOTE=jdong](1) It's safe to dist-upgrade. I've just done so, and it's working beautifully.

(2) I was actually considering one of the gdm shellscripts. Aticonfig only works when it assumes the identity and DISPLAY of the active X user. Somehow, it doesn't look like GDM responds to aticonfig at all, even if the power.sh is invoked after gdm pops up. Perhaps the gdm user is restricted in some fashion...[/QUOTE]

jdong, i think i may have a better suggestion.
for those (most?) of us who use gdm we can utilize the init script
that gdm always run which is located at /etc/X11/gdm/Init/Default
and add "/etc/acpi/power.sh" over there.
If necessary its possible to overcome premission problems by runing it suid
or chmod 777.

makes sense?

---

### Post by jdong on 2006-05-21
[QUOTE=gmc]Hi Folks,

I had a major fright a few minutes ago. I've just completed an apt-get upgrade and now during the period from entering my password on the gdm screen to the point I enter my keyring password, the fan on my machine sounds like a jet. The air flow out the side vent is enough to blow out a cigarette lighter 6 inches way.
The fan then returns to normal cooling speed and seems to stay that way from that point on.

I realize this might be a hardware problem but on the off chance, has anyone else noticed this problem?

Gord :([/QUOTE]
That is "normal". Fan control is strictly hardware controlled on this laptop (thank god!) and it's pefectly possible that you could've suddenly spiked your system temperature to a point where the system thought it appropriate to turn on the fan at full speed...


And the GDM suggestion, that is a good point. We need to code in a 10 second wait (sleep 10 && /etc/acpi/power.sh) & though, because I've found that swapping state right after X starts can lead to a kernel panic.

---

### Post by jdong on 2006-05-21
[QUOTE=Dralt]With the 5/20 daily, I don't see the ACPI Lid event flood problem. Did they fix or am I just lucky?

gmc, isn't that normal? I thought it was normal Core Duo handling. It sometimes happen with Windows as well.[/QUOTE]
I would not be surprised if either a kernel patch or a BIOS update fixed that. I'll investigate.

---

### Post by gmc on 2006-05-21
Hi jdong,

[QUOTE=jdong]That is "normal". Fan control is strictly hardware controlled on this laptop (thank god!) and it's pefectly possible that you could've suddenly spiked your system temperature to a point where the system thought it appropriate to turn on the fan at full speed...
[/QUOTE]

No, this is definately not normal. I've had this laptop since January and today is the first time I've ever heard the fan sound like this. I've tracked the problem down to XGL/Compiz. If I start a normal gnome session, the fan doesn't freak out. Since it's only occurring with XGL/Compiz, it's software related. Needless to say, I'll be steering clear of XGL/Compiz for a while. I really don't want to burn out the fan stressing it out like that.

Gord

Edited: As an after thought, maybe the new bios has something to do with it too?

---

### Post by angel12 on 2006-05-21
[QUOTE=gmc]Hi jdong,



No, this is definately not normal. I've had this laptop since January and today is the first time I've ever heard the fan sound like this. I've tracked the problem down to XGL/Compiz. If I start a normal gnome session, the fan doesn't freak out. Since it's only occurring with XGL/Compiz, it's software related. Needless to say, I'll be steering clear of XGL/Compiz for a while. I really don't want to burn out the fan stressing it out like that.

Gord

Edited: As an after thought, maybe the new bios has something to do with it too?[/QUOTE]


ok. fan=hardware controlled. With that in mind, could it be that XGL is such hardware demanding that it makes the fan run hard? thats what im thinking...

---

### Post by gmc on 2006-05-22
HI Angel12,

[QUOTE=angel12]ok. fan=hardware controlled. With that in mind, could it be that XGL is such hardware demanding that it makes the fan run hard? thats what im thinking...[/QUOTE]

I would agree, but the fan is only running insanely hard from the password prompt in gdm until I enter my gnome key ring password. After that it's slows down to normal and remains that way for the rest of the XGL session. When I was ripping/converting a DVD to avi, I pushed the cpu temperature up to 70 degrees cel. and the fan wasn't pushed this hard.

To give you an idea of what I'm talking about, put your ear to the vent and turn on the machine. Now the sound of the fan is about 10 times louder. It's loud enough that I can hear it from across a large room. Very scary.

Gord

Edited: I've tracked the problem to the XGL/Compiz packages in the Dapper repositories. When I installed packages from beerorkid.com and xgl.compiz.info the problem disappears.

---

### Post by jdong on 2006-05-22
Certain builds of Xgl are extremely tough on the graphics card when it initializes... That probably leads to the fan spinning up aggressively, as the video card's power draw exceeds the core duo processor's maximum load by far.

---

### Post by lir on 2006-05-22
[QUOTE=jdong]Certain builds of Xgl are extremely tough on the graphics card when it initializes... That probably leads to the fan spinning up aggressively, as the video card's power draw exceeds the core duo processor's maximum load by far.[/QUOTE]

in windows its possible to turn off other laptop accessories like bluetooth and
wireless or even to remove their drivers (but not necessary) in order to 
conserve the battery. how can i do it the same in linux?
should i just remove the kernel module im loading for wireless/bt/etc?

can the acpi.tar.gz scripts handle that?
i have somq qt/c++ experience. maybe we can come up with a nice gui like
windows have to adjust power savings just like we want it in a more
comfortable fashion.

lir.

---

### Post by jdong on 2006-05-22
[QUOTE=lir]in windows its possible to turn off other laptop accessories like bluetooth and
wireless or even to remove their drivers (but not necessary) in order to 
conserve the battery. how can i do it the same in linux?
should i just remove the kernel module im loading for wireless/bt/etc?

can the acpi.tar.gz scripts handle that?
i have somq qt/c++ experience. maybe we can come up with a nice gui like
windows have to adjust power savings just like we want it in a more
comfortable fashion.

lir.[/QUOTE]

The hardware buttons work just fine. The hardware switch for bluetooth disconnects the bluetooth device from the system virtually. The hardware switch for wifi turns off the radio, which draws by far the most power. Right clicking network manager and unchecking Enable Wireless or Enable Networking [or bringing down the respective interfaces if you don't use n-m] will shut off the wireless, for about an additional 15 minutes of battery life tops.

My scripts try to send the wifi card into max battery saving mode on battery power, which is good enough for me.

Removing the modules really doesn't do much more than this.

---

### Post by lir on 2006-05-22
[QUOTE=jdong]The hardware buttons work just fine. The hardware switch for bluetooth disconnects the bluetooth device from the system virtually. The hardware switch for wifi turns off the radio, which draws by far the most power. Right clicking network manager and unchecking Enable Wireless or Enable Networking [or bringing down the respective interfaces if you don't use n-m] will shut off the wireless, for about an additional 15 minutes of battery life tops.

My scripts try to send the wifi card into max battery saving mode on battery power, which is good enough for me.

Removing the modules really doesn't do much more than this.[/QUOTE]

alright.
well im not counting the hardware buttons for these so just to be clear
to turn off wifi i should just go 'ifconfig eth1 down' and im done?
no need to rmmod any modules or whatever?
what about bt?

---

### Post by jdong on 2006-05-22
Correct.

Bluetooth is more difficult to turn off without using the hardware buttons. I think it involves going into sysfs, finding the driver, and issuing a suspend command to it.

---

### Post by lir on 2006-05-22
[QUOTE=jdong]Correct.

Bluetooth is more difficult to turn off without using the hardware buttons. I think it involves going into sysfs, finding the driver, and issuing a suspend command to it.[/QUOTE]

ok i've been able to get even more time on the laptop (like 15-20 minutes more)
by going into /etc/rc3.d and just disabling some services like S20wifi, S20bluetooth, etc...

I'll put up a full list of them tomorrow when I'm connected from my laptop.

---

### Post by jdong on 2006-05-22
Cool what does that bring your total battery life to?


You can also play with CPU hotplugging via /sys to turn off the 2nd core, and see if that does anything to battery life... It's worth a shot. Note that the PSU does not squeal if one core is turned off.

---

### Post by lir on 2006-05-22
[QUOTE=jdong]Cool what does that bring your total battery life to?


You can also play with CPU hotplugging via /sys to turn off the 2nd core, and see if that does anything to battery life... It's worth a shot. Note that the PSU does not squeal if one core is turned off.[/QUOTE]

what do you mean by " Note that the PSU does not squeal if one core is turned off." ?


Uhmm, right.
So I'll have tomorrow a detailed post once I get back from work I'm gonna
charge it fully and then check.

---

### Post by jdong on 2006-05-22
There is the issue with most of the Core Duo line of laptops (including Macbook Pros, even) where if both CPU's enter the C3 sleep state, the power supply emits this awful high-pitched squeal.

The workaround has always been to disable C3 sleep through max_cstate.

---

### Post by gmc on 2006-05-23
[QUOTE=jdong]Certain builds of Xgl are extremely tough on the graphics card when it initializes... That probably leads to the fan spinning up aggressively, as the video card's power draw exceeds the core duo processor's maximum load by far.[/QUOTE]

Sure looks that way. At least the fan isn't running like the machine wants to liftoff from the desk :-).

Something's been bothering me about setting the way we've been setting the max_cstate. This might have been mentioned and I missed it, but it's a lot easier to install **sysfsutils** and then add the following lines to **/etc/sysfs.conf**

```

devices/system/cpu/cpu0/cpufreq/scaling_governor=ondemand
devices/system/cpu/cpu1/cpufreq/scaling_governor=ondemand
module/processor/parameters/max_cstate=2

```

This will set both processors for ondemand usage and take care of setting the  C3 problem with out adding echo's all over the place.

Just a thought...

Gord

---

### Post by jdong on 2006-05-23
I didn't mention sysfsutils, but that's also a possibility, if you don't mind screeching during bootup until sysfsutils is processed.

---

### Post by lir on 2006-05-23
I haven't checked yet how much more time does it give you but for sure
that its giving at least 20 minutes more.

The files that I've left enabled on /etc/rc3.d are:
lrwxrwxrwx   1 root root   22 2006-05-16 13:11 S01acpi-support -> ../init.d/acpi-support
lrwxrwxrwx   1 root root   17 2006-05-16 13:11 S05vbesave -> ../init.d/vbesave
lrwxrwxrwx   1 root root   15 2006-05-16 13:11 S10acpid -> ../init.d/acpid
lrwxrwxrwx   1 root root   18 2006-05-16 13:11 S10sysklogd -> ../init.d/sysklogd
lrwxrwxrwx   1 root root   15 2006-05-16 13:11 S11klogd -> ../init.d/klogd
lrwxrwxrwx   1 root root   14 2006-05-16 14:30 S12dbus -> ../init.d/dbus
lrwxrwxrwx   1 root root   13 2006-05-16 13:11 S13gdm -> ../init.d/gdm
lrwxrwxrwx   1 root root   14 2006-05-16 13:11 S20apmd -> ../init.d/apmd
lrwxrwxrwx   1 root root   22 2006-05-19 02:29 S20cpufrequtils -> ../init.d/cpufrequtils
lrwxrwxrwx   1 root root   22 2006-05-16 13:11 S20hotkey-setup -> ../init.d/hotkey-setup
lrwxrwxrwx   1 root root   21 2006-05-16 13:11 S20laptop-mode -> ../init.d/laptop-mode
lrwxrwxrwx   1 root root   17 2006-05-16 13:11 S20makedev -> ../init.d/makedev
lrwxrwxrwx   1 root root   23 2006-05-16 13:11 S20nvidia-kernel -> ../init.d/nvidia-kernel
lrwxrwxrwx   1 root root   17 2006-05-16 13:11 S89anacron -> ../init.d/anacron
lrwxrwxrwx   1 root root   13 2006-05-16 13:11 S89atd -> ../init.d/atd
lrwxrwxrwx   1 root root   14 2006-05-16 13:11 S89cron -> ../init.d/cron
lrwxrwxrwx   1 root root   18 2006-05-16 13:11 S99rc.local -> ../init.d/rc.local
lrwxrwxrwx   1 root root   19 2006-05-16 13:11 S99rmnologin -> ../init.d/rmnologin


And the files that I removed are:
lrwxrwxrwx   1 root root   13 2006-05-16 13:11 S14ppp -> ../init.d/ppp
lrwxrwxrwx   1 root root   15 2006-05-16 13:11 S18hplip -> ../init.d/hplip
lrwxrwxrwx   1 root root   16 2006-05-16 13:11 S19cupsys -> ../init.d/cupsys
lrwxrwxrwx   1 root root   18 2006-05-16 13:11 S20festival -> ../init.d/festival
lrwxrwxrwx   1 root root   15 2006-05-16 13:11 S20rsync -> ../init.d/rsync
lrwxrwxrwx   1 root root   20 2006-05-17 17:22 S20wifi-radar -> ../init.d/wifi-radar
lrwxrwxrwx   1 root root   21 2006-05-16 13:11 S25bluez-utils -> ../init.d/bluez-utils
lrwxrwxrwx   1 root root   15 2006-05-16 13:11 S25mdadm -> ../init.d/mdadm
lrwxrwxrwx   1 root root   17 2006-05-16 13:11 S98usplash -> ../init.d/usplash


by the way, as you can see i have still runing 'apmd', 'laptop-mode', and
'cpufrequtils' and 'acpid' -- do i need all of them? 

also, whats vbesave for?

---

### Post by Dralt on 2006-05-23
Hey, I wanted to let you know I am very happy with my recent installation.

I took a break from tweaking my config to mess around with GNOME themes, but everything works OK here.

CPU Frequency Scaling worked fine right from the start without any action on my part. I have to run 2 applets to monitor both cores, but that's OK.

I decided to stick with Network Manager and DHCP.

The latest version of flgrx works great. Even the Control Center applet.

The battery monitor produces accurate estimates.

I still don't have a solution for the memory slots, but I don't really need them.

The system temperature, as shown by the temperature monitor applet says it's between 48C and 53C. I don't know if that's within normal range.

The Device Manager still shows a number of unrecognized devices, but it only bothers the engineer in me. ;)

Now, I just need the theme that thing in a way that looks better than Windows.

---

### Post by jdong on 2006-05-23
[QUOTE=lir]I haven't checked yet how much more time does it give you but for sure
that its giving at least 20 minutes more.

The files that I've left enabled on /etc/rc3.d are:
lrwxrwxrwx   1 root root   22 2006-05-16 13:11 S01acpi-support -> ../init.d/acpi-support
lrwxrwxrwx   1 root root   17 2006-05-16 13:11 S05vbesave -> ../init.d/vbesave
lrwxrwxrwx   1 root root   15 2006-05-16 13:11 S10acpid -> ../init.d/acpid
lrwxrwxrwx   1 root root   18 2006-05-16 13:11 S10sysklogd -> ../init.d/sysklogd
lrwxrwxrwx   1 root root   15 2006-05-16 13:11 S11klogd -> ../init.d/klogd
lrwxrwxrwx   1 root root   14 2006-05-16 14:30 S12dbus -> ../init.d/dbus
lrwxrwxrwx   1 root root   13 2006-05-16 13:11 S13gdm -> ../init.d/gdm
lrwxrwxrwx   1 root root   14 2006-05-16 13:11 S20apmd -> ../init.d/apmd
lrwxrwxrwx   1 root root   22 2006-05-19 02:29 S20cpufrequtils -> ../init.d/cpufrequtils
lrwxrwxrwx   1 root root   22 2006-05-16 13:11 S20hotkey-setup -> ../init.d/hotkey-setup
lrwxrwxrwx   1 root root   21 2006-05-16 13:11 S20laptop-mode -> ../init.d/laptop-mode
lrwxrwxrwx   1 root root   17 2006-05-16 13:11 S20makedev -> ../init.d/makedev
lrwxrwxrwx   1 root root   23 2006-05-16 13:11 S20nvidia-kernel -> ../init.d/nvidia-kernel
lrwxrwxrwx   1 root root   17 2006-05-16 13:11 S89anacron -> ../init.d/anacron
lrwxrwxrwx   1 root root   13 2006-05-16 13:11 S89atd -> ../init.d/atd
lrwxrwxrwx   1 root root   14 2006-05-16 13:11 S89cron -> ../init.d/cron
lrwxrwxrwx   1 root root   18 2006-05-16 13:11 S99rc.local -> ../init.d/rc.local
lrwxrwxrwx   1 root root   19 2006-05-16 13:11 S99rmnologin -> ../init.d/rmnologin


And the files that I removed are:
lrwxrwxrwx   1 root root   13 2006-05-16 13:11 S14ppp -> ../init.d/ppp
lrwxrwxrwx   1 root root   15 2006-05-16 13:11 S18hplip -> ../init.d/hplip
lrwxrwxrwx   1 root root   16 2006-05-16 13:11 S19cupsys -> ../init.d/cupsys
lrwxrwxrwx   1 root root   18 2006-05-16 13:11 S20festival -> ../init.d/festival
lrwxrwxrwx   1 root root   15 2006-05-16 13:11 S20rsync -> ../init.d/rsync
lrwxrwxrwx   1 root root   20 2006-05-17 17:22 S20wifi-radar -> ../init.d/wifi-radar
lrwxrwxrwx   1 root root   21 2006-05-16 13:11 S25bluez-utils -> ../init.d/bluez-utils
lrwxrwxrwx   1 root root   15 2006-05-16 13:11 S25mdadm -> ../init.d/mdadm
lrwxrwxrwx   1 root root   17 2006-05-16 13:11 S98usplash -> ../init.d/usplash


by the way, as you can see i have still runing 'apmd', 'laptop-mode', and
'cpufrequtils' and 'acpid' -- do i need all of them? 

also, whats vbesave for?[/QUOTE]
Of all of those, the ones that could've had an impact are:

(1) bluez-utils: This may activate the bluetooth radio, which would be a power drain.
(2) wifi-radar: That could be sending periodic scan commands
(3) festival: It makes periodic network pings

By far the biggest effect is from bluez-utils, but overall it should not have been too significant an impact on battery life (again, unless bluetooth somehow was not disabled by the HW switch). Background tasks do not use any CPU power. In fact, many of those scripts are one-time actions, not background tasks at all. Perhaps the "20 minutes more" was just fewer actions during bootup, which leads to the battery drain average to be lower at startup, artificially inflating the numbers.

I'm not trying to call you a liar or anything like that ;) but I have a hard time explaining that great a gain in battery life, except the possibility that bluetooth is not properly disabled by the hw switch (blue light off)

---

### Post by gmc on 2006-05-24
Hi Folks,

I see that ipw3945 v1.0.5 is out. I've just compiled and replaced v1.0.3 with it and noticed that I don't seem to be having disconnection/reconnection problems anymore.

Assuming you have the current kernel headers installed, you can simply untar the new driver and compile it with the following command:

**make IEEE80211_INC=/usr/src/linux-headers-`uname -r`/include/**

Since 2.6.15-23 uses the current ieee80211 v1.1.13 drivers, you no longer need to manually compile them (or seperately). Note, you will have to manually copy the newly compiled ipw3945.ko file to the appropriate directory.

Here's a sample of what I did...

```

# Make sure I have everything needed to compile the new driver
apt-get install gcc g++ libc6-dev linux-headers-`uname -r` build-essential debhelper

# Make sure I'm compiling against the correct headers version
ln -s /usr/src/linux-headers-`uname -r` /usr/src/linux

# Uncompress and compile the new driver
tar xvfz ipw3945-1.0.5.tar.gz
cd ipw3945-1.0.5; make IEEE80211_INC=/usr/src/linux/include/

# Make a backup of the original driver, just in case I need it
mv /lib/modules/`uname -r`/kernel/drivers/net/wireless/ipw3945/ipw3945.ko /lib/modules/`uname -r`/kernel/drivers/net/wireless/ipw3945/ipw3945.ko-backup

# Copy the new driver into place
cp /usr/src/ipw3945-1.0.5/ipw3945.ko /lib/modules/`uname -r`/kernel/drivers/net/wireless/ipw3945/ipw3945.ko

# Now reboot and enjoy

```

Gord

---

### Post by lir on 2006-05-24
[QUOTE=jdong]Of all of those, the ones that could've had an impact are:

(1) bluez-utils: This may activate the bluetooth radio, which would be a power drain.
(2) wifi-radar: That could be sending periodic scan commands
(3) festival: It makes periodic network pings

By far the biggest effect is from bluez-utils, but overall it should not have been too significant an impact on battery life (again, unless bluetooth somehow was not disabled by the HW switch). Background tasks do not use any CPU power. In fact, many of those scripts are one-time actions, not background tasks at all. Perhaps the "20 minutes more" was just fewer actions during bootup, which leads to the battery drain average to be lower at startup, artificially inflating the numbers.

I'm not trying to call you a liar or anything like that ;) but I have a hard time explaining that great a gain in battery life, except the possibility that bluetooth is not properly disabled by the hw switch (blue light off)[/QUOTE]


lol cool :)
maybe it's psychological, like I disabled several scripts and figured it'd
make more impact heh

---

### Post by jdong on 2006-05-24
Alright, I've duplicated your startup sequence and note no difference in battery life... Weird.

In other news, new fglrx is out. It adds TV-out, makes firegl-controlpanel work, and fixes a number of stability issues with running multiple X servers and switching in and out of VT's.

To install, use [https://wiki.ubuntu.com/BinaryDriverHowto/ATI](https://wiki.ubuntu.com/BinaryDriverHowto/ATI) and the module-assistant way of installing. I think you'll be surprised how well ATI's installer system works. I know I am. To get the whole list of drivers, which doesn't fit on the screen, move the window up with the mouse by holding ALT and click-dragging the window up.

Enjoy!

---

### Post by lir on 2006-05-25
[QUOTE=jdong]Alright, I've duplicated your startup sequence and note no difference in battery life... Weird.

In other news, new fglrx is out. It adds TV-out, makes firegl-controlpanel work, and fixes a number of stability issues with running multiple X servers and switching in and out of VT's.

To install, use [https://wiki.ubuntu.com/BinaryDriverHowto/ATI](https://wiki.ubuntu.com/BinaryDriverHowto/ATI) and the module-assistant way of installing. I think you'll be surprised how well ATI's installer system works. I know I am. To get the whole list of drivers, which doesn't fit on the screen, move the window up with the mouse by holding ALT and click-dragging the window up.

Enjoy![/QUOTE]

i thought you weren't going for fglrx cause it kills battery life :)
anyway, the newest version i have is 8.24.8, isn't that the newest?

||/ Name                         Version                      Description
+++-============================-============================-========================================================================
ii  xorg-driver-fglrx            6.9.0-8.24.8+2.6.15.9-4      Video driver for ATI graphics accelerators

---

### Post by gmc on 2006-05-25
[QUOTE=lir]i thought you weren't going for fglrx cause it kills battery life :)
anyway, the newest version i have is 8.24.8, isn't that the newest?
[/QUOTE]

Ummm [8.25.18]("https://a248.e.akamai.net/f/674/9206/0/www2.ati.com/drivers/linux/ati-driver-installer-8.25.18-x86.run") is now the current release. ATI released them yesterday :-)

Gord

---

### Post by lir on 2006-05-25
[QUOTE=gmc]Ummm [8.25.18]("https://a248.e.akamai.net/f/674/9206/0/www2.ati.com/drivers/linux/ati-driver-installer-8.25.18-x86.run") is now the current release. ATI released them yesterday :-)

Gord[/QUOTE]

ahh cool
well they're still not on dapper's repos :p
i think ill wait till i can do an apt-get upgrade and ugrade those fglrx drivers

---

### Post by jdong on 2006-05-25
We are under kernel freeze, so Dapper's repositories will not be populated with newer drivers.

Don't worry, though...ATI drivers were very smooth to install, unlike NVidia drivers...

---

### Post by gmc on 2006-05-25
[QUOTE=jdong]We are under kernel freeze, so Dapper's repositories will not be populated with newer drivers.

Don't worry, though...ATI drivers were very smooth to install, unlike NVidia drivers...[/QUOTE]

I don't know about that.... check this out!

```

May 25 10:24:50 badokami kernel: [4295399.804000] [fglrx:firegl_pcie_lock_pages] *ERROR* unlocking pcie memory !
May 25 10:24:50 badokami kernel: [4295399.804000] [fglrx:firegl_pcie_lock_pages] *ERROR* unlocking memory at 0xf5442780
for 172032 bytes
May 25 10:24:50 badokami kernel: [4295399.805000] [fglrx:firegl_pcie_lock_pages] *ERROR* locking memory at 0xab188000 for 688128 bytes
May 25 10:24:50 badokami kernel: [4295399.807000] [fglrx:firegl_pcie_lock_pages] *ERROR* unlocking pcie memory !
May 25 10:24:50 badokami kernel: [4295399.807000] [fglrx:firegl_pcie_lock_pages] *ERROR* unlocking memory at 0xf5442740
for 688128 bytes
May 25 10:24:50 badokami kernel: [4295399.808000] [fglrx:firegl_pcie_lock_pages] *ERROR* locking memory at 0xab168000 for 819200 bytes
May 25 10:24:50 badokami kernel: [4295399.811000] [fglrx:firegl_pcie_lock_pages] *ERROR* unlocking pcie memory !
May 25 10:24:50 badokami kernel: [4295399.811000] [fglrx:firegl_pcie_lock_pages] *ERROR* unlocking memory at 0xf5442700
for 819200 bytes

```

My /var/log/syslog file is full of reports like this.. I'm not sure what to make of it as there's been no visual problems with the new driver.

Gord

Edited: I just tried jdong's xorg.conf and am still getting the same sort of errors, so I'm pretty sure it wasn't my xorg.conf file.

```

gord@badokami:~$ fglrxinfo
Xlib:  extension "XFree86-DRI" missing on display ":1.0".
display: :0.0  screen: 0
OpenGL vendor string: ATI Technologies Inc.
OpenGL renderer string: ATI Mobility Radeon X1400 Generic
OpenGL version string: 2.0.5814 (8.25.18)

```

so the driver is being recognized ok.

Update: it's XGL/Compiz that's doing it :-(

---

### Post by samir85 on 2006-05-25
[QUOTE=gmc]Hi Folks,

I see that ipw3945 v1.0.5 is out. I've just compiled and replaced v1.0.3 with it and noticed that I don't seem to be having disconnection/reconnection problems anymore.

Assuming you have the current kernel headers installed, you can simply untar the new driver and compile it with the following command:

**make IEEE80211_INC=/usr/src/linux-headers-`uname -r`/include/**

Since 2.6.15-23 uses the current ieee80211 v1.1.13 drivers, you no longer need to manually compile them (or seperately). Note, you will have to manually copy the newly compiled ipw3945.ko file to the appropriate directory.

Here's a sample of what I did...

```

# Make sure I have everything needed to compile the new driver
apt-get install gcc g++ libc6-dev linux-headers-`uname -r` build-essential debhelper

# Make sure I'm compiling against the correct headers version
ln -s /usr/src/linux-headers-`uname -r` /usr/src/linux

# Uncompress and compile the new driver
tar xvfz ipw3945-1.0.5.tar.gz
cd ipw3945-1.0.5; make IEEE80211_INC=/usr/src/linux/include/

# Make a backup of the original driver, just in case I need it
mv /lib/modules/`uname -r`/kernel/drivers/net/wireless/ipw3945/ipw3945.ko /lib/modules/`uname -r`/kernel/drivers/net/wireless/ipw3945/ipw3945.ko-backup

# Copy the new driver into place
cp /usr/src/ipw3945-1.0.5/ipw3945.ko /lib/modules/`uname -r`/kernel/drivers/net/wireless/ipw3945/ipw3945.ko

# Now reboot and enjoy

```

Gord[/QUOTE]

Thanks, works like a charm. Even some idiot was able to follow these instructions :D

btw: are you sure that those random disconnects are caused by the ipw3945 1.0.3 driver. In the changelogs of the 1.0.4 and 1.0.5 driver, I couldn't find a passage, that this issue has been fixed.

---

### Post by jdong on 2006-05-25
Those fglrx kernel messages are 'normal', it seems to show up whenever something 3D accelerated is initialized and torn down, with both fglrx releases. There are no visual consequences, though, so I'm ignoring them :)


Has anyone confirmed TV out to be working yet? I don't have a S-Video cable handy.

---

### Post by gmc on 2006-05-25
Hi Samir,

[QUOTE=samir85]Thanks, works like a charm. Even some idiot was able to follow these instructions :D

btw: are you sure that those random disconnects are caused by the ipw3945 1.0.3 driver. In the changelogs of the 1.0.4 and 1.0.5 driver, I couldn't find a passage, that this issue has been fixed.[/QUOTE]

:-) Thanks, glad they work.

As for the disconnects, no I'm not 100% but I've been connected since yesterday morning and haven't had one since.

Gord

---

### Post by gmc on 2006-05-25
Hi jdong,

[QUOTE=jdong]Those fglrx kernel messages are 'normal', it seems to show up whenever something 3D accelerated is initialized and torn down, with both fglrx releases. There are no visual consequences, though, so I'm ignoring them :)
[/QUOTE]

Really! I never noticed them with compiz and the 8.24 driver. weird.

Gord

---

### Post by samir85 on 2006-05-25
[QUOTE=gmc]Hi Samir,



:-) Thanks, glad they work.

As for the disconnects, no I'm not 100% but I've been connected since yesterday morning and haven't had one since.

Gord[/QUOTE]

I also had those disconnects with the 1.0.3 driver (with the old pre 1 driver those disconnects didn't occur). Thus, I created a bug report on Malone. Maybe those people of who are experiencing the same issue, can confirm the bug. So we can increase the chance that the 1.0.5 driver gets integrated before Dapper is released.

Here's the link:
[https://launchpad.net/distros/ubuntu/+source/linux-source-2.6.15/+bug/46601](https://launchpad.net/distros/ubuntu/+source/linux-source-2.6.15/+bug/46601)

---

### Post by samir85 on 2006-05-25
Hey, I just came home and wireless is gone nuts (using ipw3945 v1.0.5 driver).

I can't connect to my wlan anymore (it's wpa protected). Network-Manager properly detects my wlan and then I try to connect to it. But it doesn't get connected, the status remains at "connecting" for around 5 minutes and then it stops trying.

Here's the relevant part of my dmesg output:

```
[4294706.536000] ipw3945: Detected geography ABG (13 802.11bg channels, 23 802.11a channels)
[4294707.690000] Bluetooth: Core ver 2.8
[4294707.690000] NET: Registered protocol family 31
[4294707.690000] Bluetooth: HCI device and connection manager initialized
[4294707.690000] Bluetooth: HCI socket layer initialized
[4294707.715000] Bluetooth: L2CAP ver 2.8
[4294707.715000] Bluetooth: L2CAP socket layer initialized
[4294707.820000] Bluetooth: RFCOMM socket layer initialized
[4294707.820000] Bluetooth: RFCOMM TTY layer initialized
[4294707.820000] Bluetooth: RFCOMM ver 1.7
[4294718.908000] NET: Registered protocol family 10
[4294718.908000] lo: Disabled Privacy Extensions
[4294718.908000] ADDRCONF(NETDEV_UP): eth0: link is not ready
[4294718.908000] ADDRCONF(NETDEV_UP): eth1: link is not ready
[4294718.908000] IPv6 over IPv4 tunneling driver
[4294726.786000] ipw3945: Detected geography ABG (13 802.11bg channels, 23 802.11a channels)
[4294733.293000] NET: Registered protocol family 17
[4294740.670000] ipw3945: Detected geography ABG (13 802.11bg channels, 23 802.11a channels)
[4294748.287000] ipw3945: Detected geography ABG (13 802.11bg channels, 23 802.11a channels)
[4294755.906000] ipw3945: Detected geography ABG (13 802.11bg channels, 23 802.11a channels)
[4294763.525000] ipw3945: Detected geography ABG (13 802.11bg channels, 23 802.11a channels)
[4294771.141000] ipw3945: Detected geography ABG (13 802.11bg channels, 23 802.11a channels)
[4294778.760000] ipw3945: Detected geography ABG (13 802.11bg channels, 23 802.11a channels)
[4294786.380000] ipw3945: Detected geography ABG (13 802.11bg channels, 23 802.11a channels)
[4294793.997000] ipw3945: Detected geography ABG (13 802.11bg channels, 23 802.11a channels)
[4294801.611000] ipw3945: Detected geography ABG (13 802.11bg channels, 23 802.11a channels)
[4294809.229000] ipw3945: Detected geography ABG (13 802.11bg channels, 23 802.11a channels)
[4294816.847000] ipw3945: Detected geography ABG (13 802.11bg channels, 23 802.11a channels)
[4294824.467000] ipw3945: Detected geography ABG (13 802.11bg channels, 23 802.11a channels)
[4294832.083000] ipw3945: Detected geography ABG (13 802.11bg channels, 23 802.11a channels)
[4294839.700000] ipw3945: Detected geography ABG (13 802.11bg channels, 23 802.11a channels)
[4294847.318000] ipw3945: Detected geography ABG (13 802.11bg channels, 23 802.11a channels)
[4294854.938000] ipw3945: Detected geography AB/G (13 802.11bg channels, 23 802.11a channels)

```

I wonder why this is happening, because just a few hours ago wlan worked fine the 1.0.5 drivers.


 **EDIT**

Ok, I solved the issue by adding ipw3945 to /etc/modules.

Just to get a better understanding. Can somebody explain why I have to add this module to /etc/modules, even though it already resides in /etc/modprobe.d ?

---

### Post by Dralt on 2006-05-26
[QUOTE=jdong]Alright, I've duplicated your startup sequence and note no difference in battery life... Weird.

In other news, new fglrx is out. It adds TV-out, makes firegl-controlpanel work, and fixes a number of stability issues with running multiple X servers and switching in and out of VT's.

To install, use [https://wiki.ubuntu.com/BinaryDriverHowto/ATI](https://wiki.ubuntu.com/BinaryDriverHowto/ATI) and the module-assistant way of installing. I think you'll be surprised how well ATI's installer system works. I know I am. To get the whole list of drivers, which doesn't fit on the screen, move the window up with the mouse by holding ALT and click-dragging the window up.

Enjoy![/QUOTE]

So, it worked fine, eh?

My system works right now. I don't know if I should wait or upgrade.

Did you guys fix the volume control thing?

I can switch between PCM and Front in the volume control applet, but I can't push the volume very high. Even with headphones, it's not that loud at full volume.

Any idea if this is normal?

---

### Post by Dralt on 2006-05-26
[QUOTE=jdong]Alright, I've duplicated your startup sequence and note no difference in battery life... Weird.

In other news, new fglrx is out. It adds TV-out, makes firegl-controlpanel work, and fixes a number of stability issues with running multiple X servers and switching in and out of VT's.

To install, use [https://wiki.ubuntu.com/BinaryDriverHowto/ATI](https://wiki.ubuntu.com/BinaryDriverHowto/ATI) and the module-assistant way of installing. I think you'll be surprised how well ATI's installer system works. I know I am. To get the whole list of drivers, which doesn't fit on the screen, move the window up with the mouse by holding ALT and click-dragging the window up.

Enjoy![/QUOTE]

Hey, did you select the 6.06 package or the dapper package?

---

### Post by samsaga2 on 2006-05-26
I've read all the posts but nobody seems have the same problem than me. I cannot install the last Drapper because installation hungs at 80%.

Fedora Core 5 installation is ok but I have to disable pcmcia to boot the system (but I prefer Ubuntu :P).

---

### Post by angel12 on 2006-05-26
i tried fedora, but ive been babied so much with ubuntu's package management, thats why i love it so much lol. i had the same prob with fedora though, i figured they would have fixed that. but anyways, what disk are you using to install dapper? is it scratched? try burning another, or re-downloading it

---

### Post by lir on 2006-05-26
I know this is a bit unrelated, being in ubuntu forums but I just have to be sure...
I've connected an SVIDEO-RCA cable from the laptop to my TV and set it on AV 
mode (worked fine before with my desktop box) - While on Windows XP if I press
Fn-F5 which is supposed to toggle between the display I'm not seeing anything
on my TV.... I've tried rebooting with the cable plugged cause I figured it'll recognize
it on boot and show me the desktop on the TV set but again no...

So while we're at it- has anyone tested it before?
And the obviouse question- how do i get TV out to work with linux? :P

Thanks.

---

### Post by lir on 2006-05-26
[QUOTE=jdong]Those fglrx kernel messages are 'normal', it seems to show up whenever something 3D accelerated is initialized and torn down, with both fglrx releases. There are no visual consequences, though, so I'm ignoring them :)


Has anyone confirmed TV out to be working yet? I don't have a S-Video cable handy.[/QUOTE]


Tell me how to configure it and I'll confirm :)

---

### Post by gmc on 2006-05-26
[QUOTE=samsaga2]I've read all the posts but nobody seems have the same problem than me. I cannot install the last Drapper because installation hungs at 80%.

Fedora Core 5 installation is ok but I have to disable pcmcia to boot the system (but I prefer Ubuntu :P).[/QUOTE]

To be honest, it sounds like it might be a bad download or burn. Have you tried booting the CD and run the self test?

Gord

---

### Post by samsaga2 on 2006-05-26
I will try download Ubuntu again.

---

### Post by #bash on 2006-05-26
Hi there,

I would like to download the latest **Ubuntu 6.06 LTS (Dapper Drake) Release Candidate** and I'm not sure which version will be suitable for this notebook.

**PC (Intel x86) desktop CD** or **64-bit PC (AMD64) desktop CD**?

Thanks for reply

---

### Post by nolongerlivecd on 2006-05-26
It's not 64-bit yet.

---

### Post by #bash on 2006-05-26
[http://se.releases.ubuntu.com/6.06/](http://se.releases.ubuntu.com/6.06/) :confused:

---

### Post by Kurt_S on 2006-05-26
Hi people,

I installed Suse 10.1 on my Aspire 5672 along with the latest ATI driver. Unfortunately all I see is an ugly colored screen. I tried the xorg.conf I found in this thread and the one from [http://www.dicianno.org/acer-aspire-5670-v-gentoo](http://www.dicianno.org/acer-aspire-5670-v-gentoo). What am I doing wrong?

Kurt

---

### Post by angel12 on 2006-05-26
ive been wondering about the volume up keys and our problem with them only controlling pcm. there has got to be some kind of config file that tells the buttons to control the first mixer channel in also, so why cant we just change that to use the "front" channel? any takers? ive been out of the loop on linux for a while now, so i wont be much help, but i would love to see this fixed.

---

### Post by jdong on 2006-05-26
angel12, see the following two bug reports about this:

[https://launchpad.net/distros/ubuntu/+source/linux-source-2.6.15/+bug/45167](https://launchpad.net/distros/ubuntu/+source/linux-source-2.6.15/+bug/45167)

[https://launchpad.net/products/gnome-media/+bug/45345](https://launchpad.net/products/gnome-media/+bug/45345)

---

### Post by Dralt on 2006-05-26
Unfortunately, I still haven't found a solution for the weak sound output...Even at maximum volume, I can barely hear DVD playback.

---

### Post by Dralt on 2006-05-27
I found the driver for the Realtek HD Audio chipset...

[ftp://61.56.86.122/pc/hda/alc880d/realtek-linux-audiopack-4.02.tar.bz2](ftp://61.56.86.122/pc/hda/alc880d/realtek-linux-audiopack-4.02.tar.bz2)

Not sure how to install it, though.

---

### Post by #bash on 2006-05-27
OK, I'm almost convinced that the best solution for this notebook will be 32 bit distribution.
However I'm confused, because some dudes told me that KDE is faster than Gnome on Core Duo machines. Is it true? Because I don't know, whether Kubuntu will work properly on this Acer? Is there anyone who works on Kubuntu or everyone is a Ubuntu-developer? And maybe you will encourage me to download regular Ubuntu? Or maybe both of them ;)

I look forward to hearing from you folks :cool:

---

### Post by angel12 on 2006-05-27
#bash, our laptops are not 64bit. so yes. 32bit. and the kde vs gnome debate, well, its what you prefer.

---

### Post by jdong on 2006-05-27
Attached (hah, aren't you proud of me? I actually remember to attach it the FIRST time) is an updated acpi.tar.gz... Contains a fix for those using the new fglrx and frequency changing (since aticonfig --lsp now puts a star next to the active state, we need to use a different algorithm to detect powerstates)

Only fglx-powercontrol.sh has changed.

---

### Post by angel12 on 2006-05-28
jdong, so i tried using your /etc/acpi folder, and now when i try to suspend it just restarts the x server. hibernate does the same thing. then when i try to log in, it hangs. any ideas? It also does this when i try to switch to a virtual terminal, ctrl+alt+F1

---

### Post by lir on 2006-05-28
Guys, I'm lost and I need some guidance.
On Windows I couldn't get the TV-OUT to work - I just didn't see anything
on my TV screen, even after doing an upgrade to the ATI Catalyst and driver 
software. 

What steps are required to do in order to make TV-OUT work in linux?


Thanks.

---

### Post by angel12 on 2006-05-28
[QUOTE=lir]Guys, I'm lost and I need some guidance.
On Windows I couldn't get the TV-OUT to work - I just didn't see anything
on my TV screen, even after doing an upgrade to the ATI Catalyst and driver 
software. 

What steps are required to do in order to make TV-OUT work in linux?


Thanks.[/QUOTE]

right click on desktop, properties, settings, then right click on the little blue square with the number 2 in it and click attached, then hit apply. that should do it. for some reason it wasnt working the other day for me though.

---

### Post by lir on 2006-05-28
[QUOTE=angel12]right click on desktop, properties, settings, then right click on the little blue square with the number 2 in it and click attached, then hit apply. that should do it. for some reason it wasnt working the other day for me though.[/QUOTE]


God damn stupid TV.
Sorry for the language, but it seems that it was the front video-in RCA input
that was malfunctioning cause I was like - "no way this doesnt work" when
I tried a 2nd cable from a friend, so I tried the back video inputs and it works 
just fine.

Thanks for all the help and clearing that out.


To make this work on linux I have found from ATI's man page that I'd need
a directive something like "Option ForceMonitors crt1,tv". Is that the only way
or can I do it on-demand somehow?

---

### Post by angel12 on 2006-05-29
[QUOTE=lir]God damn stupid TV.
Sorry for the language, but it seems that it was the front video-in RCA input
that was malfunctioning cause I was like - "no way this doesnt work" when
I tried a 2nd cable from a friend, so I tried the back video inputs and it works 
just fine.

Thanks for all the help and clearing that out.


To make this work on linux I have found from ATI's man page that I'd need
a directive something like "Option ForceMonitors crt1,tv". Is that the only way
or can I do it on-demand somehow?[/QUOTE]

i think the ati control panel might do it for you, ive never played with tv-out in linux before.

---

### Post by gmc on 2006-05-29
Morning Folks,

As you may or may not know, the Dev's released a new copy of restricted-modules this morning. The has the unfortunate side effect of breaking things if you had previously installed the 8.25.18 fglrx drivers using ATI's package. Here's how to fix things so that you can use the newly included drivers.

```

# Disable the fglrx driver that was installed via **_ati-driver-installer-8.25.18-x86.run_**
sudo mv /lib/modules/`uname -r`/misc/fglrx.ko /lib/modules/`uname -r`/misc/fglrx.ko-backup

# Make sure the system see's the new fglrx 8.25.18 driver which is now
# included in the new restricted-modules package 
sudo depmod -a

# Make sure the system loads the fgrlx driver when booting
sudo echo "fglrx" >> /etc/modules

# You're good to go, now reboot.

```

Gord

---

### Post by jdong on 2006-05-29
Yep, a new l-r-m with latest ATI drivers has been uploaded, but kernel modules will conflict (i.e. the manually installed ones always override linux-restricted-modules)

I hope Edgy gets a better packaging system for kernel modules (such as Fedora/SUSE's separate kmod-nvidia/kmod-fglrx packages for each module) so that it's easier for 3rd parties to work with us.

---

### Post by lir on 2006-05-29
Hey guys, sorry to bother you again with laptop problems
instead of linux problems....

I'm noticing since last night that when my laptop is connected to AC
it doesn't charge the battery... the battery is kept on 27% no matter if 
the laptop is just sitting there doing nothing, it's just not charging...
Does anyone have an explanation for this phenoma?


By the way, I booted to windows just to make sure and it's the same thing...
The AC is ofcourse connected and it's running on AC but the battery isn't charged, it's kept on 27%.


Thanks guys.

---

### Post by lir on 2006-05-30
[QUOTE=lir]Hey guys, sorry to bother you again with laptop problems
instead of linux problems....

I'm noticing since last night that when my laptop is connected to AC
it doesn't charge the battery... the battery is kept on 27% no matter if 
the laptop is just sitting there doing nothing, it's just not charging...
Does anyone have an explanation for this phenoma?


By the way, I booted to windows just to make sure and it's the same thing...
The AC is ofcourse connected and it's running on AC but the battery isn't charged, it's kept on 27%.


Thanks guys.[/QUOTE]


Ok with all that said, I managed to get it to work again more or less.
I took out the battery and put it in again, after that it charged it... kinda weird.

---

### Post by lir on 2006-05-31
Has anyone else encountered this issue of a none-accurate battery monitor
from gnome's panel?

After 30 minutes I'm getting messages telling me that the battery is left with 1%
and a minute later it's jumping back to 50-something% with 1 hour and 20 minutes
more of battery life.

---

### Post by jdong on 2006-05-31
I have seen it momentarily spike to 1 minute right after unplugging power.

---

### Post by scifan on 2006-06-01
I can't say as I've experienced that as yet...

So, with much thanks to jdong and Gord, I've got linux installed (after receiving my replacement 5672) and dang, this rocks!

Gord - did you get WPA working happily?

I have to specify a static IP for my wpa wireless connection, and found this link to be very useful for how to get wpa_supplicant happy under dapper:
[http://svn.debian.org/wsvn/pkg-wpa/trunk/wpasupplicant/debian/README.modes?op=file&rev=0&sc=0](http://svn.debian.org/wsvn/pkg-wpa/trunk/wpasupplicant/debian/README.modes?op=file&rev=0&sc=0)

Note that the device driver for wpa_supplicant should be wext... not ipw... (spent a bit of time before I discovered that)

VPN connectivity is my next task... That's got to happen before I can fully move away from Windows...

---

### Post by gmc on 2006-06-01
Hi Scifan,

[QUOTE=scifan]I can't say as I've experienced that as yet...

So, with much thanks to jdong and Gord, I've got linux installed (after receiving my replacement 5672) and dang, this rocks!

Gord - did you get WPA working happily?

I have to specify a static IP for my wpa wireless connection, and found this link to be very useful for how to get wpa_supplicant happy under dapper:
[http://svn.debian.org/wsvn/pkg-wpa/trunk/wpasupplicant/debian/README.modes?op=file&rev=0&sc=0](http://svn.debian.org/wsvn/pkg-wpa/trunk/wpasupplicant/debian/README.modes?op=file&rev=0&sc=0)

Note that the device driver for wpa_supplicant should be wext... not ipw... (spent a bit of time before I discovered that)

VPN connectivity is my next task... That's got to happen before I can fully move away from Windows...[/QUOTE]

As a matter of fact, I did get WPA working. I noticed you mentioned that you can't connect unless you specify a static IP. Assuming you're router is setup for DHCP, I found that I didn't have to edit anything in /etc/wpa_supplicant/wpa_supplicant.conf -- though my router is not hiding it's essid name. From what I understand, you would need to create an entry in wpa_supplicant.conf if you do.

Great to hear things are finally working for you! Happy Dapper Day :-)

Gord

---

### Post by scifan on 2006-06-01
[QUOTE=gmc]Hi Scifan,



As a matter of fact, I did get WPA working. I noticed you mentioned that you can't connect unless you specify a static IP. Assuming you're router is setup for DHCP, I found that I didn't have to edit anything in /etc/wpa_supplicant/wpa_supplicant.conf -- though my router is not hiding it's essid name. From what I understand, you would need to create an entry in wpa_supplicant.conf if you do.

Great to hear things are finally working for you! Happy Dapper Day :-)

Gord[/QUOTE]

yeah, the router has DHCP enabled, but there is a known problem with d-link DI-624's... dhcp doesn't work on WPA connected Wireless connections... so you can either have crappy security (WEP) and DHCP ip assignement or you can have decent security w/ statically assigned IP's..

---

### Post by gmc on 2006-06-02
[QUOTE=scifan]yeah, the router has DHCP enabled, but there is a known problem with d-link DI-624's... dhcp doesn't work on WPA connected Wireless connections... so you can either have crappy security (WEP) and DHCP ip assignement or you can have decent security w/ statically assigned IP's..[/QUOTE]

Ouch! Given the choice, I'd go with static IP and better security. Of course I'm pretty paranoid

Gord

---

### Post by outofsync on 2006-06-04
Hi,

I'm planning to buy this 5672WLMI laptop, but I first need to install Breezy on it, and I'll be using Breezy for a few weeks, because of a long story that it's not worth mentioning here. After a month or so, I believe I'll be able to update to Dapper.

By reading the beginning of this thread, it seems some people was able to install Breezy on it, and the only problems were networking and the X1400.

Is that correct? Do you believe I'll be able to install Breezy on it?

I can live without networking during this month, because I've everything burnt in DVD, so, networking won't be a problem. 

The X1400 is another story, because I _NEED_ accelerated 3D, but I suppose I can install a recent version of ATI drivers (with X1xxx support) on Breezy, or maybe not?

thanks!

---

### Post by gmc on 2006-06-04
[QUOTE=outofsync]Hi,

I'm planning to buy this 5672WLMI laptop, but I first need to install Breezy on it, and I'll be using Breezy for a few weeks, because of a long story that it's not worth mentioning here. After a month or so, I believe I'll be able to update to Dapper.

By reading the beginning of this thread, it seems some people was able to install Breezy on it, and the only problems were networking and the X1400.

Is that correct? Do you believe I'll be able to install Breezy on it?

I can live without networking during this month, because I've everything burnt in DVD, so, networking won't be a problem. 

The X1400 is another story, because I _NEED_ accelerated 3D, but I suppose I can install a recent version of ATI drivers (with X1xxx support) on Breezy, or maybe not?

thanks![/QUOTE]

Breezy on the 5672, sure it works, however you're going to find the chicken and the egg scenario. 

The Breezy CD does not install the full GCC compiler and since there will be no network available, you'll have no way to get it. Thus with no compiler, you won't be able to build the ATI native install drivers and so no accelerated video support.

You might be able to over come this problem if you use the DVD version of Breezy though.

Really I wouldn't recommend going the Breezy route, You'll have better luck with Dapper.

Gord

---

### Post by outofsync on 2006-06-04
[QUOTE=gmc]You might be able to over come this problem if you use the DVD version of Breezy though.
[/QUOTE]
Yes, I've Breezy Main, Universe, and Multiverse, in DVD. I've installed a complete Breezy development environment in several machines that didn't have access to Internet (because of security reasons).

So, if I can install Breezy on the Aspire 5672, I should be able to install all the needed packages for compiling the ATI driver.

Might I encounter more things that don't work, apart from networking?

---

### Post by jdong on 2006-06-04
Sound might also be a trouble spot... Intel HDA support in breezy's kernel is spotty. I don't know how much luck you'll have with installing wireless drivers with Breezy's kernel, as ipw3945 requires some features that are new to kernel 2.6.15.

---

### Post by gmc on 2006-06-04
[QUOTE=outofsync]Yes, I've Breezy Main, Universe, and Multiverse, in DVD. I've installed a complete Breezy development environment in several machines that didn't have access to Internet (because of security reasons).

So, if I can install Breezy on the Aspire 5672, I should be able to install all the needed packages for compiling the ATI driver.

Might I encounter more things that don't work, apart from networking?[/QUOTE]

Not that I can think of, but then again your entering uncharted territory. I'll keep me fingers crossed for you.

Gord

---

### Post by gmc on 2006-06-04
[QUOTE=jdong]Sound might also be a trouble spot... Intel HDA support in breezy's kernel is spotty. I don't know how much luck you'll have with installing wireless drivers with Breezy's kernel, as ipw3945 requires some features that are new to kernel 2.6.15.[/QUOTE]

Funnily enough that was one thing that I didn't have problems with. Sound worked out of the box with Breezy.

Gord

---

### Post by outofsync on 2006-06-04
OK, if possible, I'll try to install Dapper from the beginning. Otherwise, I'll go the Breezy path.

One more thing: Is this a good quality laptop? Did you heard of people getting a 5672 with defective hardware? (I'm buying this laptop because of the hardware problems of the MacBook Pro --my software compiles on OSX too, but I need a reliable laptop, and I need it now, so I can't wait for a new revision of the MacBook Pro-- )

Thanks for all your comments, they've been very helpful for my decision.

---

### Post by gmc on 2006-06-04
[QUOTE=outofsync]OK, if possible, I'll try to install Dapper from the beginning. Otherwise, I'll go the Breezy path.

One more thing: Is this a good quality laptop? Did you heard of people getting a 5672 with defective hardware? (I'm buying this laptop because of the hardware problems of the MacBook Pro --my software compiles on OSX too, but I need a reliable laptop, and I need it now, so I can't wait for a new revision of the MacBook Pro-- )

Thanks for all your comments, they've been very helpful for my decision.[/QUOTE]

The only 5672 that I know of with any problem is SciFan's (I think, I can't find the message in this thread now). He returned/replaced his due to excessive heat on the right hand of the touchpad (btw folks, that's where the X1400 chip lives). Other than that... you've decided to get a really nice piece of equipment.

Gord

---

### Post by jdong on 2006-06-04
[QUOTE=outofsync]OK, if possible, I'll try to install Dapper from the beginning. Otherwise, I'll go the Breezy path.

One more thing: Is this a good quality laptop? Did you heard of people getting a 5672 with defective hardware? (I'm buying this laptop because of the hardware problems of the MacBook Pro --my software compiles on OSX too, but I need a reliable laptop, and I need it now, so I can't wait for a new revision of the MacBook Pro-- )

Thanks for all your comments, they've been very helpful for my decision.[/QUOTE]
I am pleased with the overall quality of the laptop. Construction is sturdy yet lightweight and portable. The choice of hardware (mostly Intel chips as dictated by the Centrino standards) is sound.

Speaking of sounds, if you're looking to escape the infamous "whine", don't bother. It's a problem that's nearly ubiquitous with the Core Duos (due to their unusually low power consumption while idle). Fortunately, if you've read through this thread, you'll see that with Linux it's pretty easy to lock out "Deeper Sleep" to eliminate the noise for good. Under Windows, the nice convenient USB bug prevents Deeper Sleep, effectively stopping the bug before it starts.


In my opinion, you can't beat the hardware quality/reliability of Apple, but your wallet feels the pain if you choose that path. The Macbook was my 2nd choice, but the same $1100 on a macbook will get you so much less in terms of disk and RAM that it was not worth the investment. I've learned not to spend any more than this much on hardware because of how fast technology is moving nowadays. Spend $2000 on a MacBook Pro, and I'll still guarantee you that in 6 months, there will be a Core 2 or Core 3 laptop that costs much less than your MBP but outperforms it. Was it worth the initial investment? I'd say unless you have something that demands that level of performance/reliability, save half your money for your next purchase ;). Buy cheap, buy often :)

---

### Post by #bash on 2006-06-04
Heh, I have this laptop for 4 days and I'm really satisfied.
It is quite quiet 8) and light, however the charger is a lil bit too heavy.
Of caurse, the first thing I've done, was repartitioning and throwing XP Home Edition away. Afterwards I've installed XP Pro and new Dapper :) 
Moreover the quality of the camera is pretty good.

---

### Post by jdong on 2006-06-04
I'd like to comment a bit on the heat. Now that the weather's been warming up around here, heat is a bit more noticeable. The fan is on (usually at a low and acceptable level) the majority of time in my 80-degree F room. There is warmth in the area where my right palm rests (right over the video card) and also on the touchpad, but both are quite acceptable. The underside's heat is not unbearably bad, but will leave you sweating a bit if you have the laptop on your lap for a few hours. In comparison the other laptops I have experienced (Toshiba Celeron M 340, Dell PIII 700MHz, Compaq P3 500MHz, Dell Precision Core Duo 2.16, MacBook Pro) there is nothing out of the ordinary with this laptop's heat level.


The heat level is greatly minimized by clocking down the video card to the lowest settings. I recommend making some launcher icons on your panel that use aticonfig to set powerstate (I have Low and High buttons). I find myself operating my laptop primarily on the lowest graphics setting, both AC and battery. It's more than adequate for all "business/desktop" graphics tasks (think of GeForce4 MX440 or Intel GMA950 performance) while being power efficient. The only time I clock up is right before gaming.

---

### Post by plaz42 on 2006-06-05
Has anyone with this laptop had issues playing DVDs?  I have an Aspire 5670 running Dapper and KDE, and I cannot get any DVDs to play.  I have installed libdvdread and libdvdcss, but I always get errors cracking the CSS key.  My output from running ogle is as follows:

```
libdvdread: Using libdvdcss version 1.2.5 for DVD access
libdvdread: Using libdvdcss version 1.2.5 for DVD access

libdvdread: Attempting to retrieve all CSS keys
libdvdread: This can take a _long_ time, please be patient

libdvdread: Get key for /VIDEO_TS/VIDEO_TS.VOB at 0x0000013c
libdvdread: Elapsed time 1
libdvdread: Get key for /VIDEO_TS/VTS_01_0.VOB at 0x0000038e
libdvdread: Elapsed time 0
libdvdread: Get key for /VIDEO_TS/VTS_01_1.VOB at 0x00000532
libdvdread: Elapsed time 0
libdvdread: Get key for /VIDEO_TS/VTS_02_0.VOB at 0x0038fd18
libdvdread: Elapsed time 0
libdvdread: Get key for /VIDEO_TS/VTS_02_1.VOB at 0x0038febc
libdvdread: Elapsed time 1
libdvdread: Get key for /VIDEO_TS/VTS_03_0.VOB at 0x003917dd
libdvdread: Elapsed time 0
libdvdread: Get key for /VIDEO_TS/VTS_03_1.VOB at 0x00391981
libdvdread: Elapsed time 0
libdvdread: Get key for /VIDEO_TS/VTS_04_0.VOB at 0x00392b33
libdvdread: Elapsed time 0
libdvdread: Get key for /VIDEO_TS/VTS_04_1.VOB at 0x00397f71
libdvdread: Error cracking CSS key for /VIDEO_TS/VTS_04_1.VOB (0x00397f71)!!
libdvdread: Elapsed time 0
libdvdread: Get key for /VIDEO_TS/VTS_05_0.VOB at 0x00397f8c
libdvdread: Elapsed time 0
libdvdread: Get key for /VIDEO_TS/VTS_05_1.VOB at 0x00398130
libdvdread: Elapsed time 0
libdvdread: Get key for /VIDEO_TS/VTS_06_0.VOB at 0x0039814d
libdvdread: Elapsed time 0
libdvdread: Get key for /VIDEO_TS/VTS_06_1.VOB at 0x003982f1
libdvdread: Elapsed time 0
libdvdread: Found 6 VTS's
libdvdread: Elapsed time 2
xscreensaver-command not found.
WARNING[ogle_mpeg_ps]: dvdreadblocks only got 1, wanted 240
FATAL[ogle_mpeg_ps]: dvdreadblocks failed
ctrl: ipc_rmid: Invalid argument

```

Any help would be greatly appreciated.

---

### Post by jdong on 2006-06-06
Since the DVD drive is on the SATA bus, keys cannot be sniffed out the traditional ways. You need to set "CSS_METHOD=title" in /etc/environment .

---

### Post by Frank Golden on 2006-06-06
[QUOTE=plaz42]Has anyone with this laptop had issues playing DVDs?  I have an Aspire 5670 running Dapper and KDE, and I cannot get any DVDs to play.  I have installed libdvdread and libdvdcss, but I always get errors cracking the CSS key.  My output from running ogle is as follows:

```
libdvdread: Using libdvdcss version 1.2.5 for DVD access
libdvdread: Using libdvdcss version 1.2.5 for DVD access

libdvdread: Attempting to retrieve all CSS keys
libdvdread: This can take a _long_ time, please be patient

libdvdread: Get key for /VIDEO_TS/VIDEO_TS.VOB at 0x0000013c
libdvdread: Elapsed time 1
libdvdread: Get key for /VIDEO_TS/VTS_01_0.VOB at 0x0000038e
libdvdread: Elapsed time 0
libdvdread: Get key for /VIDEO_TS/VTS_01_1.VOB at 0x00000532
libdvdread: Elapsed time 0
libdvdread: Get key for /VIDEO_TS/VTS_02_0.VOB at 0x0038fd18
libdvdread: Elapsed time 0
libdvdread: Get key for /VIDEO_TS/VTS_02_1.VOB at 0x0038febc
libdvdread: Elapsed time 1
libdvdread: Get key for /VIDEO_TS/VTS_03_0.VOB at 0x003917dd
libdvdread: Elapsed time 0
libdvdread: Get key for /VIDEO_TS/VTS_03_1.VOB at 0x00391981
libdvdread: Elapsed time 0
libdvdread: Get key for /VIDEO_TS/VTS_04_0.VOB at 0x00392b33
libdvdread: Elapsed time 0
libdvdread: Get key for /VIDEO_TS/VTS_04_1.VOB at 0x00397f71
libdvdread: Error cracking CSS key for /VIDEO_TS/VTS_04_1.VOB (0x00397f71)!!
libdvdread: Elapsed time 0
libdvdread: Get key for /VIDEO_TS/VTS_05_0.VOB at 0x00397f8c
libdvdread: Elapsed time 0
libdvdread: Get key for /VIDEO_TS/VTS_05_1.VOB at 0x00398130
libdvdread: Elapsed time 0
libdvdread: Get key for /VIDEO_TS/VTS_06_0.VOB at 0x0039814d
libdvdread: Elapsed time 0
libdvdread: Get key for /VIDEO_TS/VTS_06_1.VOB at 0x003982f1
libdvdread: Elapsed time 0
libdvdread: Found 6 VTS's
libdvdread: Elapsed time 2
xscreensaver-command not found.
WARNING[ogle_mpeg_ps]: dvdreadblocks only got 1, wanted 240
FATAL[ogle_mpeg_ps]: dvdreadblocks failed
ctrl: ipc_rmid: Invalid argument

```

Any help would be greatly appreciated.[/QUOTE]

Just a thought but I have this same machine and the CD/DVD drive from factory is 
set to no DVD region, If yours is set to no region set it to the region you will be playing DVD movies from. If USA it is region 1. You can set in Windows if you have  dual boot setup like I do. I had all the restricted codecs and plugins
like you do and could not get to play until I commited my hardware to region.
Be sure of your region as you will only have 4 changes left after you set region. You only have to do this once unless you want to play DVD's from different regions.
Just remember if you reach the maximum of 5 changes you are stuck with your last choice.
WinDVD7 Platinum in windows plays without setting region.

To set/check go to Device Manager in windows and open properties in 
DVD/CD drive and click on DVD region tab. To find out more about regions
check out this link.

[http://hometheaterinfo.com/dvd3.htm](http://hometheaterinfo.com/dvd3.htm)

As far as how to change in Ubuntu in case you don't have dual boot
like me I don't know. Maybe others will know. 
    This is a change at the firmware level of the drive so I don't matter
what OS you do it in. It worked for me.  Download and use XINE a much
better player.

---

### Post by jdong on 2006-06-06
There is 'regionset' in universe that does the same.

---

### Post by Frank Golden on 2006-06-06
Hi All,
   Had my 5672 for a couple of months. I've been dual booting XP-SP2 Pro
on it with Ubuntu Dapper from CD flight 7 thru final with minimal problems.
Almost all hardware worked out of box or with minimal fuss. Since I use my 
laptop as a desktop replacement I have a lot of stuff hooked up to it using 
powered USB hubs. I output my sound through a Soundblaster Audigy 2 NX
usb sound card to 5.1 speakers. Sound setup automagically in Ubuntu.
I did have minor problem with Alsa plugin in XMMS forgetting what the default
sound card was at boot up. I fixed that by blacklisting my onboard sound card
so that it is not available at start up. Did have to update ATi drivers.
Printer works and Wi-Fi worked after some configuration using WEP, need to try to setup using WPA. PCMCIA cards work.
    The only thing that doesn't work is my built-in SD card reader.
If any of you know of a solution I'm all ears.
    One of the upgrades I made right off the bat with this machine was to upgrade
the 2GB of DDR2/533MHz memory to 2GB of DDR2/667MHz.
    I have a second 120GB HDD which is mounted in a drive caddy/sled.
It has a stable Ghost 9 image of my XP partition and a partimage copy
of my stable Ubuntu 6.06LTS install on it as well. Basically an exact copy of a my working dual boot setup. If I need to all I have to do is swap drives after
a disaster and be back in business.
   I love this machine.

---

### Post by haani on 2006-06-06
guys i am new here and i have got acer aspire 5672 could please tell how did you install the drivers for ati x1400 with full 2d/3d support thanks!!

---

### Post by gmc on 2006-06-06
[QUOTE=plaz42]Has anyone with this laptop had issues playing DVDs?  I have an Aspire 5670 running Dapper and KDE, and I cannot get any DVDs to play.  I have installed libdvdread and libdvdcss, but I always get errors cracking the CSS key.  My output from running ogle is as follows:

```
libdvdread: Using libdvdcss version 1.2.5 for DVD access
libdvdread: Using libdvdcss version 1.2.5 for DVD access

libdvdread: Attempting to retrieve all CSS keys
libdvdread: This can take a _long_ time, please be patient

*(lots of errors edited for beverity)...*


```

Any help would be greatly appreciated.[/QUOTE]


Umm, I'm assuming you haven't set the region code for the drive yet. Try installing "regionset" (sudo apt-get install regionset). The gentleman at [this]("http://www.dicianno.org/category/aspire-5670/") has a few words on this subject.

Gord

Edited: Dammit jdong, you beat me to it (again) :-)

---

### Post by Frank Golden on 2006-06-06
Gord

Edited: Dammit jdong, you beat me to it (again) :-)[/QUOTE]

No he didn't I did, I just didn't know how in Ubuntu. Thanks for the reference to "regionset" jdong.

---

### Post by plaz42 on 2006-06-06
Thanks gord, jdong, and all, regionset worked like a charm.

---

### Post by gmc on 2006-06-07
[QUOTE=haani]guys i am new here and i have got acer aspire 5672 could please tell how did you install the drivers for ati x1400 with full 2d/3d support thanks!![/QUOTE]

Assuming you've installed Dapper. 


1. Ensure you have the restricted modules installed: '**apt-get install linux-restricted-modules-`uname -r`**'
2. Check /etc/modules to ensure there's an entry '**fglrx**'
3. Check /etc/X11/xorg.conf to ensure there's an entry '**driver "fglrx"**' as opposed to 'driver "vesa"'. Attached is my xorg.conf for reference or use.
4. Reboot and Enjoy.

Gord

---

### Post by lir on 2006-06-07
[QUOTE=jdong]Those fglrx kernel messages are 'normal', it seems to show up whenever something 3D accelerated is initialized and torn down, with both fglrx releases. There are no visual consequences, though, so I'm ignoring them :)


Has anyone confirmed TV out to be working yet? I don't have a S-Video cable handy.[/QUOTE]


I've got an svideo cable here which I'm using to play my movies
and watch them using Windows on my TV.

How do we configure linux to do TV-Out?
I'll test it and let you know.


Thanks.

---

### Post by haani on 2006-06-07
[QUOTE=gmc]Assuming you've installed Dapper. 


1. Ensure you have the restricted modules installed: '**apt-get install linux-restricted-modules-`uname -r`**'
2. Check /etc/modules to ensure there's an entry '**fglrx**'
3. Check /etc/X11/xorg.conf to ensure there's an entry '**driver "fglrx"**' as opposed to 'driver "vesa"'. Attached is my xorg.conf for reference or use.
4. Reboot and Enjoy.

Gord[/QUOTE]

thanks but i already managed to install the drivers by following this guide [Ubuntu_Dapper_Installation_Guide]("http://wiki.cchtml.com/index.php/Ubuntu_Dapper_Installation_Guide")

yeh i have installed dapper thanks for ur help anywayz!!

---

### Post by haani on 2006-06-07
[QUOTE=gmc]Hi Folks,

[Computer Temprature Monitor]("http://computertemp.berlios.de/index.php")

If you use Gnome as your desktop, this is definately an applet that you'll want to install. Boy has it come a long way since I last played with it.

Gord[/QUOTE]

does anyone know how do i run this program i downloaded the dapper edition installed it but how did i run it??

---

### Post by gmc on 2006-06-07
[QUOTE=haani]does anyone know how do i run this program i downloaded the dapper edition installed it but how did i run it??[/QUOTE]

Assuming you downloaded the deb version. Just click on it and follow the instructions. Then once it's installed, right click on the gnome panel bar and choose "Add to panel". Scroll around a bit and you'll see it listed under "Hardware". 

Gord

---

### Post by Thund3rstruck on 2006-06-08
Anyone get the 6-in-1 card reader working? I don't use it a lot but I definately use it. Could someone post a link or quicky instruction on how to get that running?

---

### Post by jdong on 2006-06-08
There are a number of stories about the 6-in-1. It's a TI chipset PCI reader, and I've heard rumors that either the latest testing kernel supports it or supports it when patched, or that it requires closed-source firmware that TI does not release for Linux, or that there are really buggy 3rd party drivers for it.

I've never bothered to investigate it.

---

### Post by outofsync on 2006-06-08
Well, thanks a lot for all your help. I finally bought a 5672, and I'm typing this from it :D

I installed Dapper. There're some differences from Breezy, which I need to learn, in order to install all my software. One of them is locales reconfiguration, I'm searching the forums, and it seems the only solution is to manually edit files. Breezy had a ncurses UI for that :roll:

---

### Post by gmc on 2006-06-08
[QUOTE=outofsync]Well, thanks a lot for all your help. I finally bought a 5672, and I'm typing this from it :D

I installed Dapper. There're some differences from Breezy, which I need to learn, in order to install all my software. One of them is locales reconfiguration, I'm searching the forums, and it seems the only solution is to manually edit files. Breezy had a ncurses UI for that :roll:[/QUOTE]

Great to hear! Which version did you use to install? I've downloaded the Desktop version but not actually used it to install yet. Considering all the customization/tweaking I've done, I don't really need to yet, however I am considering making some major changes to my current partitioning scheme and probably will soon.

Gord

---

### Post by outofsync on 2006-06-09
[QUOTE=gmc]Great to hear! Which version did you use to install? I've downloaded the Desktop version but not actually used it to install yet. [/QUOTE]

I used the Desktop installer CD. After installation, I changed to the i686 kernel in order to be able to use both processors.

I'd like to have a dump of all Dapper repositories as a DVD collection (I had that for Breezy, got it from cargol.net), because I don't feel 100% right when I install some version of something without having the installer.

---

### Post by gmc on 2006-06-09
[QUOTE=outofsync]I used the Desktop installer CD. After installation, I changed to the i686 kernel in order to be able to use both processors.

I'd like to have a dump of all Dapper repositories as a DVD collection (I had that for Breezy, got it from cargol.net), because I don't feel 100% right when I install some version of something without having the installer.[/QUOTE]

Good to hear. The forums are full of stories of failed installs and I wasn't looking forward to adding one more. Guess I know what I'll be doing this weekend. I just finished two hoary to dapper upgrades and I have to say... NEVER AGAIN! it took me all day, and if it wasn't for the fact that these machines were highly customized I would have just formatted and re-installed from scratch.

Thanks
Gord

---

### Post by haani on 2006-06-10
wot software u guys use for wireless intnernet any of u use network manager cuz network manager sometimes doesnt connect to the network??

---

### Post by #bash on 2006-06-10
[QUOTE=haani]wot software u guys use for wireless intnernet any of u use network manager cuz network manager sometimes doesnt connect to the network??[/QUOTE]

I'm a new Ubuntu user, so I have similar question.
Basically I use wlassistant, however I still consider installing intel's drivers.
On the other hand, I've heard that some people had problems with installation of these drivers. What's your opinion? I'm a little bit confused.

I also want to ask about sound drivers. Is it necessary to install them (otherwise nothing will work), or is it just a good habit?

Thanks guys

---

### Post by megamania on 2006-06-10
Today I was buying this notebook, and then I decided to wait - I thought I'd check ubuntuforums first, and I'm glad I did.

I went through the entire thread and it sounds like most of the issues have been solved now, right?
Would you recommend buying this machine, or would you suggest looking for something different?
Is the sound output still a issue? I'd like to connect the notebook to my stereo amplifier from time to time...

Please give your overall advice on this machine, because I plan to use it exclusively with Ubuntu - everything has to work then!

Thanks so much for the thorough reporting of your experiences so far. This forum is just amazing.

---

### Post by jdong on 2006-06-10
I stand by this laptop 100%. It's simply a wonderful machine, and I have nothing to complain about it.

---

### Post by unz on 2006-06-10
Well, i'm not an ubuntu user, but a gentoo one ... i could install linux in a while with a live cd ... xgl too is working well. Really fast machine while compiling programs ... 
I listen to web-radios and watch dvds , my audio-out goes directly to my hi-fi line-in ... and everything is ok ... but yes, bundled speakers are not for entertaiment ...
we're waiting for webcam and 5-1 XD-MMC drivers 

If you like macbooks ... well this lappy is really hardware-like but -30% € off [i think i'm going to install osX86 too ...]

ps: why don't you collect all the tips about this laptop in an how-to [kernel config, governor,acpi etc..] ...  33 pages are not really friendly :D

---

### Post by gmc on 2006-06-11
[QUOTE=megamania]Today I was buying this notebook, and then I decided to wait - I thought I'd check ubuntuforums first, and I'm glad I did.

I went through the entire thread and it sounds like most of the issues have been solved now, right?
Would you recommend buying this machine, or would you suggest looking for something different?
Is the sound output still a issue? I'd like to connect the notebook to my stereo amplifier from time to time...

Please give your overall advice on this machine, because I plan to use it exclusively with Ubuntu - everything has to work then!

Thanks so much for the thorough reporting of your experiences so far. This forum is just amazing.[/QUOTE]

I agree with jdong's assessment of the 5672. As far as what works and what doesn't. The only things that do not work are the built-in webcam, SD card reader definately do not work at this time. Firewire has been reported to work, but I can't confirm that (anyone?), the built-in modem also may or may not work. Everything else wireless, graphics, sound, USB work just fine.

On the webcam front, apparently drivers are in the works, but the SD card reader probably will never work, thanks to the fact that the hardware manufacturer won't release any details about it.

Gord

---

### Post by megamania on 2006-06-11
[QUOTE=jdong]I stand by this laptop 100%. It's simply a wonderful machine, and I have nothing to complain about it.[/QUOTE]

I think I read somewhere in this thread that you had to recompile the kernel for some features to work (not sure it was you though - this thread is getting really big!). Is that still something that has to be done, or are all the updates included in Dapper?

And do suspend and hybernate work properly?

Tomorrow I might go for it!

---

### Post by haani on 2006-06-11
[QUOTE=#bash]I'm a new Ubuntu user, so I have similar question.
Basically I use wlassistant, however I still consider installing intel's drivers.
On the other hand, I've heard that some people had problems with installation of these drivers. What's your opinion? I'm a little bit confused.

I also want to ask about sound drivers. Is it necessary to install them (otherwise nothing will work), or is it just a good habit?

Thanks guys[/QUOTE]

there no need of installin intel wireless drivers as it is already recognized by ubuntu, the only problem i have is that it doesnt connect to the network sometimes. As for the sound drivers, it is also picked up by ubuntu and everthing works ok!! i dunno wot kind of problem u r havin??..do u have acer aspire 5672?? or a different one?..

---

### Post by #bash on 2006-06-11
[QUOTE=haani]there no need of installin intel wireless drivers as it is already recognized by ubuntu, the only problem i have is that it doesnt connect to the network sometimes. As for the sound drivers, it is also picked up by ubuntu and everthing works ok!! i dunno wot kind of problem u r havin??..do u have acer aspire 5672?? or a different one?..[/QUOTE]

Well, I don't have any problems with sound so far. I was only curious, because I haven't installed drivers. And I haven't tested it on i.e. Skype (microphone & speakers).
So I'm not sure if the sound will work in every case.

---

### Post by jdong on 2006-06-11
[QUOTE=megamania]I think I read somewhere in this thread that you had to recompile the kernel for some features to work (not sure it was you though - this thread is getting really big!). Is that still something that has to be done, or are all the updates included in Dapper?
[/quote]
No kernel recompiling required.

> 
And do suspend and hybernate work properly?

Tomorrow I might go for it!

Yes, both work. Hibernate works best, flawless. After suspend the video initialization is a bit goofy. It works, but **do not** restart the X server (i.e. log out and back in), because it cannot re-initialize 1280x800 mode. Likely a future BIOS update will fix this, as it's a bug with the Video BIOS.

---

### Post by haani on 2006-06-11
has anyone got Xgl/compiz workin properly with Dapper. i installed it but my laptop goes really slow after that and i dont have the option to shutdown or restart anymore?? and how to enable duo core?? thanks!!

---

### Post by outofsync on 2006-06-12
[QUOTE=unz]If you like macbooks ... well this lappy is really hardware-like but -30% € off [i think i'm going to install osX86 too ...][/QUOTE]
I wanted to buy a MacBookPro, but I needed the laptop this month, and the current hardware problems of MacBooks were too worrying, specially considering their price (moreover, I needed a rock-solid machine). Waiting for the next revision wasn't an option, because I needed the machine now.

So, I decided to buy the 5672, because the software I use also runs on Linux.

However, I hope I'll get an Apple laptop someday, but now I'll wait for some time (and I'll wait until they ship a laptop that can run OSX in 64bit mode).

Yes, I'm very happy after purchasing this Acer. Everything runs fine.

---

### Post by gmc on 2006-06-12
[QUOTE=haani]has anyone got Xgl/compiz workin properly with Dapper. i installed it but my laptop goes really slow after that and i dont have the option to shutdown or restart anymore?? and how to enable duo core?? thanks!![/QUOTE]

I do. I followed the second howto on [this page]("http://www.compiz.net/viewtopic.php?id=389"). The deb packages in the Ubuntu repositories didn't work for me. You'll want to be sure to 
**sudo apt-get install linux-686-smp** to get both processors going.

Gord

---

### Post by haani on 2006-06-12
[QUOTE=gmc]I do. I followed the second howto on [this page]("http://www.compiz.net/viewtopic.php?id=389"). The deb packages in the Ubuntu repositories didn't work for me. You'll want to be sure to 
**sudo apt-get install linux-686-smp** to get both processors going.

Gord[/QUOTE]

thanks m8 i will try that 2nite!!

---

### Post by jaylittle on 2006-06-12
[QUOTE=jdong]No kernel recompiling required.



Yes, both work. Hibernate works best, flawless. After suspend the video initialization is a bit goofy. It works, but **do not** restart the X server (i.e. log out and back in), because it cannot re-initialize 1280x800 mode. Likely a future BIOS update will fix this, as it's a bug with the Video BIOS.[/QUOTE]
Could you provide more detail on this?  On my Acer 5672 I am unable to hibernate using 6.06.  After hitting hibernate the screensaver kicks in and nothing else happens.  I have a custom kernel compiled with suspend2 but it hangs during the atomic copy process and I have yet to determine which piece of hardware is responsible for the issue.

---

### Post by jdong on 2006-06-12
I use stock Dapper kernels and its built-in hibernate support. I've posted tarballs of my /etc/acpi setup, and it suspends and hibernates just fine... no tuning.

---

### Post by jaylittle on 2006-06-12
[QUOTE=jdong]I use stock Dapper kernels and its built-in hibernate support. I've posted tarballs of my /etc/acpi setup, and it suspends and hibernates just fine... no tuning.[/QUOTE]
I just found them an d download the tarball.  I'll let you know in a few minutes how well things go :p 

Thanks.

---

### Post by jaylittle on 2006-06-12
Okay so I gave it a shot.  Initially the change made no difference but given your statements, I began to remove hardware that I had added to the laptop.  Sure enough once I removed my PCMCIA audigy card, hibernate on the standard kernel as well as my suspend2 kernel began to function correctly.

Unfortunately pccardctl doesn't work very well on this laptop and suspending/resuming or ejecting/inserting causes the pccardctl to stop responding to further commands at some point.  This means that as long as I use the card (which I need for the time being) I will be unable to hibernate.

Pulling the card out of the socket causes Ubuntu (as well as other distros) to lock down hard.

Oh well thanks for the help :)

---

### Post by haani on 2006-06-12
[QUOTE=gmc]I do. I followed the second howto on [this page]("http://www.compiz.net/viewtopic.php?id=389"). The deb packages in the Ubuntu repositories didn't work for me. You'll want to be sure to 
**sudo apt-get install linux-686-smp** to get both processors going.

Gord[/QUOTE]

does Xgl/compiz run smoothly for u it doesnt for me. it turns off after some mins!! so i have to log out and log back in again to get it to work!!??

---

### Post by jdong on 2006-06-12
Hmm, with the PC Card, try rmmoding the associated kernel modules before yanking or disabling the card.

Xgl/compiz runs very smoothly for me under medium and high PowerStates. Under low, it's slightly choppy but still acceptable. Battery life is only minimally diminished under low clock speeds.

---

### Post by gmc on 2006-06-12
[QUOTE=haani]does Xgl/compiz run smoothly for u it doesnt for me. it turns off after some mins!! so i have to log out and log back in again to get it to work!!??[/QUOTE]

Yep. Other than it can sometimes tax the cpu(s) at startup, causing the fan to make the machine sound like it wants to take off.

Try this:

```

Section "Device"
        Identifier      "ATI X1400 Mobile"
        Driver          "fglrx"
        BusID           "PCI:1:0:0"
        VideoRam        131072
        Option          "VideoOverlay"          "on"
        Option          "OpenGLOverlay"         "off"
        Option          "UseInternalAGPGART"    "no"
        ***Option          "KernelModuleParm"      "agplock=0"***
EndSection

```

You may want to check the order of your plugins too. Open "Configuration Editor" and check /apps/compiz/general/allscreens/options. I have the order as follows:

***gconf,decoration,wobbly,fade,minimize,cube,rotate,scale,move,resize,place,switcher,trailfocus,water,bs,widget***

and I turned off the docket thing that appears at the bottom of the screen as it caused problems.

Gord


Gord

---

### Post by jdong on 2006-06-13
I recently configured Compiz+Xgl on the laptop, and here are my usage notes:

 * GPU frequency scaling still works. My ACPI script can still detect the parent :0 display and set the GPU frequency.
 * Battery life may be slightly diminished. I think I averaged 5 minutes lower battery life with Xgl, so it's not significant enough to prevent its use.
 * Xgl is still usable under lowest GPU frequency. You can feel a bit of lag, but it still works nonetheless. I think that's acceptable for an additional 30+ minutes of battery life!
 * WHAT THE HELL IS THE RAIN PLUGIN FOR?!?!??!

---

### Post by haani on 2006-06-13
[QUOTE=gmc]Yep. Other than it can sometimes tax the cpu(s) at startup, causing the fan to make the machine sound like it wants to take off.

Try this:

```

Section "Device"
        Identifier      "ATI X1400 Mobile"
        Driver          "fglrx"
        BusID           "PCI:1:0:0"
        VideoRam        131072
        Option          "VideoOverlay"          "on"
        Option          "OpenGLOverlay"         "off"
        Option          "UseInternalAGPGART"    "no"
        ***Option          "KernelModuleParm"      "agplock=0"***
EndSection

```

You may want to check the order of your plugins too. Open "Configuration Editor" and check /apps/compiz/general/allscreens/options. I have the order as follows:

***gconf,decoration,wobbly,fade,minimize,cube,rotate,scale,move,resize,place,switcher,trailfocus,water,bs,widget***

and I turned off the docket thing that appears at the bottom of the screen as it caused problems.

Gord


Gord[/QUOTE]


how do u add this

ection "Device"
        Identifier      "ATI X1400 Mobile"
        Driver          "fglrx"
        BusID           "PCI:1:0:0"
        VideoRam        131072
        Option          "VideoOverlay"          "on"
        Option          "OpenGLOverlay"         "off"
        Option          "UseInternalAGPGART"    "no"
        ***Option          "KernelModuleParm"      "agplock=0"***
EndSection

to xorg.conf?? sorry i am new at linux!! and how do u get shutdown and restart options back in xgl?? thanks!!

---

### Post by unz on 2006-06-13
[QUOTE=jdong]I recently configured Compiz+Xgl on the laptop, and here are my usage notes:

 * GPU frequency scaling still works. My ACPI script can still detect the parent :0 display and set the GPU frequency.[/QUOTE]
i got it on display :1 and ...
```
unz@unzWire ~ $ aticonfig --lsp
Error: Unable to obtain POWERplay information.

```  ... i'll try with :0
> 
 * WHAT THE HELL IS THE RAIN PLUGIN FOR?!?!??!
ahaha something for nerds :D you got rain drops over your screen on every click+key combination

---

### Post by unz on 2006-06-13
I founded that my dsdt has got an error in it ... what about yours?
> unzWire unz # cp /proc/acpi/dsdt .
unzWire unz # iasl -dc dsdt

Intel ACPI Component Architecture
AML Disassembler version 20060512 [Jun  7 2006]
Copyright (C) 2000 - 2006 Intel Corporation
Supports ACPI Specification Revision 3.0a

Loading Acpi table from file dsdt
Acpi table [DSDT] successfully installed and loaded
Pass 1 parse of [DSDT]
Pass 2 parse of [DSDT]
Parsing Deferred Opcodes (Methods/Buffers/Packages/Regions)
........................................................................................................... ........................................................................................................... ........................................................................................................... ........................................................................................................... ..................................................................................
Parsing completed
Disassembly completed, written to "dsdt.dsl"

Compiling "dsdt.dsl"
dsdt.dsl     1: ACPI
Error    4094 -    ^ syntax error, unexpected PARSEOP_NAMESEG, expecting PARSEOP_DEFINITIONBLOCK

ASL Input:  dsdt.dsl - 9062 lines, 335865 bytes, 0 keywords
Compilation complete. 1 Errors, 0 Warnings, 0 Remarks, 0 Optimizations


---

### Post by gmc on 2006-06-14
Hi haani,

[QUOTE=haani]how do u add this

ection "Device"
        Identifier      "ATI X1400 Mobile"
        Driver          "fglrx"
        BusID           "PCI:1:0:0"
        VideoRam        131072
        Option          "VideoOverlay"          "on"
        Option          "OpenGLOverlay"         "off"
        Option          "UseInternalAGPGART"    "no"
        ***Option          "KernelModuleParm"      "agplock=0"***
EndSection

to xorg.conf?? sorry i am new at linux!! and how do u get shutdown and restart options back in xgl?? thanks!![/QUOTE]

Sorry, my bad. Yes you'll need to edit your /etc/X11/xorg.conf, which you can do with
**sudo nano /etc/X11/xorg.conf**. Of course you've probably figured out it out by now, sorry about that.

Gord

---

### Post by haani on 2006-06-14
[QUOTE=gmc]Hi haani,



Sorry, my bad. Yes you'll need to edit your /etc/X11/xorg.conf, which you can do with
**sudo nano /etc/X11/xorg.conf**. Of course you've probably figured out it out by now, sorry about that.

Gord[/QUOTE]

thanks again but i already figured that out lol!! thanks anywayz.

---

### Post by haani on 2006-06-14
guys i have run into another problem soz

when i type fglrxinfo i get:

Xlib:  extension "XFree86-DRI" missing on display ":1.0".
display: :0.0  screen: 0
OpenGL vendor string: ATI Technologies Inc.
OpenGL renderer string: ATI Mobility Radeon X1400 Generic
OpenGL version string: 2.0.5814 (8.25.18)

before i installed xgl i didnt get that message Xlib:  extension "XFree86-DRI" missing on display ":1.0" wot can i do to fix this thanks!!!

---

### Post by jdong on 2006-06-14
I get that with Xgl, too. I don't think the fglrx extensions will work under Xgl.

---

### Post by bwanab on 2006-06-14
I installed the linux version of Google Earth. Installation went fine, but when I run it I get:

bill@BillWellington:~$ sudo googleearth
Password:
[fglrx] API ERROR: could not register entrypoint for SelectTextureSGIS
[fglrx] API ERROR: could not register entrypoint for SelectTextureTransformSGIS
[fglrx] API ERROR: could not register entrypoint for ClientActiveVertexStreamATI[fglrx] API ERROR: could not register entrypoint for VertexBlendEnviATI
[fglrx] API ERROR: could not register entrypoint for VertexBlendEnvfATI
[fglrx] API ERROR: could not register entrypoint for VertexStream2sATI
[fglrx] API ERROR: could not register entrypoint for VertexStream2svATI
[fglrx] API ERROR: could not register entrypoint for VertexStream2iATI
...ad nauseum

Other posters on digg who run dapper claim it runs for them. Any ideas?

---

### Post by haani on 2006-06-15
yes it does work fine for me.. have u checked ur ati drivers..type fglrxinfo in terminal to see if the drivers are working..

---

### Post by gmc on 2006-06-15
[QUOTE=bwanab]I installed the linux version of Google Earth. Installation went fine, but when I run it I get:

bill@BillWellington:~$ sudo googleearth
Password:
[fglrx] API ERROR: could not register entrypoint for SelectTextureSGIS
[fglrx] API ERROR: could not register entrypoint for SelectTextureTransformSGIS
[fglrx] API ERROR: could not register entrypoint for ClientActiveVertexStreamATI[fglrx] API ERROR: could not register entrypoint for VertexBlendEnviATI
[fglrx] API ERROR: could not register entrypoint for VertexBlendEnvfATI
[fglrx] API ERROR: could not register entrypoint for VertexStream2sATI
[fglrx] API ERROR: could not register entrypoint for VertexStream2svATI
[fglrx] API ERROR: could not register entrypoint for VertexStream2iATI
...ad nauseum

Other posters on digg who run dapper claim it runs for them. Any ideas?[/QUOTE]


I'm not sure if this is the cause of the above errors, but why are you using sudo to run googleearth? or did you install it under user googleearth. If that's the case, you may be suffering from user googleearth not having privileges to video device. 

If you login as user googleearth and type '**groups**', you should see that the user is a member of the video group, if not that might be the problem. There is a command to add a user to a specific group, but I don't use it as I tend to bugger things up. You can issue the command: **sudo nano /etc/groups** and look down the list to video and then add **,googleearth** so the line should read something like:

video:x:44:bwanab,googleearth

Note: I'm assuming your regular login username is bwanab, in that example.

Gord

---

### Post by kefkakiller on 2006-06-15
Has anyone gotten video out working? If so do you have any info/links to help me out. I've tried using [these]("http://odin.prohosting.com/wedge01/gentoo-radeon-faq.html#4_tvout")  [links]("http://thinkwiki.org/wiki/ATI_Mobility_Radeon_X300") as a starting point, but, being relatively new to linux, I know very little about configuring xorg.conf and I couldn't get them to work in my situation. I've installed the atitvout package but when I run it, it can't detect the tv. Also, I guess I should also mention that I'm using xgl/compiz, in case that changes things.

Thanks. Also thanks to all the people who have posted things earlier in the thread, this thread has been invaluable.

---

### Post by unz on 2006-06-15
i founded a solution for aticonfig and xgl.
I made an alias in .bashrc> alias aticonfigctrl='DISPLAY=:94 aticonfig --lsp'
alias aticonfigpower1='DISPLAY=:94 aticonfig --set-powerstate=1'
alias aticonfigpower2='DISPLAY=:94 aticonfig --set-powerstate=2'
alias aticonfigpower3='DISPLAY=:94 aticonfig --set-powerstate=3'
 i think aticonfig... is not a good alias .. but it works

EDIT:
in my xorg.log > 
(II) fglrx(0): POWERplay version 3.  5 power states available:
(II) fglrx(0):   1. 446/342MHz @ 60Hz [enable load balancing]
(II) fglrx(0):   2. 135/135MHz @ 60Hz [low voltage, enable sleep]
(II) fglrx(0):   3. 209/135MHz @ 60Hz [low voltage, enable sleep]
(II) fglrx(0):   4. 324/135MHz @ 60Hz [low voltage, enable sleep]
(II) fglrx(0):   5. 392/252MHz @ 60Hz [enable sleep]


maybe more options for me

---

### Post by bwanab on 2006-06-15
[QUOTE=gmc]I'm not sure if this is the cause of the above errors, but why are you using sudo to run googleearth? or did you install it under user googleearth. If that's the case, you may be suffering from user googleearth not having privileges to video device. 

Gord[/QUOTE]
You were correct that permissions were the problem. I'd originally installed using sudo because I wanted to install in /usr/local. That created root owned directories in my home directory that made it so I couldn't run as myself. I removed everything and reinstalled as myself and it now works - albeit slowly. When I launch it tells me that I'm using software opengl and recommends upgrading my driver....

---

### Post by jdong on 2006-06-15
[QUOTE=unz]i founded a solution for aticonfig and xgl.
I made an alias in .bashrc i think aticonfig... is not a good alias .. but it works

EDIT:
in my xorg.log 

maybe more options for me[/QUOTE]

That is very interesting... Does aticonfig --lsp show all 5 states also? Is it a mobility radeon X1400? What system BIOS version?

---

### Post by unz on 2006-06-16
[QUOTE=jdong]That is very interesting... Does aticonfig --lsp show all 5 states also? Is it a mobility radeon X1400? What system BIOS version?[/QUOTE]
no way ... only 3 states ..


attached lshw

---

### Post by jdong on 2006-06-16
hmm, that is really intriguing...

---

### Post by jdong on 2006-06-16
I looked at my Xorg.log and it shows the same 5 powerstates, however, aticonfig only gives me 3.

---

### Post by gmc on 2006-06-18
[QUOTE=jdong]I looked at my Xorg.log and it shows the same 5 powerstates, however, aticonfig only gives me 3.[/QUOTE]

I'm guessing, but are you now running XGL/Compiz? If that's the case where are you setting the powerstate for the X1400? If I try running 'DISPLAY=xx aticonfig --lsp', where xx=:0,:1 or :94 it either fails to return to the command prompt and I have to press ^C to exit or reports "Error: Unable to obtain POWERplay information."

Gord

---

### Post by jdong on 2006-06-18
Using DISPLAY=:0 works here, with Xgl on :1.

---

### Post by unz on 2006-06-18
[QUOTE=gmc]I'm guessing, but are you now running XGL/Compiz? If that's the case where are you setting the powerstate for the X1400? If I try running 'DISPLAY=xx aticonfig --lsp', where xx=:0,:1 or :94 it either fails to return to the command prompt and I have to press ^C to exit or reports "Error: Unable to obtain POWERplay information."

Gord[/QUOTE]

start Xgl like this ```
/usr/bin/Xgl :1 -ac -accel glx:pbuffer -accel xv:pbuffer **-xorgAc**

```

---

### Post by gmc on 2006-06-18
[QUOTE=unz]start Xgl like this ```
/usr/bin/Xgl :1 -ac -accel glx:pbuffer -accel xv:pbuffer **-xorgAc**

```[/QUOTE]

Bingo! Now it works... I must have missed the discussion on the -xorgAc option. Thanks...

Gord

---

### Post by samir85 on 2006-06-18
Hey guys,

I have a Sony laptop also based on the Intel Centrino Duo platform.
Anyway, I can't get the soundcard to work in full-duplex mode (my soundchip is intel 82801G ICH7 family). Since you should have the same shoundchip, I wanted to know if you're experiencing similiar issues?

---

### Post by gmc on 2006-06-18
[QUOTE=samir85]Hey guys,

I have a Sony laptop also based on the Intel Centrino Duo platform.
Anyway, I can't get the soundcard to work in full-duplex mode (my soundchip is intel 82801G ICH7 family). Since you should have the same shoundchip, I wanted to know if you're experiencing similiar issues?[/QUOTE]

Hi Samir,

I was having a problem with sound being problematic. Sometimes I'd boot and get no sound and other times it worked fine. I'm beginning to wish I'd stuck with Flight-7 w/updates, rather than having adjusting my partitions and installing the release version of Dapper. Anyhow, following [this thread]("http://ubuntuforums.org/showthread.php?t=187156&highlight=1.0.11") and upgraded the Alsa drivers to 1.0.11 seems to have fixed all my sound problems.

Gord

---

### Post by unz on 2006-06-19
I've done some testing with power-management ... i can't get any great bonus setting ati power-state to the minimum, nor my laptop is colder [~-1°C] nor i can get more time  for my battery ... better is decreasing lcd brightness ... it gives me back ~10 minutes ... 

Same behaviour with cpu-states ... i can't get any remarkable freshness ... but i didn't monitor battery ... 

My distro is gentoo-linux, and you know cpus are stressed quite a lot but i can live for 2 h 30' m [with wireless on and an usb mouse] ... 

What about you?

ps: i copied acpi scripts founded here ... but i don't know how to use it

---

### Post by jdong on 2006-06-19
Cardreader update: I've gotten the cardreader to work with SD cards (that's the only type I have), but it takes kernel work.

[http://openfacts.berlios.de/index-en.phtml?title=TI_FlashMedia_xx12/xx21_driver](http://openfacts.berlios.de/index-en.phtml?title=TI_FlashMedia_xx12/xx21_driver)

There is the driver. It is under very heavy development, so I recommend checking it out from SVN.

It requires a kernel greater than Dapper's (i.e. Dapper kernel does not include all the necessary modules), which means if you want to use it, you're probably gonna be compiling your own kernel :-/

I've gotten it working on an Edgy daily kernel, but that kernel is missing some other features I want, so likely I will be rolling my own vanilla kernels. I still have to contemplate between carrying an extra USB cable for my camera or maintaining my own kernel :)

---

### Post by unz on 2006-06-19
Dho ..i've got only an XD card ... can't help you testing it

---

### Post by Frank Golden on 2006-06-19
Hey Jdong,
   Texas Instruments plain and simple SUCKS!! 
Hope to see something soon that us less technical types can download
and install (read Synaptic or apt-get). I really don't want to compile a
kernel just to use this device. This (card reader) and the Acer Orbicam
are the only two built-in devices that don't work on my 5672 with Ubuntu 6.06LTS.

---

### Post by jdong on 2006-06-19
[QUOTE=Frank Golden]Hey Jdong,
   Texas Instruments plain and simple SUCKS!! 
Hope to see something soon that us less technical types can download
and install (read Synaptic or apt-get). I really don't want to compile a
kernel just to use this device. This (card reader) and the Acer Orbicam
are the only two built-in devices that don't work on my 5672 with Ubuntu 6.06LTS.[/QUOTE]
I whole-heartedly agree with you. Instead of implementing it via a standard interface (like SDHCI or USB Mass Storage) that is widely accepted by the industry, they decided to write their own protocol (FlashMedia) then not release specs on how to interface with it. The tifmxx driver is reverse-engineered.

Hopefully by the time Edgy comes around, hopefully tifmxx will be in a usable state for inclusion with the Edgy kernel. It requires new features in the 2.6.16+ kernels, so Dapper will not get support for this controller, sadly.

The webcam, Michael Xhaard of spca5xx has said that he is looking at implementing the drivers for our vivicro vc0321 controller. The full specs are available, but the hardware is just too damn new!


Like you, these are the last two pieces of the puzzle. The cardreader is already working to some degree, while we wait for spca5xx support.


P.S. 2.6.17 works quite well for me. I started with vanilla 2.6.17, applied -ck patches (for improved desktop performance), then just used "make oldconfig" to apply Dapper kernel settings to 2.6.17. For the new options, accept defaults. Say yes to the new multicore scheduler, which is a brand-new scheduler specifically designed for shared-cache CPU's (like our Core Duos) that shows 8-10% improvement in SPEC benchmarks! As far as kernel modules, ATI and ipw3945 can be compiled/installed manually, and they work cleanly with the 2.6.17 kernel.

---

### Post by samir85 on 2006-06-20
[QUOTE=gmc]Hi Samir,

I was having a problem with sound being problematic. Sometimes I'd boot and get no sound and other times it worked fine. I'm beginning to wish I'd stuck with Flight-7 w/updates, rather than having adjusting my partitions and installing the release version of Dapper. Anyhow, following [this thread]("http://ubuntuforums.org/showthread.php?t=187156&highlight=1.0.11") and upgraded the Alsa drivers to 1.0.11 seems to have fixed all my sound problems.

Gord[/QUOTE]

Ok, thanks for information.

Probably, I will switch to Edgy soon. :D

---

### Post by gmc on 2006-06-20
[QUOTE=jdong]
P.S. 2.6.17 works quite well for me. I started with vanilla 2.6.17, applied -ck patches (for improved desktop performance), then just used "make oldconfig" to apply Dapper kernel settings to 2.6.17. For the new options, accept defaults. Say yes to the new multicore scheduler, which is a brand-new scheduler specifically designed for shared-cache CPU's (like our Core Duos) that shows 8-10% improvement in SPEC benchmarks! As far as kernel modules, ATI and ipw3945 can be compiled/installed manually, and they work cleanly with the 2.6.17 kernel.[/QUOTE]

This is information handy. I guess v1.0.5 ipw3945 driver is not in the 2.6.17 kernel yet? I downloaded the kernel tarball but as I'm still struggling to get accelerated video working again. Stupid me installed the release Dapper and blew away the working flight-7 install that I had :-( . Maybe this weekend I'll try installing 2.6.17 and manually install the 8.25.18 drivers.

G.

---

### Post by unz on 2006-06-20
I add a screenshot ... you can see some gnome-applets working [gnome-2.15.3]

- Cpu monitor [frequency and governor choice with a click]
- Hardware monitor [Thermal* and hd**]
[SIZE="1"]* you have to enable acpi thermal in kernel
** you have to modify /usr/share/hddtemp/hddtemp.db for our hd support
[add  in Hitachi section, around line 96][/SIZE]
```
"HTS541010G9SA00"               194  C  "Hitachi Travelstar 100GB (5400RPM)"
```
- Network monitor [wireless traffic]
- Power management [battery*/AC monitor, suspend2/hibernate]
[SIZE="1"]* you have to enable acpi battery in kernel[/SIZE]

TODO:
Configure NetworkManager in the right way ... i can't get a valid ip
Computertemp ... it crashes for me

---

### Post by jdong on 2006-06-20
[QUOTE=gmc]This is information handy. I guess v1.0.5 ipw3945 driver is not in the 2.6.17 kernel yet? I downloaded the kernel tarball but as I'm still struggling to get accelerated video working again. Stupid me installed the release Dapper and blew away the working flight-7 install that I had :-( . Maybe this weekend I'll try installing 2.6.17 and manually install the 8.25.18 drivers.

G.[/QUOTE]
No, ipw3945 is not merged with the 2.6 kernel yet. I get the feeling that due to the binary userspace daemon, that won't happen anytime soon :-/. You'll have better luck installing ATI drivers completely from scratch, but you can try installing fglrx-kernel-source, extracting the fglrx tarball in /usr/src, and executing the various make.sh's that you find, and you might get lucky :)

---

### Post by haani on 2006-06-20
i had the same problem when i compiled kernal 2.6.17 wireless and ati drivers were gone so i had to uninstall the new kernel through synaptic. i couldn't be bother to get the wireless and video working again.

---

### Post by jdong on 2006-06-20
Yeah, we don't tend to appreciate the convenience afforded to us by our beloved kernel maintainers until we have to perform that job ourselves :)

---

### Post by Frank Golden on 2006-06-20
[QUOTE=jdong]I whole-heartedly agree with you. Instead of implementing it via a standard interface (like SDHCI or USB Mass Storage) that is widely accepted by the industry, they decided to write their own protocol (FlashMedia) then not release specs on how to interface with it. The tifmxx driver is reverse-engineered.

Hopefully by the time Edgy comes around, hopefully tifmxx will be in a usable state for inclusion with the Edgy kernel. It requires new features in the 2.6.16+ kernels, so Dapper will not get support for this controller, sadly.

The webcam, Michael Xhaard of spca5xx has said that he is looking at implementing the drivers for our vivicro vc0321 controller. The full specs are available, but the hardware is just too damn new!


Like you, these are the last two pieces of the puzzle. The cardreader is already working to some degree, while we wait for spca5xx support.


P.S. 2.6.17 works quite well for me. I started with vanilla 2.6.17, applied -ck patches (for improved desktop performance), then just used "make oldconfig" to apply Dapper kernel settings to 2.6.17. For the new options, accept defaults. Say yes to the new multicore scheduler, which is a brand-new scheduler specifically designed for shared-cache CPU's (like our Core Duos) that shows 8-10% improvement in SPEC benchmarks! As far as kernel modules, ATI and ipw3945 can be compiled/installed manually, and they work cleanly with the 2.6.17 kernel.[/QUOTE]
Hi jdong,
   Had you up to your p.s. 
Don't have a clue how to  compile 2.6.17 could you point me to fool proof tutorial?
Tried using instructions in this thread but failed miserably.

[http://www.ubuntuforums.org/showthread.php?t=157560&highlight=2.6.16](http://www.ubuntuforums.org/showthread.php?t=157560&highlight=2.6.16)

I have a spare HD with a copy of Ubuntu 6.06 LTS installed on it and a partimage backup of my latest stable configuration on another drive.
So I am brave enough and willing to try to roll my own. Just need good unambiguous instructions for a newbie.
    So Edgy for the last two pieces of puzzle. Will Edgy at release be a LTS
or a replacement for Ubuntu 6.06 LTS?

---

### Post by dyous87 on 2006-06-20
ok as of know i've been using dapper drake only on my acer...before it was released i was testing the different flights while dual booting xp. Know i have everything working fine it seems. The only thing i haven't tested yet is the card reader which i could care less about and my orbi cam which isn't a problem for me. 

One thing that seems to be an issue and i can't figure out why is with the volume control. When playing an mp3 in vlc or frostwire the volume control doesn't work. I could mute the computer volume but the sound will be exactly the same....no idea why...i duno if any of your are experiencing the same issue???

---

### Post by Frank Golden on 2006-06-20
[QUOTE=dyous87]ok as of know i've been using dapper drake only on my acer...before it was released i was testing the different flights while dual booting xp. Know i have everything working fine it seems. The only thing i haven't tested yet is the card reader which i could care less about and my orbi cam which isn't a problem for me. 

One thing that seems to be an issue and i can't figure out why is with the volume control. When playing an mp3 in vlc or frostwire the volume control doesn't work. I could mute the computer volume but the sound will be exactly the same....no idea why...i duno if any of your are experiencing the same issue???[/QUOTE]

Hi dyous87,
    My hardware volume control works fine.
I agree with you about the Orbicam and SD card reader, however it 
bugs me that these 2 pieces of onboard hardware don't work in 
Ubuntu 6.06. Just last two pieces of puzzle like jdong says.
Sorry I couldn't help with volume control.

---

### Post by unz on 2006-06-20
... does your fan roll? .... mine stops 2 secs after power on ... my temp are 51° cpu and 41° hd ... is there anything wrong?

EDIT:
found that fan starts @ 50°

---

### Post by haani on 2006-06-20
does anyone know how to fix java on firefox it cashes after an java applet starts. i am using sun-java5-jre version is 1.5.0-06-1?? and which version of swiftfox do u use because i dont see a version for intel centrino duo???

---

### Post by jdong on 2006-06-20
The fan control appears to be very passive (only kicks in when it's pretty hot already) :)

---

### Post by unz on 2006-06-20
[QUOTE=jdong]The fan control appears to be very passive (only kicks in when it's pretty hot already) :)[/QUOTE]

It's not really a good thing. In a closed system something you got usually warm becomes hotter and something hot colder ... in our system cpu @ ~50°/52°C is good ... but an hd @ 46°/47°C  :roll:  @boot my hd is 39°C, then rise to 46°C ... idle ... just thermal balance :(

---

### Post by gmc on 2006-06-21
[QUOTE=haani]does anyone know how to fix java on firefox it cashes after an java applet starts. i am using sun-java5-jre version is 1.5.0-06-1?? and which version of swiftfox do u use because i dont see a version for intel centrino duo???[/QUOTE]

Try **sudo update-alternatives --config java** and make sure everything is pointing to the correct version of Java. I noticed the rssowl (java application) was having troubles here until I straightened out the system and made sure it was trying to use the correct version of Java.

Gord

---

### Post by gmc on 2006-06-21
[QUOTE=jdong]The fan control appears to be very passive (only kicks in when it's pretty hot already) :)[/QUOTE]

Dunno about that... my system seems to hover around 49-50C but then again the fan is running all the time. Compiling the kernel (make -j 2) caused it to rocket up to 70C, adding nice (nice -n 1 make -j 2) dropped the temprature back down to 52-55C. I'm worried that with the fan running all the time that I'll burn it out before I have any other hardware failure.

Gord

P.S. :-) I finallly got the ATI/Mesa problem sorted... discovered by adding **dri** to /etc/modules corrected the problem.

---

### Post by Frank Golden on 2006-06-21
[QUOTE=gmc]Dunno about that... my system seems to hover around 49-50C but then again the fan is running all the time. Compiling the kernel (make -j 2) caused it to rocket up to 70C, adding nice (nice -n 1 make -j 2) dropped the temprature back down to 52-55C. I'm worried that with the fan running all the time that I'll burn it out before I have any other hardware failure.

Gord

P.S. :-) I finallly got the ATI/Mesa problem sorted... discovered by adding **dri** to /etc/modules corrected the problem.[/QUOTE]

Mine rarely goes to 59°-60° Fan does come on fast for a few seconds at boot up sometimes? Usually stays around 50°C. My fan runs slow all the time also and I have computer on sheet aluminum stand made for
laptops. I have drilled holes in the aluminum sheet where vent openings in computer line up. Stand holds back of computer about 2" above desk. So I get good circulation. When resting on desk by itself fan runs
high more often and temps are higher. I would think that fan running all the time is by design? Dunno!

---

### Post by unz on 2006-06-21
[QUOTE=Frank Golden]Mine rarely goes to 59°-60° Fan does come on fast for a few seconds at boot up sometimes? Usually stays around 50°C. My fan runs slow all the time also and I have computer on sheet aluminum stand made for
laptops. I have drilled holes in the aluminum sheet where vent openings in computer line up. Stand holds back of computer about 2" above desk. So I get good circulation. When resting on desk by itself fan runs
high more often and temps are higher. I would think that fan running all the time is by design? Dunno![/QUOTE]

I got my cpu stable around 50°/51°C, me too got laptop not on the desk but on a Mysql 4.0 Byble .. so air can flow around. My fan is always quite, i hear it only at boot. 
When i emerge something [install programs] cpu flies over 65°C ... but just for a few seconds ... Xgl effects don't make my cpus hotter

ps now in Rome is 34°C ... hot summer is starting #-o

---

### Post by gmc on 2006-06-21
[QUOTE=Frank Golden]Mine rarely goes to 59°-60° Fan does come on fast for a few seconds at boot up sometimes? Usually stays around 50°C. My fan runs slow all the time also and I have computer on sheet aluminum stand made for
laptops. I have drilled holes in the aluminum sheet where vent openings in computer line up. Stand holds back of computer about 2" above desk. So I get good circulation. When resting on desk by itself fan runs
high more often and temps are higher. I would think that fan running all the time is by design? Dunno![/QUOTE]

Now that's an interesting idea. I'm using a leather place mat under neat (Shhh don't tell the wife :D ).  I did pick up a **tarus coolmat**. What a piece of junk. The fans on is suck air down and blow it out the back but since the internal fan is trying to suck air up and blow it out the side, the machine ends up running hotter than without it. Buyer beware! avoid this piece of hardware... it's a waste of money.

The other thing I've just noticed. I installed KDE this morning and although there's no CPU temprature monitor, it appears that the fan does't run all the time under KDE but does so in GNOME. I'm going to **watch cat /proc/acpi/thermal_zone/THRM/temperature** for a bit and see what sort of tempratures I get.

Gord

---

### Post by Frank Golden on 2006-06-21
[QUOTE=gmc]Now that's an interesting idea. I'm using a leather place mat under neat (Shhh don't tell the wife :D ).  I did pick up a **tarus coolmat**. What a piece of junk. The fans on is suck air down and blow it out the back but since the internal fan is trying to suck air up and blow it out the side, the machine ends up running hotter than without it. Buyer beware! avoid this piece of hardware... it's a waste of money.

The other thing I've just noticed. I installed KDE this morning and although there's no CPU temprature monitor, it appears that the fan does't run all the time under KDE but does so in GNOME. I'm going to **watch cat /proc/acpi/thermal_zone/THRM/temperature** for a bit and see what sort of tempratures I get.

Gord[/QUOTE]
Hi Gord,
   See link below for product I use.
[http://www.raindesigninc.com/ilap.html](http://www.raindesigninc.com/ilap.html)

See this link for photo of mods to my iLap.

[http://i30.photobucket.com/albums/c338/fjgold/100_0083.jpg](http://i30.photobucket.com/albums/c338/fjgold/100_0083.jpg)

Product is made for Macs but I don't think it minds working for PC. LOL
Angle brackets on bottom edge is to keep laptop from slipping off the
desk when at edge of desk. There is a strip of velcro under front edge of
device so I placed sticky back velcro on desktop to keep in place.
Don't look pretty but works. Can't see when laptop is on it anyway.

---

### Post by haani on 2006-06-21
[QUOTE=gmc]Try **sudo update-alternatives --config java** and make sure everything is pointing to the correct version of Java. I noticed the rssowl (java application) was having troubles here until I straightened out the system and made sure it was trying to use the correct version of Java.

Gord[/QUOTE]
didn't fix it this is what i get after java crashes if i run firefox from terminal:

```
haani@haani-laptop:~$ firefox
#
# An unexpected error has been detected by HotSpot Virtual Machine:
#
#  SIGSEGV (0xb) at pc=0xb1a47d03, pid=10563, tid=2973051824
#
# Java VM: Java HotSpot(TM) Client VM (1.5.0_06-b05 mixed mode, sharing)
# Problematic frame:
# C  [libfontmanager.so+0x2ed03]
#
# An error report file with more information is saved as hs_err_pid10563.log
#
# If you would like to submit a bug report, please visit:
#   http://java.sun.com/webapps/bugreport/crash.jsp
#
INTERNAL ERROR on Browser End: Pipe closed during read? State may be corrupt
System error?:: Success

```

---

### Post by gmc on 2006-06-21
[QUOTE=Frank Golden]Hi Gord,
   See link below for product I use.
[http://www.raindesigninc.com/ilap.html](http://www.raindesigninc.com/ilap.html)
[/QUOTE]

Hey, now that's SMART! I'm not big on purchasing over the internet but if I can't find something like that locally I will. Thanks for the pointer.

Gord

---

### Post by gmc on 2006-06-21
[QUOTE=haani]didn't fix it this is what i get after java crashes if i run firefox from terminal:

```
haani@haani-laptop:~$ firefox
#
# An unexpected error has been detected by HotSpot Virtual Machine:
#
#  SIGSEGV (0xb) at pc=0xb1a47d03, pid=10563, tid=2973051824
#
# Java VM: Java HotSpot(TM) Client VM (1.5.0_06-b05 mixed mode, sharing)
# Problematic frame:
# C  [libfontmanager.so+0x2ed03]
#
# An error report file with more information is saved as hs_err_pid10563.log
#
# If you would like to submit a bug report, please visit:
#   http://java.sun.com/webapps/bugreport/crash.jsp
#
INTERNAL ERROR on Browser End: Pipe closed during read? State may be corrupt
System error?:: Success

```[/QUOTE]

Can you post the URL for the site that's giving you this error. I have Java installed here, I'd like to see if I can duplicate the error. The problem might be between firefox and java, not java itself.

Gord

---

### Post by haani on 2006-06-21
yes its [www.osx86project.org](www.osx86project.org) and than i click on forums login and than click on irc after java applet starts it crashes!!

its not only this site it crashes on every site that has java irc!!

---

### Post by gmc on 2006-06-21
[QUOTE=haani]yes its [www.osx86project.org](www.osx86project.org) and than i click on forums login and than click on irc after java applet starts it crashes!!

its not only this site it crashes on every site that has java irc!![/QUOTE]

Seems ok here. Have you tried installing xchat-gnome? You won't have any trouble joining the OSx86 chat forum. As for Java, I think mine works because I used [Bumps]("http://ubuntuforums.org/showthread.php?t=181251&highlight=bumps") (version 1.1 not 1.25) to install the appropriate plugins for firefox.

You might want to try either or both of the above.

Gord

---

### Post by samir85 on 2006-06-21
[QUOTE=haani]didn't fix it this is what i get after java crashes if i run firefox from terminal:

```
haani@haani-laptop:~$ firefox
#
# An unexpected error has been detected by HotSpot Virtual Machine:
#
#  SIGSEGV (0xb) at pc=0xb1a47d03, pid=10563, tid=2973051824
#
# Java VM: Java HotSpot(TM) Client VM (1.5.0_06-b05 mixed mode, sharing)
# Problematic frame:
# C  [libfontmanager.so+0x2ed03]
#
# An error report file with more information is saved as hs_err_pid10563.log
#
# If you would like to submit a bug report, please visit:
#   http://java.sun.com/webapps/bugreport/crash.jsp
#
INTERNAL ERROR on Browser End: Pipe closed during read? State may be corrupt
System error?:: Success

```[/QUOTE]

Have you installed the java plugin for firefox ?

```
sudo apt-get install sun-java5-plugin
```

---

### Post by Frank Golden on 2006-06-21
[QUOTE=gmc]Hey, now that's SMART! I'm not big on purchasing over the internet but if I can't find something like that locally I will. Thanks for the pointer.

Gord[/QUOTE]
Hi Gord,
    Got mine at CompUSA. $50.00 US. The 15W is what's in picture.
My 5672WLMi overhangs it by about 1cm on front and sides.

---

### Post by gmc on 2006-06-21
[QUOTE=samir85]Have you installed the java plugin for firefox ?
```
sudo apt-get install sun-java5-plugin
```[/QUOTE]

I do, from [http://www.politicalcrossfire.com/ubuntu/dapper](http://www.politicalcrossfire.com/ubuntu/dapper) dapper main non-free. As I recall bumps installed it, along with a ga-jillion other things for firefox.

Gord

---

### Post by gmc on 2006-06-21
[QUOTE=Frank Golden]Hi Gord,
    Got mine at CompUSA. $50.00 US. The 15W is what's in picture.
My 5672WLMi overhangs it by about 1cm on front and sides.[/QUOTE]

Good price, too bad we don't have CompUSA up here in the Great White North :-(. I'm going to check around Computer Alley (my name) for an area here in Toronto where all the decent computer stores live and see if I can find the in-your-lap version of what you have (and see if I can return the place mat without being caught by the missus :-) ).

Gord

---

### Post by Frank Golden on 2006-06-21
[QUOTE=gmc]Good price, too bad we don't have CompUSA up here in the Great White North :-(. I'm going to check around Computer Alley (my name) for an area here in Toronto where all the decent computer stores live and see if I can find the in-your-lap version of what you have (and see if I can return the place mat without being caught by the missus :-) ).

Gord[/QUOTE]
That is the in-your-lap version. It can be used on desk by taking off the 
cylindrical pad on front. That is why there is a strip of velcro already there.
I bet if you have an Apple store in Toronto......

---

### Post by TheBlueCow on 2006-06-21
I'm looking at getting one of these laptops, but I heard that Acer will be releasing one with a X1600 with 256MB in video RAM. It looks like a sweet rig and if it runs Ubuntu well, then all the better =D

---

### Post by gmc on 2006-06-22
Hi Folks,

    I know this problem was mentioned before and another 5672 user recently emailed me and asked about it. Has anyone found a solution for the weak audio / lack of volume in Ubuntu as compared to Windows?

Gord

---

### Post by unz on 2006-06-22
Can you describe your problem with more details?
What does "weak" mean? Speakers aren't the top, but work.
I've never listened to an mp3 in windows, but i think sound works well in linux.
When i connect my laptop to the HI-FI, everything is ok

Maybe gentoo and ubuntu alsa-driver are the same [alsa-driver-1.0.11]
I use alsa and alsa-oss [for skype].
ALSA_CARDS="seq-dummy dummy virmidi mtpav serial-u16550 mpu401 serialmidi loopback hda-intel intel8x0 intel8x0m usb-audio usb-usx2y"
Any particular option in modules.conf.

Ps for the "buzz" while using the touchpad, i decreased "Channel In" volume

EDIT: i got alsa drivers as package, i don't use kernel bundled drivers from 2.6.12 release ...

---

### Post by gmc on 2006-06-22
[QUOTE=unz]Can you describe your problem with more details?
What does "weak" mean? Speakers aren't the top, but work.
I've never listened to an mp3 in windows, but i think sound works well in linux.
When i connect my laptop to the HI-FI, everything is ok

Maybe gentoo and ubuntu alsa-driver are the same [alsa-driver-1.0.11]
I use alsa and alsa-oss [for skype].
ALSA_CARDS="seq-dummy dummy virmidi mtpav serial-u16550 mpu401 serialmidi loopback hda-intel intel8x0 intel8x0m usb-audio usb-usx2y"
Any particular option in modules.conf.

Ps for the "buzz" while using the touchpad, i decreased "Channel In" volume

EDIT: i got alsa drivers as package, i don't use kernel bundled drivers from 2.6.12 release ...[/QUOTE]

If you boot up Windows, you'll notice that the audio is louder volume wise compared the linux set the same volume level. On a personal level, if I have the KDE or GNOME volume all the way up to the 100% mark and try playing a DVD, I can barely hear it, though if I use headphones it's very loud. I manually installed the alsa 1.0.11 drivers (though I was fixing a different problem) doesn't help any.

Gord

---

### Post by haani on 2006-06-22
[QUOTE=samir85]Have you installed the java plugin for firefox ?

```
sudo apt-get install sun-java5-plugin
```[/QUOTE]

ofcourse i have thats y the applet starts to load and than it crashes. i reinstalled ubuntu and than installed java using bumps but still it crahses?? BTW gmc The sound is loud enough in ubuntu..its the same compare to windows

---

### Post by scifan on 2006-06-22
question - 

Is there an easy way to re-map the volume key's to run the front speaker volume control rather than the pcm volume control?

---

### Post by angel12 on 2006-06-22
nope. sorry. ive been trying to get an answer for that same thing for a while. its a bug in gstreamer, jdong has posted bug reports on it. search the thread and you can find links to the reports.

---

### Post by haani on 2006-06-24
java is really annoyin me still crashes..anyways does anyone know how to get scrolls workin on the touchpad and how to switch between Laptop/TV, in windows the hotkey is Fn+F5 but in linux i cant seem to find it??

---

### Post by unz on 2006-06-24
[QUOTE=haani]java is really annoyin me still crashes..anyways does anyone know how to get scrolls workin on the touchpad and how to switch between Laptop/TV, in windows the hotkey is Fn+F5 but in linux i cant seem to find it??[/QUOTE]
i got scrolling and tapping ...
```

Section "InputDevice"
        Identifier  "Synaptics Touchpad"
        Driver      "synaptics"
        Option      "SendCoreEvents" "true"
        Option      "Device" "/dev/psaux"
        Option      "Protocol" "auto-dev"
        Option      "LeftEdge" "1700"
        Option      "RightEdge" "4800"
        Option      "TopEdge" "1700"
        Option      "BottomEdge" "4200"
        Option      "FingerLow" "25"
        Option      "FingerHigh" "30"
        Option      "MaxTapTime" "180"
        Option      "MaxTapMove" "220"
        Option      "VertScrollDelta" "100"
        Option      "MinSpeed" "0.09"
        Option      "MaxSpeed" "0.18"
        Option      "AccelFactor" "0.0015"
        Option      "Emulate3Buttons" "yes"
EndSection

Section "ServerLayout"
        Identifier     "Simple Layout"
        Screen         "Screen 1"       0 0
        InputDevice    "Synaptics Touchpad"             "SendCoreEvents"
        InputDevice    "Mouse1"         "CorePointer"
        InputDevice    "Keyboard1"      "CoreKeyboard"
EndSection

```

---

### Post by haani on 2006-06-24
[QUOTE=unz]i got scrolling and tapping ...
```

Section "InputDevice"
        Identifier  "Synaptics Touchpad"
        Driver      "synaptics"
        Option      "SendCoreEvents" "true"
        Option      "Device" "/dev/psaux"
        Option      "Protocol" "auto-dev"
        Option      "LeftEdge" "1700"
        Option      "RightEdge" "4800"
        Option      "TopEdge" "1700"
        Option      "BottomEdge" "4200"
        Option      "FingerLow" "25"
        Option      "FingerHigh" "30"
        Option      "MaxTapTime" "180"
        Option      "MaxTapMove" "220"
        Option      "VertScrollDelta" "100"
        Option      "MinSpeed" "0.09"
        Option      "MaxSpeed" "0.18"
        Option      "AccelFactor" "0.0015"
        Option      "Emulate3Buttons" "yes"
EndSection

Section "ServerLayout"
        Identifier     "Simple Layout"
        Screen         "Screen 1"       0 0
        InputDevice    "Synaptics Touchpad"             "SendCoreEvents"
        InputDevice    "Mouse1"         "CorePointer"
        InputDevice    "Keyboard1"      "CoreKeyboard"
EndSection

```[/QUOTE]

thanks but i already installed the new synaptics drivers and made my scrollin work!! but now the problem remain is that how to switch between laptop/TV  wots the hotkey in ubuntu, in windows its Fn+F5??? 

and wot software do u use for bluetooth?

**EDIT:** I have fixed my java problem!!!

---

### Post by scifan on 2006-06-26
one other adventure....

I notice that my 5672 exhibits different behavior for hibernation... when it's unplugged from AC it will hibernate correctly... and when it's plugged in it basically just logs out and returns you to the GDM login screen...

Am I the only experiencing this?  The work around that I've figured out is to unplug from AC, wait for a minute and then hibernate... but that doesn't appear to be something that SHOULD be occuring...

Any idea's?

---

### Post by gmc on 2006-06-27
Hi Folks,

Has anyone attempted to install the new ATI drivers yet? I'm wondering about the thermal monitor and if you've gotten it working? Also I took Frank Golden's suggestion to pick up an iLap. Alas I wasn't able to locate one here in Toronto, so I ordered one from RainDesign on Saturday... low and behold, it arrived this morning. 4 days from order to delivery is pretty impressive considering they're in California and I'm up here in the GWN (Great White North). Highly recommended. (Thanks Frank).

Gord

---

### Post by Frank Golden on 2006-06-27
[QUOTE=gmc]Hi Folks,

Has anyone attempted to install the new ATI drivers yet? I'm wondering about the thermal monitor and if you've gotten it working? Also I took Frank Golden's suggestion to pick up an iLap. Alas I wasn't able to locate one here in Toronto, so I ordered one from RainDesign on Saturday... low and behold, it arrived this morning. 4 days from order to delivery is pretty impressive considering they're in California and I'm up here in the GWN (Great White North). Highly recommended. (Thanks Frank).

Gord[/QUOTE]
Hi Gord,
   What ATi drivers? Thermal monitors? I am using a gdesklet CPU monitor
that reads ACPI sensor. I had to add it manually to startup folder to get it
to boot with Ubuntu. It reads within a degree or two of NHC in XP. Don't seem to be any way to change display to °F.  I am after all American, old
and metric chalenged.:shock:
BTW, Glad you like iLap hope it works for you like mine seems to. What did it cost factory direct?

---

### Post by jdong on 2006-06-27
[QUOTE=gmc]Hi Folks,

Has anyone attempted to install the new ATI drivers yet? I'm wondering about the thermal monitor and if you've gotten it working? Also I took Frank Golden's suggestion to pick up an iLap. Alas I wasn't able to locate one here in Toronto, so I ordered one from RainDesign on Saturday... low and behold, it arrived this morning. 4 days from order to delivery is pretty impressive considering they're in California and I'm up here in the GWN (Great White North). Highly recommended. (Thanks Frank).

Gord[/QUOTE]
I am running the new fglrx release right now. Off the top, I can't see anything terribly changed/new; I've yet to play around with it much, but it's working with an Xgl desktop, glxgears inside at 4400FPS.

---

### Post by Frank Golden on 2006-06-27
[QUOTE=jdong]I am running the new fglrx release right now. Off the top, I can't see anything terribly changed/new; I've yet to play around with it much, but it's working with an Xgl desktop, glxgears inside at 4400FPS.[/QUOTE]
Just checked I'm running the latest fglrx also, running great.

---

### Post by jdong on 2006-06-27
Wow, may I comment on how well ATI drivers install! A simple "--buildpkg Ubuntu/dapper" generated dapper debs, and dumped a tbz2 of the fglrx kernel source in /usr/src, while overriding userspace libraries automagically.

---

### Post by gmc on 2006-06-28
[QUOTE=Frank Golden]Hi Gord,
   What ATi drivers? Thermal monitors? I am using a gdesklet CPU monitor
that reads ACPI sensor. I had to add it manually to startup folder to get it
to boot with Ubuntu. It reads within a degree or two of NHC in XP. Don't seem to be any way to change display to °F.  I am after all American, old
and metric chalenged.:shock:
BTW, Glad you like iLap hope it works for you like mine seems to. What did it cost factory direct?[/QUOTE]

Yup, NEW drivers. ATI released [8.26.18]("http://www.ubuntuforums.org/showthread.php?t=204109&highlight=8.26.18") drivers that include a thermal watchdog daemon that clocks the GPU down when it's too hot. Unfortunately there's no way to display that information (yet!).

Total cost for the Ilap was $92cnd which is a bit pricey but considering I can now sit comfortably with the 5672 on my lap and not cooking my ummm.. legs :-) it's worth it.

Gord

---

### Post by Frank Golden on 2006-06-28
[QUOTE=gmc]Yup, NEW drivers. ATI released [8.26.18]("http://www.ubuntuforums.org/showthread.php?t=204109&highlight=8.26.18") drivers that include a thermal watchdog daemon that clocks the GPU down when it's too hot. Unfortunately there's no way to display that information (yet!).

Total cost for the Ilap was $92cnd which is a bit pricey but considering I can now sit comfortably with the 5672 on my lap and not cooking my ummm.. legs :-) it's worth it.

Gord[/QUOTE]
Hey Gord,
   According to ATi site the thermal monitor is a tool used by card to throttle back
proc when heat excedes a preset limit. I bet ATi won't provide tool to read temp, rather someone will (in open source community) have to create app.
BTW, Further checking revealed that I didn't have the latest driver. Used the wiki, [http://wiki.cchtml.com/index.php/Ubuntu_Dapper_Installation_Guide](http://wiki.cchtml.com/index.php/Ubuntu_Dapper_Installation_Guide), method 2 to update. Works Great.

---

### Post by haani on 2006-06-28
i also install the new drivers but the ATI control doesnt work properly says  ```
Driver does not provide the FireGL X11 extensions!
panel components will operate only partially
```

anyone else had this problem i am running it under Xgl!!

---

### Post by Frank Golden on 2006-06-28
Not using Xgl. But I noticed a new ATi control panel (GUI).
Is that what isn't working? Probably related to Xgl judging by
the other posts regarding problems with Xgl.

---

### Post by Frank Golden on 2006-06-29
BTW, Just want to comment that this is an amazing thread. Acer must be 
happy with the sales of the 5672 if this thread and others like it are any
indication of popularity. Info here has been of great use to me, wish I was 
more Ubuntu/Linux savvy so I could help more.

---

### Post by gmc on 2006-06-29
Well Folks,

I took the plunge and installed the 8.26.18 drivers, even after my inner voice was screaming "You'll be sorry..." and reminding me of all the problems I had after installing the release version of 6.06. 

I'm pleased to say, everything went flawlessly. I'm probably imagining it, but it seems the heat problem on the right hand side of the touch pad is considerably lessened.

Gord

---

### Post by gmc on 2006-06-29
[QUOTE=Frank Golden]BTW, Just want to comment that this is an amazing thread. Acer must be 
happy with the sales of the 5672 if this thread and others like it are any
indication of popularity. Info here has been of great use to me, wish I was 
more Ubuntu/Linux savvy so I could help more.[/QUOTE]

I whole heartedly agree. It's nice to be able to say that I'm no longer a guy with BIG eye's and a sad story.
And just for the record, I wouldn't trade my 5672 for a 5002 in a million years :D

Gord

---

### Post by Frank Golden on 2006-06-29
[QUOTE=gmc]Well Folks,

I took the plunge and installed the 8.26.18 drivers, even after my inner voice was screaming "You'll be sorry..." and reminding me of all the problems I had after installing the release version of 6.06. 

I'm pleased to say, everything went flawlessly. I'm probably imagining it, but it seems the heat problem on the right hand side of the touch pad is considerably lessened.


Gord[/QUOTE]

There is supposed to be a 8.28.x release in August I read somewhere.
I used the method 2 in wiki, went flawlessly. I too seem to have less 
heat on right side of touchpad. BTW, Just checked almost all fn+key 
combos seem to work except fn+F2,F3 and F4. Don't know what those
keys are supposed to do anyway. More importantly fn+F7 (shut off
touchpad) works as I use a G-7 gaming mouse. I noticed I don't have any entry in /etc/X11/xorg.conf file for my touchpad. Don't know if I have latest 
software or where to get.

---

### Post by haani on 2006-07-02
anyone know a good bluetooth software?? and how do i setup my bluetooth on ubuntu?

---

### Post by BigMac780 on 2006-07-03
Hey guys first off thank you for having this forum it's been awesome. I've been reading for a long time and I finally need to post some questions. I've been having a hell of a time with the ati drivers. I've followed the directions many times. Now it seems to have worked but i got this message in the install log:
> [Message] Kernel Module : Trying to install a precompiled kernel module.
[Message] Kernel Module : Precompiled kernel module version mismatched.
[Error] Kernel Module : No kernel module build environment - please consult readme.
Note: When I open the installer it only runs in the terminal a graphical installer like on the ATI page does not appear.

I'm new to the linux world. Finally decided to take the plunge. I'm slowly trying to pick up more info everywhere I can.
I could not get the installer to run until i right clicked on the file/properties and then hit the permissions tab and had to toggle the file to allow me to execute it. Is that normal?  
Also I've tried editing and replacing files in the "filesystem" subfolders and i'm always told i do not haver permission. this has proved to be very frustrating when i read about the cool things you guys gave been building and I can't get them. 

Also I have a network drive on my network and when i tried SUSE 10.1 i could access it butnnow with ubuntu i can't access it or the other partitions on my acer. Any Ideas?
Note: I am running Ubuntu off of a 80gig usb HDD not sure i that affects anything.

I love the challenge of working with linux but some pointers would save me a few hours so I can sleep.  

Thank you again for all your help!!!

P.S. Figuring out how to get to the Super User in the terminal took me way to long.......:cry:

---

### Post by gmc on 2006-07-03
Hi Folks,

I see version 1.0.12 & 1.1.0-pre2 ipw3945 drivers are now available. I've tried compiling both (fortunately I saved 1.0.5). Has anyone had success with either of these new drivers? When either is installed and my router is configured for WPA2, the connection rapidly goes up and down.

Gord

---

### Post by haani on 2006-07-04
guys how can i use ati powerplay on xgl my startxgl.sh looks like this

```
xmodmap /usr/share/xmodmap/xmodmap.gb
Xgl -fullscreen :1 -ac -accel glx:pbuffer -accel xv:pbuffer & sleep 2 && DISPLAY=:1
exec gnome-session

```

i did add the xorgAc argument and aticonfig --lsp but my xgl stops working after i add these arguments to startxgl.sh??

---

### Post by gmc on 2006-07-04
Hi Haani,

I cheated! I added the setting that I wanted in the script as follows:

```
xmodmap /usr/share/xmodmap/xmodmap.gb
aticonfig --set-powerstate=1 ; # Set GPU core/mem to 135/135 Mhz
Xgl -fullscreen :1 -ac -accel glx:pbuffer -accel xv:pbuffer & sleep 2 && DISPLAY=:1
exec gnome-session

```

Gord

---

### Post by haani on 2006-07-04
[QUOTE=gmc]Hi Haani,

I cheated! I added the setting that I wanted in the script as follows:

```
xmodmap /usr/share/xmodmap/xmodmap.gb
aticonfig --set-powerstate=1 ; # Set GPU core/mem to 135/135 Mhz
Xgl -fullscreen :1 -ac -accel glx:pbuffer -accel xv:pbuffer & sleep 2 && DISPLAY=:1
exec gnome-session

```

Gord[/QUOTE]

thanks but how can you tell if its workin??

---

### Post by BigMac780 on 2006-07-05
[QUOTE=BigMac780]Hey guys first off thank you for having this forum it's been awesome. I've been reading for a long time and I finally need to post some questions. I've been having a hell of a time with the ati drivers. I've followed the directions many times. Now it seems to have worked but i got this message in the install log:

Note: When I open the installer it only runs in the terminal a graphical installer like on the ATI page does not appear.

I'm new to the linux world. Finally decided to take the plunge. I'm slowly trying to pick up more info everywhere I can.
I could not get the installer to run until i right clicked on the file/properties and then hit the permissions tab and had to toggle the file to allow me to execute it. Is that normal?  
Also I've tried editing and replacing files in the "filesystem" subfolders and i'm always told i do not haver permission. this has proved to be very frustrating when i read about the cool things you guys gave been building and I can't get them. 

Also I have a network drive on my network and when i tried SUSE 10.1 i could access it butnnow with ubuntu i can't access it or the other partitions on my acer. Any Ideas?
Note: I am running Ubuntu off of a 80gig usb HDD not sure i that affects anything.

I love the challenge of working with linux but some pointers would save me a few hours so I can sleep.  

Thank you again for all your help!!!

P.S. Figuring out how to get to the Super User in the terminal took me way to long.......:cry:[/QUOTE]
Seriously no help at all?

---

### Post by gmc on 2006-07-06
Hi BigMac,

[QUOTE=BigMac780]Hey guys first off thank you for having this forum it's been awesome. I've been reading for a long time and I finally need to post some questions. I've been having a hell of a time with the ati drivers. I've followed the directions many times. Now it seems to have worked but i got this message in the install log:

Note: When I open the installer it only runs in the terminal a graphical installer like on the ATI page does not appear.
[/QUOTE]

What graphical installer are you referring to? What errors or problems are being reported? A few more details would be hepful.

> 
I'm new to the linux world. Finally decided to take the plunge. I'm slowly trying to pick up more info everywhere I can.
I could not get the installer to run until i right clicked on the file/properties and then hit the permissions tab and had to toggle the file to allow me to execute it. Is that normal?


Yes, specifically if the file in question is a script or program. Linux uses permissions/groups to determine how to use the file or what to do with it.
  
> 
Also I've tried editing and replacing files in the "filesystem" subfolders and i'm always told i do not haver permission. this has proved to be very frustrating when i read about the cool things you guys gave been building and I can't get them.


Linux (and unices) protect themselves from non-root users changing or damaging the base operating system by implimenting ownership, groups and permissions. The whole permission/group idea is a foreign concept to most new users. I'll see if I can find a decent website that can get you upto speed on how it all works. (I use to have one, but the page is gone).

> 
Also I have a network drive on my network and when i tried SUSE 10.1 i could access it butnnow with ubuntu i can't access it or the other partitions on my acer. Any Ideas? Note: I am running Ubuntu off of a 80gig usb HDD not sure i that affects anything.


No idea specifically. By "network drive" do you mean it's an external USB drive, or is it an intelligent drive you can hang on an ethernet network and access it with SMB/IP address?

> 
I love the challenge of working with linux but some pointers would save me a few hours so I can sleep.  


Learning the underlaying technology for linux (Ubuntu) can be frustrating at first but once you start picking up how things fit together, it's very satisfying.
Keep at it... it took me a year of dual booting between Redhat v5.0 and Windows 98 (back in '97).

Gord

Check [this site]("http://linux.about.com/od/linux101/a/desktop03b.htm"). It's a reasonable introduction to file permissions and groups. Does anyone have a better one?

---

### Post by angel12 on 2006-07-08
well. after many installs of ubuntu, i decided to give kubuntu a try. the main reason for me not to stick with ubuntu on this laptop were the multimedia keys, i know, minor reason, but i use them so much that them not working got to me. So, i tried kubuntu, and am pleased to announce that everything worked out of the box minus some tinkering with the mulimedia key settings, the camera (i dont think its working for any linux distro yet) and the card reader. I can suspend out of the box, and hibernate almost works.

---

### Post by kxgard3 on 2006-07-09
> **angel12 said:**
> well. after many installs of ubuntu, i decided to give kubuntu a try. the main reason for me not to stick with ubuntu on this laptop were the multimedia keys, i know, minor reason, but i use them so much that them not working got to me. So, i tried kubuntu, and am pleased to announce that everything worked out of the box minus some tinkering with the mulimedia key settings, the camera (i dont think its working for any linux distro yet) and the card reader. I can suspend out of the box, and hibernate almost works.

Did wireless work out of the box? The biggest thing holding me back is wireless, well that and the fact that I have a lot of DRM protected music from apple.

---

### Post by angel12 on 2006-07-09
yeah, it worked out of the box, and just like ubuntu, to get the full use of both cores, you need to install the 686 kernel and the 686 restricted modules. 

as for the itunes music, well, im in the same boat, and the only way to get around it is to burn the full cd in itunes in windows, and then import them in linux as an mp3. also, if you are using an itunes version pre-5, you can use jhymn

---

### Post by kxgard3 on 2006-07-10
> **angel12 said:**
> yeah, it worked out of the box, and just like ubuntu, to get the full use of both cores, you need to install the 686 kernel and the 686 restricted modules. 

as for the itunes music, well, im in the same boat, and the only way to get around it is to burn the full cd in itunes in windows, and then import them in linux as an mp3. also, if you are using an itunes version pre-5, you can use jhymn

Okay so I will need to install the 386 build and then upgrade to a 686 kernel right?

---

### Post by Frank Golden on 2006-07-10
Yeah, to use both cores. You can add two CPU freq. applets to
your panel by right clicking panel and choosing add. This will allow you to monitor you cores. After updating to 686 kernel you can configure each applet by right
clicking each and choosing your individual core. For example one applet set to core 0 and the other to core 1. You don't have this option using
the default kernel. Great way to check if both cores are being detected.

---

### Post by mfa81 on 2006-07-10
> **Frank Golden said:**
> Yeah, to use both cores. You can add two CPU freq. applets to
your panel by right clicking panel and choosing add. This will allow you to monitor you cores. After updating to 686 kernel you can configure each applet by right
clicking each and choosing your individual core. For example one applet set to core 0 and the other to core 1. You don't have this option using
the default kernel. Great way to check if both cores are being detected.

i cant find this applet on kde... waht applet should i use on kde ? using top a can see cores 0 and 1

---

### Post by Frank Golden on 2006-07-10
Don't know if KDE (Kubuntu) has a CPU frequency monitor applet.
I'm using gnome (Ubuntu). Maybe a Kubuntu user can help here. I
would think Kubuntu has a similar applet. If not that's too bad 
it is neat tool, shows CPU frequency in real time. I have mine
setup flanking System Monitor applet which shows graph of CPU usage
and when clicked is the same as top command.

---

### Post by jdong on 2006-07-13
In KDE, ksysguard is pretty good. It even has an applet. You'll have to drag on two sensors -- one for processor 0 and one for 1.

---

### Post by gmc on 2006-07-13
Hi Folks,

If you are using Gnome and want to play with the new SLED menu. Here's a blog posting that details how to install it.

[how to add-new-sled-menu-to-ubuntu]("http://angelicpenguins.blogspot.com/2006/07/add-new-sled-menu-to-ubuntu.html").

Pretty neat

Gord

---

### Post by BigMac780 on 2006-07-15
Thank you for replying. I have just sunk many more hours into getting this lap top running. I understand the idea of permissions I just need to know how to be able to change files in the  system folders such as bin. 

As far as the ati errors i posted them on page 43 of this forum. Thanks

---

### Post by marianoi on 2006-07-16
Hello guys,

I just noticed my mic is not working (no sound recorded, I checked the volume control and the mic is on), I could not find the answer scanning the post...

Could you give a hand with this?

THANKS!

Cheers

Marianoi

---

### Post by cville on 2006-07-30
Any news about the Orbicam camera ?

I had a problem with my wireless, every time I start the notebook
the wireless dont start, i need to restart and all go well... any solution ?

Also any news aboutn the SD Smart Card ?

Damn :(

Thanks

---

### Post by angel12 on 2006-07-30
> **cville said:**
> Any news about the Orbicam camera ?

I had a problem with my wireless, every time I start the notebook
the wireless dont start, i need to restart and all go well... any solution ?

Also any news aboutn the SD Smart Card ?

Damn :(

Thanks

the camera is unknown afik. and the sd card, there is a driver out there, i just dont know where, if you look through the thread you may find it. sorry i cant be of much help :(

---

### Post by cville on 2006-07-30
Thanks for your reply, I did try but not success with the compile etc..
Damn .. :(

---

### Post by jdong on 2006-07-30
The tifm21xx open source driver works with the SD card reader, but it needs a 2.6.16+ kernel to compile, so you'll need to compile your own kernel to use it.

Still no drivers for the orbicam yet, though they are promised for the next spca5xx release.

---

### Post by cville on 2006-07-30
Ok, thanks a lot for your fast reply... 
Right now not in mood to change the kernel, I use the automatic upgrade from the ubuntu system.

---

### Post by unz on 2006-07-31
New ati-drivers for last xorg came out ... before nvidia ones ... something is changing? :KS 

c'mon men, are you all on vacation? there are some holes in our notebook ... anyone closed'em?

any advice for:

- Infrared [driver + software]
- bluetooth [driver + software]
- internal modem [driver + software]
- audio problems with skype ... mic and speakers work, but crackling. 

:p

---

### Post by jdong on 2006-08-02
> **unz said:**
> New ati-drivers for last xorg came out ... before nvidia ones ... something is changing? :KS 

c'mon men, are you all on vacation? there are some holes in our notebook ... anyone closed'em?

any advice for:

- Infrared [driver + software]
- bluetooth [driver + software]
- internal modem [driver + software]
- audio problems with skype ... mic and speakers work, but crackling. 

:p


IR And Bluetooth work out-of-the-box already, as far as how to use it, there's plenty of documentation floating around that you can google. If you can't find what you're looking for, ask back for specifics.

The internal modem is a Conexant HDA/HSF modem. Only closed-source Linuxant drivers are available. There is a free download (closed source) that supports 14.4K, but to get full 56K you need to fork over cash to Linuxant.


I don't know about the skype thing.

---

### Post by chantra on 2006-08-04
Hi,

I've just bought an acer with centrino duo core, It seems that the latest -686 kernel doesn't work real good. My lappy suffers freezes and big lags.

Are you having the same troubles?
cheers

---

### Post by tonyr1988 on 2006-08-04
Has anyone got the Orbicam / webcam / camera thingie working yet? I e-mailed Acer support about it. Of course, there aren't any Linux drivers (and "There are no plans to provide Linux drivers or support in the future"), but she gave me the chipset info:

Chipset
 North Bridge:
 915GM/915PM
 South Bridge:
 ICH7M-DH/ICH7M

No idea if that's any use at all - I don't know what to do with it. :) Just wondering what the status on it is - when searching the thread, it doesn't look like it works yet...

---

### Post by jdong on 2006-08-06
> **chantra said:**
> Hi,

I've just bought an acer with centrino duo core, It seems that the latest -686 kernel doesn't work real good. My lappy suffers freezes and big lags.

Are you having the same troubles?
cheers

Hmm, -686 kernels should work well. Sometimes ACPI C3 causes those big lags, so first try setting max_cstate to 2 (which has been described earlier in this thread).


With regards to the camera, I've already stated it twice in this thread, the spca5xx driver is promising support for the next release.

---

### Post by chantra on 2006-08-06
thanks jdong,

I'm giving a try to cstate and will see if there is any changes.

I discovered that in my dmesg:
[17179742.044000] ata1 is slow to respond, please be patient
[17179767.000000] ata1: command 0xa0 timeout, stat 0xd0 host_stat 0x0
[17179767.000000] ata1: translated ATA stat/err 0xd0/00 to SCSI SK/ASC/ASCQ 0xb/47/00
[17179767.000000] sr0: CDROM (ioctl) error, command: <6>Test Unit Ready 00 00 00 00 00 00
[17179767.000000] sr: Current [descriptor]: sense key: Aborted Command
[17179767.000000]     Additional sense: Scsi parity error
[17179768.328000] ata1 failed to respond (30 secs)
[17179768.332000] ata1: status=0x50 { DriveReady SeekComplete }
[17179768.332000] sda: Current: sense key: No Sense
[17179768.332000]     Additional sense: No additional sense information
[17179768.332000] Info fld=0xe4c3de

after any lags.
So it seems this is due to my sata disc not responding quickly :s

---

### Post by unz on 2006-08-07
launching 
```
slmodemd -a --country=ITALY --alsa hw:0
error: mixer setup: Off-hook switch not found for card hw:0
SmartLink Soft Modem: version 2.9.11 Aug  3 2006 21:26:40
symbolic link `/dev/ttySL0' -> `/dev/pts/3' created.
modem `hw:0' created. TTY is `/dev/pts/3'
Use `/dev/ttySL0' as modem device, Ctrl+C for termination.
error: cannot set channels for playback: Invalid argument

```
and then gnome-ppp
```
GNOME PPP: STDOUT: Editing `/dev/null'.
GNOME PPP: STDERR: Modem Port Scan<*1>: S0   
GNOME PPP: STDOUT: 
GNOME PPP: STDERR: ttyS1<*1>: ATQ0 V1 E1 -- failed with 2400 baud, next try: 9600 baud
GNOME PPP: STDOUT: Scanning your serial ports for a modem.
GNOME PPP: STDOUT: 
GNOME PPP: STDERR: ttyS1<*1>: ATQ0 V1 E1 -- failed with 9600 baud, next try: 115200 baud
GNOME PPP: STDERR: ttyS1<*1>: ATQ0 V1 E1 -- and failed too at 115200, giving up.
GNOME PPP: STDERR: Modem Port Scan<*1>: S2   S3   
GNOME PPP: STDERR: ttySL0<*1>: ATQ0 V1 E1 -- failed with 2400 baud, next try: 9600 baud
GNOME PPP: STDERR: ttySL0<*1>: ATQ0 V1 E1 -- OK
GNOME PPP: STDERR: ttySL0<*1>: ATQ0 V1 E1 Z -- OK
GNOME PPP: STDERR: ttySL0<*1>: ATQ0 V1 E1 S0=0 -- OK
GNOME PPP: STDERR: ttySL0<*1>: ATQ0 V1 E1 S0=0 &C1 -- OK
GNOME PPP: STDERR: ttySL0<*1>: ATQ0 V1 E1 S0=0 &C1 &D2 -- OK
GNOME PPP: STDERR: ttySL0<*1>: ATQ0 V1 E1 S0=0 &C1 &D2 +FCLASS=0 -- OK
GNOME PPP: STDERR: ttySL0<*1>: Modem Identifier: ATI -- SmartLink Soft Modem
GNOME PPP: STDERR: ttySL0<*1>: Speed 19200: AT -- OK
GNOME PPP: STDERR: ttySL0<*1>: Speed 38400: AT -- OK
GNOME PPP: STDERR: ttySL0<*1>: Speed 57600: AT -- OK
GNOME PPP: STDERR: ttySL0<*1>: Speed 115200: AT -- OK
GNOME PPP: STDERR: ttySL0<*1>: Speed 230400: AT -- OK
GNOME PPP: STDERR: ttySL0<*1>: Speed 460800: AT -- OK
GNOME PPP: STDOUT: 
GNOME PPP: STDERR: ttySL0<*1>: Max speed is 460800; that should be safe.
GNOME PPP: STDOUT: Found a modem on /dev/ttySL0.
GNOME PPP: STDERR: ttySL0<*1>: ATQ0 V1 E1 S0=0 &C1 &D2 +FCLASS=0 -- OK
GNOME PPP: STDOUT: Modem configuration written to /dev/null.
GNOME PPP: STDERR: ttySL0<Info>: Speed 460800; init "ATQ0 V1 E1 S0=0 &C1 &D2 +FCLASS=0"
```
modem seems found and configured, but if i try to connect i get```
GNOME PPP: STDERR: ttySL0<Info>: Speed 460800; init "ATQ0 V1 E1 S0=0 &C1 &D2 +FCLASS=0"
GNOME PPP: Connessione...
GNOME PPP: STDERR: --> Ignoring malformed input line: ";Do NOT edit this file by hand!"
GNOME PPP: STDERR: --> WvDial: Internet dialer version 1.56
GNOME PPP: STDERR: --> Initializing modem.
GNOME PPP: STDERR: --> Sending: ATZ
GNOME PPP: STDERR: ATZ
GNOME PPP: STDERR: OK
GNOME PPP: STDERR: --> Sending: ATQ0 V1 E1 S0=0 X3 &C1 &D2 +MS=34
GNOME PPP: STDERR: ATQ0 V1 E1 S0=0 X3 &C1 &D2 +MS=34
GNOME PPP: STDERR: OK
GNOME PPP: STDERR: --> Modem initialized.
GNOME PPP: STDERR: --> Sending: ATM1L3DT7027020000
GNOME PPP: STDERR: --> Waiting for carrier.
GNOME PPP: STDERR: ATM1L3DT7027020000
GNOME PPP: STDERR: NO CARRIER
GNOME PPP: STDERR: ERROR
GNOME PPP: STDERR: --> No Carrier!  Trying again.
GNOME PPP: STDERR: --> Sending: ATM1L3DT7027020000
GNOME PPP: STDERR: --> Waiting for carrier.
GNOME PPP: STDERR: ATM1L3DT7027020000
GNOME PPP: STDERR: NO CARRIER
GNOME PPP: STDERR: ERROR
GNOME PPP: STDERR: --> No Carrier!  Trying again.
GNOME PPP: STDERR: --> Sending: ATM1L3DT7027020000
GNOME PPP: STDERR: --> Waiting for carrier.
GNOME PPP: STDERR: ATM1L3DT7027020000
GNOME PPP: STDERR: NO CARRIER
GNOME PPP: STDERR: ERROR
GNOME PPP: STDERR: --> No Carrier!  Trying again.
GNOME PPP: STDERR: --> Maximum Attempts Exceeded..Aborting!!
GNOME PPP: STDERR: --> Disconnecting at Mon Aug  7 20:20:19 2006

```

i'm using hda-intel module

---

### Post by irwin.msstate on 2006-08-07
[http://wiki.cchtml.com/index.php/Ubuntu_Dapper_Installation_Guide#Blacklist_fglrx_module_from_linux-restricted-modules](http://wiki.cchtml.com/index.php/Ubuntu_Dapper_Installation_Guide#Blacklist_fglrx_module_from_linux-restricted-modules)

I followed the instructions here for installing ATI Mobility Radeon x1400 on my acer.

---

### Post by cville on 2006-08-09
> **tonyr1988 said:**
> Has anyone got the Orbicam / webcam / camera thingie working yet? I e-mailed Acer support about it. Of course, there aren't any Linux drivers (and "There are no plans to provide Linux drivers or support in the future"), but she gave me the chipset info:

Chipset
 North Bridge:
 915GM/915PM
 South Bridge:
 ICH7M-DH/ICH7M

No idea if that's any use at all - I don't know what to do with it. :) Just wondering what the status on it is - when searching the thread, it doesn't look like it works yet...

Something wrong here :) This is the intel video card in some acer model not on 5672 :)

---

### Post by dappervaz on 2006-08-09
I have the 5562WXMi i first installed Kubuntu and Bluetooth worked out of the box but when I installed Ubuntu 6.06 the bluetooth does not show up even in the devices. I m quite new can I have some advice?

---

### Post by mfa81 on 2006-08-09
> **unz said:**
> New ati-drivers for last xorg came out ... before nvidia ones ... something is changing? :KS 
:p

whats the last version of ati-drivers ?

---

### Post by dappervaz on 2006-08-09
Use [http://easyubuntu.freecontrib.org/get.html](http://easyubuntu.freecontrib.org/get.html) to get the ATI working on your system

---

### Post by zeca_pedra on 2006-08-12
Hi there!
I also received one of these laptops in my service and I installed XP and Ubuntu 6.06 on dual boot.
Although the installation went very well now I'm noticing that my Ubuntu it's not taking the most out of my ATI 512MB graphics card.
I think I've followed almost every HowTo found here at ubuntuforums trying to solve that problem with no luck at all.

Things are:
fglrxinfo gives me

[HTML]display: :0.0  screen: 0
OpenGL vendor string: Mesa project: [www.mesa3d.org](www.mesa3d.org)
OpenGL renderer string: Mesa GLX Indirect
OpenGL version string: 1.2 (1.5 Mesa 6.4.1)[/HTML]

lspci | grep ATI gives me
[HTML]
0000:01:00.0 VGA compatible controller: ATI Technologies Inc: Unknown device 7145
[/HTML]
glxinfo | grep rendering returns this:
[HTML]
direct rendering: No
[/HTML]

I don't know what else to do. I believe my problems all started when I wanted to experiment XGL and Compiz and followed an HowTo on these forums but now I'm not sure if ATI was working even before that (since only recently I typed these commands to see what was going on - fglrxinfo, glxgears, glxinfo... )

Any ideas? I believe I have to get ride of mesa but don't know how.
I should know better how to deal with these issues since I'm dual booting XP and Ubuntu more than one year ago but I just got stucked into this ATI problem since this is totally new for me (on my wife's desktop we've NVIDIA MX440 and I loved that graphics card, since it was so easy to config and work with)

Thanks in advance for any suggestion taht you may have,
Zeca

------------------------------------------------------------------
Laptop specs:
Acer Aspire 5672WLMi
Intel Core Duo T2300 1.66 Ghz 2MB L2 Cache
15.4'' WXGA Lcd
ATI Radeon X1400 512MB
100 GB 5400 rpm SATA HDD
1GB DDR2 ram
802.11 wireless LAN

---

### Post by zeca_pedra on 2006-08-12
Ok, problem solved!
Now when I type fglrxinfo it returns:
[HTML]display: :0.0  screen: 0
OpenGL vendor string: ATI Technologies Inc.
OpenGL renderer string: ATI Mobility Radeon X1400 Generic
OpenGL version string: 2.0.5946 (8.27.10)[/HTML]
What I did?
1) Installed the proprietary ATI drivers from [their site]("https://support.ati.com/ics/support/default.asp?deptID=894&task=knowledge&folderID=27"), following their instructions;
2) After that I realised I still have the «mesa» problem (driver didn't installed properly, mesa stayed over it);
3) I found a thread in these forums (but forgot to pointed out so that I could pass the word :( )
4) Anyway, the only two things I had to do, according to that post were:
[HTML]sudo depmod
modprobe fglrx[/HTML]
Once I rebooted I had the info on the ATI driver that I told you above and I have direct rendering and glxgears give me an average of 125.594 FPS

I believe it's all ok now? Or am I being too much optimist? 
Can you help me understanding these results?

Thank you for all the people here sharing their knowledge and helpful advises on using and learning linux :grin: 
Without your help I'll be in the dark for ages...

Zeca

---

### Post by jdong on 2006-08-14
Hmm, 125fps sounds low. I get around 1800-1900fps.

jdong@coreduo:~$ glxinfo  | grep rendering
direct rendering: Yes


Direct rendering should be Yes, unless you are using XGL, then the numbers you're reporting may be normal.

---

### Post by Frank Golden on 2006-08-15
> **jdong said:**
> Hmm, 125fps sounds low. I get around 1800-1900fps.

jdong@coreduo:~$ glxinfo  | grep rendering
direct rendering: Yes


Direct rendering should be Yes, unless you are using XGL, then the numbers you're reporting may be normal.

[http://wiki.cchtml.com/index.php/Glxgears_is_not_a_Benchmark](http://wiki.cchtml.com/index.php/Glxgears_is_not_a_Benchmark)
If direct rendering is yes everything is ok.
Use commands at bottom of the aboved linked page instead.

---

### Post by jdong on 2006-08-16
glxgears is not a benchmark, but on identical hardware setups it could expose configuration problems... And being off by an order of magnitude is a very significant difference, unlike being off by a couple FPS.

---

### Post by dappervaz on 2006-08-16
I cant power up my wireless or bluetooth so they dont are not working, Is there any way I can power them Up . Turning on the button does not work

---

### Post by Frank Golden on 2006-08-16
> **jdong said:**
> glxgears is not a benchmark, but on identical hardware setups it could expose configuration problems... And being off by an order of magnitude is a very significant difference, unlike being off by a couple FPS.
Ok jdong,
   Since we both have same hardware (see my sig) and I too get 
about 128 FPS, explain how you get such high numbers.
I am using the latest fglrx from the ATi wiki(second method).
fglrxinfo shows that I am using ATi not Mesa. Glxinfo shows
direct rendering yes. What's your secret. I don't appear to have any display issues or any thing.

---

### Post by jdong on 2006-08-16
Hmm, strange, I retract my statements -- now I'm getting around 248FPS. I have no idea how that happened or why my original numbers were so high.


I'm running a self-compiled 2.6.17.8 kernel, latest ATI drivers installed with the ATI installer, and my xorg.conf has already been posted in this thread, so I have no secrets :)

---

### Post by Frank Golden on 2006-08-16
> **jdong said:**
> Hmm, strange, I retract my statements -- now I'm getting around 248FPS. I have no idea how that happened or why my original numbers were so high.


I'm running a self-compiled 2.6.17.8 kernel, latest ATI drivers installed with the ATI installer, and my xorg.conf has already been posted in this thread, so I have no secrets :)
I think that's what the author of the article about glxgears not being a benchmark is talking about. I haven't been able to create a custom self compiled 2.6.17 kernel. Tried awhile ago failed? Still using the 2.6.15.

---

### Post by jdong on 2006-08-17
Interesting... I've traditionally been a 100% NVidia person, and I can say that FPS'es stay within the same order of magnitude no matter what you do :D

Maybe things are different with ATI... oh well.

Originally, I thought the author just meant what most of us already know: GLXGears is not 3DMark or UT2004's FPS display. You can't use something as simple as GLXGears to compare the performance between two video card models or two different computers.

---

### Post by FreeWill on 2006-08-18
I am a Linux rookie this is my cpu
Acer Aspire 5672WLMi, Core Duo (T2300), 120 GB SATA HDD, 2 GB DDR2-PC5300 ram, ATi Radeon
X1400/128 MB vram, XP-SP2 Pro/Kubuntu 6.06.1 LTS (dual)

When I tried install the ATI driver I get this

fglrxinfo
Xlib:  extension "XFree86-DRI" missing on display ":0.0".
display: :0.0  screen: 0
OpenGL vendor string: Mesa project: [www.mesa3d.org](www.mesa3d.org)
OpenGL renderer string: Mesa GLX Indirect
OpenGL version string: 1.2 (1.5 Mesa 6.4.1)

does anyone have a fix thanks I am sorry if this is trivial I am a rookie

---

### Post by YourDoom123 on 2006-08-19
sorry to bring up an old part of this thread, but I found a fix for people wanting to use jdong's acpi fixing stuff, but also want to use Xgl. First, create the nonXgl script as so: [http://www.ubuntuforums.org/showthread.php?t=176636](http://www.ubuntuforums.org/showthread.php?t=176636)

then, you need to modify the /etc/acpi/fglrx-powermode.sh file. 

```

sudo gedit /etc/acpi/fglrx-powermode.sh

```

find the block of code that looks like so:

```

if [ ${lid_closed} -eq 1 -o ${on_dc} -eq 1 ]; then
    echo "fglrx: setting low power"
    for x in /tmp/.X11-unix/*; do
	displaynum=`echo $x | sed s#/tmp/.X11-unix/X##`
	getXuser;
	if [ x"$XAUTHORITY" != x"" ]; then
	    export DISPLAY=":$displaynum"	    
	    powermode=`/usr/bin/aticonfig --lsp | grep -m1 low | cut -f1 -d:`
	    if [ x"$powermode" != x"" ]; then
	        su $user -c "/usr/bin/aticonfig --set-powerstate=$powermode --effective=now" &>/dev/null
	    fi
	fi
    done
else
    echo "fglrx: setting default powermode"
    for x in /tmp/.X11-unix/*; do
	displaynum=`echo $x | sed s#/tmp/.X11-unix/X##`
	getXuser;
	if [ x"$XAUTHORITY" != x"" ]; then
	    export DISPLAY=":$displaynum"
	    powermode=`/usr/bin/aticonfig --lsp | grep -m1 default | cut -f1 -d:`
	    if [ x"$powermode" != x"" ]; then
	        su $user -c "/usr/bin/aticonfig --set-powerstate=$powermode --effective=now" &>/dev/null
	    fi
	fi
    done
fi

```

and modify it to look like this:
```

if [ ${lid_closed} -eq 1 -o ${on_dc} -eq 1 ]; then
    echo "fglrx: setting low power"
    for x in /tmp/.X11-unix/*; do
	displaynum=`echo $x | sed s#/tmp/.X11-unix/X##`
	getXuser;
	if [ x"$XAUTHORITY" != x"" ]; then
	    export DISPLAY=":$displaynum"	    
	    powermode=`nonXgl /usr/bin/aticonfig --lsp | grep -m1 low | cut -f1 -d:`
	    if [ x"$powermode" != x"" ]; then
	        su $user -c "/usr/bin/aticonfig --set-powerstate=$powermode --effective=now" &>/dev/null
	    fi
	fi
    done
else
    echo "fglrx: setting default powermode"
    for x in /tmp/.X11-unix/*; do
	displaynum=`echo $x | sed s#/tmp/.X11-unix/X##`
	getXuser;
	if [ x"$XAUTHORITY" != x"" ]; then
	    export DISPLAY=":$displaynum"
	    powermode=`nonXgl /usr/bin/aticonfig --lsp | grep -m1 default | cut -f1 -d:`
	    if [ x"$powermode" != x"" ]; then
	        su $user -c "/usr/bin/aticonfig --set-powerstate=$powermode --effective=now" &>/dev/null
	    fi
	fi
    done
fi

```

in case you can't find the differences, what's changed is just 2 lines. the first is in the first half of the major if block (ie the first half of the code). where you see the variable called powermode being set (powermode= 'blah blah blah') change it so that the first command inside the ' ' is nonXgl. Do the same in the second half of the code. And wala, fixed. Warning, this might make Xgl unstable on battery power.

jdong, instead of the ondemand power mode, why not use conservative? That way, the touchpad doesn't get so hot, but you still get the juice you need.

---

### Post by jdong on 2006-08-19
Well, I chose ondemand because conservative doesn't bounce up as fast. At times you can notice a performance hit, which is something that I didn't want users to feel.

---

### Post by anionline on 2006-08-20
I have installed Ubuntu Dapper in my Acer 5672, and have obtained that almost all whole works to me correctly. Single I have some problems to see if somebody can help me.  
I have installed KMobiletools and moto4lin, but profit not to make them work by means of bluetooth. How do do that?

    Somebody has managed to make work webcam?

    From already thank you very much. 

PD: sorry for my bad english.:(

---

### Post by jdong on 2006-08-20
Webcam is still not supported yet.

---

### Post by cbudden on 2006-08-20
> **jdong said:**
> Webcam is still not supported yet.


I know this probably has been discussed before, but iirc, webcam drivers are in developement right?

If they are then I will spend an extra £40 for the model with camera, bluetooth and extra 20gb.

Thanks

---

### Post by jdong on 2006-08-20
Michael Xhaard, the lead developer of the spca5xx (now the gspca) driver, has promised support on the driver's mailing list, so yes, there is active interest in developing a driver for this chipset.

---

### Post by cbudden on 2006-08-20
> **jdong said:**
> Michael Xhaard, the lead developer of the spca5xx (now the gspca) driver, has promised support on the driver's mailing list, so yes, there is active interest in developing a driver for this chipset.

Thanks, that is great news.

---

### Post by jdong on 2006-08-21
[ftp://ftp.acer-euro.com/notebook/aspire_5620_5670/bios/3234.zip](ftp://ftp.acer-euro.com/notebook/aspire_5620_5670/bios/3234.zip)

FYI, new BIOS update released today. I've applied it, and so far everything looks unchanged. From the changelog, it seems to be mostly thermal work:

```

#========================================================================#

|  Version: 0.32        Date : 08/14/2006    Author:Anda Chen            |

|------------------------------------------------------------------------|

|  1.Add disable instant off in post time .											 |

#========================================================================#



#========================================================================#

|  Version: V0.31       Date : 05/18/2006     Author:Joms Kuan           |

|------------------------------------------------------------------------|

|  1.Fixed can't execute 591PCU 					 |

#========================================================================#



#========================================================================#

|  Version: V0.30       Date : 05/16/2006     Author:Anda Chen           |

|------------------------------------------------------------------------|

|  1.Modify SW shutdown 100 degrees					 |

|  2.Add 6C Command A0~A8 for thermal tools				 |

#========================================================================#



#========================================================================#

|  Version: V0.29       Date : 05/15/2006     Author:Anda Chen           |

|------------------------------------------------------------------------|

|  1.Modify TJ85 thermal table						 |

#========================================================================#


```

---

### Post by Drife on 2006-08-24
Hi!
I am a new user of ubuntu but have been using Linux since 1997 (kernel 2.0).
I just purchaste an Acer 5672 and installed ubuntu since it is supposed
to be great on hardware recognition. I, however, seem to have a problem few of you guys have. I have no sound, I never get a single beep or scratch out of my speakers. I have dual boot and I know the soundcard works since it works great in W$. 
The soundcard is recognised as an Intel HD Audio
output of lspci is (the important line)
0000:00:1b.0 Audio device: Intel Corporation 82801G (ICH7 Family) High Definition Audio Controller (rev 02)

Not just that, _everything_ seems to be working.. soundcontrol,
device listings etc. etc. But there is never a single sound from
the speakers (or headphones for that matter).
I have been able to play sounds in my VoIP phone (pk1-phone) so
everything is not screwed up.

The thing is that in my Acer the soundcard is a RealTek but ought to be
Intel HDA compatible.
I have tried with the driver package from RealTek's webpage (working suberp in W$) but not a sound in Linux.

I read on alsa's homepage that the release 1.0.12?? have some updates on
Intel HDA in the changelog. But installing them from scratch needs a new vanilla compiled kernel and everything else works great (ATI-gfx, wireless etc) so I would prefer not to go in to all the trouble with kompiling my own kernel just yet (I sure will in some distant future to optimize my lappie but not now). 
I know have the following questions:

Has anyone else experianced the same problem and found a solution?
Has anyone installed the new alsa-drivers 1.0.12rc* and would
like to comment?

All suggestions are of course encouraged!

Best regards
/Ola

---

### Post by snofix on 2006-08-24
Hi,

i have an Acer Aspire 5672 and had the same problems with the sound, the problem is a bug in alsa-driver.
The developers have allready fixed this bug a few days ago, just check out this link for more details:
[https://bugtrack.alsa-project.org/alsa-bug/view.php?id=2104](https://bugtrack.alsa-project.org/alsa-bug/view.php?id=2104)

My suggestion is to download the alsa-driver-1.0.12rc3 source and patch (you can find the patch-file when you follow the link above).
Then compile the driver and you will have sound - actually it worked for me :)

You can also wait for the final alsa-driver version 1.0.12, the patch should then be included.

greetz,
snofix

---

### Post by jdong on 2006-08-24
Are you guys sure about the sound issues? Sound worked fine out-of-the-box on my 5672, both with Dapper and latest vanilla kernels. In fact, I was just on a 6.06.1 livecd yesterday listening to music.

---

### Post by snofix on 2006-08-24
hm, that's interesting... when you take a look at the alsa-bugtrack link above you can see that many acer-users experienced sound-problems, so there's definitely a bug.
I just know that I didn't have sound out-of-the box, but after installing the newest alsa-driver with patch it works find.

---

### Post by Drife on 2006-08-24
Thanx snofix!!
The sound is working now and I'm a happy puppy!
They released 1.0.12 a couple of hours ago but it didn't seem
to work. Didn't do any tweaking though, just settled for the
working patch to 1.0.12rc3.

Thanx again!
/Drife

---

### Post by snofix on 2006-08-24
i was quite happy too :) took my more than 1 week to get the soundcard working on my acer aspire

for any reason the patch didn't make it into ALSA 1.0.12 final (see lodp's comment in [this thread]("http://www.ubuntuforums.org/showthread.php?t=202555&page=5"))

---

### Post by Frank Golden on 2006-08-24
Hi All,
  Odd, I had sound out of box with my onboard sound card.
Of course since I use a USB external sound card (Creative Audigy 2 NX) with my 5672 (I use my laptop as a desktop) I was getting
occasional conflicts. I had just the opposite problem, kinda.
About 1 out of 4 bootups would use the internal card regardless
of whether the default was set to my USB card or not.
The fix I "blacklisted" my internal sound card. For me, in this distro sound has not been a real issue. The only real problems
have been no Orbicam and no 5 in 1 card support. I can live with that. I am using XP dual boot so if needed I can boot to XP
and use those hardware items. As soon as those items are fixed
I will try to do without M$.:)

---

### Post by dude051 on 2006-08-24
All I gotta say, is wow! Ubuntu rocks! I've owned this laptop going on 4 months now and have been dieing to install a linux distro on it. Debian etch, FC5 and Gentoo all refused to even install. I had to resort to older distros and in turn most of the time got stuck trying to compile my own kernel and work every single thing by hand. Only thing I got actually working was Debian Sarge, 2.6.16 SMP custom kernel and I couldnt even get my sound to work. This was after a week or more of hard work too :(

If was a few days ago I had some friends mention Ubuntu and how it worked so well out-of-the-box. So I gave it a go. I installed Dapper 6.06 and even in the Live-CD I had everything from working VESA video, to perfect ethernet and sound!! I was floored. The install went just as smooth and within the night I had the new ATI drivers in with hardware acceleration, the SMP kernel and wireless working all flawlessly :D   One note I want to absolutly congradulate the devs about is the ipw3945d was working out of the box for my wireless. I had gotten installing ieee to the daemon down pat in other distros (which still wouldnt work perfect), but I happened to look down and saw the LED blinking... again my jaw dropped, and I went to the wireless config to set the essid and I was in business! 

Things I have yet working though are:
Synaptics Touchpad (properly with all the features)
5in1 Card Reader

Firewire and Bluetooth seem to be working, but I dont have anything to test them with. As for the Synaptics Touchpad drivers, Ubuntu installed the X11 drivers and I added the config to my xorg.conf but I still just have "touch" capabilities. It gets rather annoing when trying to scroll or just move as its sensitive and clicks/drags random things. I've also noted that in my xorg.conf there is input devices for Tablet PC Only devices... things like eraser and the pen? Is this normal, I can't find too much info about that.

Again thanks to everyone, this dev is awesome and this forum has helped tons.

---

### Post by jdong on 2006-08-24
Yeah, Dapper virtually works out of the box on this laptop, which is amazing given that the hardware was just fresh out on the market when Dapper was released! ipw3945 was frantically put in at the last few weeks, as was the necessary ATI drivers.

As far as the 5-in-1, there are experimental drivers (which I have linked to in this thread... dig around a bit!) that provide at least SD/MMC support, but they will require a 2.6.16+ kernel that you must compile yourself. Or, wait till Edgy comes out to use it.

---

### Post by Frank Golden on 2006-08-24
> **dude051 said:**
> All I gotta say, is wow! Ubuntu rocks! I've owned this laptop going on 4 months now and have been dieing to install a linux distro on it. Debian etch, FC5 and Gentoo all refused to even install. I had to resort to older distros and in turn most of the time got stuck trying to compile my own kernel and work every single thing by hand. Only thing I got actually working was Debian Sarge, 2.6.16 SMP custom kernel and I couldnt even get my sound to work. This was after a week or more of hard work too :(

If was a few days ago I had some friends mention Ubuntu and how it worked so well out-of-the-box. So I gave it a go. I installed Dapper 6.06 and even in the Live-CD I had everything from working VESA video, to perfect ethernet and sound!! I was floored. The install went just as smooth and within the night I had the new ATI drivers in with hardware acceleration, the SMP kernel and wireless working all flawlessly :D   One note I want to absolutly congradulate the devs about is the ipw3945d was working out of the box for my wireless. I had gotten installing ieee to the daemon down pat in other distros (which still wouldnt work perfect), but I happened to look down and saw the LED blinking... again my jaw dropped, and I went to the wireless config to set the essid and I was in business! 

Things I have yet working though are:
Synaptics Touchpad (properly with all the features)
5in1 Card Reader

Firewire and Bluetooth seem to be working, but I dont have anything to test them with. As for the Synaptics Touchpad drivers, Ubuntu installed the X11 drivers and I added the config to my xorg.conf but I still just have "touch" capabilities. It gets rather annoing when trying to scroll or just move as its sensitive and clicks/drags random things. I've also noted that in my xorg.conf there is input devices for Tablet PC Only devices... things like eraser and the pen? Is this normal, I can't find too much info about that.

Again thanks to everyone, this dev is awesome and this forum has helped tons.
It's almost like Ubuntu was made for this laptop isn't it.:) It wasn't always (read the first post of this thread). My first experience was with Breezy live CD. I had got Breezy running fine on a HP Centrino laptop but had trouble getting it to run on my 5672. Downloaded Flight 5 or 6 Dapper beta and bingo.
Now running Ubuntu 6.06.1 LTS. Still have to change to the 686smp
kernel and install ATi drivers on a fresh install. No biggie.
Haven't had to fresh install since discovering partimage
on the linux SystemRescueCD. I now make an image after every 
major update proves out. I have one right after initial install and customization also. Great backup.

---

### Post by dude051 on 2006-08-25
Dapper really does feel like it was made for this laptop, I have looked through as much of the previous post that I could and see a lot of work has gone into it. 
I might look into the 5-in-1 drivers, not too important, but would be nice to make it 100%. Just got the touchpad working, and I also just installed xgl. WOW this awesome.

Frank, if you havent installed the 686 SMP or latest ATI drivers for xorg 7, you should. The 686 SMP really made a speed difference. And the ATI drivers have excellent acceleration.. esp on my new toy, xgl hehe.

---

### Post by Frank Golden on 2006-08-25
> **dude051 said:**
> Dapper really does feel like it was made for this laptop, I have looked through as much of the previous post that I could and see a lot of work has gone into it. 
I might look into the 5-in-1 drivers, not too important, but would be nice to make it 100%. Just got the touchpad working, and I also just installed xgl. WOW this awesome.

Frank, if you havent installed the 686 SMP or latest ATI drivers for xorg 7, you should. The 686 SMP really made a speed difference. And the ATI drivers have excellent acceleration.. esp on my new toy, xgl hehe.
I got all that except the xgl. Should try xgl I guess. The first thing I do on a fresh install is install the 686smp and ATi drivers. Since using partimage I have a fully customized image to restore to my 
Ubuntu if I screw it up.

---

### Post by jdong on 2006-08-25
It seems like BIOS 3234 has modified the thermal control behavior on the laptop similar to what the MacBooks are doing. The fan comes on at lower temps and stays on low-speed longer. To me, it seems like it's helping with the bottom heating up after long periods of time being on.

---

### Post by Frank Golden on 2006-08-25
> **jdong said:**
> It seems like BIOS 3234 has modified the thermal control behavior on the laptop similar to what the MacBooks are doing. The fan comes on at lower temps and stays on low-speed longer. To me, it seems like it's helping with the bottom heating up after long periods of time being on.
That's interesting jdong. I got it installed on my machine the other day. Haven't really noticed a big difference. My machine
stays pretty cool anyway. Can't wait to transplant a 2.0 GHz
Merom in this beast. I'm ready for it.:mrgreen: Kinda looks
like Intel is making a comeback with this new architecture.

---

### Post by jdong on 2006-08-25
Wow, tell us how that merom works out for you!

As for me, I'm considering making another laptop purchase in a year or so much in the same fashion as this one.... Definitely Acer will be on top of the list of brand names I will consider.


Kudos to Intel... I don't see much of a motivation for me to buy a desktop anymore :)

---

### Post by snofix on 2006-08-25
...just curious to know how hot (or cool) you cpu gets in idle mode using the new BIOS version?

---

### Post by jdong on 2006-08-25
Well, right now it's been on for about 50 hours, and the CPU temp is reported at 60 degrees.

---

### Post by Frank Golden on 2006-08-25
> **jdong said:**
> Well, right now it's been on for about 50 hours, and the CPU temp is reported at 60 degrees.
Wow mine never gets that hot. I get around 120-130°F during idle
or moderate use. When I'm really pushing it I have seen it hit
140-145°F. No fancy laptop coolers, just an aluminum device
called an iLap that helps keep the laptop off the desk a couple of inches, promoting airflow. 

[http://i30.photobucket.com/albums/c338/fjgold/100_0083.jpg](http://i30.photobucket.com/albums/c338/fjgold/100_0083.jpg)

The small holes I added, along with the brass brackets at the botton edges.
I never leave my machine on for overnight or when I go out.
You got more courage than I jdong. 

I expect to see the Meroms become available soon, will report here.

---

### Post by jdong on 2006-08-25
My temp readings are in celcius, so they aren't far from yours, actually.

The heat levels this laptop reaches look concerning, but the cooling system handles it quite well. Intels in general are quite heat tolerant, unlike AMD's. Before buying this laptop, I did read some complaints about the passive cooling policy, so at a local store I did CPUBurn the laptop for around 6 hours (while I played with the then-new Macbook Pros) and it survived just fine.


I've been recently using this laptop as my primary system... I am replacing our family PC with my AMD64 shuttle because it was just simply too old. (sadly, it meant replacing Ubuntu with XP, but that's another story). I've been keeping this system on 24/7 for quite some time now. As I said, I only need for this system to last me around a year, so I'm gonna use it to its full potential until then :)

---

### Post by Frank Golden on 2006-08-25
> **jdong said:**
> My temp readings are in celcius, so they aren't far from yours, actually.

The heat levels this laptop reaches look concerning, but the cooling system handles it quite well. Intels in general are quite heat tolerant, unlike AMD's. Before buying this laptop, I did read some complaints about the passive cooling policy, so at a local store I did CPUBurn the laptop for around 6 hours (while I played with the then-new Macbook Pros) and it survived just fine.


I've been recently using this laptop as my primary system... I am replacing our family PC with my AMD64 shuttle because it was just simply too old. (sadly, it meant replacing Ubuntu with XP, but that's another story). I've been keeping this system on 24/7 for quite some time now. As I said, I only need for this system to last me around a year, so I'm gonna use it to its full potential until then :)
Yeah I'm also using my 5672 as a desktop replacement. I don't own a desktop.:) Probably never will. This is a great notebook, runs Ubuntu very well
and does everything I want. It will be a screamer with Merom.
I don't game so the x1400 radeon works great for me.

---

### Post by jdong on 2006-08-25
You and I are much alike. I honestly have not used this video card at all except for some Xgl fun, which can be done with an intel GMA, and UT2004/3dmark the first few days just for benchmarking purposes.

I don't game. I just need a computer that keeps up with my CPU/RAM-intensive work patterns. And this system works far better in that regards than any other system in my house.

---

### Post by Frank Golden on 2006-08-25
> **jdong said:**
> You and I are much alike. I honestly have not used this video card at all except for some Xgl fun, which can be done with an intel GMA, and UT2004/3dmark the first few days just for benchmarking purposes.

I don't game. I just need a computer that keeps up with my CPU/RAM-intensive work patterns. And this system works far better in that regards than any other system in my house.
Yeah, we both are Michiganders too. What part of Michigan are you from? I am a transplant though. I'm originally a downeaster. Born and grew up in Brunswick, Maine.
I love Michigan though. Been here for 15-16 years.

---

### Post by jdong on 2006-08-25
I live in the metro detroit area. I'm gonna be moving over to Boston to attend college in MIT soon though :)

---

### Post by Frank Golden on 2006-08-25
> **jdong said:**
> I live in the metro detroit area. I'm gonna be moving over to Boston to attend college in MIT soon though :)
Cool, Be aware Boston is a nice old New England town but navigating the streets can be daunting to say the least. The city was built on "cowpaths".
It wasn't laid out and engineered like newer cities. A lot of the streets are narrow and winding. They do have great rapid transit. Lot's of old history in New England. Personally I would rather have, two root canals and a vasectomy without anasthesia than live in Detroit or Boston or any large city.:p 
Where I live in Michigan is at the lower end of Lake Michigan in a largely rural or suburban area. I am within 5 miles of DC Cook nuclear station and 25 miles of Palisades nuclear station. I am a contractor (valve repair tech) in the US nuclear industry and have worked many refuel outages at both these plants as well as Fermi2 just south of you. As a matter of fact I just completed a 5 month assignment at Fermi2 in June. Ran up to Detroit a lot during that time, mostly to the MGM Grand casino.:(  One of the reasons I live here is that I am close to many northern nukes and better positioned to the other 103 US nukes. Been doing this work for 20+ years. Been all over the country. Anyway good luck at MIT. Great school.

---

### Post by jdong on 2006-08-26
[http://kernel.org/git/?p=linux/kernel/git/bcollins/ubuntu-dapper.git;a=commit;h=a1f540b44e934bba867fefc6eb94d9ebd2d7c1b0](http://kernel.org/git/?p=linux/kernel/git/bcollins/ubuntu-dapper.git;a=commit;h=a1f540b44e934bba867fefc6eb94d9ebd2d7c1b0)

Good news, Dapper's kernel is getting a backported version of the Core Duo scheduler from 2.6.17. This should boost performance a bit for us.

---

### Post by Frank Golden on 2006-08-26
> **jdong said:**
> [http://kernel.org/git/?p=linux/kernel/git/bcollins/ubuntu-dapper.git;a=commit;h=a1f540b44e934bba867fefc6eb94d9ebd2d7c1b0](http://kernel.org/git/?p=linux/kernel/git/bcollins/ubuntu-dapper.git;a=commit;h=a1f540b44e934bba867fefc6eb94d9ebd2d7c1b0)

Good news, Dapper's kernel is getting a backported version of the Core Duo scheduler from 2.6.17. This should boost performance a bit for us.
A comment and a question. Two part comment 1) why can't they
backport the entire 2.6.17 kernel 2) I don't know if the Core Duo(Yonah)has shared cache. I know Merom has as a feature. From what
I've read it allows the cores to share each others cache without
a round trip to system memory. Maybe I should read the "white paper" on Yonah.

Question if it (patch) applies to our machines how to get?

---

### Post by jdong on 2006-08-26
> **Frank Golden said:**
> A comment and a question. Two part comment 1) why can't they
backport the entire 2.6.17 kernel

Because it's a huge monumental task with rippling effects everywhere. If you think a lot of people had problems with that xorg-server-core patch, you'd be really entertained to see how many systems can be broken by a kernel upgrade.

> 
 2) I don't know if the Core Duo(Yonah)has shared cache. I know Merom has as a feature. From what
I've read it allows the cores to share each others cache without
a round trip to system memory. Maybe I should read the "white paper" on Yonah.

Yes, the Core Duo has 2MB shared cache. It's one of the most significant features of the Intel Core architecture. Merom basically adds faster clock speeds, 64-bit extensions, and I don't remember off the top of my head what else (SSE4?).

> 

Question if it (patch) applies to our machines how to get?
I suggest waiting :). They will be included in the next kernel update, which will happen when a kernel security vulnerability is discovered.

---

### Post by Frank Golden on 2006-08-26
> **jdong said:**
> Because it's a huge monumental task with rippling effects everywhere. If you think a lot of people had problems with that xorg-server-core patch, you'd be really entertained to see how many systems can be broken by a kernel upgrade.


Yes, the Core Duo has 2MB shared cache. It's one of the most significant features of the Intel Core architecture. Merom basically adds faster clock speeds, 64-bit extensions, and I don't remember off the top of my head what else (SSE4?).


I suggest waiting :). They will be included in the next kernel update, which will happen when a kernel security vulnerability is discovered.

That's what I thought about the 2.6.17 kernel.

The Merom's from 2 GHz up will have 4MB cache shared.
and up to 1066MHz FSB (Conroe). CPU magazine just did a feature on the Core
architecture included was discussion about Conroe (Core Duo2 for desktops) and some mention of Merom (mobile). They seem impressed. Be interesting to see what AMD does. 

Ok. I will wait.

---

### Post by snofix on 2006-08-27
> **jdong said:**
> [http://kernel.org/git/?p=linux/kernel/git/bcollins/ubuntu-dapper.git;a=commit;h=a1f540b44e934bba867fefc6eb94d9ebd2d7c1b0](http://kernel.org/git/?p=linux/kernel/git/bcollins/ubuntu-dapper.git;a=commit;h=a1f540b44e934bba867fefc6eb94d9ebd2d7c1b0)

Good news, Dapper's kernel is getting a backported version of the Core Duo scheduler from 2.6.17. This should boost performance a bit for us.

I'm using a self-compiled 2.6.17 from kernel.org on my Acer 5672 and didn't experience any performance-problems until now (I just used a config based on the 686-smp dapper kernel)

Btw: in idle-mode the CPU has ~52°C and under load (e.g. compiling the kernel) it reaches up to 70°C according to acpi.
Funnily enough when running Windows the temperature never goes below 61 °C :confused:

---

### Post by cbudden on 2006-08-27
Well I finally bought one of these laptops, and I have to say, like many other people, it works great.   Couple of niggles apart from the obvious. (webcam etc).  The FN/side multimedia controls not controlling Front but PCM instead?  Whats up with that? Has there been any progress anyone knows of?  Also, I have added cpu frequency applets but when I click on them, they freeze and lock up some other panel items.  On my old machine I think I needed to reconfigure panel applets or something so scaling worked.  Do I need to do the same here?

This thread is very very helpful.

Thanks everyone who has contributed.

Edit.

I have noticed that occasionally when I am playing sound, and I "use" compiz, switch workspace ect, the sound goes all watery.  Sometimes this does not occur and I can do all the comiz effects I want with no watery interruption.

---

### Post by jdong on 2006-08-27
> **cbudden said:**
> Well I finally bought one of these laptops, and I have to say, like many other people, it works great.   Couple of niggles apart from the obvious. (webcam etc).  The FN/side multimedia controls not controlling Front but PCM instead?  Whats up with that? Has there been any progress anyone knows of?

Yeah, I was in #kubuntu-devel complaining with Daniel T Chen (a kernel/alsa developer) about the issue. The naming convention is what the codec manufacturer and ALSA uses. The inconsistency in volume control is a gnome-media bug, and I have already launchpadded bug reports against both GNOME and KDE for this issue. KDE 3.5.4 now correctly respects a user-set master channel, but GNOME 2.14 is still affected. I don't know if GNOME 2.16 will fix this issue, but I'll continue to pursue it.

> 
  Also, I have added cpu frequency applets but when I click on them, they freeze and lock up some other panel items.  On my old machine I think I needed to reconfigure panel applets or something so scaling worked.  Do I need to do the same here?

I've seen similar problems with the GNOME CPU frequency applet. Don't click them! :)

---

### Post by cbudden on 2006-08-27
> **jdong said:**
> Yeah, I was in #kubuntu-devel complaining with Daniel T Chen (a kernel/alsa developer) about the issue. The naming convention is what the codec manufacturer and ALSA uses. The inconsistency in volume control is a gnome-media bug, and I have already launchpadded bug reports against both GNOME and KDE for this issue. KDE 3.5.4 now correctly respects a user-set master channel, but GNOME 2.14 is still affected. I don't know if GNOME 2.16 will fix this issue, but I'll continue to pursue it.


I've seen similar problems with the GNOME CPU frequency applet. Don't click them! :)


Thanks for that info.  I was using the gnome cpy frequency app with my pentium m machine no problem.

---

### Post by cbudden on 2006-08-29
> **cbudden said:**
> 

I have noticed that occasionally when I am playing sound, and I "use" compiz, switch workspace ect, the sound goes all watery.  Sometimes this does not occur and I can do all the comiz effects I want with no watery interruption.

I have narrowed the watery sound problem a bit.  If I play a song in rhythmbox or banshee, I get an "underwater" effect.  Play the song in mplayer, vlc or amarok and it is fine.  Could someone confirm this for me? 

thanks

---

### Post by cbudden on 2006-08-29
> **cbudden said:**
> I have narrowed the watery sound problem a bit.  If I play a song in rhythmbox or banshee, I get an "underwater" effect.  Play the song in mplayer, vlc or amarok and it is fine.  Could someone confirm this for me? 

thanks


Hopefully I won't be replying to my own posts for much longer!

Ok, here is how I fixed the underwater problem.  (With HUGE help from #gstreamer on freenode and #rhythmbox on irc.gnome.org)

```

sudo apt-get remove gstreamer0.10-fluendo-mp3

```

Then install 

```

sudo apt-get install gstreamer0.10-plugins-ugly

```

Worked for me!

---

### Post by jdong on 2006-08-29
Interesting... so fluendo's mp3 plugin sounds abnormal?

---

### Post by jdong on 2006-09-01
I have taken the plunge and dist-upgraded my laptop to Edgy. I want to make sure that Edgy works even better than Dapper on this laptop.

So far, the experience has been excellent. The dist-upgrade takes a bit of manual apt-get coaxing to go through, but it does indeed work. Edgy feels fairly stable right now, but of course it's gonna get updated packages like crazy, which will surely drive me nuts for the next month!

The only snag I hit is xorg.conf. In Xorg 7.1, the composite extension is **enabled by default**. Remember that fglrx disables DRI if it detects composite. As a result, you need this explicitly in your Xorg.conf:

```


Section "Extensions"
        Option  "Composite" "0"

EndSection

```

---

### Post by Frank Golden on 2006-09-03
> **jdong said:**
> I have taken the plunge and dist-upgraded my laptop to Edgy. I want to make sure that Edgy works even better than Dapper on this laptop.

So far, the experience has been excellent. The dist-upgrade takes a bit of manual apt-get coaxing to go through, but it does indeed work. Edgy feels fairly stable right now, but of course it's gonna get updated packages like crazy, which will surely drive me nuts for the next month!

The only snag I hit is xorg.conf. In Xorg 7.1, the composite extension is **enabled by default**. Remember that fglrx disables DRI if it detects composite. As a result, you need this explicitly in your Xorg.conf:

```


Section "Extensions"
        Option  "Composite" "0"

EndSection

```

Hey jdong,
  What's the code to do that and what were the things that needed coaxing. I'm sure I need to add to my sources.list also.
I have a duplicate drive I can swap in to experiment.
It is byte by byte identical to my main drive (it's my backup).
I have a partimage image of the Ubuntu install on this drive
so I would like to experiment. If I mess up all I need do is restore my backup image and start over, take about 4 minutes.
So I'm feeling adventurous.

---

### Post by jdong on 2006-09-03
> **Frank Golden said:**
> Hey jdong,
  What's the code to do that and what were the things that needed coaxing. I'm sure I need to add to my sources.list also.

Just add that snippet to the end of /etc/X11/xorg.conf. The things that needed coaxing was a generally involved dist-upgrade procedure:

(1) Replace dapper with edgy in sources.list
(2) sudo apt-get update
(3) sudo apt-get dist-upgrade
Repeat #3 until it refuses to upgrade any more packages.
(4) sudo apt-get install ubuntu-desktop
Repeat #4 for any of the other Ubuntu flavors you have installed


Next, run a sudo apt-get dist-upgrade again, noting all the packages it claims are "held back". Then, run sudo apt-get install {PASTE BIG LIST HERE}

---

### Post by jdong on 2006-09-03
I finally had it with my Dapper configuration.... Over the course of my work, I've been messily installing packages all over the system, and my root expanded to this 8GB hairball that I didn't really feel like cleaning out.

So, I did a 2nd backup, and did a fresh install of kubuntu Edgy.

The live installer worked perfectly, even on my custom setup (reiserfs /). The installation took less than 10 minutes to complete.


After a reboot, everything was ready, 686 kernel and all. All I needed was to install xorg-driver-fglrx, knetworkmanager, and edit my xorg.conf as mentioned above, and it's ready to use. That's out of the box!

---

### Post by Frank Golden on 2006-09-03
> **jdong said:**
> Just add that snippet to the end of /etc/X11/xorg.conf. The things that needed coaxing was a generally involved dist-upgrade procedure:

(1) Replace dapper with edgy in sources.list
(2) sudo apt-get update
(3) sudo apt-get dist-upgrade
Repeat #3 until it refuses to upgrade any more packages.
(4) sudo apt-get install ubuntu-desktop
Repeat #4 for any of the other Ubuntu flavors you have installed


Next, run a sudo apt-get dist-upgrade again, noting all the packages it claims are "held back". Then, run sudo apt-get install {PASTE BIG LIST HERE}

Ok two attempts to upgrade to edgy two completely and hopelessly
broken Ubuntus two restorations via partimage. Thank goodness for partimage! Edgy, Nope not for me.

---

### Post by gmc on 2006-09-05
HI Folks,

Well seems everyone else is taking the dive into Edgy, so I thought I'd try too. After downloading 1072 packages the upgrade went fairly smoothly. Apt-get dist-upgrade broke twice and forced me to issue an apt-get -f install to continue.

I did this upgrade wirelessly which went well until the very end when wpasupplicant was shutdown to be upgraded. I was left with about 35 or 40 packages to be installed, mostly python related stuff. One exception was v7 of Xorg. I was forced to reboot at this point and found that no matter what I did, I was unable to reconnect to my router via wired connection, wireless was out of the question since I couldn't get into gnome to startup network managed.

In the end, I had to hook the laptop directly to my IPCop firewall machine to get a dhcp connection and finish the upgrade, which I was able to do.

Now a couple of problems, I noticed the the 2.6.17-686 kernel's restricted package doesn't have the fglrx driver and there seems to be a problem with network manager/wpasupplicant as even though I reverted back to the vesa driver and can get back into gnome, I'm not able to connect to my router wirelessly.

All in all, the upgrade went better than I expected considering this is Knot-2 (plus a few days).

Gord

---

### Post by jdong on 2006-09-05
Strange -- fglrx is working fine for me in 2.6.17-6-686... Remember to turn off composite in xorg.conf though.

---

### Post by gmc on 2006-09-05
Hi JD,

I took your advice and disabled composite however there's no fglrx in the /lib/modules/2.6.17-6-686 tree, at least doesn't find it and the appropriate linux-restricted packages are installed.

$ find | grep fglrx
(reports nothing)

# apt-get install linux-restricted-modules-2.6.17-6-686 linux-restricted-modules-2.6.17-6-386
Reading package lists... Done
Building dependency tree       
Reading state information... Done
linux-restricted-modules-2.6.17-6-686 is already the newest version.
linux-restricted-modules-2.6.17-6-386 is already the newest version.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.

# modprobe fglrx
FATAL: Module fglrx not found.

G.

Edited: I just used Synaptic to reinstall the above modules and sure enough they're there now. I suspect that because I manually installed the 8.28.8 drivers via the instructions on the Wiki, I had to remove the "disable_modules=" in /etc/default/linux-restricted-modules-common.

It's working now :-)

---

### Post by gmc on 2006-09-05
Hi,

Further updates. I've got wireless working again. Seems a power cycle on my router sorted out the problems I was having connecting to it. So just to make a few recommendations:

(1) Don't upgrade from Breezy to Edgy via wireless (I knew that, I was just lazy and paid for it)
(2) Remove the **fglrx** entry in **/etc/defaults/linux-restricted-modules-common** (if you manually upgraded you ATI drivers in dapper
(3) Add the following to the end of your /etc/X11/xorg.conf

```

Section "Extensions"
        Option  "Composite" "0"
EndSection

```

(4) Be prepared to issue a couple of apt-get -f install when apt-get dist-upgrade errors out.
(5) Personally I'd recommend doing the upgrade from the command line not from with in Xorg (gnome/kde)

G.

---

### Post by Drife on 2006-09-06
Just to help out newcommers with soundproblem
I like to inform you guys that the latest dev.release of alsa-driver 1.0.13rc1
has fixed the "acer bug" for intel-hda sound driver according to [changelog]("http://www.alsa-project.org/changes/v1-0-12--v1-0-13rc1.txt")
and (yes I know it is almost a week old but..) I just tried it and it is working...
So no more patches.

/Drife

---

### Post by cbudden on 2006-09-06
Thanks for the alsa info.  Will I need to just install the new alsa driver?  Or the other 2 dev packages listed.  Is this the bug about the watery sound or the keyboard buttons for volume?

---

### Post by Drife on 2006-09-06
Sorry for the unclearity but it is for neither.
The bug fix is for those who didn't get _any_ sound at all. But if you are experiencing problems an upgrade might do the trick.. Anyways to make use of the "Acer bugfix" you only need to download and upgrade the drivers package.

/D

---

### Post by cbudden on 2006-09-06
> **Drife said:**
> Sorry for the unclearity but it is for neither.
The bug fix is for those who didn't get _any_ sound at all. But if you are experiencing problems an upgrade might do the trick.. Anyways to make use of the "Acer bugfix" you only need to download and upgrade the drivers package.

/D

Ok, thanks.  I will give it a try when I upgrade to edgy, which by the sounds of it will be soon.

---

### Post by jdong on 2006-09-07
Edgy testers: seems like our BIOS doesn't properly let Ubuntu know that it's a laptop, and as a result gnome-power-manager will hide its shiny new graphs. See bug [https://launchpad.net/bugs/59342](https://launchpad.net/bugs/59342) for more info and a workaround... I'm guessing adding that to a bootup script that executes before gnome-power-manager loads (but after dbus loads) will do the trick, trying rc.local to be non-invasive.... when I reboot I'll report back.

---

### Post by jdong on 2006-09-08
[https://launchpad.net/distros/ubuntu/+source/linux-source-2.6.15/+bug/59562](https://launchpad.net/distros/ubuntu/+source/linux-source-2.6.15/+bug/59562)

After a quick talk with Ben Collins, I filed the above bug ticket in hopes of getting Edgy's tifm21xx driver (for the 5-in-1 cardreader) backported to Dapper's kernel, available via a future Dapper kernel update. Guess we'll have to wait and see the results :)

---

### Post by mrgez on 2006-09-12
> **jdong said:**
> Edgy testers: seems like our BIOS doesn't properly let Ubuntu know that it's a laptop, and as a result gnome-power-manager will hide its shiny new graphs

Today's *hal*-update to version 0.5.7.1-0ubuntu10 seems to fix this! Hooray!

---

### Post by jdong on 2006-09-12
Yep, that hal update does the trick!

---

### Post by cbudden on 2006-09-12
I upgraded to Edgy last night, pretty painless.  

Now my laptop doesn't want to hibernate.

Anyone else getting this?

---

### Post by beni on 2006-09-13
Hi, I'm using Ubuntu on Acer Aspire 5672WLMI. Everything's been working well so far...except the Mic. I did some search on how to fix it but still got clue. Can somebody please help me make the Mic work?

---

### Post by gmc on 2006-09-14
> **jdong said:**
> [https://launchpad.net/distros/ubuntu/+source/linux-source-2.6.15/+bug/59562](https://launchpad.net/distros/ubuntu/+source/linux-source-2.6.15/+bug/59562)

After a quick talk with Ben Collins, I filed the above bug ticket in hopes of getting Edgy's tifm21xx driver (for the 5-in-1 cardreader) backported to Dapper's kernel, available via a future Dapper kernel update. Guess we'll have to wait and see the results :)

Hi JD,

I've manually compiled the tifm21xx driver and added it to /etc/modules. I know the drivers are loading, but when I plug in a 32M SDcard nothing appears to be happening. Is there some trick in accessing the SDcard or should it act like a usb device and just appear on the desktop?

G.

---

### Post by jdong on 2006-09-14
Are you sure you added all the modules to etc/modules, including mmc_core/mmc_block? (See the README file). It should show up as a hotpluggable block device and HAL should pick it up automagically.

---

### Post by cbudden on 2006-09-14
Regarding the driver, on the website for it they say it is merged into 2.6.17, which edgy has, but when I insert a SD card it does not mount.  Also, can someone post a direct download link as I cannot find it.

Thanks

Chris

---

### Post by gmc on 2006-09-14
> **jdong said:**
> Are you sure you added all the modules to etc/modules, including mmc_core/mmc_block? (See the README file). It should show up as a hotpluggable block device and HAL should pick it up automagically.

Dunno how I missed that one. Yup adding the mmc_core fixed the problem. Thanks!

G.

P.S. Just discovered the tifm_7xx1 drivers are already included with the current common kernel

---

### Post by Drife on 2006-09-15
> **beni said:**
> Hi, I'm using Ubuntu on Acer Aspire 5672WLMI. Everything's been working well so far...except the Mic. I did some search on how to fix it but still got clue. Can somebody please help me make the Mic work?

Are you sure you have the "volume" turned up?
You could try this if you have the OSS mixer as well.
Open the "full" volyme control, change device to RealTek ALC883 OSS,
choose edit preferences make sure you have marked In-Gain as a visible
control. Turn it up to max. Check with Recording level monitor.

Also make sure you have the latest alsa-driver 1.0.13rc1 or have
applied the Acer-patch if you are using an older version.
(If sound is working you should be ok though).

Don't know if this helps but it's a tip.

/D

---

### Post by cbudden on 2006-09-15
> **gmc said:**
> Dunno how I missed that one. Yup adding the mmc_core fixed the problem. Thanks!

G.

P.S. Just discovered the tifm_7xx1 drivers are already included with the current common kernel

Looks like you have a working card reader!

Would you mind writing a little howto explaining how to do it please.

Thanks in advance.

Chris

---

### Post by beni on 2006-09-19
Thank Drife! It worked right when I changed to RealTek.

---

### Post by kxgard3 on 2006-09-19
I know this is the ubuntu forum but mabye someone could tell me how well Kubuntu is running on this laptop at the moment? What version is the best and what works and what doesn't?

Thanks

---

### Post by jdong on 2006-09-19
I think everything said here also applies to KUbuntu.... I run both KDE and GNOME on mine, and they both work well.

---

### Post by cbudden on 2006-09-26
I noticed that there has been a new release for the webcam drivers, does it now mean our cameras work?

[http://mxhaard.free.fr/download.html](http://mxhaard.free.fr/download.html)

Thanks

Chris

---

### Post by jdong on 2006-09-26
No, sadly the zc32x chipset is not supported by the gpscav1 driver yet. I've heard it's supposed to be targeted at gspcav2.

---

### Post by cbudden on 2006-09-26
> **jdong said:**
> No, sadly the zc32x chipset is not supported by the gpscav1 driver yet. I've heard it's supposed to be targeted at gspcav2.


Ok cool.

---

### Post by eightballrj on 2006-09-27
I really would like to be able to get this card reader working what can I do?? Thanks a bunch!!

Richard

---

### Post by kxgard3 on 2006-09-27
Well I just installed Kubuntu Edgy and seems all is working except wireless. Its really odd, I can see all the networks within my range including my own but can not connect. 

I was using WPA but realized that its not supported(?) so I changed my access point to WEP and set up my key, I was unable to connect. Kubuntu was able to see the access point but keep reporting back that the connection had failed. Thinking maybe I was having WEP key problems I changed it a couple of times and still was unable to connect. I even went as far as turning off WEP but I am still unable to make a connection at all. 

Does anyone have a clue what could cause such a thing? I know my access point is working as I am using it now, I am not using any MAC filters. Does anyone know where a error log might be stored I could look at? 

I am really not that well versed in Linux but I know a little. 

Thanks
K.C.

edit/ Okay if this helps anyone when I run iwconfig I have no wlan0 like most people say they do. However I have a eth1 which shows all the wireless info.

---

### Post by mrgez on 2006-09-27
> **eightballrj said:**
> I really would like to be able to get this card reader working what can I do??

You could upgrade to edgy. At least for SD cards it works like a charm for me...

---

### Post by jdong on 2006-09-27
The SD cardreader driver is in Edgy. I've requested that it be backported to Dapper also, but it's a bit complex a backport, so it might take a bit of time.

---

### Post by phoenixleo on 2006-09-27
I have an Acer 5671AWLMi and when I updated to kernel 2.6.15-27-686 I saw a strange effect.
According to the resource monitor, one of the processor cores are always at 100% alternating between the two. Anyone else see this?

A non-ubuntu issue is that according to the specs I'm supposed to have a T2050 processor, but both windows and intels own software identifies it as an T2250. Another issue that might be related is that I can't run any 3D game from the last 3-5 years. After 30-60 seconds the computer is overheating and auto-shuts down. With an ATI X1600 I'm getting pretty decent graphic performance. It just won't last very long...

A small plus though, was that when I used the factory backup disk it respected my choice of partitioning and didn't even mess with the MBR.
My windows partition was restored and my Ubuntu partition was untouched.

---

### Post by cbudden on 2006-09-27
> **jdong said:**
> The SD cardreader driver is in Edgy. I've requested that it be backported to Dapper also, but it's a bit complex a backport, so it might take a bit of time.

When I plug my card nothing happens.  Do I need to load a module for it?  Should it happen automatically.

---

### Post by Kwunman on 2006-09-27
> **phoenixleo said:**
> I have an Acer 5671AWLMi and when I updated to kernel 2.6.15-27-686 I saw a strange effect.
According to the resource monitor, one of the processor cores are always at 100% alternating between the two. Anyone else see this?
.

I also had the same problem and had no idea what to do about. however, a few days ago, i noticed that cpufreqd failed to load, and magically, my processor was running at normal speed yet next time i restarted my laptop, the problem had returned. 

i immidiately uninstalled cpufreqd through adept (i'm using kubuntu, but synaptic should do the trick), restarted my laptop, and viola! normal processor speed :D ! I also noticed that i was getting longer battery life as well!

i hope that solves your problem!

Daniel

---

### Post by jdong on 2006-09-27
> **cbudden said:**
> When I plug my card nothing happens.  Do I need to load a module for it?  Should it happen automatically.

You may need to load mmc_core? If that is the case, then we should really file a kernel bug against it.

---

### Post by cruiseraddict on 2006-09-27
Couple of Questions. I have teh 5102wlmi. it is a scaled down version of the 5672 from what I have read. It has the AMD Turion 64x2 processor. Is this the same as the 5672? Also I do not see mmc_core package to install to get the card reader working. where did you get the package? any repositories I need to add. Also I am running the 32 bit version. Do you think the 64 bit version is running well enough to upgrade for an every day use laptop. Any help would be greatly appreciated

Thanks
Dave



> **jdong said:**
> You may need to load mmc_core? If that is the case, then we should really file a kernel bug against it.

---

### Post by jdong on 2006-09-27
Whoa, if it has a Turion processor, then it's completely different hardware-wise than the 5672, which is almost pure-Intel. Most of the information in this thread is not going to apply to your laptop then.

---

### Post by kxgard3 on 2006-09-28
Does anyone have a idea what could be causing my wireless problems I posted a page back?

---

### Post by unz on 2006-09-28
I think you got some problems with config files. WPA works with our card.
I don't know if here is the correct place to discuss your problem.
Post some logs [tail -f /var/log/messages] while you are attempting to connect to AP.

---

### Post by cruiseraddict on 2006-09-28
Would the packages from the sd card reader not be the same even though the rest of the chipsets are different? I do not see many people with this laptop, although more do seem to be asking qustions about it. 


Dave

> **jdong said:**
> Whoa, if it has a Turion processor, then it's completely different hardware-wise than the 5672, which is almost pure-Intel. Most of the information in this thread is not going to apply to your laptop then.

---

### Post by jdong on 2006-09-29
I'm not certain that the same SD chipset is being used. Can you post lspci and lsusb output?

---

### Post by phoenixleo on 2006-09-29
> **Kwunman said:**
> I also had the same problem and had no idea what to do about. however, a few days ago, i noticed that cpufreqd failed to load, and magically, my processor was running at normal speed yet next time i restarted my laptop, the problem had returned. 

i immidiately uninstalled cpufreqd through adept (i'm using kubuntu, but synaptic should do the trick), restarted my laptop, and viola! normal processor speed :D ! I also noticed that i was getting longer battery life as well!

i hope that solves your problem!

Daniel

Thanks, but it appears I don't have cpufrqd installed. I do have powernowd, though, but removing it requires me to remove the whole ubuntu-desktop shebang. I'll rather just stay with the previous kernel and see what happens when the next one comes out.

Cheers.

---

### Post by cbudden on 2006-09-30
Regarding my card slot issue.

If I put in any SD card, they do not get mounted.  In /var/log/messages I get the following:

```

Sep 30 17:12:44 cbudden-laptop kernel: [17196503.116000] tifm_7xx1: sd card detected in socket 1

```

Why won't it mount?

---

### Post by kxgard3 on 2006-10-02
Okay I uninstalled Edgy and then installed Drapper. Every thing is working great except no matter what I do the volume is really really low!

I installed alsamixer and made sure the volume was up in that but no good still really low volume.

---

### Post by Hugin on 2006-10-24
I just wanted to say that this thread has been of great help.
Just did a fresh install of Edgy. To get the SD card to mount I used 

sudo modprobe tifm_core
sudo modprobe tifm_sd

and the SD card shows up

adding
tifm_core
tifm_sd
to /etc/modules will have them load at boot

---

### Post by jdong on 2006-10-24
I think you only need to add tifm_sd to /etc/modules... udev magically gets tifm_core for me.

---

### Post by llbra on 2006-10-27
Thank you guys. I also agree this topic has been great for all of us.
Just the
sudo modprobe tifm_sd
worked great.

I did also add it to /etc/modules

---

### Post by scifan on 2006-10-27
So edgy fixes the SD reader issue... I haven't paid attention for a little while... have they better stabilized the wireless... or is there a driver yet for the camera on the 5672?

---

### Post by cbudden on 2006-10-27
> **scifan said:**
> So edgy fixes the SD reader issue... I haven't paid attention for a little while... have they better stabilized the wireless... or is there a driver yet for the camera on the 5672?

Wireless has been fine for me, but no camera driver yet.

---

### Post by Drife on 2006-10-27
Hi all! Today I upgraded to Edgy from Dapper. It went anything but smoothly! I had a lot of trouble with a lot of stuff but I managed to fix most of it. However I can't get the fglrx-drivers to work no matter what I do. Has somebody else had this problem after upgrading? I have used the drivers from the repositories and both self compiled 8.28.8 and 8.29.6 with various xorg.conf-files. I have the X1600 chipset.
cat /var/log/Xorg.0.log |grep "WW\|EE"  gives
(WW) The directory "/usr/share/X11/fonts/cyrillic" does not exist.
(II) Loading extension MIT-SCREEN-SAVER
(WW) fglrx(0): board is an unknown third party board, chipset is supported
(WW) fglrx(0): ***********************************************
(WW) fglrx(0): * DRI initialization failed!                  *
(WW) fglrx(0): * (maybe driver kernel module missing or bad) *
(WW) fglrx(0): * 2D acceleraton available (MMIO)             *
(WW) fglrx(0): * no 3D acceleration available                *
(WW) fglrx(0): ********************************************* *
(WW) fglrx(0): Failed to set up write-combining range (0xd7000000,0xfe0000)
(WW) fglrx(0): Failed to set up write-combining range (0xd6000000,0x1fe0000)
(WW) fglrx(0): Failed to set up write-combining range (0xd4000000,0x3fe0000)
(WW) fglrx(0): Failed to set up write-combining range (0xd0000000,0x7fe0000)
(WW) fglrx(0): Option "VendorName" is not used
(WW) fglrx(0): Option "ModelName" is not used
(EE) AIGLX: Screen 0 is not DRI capable
(EE) xf86OpenSerial: Cannot open device /dev/wacom
(EE) xf86OpenSerial: Cannot open device /dev/wacom
(EE) xf86OpenSerial: Cannot open device /dev/wacom
(EE) xf86OpenSerial: Cannot open device /dev/wacom
(EE) xf86OpenSerial: Cannot open device /dev/wacom
(EE) xf86OpenSerial: Cannot open device /dev/wacom

and dmesg
[17179644.156000] fglrx: module license 'Proprietary. (C) 2002 - ATI Technologies, Starnberg, GERMANY' taints kernel.
[17179644.160000] [fglrx] Maximum main memory to use for locked dma buffers: 927 MBytes.
[17179644.160000] [fglrx] module loaded - fglrx 8.28.8 [Aug 17 2006] on minor 0
 
while trying with the 8.28.8 version..

The module seems to load but somehow the drivers seems to be unable to initialize DRI. 

Please.. I'm out of clues.. does anyone have any ideas?

/Drife

---

### Post by Kwunman on 2006-10-27
Hi,

I personally have had no real problems upgrading to Edgy, but still have to try a few things.
Concerning the fglrx drivers, although i have the x1400 chipset as opposed to the x1600, i noticed the following whilst reading through the unofficial ATI Linux driver Wiki:

[INDENT]In Ubuntu Edgy the Composite extension is enabled by default, however, fglrx does not yet support Composite with DRI. In order to to disable Composite you have to edit the xorg.conf file:

sudo gedit /etc/X11/xorg.conf

and add these lines at the end of the file:
File: /etc/X11/xorg.conf

Section "Extensions"
        Option  "Composite" "0"
EndSection[/INDENT]

I'm no Linux expert, but i hope this helps.

Kwun-man

---

### Post by Drife on 2006-10-27
Yes!!
I did a complete reinstall of X and compiled the 8.29-drivers and added the lines you said Kwun-man and now it's working! Definitly give your contribution the credit for getting it to work! Thanks Kwun-man!

Drife

---

### Post by haani on 2006-10-27
how do u enable dual core in edgy!!??

---

### Post by jdong on 2006-10-28
Dual core is enabled by default with the generic kernel, which is installed by default. No configuration is necessary.

---

### Post by unz on 2006-10-28
Is someone using tv-out? How can you manage our 16:10 LCD with 4:3 TV? Seems changing LCD's resolution to a 4:3 does the trick on TV, but everything is streched on LCD. If i use Center Mode ... tv-output is really strange, smaller dimension and resolution.
Last but not the least my Fn+F5 doesn't work.

ps camera driver is coming ... stay tuned

---

### Post by haani on 2006-10-28
is there any way of enablin OpenGL in XGL/Beryl???

---

### Post by jdong on 2006-10-28
> **haani said:**
> is there any way of enablin OpenGL in XGL/Beryl???

OpenGL should work fine inside Xgl/Beryl, though it'll run at somewhat lower framerates than native OpenGL.

---

### Post by mfa81 on 2006-10-28
after upgrade to edgy i cant mut pcm channel, any solution ? multimedia keys works for volume control, play, stop, etc, humm there is another issue with play/pause key, it just play and not pause... well, about pcm channel i cant mute i tried, alsamixer, kmixer, nothing works ! any solution ?

ps: i made a fresh install of edgy and on dapper i was able to mute pcm

another issue i was receiving he following error messages during boot, it is the first messages printed during boot

```

[17179570.340000] PCI: Cannot allocate resource region 7 of bridge 0000:00:1c.0
[17179570.340000] PCI: Cannot allocate resource region 8 of bridge 0000:00:1c.0
[17179570.340000] PCI: Cannot allocate resource region 9 of bridge 0000:00:1c.0
[17179570.340000] PCI: Cannot allocate resource region 7 of bridge 0000:00:1c.1
[17179570.340000] PCI: Cannot allocate resource region 8 of bridge 0000:00:1c.1
[17179570.340000] PCI: Cannot allocate resource region 9 of bridge 0000:00:1c.1
[17179570.340000] PCI: Cannot allocate resource region 7 of bridge 0000:00:1c.2
[17179570.340000] PCI: Cannot allocate resource region 8 of bridge 0000:00:1c.2
[17179570.340000] PCI: Cannot allocate resource region 9 of bridge 0000:00:1c.2
[17179570.340000] PCI: Cannot allocate resource region 7 of bridge 0000:00:1c.3
[17179570.340000] PCI: Cannot allocate resource region 8 of bridge 0000:00:1c.3
[17179570.340000] PCI: Cannot allocate resource region 9 of bridge 0000:00:1c.3

```

---

### Post by haani on 2006-10-28
> **jdong said:**
> OpenGL should work fine inside Xgl/Beryl, though it'll run at somewhat lower framerates than native OpenGL.

OpenGL isnt Workin on my XGL/Beryl wot guide did u use to install XGL/Beryl??

because when i run google earth it says Xlib:  extension "XFree86-DRI" missing on display 1 and google earth then doesnt start up!!!

---

### Post by jdong on 2006-10-28
> **haani said:**
> OpenGL isnt Workin on my XGL/Beryl wot guide did u use to install XGL/Beryl??

because when i run google earth it says Xlib:  extension "XFree86-DRI" missing on display 1 and google earth then doesnt start up!!!

Google earth is a completely different story... it has to be run outside of display 1, such as display=:0 googleearth.

---

### Post by Kwunman on 2006-10-28
hi,

i've installed xgl/beryl and it is working perfectly on my edgy installation.
Google earth also works under it.
I used the following installation guide:

[URL="http://lhansen.blogspot.com/2006/10/3d-desktop-beryl-and-xgl-on-ubuntu-edgy.html"]http://lhansen.blogspot.com/2006/10/3d-desktop-beryl-and-xgl-on-ubuntu-edgy.html
[/URL]
I used a different one before that and nearly had to reinstall my whole system, so it may just be the guide you used to install it that is causing the problem.

I hope this helps

Kwun-man

---

### Post by mfa81 on 2006-10-29
my touchpad is generating a noise on my speakers, every time I use the touchpad, I heard a noise from speakers, I have no idea on how to solve this... fresh edgy install, first time I used the touchpad i heard this noise... any suggestion to solve the problem ?

---

### Post by Rothguard on 2006-10-29
ahh just  turned up to say i have a Aspire 5670 and  im just installing 6.06 on it the very next thing is to get xgl happening  i have the x1400 gfx carda and a lot of guides say to replace "fglrx" but i have vesa drivers  is ther any extra hastles wit this 

thanks in advance

---

### Post by jdong on 2006-10-29
You must use fglrx drivers if you want to use Xgl. VESA drivers are not recommended, since they do not take advantage of your laptop's widescreen resolution, and they are extremely slow (you've probably noticed the lag while scrolling in Firefox, for example)

---

### Post by Kwunman on 2006-10-29
hi,

If you want to use xgl, i strongly suggest using the following guide:

[http://lhansen.blogspot.com/2006/10/3d-desktop-beryl-and-xgl-on-ubuntu-edgy.html]("http://lhansen.blogspot.com/2006/10/3d-desktop-beryl-and-xgl-on-ubuntu-edgy.html")

It is very simple to follow, doesn't use the terminal and gets xgl working well in a short space of time. u need to use the fglrx drivers for it though.

Hope this helps,

Kwun-Man

---

### Post by Rothguard on 2006-10-29
OK awsome i have cube!! ill be blowing some minds this week for sure..   just a few questions 

#1 at boot up i get the same errors as mfa81 Eg  PCI: Cannot allocate resource region 9 of bridge 0000:00:1c.0  whats this? is it a problem? how do i fix it?

#2 CPU usage is bizzare in a noraml " non beryl/xgl " boot the cpu is using %25 of my coreduo 1.66  

#3 when i do run an xgl/beryl desktop weird stuff happens  i cant drag windows theres is no | _ [ ] X | frames  and cpu usage goes to %100 allthough top displays only %50 


all i have is a default install of ubuntu 6.06  
the default install of xgl/beryl from the guide at [http://lhansen.blogspot.com/2006/10/beryl-and-xgl-on-ubuntu-linux-with-ati.html](http://lhansen.blogspot.com/2006/10/beryl-and-xgl-on-ubuntu-linux-with-ati.html)
and the 686 SMP kernal that was installed via synaptic 
----------------------------------------------
Acer Aspire 5670WLMi
Intel CoreDuo T2300 (1.66)
1 Gig RAM 
ATi X1400 Mobility Radeon
up to 512Mb HyperMemory
-----------------------------------------------
not sure if its a 128 or 256 card  or if there are even 2 versions

---

### Post by jdong on 2006-10-29
> **Rothguard said:**
> OK awsome i have cube!! ill be blowing some minds this week for sure..   just a few questions 

#1 at boot up i get the same errors as mfa81 Eg  PCI: Cannot allocate resource region 9 of bridge 0000:00:1c.0  whats this? is it a problem? how do i fix it?

Normal... well normal in the sense of harmless and should be ignored.

---

### Post by cbudden on 2006-10-30
Hey.
Since using Edgy, my suspend and hibernate does not work.

Here is my acpi-support file.  It did used to work earlier in the dev cycle

[http://paste.ubuntu-nl.org/29471/](http://paste.ubuntu-nl.org/29471/)

---

### Post by mfa81 on 2006-10-31
anyone are having problem with pcm channel ? I can't mute pcm channel in edgy, with dapper I was able to do this.

---

### Post by jdong on 2006-10-31
GNOME seems to have no issue "muting" the PCM channel (it simply sets the volume to zero temporarily) but KDE will refuse to mute PCM.

---

### Post by mfa81 on 2006-10-31
Well I used kmix to set the default channel to Front, after that I used Kcontrol to assign multimedia keys Mute, Volume +/-, but after that Kmilo is unable to show OSD messages, thats the solution because it is not possible to configure hotkeys on kmilo yet.

---

### Post by unz on 2006-11-03
> **mfa81 said:**
> my touchpad is generating a noise on my speakers, every time I use the touchpad, I heard a noise from speakers, I have no idea on how to solve this... fresh edgy install, first time I used the touchpad i heard this noise... any suggestion to solve the problem ?

mute channel-in

---

### Post by jdong on 2006-11-03
> **mfa81 said:**
> Well I used kmix to set the default channel to Front, after that I used Kcontrol to assign multimedia keys Mute, Volume +/-, but after that Kmilo is unable to show OSD messages, thats the solution because it is not possible to configure hotkeys on kmilo yet.

Right that's another solution too. The problem with Kmilo is that Kmilo uses DCOP to talk to KMix, and KMix's DCOP calls automatically work on the perceived master channel regardless of user settings.

---

### Post by mfa81 on 2006-11-03
> **unz said:**
> mute channel-in

problem solved after change master channel to front using kmix.

another issue with edgy, my battery indicator, when I am on battery my power indicator jumps from 100% to 66%, 33% and hibernate when I think that I still have 1 hour ! I am using kde power manager...

---

### Post by jdong on 2006-11-03
> **mfa81 said:**
> problem solved after change master channel to front using kmix.

another issue with edgy, my battery indicator, when I am on battery my power indicator jumps from 100% to 66%, 33% and hibernate when I think that I still have 1 hour ! I am using kde power manager...

That is bug [https://launchpad.net/distros/ubuntu/+source/hal/+bug/60989](https://launchpad.net/distros/ubuntu/+source/hal/+bug/60989) , and there is a workaround (rebuild hal removing one patch). There isn't a fix (yet) for it because reverting that patch fixes our laptops but breaks a bunch of other laptops. For now, those other laptops outnumber our acers, so we lose :D

---

### Post by mfa81 on 2006-11-04
> **jdong said:**
> That is bug [https://launchpad.net/distros/ubuntu/+source/hal/+bug/60989](https://launchpad.net/distros/ubuntu/+source/hal/+bug/60989) , and there is a workaround (rebuild hal removing one patch). There isn't a fix (yet) for it because reverting that patch fixes our laptops but breaks a bunch of other laptops. For now, those other laptops outnumber our acers, so we lose :D

and how can I rebuild hal removing debian/patches/00upstream-02-mWh-conversion.patch ?

---

### Post by jdong on 2006-11-04
(0) sudo apt-get build-dep hal; sudo apt-get install fakeroot
(1) cd /tmp
(2) apt-get source hal
(3) cd hal-*
(4) rm debian/patches/00upstream-02-mWh*
(5) dch -i

This opens up an editor window. Save and quit (if it's vim, that's ESC :wq)

(6) dpkg-buildpackage -b -rfakeroot
(7) look in /tmp, and all the .debs should be there.


After installing HAL, you should either reboot or restart /etc/init.d/dbus... I personally recommend a reboot, as restarting dbus makes some of your panel programs (power manager, network manager, and more) VERY upset :D

---

### Post by badhorse on 2006-11-05
Sorry.
I try to follow your tip for rebuild HAL but in the step 5: dch -i, i get a command not found. What is dch -i?
Thanks.

---

### Post by cbudden on 2006-11-05
> **badhorse said:**
> Sorry.
I try to follow your tip for rebuild HAL but in the step 5: dch -i, i get a command not found. What is dch -i?
Thanks.

Install the devscripts package

sudo apt-get install devscripts

---

### Post by badhorse on 2006-11-05
It Works!!!!!!!
Thanks, thanks,\\:D/ \\:D/

---

### Post by cbudden on 2006-11-05
> **badhorse said:**
> It Works!!!!!!!
Thanks, thanks,\\:D/ \\:D/

Also working for me.  Getting sensible values for time left now.  Thanks

---

### Post by mfa81 on 2006-11-05
> **Hugin said:**
> I just wanted to say that this thread has been of great help.
Just did a fresh install of Edgy. To get the SD card to mount I used 

sudo modprobe tifm_core
sudo modprobe tifm_sd

and the SD card shows up

adding
tifm_core
tifm_sd
to /etc/modules will have them load at boot

I tried to load tifm_sd and tifm_core but I cant get sd card working fine ! whem I insert a MS, SD card I just receive messages from tifm_7xx1, if I unload tifm_7xx1 I dont see any message inserting or remove a media card, just messages about device disable / enabled! Again fresh Edgy install... on dapper my sd card was working out of the box, just insert a media card to see the icon on my kde desktop.

```

Nov  6 22:13:14 sharapova kernel: [17181235.068000] tifm_7xx1: ms card detected in socket 0
Nov  6 22:13:18 sharapova kernel: [17181239.456000] tifm_7xx1: demand removing card from socket 0
Nov  6 22:13:28 sharapova kernel: [17181249.124000] ACPI: PCI interrupt for device 0000:0a:09.2 disabled
Nov  6 22:15:49 sharapova kernel: [17181390.520000] ACPI: PCI Interrupt 0000:0a:09.2[A] -> GSI 20 (level, low) -> IRQ 201

```

why so many things just stop to work on Edgy ?

---

### Post by tonyr1988 on 2006-11-06
Hey guys - 

It's getting really hard to read through over 60 pages on one forum topic, so I used a free wikifarm to set this up:

[http://acer5672ubuntu.elwiki.com](http://acer5672ubuntu.elwiki.com)

If you guys don't want to use this, that's not a problem. I just thought it'd be nice to keep all this information in one central repository that's easy for all to access.

However, the first big question is: Dapper or Edgy? It'd be hard (impossible?) to try and manage both versions completely. On one hand, Dapper seems to have better compatibility. Then again, Edgy is the newest version, so many newcomers will try and use it.

Just thought I'd let everyone know. Good idea, or horrible?

---

### Post by jdong on 2006-11-06
That's definitely a superb idea to organize this onto a wiki.

I use my laptop with both Dapper and Edgy... both distributions work with it, so why not maintain information on using both?

---

### Post by nik1111 on 2006-11-07
> **jdong said:**
> (0) sudo apt-get build-dep hal; sudo apt-get install fakeroot
(1) cd /tmp
(2) apt-get source hal
(3) cd hal-*
(4) rm debian/patches/00upstream-02-mWh*
(5) dch -i

This opens up an editor window. Save and quit (if it's vim, that's ESC :wq)

(6) dpkg-buildpackage -b -rfakeroot
(7) look in /tmp, and all the .debs should be there.


After installing HAL, you should either reboot or restart /etc/init.d/dbus... I personally recommend a reboot, as restarting dbus makes some of your panel programs (power manager, network manager, and more) VERY upset :D



Hi, I have the same issue with gnome power manager.It goes from 100-75-50-25 % !Does the same fix apply for gnome too?I am on Edgy.

---

### Post by Drife on 2006-11-07
> **nik1111 said:**
> Does the same fix apply for gnome too?I am on Edgy.

It did for me.
/Drife

---

### Post by Drife on 2006-11-07
> **unz said:**
> Is someone using tv-out? How can you manage our 16:10 LCD with 4:3 TV? Seems changing LCD's resolution to a 4:3 does the trick on TV, but everything is streched on LCD. If i use Center Mode ... tv-output is really strange, smaller dimension and resolution.
Last but not the least my Fn+F5 doesn't work.

ps camera driver is coming ... stay tuned

I'm using tvout. I solved the ratioproblem with a dual screen setup in xorg.conf. I have the tv-screen to the right of my desktop. I.e.
in ServerLayout
Screen      0  "aticonfig-Screen[0]" 0 0
Screen         "aticonfig-Screen[1]" RightOf "aticonfig-Screen[0]"

Then I used aticonfig's tv-geometry tool to adjust it to fit my old 4:3 tv.
tv-geometry string "87x90+0+10" does the trick for me.

However... I'm experiencing some flicker when watching movies.
I normally use mplayer and have tried different codec's but nothing gives me a perfect picture (still's are excellent but movies tend to flicker).

Does anyone have an idea on how to solve this? I have a dual boot but the only thing I use windows for is movie watching on the tv since the picture is excellent there and I would very much like to not having to reboot for that.

Regards
/Drife

---

### Post by nik1111 on 2006-11-07
> **Drife said:**
> It did for me.
/Drife

It doesnt seem to work here.. I get this error message during the last step ..Any ideas?..



dpkg-deb: building package `libhal-storage-dev' in `../libhal-storage-dev_0.5.7.1-0ubuntu18_i386.deb'.
tar: -: file name read contains nul character
 dpkg-genchanges -b
dpkg-genchanges: warning: unknown information field `Xb-Python-Version' in input data in package's section of control info file
dpkg-genchanges: binary-only upload - not including any source code
 signfile hal_0.5.7.1-0ubuntu18_i386.changes
gpg: WARNING: unsafe ownership on configuration file `/home/nik/.gnupg/gpg.conf'
gpg: skipped "root <root@nik-laptop>": secret key not available
gpg: [stdin]: clearsign failed: secret key not available

dpkg-buildpackage: binary only upload (no source included)
(WARNING: Failed to sign .changes file)

---

### Post by nik1111 on 2006-11-07
> **Drife said:**
> Hi all! Today I upgraded to Edgy from Dapper. It went anything but smoothly! I had a lot of trouble with a lot of stuff but I managed to fix most of it. However I can't get the fglrx-drivers to work no matter what I do. Has somebody else had this problem after upgrading? I have used the drivers from the repositories and both self compiled 8.28.8 and 8.29.6 with various xorg.conf-files. I have the X1600 chipset.
cat /var/log/Xorg.0.log |grep "WW\|EE"  gives
(WW) The directory "/usr/share/X11/fonts/cyrillic" does not exist.
(II) Loading extension MIT-SCREEN-SAVER
(WW) fglrx(0): board is an unknown third party board, chipset is supported
(WW) fglrx(0): ***********************************************
(WW) fglrx(0): * DRI initialization failed!                  *
(WW) fglrx(0): * (maybe driver kernel module missing or bad) *
(WW) fglrx(0): * 2D acceleraton available (MMIO)             *
(WW) fglrx(0): * no 3D acceleration available                *
(WW) fglrx(0): ********************************************* *
(WW) fglrx(0): Failed to set up write-combining range (0xd7000000,0xfe0000)
(WW) fglrx(0): Failed to set up write-combining range (0xd6000000,0x1fe0000)
(WW) fglrx(0): Failed to set up write-combining range (0xd4000000,0x3fe0000)
(WW) fglrx(0): Failed to set up write-combining range (0xd0000000,0x7fe0000)
(WW) fglrx(0): Option "VendorName" is not used
(WW) fglrx(0): Option "ModelName" is not used
(EE) AIGLX: Screen 0 is not DRI capable
(EE) xf86OpenSerial: Cannot open device /dev/wacom
(EE) xf86OpenSerial: Cannot open device /dev/wacom
(EE) xf86OpenSerial: Cannot open device /dev/wacom
(EE) xf86OpenSerial: Cannot open device /dev/wacom
(EE) xf86OpenSerial: Cannot open device /dev/wacom
(EE) xf86OpenSerial: Cannot open device /dev/wacom

and dmesg
[17179644.156000] fglrx: module license 'Proprietary. (C) 2002 - ATI Technologies, Starnberg, GERMANY' taints kernel.
[17179644.160000] [fglrx] Maximum main memory to use for locked dma buffers: 927 MBytes.
[17179644.160000] [fglrx] module loaded - fglrx 8.28.8 [Aug 17 2006] on minor 0
 
while trying with the 8.28.8 version..

The module seems to load but somehow the drivers seems to be unable to initialize DRI. 

Please.. I'm out of clues.. does anyone have any ideas?

/Drife



[http://wiki.cchtml.com/index.php/Ubuntu_Edgy_Installation_Guide#Method_2:_Generating.2FInstalling_Ubuntu_packages_for_the_new_8.30.3_drivers_in_Ubuntu_Edgy_Manually](http://wiki.cchtml.com/index.php/Ubuntu_Edgy_Installation_Guide#Method_2:_Generating.2FInstalling_Ubuntu_packages_for_the_new_8.30.3_drivers_in_Ubuntu_Edgy_Manually)

A great guide (though you already solved it but if anyone needs it..). for X1600 you ll need method 2.

---

### Post by jdong on 2006-11-07
> **nik1111 said:**
> It doesnt seem to work here.. I get this error message during the last step ..Any ideas?..



dpkg-deb: building package `libhal-storage-dev' in `../libhal-storage-dev_0.5.7.1-0ubuntu18_i386.deb'.
tar: -: file name read contains nul character
 dpkg-genchanges -b
dpkg-genchanges: warning: unknown information field `Xb-Python-Version' in input data in package's section of control info file
dpkg-genchanges: binary-only upload - not including any source code
 signfile hal_0.5.7.1-0ubuntu18_i386.changes
gpg: WARNING: unsafe ownership on configuration file `/home/nik/.gnupg/gpg.conf'
gpg: skipped "root <root@nik-laptop>": secret key not available
gpg: [stdin]: clearsign failed: secret key not available

dpkg-buildpackage: binary only upload (no source included)
(WARNING: Failed to sign .changes file)

That's perfectly fine, it's just saying you can't GPG-sign the package, because there's no GPG key set up. No big deal. Look in the current directory or ../, and all the debs will be there.

---

### Post by nik1111 on 2006-11-07
Yes the debs are there, but then i reboot and the situation isnt fixed.. do I have to install the debs by double clicking all of them, is that what you mean?

---

### Post by jdong on 2006-11-07
> **nik1111 said:**
> Yes the debs are there, but then i reboot and the situation isnt fixed.. do I have to install the debs by double clicking all of them, is that what you mean?

Yeah, you have to install all of them. Use "sudo dpkg -i *.deb" -- gdebi is going to have a hard time resolving the dependencies.

---

### Post by nik1111 on 2006-11-07
I did it and it fixes one issue..It kind of reads the correct acpi info, so no more 25% scaling.

But it still doesnt fix the second issue, when I unplug it at lets say 43% of charging, it will report after a couple of minutes that power is critically low and it will shutdown while in the same message it reports that it's about 40% ! 

It says something like "Power level critically low (40%) , 2 minutes of battery life remaining" and shuts down if I dont plug it in within the next few seconds.

So critically low and 40 % dont really add up, so any ideas about that?It seems it reads the correct %, but doesnt do well when it translates it to time.
Maybe kpowersave can fix that?Or re-installing gnome power management?

---

### Post by nik1111 on 2006-11-08
I noticed that in the Edgy repositories, there is the source for spa5xx driver. I suppose installing it wont resolve the camera issue :(

---

### Post by jdong on 2006-11-08
> **nik1111 said:**
> I did it and it fixes one issue..It kind of reads the correct acpi info, so no more 25% scaling.

But it still doesnt fix the second issue, when I unplug it at lets say 43% of charging, it will report after a couple of minutes that power is critically low and it will shutdown while in the same message it reports that it's about 40% ! 

It says something like "Power level critically low (40%) , 2 minutes of battery life remaining" and shuts down if I dont plug it in within the next few seconds.

So critically low and 40 % dont really add up, so any ideas about that?It seems it reads the correct %, but doesnt do well when it translates it to time.
Maybe kpowersave can fix that?Or re-installing gnome power management?
[http://cvs.gnome.org/viewcvs/*checkout*/gnome-power-manager/docs/faq.html#faq-discharge-time-wrong](http://cvs.gnome.org/viewcvs/*checkout*/gnome-power-manager/docs/faq.html#faq-discharge-time-wrong)

This workaround is pretty nice for that issue...

That's actually a "BIOS bug" that when you first unplug the cord, the discharge rate info is very inaccurate, and it takes time to settle.... However, it's equally gnome-power-manager's fault for taking that first reading so seriously.

I believe there are several Launchpad bugs regarding this, so it's a known problem.

---

### Post by nik1111 on 2006-11-08
It seems to be working now..

---

### Post by Rothguard on 2006-11-08
YES im back again  ok SO  i get the same no gpg key error as nik111 but the packages are not in /tmp  does that mean it went right  or wrong??
 i think wrong the battery power level still goes 100% 66% 33% 0% if i let the battery drain to 33% then plugh the power in it instantly goes to 42% i guess i stuffed something up :S

---

### Post by jdong on 2006-11-08
> **Rothguard said:**
> YES im back again  ok SO  i get the same no gpg key error as nik111 but the packages are not in /tmp  does that mean it went right  or wrong??
 i think wrong the battery power level still goes 100% 66% 33% 0% if i let the battery drain to 33% then plugh the power in it instantly goes to 42% i guess i stuffed something up :S

The packages are in whatever directory you issued apt-get source from. If you get the GPG sign message that means the build succeeded.

---

### Post by llbra on 2006-11-09
Jdong, thanks for the acpi tips!

I read someone`s tip to for the SD (maybe yours, dunno), and I really got it working. But everytime I put something it the SD it gets corrupted or it fails to write.

dmesg shows so block device errors. I haven`t got this when I try to record on the SD plugged in a USB device. I caused me a lot of trouble last week, since I took a bit to discover, and a kept formating and (re)formating my SD and my palm wouldn`t read it. I even used the palm to format it but the same error kept appearing.

Thanks in advance.

BTW, have one of you folks has news on spca5xx for the OrbiCam?

---

### Post by jdong on 2006-11-09
> **llbra said:**
> Jdong, thanks for the acpi tips!

I read someone`s tip to for the SD (maybe yours, dunno), and I really got it working. But everytime I put something it the SD it gets corrupted or it fails to write.

Interesting... My SD cardreader also shows block errors on eject, but the data is never corrupted. You sure you're unmounting the card before ejecting?

> 
BTW, have one of you folks has news on spca5xx for the OrbiCam?

Still not ready yet, the head developer acknowledges that he's working on it, but he needs more time (since it's a completely new camera chipset)

---

### Post by mfa81 on 2006-11-09
> **mfa81 said:**
> I tried to load tifm_sd and tifm_core but I cant get sd card working fine ! whem I insert a MS, SD card I just receive messages from tifm_7xx1, if I unload tifm_7xx1 I dont see any message inserting or remove a media card, just messages about device disable / enabled! Again fresh Edgy install... on dapper my sd card was working out of the box, just insert a media card to see the icon on my kde desktop.

```

Nov  6 22:13:14 sharapova kernel: [17181235.068000] tifm_7xx1: ms card detected in socket 0
Nov  6 22:13:18 sharapova kernel: [17181239.456000] tifm_7xx1: demand removing card from socket 0
Nov  6 22:13:28 sharapova kernel: [17181249.124000] ACPI: PCI interrupt for device 0000:0a:09.2 disabled
Nov  6 22:15:49 sharapova kernel: [17181390.520000] ACPI: PCI Interrupt 0000:0a:09.2[A] -> GSI 20 (level, low) -> IRQ 201

```

why so many things just stop to work on Edgy ?

Can anyone take a look at my post and give me a tip on how to get sd card reader works

---

### Post by jdong on 2006-11-09
I'm not sure if the driver supports anything other than MMC and SD cards.

---

### Post by nik1111 on 2006-11-09
My MMC card works fine.Dont know for other cards.

---

### Post by mfa81 on 2006-11-09
> **jdong said:**
> I'm not sure if the driver supports anything other than MMC and SD cards.

on dapper I was able to read MS and SD cards, but nothing works with edgy

---

### Post by unz on 2006-11-10
with my xd and ms cards ... 
```
Nov 11 00:55:50 unzWire [4306021.639000] tifm_7xx1: xd card detected in socket 0
Nov 11 01:01:58 unzWire [4306389.559000] tifm_7xx1: demand removing card from socket 0

Nov 11 01:05:00 unzWire [4306571.837000] tifm_7xx1: ms card detected in socket 0
Nov 11 01:06:34 unzWire [4306665.460000] tifm_7xx1: demand removing card from socket 0


```they are detected, but i can't get anything else, neither a mount point to check

---

### Post by Kwunman on 2006-11-16
Hi,

A quick note about the Card Reader.

I use edgy and find that my 512mb sd card (actually a mini sd card used through an adaptor) has no problems whatsoever when used in the laptop.

However, recently i bought a 2gb version hoping it would work just as well.
Unfortunately, when i put it in the card reader, the log says that the card failed to respond for a long period of time and demands me to remove the card.

Doing a bit of quick research on the net, i have found out that the kernel seems to have problems with larger sized cards.

This may be the reason that some peoples cards aren't working.

In my opinion, i think that the laptop is timing out before it has finished reading or doing what ever it does with the card.

I am no linux expert or developer, but would really like to see this problem fixed, and i hope this info helps.

Thanks.

Kwun-Man

---

### Post by nichomerri on 2006-11-16
Any news on the ms cards? I've got the same problem as unz

---

### Post by T-One on 2006-11-17
I can confirm adding the tifm_sd module allows the SD slot on an HP/Compaq nc6230 to work just fine. I have a 256MB MicroSD card in an SD adapter, formatted FAT32. Udev/HAL recognizes it, Gnome has an icon for it, and it works fine. (Remember to unmount an SD/MMC before removing it).

I think I also read somewhere (I believe it was the Texas Instruments SD drivers mailing list) that the current driver only supports up to 512 cards at the moment.

Thanks for the tip on the driver!

---

### Post by jdong on 2006-11-17
Yeah, this driver is definitely in infancy. I've used SD and MMC, haven't had a chance to test any other media.



Maybe grabbing the svn snapshot of the driver would get you better results, too.

EDIT: I have used a 1GB SD card successfully with the reader before.

---

### Post by cbudden on 2006-11-18
Does anyone know the status of the webcam driver?

---

### Post by jdong on 2006-11-18
No change from last time. Please follow the spca50x-devs mailing list :)

---

### Post by cbudden on 2006-11-18
> **jdong said:**
> No change from last time. Please follow the spca50x-devs mailing list :)

Thanks jdong.  I have subscribed to the list now.

---

### Post by giorgenes on 2006-11-18
Hi there,

I`ve just bought an aspire 5672wlmi an I`m experiencing some problem.
I`ve installed ubuntun edgy on the "D:" partition that comes shiped with it.
In the beggining, everything worked fine.
Sometimes, after swithing from windows to ubuntu, either my wireless or sound doesn`t work. Then I reboot and it gets working again.
After some days, the wireless stoped working. just work on windows, and sometimes I have to enable the antenna becouse it gets misteriously turned off.
Now my ubuntu doensn`t boot anymore. It gets freezed in the boot screen. :(

Any similar experience?
thank you

---

### Post by nik1111 on 2006-11-18
I had the same issue. Sometimes, rarely though, the sound will not work or edgy may hang after boot.Don't know why it happens, but it seems as if dapper was a bit more stable than edgy. But edgy fixes many other problems and it's better to use in general. Wireless would work every time but since I re-formatted it doesnt work, I don't know why and I don't care cause I don't use it. My hard disk died and it could be a general failure of hardware for me so I can't say anything about the wireless.

About the sound, it happens rarely and at random so I can't say what is causing it. I am sure others have that issue too. Just reboot, don't worry.

About the freezing during boot, try to wait 2-5 minutes, it may be having a hard time configuring the network. Or you may have some faulty hardware that causes that. Or...anything. I had to re-install edgy over something similar a month ago. Try control alt and backspace, perhaps it's loading everything but fails to show it.If you can get to the console, try to start X as root. And download some hard disk monitoring tools if you get it to boot, they are in synaptic they might come in handy in the future, I hope you don't have the same problem I had.

---

### Post by jdong on 2006-11-18
I've seen the "sound doesn't work on a few rare bootups, it hangs during modprobe for a while before booting" twice.. I dismissed it as a fluke. Interesting problem, I got to say.

---

### Post by nik1111 on 2006-11-19
In my opinion there are differences in our hardware and thats why we have different problems in edgy. Depending where and when you bought it. Mine is a 5672AWLMi. There are some variations for this model.

---

### Post by Frank Golden on 2006-11-20
Hi Guys,
   Just upgraded my 5672 from the stock 1.66 GHz Core Duo (yonah)
to a 2.00 GHz Core 2 Duo (merom). Difficulty, easy for this user.
Acer made it fairly easy and straightfoward, especially with the BIOS updates on their Euro sites. Hmmm, wonder why the US site
still has the stock BIOS. Modest gains in performance but Ubuntu
6.06.1 LTS and Edgy work perfectly with it. Same goes for PCLinuxOs and Zenwalk 3.0 which also share my HDD.
Downside a slight increase in heat as reported by ACPI.

---

### Post by giorgenes on 2006-11-20
the main problem with my 5672wlmi is the wireless.
frequently when I boot up, the antenna is turned off, and ubuntu simply can't find the device.
That happens inside windows too, but there I can turn the antenna on by hand.

Does someone know how to turn it on inside ubuntu?
tks

---

### Post by gmc on 2006-11-22
> **Frank Golden said:**
> Hi Guys,
   Just upgraded my 5672 from the stock 1.66 GHz Core Duo (yonah)
to a 2.00 GHz Core 2 Duo (merom). Difficulty, easy for this user.
Acer made it fairly easy and straightfoward, especially with the BIOS updates on their Euro sites. Hmmm, wonder why the US site
still has the stock BIOS. Modest gains in performance but Ubuntu
6.06.1 LTS and Edgy work perfectly with it. Same goes for PCLinuxOs and Zenwalk 3.0 which also share my HDD.
Downside a slight increase in heat as reported by ACPI.

Can you elaborate on this upgrade. I'd love to upgrade mine.

G.

---

### Post by Frank Golden on 2006-11-22
> **gmc said:**
> Can you elaborate on this upgrade. I'd love to upgrade mine.

G.
Hi G,
First, be aware that Acer considers this voiding your warranty.
Second, make sure you have the latest BIOS update from Acer Euro
for full merom support.
Third, start up your machine and let it warm up for a few minutes, then power it down. (this will soften the thermal paste
to make dissasembly easier)
Fourth, remove battery and follow normal procedures to prevent static discharge.
  I obtained my new Merom from NewEgg. I paid approx $300.00
for it. To change out remove the screws holding the plastic cover on the underside of computer. The one you remove to change RAM. You will see the fan/heatpipe assy. There are 7 screws holding it in and a small electrical connector. Loosen all 7 screws. They are held captive with small plastic washers like the screws that secure the cover you removed earlier. Now using a needle nose plier gently unplug the electrical connector.
At this point you should be able to gently lift the fan/heatpipe assembly out of your computer. On my machine the cpu had a piece of foil with a pink thermal compound on it.
Remove and using isopropyl alcohol remove the remaining compound from the underside of the copper heat spreader in the area of the cpu. Remove the old cpu by turning the lock screw a half turn counterclockwise as shown in the diagram/instruction
that came with your new cpu. This will free up the cpu so you can
lift it out. Place a small amount of a thermal paste on the rectangular die in the center of the cpu and spread it around with your finger. I used Dynex silver but any good thermal compound will work. Install the new cpu by gently lowering
into the socket. There is a small triangle on the corner of the cpu that needs to line up to a similar triangle on the socket.
Make sure it is fully seated and turn the lock screw clockwise to seat. Be gentle, don't force any thing.
  You will notice several other heat pads on the heatpipe assy.
I didn't disturb mine, but I did put a small amount of thermal compound on each and spread evenly.
   Now gently reinstall the fan/heatpipe assy, making sure to align the screws. Tighten screws snug but don't overtighten.
Reconect the electrical plug and reinstall the bottom cover.
Make sure the cover is fully seated in the area in back of computer (around the DVI connector). Reinstall battery.
Boot computer. BIOS should recognize new processor etc.

See the below link for more info and pictures.

[http://www.notebookforums.com/thread156778.html](http://www.notebookforums.com/thread156778.html)

---

### Post by gmc on 2006-11-22
Hi Frank,

Looks to be pretty involved and it looks like I'll be getting a Core 2 for Christmas after all. Thank You! (though the wife won't :-)

G(ord).

---

### Post by lir on 2006-11-22
I've upgraded from dapper flight 7 most of the packages like kernels, acpi and others, I'm running on 2.6.15-27-686 but cpu scaling is acting all weird.
At first login to gnome (after the upgrade) it notified me that I don't have cpu scaling working cause powernowd is not installed so I installed it and it should have been working only it's not.

Whatever I set the cpu scaling to be (manually with the applet) I continue seeing the max rate of the processor in /proc/cpuinfo.

I remember then that I was using jdong's scripts (acpi.tar.gz) for doing the cpu frequency thing rather than powernowd so maybe it has something related... where are the current/updated acpi.tar.gz packages available?


Thanks.

---

### Post by lir on 2006-11-22
Another important issue I'm experiencing is that the laptop just freezes from time to time for several seconds and then continues as if everything is ok... I think I noticed this on windows as well but still... has anyone ever encountered in something like this?

/var/log/syslog shows:
```

Nov 23 00:39:39 localhost kernel: [17191692.132000] psmouse.c: TouchPad at isa0060/serio4/input0 lost sync at byte 4
Nov 23 00:39:39 localhost kernel: [17191692.136000] psmouse.c: TouchPad at isa0060/serio4/input0 lost sync at byte 1
Nov 23 00:39:39 localhost kernel: [17191692.148000] psmouse.c: TouchPad at isa0060/serio4/input0 - driver resynched.

```

(By the way, I followed the thread and saw you mentioned the sd card reader  module tifm_sd which I don't have on my system... where do I get it from?)


Thanks.
This thread has been a great help.

---

### Post by Frank Golden on 2006-11-22
> **gmc said:**
> Hi Frank,

Looks to be pretty involved and it looks like I'll be getting a Core 2 for Christmas after all. Thank You! (though the wife won't :-)

G(ord).
Hi Gord,
   It's not really too involved. Just move deliberately
and take your time. I was able to swap out the processor in about 15 minutes. Acer really does make it easy.
Search around at the 
notebook forums site I linked to earlier here for much more info
about the Core 2 Duo and the 5672 as well..
Processor works great with Ubuntu 6.06.1 LTS.
I also have Edgy final installed on another HDD and it works great there also.
Works great with Zenwalk 3.0 and PCLinuxOS .93 as well.
Powernowd or some kind of throttling is in action on all distros.
This keeps the processor's heat relatively low, around 122° to 124° F with occasional highs of around 150° F.
In XP I use Notebook Hardware Control (NHC) to keep processor at 2.0GHz all the time and normal temps are around 128°-132° F. When I run SisoftSandra's burn in utility I see highs of around 163° F.
As I reported earlier ~10° F. warmer overall.

---

### Post by lir on 2006-11-25
I'm using jdong's acpi.tar.gz package for cpu frequency scaling and I hav all the module for it loaded (no powernowd daemon running) and I'm seeing in the gnome-applet thing that indicates cpu usage that it sometimes jumps from 1ghz to 1.66ghz but if I look at /proc/cpuinfo the "cpu MHz" column always show the speed on 1666, so is this working or not?


Thanks everyone.

---

### Post by scifan on 2006-11-25
I think I'll wait for the warranty to expire on mine before doing this...

---

### Post by Frank Golden on 2006-11-28
> **scifan said:**
> I think I'll wait for the warranty to expire on mine before doing this...
I got extended warranty from Acer. 2.5 years more. Couldn't wait. Had to have something to tinker with. LOL

---

### Post by jdong on 2006-11-29
The issue with PCM being selected as the master channel instead of Front in GNOME ([https://launchpad.net/distros/ubuntu/+source/gst-plugins-base0.10/+bug/45345](https://launchpad.net/distros/ubuntu/+source/gst-plugins-base0.10/+bug/45345)) has been fixed in GStreamer CVS. The patch is at [http://bugzilla.gnome.org/attachment.cgi?id=72541](http://bugzilla.gnome.org/attachment.cgi?id=72541)


I've prepared a modified source package with these changes at [http://buntudot.org/people/~jdong/gst-plugins-base/gst-plugins-base0.10_0.10.10-2ubuntu1.0jdong1.dsc](http://buntudot.org/people/~jdong/gst-plugins-base/gst-plugins-base0.10_0.10.10-2ubuntu1.0jdong1.dsc)

I'm not gonna upload binaries because (1) there's like 5 or 6 debs generated and they'll be a pain for you guys to download, and err.... (2) YOU GUYS HAVE DUAL CORE LAPTOPS and no excuse for not wanting to compile something :D

It's recommended to use prevu (search the forum HOWTO's) to build it, by issuing
```

prevu http://buntudot.org/people/~jdong/gst-plugins-base/gst-plugins-base0.10_0.10.10-2ubuntu1.0jdong1.dsc
apt-get update
apt-get dist-upgrade

```

Logoff/login, and your volume hotkeys should now change Master instead of PCM. You may still need to change the preferences on your mixer applet to control Front.

---

### Post by cbudden on 2006-11-29
> **jdong said:**
> The issue with PCM being selected as the master channel instead of Front in GNOME ([https://launchpad.net/distros/ubuntu/+source/gst-plugins-base0.10/+bug/45345](https://launchpad.net/distros/ubuntu/+source/gst-plugins-base0.10/+bug/45345)) has been fixed in GStreamer CVS. The patch is at [http://bugzilla.gnome.org/attachment.cgi?id=72541](http://bugzilla.gnome.org/attachment.cgi?id=72541)


I've prepared a modified source package with these changes at [http://buntudot.org/people/~jdong/gst-plugins-base/gst-plugins-base0.10_0.10.10-2ubuntu1.0jdong1.dsc](http://buntudot.org/people/~jdong/gst-plugins-base/gst-plugins-base0.10_0.10.10-2ubuntu1.0jdong1.dsc)

I'm not gonna upload binaries because (1) there's like 5 or 6 debs generated and they'll be a pain for you guys to download, and err.... (2) YOU GUYS HAVE DUAL CORE LAPTOPS and no excuse for not wanting to compile something :D

It's recommended to use prevu (search the forum HOWTO's) to build it, by issuing
```

prevu http://buntudot.org/people/~jdong/gst-plugins-base/gst-plugins-base0.10_0.10.10-2ubuntu1.0jdong1.dsc
apt-get update
apt-get dist-upgrade

```

Logoff/login, and your volume hotkeys should now change Master instead of PCM. You may still need to change the preferences on your mixer applet to control Front.


I have attempted to install prevu, and on the prevu-init step it stops on :

```

I: Base system installed successfully.
 -> debootstrap finished
 -> copying local configuration
  -> Installing apt-lines
Refreshing the base.tgz 
 -> upgrading packages
 -> mounting /proc filesystem
 -> mounting /dev/pts filesystem
-> Mounting /var/cache/prevu/debs
 -> installing dummy policy-rc.d
Ign file: ./ Release.gpg
Ign file: ./ Release                  
Ign file: ./ Packages                 
44% [Connecting to archive.ubuntu.com (195.248.90.35)]

```

I am behind a proxy and have set a proxy for wget, apt and export http_proxy.  I can access that IP address through firefox. Anyone know whats going on?

---

### Post by cbudden on 2006-11-29
> **cbudden said:**
> I have attempted to install prevu, and on the prevu-init step it stops on :

```

I: Base system installed successfully.
 -> debootstrap finished
 -> copying local configuration
  -> Installing apt-lines
Refreshing the base.tgz 
 -> upgrading packages
 -> mounting /proc filesystem
 -> mounting /dev/pts filesystem
-> Mounting /var/cache/prevu/debs
 -> installing dummy policy-rc.d
Ign file: ./ Release.gpg
Ign file: ./ Release                  
Ign file: ./ Packages                 
44% [Connecting to archive.ubuntu.com (195.248.90.35)]

```

I am behind a proxy and have set a proxy for wget, apt and export http_proxy.  I can access that IP address through firefox. Anyone know whats going on?


Thanks to jdong, I have built some packages.  Here are the debs:

[http://cbudden.sitesled.com/Fixed_debs.zip](http://cbudden.sitesled.com/Fixed_debs.zip)

---

### Post by tonyr1988 on 2006-11-30
I got my first SD card ever the other day (1GB on sale for $3 after rebate :D) for my upcoming Wii and my wife's camera. Problem: I have no clue where to start. I can plug it into the card reader, but I'm not really sure where to go from here.

I've searched this thread and found a few topics on getting SD cards to work, but most of them say "it worked out of the box." Nothing shows up on my desktop (like a thumb drive, CD, etc does). Is it in /media somewhere?

Sorry for the uber-n00b question, I just need help on getting started.

PS Should it stick out a little bit or go all the way in? It should stick out, right?

---

### Post by jdong on 2006-12-03
I've got some good news (and no, it doesn't involve saving money on car insurance....) regarding our webcams. The new gpsca driver ([http://mxhaard.free.fr/spca50x/Investigation/Gspca/gspcav1-01.00.08.tar.gz](http://mxhaard.free.fr/spca50x/Investigation/Gspca/gspcav1-01.00.08.tar.gz)) now recognizes our webcam as a Vimicro vc0321 chipset and creates /dev/video0 device for it, but unfortunately it's not functional yet. However, it does show a good step forward :)

Currently accessing /dev/video0 generates the following errors:
```

[17188907.224000] 
[17188907.268000] /home/jdong/tmp/backports/gspcav1/gspca_core.c: [spca5xx_set_light_freq:1839] Sensor currently not support light frequency banding filters.
[17188907.268000] /home/jdong/tmp/backports/gspcav1/gspca_core.c: [gspca_init_transfert:938] get iso nbalt 7
[17188907.268000] /home/jdong/tmp/backports/gspcav1/gspca_core.c: [gspca_set_isoc_ep:847] enter get iso ep 
[17188907.268000] /home/jdong/tmp/backports/gspcav1/gspca_core.c: [gspca_set_isoc_ep:854] test ISO EndPoint  129
[17188907.268000] /home/jdong/tmp/backports/gspcav1/gspca_core.c: [gspca_set_isoc_ep:854] test ISO EndPoint  130
[17188907.268000] /home/jdong/tmp/backports/gspcav1/gspca_core.c: [gspca_set_isoc_ep:854] test ISO EndPoint  129
[17188907.268000] /home/jdong/tmp/backports/gspcav1/gspca_core.c: [gspca_set_isoc_ep:854] test ISO EndPoint  130
[17188907.268000] /home/jdong/tmp/backports/gspcav1/gspca_core.c: [gspca_set_isoc_ep:854] test ISO EndPoint  129
[17188907.268000] /home/jdong/tmp/backports/gspcav1/gspca_core.c: [gspca_set_isoc_ep:854] test ISO EndPoint  130
[17188907.268000] /home/jdong/tmp/backports/gspcav1/gspca_core.c: [gspca_set_isoc_ep:854] test ISO EndPoint  129
[17188907.268000] /home/jdong/tmp/backports/gspcav1/gspca_core.c: [gspca_set_isoc_ep:854] test ISO EndPoint  130
[17188907.268000] /home/jdong/tmp/backports/gspcav1/gspca_core.c: [gspca_set_isoc_ep:854] test ISO EndPoint  129
[17188907.268000] /home/jdong/tmp/backports/gspcav1/gspca_core.c: [gspca_set_isoc_ep:854] test ISO EndPoint  130
[17188907.268000] /home/jdong/tmp/backports/gspcav1/gspca_core.c: [gspca_set_isoc_ep:854] test ISO EndPoint  129
[17188907.268000] /home/jdong/tmp/backports/gspcav1/gspca_core.c: [gspca_set_isoc_ep:854] test ISO EndPoint  130
[17188907.268000] /home/jdong/tmp/backports/gspcav1/gspca_core.c: [gspca_set_isoc_ep:854] test ISO EndPoint  129
[17188907.268000] /home/jdong/tmp/backports/gspcav1/gspca_core.c: [gspca_set_isoc_ep:854] test ISO EndPoint  130
[17188907.268000] /home/jdong/tmp/backports/gspcav1/gspca_core.c: [gspca_set_isoc_ep:875] FATAL ISO EndPoint not found 
[17188907.268000] /home/jdong/tmp/backports/gspcav1/gspca_core.c: [spca5xx_open:1904]  DEALLOC error on init_Isoc
[17188907.268000] 

```

---

### Post by cbudden on 2006-12-03
> **jdong said:**
> I've got some good news (and no, it doesn't involve saving money on car insurance....) regarding our webcams. The new gpsca driver ([http://mxhaard.free.fr/spca50x/Investigation/Gspca/gspcav1-01.00.08.tar.gz](http://mxhaard.free.fr/spca50x/Investigation/Gspca/gspcav1-01.00.08.tar.gz)) now recognizes our webcam as a Vimicro vc0321 chipset and creates /dev/video0 device for it, but unfortunately it's not functional yet. However, it does show a good step forward :)

Currently accessing /dev/video0 generates the following errors:
```

[17188907.224000] 
[17188907.268000] /home/jdong/tmp/backports/gspcav1/gspca_core.c: [spca5xx_set_light_freq:1839] Sensor currently not support light frequency banding filters.
[17188907.268000] /home/jdong/tmp/backports/gspcav1/gspca_core.c: [gspca_init_transfert:938] get iso nbalt 7
[17188907.268000] /home/jdong/tmp/backports/gspcav1/gspca_core.c: [gspca_set_isoc_ep:847] enter get iso ep 
[17188907.268000] /home/jdong/tmp/backports/gspcav1/gspca_core.c: [gspca_set_isoc_ep:854] test ISO EndPoint  129
[17188907.268000] /home/jdong/tmp/backports/gspcav1/gspca_core.c: [gspca_set_isoc_ep:854] test ISO EndPoint  130
[17188907.268000] /home/jdong/tmp/backports/gspcav1/gspca_core.c: [gspca_set_isoc_ep:854] test ISO EndPoint  129
[17188907.268000] /home/jdong/tmp/backports/gspcav1/gspca_core.c: [gspca_set_isoc_ep:854] test ISO EndPoint  130
[17188907.268000] /home/jdong/tmp/backports/gspcav1/gspca_core.c: [gspca_set_isoc_ep:854] test ISO EndPoint  129
[17188907.268000] /home/jdong/tmp/backports/gspcav1/gspca_core.c: [gspca_set_isoc_ep:854] test ISO EndPoint  130
[17188907.268000] /home/jdong/tmp/backports/gspcav1/gspca_core.c: [gspca_set_isoc_ep:854] test ISO EndPoint  129
[17188907.268000] /home/jdong/tmp/backports/gspcav1/gspca_core.c: [gspca_set_isoc_ep:854] test ISO EndPoint  130
[17188907.268000] /home/jdong/tmp/backports/gspcav1/gspca_core.c: [gspca_set_isoc_ep:854] test ISO EndPoint  129
[17188907.268000] /home/jdong/tmp/backports/gspcav1/gspca_core.c: [gspca_set_isoc_ep:854] test ISO EndPoint  130
[17188907.268000] /home/jdong/tmp/backports/gspcav1/gspca_core.c: [gspca_set_isoc_ep:854] test ISO EndPoint  129
[17188907.268000] /home/jdong/tmp/backports/gspcav1/gspca_core.c: [gspca_set_isoc_ep:854] test ISO EndPoint  130
[17188907.268000] /home/jdong/tmp/backports/gspcav1/gspca_core.c: [gspca_set_isoc_ep:854] test ISO EndPoint  129
[17188907.268000] /home/jdong/tmp/backports/gspcav1/gspca_core.c: [gspca_set_isoc_ep:854] test ISO EndPoint  130
[17188907.268000] /home/jdong/tmp/backports/gspcav1/gspca_core.c: [gspca_set_isoc_ep:875] FATAL ISO EndPoint not found 
[17188907.268000] /home/jdong/tmp/backports/gspcav1/gspca_core.c: [spca5xx_open:1904]  DEALLOC error on init_Isoc
[17188907.268000] 

```


This is good news!  I guess its make;make install to install these drivers?

Chris

---

### Post by jdong on 2006-12-03
There's a ./gspca_build script that automates the process for you. Just have your compiler and linux headers installed.

But I wouldn't spend much time for it. As I said, the current release doesn't actually work. It just contains the bare-bones code that detects the new camera chipset.

---

### Post by nik1111 on 2006-12-03
Jdong what does this actually mean? Will a working version be out soon or it's gonna take a long time?

---

### Post by jdong on 2006-12-03
> **nik1111 said:**
> Jdong what does this actually mean? Will a working version be out soon or it's gonna take a long time?

It means we are really close to having functional webcam drivers (I'd estimate 1 or 2 more releases of the driver before we can start seeing video streaming from the cam!). Before this, all we've heard is the talk. Now, we finally see actual code towards the webcam working :)

---

### Post by jdong on 2006-12-04
Another gspca snapshot was made available last night, and now the /dev/video0 device opens without errors, though I can't get any output than a black screen :)

It's pretty cool and exciting to see that green light on our camera light up though!

---

### Post by nik1111 on 2006-12-04
Great news! should we try it or it wont work with any application?did you try amsn?

---

### Post by jdong on 2006-12-04
It's yet-another-step closer to working but still non-working at the moment. All you'll get is a blank video feed. but the shiny green light on the camera will light up :)

---

### Post by llbra on 2006-12-07
> **jdong said:**
> Interesting... My SD cardreader also shows block errors on eject, but the data is never corrupted. You sure you're unmounting the card before ejecting?

Pretty sure. The problem also occours before ejecting the card. I tried to read from it, and the card just don`t read. "dmesg" explains it:


(Starting from when I plug the card. The errors appear when I try to backup it - from my Dane-elec card reader I can read and write)
$ dmesg
[17190772.360000] tifm_7xx1: sd card detected in socket 1
[17190773.264000] mmcblk0: mmc0:a95c SD01G 992000KiB 
[17190773.264000]  mmcblk0: p1
[17190773.384000] mmcblk0: error 4 sending stop command
[17190773.384000] end_request: I/O error, dev mmcblk0, sector 1983992
[17190773.384000] Buffer I/O error on device mmcblk0, logical block 247999
[17190773.384000] mmcblk0: error 4 sending stop command
[17190773.384000] end_request: I/O error, dev mmcblk0, sector 1983992
[17190773.384000] Buffer I/O error on device mmcblk0, logical block 247999
[17190773.384000] mmcblk0: error 4 sending stop command
[17190773.384000] end_request: I/O error, dev mmcblk0, sector 1983992
[17190773.384000] Buffer I/O error on device mmcblk0, logical block 247999
[17190773.388000] mmcblk0: error 4 sending stop command
[17190773.388000] end_request: I/O error, dev mmcblk0, sector 1983992
[17190773.388000] Buffer I/O error on device mmcblk0, logical block 247999
[17190773.388000] mmcblk0: error 4 sending stop command
[17190773.388000] end_request: I/O error, dev mmcblk0, sector 1983992
[17190773.388000] Buffer I/O error on device mmcblk0, logical block 247999
[17190773.388000] mmcblk0: error 4 sending stop command
[17190773.388000] end_request: I/O error, dev mmcblk0, sector 1983992
[17190773.388000] Buffer I/O error on device mmcblk0, logical block 247999
[17190773.392000] mmcblk0: error 4 sending stop command
[17190773.392000] end_request: I/O error, dev mmcblk0, sector 1983992
[17190773.392000] Buffer I/O error on device mmcblk0, logical block 247999
[17190773.396000] mmcblk0: error 4 sending stop command
[17190773.396000] end_request: I/O error, dev mmcblk0, sector 1983992
[17190773.396000] Buffer I/O error on device mmcblk0, logical block 247999
[17190775.244000] FAT: utf8 is not a recommended IO charset for FAT filesystems, filesystem will be case sensitive!


Just for the notice, my system is using pt_BR.utf-8 char encoding.

Thanks in advance.

---

### Post by tonyr1988 on 2006-12-11
My 5-in-1 reader (specifically, the SD card) isn't working at all. When I put an SD card in, nothing shows up on my desktop, nothing seems special in /media (what should it be under?), and I notice no changes.

I read on another thread to do these:

> sudo modprobe tifm_7xx1
sudo modprobe tifm_core
sudo modprobe tifm_sd

On all of them, it tells me "FATAL: Module __________ not found."

However, the other thread DID mention running Edgy. Do I need to upgrade just to get the drivers? How did the rest of you get your SD cards working?

Oh yeah, and I'm not sure if it helps, but this is from lspci:

> 0000:0a:09.0 CardBus bridge: Texas Instruments: Unknown device 8039
0000:0a:09.1 FireWire (IEEE 1394): Texas Instruments: Unknown device 803a
0000:0a:09.2 Mass storage controller: Texas Instruments: Unknown device 803b

---

### Post by jdong on 2006-12-11
Right, the card driver is only in Edgy. It will not compile in Dapper either because it demands a newer kernel (2.6.16 or higher)

---

### Post by tonyr1988 on 2006-12-11
Has anyone experienced problems upgrading to Edgy from Dapper on this Acer? Of course I'll back everything up, but is it best to upgrade or fresh install?

---

### Post by jdong on 2006-12-11
Your hardware will work perfectly in Edgy, minus the noted HAL thing in this thread (without a patch to HAL, battery discharge % and time will be incorrectly reported)

As far as the upgrade procedure, I cannot guarantee how smoothly it would work out for you. Definitely approach it with a full backup, and if possible try not to be heavily using your system while the upgrade is in progress.

Approach it with the attitude that the upgrade will fail halfway through, the system will be unbootable, and only /home will be intact and you may need to go in with a LiveCD to pull off data. That way, you are properly prepared to deal with the worst.

---

### Post by nik1111 on 2006-12-11
When I updated from dapper to edgy the upgrade went smoothly till the end when I had to reboot.
But..
When i rebooted the system hung up. Every time. I was lucky enough that I could access the command line,and I was able to do that only by using the oldest kernel version..I had installed 4 or 5 at that time and none other worked, I dont know why. So I was able to burn my /home directory through the command line. 
So
Backup and if you don't have a very loaded system, a fresh install is better. But since the update procedure might have been debugged by now you can try that as well and see how it goes. It might work for you.

---

### Post by nik1111 on 2006-12-11
My last post was number 666 and gave me 13 beans!Even if you aren't superstitious you have to change that!

---

### Post by mfa81 on 2006-12-12
> **jdong said:**
> Right, the card driver is only in Edgy. It will not compile in Dapper either because it demands a newer kernel (2.6.16 or higher)

Well, my SD card reader worked out of box with Dapper. Just put the sd card and the folder appears on desktop. With Edgy I can't get sd card working yet.  The modules are loaded some messages in /var/log/messages, but nothing on my desktop. See the link


[http://www.ubuntuforums.org/showthread.php?p=1736121#post1736121](http://www.ubuntuforums.org/showthread.php?p=1736121#post1736121)

---

### Post by jdong on 2006-12-12
> **mfa81 said:**
> Well, my SD card reader worked out of box with Dapper. Just put the sd card and the folder appears on desktop. With Edgy I can't get sd card working yet.  The modules are loaded some messages in /var/log/messages, but nothing on my desktop. See the link


[http://www.ubuntuforums.org/showthread.php?p=1736121#post1736121](http://www.ubuntuforums.org/showthread.php?p=1736121#post1736121)

If your SD cardreader worked in any fashion on Dapper without self-compiling a 2.6.16 or greater kernel, then you **do not** have the same cardreader that the others here have... Our readers only operate with the proprietary TI FlashMedia protocol, not the generic USB Mass Storage or SDHCI interfaces and as a result only work with the tifm21xx driver.

---

### Post by nik1111 on 2006-12-12
That's probably true, there are hardware differences. For example, I remember some guys reporting they had some dvd drive brand other than pioneer. It has to do with where and when you bought the laptop.

---

### Post by Frank Golden on 2006-12-13
> **nik1111 said:**
> That's probably true, there are hardware differences. For example, I remember some guys reporting they had some dvd drive brand other than pioneer. It has to do with where and when you bought the laptop.I second that. My
5672 has the TI card reader and does not have the Pioneer DVD.
It uses the Matshita DVD drive. My machine war bought in April at CompUSA in Ann Arbor, Mi.

---

### Post by cbudden on 2006-12-13
Hello.

Has anyone had trouble with suspend and hibernate on edgy?  With Dapper and edgy testing they both worked fine, but now it is random if they work, so I can't use either in case I loose data.

Anyone else getting this?

---

### Post by jdong on 2006-12-13
I've had slight bits of random flakiness in both Dapper and Edgy with suspending. Sometimes upon resume it will just hang at a blank screen, no HD activity, no response to keyboard input.

Hibernate has been rock solid though, with both standard kernel swsusp and uswsusp from universe.

I typically don't find myself using either suspend or hibernate... Edgy boots in 30 seconds which is fast enough to resume work, while just closing the lid is "good enough" for a quick break.

---

### Post by cbudden on 2006-12-13
> **jdong said:**
> I've had slight bits of random flakiness in both Dapper and Edgy with suspending. Sometimes upon resume it will just hang at a blank screen, no HD activity, no response to keyboard input.

Hibernate has been rock solid though, with both standard kernel swsusp and uswsusp from universe.

I typically don't find myself using either suspend or hibernate... Edgy boots in 30 seconds which is fast enough to resume work, while just closing the lid is "good enough" for a quick break.

Hibernate has been more reliable of late, but sometimes it just hangs on a black screen after doing the hibernate process.

edit

Another reason that hibernate was dodgy for me was probs my /sys/power/image_size set to 5 gigs rather than the 2 gigs that it should be.

---

### Post by nik1111 on 2006-12-13
Guys I just saw the new headers are available via ubuntu update. I am wondering though if there will be a problem with the ATI cards. I heard some guys had a problem with nvidia, what about our laptops?

---

### Post by jdong on 2006-12-13
It did not cause an issue with my fglrx 8.31.5 setup, but I don't know if it would cause any other problems.

Today's nvidia issue only affected a handful of people, like maybe 5-10 forum members, compared to the last upgrade issue with Dapper that affected thousands after thousands of people.

I wouldn't worry about it.

---

### Post by cbudden on 2006-12-14
Well, I thought I fixed my hibernate...

After making sure my /sys/power/image_size was set to 2096472, I told the machine to hibernate.  After it didn't work i looked at /sys/power/image_size and that had reset to 524288000.  I have a script in the suspend.d folder to echo 2096472 to /sys/power/image_size and it is set to executable but something seems to be overriding it. This is very annoying as this used to work!

Here is my syslog

```

Dec 14 21:14:55 cbudden-laptop kernel: [17191716.916000] atkbd.c: Unknown key pressed (translated set 2, code 0xb3 on isa0060/serio0).
Dec 14 21:14:55 cbudden-laptop kernel: [17191716.916000] atkbd.c: Use 'setkeycodes e033 <keycode>' to make it known.
Dec 14 21:14:55 cbudden-laptop kernel: [17191717.140000] atkbd.c: Unknown key released (translated set 2, code 0xb3 on isa0060/serio0).
Dec 14 21:14:55 cbudden-laptop kernel: [17191717.140000] atkbd.c: Use 'setkeycodes e033 <keycode>' to make it known.
Dec 14 21:21:42 cbudden-laptop dhcdbd: Unrequested down ?:3
Dec 14 21:21:42 cbudden-laptop kernel: [17192124.320000] ACPI: PCI interrupt for device 0000:04:00.0 disabled
Dec 14 21:21:46 cbudden-laptop kernel: [17192127.652000] Freezing cpus ...
Dec 14 21:21:46 cbudden-laptop kernel: [17192127.768000] CPU 1 is now offline
Dec 14 21:21:46 cbudden-laptop kernel: [17192127.768000] SMP alternatives: switching to UP code
Dec 14 21:22:09 cbudden-laptop kernel: [17192127.768000] CPU1 is down
Dec 14 21:22:11 cbudden-laptop kernel: [17192127.768000] Stopping tasks: ===========================================================================================================================================================|
Dec 14 21:22:11 cbudden-laptop kernel: [17192127.776000] Shrinking memory...  ^H-^H\^H|^H/^H-^H\^H|^H/^H-^Hdone (89912 pages freed)
Dec 14 21:22:11 cbudden-laptop kernel: [17192135.008000] gspca 5-8:1.0: no suspend for driver gspca?
Dec 14 21:22:11 cbudden-laptop kernel: [17192135.296000] ACPI: PCI interrupt for device 0000:0a:09.2 disabled
Dec 14 21:22:11 cbudden-laptop kernel: [17192135.296000] ACPI: PCI interrupt for device 0000:0a:09.0 disabled
Dec 14 21:22:11 cbudden-laptop kernel: [17192135.296000] eth%%d: Going into suspend...
Dec 14 21:22:11 cbudden-laptop kernel: [17192135.296000] ACPI: PCI interrupt for device 0000:03:00.0 disabled
Dec 14 21:22:11 cbudden-laptop kernel: [17192145.904000] ACPI: PCI interrupt for device 0000:01:00.0 disabled
Dec 14 21:22:11 cbudden-laptop kernel: [17192145.904000] ACPI: PCI interrupt for device 0000:00:1f.2 disabled
Dec 14 21:22:11 cbudden-laptop kernel: [17192145.904000] ACPI: PCI interrupt for device 0000:00:1d.7 disabled
Dec 14 21:22:11 cbudden-laptop kernel: [17192145.920000] ACPI: PCI interrupt for device 0000:00:1d.3 disabled
Dec 14 21:22:11 cbudden-laptop kernel: [17192145.920000] ACPI: PCI interrupt for device 0000:00:1d.2 disabled
Dec 14 21:22:11 cbudden-laptop kernel: [17192145.920000] ACPI: PCI interrupt for device 0000:00:1d.1 disabled
Dec 14 21:22:11 cbudden-laptop kernel: [17192145.920000] ACPI: PCI interrupt for device 0000:00:1d.0 disabled
Dec 14 21:22:11 cbudden-laptop kernel: [17192145.936000] ACPI: PCI interrupt for device 0000:00:1b.0 disabled
Dec 14 21:22:11 cbudden-laptop kernel: [17192145.936000] ....
Dec 14 21:22:11 cbudden-laptop kernel: [17192145.936000] swsusp: Need to copy 131394 pages
Dec 14 21:22:11 cbudden-laptop kernel: [17192145.936000] swsusp: Restoring Highmem
Dec 14 21:22:12 cbudden-laptop kernel: [17192145.940000] ACPI: PCI Interrupt 0000:00:01.0[A] -> GSI 16 (level, low) -> IRQ 169
Dec 14 21:22:12 cbudden-laptop kernel: [17192145.940000] ACPI: PCI Interrupt 0000:00:1b.0[A] -> GSI 22 (level, low) -> IRQ 74
Dec 14 21:22:12 cbudden-laptop kernel: [17192146.020000] ACPI: PCI Interrupt 0000:00:1c.0[A] -> GSI 17 (level, low) -> IRQ 177
Dec 14 21:22:12 cbudden-laptop kernel: [17192146.020000] ACPI: PCI Interrupt 0000:00:1c.1[B] -> GSI 16 (level, low) -> IRQ 169
Dec 14 21:22:12 cbudden-laptop kernel: [17192146.020000] ACPI: PCI Interrupt 0000:00:1c.2[C] -> GSI 18 (level, low) -> IRQ 185
Dec 14 21:22:12 cbudden-laptop kernel: [17192146.020000] ACPI: PCI Interrupt 0000:00:1c.3[D] -> GSI 19 (level, low) -> IRQ 193
Dec 14 21:22:12 cbudden-laptop kernel: [17192146.020000] ACPI: PCI Interrupt 0000:00:1d.0[A] -> GSI 23 (level, low) -> IRQ 66
Dec 14 21:22:12 cbudden-laptop kernel: [17192146.020000] ACPI: PCI Interrupt 0000:00:1d.1[B] -> GSI 19 (level, low) -> IRQ 193
Dec 14 21:22:12 cbudden-laptop kernel: [17192146.020000] ACPI: PCI Interrupt 0000:00:1d.2[C] -> GSI 18 (level, low) -> IRQ 185
Dec 14 21:22:12 cbudden-laptop kernel: [17192146.020000] ACPI: PCI Interrupt 0000:00:1d.3[D] -> GSI 16 (level, low) -> IRQ 169
Dec 14 21:22:12 cbudden-laptop kernel: [17192146.036000] PCI: Enabling device 0000:00:1d.7 (0000 -> 0002)
Dec 14 21:22:12 cbudden-laptop kernel: [17192146.036000] ACPI: PCI Interrupt 0000:00:1d.7[A] -> GSI 23 (level, low) -> IRQ 66
Dec 14 21:22:12 cbudden-laptop kernel: [17192146.036000] ACPI: PCI Interrupt 0000:00:1f.2[B] -> GSI 19 (level, low) -> IRQ 193
Dec 14 21:22:12 cbudden-laptop kernel: [17192146.036000] ACPI: PCI Interrupt 0000:01:00.0[A] -> GSI 16 (level, low) -> IRQ 169
Dec 14 21:22:12 cbudden-laptop kernel: [17192146.148000] eth%%d: Coming out of suspend...
Dec 14 21:22:12 cbudden-laptop kernel: [17192146.164000] PCI: Enabling device 0000:03:00.0 (0000 -> 0002)
Dec 14 21:22:12 cbudden-laptop kernel: [17192146.164000] ACPI: PCI Interrupt 0000:03:00.0[A] -> GSI 17 (level, low) -> IRQ 177
Dec 14 21:22:12 cbudden-laptop kernel: [17192146.164000] ACPI: PCI Interrupt 0000:0a:09.0[A] -> GSI 20 (level, low) -> IRQ 201
Dec 14 21:22:12 cbudden-laptop kernel: [17192146.164000] ACPI: PCI Interrupt 0000:0a:09.1[A] -> GSI 20 (level, low) -> IRQ 201
Dec 14 21:22:12 cbudden-laptop kernel: [17192146.180000] PCI: Enabling device 0000:0a:09.2 (0000 -> 0002)
Dec 14 21:22:12 cbudden-laptop kernel: [17192146.180000] ACPI: PCI Interrupt 0000:0a:09.2[A] -> GSI 20 (level, low) -> IRQ 201
Dec 14 21:22:12 cbudden-laptop kernel: [17192146.180000] pnp: Device 00:08 does not support activation.
Dec 14 21:22:12 cbudden-laptop kernel: [17192146.180000] pnp: Device 00:09 does not support activation.
Dec 14 21:22:12 cbudden-laptop kernel: [17192146.836000] ata1: dev 0 configured for UDMA/100
Dec 14 21:22:12 cbudden-laptop kernel: [17192147.400000] ata2: dev 0 configured for UDMA/33
Dec 14 21:22:12 cbudden-laptop kernel: [17192147.644000] gspca 5-8:1.0: no resume for driver gspca?
Dec 14 21:22:12 cbudden-laptop kernel: [17192147.644000] Restarting tasks... done
Dec 14 21:22:12 cbudden-laptop kernel: [17192147.648000] Thawing cpus ...
Dec 14 21:22:12 cbudden-laptop kernel: [17192147.660000] SMP alternatives: switching to SMP code
Dec 14 21:22:12 cbudden-laptop kernel: [17192147.660000] Booting processor 1/1 eip 3000
Dec 14 21:22:12 cbudden-laptop kernel: [17192147.668000] Initializing CPU#1
Dec 14 21:22:12 cbudden-laptop kernel: [17192147.748000] Calibrating delay using timer specific routine.. 3333.77 BogoMIPS (lpj=6667542)
Dec 14 21:22:12 cbudden-laptop kernel: [17192147.748000] monitor/mwait feature present.
Dec 14 21:22:12 cbudden-laptop kernel: [17192147.748000] CPU: L1 I cache: 32K, L1 D cache: 32K
Dec 14 21:22:12 cbudden-laptop kernel: [17192147.748000] CPU: L2 cache: 2048K
Dec 14 21:22:12 cbudden-laptop kernel: [17192147.748000] CPU: Hyper-Threading is disabled
Dec 14 21:22:12 cbudden-laptop kernel: [17192147.748000] CPU1: Intel Genuine Intel(R) CPU           T2300  @ 1.66GHz stepping 08
Dec 14 21:22:12 cbudden-laptop kernel: [17192147.752000] CPU1 is up
Dec 14 21:22:14 cbudden-laptop kernel: [17192156.896000] tg3.c:v3.59.1 (August 25, 2006)
Dec 14 21:22:14 cbudden-laptop kernel: [17192156.896000] ACPI: PCI Interrupt 0000:04:00.0[A] -> GSI 18 (level, low) -> IRQ 185
Dec 14 21:22:14 cbudden-laptop kernel: [17192156.932000] eth0: Tigon3 [partno(BCM95789) rev 4201 PHY(5750)] (PCI Express) 10/100/1000BaseT Ethernet 00:16:36:39:12:bf
Dec 14 21:22:14 cbudden-laptop kernel: [17192156.932000] eth0: RXcsums[1] LinkChgREG[0] MIirq[0] ASF[0] Split[0] WireSpeed[1] TSOcap[1] 
Dec 14 21:22:14 cbudden-laptop kernel: [17192156.932000] eth0: dma_rwctrl[76180000] dma_mask[64-bit]
Dec 14 21:22:16 cbudden-laptop kernel: [17192158.516000] ADDRCONF(NETDEV_UP): eth0: link is not ready
Dec 14 21:22:18 cbudden-laptop kernel: [17192160.708000] ACPI: Power Button (FF) [PWRF]
Dec 14 21:22:18 cbudden-laptop kernel: [17192160.708000] ACPI: Lid Switch [LID]
Dec 14 21:22:18 cbudden-laptop kernel: [17192160.708000] ACPI: Power Button (CM) [PWRB]
Dec 14 21:22:18 cbudden-laptop kernel: [17192160.708000] ACPI: Sleep Button (CM) [SLPB]
Dec 14 21:22:18 cbudden-laptop kernel: [17192160.752000] tg3: eth0: Link is up at 10 Mbps, half duplex.
Dec 14 21:22:18 cbudden-laptop kernel: [17192160.752000] tg3: eth0: Flow control is off for TX and off for RX.
Dec 14 21:22:18 cbudden-laptop kernel: [17192160.752000] ADDRCONF(NETDEV_CHANGE): eth0: link becomes ready
Dec 14 21:22:18 cbudden-laptop kernel: [17192160.784000] ACPI: Thermal Zone [THRM] (60 C)
Dec 14 21:22:18 cbudden-laptop kernel: [17192160.948000] ACPI: AC Adapter [ACAD] (on-line)
Dec 14 21:22:18 cbudden-laptop kernel: [17192160.980000] ACPI: Battery Slot [BAT1] (battery present)
Dec 14 21:22:49 cbudden-laptop dhcdbd: message_handler: message handler not found under /com/redhat/dhcp/eth0 for sub-path eth0.dbus.get.host_name
Dec 14 21:22:49 cbudden-laptop dhcdbd: message_handler: message handler not found under /com/redhat/dhcp/eth0 for sub-path eth0.dbus.get.nis_domain
Dec 14 21:22:49 cbudden-laptop dhcdbd: message_handler: message handler not found under /com/redhat/dhcp/eth0 for sub-path eth0.dbus.get.nis_servers

```

---

### Post by cbudden on 2006-12-15
Would anyone mind posting how much ram they have and the output of 
```

cat /sys/power/image_size

```

Thanks

Chris

---

### Post by Frank Golden on 2006-12-16
> **cbudden said:**
> Would anyone mind posting how much ram they have and the output of 
```

cat /sys/power/image_size

```

Thanks

Chris
2 GB

frankgolden@frankgolden-laptop:~$ cat /sys/power/image_size
524288000
frankgolden@frankgolden-laptop:~$

Why?

---

### Post by cbudden on 2006-12-16
> **Frank Golden said:**
> 2 GB

frankgolden@frankgolden-laptop:~$ cat /sys/power/image_size
524288000
frankgolden@frankgolden-laptop:~$

Why?

Thanks.  My hibernate is playing up and I suspect that has something to do with it.  I have 1gb of ram and the same figure for that.  Thanks

---

### Post by gmc on 2006-12-16
Hi Folks,

Just in case you need a project for the weekend. AMD/ATI released 8.32.5 drivers, which can be found [here]("http://ati.amd.com/support/drivers/linux/linux-radeon.html").

...and before you ask, no they still don't support AIGLX :-(

G.

---

### Post by cbudden on 2006-12-16
More news about drivers.


[http://mxhaard.free.fr/spca50x/Download/gspcav1-20061216.tar.gz](http://mxhaard.free.fr/spca50x/Download/gspcav1-20061216.tar.gz)

Download that and run ./gspca_build

Working webcam !

I tried modprobe gspca but that did not work, but after a reboot it did.

Enjoy!

---

### Post by Frank Golden on 2006-12-16
> **cbudden said:**
> Thanks.  My hibernate is playing up and I suspect that has something to do with it.  I have 1gb of ram and the same figure for that.  ThanksWhat is the number showing?

---

### Post by Frank Golden on 2006-12-17
> **gmc said:**
> Hi Folks,

Just in case you need a project for the weekend. AMD/ATI released 8.32.5 drivers, which can be found [here]("http://ati.amd.com/support/drivers/linux/linux-radeon.html").

...and before you ask, no they still don't support AIGLX :-(

G.
Installed on both my dapper and edgy partitions. No problems.
The [http://wiki.cchtml.com/index.php/Main_Page](http://wiki.cchtml.com/index.php/Main_Page)

wiki is greatly improved.

Will try to install on My PCLinuxOS partition.

---

### Post by cbudden on 2006-12-17
> **Frank Golden said:**
> What is the number showing?
```

cbudden@cbudden-laptop:~$ cat /sys/power/image_size 
524288000


```

I have 1 gb of ram and 2 of swap.

The readout from free is :
```

cbudden@cbudden-laptop:~$ free
             total       used       free     shared    buffers     cached
Mem:       1034160     852316     181844          0      27652     376064
-/+ buffers/cache:     448600     585560
Swap:      2096472          0    2096472

```


I have uswsusp installed, and it did work for a couple of hibernates, but when it doesn't it gets to the first 3 bars and then stalls and returns me to my desktop.

---

### Post by bwanab on 2006-12-17
I've got a question. Does hardware video 3D acceleration work with the 5672 using the ati fglrx drivers? I've got fglrx installed so I get full 1280x800 for which I'm happy, but I was wondering about hardware acceleration. I've followed the list over the last few months, but at times I've missed a couple of weeks at a time, so I could have missed something.

---

### Post by unz on 2006-12-17
> **cbudden said:**
> More news about drivers.


[http://mxhaard.free.fr/spca50x/Download/gspcav1-20061216.tar.gz](http://mxhaard.free.fr/spca50x/Download/gspcav1-20061216.tar.gz)

Download that and run ./gspca_build

Working webcam !

I tried modprobe gspca but that did not work, but after a reboot it did.

Enjoy!

I got only a streaming for a few seconds ... than it hangs, how about you?

screenshot:
[http://www.romastyle.info/media/webcam.png](http://www.romastyle.info/media/webcam.png)

---

### Post by cbudden on 2006-12-17
> **unz said:**
> I got only a streaming for a few seconds ... than it hangs, how about you?

screenshot:
[http://www.romastyle.info/media/webcam.png](http://www.romastyle.info/media/webcam.png)

Doesn't do that for me.  Sorry.  Have you tried Camorama ?  I need to add the colour correction filter otherwise you will look funny.

---

### Post by giostau on 2006-12-17
> **cbudden said:**
> More news about drivers.


[http://mxhaard.free.fr/spca50x/Download/gspcav1-20061216.tar.gz](http://mxhaard.free.fr/spca50x/Download/gspcav1-20061216.tar.gz)

Download that and run ./gspca_build

Working webcam !

I tried modprobe gspca but that did not work, but after a reboot it did.

Enjoy!

Thanks!
It's working!
....BUT the image is VERY VERY dark! (almost black!) :( 
any ideas???

(i'm using Camorama....)

Thanks again!

---

### Post by Frank Golden on 2006-12-17
> **bwanab said:**
> I've got a question. Does hardware video 3D acceleration work with the 5672 using the ati fglrx drivers? I've got fglrx installed so I get full 1280x800 for which I'm happy, but I was wondering about hardware acceleration. I've followed the list over the last few months, but at times I've missed a couple of weeks at a time, so I could have missed something.

Try the command [sudo fglrxinfo]. This will show your video driver. It should show the ATi driver not Mesa.

Also try [sudo glxinfo] if you have hardware acceleration there will be an entry at top
that says direct rendering=yes.

There are two commands that run some test applets. [sudo fgl_glxgears] which shows a spinning cube with frame per second data in the terminal window. The other is [glxgears -printfps] this shows a 2-D image with frame per second data in it's terminal. These aren't really reliable benchmarks but if you show direct rendering enabled these applets should run smoothly. You will get much higher frame rates if the gears windows are minimized.
The above commands minus the brackets of course.

See this for more info

[http://wiki.cchtml.com/index.php/Glxgears_is_not_a_Benchmark](http://wiki.cchtml.com/index.php/Glxgears_is_not_a_Benchmark)

---

### Post by Kwunman on 2006-12-17
Hi,

I have a strange suspicion that I have missed something, but I was just wandering how you install these new webcam drivers.

Thanks

Kwun-man

---

### Post by cbudden on 2006-12-17
> **cbudden said:**
> More news about drivers.


[http://mxhaard.free.fr/spca50x/Download/gspcav1-20061216.tar.gz](http://mxhaard.free.fr/spca50x/Download/gspcav1-20061216.tar.gz)

Download that and run ./gspca_build

Working webcam !

I tried modprobe gspca but that did not work, but after a reboot it did.

Enjoy!

This should get your drivers installed.

---

### Post by gmc on 2006-12-18
> **cbudden said:**
> Doesn't do that for me.  Sorry.  Have you tried Camorama ?  I need to add the colour correction filter otherwise you will look funny.

What did you do to "add the colour correction"? I've played with all the controls on Camorama but the image doesn't change at all and it's very dark.

Gord

Doh! I found the filters option but it doesn't seem to help in brightening the image any.

---

### Post by cbudden on 2006-12-18
> **gmc said:**
> What did you do to "add the colour correction"? I've played with all the controls on Camorama but the image doesn't change at all and it's very dark.

Gord

In the effects section to the right, right click -> add effect, colour correction.  Not sure about the brightness though.

---

### Post by tonyr1988 on 2006-12-18
Probably a stupid question, but I'm stuck installing the camera drivers. I get:

>  FATAL you need to install the Kernel Source for your running kernel

uname -r is showing 2.6.15. The problem is that I don't see a kernel-source-2.6.15 package. It only goes to 2.6.13. Should I just start running a lower kernel?

---

### Post by gmc on 2006-12-18
> **tonyr1988 said:**
> Probably a stupid question, but I'm stuck installing the camera drivers. I get:



uname -r is showing 2.6.15. The problem is that I don't see a kernel-source-2.6.15 package. It only goes to 2.6.13. Should I just start running a lower kernel?

Sounds like you might be missing some of the utilities needed to compile addon modules (drivers) for your system. Try issuing the following commands:

```

sudo apt-get update
sudo apt-get install gcc g++ libc6-dev linux-headers-`uname -r` build-essential debhelper
sudo apt-get install module-assistant build-essential fakeroot dh-make debconf libstdc++5
sudo apt-get install gcc-3.3-base

```

This should allow you to build the webcam driver (and the latest fglrx driver if you feel adventurous ;-) )

Gord

---

### Post by bwanab on 2006-12-18
> **Frank Golden said:**
> Try the command [sudo fglrxinfo]. This will show your video driver. It should show the ATi driver not Mesa.



Thanks for the response. My fglrxinfo shows that I have the mesa driver. AFAICT, I installed the latest 8.32.5 driver from ATI and it seemed to install correctly. I don't see any other video driver, but I've got mesa indirect.

Any clue on how to correct this. Would it be settings in my xorg.conf?

---

### Post by Frank Golden on 2006-12-18
> **bwanab said:**
> Thanks for the response. My fglrxinfo shows that I have the mesa driver. AFAICT, I installed the latest 8.32.5 driver from ATI and it seemed to install correctly. I don't see any other video driver, but I've got mesa indirect.

Any clue on how to correct this. Would it be settings in my xorg.conf?
Hi Bwanab,
  A couple of questions what flavor ubuntu do you use. (edgy or dapper, Kbuntu or ubuntu etc)? 
How did you install the 8.32.5 drivers?

Lastly, a stupid question did you reboot after install?

Choose your distro from the list on the following tutorial. Use method 2 for any version of Ubuntu.
[http://wiki.cchtml.com/index.php/Ubuntu](http://wiki.cchtml.com/index.php/Ubuntu)

Note that the edgy code  has an additional step to correct a potential error, as well as edgy specific instructions.

I have used this tutorial on both Ubuntu 6.06 LTS and Edgy Ubuntu 6.10 installs several times
after kernel upgrades without problems. (I have a spare HDD with Edgy on it that I keep
updated).

---

### Post by tonyr1988 on 2006-12-18
> **gmc said:**
> Sounds like you might be missing some of the utilities needed to compile addon modules (drivers) for your system. Try issuing the following commands:

```

sudo apt-get update
sudo apt-get install gcc g++ libc6-dev linux-headers-`uname -r` build-essential debhelper
sudo apt-get install module-assistant build-essential fakeroot dh-make debconf libstdc++5
sudo apt-get install gcc-3.3-base

```

This should allow you to build the webcam driver (and the latest fglrx driver if you feel adventurous ;-) )

Gord
That did it - I didn't even have to restart to get modprobe to work. It's awesome that it's finally working great!

But...I'll second the darkness problem, and I see blue dots around the border of the picture. It's still awesome, and mad props to the developer(s) of the driver. w00t

It won't be long before this laptop runs perfectly in Linux.

---

### Post by bwanab on 2006-12-19
> **Frank Golden said:**
> Hi Bwanab,
  A couple of questions what flavor ubuntu do you use. (edgy or dapper, Kbuntu or ubuntu etc)? 

ubuntu dapper

> **Frank Golden said:**
> How did you install the 8.32.5 drivers?

I just ran the .run file.

> **Frank Golden said:**
> Lastly, a stupid question did you reboot after install?

Yes, but I probably didn't do install correctly.

> **Frank Golden said:**
> Choose your distro from the list on the following tutorial. Use method 2 for any version of Ubuntu.
[http://wiki.cchtml.com/index.php/Ubuntu](http://wiki.cchtml.com/index.php/Ubuntu)

Note that the edgy code  has an additional step to correct a potential error, as well as edgy specific instructions.

I have used this tutorial on both Ubuntu 6.06 LTS and Edgy Ubuntu 6.10 installs several times
after kernel upgrades without problems. (I have a spare HDD with Edgy on it that I keep
updated).

I followed the instructions (method 1 to start), but get the following. I'll try doing the method 2 install (building and installing the 8.32.5 driver correctly :) ) tonight. Thanks for your help.


dmesg | grep fglrx
[17179601.468000] fglrx: module license 'Proprietary. (C) 2002 - ATI Technologies, Starnberg, GERMANY' taints kernel.
[17179601.468000] [fglrx] Maximum main memory to use for locked dma buffers: 1896 MBytes.
[17179601.468000] [fglrx] module loaded - fglrx 8.25.18 [May 18 2006] on minor 0
[17179603.416000] [fglrx:firegl_unlock] *ERROR* Process 4802 using kernel context 0

---

### Post by miguelneves on 2006-12-19
> **cbudden said:**
> More news about drivers.


[http://mxhaard.free.fr/spca50x/Download/gspcav1-20061216.tar.gz](http://mxhaard.free.fr/spca50x/Download/gspcav1-20061216.tar.gz)

Download that and run ./gspca_build

Working webcam !

I tried modprobe gspca but that did not work, but after a reboot it did.

Enjoy!

This is really great!

I try them on my aspire 5634 and work without any problem, and I didn't need to reboot. 

The picture quality isn't the best you could get, but at least you get something. (I use Camorama)

Keep the good work!

---

### Post by tonyr1988 on 2006-12-20
I'm stuck on getting bluetooth to work. I installed gnome-bluetooth (not sure if that's the right package, if any, that I need to install) and have it running in the tray.

I set my BT device to discover mode, and nothing at all happens. I have no clue what to do next (I've never owned a BT device before). The blue light is on, next to the wireless one. Anyone else got bluetooth things working?

---

### Post by cbudden on 2006-12-20
[SIZE="2"]> **cbudden said:**
> ```

cbudden@cbudden-laptop:~$ cat /sys/power/image_size 
524288000


```

I have 1 gb of ram and 2 of swap.

The readout from free is :
```

cbudden@cbudden-laptop:~$ free
             total       used       free     shared    buffers     cached
Mem:       1034160     852316     181844          0      27652     376064
-/+ buffers/cache:     448600     585560
Swap:      2096472          0    2096472

```


I have uswsusp installed, and it did work for a couple of hibernates, but when it doesn't it gets to the first 3 bars and then stalls and returns me to my desktop.

[/SIZE]

Unfortunately, now hibernate never works.  Any ideas?

---

### Post by Frank Golden on 2006-12-20
[QUOTE=bwanab;1905575]ubuntu dapper



I just ran the .run file.[COLOR="Red"]You are correct in assuming that just running the .run file wont work.[/COLOR]



I followed the instructions (method 1 to start), but get the following. I'll try doing the method 2 install (building and installing the 8.32.5 driver correctly :) ) tonight. Thanks for your help. [COLOR="red"]Follow the instructions to the letter. Make sure your universe and restricted repos are enabled as noted in wiki. This has always worked for me. You will need to do again after every kernel upgrade. If you want the latest driver (8.32.5) then download the latest to your desktop and substitute [bash ati-driver-installer-8.32.5-x86.x86_64.run --buildpkg Ubuntu/dapper] for the command [bash ati-driver-installer-8.29.6.run --buildpkg Ubuntu/dapper] you will also need to modify the .deb install codes
[sudo dpkg -i xorg-driver-fglrx_8.29.6-1_i386.deb 
sudo dpkg -i fglrx-kernel-source_8.29.6-1_i386.deb
sudo dpkg -i fglrx-control_8.29.6-1_i386.deb
by changing the 8.29.6-1 on each command to 8.32.5-1]. Ignore the above brackets. Of course if you want just download the 8.29.6 driver that this tutorial was originally written for and install it with0ut modifying code. I have installed the latest driver (8.32.5) using the modified
method outlined above with no problems on my Acer Aspire as5672WLMi.
 [/COLOR]

---

### Post by cbudden on 2006-12-21
> **cbudden said:**
> [SIZE="2"]

[/SIZE]

Unfortunately, now hibernate never works.  Any ideas?

I removed uswsusp and hibernate works again :S.

Jdong, did you say that you use uswsusp with no problems?

---

### Post by bwanab on 2006-12-22
> **Frank Golden said:**
> [QUOTE=bwanab;1905575]ubuntu dapper



I just ran the .run file.[COLOR="Red"]You are correct in assuming that just running the .run file wont work.[/COLOR]



I followed the instructions (method 1 to start), but get the following. I'll try doing the method 2 install (building and installing the 8.32.5 driver correctly :) ) tonight. Thanks for your help. [COLOR="red"]Follow the instructions to the letter. Make sure your universe and restricted repos are enabled as noted in wiki. This has always worked for me. You will need to do again after every kernel upgrade. If you want the latest driver (8.32.5) then download the latest to your desktop and substitute [bash ati-driver-installer-8.32.5-x86.x86_64.run --buildpkg Ubuntu/dapper] for the command [bash ati-driver-installer-8.29.6.run --buildpkg Ubuntu/dapper] you will also need to modify the .deb install codes
[sudo dpkg -i xorg-driver-fglrx_8.29.6-1_i386.deb 
sudo dpkg -i fglrx-kernel-source_8.29.6-1_i386.deb
sudo dpkg -i fglrx-control_8.29.6-1_i386.deb
by changing the 8.29.6-1 on each command to 8.32.5-1]. Ignore the above brackets. Of course if you want just download the 8.29.6 driver that this tutorial was originally written for and install it with0ut modifying code. I have installed the latest driver (8.32.5) using the modified
method outlined above with no problems on my Acer Aspire as5672WLMi.
 [/COLOR]


Thanks Frank, I did this and it worked without a hitch.

---

### Post by Frank Golden on 2006-12-22
Hi Bwanab, Just remember to do this everytime you upgrade your kernel. I'm glad it worked for you.

---

### Post by nik1111 on 2006-12-22
Guys I get a funny problem with this laptop after the latest (kernel?) updates a week ago. When I use the dvdrom or when i insert the headset cable into the respective jack, all sound is lost. I have to reboot to get the sound back.

I had this problem with dapper as well but when I installed edgy the problem just vanished.. now after the updates it came back. Can anyone help?

---

### Post by gmc on 2006-12-24
Hi Folks,

I'm not sure what was updated in Edgy but I'm now seeing the gnome power management reporting that my battery is at 0% and going to take 27+ hours to recharge even though I'm permanently running on the mains (and the system's been plugged in for over 27 hours).

Removing and reseating the battery and rebooting the system hasn't solved the problem. Anyone notice a problem with gnome power management in the last few days?

Gord

---

### Post by nik1111 on 2006-12-24
The way I see it updates should be more careful and less frequent, apart from security updates. There is no point in solving problems for ten users if you create problems for two users at the same time.

---

### Post by jdong on 2006-12-24
If you want security-only updates, turn off the edgy-updates and edgy-backports channels. This is what I do on my servers and highly-critical workstation desktops.

As far as the symptoms you describe, I have not experienced them on an updated Edgy.

---

### Post by gmc on 2006-12-24
Hi Folk (again),

I've solved my battery/power management problem. I had to remove the power adapter, so the machine switched to the battery and let it drain (1.5 hours) then plug the mains back in and let the battery charge up again. Everything seems to be back to working order again.

Gord

---

### Post by Frank Golden on 2006-12-24
> **gmc said:**
> Hi Folk (again),

I've solved my battery/power management problem. I had to remove the power adapter, so the machine switched to the battery and let it drain (1.5 hours) then plug the mains back in and let the battery charge up again. Everything seems to be back to working order again.

Gord
I had a similar issue with my wireless mouse. I would get a popup informing me that my mouse battery was at 28% and would shut down unless I recharged it. My mouse was at full power. All of a sudden the popups stopped all by themselves.
This happened after the latest update cycle also.

---

### Post by jdong on 2006-12-24
Is it finally time for this thread's contents to be put into a coherent Wiki page and finally let this thread die peacefully? We can't honestly expect the 5672 purchaser to look through all these replies, right? ;-)

---

### Post by cbudden on 2006-12-25
> **jdong said:**
> Is it finally time for this thread's contents to be put into a coherent Wiki page and finally let this thread die peacefully? We can't honestly expect the 5672 purchaser to look through all these replies, right? ;-)

Sounds like a good idea, but Christmas day isn't the day to do it !!!!8)

---

### Post by Frank Golden on 2006-12-25
> **cbudden said:**
> Sounds like a good idea, but Christmas day isn't the day to do it !!!!8)
I agree. This has been a most helpful thread for me as well as many other owners
of this fine laptop. A wiki devoted to the 5672 based on this thread is a great idea.

---

### Post by gmc on 2006-12-25
Hi Folks,

I agree! Condensing this thread into a wiki is an excellent idea.

When I originally started this thread, I never thought it would end up with 700+ posts and 58200+ reads. As of Jan 19th, it'll be a year to the day that I picked up my machine and I can honestly say I'm still very happy with it.

Anyhow, Merry Christmas and a Happy New Year to one and all!

Gord

---

### Post by Frank Golden on 2006-12-25
> **gmc said:**
> Hi Folks,

I agree! Condensing this thread into a wiki is an excellent idea.

When I originally started this thread, I never thought it would end up with 700+ posts and 58200+ reads. As of Jan 19th, it'll be a year to the day that I picked up my machine and I can honestly say I'm still very happy with it.

Anyhow, Merry Christmas and a Happy New Year to one and all!

Gord
That's right Gord you started this thread didn't you. LOL. I am very happy with my 5672 also  and have grown
to love how it and Ubuntu have seemed to develop together. I will have had my machine for a year in April.
It has faster memory than when I got it and a 2GHz Core2Duo (merom) rather than the 1.66GHz Core Duo (yonah). Very (for this user) user friendly upgrades, BTW.

Merry Christmas and a Happy New Year to you and to everyone.

---

### Post by tonyr1988 on 2006-12-26
> **jdong said:**
> Is it finally time for this thread's contents to be put into a coherent Wiki page and finally let this thread die peacefully? We can't honestly expect the 5672 purchaser to look through all these replies, right? ;-)

A few pages ago I posted a link to a wiki page I created for the Aspire 5672WLMi, but:

1) I haven't done much with it (yet), and
2) It's on one of those free wiki-farms, so it's not the most customizable thing in the world.

If anyone else has a server they'd be willing to donate, I'd be willing to give my time to add as much stuff as I can. I plan on wiping my XP partition soon and putting a fresh Edgy install on it, and I'll write down every single tiny thing that I need to do to get as much of it working as possible. I've forgotten all the things I've done to my Dapper partition. :D

---

### Post by tonyr1988 on 2007-01-02
Has anyone gotten the S-Video out to work? I don't even know where to start on it...

---

### Post by cbudden on 2007-01-02
> **tonyr1988 said:**
> Has anyone gotten the S-Video out to work? I don't even know where to start on it...


If you have the fglrx driver installed, plug in the s-video cable and restart X.

Thats it :)

---

### Post by jdong on 2007-01-02
Yes, at one point I did confirm that TV-out works. IT was activated through a series of aticonfig commands I pulled off another wiki dealing with ATI-chipset laptops. I don't remember where the documents were or what the exact commands were though, but I don't think it'd be hard to find.

---

### Post by gmc on 2007-01-04
Hi Folks,

I've been fooling around with my keyboard settings but have run into a couple of problems. Pressing the 'euro' key starts my default email client, the 'dollar' key (not shift 4) doesn't do anything, and the win-key also does nothing. Specifically I was trying to get the win-key to act as the "super key" for compiz/beryl but I'm not having any luck.

Has anyone been able to map these keys?

Gord

---

### Post by jdong on 2007-01-04
wha! the Euro and dollar keys don't do anything on mine; they're unmapped and generate keycode errors in dmesg.

---

### Post by gmc on 2007-01-05
> **jdong said:**
> wha! the Euro and dollar keys don't do anything on mine; they're unmapped and generate keycode errors in dmesg.

I added the following lines to /etc/rc.local

```

setkeycodes e034 156 #Dollar
setkeycodes e033 155 #Euro

```

In theory, they are suppost to map the 'euro' and 'dollar' keys to the appropriate symbols. Unfortunately that's not what's happening.

Gord

---

### Post by janmartin on 2007-01-05
Hi all,

thank you for this thread and you hard work on Acer laptops issues.

Because of this I felt save to buy an Acer Aspire 5633WLMi Laptop.

Due to your work most things work right out of the box.

See my thread for how I dealt with the rest.
[http://ubuntuforums.org/showthread.php?t=332019](http://ubuntuforums.org/showthread.php?t=332019)

Thanks again, great work,

Jan
:)

---

### Post by unz on 2007-01-06
> **gmc said:**
> Hi Folks,

I've been fooling around with my keyboard settings but have run into a couple of problems. Pressing the 'euro' key starts my default email client, the 'dollar' key (not shift 4) doesn't do anything, and the win-key also does nothing. Specifically I was trying to get the win-key to act as the "super key" for compiz/beryl but I'm not having any luck.

Has anyone been able to map these keys?

Gord.
set your keyboard as generic pc-104

---

### Post by gmc on 2007-01-06
> **unz said:**
> set your keyboard as generic pc-104

Tried it but no luck. Windows-Key is not acting as the "Superkey" for Beryl/Compiz and the "euro" and "dollar" keys remain unresponsive, unless reprogrammed with the 'setkeycode' commands. Which I still haven't figured out how to get the appropriate symbols set.

Gord

---

### Post by Frank Golden on 2007-01-07
> **janmartin said:**
> Hi all,

thank you for this thread and you hard work on Acer laptops issues.

Because of this I felt save to buy an Acer Aspire 5633WLMi Laptop.

Due to your work most things work right out of the box.

See my thread for how I dealt with the rest.
[http://ubuntuforums.org/showthread.php?t=332019](http://ubuntuforums.org/showthread.php?t=332019)

Thanks again, great work,

Jan
:)
Hi Janmartin,
  I noticed in your linked thread you cite using F2 to access the BIOS for boot order.
I don't know about the 5633 family of laptops but the BIOS used in the 5672 has a neat feature, an option to activate the F12 key to provide a boot menu during POST.
When you activate this feature and press F12 during POST, a menu will appear
showing your HDD, Optical drive and any bootable drives you have connected at that time.
Simply arrow down to select the device you want to boot and press enter.
This keeps the boot order specified in the BIOS, which most people set as HDD first, Optical second etc. but allows you to choose your boot device on the fly so to speak.
No need to completely enter the BIOS.
Cool.

---

### Post by nik1111 on 2007-01-07
Guys, I lost all sound somewhere in the way :)
I installed the latest alsa drivers and i tried to modprobe snd_hda_intel but i am getting 

FATAL: Error inserting snd_hda_intel (/lib/modules/2.6.17-10-generic/extra/snd-hda-intel.ko): Unknown symbol in module, or unknown parameter (see dmesg)

Could anyone help? the rest sound modules are loaded correctly.Aplay -l says i dont have any soundcards installed and the mixer is not working.

---

### Post by tonyr1988 on 2007-01-08
This isn't completely relevant to Linux on the Acer Aspire, but has anyone seen this:

[http://yro.slashdot.org/article.pl?sid=07/01/08/0515200](http://yro.slashdot.org/article.pl?sid=07/01/08/0515200)

Of course, it's a Windows-only thing, so we're safe, but those of you (including me) that dual-boot may want to boot into Internet-connected WinXP a little less. :)

---

### Post by gmc on 2007-01-08
> **tonyr1988 said:**
> This isn't completely relevant to Linux on the Acer Aspire, but has anyone seen this:

[http://yro.slashdot.org/article.pl?sid=07/01/08/0515200](http://yro.slashdot.org/article.pl?sid=07/01/08/0515200)

Of course, it's a Windows-only thing, so we're safe, but those of you (including me) that dual-boot may want to boot into Internet-connected WinXP a little less. :)

 I saw it. If you read the comments (on Slashdot), someone posted a couple of simple instructions on how to remove the entry in the registry.  Gord

---

### Post by jdong on 2007-01-08
I'm using a fresh install of XP Pro, so fortunately I'm not affected :)

---

### Post by Frank Golden on 2007-01-08
> **jdong said:**
> I'm using a fresh install of XP Pro, so fortunately I'm not affected :)Sometime's these companies are grossly misguided. Witness the Sony
Rootkit debacle of last year. In that case it wasn't easy to fix. This is the main reason I
won't knowingly buy a Sony product and eventually settled on Acer. And yes I now know
that our computer uses a Sony battery but I did not know that when I bought my 5672.

Besides, like jdong, I am using a retail install of XP pro without the Acer software.
Except for the webcam software and drivers from Acers european ftp site.

I does seem as if more companies are getting more intrusive though.

---

### Post by jdong on 2007-01-09
The situation is no different than with, say, Dell, as we found out in our school when kids started hijacking teacher workstations... suddenly in the middle of a class when a TV was hooked up  to the computer, the mouse started moving by itself, opening up a gradebook and bumping up grades ;-)

---

### Post by nik1111 on 2007-01-10
I dont know if it has been mentioned before, or if anyone will ever use it, but i can confirm that the internal modem works with the driver from [www.linuxant.com](www.linuxant.com) but the speed is only 14.4 kbps. I just checked the wiki for this laptop and saw it it says that it's supposed to work, so I just thought I should confirm it.

---

### Post by jdong on 2007-01-10
I also confirm the linuxant blob drivers work fine for 14.4K, which should mean if you dish out the money for the full driver, it'll work for V.92 also. In my testing Linuxant's driver is very solid and professionally done, and using the modem actively does not add any noticeable lag or latency.

If I were a heavier dial-up user, I would definitely pay the money for the full driver to support Linuxant's work on making available Linux support to one of the most common modem chipsets (Conexant) today.

---

### Post by tonyr1988 on 2007-01-23
I made the switch to Edgy today (fresh install), and I'm having problems with the wireless.

It doesn't show up in System -> Admin -> Networking at all. I'm assuming it's because I don't have it turned on (the orange light isn't glowing). But...when I flip the switch, it doesn't do anything. I've held it, restarted, etc...still no luck.

Is there anything I can do to manually get that turned on? Has anyone else experienced this problem?

P.S. Is it something I should have activated during installation? I didn't even think about it then - if needed, I could easily re-install.

---

### Post by cbudden on 2007-01-23
I'm not sure if it does need to be activated during install, maybe others will know but you can try this to get it working:
```

sudo modprobe ipw3945 
```

---

### Post by tonyr1988 on 2007-01-23
Unfortunately, the modprobe doesn't work.

I know for a fact that it's not a hardware issue, because when I boot into my old Dapper partition, it works perfectly. When I restart into Edgy, the wireless orange light never comes on, and I cannot turn it on.

Under Device Manager, it recognizes it:

PRO/Wireless 3945ABG Network
info.linux.driver = ipw3945
etc etc etc

modinfo ipw3945 gives me (what looks like) the correct info. Is /lib/modules/2.6.17-10-generic/kernel/drivers/net/wireless/ipw3945/ipw3945.ko the correct path?

I guess I'll do a reinstall with the wireless turned on. Any other ideas?

P.S. I used the Edgy Alternate CD this time, and the Dapper LiveCD last time. That wouldn't make a difference, would it? When I installed Edgy via LiveCD on my desktop...when I got to the networking stage, it asked me about eth0, ath0 (my wireless), etc...even though I didn't have the right drivers and my wireless wasn't working. It didn't ask me anything about that on my Acer. Does that mean it didn't think it was activated or something?

---

### Post by jdong on 2007-01-23
Look at iwconfig output. See if the interface is being detected. Also check output of **ps aux | grep ipw3945d** perhaps the regulatory daemon isn't running.

---

### Post by tonyr1988 on 2007-01-23
I got impatient. :P

I tried installing from the 6.10 Alternate CD again - exact same problem. Downloaded / burned / used the 6.10 LiveCD, and it works perfectly. No configuration needed (except activating and choosing my network, of course).

I wonder if it's something wrong with the Alternate CD's hardware detection? Has anyone used the Alternate CD with success? I guess there's no significant reason to use it - the laptop's fully capable of handling it - it just happened to be the only Edgy CD I had available.

I'm actually going through and recording every step I take to get everything running smoothly to (hopefully) add to a wiki. I figured a fresh install was the best way to go.

Thanks for the tip, though, jdong. If nothing else, I learned about the aux paramater on ps. :)

---

### Post by jdong on 2007-01-23
alternate CD should work just as well... sounds like a weird fluke. I'd be curious to know what exactly happened. Oh well, one of those mysteries of the deep dark unknown :D

---

### Post by scifan2 on 2007-01-23
I'm unsure if the guy above figured out his hibernate problem... but I found that changing the "UUID/blkid" references to the swap partition worked for me.

On my 5672, /dev/sda4 is my swap partition.

So I edited /etc/initramfs-tools/conf.d/resume and modified the RESUME=UUID=(big number) to read "RESUME=/dev/sda4"
Then I executed: sudo update-initramfs -c -k `uname -r`

after having done this, I altered my /etc/fstab file to replace the UUID swap line to reference /dev/sda (e.g. "/dev/sda4 none swap 0 0" )

I found this link [http://article.gmane.org/gmane.user-groups.linux.delhi/13814](http://article.gmane.org/gmane.user-groups.linux.delhi/13814) to be useful in helping with this.

Best of luck

I haven't tried suspending, but having hibernating working correctly is great... actually this works better than it did under dapper now.  And just in case anyone was curious, I did verify that my UUID numbers were correct for my swap partition... apparently there's a bug in the change over to UUID...

Oh, and I had a bizzare adventure with my root partition after installing edgy... my root volume UUID was incorrect and while the system would run, and the root FS was writable, it wouldn't show up in the "df" command output, and I would get a bizzare error on boot.

Cheers.

---

### Post by Frank Golden on 2007-01-24
> **jdong said:**
> alternate CD should work just as well... sounds like a weird fluke. I'd be curious to know what exactly happened. Oh well, one of those mysteries of the deep dark unknown :D

Hi jdong,
I noticed the exact same problem the alternate CD install wouldn't detect my Wi-Fi
card and I could not turn it on with the hardware switch. The Live CD install would.
The live cd install seemed to have p-mount broken however. USB thumb drives wouldn't
mount and when located in /media returned an error message when clicked on.
Very strange behavior.

BTW, this install is on a USB external HDD.

---

### Post by tonyr1988 on 2007-01-26
I just fixed my battery indication problem using jdong's HAL advice:

[http://www.ubuntuforums.org/showthread.php?p=1714965#post1714965](http://www.ubuntuforums.org/showthread.php?p=1714965#post1714965)

After a reboot, my update manager pops up telling me that the hal package has a newer version available. It's:

> From version 0.5.7.1-0ubuntu17 to 0.5.7.1-0ubuntu17 (Size: 347 KB)

I've triple-checked, and yes - they're the same version.

As far as changes:

> The list of changes is not available

Should I update or not? Honestly, I'm not positive what each step of jdong's post did - it seemed like I was building my own hal package, though - will this revert to the previous (broken) one?

If it will, is there a way to permanently stop it from asking me to update this package, or will I have to uncheck it every time it's time to update things?

Just wanted to be cautious.

---

### Post by jdong on 2007-01-26
Don't update. You forgot to go into debian/changelog and bump up the version a bit (like 17**+0**). By default repository packages are always prioritized over locally installed debs. That's why it wants to do that.

---

### Post by tonyr1988 on 2007-01-26
I figured that I had forgotten something. Is there an easy way to go back and edit that (or Force Version or something), or should I start over?

In case I need to start over, what step did I mess up? Like I said, I didn't completely understand each step, so I could've easily missed something.

If I force version, which one should I choose? There is:

0.5.7.1-0ubuntu17 (edgy)
0.5.7.1-0ubuntu17 (now)

I assumed it was now, so I tried a Force Version on it, but when I click Apply it's still wanting me to upgrade.

---

### Post by jdong on 2007-01-26
Before building (executing dpkg-buildpackage), edit the debian/changelog file. The first line specifies the version number. Bump that with with an additional **.0** or **+0** appended to the version number (no more than that, please.... or it could lead to upgrade trouble)


By the way, this has been fixed in Feisty -- HAL in Feisty will report correct battery percentages. You can also backport HAL from feisty (prevu feisty), but HAL's behavior has changed slightly (devices are mounted at /media/label rather than the generic /media/usbdisk) so maybe that's not such a hot idea :D

---

### Post by tonyr1988 on 2007-01-26
I'll try that tonight once I get home. What packages do I need to remove before trying again? I'm not sure if I've still got the *.deb files in my /tmp directory - I can go through apt for the same result, right?

---

### Post by jdong on 2007-01-26
no need to remove any; they're going to be overridden by properly built packages anyway :)

---

### Post by tonyr1988 on 2007-01-26
Thanks - it worked perfectly.

I also have (hopefully) good news: since I recently did a fresh install of Edgy, I decided to record every step I needed to take to get things working on the 5672. Now that most of the basic problems are solved, I added everything to the wiki.

[http://acer5672ubuntu.elwiki.com/Main_Page](http://acer5672ubuntu.elwiki.com/Main_Page)

I tried to keep it as organized as possible. The discussion tab on the main page lists some things that are lacking in the guide right now.

---

### Post by haani on 2007-01-28
hi is there anyway to enable direct rendering using beryl (XGL)???..
apps like google earth doesnt work then.....

---

### Post by jdong on 2007-01-28
No, that's not technically possible for Xgl to pass control of the video card to a particular program. OpenGL/XVideo are still hardware-accelerated, but not direct-rendered.

---

### Post by haani on 2007-01-28
so how am i suppose to run apps that require openGL to run e.g google earth in XGL??

---

### Post by jdong on 2007-01-28
OpenGL should work fine within Xgl -- at least it does for me?

---

### Post by nik1111 on 2007-01-28
> **jdong said:**
> OpenGL should work fine within Xgl -- at least it does for me?

I believe Xgl does not support OpenGl on top of it.But I may be mistaken. 

I have the same problem with direct rendering so what I have done is that I have created 2 separate profiles one for gnome+3D acceleration for games mainly and one for Gnome+Xgl for beryl which I mostly use. The way to do it is described in the wiki for the beryl-project.

[http://wiki.beryl-project.org/wiki/Install_Beryl_on_Ubuntu](http://wiki.beryl-project.org/wiki/Install_Beryl_on_Ubuntu)

---

### Post by nik1111 on 2007-01-28
Hi guys
Did anybody get a problem with the sound with the following update?

linux-libc-dev

I see there is a patch for hda_intel.c in there so I just wanted to ask you..

---

### Post by jdong on 2007-01-28
> **nik1111 said:**
> I believe Xgl does not support OpenGl on top of it.But I may be mistaken. 

I have the same problem with direct rendering so what I have done is that I have created 2 separate profiles one for gnome+3D acceleration for games mainly and one for Gnome+Xgl for beryl which I mostly use. The way to do it is described in the wiki for the beryl-project.

[http://wiki.beryl-project.org/wiki/Install_Beryl_on_Ubuntu](http://wiki.beryl-project.org/wiki/Install_Beryl_on_Ubuntu)


Excuse me? Do I need screenshots of supertux, chromium, glxgears, and mplayer -vo gl2 running at the same time on Xgl?

Xgl cannot "direct render" because it is passing control of the desktop to a compositing manager -- same can be said about AIGLX. The benefit of AIGLX in this case is being easily deactivatable without a logout/login. Doom3 does not run with beryl+NVidia 9xxx either -- Beryl must first be deactivated and only then will Doom not run on a distorted screen.

---

### Post by nik1111 on 2007-01-29
jdong, I didnt quite get what you meant by that. You mean you can run all those without direct rendering?.. I can't that's why I posted the second point of the post

The second one although I didnt quote, was aimed at haani's question. 

And if I made a mistake about opengl, as I said, I may be mistaken, I hope you were not offended by that.

---

### Post by jdong on 2007-01-29
> **nik1111 said:**
> jdong, I didnt quite get what you meant by that. You mean you can run all those without direct rendering?.. I can't that's why I posted the second point of the post

The second one although I didnt quote, was aimed at haani's question. 

And if I made a mistake about opengl, as I said, I may be mistaken, I hope you were not offended by that.
Right, Xgl supports using OpenGL and XVideo inside of it, and it's still hardware-accelerated, just not "direct rendered".

Sorry I didn't mean to sound like I was offended -- just wanted to point out that direct rendering and hardware acceleration are two completely different concepts (direct rendering is _one method_ of obtaining hardware acceleration, but it is not the only one).


Note that it's not perfect -- direct rendering is still faster for things like 3D games. However, an interesting point is Xgl acceleration draws fullscreen videos more smoothly than non-Xgl XVideo or OpenGL acceleration on our video cards :)

---

### Post by nik1111 on 2007-01-29
Yeah, some apps like dvd's run a bit better when direct rendering is enabled but glxgears runs at double fps for me in xgl than in the direct rendered session :) on the other hand google-earth won't start in xgl... Oh well!

---

### Post by jdong on 2007-01-29
glxgears is not meant as any kind of benchmark or performance-verifying tool, it just serves to show if your system can render any OpenGL, without crashing.

I don't have experience with Google Earth -- it is very possible that it needs some opengl extension not implemented by the Xgl server :(

---

### Post by gmc on 2007-02-01
Hi Folks,

Um, I've got a problem with my internal drive. I attempted to install Edgy-Alternate. During the install, I decided to use LVM. Since the the default swap partition was going to be 6.4GB, I tried to resize it down to 1GB. The system reported that it was resizing the partition in question. After waiting for 45 minutes, I decided to reboot the system.

Now I can't re-install Ubuntu at all. I'm getting error messages as follows:

ata1: command 0xc8 timeout, stat 0xd0 host_stat 0x21
ata1: translated ATA stat/err 0xd0/00 to SCSI SK/ASC/ASCQ 0xb/47/00
ata1: status=0xd0 {Busy}
sd 0:0:0:0: SCSI error: return code =0x8000004
sda: Current: sense key: Aborted Command
      Additional sense: Scsi parity error
Info fld=0x0
end_request: I/O error, dev sda, sector 0

Any idea's, or have I blown away my harddrive?

Gord

---

### Post by cbudden on 2007-02-01
> **gmc said:**
> Hi Folks,

Um, I've got a problem with my internal drive. I attempted to install Edgy-Alternate. During the install, I decided to use LVM. Since the the default swap partition was going to be 6.4GB, I tried to resize it down to 1GB. The system reported that it was resizing the partition in question. After waiting for 45 minutes, I decided to reboot the system.

Now I can't re-install Ubuntu at all. I'm getting error messages as follows:

ata1: command 0xc8 timeout, stat 0xd0 host_stat 0x21
ata1: translated ATA stat/err 0xd0/00 to SCSI SK/ASC/ASCQ 0xb/47/00
ata1: status=0xd0 {Busy}
sd 0:0:0:0: SCSI error: return code =0x8000004
sda: Current: sense key: Aborted Command
      Additional sense: Scsi parity error
Info fld=0x0
end_request: I/O error, dev sda, sector 0

Any idea's, or have I blown away my harddrive?

Gord

Not really sure but if you booted into a live cd then you could use gparted to blank your drive and start over?

---

### Post by gmc on 2007-02-01
> **cbudden said:**
> Not really sure but if you booted into a live cd then you could use gparted to blank your drive and start over?

I wish I could! The system won't boot any CD or DVD's. I've tried 6.06 live,6.10 live, 6.10 Alt, and my gparted recovery CD. I think the drive is dead, and so I'm on my way out the door to get a new drive :-(

So for the record, my drive was 1 year old on 19 Jan, so I'm not too impressed with Seagate

Gord

---

### Post by nik1111 on 2007-02-02
> **gmc said:**
> I wish I could! The system won't boot any CD or DVD's. I've tried 6.06 live,6.10 live, 6.10 Alt, and my gparted recovery CD. I think the drive is dead, and so I'm on my way out the door to get a new drive :-(

So for the record, my drive was 1 year old on 19 Jan, so I'm not too impressed with Seagate

Gord

You are worried about that? Mine died in 2 months!

---

### Post by llbra on 2007-02-02
The camera is working well, VLC makes it rock.
The downside is that everytime there is kernel headers update I need to reinstall the driver, and I`m not being able to shut off my PC. The bad news it is because of the driver. Don`t know why, but after I installed it, in both times, the PC won`t shut off and it stops at the "loading bar" screen, every time at the same point, almost in the "U" from Ubuntu.

Another problem I`m facing is with the Beryl. To make it work, I had to turn off Composite in /etc/X11/xorg.conf and coudn`t put DRI as "true", so I removed this line, set Composito to "0" and it worked, but I`m getting some dirty image in the screen.

---

### Post by gmc on 2007-02-02
> **nik1111 said:**
> You are worried about that? Mine died in 2 months!

 :-o now that really sucks. I see Fujitsu is about to release a 300GB 2.5¨ SATA drive, though it´s only 4200 rpm. I might get one of those in the summer and put this Hitachi in an external enclosure.  Gord

---

### Post by unz on 2007-02-02
> **llbra said:**
> Another problem I`m facing is with the Beryl. To make it work, I had to turn off Composite in /etc/X11/xorg.conf and coudn`t put DRI as "true", so I removed this line, set Composito to "0" and it worked, but I`m getting some dirty image in the screen.

i got beryl [0.1.9999.1] working with this conf [ati-drivers 8.33.6]
```

Section "ServerFlags"
   Option "AIGLX" "off"
EndSection 

Section "Device"
        Driver      "fglrx"
#       Driver      "radeon"
        Option      "no_accel" "no"
        Option      "no_dri" "no"
        Option      "UseFBDev" "off"
        Option      "DynamicClocks" "on"
        Option      "mtrr" "off"
#       Option       "Capabilities" "0x00000000"
        Option      "UseFastTLS" "0"
#       Option       "BlockSignalsOnLock" "on"
        Option      "UseInternalAGPGART" "no"
#       Option       "ForceGenericCPU" "no"
        Option      "Composite" "Off"
        Option      "PowerState" "1"
        # attiva l'uscita TV
        Option      "DesktopSetup" "clone"
        Option      "ScreenOverlap" "0"
        Option      "NoTV" "no"
        Option      "TVFormat" "PAL-B"
        Option      "TVStandard" "PAL-B"
        Option      "TVHSizeAdj" "100"
        Option      "TVVSizeAdj" "100"
        Option      "TVHPosAdj" "20"
        Option      "TVVPosAdj" "0"
        Option      "TVHStartAdj" "0"
        Option      "TVColorAdj" "0"
        Option      "GammaCorrectionI" "0x06419064"
        Option      "GammaCorrectionII" "0x06419064"
        Option      "PairModes" ""
        BusID       "PCI:1:0:0"
EndSection

```


ps: i'm on gentoo, not ubuntu ... but i think it's the same

---

### Post by nik1111 on 2007-02-02
> **gmc said:**
> :-o now that really sucks. I see Fujitsu is about to release a 300GB 2.5¨ SATA drive, though it´s only 4200 rpm. I might get one of those in the summer and put this Hitachi in an external enclosure.  Gord

I use a 320 gb usb harddisk and it works just fine,no performance issues, so you can do that as well.

---

### Post by nik1111 on 2007-02-02
> **llbra said:**
> The camera is working well, VLC makes it rock.
The downside is that everytime there is kernel headers update I need to reinstall the driver, and I`m not being able to shut off my PC. The bad news it is because of the driver. Don`t know why, but after I installed it, in both times, the PC won`t shut off and it stops at the "loading bar" screen, every time at the same point, almost in the "U" from Ubuntu.

Another problem I`m facing is with the Beryl. To make it work, I had to turn off Composite in /etc/X11/xorg.conf and coudn`t put DRI as "true", so I removed this line, set Composito to "0" and it worked, but I`m getting some dirty image in the screen.

Are you trying ot use it with aiglx? perhaps you need xgl.

---

### Post by nik1111 on 2007-02-02
I was just wondering is it possible for our laptop, with the official ati drivers to get more than
1280x800 resolution? Is it safe to add any more to xorg.conf? 1280x800 is the maximum detected in my case.

---

### Post by cbudden on 2007-02-02
Does anyone have a problem with bluetooth and edgy.  My phone cannot see my laptop, but the laptop can see the phone.  :S

---

### Post by Frank Golden on 2007-02-02
> **nik1111 said:**
> I was just wondering is it possible for our laptop, with the official ati drivers to get more than
1280x800 resolution? Is it safe to add any more to xorg.conf? 1280x800 is the maximum detected in my case.1280x800 is the native resolution any thing more wouldn't
look right would it?

Update: just checked in XP 1280X800 appears to be the max available using the Omega drivers.

---

### Post by nik1111 on 2007-02-02
> **Frank Golden said:**
> 1280x800 is the native resolution any thing more wouldn't
look right would it?

Update: just checked in XP 1280X800 appears to be the max available using the Omega drivers.

I was under the impression I could get more in xp with ati drivers. I had omega as well for some time. I can't check it now though cause I don't have xp any more. Anyway thanx for the answer.

---

### Post by llbra on 2007-02-02
> **cbudden said:**
> Does anyone have a problem with bluetooth and edgy.  My phone cannot see my laptop, but the laptop can see the phone.  :S

You need to make your PC discoverable. I don`t remember how to do that, but I think I some tutorials on that, maybe looking at Google should do.

---

### Post by gmc on 2007-02-03
> **nik1111 said:**
> I use a 320 gb usb harddisk and it works just fine,no performance issues, so you can do that as well.

:-) I do... I currently have 2x250GB + 1x320GB drives in 3 external USB enclosures, so I´m not really hurting for drive space at the moment, but it sure would be nice to have 300GB to go (with the laptop).

In case you´re wondering why so much drive space, I added a WinTV PVRUSB2 and record and edit video on my machine.

Gord

---

### Post by nik1111 on 2007-02-03
> **gmc said:**
> :-) I do... I currently have 2x250GB + 1x320GB drives in 3 external USB enclosures, so I´m not really hurting for drive space at the moment, but it sure would be nice to have 300GB to go (with the laptop).

In case you´re wondering why so much drive space, I added a WinTV PVRUSB2 and record and edit video on my machine.

Gord

I know what you mean :) 
I havent bothered to fix it too but I will some time soon because it's more of a desktop now than a laptop ;)

---

### Post by llbra on 2007-02-05
Here comes a tip.

Before doing the 'sudo modprobe tifm_sd' just do:

update the pci hardware info, to recognize properly our hardware

    sudo update-pciids

and the see the devices.

    lspci | grep Texas

---

### Post by gmc on 2007-02-12
Hi Folks,

Just a heads up. Seems like there's a new driver for our beloved ipw3945 wireless coming down the pike. [Here's]("http://kerneltrap.org/node/7704") the details and installation instructions in case you need a little project to work on. Apparently it can be implemented concurrently with the current setup, so no need to break your working setup to test this new driver. Hopefully Feisty will be able to include this for release date.

Gord

---

### Post by anionline on 2007-02-13
Hello!
I read this thread since i buy my Acer Aspire 5672 in July 2006. This resolve very problems and tips in my ubuntu. Thanks a lot for that.
I installed dapper, migrated to edgy, with 2.4.17 kernel.
I use my notebook to work, develop applications, testing other servers, access via ssh , etc. And to personal use music, photos, videos, mldokey, etc.

Now, i take a two few problem.
1- My webcam. I installed [http://mxhaard.free.fr/spca50x/Downl...0061216.tar.gz;](http://mxhaard.free.fr/spca50x/Downl...0061216.tar.gz;) but webcam not work. I see the light indicate turn on is on, but when i test with amsn, did not work. How can i do to resolve this.

2- how can it work my sd/mmc/memory stick card reader?

Ok, sorry for my BAD english :( :( :( , i'm spanish/argentinian user...

thanks

---

### Post by jdong on 2007-02-13
**Heads-up:** Flashreader is broken in 2.6.20 (Feisty) as of now -- it's an upstream kernel bug, the maintainer acknowledges that it's true.

---

### Post by cbudden on 2007-02-13
Is there any news on the card reader support more card types such as Sony memory stick or XD?

---

### Post by jdong on 2007-02-13
The guy says it's 'in development' -- that's all we have to work with. He has been donated samples of each kind of card and he's pretty active fixing his driver, so I have to assume he means it.

---

### Post by beejay82 on 2007-02-16
Hi all,

Noob question,

Is there a way to get the VGA out or DVI out to work?  I am using the generic fglrx driver and was trying to do the HowTo MergedFB with no success?  Anyone have steps to do this?  I really need to do a slideshow presentation and I can't get it to work in LInux so I am ashamed that I swap out HDD with a Windows OS.  Do I need to install the ATI drivers from ATI's website?  Any help is greatly  appreciated.

_____________________________________
Laptop - Acer Aspire 5672WLMi | Intel Core Duo T2300 | ATI Mobility Radeon X1400 512MB| 1GB DDR2-PC5300 |  100GB SATA 8MB Cache HDD
Desktop - AMD Athlon 64x2 3800+ (2000 MHz) | NVIDIA GeForce 7600 GT (256 MB) | 2GB DDR-PC3200 | 250GB SATA2 16MB Cach HDD

---

### Post by giorgenes on 2007-02-16
VGA out worked fine for me, I didn't do any special setup about it.
I have ati driver installed.
All I had to to was connect the VGA out to the projector and then reboot the system.
Doing that all output goes to the VGA out (but the LCD goes black).

---

### Post by beejay82 on 2007-02-16
Is it possible to go dual display or stretched desktop with this?  Thanks!

___________________
Laptop - Acer Aspire 5672WLMi | Intel Core Duo T2300 | ATI Mobility Radeon X1400 512MB| 1GB DDR2-PC5300 | 100GB SATA 8MB Cache HDD
Desktop - AMD Athlon 64x2 3800+ (2000 MHz) | NVIDIA GeForce 7600 GT (256 MB) | 2GB DDR-PC3200 | 250GB SATA2 16MB Cach HDD

---

### Post by giorgenes on 2007-02-16
hm, i'm not sure.
didn't work like that for me.
all I got is the VGA out working and a black screen on the main screen.
but that helps, anyway, and I guess no special setup is needed.

---

### Post by jdong on 2007-02-16
It should work but IIRC fglrx only supports identical resolutions on both screens.
You can instead use Xinerama which allows arbitrary sized screens but you'll lose 3D.

---

### Post by beejay82 on 2007-02-16
I probably really don't need any 3d for doing Slideshows.  Is there a HowTo to configure Xinerama?  Thanks for all the info on this.  I'm very new to Linux so still trying to get familiar with it.

---

### Post by nik1111 on 2007-02-20
For those of you running Xgl, do you ever get a "display-freeze" if you try to log out of gnome?Sometimes I just see an orange screen and just stays there.. May be related to fglrx.

---

### Post by jdong on 2007-02-20
That's more of an Xgl issues -- you should use the dbus variant method to launch gnome-session rather than just exec gnome-session (explained in the Beryl wiki pages)

---

### Post by nik1111 on 2007-02-20
I have done it otherwise it wouldn't load the theme as well.. I think I ll just wait for any beryl&Xgl updates as I can't find a single cause nor a single solution for those freezes. They don't happen each time as well which is another strange point :)

---

### Post by jdong on 2007-02-20
Can ctrl+alt+bksp zap out of your 'display freeze'? Maybe I'm just not comprehending what constitutes a freeze :)

---

### Post by nik1111 on 2007-02-20
> **jdong said:**
> Can ctrl+alt+bksp zap out of your 'display freeze'? Maybe I'm just not comprehending what constitutes a freeze :)

A freeze (using my terminology :) ) is a screen where nothing moves. 
The typical freeze I get is an orange screen during logout which just stays there.
ctrl+alt+backspace works from inside the session.But that's not really logging out is it? It stills leaves the other session logged in and allows you to switch user.. Oh, and of course if I press the logout button and it "freezes" then pressing that combination doesn't do anything.

It's not so bad, it's just that when it happens the only thing I can do is press the shutdown button and then restart the laptop.Strangely enough that initiates a normal shutdown which means it can run some commands, while at the same time I can't ctrl-alt-backspace. If you search the forums here for freeze you ll see many people have such problems and no single solution exists. The wiki for beryl doesn't suggest anything for that so I ll just hang around and see what happens.

I m quite curious how you don't get the same thing though. Maybe because my card is an X1600? :-k Maybe it's beryl because when I reboot after the freeze there is an indicator in the tray which says that beryl-xgl had crashed. 
i hope the next version of beryl fixes that.

---

### Post by jdong on 2007-02-20
no, ctrl+alt+bksp is a totally valid logout -- it kills the X server, which GDM then respawns.

And if your GNOME line is like '        exec dbus-launch --exit-with-session gnome-session
'

Then you should not be left @ the orange.

---

### Post by nik1111 on 2007-02-21
After a few tries I came to the conclusion that if the logout button wants to hang my display so will ctrl alt and backspace.
The line you mention is in the startberyl script, is that what you mean?

Anyway don't bother any more over it, I won't.

---

### Post by gmc on 2007-02-22
Hi Folks,

Anyone here running Feisty? I've noticed that irregardless of the settings I tell sysfsutil to set the processor(s) speedstep value to 'powersave', something in gnome keeps changing it to 'ondemand'. It's a little frustrating as I'm working with a lot of video editing and really don't want the processors cranking along at full speed and heating the laptop up for hours on end.

Anyone have any ideas where gnome is overriding my choice and setting them to 'ondemand'?

Frustrated
Gord

---

### Post by jdong on 2007-02-22
Hmm I have no idea why that's happening for you on Feisty, but I'm running Feisty too.

As I said the cardreader doesn't work in 2.6.20 (upstream bug) but everything else looks good.

P.S. ATI 8.34.6 is posted; it helps make suspend to disk/ram work again (it was pretty broken since like 8.31)

---

### Post by gmc on 2007-02-22
> **gmc said:**
> 
Anyone have any ideas where gnome is overriding my choice and setting them to 'ondemand'?

Frustrated
Gord


I found my answer. Using the configuration editor and navigating to **/app/gnome-powermanager/cpufreq_ac_performance** and   **/app/gnome-powermanager/cpufreq_battery_performance** were both set to ondemand. I just needed to edit the cpufreq_ac_performance to powersave and re-login to gnome.

Hope this helps,
Gord

---

### Post by llbra on 2007-02-22
Has anyone got XGL to work, since AIGLX doesn`t work due to Composition? All my tries led me to some sort of failures.

If so, could post here the steps??

Thanks in advance.

---

### Post by gmc on 2007-02-22
> **llbra said:**
> Has anyone got XGL to work, since AIGLX doesn`t work due to Composition? All my tries led me to some sort of failures.

If so, could post here the steps??

Thanks in advance.

 3 updates ago, beryl worked but since then I've had to disable it as when it starts up all I get is a white screen. So the problem may be something your missing, but I seriously suspect it's currently broken.  Gord

---

### Post by Frank Golden on 2007-02-23
Hi All, Just updated Edgy on our laptop. Wi-Fi stopped working. Computer don't see
Wi-Fi card. Anyone else having same problem. Updated kernel 2.6.17.11.

---

### Post by nik1111 on 2007-02-23
> **gmc said:**
> 3 updates ago, beryl worked but since then I've had to disable it as when it starts up all I get is a white screen. So the problem may be something your missing, but I seriously suspect it's currently broken.  Gord

Gmc you can fix that. Search synaptic for beryl and downgrade every package that has the word beryl in it to version 0.1.99.2

---

### Post by gmc on 2007-02-23
> **nik1111 said:**
> Gmc you can fix that. Search synaptic for beryl and downgrade every package that has the word beryl in it to version 0.1.99.2

Thanks for the tip. I'll just wait until they get the problem sorted out.

Gord

---

### Post by Frank Golden on 2007-02-26
> **Frank Golden said:**
> Hi All, Just updated Edgy on our laptop. Wi-Fi stopped working. Computer don't see
Wi-Fi card. Anyone else having same problem. Updated kernel 2.6.17.11.
Anyone? jdong? Is this a known problem? Any dev's reading? Please help.

---

### Post by jdong on 2007-02-26
I installed Edgy to an external and upgraded it to -11, and it's still working. You sure linux-generic metapackage is installed?

---

### Post by Frank Golden on 2007-02-26
> **jdong said:**
> I installed Edgy to an external and upgraded it to -11, and it's still working. You sure linux-generic metapackage is installed?
Thank You, jdong as usual you hit it right on the head. Installed the metapackage from Synaptic and have Wi-Fi working again.

Why was it not installed? Why did Wi-Fi work on the earlier kernel? Did the earlier kernel have a different
metapackage associated with it? Why did that get installed if it did but not the newer one?

I guess I will have to check that on future updates.

---

### Post by jdong on 2007-02-26
You probably never installed the linux-generic metapackage, but did something like find linux-image-2.6.17-10-generic and then followed a HOWTO that recommended apt-get install linux-restricted-modules-`uname -r`

This bypasses Ubuntu's metapackage system of making sure kernel packages are all installed together.

Another possibility is executing a dist-upgrade when only an updated linux-image and not restricted-modules is available, in which case dist-upgrade goes to extraordinary measures to update (i.e. remove metapackage).

---

### Post by cbudden on 2007-03-02
Hello again.

Is anyone using Feisty?  I upgraded last night, and my bluetooth is working again!  BUT my suspend to ram isn't.  The machine goes down, and "off" but when I go to resume the screen does not turn on, not even the backlight.  Has anyone else got this problem?  I will fiddle with /etc/default/acpi-support to see if I can get it to work.

Chris

---

### Post by jdong on 2007-03-02
Upgrade (manually) to the latest ATI drivers -- that fixes it.

---

### Post by cbudden on 2007-03-02
Ok jdong, ill do that and get back to you.  Thanks

---

### Post by cbudden on 2007-03-02
Right, I tried the howto here - [http://wiki.cchtml.com/index.php/Ubuntu_Feisty_Installation_Guide](http://wiki.cchtml.com/index.php/Ubuntu_Feisty_Installation_Guide) but I couldn't get any 3d accel at all.  Is this howto accurate?

---

### Post by jdong on 2007-03-04
Ok, I got the **cardreader working in feisty!**


Somehow the one bundled with the kernel does not work... we need a newer one:
[http://prdownload.berlios.de/tifmxx/tifm-0.8b.tar.bz2](http://prdownload.berlios.de/tifmxx/tifm-0.8b.tar.bz2)

```

find /lib/modules/`uname -r` -name "tifm*" | xargs sudo rm
cd /tmp
wget http://prdownload.berlios.de/tifmxx/tifm-0.8b.tar.bz2
tar xjvf *.bz2
make
sudo make install

```

Now, reboot or unload/reload all the tifm modules, and your cardreader works again!

---

### Post by cbudden on 2007-03-04
Works a treat.  Ish.  I needed to go to [http://prdownload.berlios.de/tifmxx/tifm-0.8b.tar.bz2](http://prdownload.berlios.de/tifmxx/tifm-0.8b.tar.bz2) and then click download.  Jdong, do you have beryl working at all?

---

### Post by jdong on 2007-03-04
Yes:

First you need to prevu my xserver-xgl packages at [https://launchpad.net/ubuntu/+source/xserver-xgl/+bug/87687](https://launchpad.net/ubuntu/+source/xserver-xgl/+bug/87687)

Getting beryl working was a real pain, involving copying beryl to beryl-xgl, and activating copy instead of texture_from_pixmap.

But Compiz, once you get new xgl package, is as easy as installing desktop-effects and hitting that checkbox.

---

### Post by cbudden on 2007-03-04
Have you got a deb you could upload, as your prevu doesn't work well behind a proxy, which I have to use at my uni :(.  Thanks

Also, what version of beryl are you running?  SVN or the official feisty repo version?

Edit

FYI, here is the output of prevu-init from the prevu package in the feisty repo :
```

I: Base system installed successfully.
 -> debootstrap finished
 -> copying local configuration
  -> Installing apt-lines
Refreshing the base.tgz 
 -> upgrading packages
 -> mounting /proc filesystem
 -> mounting /dev/pts filesystem
-> Mounting /var/cache/prevu/feisty-debs
 -> installing dummy policy-rc.d
Ign file: ./ Release.gpg
Ign file: ./ Release
Ign file: ./ Packages
Err http://archive.ubuntu.com feisty Release.gpg    
  Could not connect to archive.ubuntu.com:80 (91.189.89.8), connection timed out [IP: 91.189.89.8 80]
44% [Connecting to archive.ubuntu.com (91.189.89.6)]

```

---

### Post by jdong on 2007-03-04
Look in that same folder on the webserver as the .dsc files, there should be two i386 debs (one of an older version, one of current)

---

### Post by plaz42 on 2007-03-28
I just bit the bullet and wiped my Kubuntu Edgy and did a clean install of Ubuntu Feisty Beta on the 5672.  Everything seems to be working like a charm, but Compiz won't get working for me.  I installed xserver-xgl, and the first time i enable desktop effects, it engaged right off the bat, with snazzy wobbly menus and all that.  

However, I installed gnome-compiz-manager and clicked on the "GL Desktop" menu item.  After that, my panels started flickering and became unresponsive.  After multiple Ctrl-Alt-Backspaces, I managed to disable Compiz and XGL still works, but enabling Compiz again gives the same result.

Any ideas?


EDIT:  Solved ... ish.  I forgot that I also installed compiz-extras at the same time, and uninstalling that package brings Compiz back to full operation.  Now if only that package would get fixed.

---

### Post by cbudden on 2007-03-28
I am using feisty, since an update a couple of days ago, if I log in using XGL, all i get is my desktop background :(.  Need to login using a standard gnome desktop.  Unfortunatly I can't run desktop-effects to disable them, as there is no composite extention enabled.

---

### Post by phatloader69 on 2007-04-14
Could someone please help me out? I tried to use system recover, alt-f10 app pulls up, selected restore fact. settings, says it will boot and dorsn't go to restoring drive, it just boots to windows!! Where is my hammer. I read someone's post about uploading dvd recovery disc. I would be forever greatful. I can't find mine,, and don't think i'llbe able to restore my laptop without it. The comp usa techs will give me a winxp home version,(I bought the 3 yr warranty ) but it won't have the device drivers, nor do I really want to search for them. I have google acer aspire reciver disk, image and the like with no luck. If you up the image,(rapidshare it, I have a prem account) mail it, I'll pay the postage on it,, whatever. I think the only way this is going to work, is if I get a young priest and a old priest ;)  

Thanks guys!

[email]Phatloader69@hotmail.com[/email]

---

### Post by phatloader69 on 2007-04-15
[COLOR="black"]_could you please make me a copy of that recovery dvd cd _[/COLOR], mine is LOST,, I'm trying to restore factory setting,, but apparently can't , shoot, I can't even find my last post asking same thing, forgive if it seems like spamming,, at wits end here(its a short walk! ;) send message, apparently I know how to get at least those! LOL

phatloader69
[email]phatloader69@hotmail.com[/email]

thanks guys!!

---

### Post by jdong on 2007-04-15
It is against the EULA to redistribute the recovery CD. Such behavior will not be tolerated at these forums.

---

### Post by gmc on 2007-04-15
> **phatloader69 said:**
> Could someone please help me out? I tried to use system recover, alt-f10 app pulls up, selected restore fact. settings, says it will boot and dorsn't go to restoring drive, it just boots to windows!! Where is my hammer. I read someone's post about uploading dvd recovery disc. I would be forever greatful. I can't find mine,, and don't think i'llbe able to restore my laptop without it. The comp usa techs will give me a winxp home version,(I bought the 3 yr warranty ) but it won't have the device drivers, nor do I really want to search for them. I have google acer aspire reciver disk, image and the like with no luck. If you up the image,(rapidshare it, I have a prem account) mail it, I'll pay the postage on it,, whatever. I think the only way this is going to work, is if I get a young priest and a old priest ;)  

Thanks guys!

[EMAIL="Phatloader69@hotmail.com"]Phatloader69@hotmail.com[/EMAIL]



Unfortunately, I can't help with the recovery disk. I haven't seen mine in quite sometime. However, you say that CompUSA will assist you with WindowsXP Home (less the drivers). You can find the drivers and all the custom software [***here***.]("ftp://ftp.support.acer-euro.com/notebook/") Maybe it might be worth getting CompUSA's help and download what you need/want from the above site and rebuild your system that way.


Gord

---

### Post by phatloader69 on 2007-04-15
> **jdong said:**
> It is against the EULA to redistribute the recovery CD. Such behavior will not be tolerated at these forums.

Forgive me, but this is a reply I recieved from Acer tech when I inquired about my plight.

Excuse me, but the recovery disk which ONLY works with said listed model aspire 5672 WLMI, is within end user lincense agreement "Provided that said laptop/computer had Originally said software. The end user of said hardware IS allowed to have ONE copy of back-up or restore disk, as long as it is NOT installed 2 computers simutanulusly. It however is NOT allowed to have a version that had not originally shipped with said model, UNLESS a upgrade is offered which would require the aquiring of a new product key, which would acccompany said upgrade"(acer tech quote). Since Comp USA sold me the acer, which I love, with a 3yr replacemnt warranty that covers everything(should since it was 359.00, they could get me the restore disk. The tech manager asked me to bring in the notebook, took model make and serial, and said he would order the disk for me. I had originally thought that I would have to ship the notebook, or be without it, and since it has my store business on it, it wasn't an option. I was wrong, he said he only needed the serial# and product number, and they already had the service agreement, which has 2 yrs left on it and sent me on my way. He said it will take 7-10 days. I'm relieved.

I'm replying to your previous post, as I'm sure you don't want to give out the wrong information to someone else.I don't want to be misinformed, and sure you don't want to be misinformed either. IF you'd like, I'm more than happy to send you a copy of his email. Have a blessed day.Thanks again for  allowing me to post in your great forum.

Phatloader:D

---

### Post by phatloader69 on 2007-04-15
> **gmc said:**
> Unfortunately, I can't help with the recovery disk. I haven't seen mine in quite sometime. However, you say that CompUSA will assist you with WindowsXP Home (less the drivers). You can find the drivers and all the custom software [***here***.]("ftp://ftp.support.acer-euro.com/notebook/") Maybe it might be worth getting CompUSA's help and download what you need/want from the above site and rebuild your system that way.


Gord

Thanks Gord, I have COMP USA's great tech manager getting me the disk. As previous posted, let me know if you need it,, the EULA, allows 1 backup/resotre copy for your Laptop. Keep in mind that you HAVE to use the Product #, sticker that came with THAT laptop, otherwisee you can get into trouble. It would considered a Pirate copy, which is against the law. 

Keep it legal, and love it. The law is setup to protect the simple people.

Phatloader:guitar:

---

### Post by jdong on 2007-04-15
Of course you are allowed to have a copy of the software, but it is not within the terms of the agreement for me, having a licensed copy, to give it to someone else -- even if they have the exact model laptop.

---

### Post by phatloader69 on 2007-04-15
You could, only IF they person who owns the same make and model, who can provide both receipt of said purchase and a valid OEM product key which should be stickered to the bottom, not the back of the laptop. It's what i was told, probably why Comp USA is ordering, at no cost mind you, the exact same recovery disk.I just left there. Jamie the M.O.D. of the store, offered again to give me a WinXP Home disk, loaded with all device drivers, for this laptop. I explained to him, that winxp full disk will wipe out the d drive including the hidden partition, and all information and data within. He spoke to his senior tech, whick confirmed this. I conveyed your comments, about violating EULA, and he said it doesn't aply as I own the rights to having a restore disk for my laptop. He wanted to remind you that the poster, you, are not releasing the product code from your laptop, that I would be using mine, which came with my laptop. which is in terms of the lincense agreement. I'm not asking your restore disk with product code, only the restore disk which to start restore, and use my product code which shipped with this laptop. Apparently, when they started selling laptops, without system restore disk packed in the box, people would by pass making restore disk, then if the disk or data became damaged, people were unable resotre their respective systems. Comp USA tech department actually uses a outside company that stores/sells thoses restore disks, which is where jamie and the people from tech can restore factory settings.He was going to make a restore disk from another acer, which was on display,new make, same features, but it was running vista. I politely said no,, as that version did NOT ship with this lapetop,, not does vista have an extensive libriary of drivers, which I'm sure you know. I have it on another computer. I only want what came on this laptop. He said he understood. there are many sitez I'm sure you know, that pander illeigal copys of software, as stated in prev. post. Keep it legal. Software developers have familes too, that they need to support. If the program is well written, and you find it viable and useful. Pay for it. Simply stated. Its probably why you can buy quick books, and if doesn't suit you needs,, they will refund your money(90 day trial w/money back guarantee) Where if you buy say MS Office,, buddy, wether it works for you or not, you own it. Its why you'll find alot on ebay.

I again, was looking for help legally,, I would never ask for someone to do something legal nor immorally.
I do well finacially, and could just buy another laptop if needed, but i like this one.Enuf said:) 

phatloader69

---

### Post by phatloader69 on 2007-04-15
See Microsoft EULA, heres the link read section 1 -1.5 :KS 

[http://www.microsoft.com/windowsxp/home/eula.mspx](http://www.microsoft.com/windowsxp/home/eula.mspx)

have a great day! really like your forum!

phatloader69:popcorn:

---

### Post by jdong on 2007-04-15
For the record:
No, you may not furnish another user with a copy of your own recovery CD, even if they are legally entitled one, unless you are transferring your license to that person and proceed to destroy any you own. I know it's not your intention to violate the EULA, but you were asking for someone to send you a copy of the recovery CD, which is not legal. Whoever is telling you is also misinformed.

> 13. SOFTWARE TRANSFER. Internal. You may move the Software to a different Workstation Computer. After the transfer, you must completely remove the Software from the former Workstation Computer. Transfer to Third Party. The initial user of the Software may make a one-time permanent transfer of this EULA and Software to another end user, provided the initial user retains no copies of the Software. This transfer must include all of the Software (including all component parts, the media and printed materials, any upgrades, this EULA, and, if applicable, the Certificate of Authenticity). The transfer may not be an indirect transfer, such as a consignment. Prior to the transfer, the end user receiving the Software must agree to all the EULA terms.

---

### Post by phatloader69 on 2007-04-15
For Comp USA to be a lincensed retailer of Microsoft products, I'm sure that since they deal with Microsoft direct. I.E. sales, service and support, They, Compusa are well aware of what is and isn't a breach of the EULA.Comp USA could and would be liable for the loss of their retailers lincense. Are you also saying that Compusa is in violation of the EULA also? If so you may want to bring it to Microsoft attention. I'm sure that the 100 or so lawyers Compu USA employs for frivous lawsuits, have a complete understanding of microsoft's EULA, Considering it was lawyers that wrote it for microsoft. Don't you agree?

Qoute for qoute then
1.5 Storage/Network Use. ][U]You may also store or install a copy of the Software on a storage device, such as a network server, used only to install or run the Software on your other Workstation Computers over an internal network; however, you must acquire and dedicate an additional license for each separate Workstation Computer on or from which the Software is installed, used, accessed, displayed or run[/U Except as otherwise permitted by the NetMeeting and Remote Assistance features described above, a license for the Software may not be shared or used concurrently on different Workstation Computers

---

### Post by jdong on 2007-04-15
CompUSA is most certainly licensed/authorized to distribute recovery CD's and Windows CD's, but none of us are. The warning was with respect to post

> 
could you please make me a copy of that recovery dvd cd , mine is LOST,, I'm trying to restore factory setting,, but apparently can't , shoot, I can't even find my last post asking same thing, forgive if it seems like spamming,, at wits end here(its a short walk!  send message, apparently I know how to get at least those! LOL


---

### Post by Frank Golden on 2007-04-20
Well I'm stumped. I downloaded the alternate Feisty CD and while trying to install, everything freezes up
at the point in the software installation (85%) that says "installed brltty-x11". I repeated this twice.
No error message, just everything comes to a screeching halt. Any ideas?

BTW, MD5 sum on the D/L checked out, burned disc slow and disk integrity check showed valid CD.

---

### Post by nik1111 on 2007-04-21
Guys whats going on with that "cannot access tty job" error? I downloaded feisty livecd and can't boot it without using some extra options.
If I upgrade online to feisty is there any chance of ending up with an unbootable system?

---

### Post by mfa81 on 2007-04-22
Where can i get the tifm-0.8b.tar.bz2 file ? [http://prdownload.berlios.de/tifmxx/tifm-0.8b.tar.bz2](http://prdownload.berlios.de/tifmxx/tifm-0.8b.tar.bz2) is offline !

---

### Post by gmc on 2007-04-25
> **Frank Golden said:**
> Well I'm stumped. I downloaded the alternate Feisty CD and while trying to install, everything freezes up
at the point in the software installation (85%) that says "installed brltty-x11". I repeated this twice.
No error message, just everything comes to a screeching halt. Any ideas?

BTW, MD5 sum on the D/L checked out, burned disc slow and disk integrity check showed valid CD.

Hi Frank,

Are you still having trouble with feisty? I did an install of the desktop and alternate versions over the last day or so and didn't have any troubles?

Regards
Gord

P.S. I picked up a Macbook to go with my Rain Design tray you recommended last summer! :-)

---

### Post by dyous87 on 2007-04-25
I just wanted to warn everyone who owns this laptop that acer has just recalled the batteries due to overheating problems. 

Visit this [site]("http://www.acerbatteryrecall.com/AcerWeb/") for more information and to send for a new replacement battery.

---

### Post by Jensdt on 2007-04-25
Hello,

I did a fresh install to Feisty recently, and I seem to be have some problems with hibernate, namely:

* Sometimes wireless works, sometimes it doesn't (It just doesn't show any wireless devices, as if the 'kill switch' would be on - but it's not.)
* Sound never works
* The 'power-led' keeps blinking.

Any help on this?

Regards,
Jens

---

### Post by tonyr1988 on 2007-04-25
> **dyous87 said:**
> I just wanted to warn everyone who owns this laptop that acer has just recalled the batteries due to overheating problems. 

Visit this [site]("http://www.acerbatteryrecall.com/AcerWeb/") for more information and to send for a new replacement battery.
Thank you very much for that link. Fortunately, it looks like my battery isn't specifically being recalled, but I never would have heard about that if it weren't for you.

Does anyone know if they have e-mail alerts set up for this thing? Like, can I register somewhere and have them e-mail me for important information like this?

---

### Post by mfa81 on 2007-04-25
> **mfa81 said:**
> Where can i get the tifm-0.8b.tar.bz2 file ? [http://prdownload.berlios.de/tifmxx/tifm-0.8b.tar.bz2](http://prdownload.berlios.de/tifmxx/tifm-0.8b.tar.bz2) is offline !

can someone upload the file tifmxx-0.8b.tar.bz2 ? there is only 0.8d for download, and I got some errors compiling the driver, and I cant resolve the problem because I have no idea about the source code of tifm

---

### Post by jdong on 2007-04-25
HECK YEA!! MY BATTERY IS UNDER RECALL! And I have 34% capacity right now. GREAT timing!

As far as tifm, **PLEASE SIT TIGHT**!! The developers have acknowledged the problem and are preparing a kernel update for it!

The stock driver will not install, but there is a script out there to patch the driver. Personally, **I recommend to WAIT**. If that script conflicts with the official update, it would definietly be not worth your time to chase after more broken modules....

---

### Post by dyous87 on 2007-04-26
yes me too, i'm just upset that it doesn't cover my laptop. it has overheated a few times due to the battery and the frame around the keyboard and monitor melted and shifted a bit because of it.

---

### Post by jdong on 2007-04-26
Try to talk to Acer support about something like that.

---

### Post by dyous87 on 2007-04-26
I did, they are no help, especially since my warranty is up.

---

### Post by gmc on 2007-04-26
> **jdong said:**
> HECK YEA!! MY BATTERY IS UNDER RECALL! And I have 34% capacity right now. GREAT timing!

WHAT? what's the deal with this? Should I be worried about an exploding battery?

Gord

---

### Post by jdong on 2007-04-26
Check your serial number at [http://www.acerbatteryrecall.com/AcerWeb/](http://www.acerbatteryrecall.com/AcerWeb/)

It's the same sony recall... no Acers were affected but they are sony cells, so they are just being safe and cautious.

---

### Post by gmc on 2007-04-26
> **jdong said:**
> Check your serial number at [http://www.acerbatteryrecall.com/AcerWeb/](http://www.acerbatteryrecall.com/AcerWeb/)

It's the same sony recall... no Acers were affected but they are sony cells, so they are just being safe and cautious.

Whoa! You had me freaking out for a moment there. I've been running mine on the mains for months now. As a matter of fact it's replaced my desktop system. Now that I think on it, I believe we both got our machines within a few weeks of each other (Jan/19/06) so chances are I'm due a replacement too

Regards
Gord

Update: Luck me, it appears my battery isn't on recall <whew>

---

### Post by lw5 on 2007-04-27
Hi;

I just installed Feisty on an Acer Aspire 5670 and I have a 'problem' with booting. I also posted it [_here_](http://ubuntuforums.org/showthread.php?t=424259&highlight=Acer+Aspire).

During boot, there is quite a long pause, also described [_here_](http://gez.plain.at/blog/ubuntu/installing-ubuntu704-feisty-fawn-herd2-on-an-acer-5672wlmi-laptop/) as:> 
The laptop boots Ubuntu just fine, however it takes a break of about 30 seconds in the mid of starting up. But as this is an early alpha version of Feisty, there is no need to worry — bugs of this sort will vanish once upstart reaches maturity.


Is anyone else experiencing this?

---

### Post by gmc on 2007-04-27
> **lw5 said:**
> Hi;

I just installed Feisty on an Acer Aspire 5670 and I have a 'problem' with booting. I also posted it [_here_]("http://ubuntuforums.org/showthread.php?t=424259&highlight=Acer+Aspire").

During boot, there is quite a long pause, also described [_here_]("http://gez.plain.at/blog/ubuntu/installing-ubuntu704-feisty-fawn-herd2-on-an-acer-5672wlmi-laptop/") as:

Is anyone else experiencing this?

Are you referring to a delay just after USB devices are detected. If so, then yes, I see that here too. Also I find a lot of the time, my external usb drivers will get mounted twice.

Gord

---

### Post by jdong on 2007-04-27
I get like a 5 second hang on bootup while HAL is probing ACPI...

---

### Post by lw5 on 2007-04-27
> **gmc said:**
> Are you referring to a delay just after USB devices are detected. If so, then yes, I see that here too. Also I find a lot of the time, my external usb drivers will get mounted twice.

I'd have to check that. I installed Feisty on a friends laptop and I don't currently have it here. I was planning on checking what exactly is happening when this happens so I'll get back on the subject.

More people seeing this? Should it be reported as a bug?

edit:
@Jdong; no this is not it, it takes at least half a minute.

---

### Post by gmc on 2007-04-27
> **jdong said:**
> I get like a 5 second hang on bootup while HAL is probing ACPI...

Any problems with usb devices? I forgot to mention that when I plug in my portable 80g drive or ipod nano, rebooting is the only way I can unmount them. Manual unmount, dismounts and then immediately remounts the device so that it's no longer safe to remove. I've lost the contents of my Ipod (mostly podcasts) twice now.

Gord

---

### Post by jdong on 2007-04-27
Hmm, nope, iPods/USB works just fine for me, both on my 2-time upgraded system and my livecd's.

---

### Post by lw5 on 2007-04-27
About the USB problems; I see a lot of people having trouble with that. [This](https://bugs.launchpad.net/ubuntu/+source/linux-source-2.6.20/+bug/102659) doesn't happen to be it, does it?

---

### Post by dude051 on 2007-04-27
I tried booting up 7.04 last night on my 5672WLMI but the X Server would not load during the Live CD boot and just error me out to CLI. I got a 6.10 install currently, but I wanted a clean install since I got Beryl running, just wanted no conflicts. Searching I can't find any similar problems posted, but has anyone here ran into this yet?

---

### Post by anionline on 2007-04-27
I have Feisty installed in my Acer 5672. 
I can read SD Card, but not memory stick.
Can anyone help me about how i do to read memory stick card in my notebook?

I have read the post about a driver, but the download server is offline.


tks

---

### Post by jdong on 2007-04-27
It is a known kernel bug in Feisty that the cardreader does not work. A fix is being worked on.

---

### Post by Frank Golden on 2007-04-28
> **dude051 said:**
> I tried booting up 7.04 last night on my 5672WLMI but the X Server would not load during the Live CD boot and just error me out to CLI. I got a 6.10 install currently, but I wanted a clean install since I got Beryl running, just wanted no conflicts. Searching I can't find any similar problems posted, but has anyone here ran into this yet?Same happened here. Booted once no problem. Second time no joy. Rebooted in safe graphics mode no problem. From there was able to install. Not really impressed.
Like Edgy and love Dapper.

---

### Post by dude051 on 2007-04-28
Sadly, I can't even get it to boot once. Looking at the xorg.conf using regular start it uses Vesa but sets my screen resolutions at 4040x4040.... ok, so I run safe graphics mode which uses vga, doesnt work either. So I do a xorg reconfig using vesa,vga then ati and correct (even under) resolutions it throws different errors. Arg, Dapper and Edgy worked fine :(  . My guess might be the kernel being a new version and smp 686, but I'm not sure. Maybe a bug here, who knows. My next trick will be to do an apt-get fglrx to install the official ATI drivers and give that a go. It would be great if these drivers were included in future installs... seeing as how there is more of a move to "unofficial" packages. Is there a way to force a just a regular 386 vanilla kernel during the cd boot?

Also, @Frank Golden  did you do that memrom update yourself and how much did it improve? I was thinking of getting the T7200 cpu for my 5672, but wasn't sure if I should just get a new entire system or not.

---

### Post by jdong on 2007-04-28
Vesa is broken for the ATI X1x00 series: [https://bugs.beta.launchpad.net/ubuntu/+source/xorg-server/+bug/89853](https://bugs.beta.launchpad.net/ubuntu/+source/xorg-server/+bug/89853)

A fix is being worked on.

In the meantime, a workaround:

When it boots to the command line, run "sudo apt-get update; sudo apt-get install xorg-driver-fglrx; sudo aticonfig --initial"

Then, run "sudo /etc/init.d/gdm restart"


This will activate fglrx and hopefully make everything work :)

---

### Post by gmc on 2007-04-28
> **jdong said:**
> It is a known kernel bug in Feisty that the cardreader does not work. A fix is being worked on.

As is bluetooth. I'd discovered that even though the bluetooth light is on but gnome can't see it. Or am I missing something.

```

gord@okami:~$ hciconfig 
hci0:   Type: USB
        BD Address: 00:00:00:00:00:00 ACL MTU: 0:0 SCO MTU: 0:0
        DOWN 
        RX bytes:0 acl:0 sco:0 events:0 errors:0
        TX bytes:0 acl:0 sco:0 commands:0 errors:0

```
Gord

---

### Post by Kwunman on 2007-04-28
Hey,

So far for me Fiesty has worked perfectly. I did a fresh install using the standard live cd install.

webcam worked by installing spc5xx-source through synaptic. 

To get bluetooth working I installed all the bluetooth programs available in Add/Remove Applications, and then added gnome-obex-server to the startup programs, and it works perfectly - others can see me, i can see others and file transfers both ways work.

The card reader reads my sd cards, although i had trouble deleting things from it as well as formatting it, what ever i tried.

If any one has any questions about my set-up, don't hesitate to ask.

Kwun-man

---

### Post by gmc on 2007-04-29
> **Kwunman said:**
> 
To get bluetooth working I installed all the bluetooth programs available in Add/Remove Applications, and then added gnome-obex-server to the startup programs, and it works perfectly - others can see me, i can see others and file transfers both ways work.


I wish it were that simple, unfortunately the device is not recognized by the kernel. So installing every bluetooth package isn't going to help. I wish I still had Feisty-beta installed, I had a bunch of older (2.6.17?) that I could test. Something is definately broken with usb/bluetooth.

Believe it or not, I don't have these same problems with Feisty on my Macbook. Go Figure!

Gord

---

### Post by Frank Golden on 2007-05-01
> **dude051 said:**
> Sadly, I can't even get it to boot once. Looking at the xorg.conf using regular start it uses Vesa but sets my screen resolutions at 4040x4040.... ok, so I run safe graphics mode which uses vga, doesnt work either. So I do a xorg reconfig using vesa,vga then ati and correct (even under) resolutions it throws different errors. Arg, Dapper and Edgy worked fine :(  . My guess might be the kernel being a new version and smp 686, but I'm not sure. Maybe a bug here, who knows. My next trick will be to do an apt-get fglrx to install the official ATI drivers and give that a go. It would be great if these drivers were included in future installs... seeing as how there is more of a move to "unofficial" packages. Is there a way to force a just a regular 386 vanilla kernel during the cd boot?

Also, @Frank Golden  did you do that memrom update yourself and how much did it improve? I was thinking of getting the T7200 cpu for my 5672, but wasn't sure if I should just get a new entire system or not. Yes I did the CPU upgrade myself. It was a piece of cake. The new proc was about $300.00, much less than the price of a new computer. Some of the performance gain was the result of the faster clock speed some as the result of the merom core. Over all about 40% gain. The proc does run about 10°F warmer on average though, but still well below the maximum allowable. You do need the latest BIOS for merom support, available at Acer Euro web site.

---

### Post by gmc on 2007-05-01
> **Frank Golden said:**
> Yes I did the CPU upgrade myself. It was a piece of cake.

Speaking of which, I'm wondering if you've stumbled on some sort of hardware bug. I've done several installed of feisty on my acer and haven't run into problems like you have.

Have you thought about installing Edgy and dist-upgrade to feisty, at least you'll be able to test if it's the default kernel in feisty.

Regards
Gord

---

### Post by gmc on 2007-05-01
Hi Folks,

Although I seemed to be the only one with this problem here, I'll post the solution just in case someone needs it.

The problem was certain usb devices, upon unmounting, the system will immediately remount and not allow safe removal or booting up with usb devices plugged in, would occasionally show up as multiple devices on the gnome desktop.

It seems there's a problem with the hal subsystem and a minor edit is required to correct the problem. As root edit the following file and make the appropriate change.

```

sudo vi /usr/share/hal/fdi/policy/10osvendor/10-storage-policy.fdi

change the line that reads:

<match key="storage.bus" string="usb">
<merge key="storage.requires_eject" type="bool">true</merge>

to:

<match key="storage.bus" string="usb">
<merge key="storage.requires_eject" type="bool">**false**</merge>


```This seems to have fixed both problems.

Regards
Gord

---

### Post by Frank Golden on 2007-05-03
> **gmc said:**
> Speaking of which, I'm wondering if you've stumbled on some sort of hardware bug. I've done several installed of feisty on my acer and haven't run into problems like you have.

Have you thought about installing Edgy and dist-upgrade to feisty, at least you'll be able to test if it's the default kernel in feisty.

Regards
GordHi Gord, I will try the dist upgrade option from Edgy. I did manage a clean install from the LiveCD. My internet connection here at the hotel i'm staying at here in Groton, Ct. (working at Millstone unit
3 Spring refuel) is flakey at best. This could be part of my woes.

---

### Post by jdong on 2007-05-03
I hope by dist upgrade, you guys mean that you are going to run the official update-manager upgrade tool and not an apt-get dist-upgrade, which is the least recommended upgrade method as per Ubuntu's release notes on upgrading ;-)

---

### Post by Frank Golden on 2007-05-04
> **jdong said:**
> I hope by dist upgrade, you guys mean that you are going to run the official update-manager upgrade tool and not an apt-get dist-upgrade, which is the least recommended upgrade method as per Ubuntu's release notes on upgrading ;-)Yep, what he said. I do mean the official tool. But since having mastered partimage I can destroy my Ubuntus at will. As long as I have a partimage image to restore.:) :)

---

### Post by eragorn on 2007-05-04
Can anyone help me?  I have an Acer Aspire 7104WSMi.  I ran edgy for a year with no problems.  I had to fool around with drivers and what not but it was fully functional and ran beryl no worries.

I upgraded to feisty with a fresh install and have worked out everything except video issues.  I have the Intel 915gm chipset and am running the i810 drivers.  Most things work but I can't launch firefox b/c it comes up all distorted.  When I play video with vlc or movie player the video is sketchy at best??  If I alter the size the window the video goes blank.  If I change to the intel driver then the video apps will open then close.....

Any ideas at all???  Should I just revert back to edgy for now?

---

### Post by Kwunman on 2007-05-06
Hey,

I'm not too sure how many of you managed to get Beryl working on this Laptop in the end, but I just found a guide to get Beryl and XGL working.

Some of it is in Swedish, but the majority of the instructions are in English and work fine for me:
[http://ubuntu-se.org/smf/index.php?topic=8913.msg67326]("http://ubuntu-se.org/smf/index.php?topic=8913.msg67326")

It works really well, and the only problem I have is that if I want to change the Emerald theme, I have to reload the window decorator.

I hope this helps,

Kwun-Man

---

### Post by gmc on 2007-05-09
> **eragorn said:**
> Can anyone help me?  I have an Acer Aspire 7104WSMi.  I ran edgy for a year with no problems.  I had to fool around with drivers and what not but it was fully functional and ran beryl no worries.

I upgraded to feisty with a fresh install and have worked out everything except video issues.  I have the Intel 915gm chipset and am running the i810 drivers.  Most things work but I can't launch firefox b/c it comes up all distorted.  When I play video with vlc or movie player the video is sketchy at best??  If I alter the size the window the video goes blank.  If I change to the intel driver then the video apps will open then close.....

Any ideas at all???  Should I just revert back to edgy for now?

I'm not really familiar with the 7104 machine but I think you might be looking for a program called 915resolution. I noted a similar problem with my Macbook which also has an Intel video chips set.


Gord

---

### Post by Markiedam on 2007-05-09
I have a Aspire 5671with the Intel T2300 processor
According to the site
[http://www.intel.com/products/processor_number/chart/coreduo.htm](http://www.intel.com/products/processor_number/chart/coreduo.htm)
this processor is capable of running the Intel VT techology.

Is it true that Acer disabled this feature in the BIOS?
When I run  egrep '^flags.*(vmx|svm)' /proc/cpuinfo it does not give any information.

Is there maybe a BIOS update?

---

### Post by jdong on 2007-05-09
```

flags           : fpu vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov pat clflush dts acpi mmx fxsr sse sse2 ss ht tm pbe nx constant_tsc pni monitor <b>vmx</b> est tm2 xtpr
```
vmx is in my CPU:

```

processor       : 1
vendor_id       : GenuineIntel
cpu family      : 6
model           : 14
model name      : Genuine Intel(R) CPU           T2300  @ 1.66GHz
stepping        : 8
cpu MHz         : 1000.000
cache size      : 2048 KB

```

Are you sure you have the T2300 and not one of the modern variants of it, like the T2300E? The newer variants are cheaper but lack virtualization.

---

### Post by Markiedam on 2007-05-09
According to my cpuinfo
```

processor       : 0
vendor_id       : GenuineIntel
cpu family      : 6
model           : 14
model name      : Genuine Intel(R) CPU           T2300  @ 1.66GHz
stepping        : 8
cpu MHz         : 1000.000
cache size      : 2048 KB

```

My flags

```

fpu vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov pat clflush dts acpi mmx fxsr sse sse2 ss ht tm pbe nx constant_tsc pni monitor est tm2 xtpr

```

---

### Post by Markiedam on 2007-05-10
*update*

I just did a update of the BIOS for the laptop (Vista BIOS) and suddenly my FLAGS look like this:
```

fpu vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov pat clflush dts acpi mmx fxsr sse sse2 ss ht tm pbe nx constant_tsc pni monitor est tm2 xtpr

```
I have the EST, TM2, XTPR functions enabled now.. but still missing the VMX flag

---

### Post by gkraft on 2007-05-13
From reading the forum, it sounds like I'm not the only one having problems installing the Ubuntu into this laptop.  A friend was successfully able to install the Feisty Fawn Kubuntu into my laptop, fortunately with a partition so I still run my windows programs.

I too am unable to work my Skype from this platform.  It looks like it may take some time for this to get sorted.

I do have a couple of problems that may be easier to fix: 

1. No matter which application I open, I am not able to see the full screen on my monitor, as the content stretch beyond the screen, including in the tool bar.  It almost looks like it is permanently zoomed in.
2. On start up I get all kinds of stuff jumping up at me like Kopete (no clue what that is) and Skype (which doesn't work).  How do I stop that?  I want to decide which applications I want to use.  I also want to determine which programs display on the tool bar and the desk top.  How do I do that?

Cheers!

---

### Post by dyous87 on 2007-05-13
I was wondering if anyone was having battery trouble like me. My acer is about a year old now and all of the sudden today my battery will not hold a charge. Yesterday it was fine, the battery charged and I was able to use it without being plugged in.  I had it charging last night and when I woke up my battery applet said I had 0% left. If I unplug it for more then 4 minutes it dies. The battery just will not charge I don't know how this could just happen overnight.

ACPI gives me this output:
```

Battery 1: charging, 0%, charging at zero rate - will never fully charge.


```

---

### Post by jdong on 2007-05-13
sounds like battery death... the charging system is totally regulated by the BIOS and chipset; Linux has nothign to do with it at all.

---

### Post by dyous87 on 2007-05-13
Yes I figured so, that's terrible. I just found it odd that yesterday it was fine and it just happened all of the sudden.  Well there was a recall on my battery so hopefully i should be receiving the replacement soon.

---

### Post by Frank Golden on 2007-05-15
> **dyous87 said:**
> Yes I figured so, that's terrible. I just found it odd that yesterday it was fine and it just happened all of the sudden.  Well there was a recall on my battery so hopefully i should be receiving the replacement soon.Got my new recall battery in less than a week.

---

### Post by jdong on 2007-05-15
That's impressive, I _just_ got my fedex tracking number; going to arrive in a week's time.

---

### Post by gmc on 2007-05-16
HI Folks,

Um, I'm a little lost and in need of some suggestions. 

I'm looking to display the output of vlc on my TV. As I understand it, I need to get a DVI-D to RCA converter box (the TV on has RCA inputs).

The problem is that these boxes are very expensive, is there another way to accomplish this feat that doesn't cost $300+

Gord

---

### Post by cbudden on 2007-05-16
> **gmc said:**
> HI Folks,

Um, I'm a little lost and in need of some suggestions. 

I'm looking to display the output of vlc on my TV. As I understand it, I need to get a DVI-D to RCA converter box (the TV on has RCA inputs).

The problem is that these boxes are very expensive, is there another way to accomplish this feat that doesn't cost $300+

Gord

If your TV supports it, you can use s video to output your laptops screen to the TV.

---

### Post by gmc on 2007-05-16
> **cbudden said:**
> If your TV supports it, you can use s video to output your laptops screen to the TV.

Ok, so what I want to is get a cable with svideo connector and rca (3) on the other end?

Gord

---

### Post by Frank Golden on 2007-05-16
> **jdong said:**
> That's impressive, I _just_ got my fedex tracking number; going to arrive in a week's time.The thing is there is nothing wrong with my old battery. So I guess it doesn't go back.
That is unless they "force" the issue.

---

### Post by jdong on 2007-05-16
> **Frank Golden said:**
> The thing is there is nothing wrong with my old battery. So I guess it doesn't go back.
That is unless they "force" the issue.

Hmm... how "legal" is it to keep your own battery? Will they send collections demons after you?

---

### Post by Frank Golden on 2007-05-16
> **jdong said:**
> Hmm... how "legal" is it to keep your own battery? Will they send collections demons after you?I guess they could threaten my warranty, but I voided that by upgrading my processor to the T7200 (merom). Probably voided it by having this "nasty Linux" stuff on also.

---

### Post by cbudden on 2007-05-17
> **gmc said:**
> Ok, so what I want to is get a cable with svideo connector and rca (3) on the other end?

Gord

It depends on the config of your TV really.  Some have svideo inputs, some scart, some RCA.  Have a look at what your TV has.

---

### Post by tonyr1988 on 2007-05-17
> **gmc said:**
> Ok, so what I want to is get a cable with svideo connector and rca (3) on the other end?

Gord
Would something like [this](http://www.s-video.com/svideoaudiorca.html) work?

S-video itself is just the video cable, so you need a separate cord for the audio. I'm not sure if the placement of the S-Video and headphone jacks are close enough for that cable to work (I'm not near my laptop right now). But if they aren't, you can just get the cables seperate.

---

### Post by gmc on 2007-05-21
> **tonyr1988 said:**
> Would something like [this]("http://www.s-video.com/svideoaudiorca.html") work?

S-video itself is just the video cable, so you need a separate cord for the audio. I'm not sure if the placement of the S-Video and headphone jacks are close enough for that cable to work (I'm not near my laptop right now). But if they aren't, you can just get the cables seperate.

That's exactly what I want. However $140cnd worth of cables and crap from FutureShop (returned the next day), The Source (Radio Shack) and BestBuy either don't have such an adapter/cable or claimed that it couldn't be done! The Moral: I'm never buying anything from Future Shop again.

You're right about having to get the cables separately as the 1/8" jack cable  isn't long enough to plug in and have the s video plugged in too.

I'm going to see if I can locate that cable a little closer to home, if not, I'll order one from that site. Thanks!

Gord

Edited: No luck closer to home, so I've ordered one

---

### Post by devlunatic on 2007-05-23
hello,
i have acer aspire 1640 nwlmi, 256mb ram, 60gb, intel i686 and i am running feisty on it.
i have a problem with the leds of wireless and bluetooth buttons. they don't  seem to co-operate.\
please help.

thanks in advance!!

devlunatic

---

### Post by gmc on 2007-05-23
> **devlunatic said:**
> hello,
i have acer aspire 1640 nwlmi, 256mb ram, 60gb, intel i686 and i am running feisty on it.
i have a problem with the leds of wireless and bluetooth buttons. they don't  seem to co-operate.\
please help.

thanks in advance!!

devlunatic

Does you laptop have manual buttons to turn on/off wireless and bluetooth? If so you might try holding those buttons in the on position while turning on the laptop. I found at one point in time during Edgy's developement, I had a similar problem and told that would sort the problem.... it did :-)

Gord

---

### Post by dyous87 on 2007-05-31
Strange thing, I received my new battery from the recall center and it still will not charge. Acer has been no help I keep calling them but their customer service is the pits gah....

---

### Post by haani on 2007-06-04
hey guys does anyone know how do i get beryl workin on 7.04? i have installed ATI Driver using [THIS]("http://wiki.cchtml.com/index.php/Ubuntu_Feisty_Installation_Guide") (method 2) website and the desktop effects doest work aswell, it says "the composite extension is not available"

---

### Post by Kwunman on 2007-06-05
> **haani said:**
> hey guys does anyone know how do i get beryl workin on 7.04? 

Hey,

I found that the version of beryl in the official repo doesn't work, but i managed to find this guide. Follow all the instruction, including the disabling of some of your current repos, and then just lock the version/prevent it from upgrading all the packages you installed before re-enabling the original repos. 

Concerning the method you used to install the driver, that shouldn't make a difference.

Some of it is in Swedish, but the majority of the instructions are in English and work fine for me:
[http://ubuntu-se.org/smf/index.php?topic=8913.msg67326](http://ubuntu-se.org/smf/index.php?topic=8913.msg67326)

It works really well, and the only problem I have is that if I want to change the Emerald theme, I have to reload the window decorator.

I hope this helps,

Kwun-Man

---

### Post by gmc on 2007-06-06
Hi Folks,

Well my Svideo to 3 RCA cable arrived this morning and I'm pleased to say that it does indeed work with our beloved 5672 machines. The only problem I have is that the TV wants 640x480. Now because the LCD on the laptop is 1280x800, the image displayed on the TV allows scrolling left/right and up/down. I haven't figured out how to adjust the resolution shows on the TV and keep the maximum resolution on the laptop.

Thanks TonyR for pointing out the cable I needed to get this working. :D

Gord

---

### Post by Drife on 2007-06-07
Gord>>

It is possible to change ratio and position on the tv-output by using
ati-config --tv-geometry switch.

Works for me if I run it in a terminal on the tv screen.

When I watch movies on my TV I get some flicker in the picture some times.
I recently did a fresh install of 7.04 and the newest ati drivers. This reduced
the problem significantly but it is still there to some extent. Is someone else
experiancing this or have a solution to the problem? I haven't tried another
TV set and mine is quite old so it might just be the TV not coping with the signal.


BR
/Drife

---

### Post by gmc on 2007-06-07
Hi Drife,

> **Drife said:**
> Gord>>
It is possible to change ratio and position on the tv-output by using
ati-config --tv-geometry switch.


I did discover the --tv-geometry option after some googling and spent part of the day playing with different values. It appears that even though the you can control the viewable window (changing the size of the borders around the picture), the TV is still trying to display a 1280x800 image. When I got to work this eveneing, I was talking to a workmate about the problem and he pointed me to [this information]("http://gentoo-wiki.com/HOWTO_TV-Out#ATI-proprietary-drivers"). It appears I need to add some stanza's to my xorg.conf specifically for the TV's 640x480@60Hz and looks promising. I'm going to go at it again tomorrow when I get home and see if this solves the problem.

As for 'flickering', I don't see that at all, but occasionally I'll see a tear line scroll up the screen when the laptop's LCD is set to 1280x800, but not at all when it's set to 640x480 ; I attributed this tearing to incorrect resolution settings.

All in all, I'm very pleased with the setup and all I need to do is get the bluetooth remote that came with my Macbook working with the Acer and I'll have a nice little PVR system. :p

Thanks
Gord

---

### Post by jdong on 2007-06-07
The latest 8.37 series fglrx seems to cause a dramatic drop in 3D and XVideo performance on my machine... can anyone confirm? The version-to-version flaking nature of fglrx is really starting to get on my nerves.

---

### Post by dyous87 on 2007-06-08
Ok I don't know what's going on. I finally got my new battery from Acer. I plugged it in and charged it all night. This morning I turned on my laptop and it told be 7 minutes of battery life left. I thought maybe it was an acpi problem so I ignored it. 

Well after about 7 minutes my battery died and the computer shut down. I plugged it back in and powered it up. Now when i type in acpi into the terminal it tells me > Battery 1: charging, 0%, 960:00:00 until charged
. 

I don't know what is going on and this is becoming annoying. Could it be something damaged with my laptop because this is the third battery I've been through in about a months. 

Any one experience something similar to this?

---

### Post by Kwunman on 2007-06-12
Hey,

I've recently updated by Kernel, and for some reason Windows XP has disappeared from my Grub Boot Options. I was wondering if it would be possible for anyone to post their Windows entry from /boot/grub/menu.lst

Thanks,

Kwun-Man

Edit: Managed to sort this out relatively painlessly.

---

### Post by Kwunman on 2007-06-18
Hey Guys,

I was just wondering if anyone has suspend working yet.

when i select suspend, it seems to go in to suspend mode, but freezes when trying to get back to it's normal state. Hibernate seems to work no problem though.

I hope someone can help,

thanks,

Kwun-Man

---

### Post by Frank Golden on 2007-06-26
> **Kwunman said:**
> Hey,

I've recently updated by Kernel, and for some reason Windows XP has disappeared from my Grub Boot Options. I was wondering if it would be possible for anyone to post their Windows entry from /boot/grub/menu.lst

Thanks,

Kwun-Man

Edit: Managed to sort this out relatively painlessly.

The reason grub changes with a kernel update is the update writes a new menu.lst and drops XP from it. What I do is copy my menu.lst and place it on the desktop for a reference. I often just note the version of the new kernel then edit the old menu.lst to reflect the new kernel. I then just replace the new menu.lst with the amended old one. Not very elegant but it works.

You are aware that kernel upgrades need you to recompile your fglrx module to get full hardware 3-D from
the ATi card. See the following link for instructions.

[http://wiki.cchtml.com/index.php/Main_Page](http://wiki.cchtml.com/index.php/Main_Page)

Its really quite easy if follow the directions exactly and cut and paste the various commands.
It sucks having to do this but needed if you want full hardware acceleration.

To check whether you need to recompile fglrx module run the following commands in terminal.

```
$fglrxinfo
```

If fglrx is working the output should be the following

display: :0.0  screen: 0
OpenGL vendor string: ATI Technologies Inc.
OpenGL renderer string: MOBILITY RADEON 9700 Generic
OpenGL version string: 2.0.6286 (8.33.6)

or something like that.
If mesa you don't have hardware acceleration


```
$ glxinfo | grep render
```

The output of this command should be the following

direct rendering: Yes

Hope I have been of help.

---

### Post by Kwunman on 2007-06-26
Thanks for that explanation, will keep all that in mind next time I update my Kernel!

Kwun-Man

---

### Post by jdong on 2007-06-28
Notice where it says "BEGIN AUTOMAGIC .... ... " and "END AUTOMAGIC ... ..." in menu.lst. Place your own entries **OUTSIDE** this area, and the automated scripts won't touch your entries.

---

### Post by unz on 2007-06-29
Anyone is playing with powertop?
It is an Intel's software that gives you tips about powersaving.

[http://www.linuxpowertop.org/](http://www.linuxpowertop.org/)

It works really good, but i can't access current voltage state, i don't know if it is a bios problem or an hardware one.
I use the last bios  [the vista one]

---

### Post by stani on 2007-08-07
My sister has an acer aspire 5670. After hibernating, sound doesn't work anymore. Any tips, such as:
- a custom "/etc/default/acpi-support"
- suspend2 (any experience someone on this laptop?)

Suspending doesn't seem to work also. Does someone have a solution?

Stani

---

### Post by tonyr1988 on 2007-08-18
Has anyone gotten DVI-out to work? I've tried both my desktop and my laptop, and I can't seem to get anything out of either of them. I've been Googling (and searching here), but so far haven't found anything helping me at all. I've never messed with DVI before, so I'm kinda lost to it all. :)

---

### Post by jdong on 2007-08-18
> **unz said:**
> Anyone is playing with powertop?
It is an Intel's software that gives you tips about powersaving.

[http://www.linuxpowertop.org/](http://www.linuxpowertop.org/)

It works really good, but i can't access current voltage state, i don't know if it is a bios problem or an hardware one.
I use the last bios  [the vista one]

Powertop works on Gutsy with the Vista BIOS. The results, however, are a bit depressing. It seems like our touchpad system (i8042.c) generates a lot of interrupts.

---

### Post by jdong on 2007-08-31
[ftp://ftp.acer-euro.com/notebook/aspire_5670/bios](ftp://ftp.acer-euro.com/notebook/aspire_5670/bios)

New BIOS 3239 posted. I'm not gonna try it yet; have too much stuff to do to worry about upgrading a working BIOS.

---

### Post by Frank Golden on 2007-09-12
Hi All, For the adventursome out there I just installed the new ATi 8.41.7 drivers to Feisty.
Used the method 2 instructions from

[http://wiki.cchtml.com/index.php/Ubuntu_Feisty_Installation_Guide](http://wiki.cchtml.com/index.php/Ubuntu_Feisty_Installation_Guide) 

I just changed the commands from the old 8.40.4 driver to to the new 8.41.7 driver.
Worked like a charm. Got the new driver here.

[http://rage3d.com/board/showthread.php?t=33901923](http://rage3d.com/board/showthread.php?t=33901923)

I seem to get faster frame rates and smoother screensaver action. I haven't tried reactivating composite (the new driver is supposed to support composite). 

Best yet GoogleEarth works! As many of you know the 8.40.4 driver broke GoogleEarth.

I haven't seen any ill effects yet.

Because I made a partimage  backup of my Feisty install I felt safe doing this. Thank goodness for partimage.

The above wiki does not outline the install of the new driver and probably won't for awhile as the driver just became available today, Sept 12, 2007. 

I have made a text file copy of the wiki instructions with the appropriate changes for anyone interested. PM me for a copy of it. Will now install my backup image of Ubuntu 6.06.1 LTS and attempt to install there using the same method, wish me luck.

Will try to figure out how to install on PCLinuxOS 2007 also.

---

### Post by jdong on 2007-09-12
I'm gonna give the new fglrx a shot tonight or tommorow; it still does **not** support composite+DRI or texture_from_pixmap -- that is slated for the next release in a month.

---

### Post by Frank Golden on 2007-09-12
error, mods please remove.

---

### Post by Frank Golden on 2007-09-12
error Mods please remove.

---

### Post by Frank Golden on 2007-09-12
UPDATE: tried method on Ubuntu 6.06.1 LTS worked great. Have modified instructions for Ubuntu 6.06.1 LTS available also. Checked framerates before and after before for
```
glxgears
```
I got approx. 1500 FPS after I got approx. 2165 FPS. For ```
fgl_glxgears
```
before I got approx. 366 FPS and after I got approx. 418 FPS. Although we shouldn't consider these applets to be benchmarks I think the increase in framerates is significant.
I did not compare framerates in Feisty.

---

### Post by jdong on 2007-09-12
I've got some 3D games on my system, and insane Compiz profiles that I can test out.... heck even full-screen 1900x1200-resolution H.264 diagonally rips currently due to poor GL performance.  I'll test the practical nature of this, and also whether this makes powermode 1 more appealing (i.e. not unbearably slow)

---

### Post by Frank Golden on 2007-09-12
Hi Jdong, Just got done testing Feisty results were similar. Looking forward to some real world benchmarks. stuff like this is what makes Linux fun.

---

### Post by jdong on 2007-09-12
Yeah I'm interested what's gonna happen as the specs for this chip have been openly released to Xorg devs too :)

This might be a historic moment in FOSS graphics history.

---

### Post by Frank Golden on 2007-09-12
Reporting that Edgy specific modified instruction work for Edgy also. Similar FPS results. That about does it for Ubuntu as far as I'm concerned.:)

---

### Post by KaYnemO on 2007-09-22
ubuntu The Feisty Fawn works awesome on my aspire 5670 - mind you I went through lots of distros and ubuntu beats the rest in the way it found all hardware ECXCEPT for touchpad (kinda sucks, but I will fix it later it is just a bit buggy). Anyhow it works great - webcam., WiFi, CardReader, ATI (shucks - never'll buy another ATI card) etc. good luck!

---

### Post by jdong on 2007-09-22
Let us know if there's any specific problems with your touchpad -- I've posted my xorg.conf in this thread before and that synaptic configuration section works beautifully for me.

---

### Post by KaYnemO on 2007-09-23
> **jdong said:**
> Let us know if there's any specific problems with your touchpad -- I've posted my xorg.conf in this thread before and that synaptic configuration section works beautifully for me.

well it's really strange: here is what my xorg.conf looks like (i googled and got this to put in)
> Section "InputDevice"
          Identifier "Synaptics Touchpad"
          Driver "synaptics"
          Option "SendCoreEvents"          "True"
          Option "Protocol"                "auto-dev"
          Option "Device"                  "/dev/psaux"
          Option "SHMConfig"               "True"
          Option "LeftEdge"                "100"
          Option "RightEdge"               "1100"
          Option "TopEdge"                 "50"
          Option "BottomEdge"              "300"
          Option "FingerLow"               "30"
          Option "FingerHigh"              "40"
          Option "MaxTapMove"              "100"
          Option "TapButton1"              "1"
          Option "TapButton2"              "3"
          Option "TapButton3"              "2"
          Option "MinSpeed"                "0.15"
          Option "MaxSpeed"                "0.90"
          Option "AccelFactor"             "0.10"
          Option "VertScrollDelta"         "25"
          Option "HorizScrollDelta"        "30"
EndSection

 as you can see SHMConfig is set to "True" but when I start gsynpatics it shows:

> GSynaptics couldn't initialize.
You have to set 'SHMConfig' 'true' in xorg.conf or XF86Config to use GSynaptics

currently - the scrolling buttons don't scroll, the down button just opens the dialog window like the right mouse button would. and there is no drag when double touch and hold. :(

any advice?

thnx

---

### Post by busman on 2007-09-24
I have an Acer Aspire 5672WLMI, that the hard drive died in.  I had to replace it, and when I reinstalled Ubuntu, it can't seem to find my internet.  The light blinks while it searches for it, but never finds it.  Any suggestions how to solve this problem so I can get it back online?  Thank you.

---

### Post by tonyr1988 on 2007-09-25
I've got 2 questions that have absolutely nothing to do with Linux:

1) I've had this laptop for a while, and I'm sure some stuff has fallen under the keys. I'm not having any real problems now, but I want to make sure that I keep everything as clean as possible for the future. I know in a desktop keyboard you can just pop the keys off with a screwdriver and throw them back on - is it that easy on our laptop? I'm assuming it is, but I really don't want to take the chance. Replacing the entire laptop is a tad different than buying a new keyboard. :)

2) The top lid of mine is getting kind of dirty. I don't mean the screen - I've got a cleaner for that. But the actual lid. What should I use for it? I'm assuming everything is sealed up tight, but just wanna make sure. If I use a sponge, water, and some cleaner, will it be safe?

Thanks,
Tony

---

### Post by tonyr1988 on 2007-09-25
Are you trying to connect to a wired or wireless connection?

I had problems with my wireless connection one time when I installed using the Alternate CD. Did you use the LiveCD?

---

### Post by jdong on 2007-09-25
> **tonyr1988 said:**
> I've got 2 questions that have absolutely nothing to do with Linux:

1) I've had this laptop for a while, and I'm sure some stuff has fallen under the keys. I'm not having any real problems now, but I want to make sure that I keep everything as clean as possible for the future. I know in a desktop keyboard you can just pop the keys off with a screwdriver and throw them back on - is it that easy on our laptop? I'm assuming it is, but I really don't want to take the chance. Replacing the entire laptop is a tad different than buying a new keyboard. :)


I do not recommend popping off the keys on the keyboard. It is a typical laptop keyboard supported by flimsy plastic stands, and improper removal techniques can lead to those joints failing, ruining the key. Best advice is a bit of compressed air, or if you can remove the entire keyboard, running it under water and letting it dry for a day or two before reinstalling it is generally safe too.

> 

2) The top lid of mine is getting kind of dirty. I don't mean the screen - I've got a cleaner for that. But the actual lid. What should I use for it? I'm assuming everything is sealed up tight, but just wanna make sure. If I use a sponge, water, and some cleaner, will it be safe?

Thanks,
Tony

Yes, you can use a sponge with water. Turn the laptop off first. Don't use abrasive cleaners or solvents and don't use a rough sponge either.

---

### Post by KaYnemO on 2007-09-26
hey jdong!

I have downloaded your version of the xorg.conf and now the touchpad works yaupeeeee!!!! Thanks, man. Now EVERYTHING works under Feisty Fawn. This is cool.

---

### Post by jdong on 2007-10-12
[https://bugs.edge.launchpad.net/ubuntu/+source/linux-source-2.6.22/+bug/121653](https://bugs.edge.launchpad.net/ubuntu/+source/linux-source-2.6.22/+bug/121653)

WARNING to Gutsy adopters: Suspend to RAM will not work in Gutsy. There is an interaction between fglrx and the new SLUB allocator in the kernel.

---

### Post by cbudden on 2007-10-12
So that is why it doesn't work.  Also I haven't been able to get hibernate to work with uswsusp.

In other news, our card readers now work with Sony memory sticks!

---

### Post by tonyr1988 on 2007-10-18
> **jdong said:**
> [https://bugs.edge.launchpad.net/ubuntu/+source/linux-source-2.6.22/+bug/121653](https://bugs.edge.launchpad.net/ubuntu/+source/linux-source-2.6.22/+bug/121653)

WARNING to Gutsy adopters: Suspend to RAM will not work in Gutsy. There is an interaction between fglrx and the new SLUB allocator in the kernel.
1) Is that the only problem (so far) you've seen in Gutsy with the 5672?

2) Does Hibernate still work, or is both Suspend and Hibernate messed up?

3) Did you upgrade or do a fresh install?

I'm so happy that you use this laptop. It makes everything so much easier. Hip hip horray for jdong! :P

---

### Post by jdong on 2007-10-18
> **tonyr1988 said:**
> 1) Is that the only problem (so far) you've seen in Gutsy with the 5672?

Yes -- Gutsy works excellent with this laptop out-of-the-box.

> 
2) Does Hibernate still work, or is both Suspend and Hibernate messed up?


I am unsure; to be honest I haven't tried for months.

> 
3) Did you upgrade or do a fresh install?

I've upgraded ever since Dapper prerelease, following official procedures (using the update-manager) and it has succeeded all the way, except for one upgrade there were two overwritten-file type conflicts that were resolved by hand with relative ease.

---

### Post by Kwunman on 2007-10-20
Hey,

I was just wondering if anyone has got the webcam working in Gusty yet? I've installed the required packages, but on opening camorama I get a box saying that it "could not connect to device"

Any ideas?

Kwunman

---

### Post by tonyr1988 on 2007-10-21
I had the webcam/Camorama installed and working in Feisty, and it still works in Gutsy. Did you do a fresh install or an upgrade?

---

### Post by cbudden on 2007-10-21
I had this problem, where my user wasn't in the video group (in fact there wasn't even a video group).  Just add the video group,then add your user to it and it should work.

---

### Post by Kwunman on 2007-10-21
Strange, my user is a member of the group "video", but still the same thing.

The full error that appears in the pop up is as follows:

"Could not connect to video device (/dev/video0).
Please check connection"

And this is on a fresh install of gusty.

---

### Post by cbudden on 2007-10-21
What do you get from lsusb ?

---

### Post by Kwunman on 2007-10-21
on typing lsusb i get:

Bus 005 Device 001: ID 0000:0000  
Bus 003 Device 002: ID 0a5c:2101 Broadcom Corp. 
Bus 003 Device 001: ID 0000:0000  
Bus 004 Device 001: ID 0000:0000  
Bus 002 Device 001: ID 0000:0000  
Bus 001 Device 001: ID 0000:0000

---

### Post by Kwunman on 2007-10-23
Anyway, moving aside from my webcam issue...

I have some great news. ATI fglrx driver version 8.42.3 has been released! And you know what that means -  AIGLX support!!!

I've installed it, and so far, i couldn't be happier!

You can download it from here:

[http://www.phoronix.com/scan.php?page=news_item&px=NjE0Ng](http://www.phoronix.com/scan.php?page=news_item&px=NjE0Ng)

and then follow the normal install instructions for the ati driver ([http://wiki.cchtml.com/index.php/Ubuntu_Gutsy_Installation_Guide](http://wiki.cchtml.com/index.php/Ubuntu_Gutsy_Installation_Guide)), just changing the version number here and there.

Don't forget to add "fglrx" to the compiz whitelist:

gksudo gedit /usr/bin/compiz

and then:

# Driver whitelist
WHITELIST="nvidia intel ati radeon i810"

On restarting my laptop, Compiz working by default! It's great!

Enjoy...

Kwun-Man

---

### Post by jdong on 2007-10-23
Yeah I saw the story -- I'll have to try this when I get home today!

---

### Post by jdong on 2007-10-23
Ok just installed 8.42, performance is decent, Compiz is working (a bit laggy on some plugins, but whatever)


One major problem is I get massive video flickering under xvideo in mplayer. Anyone else experience this?

---

### Post by Kwunman on 2007-10-23
> **jdong said:**
> One major problem is I get massive video flickering under xvideo in mplayer. Anyone else experience this?

hmm, i get this too, in whatever video app i use, vlc, totem, etc.

any ideas?

---

### Post by jdong on 2007-10-23
Temporary workaround, when compiz's unidirect on full screen setting is enabled (now default), fullscreen videos, games, etc all work at native speeds :)

I do not have a solution for windowed 3D stuff flickering yet.

---

### Post by cbudden on 2007-10-23
For me, fullscreen in VLC, Mplayer and totem work fine, but i get the weird diagonal flickery line thing in non full screen .

---

### Post by jdong on 2007-10-23
I am guessing AIGLX bug in fglrx -- if you move around a window with a flickering video the flickering remains in the same spot, empty window border moves with you. Maybe that can be worked around with one of those indirect binding or strict binding compiz flags.

---

### Post by macvr on 2007-10-24
> **Kwunman said:**
> Hey,

I was just wondering if anyone has got the webcam working in Gusty yet? I've installed the required packages, but on opening camorama I get a box saying that it "could not connect to device"

Any ideas?

Kwunman
heard tht this softwore works -
 [http://mxhaard.free.fr/download.html](http://mxhaard.free.fr/download.html) 
i havent tried it out yet, (waitin for d ATI probs to get resolved to switch my OS) but found tht link in another forum.

---

### Post by plaz42 on 2007-10-24
I'm having the same flickering problems with most videos and GL programs.  Building a patched mplayer and using the compiz video plugin did fix it for all mplayer windows, not just fullscreen, though.
[MPlayer patch is available here.]("http://smspillaz.wordpress.com/2007/10/18/unlocking-the-full-video-potential-of-your-video-card/")

---

### Post by Kwunman on 2007-10-24
> **macvr said:**
> heard tht this softwore works -
 [http://mxhaard.free.fr/download.html](http://mxhaard.free.fr/download.html) 
i havent tried it out yet, (waitin for d ATI probs to get resolved to switch my OS) but found tht link in another forum.

Yeah, tried that, it was all working in feisty, i found that even the packages from the official repos worked for it.

And concerning the Video problem, i find that it gets worse if i do anything requires more graphics power, i.e. when wobbly windows is being used at the same time, or even when i place my mouse over the close button, which flashes.

hmm...

:confused:

---

### Post by macvr on 2007-10-25
hi guys,
i'm thinkin of dual bootin UBUNTU n XP which is pre-installed in my 5672WLMi. i'm a total nOOb!:confused:
i'd lik to know how to partition my harddrive-XP is in my C drive,,,, i wan 2 empty my D Drive(54GB) n install Ubuntu in D:
      
i'd lik 2 know d ideal config for this :-k
1)could some1 tel me how much GB 2 use for root,swap,home?all as ext3?
2) is it possible to do this when i choose manual partitioning or would ubuntu do this EFFICIENTLY by itself on D once it is empty?
3)will i b able 2 view d UBUNTU files wen i boot from XP?
4)does any1 know wen ATI wil release new updates for its drivers?:-?:-?

thanx in advance guys:KS

---

### Post by jdong on 2007-10-25
Please rewrite your post using full English words so we can understand what you are asking.

---

### Post by macvr on 2007-10-25
hi guys,
i'm thinking of installing UBUNTU & dual booting UBUNTU with XP(which is pre-installed) in my [COLOR="Red"]5672WLMi[/COLOR].
i'm a total beginner!
i'd like to know how to partition my hard drive.i have single physical hard drive partioned as C,D Drives.
XP is in my C drive, i plan to empty my D Drive(54GB) & install Ubuntu in D Drive

i'd like to know the ideal way to configure this
1)could someone tell me how much GB to use for root,swap,home partitions(i have 2GB DDR2)?should all three be formated as ext3?
2) is it possible to install UBUNTU only on D drive when i choose manual partitioning during installation or would UBUNTU do this installation EFFICIENTLY(ONLY on D Drive)during automatic partitioning(when D drive is empty)?

3)does anyone know when ATI will release updates for its drivers(heard there are problems with the 3D Desktop graphics,wanna change to  mainly for GUI)?

4)after installation,when i boot from XP will i be able to view the files created in UBUNTU(as they will be created on ext3 partition) ?

thanks in advance guys

[COLOR="Red"] I'V ASKED THESE QUESTIONS HERE SINCE I THOUGHT THAT MOST OF U GUYS HAVE ACER ASPIRE 5672WLMi, I COULD GET A FEEDBACK FROM U & PROBABLY U WOULD SHARE YOUR CONFIGURATION [/COLOR]

---

### Post by DreamVidz on 2007-10-26
i have exatly the same laptop and i'm a totaly new beginner with Linux 
also dual booting UBUNTU with XP
i instalt ubuntu 7.10 oem  but some friends told me to try mandriva 2008 
the 3d isn't working...
guys i don't know 
i don't wont any more microso.... 
it's enough
i saw what ubuntu can do on a laptop ...nice
can anyone explain me how to instal a driver ,where to find or how this tweek things work?
is there maybe any Turtorial like linux for dummies?
i would like so much to learn more about linux and  specialy ubuntu
thanks in advance for any help:confused:
the turtorial can be also in german or greek language..

---

### Post by tonyr1988 on 2007-10-30
This is kind of a long story, so I'll try and condense it:

-In class today, I shut down my laptop and immediately closed the lid. I realized later that it may have messed it up since it would try to Suspend and Shut Down at the same time (maybe?)

-The next time I boot it, it won't boot. It gets to 3 orange bars on the startup screen and freezes.

-I tried booting in recovery mode. It spits out tons of errors, but they're going too fast for me to read what they're saying. However, it looks like it's something with my camera drivers.

-The only thing that kind of works is booting with an older kernel, but some things are messed up and it's generally slow.

Is there any way to:

-See what the error message was when booting from the newer kernel from within the older kernel?

-Completely uninstall the webcam drivers (I had installed them in Feisty and kept them during the upgrade. I don't remember exactly what I did, but I believed I followed a guide in this thread)?

-Anything else? :)

P.S. Old kernel (that "works") = 2.6.20-16-generic, New kernel (completely busted) = 2.6.22-14-generic

P.P.S. I completely removed spca5xx-source and rebooted, but nothing changed.

P.P.P.S. Well, after changing absolutely nothing, I restarted in recovery mode and it dumped me to the root command line with no problem. I did "exit" (nothing else), and it took me to GDM with no problem. I logged in, and everything was fine. I restarted, chose non-recovery "new kernel," and everything works fine. The kernel baffles me, but I'm happy it's working again. :)

---

### Post by rodri83 on 2007-11-08
Hi,

I have an Acer Aspire 5672. Recently I've installed ubuntu 7.10 on it. I'm trying to configure it (specially power configuration). With fresh install and compiz, battery last about 1'30h. In windows and mandriva, battery last about 2,30h-3h. What can I tweak? Thanks in advance.

PD: I found some tips/scripts in the thread, but I'think that are for older versions of ubuntu

---

### Post by jdong on 2007-11-08
You are missing the aticonfig tweaks, and the ones posted here before still apply for Gutsy.

---

### Post by rodri83 on 2007-11-14
Thanks jdong. I will try it on weekend

---

### Post by cbudden on 2007-11-17
Has anyone managed to get hibernate or, dare i say it, suspend working under gutsy?

---

### Post by tonyr1988 on 2007-11-18
For me, Hibernate works just fine out-of-the-box. I haven't tried Suspend, though. Are you having problems, or are you just asking?

---

### Post by cbudden on 2007-11-19
Yea I am having problems, it doesn't work!  I've  got uswsusp installed, and it gets to snapshotting system, and then just hangs there.  I've got fglrx installed and hibernate worked in feisty.

Any ideas?

---

### Post by DreamVidz on 2007-11-19
> **DreamVidz said:**
> i have exatly the same laptop and i'm a totaly new beginner with Linux 
also dual booting UBUNTU with XP
i instalt ubuntu 7.10 oem  but some friends told me to try mandriva 2008 
the 3d isn't working...
guys i don't know 
i don't wont any more microso.... 
it's enough
i saw what ubuntu can do on a laptop ...nice
can anyone explain me how to instal a driver ,where to find or how this tweek things work?
is there maybe any Turtorial like linux for dummies?
i would like so much to learn more about linux and  specialy ubuntu
thanks in advance for any help:confused:
the turtorial can be also in german or greek language..

sofare nobody that can help me???i can't conect to the internet with my linksys w- fi

---

### Post by cbudden on 2007-12-25
Hey there.

Last week I installed the new ATI drivers (7.12), and suspend worked! what a good xmas pressie.

However, after a reboot or two it decided to stop working again.  This is not good....

Anyone tried them and had the same problem?  It now goes down, the 2 first lights near the power button flash (num lock and HDD light i think) flash but a flashing cursor stays on the screen and it never turns off.

Same happens w/ hibernate

Merry Christmas to all

Chris

---

### Post by giostau on 2008-01-03
hi guys,

i'm using gutsy and i was wondering if anyone has got the multimedia keys (play/pause, next, previus) to work....
the volume up/down buttons work fine, but it would be great to have the rest of the keys to work globally with amarok or movie player....


thanks!!!

---

### Post by Helios1276 on 2008-03-14
hey guys, is this thread still warm??:confused:

Im a total newcomer to linux and just installed the latest gutsy on my 5672 wlmi, has anyone got the empathy to give me a walkthrough on getting my wireless and ati x1400 up and running??:) I've read ALOT here but with all the posts and my limited knowledge im lost!

---

### Post by Kwunman on 2008-03-14
Hey,

Basically, the easiest way to get you x1400 working fully is to follow the instructions at:

[URL="http://wiki.cchtml.com/index.php/Ubuntu_Gutsy_Installation_Guide"]
http://wiki.cchtml.com/index.php/Ubuntu_Gutsy_Installation_Guide[/URL]

There are still a few issues with AIGLX and compiz, but i haven't checked in a while, so these may be fixed.

If you encounter any problems, just post back here and we'll see what we can do.

Kwun-Man.

---

### Post by Helios1276 on 2008-03-14
Ok, before I saw your post I tried to turn on the restricted drivers for the card and ended up  with the window just hanging but everything else working. I then tried to restart and couldnt get Ubuntu to load up , just a black screen and nothing happening. I booted from the live cd wich worked , then I found your post and followed the pre installation and then enabling the card worked..it just needed a restart, which i figured was no use in the live cd so i decided to install Ubuntu again which worked but upon loading it up i ended in the same black screen again with no Ubuntu??

---

### Post by Kwunman on 2008-03-14
> **Helios1276 said:**
> i decided to install Ubuntu again which worked but upon loading it up i ended in the same black screen again with no Ubuntu??

Hmm, Did you do a complete reinstall, as in reformatting the hard drive it was installed on, etc, otherwise it may have kept some of the configuration files from before.

Also, I think that if you make any changes on the live cd, and then reinstall, it keeps those changes through to the installed version on your computer.

---

### Post by Helios1276 on 2008-03-14
No I just hit install as a panic reaction lol, how do you go about reformatting and then installing? thanks for all your help so far by the way!

---

### Post by Kwunman on 2008-03-14
Hmm, usually it automatically formats the hard drive, but maybe not if Ubuntu is already installed. 
Basically, during the install process you will come to a screen with the heading "Prepare Disk Space", if the guided option mentions anything about using the entire disk, formatting everything, etc, use that, if not, you will need to go through the manual option. Here, try and work out how to Format everything, it should be pretty simple, but this is providing you don't have windows or anything else on the hard drive, otherwise, try and find a guide.

Also, make sure you haven't changed any settings at all whilst using the live cd.

Another option is to, whilst using the live cd, open gparted (i think that's what's available on the livecd), locate your hard drive, and then format it before starting the install process. A quick search of google should give you a guide if you can't figure it out.

Let me know if it's still not working.

---

### Post by Helios1276 on 2008-03-14
ok , followed your instructions, format and reinstall worked great and I got my resolution up after enabling the restricted drivers but I still cant get 3d effects or start figuring out how compiz works.When I select higher desktop effects I get "The Composite Extension is not available"

---

### Post by Kwunman on 2008-03-14
Have you added "fglrx" to the compiz whitelist?

---

### Post by Helios1276 on 2008-03-14
No not yet , I looked at that option but having done nothing (ever) with the terminal I backed out lol is it pretty simple ya?

---

### Post by Kwunman on 2008-03-14
True, the terminal can be a little scary at first, but if you follow the instructions on that link i gave you earlier, it should be no problem.

And yeah, it is essential, Compiz etc wont work until fglrx is white listed.

---

### Post by Helios1276 on 2008-03-14
alrightey, I guess it's time I just bloody did it lol I moved to linux for a reason:)
Here goes nothing!

---

### Post by Helios1276 on 2008-03-14
3D desktop effects

The new ATI drivers use AIGLX so there is not need to install XGL that older drivers (< 8.40) required.

Remove this section from to the /etc/X11/xorg.conf file. The new xorg server enables "Composite" by default.

# Section "Extensions"
#        Option  "Composite" "0"
# EndSection
(Im unsure how I actually go about this, I open the terminal and type : /etc/x11/xorg.conf..and then delete the other piece from it?)..it wont seem to find the file
Compiz does not know about the fglrx driver. You can either skip the checks

mkdir -p ~/.config/compiz && echo SKIP_CHECKS=yes >> ~/.config/compiz/compiz-manager

or add it to the compiz white list, and clear the blacklist pci Ids variable *Recommended*

sudo gedit /usr/bin/compiz
( this worked)
# Driver whitelist
WHITELIST="fglrx nvidia intel ati radeon i810"
(what to do here?)
# blacklist based on the pci ids 
# BLACKLIST_PCIIDS="$T"
BLACKLIST_PCIIDS=""
(and here?)

You might have to modify the path for line 30 and 31

   COMPIZ_BIN_PATH="/usr/bin/" # For window decorators and compiz
   PLUGIN_PATH="/usr/lib/compiz/"

The COMPIZ_NAME on line 35 should also be modified accordingly

   COMPIZ_NAME="compiz.real" # Final name for compiz (compiz.real)
( I make the original look like the above?) 

After the necessary configurations, just restart X and enjoy the cool effects. 
(whats x?)

Im sur ethis is frustrating for those who know what they are doing but like i've said before im am a complete beginner and afraid of fracking the whole thing up

---

### Post by Helios1276 on 2008-03-14
ok , for the first part, I typed sudo gedit /etc/x11/xorg.conf, put in my password and it opened a new file saying loading but nothing loaded ..I just had a blank page

---

### Post by Kwunman on 2008-03-14
Ok,

to edit the contents of a file, in the terminal you will need to type:

[INDENT]sudo gedit[/INDENT]

following that you put the file name, so what you would have to do is:

[INDENT]sudo gedit /etc/X11/xorg.conf[/INDENT]

Then you delete the following lines from that file:

# Section "Extensions"
# Option "Composite" "0"
# EndSection


Next, add fglrx to the white list. If fglrx is listed after "WHITELIST" you don't do anything, if it isn't make sure that it is added so that it looks like this:

[INDENT]sudo gedit /usr/bin/compiz[/INDENT]

# Driver whitelist
WHITELIST="fglrx nvidia intel ati radeon i810"
(what to do here?)
# blacklist based on the pci ids
# BLACKLIST_PCIIDS="$T"
BLACKLIST_PCIIDS=""


For all the other instructions, just make the original look like the new lines:


You might have to modify the path for line 30 and 31

COMPIZ_BIN_PATH="/usr/bin/" # For window decorators and compiz
PLUGIN_PATH="/usr/lib/compiz/"

The COMPIZ_NAME on line 35 should also be modified accordingly

COMPIZ_NAME="compiz.real" # Final name for compiz (compiz.real)


And concerning this:

After the necessary configurations, just restart X and enjoy the cool effects.

In short, X is the name for the windows manager, and everything you see, so the least problematic way is probably just to restart the laptop.


Hope this helps.

---

### Post by Helios1276 on 2008-03-14
ok I deleted the first bit (as in with the delete key and saved out of it ). Then for the /usr/bin/compiz part I have made the changes and cant get the desktop effects under'Apperance' still. Heres a copy of what i've  done maybe you can see what i dont 

COMPIZ_BIN_PATH="/usr/bin/" # For window decorators and compiz
PLUGIN_PATH="/usr/lib/compiz/" 
GLXINFO="/usr/bin/glxinfo"
KWIN="/usr/bin/kwin"
METACITY="/usr/bin/metacity"
COMPIZ_NAME="compiz.real" # Final name for compiz (compiz.real) 

# For Xgl LD_PRELOAD
LIBGL_NVIDIA="/usr/lib/nvidia/libGL.so.1.2.xlibmesa"
LIBGL_FGLRX="/usr/lib/fglrx/libGL.so.1.2.xlibmesa"

# Minimum amount of memory (in kilo bytes) that nVidia cards need
# to be allowed to start
# Set to 262144 to require 256MB
NVIDIA_MEMORY="65536" # 64MB
NVIDIA_SETTINGS="nvidia-settings" # Assume it's in the path by default

# For detecting what driver is in use, the + is for one or more /'s
XORG_DRIVER_PATH="/usr/lib/xorg/modules/drivers/+"

FALLBACKWM="${METACITY}"
FALLBACKWM_OPTIONS="--replace $@"

# Driver whitelist
WHITELIST="fglrx nvidia intel ati radeon i810"

# blacklist based on the pci ids 
# See [http://wiki.compiz-fusion.org/Hardware/Blacklist](http://wiki.compiz-fusion.org/Hardware/Blacklist) for details
T="   1002:5954 1002:5854 1002:5955" # ati rs480
T="$T 1002:4153" # ATI Rv350
T="$T 8086:2982 8086:2992 8086:29a2 8086:2a02 8086:2a12"  # intel 965
T="$T 8086:2972" # i965 (x3000)
T="$T 1002:3152 1002:3150 1002:5462 1002:5653 " # ati X300 X600,X600 X700 
BLACKLIST_PCIIDS="$T"
BLACKLIST_PCIIDS=""
unset T

COMPIZ_OPTIONS="--ignore-desktop-hints --replace"
COMPIZ_PLUGINS=""
ENV=""

# Use emerald by default if it exist
USE_EMERALD="yes"

# No indirect by default
INDIRECT="no"

# Set to yes to enable verbose
VERBOSE="yes"

# Echos the arguments if verbose
verbose()

---

### Post by Kwunman on 2008-03-14
Hmm. Ok, firstly, it will only work after a reboot, which I'm sure you've done.

What do you get when you type the following in to a terminal?

[INDENT]fglrxinfo[/INDENT]

---

### Post by Helios1276 on 2008-03-14
hey man , ya i rebooted afterwards.

shane@Acer:~$ fglrxinfo
display: :0.0  screen: 0
OpenGL vendor string: ATI Technologies Inc.
OpenGL renderer string: ATI Mobility Radeon X1400
OpenGL version string: 2.0.6473 (8.37.6)

---

### Post by Kwunman on 2008-03-14
Strange, it should be working then.

Try following this guide, hopefully that should do the trick.

[http://ubuntuforums.org/showthread.php?t=593348]("http://ubuntuforums.org/showthread.php?t=593348")

---

### Post by Helios1276 on 2008-03-14
I dont know if i'd be able to follow that guide..it looks very noob unfriendly! just a hunch but when i deleted the part at the start should i have put the #'s in or deleted them with DELETE..after that i cant see what i've done wrong

---

### Post by Helios1276 on 2008-03-14
f it still does not work, locate /etc/xdg/compiz/compiz-manager.ubuntu [this line may instead be in /etc/xdg/compiz/compiz-manager] and see if it contains an infinite loop in it. If it does, comment out the line that causes the infinite loop.

# . /etc/xdg/compiz/compiz-manager.ubuntu
(not sure what im looking for here but i got this below)

# Ubuntu specifc compiz-manager configuration file
# goes into /etc/xdg/compiz/compiz-manager
# works with git://anongit.compiz-fusion.org/fusion/misc/compiz-manager
COMPIZ_BIN_PATH="/usr/bin/" 
PLUGIN_PATH="/usr/lib/compiz/" 
COMPIZ_NAME="compiz.real"

---

### Post by Kwunman on 2008-03-14
Ok, just realised the problem.

The default driver that you've installed (8.37.6), doesn't support AIGLX.

To get Compiz working you need to install the drivers using method 2 from the original link i gave you. It may look a little daunting, but try sticking to it, as it's the only way you'll get the special effects working.

---

### Post by Helios1276 on 2008-03-14
ok , do i need to undo what i've done so far?

---

### Post by Kwunman on 2008-03-14
um, I don't think so, it's just installing a different driver. 
Hopefully you can leave all the whitelist changing stuff, and it saves you from doing it later.

---

### Post by Helios1276 on 2008-03-14
haha (laugh of despair) I think ill have a drink for myself and try again in the morning, thanks for all the help , you have been at this as long as me almost :popcorn:

---

### Post by Re1lly on 2008-04-24
Is this thread still on? i was wondering if all the problems that the last ubuntu releases had with ATI cards are still there. I can't beleive all the problems i went through when i tried to install Compiz the first time..anyone have news on Hardy?

---

### Post by jdong on 2008-04-24
Compiz roughly works out of the box for me.

---

### Post by Frank Golden on 2008-04-24
Just installed final Hardy on my 5672 and no wifi. Any clues folks.

---

### Post by tonyr1988 on 2008-04-24
> **Frank Golden said:**
> Just installed final Hardy on my 5672 and no wifi. Any clues folks.

Oh no - I just finished downloading the iso and was going to do a fresh install (I had a lot of problems with Gutsy upgrade from Feisty, but decided to wait it out until the LTS)

Did you happen to use the Alternate Install CD? I know we used to have problems with WiFi when installed via the alternative. If not, did WiFi work during the live session, or did you skip testing?

P.S. W00h00! First post on page 100!

---

### Post by Frank Golden on 2008-04-25
Used the desktop CD not the alternate. From what I can see on the internet
it is a bug related to the 2.6.24-16 kernel. Sloppy! Wi-Fi is important and a bug like this is a SHOWSTOPPER!!!
To the devs a quick fix would be nice.

---

### Post by jdong on 2008-04-25
This is likely due to the switch from the closed-source ipw3945 driver to the open-source iwl3945 driver. Currently it seems to work for me connecting to MIT wifi on stock Hardy

> 
207121.582968] eth1: Initial auth_alg=0
[207121.582977] eth1: authenticate with AP 00:20:a6:51:cd:99
[207121.583761] eth1: Initial auth_alg=0
[207121.583773] eth1: authenticate with AP 00:20:a6:51:cd:99
[207121.585793] eth1: RX authentication from 00:20:a6:51:cd:99 (alg=0 transaction=2 status=0)
[207121.585800] eth1: authenticated
[207121.585805] eth1: associate with AP 00:20:a6:51:cd:99
[207121.588295] eth1: RX AssocResp from 00:20:a6:51:cd:99 (capab=0x421 status=0 aid=24)


---

### Post by cbudden on 2008-04-25
My Wifi does work, but the indicator light on the front of my machine does not.

---

### Post by poohlo on 2008-04-25
hi to all. i upgraded mi Acer TM 2413 and as i undestood my wifi is came down. no lights, and no nothing i can't connect to my router :( i tried to do the same i've done on 7.10 with mcb43fwcu&#1077;&#1077; but nothing :( if someone will solve thos please post.

---

### Post by jdong on 2008-04-25
> **cbudden said:**
> My Wifi does work, but the indicator light on the front of my machine does not.

Light doesn't work for me either -- apparently the LED patch was unstable so it was backed out?

---

### Post by Kwunman on 2008-04-25
Hey, Just installed Hardy.

Like most of you, Wifi is working great, but no LED, but to be honest, i can live without that.

Installed the latest ATI drivers and am pleased to say that everything is working fine in respect to that.

Also, for the first time ever - Suspend is working properly! I've yet to try hibernate and various other things, but so far I'm happy with this release. :)

---

### Post by Frank Golden on 2008-04-25
Found this fix after some googling. Apparently you were right about the change from ipw to iwl driver. This fix worked for me.

[http://linuxtechie.wordpress.com/2008/04/24/making-intel-wireless-3945abg-work-better-on-ubuntu-hardy/](http://linuxtechie.wordpress.com/2008/04/24/making-intel-wireless-3945abg-work-better-on-ubuntu-hardy/)

GoogleEarth is choppy with advanced desktop effects enabled.

---

### Post by jdong on 2008-04-25
IMO the move to the IWL driver is the right choice considering even a year down the road, IPW will be ancient history and IWL will be preferred. It might make the first few weeks of Hardy rocky as upstream's still putting effort into this driver that will get continously updated in linux-backports-modules.

---

### Post by tonyr1988 on 2008-04-27
> **jdong said:**
> IMO the move to the IWL driver is the right choice considering even a year down the road, IPW will be ancient history and IWL will be preferred. It might make the first few weeks of Hardy rocky as upstream's still putting effort into this driver that will get continously updated in linux-backports-modules.

So how long should I wait until I go from Gutsy->Hardy? Is the WiFi reasonably stable, or should I expect it to be up/down with the various driver changes? I use my laptop as my main computer, so it's kind of important that it works all the time (or close to it :D).

P.S. Post #1000! I'm hitting all the records for this thread. :P

---

### Post by Frank Golden on 2008-04-28
> **tonyr1988 said:**
> So how long should I wait until I go from Gutsy->Hardy? Is the WiFi reasonably stable, or should I expect it to be up/down with the various driver changes? I use my laptop as my main computer, so it's kind of important that it works all the time (or close to it :D).

P.S. Post #1000! I'm hitting all the records for this thread. :P

Hi Tony the fix I linked to in my earlier post worked for me.
If you have an intel card it should work for you.
I agree with you Jdong about the open source drivers being the best in the long run but IMHO the devs should have let them mature some before abandoning the the proprietary drivers. 

I don't much care for the decision to install FF3 _BETA _ by default.
I mean after all it is a beta product with very limited addon support.
I think the final release of Hardy should have included a final Firefox (2) with FF3 as an option.

---

### Post by jdong on 2008-04-28
> **Frank Golden said:**
> Hi Tony the fix I linked to in my earlier post worked for me.
If you have an intel card it should work for you.
I agree with you Jdong about the open source drivers being the best in the long run but IMHO the devs should have let them mature some before abandoning the the proprietary drivers. 

I don't much care for the decision to install FF3 _BETA _ by default.
I mean after all it is a beta product with very limited addon support.
I think the final release of Hardy should have included a final Firefox (2) with FF3 as an option.

FF2 is in the repos if you choose to use it. Ultimately the problem with FF2 is that in 3 years, Mozilla will no longer care about that branch and we'd be completely on our own to provide security updates for it. FF3 was a major transition to do repo-wide and I'm glad we got a lot of the rough parts of the migration done in development-phase so we can just supply incremental updates to FF3 final as it comes out.

---

### Post by articpenguin on 2008-04-28
> **jdong said:**
> FF2 is in the repos if you choose to use it. Ultimately the problem with FF2 is that in 3 years, Mozilla will no longer care about that branch and we'd be completely on our own to provide security updates for it. FF3 was a major transition to do repo-wide and I'm glad we got a lot of the rough parts of the migration done in development-phase so we can just supply incremental updates to FF3 final as it comes out.

will ff2 get security updates in the repos since it is in main?

---

### Post by jdong on 2008-04-28
> **articpenguin said:**
> will ff2 get security updates in the repos since it is in main?

Although it's in universe, I understand that it will continue to get maintenance updates like it had in gutsy, until Mozilla stops providing them anymore (i.e. a few months after FF3 becomes released). At which time whether or not we provide any more FF2 updates will depend on what other big distros (RedHat, Novell) are going to do with their FF2-shipping distros. Last time around with Firefox 1.5, a few enterprise distros banded together to do patches for Firefox 1.5 after Mozilla EOLed it but that was a scary experience to almost be stranded with a browser with no security updates!

---

### Post by Frank Golden on 2008-04-28
> **jdong said:**
> FF2 is in the repos if you choose to use it. Ultimately the problem with FF2 is that in 3 years, Mozilla will no longer care about that branch and we'd be completely on our own to provide security updates for it. FF3 was a major transition to do repo-wide and I'm glad we got a lot of the rough parts of the migration done in development-phase so we can just supply incremental updates to FF3 final as it comes out.HI Jdong, are you saying that FF3 is years away from final?
Anyway my main objection to FF3 are the lack of support for many of the add-ons I use.
Removing FF3 and replacing with FF2 breaks many of the multimedia plugins that are installed in FF3 by default.
I guess what I'm saying is that FF3 has been available in the repos for awhile now as an option. I think it should have remained an option and not FF2.

---

### Post by jdong on 2008-04-28
> **Frank Golden said:**
> HI Jdong, are you saying that FF3 is years away from final?
Anyway my main objection to FF3 are the lack of support for many of the add-ons I use.
Removing FF3 and replacing with FF2 breaks many of the multimedia plugins that are installed in FF3 by default.
I guess what I'm saying is that FF3 has been available in the repos for awhile now as an option. I think it should have remained an option and not FF2.

No, I'm not saying that FF3 is years away from final. It's in its very close to release stage in fact, it's almost in full freeze. Granted the decision to ship FF3 as the predominant default does disrupt add-ons, I guarantee you that in 3 months you'll agree with the decision as Mozilla begins end-of-life process on security updates for the 2.x.x branch. Then if we push an update that'll break all 20-30 whatever extensions in the repo and force a rebuild of a bunch of plugins, people are going to whine even more :)

---

### Post by Frank Golden on 2008-04-29
> **jdong said:**
> No, I'm not saying that FF3 is years away from final. It's in its very close to release stage in fact, it's almost in full freeze. Granted the decision to ship FF3 as the predominant default does disrupt add-ons, I guarantee you that in 3 months you'll agree with the decision as Mozilla begins end-of-life process on security updates for the 2.x.x branch. Then if we push an update that'll break all 20-30 whatever extensions in the repo and force a rebuild of a bunch of plugins, people are going to whine even more :)
Ok will wait and see.:)

---

### Post by cbudden on 2008-04-30
Just wanted everyone's thoughts on the current release of the ATI driver.  How is everyone finding it?  Personally I haven't used it for a while now as I decided I would rather have suspend/hibernate and good video playback instead of compiz and 3D.

How is it playing for everyone?

---

### Post by Re1lly on 2008-04-30
Today i updated from feisty to Hardy. The graphics card was not a problem as it was before. No use of an XGL session for compiz, but video playback is not as good quality as before. but as i said i just installed hardy this morning so i might figure that out.

I am more concernerd with the very high cpu temperatures i am registering since i installed. After 5 minutes i turn it on temperature always rises at least to 70 degrees Celsius and doesn't go down... I know this laptop is usually hot on its own, but i'm not feeling ok with this, even though the computer doesn't show signs of slowing down.At the moment i am running Firefox, Emesene, and Ktorrent and temperature is 74°C (same stuff running feisty was around 60° stable)
Any clues??

---

### Post by Frank Golden on 2008-05-30
Hi All, Well the release candidate for Firefox 3 has been out for a while, at least in the Windows world, anybody got any idea when it will be in the repos for hardy. Soon I hope. Be nice if some of the add-ons I like would work in FF3 also. Wishful thinking I guess.

---

### Post by cbudden on 2008-05-30
It already is !  Add the hardy-proposed repo and update.

---

### Post by jdong on 2008-05-30
> **Frank Golden said:**
> Hi All, Well the release candidate for Firefox 3 has been out for a while, at least in the Windows world, anybody got any idea when it will be in the repos for hardy. Soon I hope. Be nice if some of the add-ons I like would work in FF3 also. Wishful thinking I guess.

It's already in -proposed as a testing update; the developers were all at UDS at the time of FF3 RC1's release, which accounts for the week-ish delay before -proposed packages.

---

### Post by Frank Golden on 2008-06-12
Hi Folks, Just recently updated my 5672's ram from 2GB to 4Gb using a 4GB kit from Crucial.
As expected XP 32 bit reports only 3GB of ram installed. My laptop has a Core2Duo (merom) processor which according to Intel is a 64 bit setup with the chipset I have. A member of another forum suggested that I give 64 bit Ubuntu a try to utilize all of the installed ram.

So not missing an opportunity to tinker I did just that (Ubuntu 8.04.1 LTS 64 bit).
That was a bit of an adventure in itself as the 64 bit version needed some special attention and research on my part to install correctly. Mostly Amd/ ATi's latest drivers and multimedia codecs/plugins gave me fits.
I finally got it set up and running very well.
Imagine my surprise when checking System Monitor (see screen shot below) to see Ubuntu reporting 3Gb of installed ram.


[[IMG]http://i30.photobucket.com/albums/c338/fjgold/th_Screenshot-7.png[/IMG]](http://i30.photobucket.com/albums/c338/fjgold/Screenshot-7.png)



```
free -m
```


output shows 3GB also.

```
frank@frank-laptop:~$ free -m
             total       used       free     shared    buffers     cached
Mem:          3023       1032       1991          0         26        598
-/+ buffers/cache:        407       2615
Swap:          823          0        823
frank@frank-laptop:~$
```


I thought 64 bit OS's were capable of seeing and uses much more than 4GB of ram.
Any thoughts?
BTW, my BIOS reports 3GB also and there appears to be no way to change it.
I have the latest BIOS update from Acer Europe.

---

### Post by beejay82 on 2008-06-12
I actually thought the 5672 only supported up to 2GB of RAM. At least that's what I thought I read on Maximum Memory installed on their website a few years back.

Maybe the BIOS can only utilize upto 3GB.

---

### Post by jdong on 2008-06-12
Not all 64-bit chipsets are capable of moving the PCI reserved window from 3.3->4GB up higher to another region. In fact with PAE on 32-bit you are able to do the same thing WITHOUT being in long (64-bit) mode.

I believe for Intel mobiles, only the Santa Rosa chipset or higher can move around this reserved window; the bit-ness of your OS is irrelevant for the most part.


EDIT: With that said, having 4GB RAM is not a waste; these systems use HyperMemory which extends video RAM with system RAM, so bandwidth and speed of system RAM is crucial to decent graphics performance, so using symmetrical sticks to get dual-channel and interleaving is almost mandatory.


The 2GB number comes from the fact that at the time of publishing I bet only 1GB sticks of RAM were available... 2GB sticks are accepted by this laptop perfectly; if you want more than 2GB, 4GB of RAM with 700MB unaddressable is the best that you can do.

---

### Post by Frank Golden on 2008-06-12
> **jdong said:**
> Not all 64-bit chipsets are capable of moving the PCI reserved window from 3.3->4GB up higher to another region. In fact with PAE on 32-bit you are able to do the same thing WITHOUT being in long (64-bit) mode.

I believe for Intel mobiles, only the Santa Rosa chipset or higher can move around this reserved window; the bit-ness of your OS is irrelevant for the most part.


EDIT: With that said, having 4GB RAM is not a waste; these systems use HyperMemory which extends video RAM with system RAM, so bandwidth and speed of system RAM is crucial to decent graphics performance, so using symmetrical sticks to get dual-channel and interleaving is almost mandatory.

The 2GB number comes from the fact that at the time of publishing I bet only 1GB sticks of RAM were available... 2GB sticks are accepted by this laptop perfectly; if you want more than 2GB, 4GB of RAM with 700MB unaddressable is the best that you can do.

Thanks jdong. I guess that answers my question. I didn't think I wasted
my money ($79.00) for the 4GB matched kit. After all even if the OS only uses 3GB that is still 1GB more than I and it is the only way to get 3GB
dual channel interleaved.
As far as using the 64 bit Hardy is concerned I might as well keep it even though it won't see the last 1GB of installed ram. Installing it was a chore but an interesting one. I've learned some stuff I wouldn't have otherwise.

Your answer seems to make the most sense out of all the other ones I've seen during my google research on this subject.

BTW, the online system scanner from Crucial does show 4GB being max for our notebook and not 2GB.

---

### Post by zeca_pedra on 2008-06-22
> **Frank Golden said:**
> Hi Folks, Just recently updated my 5672's ram from 2GB to 4Gb using a 4GB kit from Crucial.
As expected XP 32 bit reports only 3GB of ram installed. My laptop has a Core2Duo (merom) processor which according to Intel is a 64 bit setup with the chipset I have[...]
I have this same model of Acer Laptop and I really don't believe it's using 64 bit processor technology!
No matter what you see on Intel's site I think the chipset that came with this laptop it's not 64 bit - I have friends that also feel a little bit confused with this duo core versus 64 bit processors!
I myself am not sure what the differences are, but one thing I know: Aspire 5672WLMI it's not equiped with 64 bit processors :(

---

### Post by jdong on 2008-06-22
> **zeca_pedra said:**
> I have this same model of Acer Laptop and I really don't believe it's using 64 bit processor technology!
No matter what you see on Intel's site I think the chipset that came with this laptop it's not 64 bit - I have friends that also feel a little bit confused with this duo core versus 64 bit processors!
I myself am not sure what the differences are, but one thing I know: Aspire 5672WLMI it's not equiped with 64 bit processors :(

This thread is getting too long.... but Frank upgraded his CPU after-market with a 64-bit capable Merom (Core 2 Duo) chip.

---

### Post by Frank Golden on 2008-06-28
Hey Jdong,

> This thread is getting too long.... but Frank upgraded his CPU after-market with a 64-bit capable Merom (Core 2 Duo) chip.

Why not start a new thread for the 5672? It may be long but it sure is helpful.

The chipset sure does support 64 bit but the original processor indeed did not.
I am presently running 64 bit Ubuntu 8.04.1 LTS on it with no problems, other than the aforementioned ram issues. 
I'm not sure but I don't think 64 bit Ubuntu would run on a 32 bit machine??

---

### Post by daveappendix on 2008-06-29
Hello folks.

I've been using Feisty on my 5672 for a long time now, and tried this morning to do a fresh install of Hardy. First off, I just booted into the live cd, but it just froze during boot. When I went into the virtual console with Ctrl-Alt-F1, it continually spits out the same message, something along the lines of "error detecting camera," mentioning gspca, but nothing helpful. If I then C-A-Del, the rest of it boots up, with the progress bar jumping right to the end. I'm not convinced everything else is then detected cos of the C-A-Del.

So I guess my point is has anyone else seen this? Any suggestions for cleanly skipping the camera tests during boot? (Ctrl-C in the console just shuts down, surprisingly)

Cheers for any help.
Dave.

---

### Post by daveappendix on 2008-06-29
The camera thing could be a red herring as Feisty is giving me the exact same error, I just didn't realise.

The live cd seems to stall on "Loading hardware drivers...". If I wait long enough, the system just shuts down. C-A-Del doesn't always work to get things moving along, but when it does everything seems ok.

I'm about to backup my Feisty install and just give Hardy a try, going to install instead of live cd, though I'd still welcome any insight/anecdotes.

Cheers,
Dave

---

### Post by cbudden on 2008-06-29
I've got a similar camera error.  I think it is to do with poor hardware than anything, because if you move the camera about, push it a bit, the errors stop for a while.

Also, has anyone noticed that waking up from RAM fails on the latest two kernel updates?  I have to boot in 2.6.24-17-generic for it wake (non fglrx)

---

### Post by tonyr1988 on 2008-06-29
I'm getting extremely slow boot times due to a camera configuration failure. This happened in Gutsy (I ignored it, for the most part, assuming it was something I messed up), but I just did a fresh install of Hardy and it's happening again.

In dmesg, it shows:

> [  159.765686] /build/buildd/linux-ubuntu-modules-2.6.24-2.6.24/debian/build/build-generic/media/gspcav1/gspca_core.c: USB GSPCA camera found.(VC0321) 
[  159.974114] usb 5-8: USB disconnect, address 106
[  159.974135] /build/buildd/linux-ubuntu-modules-2.6.24-2.6.24/debian/build/build-generic/media/gspcav1/gspca_core.c: Failed to configure camera
[  159.974148] gspca: probe of 5-8:1.0 failed with error -5
[  160.108061] usb 5-8: new high speed USB device using ehci_hcd and address 107
[  160.267097] usb 5-8: configuration #1 chosen from 1 choice

And it repeats this for a couple of minutes.

Should I:

[LIST=1]
[*]Try to get the camera working, so it doesn't fail at boot?, or
[*]Completely disable the camera, so it doesn't even try?
[/LIST]

I don't use the camera, so I don't care which one I do - as long as it boots faster. It's insanely slow.

---

### Post by tonyr1988 on 2008-06-29
> **tonyr1988 said:**
> I'm getting extremely slow boot times due to a camera configuration failure. This happened in Gutsy (I ignored it, for the most part, assuming it was something I messed up), but I just did a fresh install of Hardy and it's happening again.

In dmesg, it shows:



And it repeats this for a couple of minutes.

Should I:

[LIST=1]
[*]Try to get the camera working, so it doesn't fail at boot?, or
[*]Completely disable the camera, so it doesn't even try?
[/LIST]

I don't use the camera, so I don't care which one I do - as long as it boots faster. It's insanely slow.

If anyone else has problems, the simple solution is to just blacklist gspca (add it to /etc/modprobe.d/blacklist), but this disables the webcam.

I'm not sure how to make it consistently work, but that's fine with me. It boots much faster now. :)

---

### Post by Frank Golden on 2008-06-30
> **cbudden said:**
> I've got a similar camera error.  I think it is to do with poor hardware than anything, because if you move the camera about, push it a bit, the errors stop for a while.

I've noticed the same thing. One of the reasons I switched to an external camera (Logitech QuickCam pro 9000). Did have to fiddle with uvcvideo to get
it working right but I can video conference with my daughter and grandkids
using Skype 2.0 from Hardy. Camorama doesn't work with the new camera but luvcview does.

---

### Post by daveappendix on 2008-06-30
> **cbudden said:**
> I've got a similar camera error.  I think it is to do with poor hardware than anything, because if you move the camera about, push it a bit, the errors stop for a while.

Well, that solved it! I flipped the camera round to the alternate orientation, and then back again. Next time I booted, there were no complaints. It might explain why I've been having camera trouble in windows too. Shoddy hardware + it's over 2 years old now.

Cheers,
Dave.

---

### Post by Frank Golden on 2008-06-30
> **daveappendix said:**
> Well, that solved it! I flipped the camera round to the alternate orientation, and then back again. Next time I booted, there were no complaints. It might explain why I've been having camera trouble in windows too. Shoddy hardware + it's over 2 years old now.

Cheers,
Dave.
Age has nothing to do with it. My 5672 when new experienced the same camera issues, it was by dumb luck that I figured out that moving the camera around
would "fix" it. I guess the electrical connections are touchy. The camera is a USB device.
The camera is a P.O.S. for video conferencing. Low rez and needs a lot of light.
If you use a web cam you are better off with a device like the QuickCam Pro 9000.
It cost me less than $100.00 US is 2 megapixel, works great in low light and auto focuses.
Integrates well with Skype 2.0. 
XP does offer more control over the camera (with the supplied software) than Linux does though.

For best results with the 9000 camera it is best to plug it in before doing a fresh install of Ubuntu Hardy, letting hardy detect and configure it during install.
The program lucview (via Synaptic) is needed to change settings.

---

### Post by beejay82 on 2008-06-30
The camera is buggy. The connector inside gets loose easily especially with all the rotating. I opened my camera up and placed electrical tape inside where the cable was coming out. It gave it a more snug feel and since then I haven't had any more problems.

But ya, the camera sucks. Unless you have flourescent lighting or direct sunlight, the image quality is poor.

---

### Post by daveappendix on 2008-07-02
Hello again.

I don't want to bloat this thread too much, but since you lot are such experts with the 5672, I wonder if you wouldn't mind taking a look at the thread below if you've got any words of wisdom on pcmcia and eSata.

[http://ubuntuforums.org/showthread.php?t=511821](http://ubuntuforums.org/showthread.php?t=511821)

Cheers,
Dave.

---

