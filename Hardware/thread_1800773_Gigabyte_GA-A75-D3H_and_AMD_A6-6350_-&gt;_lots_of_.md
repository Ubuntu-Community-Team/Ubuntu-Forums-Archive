---
title: "Gigabyte GA-A75-D3H and AMD A6-6350 -&gt; lots of trouble"
date: 2011-07-09
forum: Hardware
---

### Post by Astralix on 2011-07-09
[SIZE=1]Hi!
new to the forum, but not new to linux, so I hope we could solve that together...

Installed is ubuntu amd64 latest image: [/SIZE] [SIZE=1]
2.6.38-8-generic #42-Ubuntu SMP Mon Apr 11 03:31:24 UTC 2011 x86_64 x86_64 x86_64 GNU/Linux   

Mainboard: Gigabyte GA-A75-D3H  [/SIZE] [SIZE=1]
CPU/GPU: AMD A6-6350    

I have actually two problems:   [/SIZE] [SIZE=1]
1) The small one is audio:  
lspci -v:
00:01.1 Audio device: ATI Technologies Inc Device 1714
    Subsystem: Giga-byte Technology Device 1714
    Flags: bus master, fast devsel, latency 0, IRQ 53
    Memory at fe01c000 (32-bit, non-prefetchable) [size=16K]
    Capabilities: <access denied>
    Kernel driver in use: HDA Intel
    Kernel modules: snd-hda-intel
00:14.2 Audio device: Advanced Micro Devices [AMD] Hudson Azalia Controller (rev 01)
    Subsystem: Giga-byte Technology Device a102
    Flags: bus master, slow devsel, latency 32, IRQ 16
    Memory at fe020000 (64-bit, non-prefetchable) [size=16K]
    Capabilities: <access denied>
    Kernel driver in use: HDA Intel
    Kernel modules: snd-hda-intel

Audio-Device is set to standard stereo, I'd like to have stereo audio only at this time. Audio on this combination is only working with crackling sound. No options in mixer do help. Streams are played with packets messed up, so you sometimes hear pieces of sound with wrong follow up. And lots od plopping and crackling.  [/SIZE] [SIZE=1]

2) Big Problem VIDEO [SIZE=2]
[SIZE=1]lspci -v:
00:01.0 VGA compatible controller: ATI Technologies Inc Device 964a (prog-if 00 [VGA controller])
    Subsystem: Giga-byte Technology Device d000
    Flags: bus master, fast devsel, latency 0, IRQ 18
    Memory at d0000000 (32-bit, prefetchable) [size=256M]
    I/O ports at f800 [/SIZE][/SIZE][SIZE=1]
    Memory at fdfc0000 (32-bit, non-prefetchable) [size=256K]
    Expansion ROM at <unassigned> [disabled]
    Capabilities: <access denied>
    Kernel driver in use: fglrx_pci

No chance to get it working. 
I booted up with no extra driver instralled and I have video. But unity is not running as my 'vga card doesn't support it', it says. 
I installed the fglrx driver via the foreign-hardware icon, that poped up right after installation.  After reboot I end at the text console. All trials of aticonfig --... do only report that I do not have any supported hardware.  
I read the net and I think I ran into the kernel compatibility issue with that driver. 
I removed the driver according the pretty fine manuals in this forum an am now back to the standard driver that doesn't support anything but at least shows some graphic desktop.  

I do have a 32bit installation of kubuntu too, but here it is almost the same. No working AMD/ATI graphics.  What do I need: I do a lot of picture/photo/video work and need proper flash working in chrome/mozilla. What I don't need is any 3D gaming.  

Can you push me to the right threads or give me some solutions?  

Best regards and thanks in advance 

Ulrich[/SIZE]

---

### Post by Astralix on 2011-07-13
Ok, no response, so I reply to myself :)

The video issue is partly solved. With the plain install of nattys amd64 version video works mostly perfect. 
While trying to install this to a newly bought Lenovo S205 I read a lot about all the installation issues and so I got all the ideas for the Gigabyte board too.

The trick is to just do nothing!

Some small issues:
1) Monitor is not recognized but aspect ratio can be trimmed manually.
2) Unity doesn't like to start as it does not recognize any 3D accelerated card. Ok, Llano is to new for the kernel fglrx. But while I like unity on the Netbook I prefer gnome for my workstation.

Video works absolutely fine and I tested dozens of formats.
The 64bit preview of Adobes flash player works fine too.

I will try to compile some of the mainline kernels and patch some things in that I learned from other kernel/graphics related threads and report back.
I wonder that there is so low response for the AMD A6/A8 hardware. Nobody buying that thing?

--------------
Only problem left is the audio stutter. 

I don't had time to search for a solution on that one. But I will do that now and report back here.

Best regards
Astralix

