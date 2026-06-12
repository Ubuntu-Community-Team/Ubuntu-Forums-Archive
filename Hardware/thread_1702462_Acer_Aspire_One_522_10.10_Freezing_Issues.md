---
title: "Acer Aspire One 522 10.10 Freezing Issues"
date: 2011-03-07
forum: Hardware
---

### Post by Shanfara on 2011-03-07
I just picked up a 522 today and installed Ubuntu 10.10 desktop to get rid of Windows 7 starter. After getting past the installation issues (have to install from live cd with thumbdrive, won't do it directly from the boot list) I got the Radeon drivers installed (watermark included, will fix later)and then ran into a massive issue. Within five minutes of EVERY reboot, the kernel (I am assuming) crashes completely. It is always within 5 minutes. I have checked the smiles and frowns thread as well as the phoronix forum with no luck. This is extremely frustrating and the word on the street is that the wireless driver is the culprit. Question to the more experienced Ubuntuites out there- What are my options and how can I fix this?

I have tried running off wireless and wired connections. The system won't stay stable long enough to update. I am basically screwed.

---

### Post by md80hb-iuh on 2011-03-10
Got about the same issue at the begining. I was not able to run the update it was freezing up at random. I've tried 9.10 and 10.10. I've messed around so much that I've to start a clean install with Ubuntu Netbook Remix 10.10. and I was able to perform the updates. Before this it was dropping network (wifi at random) and wired port was inop.

I've fixed the waterwark by loading the new 11.2 driver from ATI  available here [http://support.amd.com/us/gpudownload/linux/Pages/radeon_linux.aspx](http://support.amd.com/us/gpudownload/linux/Pages/radeon_linux.aspx) . To install save the file, do a chmod +x file_name and run it. Take all default answers. However performance full screen for video is bad compared to the previous driver (do not recall the one I had before).

So far things working are:
-Skype = Works, used a Pro9000 webcam. Integrated webcam works fine too.
-Empathy = Works

So far things not working are:
-Can't get out of sleep mode.
-Random freeze  after login. It will freeze within 2 minutes. Passed that will it run forever.
-Headphones: If you plug the headphones in , the speaker is still working.

Things to be checked:
- Card reader.

Suspicious: 
- Hard disk LED drive sometimes always active, but if I reboot in windows 7, she's always lit too. This is recent, was not doing it 1 week ago. Seems related to the way I've rebooted the machine when she was freezing.

---

### Post by 5tj on 2011-03-13
Same freezing here on acer aspire one 522.

Installed Ubuntu Desktop 10.10 for amd64 from alternate installer DVD using a USB DVD drive without a problem.

Do not remember if there was a freeze after installation in this phase (800x600 screen resolution).

Activated fglrx driver from Ubuntu archives (with "unsupported hardware" watermark) - Random freezes.

Updated fglrx driver to latest available on ATI website (no more watermark) - random freezes.

Completely deinstalled all fglrx packages and deleted /etc/X11/xorg.conf (back to 800x600) - random freezes

Upgraded memory - now 4GB. Random freezes.

Upgraded Ubuntu to 11.04. Surprisingly, the update process ran without a single freeze - until I tried to shut down after the upgrade was finished.

Freezes got even worse after that. 

Tried to install fglrx driver in 11.04, but it won't compile for the kernel in 11.04 (neither the one in Ubuntu nor the latest from ATI).

The worst: The netbook froze while still in grub, editing the kernel command line to delete the "quiet splash". So the freezes are not even linux related? However, Windows 7 starter has not frozen even once.

Another observation: Netbook gets very hot under the VGA connector while linux runs. Not so in windows.

---

### Post by andi666 on 2011-03-13
Same problem here. 10.10 32 bit.

Tried kernel 2.6.35, 2.6.37 and 2.6.38-rc8 (with patch for frglx to compile)

Strage thing is that I could use a full battery charge before ubuntu first froze. Now I barely come past the gdm login screen.

I also noted that battery life is far worse than in windows.

This really really sucks. I bought this for ubuntu. My systems normally are 100% pure ubuntu. Now for the first time in my life I am forced to use windows. ugh.

---

### Post by 5tj on 2011-03-13
More data: The freeze in grub occurs in command line editing mode when pressing ctrl+k.

There are different kinds of freezes in linux. Sometimes only screen & keyboard freezes, but the computer remains accessible via ssh and can be shut down this way. Sometimes, also the network is inaccessible.

I tried removing more drivers. I completely removed the radeon driver and the ath9k wireless driver by removing all corresponding kernel modules from /lib/modules and from the initrd filesystem. The system is still freezing regularly.

Summary: This netbook is not usable with linux.

---

### Post by manticoretrader on 2011-03-13
The laptop is very usable with Linux, you are welcome to follow my guide: [http://www.manticore-projects.com/content/en/software/guides/aspire522.htm](http://www.manticore-projects.com/content/en/software/guides/aspire522.htm)

However there are three issues: it freezes when shutting down the wired network (e.g. "ifconfig eth0 down" --> freeze), which seems to be related to the network driver. Also I could not make the internal mic working, neither bluetooth.

Best regards!

---

### Post by andi666 on 2011-03-14
Do you have any idea why it freezes for us?

It could be possible that you have an earlier hw revision. Mine was sold beginning of march and manufactured in January 2011. There are versions with broadcom wlan chips, maybe some other revisions with more changes. I dont know.

The only difference I see judging from your howto is that you use the free display drivers.

Thanks for your HOWTO anyway. I will follow it and see what happens.

---

### Post by andi666 on 2011-03-14
For those of you who still have the windows 7 starter partition and istalled ubuntu after resizing it, here is something I want you to test:

1) power your computer off.
2) start windows 7, log in
3) restart your computer (do not shut down, reboot)
4) boot into ubuntu, login

