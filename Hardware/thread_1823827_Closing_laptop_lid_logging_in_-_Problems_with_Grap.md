---
title: "Closing laptop lid/ logging in - Problems with Graphic Card"
date: 2011-08-12
forum: Hardware
---

### Post by WongTschon on 2011-08-12
Hello,
first of all I am pretty much new to Ubuntu/Linux as well as to this forum.
I appreciate every precious help and advice you can give me :).

Recently I followed some instructions how to install and play games on Linux that only work on Windows, which included installing wine, PlayonLinux etc. 

Somehow it didn't work out as I thought it would be, hence everytime I start a new session/login I see some flashing colourful lights (Only logging in after rebooting) . Adding to this closing my lid and opening it again results in a black screen and I have to reboot my system.

I am sure it has something to do with me following these instructions, though I always tried to understand what I was doing. Unfortunately I have the feeling I wasn't paying enough attention to some of these instructions and I managed to mess up with my Graphic Card Drivers or something related to it.

Can you people help me? There's no thread like this one as far as I noticed, so it should be new and thrilling (haha :) ) for you to solve this problem. Thanks!

Here's my lspci output, maybe it can help:

```

00:00.0 Host bridge: Advanced Micro Devices [AMD] RS780 Host Bridge Alternate
00:01.0 PCI bridge: Hewlett-Packard Company Device 9602
00:04.0 PCI bridge: Advanced Micro Devices [AMD] RS780 PCI to PCI bridge (PCIE port 0)
00:07.0 PCI bridge: Advanced Micro Devices [AMD] RS780 PCI to PCI bridge (PCIE port 3)
00:09.0 PCI bridge: Advanced Micro Devices [AMD] RS780 PCI to PCI bridge (PCIE port 4)
00:11.0 SATA controller: ATI Technologies Inc SB700/SB800 SATA Controller [AHCI mode]
00:12.0 USB Controller: ATI Technologies Inc SB700/SB800 USB OHCI0 Controller
00:12.2 USB Controller: ATI Technologies Inc SB700/SB800 USB EHCI Controller
00:13.0 USB Controller: ATI Technologies Inc SB700/SB800 USB OHCI0 Controller
00:13.2 USB Controller: ATI Technologies Inc SB700/SB800 USB EHCI Controller
00:14.0 SMBus: ATI Technologies Inc SBx00 SMBus Controller (rev 42)
00:14.2 Audio device: ATI Technologies Inc SBx00 Azalia (Intel HDA) (rev 40)
00:14.3 ISA bridge: ATI Technologies Inc SB700/SB800 LPC host controller (rev 40)
00:14.4 PCI bridge: ATI Technologies Inc SBx00 PCI to PCI Bridge (rev 40)
00:14.5 USB Controller: ATI Technologies Inc SB700/SB800 USB OHCI2 Controller
00:16.0 USB Controller: ATI Technologies Inc SB700/SB800 USB OHCI0 Controller
00:16.2 USB Controller: ATI Technologies Inc SB700/SB800 USB EHCI Controller
00:18.0 Host bridge: Advanced Micro Devices [AMD] K10 [Opteron, Athlon64, Sempron] HyperTransport Configuration
00:18.1 Host bridge: Advanced Micro Devices [AMD] K10 [Opteron, Athlon64, Sempron] Address Map
00:18.2 Host bridge: Advanced Micro Devices [AMD] K10 [Opteron, Athlon64, Sempron] DRAM Controller
00:18.3 Host bridge: Advanced Micro Devices [AMD] K10 [Opteron, Athlon64, Sempron] Miscellaneous Control
00:18.4 Host bridge: Advanced Micro Devices [AMD] K10 [Opteron, Athlon64, Sempron] Link Control
01:05.0 VGA compatible controller: ATI Technologies Inc M880G [Mobility Radeon HD 4200]
01:05.1 Audio device: ATI Technologies Inc RS880 Audio Device [Radeon HD 4200]
02:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL8101E/RTL8102E PCI Express Fast Ethernet controller (rev 02)
06:00.0 Network controller: Broadcom Corporation Device 4727 (rev 01)

```EDIT.a:
My current Hardware Drivers are:
Broadcom STA wireless driver
ATI/AMD proprietary FGLRX graphics driver
Both are "activated and currently in use" - normal?

EDIT.b:

When I run PlayOnLinux it says Install/Enable 3d acceleration.
Do I have to?

glxinfo is not showing usual stuff, according to some other instructions:
```

name of display: :0.0
Segmentation fault

```Thats all.

EDIT.c:

As I tried to find a solution to my problem, it appears I made more mistakes.
Now theres an error-message telling me following:

```

Could not update ICEauthority file
/home/myname/.ICEauthority

```Maybe I can delete my whole system by trying harder? Let's go!

EDIT.d:

