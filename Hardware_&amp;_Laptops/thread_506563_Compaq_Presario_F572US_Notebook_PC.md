---
title: "Compaq Presario F572US Notebook PC"
date: 2007-07-21
forum: Hardware &amp; Laptops
---

### Post by DarkW0lf on 2007-07-21
Staples is having a sale on this laptop in the coming week and for the price for the hardware is better than what I usually see. But it uses an NVIDIA graphics card, and usually the linux world has been split with one half having issues with it and the other half works out of the box.

Does this card in this laptop work out of the box or might I have issues ?

Compaq Presario F572US Notebook PC
1.7 GHz AMD Athlon &#8482; 64 X2 Dual-Core Mobile Technology TK-53
NVIDIA GeForce Go 6150 (UMA)

MFG link
[http://h10025.www1.hp.com/ewfrf/wc/document?docname=c01069714&lc=en&cc=us&dlc=en&product=3441671&lang=en#](http://h10025.www1.hp.com/ewfrf/wc/document?docname=c01069714&lc=en&cc=us&dlc=en&product=3441671&lang=en#)

Edit follows:

My system is xubuntu 8.04

For Wireless support:
[http://ubuntuforums.org/showthread.php?t=475963](http://ubuntuforums.org/showthread.php?t=475963)
[https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx/Feisty_No-Fluff](https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx/Feisty_No-Fluff)
Warning Ubuntu has borked wireless support, you need to reload driver modules.
Instructions at the above links.

Repository ndiswrapper works with the drivers from the no-fluff docs.

For Native Widescreen Resolution:
Looks like it works with 7.10, 1280x768 is the currently used res
The restricted driver manager will download packages but it works for me without that.
The restricted manager may have reduced the resolution, now = 1152x768
Can't get manager to run in 8.04 can't check res, also can't find the screen resolution tool in the settings manager.

For SoftModem support:
Doesn't look good (HD Audio Softmodem from Conexant non-DSP chipset; requires key for speeds over 14.4k)

For Sound support:
None needed, it works out of the box.
Unless you upgraded to 8.04 then there is sounds issues, clean install you are good.

Known (to me) Issues:
USB hot swapping seems to be okay, don't know about IRQ 7.
Haven't tried it with the casper-cow disk label.

I may have the same suspend issue as ragingocelot, but I don't know if it my video card or not.
Install gnome-power-manager Xubuntu does not have it by default and it will add the power management button to the screensaver manager (no 8.04 info yet)

---

### Post by fastpakr on 2007-07-25
I'll get back with on you on this early next week - mine should be here on Friday and I'll try to install 7.04 on it as soon as possible.

---

### Post by 67GTA on 2007-07-25
From looking at other posts, it will work if the restricted drivers manager is used to install the Nvidia driver. There are posts about black screens when using Envy. I am going to Staples later tonight to grab one of these before they are gone!

---

### Post by fastpakr on 2007-07-25
If you can, buy it online and use a 30/150 or 50/200 coupon.  It may be out of stock online, however.  I ordered mine last night using a 30/150 and was out the door for $470 with tax (before the $30 rebate).  I picked up a DDR2 533 1GB stick for it on eBay today for $30, so including the rebate I'll be at $470 with 1.5GB of RAM.

---

### Post by DarkW0lf on 2007-07-27
fastpakr: yours only has 512 MB RAM at stock ?
At stock mine is 1 GB RAM and I paid $470 in store.

Any ways I tried both Ubuntu 7.04 and xubuntu 7.04 and get a system hang during boot.
Either when loading hardware drivers or when failing to load firmware for broadcomm 43xx (some message like that). Anyone have a successful boot/install ?

---

### Post by Walkboss on 2007-07-27
I also have the 6150  in my HP Pavillion dv9005us.

My system would blank and hang after the initial "Ubuntu" loading screen. The problem is with the drivers (obviously)

To remedy try the following:

1. Boot into recovery mode via GRUB.

2. Check that the Universe Repositories are enabled via sudo nano -w /etc/apt/sources.list (remove the '#' from in front of it)

3. sudo aptitude install nvidia-glx

4. sudo nano /etc/X11/xorg.conf

5. Change the driver for your video card (should be listed near the middle) as "nvidia" instead of "nv"

6. Save and reboot.


I hope this helps! :)

---

### Post by fastpakr on 2007-07-27
> **DarkW0lf said:**
> fastpakr: yours only has 512 MB RAM at stock ?
At stock mine is 1 GB RAM and I paid $470 in store.

Any ways I tried both Ubuntu 7.04 and xubuntu 7.04 and get a system hang during boot.
Either when loading hardware drivers or when failing to load firmware for broadcomm 43xx (some message like that). Anyone have a successful boot/install ?

It's got 1GB stock, but it's in 2 512MB sticks, so adding a 1GB stick requires removing a 512MB.

---

### Post by fastpakr on 2007-07-27
> **Walkboss said:**
> I also have the 6150  in my HP Pavillion dv9005us.

My system would blank and hang after the initial "Ubuntu" loading screen. The problem is with the drivers (obviously)

To remedy try the following:

1. Boot into recovery mode via GRUB.

2. Check that the Universe Repositories are enabled via sudo nano -w /etc/apt/sources.list (remove the '#' from in front of it)

3. sudo aptitude install nvidia-glx

4. sudo nano /etc/X11/xorg.conf

5. Change the driver for your video card (should be listed near the middle) as "nvidia" instead of "nv"

6. Save and reboot.


I hope this helps! :)