---

### Post by Astralix on 2011-07-15
Ok, still the only one that bought that board and installed Ubuntu 64bit on it :)

Tody I saw that Gigabyte provieded a BIOS update for the board, version F2. With that the sound problems are almost solved. I just have some single droputs (shot plops) every now and then. But It is far better than before. I'll continue to follow the reports on alsa's buglist around the Hudson chipset.

---

### Post by AMP444 on 2011-07-17
> **Astralix said:**
> Ok, still the only one that bought that board and installed Ubuntu 64bit on it :)

Tody I saw that Gigabyte provieded a BIOS update for the board, version F2. With that the sound problems are almost solved. I just have some single droputs (shot plops) every now and then. But It is far better than before. I'll continue to follow the reports on alsa's buglist around the Hudson chipset.

To be honest I tried 3x to install 
Ubuntu 11.04 64bit,
Mobo:A75M-D2H BIOS F2 updated from F1
CPU A8-3850Quad+HD6550D 256MB set in BIOS 
MEM: 4GB 1333
Last installation was fine, sound is a bit choppy but no solution yet.
Ati driver downloaded from 

[http://support.amd.com/us/gpudownload/linux/Pages/radeon_linux.aspx?type=2.4.1&product=2.4.1.3.42&lang=English](http://support.amd.com/us/gpudownload/linux/Pages/radeon_linux.aspx?type=2.4.1&product=2.4.1.3.42&lang=English)

restart everything is working fine except sound sometimes lagging while browsing web. Issue is only in Unity, on standard desktop no lags clean sound.

---

### Post by Astralix on 2011-07-22
Hi!

Let's start the odyssee:

I had kernel 2.6.38-10 running in standard VGA configuration. Blurry picture as X cannot read the display data. Manual setup made it a bit better, but I lost the manual fromo the display so no idea of the resolution.
As the first problems of AMD/ATI drivers and Natty were reported back a while I gave it a try with this kernel.
No chance. At least, after rebooting and ending in a tree of error messages from X, I coud Ctrl-ALT-F2 to a text console and uninstall fglrx again.

As there were rumors of some fixes in new beta kernels, I downloaded 2.6.39.rc4 and installed it. After reboot graphics are ok, but still monitors are not recognized. Unfortunately I only have a large VGA panel and a small DVI panel. So I gave it a try with the small DVI but even there the monitor seems not to be recognized correctly. Picture is small but brilliant. But monitor panel has no idea of supported resolutions.

OK.... Let's try the fglrx drivers on Kernel 2.6.39.rc4...

I used Additional Drivers menue to install the listed proprietary ATI driver. 
Reboot: Blackscreen... No way out... Think that somewhere behind the blackscreen is the kernel-ups...

Rebooted to rescue console and uninstalled fglrx drivers again.
Rebooted again (good old windows feeling :) )
And landet back in the blurry VGA mode.

While cleaning up some things with apt-get, I got the message that there is an official kernel 2.6.38-11 available. Fine, while loading/installing that one, I popped in here and read your message AMP444.

So there are differences between the version upuntu proposes in his manager tool and the one from ATI server...
Ok, I run the package for installation and rebootet.

