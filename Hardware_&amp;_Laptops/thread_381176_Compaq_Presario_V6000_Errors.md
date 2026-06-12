---
title: "Compaq Presario V6000 Errors"
date: 2007-03-10
forum: Hardware &amp; Laptops
---

### Post by bradweiser on 2007-03-10
Hello, I have a Compaq Presario V6110CA series laptop with the following specifications:

[LIST]
[*]AMD Turion™ 64 X2 Dual-Core Mobile Technology TL-50, 1.6 GHz, 256KB+256KB L2 Cache
[*]15.4" WXGA High-Definition* BrightView Widescreen (1280 x 800) Display
[*]80GB (5400RPM) Hard Drive (SATA)
[*]1024MB DDR2 System Memory
[*]Integrated 802.11 b/g Wireless LAN
[*]NVIDIA GeForce Go 6150 (UMA) with up to 128MB (shared)
[/LIST]

I am having several problems configuring this laptop and was hoping that someone could help me out. I am also relatively new to linux.

What I have done so far...

I set up a dual boot system with Windows XP and Ubuntu 6.10 last night. It took me a while to get it installed because the Live CD would crash frequently when starting Ubuntu. I finally got Ubuntu installed and performed all updates. Also, when restarting or shutting down Ubuntu the computer crashes.

Next I ran Easy Ubuntu to install the Nvidia drivers. After Easy Ubuntu installed the new drivers I restarted the computer. Once again it crashed so I powered the computer back up again. Everything seems to load properly except the Ubuntu login screen does not appear. I can hear the drums but the screen is black.

Has anyone ever had a similar problem and know of a way to correct this problem without reinstalling Ubuntu? Any advice would be greatly appreciated. Thanks.

---

### Post by teaker1s on 2007-03-10
yep I've had these problems and your core issue is xorg crashing with NVIDIA GeForce Go 6150.
Mine became so bad I moved to debiah etch and beta driver from nvidia.

firstly  boot recovery kernel from grub and 
```
sudo dpkg-reconfigure xserver-xorg
```
set driver as "nv" or try "vesa"
failing that you can try nvidia beta driver (openGL)

note of my hp laptop issues here
[https://wiki.ubuntu.com/hp_dv6000_series_%28dv6116eu%29#head-da222db055e3979c23d4e2e5cc50bcc211672165]("https://wiki.ubuntu.com/hp_dv6000_series_%28dv6116eu%29#head-da222db055e3979c23d4e2e5cc50bcc211672165")

---

### Post by bradweiser on 2007-03-11
Thanks teaker1s. I switched back to the Vesa driver temporarily. I will definitely check out your link and try the nvidia beta driver (openGL).

---

### Post by bradweiser on 2007-03-11
Oh yah, on this series laptop I have to boot with noapic.

---

### Post by jcaveman on 2007-03-12
If you want nVidia drivers to work with this system you'll have to go out to nVidia and get the latest and greatest drivers.  The ones in the repository don't seem to correctly support the integrated nVidia graphics in this laptop.

---

### Post by bradweiser on 2007-03-12
Yes I have been having problems getting the correct nVidia driver to work on my laptop. I've been unsuccessful with both Automatix and Envy.

Does anyone know which driver I need and what would be the best way to obtain the driver?

Once I get the correct nVidia driver I would like to get Beryl running and then work on the wireless situation.

On another note, my laptop can now restart and shutdown without crashing.

---

### Post by teaker1s on 2007-03-12
direct from nvidia and select the 64bit :) one
[http://www.nvidia.com/object/linux_display_ia64_1.0-5336]("http://www.nvidia.com/object/linux_display_ia64_1.0-5336")

---

### Post by bradweiser on 2007-03-25
Oops! I just read your last post after trying to install the Linux IA32 Nvidia drivers (NVIDIA-Linux-x86-1.0-9755-pkg1) and am now having some problems.

Will this driver work properly, or should I install the 64 bit driver?

My system boots, gets all the way through the basic load & initialization sequence (Nvidia splash screen displays too), tries to put up a user login screen, then puts up an error dialog with the message "No serving hosts were found."

Does anyone know how do I fix this? Thank you.

---

### Post by teaker1s on 2007-03-26
I'm no nvidia expert, but I'd try the 64bit if your system is 64bit and you have 64bit ubuntu

---

### Post by bradweiser on 2007-03-26
I'm running 32 bit Ubuntu, so that's why I figured I should install the 32 bit Nvidia driver.

---

### Post by randall_l on 2007-03-26
Hopefully the information here will help someone...

I purchased a Compaq V6000 (V6215CA) from a local FutureShop:
[INDENT]AMD Turion™ 64 X2 Dual-Core TL-50, 1.6 GHz;
15.4" WXGA High-Definition* BrightView Widescreen (1280 x 800);
120GB Hard Drive (SATA);
1024MB DDR2 RAM;
Integrated 802.11 b/g Wireless LAN (Turns out to be a Broadcom 4311 (rev 1));
NVIDIA GeForce Go 6150 with up to 288MB (shared).[/INDENT]

I've been using Debian on my 4 desktop systems for the past 3.5 years, and recently switched to Ubuntu (stripped down) for the more frequent bug fixes.

At first, I couldn't get Edgy (i386) to boot at all from the Live CD.  Fortunately, I hadn't wiped out Vista yet, so I Googled the issue and found that adding the kernel parameter "noapic" at boot (using F6 from boot menu) allowed the Live CD to boot.

Upon install, Edgy carried over the "noapic" option to the install, so I had no worries there.

The issues upon reboot:
[INDENT]touchpad intermittent;
only 1024x768 available;
wireless networking non-functional;
headset/mic jack non-functional;
unable to mount USB devices.[/INDENT]

The touchpad issue disappeared when I switched over to Edgy AMD64 (alternate) and got rid of the wacom sections in xorg.conf. (I can't stand Gnome or KDE, so I only installed the base system, then added Enlightenment [it's faster, it's pretty, and it's got a *much* smaller footprint], gsynaptics and hotkeys)

