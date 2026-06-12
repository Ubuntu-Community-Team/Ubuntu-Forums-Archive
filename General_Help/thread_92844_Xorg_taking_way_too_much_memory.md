---
title: "Xorg taking way too much memory"
date: 2005-11-20
forum: General Help
---

### Post by endersshadow on 2005-11-20
I was using Breezy on my desktop w/ 256mb ddr ram and only a 900mhz processor and it was running fine, at about 150mb of memory being used at idle (including swap), so I didn't really think too much of it.  Well, I decided to go full Ubuntu and loaded Breezy onto my laptop, which has 512mb ddr and is a 3.1ghz processor and it's using 267mb with 10mb of swap.  I check the system monitor, and my Xorg is using 168mb of ram constantly.  Is there a reason for this, and can I fix it to lower that usage?

Thanks!

---

### Post by endersshadow on 2005-11-21
As more info, I'm on a laptop that's running an Intel 855 video chipset that I've got the 855 resolution fix for...

---

### Post by Niomi on 2005-11-22
I have the same problem, here are some notes I took while restarting gnome:

> 184 at boot, only a few minutes into session and already at 215. after last sentence was typed RAM usage was at 220. about 10 minutes into boot and RAM at 265

40-60% CPU to move a window

My xorg memory usage has been into the nine-hundreds on my 1gig machine. I don't have this problem in KDE/Kubuntu, so I've been using it instead, but I miss gnome.

Edit: Others seem to be having the same problem
[http://ubuntuforums.org/showthread.php?t=85869](http://ubuntuforums.org/showthread.php?t=85869)

---

### Post by unixfudotnet on 2005-11-22
I don't know why, yet I can suspect that it is caching the memory for faster rendering. The cpu spikes may be from the cpu doing the processing that the video card would be doing if dri was enabled. 

That is just some ideas. I would check that dri is working (xdriinfo). Here is what a machine looks like without DRI:

$ xdriinfo 
Xlib:  extension "XFree86-DRI" missing on display ":0.0".
Screen 0: not direct rendering capable.

The way gnome and kde use memory is obviously different, so that may be why you see different results. Not sure on your specifics, though I would suspect DRI is not enabled.

---

### Post by Niomi on 2005-11-22
[QUOTE=unixfudotnet]That is just some ideas. I would check that dri is working (xdriinfo).[/QUOTE]

> niomi@Isis:~$ xdriinfo
xdriinfo: symbol lookup error: xdriinfo: undefined symbol: glXGetProcAddress

What does this error mean? Could this has something to do with the problem?

> I don't know why, yet I can suspect that it is caching the memory for faster rendering.

I do not think the cache is the issue. Upon hover on the system monitor I have running in the taskbar, I get a tooltip stating that my used memory is 100% and my cached memory is 24%. System monitor reports that Xorg is currently using 566.9 MB

---

### Post by endersshadow on 2005-11-24
DRI is enabled...here's my output:

```
Screen 0: i915
```

---

### Post by ekravche on 2005-11-25
[QUOTE=endersshadow]DRI is enabled...here's my output:

```
Screen 0: i915
```[/QUOTE]

I have an integrated intel mobo with an intel 915 video chipset and I experience the same problem.

---

### Post by r0ll3r on 2005-11-26
Same problem here. I have a Clevo M121C notebook with Intel 855GME, 256 MB RAM, and Xorg takes up 172 megs of memory. Of course this is virtual memory, so only the needed part is staying in the real memory, but i don't like that. I've installed Ubuntu to other machines, desktops and laptops too, but none of them are taking up that much memory by Xorg.
Running xrestop does not reveal much info about that issue. But i am keen on solving that. Really.

EDIT:
setting /etc/X11/xorg.conf: Section "Device": Driver "vesa" will decrease my Xorg memory usage to 58.1 MB. This will also make direct rendering disabled.

EDIT2:
I had to realize, that when you look at Xorg virtual memory usage, it is not what we think it is. It is a sum of shared libraries and other thingies. Anyway. Check out the System Monitor's Resources tab, where i see that i only consumed 108.7 MiB. The reason Xorg has this big number at virtual memory info is i belive the shared memory architecture on my laptop (intel 855gme).

Todo: find out, why it is so slow after logging in to get to the desktop.

---

### Post by Niomi on 2005-12-03
I am really dissapointed with the response (or lack of) on this problem. I have been trying to get this fixed for months. It is a -major- bug. For some reason it has now begun to affect me while using KDE as well as gnome, there is no reason xorg should be using 950MB out of my 1GB of memory.
If this continues I'll be switching to another distro.. until then I'm going to consider permanantly switching to XFCE

---

### Post by soulestream on 2005-12-04
> I am really dissapointed with the response (or lack of) on this problem. I have been trying to get this fixed for months. It is a -major- bug

I have no problems on my laptop.I tried logging into your laptops, but that wouldnt work.;) 

