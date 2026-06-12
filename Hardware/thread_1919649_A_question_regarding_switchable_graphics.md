---
title: "A question regarding switchable graphics"
date: 2012-02-03
forum: Hardware
---

### Post by Aldo93 on 2012-02-03
I recently purchased a HP Pavilion DV6 6b50sa with switchable graphics containing Intel and ATI processors. 

Obviously I've been having the same problem as everyone else with switchable graphics, the proprietary drivers simply render my Ubuntu install unbootable. The open source drivers do their job quite nicely, however VGAswitcheroo is informing me that both my graphics cards are turned on, again, same problem as everyone else.

I do realise there are workarounds to this issue, however I'm not concerned about my battery life as my laptop is always plugged into the mains, what I'm more concerned about is which graphics card my system is actually using to process graphics? 

In my BIOS I have set the switchable graphics option to dynamic, which in theory should let the application decide which GPU to use, but is this the case in Ubuntu? Obviously I do not want to be streaming 720p video which is being processed only by my Intel card.

I've come to the conclusion that 1 of 2 things could be happening. Either the settings in the BIOS are actually doing their job, and specific applications can choose which GPU they use, or one card (most likely my Intel card) is in use 100% of the time and my ATI card is powered on but not being used. 

I do not mind the fact both cards are turned on as I'm not concerned about power, I'm more concerned about performance and the fact I'd like to take advantage of the better performance that the ATI card naturally offers, which I and many others cannot achieve with proprietary drivers.

Thanks for any insight you may be able to offer regarding this situation.

---

### Post by sunfromhere on 2012-02-04
Hi, it looks like you're in the similar situation like us g-series, however, you have one advantage.