I had crashes as soon as I entered username and passwort in gdm before. Three times is a row I was unable to see the desktop. After trying the steps above. I was unable to freeze ubuntu (running for 3 hours now)

This might be a cooincidence, but please try anyway.

FYI, my configuration:
Ubuntu 10.10 32 bit
2.6.38-rc8 kernel (natty version from the mainline ppa)
latest ati drivers (8.21) with patch for 2.6.38

---

### Post by manticoretrader on 2011-03-14
The freezing comes from the ethernet-module. The ath1c is famous for freezes. Try it out: ifconfig eth0 down --> freeze.  Do not start any eth0-related services when starting up and point your Networkmanager to different device (/dev/null). Since then I had no freeze anymore.

---

### Post by andi666 on 2011-03-14
Thanks, you are right.

This is what I did

edit /etc/modprobe.d/blacklist.conf and add the follwing line
```

blacklist atl1c

```

then run 
```

update-initramfs -u

```

No crashes so far, even without the "windows 7 trick".

Seems we have two options now
1) boot windows 7 first, then reboot into ubuntu
2) blacklist the atl1c module 

I chose 2 because I dont need ethernet.

Thanks to everyone examining the issue

---

### Post by GenBattle on 2011-03-14
> **andi666 said:**
> Do you have any idea why it freezes for us?

It could be possible that you have an earlier hw revision. Mine was sold beginning of march and manufactured in January 2011. There are versions with broadcom wlan chips, maybe some other revisions with more changes. I dont know.

The only difference I see judging from your howto is that you use the free display drivers.

Thanks for your HOWTO anyway. I will follow it and see what happens.

I also bought one of these laptops just this week (in New Zealand) and mine comes with the Broadcom wireless chip (which works fine under OpenSuse 11.4) and an Atheros ethernet chip. Both won't work in Ubuntu 10.10, and i get strange issues with the graphics in 11.04 Alpha which prevent gdm or unity from starting (switching to the ATI driver makes both Suse and Ubuntu unbootable).

So to conclude: graphical driver issues with OpenSuse 11.4 (KDE desktop), AMD CCC 11.2 drivers will not install properly.

Ubuntu 11.04 Alpha 3 installs, but gdm and unity won't start, installing AMD driver 11.2 (CCC) prevents ubuntu from booting. Due to the graphical issues I haven't been able to determine whether wlan or ethernet work.

Ubuntu 10.10 installs and run in 800x600 graphics mode, ethernet and wlan both not working.

---

### Post by GenBattle on 2011-03-14
Just tested OpenSuse 11.4 GNOME with no issues.

It's a little bit faster than KDE (a no-brainer i guess), and seems to be just as stable on the Aspire One 255. On mine the wireless and wired networks work fine under OpenSuse, and it has no problems resuming from sleep.