Maybe you could tell us what applications you are running or give the output of

top
ps -ef
and post your xorg.conf

that way if something was out of the ordinary someone might be able to tell other than guessing. Just a for instance if I use my tuner card my PC usage/Mem spikes greatly because X is drawing the screen. Some many be using E17, etc

soule

---

### Post by Niomi on 2005-12-21
For awhile this didn't appear to be a problem on KDE, but recently it seems to be affecting that as well, so I started playing around in fluxbox. Unfortunately it affects flux as well... it will get up anywhere to 400ish resident memory before I restart X.

I poked around the forum and found a tip to disable glx and dri.. I did that and went to the dpkg xserver reconfigure routine. I also switched from 'nvidia' drivers to 'nv'. For this session, memory was around 23MB at boot and it's now around 45MB. Not bad so far, I'm going to leave it overnight and see how it's done since morning. I also grabbed a program called xrestop, here is the output of that:

```
res-base Wins  GCs Fnts Pxms Misc   Pxm mem  Other   Total   PID Identifier
2000000   251  133    1  468  117     9965K     12K   9978K   ?   Ubuntu Forums - Reply to To1800000    40  126    0  104   37     9591K      4K   9596K   ?   wnck-applet
3e00000    56  100    1   33   57     7005K      5K   7011K   ?   niomi@Isis: ~
3600000     0    0    0    1    0     5120K      0B   5120K   ?   <unknown>
3c00000    62  136    1   66   70     3690K      7K   3697K   ?   System Monitor
2a00000    38   49    0   23   17     2384K      2K   2387K   ?   notification-area-applet
1400000    44  114    1   23   29     1875K      5K   1880K   ?   Left Centered Panel
3200000    32   27    0   15   14     1868K      1K   1870K   ?   quick-lounge-applet
3400000    14   25    0   15   12     1684K      1K   1685K   ?   gweather-applet-2
3000000    20  116    1   26   26     1588K      4K   1593K   ?   mini_commander_applet
0e00000    98   33    1  144 2777     1092K     69K   1161K  1839 xfwm4
1600000    18   33    1   12   16     1086K      2K   1088K   ?   Desktop
3800000    20   28    0    9   15      885K      1K    886K   ?   workrave
1c00000    19   25    0    6   12      784K      1K    785K  1907 update-notifier
2800000    16   25    0    6   10      784K      1K    785K   ?   workrave-applet
1200000    16   25    0    6    9      784K      1K    785K  1878 gnome-typing-monitor
2c00000    15   68    0   11   12      702K      2K    704K   ?   clock-applet
2e00000    18   33    0   11    6      608K      1K    609K   ?   multiload-applet-2
0600000     2    2    0    2    9      384K    312B    384K  1775 gnome-session
1a00000    13   24    0    2    7      100K      1K    101K  1895 gnome-volume-manager
2600000    13   37    1   40   29       34K      2K     37K   ?   klipper
3a00000     0    1    0    0  842        0B     19K     19K   ?   <unknown>
0a00000     1    1    0    0  825        0B     19K     19K   ?   screensaver
0800000    13    1    0    0  428        0B     10K     10K  1842 gnome-settings-daemon
0200000     0    1    1    0    0        0B      1K      1K   ?   <unknown>
1000000     5    1    0    0   13        0B    456B    456B  1944 kded
0c00000    11    1    0    0    5        0B    408B    408B  1844 vino-server
2200000     2    1    0    0    3        0B    144B    144B  1915 notification-daemon
```