It might help, but I can't even boot into recovery mode.  No idea how to edit the file without access to the live CD, recovery mode, etc...  Thoughts?

---

### Post by Walkboss on 2007-07-28
If you cannot boot into recovery mode then I'm afraid the problem is a little more complex than a simple video driver issue. I only know enough at this point to help solve problems I've experienced myself. I'll try though.

What happens when you try to boot into recovery mode? The option is in the GRUB (or LiLO) menu, right?

---

### Post by DarkW0lf on 2007-07-28
There is no recovery mode, there is no grub.
This is a fresh MS Vista Laptop that I am trying to load the desktop AMD 64 cd's for Ubuntu and xubuntu.

System hangs when trying to load hardware drivers or the broadcom formware.

---

### Post by fastpakr on 2007-07-29
There *is* grub, but choosing recovery mode doesn't complete the boot process either.

---

### Post by Jamasony on 2007-07-29
I'm getting stuck also, just bought this laptop to try linux for the first time.  Same problem, hangs when loading hardware drivers or broadcom drivers.

---

### Post by fastpakr on 2007-07-29
Did any of you guys happen to make recovery cd's before waxing the Vista install?  I failed to notice that they weren't included until it was too late.  It would be nice to put Windoze back on it until we can get the problem sorted out.

---

### Post by DarkW0lf on 2007-07-29
My vista isn't 'waxed' I hadn't wiped the drive yet I was trying to get the live cd to load first and make sure the system would function.

What recovery mode is availble on the desktop (live) cd's I don't see that option. Is it a boot parameter I have to pass with the F6 option at the bottom of the screen ?

---

### Post by fastpakr on 2007-07-29
Yes, I've been trying it using F6.  Try adding acpi=off at the end - I know I just swore in another post that I'd tried that and it failed, but I just tried again and must have been wrong - the laptop booted all the way for the first time.  It did throw a set of BIOS errors that I'm going to try to get a copy of, but at least it booted.

---

### Post by DarkW0lf on 2007-07-31
That's power management correct ?
Any idea why that would have anything to do with the hardware driver loading or the broadcomm firmware issues ?

I'll try this out later.

---

### Post by fastpakr on 2007-07-31
Use 'noapci' rather than acpi=off.  I just used that at the end of the boot string on the live CD by pressing F6.  Worked great to boot the live cd, and then it added it automatically when I installed.  Good luck!

---

### Post by DarkW0lf on 2007-08-01
What is the difference between 'noacpi' and 'acpi=off' ?
Do you mean that you turned acpi off to boot and then on again after loading ?
I haven't installed yet and am trying to get the liveCD working (when that works I'll install).

Ubuntu and xubuntu both load after 'acpi=off' doesn't look like the wireless card is detected and I have sound issues (a persistent clicking and hangs after a few seconds of playing).

Can't get casper-cow to work with Ubuntu the system hangs on boot after X loaded (and that damn jungle beat just sits there and clicks cause of the sound card). But it did work under xubuntu, I pulled kern.log, syslog and Xorg.0.log (not sure what was relevant). And ran ScanModem while I was at it.

---

### Post by fastpakr on 2007-08-01
> **DarkW0lf said:**
> What is the difference between 'noacpi' and 'acpi=off' ?
Do you mean that you turned acpi off to boot and then on again after loading ?
I haven't installed yet and am trying to get the liveCD working (when that works I'll install).

Ubuntu and xubuntu both load after 'acpi=off' doesn't look like the wireless card is detected and I have sound issues (a persistent clicking and hangs after a few seconds of playing).

Can't get casper-cow to work with Ubuntu the system hangs on boot after X loaded (and that damn jungle beat just sits there and clicks cause of the sound card). But it did work under xubuntu, I pulled kern.log, syslog and Xorg.0.log (not sure what was relevant). And ran ScanModem while I was at it.

Sorry - try 'noapic' rather than noapci.  I gave you the wrong one...  That should get you booting with working sound!  Wireless is working fairly well for me, but you're better off worrying about that once it's installed.

---

### Post by DarkW0lf on 2007-08-02
What does 'noapic' do ?

What do you mean fairly well ? When I get the system booted it appears that the wireless is disabled ( orange indicator on card ).

So you used 'noapic' to boot and then let apic run or did you use 'noapic' to boot and installed (x)Ubuntu.
Did you have any problems on subsequent boots ?

---

### Post by fastpakr on 2007-08-02
> **DarkW0lf said:**
> What does 'noapic' do ?

What do you mean fairly well ? When I get the system booted it appears that the wireless is disabled ( orange indicator on card ).