If you're looking for a relatively easy way to get your 522 up and running with linux, i recommend OpenSuse 11.4. In the meantime, hopefully Ubuntu 11.04's hardware support will improve as it gets closer to release.

EDIT:
Not completely true, i'm now getting freezes after startup. This seems to have started when i set up a default wireless network to connect to on startup.

---

### Post by 5tj on 2011-03-15
I can confirm that the netbook does not freeze in linux after direct rebooting from windows 7 to linux.

I have reactivated the open source radeon driver.

I also had deactivated the atl1c driver. Now I am missing the network manager applet and the battery applet from the panel. I found that I can start the network-manager applet by invoking nm-applet, still searching for the battery applet. And for the reason why they are suddenly missing.

reactivated the atl1c driver, but the applets are still missing. Booting through windows 7 first and then rebooting still works but is rather inconvenient.
 
System is now Ubuntu 11.04 alpha 3 amd64. Notebook still gets very hot. in the area of the VGA connector.

May after all not be worth the trouble. Still have to try Cardreader, VGA and HDMI output.

---

### Post by GenBattle on 2011-03-15
Posting this from my Aspire One 522 running Linux Mint 10. Both Linux Mint 10 and Ubuntu 10.10 do seem to work ok with the Atheros/Broadcom version of this netbook.

Start with a standard install, reboot (it will be running at 800x600). Then just install both the ATI and Broadcom restricted drivers from the restricted driver manager, restart. Install the latest AMD graphics driver (11.2).

It seems half the problem is because of a mix of the new kernel and the non-binary drivers for network cards and video cards.

Haven't had any issues with overheating yet with all the drivers installed, although last night while i was installing Ubuntu it got very very warm.

---

### Post by Lngly on 2011-03-17
I also aqcuired one of the 522s and I have the same freezing problem with ubuntu 10.10 netbook edition.
I tried blacklisting the ethernet but it didn't seem to help. Any other ideas?
I have freezes even after rebooting from Windows into Ubuntu.

---

### Post by andi666 on 2011-03-17
> **Lngly said:**
> 
I tried blacklisting the ethernet but it didn't seem to help. Any other ideas?

Strange, did you regenerate your initramfs?
if you havent it wont have any effect.
check if it is really not loaded by typing
```
lsmod | grep atl
```

> **Lngly said:**
> 
I have freezes even after rebooting from Windows into Ubuntu.
Hmm, for me either of the two workaround works. I have never had a single freeze since I blacklisted the ethernet module.

Under the VGA connector the netbook does not get hot for me.

I use kernel 2.6.38-rc8 and catalyst 11.2 with patch for 2.6.38 compatibility, maybe this makes a difference...

---

### Post by Lngly on 2011-03-17
I'm currently sending the thing back because the screen flickers but I'll check once I receive it again.
Thank you :)

---

### Post by jason.s on 2011-03-19
I too have issues after blacklisting the ethernet.  

lsmod | grep atl produces no output, which means it is in fact not loaded.

The freezing seems very frequent when running on battery.  I don't think I've seen it running plugged-in.  As soon as I unplugged it though, it froze.  It doesn't last long without freezing when unplugged... 

Any ideas or is there anywhere I can look that might give me more information as to why this is happening?

---

### Post by vladilinsky on 2011-03-19
I have a aspire one 522 with a broadcom chipset.  I am currently running kubuntu 10.10 with kde 4.6.1 and the display drivers from 

ppa:ubuntu-x-swat/x-updates   

and the kubuntu backports enabled from

ppa:kubuntu-ppa/backports

I also copied the control file copied from the newest ati driver (this is really important, before doing this it would freeze up and it gets rid of the annoying watermark in addition to really speeding up the netbook)

every thing works great now and the performance seams really snappy (I have only had this for 2 days so I may be in for disappointment yet)  The biggest hassle was the sd card reader which does not work out of the box but if you follow comment #138 on this page [https://bugs.launchpad.net/ubuntu/+source/linux/+bug/530277](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/530277)   it will work.  

If you need any more info from me I will do what I can to help

---

### Post by andi666 on 2011-04-14
I just updated by BIOS to 1.07 (downloaded from the acer homepage). I had not much hope because the changelog does not say anything about ethernet.

