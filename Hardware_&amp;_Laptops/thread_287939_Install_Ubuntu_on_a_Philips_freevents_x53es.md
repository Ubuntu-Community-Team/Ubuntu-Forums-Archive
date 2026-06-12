---
title: "Install Ubuntu on a Philips freevents x53es"
date: 2006-10-29
forum: Hardware &amp; Laptops
---

### Post by Pionner on 2006-10-29
I'm trying to install Ubuntu Edgy on a Philips freevents X53es.

Both the default live-cd and alternate-cd installs froze at network hardware detection. I've tried dapper installation unsuccessfully but breeze one works great. I suppose it's a kernel version issue with the network card (the *8139too* kernel module is loaded correctly on Breezy).

On verbose mode, the last lines of kernel boot are:

> 8139too Fast Ethernet driver 0.9.27
ACPI: PCI Interrupt 0000:03:04.0[a] -> GSI 16 (level, low) -> IRQ 177

the the system gets frozen.

Any idea? Thanks in advance.

---

### Post by Hrugaar on 2006-11-04
Hi, i seem to be having the same problem with my X56, did you figure out what was wrong?

---

### Post by Pionner on 2006-11-05
I've finally fixed it  by compiling the lastest kernel form kernel.org disabling the *8139cp* module and enabling the *8139too* with the 
*CONFIG_8139TOO_OLD_RX_RESET* option enabled (it's disabled by default on most distros, that's the reason hardware-detection fails).

My complete install process was:

- Install Ubuntu Breeze
- Compile custom kernel
- Upgrade to Dapper
- Upgrade to Edgy

Not linux-firendly at all :-k 

I hope it helps.

---

### Post by epokh on 2006-11-12
> **Pionner said:**
> 
My complete install process was:

- Install Ubuntu Breeze
- Compile custom kernel
- Upgrade to Dapper
- Upgrade to Edgy

Not linux-firendly at all :-k 

I hope it helps.

Pioneer good job! I have a philips x56 laptop, like Hruggar.
When I install the Ubuntu breeze, do I have to boot with normal parameters?

---

### Post by Pionner on 2006-11-12
Yes, the breeze kernel works well.
The trick is to select the breeze kernel (2.6.12) each time you boot, even after upgrading to dapper/edgy.

[EDIT]
You can compile your own kernel too; I've tried with latest vanilla version from kernel.org, using the breeze configuration and **enabling** the CONFIG_8139TOO_OLD_RX_RESET in the 8139too module and it works.
[/EDIT]

If you compile a custom kernel, you must install the IntelProWireless module by hand or using module-assistant.

---

### Post by Hrugaar on 2006-11-14
Pioneer, in your last post you said to disable the CONFIG_8139TOO_OLD_RX_RESET option in the 8139too module, but in a previous post you said to enable it. Which one worked for you?

Thanks

Hrugaar

---

### Post by Pionner on 2006-11-14
I've corrected my last post. The correct method is enabling it.

Sorry  :rolleyes:

---

### Post by Hrugaar on 2006-11-15
No problem :) 

Thanks for the help.

---

### Post by angus_mcfisher on 2006-11-19
Does this method work on the X56 also? Does anyone here use OpenSuse and knows how to get this working too? I'm rather new to linux - well - as far as I haven't compiled my own kernel before. Would you be able to give me a step by step approach.

Kind regards,

Lee

---

### Post by amar on 2006-11-19
I have been using Kubuntu on my desktop for a couple of months now. I have just got a nice new Philips X56 and have run into the same problems. i don't have a copy of breezey and am not too shure how i would compile my own kernal if i did. can anyone point me in the right direction of an old copy or another way of fixing this

Thanks Amar

---

### Post by derjames on 2006-11-19
I can confirm this problem when using Dapper 64, I do not have a Breeze CD so I haven't been able to run Ubuntu and I haven't had enough time to figure out a solution. A bug report was filled on june 5th, 2006 but it is rated as medium and unconfirmed the bug# is 48456, I did add some comments and links to this thread...

---

