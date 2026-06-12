---
title: "Nvidia 9600GT dual monitor boot up and power state issues"
date: 2010-07-25
forum: Hardware
---

### Post by johnnyis42 on 2010-07-25
Here's my situation:

nvidia 9600 GT dual monitors
lucid 68bit
AMD x4 940 8 GB ram

Prior to my upgrade to 10.04 this system functioned fine with the 185 nvidia proprietary drivers installed manually, and had done so since the 9.04 fresh install.  Power states worked fine, suspend and hibernate and I never had an issue with hanging on boot.

Upgrade to 10.04 resulted in me having to purge the old Nvidia drivers as re-compiling them consistently failed, so I switched to the restricted community maintained drivers.  I then started to experience the wearing down of my will to what felt like a bad race condition in upstart and/or xorg and the Nvidia drivers with my card... possibly exposed with my quad core system but I have nothing to base that on conclusively... when my machine would hang on boot up right before the gdm greeter was displaying.  Sometimes it wouldn't hang, and sometimes I had to reset my machine 10 times before I would get a login screen.

(un)fortunately a SATA cable failure resulted in me re-installing 10.04 from scratch on a different HDD, all other hardware the same.  This time with a clean install and Nvidia restricted drivers the problems with boot up were not as bad, but still present, and resuming after suspend would almost certainly cause gdm to crash and upstart to restart gdm, and that was the times that X didn't lock my machine at 100% cpu (only one core) with blank screens and maybe ssh access... and when I could ssh in I couldn't kill X.

Eventually I found the simple fix to install the drivers off nvidia.com, and at first the problems seemed to subside, but it turned out they were just a little different, and it all seemed to revolve around something AFTER loading the driver module... maybe power/acpi related (the gpu fan spun down consistently on the fresh install), and only using one monitor didn't seem to change anything.

Fed up I went to install Debian and build my own system my way, damn the torpedoes.. but after removing the nvidia card to use my onboard ATI video for the life of me I couldn't get lenny to load the drivers for the ATI HD 3300.... and I realized I probably needed to be installing squeeze and I then realized I bought myself a ton of other issues I was hoping wouldn't come up... and then the miracle of miracles happened... I loaded up my old ubuntu install, uninstalled the nvidia driver, apt-get install fglrx (after failing to install the ati proprietary drivers and removing them), and viola, dual monitor, suspend works fine, startup never hangs... 

So it seems it was the nvidia driver on lucid the whole time it seems.  Now the point of this post:  am I the only one who has had to deal with this?  I see a lot of reports about 10.04 splash screen in low res hanging for people, but all the fixes were supposedly implemented.  At this point I'm not sure I can submit a helpful bug report, and I'm not even certain this wasn't my hardware causing the problem.

---

### Post by nerdy_kid on 2010-07-25
ive had some fun with my nvidia since 8.04:
first vsync wouldnt work -- found out i needed to add a script to /etc/X11/Xsession.d to invoke nvidia-settings -l.  that was hardy.

all was fine through 9.04.

then i got seg faults resuming kde from suspend -- took me months but was a bug in the nvidia drivers that kwin triggered when i suspended with compositing disabled.  -- karmic & lucid -- i reinstalled lucid and that went away.

then i had the ugly plymouth splash to deal with -- had to add a few lines to grub's config. -- lucid

currently my mouse lags in games...another nvidia bug.

but on the bright side, the driver's performance has been getting noticeably faster with each update since 180, and VDPAU works nicely for me.  No fan issues, no power saving issues.  And screen rotation works :D


all in all, yeah its been a pain in the butt.  but nvidia is not all to blame -- ubuntu could do a little more to integrate the drivers -- i.e. the splash issue and the vblank syncing.  However; the drivers have behaved much better then they did in vista -- that was BSOD every other day for me.

---