Here's my xorg before I made the changes:

```
# /etc/X11/xorg.conf (xorg X Window System server configuration file)
#
# This file was generated by dexconf, the Debian X Configuration tool, using
# values from the debconf database.
#
# Edit this file with caution, and see the /etc/X11/xorg.conf manual page.
# (Type "man /etc/X11/xorg.conf" at the shell prompt.)
#
# This file is automatically updated on xserver-xorg package upgrades *only*
# if it has not been modified since the last upgrade of the xserver-xorg
# package.
#
# If you have edited this file but would like it to be automatically updated
# again, run the following command:
#   sudo dpkg-reconfigure -phigh xserver-xorg

Section "Files"
	FontPath	"/usr/share/X11/fonts/misc"
	FontPath	"/usr/share/X11/fonts/cyrillic"
	FontPath	"/usr/share/X11/fonts/100dpi/:unscaled"
	FontPath	"/usr/share/X11/fonts/75dpi/:unscaled"
	FontPath	"/usr/share/X11/fonts/Type1"
	FontPath	"/usr/share/X11/fonts/CID"
	FontPath	"/usr/share/X11/fonts/100dpi"
	FontPath	"/usr/share/X11/fonts/75dpi"
        # paths to defoma fonts
	FontPath	"/var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType"
	FontPath	"/var/lib/defoma/x-ttcidfont-conf.d/dirs/CID"
EndSection

Section "Module"
	Load	"GLcore"
	Load	"bitmap"
	Load	"ddc"
	Load	"dri"
	Load	"extmod"
	Load	"freetype"
	Load	"glx"
	Load	"int10"
	Load	"type1"
	Load	"vbe"
EndSection

Section "InputDevice"
	Identifier	"Generic Keyboard"
	Driver		"kbd"
	Option		"CoreKeyboard"
	Option		"XkbRules"	"xorg"
	Option		"XkbModel"	"pc104"
	Option		"XkbLayout"	"us"
	Option		"XkbOptions"	"altwin:metawin"
EndSection

Section "InputDevice"
	Identifier	"Configured Mouse"
	Driver		"mouse"
	Option		"CorePointer"
	Option		"Device"		"/dev/input/mice"
	Option		"Protocol"		"ImPS/2"
	Option		"Emulate3Buttons"	"true"
	Option		"ZAxisMapping"		"4 5"
EndSection

Section "Device"
	Identifier	"NVIDIA Corporation NV36 [GeForce FX 5700 LE]"
	Driver		"nvidia"
	BusID		"PCI:1:0:0"
	Option		"UseFBDev"		"true"
	Option		"RenderAccel" "true"
	Option		"NvAGP" "1"
	Option		"NoLogo"
EndSection

Section "Monitor"
	Identifier	"SAMSUNG"
	Option		"DPMS"
	HorizSync	30-68
	VertRefresh	50-85
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Device		"NVIDIA Corporation NV36 [GeForce FX 5700 LE]"
	Monitor		"SAMSUNG"
	DefaultDepth	24
	SubSection "Display"
		Depth		1
		Modes		"1280x1024" "1280x960" "1152x864" "1024x768" "800x600"
	EndSubSection
	SubSection "Display"
		Depth		4
		Modes		"1280x1024" "1280x960" "1152x864" "1024x768" "800x600"
	EndSubSection
	SubSection "Display"
		Depth		8
		Modes		"1280x1024" "1280x960" "1152x864" "1024x768" "800x600"
	EndSubSection
	SubSection "Display"
		Depth		15
		Modes		"1280x1024" "1280x960" "1152x864" "1024x768" "800x600"
	EndSubSection
	SubSection "Display"
		Depth		16
		Modes		"1280x1024" "1280x960" "1152x864" "1024x768" "800x600"
	EndSubSection
	SubSection "Display"
		Depth		24
		Modes		"1280x1024" "1280x960" "1152x864" "1024x768" "800x600"
	EndSubSection
EndSection

Section "ServerLayout"
	Identifier	"Default Layout"
	Screen		"Default Screen"
	InputDevice	"Generic Keyboard"
	InputDevice	"Configured Mouse"
EndSection

Section "DRI"
	Mode	0666
EndSection

```