### Post by derjames on 2006-11-19
> **angus_mcfisher said:**
> Does this method work on the X56 also? Does anyone here use OpenSuse and knows how to get this working too? I'm rather new to linux - well - as far as I haven't compiled my own kernel before. Would you be able to give me a step by step approach.

Kind regards,

Lee

Dear Angus

Please check the following threads which might be useful

[http://www.howtoforge.com/kernel_compilation_ubuntu](http://www.howtoforge.com/kernel_compilation_ubuntu)

[http://www.ubuntuforums.org/showthread.php?t=56835](http://www.ubuntuforums.org/showthread.php?t=56835)

hope this helps

J

---

### Post by derjames on 2006-11-21
Well, I was still trying to dual boot Ubuntu Dapper in this machine, but I couldn't. However there is no need to dual boot. I've just installed Edgy Eft under VMware server... and belive me this Philips X56 runs really fast...

(1)  Under windows install VMware server (NOT VMPlayer) which is free to download from the vmware website.

(2)  Create you virtual machine. Set memory, hard drive space and a sound interface.

(3)  Download the 32 bit .iso 'Edgy' file and save it in your hard drive (the location is your choice)

(4)  Instruct the virtual machine to boot from the 'Virtual CD ROM drive' which in this case is the .iso file in your hard drive

(5)  Start your virtual machine

(6)  Enter to Live Ubuntu as asual 

(7)  Once Ubuntu is on live mode just install Ubuntu to your new virtual machine

('8')After finishing the first thing you will notice is that the resolution is SVGA instead of WXGA (1280x800)

(9)  Open terminal and type: sudo gedit /etc/X11/xorg.conf
(10) After typing your password the content appears
(11) go to the 'screen' section
(12) Whenever you see modes add "1280x800"

     Example:
     ...
     Section "Screen"
          ...
         DefaultDepth    24
         SubSection "Display"
           Depth   24
           Modes   **"1200x800"** "1024x728" "800x600"
         EndSubsection
     EndSection
     ...
(13) Reestart Ubuntu
(14) That's it Now Running Windows XP and Ubuntu in the same session.

This Core 2 duo processor is amazing... I still don't belive the speed of Edgy running under Windows is like if Ubuntu were running in native mode!!!...

Just one last thing... It seems that all have been recognised even the wireless adapter... If I have a problem I will post it here...

Cheers

---

### Post by amar on 2006-11-21
do you add 12**8**0x800 or 12**0**0x800?
unfortunately i have just installed breezy and now the x server won't start. i can see many hours of playing to be had before i fix this

not exactly what a linux newbie wants to deal with

---

### Post by amar on 2006-11-21
from the [edlug]("http://www.edlug.ed.ac.uk/archive/Nov2006/msg00205.html") mailing list

> I too have a X56 which I've got Gentoo (and originally Ubuntu) running
on. I had to use the "alternate" Ubuntu disk image to install, choosing
to run without the hardware autodetection from the boot prompt (I think
it is F2), then manually modprobing for the SATA disk (modprobe ahci).
Be careful not to let it attempt to detect any more drivers as it is the
8139too driver that causes the problems during hardware autodetection.
After the install you should remove the 8139too.ko file
from /lib/modules/linux-*, I've also had problems with the sd_hci driver
for the SD reader, which can also hang. So you should get rid of that
one too.

I will be putting up a webpage going over all the steps that I took for
Ubuntu X56 in a few days with fulld details. Hopefully above should get
you going or if you need specific help you can email me directly.

Regards,

Tom

---

### Post by derjames on 2006-11-22
> **amar said:**
> do you add 12**8**0x800 or 12**0**0x800?
unfortunately i have just installed breezy and now the x server won't start. i can see many hours of playing to be had before i fix this

not exactly what a linux newbie wants to deal with

Sorry for the Typo it is 1280x800

cheers

---

### Post by derjames on 2006-11-22
I am very happy with my Philips X56 and all these virtualisation stuff... Edgy is simply running so smooth and nicely in VMware

cheers

---

### Post by neemz on 2006-12-04
Right folks, I have an X56 and successfully got everything working on it.

I'll give you some rough quick and dirty tips for getting it working, (these will be vague so its not for a novice to follow).

Grab the alternate install CD of your choice. Slam it in and begin the install. As soon as the installer starts up Press Alt-F2 to switch out to another console, change directory to /lib/modules/(kernel)/drivers/net 

Now type into the console rm 8139too.ko but don't hit enter.

Switch back to the main installer (alt F1) and carry on, at the point where it starts some hardware detection press alt f2 to switch out.

At this stage you must hit enter to run the remove command and then press up and enter and keep hammering it, up enter, up enter, up enter. This is because you will need to delete the driver as soon as the installer extracts it yet before it has chance to load it! You will know when you are successful cos the remove command wont give you an error.

ALT F1 back and carry on, at the point where the installer starts installing files switch back out to altf2.

Navigate to /target/libs/(kernel)/drivers/net

delete 8139too, also delete the driver for the sd card (cant remember what it is called now but its in the mmc directory and starts with s!

Switch back and continue the install.

Ubuntu will boot up and you will have a working system (without wired ethernet or MMC card support).

sudo apt-get linux-restricted-modules

This will get the wireless working.

Now use the wireless to grab the latest kernel sources (2.6.19) or a usb stick or anything.

Extract them in /usr/src

go in and do a make menuconfig

In drivers | Net | Ethernet 10/100 | Find 8139too and enable all the suboptions for it, disable 8139cm.

You will also want to enable sata support and AHCI, might aswell do 1000hz tick rate and Pentium 4 processor while your at it, hell put full preempt in to.

use the fakeroot kpkg method of compiling.

you will have two .deb files in /usr/src/ after compilation. Install these

Before rebooting grab the ipw3945 drivers from intel and the ieee80211 drivers from sourceforge.

Reboot (the new kernel image should come up automatically and your wired ethernet will now work! But wireless wont!

Now listen to this bit because it annoted me for ages

rename sh! we don't want sh being used to run our scripts!

link bash to sh, this way whenever sh is called bash will run instead. this will allow the ieee80211 and ipw3945 to compile properly!

Follow intels instructions for installing their driver.

and Bingo! You now have everything but the mmc card working on Ubuntu Edgy, full powermanagement, sleep, hibernate, processor speed changing... it all works fine.

(I haven't actually tried the mmc card reader to see if it works with the new kernel, I blacklisted it earlier on).

---

### Post by amar on 2006-12-04
thanks
i have it booting and working ish

I haven't attempted to connect to any networks yet there are some other teething problems first
the boot time takes ages (several minuets)
the resolution is wrong (xorg says it is right but the system settings wont let it go any higher than 1024 x 768

I think I have a few hours of fun ahead of me but it should wait till after exams

---

### Post by neemz on 2006-12-04
Hi amar,

apt-get install 915resolution, then reboot, thats your resolution sorted ;p

As for the long bootup, thats because of the way the ubuntu kernel is handling acpi, recompiling the kernel (2.6.19) as I mentioned will solve that bootup issue and allow a sub 40second boot.

A temporary nasty fix is to put acpi=off on the kernel load line in grub, this isn't really a fix though as it breaks all forms of powermanagement that are built in to the ubuntu kernel.

---

### Post by amar on 2006-12-04
great, i will have to wait till i am in a wi-fi area and should wait till after exams though your help is greatly appreciated
I can live with windows for another few days

---

### Post by amar on 2006-12-05
Baah, sudo apt-get linux-restricted-modules gives
E: Invalid operation linux-restricted-modules

is there something i am doing horribly wrong here?

EDIT- I think i have it sorted now had to use
sudo apt-get install linux-restricted-modules-(kernel name goes here)

---

### Post by neemz on 2006-12-05
Yeah sorry about that I typed it out in some haste, I didn't have much battery power left :p

---

### Post by amar on 2006-12-07
I tried to compile my own kernel but that didn't work (i gave up letting it boot after 15 mins) could you post your config file it might be easier

i kind of got lost around > You will also want to enable sata support and AHCI, might aswell do 1000hz tick rate and Pentium 4 processor while your at it, hell put full preempt in to

---

### Post by neemz on 2006-12-07
Certainly

---

### Post by dc243 on 2006-12-23
I've followed the instructions given here, and everything works after a fashion, however once I've compiled the kernel I seem to have problems with sdhci:slot0 , which I presume is related to the SD card.  The machine doesn't boot beyond this error message (at least not within 10 mins).  Has anyone else experienced this problem?

---

### Post by snorkelman on 2006-12-24
looks like you've left support for mmc in the custom kernel you compiled? If so just delete the mmc driver(s) located in

**/lib/modules***/(name of your custom kernel)/*[B]kernel/drivers/mmc
[/B]

and that should take care of the SD card reader lockup (the card reader on the X56 isn't supported by the drivers at this time) You can delete the sdhci driver on its own, dump all drivers in the mmc directory or just nuke the mmc direcotry entirely whichever you prefer

stevie

---

### Post by neemz on 2006-12-24
I prefer to block the mmc drivers by adding their names in the blacklist file in /etc/modules

This way when I recompile or test new kernels I don't have to be super careful about deleting modules in every kernel version.

---

### Post by amar on 2006-12-24
I found Slax worked well on the laptop so i used it to delete the appropriate files when i couldn't boot.

After compiling the vanila kernel it boots alot nicer however i am having trouble compiling the wireless driver. I have linked bash to sh. the ieee80211-1.1.14 compiles fine however ipw3945-1.1.0 causes errors
```
In file included from /home/amar/ipw3945-linux-1.1.0/ipw3945-1.1.0/ipw3945.c:68:
/home/amar/ipw3945-linux-1.1.0/ipw3945-1.1.0/ipw3945.h:32:26: error: linux/config.h: No such file or directory
/home/amar/ipw3945-linux-1.1.0/ipw3945-1.1.0/ipw3945.c: In function &#8216;ipw_pci_probe&#8217;:
/home/amar/ipw3945-linux-1.1.0/ipw3945-1.1.0/ipw3945.c:16355: warning: passing argument 2 of &#8216;request_irq&#8217; from incompatible pointer type

```

any ideas?

---

### Post by snorkelman on 2006-12-24
I went with 1.1.3 which addresses that issue

[http://www.bughost.org/pipermail/ipw-bugs/2006-November/000805.html]("http://www.bughost.org/pipermail/ipw-bugs/2006-November/000805.html")

---

### Post by neemz on 2006-12-25
> **amar said:**
> I found Slax worked well on the laptop so i used it to delete the appropriate files when i couldn't boot.

After compiling the vanila kernel it boots alot nicer however i am having trouble compiling the wireless driver. I have linked bash to sh. the ieee80211-1.1.14 compiles fine however ipw3945-1.1.0 causes errors
```
In file included from /home/amar/ipw3945-linux-1.1.0/ipw3945-1.1.0/ipw3945.c:68:
/home/amar/ipw3945-linux-1.1.0/ipw3945-1.1.0/ipw3945.h:32:26: error: linux/config.h: No such file or directory
/home/amar/ipw3945-linux-1.1.0/ipw3945-1.1.0/ipw3945.c: In function &#8216;ipw_pci_probe&#8217;:
/home/amar/ipw3945-linux-1.1.0/ipw3945-1.1.0/ipw3945.c:16355: warning: passing argument 2 of &#8216;request_irq&#8217; from incompatible pointer type

```

any ideas?

This issue is to do with no config.h existing in the newer kernels I think, as far as I can remember I fixed it like this

touch /usr/src/(kernelversionhere/config.h

---

### Post by gsmlinux on 2007-01-02
> **neemz said:**
> Hi amar,

apt-get install 915resolution, then reboot, thats your resolution sorted ;p
l.
Neemz, 

Could you please post your xorg.conf as although I can get the 1280*800 display up, X hangs when I launch the menu or an application. 

Cheers

George

---

### Post by amar on 2007-01-02
here you go

---

### Post by gsmlinux on 2007-01-03
Thanks Neemz, that's my xorg sorted out.

Now for sound and acpi

---

### Post by amar on 2007-01-04
I am beginning to wonder how many problems you can run into with this thing and if i have had every one. managed to get the module compiled and it appears to work fine at first but then when i try to connect to a network it fails.

It has no problems detecting the presence of the network and gets as far as asking you for the passphrase (if any) then goes of to connect and gets stuck before crashing. I have tried it with different networks and even withought encryption, it works fine with the original generic kernel.

Again it is probably really simple - if you know the solution

EDIT - Don't know what i did differently this time but i deleted all wireless files and started again and works fine now!
Woot!

---

### Post by amar on 2007-02-24
Has anyone gotten dual monitors to work properly on this thing. I can get it to show the right side of the screen if the external monitor is plugged in on boot but can't any time i try to press fn + F5 it shows a black screen same effect when i edit the xorg file

Amar

---

### Post by ppan76 on 2007-03-04
> **Pionner said:**
> I'm trying to install Ubuntu Edgy on a Philips freevents X53es.

Both the default live-cd and alternate-cd installs froze at network hardware detection. I've tried dapper installation unsuccessfully but breeze one works great. I suppose it's a kernel version issue with the network card (the *8139too* kernel module is loaded correctly on Breezy).

On verbose mode, the last lines of kernel boot are:


the the system gets frozen.

Any idea? Thanks in advance.

I have the same problem with my cheap Everex SA2050T. The motherboard is also made by twinhead :-(

I solved my problem by installing Vista. :-)

---

### Post by tsaarni on 2007-03-05
> **neemz said:**
> 
Grab the alternate install CD of your choice. Slam it in and begin the install. As soon as the installer starts up Press Alt-F2 to switch out to another console, change directory to /lib/modules/(kernel)/drivers/net 

Now type into the console rm 8139too.ko but don't hit enter.


Is there no easier way to disable certain modules when booting Ubuntu installer (like noload=nnn on gentoo and brokenmodules=nnn on suse)?

I tried the "rm trick" with Feisty alternate CD but ran into unrelated problems with the text based partitioner. I would rather just use the live CD install and GParted if only could I skip the hanging Realtek ethernet chip detection.

---

### Post by novakry on 2007-04-23
Hi I've recently obtained an x56, I've made good progress so far. however I've hit nothing but errors when compiling the drivers for the wireless. Neemz mentions something about linking bash to sh, I just need someone to detail how to install the drivers. I'm so close to having it fully working, I just hope someone is kind enough to help me get it working.

TYIA

NovaKry

---

### Post by skrpc on 2007-05-10
I too have tried to install ubuntu and fedora on a philips X56 laptop and had the same problem.

I have determined the problem seems to be with the sdhci "Secure Digital Host Controller Interface" driver.  I downloaded the Debian 4 (Etch) business card installation and this started up ok, in fact it recognised two ethernet interfaces and allowed me to select which one I wanted.  The installation completed ok and as I used the business card installation it downloaded all the packages over the internet proving the wired ethernet was working.

However, the installed kernel image then had the same problem so when I rebooted the machine after the installation completed it froze.  I went back to the business card installation and booted the installation in rescue mode which allowed me to mount my installed debian 4 system and run a shell against it.  From here I was able to download the kernel source for 2.6.18.4 and build my own kernel image.  I took the configuration file my Debian 4 installation had created as the base for my custom kernel and the only change I made was to deselect the option to load the sdhci "EXPERIMENTAL" driver under the MMC and SD sub option.

I used the instructions at [http://www.debianhelp.co.uk/kernel2.6.htm](http://www.debianhelp.co.uk/kernel2.6.htm) to build the kernel.

This installation does not enable the wireless network and I guess to get this working I need to download the drivers from the intel site and follow their instructions on installing it but for me wired ethernet is good enough for now.

---

### Post by novakry on 2007-05-13
Hi,

Just to let everyone know, i have the laptop working in ubuntu feisty just fine. i don't have a wired lan, but then i never really use it. the boot time rivials neemz custom build kernel, so for anyone looking for a quick fix and aren't bothered about wired lan. just download yourself a fiesty fawn alternative disk and following neemz's directions up to the point where you have ubuntu installed. 

just loaded beryl and very chuffed to have left windows for good, for how small this laptop is and what it does is very impressive.

---

### Post by Arne.F on 2007-05-26
I had similar Problems on my Averatec 2460. (8139too and sdhci crash the kernel)

8139too works if compiled without mmio support.

I have build a Ubuntu 7.04 Desktop CD with 8139too in Pio-Mode and without SDHCI.

[http://www.fitzenreiter.de/averatec](http://www.fitzenreiter.de/averatec)

Please try if this CD works also on your Philips Notebook.

---

### Post by amar on 2007-05-28
EXCELLENT! I love it, just downloaded it, live CD works nicely and installed fine. Thanks

---

### Post by rojanu on 2007-06-04
Hi Everyone! I have just installed Ubuntu feisty on my friends laptop philips X56 using iso from [http://www.fitzenreiter.de/averatec](http://www.fitzenreiter.de/averatec), Both wired and wireless establish connection and failed to get an ip, even manual configuration does not get me on the lan

---

### Post by Arne.F on 2007-06-05
Hi rojanu, 

Because i have nothing changed on the wireless part so i think you should check if your router accept connections from new networkcards. (Is there a mac-filtering list or similar functions active?)

Arne

---

### Post by phenest on 2007-07-03
> **Arne.F said:**
> I had similar Problems on my Averatec 2460. (8139too and sdhci crash the kernel)

8139too works if compiled without mmio support.

I have build a Ubuntu 7.04 Desktop CD with 8139too in Pio-Mode and without SDHCI.

[http://www.fitzenreiter.de/averatec](http://www.fitzenreiter.de/averatec)

Please try if this CD works also on your Philips Notebook.

Any chance of a direct download link to this. It's taking hours and hours via bit-torrent.

---

### Post by phenest on 2007-07-03
11 hours to download it, to be exact.

I managed to install Ubuntu (7.04) but it hangs when I try to start it. I guess there must still be one of those 8139too files there somewhere. Is there a way to achieve a command line to make amendments? Normally, I would use the Live CD. But not this time.

---

### Post by phenest on 2007-07-03
Ok. I can use the Alternate Live CD to get a BusyBox prompt. Is there any thing I can do from that to fix this?

P.S. I never found that /target/libs/... during installation.

---

### Post by Arne.F on 2007-07-05
Sorry. For the bad speed.
I have choosed bittorrent because i can only upload with 10KB/s, normal this is a good solution to provide large files to other users. But the most downloaders act's as leecher only. The images was downloaded 25 times and only three seeders are still active. So if you download it, let the torrent active to support the other downloaders.

Many users have also misconfigured the clients so that other users can't connect it. (Bittorrent port is not open from internet.)

If someone want to mirror the files please send me the links and i will add it to the website.

Arne

---

### Post by phenest on 2007-07-05
No worries. Got it downloaded after leaving it running all night. It installed a treat on my Philips x56. Many thanks for that.

Someone here mentioned about blocking the mmc module. What do I enter into the list? I found the Ubuntu updates re-install the mmc driver and you're back to square one (an unbootable system).

---

### Post by phenest on 2007-07-08
I forgot to install the patch for 2.6.20-16 kernel. Once done, boots up fine. If the kernel gets a further update, will it still boot ok, or will I need another patch?

Boot speed seems slow, and general use of the X56 seems slow too. Some of the screen savers run a bit sluggish.

How do I get the wireless working again? After installing the kernel patch, wireless disappeared completely! I've downloaded the drivers, but have no idea how to compile them. I tried following the instructions with no success. As someone who has never compiled anything before on Linux, can anyone supply me a step by step guide to get my wireless working again?

Oh, and is there a utility to configure my touchpad?

---

### Post by phenest on 2007-07-10
I've instaled gsynaptics to be able to configure my touchpad. To get the wireless working, I had to setup a WEP key (ascii) and enter the IP, submask, and gateway addresses.

Pretty much sorted now. Shame about the memory card reader not working.

This machine does seem to run a bit slow. Some screen savers are a bit sluggish and some apps take a while (up to a minute or 2) to load from the hard drive. Any one else had this problem?

---

### Post by phenest on 2007-07-21
If anyone is interested, I created a script to customize the Gutsy Tribe 3 CD that will work on the Philips X56.

The 2.6.22 kernel gives much better performance but there is no sound. Also, although I added a PIO version of the 8139too.ko module for the ethernet, it didn't use it, so the wired connection is useless. The card reader driver still doesn't work as before.

Does anyone have a fix for the sound? It works perfectly in Feisty, but silent in Gutsy.

I wish I had the 2.6.22 kernel in Feisty, but I don't have the patience to compile it.

---

### Post by derjames on 2007-09-14
Hello there...

has anyone upgraded the memory to more than 1GB on the X53 or X56? is it possible?

cheers

---

### Post by Arne.F on 2007-10-22
@derjames: Because the Averatec 2460 accept also a 2GB Module, so i think it is no problem to replace your 1GB DDRII with a 2GB Module because our Laptop has the same Mainboard.

@phenest: To get the sound back to work add a line "option snd-intel-hda model=acer" at /etc/modprobe.d/alsa-base

@all: H12Y-Modified 7.10 CD's are online now at [http://www.fitzenreiter.de/averatec/index-e.htm](http://www.fitzenreiter.de/averatec/index-e.htm)

Arne

---

### Post by amar on 2007-10-24
> **Arne.F said:**
> @all: H12Y-Modified 7.10 CD's are online now at [http://www.fitzenreiter.de/averatec/index-e.htm](http://www.fitzenreiter.de/averatec/index-e.htm)


Excellent thanks! this makes life with my laptop so much easier. 

thanks again for providing this

Amar

---

### Post by derjames on 2007-10-24
> **Arne.F said:**
> @derjames: Because the Averatec 2460 accept also a 2GB Module, so i think it is no problem to replace your 1GB DDRII with a 2GB Module because our Laptop has the same Mainboard.

Arne


yeap you are right... I was expecting to see two independent modules and buy just an extra GB...  cheers for that

---

### Post by neott on 2007-10-26
@Arne.F
I am Using the new 7.10 release from your site.
Runs like a dream, nice work :)

Has anyone managed to get the x59 running 1280x800 from kernel load?

---

### Post by amar on 2007-12-22
Is any one else having trouble after updateing? Since runing apt update on the 19th, I havent managed to get my x56 to boot, I tried reinstalling both kubuntu and ubuntu and in each case it works fine until I run an update and reboot.

In the past this was usualy due to a kernal update but it always gave me the option of useing the old kernal in grub.

---

### Post by vaalbygaardsvej on 2008-01-05
> **amar said:**
> Is any one else having trouble after updateing? Since runing apt update on the 19th, I havent managed to get my x56 to boot, I tried reinstalling both kubuntu and ubuntu and in each case it works fine until I run an update and reboot.

In the past this was usualy due to a kernal update but it always gave me the option of useing the old kernal in grub.

yeah i just updated aswell on a clean inbstall, got myself a non working ubuntu also. sigh :(

---

### Post by derjames on 2008-01-25
Hello folks, I hope all is well with you...
It seems that the guys at canonical are pretty aware of the bug affecting the boot up of Philips and Averatec laptops (X56 and similar). Basically they need your help to test the alpha version of the 'Hardy Heron' release to see if the problem is still there and report back the result to the bugs section at 'lauchpad'...

The full thread discussing the issue is here:

[https://bugs.launchpad.net/ubuntu/+source/linux-source-2.6.20/+bug/90271](https://bugs.launchpad.net/ubuntu/+source/linux-source-2.6.20/+bug/90271)

cheers
j

---

### Post by vaalbygaardsvej on 2008-01-26
thanks eversomuch for directing me.i senserely hope i can succede in running ubuntu on my machine again:)

---

### Post by vaalbygaardsvej on 2008-02-22
crud. still not working.. but they seem to have fixed the one bug..

---

