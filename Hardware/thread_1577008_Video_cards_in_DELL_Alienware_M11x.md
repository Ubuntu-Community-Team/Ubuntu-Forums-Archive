---
title: "Video cards in DELL Alienware M11x"
date: 2010-09-18
forum: Hardware
---

### Post by cyatomato on 2010-09-18
Hi, everyone
I have some problems in my laptop (Dell Alienware M11x, Ubuntu 10.04). For this machine, there are 2 video cards, one intel, another is Nvidia 335M. So there are two graphic mode in BIOS setting, swithable(which use intel card) and disecrete(nvidia card). I installed the newest nvidia driver.  And then I find I can only use the nvidia card. When I change  the BIOS setting into switchable mode(intel card) and restart system. I can only see the black screen. 
below is my xorg.conf file.
> 

Section "Screen"
    Identifier    "Default Screen"
    DefaultDepth    24
EndSection

Section "Module"
    Load    "glx"
EndSection

Section "Device"
    Identifier    "Default Device"
    Driver    "nvidia"
    Option    "NoLogo"    "True"
EndSection

Section "Device"
    Identifier    "Altanative Device"
    BusID    "PCI:0:1.0"
    Driver    "nvidia"
    Option    "NoLogo"    "True"
EndSection

It work in disecrete mode.
Thanks for your help!!!!

---

### Post by nourathar on 2010-09-19
Hi,
are you aware of this thread: [http://ubuntuforums.org/showthread.php?t=1396552](http://ubuntuforums.org/showthread.php?t=1396552) ?

---

### Post by cyatomato on 2010-09-21
As indictaed in the thread about M11x
> **soleblaze said:**
> Ok, I have Ubuntu running on it.  It looks like  switchable = Intel and discrete = NVIDIA.  If you try to install the  nvidia closed source driver and it's set to switchable it will cause a  kernel panic.  If you install the driver when it's on discrete it will  work fine, but then it will fail to start once you switch it back to  switchable.  (The graphics fail to work correctly on the splash screen  and it didn't seem to get any farther.  However, it didn't kernel panic  on me..when I pressed the alien head it shut down.)  

The wireless card is a Dell 1520, which uses the broadcom BCM4353  chipset.  It works fine with the closed source STA driver, but I'm  currently unsure if there's any open source alternatives to this card.

Sound does not work as jebinem1999 mentioned.  

The fan also feels like it spins up a lot more than it does in Windows  7.  Currently it looks like the fan is either off or on, without being  throttled in any way.  It can become annoying depending on what you're  doing.  I'm hoping this will be fixed in the next bios update.  (The  laptop also doesn't overclock correctly, which is supposed to be fixed  in the next BIOS revision)

That's about all the testing that I've done on it so far.  I'm guessing  the nvidia screws up because it adds the nvidia line to the xorg.conf  file.  I'm wondering if X will still pick up on that driver even if it's  not in the conf file.  I'll have to test that out when I have more  time.

I think we have the same problem.
it will fail to start once you switch it back to  switchable. The graphics fail to work correctly on the splash screen  and it didn't seem to get any farther.
So we still need to find the solutions

---

### Post by ronz0o on 2011-05-21
I also have an Alienware m11x R1, and wanted to get switchable vs. discrete working. This is the script that came out with for Ubuntu 11.04.



# ./vidswitch.py 
[ Alienware m11x Video Changer ]
[      Written by Marfi        ]

Usage:
./vidswitch.py [-s, -d]

-s - Switchable (Using Intel Graphics)
-d - Discrete (Using Nvidia Graphics)

In order for switchable graphics to work, you must not have an existing xorg.conf file. The -s flag will remove this file. (NOTE! This does NOT back it up before removing it!) Once you reboot, change the BIOS to switchable, and it should pick up that you're using the Intel card.

The -d flag is for discrete graphics, or making use of the Nvidia graphics. When you run ./vidswitch.py -d, it will remove the current xorg.conf, create an empty xorg.conf, then write a new xorg.conf (similar to cyatomato's). Once complete, you'll reboot and change to discrete graphics. 

Few things to note...
 - Make sure you're running as root. (sudo -s, sudo su, etc)
 - Make sure you back up any customizations you have made to your xorg.conf file. (saved in /etc/X11/xorg.conf)
 - No warranties with the script, as it only plays with the xorg file. =)

If I get bored enough, I may write it into a script that can start at runtime, detect which mode is running, and go from there.

Let me know if there are any other questions.

Regards,

Marfi

---

