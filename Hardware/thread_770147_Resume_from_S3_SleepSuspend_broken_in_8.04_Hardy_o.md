---
title: "Resume from S3 Sleep/Suspend broken in 8.04 Hardy on Sony Vaio TZ"
date: 2008-04-27
forum: Hardware
---

### Post by queno on 2008-04-27
Hi!

I did a fresh & clean Hardy install yesterday and have since then wasted more than 20h on trying to fix a very new suspend-problem.

With Gutsy Gibbon on the same laptop (Sony Vaio TZ21MN/N), suspend & resuming from it worked fine after fixing a problem with the uvcvideo-module and a problem with the soundcard. All of that is already documented in the forums.

For Hardy, I also had to use the fix for the uvcvideo-module (removing it) in order to get the laptop to s3 sleep/suspend. That's OK.

BUT: Now - in Hardy - trying to wake up the laptop results in a black screen with no reaction whatsoever. And the strangest thing is that NO logfile actually notices that the machine was supposed to wake up!

It is logged that the device goes to sleep & outputs the messages respectively. But the very next thing the logfiles document is a cold restart I had to force via power-button because the laptop would not successfully wake up from s3 sleep/suspend.

So I basically have nothing to go on! What causes this problem? Which module? What hinders the laptop from performing the resume-procedure? I sure don't know because there's no output whatsoever!

Please help me if you can! Besides having a working wifi-connection, sleep-mode is the most important thing for me!

Thank you for your help!

---

### Post by razorbuzz on 2008-05-01
I'm having exactly the same problem, with the added confusion in the fact that I turned SUSPEND and SLEEP off.  The only thing I have going to sleep is the display, but the problem persists.  Upgrade & clean install both exhibit the issue.

---

### Post by queno on 2008-05-02
For people having the same problem, I can put together what I have found out so far:

[LIST]
[*]Sleep does not work, but hibernation (Suspend to Disk) does
[*]Without changes, the Sony Vaio TZ cannot enter Sleep-Mode because of the uvcvideo-module
[*]Blacklisting the uvcvideo-module, rmmod'ing it or using any other way to get rid of it before trying to enter sleep-mode will enable the Vaio TZ to successfully ENTER sleep-mode
[*]The trouble so far is that there is NO way to get the Vaio out of sleep-mode
[/LIST]

Trying to wake up the sleeping beauty results in a active powerswitch-light and a fan that acts as if the system was actually back on - But it isn't.

It is NOT the case - like I've read with other laptops, e.g. Dell - that the backlight is simply off and typing in your password at the blank screen actually brings the device back.

The Vaio TZ simply does not resume. Pressing CTRL+ALT+F1-7, ALT+Sys+K, CTRL+ALT+Backspace or CTRL+ALT+Delete does not lead to anything. The system is completely gone. The only thing one CAN do is press the powerbutton for > 4 seconds to shutdown the laptop and do a restart.

While trying to debug sleep-mode, I found out that my Vaio has some more problems with modules aside from ucvideo. So, if you own a Vaio TZ, you might want to add the following lines to /etc/modprobe.d/blacklist:

blacklist uvcvideo
blacklist intel_rng
blacklist iTCO_wdt

Save & restart. Then all modules producing errors are gone & there's no downside to it (as far as I've researched this).

Further research has brought me to believe that what's actually going wrong is the restore of VBEstate. I've since then toyed with every possible acpi-support configuration setting, I've tried to amend vbe-restore options to my menu.lst for boot-up, debugged 80-video-vesa-state and more. But all to no avail.

The only thing that made a very, very slight difference is if I command my laptop to enter sleep mode by entering:

pm-suspend --quirk-vbemode-restore --quirk-s3-bios 

into a terminal. The difference that makes is that after trying to resume, I'm greeted with a black screen + blinking cursor instead of a completely black screen. I can then hit CTRL+ALT+F1 to get a terminal and then kill off GDM in order to get my laptop back without forced reboot. Of course this isn't how it should be. Switching back from the terminal of CTRL+ALT+F1 to F7 (X-Session) makes the system hang just like the rest of the time: black screen, absolutely no reaction.

