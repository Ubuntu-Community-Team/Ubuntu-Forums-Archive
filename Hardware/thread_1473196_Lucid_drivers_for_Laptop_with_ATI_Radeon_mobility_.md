---
title: "Lucid drivers for Laptop with ATI Radeon mobility X1600 faulty"
date: 2010-05-05
forum: Hardware
---

### Post by Tiko on 2010-05-05
Hi all,

I just updated from ubuntu karmic to lucid, using ATI M56P Radeon Mobility X1600.
When I log into the desktop environments, my windows manager(metacity?) is faulty.
I couldn't get a proper boot log of grub(i think i have ubuntu's log), though i see flashes" of messages less than 0.2 seconds showing some "IRQ" error. The irq error was later replaced with some lines of number in square brackets and messages too fast to read, after i played around in synaptics with the drivers.

Also, not knowing what the "nvidia x server" was (since i'm using ati), I removed it and found out it was essential. Later I installed it back.


In the desktop environment:

First, the mouse cursor stuck at a perpetual "X" indicating busy.

Second, all applications opened, do not have a wrapper, i.e. application window, if there's any, cannot be moved. Hence, all application stack atop one another on the top left screen.

Remedy:
1) Go to, system->preference->appearence -> visual effects tab.
Click on any of the "normal" or "extra", it'll attempt to search for driver. After searching, it'll say "driver cannot be found", and the wrapper of all the applications miraculously came back. Though "appearance effects" cannot be switched on.

2) open terminal. type in "metacity --replace". Same thing appearance effects is gone.


Problem Identification:

The very first release of Karmic, everything works fine for my displays and environments.
If I'm not wrong I was using xorg's or xserver (notice the name is singular, not the combined one) ATI drivers. Later into Dec-Jan, I decided to play around and update my driver through synaptics using the latest xserver-xorg ati driver and the problem surfaced. I downgraded back and it works.

By deduction, I'm pretty sure Lucid's new packages of xserver-xorg drivers has some problems with my hardware compatibility.

I've read that I'm not supposed to use fglrx drivers, and it isn't installed by default. So, it's not related to my issue.

Now i'm usind the xorg-edger's drivers, still no improvement.

I'm not a hardcore geek(in fact I'm very noob), so perhaps I may have missed some cues. This is all that I have observed.

Is anyone facing the same issue? I can provide some logs if anyone can show me directions.
Any help will very much be appreciated.

Thank you very much!

---

### Post by Tiko on 2010-05-05
Ok, I found some other users with similar problem, but different hardware.