Now, I am back on my blurry screen, no 3D no unitiy (I don't need it, I stay with gnome, I think) no monitor recognized...

Ok, I am now following this manual:
[http://wiki.ubuntuusers.de/Grafikkarten/ATI/fglrx/Manuelle_Treiberinstallation](http://wiki.ubuntuusers.de/Grafikkarten/ATI/fglrx/Manuelle_Treiberinstallation)
(sorry it's german)
After package installation fglrxinfo at least crashes with memfault. But aticonfig shows millions of parameters...

Let's see what the reboot brings :)

....

Wow!

Monitors are recognized, actually testing kernel 2.6.39-rc4.
Trying to configure big VGA panel to the left and small DVI panel to the right. Some messages popping up that there is a bugreport to be sent to ubuntu... But Catalyst Control Center is still responsive. 
Telling me to restart for taking over the configuration... Ctrl-Alt-Back doesn't work...
Oh, I have Unity running... Ok, never mind... Reboot...

Now I have two desktops, DVI panel working excellent, but VGA panel seems to have right resolution now but lots of flashing vertical lines.
CCC shows both monitors as deactivated.... So I reactivate them. Oh no, I have to reboot...

I give up for now. I just keep the VGA panel plugged in and reboot.

Wow again!

Now the VGA panel shows brilliant color and sharp letters! I think I can live with that for now, even I'd like to have the second display running. Most I do is programming and two monitors are making that job very much easier. 

Ok, video works with no sound issues...
I now thow some playlists at Clementine and we see what goes there while doing some embedded kernel compilation on 3 of the 4 cores the A6 has.

I contine the report if I take another trial to get the second monitor working.

Ulrich

---

### Post by Peterpwho on 2011-08-18
Hi Ulrich,

I am new to the forum as well.

I have the same problem as you with the audio on a similar mother board  GA-A75-UD4H. Again, I downloaded the latest 11.04 Desktop.

Unfortunately, my German is NIL. I am not able to follow the page that seems to have solved your problems.

At present, I got nothing with "dpkg -l |grep fglrx". Also, this is what I got when I keyed in the following...

$ dpkg-divert --list |grep fglrx
$ ls -l /usr/lib/libGL.so*
ls: cannot access /usr/lib/libGL.so*: No such file or directory
$ ls -l /usr/lib32/libGL.so*
lrwxrwxrwx 1 root root 15 2011-08-13 15:15 /usr/lib32/libGL.so -> mesa/libGL.so.1
$ ls /etc/ati
ls: cannot access /etc/ati: No such file or directory
$ ls /etc/X11/xorg.conf
ls: cannot access /etc/X11/xorg.conf: No such file or directory

Could you please post how you fixed the audio/video problems in English?  I am sure there will a lot people who has invested in the latest GA  A75-* Mother board would be very much interested in your solutions.

Thanks
Peter.

---

### Post by chicom9 on 2011-08-27
Hi I have the same exact problem  here is some info:
        Manufacturer: Gigabyte Technology Co., Ltd.
        Product Name: GA-A75-UD4H
        Version:  
        Serial Number:
I'm running Ubuntu 10.10 Mav. Linux 2.6.35-30-generic #54-Ubuntu SMP
My main problem is the audio is crackling I have tried playing w the mixer but no luck. any suggestions out there.. 
thanks

---

### Post by Peterpwho on 2011-11-08
All,

Finally I got it all working now for my GA-A75-UD4H card. The steps are as follows:

1) First back up all your data. In my case, all data under home to an USB stick.
2) Download Ubuntu 11.04 desktop to a CD or DVD (11.10 did NOT work and hung on me).
3) Boot off the CD/DVD. I selected testing first to browse around and checked it was working before installing it.
4) Install 11.04.
5) After installation is complete and a reboot, you can now login. 
6) At the bottom bar of the login screen, you can choose the Ubuntu (Unity) or Ubuntu Classic desktop. My choice was classic. I am new to Unity. 
7 )  After login, from the top menu bar go to System->Admininstration-> Additional Drivers
8 ) The ATI/AMD proprietary FGLRX graphics driver should come up. Click Activate to install the drivers.
9 ) After a system restart, the sound was still not OK in my case. I needed to update Ubuntu.
10) Go to  System->Admininstration->Update Manager and just click update 

 WARNING : NOT DO UPGRADE to 11.10. ONLY DO AN UPDATE of 11.04.

I made the same mistake TWICE and I was not able to even Ctrl+Alt+F1 back to command mode.

11) After another system restart, all the sound and 3D graphic works fine. Unity also working.
12) I had an old monitor which was not recognised by the system. It defaulted to 800x600 Therefore, I also needed to go to System->Preference->Monitors. Select the appropriate resolution and set it as default.
13) After reboot, it works fine, except for the "AMD Unsupported  Hardware" Watermark in the lower right corner of the screen. To get rid  of this, you can download the latest version of the ati driver from ADM  (for me I downloaded it from  [http://www2.ati.com/drivers/linux/ati-driver-installer-11-9-x86.x86_64.run](http://www2.ati.com/drivers/linux/ati-driver-installer-11-9-x86.x86_64.run)).  Extract the control file using --extract and replace the /etc/ati/control  with it. You need a reboot for it to take effect.

$ sh ati-driver-installer-11-9-x86.x86_64.run --extract
$ cd fglrx-install.84E8ac/common/etc
$ sudo mv /etc/ati/control /etc/ati/control.orig
$ sudo cp control /etc/ati/control

I hope this will help for those who have the same GA-A75-UD4H mother board as me and had been searching around for a solution.

Peter.

---

### Post by gnusci on 2012-01-17
Thanks a lot Peter... The instructions worked like a charm on my GA-A75M-S2V.

---

### Post by Peterpwho on 2012-04-14
Hi gnusci,

You are most welcome.

Has anyone able to get Ubuntu 11.10 working on a GA-A75-UD4H board yet? If you have, could you please post your solution here or point me to the right directions/links/pages?


I am still trying to get 11.10 working my mother board (GA-A75-UD4H). I have burn the latest version of 11.10 to a DVD-RW disc. I got only a blank screen 10 seconds after booting from the DVD.


Regards,
Peter

---

### Post by tanveerahmed2k8 on 2012-05-06
hi did you get the sound working i have the same motherboard but no sound in 12.04 via HDMI

---