WOW! I managed to solve that ICEauthoriy error. I dont know why it appeared and why my account had no rights for this file, .ICEauthority, and what it even does, but now I am still stucked at my previous problem. Still flashing colorful boxes and weird things happening when I reboot without any clue what it could be. My driver might be the wrong one, maybe I can find out how if and how I correct this issue. 

Maybe it was wrong to give rights to this file? Well we will see, this is what I did
```

chown user:user /home/user/.ICEauthority
chmod 644 /home/user/.ICEauthority
exit

user = myusername

Source: http://ubuntuforums.org/showthread.php?t=1021106

```however chown user:user /home/user/.ICEauthority was not successful, I needed sudo rights.

Let's continue my journey to find a solution to my first problem, weeee!

EDIT.e:

Read...so...much...
So...much...to..read... :( 

The fight continues, Mighty wizard google, give me an idea!

EDIT.f:

Maybe changing my Power Management Preferences will end in a good solution? I don't think so, but let's try it out, I can't lose much!
Brb trying it again. 
Oh is there a #ubuntuforums channel for live action? I'll try it out , too! Let's google it.
If you don't see an update for ~10 minutes it means my laptop lid ate me. (I hope it doesn't.. or.. maybe?)

EDIT.g:

Ok Blank Screen Power Management Preferences when closing lid [CHECK]
Works. But who wants his laptop to be awake while you are doing some stuff? It's not cruel or something. Like when its halloween, your door bell rings and there are kids, you tell them you'll get some candies for them and never come back? or come back like 30 minutes later and these kids still stay there drooling and begging for candies? Nobody wants to be that cruel! I need another solution. Let's continue reading.

```

Source: http://askubuntu.com/questions/15520/how-can-i-tell-ubuntu-to-do-nothing-when-i-close-my-laptop-lid

```EDIT.h:

Oh look what do we have here!
I've seen some people blabbering about fglrx, maybe i'll wikipedia that. It seems some people had issues with it, but I think I might not related to this one? 
However i'll try something someone wrote there:
```

http://forum.notebookreview.com/linux-compatibility-software/542390-my-ubuntu-laptop-won-t-wake-up-after-i-close-lid-how-do-i-fix.html

```I hope it works! Let's  CTRL+ALT+F1 it! (Oh and yeah I press buttons on my keyboard and move my mouse after re-opening my lid, I am not fully brain liquid)

Also I might be switching to numbers after hitting EDIT.z! 
Poor laptop, you will be having your rest, soon! DON'T GIVE UP SON, DON'T GIVE UP!

EDIT.i:

Sweet mother of god, it appears that CTRL+ALT+F1 reboots your system. That was a good one, I laughed. I feel not very intelligent now. But well it brought back my screen. 
Also my ubuntu-loads start-up purple screen thingy changed back then from small to OhyouturnedoldIllswitchtofont999, so I can read it very well. Thanks my dear ubuntu system, I love you too, maybe i should give you some sweet sudo apt-get updates ? Well no that didn't work either.
I feel alone... can someone at least laugh at me? Maybe laugh harder when I go the wronger way of the wrong ones? And only cheer if I go the right way? Oh god I think I'll be writing to myself in about 10 edits. 
LET'S CONTINUE ! ALRIGHTY!

EDIT.j:

An ant just tried to crawl into my butt. True story.

EDIT.k:

Asking several #ubuntu channels to help me. It's a desperate try to get ANY idea. Maybe I just don't see it :(.

EDIT.l:

Found something that might help.
For anyone who wants more info what I may've done wrong, following should help:


output of
dpkg -l | grep "fglrx\|nvidia"
```

ii  fglrx                                          2:8.723.1-0ubuntu5                              Video driver for the ATI graphics accelerato
ii  fglrx-amdcccle                                 2:8.723.1-0ubuntu5                              Catalyst Control Center for the ATI graphics
ii  fglrx-modaliases                               2:8.723.1-0ubuntu5                              Identifiers supported by the ATI graphics dr
ii  nvidia-173-modaliases                          173.14.22-0ubuntu11                             Modaliases for the NVIDIA binary X.Org drive
ii  nvidia-96-modaliases                           96.43.17-0ubuntu1                               Modaliases for the NVIDIA binary X.Org drive
ii  nvidia-common                                  0.2.23                                          Find obsolete NVIDIA drivers
ii  nvidia-current-modaliases                      195.36.24-0ubuntu1~10.04                        Modaliases for the NVIDIA binary X.Org drive

```There is no xorg.conf file in my /etc/X11 folder. I think that's not right. But well I don't know what I am even doing D:.

EDIT.m:

Though It's not right, i'll bump!

EDIT.n:

Name of laptop: HP 625

---

### Post by WongTschon on 2011-08-12
bump

---

### Post by WongTschon on 2011-08-12
With the help of some friendly guy in #ubuntu a solution was found:

As long as you have Ubuntu <=10.04 make sure youve deactivated following driver:

[IMG]http://img694.imageshack.us/img694/936/screenshot43l.png[/IMG]

---

