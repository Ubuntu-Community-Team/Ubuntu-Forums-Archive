---
title: "ubuntu install problems on brand new laptop"
date: 2009-10-30
forum: Installation &amp; Upgrades
---

### Post by kamiisama on 2009-10-30
hello, i'm new to the ubuntuforums' community but not to linux/ubuntu. today i bought a brand new laptop:
 
toshiba satellite l505d-s5983
basic specs - amd II (m300) 2.0ghz dual core cpu, 3 gigs ddr2 ram , 320 gb hd 

nothing special. ah and it came with windows 7! yaay....not so much, SO of course the FIRST thing i wanted to do when i got my brand new shiny laptop home was get rid of that pesky POS windows and put a REAL OS onto it! and what a coincidence ubuntu 9.10 just came out!! i figured it was meant to be~! but not so much.

SO here is my problem, tried an older distro (9.04) and didnt work, kept hanging before even getting into the install screen. so i scrapped that and tried 9.10, this time ...same thing, so i went poking around the bios (which has an advanced section about |   | <-that big) and found AHCI was messing things up, switched that and rebooted and YES! got to page 1/6 of the install! or so i thought, it locked up...tried restarting locked again...and again....sooo now i'm stuck with a $500 paperweight until the next big update? because i THINK it has to do with the drivers but again i'm not an expert...which is why i'm here..

SO please...any thoughts/advice/help? even stabs in the dark are greatly appreciated at this point! 
thanks~

---

### Post by dvlchd3 on 2009-10-30
Try alternative disc:

[http://www.ubuntu.com/getubuntu/downloadmirrors#alternate](http://www.ubuntu.com/getubuntu/downloadmirrors#alternate)

---

### Post by colinwhipple on 2009-10-31
I have the same laptop.  After disabling AHCI I was able to use the alternate text-based install.  But when I get to the main Ubuntu screen all input, mouse and keyboard, is ignored.

---

### Post by CalderCoalson on 2009-10-31
Do you have an Intel graphics card?  If so, you might have the same issue I'm having here: [http://ubuntuforums.org/showthread.php?t=1307886](http://ubuntuforums.org/showthread.php?t=1307886)

---

### Post by colinwhipple on 2009-10-31
No, my laptop has an ATI video card.

---

### Post by Dazed_75 on 2009-10-31
I spent most of today trying to install Fedora 10 or 11 on a Toshiba L505D-S5983 for someone else.  When I could not make those work the guy let me try ubuntu 9.10.  I did get it to work by adding "acpi=off" to the boot command.  Everything then worked fine until you try to shutdown.  Then it goes to a graphic pattern indication a graphic mode the cord does not understand and appears hung.  

But the install worked and the installed ubuntu works as long as you get the "acpi=off" clause into the boot line.  I was not sure the wireless was working either but that was not a priority today.

On the other hand, a clean install of 9.10 puts in grub2 which does not use /boot/grub/menu.lst and I have not yet learned how to edit the equivalent for grub2 to make a permanent fix.

---

### Post by colinwhipple on 2009-11-02
What did you do to get acpi=off in the boot line?  I was able to do the install, but don't know where to go from there.  I have tried a couple things at the Grub2 screen, but they don't work.

---

### Post by colinwhipple on 2009-11-02
I found some instructions for Grub2.  I pressed "e" and went into edit.  I tried three different times, putting "acpi=off" (without the quotes) in various places, then pressing CTRL-x to initiate the boot with the edited commands.  No luck; after logging in and entering "startx" I end up with a Ubuntu desktop that is non-responsive to keyboard and mouse input.  The system is not locked; the time updates as time goes by.

---

### Post by kamiisama on 2009-11-02
yeaaa nothing seems to work so far hah just suppose i'll have a nice shiny paper weight til the next big update? :(

---

### Post by Larry Linux on 2009-11-02
Many people have brought up the problem of 9.10 Live CD hanging just after boot - for example, once the CD boots up, it asks whether you want "to install"..or "use Ubuntu live". Unfortunately, no matter which option is chosen, the screen goes black with a white hash mark in the upper left corner of the screen once you choose which option you want.

I've tried numerous burns, six to be exact - at all 4x speed. I've even downloaded three separate ISO's, including two Ubuntu 9.10 and one Kubuntu 9.10. All have the exact same problem on computers with ATI graphics and Intel processors. On computers without ATI using AMD processors, this problem doesn't exist, and the CD works. Obviously, there is some type of driver recognition problem, or a problem with the kernel itself when using ATI/Intel.

I've never had this problem before with previous Ubuntu releases. In fact, previous Ubuntu releases worked as reliably as any os I've ever used. Hopefully someone at Ubuntu will read this and figure out what the problem is and get it resolved.

---

### Post by colinwhipple on 2009-11-03
With respect to the laptop which was the original subject of this thread, the Toshiba Satellite L505D-S5983, my guess is that it includes some new hardware which Unbuntu and some other distros can't handle.  Maybe future Linux releases will be able to handle it.

---

### Post by kamiisama on 2009-11-21
ok so i've been playing around with my shiny paperweight (lol?) for a few weeks now and tonight i actually got ubuntu 9.04 to install while logged into windows. so i thought yes!!! i've done it! but nope :confused: still doesnt work. so i tried rebooting and launching ubuntu (you actually get the selection while its booting like its teasing you that it actually may work this time!) and so i went into the boot menu and went to safe mode with graphics annnd it starts, hangs a sec, starts again then boom! crash and goes into an infinite loop:

ACPI Error (psparse_0524): Method Parse / Execution Failed [ \_GPE._L07] Node f6c15f48 AE_NOT_FOUND
ACPI Error (psparse_0358 ): Method Parse / Execution Failed [RSOF (<- and actually the o has the 2 '' over it)] Namespace lookup failure AE_NOT_FOUND
ACPI Exception (evgpe_0571): AE_NOT_FOUND while evaluating GPE method [_L07] [20080926]

dunno if this means anything to someone with a whole hell of alot more knowledge than me lol but i'm gonna take a stab in the dark and say THIS may be what's causing the hiccup while trying to install ubuntu onto this @^%@#$ laptop :?:

---

### Post by garvinrick4 on 2009-11-21
The original disc from Thread really sounds like to was BURNED at x24 and was not
such a good image. Burn one at 8x before you start to burn it will be an option. The slower
the burn the better chance of a pure image. I Know that is a fact because a am the choir.
Been there done that.

---

### Post by CalderCoalson on 2009-11-22
Actually, I just recently found out that the keyboard and mouse not responding aren't graphics card related but most likely a bug in gnome.  See this thread again: [http://ubuntuforums.org/showthread.php?t=1307886](http://ubuntuforums.org/showthread.php?t=1307886) .

---

### Post by colinwhipple on 2009-11-22
> **CalderCoalson said:**
> Actually, I just recently found out that the keyboard and mouse not responding aren't graphics card related but most likely a bug in gnome.  See this thread again: [http://ubuntuforums.org/showthread.php?t=1307886](http://ubuntuforums.org/showthread.php?t=1307886) .

It doesn't look to me like a Gnome problem.  After reading your message I downloaded Kubuntu, used unetbootin to write it to a UBS stick, and booted from that.  I ended up in the Kubuntu desktop with a locked mouse.

Colin

---

### Post by CalderCoalson on 2009-11-22
Huh...  Did you add 'i915.modeset=0' to the boot options?

---

### Post by colinwhipple on 2009-11-22
> **CalderCoalson said:**
> Huh...  Did you add 'i915.modeset=0' to the boot options?

Yep, did that.

Colin

---

### Post by Linux_Lurker on 2009-12-10
Hello,

I've been lurking around this thread for about a month, because I have the same laptop and the same problem.  Tonight, I finally fixed my Kubuntu 9.10 install by doing this:

At boot:

Hit 'e' to edit grub, change this line:

ro  quiet splash

to look like this:

ro acpi_os_name="Windows 2006 SP1" acpi_osi="Windows 2006 SP1" pci=noacpi hpet=off  quiet splash

it now boots up with minimal fuss.  Before I was using just acpi=off, I'd get only one core running, stuck at 2ghz.  Now, both cores work, and idle at 800mhz, and the temps at the CPU are way down.

To make permanent:

sudo nano /etc/default/grub

change this line:

GRUB_CMDLINE_LINUX=""

to look like:

GRUB_CMDLINE_LINUX="acpi_os_name=\"Windows 2006 SP1\" acpi_osi=\"Windows 2006 SP1\" pci=noacpi hpet=off"

now run:

sudo update-grub

now you have a laptop that works properly.  I haven't thoroughly tested every ACPI feature, but I believe it's finally good enough, I'm not going to cry if a few ACPI functions aren't working....

---

### Post by kingofnerds on 2009-12-13
I have performed the steps outlined in the previous post and everything seems to be working except the touch pad. Has anyone else had similar experiences?

ps, I am using mint 8 instead of ubuntu, but I figured how mint is based off of ubuntu it might work just fine. perhaps I will try with ubuntu instead.

---

### Post by Linux_Lurker on 2009-12-13
I found out later that the touchpad doesn't work, and I've found no good way of making it work, despite trying numerous different combinations of boot switches.  I hadn't noticed myself, because I always used a USB mouse, and never the touchpad.  I did find out that the touchpad apparently isn't getting picked up at boot time, possibly an IRQ assignment type problem, but nothing I tried was able to fix it.

EDIT:  I almost forgot, it turns out  that hpet=off isn't necessary, I'd omit that part...

---

### Post by kingofnerds on 2009-12-14
The only time the touch pad did work was when I used only the acpi=off and then I didn't get wireless

I am currently running the linux off of a sd card. From my research under windows trying to determine how the touch pad is connected, it is using a ps2 internal link. and as you stated, lshw doesn't show any ps2 ports in the laptop when using the pci=noacpi

---

### Post by colinwhipple on 2009-12-14
> **kingofnerds said:**
> The only time the touch pad did work was when I used only the acpi=off and then I didn't get wireless

I am currently running the linux off of a sd card. From my research under windows trying to determine how the touch pad is connected, it is using a ps2 internal link. and as you stated, lshw doesn't show any ps2 ports in the laptop when using the pci=noacpi

Same here.  My mouse works but not my touchpad with the alternate boot parameters.  With acpi=off they both work.

Colin

---

### Post by seenthelite on 2009-12-14
[QUOTE=kamiisama;8193470]hello, i'm new to the ubuntuforums' community but not to linux/ubuntu. today i bought a brand new laptop:
 
toshiba satellite l505d-s5983
basic specs - amd II (m300) 2.0ghz dual core cpu, 3 gigs ddr2 ram , 320 gb hd 

nothing special. ah and it came with windows 7! yaay....not so much, SO of course the FIRST thing i wanted to do when i got my brand new shiny laptop home was get rid of that pesky POS windows and put a REAL OS onto it! and what a coincidence ubuntu 9.10 just came out!! i figured it was meant to be~! but not so much.

If you got rid of that pesky POS windows ( which I assume was working perfectly ) have you found a REAL OS yet ? I have the same problem with 9.10 on a Toshiba P500 PSPG8A-01U004. Will 10.04 be any better ?

---

### Post by kingofnerds on 2009-12-22
I am still waiting for a patch or something that will allow me to not have to turn off my acip because like stated earlier in this thread, when I set acip=off, I only get the use of one core, and my cooling fan doesn't ever slow down. Also, in no mode have i been able to get my battery meter working. 

Has anyone else been able to get their battery meter working on this laptop?

---

### Post by Linux_Lurker on 2009-12-23
Just a quick update:

A few minor quirks were fixed by changing the acpi osi/osname to "Windows 2001".

Also, boot-up and shutdown were smoothed out considerably by adding:

pci=assign-busses   (it seems to circumvent a few pauses in the boot process, probably because of hardware errors and timeouts)

, and last but not least, they made it 3gb of ram by mismatching a 1gb and 2gb stick of ram, since my gf has the same laptop, I traded my 1gb stick for her 2gb stick, and now both laptops have snappier performance(she doesn't begin to use 2gb of ram, much less 3gb).

There were some toshiba laptop specific acpi fixes in the latest kernel, although I haven't tried it out yet.

Finally, I've gotten 32bit and 64bit Ubuntu and 32bit Kubuntu all running well enough, but 32bit Ubuntu wins for best/most reliable performance.

---

### Post by newbie84 on 2009-12-23
> **Linux_Lurker said:**
> Just a quick update:

A few minor quirks were fixed by changing the acpi osi/osname to &quot;Windows 2001&quot;.

Also, boot-up and shutdown were smoothed out considerably by adding:

pci=assign-busses   (it seems to circumvent a few pauses in the boot process, probably because of hardware errors and timeouts)

, and last but not least, they made it 3gb of ram by mismatching a 1gb and 2gb stick of ram, since my gf has the same laptop, I traded my 1gb stick for her 2gb stick, and now both laptops have snappier performance(she doesn't begin to use 2gb of ram, much less 3gb).

There were some toshiba laptop specific acpi fixes in the latest kernel, although I haven't tried it out yet.

Finally, I've gotten 32bit and 64bit Ubuntu and 32bit Kubuntu all running well enough, but 32bit Ubuntu wins for best/most reliable performance.

Hi, 
  Thank you very much. 
  I managed to install Ubuntu 9.10 (amd64) with acpi=off option on my  Toshiba L505D-S5983. Initially, it was hot, noisy and only a single core was active.  
  Now I have two cores running after following your instructions. The laptop is cooler than before and the processor becomes idle at around 800 MHz, but still a bit noisy. 
  I am using ATI catalyst driver for the IGP.  
The thing bother me most is the zombie size log files ( /var/log/kern.log.1 and /var/log/messages.1). Both files occupy about 3 GB hard disk space. 
  The reason is that the system is perpetually generating in the kern.log file the following 3 lines:  
   >    ACPI Exception: AE_NOT_FOUND, while evaluating GPE method [_L07] 20090521 evgpe-568  
ACPI Error (psargs-0359): [RSF] Namespace lookup failure, AE_NOT_FOUND 
 ACPI Error (psparse-0537): Method parse/execution failed [\_GPE._L07] (Node ffff8800ac62d780), AE_NOT_FOUND    Is there a workaround for this problem?

---

### Post by Linux_Lurker on 2009-12-23
Hello n00b :D

I know that ACPI errors are still happening, our best chance is for Toshiba/Insyde to release a BIOS fix.  ACPI errors are somewhat common, the only thing wrong with my laptop is that the touchpad doesn't work(which doesn't bother me, but does bother others).

You could manually dump your dsdt ACPI tables, then disassemble with iasl, and then fix yourself, but that is extremely difficult.  I made some attempt at it, I am a developer, but that's not really what I develop, I develop .NET applications for Active Directory *insert boos and hisses*

Also, after trying the Catalyst driver in the repository, I would recommend the latest 9.12 driver from here instead:

[http://support.amd.com/us/gpudownload/linux/Pages/radeon_linux.aspx?type=2.4.2&product=2.4.2.3.32&lang=English](http://support.amd.com/us/gpudownload/linux/Pages/radeon_linux.aspx?type=2.4.2&product=2.4.2.3.32&lang=English)

it fixed a number of graphics/compositing quirks, and (as far as I can tell) reduced system temperatures, which in turn decreased fan noise.  My laptop is more-or-less whisper quiet...

---

### Post by Linux_Lurker on 2009-12-24
Here is a courtesy cross-post from the other big thread on the internet:

********************************

Oh, here's my explanation of those:

pci=noacpi means:  do not use acpi for assigning pci IRQs

pci=assign-busses:  kernel will override any IRQ assignments done by the firmware


Currently, I can't get my touchpad or the software battery meters to work, but other than that, everything is fine.

Performance was somewhat increased by installing cpufreq-utils from the repository, and then converting these 2 rpm packages to deb packages using sudo alien -k [filename]

[http://support.amd.com/us/Pages/dyna...42f&ItemID=188]("http://support.amd.com/us/Pages/dynamicDetails.aspx?ListID=c5cd2c08-1432-4756-aafa-4d9dc646342f&ItemID=188")

[http://support.amd.com/us/Pages/dyna...42f&ItemID=101]("http://support.amd.com/us/Pages/dynamicDetails.aspx?ListID=c5cd2c08-1432-4756-aafa-4d9dc646342f&ItemID=101")

It seems to do a better job now of ramping up to 2ghz when you're actually doing something, 2d webpage scrolling and 3d compiz effects are both smoother. I can currently run a full-on compiz desktop without any issues, at acceptable FPS.

---

### Post by adam814 on 2009-12-24
> **Dazed_75 said:**
> I spent most of today trying to install Fedora 10 or 11 on a Toshiba L505D-S5983 for someone else.  When I could not make those work the guy let me try ubuntu 9.10.  I did get it to work by adding "acpi=off" to the boot command.  Everything then worked fine until you try to shutdown.  Then it goes to a graphic pattern indication a graphic mode the cord does not understand and appears hung.  

But the install worked and the installed ubuntu works as long as you get the "acpi=off" clause into the boot line.  I was not sure the wireless was working either but that was not a priority today.

On the other hand, a clean install of 9.10 puts in grub2 which does not use /boot/grub/menu.lst and I have not yet learned how to edit the equivalent for grub2 to make a permanent fix.

GRUB2 uses the files in the /etc/grub.d directory to build the grub.cfg file.  To append boot parameters for Ubuntu 9.10 edit /etc/grub.d/10_linux and find where the variable GRUB_CMDLINE_EXTRA is set and add the parameter you need (pci=noacpi or pci=assign-busses perhaps?) to it.  Then run (as privileged user) grub-mkconfig to re-build your grub.cfg.

---

### Post by Linux_Lurker on 2009-12-24
> **adam814 said:**
> GRUB2 uses the files in the /etc/grub.d directory to build the grub.cfg file.  To append boot parameters for Ubuntu 9.10 edit /etc/grub.d/10_linux and find where the variable GRUB_CMDLINE_EXTRA is set and add acpi=off to it.  Then run (as privileged user) grub-mkconfig to re-build your grub.cfg.

I'm guessing that you didn't read the rest of the thread before responding to that post.  I would definitely avoid acpi=off and use my instructions instead, acpi=off will cause the processor to be stuck at 2ghz, and only be able to use one core.  This will shorten battery life to about 1 hour, and keep your CPU constantly at ~60c.   After about 6 to 12 months of that, the CPU would probably crap out.  Desktops could handle being stuck at full speed, but laptops just can't dissipate that much heat on a constant basis.

---

### Post by Linux_Lurker on 2009-12-24
> **newbie84 said:**
> 
The thing bother me most is the zombie size log files ( /var/log/kern.log.1 and /var/log/messages.1). Both files occupy about 3 GB hard disk space. 
  The reason is that the system is perpetually generating in the kern.log file the following 3 lines:  
      Is there a workaround for this problem?

OK, I found a solution to the problem of log size:

run:

sudo gedit /etc/logrotate.d/rsyslog

go to the 2nd { bracket, the one that's preceded by a bunch of /var/log/* files, then change the word "weekly" to "daily".  This will cause those logs to be deleted everyday.

---

### Post by adam814 on 2009-12-24
Linux_Lurker, you are correct.  My post was more of a tangent and I'll edit it to reflect the inadvisability of running laptops with acpi off.

---

### Post by newbie84 on 2009-12-24
> **Linux_Lurker said:**
> OK, I found a solution to the problem of log size:

run:

sudo gedit /etc/logrotate.d/rsyslog

go to the 2nd { bracket, the one that's preceded by a bunch of /var/log/* files, then change the word &quot;weekly&quot; to &quot;daily&quot;.  This will cause those logs to be deleted everyday.

  Thanks,
  I did manage to trim the size of log files by assigning the size  (e.g. 10 MB) in 
/etc/logrotate.conf 
 and then executing 
 #logrotate -f /etc/logrotate.conf 
Definitely, changing it form weekly to daily basis will help further. 
LM sensor for AMD K10  is not working with ubuntu karmic. So, no temperature data. 
 With win7, the fan remains silent at idle but with ubuntu karmic (and winxp sp2), it revolves continuously at certain speed. 
 That's why it is noisy and a bit unpleasant.

---

### Post by Linux_Lurker on 2009-12-25
> **newbie84 said:**
> Thanks,
  I did manage to trim the size of log files by assigning the size  (e.g. 10 MB) in 
/etc/logrotate.conf 
 and then executing 
 #logrotate -f /etc/logrotate.conf 
Definitely, changing it form weekly to daily basis will help further. 
LM sensor for AMD K10  is not working with ubuntu karmic. So, no temperature data. 
 With win7, the fan remains silent at idle but with ubuntu karmic (and winxp sp2), it revolves continuously at certain speed. 
 That's why it is noisy and a bit unpleasant.

My fan is pretty quiet, I can barely hear it at idle.  IMHO, maybe someone (not me, I finally got mine 100% stable, LOL), should try OpenSUSE.  OpenSUSE will probably still need those boot switches to run, but since AMD sponsors OpenSUSE, I can't help but think that it would have better support for the latest AMD hardware than Ubuntu.  If anybody does try it, please post your findings back here.

---

### Post by colinwhipple on 2009-12-26
Lurker,

I am posting this from a Live bootup of the latest version of SUSE.  pci=noacpi as a boot option worked.  I haven't tried the other options yet.

There is no discussion of these problems with the L505D series Toshibas in the SUSE forums.  Maybe they are not having them, but that is not consistent with my experience so far.

Colin

---

### Post by kingofnerds on 2009-12-27
I have found a kernel bug that describes the problems that we are having with acpi, however I have not as of yet compiled my kernel with the patch.  If anyone wants to try it before I get around to it, the link to the kernel dev thread is here: [http://bugzilla.kernel.org/show_bug.cgi?id=14679](http://bugzilla.kernel.org/show_bug.cgi?id=14679) 

It appears as though the dscp table is being changed after it is initially read during boot.

---

### Post by buccaneere on 2009-12-27
> **kamiisama said:**
> yeaaa nothing seems to work so far hah just suppose i'll have a nice shiny paper weight til the next big update? :(

Huh? :confused:

Have you read the first 8 replies? Did you try any of them? :confused: If you did, what happened? If you didn't, what is this paperweight post about? :confused:

---

### Post by kingofnerds on 2009-12-28
I tried opensuse 11.1 live cd without any extra boot options, and yes, it still hangs.

---

### Post by kingofnerds on 2009-12-28
I was looking at the changelog for the next release of kernel [http://www.kernel.org/pub/linux/kernel/v2.6/testing/ChangeLog-2.6.33-rc2](http://www.kernel.org/pub/linux/kernel/v2.6/testing/ChangeLog-2.6.33-rc2) , and it appears as though there are a lot of acpi fixes. perhaps this will fix our problem of the acpi not working properly on this laptop? any thoughts?

---

### Post by colinwhipple on 2009-12-28
> **kingofnerds said:**
> I was looking at the changelog for the next release of kernel [http://www.kernel.org/pub/linux/kernel/v2.6/testing/ChangeLog-2.6.33-rc2](http://www.kernel.org/pub/linux/kernel/v2.6/testing/ChangeLog-2.6.33-rc2) , and it appears as though there are a lot of acpi fixes. perhaps this will fix our problem of the acpi not working properly on this laptop? any thoughts?

33-rc2 can be obtained from here for tryout:

[http://kernel.ubuntu.com/~kernel-ppa/mainline/](http://kernel.ubuntu.com/~kernel-ppa/mainline/)

I tried it over the weekend and it did not help.

Colin

---

### Post by kingofnerds on 2009-12-29
Ok, I guess I will continue waiting for a proper fix then while using the work arounds previously mentioned

---

### Post by kingofnerds on 2010-01-21
Just in case someone has not yet found the other thread tracking this problem, there is a fix

[http://ubuntuforums.org/showthread.php?t=1301101&page=8](http://ubuntuforums.org/showthread.php?t=1301101&page=8)

---