So you used 'noapic' to boot and then let apic run or did you use 'noapic' to boot and installed (x)Ubuntu.
Did you have any problems on subsequent boots ?

From [here](http://www.linuxquestions.org/questions/showthread.php?t=454675) I found this:
> APIC = Advanced Programmable Interrupt Controllers

APIC is the replacement for the old PIC chip that used to come imbedded on motherboards that allowed you to setup interrupts for your soundcard, ide controllers, ect.

Many computers ship with buggy or out of spec. ACPI firmware which can cause any number of wackiness. If you are noticing your machine randomly powering off or failing to boot disabling this often helps.

Once you install the OS, you'll have to use ndiswrapper to get the wireless going.  I've got mine installed properly where I can connect to networks.  However, it still seems to lose the connection intermittently, and I had a full lockup of the OS last night that appears to have occurred while something was going on with wireless...

---

### Post by LavianoTS386 on 2007-08-02
I've found that on my F579WM if you press the power button for a second it will then continue loading. However I myself am having video woes. The Live CD of 7.10 worked amazingly well, but after the install my screen looked like somebody left it in the cold and punched it.

---

### Post by DarkW0lf on 2007-08-04
xubuntu is installed and boots fine without noapic in the menu.lst file.
Do I need to do that to get the wireless working ?

ndiswrapper is installed and I copied the sys and inf file from the windows partition.
Ran ndiswrapper as it says in the man page and /? command but how am I to check if it is working ? (card still indicates disabled).

---

### Post by fastpakr on 2007-08-04
I don't think you need noapic as long as you can boot.  I was never able to get any WM up without that option, but if it works for you...
Check [here](http://ubuntuforums.org/showthread.php?t=475963) for where I got wireless working.

---

### Post by RagingOcelot on 2007-08-22
Ok, so I just picked up one of these fine machines the other day.  I have gone through every wireless installation I could find and still no dice.  When I type lspci, I get:

```
03:00.0 Network controller: Broadcom Corporation Dell Wireless 1390 WLAN Mini-PCI Card (rev 02)

```

I'd like to hear what kind of success stories are out there with this machine so someone in my position could be pointed in the right direction.  I've tried the 32-bit and 64-bit Feisty install Cds.  I've tried the ndiswrapper that is Feisty's default.  I've tried the ndiswrapper 1.47 version, all to no avail.  

I've tried the hopeless bcm43xx driver, the bcm43xx-fwcutter driver...nothing.  

I'm afraid I might have to chuck this thing out the window or at the very least chuck myself out the window if I have to endure the wacky world of Windows for a moment longer.

So after a fresh Feisty install, what should I do?

---

### Post by fastpakr on 2007-08-22
Did you follow the link in my post above yours?  If so, exactly what did you get?  The basic steps you need to follow are 1) blacklist the bcm43xx driver, 2) compile ndiswrapper 1.47, and 3) add the bcmwl5.inf driver.  Obviously the details are a little more complicated, but that's the basics.

I'll admit that I'm still getting some weird wireless issues with it, but it definitely works - I can connect to WPA networks through the built in network manager applet.

---

### Post by RagingOcelot on 2007-08-22
Ok, will do a fresh install and try it again.

What kind of issues are you getting?  Have you found any workarounds?

Have you played around with wifi-radar by any chance?

---

### Post by RagingOcelot on 2007-08-23
Nope, still no wireless.  For some reason, my wireless connection has always shown up as "eth1" instead of "wlan0".  Does that perhaps have any impact on the installation instructions?  Oh, and eth1 no longer shows up in iwconfig:

```
lo        no wireless extensions.

eth0      no wireless extensions.

```

...whereas right after the fresh system install, eth1 showed up with all the usual pertinent wireless info.

---

### Post by Satpam on 2007-08-25
Hi guys,

I have the same laptop too, just bought it from circuit city 2 days ago for 470 and the last one :) I am trying to install ubuntu 7.0.4 on it.

My spec is 
AMD 64 X2 1.7
1GB memory
nvidia 6100 
80 gigs of hard disk

Everytime i boot it from the disk and try to install ubuntu, it will give a blank screen. I tried start it with safe graphical mode and it stops somewhere after displaying some error or kernel panic: can't synch. Anyone know how to install it :confused: ? Thank you.

---

### Post by RagingOcelot on 2007-08-25
I booted with the options "noapic" and "irqpoll" added to the end of the kernel boot line after you press F6.  I never had to boot in safe graphics mode to install Feisty but others have reported that they had to.

---

### Post by DarkW0lf on 2007-08-25
Satpam what is the error you are getting and which ubuntu flavor (U,K,X,and on....)
You are using the 64 bit version right ?

---

### Post by doug98382 on 2007-08-27
> **DarkW0lf said:**
> There is no recovery mode, there is no grub.
This is a fresh MS Vista Laptop that I am trying to load the desktop AMD 64 cd's for Ubuntu and xubuntu.

System hangs when trying to load hardware drivers or the broadcom formware.

I have the identical presario F572US, bought at Staples, mine also hangs "Loading hardware drivers."

Have you gotten any further?