So, what I need now is a really smart gall/guy, who can tell me just wtf pm-suspend --quirk-vbemode-restore --quirk-s3-bios does differently, why it had absolutely no effect when I - after discovering that line - added it to my boot parameters as "acpi_sleep=s3_bios" and just how I'll debug the whole darn thing in order to get back successfully from sleep-mode.

I really need that sleep mode + resume. 
I am desperate and wasted more than 30h on this already.
I'm beginning to think that this is actually worth some money to me.

Please help me fix this. It is unbelievably annoying having been an Ubuntu-evangelist for almost three years and now that 'normal' people around me are actually starting to use it and tell me how great Hardy Heron is being the one guy whose laptop actually SUCKS thanks to Hardy.

Don't get me wrong. There's so much good stuff in Hardy! But more than an hour less of battery-power just because of a new distribution? WTF? And everybody seems to have sleep & hibernate now - even on 6-year old laptops. Just my oh-so-lousy Sony Vaio gets broken from Gutsy to Hardy. What's up with that?!

---

### Post by razorbuzz on 2008-05-04
Our problems appear to be different.  The problem I was having seems to have prevented the computer from actually going to sleep, although it gave all the appearances.

My problem had to do with trackerd and beagled conflicting with one another and trying to index concurrently.  Uninstalled Beagle and now all is copacetic.

---

### Post by thorbjornw on 2008-05-06
I have just make a clean install of Ubuntu 8.04 (64 bit version) on a new Vaio VGN SZ 750N.  Most (but far from all) is working OK,but I couldn't get the suspend/hibernation to work, which I think is vital for a laptop. 
After using the whole day, and getting s2both to work for hibernation by installing uswsusp and changing the uswsusp configuration file (to device=my swap file),but only from a terminal window,I finally came over your proposal to blacklist the uvcvideo module.  That worked - now my laptop both suspends and hibernates.  If it has some consequences for the webcam has still to be seen.

---

### Post by queno on 2008-05-25
After spending far too much time on this problem, I finally solved it!

You have to blacklist the uvcvideo-module like I described in my earlier post.

You then have to add the line

options snd-hda-intel probe_mask=1

to your /etc/modprobe.d/alsa-base. Save it & enjoy a sleeping Sony Vaio.

This damned error had me on the wrong track for many hours... Why the hell is a Conexant 56K-Modem driver confusing a Intel onboard soundcard when waking up from sleep so that the whole screen stays black & the system dies which makes it look like something much less trivial!?! WTF?

---

### Post by oguzy on 2008-06-21
Hi queno,

I have the same problem with my laptop and trying to solve it. It is not a Sony. It is a laptop that is a kind of collected type, that is no brand but some collection of different oem devices.

I want to learn that how you found the solution. How did you find which modules should be blacklisted?

I save the output of the dmesg before suspend and after suspend. Maybe you can check and give me a clue.

I tried many different solutions but none worked. My problem about suspend is that, when i open the laptop and press suspend button it goes off and suspends itself. When i press the power. it wakes up and i can see my desktop back again. But when i try suspending again, it goes off and pressing the power doesnt wakes it up. The power led flushes like it is waked up but i dont see my desktop, just a blank screen. So i had to press the power button and wait for the shutdown. So same problem with you. But i dont know where the problem is.

I put some log outputs. Will be happy if you give some clues or guide.