But after updating I could actually unload the atl1c module whithout a total system freeze. I stopped blacklisting the module and had no freeze since I upgraded the BIOS.

It is too early to say that the problems are solved, if I dont edit this post soon, assume that it is fixed...

Oh and by the way, in Ubuntu 11.04, everthing seems to work out of the box, closed source ati drivers, cardreader, bluetooth, etc. :)

**EDIT: I was stupid, the atl1c device was still "healed" by Windows 7 :/ Things dont get better by flashing the BIOS. If you really need ethernet in ubuntu, you have to boot in Windows 7 once and then reboot to ubuntu**

---

### Post by tigrezno on 2011-04-15
My problem with this netbook is CPU fan not working at all.

After some intensive process, it just shut downs.

Is it happening to you?

Also, do you know how to reinstall win7 starter? alt+f10 not working

---

### Post by mök on 2011-04-18
> My problem with this netbook is CPU fan not working at all.

> After some intensive process, it just shut downs.

> Is it happening to you?

No. Pretty hot air gets blown out of the slits between VGA and USB slots on the left. 
That air is much cooler when running windows.

> Also, do you know how to reinstall win7 starter? alt+f10 not working

I don't know what alt+f10 is supposed to do. You just reinstall it from the backup dvds that you created before installing Linux, using a USB DVD drive. Boot order can be changed in BIOS setup.

---

### Post by mök on 2011-04-18
Thanks for the tips in this thread. I was able to get Ubuntu 11.04 amd64 running without eth0.

I notice that the screen flickers heavily in linux when it had been blank for some time. The flickering stops again after a few minutes. Strange, I had thought the display light would come from LEDs, but this behaviour reminds me of fluorescent lamps.

Does not happen when running windows. Also does not happen in linux when the netbook was switched off or suspended. Only happens when the netbook was running but screen blanked due to inactivity.

---