And after:

```
# /etc/X11/xorg.conf (xorg X Window System server configuration file)
#
# This file was generated by dexconf, the Debian X Configuration tool, using
# values from the debconf database.
#
# Edit this file with caution, and see the /etc/X11/xorg.conf manual page.
# (Type "man /etc/X11/xorg.conf" at the shell prompt.)
#
# This file is automatically updated on xserver-xorg package upgrades *only*
# if it has not been modified since the last upgrade of the xserver-xorg
# package.
#
# If you have edited this file but would like it to be automatically updated
# again, run the following command:
#   sudo dpkg-reconfigure -phigh xserver-xorg

Section "Files"
	FontPath	"/usr/share/X11/fonts/misc"
	FontPath	"/usr/share/X11/fonts/cyrillic"
	FontPath	"/usr/share/X11/fonts/100dpi/:unscaled"
	FontPath	"/usr/share/X11/fonts/75dpi/:unscaled"
	FontPath	"/usr/share/X11/fonts/Type1"
	FontPath	"/usr/share/X11/fonts/CID"
	FontPath	"/usr/share/X11/fonts/100dpi"
	FontPath	"/usr/share/X11/fonts/75dpi"
        # paths to defoma fonts
	FontPath	"/var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType"
	FontPath	"/var/lib/defoma/x-ttcidfont-conf.d/dirs/CID"
EndSection

Section "Module"
	Load	"GLcore"
	Load	"bitmap"
	Load	"ddc"
	Load	"extmod"
	Load	"freetype"
	Load	"int10"
	Load	"type1"
	Load	"vbe"
EndSection

Section "InputDevice"
	Identifier	"Generic Keyboard"
	Driver		"kbd"
	Option		"CoreKeyboard"
	Option		"XkbRules"	"xorg"
	Option		"XkbModel"	"pc104"
	Option		"XkbLayout"	"us"
	Option		"XkbOptions"	"altwin:metawin"
EndSection

Section "InputDevice"
	Identifier	"Configured Mouse"
	Driver		"mouse"
	Option		"CorePointer"
	Option		"Device"		"/dev/input/mice"
	Option		"Protocol"		"ImPS/2"
	Option		"Emulate3Buttons"	"true"
	Option		"ZAxisMapping"		"4 5"
EndSection

Section "Device"
	Identifier	"NVIDIA Corporation NV36 [GeForce FX 5700 LE]"
	Driver		"nv"
	BusID		"PCI:1:0:0"
EndSection

Section "Monitor"
	Identifier	"SAMSUNG"
	Option		"DPMS"
	HorizSync	30-65
	VertRefresh	50-75
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Device		"NVIDIA Corporation NV36 [GeForce FX 5700 LE]"
	Monitor		"SAMSUNG"
	DefaultDepth	24
	SubSection "Display"
		Depth		1
		Modes		"1280x1024"
	EndSubSection
	SubSection "Display"
		Depth		4
		Modes		"1280x1024"
	EndSubSection
	SubSection "Display"
		Depth		8
		Modes		"1280x1024"
	EndSubSection
	SubSection "Display"
		Depth		15
		Modes		"1280x1024"
	EndSubSection
	SubSection "Display"
		Depth		16
		Modes		"1280x1024"
	EndSubSection
	SubSection "Display"
		Depth		24
		Modes		"1280x1024"
	EndSubSection
EndSection

Section "ServerLayout"
	Identifier	"Default Layout"
	Screen		"Default Screen"
	InputDevice	"Generic Keyboard"
	InputDevice	"Configured Mouse"
EndSection

Section "DRI"
	Mode	0666
EndSection
```

Earlier in this post I reported xorg was at 45MB of resident memory, now it's using 55MB :( Please help! I'm getting desperate. Not desperate enough to go back to windows but I'm starting to look at other distros. (Arch doesn't look bad!)