dmesg at the firs login to desktop: [http://pastebin.ubuntu.com/21805/](http://pastebin.ubuntu.com/21805/)
dmesg after suspend and relogin to desktop: [http://pastebin.ubuntu.com/21807/](http://pastebin.ubuntu.com/21807/)
/etc/default/acpi-support: [http://pastebin.ubuntu.com/21808/](http://pastebin.ubuntu.com/21808/)
/etc/modprobe.d/blacklist: [http://pastebin.ubuntu.com/21809/](http://pastebin.ubuntu.com/21809/)
lsmod: [http://pastebin.ubuntu.com/21810/](http://pastebin.ubuntu.com/21810/)
lspci -vvvv: [http://pastebin.ubuntu.com/21811/](http://pastebin.ubuntu.com/21811/)
uname -a: Linux some-laptop 2.6.24-19-generic #1 SMP Wed Jun 4 16:35:01 UTC 2008 i686 GNU/Linux
# cat /etc/lsb-release 
DISTRIB_ID=Ubuntu
DISTRIB_RELEASE=8.04
DISTRIB_CODENAME=hardy
DISTRIB_DESCRIPTION="Ubuntu 8.04"

I also tried the solution here, but didnt get any result: [http://blog.vaxius.net/?p=19](http://blog.vaxius.net/?p=19)

xorg.conf: [http://pastebin.ubuntu.com/21812/](http://pastebin.ubuntu.com/21812/)
i am also using 915resolution.

---

### Post by auspex on 2008-06-24
> **queno said:**
> After spending far too much time on this problem, I finally solved it!

You have to blacklist the uvcvideo-module like I described in my earlier post.

You then have to add the line

options snd-hda-intel probe_mask=1

to your /etc/modprobe.d/alsa-base. Save it & enjoy a sleeping Sony Vaio.

This damned error had me on the wrong track for many hours... Why the hell is a Conexant 56K-Modem driver confusing a Intel onboard soundcard when waking up from sleep so that the whole screen stays black & the system dies which makes it look like something much less trivial!?! WTF?

First, don't blacklist modules: use the inbuilt support to remove them before hibernation and reload them afterwards.  For acpi-support, this is SUSPEND_MODULES= in /etc/default/acpi-support.  For pm-utils, it's MODULES= in 
/usr/lib/pm-utils/defaults.

Second, the reason why a Conexact modem driver confuses a sound card is simple - many, if not all, of the Winmodems are extensions of the onboard sound card.  That's what makes them so cheap.

---

### Post by Konradbaniel on 2008-12-19
It was working fine on my TZ with Hardy. Then I upgraded to Intrepdid. Still working except with AC Power. Then after a new upgrade under Intrepdid, my VAIO TZ accept suspend to ram but dont wake up (black screen).

Any idea?

Konrad

---

### Post by aveminus on 2010-07-15
> **queno said:**
> After spending far too much time on this problem, I finally solved it!

You have to blacklist the uvcvideo-module like I described in my earlier post.

You then have to add the line

options snd-hda-intel probe_mask=1

to your /etc/modprobe.d/alsa-base. Save it & enjoy a sleeping Sony Vaio.

This damned error had me on the wrong track for many hours... Why the hell is a Conexant 56K-Modem driver confusing a Intel onboard soundcard when waking up from sleep so that the whole screen stays black & the system dies which makes it look like something much less trivial!?! WTF?
@[queno]("http://ubuntuforums.org/member.php?u=224794"):

Thanx for the solution. My Vaio sleeps well now :D

---

### Post by poserslipjack on 2010-07-15
Hey, it looks like I'm not the only one trolling year-and-a-half old forum threads for a solution to this issue. :) Unfortunately, queno's solution didn't seem to do the trick for me.... 

Did you use /etc/modprobe.d/blacklist.conf or one of the suspend-specific config files (/etc/default/acpi-support or /etc/pm/config.d/<whatever>) to disable uvcvideo? 

Did you also do the "options snd-hda-intel probe_mask=1" trick in /etc/modprobe.d/alsa-base.conf? 

Anything else? (Modifications to the grub boot line, etc.?)

I'm on a Vaio P Series (Ubuntu 10.04 normal edition on a VPCP118KX), so it might be a different issue, but...the symptoms sure sound identical.

Thanks.

---