### Post by herr-k on 2011-04-18
All network related freezing issues seems to be gone in 11.04 after latest updates. Even overheating is fixed. Everything seems to work smoothly and without any segmentation faults.
Ecxept:
[LIST]
[*]suspend-mode (at least with catalyst drivers)
[*]audio connectors
[*]HDMI sound (someone said it's working though)
[/LIST]


> **tigrezno said:**
> 
Also, do you know how to reinstall win7 starter? alt+f10 not working
Grub creates a menu item in boot menu for windows recover partition during installation. Of course only if you didn't partition whole disk for ubuntu exclusively.

**Edit:**
Unfortunately after today&#8217;s update of 11.04 beta everything returned to former status. I.e. i had to blacklist ethernet device again.

---

### Post by tigrezno on 2011-04-19
The blacklist thing really works, no more freezes when opening gkrellm for example.

pm-suspend works great with xorg ati driver

Is there any cpu frequency trottle support??? I can't find it on /sys

Also, how do you change screen brightness? (using linux and not fn-keys)

---

### Post by cubeist on 2011-04-19
> **herr-k said:**
> 
[LIST]
[*]HDMI sound (someone said it's working though)
[/LIST]


Install Pulse Audio Volume Control, select your HDMI as output, BAM!

---

### Post by herr-k on 2011-04-20
> **cubeist said:**
> Install Pulse Audio Volume Control, select your HDMI as output, BAM!
Indeed. It work's! My bad not thoroughly checking monitor's audio jacks. And pavucontrol still the best API for pulseaudio for sure.

Also checked suspend mode with xorg-driver and it worked three times in series. Of course for lack of graphic performance. Call me old school: I can live without suspend-mode.

---

### Post by 5tj on 2011-04-20
> **tigrezno said:**
> Is there any cpu frequency trottle support??? I can't find it on /sys

Right click on panel, Add to panel, CPU Frequency Scaling Monitor. Using this applet, you can choose the CPU frequency directly or one of 4 "governors". Won't help much, though, only 800 MHz and 1 GHz are available.

---

### Post by tigrezno on 2011-04-23
> **5tj said:**
> Right click on panel, Add to panel, CPU Frequency Scaling Monitor. Using this applet, you can choose the CPU frequency directly or one of 4 "governors". Won't help much, though, only 800 MHz and 1 GHz are available.

Don't know how it's working on gnome since I can't find any support on /sys about cpu scaling

I use openbox btw, that's why I need to directly touch /sys

Can you check wich kernel module is giving you scaling support?

Should have "freq" in it.

Thanks

[edit]

nevermind, i found it! powernowk8 module

---

### Post by tigrezno on 2011-04-27
can't get hdmi sound to work

pavucontrol works, and I can select hdmi sound output for play, but I can't hear anything

it's not muted btw

---

### Post by md80hb-iuh on 2011-05-06
Since my last post I've installed Ubuntu 11. ATI catalyst does not work any more and I have poor video playback (regression)

I still have random freeze but this is only when I'm not plugged on A/C power. If I go on battery it will freeze within the two minutes of use. Passed 2 minutes  it will continue working regardless of wifi settings (on or off). Checked and rechecked all the power management with no luck.

On battery it will not freeze if I'm wired ethernet.

Still problems with audio jack, mic and card reader.

I have several environment installed on it (Ubuntu, Kbuntu, Netbook remix) and they all behave the same way. Yes all updates have been run.

---

### Post by tigrezno on 2011-05-06
> **md80hb-iuh said:**
> Since my last post I've installed Ubuntu 11. ATI catalyst does not work any more and I have poor video playback (regression)

I still have random freeze but this is only when I'm not plugged on A/C power. If I go on battery it will freeze within the two minutes of use. Passed 2 minutes  it will continue working regardless of wifi settings (on or off). Checked and rechecked all the power management with no luck.

On battery it will not freeze if I'm wired ethernet.

Still problems with audio jack, mic and card reader.

I have several environment installed on it (Ubuntu, Kbuntu, Netbook remix) and they all behave the same way. Yes all updates have been run.


Hi, have you tried blacklisting ath9k and atl1c modules?
I had no more freezes after doing it

---

### Post by andi666 on 2011-05-24
I noticed that apart from the ethernet issues, even the overheating issue is gone if you boot into windows and then reboot into ubuntu.

So booting into windows once after every complete shutdown fixes pretty much everyting.

The real news however is that BIOS 1.09 is available which says to have fixes for non-windows in the changelog.

I cannot try now but will report back asap.

**EDIT: Confirmed, with BIOS 1.09 wired ethernet works without prior booting into windows now :) - Cant say if it is 100% stable yet, but rmmod atl1c no longer leads to freezes as before.**

---

### Post by kranezor on 2011-05-30
I have the freeze problem too (11.04)
and already upgrade BIOS to 1.09 but still frozzzzzze!!
and still blacklist atl1c ,load when need
testing both AC and Battery
testing both unactivated and activated ATI driver
also nosound with jack ,mic not test,fan not test,wifi not test (internet via bluetooth out of box)
and want to upgrade new kernel asap
so nerve pain every time to load and unload atl1c when booting.

---

### Post by SnappyU on 2011-05-30
I have the Asus 1015B (AMD c-50 APU), and had similar freezing issues.

I've since downgraded to maverick and practically everything works.
Shutdown, suspend, resume etc.

Only thing is that if I ever go into suspend, I can resume but not reboot or shutdown.  Reboot and shutdown will be ok, but when the machine restart, it will act like the hdd is not detected and timeout after awhile.  The system will not go to grub and boot.

To fix this, I need to remove dc power + batt, reinsert either, power up and it is ok.

Not sure if it is an APU, EFI or grub problem.

EDIT: EIF -> EFI

---

### Post by C@illou on 2011-05-31
> **md80hb-iuh said:**
> Since my last post I've installed Ubuntu 11. ATI catalyst does not work any more and I have poor video playback (regression)

I still have random freeze but this is only when I'm not plugged on A/C power. If I go on battery it will freeze within the two minutes of use. Passed 2 minutes  it will continue working regardless of wifi settings (on or off). Checked and rechecked all the power management with no luck.

On battery it will not freeze if I'm wired ethernet.

Still problems with audio jack, mic and card reader.

I have several environment installed on it (Ubuntu, Kbuntu, Netbook remix) and they all behave the same way. Yes all updates have been run.
(Hi everybody, my first post on the forum even if I read the forum for a long time now.)

I Have the exact same issue! No problem on AC power, freeze within 2 minutes on battery. And if I disable my wifi (ath9k),  there is no more freezes (for what I have experienced). Maybe this can be power-saving related, because it happens only on battery.

I have installed ubuntu 10.10 because ubuntu 11.04 freeze on boot (on the cd), even with the alternate cd. still dont know why.

I've tried the workaround, blacklisting atl1c, without success, maybe because I have an atheros wireless card and wired card, not the broadcom model.

Thanks for sharing your personal experiments!

UPDATE: I've upgrade to kernel 2.6.38 and the freezes are gone! though,  when suspending to ram the netbook wont come back. I continue my  research.

---

### Post by oxide94 on 2011-09-04
i just installed kubuntu 11.10 oneiric ocelot beta 1 x64 and all my problems gone! :) no freezing, wi-fi works, sleeping and waking up too. and my USB modem works too, without any problems! (i have huawei e1750c, i just only disabled pin verification). try it on your AO 522 ;)