From what I gather, your Intel card is always running if you select Dynamic mode (apparently the dynamic mode wasn't working even in Windows on some models). However, if not already present in your version of BIOS, [read this post on hp forums]("http://h30434.www3.hp.com/t5/Notebook-Display-and-Video/Official-HP-statement-on-Switchable-Graphics-and-Open-GL/td-p/766285").
It appears you can upgrade your BIOS to have fixed mode and to select which GPU you want.

---

### Post by Mark Phelps on 2012-02-06
> **Aldo93 said:**
> In my BIOS I have set the switchable graphics option to dynamic, which in theory should let the application decide which GPU to use, but is this the case in Ubuntu? Obviously I do not want to be streaming 720p video which is being processed only by my Intel card.
As far as I know -- NO.  Linux currently does not provide support for switchable (or as some call it -- hybrid) graphics.

> I've come to the conclusion that 1 of 2 things could be happening. Either the settings in the BIOS are actually doing their job, and specific applications can choose which GPU they use, or one card (most likely my Intel card) is in use 100% of the time and my ATI card is powered on but not being used. 
The second is the case -- one of the chipsets is in use all the time.

> I do not mind the fact both cards are turned on as I'm not concerned about power, I'm more concerned about performance and the fact I'd like to take advantage of the better performance that the ATI card naturally offers, which I and many others cannot achieve with proprietary drivers.

Evidently, hybrid graphics is a real tough nut to crack.  Read the link below for more info:

[https://help.ubuntu.com/community/HybridGraphics]("https://help.ubuntu.com/community/HybridGraphics")

---

### Post by markackerman8@gmail.com on 2012-02-17
Please help,
&#8728; For 2 months and over 100 hours, I have been trying to get my new HP Envy 2195ca Laptop working with Ubuntu using the Switchable discrete AMD/ATI HD 6850m graphics card and not the embedded Intel hd3000 low end card,  with no success.  I think perhaps I am missing something basic and don't know what it is???   Here is what I have tried (part thereof) :
&#8227; Installed using additional drivers - seemingly successfully - ie. says enabled, and active and green dot, but
• running ATI's CCC gives:
&#8728; There was a problem initializing Catalyst Control Center Linux edition.  It could be caused by the following.
&#8728; No AMD graphics driver is installed, or the AMD driver is not functioning properly.
&#8728; Please install the AMD driver appropriate for you AMD hardware, or configure using aticonfig.
&#8227; Installed from the amd website:    amd-driver-installer-12-1-x86.x86_64.run, (previous version over the past 2 months as well)
• sudo apt-get install ia32-libs
• created the 3 debian packages seemingly successfully and installed all three:
&#8728; fglrx_8.930-0ubuntu1_amd64.deb,    plus 2 similarly named ones
• For the first time using 12.1 today I seemingly successfully ran:
&#8728; aticonfig --initial -f, with no errors  BUTTTTTT
&#8227; after a reboot just a black screen with a few tiny white dots flicking around
• and safe mode works fine
• I can get back into Ubuntu Normal mode by deleting 
&#8728; /etc/X11/xorg.conf (perhaps I just need the right file contents for switchable graphics)
&#8227; Again PLEASE HELP. and Thanks in advance
&#8227; Here is some additional information 
• lspci -nn | grep VGA
&#8728; 00:02.0 VGA compatible controller [0300]: Intel Corporation 2nd Generation Core Processor Family Integrated Graphics Controller [8086:0116] (rev 09)
&#8728; 01:00.0 VGA compatible controller [0300]: ATI Technologies Inc Broadway [ATI Mobility Radeon HD 6800 Series] [1002:68a8]
• Recommended configuration for X.org
&#8728; No configuration is necessary for ATI driver in the modern versions of Ubuntu. You can safely take away your xorg.conf and your computer will run fine. 
•     To see if your driver uses KMS (Kernel Mode Setting), run command 
&#8728; ack@Arawn:~$ dmesg | grep drm
[    9.153946] [drm] Initialized drm 1.1.0 20060810
[    9.400960] [drm] MTRR allocation failed.  Graphics performance may suffer.
[    9.402250] [drm] Supports vblank timestamp caching Rev 1 (10.10.2010).
[    9.402255] [drm] Driver supports precise vblank timestamp query.
[   13.040646] fbcon: inteldrmfb (fb0) is primary device
[   13.040932] fb0: inteldrmfb frame buffer device
[   13.040935] drm: registered panic notifier
[   13.049332] [drm] Initialized i915 1.6.0 20080730 for 0000:00:02.0 on minor 0


• vgaswitcheroo 
&#8728; Never has worked and probably because there is NEVER a file called
&#8227; /sys/kernel/debug/vgaswitcheroo/switch
&#8227; root@Arawn:/home/ack# echo DIGD > /sys/kernel/debug/vgaswitcheroo/switch
• bash: /sys/kernel/debug/vgaswitcheroo/switch: No such file or directory
&#8728; root@Arawn:/home/ack# grep -i switcheroo /boot/config-3.0.*
&#8227; /boot/config-3.0.0-16-generic:CONFIG_VGA_SWITCHEROO=y
&#8728; To test if vga_switcheroo is enabled, look for the switch file: 
&#8227; ls -l /sys/kernel/debug/vgaswitcheroo/switch
• ls: cannot access /sys/kernel/debug/vgaswitcheroo/switch: No such file or directory
&#8728; never once had this switch file with or without open source/fglrx/ or no driver at all
&#8227; If you are not using the open-source radeon driver (or the nouveau driver in case of nvidia hardware), there won't be a /sys/kernel/debug/vgaswitcheroo/switch file. (ignoring hacks like asus-switcheroo and byo-switcheroo). Disabling KMS ("modeset=0") turns off this functionality too.
• hmmmmmm
&#8227; Soooo
• The last thing in my many attempts was to reinstall ubuntu to install the amd/ati driver thru additionhal drivers (post release) as I read that this was the only one to work with vgaswitcheroo.  Oddly after the reinstall of Ubuntu and no updates I saw the switch file (/sys/kernel/debug/vgaswitcheroo/switch) for my first time  (Ubuntu 3.0.0-12) (no additional driver yet).  Then I tried to install the ati driver no luck  - errors so I thought I should update Ubuntu - restart and try again.  After the restart my kernel was at 3.0.0-16 from 12, and no /sys/kernel/debug/vgaswitcheroo folder at all

---

### Post by Mark Phelps on 2012-02-20
Don't know what you've tried -- but read through the link below:

[http://linuxenvy.blogspot.com/2011/01/tackling-switchable-graphics.html]("http://linuxenvy.blogspot.com/2011/01/tackling-switchable-graphics.html")

---