I tried installing the older 6.06.1 desktop-amd64 and the ubuntu-7.04-alternate-amd64 as well as the version you mentioned. Same hang point, something in hardware. 

Any ideas on working around hardware drivers hangups during boot up after installation will be welcomed. Thanks
AMD Athlon 64x2 Dual Core Processor TK53
1.7 GHZ
960 Mb RAM
nVidia GeForce Go6100
Presario F572US
Phoenix Bios

---

### Post by fastpakr on 2007-08-27
Have you tried the boot parameter 'noapic'?

---

### Post by RagingOcelot on 2007-08-27
Anybody else having high iowait issues and also disk issues?

I keep getting:

[28675.752053] hda: status error: status=0x58 { DriveReady SeekComplete DataRequest }
[28675.752056] ide: failed opcode was: unknown
[28675.752058] hda: drive not ready for command

when I type dmesg.

Also a lot of disk activity in my System Monitor applet, too.

---

### Post by RagingOcelot on 2007-08-27
Weird.  Well, /dev/hda is the optical drive.  I tried putting a CD in and the system crashed.  After bootup, I put the same CD in and it mounts just fine with no system crash.

The disk access is way down in System Monitor, while the IOwait is still sky high.  Would love to figure out why that is.

---

### Post by doug98382 on 2007-08-28
Thanks fastpacr for the suggestion of noapic, I am watching the install working now after much frustration.

I'd like to learn more. How does one learn about the noapic? Where can I go to learn?
Is hanging around the forums the only way?

Also,
Can anyone tell me what the tiny blue light is that turns on next to my keyboard caps lock key? 
It only comes on when the system hung, locked up. That light is right above where the cable plugs in. All I could find at HP made the light appear to indicate "wireless". 

I am looking forward to seeing Ubuntu again.

presario F572US

---

### Post by fastpakr on 2007-08-28
> **doug98382 said:**
> Thanks fastpacr for the suggestion of noapic, I am watching the install working now after much frustration.

I'd like to learn more. How does one learn about the noapic? Where can I go to learn?
Is hanging around the forums the only way?

Also,
Can anyone tell me what the tiny blue light is that turns on next to my keyboard caps lock key? 
It only comes on when the system hung, locked up. That light is right above where the cable plugs in. All I could find at HP made the light appear to indicate "wireless". 

I am looking forward to seeing Ubuntu again.

presario F572US

I'm not trying to be rude here, but have you actually read this thread?

---

### Post by RagingOcelot on 2007-08-28
That light is simply the caps lock on light.  The wireless light is the one in the front of the laptop that is amber if the wireless card is not on and blue if it is (next to the switch that goes left to right).  It will stay amber until you install the necessary drivers for Ubuntu.

---

### Post by bigbee79 on 2007-08-29
I'm really new at Ubuntu (or linux at all really) so please be kind.

After following instructions in another thread I was able to install the wireless card on my f572us and it seems to be working fine.  Now I have another problem that I was hoping someone could help with.

I have a usb thumbdrive and when I plug it into any of my usb ports, the thumbdrive's light comes on for a second, and then goes off.  The drive isn't seeming to be recognized at all.

I put the "noapic" in the start up string when I first installed, but I didn't use the "irqpoll" because I didn't know what that did and my computer seemed to boot just fine without it. Is that what's causing this problem with my usb ports?  And if so, how do I do now go back and put the "irqpoll" part in now that I've already installed Ubuntu?  

If anyone could help, I would really appreciate it.

---

### Post by bigbee79 on 2007-08-29
I'm having another problem that I didn't realize.  My video card isn't installed correctly.  When I tried to use the "Restricted Drivers Manager" to install the driver, it says something like "Your hardware does not need any restricted drivers." Which I know is wrong since my Nvidia card isn't installed.

---

### Post by The_Id on 2007-08-29
To get my USB plug and play working I had to add:

pnpbios=off 

to the boot line, along with the noapic.

Also, I got my video working by installing Automatix and using that to install my video drivers, there are other ways but that seemed to work.

---

### Post by mootpoint on 2007-08-30
bigbee,

you add the option to the "kernel" line for your kernel in the file /boot/grub/menu.lst. The entry for my current kernel looks like this in the file:

title           Linux Mint, kernel 2.6.20-16-generic
root            (hd0,1)
kernel          /boot/vmlinuz-2.6.20-16-generic root=UUID=608d3109-0b69-499c-a5a4-9c448be36cff ro quiet splash noapic
initrd          /boot/initrd.img-2.6.20-16-generic
quiet
savedefault

You'd add irqpoll, pnpbios=off, or any other kernel boot flags to the end of the line that begins "root=" As you can see, I currently have "noapic" added to mine.

irqpoll and/or pnpbios=off might take care of your video driver and flash drive issues.

ALWAYS make a backup of this file before you change it. If you make a change that breaks the machine, hit "Esc" during the initial bootup to get to the grub menu, and boot the recovery kernel. Then just go to /boot/grub and undo your changes.

mootpoint

---

### Post by bigbee79 on 2007-08-31
Thanks, mootpoint.  i now have this laptop running pretty well, and I'm really enjoying Ubuntu.  