i didn't tested hdmi, hdmi with audio and sound minijack 3.5 output.

ps: sorry for my english ;)

---

### Post by tigrezno on 2011-09-05
> **oxide94 said:**
> i just installed kubuntu 11.10 oneiric ocelot beta 1 x64 and all my problems gone! :) no freezing, wi-fi works, sleeping and waking up too. and my USB modem works too, without any problems! (i have huawei e1750c, i just only disabled pin verification). try it on your AO 522 ;)

i didn't tested hdmi, hdmi with audio and sound minijack 3.5 output.

ps: sorry for my english ;)

all that already worked for me months ago, but can't get hdmi audio and audio jack to work properly

Try it pls and let us know

---

### Post by oxide94 on 2011-09-05
> **tigrezno said:**
> all that already worked for me months ago, but can't get hdmi audio and audio jack to work properly

Try it pls and let us know
ok, maybe tomorrow, 'cos i don't have hd tv @ home, i'll try @ school ;)

edit @* 8:52 pm, 2011.09.05*: oh, i forget about drivers for integrated ATI card: in (k)ubu 11.04 drivers installed through ubu drivers installer worked, but now, when i tried to install them, after restart, X environment freezes. i must uninstall them by starting computer in rescue mode. i also tried to install drivers for x86_64 linux from ATI website, but after installing i can't access to desktop (in kubu after typing my username & password is an animation and there are 4 or 5 pictures, it stops while the second picture is appearing, and X's are reloaded). so i must reinstall 11.10 beta 1 and i am doing it right now.

edit2 @* 7:45 pm*, 2011.09.06: damn. i thought it works on oneiric, but it doesn't. freezing problems came back. ehhh. back to aspire one 5732Z (laptop, not netbook).

---

### Post by Pilen on 2011-09-26
Bought this machine yesterday. First thing I did was to install ubuntu.
Problem is now, I erased all the partitions, including the one with windows, and installed ubuntu. Now it freezes a few seconds after lightdm starts, so I can't do anything to fix the issue.
I tried booting from a live usb, but it freezes too. Tried both 11.04 and 11.10 beta2.

I'm calm for the moment.

Why did I erase Windows? Well, all the problems in the past that Ubuntu has brought me always had a solution. You had internet, and you had a terminal. This I can't dix. How can I do anything without a terminal!?!?

So what can I do?

EDIT: Forget it. I Read that I could boot with network boot first. It worked.

---

### Post by GenBattle on 2011-09-29
I've also been having problems with my netbook freezing on just about every Ubuntu edition. The problem seems to lie for the open-source driver for the BCM4313 wireless module. Of course there are actually two version of this netbook in the wild; some have the Broadcom wireless chipset, while others have an Atheros chipset.

Anyway I have sort of solved my issue by installing mint 10 and using the proprietary broadcom wireless driver. It's kind of slack that the open source wireless driver has been causing these freezing issues on 3 successive Ubuntu releases.

---

### Post by casainho on 2011-10-23
Hello everyone.

I got hacks for:
- touchpad horizontal and vertical scrool
- GPU dynamic
- Undervoltage!!
- some info about EC
- unlock advanced BIOS menus

Please see here: [https://help.ubuntu.com/community/AspireOne522](https://help.ubuntu.com/community/AspireOne522)

---

### Post by maspai on 2012-02-21
Sorry for repost. I just want to reply & help solve the problem :).
I did change boot order of BIOS, the network boot becomes the first. No more freeze since.
Hopefully it works for you all.

---