[QUOTE=soulestream]I have no problems on my laptop.I tried logging into your laptops, but that wouldnt work.;) 

Maybe you could tell us what applications you are running or give the output of

top
ps -ef
and post your xorg.conf

that way if something was out of the ordinary someone might be able to tell other than guessing. Just a for instance if I use my tuner card my PC usage/Mem spikes greatly because X is drawing the screen. Some many be using E17, etc

soule[/QUOTE]

---

### Post by Niomi on 2005-12-28
Here are some notes I have taken:
> 184 at boot, only a few minutes into session and already at 215. after last sentance was typed RAM usage was at 220. about 10 minutes into boot and RAM at 265

40-60% CPU to move a window

switching to xfwm4
before switch xorg memory usage is at 567.9 MB
after logout/login xorg at 466.0MB
after reboot xorg starts at 177 MB, by the time gedit is going to take these notes xorg is at 191.2 MB
some minutes later xorg is at 240.0MB

> 32.6MiB on boot
52.7 at 11:22
58.6 at 11:30
85.2 at 13:44
121.2 at 13:53
409 at 18:33

I am about ready to move to another distro. Ubuntu has been a great learning expirience but it's just running waaay to clunky on my PC.

---

### Post by Niomi on 2005-12-29
[xorg log](http://pastebin.com/483145)

---

### Post by pelle.k on 2005-12-29
[http://ubuntuforums.org/showthread.php?t=75620](http://ubuntuforums.org/showthread.php?t=75620)
> Xorg's memory usage includes however much RAM your video card has, iirc. So subtract that from the value you're getting and you should have something close to the real ammount (although there is no sane way of finding out exactly how much RAM it's using). Check the Resources tab and see how much total RAM and swap is being used, that should be a real ammount.

Please post output of top here and we will take a look at it... :)

---

### Post by psusi on 2005-12-29
Ignore it.  Most of that memory is the ram on the video card, not your main ram.

---

### Post by Niomi on 2005-12-29
My video card only has 128MB RAM.. is there a reason it should be running 400MB~600MB, in a minority of cases even 900+ MB?

---

### Post by psusi on 2005-12-29
Whoa!  That does sound like a problem.  A lot of people wonder why X uses ~150 megs of ram and are concerned because they only have 512, but 128 megs of that is the ram on their video card.  If X is using over 500 megs, then something definately is wrong.  

[QUOTE=Niomi]My video card only has 128MB RAM.. is there a reason it should be running 400MB~600MB, in a minority of cases even 900+ MB?[/QUOTE]

---

### Post by pelle.k on 2005-12-29
OK it sounds a little bit crazy. But you haven't posted an output of top yet?
Are you refering to physical memory, or virtual memory then?

Also, just in the spirit of experimenting, my xorg did use 170 megs virtual, 30 meg physical memory, completely standard and untouched during a normal session, Kubuntu - kde 3.5.
After updating and configuring ATI driver 8.20.8 using a Radeon 9600 se, 256 mb ddr, my xorg consumes 50 meg virtual mem, and 30 meg physical mem, though.

This might be a stupid question, but have you apt-get updated your installation and so on? What appz are you using?

---

### Post by Niomi on 2005-12-29
```
top - 20:13:04 up 3 days,  3:41,  2 users,  load average: 5.25, 5.18, 5.09
Tasks: 137 total,   2 running, 135 sleeping,   0 stopped,   0 zombie
Cpu(s): 96.3% us,  3.3% sy,  0.0% ni,  0.0% id,  0.0% wa,  0.3% hi,  0.0% si
Mem:   1036648k total,   990572k used,    46076k free,    37316k buffers
Swap:  3036244k total,    76432k used,  2959812k free,   121940k cached

  PID USER      PR  NI  VIRT  RES  SHR S %CPU %MEM    TIME+  COMMAND
27941 root      25   0  595m 421m 6792 R 92.5 41.6 261:19.18 Xorg
29094 niomi     15   0 63348  25m  12m S  2.3  2.6   7:10.15 krfb
28116 niomi     15   0 30808  17m  12m S  2.0  1.7   8:56.37 gnome-system-mo
28147 niomi     16   0 60128  20m  14m S  1.0  2.0   0:04.54 gnome-terminal
28432 niomi     16   0  236m 161m  22m S  0.7 15.9  14:04.25 firefox-bin
29886 niomi     16   0  2132 1120  844 R  0.3  0.1   0:00.06 top
    1 root      16   0  1560  508  456 S  0.0  0.0   0:01.07 init
    2 root      34  19     0    0    0 S  0.0  0.0   0:00.41 ksoftirqd/0
    3 root      10  -5     0    0    0 S  0.0  0.0   0:01.11 events/0
    4 root      11  -5     0    0    0 S  0.0  0.0   0:00.01 khelper
    5 root      10  -5     0    0    0 S  0.0  0.0   0:00.00 kthread
    7 root      20  -5     0    0    0 S  0.0  0.0   0:00.00 kacpid
   95 root      10  -5     0    0    0 S  0.0  0.0   0:00.65 kblockd/0
  123 root      15   0     0    0    0 S  0.0  0.0   0:07.73 pdflush
  124 root      15   0     0    0    0 S  0.0  0.0   0:04.20 pdflush
  126 root      15  -5     0    0    0 S  0.0  0.0   0:00.00 aio/0
  125 root      15   0     0    0    0 S  0.0  0.0   0:03.96 kswapd0
```

[QUOTE=pelle.k]Are you refering to physical memory, or virtual memory then?[/QUOTE]

I was refering to what in gnome-system-monitor it is described as 'resident memory'. Virtual memory consumption is at 595.3MB.

---

### Post by pelle.k on 2005-12-29
I've read up on intel igp:s and stuff. It seems they are problematic indeed.
I honestly don't know what's the problem, but have you tried installing the ati 8.16.20 driver from repositorys? Or even sudo dpkg-reconfigure xserver-xorg and played aroud with some values? I noticed you haven't set the size of (shared) graphics ram in xorg.conf, and you know the 855 chipset, or was it 915, had problems reporting the size itself from BIOS...
I would start with a simple sudo dpkg-reconfigure xserver-xorg and maybe update the kernel if that isn't done yet. 686 would be recommended.

---

### Post by Niomi on 2005-12-29
[QUOTE=pelle.k]I honestly don't know what's the problem, but have you tried installing the ati 8.16.20 driver from repositorys?[/quote]

I have a Nvidia! Should I try installing the ATI anyway?

> Or even sudo dpkg-reconfigure xserver-xorg and played aroud with some values? I noticed you haven't set the size of (shared) graphics ram in xorg.conf,

I posted my whole xorg.conf, or thought I did. Did I miss anything?

> and you know the 855 chipset, or was it 915, had problems reporting the size itself from BIOS...

I have no idea what you are refering to here.. sorry.

> I would start with a simple sudo dpkg-reconfigure xserver-xorg and maybe update the kernel if that isn't done yet. 686 would be recommended.

Can you recomend any specific xorg.conf changes, or a recomend a good resource on updating the kernel?

---

### Post by pelle.k on 2005-12-30
Hi! Sorry it took me this log to answer :(

I was a bit tired and confused when i wrote that last post :P

No, if you've got an nvidia card, then you i think you should try installing nvidia driver 7667. The nvidia driver 7667 does not support cards older than Geforce3 though.
Try this thread, method 1.
[http://www.ubuntuforums.org/showthread.php?t=75074&highlight=nvidia+drivers](http://www.ubuntuforums.org/showthread.php?t=75074&highlight=nvidia+drivers)

About the 855 and 915 chipset, i was refering to the two posters before you. They too apparently had issues with Xorg.

Using a 686 kernel instad of a 386 (which is the default) would give you a uncertain performance boost, and might even be related to your problem. You won't know that until you've tried it.

Just do: "sudo apt-get install linux-686" and then reboot.

tell us if you were succesful...

---

### Post by Niomi on 2006-03-30
Okay, here's an update...
I upgraded to Dapper, and my kernel with it. The problem persisted.
This obviously required me to drag out the big guns, which would be in my friend John, who is considerably more guru-rific than I am. He's been monitoring and tweaking my system via openvpn the last few days. He suspects it may be related to the following bug:
[https://bugs.eclipse.org/bugs/show_bug.cgi?id=128617](https://bugs.eclipse.org/bugs/show_bug.cgi?id=128617)

I meant to paraphrase what he said, but it goes over my head a leeeetle bit, so here's the original (unaltered) conversation.

> (17:36:54) John: Hey I may have found some more info on this X problem of yours
(17:37:10) Niomi: ooh! what did you find out!
(17:39:09) John: What do you use that loads up hordes of little graphics? Like menu icons and such?
(17:39:48) Niomi: menu icons are my best guess.. maybe konqueror thumbnails?
(17:40:35) John: What about Gaim?
(17:40:51) Niomi: i have buddy icons turned off
(17:41:44) John: okay.  Lemme send you this link I found...
(17:43:53) John: [https://bugs.eclipse.org/bugs/show_bug.cgi?id=128617](https://bugs.eclipse.org/bugs/show_bug.cgi?id=128617)
(17:44:26) John: I know we're not using eclipse.. but they've traacked it down to the swt library... and the swt library is also used by *drumroll* GTK
(17:44:53) John: And the swt library I believe loads pixmaps into the X memory space
(17:45:03) Niomi: so THAT's why KDE worked better.. but sometimes didn't.. because i usually prefer GTK apps
(17:45:41) Niomi: you.. rule teh world !
(17:48:40) John: I may be off on what SWT is used for, it seems to be primarily used by Eclipse (software development package) but nevertheless I'm seeing tons of different people reporting X memory leaks, and it always seems to come back to software that loads up large amounts of very small graphics or icons, and especially software that is GTK based
(17:49:03) John: This is a fairly big issue, I have to believe it'll be fixed soon.
(17:53:30) John: Hrm. Here's another method of attack
(17:53:48) John: Yesterday I wiped my laptop and installed the latest Dapper on it.
(17:54:17) John: I've been running X all day, using firefox (version that came with Dapper) and other apps all day... my X is 28m in RAM, 60 in swap.
(17:55:37) John: Since it doesn't seem to be related to the X video driver (since our  VESA test the other day didn't seem to fix it) it stands to reason that some app you are running is causing the problem, and I'm not running it. 
(17:55:53) John: I could try running some of the same apps you do and see if I get the same problem.
(17:56:31) Niomi: sorry i poofed.. workrave.. i had to pee XD
(17:56:38) John: heh
(17:57:05) Niomi: what is eclipse?
(17:57:29) John: Java-based integrated developer environment
(17:57:52) John: Very nice one, too, I used it in Windows when I was messing around with the Celestia source
(17:58:33) Niomi: i'll post at the forums that the issue very well be related !
(17:59:09) John: Yeah, it sure sounds like the exact same problem.. just very different apps

---

### Post by Niomi on 2006-04-03
According to my Linux guru friend, xorg balloned up to consume nearly all of my RAM and swap space over the past few days...

---

### Post by cosmoshell on 2006-04-23
xorg is useing about  70 mb of ram on my computer what availible alternatives are there to xorg?

---

### Post by ekravche on 2006-04-26
Still no fix to this problem? Oh well, I guess it will never be fixed and we all will have to live with it.

---

### Post by cosmoshell on 2006-04-26
[QUOTE=psusi]Ignore it.  Most of that memory is the ram on the video card, not your main ram.[/QUOTE]
is that realy true what if its intergrated with the mother board.

---

### Post by Niomi on 2006-05-04
We seem to have narrowed this down to a conflict between **Xorg**, **Nvidia drivers** and the **gtk2-engines-gtk-qt** package. If you are expiriencing this problem, try an **sudo apt-get remove gtk2-engines-gtk-qt**. This will disable KDE's ability to make GTK applications appear to be native ones. This may also disable your custom gnome theme, if you set the colors in KDE.

---