[http://ubuntuforums.org/showthread.php?t=1470735](http://ubuntuforums.org/showthread.php?t=1470735)

Seems "compiz --replace" works too.
However that doesn't solve the special effects disabled problem.

Anyone familiar with the same problem?

---

### Post by Tiko on 2010-05-05
Some small updates and things I forgot to mention:

I can't find my xconf.d file which according to some threads, is supposed to exist.

When i run compiz i get output that looks like this.

```
Xlib:  extension "GLX" missing on display ":0.0".
compiz (core) - Fatal: Root visual is not a GL visual
compiz (core) - Error: Failed to manage screen: 0
compiz (core) - Fatal: No manageable screens found on display :0.0

Launching fallback window manager

```

Something to do with my driver not supporting OpenGL?

---

### Post by Tiko on 2010-05-05
bump

---

### Post by facelessloser on 2010-05-06
hi i had the same problem you are having

i since have put 9.10 back on my machine but it was still the same and then i upgraded to 10.04 again and still nothing

---

### Post by Tiko on 2010-05-06
> **facelessloser said:**
> hi i had the same problem you are having

i since have put 9.10 back on my machine but it was still the same and then i upgraded to 10.04 again and still nothing


I'm guessing you've got one of the later updated packages from the repos of one of the component which breaks the windows manager. Either that, or packages that conflicts with each other.

Are you able to get hold of the very first, karmic release that was 2 days after the official launch to try installing?

I, like any advocate, gave away my ubuntu karmic cd. I'll need to dig for my iso file somewhere. I remember my karmic live cd works, and the effects (wobbly windows ftw) works too.

---

### Post by Confused Computer User on 2010-05-07
Dito here. ATI Radeon X1600 on my desktop (with an asus P4P 800 mother board) and the system is slow as ...

@facelessloser
I ran and still run sometimes 9.10 with no obvious problems or slowdowns. It works the best for me but its support runs out in a year so I want to move on to the new release. Problem is, as stated, 10.04 is not working well with this video card.

I actually went all the way to removing the ATI card and rely on the onboard video memory (and I did pay attention to the bio settings).
This proved itself flawed as well as I ran in other video related issues. Mainly not being able to play video for DVDs (sound works but I get a black screen for the video)

So any feed back from advanced users would be appreciated.

Thanks.

---

### Post by Tiko on 2010-05-10
Ok, I got rid of the "IRQ" error. Actually, I managed to see the text when the screen froze and boot up hung. It's a "I/O error" with "sr0 read error" of sorts. Turns out that blank cd-r in my drive is giving part of the quirky problem. Took it out and that msg didn't flash again.

*bump* Could any guru provide some kind of help please?

Thanks~

---

### Post by Tiko on 2010-05-16
Hmm... new observation.
My laptop overheats now, which never happened in Karmic. Though it did when I was using windows.

Flash based players (youtube) cannot be enlarged to full screen mode, firefox will crash.

Some kernel processes seems to hang quite a lot. Unable to shutdown properly.
There always seems to be some program hanging with the status "tty" something.

The slew of issues is hard to pinpoint whether I'm experience failing hardware, driver problem, or other software problem...

*bump*

---

### Post by Confused Computer User on 2010-05-16
> **Chrisco66 said:**
> Try this, it worked for me.  

[http://wiki.cchtml.com/index.php/Ubuntu_Lucid_Installation_Guide](http://wiki.cchtml.com/index.php/Ubuntu_Lucid_Installation_Guide)


I tried this on a fresh install of 10.04 and I at least got it out of the slow motion effect and it seems to runs fine. The only issue is that I can't activate the visual effects but otherwise it's a step forward for usability at least.

---

### Post by Tiko on 2010-05-18
> **Confused Computer User said:**
> I tried this on a fresh install of 10.04 and I at least got it out of the slow motion effect and it seems to runs fine. The only issue is that I can't activate the visual effects but otherwise it's a step forward for usability at least.

Thanks I tried the method, though fglrx stuff doesn't seem to work for me. And I'm not sure where to check what driver is actually being used. The closest I have of a report summary is from the benchmark tools (attached kernel and display report at bottom).
Not sure why my "VIDEO" is "ACPI Video Driver"

I'm using mobility radeon here, so AMD don't directly support it. The vendors for my laptop seems to only have window's drivers, and I'm too noob to port it to linux.

Anyway I traced your link to a bug report [https://bugs.launchpad.net/ubuntu/+source/fglrx-installer/+bug/494699](https://bugs.launchpad.net/ubuntu/+source/fglrx-installer/+bug/494699)
Seems like X11 has issues with ATI, or vice versa.

```

-Loaded Modules-
btrfs
zlib_deflate
crc32c        : CRC32c (Castagnoli) calculations wrapper for lib/crc32c
libcrc32c        : CRC32c (Castagnoli) calculations
ufs
qnx4
hfsplus        : Extended Macintosh Filesystem
hfs
minix
ntfs        : NTFS 1.2/3.x driver - Copyright (c) 2001-2007 Anton Altaparmakov
vfat        : VFAT filesystem support
msdos        : MS-DOS filesystem support
fat
jfs        : The Journaled Filesystem (JFS)
xfs        : SGI XFS with ACLs, security attributes, realtime, large block/inode numbers, no debug enabled
exportfs
reiserfs        : ReiserFS journaled filesystem
binfmt_misc
rfcomm        : Bluetooth RFCOMM ver 1.11
ppdev
sco        : Bluetooth SCO ver 0.6
bridge
stp
bnep        : Bluetooth BNEP ver 1.3
l2cap        : Bluetooth L2CAP ver 2.14
vboxnetadp        : VirtualBox Network Adapter Driver
vboxnetflt        : VirtualBox Network Filter Driver
vboxdrv        : VirtualBox Support Driver
fbcon
tileblit        : Tile Blitting Operation
font        : Console Fonts
bitblit        : Bit Blitting Operation
softcursor        : Generic software cursor
vga16fb        : Legacy VGA framebuffer device driver
vgastate        : VGA State Save/Restore
btusb        : Generic Bluetooth USB driver ver 0.6
bluetooth        : Bluetooth Core ver 2.15
joydev        : Joystick device interfaces
snd_hda_codec_realtek        : Realtek HD-audio codec
snd_hda_intel        : Intel HDA driver
pcmcia        : PCMCIA Driver Services
snd_hda_codec        : HDA codec core
snd_hwdep        : Hardware dependent layer
snd_pcm_oss        : PCM OSS emulation for ALSA.
snd_mixer_oss        : Mixer OSS emulation for ALSA.
snd_pcm        : Midlevel PCM code for ALSA.
snd_seq_dummy        : ALSA sequencer MIDI-through client
snd_seq_oss        : OSS-compatible sequencer module
arc4        : ARC4 Cipher Algorithm
snd_seq_midi        : Advanced Linux Sound Architecture sequencer MIDI synth.
snd_rawmidi        : Midlevel RawMidi code for ALSA.
snd_seq_midi_event        : MIDI byte &lt;-&gt; sequencer event coder
snd_seq        : Advanced Linux Sound Architecture sequencer.
snd_timer        : ALSA timer interface
snd_seq_device        : ALSA sequencer device management
radeon        : ATI Radeon
iwl3945        : Intel(R) PRO/Wireless 3945ABG/BG Network Connection driver for Linux
ttm        : TTM memory manager subsystem (for DRM device)
iwlcore        : iwl core
sdhci_pci        : Secure Digital Host Controller Interface PCI driver
snd        : Advanced Linux Sound Architecture driver for soundcards.
tifm_7xx1        : TI FlashMedia host driver
drm_kms_helper        : DRM KMS helper
yenta_socket
rsrc_nonstatic
sdhci        : Secure Digital Host Controller Interface core driver
mac80211        : IEEE 802.11 subsystem
acer_wmi        : Acer Laptop WMI Extras Driver
irda        : The Linux IrDA Protocol Stack
crc_ccitt        : CRC-CCITT calculations
video        : ACPI Video Driver
tifm_core        : TI FlashMedia core driver
led_class        : LED Class Interface
pcmcia_core        : Linux Kernel Card Services
output        : Display Output Switcher Lowlevel Control Abstraction
drm        : DRM shared core routines
i2c_algo_bit        : I2C-Bus bit-banging algorithm
psmouse        : PS/2 mouse driver
serio_raw        : Raw serio driver
cfg80211        : wireless configuration support
intel_agp
agpgart        : AGP GART driver
soundcore        : Core sound module
lp
snd_page_alloc        : Memory allocator for ALSA system.
parport
usbhid        : USB HID core driver
hid
ohci1394        : Driver for PCI OHCI IEEE-1394 controllers
ieee1394
tg3        : Broadcom Tigon3 ethernet driver

``````
-Display-
Resolution        : 1280x800 pixels
Vendor        : The X.Org Foundation
Version        : 1.8.1
-Monitors-
Monitor 0        : 1280x800 pixels
-Extensions-
BIG-REQUESTS
Composite
DAMAGE
DOUBLE-BUFFER
DPMS
DRI2
Generic Event Extension
MIT-SCREEN-SAVER
MIT-SHM
RANDR
RECORD
RENDER
SECURITY
SHAPE
SYNC
X-Resource
XC-MISC
XFIXES
XFree86-DGA
XFree86-VidModeExtension
XINERAMA
XInputExtension
XKEYBOARD
XTEST
XVideo
-OpenGL-
Vendor        : Unknown
Renderer        : Unknown
Version        : Unknown
Direct Rendering        : No
```

---

### Post by scary_jeff on 2010-05-18
> **Tiko said:**
> Hmm... new observation.
My laptop overheats now, which never happened in Karmic. Though it did when I was using windows.

Flash based players (youtube) cannot be enlarged to full screen mode, firefox will crash.

Some kernel processes seems to hang quite a lot. Unable to shutdown properly.
There always seems to be some program hanging with the status "tty" something.

The slew of issues is hard to pinpoint whether I'm experience failing hardware, driver problem, or other software problem...

*bump*

Full screen youtube will crash my firefox as well. I am also unable to enable desktop effects. Running glxinfo shows that I don't seem to have GLX set up at all. I followed the guide here [https://wiki.ubuntu.com/X/Troubleshooting/FglrxInteferesWithRadeonDriver](https://wiki.ubuntu.com/X/Troubleshooting/FglrxInteferesWithRadeonDriver) to fully remove the fglrx driver, but this didn't help me. The instructions for removing fglrx also left behind lots of files, so I ended up installing fglrx, then apt-get remove --purge ing it, before restoring the open source driver. This left me back where I started (still no GLX). I found a number of threads where people were having GLX issues in 10.04, especially with ATI graphics adapters; the most common solution seems to have been to go back to 9.10 :/

---

### Post by Tiko on 2010-05-18
> **scary_jeff said:**
> Full screen youtube will crash my firefox as well. I am also unable to enable desktop effects. Running glxinfo shows that I don't seem to have GLX set up at all. I followed the guide here [https://wiki.ubuntu.com/X/Troubleshooting/FglrxInteferesWithRadeonDriver](https://wiki.ubuntu.com/X/Troubleshooting/FglrxInteferesWithRadeonDriver) to fully remove the fglrx driver, but this didn't help me. The instructions for removing fglrx also left behind lots of files, so I ended up installing fglrx, then apt-get remove --purge ing it, before restoring the open source driver. This left me back where I started (still no GLX). I found a number of threads where people were having GLX issues in 10.04, especially with ATI graphics adapters; the most common solution seems to have been to go back to 9.10 :/

Ran glxinfo and here's what i got.
```

name of display: :0.0
Xlib:  extension "GLX" missing on display ":0.0".
```Same thing with the display report above in the post above you. OpenGL renderer seems to be not installed.

I tried removing all packages that are connected to ATI, hoping to revert to default VESA. However, I got into complications and VESA failed to load as some kernel process is using it.

I'm tempted to revert to Karmic 9.10, but I heard support is cutting off soon :/
Perhaps digging the bug reports on the missing OpenGL renderer would yield something useful.

---

### Post by Confused Computer User on 2010-05-18
> **Tiko said:**
> Thanks I tried the method, though fglrx stuff doesn't seem to work for me. 


You're welcomed. Like you i'm not an advance user so i only posted what worked for me. As I mentioned in my post the visual effects don't work ie compiz and company


> **Tiko said:**
> Ran glxinfo and here's what i got.
Same thing with the display report above in the post above you. OpenGL renderer seems to be not installed.

I tried removing all packages that are connected to ATI, hoping to revert to default VESA. However, I got into complications and VESA failed to load as some kernel process is using it.

I'm tempted to revert to Karmic 9.10, but I heard support is cutting off soon :/
Perhaps digging the bug reports on the missing OpenGL renderer would yield something useful.

I get the same thing. ATI is no help. They no longer support older models and Ubuntu seems to be having a "field day" in what concerns older ATI models.

For 9.10 the support ends in April 2011. This is according to:
[http://en.wikipedia.org/wiki/List_of_Ubuntu_releases#Ubuntu_9.10_.28Karmic_Koala.29](http://en.wikipedia.org/wiki/List_of_Ubuntu_releases#Ubuntu_9.10_.28Karmic_Koala.29)

Now i reverted back to that and then went back to 10.04 again when I got the solution/fix that I posted. I figure that the eye candy is not a must have and as long as the comp runs smooth i'm ok. I'll wait for further updates as well as the release of 10.10. My understanding is that 10.10 will offer better support for ATI cards. 

See:
[http://www.phoronix.com/scan.php?page=news_item&px=ODI0Nw](http://www.phoronix.com/scan.php?page=news_item&px=ODI0Nw)

The issue is that I'm not sure to what degree this extends to older video cards:(

---

### Post by Tiko on 2010-05-18
> **Confused Computer User said:**
> You're welcomed. Like you i'm not an advance user so i only posted what worked for me. As I mentioned in my post the visual effects don't work ie compiz and company




I get the same thing. ATI is no help. They no longer support older models and Ubuntu seems to be having a "field day" in what concerns older ATI models.

For 9.10 the support ends in April 2011. This is according to:
[http://en.wikipedia.org/wiki/List_of_Ubuntu_releases#Ubuntu_9.10_.28Karmic_Koala.29](http://en.wikipedia.org/wiki/List_of_Ubuntu_releases#Ubuntu_9.10_.28Karmic_Koala.29)

Now i reverted back to that and then went back to 10.04 again when I got the solution/fix that I posted. I figure that the eye candy is not a must have and as long as the comp runs smooth i'm ok. I'll wait for further updates as well as the release of 10.10. My understanding is that 10.10 will offer better support for ATI cards. 

See:
[http://www.phoronix.com/scan.php?page=news_item&px=ODI0Nw](http://www.phoronix.com/scan.php?page=news_item&px=ODI0Nw)

The issue is that I'm not sure to what degree this extends to older video cards:(

Thanks for the links, good to know more info :)

I'm trying to do graphics design, and I can't start/run the Blender 3d-imaging software.
So I'm sort of in desperate mode to get cracking on stuff that has been held up.
The only fix I have is use VBOX to run windows and try to see if it works properly.
Sigh~

---

### Post by Confused Computer User on 2010-05-18
> **Tiko said:**
> Thanks for the links, good to know more info :)

I'm trying to do graphics design, and I can't start/run the Blender 3d-imaging software.
So I'm sort of in desperate mode to get cracking on stuff that has been held up.
The only fix I have is use VBOX to run windows and try to see if it works properly.
Sigh~
No prob. It helps to know where someone gets their info from.

Windows might do a better job but do remember that the support is still out (regardless of your operating system). In my case, i only paid 10 dollars for the whole system so I'm not taking too much of a punch, yet I'm not willing to fork up an extra 200$ for a widows OS. Ergo, I'm sticking with Linux for now.

In the mean time, I hope there will be a solution to this issue prior to the 10.10 release. Other wise, wait till then and hope that release works better.


Quick note. I remember seeing someone mention going from Ubuntu to Debian as the later offer better support (as in it worked better) for ATI cards. I'll try to find that post again and add the link to it.

EDIT:
And here it is:
> **waynefoutz said:**
> Welcome to my hell. I have ATI Radeon x1270. If you install Intrepid (8.10) instead of Karmic, you can get Catalyst 9.3 running fine, no, not fine, BEAUTIFUL. ATI stinks, this is their fault. They made the video system in my one year old laptop obsolete 3 months after I purchased it.  You need xorg-xserver 1.5.2 or lower running, which is what Intrepid is using. Problem is Intrepid becomes obsolete in April. The latest kernel update was supposed to fix this, the open source drivers were going to be improved. It failed miserably in my opinion.2d and Compiz work fine, but no 3d.  Hopefully the next build will have better open source drivers. In the meantime, I'd go with intrepid, or what I plan on doing is abandoning Ubuntu all together for the time being and installing Debian 5.0. It has a compatible xorg for the ATI drivers.

---

### Post by Confused Computer User on 2010-05-22
> **Confused Computer User said:**
> I found a link that suggests:

> If you find that after upgrading to X.Org 7.3 your display becomes very slow, and you own ATI Radeon, all you need to do is to put this line in the Device section of your xorg.conf:

Option "MigrationHeuristic" "greedy"

After that, your display should return to the normal speed, and X server will stop burning CPU cycles during such simple tasks like moving windows or switching workspaces.

See:
[http://www.linuxinsight.com/your-ati-radeon-very-slow-on-xorg-x-server-1.3.html](http://www.linuxinsight.com/your-ati-radeon-very-slow-on-xorg-x-server-1.3.html)

Now I haven't tried this, and after 10 re-installs I am not willing to try this yet.

Didn't want to rephrases this so I quoted myself. If any one has luck with this please post back with outcome.

---

### Post by Tiko on 2010-05-23
Posted bug at launchpad
[https://bugs.launchpad.net/bugs/584202](https://bugs.launchpad.net/bugs/584202)

Interestingly, in Lucid my display is now running on Nvidia X driver, even though my hardware is ATi.
I'm really confused that even works at all.

I read up:
[https://wiki.ubuntu.com/X/Drivers](https://wiki.ubuntu.com/X/Drivers)

Upon further testing broke the display totally. Lucid is not usable due to visual issues.
I installed my Karmic side by side, and is trying to further diagnose it.

---

### Post by Tiko on 2010-05-23
Just thought I would paste my working-system report here with Karmic to see the difference with Lucid

```
-Loaded Modules-
ufs
qnx4
hfsplus        : Extended Macintosh Filesystem
hfs
minix
ntfs        : NTFS 1.2/3.x driver - Copyright (c) 2001-2007 Anton Altaparmakov
vfat        : VFAT filesystem support
msdos        : MS-DOS filesystem support
fat
jfs        : The Journaled Filesystem (JFS)
xfs        : SGI XFS with ACLs, security attributes, realtime, large block/inode numbers, no debug enabled
exportfs
reiserfs        : ReiserFS journaled filesystem
binfmt_misc
ppdev
bridge
stp
bnep        : Bluetooth BNEP ver 1.3
snd_hda_codec_realtek        : Realtek HD-audio codec
arc4        : ARC4 Cipher Algorithm
snd_hda_intel        : Intel HDA driver
snd_hda_codec        : HDA codec core
pcmcia        : PCMCIA Driver Services
snd_hwdep        : Hardware dependent layer
ecb        : ECB block cipher algorithm
snd_pcm_oss        : PCM OSS emulation for ALSA.
snd_mixer_oss        : Mixer OSS emulation for ALSA.
snd_pcm        : Midlevel PCM code for ALSA.
btusb        : Generic Bluetooth USB driver ver 0.5
snd_seq_dummy        : ALSA sequencer MIDI-through client
snd_seq_oss        : OSS-compatible sequencer module
snd_seq_midi        : Advanced Linux Sound Architecture sequencer MIDI synth.
snd_rawmidi        : Midlevel RawMidi code for ALSA.
snd_seq_midi_event        : MIDI byte &lt;-&gt; sequencer event coder
snd_seq        : Advanced Linux Sound Architecture sequencer.
snd_timer        : ALSA timer interface
snd_seq_device        : ALSA sequencer device management
snd        : Advanced Linux Sound Architecture driver for soundcards.
yenta_socket
soundcore        : Core sound module
iptable_filter        : iptables filter table
joydev        : Joystick device interfaces
rsrc_nonstatic
sdhci_pci        : Secure Digital Host Controller Interface PCI driver
snd_page_alloc        : Memory allocator for ALSA system.
pcmcia_core        : Linux Kernel Card Services
iwl3945        : Intel(R) PRO/Wireless 3945ABG/BG Network Connection driver for Linux
iwlcore        : iwl core
tifm_7xx1        : TI FlashMedia host driver
tifm_core        : TI FlashMedia core driver
sdhci        : Secure Digital Host Controller Interface core driver
acer_wmi        : Acer Laptop WMI Extras Driver
mac80211        : IEEE 802.11 subsystem
ip_tables        : IPv4 packet filter
psmouse        : PS/2 mouse driver
serio_raw        : Raw serio driver
led_class        : LED Class Interface
cfg80211        : wireless configuration support
x_tables        : {ip,ip6,arp,eb}_tables backend module
irda        : The Linux IrDA Protocol Stack
crc_ccitt        : CRC-CCITT calculations
lp
parport
usbhid        : USB HID core driver
ohci1394        : Driver for PCI OHCI IEEE-1394 controllers
ieee1394
video        : ACPI Video Driver
output        : Display Output Switcher Lowlevel Control Abstraction
radeon        : ATI Radeon
ttm        : TTM memory manager subsystem (for DRM device)
drm        : DRM shared core routines
i2c_algo_bit        : I2C-Bus bit-banging algorithm
tg3        : Broadcom Tigon3 ethernet driver
intel_agp
agpgart        : AGP GART driver
```
```
-Display-
Resolution        : 1280x800 pixels
Vendor        : The X.Org Foundation
Version        : 1.6.4
-Monitors-
Monitor 0        : 1280x800 pixels
-Extensions-
BIG-REQUESTS
Composite
DAMAGE
DOUBLE-BUFFER
DPMS
DRI2
GLX
Generic Event Extension
MIT-SCREEN-SAVER
MIT-SHM
RANDR
RECORD
RENDER
SECURITY
SGI-GLX
SHAPE
SYNC
X-Resource
XC-MISC
XFIXES
XFree86-DGA
XFree86-DRI
XFree86-VidModeExtension
XINERAMA
XInputExtension
XKEYBOARD
XTEST
XVideo
-OpenGL-
Vendor        : DRI R300 Project
Renderer        : Mesa DRI R300 (RV530 71C5) 20090101 x86/MMX/SSE2 TCL
Version        : 1.5 Mesa 7.6.1-rc4
Direct Rendering        : Yes
```

---