I have noticed since installing Ubuntu that my battery doesn't last nearly as long as it used to.  Is this due to adding "noapic" to the boot up or is this just a general issue with running Ubuntu?  Is there anything I can do to have better power management so that my battery will last a little longer?

Any help would be greatly appreciated.

---

### Post by RagingOcelot on 2007-08-31
I also wonder about the battery and what I can do to make it last a little longer.  Before I installed the Nvidia proprietary drivers, I had the cpu frequency scaling working perfectly and ever since I installed those drivers I've had nothing but erratic behavior out of the cpus.  Sometimes they want to stay on 800 mhz all the time, sometimes they insist on 1.7 ghz all the time. 

I think maybe it has something to do when I had to compile the Nvidia drivers into the kernel.  I can't figure out if I need to compile cpu frequency scaling back into this kernel I'm using or what I need to do.

bigbee, have you been able to get able to get the cpus scaled back to 800 mhz?  I would recommend that as a starting point to getting more life out of the battery.

---

### Post by bigbee79 on 2007-09-01
Honestly, I have absolutely no idea what cpu frequency scaling is or how it's working on my computer, or how to test it.  Could you tell me how to check it and then I can let you know.  But if you're saying that I should lower my cpu speed permanently just to get the battery to last longer, that seems to be a bad solution (at least to me as a layperson) because I'd be sacrificing half the speed of my computer.  Wouldn't I just be trading one problem for another?  Maybe I'm really  clueless here and completely misunderstanding.

This battery issue is driving me crazy, though.  The stats for the laptop battery on my panel are all messed up.  At one point they'll say that I have some crazy time left o n my battery (once it said that I had 4 days of battery left) then it will soon after that start telling me that I have less than 30 minutes left.  The longest my laptop will run on a fully charged battery is something like 30 or 35 minutes, tops.  As much as I'm loving Ubuntu, I don't know if that's going to be enough for me.  I know on Vista I could last for 2 and a 1/2 hours if I turned my screen brightness down.

---

### Post by RagingOcelot on 2007-09-01
I've been having the same issue with regards to time left on the battery.  Beats me how to fix that.

For cpu scaling, yes, you'd be giving up cpu performance for more battery life.  It depends on how you use your computer, I guess.  I have no problem at all with the power the machine has even at 800 mhz.  Fact, I'd be happy with that speed even on AC power.  But the fact is, you have much more speed to play with, so of course, you're going to want the full 1.7 ghz from time to time.  

The thing about lowering the speed while on battery is that doing so even reduces the idling wattage.  The computer saves about 5 watts at idle going from 1.6 or 1.7 ghz to 800 mhz.  

If you follow the directions in this thread:

[http://ubuntuforums.org/showthread.php?t=248867&highlight=cpufreqd+howto]("http://ubuntuforums.org/showthread.php?t=248867&highlight=cpufreqd+howto")

...you may be able to get it working.  

If you're in Gnome, do you have the CPU Frequency Scaling applet loaded?  You might want to try loading that first to see if you already are capable of scaling your cpu.

---

### Post by Satpam on 2007-09-02
> **DarkW0lf said:**
> Satpam what is the error you are getting and which ubuntu flavor (U,K,X,and on....)
You are using the 64 bit version right ?

Yes, I am using the 64 bit version. Do you know how to fix this?

By the way I create a thread for this, but it seems nobody know how to fix this.

[http://ubuntuforums.org/showthread.php?t=534762](http://ubuntuforums.org/showthread.php?t=534762)

---

### Post by DarkW0lf on 2007-09-08
When you put the LiveCD in, at the first menu (with the boot and disk check and other options). Press F6 and add "noapic" to the end of those options then press enter.

As it boots it should scroll all the things it is currently loading. Look to see where it hangs if it still having problems booting, for me it usually hanged at firmware for the wireless card.

---

### Post by DarkW0lf on 2007-09-08
As far as usb drives, check my first post (I edited it).
There is something with IRQ7 that relates to USB1.
I have off and on again issues with the USB ports.

---

### Post by DarkW0lf on 2007-09-08
Anyone got the native widescreen resolution working ?

---

### Post by fastpakr on 2007-09-10
Widescreen worked great for me.  You've tried doing 'dpkg-reconfigure xserver-xorg' and setting 1280x800?

---

### Post by DarkW0lf on 2007-09-22
I just noticed today that it listed as 1280x768 in my display settings.
When before I thought the highest listed was 1024x768.

I am not all that famalir with widescreen resolutions, it's too new :-p
I am still used to the older full screen res'

---

### Post by DarkW0lf on 2007-10-19
fastpakr: did you ever figure out the system freezes.

Mine has started to do that more frequently but has behaved itself today so far.

---

### Post by Cuford on 2007-11-10
I just set up one of these to run 7.10, and I wanted to post some success I had.

I've been trying various kernel options, because udev was locking up during boot.  noapic fixed that, but I also had to use irqpoll or else I got the problem with the USB interrupt, and the system eventually would crash.  With irqpoll, though, the system was a lot less responsive; typing in the terminal, for instance, was very slow.

I've just started using "noapic nosmp", and everything seems to be working great.  Of course, this means I can only use one core of my system, but I prefer that to the other solutions.  And I bet my system will run cooler, too. :) Hopefully, the APIC will eventually be fixed and I'll be able to use this computer to its full capabilities, but it works fine for now...

I was able to boot a couple times with the APIC enabled, but it was hit or miss.  Add --verbose to udevtrigger in /etc/init.d/udev showed the program halting at random points, which leads me to suspect some sort of race with interrupts and SMP on this computer, caused by a faulty APIC configuration or something. (Curiously, seems to work just fine in the Windows dual boot. :()

Wireless works fine with ndiswrapper; I hear a native driver that supports the updated firmware needed for this computer is slotted for maybe kernel .23 or .24.

I used gconf-editor to adjust /app/gnome-power-manager/cpufreq/performance_ac and lower it to 25, same as performance_battery.  This keeps the CPU frequency lower more of the time when I'm plugged in, and the fan running less.

Other than that, this is a fresh install, and everything seems to work great.  Heck, suspend seems to work better than under Windows. :)

EDIT #1: Sigh: Never mind.  I spoke too soon, it just crashed. :( Curse you, APIC.  I'm starting to think I should just run under VMware on this computer...

EDIT #2: While looking around on the kernel mailing list, someone with a similar computer had success with maxcpus=1.  I tried this, and it booted up fine with APIC enabled. :) No "noapic irqpoll" needed.  It's still just one core, but that's good enough for me, at least for now.

---

### Post by DarkW0lf on 2007-11-11
I haven't had any issue with IRQ's with the current 7.10 release.
I still boot with noapic but haven't seen the IRQ 7 message in the terminal and no boot issues.

ndiswrapper worked for me as well and there as been no system crashes yet.

So far the only weirdness I have come across is it didn't recognize my password after resuming from suspend. A hard reboot fixed that, I'll need to check it out more.

---

### Post by faheyd on 2007-11-16
I cannot get the nvidia drivers to work so that I can use all the bells and whistles.
What is the secret handshake to get this video driver working?
Exactly what drivers need to be loaded, and is everyone using 1280x800 per the LCD.
And how are you selecting the LCD, just plain old LCD 1280x800 widescreen, or is there a particular one you are choosing?

I seem to be stuck on the open X drivers, and just can't for the life of me get those proprietary ones working.

---

### Post by faheyd on 2007-11-18
Ok , this is how I got my F572US up and running.
I first had to boot with acpi_osi=!Linux noapci irqroll.
I then was able to do get the restricted video drivers to work, and nsdiswrapper working per [http://ubuntuforums.org/showthread.php?t=297092](http://ubuntuforums.org/showthread.php?t=297092) .  Probably the wireless would have worked, but I'm using ndiswrappers. After that, I rebooted and still had problems when it came to 'hardware drivers'.

  I then found another post that the user booted with this:
kernel          /boot/vmlinuz-2.6.xx-xx-generic root=UUID=068b233d-8987-4952-a147-e36ac86fxxxx ro  splash noapic acpi=on irqroll

This is the only combination that worked for me, adding noapic acpi=on irqroll .  (no 'quiet' as I want to see what's loading).

I now have all the compiz joy (you must load some addtions to get compiz working and configured, search google) and wireless access (sometimes goes out for no reason).

Note: when you select 1280x800 LCD in the graphics panel, you must click on the 'widescreen' to get it to show up as a valid selection later on.

---

### Post by DarkW0lf on 2007-12-01
I am a Xubuntu user so some of those display menus you are talking about don't exist.
I just select 1200x780 from the display settings and that is all I need to do.
I had no 'widescreen' option to click on.
The restricted driver manager in 7.10 gets the right driver I need.

The only boot option I added to the default options was noapic.

I haven't had many problems with xubuntu 7.10 and my hardware.

---

### Post by faheyd on 2007-12-02
> **DarkW0lf said:**
> I am a Xubuntu user so some of those display menus you are talking about don't exist.
I just select 1200x780 from the display settings and that is all I need to do.
I had no 'widescreen' option to click on.
The restricted driver manager in 7.10 gets the right driver I need.

The only boot option I added to the default options was noapic.

I haven't had many problems with xubuntu 7.10 and my hardware.

Which goes to show that maybe there are different chips in some of these lappy's.  I did try just the noapic and it didn't work.  I did want the native resolution of the panel, that's whey I selected the widescreen lcd option with 1280x800, very sharp, no fuzzy's.
If it wasn't for your hard work and others that posted here, I would never have gotten this lappy up and running :popcorn:, thanks,
Dylan

---

### Post by DarkW0lf on 2007-12-08
I think it may be software related.
There seems to be some different performance between Ubuntu and xubuntu with this machine judging from other have posted and my experiences.

The lastest version of xubuntu has included alot of Ubuntu software (Totem instead of gxine for example) and now I am not sure as to what code is running now or which of the two I want to use.

xfce is supposed to be a lighter desktop but alot of Gnome/GTK code got loaded in the current xubuntu release.

---

### Post by RagingOcelot on 2007-12-28
Has anyone loaded the new Nvidia proprietary driver (version 169.07)?  I installed it and had problems with the screen turning off and back on again (suspend).  The screen would just turn black (with the backlight still on) when I moved the mouse to wake the screen up.  I would have to force an Xorg restart (Ctrl+Alt+Backspace) to get out and back to a login screen, where I was able to log back in normally.  

Also, I couldn't exit X to a console.  Screen would turn blank again and I'd have to restart X.  

Just wondering if anyone's tried 169.07 out on this machine.

---

### Post by DarkW0lf on 2008-02-29
Where do you find the version ?

I check Synaptic and nvida-glx-new package and mine is listed as 100.14.19
Where are you getting the version number from ?

---

### Post by RagingOcelot on 2008-02-29
I just loaded the nvidia-settings app and it shows up on the opening screen.

I'm now up to version 169.09 and have had good luck with it so far.

---

### Post by RagingOcelot on 2008-02-29
Oh, and I've been running AMD's AMD-V virtualization technology with Virtualbox, which has experimental support for it.  I must say running XP absolutely smokes while inside Virtualbox.

---

### Post by DarkW0lf on 2008-03-09
Are you using an existing XP partition ?
Or did you install a new one in the VM ?

I had been thinking about running the Windows partiton in a VM, there are some things I still am having problems with that xUbuntu Firefox doesn't handle well (FoxOnDemand, no 64 bit Java plugin, etc) that I can run in WIndows version of Firefox.

---

### Post by RagingOcelot on 2008-03-09
I'm using a new partition I set up with Virtualbox.  It's a huge .vdi file that resides on one of my drives.  

Aside from the issues you've been having with Firefox, how has the 64-bit Ubuntu been running for you?  I switched back to 32-bit some time ago because the hassles of 64-bit were just not worth it at the time.  

I may switch back since I'd rather make the most of my hardware.

---

### Post by DarkW0lf on 2008-03-09
Yeah aside from Fx/Java I haven't had an issue with 64bit xubuntu over any 32bit.

---

### Post by DarkW0lf on 2008-03-22
I found that to adjust power management you need to install gnome-power-manager
Xubuntu doesn't have it by default.
This is the easy way to keep display from suspend than to edit config files.

[http://ubuntuforums.org/showthread.php?t=701438&highlight=xubuntu+power+management](http://ubuntuforums.org/showthread.php?t=701438&highlight=xubuntu+power+management)

---

### Post by firecrow8 on 2008-03-22
I have this computer too and it's all working.

well accept it wont hibernate on it's own when the battery runs out it just cuts off, so I have to pay real attention to that 10% battery left warning.

I had some initial issues with it not working with the monitor and booting into a blank screen but adding the following to the boot string resolved that issue for installation and I've since been able to remove it all together as it's now properly configured.
```
noapic nalapic vga=792
```

Getting the Nvidia driver to work was no problem. it downloaded the proprietary driver and worked by itself. and this is probably why the above code is no longer necessary.

It was also slow until I installed the proper windows xp wireless driver. don't know why this is but litterally performance doubled when I installed the driver. there's alot of information on line about how to do this so it was pretty easy.

some minor funnies like crashing in the KDE and XFCE desktops. which i had installed because of the perfomance issues prior to fixing my WLAN driver. but the gnome desktop is great and very stable. much more so than vista

BUT NOW IT'S AWSOME

I'm very happy with it's performance. much faster and more stable than Vista. and I'm convinced anything that needs configuration can be resolved.

---

### Post by DarkW0lf on 2008-03-30
I didn't have video issues, I needed noapic boot option for other reasons.

You are using the stock ndiswrapper for your wireless drivers right ?

---

### Post by firecrow8 on 2008-03-31
yeah I'm using ndiswrap-whatever. I found the custom system file for my wireless card. i works buy has some DHCP issues. so it only works if I set it to manual configuration and set the Automatically Obtain IP (DHCP) setting. 

is your wireless working?

I'm going to delve deep into the dhcp-client and hopefully run it from terminal soon so I may uncover what's really going on. I find the options of the wireless manager not a detailed as I'd like them. that and I'm curious.

---

### Post by DarkW0lf on 2008-04-05
I followed the howto I linked in my first post and I had no major problems.

There is an occasional system freeze that occurs when I use firefox.
For awhile it was limited to Linux but I had it occur in windows vista too.

---

### Post by Amish_Gramish on 2008-05-01
With the help of an Ubuntu buff, I was able to get Flash and WiFi working on my CP F572US, but now, when I upgraded to Hardy Heron 8.04, the sound is messed up, Flash is messed up (I have to click on the area where the Flash object is to get it working most of the time, and sometimes it doesn't even work) and my sound is messed up.

Does anyone have a fix for this?

---

### Post by RagingOcelot on 2008-05-02
I get tired of doing clean re-installs every time a major release comes out, but that's what did the trick for me.  I also had sound issues before I re-installed.  

I have 8.04 64-bit installed now and it seems to be working well.  Sound and flash both work fine.  

I followed the pretty long-winded instructions (including the Hardy Bug Fix) to install the wireless driver at:

[https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx/Feisty_No-Fluff](https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx/Feisty_No-Fluff)

So far, no issues with wireless.

---

### Post by DarkW0lf on 2008-05-09
Hmm, great more upgrade issues.
Glad I wanted before downloading iso's.
I'll wait and see before upgrading xubuntu to Hardy.

---

### Post by castillo9696 on 2008-06-02
***HI everyone, i have a problem with my laptop because i lost my recovery disks and i live in central america, does anyone now were can i download this disk??????????????***

---

### Post by DarkW0lf on 2008-06-03
[http://neosmart.net/blog/2008/windows-vista-recovery-disc-download/](http://neosmart.net/blog/2008/windows-vista-recovery-disc-download/)

Download that ISO, it is the MS recovery disc.
If you are asking about the recovery disc for this brand laptop, you pay HP $15 bucks and they'll be happy to mail you one.

---

### Post by DarkW0lf on 2008-06-03
RagingOcelot:
I have a wierd issue with networking.
When trying the Hardy fix (reloading the modules), it tells me it can't resolve the host. I think it means the laptop's hostname not resolving to IP. I don't know, I also asked this on the no fluff thread.

Otherwise I am seeing the same issues as 7.10 with this hardware.

---

### Post by DarkW0lf on 2008-06-28
Yeah sudo was screwed up.
Had issue with the /etc/hosts and /etc/hostname files.
I needed the fullname in their else sudo complains about resolving host name.

Way can't ubuntu do things the same way twice.

---

### Post by Mahsud on 2008-07-07
Hi, I have a compaq presario F572US and i had two operating systems on it. XP and the VISTA 64 bit. I updated my drivers from the HP site and also installed the new BIOS F.1F while i was in the XP OS, but there is no recommended BIOS update for VISTA 64 bit. The problem now is that my Broadcom Wireless LAN has stopped working and the light remains amber and does not change to blue in ON or OFF state, I am also not getting to see it under Network Adapters in the Device Manager. I beleive the BIOS update did it! Spoke to their tech support person who was not much help after hours of explaining and also did not agree on giving me the older BIOS with which it worked. Instead he told me to mail in the laptop as it has malfunctioned :( Please Help

---

### Post by faheyd on 2008-07-08
> **Mahsud said:**
> Hi, I have a compaq presario F572US and i had two operating systems on it. XP and the VISTA 64 bit. I updated my drivers from the HP site and also installed the new BIOS F.1F while i was in the XP OS, but there is no recommended BIOS update for VISTA 64 bit. The problem now is that my Broadcom Wireless LAN has stopped working and the light remains amber and does not change to blue in ON or OFF state, I am also not getting to see it under Network Adapters in the Device Manager. I beleive the BIOS update did it! Spoke to their tech support person who was not much help after hours of explaining and also did not agree on giving me the older BIOS with which it worked. Instead he told me to mail in the laptop as it has malfunctioned :( Please Help

1.  Try flashing the bios again with the same bios, 1.1F .
2.  There are no separate bios's for different OS's. There are different installers in some cases, but the bios remains the same.
3.  On Boot, did you look inside your bios to make sure something did not get turned off?
4. I agree, HP laptop support are morons, if you need to get the old bios, PM me, I'm on vacation right now, but I think I have a copy of the old bios on my server drive when I get back on 16 Jul 08.

---

### Post by Mahsud on 2008-07-16
Hey Bro thanks! I did manage to get hold of an older BIOS from one of my USB's but the Wireless is still looking DEAD! Any other suggestions before i sell this unit!

---

### Post by faheyd on 2008-07-16
> **Mahsud said:**
> Hey Bro thanks! I did manage to get hold of an older BIOS from one of my USB's but the Wireless is still looking DEAD! Any other suggestions before i sell this unit!

Yes, HP and Compaq are honoring out of warranty repairs on that model because of faulty fan speeds, motherboard and wireless stuff.  Open a job with them even though it may be out of warranty and they [COLOR="Red"]**may**[/COLOR] fix it for free!!!

However, I would flash that thing with f1f one more time to see what happens.

---

### Post by nimmijones on 2008-07-17
This laptop also comes preinstalled with Microsoft Windows Vista Home Basic, which delivers a safer, more reliable, and more productive computing environment. It integrates new search tools throughout the operating system, includes new parental control features, and offers new tools that can warn you of hardware failures.
--------------------------------------------------
Nimmijones

[Guaranteed ROI](http://www.inspire-itsolutions.com)
[Viral Marketing](http://www.inspire-itsolutions.com)
[Social Media Marketing](http://www.inspire-itsolutions.com)
[Search Engine Submissions](http://www.inspire-itsolutions.com)
[Email Marketing](http://www.inspire-itsolutions.com)
[Search Engine Marketing](http://www.inspire-itsolutions.com)
[Search Engine Optimization](http://www.inspire-itsolutions.com)

[Inspire Internet Marketing](http://www.inspire-itsolutions.com)

---