The resolution issue disappeared when I installed NVIDIA-Linux-x86_64-1.0-9755-pkg2.run from [www.nvidia.com](www.nvidia.com)

The wireless network issue disappeared when I followed the instructions here: [http://ubuntuforums.org/showthread.php?p=1071920&mode=linear]("http://ubuntuforums.org/showthread.php?p=1071920&mode=linear")

At first, I tried the instructions here: [http://ubuntuforums.org/showthread.php?t=322817]("http://ubuntuforums.org/showthread.php?t=322817")
But then the mixer epplets and media keys couldn't change the volume (had to use alsamixer or alsamixergui).  I suffered for a bit, but then got too frustrated with the extra steps to change the volume.  I downloaded RC3 of alsa-driver/alsa-lib 1.14 and RC2 of alsa-utils 1.14 (compiled and installed respectively) and upon reboot, EVERYTHING works, headset/mic jacks, speakers, internal mic, PCM volume.  The only issue is that when I plug in earphones, it doesn't mute the speakers--I have to mute/unmute to get the switch to happen (something I can live with).

The USB issue disappeared when I followed the instructions here [https://launchpad.net/ubuntu/+source/linux-source-2.6.15/+bug/49367/comments/2]("https://launchpad.net/ubuntu/+source/linux-source-2.6.15/+bug/49367/comments/2")
(Additionally, I wrote a couple scripts [ehci-disable and ehci-enable], put them in /scripts/ that I created and edited rc.local to call ehci-disable).

I really only have one issue left to resolve: the QuickPlay media key doesn't seem to be mapped (I'm sure I just have to play with the keymap).

Cheers!
Randall

---

### Post by bradweiser on 2007-03-26
Good information, but how can I resolve the "No serving hosts were found" issue?

---

### Post by randall_l on 2007-03-26
Sounds like gdm is having issues connecting to the Xserver, bradweiser.  It might be worth taking a look at your logs for any clues.

I don't use any sort of graphical login myself.  A console login is fine for me as I don't always want to start X right away, and I've always found them (xdm, gdm) to be a bit buggy for my taste.

Cheers!
Randall

---

### Post by randall_l on 2007-03-26
I've got an update on the QuickPlay media key from earlier...

After responding to bradweiser's question, the light bulb went on about checking logs.

I found:
[INDENT]Mar 26 16:15:51 localhost kernel: [  464.997436] atkbd.c: Unknown key pressed (translated set 2, code 0x88 on isa0060/serio0).
Mar 26 16:15:51 localhost kernel: [  464.997443] atkbd.c: Use 'setkeycodes e008 <keycode>' to make it known.[/INDENT]

So I did.  Then I ran xev and it responded just fine when the QuickPlay button was pressed.

A quick change to my hotkeys keyboard definition and it works perfectly.

Now more than ever, Linux just works!

Cheers!
Randall

---

### Post by bradweiser on 2007-03-27
Okay, I've resolved the "No serving hosts were found" issue. 

To correct this issue I ran recovery mode and then edited /etc/gdm/gdm.custom.conf

I set
[xdmcp]
Enable=false

Then I set
[servers]
0=gdm

I then restarted the computer and ran Ubuntu as I normally would and voila! It worked!

So far it seems like the video drivers are working properly. I'm going to bed so I'll have to verify tomorrow.

There was a usefull thread from which I obtained some useful information.
[http://www.ubuntuforums.org/showthread.php?t=135304&highlight=No+serving+hosts+were+found]("http://www.ubuntuforums.org/showthread.php?t=135304&highlight=No+serving+hosts+were+found")

---

### Post by bradweiser on 2007-04-03
So I tried setting up the wireless as provided based on the instructions found here [http://ubuntuforums.org/showthread.php?t=185174]("http://ubuntuforums.org/showthread.php?t=185174")

My blue wireless light now turns on and I can see unsecured wireless networks in Network Manager; however, I cannot connect. I'm thinking this may be a driver issue, but then again why would I be able to see a variety of networks?

On another note, does anyone know how to share an internet connection with another Ubuntu laptop? Say one laptop is connected directly to a cable modem, can another laptop share the internet connection via wireless?

Thanks again.

---

### Post by bradweiser on 2007-04-03
I installed wifi radar and now my network manager basically has no wireless options. I can see wireless networks but I can't obtain an IP address when I try to connect.

---

### Post by impkokay on 2007-04-09
I have the exact same system as you but I can not even load from the install cd. I have tried the 32 and 64 bit versions and both crash to a blank screen after the initial moving bar shows up. I'm a newby as well so specific instructions would be greatly appreciated.
Thanks

---

### Post by RD1945 on 2007-04-13
try to load the cd with the noapic kernel option...

---

