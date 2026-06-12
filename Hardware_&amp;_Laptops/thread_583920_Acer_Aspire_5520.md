---
title: "Acer Aspire 5520"
date: 2007-10-20
forum: Hardware &amp; Laptops
---

### Post by alquemir on 2007-10-20
Hi!

I recently installed ubuntu 7.10 on a Acer Aspire 5520. So far i managed to install the video card drivers, but i still don't have sound! Can anyone please, provide a solution to enable sound on this laptop?

Thanks :)

---

### Post by akhil on 2007-10-25
Hi,

I am facing the same problem on acer aspire 5520. I somehow managed to install nvidia driver and could change the resolution to 1024x768. But still the screen looks stretched. I think the resolution expected for my screen is 1280x768 or 1280x800 as my screen size is 15'4". And i dont get to hear any sound either???

Is there any way to increase the screen resolution to appropriately fit my widescreen and configure the sound. I have installed ubuntu 7.10????

i just so wanna get my machine up and working .... :)

Thanks,
Akhil

---

### Post by grenier on 2007-10-29
Same problem here with an Aspire 5520.
- The graphic card (7000M) uses the right driver, but I can find no way of configuring the screen to the proper 1280x800. The doc that came with the laptop doesn't give the specs, so I'm a bit leery of editing xorg by hand
- No sound. lspci says I have the nVidia Corp. MCP67 High Definition Audo (rev1), but there isn't a whisper coming out.

I still haven't got to the point of trying to configure the wireless.

---

### Post by i_TheDevil_i on 2007-10-29
have the same laptop.. but in my case the problem is that i can't even start ubuntu live cd. xorg gives me an error "no screens found" or something.. well it's all because the nv driver doesn't have the GeForce 7000M in it.. then i tried startng it in Safe Graphics mode, but it is still impossible to install... it seems to be that it is impossible to resize the install window. i need it because it goes out of borders of screen, so i can't set up everything properly.... =(((

---

### Post by grenier on 2007-10-30
- For the geforce 7000M's driver: 
[LIST=1]
[*]Install (search in synaptic, I don't remember the exact name) nvidia-glx-new (I think that's the name).
[*]In a terminal type "sudo nvidia-glx-config enable" (I think, again)
[*]sudo gedit /etc/X11/xorg.conf - check whether the entry "Driver" is nv or nvidia. If it's the former, change it to nvidia.
[*]Reboot
[/LIST]

- For the sound card:
[LIST=1]
[*]Install the ...-modules-backport (where ... may be kernel. I'm not in front of my computer right now so I can't check the exact names. Looking for backport should give it to you. Be careful not to select the one with version number so it'll be upgraded when necessary)
[*]Reboot
[/LIST]


I haven't gotten further so far. But I did check that both suspend to ram and the integrated sd card reader worked out of the box.

---

### Post by Wathoom on 2007-10-31
I have aspire 5520G with Gefroce 8600m gs.
As for video just go Applications>Add/remove>NVidia-glx-new and in System>Administration>Restricted drivers anable the drivers.

As for sound still dont have any solution. Just cant get it to work. Folowed few guides but none works.
Grenier if you could be more specific about your solution i would be thankfull.

---

### Post by Wathoom on 2007-10-31
Forgot to say that in alsamixer i see card and chip it uses. I allso can change volume controls but dont have option to mute or unmute device.
I allso get this in dmesg:

[    7.244000] NFORCE-MCP67: IDE controller at PCI slot 0000:00:06.0
[    7.244000] NFORCE-MCP67: chipset revision 161
[    7.244000] NFORCE-MCP67: not 100% native mode: will probe irqs later
[    7.244000] NFORCE-MCP67: BIOS didn't set cable bits correctly. Enabling workaround.
[    7.244000] NFORCE-MCP67: 0000:00:06.0 (rev a1) UDMA133 controller

Some conflict maybe?

---

### Post by i_TheDevil_i on 2007-10-31
**grenier**! you are genius! =)
about the sound problem. i'll give the exact package names to be installed:
open Synaptic Package Manager, then search packages by the name "backport"
you'll see the list in which just check the "linux-backports-modules".. in the description it's written, that "This package will always depend on the latest generic Linux backported
drivers available." so i think it will automatically upgrade the package when the linux kernel is upgraded.
after installing the package i got the sound working! once again thank you grenier!!!

now, the video problem... i simply installed the latest Nvidia drivers (downloaded from Nvidia site) NVIDIA-Linux-x86-100.14.19-pkg1.run
after install just run in terminal "nvidia-settings". u can choose the monitor resolution and refresh rate =))

> and there is one more problem i couldn't solve. it's wifi =) cant get it working. i installed the ndiswrapper, got the windows drivers and it keeps telling me, that the driver is invalid... =/// > [edit]: ok, i've setup my wifi (using [this]("https://help.ubuntu.com/community/WifiDocs/Driver/Ndiswrapper") HowTo). but, i can't make it to load at startup... [edit_2]: finally i've managed to set the ndiswrapper to load at startup =)))

P.S.: one more thing! the sound control wheel works nicely too.. and when u trun it, the nice [pic appears]("http://www.hot.ee/vitaly86/sound.png") =))))))
P.P.S.: [here]("http://www.atheros.cz/download.php?atheros=AR5006EG&system=1") is the driver needed for wifi adapter (for ndisgtk actually) =)
just install the ndisgtk as described [here]("https://help.ubuntu.com/community/WifiDocs/Driver/Ndiswrapper") and use the driver... it has graphical utility to install drivers, so it's not so hard (located in "System>Administration>Windows Wireless Drivers"... of course it will be there after ndisgtk is installed)

---

### Post by Muki on 2007-10-31
Alquemir,
I am having trouble installing Ubuntu 7.10 on my new 5520. The default video driver makes the screen too big and I am not able to resize the window to be able to click through.

At one point, I successfully installed the correct nvidia-glx-new driver, but it required a reboot from my install sequence, and I lost it when I rebooted.

Did you choose an alternative generic driver and resize the screen so that you could click through??? Which one, if so?

Grateful for any tips you could throw my way.

Thanks.

Muki -- a wannabe Gutsy Gibbon user..............


Update:: Even though the screens could not be resized, I used the keyboard, and tabbed -- kind of in the dark -- though, and 7.10 installed fine.

When I went to update to the proper NVIDIA driver through Synaptic Package Manager, and it failed. Sorry I am a newbie and tried three or four things that I googled, and am not sure just how I broke it. Will reinstall today and take proper notes.


[COLOR="Blue"]Update 01NOV07: Have solved part of the problem, and have installed 7.10 64 Desktop on my Acer Aspire 5520,
along with the new NVIDIA driver. See new post with details.[/COLOR]

---

### Post by Wathoom on 2007-11-01
well sound problem soloved. 

thanks guys.

---

### Post by grenier on 2007-11-01
Well, no luck for the resolution.
In nvidia-settings, I see the screen is properly detected, but no apparent way to use that (or did I miss something obvious?)
The most infuriating of all is that I *can* have everything work properly. Following something I got from the linuxquestions forum, I erased every reference to resolution in xorg.conf (appart from color depth) and let xorg figure it out by itself.

A reboot of the xserver later, everything was working properly and I finally had the appropriate entry (1280x800) available in the settings.

Unfortunately, after checking, I also found out that between that X server reboot and me logging back in, there's something that rewrites the #%$!ng wrong entries in xorg.conf. That means that for now, if I want the proper resolution, I have to edit by hand the damn xorg.conf each and every time the X server gets rebooted.

](*,)

---

### Post by i_TheDevil_i on 2007-11-01
> **Muki said:**
> 
Even though the screens could not be resized, I used the keyboard, and tabbed -- kind of in the dark -- though, and 7.10 installed fine.

When I went to update to the proper NVIDIA driver through Synaptic Package Manager, and it failed.

Did the same trick with tabbing. =) And after rebooting the resolution set up to 1024x768 itself.. =) Then i just installed official Nvidia driver and i could change the resolution to 1280x800 through the nvidia-settings =)

P.S.:it is strange, that Nvidia driver works. Because there are no drivers from Nvidia for GeForce 7000M (nForce 610M chipset) for any Windows on their site yet... And there's no the GeForce 7000M/nForce 610M entry in list of supported devices for the linux driver =)) It's very strange =))

---

### Post by i_TheDevil_i on 2007-11-01
> **grenier said:**
> Well, no luck for the resolution.
In nvidia-settings, I see the screen is properly detected, but no apparent way to use that (or did I miss something obvious?)
The most infuriating of all is that I *can* have everything work properly. Following something I got from the linuxquestions forum, I erased every reference to resolution in xorg.conf (appart from color depth) and let xorg figure it out by itself.

A reboot of the xserver later, everything was working properly and I finally had the appropriate entry (1280x800) available in the settings.

Unfortunately, after checking, I also found out that between that X server reboot and me logging back in, there's something that rewrites the #%$!ng wrong entries in xorg.conf. That means that for now, if I want the proper resolution, I have to edit by hand the damn xorg.conf each and every time the X server gets rebooted.

](*,)


Maybe this helps with resolution:
this is some part of my xorg.conf

```
Section "Screen"
    Identifier     "Default Screen"
    Device         "GeForce 7000M"
    Monitor        "Generic Monitor"
    DefaultDepth    24
    SubSection     "Display"
        Virtual     1280 800
        Depth       24
        Modes      "1280x800@60" "1024x768@60" "800x600@60" "800x600@56" "640x480@60"
    EndSubSection
EndSection
```

The "Virtual" was 1024 768 in original, i thought that if i change it to 1280 800, it would help... Maybe it did. =))

---

### Post by grenier on 2007-11-01
> **i_TheDevil_i said:**
> Maybe this helps with resolution:
this is some part of my xorg.conf

```
Section "Screen"
    Identifier     "Default Screen"
    Device         "GeForce 7000M"
    Monitor        "Generic Monitor"
    DefaultDepth    24
    SubSection     "Display"
        Virtual     1280 800
        Depth       24
        Modes      "1280x800@60" "1024x768@60" "800x600@60" "800x600@56" "640x480@60"
    EndSubSection
EndSection
```

The "Virtual" was 1024 768 in original, i thought that if i change it to 1280 800, it would help... Maybe it did. =))

Now this could be a great help. But I would need the modelines that are called up by the modes' names (specifically the line for "1280x80@60").

Could you post your "Monitor" section?

Thanks

---

### Post by i_TheDevil_i on 2007-11-02
it would be better if i post more than the "Monitor" section.
there is more than one section which have some options for monitor =)

```

Section "Monitor"
    Identifier     "Generic Monitor"
    VendorName     "Generic LCD Display"
    ModelName      "LCD Panel 1280x800"
    HorizSync       31.5 - 50.0
    VertRefresh     56.0 - 65.0
    Gamma           1
    ModeLine       "640x480@60" 25.2 640 656 752 800 480 490 492 525 -hsync -vsync
    ModeLine       "800x600@56" 36.0 800 824 896 1024 600 601 603 625 +hsync +vsync
    ModeLine       "800x600@60" 40.0 800 840 968 1056 600 601 605 628 +hsync +vsync
    ModeLine       "1024x768@60" 65.0 1024 1048 1184 1344 768 771 777 806 -hsync -vsync
EndSection

Section "Monitor"

 # 
    Identifier     "monitor1"
    Gamma           1
EndSection

Section "Monitor"
    Identifier     "Monitor0"
    VendorName     "Unknown"
    ModelName      "AUO"
    HorizSync       30.0 - 75.0
    VertRefresh     60.0
EndSection

Section "Device"
    Identifier     "GeForce 7000M"
    Driver         "nvidia"
    BoardName      "vesa"
    BusID          "PCI:0:18:0"
    Screen          0
EndSection

Section "Device"

 # 
    Identifier     "device1"
    Driver         "vesa"
    BoardName      "vesa"
    BusID          "PCI:0:18:0"
    Screen          1
EndSection

Section "Device"
    Identifier     "Videocard0"
    Driver         "nvidia"
    VendorName     "NVIDIA Corporation"
    BoardName      "GeForce 7000M / nForce 610M"
EndSection

Section "Screen"
    Identifier     "Default Screen"
    Device         "GeForce 7000M"
    Monitor        "Generic Monitor"
    DefaultDepth    24
    SubSection     "Display"
        Virtual     1280 800
        Depth       24
        Modes      "1280x800@60" "1024x768@60" "800x600@60" "800x600@56" "640x480@60"
    EndSubSection
EndSection

Section "Screen"

 # 
    Identifier     "screen1"
    Device         "device1"
    Monitor        "monitor1"
    DefaultDepth    24
EndSection

Section "Screen"
    Identifier     "Screen0"
    Device         "Videocard0"
    Monitor        "Monitor0"
    DefaultDepth    24
    Option         "TwinView" "0"
    Option         "metamodes" "1280x800_60 +0+0; 1024x768@60 +0+0; 800x600@60 +0+0; 640x480@60 +0+0"
EndSection

```

it's kind of mess here, but somehow it works fine =))) there's no 1280x80@60 option here, but i think the key entry is in last "Screen" section ( Option         "metamodes" "1280x800_60 +0+0; 1024x768@60 +0+0; 800x600@60 +0+0; 640x480@60 +0+0")

---

### Post by urindian on 2007-11-04
Great forum guys...i read all your replys...i too have the same problem..

I have a laptop with 7.04 installed on it...couldt get the atheros wireless card to work..i will try all the steps mentioned here and get back to you if i can't ;)


Great Work !!! :popcorn:

---

### Post by -TANNER- on 2007-11-06
Hello,  and thank, now I have not  problems with nvidia and sound but I have other problems:

- The memory card reader
- s-video TV-Out

I can't read any memory card. 
I try to use nvtv to use the s-video but it not open.

Other cuestion, is the same nvidia-glx-new than  oficial nvidia drivers?
I use ubuntu 7.10 and I need help.
Thank

---

### Post by i_TheDevil_i on 2007-11-07
mem card reader:
it has been working from the beginning =) but, somehow it does read only SD family card (SD, MiniSD, MicroSD). i tried xD card, but it won't read them. it's not a big problem for me, because i only use the MicroSD cards (for my Nokia). so i have't yet worked on that.
s-video: don't use it...

i don't know if nvidia-glx-new and off drivers for Nvidia cards are the same, but i haven't seen the graphical settings utility in nvidia-glx-new when i was using it =) the off driver has it =)

---

### Post by -TANNER- on 2007-11-07
This not a good solution but thank, and I use MMC but I can't read it.
I'm going to install Ubuntu Ultimate 1.6 and I hope to be a good results
, I'll post abaut.

---

### Post by Muki on 2007-11-07
> **grenier said:**
> - For the geforce 7000M's driver: 
[LIST=1]
[*]Install (search in synaptic, I don't remember the exact name) nvidia-glx-new (I think that's the name).
[*]In a terminal type "sudo nvidia-glx-config enable" (I think, again)
[*]sudo gedit /etc/X11/xorg.conf - check whether the entry "Driver" is nv or nvidia. If it's the former, change it to nvidia.
[*]Reboot
[/LIST]

- For the sound card:
[LIST=1]
[*]Install the ...-modules-backport (where ... may be kernel. I'm not in front of my computer right now so I can't check the exact names. Looking for backport should give it to you. Be careful not to select the one with version number so it'll be upgraded when necessary)
[*]Reboot
[/LIST]


I haven't gotten further so far. But I did check that both suspend to ram and the integrated sd card reader worked out of the box.



I got the sound working as grenier instructed. It worked like magic. Just selected the "linux-backports-modules v.2.6.22-14.21" in the Synaptic Package Manager, which caused the "linux-backports-modules v.2.6.22-14.21-2.6.2" package to be automatically selected. Applied, rebooted, and it worked! Thanks grenier!

---

### Post by lucasrossi on 2007-11-08
Hi to every body!
I have an Acer Aspire 5520, and I have big problems to install Ubuntu 7.10.
The huge problems reguards the GeForce 7000M...Ubuntu doesn't recognize it.

Could you help me?

Please

---

### Post by Muki on 2007-11-08
> **lucasrossi said:**
> Hi to every body!
I have an Acer Aspire 5520, and I have big problems to install Ubuntu 7.10.
The huge problems reguards the GeForce 7000M...Ubuntu doesn't recognize it.

Could you help me?

Please


Hey lucasrossi:
This is what I did. I installed the 32-bit version rather than the 64-bit, BTW.
1.) Install with the Live CD, and choose "Start Ubuntu in safe graphics mode". Now here, you will have a problem, as the dialog windows cannot be resized (made smaller). I think with one exception, I just hit Enter through the windows. If you hit the wrong button, you will have the option of going back. Then just use the Tab key to make another choice. (You could also look at [http://www.howtoforge.com/the_perfect_desktop_ubuntu_gutsy_gibbon](http://www.howtoforge.com/the_perfect_desktop_ubuntu_gutsy_gibbon) which will show you all the windows in the installation process, and all the buttons in each window. This also gives you some good tips on extra software to load.)
2.) Once you have rebooted and logged in, go to System -> Adminsistration -> Software Sources and under Ubuntu Software, enable the first four items (including Proprietary drivers for devices). While you are here, on the Updates Tab, I would enable the Important Security and Recommended Updates as well.
3.) Then go to System -> Adminsistration -> Restricted Drivers and enable the NVIDIA accelerated graphics driver (latest cards). It seems the kernel recognizes the video card, but you must enable the proprietary drivers as under #2 above, or you will not be able to enable the NVIDIA driver here. Reboot, and you should be OK.

BTW the ethernet and touchpad work without any tweaking. I also got the sound to work, by following a tip from grenier above:

"- For the sound card:
Install the ...-modules-backport (where ... may be kernel. I'm not in front of my computer right now so I can't check the exact names. Looking for backport should give it to you. Be careful not to select the one with version number so it'll be upgraded when necessary) 
Reboot "

The package is called "linux-backports-modules v. 2.6.22-14.21". When you select this one, the package named "linux-backports-modules v. 2.6.22-14.21-2.6.2" is automatically selected. Keep both, and reboot, and you will have sound.

I also installed most of the apps and utilities in the above-mentioned howtoforge article, and my webcam works, and I was also able to burn a CD.


Good luck. Let me know how it went!

Tanti saluti da Boston! Muki

---

### Post by lucasrossi on 2007-11-10
Hi Muki!
Now I succed in installing ubuntu 7.10 (64bit)  ( I tried 7.04 but more problems). The audio is fine thanks to your advice. But the resolution is "only" 800x600, even if the driver seems to be enabled.  Could you help me with this? I tried to copy some xorg.conf I found in the previous messages but fail..
tnx

---

### Post by Doggtagg on 2007-11-11
Hey everyone, i first i would like to thank all of you that contributed to this post, it has been a great help getting sound to work. 

I've been a religious slackware/zenwalk user for the last 4 or 5 years now, and today decided to give ubuntu a try on my new acer aspire 5520. I must say that so far i am pretty impressed with what i see, although i think i will keep using zenwalk on my desktop box.

Anyways, i am still having a problem getting ndiswapper setup. i have used the guide found [here]("https://help.ubuntu.com/community/WifiDocs/Driver/Ndiswrapper") and the drivers i_TheDevil_i refereed to on the first page of this thread, which installed and are displayed using the ndisgtk gui. I also ran the commands "sudo depmod -a" and "sudo modprobe ndiswrapper" from terminal. However no wireless card is shown using the system/administration/network tool or when running iwconfig from the command line.

Any suggestions?



Also to lucasrossi  and anyone else having trouble getting a better screen resolution then 800x600 what worked for me was changing the monitor to a "acer 55s (widescreen)" using the system/administration/screens and graphics then running nvidia-settings from the command line.

---

### Post by Muki on 2007-11-11
Don't know, lucasrossi. Maybe something went wrong when you tinkered with the xord.conf file. I seem to remember that the resolution was set automatically when I got the right driver working. Maybe reinstall???

---

### Post by juanvvc on 2007-11-13
I have successfully installed Ubuntu 7.10 (AMD64) on my new Aspire 5520. Sound and screen working thanks to this thread. WiFi needed some extra work, thought. Webcam, internal microphone, DVD writer and card reader work out of the box. The only missing bit is the special keys ('e', browser and eMail keys) since they are not detected at the kernel level. Amaizingly, the stop, play, next and prev song keys work in Amarok without further configuration, and also the control of the brightness of the screen.

Sound and Graphics: During the installation process you have to use the 'safe graphics' option. After the main installation, run:

```

sudo apt-get install linux-restricted-modules linux-backport-modules nvidia-glx-new

```

After rebooting, sound and 1024x800 worked as charm.

Wifi: you have to use the WindowsXP drivers and forbid the ath_pci module to load. The driver in your Windows Vista partition (c:\DRV\802BG\Atheros\netathrx.inf) installs in ndiswrapper, but won't load. I used the drivers [here](http://blakecmartin.googlepages.com/ar5007eg-64-0.2.tar.gz). (accessible during November, 2007) and then

```

tar -xvzf ar5007eg-64-0.2.tar.gz
cd ar5007eg-64-0.2/ar5007eg
sudo ndiswrapper -i net5211.inf
sudo echo 'blacklist ath_pci' >> /etc/modprobe.d/blacklist
sudo echo 'ndiswrapper' >> /etc/modules

```

Finally, reboot your machine. Rebooting at this moment is important: altough you can 'rmmod ath_pci', it seems that ath_pci loaded some other module that prevents ndiswrapper to start. Reboot your system to have a clean module list.

Thanks!

---

### Post by lucasrossi on 2007-11-13
Ok, for me it worked Doggtagg's way. Now I'm gonna try wireless..
tnx!

---

### Post by Chugaister on 2007-11-21
Could someone who succeed with sound and VGA drivers list your wirking kernel modules and their parameters. 
I am using 64 bit distro and haven't heard any sound yet.

```
cat /proc/modules
sudo /sbin/lsmod 
```

---

### Post by Muki on 2007-11-21
As for the sound, the following is from my post above..... The video is almost detailed in my post above...


BTW the ethernet and touchpad work without any tweaking. I also got the sound to work, by following a tip from grenier above:

"- For the sound card:
Install the ...-modules-backport (where ... may be kernel. I'm not in front of my computer right now so I can't check the exact names. Looking for backport should give it to you. Be careful not to select the one with version number so it'll be upgraded when necessary) 
Reboot "

The package is called "linux-backports-modules v. 2.6.22-14.21". When you select this one, the package named "linux-backports-modules v. 2.6.22-14.21-2.6.2" is automatically selected. Keep both, and reboot, and you will have sound.

---

### Post by naelr on 2007-11-22
Hi all... I recently purchased the 5520-5716.  The live cd for Kubuntu works just fine but it will not boot into linux at all.  see this thread

[http://ubuntuforums.org/showthread.php?t=565213&highlight=acer+5520](http://ubuntuforums.org/showthread.php?t=565213&highlight=acer+5520)

has anyone who has gotten it to install and run experienced these problems?  I have not tried Ubuntu over Kubuntu because they have the same sources .. might this be a problem?  I was next gonna try the alternate driver cd but good old turkey day preparations took my time from me.  Any one have any other suggestions?

thanks 

Naelr

---

### Post by k3pp0 on 2007-11-28
hi all
i have installed succesfully on my Aspire 5520 Ubuntu gutsy, ad managed audio to work thanks to your advices.
the problem is WICD (network manager i used on my old laptop ad worked like a charm)....i can't make it work on 5520...neither the wireless is workin...
any piece of advice?

Thanks a lot!!!

---

### Post by k3pp0 on 2007-11-30
bump!

problem is: wicd freeze and not work
webcam has always been dead
after installing (and removing) wicd, afetr reboot all network eth interfaces are not configured...
Help guys!!
Thanks anyway :)

---

### Post by i_TheDevil_i on 2007-11-30
why not using the standart Ubuntu network manager? =)

P.S.: btw, it seem to be that Acer Aspire 5520 is not on the list of (un)successfully tested hardware [here]("http://wicd.sourceforge.net/wiki/doku.php?id=testing"), so i think u have to do some tweaks manually. in other way use standart network manager.

---

### Post by k3pp0 on 2007-12-01
Hi,
finally got latest wicd 1.4.7 working.
First apt-remove network manager.
Then foud the problem: each reboot the ethx name changed in ethx+1.

Had to tweak the  /etc/udev/rules.d/70-persistent-net.rules removing all ethx entries (it generated a new ethx interface alias each time i reboot...that's why even if i configure an interface, next reboot it was not recognised...it changed name!
the file showed 34 ethx interface...34 reboot since i bougth the notebook)

Then i added these 2 lines:

# PCI device 0x10de:0x054c (forcedeth)
SUBSYSTEM=="net", DRIVERS=="forcedeth", NAME="eth0"

All is fine now.

Therefore i'm having truobles managing the Crystal Eye...the system recognise it but i can't make any read i/o to the device with any software.

If anybody can help...it would be appreciated.

---

### Post by jackpcws on 2007-12-03
I also have the same laptop but I have not been able to successfully install 7.10.  I used the alternate cd and the install ran successfully.

At first boot, the splash screen appears,and the progress bar barely starts, then does nothing.   After a few minutes, I get the prompt (initramfs).

Any advice appreciated.

---

### Post by Stryker777 on 2007-12-06
Same exact problem.  It is a kernel issue.  I was able to change to the I386 kernel and get it working but only with one core.  I am now running under feisty and everything except the webcam is working.  The webcam is recognized and even activates, just errors after that so I am working on it tonight.  I sure wish I could run gutsy though.  If I even do a kernel update from the base feisty cd, the pc is unrecoverable without a live cd.

---

### Post by juanvvc on 2007-12-10
jackpcws and Stryker777, the AMD64 version works but you need to select the safe graphics mode in the first installation menu, and then configure the video card as described in previous posts of this very thread.

The webcam works out of the box in Kopete but I do not know why other applications can't make the webcam work. I managed to use the internal microphone once, so it works. Unfortunately it is dead for me right now.

---

### Post by Stryker777 on 2007-12-15
Thank you for your response Jaunvvc, and I wish you were correct in my case.  Unfortunatley it does not work on this one.  Maybe it is a revision issue.  I do not know.  What I do know is that the drive goes into a read only state and never exits.  It has nothing to do with video.  This only happens on dual core enabled kernels.

---

### Post by -TANNER- on 2007-12-26
This is the madwifi solution but only for 32bit

[http://madwifi.org/ticket/1679](http://madwifi.org/ticket/1679)

---

### Post by jackpcws on 2007-12-27
I finally have my Acer 5520 running with ubuntu 64 bit 7.10.   I found this in another forum and it worked.
I added the kernel option "all_generic_ide".  You will need to edit the grub prompt by pressing "e", select kernel and press "e" again.  I removed "quiet splash" and then appended "all_generic_ide" and it worked.
It is now working with the nvidia driver at 1280x800.  I add to edit the xorg.conf and described eariler in this post.
Now I need to fix the sound, wifi, and get bluetooth working.

---

### Post by i_TheDevil_i on 2007-12-27
i wrote about sound and wifi [here]("http://ubuntuforums.org/showpost.php?p=3679018&postcount=8") (1st page of this thread)

P.S.: Acer Aspire 5520 has not got the bluetooth... well, i don't know if that's absolutely correct, but i saw 3 models of Aspire 5520 and non of 'em had bluetooth =)

---

### Post by fwhill on 2008-01-04
THANK YOU!  An excellent post that was clear and effective.

I have and Acer Aspire 5520-5912.  It's working at 1280x800, with sound & Wifi.  I have not tested the webcam or mic yet.  Not sure what app to use for the test, but I'm a happy camper!

Again, thank you!

Frank Hill

---

### Post by Stryker777 on 2008-01-05
Thanks jackpcws
That was it for me.  I had never seen that anywhere else.  Much nicer being on gutsy now with dual core support.
Thanks again

---

### Post by daveequalscool on 2008-01-06
Thanks for all the help I've already taken from this thread -- I'm a linux noob and require lots of it.

I'm running 7.10 desktop for AMD64 I seem to have set up the nVidia card inadvertently. Not sure if this is a bad way of doing it but I figured I'd throw it up.

Open System... Preferences... Appearance, and click on the Visual Effects tab,
You should see three options: None (which is selected), Normal and Extra. Select Normal.
If nothing happens, close the dialog, open it back up and click on Extra.

I can't remember if it happened after I clicked on Normal or Extra, but I did eventually click on Extra. After one of the two became selected a prompt opened up for installation of what was needed. I clicked yes or OK a couple more times and it told me to reboot. I rebooted, and the resolution was 1280x800. The windows and workspaces are now flying around nicely as well.

---

### Post by giobertox on 2008-01-08
i tried this too ( on my ubuntu 64 , on my acer 5520 ) and
it finds my wireless card 
it finds the wireless network around me (name and signal strength)
but it CANT connect to any of em 

can you assure me that it allow you to USE the wireless connection around and not just SEE them  ?
Thank you very much  

> **juanvvc said:**
> I have successfully installed Ubuntu 7.10 (AMD64) on my new Aspire 5520. Sound and screen working thanks to this thread. WiFi needed some extra work, thought. Webcam, internal microphone, DVD writer and card reader work out of the box. The only missing bit is the special keys ('e', browser and eMail keys) since they are not detected at the kernel level. Amaizingly, the stop, play, next and prev song keys work in Amarok without further configuration, and also the control of the brightness of the screen.

Sound and Graphics: During the installation process you have to use the 'safe graphics' option. After the main installation, run:

```

sudo apt-get install linux-restricted-modules linux-backport-modules nvidia-glx-new

```

After rebooting, sound and 1024x800 worked as charm.

Wifi: you have to use the WindowsXP drivers and forbid the ath_pci module to load. The driver in your Windows Vista partition (c:\DRV\802BG\Atheros\netathrx.inf) installs in ndiswrapper, but won't load. I used the drivers [here](http://blakecmartin.googlepages.com/ar5007eg-64-0.2.tar.gz). (accessible during November, 2007) and then

```

tar -xvzf ar5007eg-64-0.2.tar.gz
cd ar5007eg-64-0.2/ar5007eg
sudo ndiswrapper -i net5211.inf
sudo echo 'blacklist ath_pci' >> /etc/modprobe.d/blacklist
sudo echo 'ndiswrapper' >> /etc/modules

```

Finally, reboot your machine. Rebooting at this moment is important: altough you can 'rmmod ath_pci', it seems that ath_pci loaded some other module that prevents ndiswrapper to start. Reboot your system to have a clean module list.

Thanks!

---

### Post by cfar893fm on 2008-01-09
how do i set the default resolution for gdm to 1280x800? whenever i restart the computer, gdm always reverts to 800x600, and gnome sometimes does. surely there's some x11 config file i can edit, right?

---

### Post by CyDharttha on 2008-01-13
> **jackpcws said:**
> I finally have my Acer 5520 running with ubuntu 64 bit 7.10.   I found this in another forum and it worked.
I added the kernel option "all_generic_ide".  You will need to edit the grub prompt by pressing "e", select kernel and press "e" again.  I removed "quiet splash" and then appended "all_generic_ide" and it worked.
It is now working with the nvidia driver at 1280x800.  I add to edit the xorg.conf and described eariler in this post.
Now I need to fix the sound, wifi, and get bluetooth working.

Thanks so much jackpcws, all_generic_ide got my 5520 booting, Up and running now! (Step one complete).

---

### Post by syno8 on 2008-01-14
Hey guys i have the acer 5520-5912

Thanks to this thread i got sound and screen working.  and i followed this line below and got my wireless working.

i think what my problem was i was using the driver net5211 instead of net5416

i have the  Atheros ARG5006EG


[http://quilombo.wordpress.com/2008/01/09/atheros-ar5006eg-in-ubuntu-710-gutsy-gibbon/](http://quilombo.wordpress.com/2008/01/09/atheros-ar5006eg-in-ubuntu-710-gutsy-gibbon/)

---

### Post by juanvvc on 2008-01-17
> **giobertox said:**
> 
it finds the wireless network around me (name and signal strength)
but it CANT connect to any of em 

can you assure me that it allow you to USE the wireless connection around and not just SEE them  ?

Since I'm writing through my Wifi connection, yes I can.

Keep in mind that this particular driver doesn't remove networks that are out of reach. Many of the networks that you see are no longer available. 

Besides, If your Wifi uses WPA it will be a bit more tricky to configure, and maybe not possible with this driver (i didn't test)

Connecting to a WEP Wifi network with DHCP (of course, just to test. Once confirmed use any graphical tool)

```

sudo iwconfig wlan0 essid 'YOUR_ESSID' enc on key s:YOUR_KEY
iwconfig <--------- if you see YOUR_ESSID listed here after ten seconds, you are in!
sudo dhclient wlan0

```

---

### Post by foppeh on 2008-01-17
> **cfar893fm said:**
> how do i set the default resolution for gdm to 1280x800? whenever i restart the computer, gdm always reverts to 800x600, and gnome sometimes does. surely there's some x11 config file i can edit, right?
/etc/X11/xorg.conf

---

### Post by Zendarin on 2008-01-25
> **syno8 said:**
> Hey guys i have the acer 5520-5912

Thanks to this thread i got sound and screen working.  and i followed this line below and got my wireless working.

i think what my problem was i was using the driver net5211 instead of net5416

i have the  Atheros ARG5006EG


[http://quilombo.wordpress.com/2008/01/09/atheros-ar5006eg-in-ubuntu-710-gutsy-gibbon/](http://quilombo.wordpress.com/2008/01/09/atheros-ar5006eg-in-ubuntu-710-gutsy-gibbon/)


Hey, I have the same wifi card, Atheros ARG5006EG, and the Net5211.inf driver works great for me. Did you install the 32-bit or 64-bit version of Ubuntu?? The windows driver has to match the bit version you installed.

---

### Post by cforput on 2008-01-26
Seems like everyone has their own way of getting their graphics card to work. Here is what I did.

You will need to reboot a couple of times during this process.
Install Drivers
  1.System
  2.Synaptic Package Manager
  3.Search for nVidia and select the following:
    1.nVidia-glx-new driver
    2.nVidia-cg-toolkit
    3.nVidia-kernel-common

Enable nVidia Driver
  1.System
  2.Administration
  3.Restricted Driver Manager
  4.Make sure nVidia accelerated graphics driver (latest cards) is enabled.

Setting up the Screen Size
  1.System
  2.Administration
  3.Screen and Graphics Preferences
  4.Make screen 1 Aspire 55s (Widescreen)
    1.Click on Model
    2.Select Acer
    3.Select Aspire 55s
    4.Click on Widescreen
      This is IMPORTANT. I never got the option to select 1280 x 800 until I chose Widescreen
    5.Click on OK.

I new to Ubuntu so don't ask me for any help if this doesn't work! Hahaha

---

### Post by i_TheDevil_i on 2008-01-26
> **cforput said:**
> Seems like everyone has their own way of getting their graphics card to work. Here is what I did.

You will need to reboot a couple of times during this process.
Install Drivers
  1.System
  2.Synaptic Package Manager
  3.Search for nVidia and select the following:
    1.nVidia-glx-new driver
    2.nVidia-cg-toolkit
    3.nVidia-kernel-common

Enable nVidia Driver
  1.System
  2.Administration
  3.Restricted Driver Manager
  4.Make sure nVidia accelerated graphics driver (latest cards) is enabled.

Setting up the Screen Size
  1.System
  2.Administration
  3.Screen and Graphics Preferences
  4.Make screen 1 Aspire 55s (Widescreen)
    1.Click on Model
    2.Select Acer
    3.Select Aspire 55s
    4.Click on Widescreen
      This is IMPORTANT. I never got the option to select 1280 x 800 until I chose Widescreen
    5.Click on OK.

I new to Ubuntu so don't ask me for any help if this doesn't work! Hahaha

good! =))))
i totally forgot about this way of setting up the resolution (i mean choosing widescreen)
i think it's because i tried it on earlier versions of ubuntu and there weren't good support for widescreens of notebooks =)))))

---

### Post by Pinger05 on 2008-01-29
First off I want to say this is an awesome thread!  I bought a Aspire 5520 thinking it would only run Vista...

So I have configured everything using this thread and a tutorial regarding NDISWRAPPER located here [https://help.ubuntu.com/community/WifiDocs/Driver/Ndiswrapper](https://help.ubuntu.com/community/WifiDocs/Driver/Ndiswrapper) and the wifi driver pointed out on page three of this thread.

My problem is this.  Now that I am using 1200 X 800 for my screen but every time I reboot or shut down it goes back to 800 X 600.  I would like to find out why.  Here is my xorg.conf file:
```
Section "Monitor"
	Identifier	"Generic Monitor"
	Vendorname	"Acer"
	Modelname	"Aspire 55s"
	Horizsync	30.0-54.0
	Vertrefresh	50.0-120.0
  modeline  "640x400@85" 31.5 640 672 736 832 400 401 404 445 -hsync +vsync
  modeline  "640x350@85" 31.5 640 672 736 832 350 382 385 445 +hsync -vsync
  modeline  "720x400@85" 35.5 720 756 828 936 400 401 404 446 -hsync +vsync
  modeline  "800x600@56" 36.0 800 824 896 1024 600 601 603 625 +hsync +vsync
  modeline  "800x600@72" 50.0 800 856 976 1040 600 637 643 666 +hsync +vsync
  modeline  "800x600@75" 49.5 800 816 896 1056 600 601 604 625 +hsync +vsync
  modeline  "800x600@85" 56.3 800 832 896 1048 600 601 604 631 +hsync +vsync
  modeline  "800x600@60" 40.0 800 840 968 1056 600 601 605 628 +hsync +vsync
  modeline  "1152x768@54" 64.995 1152 1178 1314 1472 768 771 777 806 +hsync +vsync
  modeline  "1280x854" 80.0 1280 1309 1460 1636 854 857 864 896 +hsync +vsync
  modeline  "1280x768@60" 80.14 1280 1344 1480 1680 768 769 772 795 -hsync +vsync
  modeline  "1280x720@60" 74.48 1280 1336 1472 1664 720 721 724 746 -hsync +vsync
  modeline  "1280x720@50" 60.47 1280 1328 1456 1632 720 721 724 741 -hsync +vsync
  modeline  "1280x800@60" 83.46 1280 1344 1480 1680 800 801 804 828 -hsync +vsync
	Gamma	1.0
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Device		"Generic Video Card"
	Monitor		"Generic Monitor"
	Defaultdepth	24
	SubSection "Display"
		Depth	24
		Virtual	1280	854
		Modes		"1280x800@60"	"1280x720@50"	"1280x720@60"	"1280x768@60"	"1280x854"	"1152x768@54"	"800x600@60"	"800x600@85"	"800x600@75"	"800x600@72"	"800x600@56"	"720x400@85"	"640x350@85"	"640x400@85"
	EndSubSection
EndSection

Section "ServerLayout"
	Identifier	"Default Layout"
  screen 0 "Default Screen" 0 0
	Inputdevice	"Generic Keyboard"
	Inputdevice	"Configured Mouse"
	
	# Uncomment if you have a wacom tablet
	#	InputDevice     "stylus"	"SendCoreEvents"
	#	InputDevice     "cursor"	"SendCoreEvents"
	#	InputDevice     "eraser"	"SendCoreEvents"
	Inputdevice	"Synaptics Touchpad"
EndSection
Section "Module"
	Load		"glx"
	Load		"v4l"
EndSection
Section "device" #      
	Identifier	"device1"
	Boardname	"nv"
	Busid		"PCI:0:18:0"
	Driver		"nvidia"
	Screen	1
EndSection
Section "screen" #      
	Identifier	"screen1"
	Device		"device1"
	Defaultdepth	24
	Monitor		"monitor1"
	SubSection "Display"
		Depth	24
		Modes		"640x480@60"
	EndSubSection
EndSection
Section "monitor" #      
	Identifier	"monitor1"
	Vendorname	"Plug 'n' Play"
	Modelname	"Plug 'n' Play"
  modeline  "640x480@60" 25.2 640 656 752 800 480 490 492 525 -vsync -hsync
	Gamma	1.0
EndSection
Section "ServerFlags"
EndSection
```

If this annoyance can be fixed I would really appreciate it.  BTW this thread rocks!!:guitar:

---

### Post by i_TheDevil_i on 2008-01-30
well, i just set the resolution of 1280 by 800 in Nvidia Control Panel that goes with official drivers from Nvidia. =)   there's an option to change the resolution of a monitor.. and u can save the settings to xorg.conf directly from there

---

### Post by cfar893fm on 2008-02-09
> My problem is this. Now that I am using 1200 X 800 for my screen but every time I reboot or shut down it goes back to 800 X 600. I would like to find out why.

had the same problem until the other day. there are two ways to reset the resolution in gnome, system> prefs> screen resolution and system> admin> screens and graphics. at first, only the second one would change the resolution, and after restarting the pc, it would revert to 800x600. 

in system> prefs> screen resolution, there's a check box to set the default. i did that, restarted, then it worked fine once. after restarting again, it locked the resolution to 800x600 and nothing would change it. so i unchecked the box, restarted, and now the resolution always automatically changes to 1280x800 when gnome starts. 

fyi.

---

### Post by Pinger05 on 2008-02-12
> **cfar893fm said:**
> 
in system> prefs> screen resolution, there's a check box to set the default. i did that, restarted, then it worked fine once. after restarting again, it locked the resolution to 800x600 and nothing would change it. so i unchecked the box, restarted, and now the resolution always automatically changes to 1280x800 when gnome starts. 

fyi.

Worked perfectly.  Thanks!

---

### Post by mauriciolopez on 2008-02-17
I've got this laptop with the 1280 x 800 resolution working perfectly, but as in Windows XP I want to use 1440 x 900 resolution and I can't make it work.

How can I do to change the resolution to 1440 x 900?

Thanx in advance.

---

### Post by i_TheDevil_i on 2008-02-17
the monitor of **Acer Aspire 5520** doesn't support that resolution. MAX is 1280 by 800... maybe u have another model of Acer Aspire?

P.S.: btw, does anyone know how to get new version (169.09) of nvidia drivers to work? i was trying to install them "the right way" (as described on nvidia forums), but anyway i do the install, ubuntu starts in low-graphics mode... don't know what to do... =((

---

### Post by petterborg on 2008-02-21
> **grenier said:**
> Well, no luck for the resolution.
In nvidia-settings, I see the screen is properly detected, but no apparent way to use that (or did I miss something obvious?)
The most infuriating of all is that I *can* have everything work properly. Following something I got from the linuxquestions forum, I erased every reference to resolution in xorg.conf (appart from color depth) and let xorg figure it out by itself.

A reboot of the xserver later, everything was working properly and I finally had the appropriate entry (1280x800) available in the settings.

Unfortunately, after checking, I also found out that between that X server reboot and me logging back in, there's something that rewrites the #%$!ng wrong entries in xorg.conf. That means that for now, if I want the proper resolution, I have to edit by hand the damn xorg.conf each and every time the X server gets rebooted.

](*,)

I read through this thread and it has helped me out A LOT.  Thanks everybody for being cool and doing the research.  :)  So far everything works on my 5520-5912:  sound, Crystal Eye, nVidia driver, wireless, and I believe BlueTooth.

I have the same problem mentioned here by Grenier, that my X gets killed every time I reboot.  Re-running the nvidia *.run script as sudoer brings it back to life.  The interesting thing is that every time I do this, I choose not to have it automatically edit my xorg.conf, though I have before and there is no difference to the behavior.

I got all excited when properly-confed X came up for the first time, then got angry:confused:when upon rebooting I got the same blinking behavior present before the successful config, switching available configs:mad:, so I think my modules are getting destroyed somehow.  I looked through all 6 pages, but nobody directly answered Grenier's question.  They just offered alternative xorg.conf options, but I assume that doesn't help when something automatically evil takes out whatever changes get done every time on reboot.  I want to swear, too!  ](*,)

Another note:  It wasn't until after I got rid of the Ubuntu packages that deal with the driver and using the *.run script from nVidia that I had my first successful nVidia-accelerated X session, choosing the right monitor (as importantly and helpfully described here), then doing sudo nvidia-xconfig.  Since I've noticed quite a few methods, I thought that would be important to note.  Thanks again everybody for the work...

---

### Post by i_TheDevil_i on 2008-02-21
i discovered for me, that doing
```
sudo nvidia-settings
```
does everything nice. i mean, that u can set the resolution of the monitor through the nvidia-settings, but if u do this not as root, it won't be saved to xorg.conf , so the resolution will restore back after reboot.

ok, here's what i did exactly:

in terminal
```
sudo nvidia-settings
```

then in the area of X Server Display Configuration i set the Resolution to "Auto", then clicked on a button "Save to X Configuration File"... and after that i got the 1280 by 800 resolution working =)))))

---

### Post by petterborg on 2008-02-21
Wow!  Talk about a quick response!  I just tried that and no dice :(

I thought a copy of my X log would be useful...  After that I give you a copy of my xorg.conf.  I'm currently running X with the happy config right now (of course GDM loaded, but X blinked a few times then gave up), but only because I re-ran that *.run script from nVidia...  This is a "startx" session as we speak...

```

X Window System Version 1.3.0
Release Date: 19 April 2007
X Protocol Version 11, Revision 0, Release 1.3
Build Operating System: Linux Ubuntu (xorg-server 2:1.3.0.0.dfsg-12ubuntu8.3)
Current Operating System: Linux gringuito 2.6.22-14-generic #1 SMP Tue Feb 12 02:46:46 UTC 2008 x86_64
Build Date: 18 January 2008
	Before reporting problems, check http://wiki.x.org
	to make sure that you have the latest version.
Module Loader present
Markers: (--) probed, (**) from config file, (==) default setting,
	(++) from command line, (!!) notice, (II) informational,
	(WW) warning, (EE) error, (NI) not implemented, (??) unknown.
(==) Log file: "/var/log/Xorg.0.log", Time: Thu Feb 21 02:48:16 2008
(==) Using config file: "/etc/X11/xorg.conf"
(==) ServerLayout "Layout0"
(**) |-->Screen "Screen0" (0)
(**) |   |-->Monitor "Monitor0"
(**) |   |-->Device "Videocard0"
(**) |-->Input Device "Keyboard0"
(**) |-->Input Device "Mouse0"
(**) Option "Xinerama" "0"
(WW) The directory "/usr/share/fonts/X11/cyrillic" does not exist.
	Entry deleted from font path.
(==) FontPath set to:
	/usr/share/fonts/X11/misc,
	/usr/share/fonts/X11/100dpi/:unscaled,
	/usr/share/fonts/X11/75dpi/:unscaled,
	/usr/share/fonts/X11/Type1,
	/usr/share/fonts/X11/100dpi,
	/usr/share/fonts/X11/75dpi,
	/var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType
(**) RgbPath set to "/usr/X11R6/lib/X11/rgb"
(==) ModulePath set to "/usr/lib/xorg/modules"
(II) Open ACPI successful (/var/run/acpid.socket)
(II) Loader magic: 0x7cdb20
(II) Module ABI versions:
	X.Org ANSI C Emulation: 0.3
	X.Org Video Driver: 1.2
	X.Org XInput driver : 0.7
	X.Org Server Extension : 0.3
	X.Org Font Renderer : 0.5
(II) Loader running on linux
(II) LoadModule: "pcidata"
(II) Loading /usr/lib/xorg/modules//libpcidata.so
(II) Module pcidata: vendor="X.Org Foundation"
	compiled for 1.3.0, module version = 1.0.0
	ABI class: X.Org Video Driver, version 1.2
(--) using VT number 9

(II) PCI: PCI scan (all values are in hex)
(II) PCI: 00:00:0: chip 10de,0547 card 1025,0126 rev a2 class 05,00,00 hdr 00
(II) PCI: 00:01:0: chip 10de,0548 card 1025,0126 rev a2 class 06,01,00 hdr 80
(II) PCI: 00:01:1: chip 10de,0542 card 1025,0126 rev a2 class 0c,05,00 hdr 80
(II) PCI: 00:01:2: chip 10de,0541 card 10de,cb84 rev a2 class 05,00,00 hdr 80
(II) PCI: 00:01:3: chip 10de,0543 card 1025,0126 rev a2 class 0b,40,00 hdr 80
(II) PCI: 00:02:0: chip 10de,055e card 1025,0126 rev a2 class 0c,03,10 hdr 80
(II) PCI: 00:02:1: chip 10de,055f card 1025,0126 rev a2 class 0c,03,20 hdr 80
(II) PCI: 00:04:0: chip 10de,055e card 1025,0126 rev a2 class 0c,03,10 hdr 80
(II) PCI: 00:04:1: chip 10de,055f card 1025,0126 rev a2 class 0c,03,20 hdr 80
(II) PCI: 00:06:0: chip 10de,0560 card 1025,0126 rev a1 class 01,01,8a hdr 00
(II) PCI: 00:07:0: chip 10de,055c card 1025,0126 rev a1 class 04,03,00 hdr 80
(II) PCI: 00:08:0: chip 10de,0561 card 0000,0000 rev a2 class 06,04,01 hdr 01
(II) PCI: 00:09:0: chip 10de,0550 card 1025,0126 rev a2 class 01,01,85 hdr 80
(II) PCI: 00:0a:0: chip 10de,054c card 1025,0126 rev a2 class 02,00,00 hdr 00
(II) PCI: 00:0c:0: chip 10de,0563 card 0000,0000 rev a2 class 06,04,00 hdr 01
(II) PCI: 00:0d:0: chip 10de,0563 card 0000,0000 rev a2 class 06,04,00 hdr 01
(II) PCI: 00:12:0: chip 10de,0533 card 1025,0126 rev a2 class 03,00,00 hdr 00
(II) PCI: 00:18:0: chip 1022,1100 card 0000,0000 rev 00 class 06,00,00 hdr 80
(II) PCI: 00:18:1: chip 1022,1101 card 0000,0000 rev 00 class 06,00,00 hdr 80
(II) PCI: 00:18:2: chip 1022,1102 card 0000,0000 rev 00 class 06,00,00 hdr 80
(II) PCI: 00:18:3: chip 1022,1103 card 0000,0000 rev 00 class 06,00,00 hdr 80
(II) PCI: 01:04:0: chip 1180,0832 card 1025,0126 rev 05 class 0c,00,10 hdr 80
(II) PCI: 01:04:1: chip 1180,0822 card 1025,0126 rev 22 class 08,05,00 hdr 80
(II) PCI: 01:04:2: chip 1180,0843 card 1025,0126 rev 12 class 08,80,00 hdr 80
(II) PCI: 01:04:3: chip 1180,0592 card 1025,0126 rev 12 class 08,80,00 hdr 80
(II) PCI: 01:04:4: chip 1180,0852 card 1025,0126 rev 12 class 08,80,00 hdr 80
(II) PCI: 05:00:0: chip 168c,001c card 1468,0428 rev 01 class 02,00,00 hdr 00
(II) PCI: End of PCI scan
(II) PCI-to-ISA bridge:
(II) Bus -1: bridge is at (0:1:0), (0,-1,-1), BCTRL: 0x0008 (VGA_EN is set)
(II) Subtractive PCI-to-PCI bridge:
(II) Bus 1: bridge is at (0:8:0), (0,1,1), BCTRL: 0x0204 (VGA_EN is cleared)
(II) Bus 1 non-prefetchable memory range:
	[0] -1	0	0xf2300000 - 0xf23fffff (0x100000) MX[B]
(II) PCI-to-PCI bridge:
(II) Bus 3: bridge is at (0:12:0), (0,3,4), BCTRL: 0x0004 (VGA_EN is cleared)
(II) Bus 3 I/O range:
	[0] -1	0	0x00004000 - 0x000040ff (0x100) IX[B]
	[1] -1	0	0x00004400 - 0x000044ff (0x100) IX[B]
	[2] -1	0	0x00004800 - 0x000048ff (0x100) IX[B]
	[3] -1	0	0x00004c00 - 0x00004cff (0x100) IX[B]
(II) Bus 3 non-prefetchable memory range:
	[0] -1	0	0xf2000000 - 0xf21fffff (0x200000) MX[B]
(II) Bus 3 prefetchable memory range:
	[0] -1	0	0xf2800000 - 0xf29fffff (0x200000) MX[B]
(II) PCI-to-PCI bridge:
(II) Bus 5: bridge is at (0:13:0), (0,5,5), BCTRL: 0x0004 (VGA_EN is cleared)
(II) Bus 5 non-prefetchable memory range:
	[0] -1	0	0xf2200000 - 0xf22fffff (0x100000) MX[B]
(II) Host-to-PCI bridge:
(II) Bus 0: bridge is at (0:24:0), (0,0,5), BCTRL: 0x0008 (VGA_EN is set)
(II) Bus 0 I/O range:
	[0] -1	0	0x00000000 - 0x0000ffff (0x10000) IX[B]
(II) Bus 0 non-prefetchable memory range:
	[0] -1	0	0x00000000 - 0xffffffff (0x100000000) MX[B]
(II) Bus 0 prefetchable memory range:
	[0] -1	0	0x00000000 - 0xffffffff (0x100000000) MX[B]
(--) PCI:*(0:18:0) nVidia Corporation unknown chipset (0x0533) rev 162, Mem @ 0xf1000000/24, 0xd0000000/28, 0xf0000000/24
(II) Addressable bus resource ranges are
	[0] -1	0	0x00000000 - 0xffffffff (0x100000000) MX[B]
	[1] -1	0	0x00000000 - 0x0000ffff (0x10000) IX[B]
(II) OS-reported resource ranges:
	[0] -1	0	0x00100000 - 0x3fffffff (0x3ff00000) MX[B]E(B)
	[1] -1	0	0x000f0000 - 0x000fffff (0x10000) MX[B]
	[2] -1	0	0x000c0000 - 0x000effff (0x30000) MX[B]
	[3] -1	0	0x00000000 - 0x0009ffff (0xa0000) MX[B]
	[4] -1	0	0x0000ffff - 0x0000ffff (0x1) IX[B]
	[5] -1	0	0x00000000 - 0x000000ff (0x100) IX[B]
(II) Active PCI resource ranges:
	[0] -1	0	0xf2200000 - 0xf220ffff (0x10000) MX[B]
	[1] -1	0	0xf2301400 - 0xf23014ff (0x100) MX[B]
	[2] -1	0	0xf2301000 - 0xf23010ff (0x100) MX[B]
	[3] -1	0	0xf2300c00 - 0xf2300cff (0x100) MX[B]
	[4] -1	0	0xf2300800 - 0xf23008ff (0x100) MX[B]
	[5] -1	0	0xf2300000 - 0xf23007ff (0x800) MX[B]
	[6] -1	0	0xf2689800 - 0xf268980f (0x10) MX[B]
	[7] -1	0	0xf2689c00 - 0xf2689cff (0x100) MX[B]
	[8] -1	0	0xf2688000 - 0xf2688fff (0x1000) MX[B]
	[9] -1	0	0xf2684000 - 0xf2685fff (0x2000) MX[B]
	[10] -1	0	0xf2680000 - 0xf2683fff (0x4000) MX[B]
	[11] -1	0	0xf2689400 - 0xf26894ff (0x100) MX[B]
	[12] -1	0	0xf2687000 - 0xf2687fff (0x1000) MX[B]
	[13] -1	0	0xf2689000 - 0xf26890ff (0x100) MX[B]
	[14] -1	0	0xf2686000 - 0xf2686fff (0x1000) MX[B]
	[15] -1	0	0xf0000000 - 0xf0ffffff (0x1000000) MX[B](B)
	[16] -1	0	0xd0000000 - 0xdfffffff (0x10000000) MX[B](B)
	[17] -1	0	0xf1000000 - 0xf1ffffff (0x1000000) MX[B](B)
	[18] -1	0	0xf2400000 - 0xf247ffff (0x80000) MX[B]
	[19] -1	0	0x000030f8 - 0x000030ff (0x8) IX[B]
	[20] -1	0	0x000030d0 - 0x000030df (0x10) IX[B]
	[21] -1	0	0x000030e0 - 0x000030e3 (0x4) IX[B]
	[22] -1	0	0x000030e8 - 0x000030ef (0x8) IX[B]
	[23] -1	0	0x000030e4 - 0x000030e7 (0x4) IX[B]
	[24] -1	0	0x000030f0 - 0x000030f7 (0x8) IX[B]
	[25] -1	0	0x000030c0 - 0x000030cf (0x10) IX[B]
	[26] -1	0	0x00003000 - 0x0000303f (0x40) IX[B]
	[27] -1	0	0x00003040 - 0x0000307f (0x40) IX[B]
	[28] -1	0	0x00003080 - 0x000030bf (0x40) IX[B]
	[29] -1	0	0x00001d00 - 0x00001dff (0x100) IX[B]
(II) Active PCI resource ranges after removing overlaps:
	[0] -1	0	0xf2200000 - 0xf220ffff (0x10000) MX[B]
	[1] -1	0	0xf2301400 - 0xf23014ff (0x100) MX[B]
	[2] -1	0	0xf2301000 - 0xf23010ff (0x100) MX[B]
	[3] -1	0	0xf2300c00 - 0xf2300cff (0x100) MX[B]
	[4] -1	0	0xf2300800 - 0xf23008ff (0x100) MX[B]
	[5] -1	0	0xf2300000 - 0xf23007ff (0x800) MX[B]
	[6] -1	0	0xf2689800 - 0xf268980f (0x10) MX[B]
	[7] -1	0	0xf2689c00 - 0xf2689cff (0x100) MX[B]
	[8] -1	0	0xf2688000 - 0xf2688fff (0x1000) MX[B]
	[9] -1	0	0xf2684000 - 0xf2685fff (0x2000) MX[B]
	[10] -1	0	0xf2680000 - 0xf2683fff (0x4000) MX[B]
	[11] -1	0	0xf2689400 - 0xf26894ff (0x100) MX[B]
	[12] -1	0	0xf2687000 - 0xf2687fff (0x1000) MX[B]
	[13] -1	0	0xf2689000 - 0xf26890ff (0x100) MX[B]
	[14] -1	0	0xf2686000 - 0xf2686fff (0x1000) MX[B]
	[15] -1	0	0xf0000000 - 0xf0ffffff (0x1000000) MX[B](B)
	[16] -1	0	0xd0000000 - 0xdfffffff (0x10000000) MX[B](B)
	[17] -1	0	0xf1000000 - 0xf1ffffff (0x1000000) MX[B](B)
	[18] -1	0	0xf2400000 - 0xf247ffff (0x80000) MX[B]
	[19] -1	0	0x000030f8 - 0x000030ff (0x8) IX[B]
	[20] -1	0	0x000030d0 - 0x000030df (0x10) IX[B]
	[21] -1	0	0x000030e0 - 0x000030e3 (0x4) IX[B]
	[22] -1	0	0x000030e8 - 0x000030ef (0x8) IX[B]
	[23] -1	0	0x000030e4 - 0x000030e7 (0x4) IX[B]
	[24] -1	0	0x000030f0 - 0x000030f7 (0x8) IX[B]
	[25] -1	0	0x000030c0 - 0x000030cf (0x10) IX[B]
	[26] -1	0	0x00003000 - 0x0000303f (0x40) IX[B]
	[27] -1	0	0x00003040 - 0x0000307f (0x40) IX[B]
	[28] -1	0	0x00003080 - 0x000030bf (0x40) IX[B]
	[29] -1	0	0x00001d00 - 0x00001dff (0x100) IX[B]
(II) OS-reported resource ranges after removing overlaps with PCI:
	[0] -1	0	0x00100000 - 0x3fffffff (0x3ff00000) MX[B]E(B)
	[1] -1	0	0x000f0000 - 0x000fffff (0x10000) MX[B]
	[2] -1	0	0x000c0000 - 0x000effff (0x30000) MX[B]
	[3] -1	0	0x00000000 - 0x0009ffff (0xa0000) MX[B]
	[4] -1	0	0x0000ffff - 0x0000ffff (0x1) IX[B]
	[5] -1	0	0x00000000 - 0x000000ff (0x100) IX[B]
(II) All system resource ranges:
	[0] -1	0	0x00100000 - 0x3fffffff (0x3ff00000) MX[B]E(B)
	[1] -1	0	0x000f0000 - 0x000fffff (0x10000) MX[B]
	[2] -1	0	0x000c0000 - 0x000effff (0x30000) MX[B]
	[3] -1	0	0x00000000 - 0x0009ffff (0xa0000) MX[B]
	[4] -1	0	0xf2200000 - 0xf220ffff (0x10000) MX[B]
	[5] -1	0	0xf2301400 - 0xf23014ff (0x100) MX[B]
	[6] -1	0	0xf2301000 - 0xf23010ff (0x100) MX[B]
	[7] -1	0	0xf2300c00 - 0xf2300cff (0x100) MX[B]
	[8] -1	0	0xf2300800 - 0xf23008ff (0x100) MX[B]
	[9] -1	0	0xf2300000 - 0xf23007ff (0x800) MX[B]
	[10] -1	0	0xf2689800 - 0xf268980f (0x10) MX[B]
	[11] -1	0	0xf2689c00 - 0xf2689cff (0x100) MX[B]
	[12] -1	0	0xf2688000 - 0xf2688fff (0x1000) MX[B]
	[13] -1	0	0xf2684000 - 0xf2685fff (0x2000) MX[B]
	[14] -1	0	0xf2680000 - 0xf2683fff (0x4000) MX[B]
	[15] -1	0	0xf2689400 - 0xf26894ff (0x100) MX[B]
	[16] -1	0	0xf2687000 - 0xf2687fff (0x1000) MX[B]
	[17] -1	0	0xf2689000 - 0xf26890ff (0x100) MX[B]
	[18] -1	0	0xf2686000 - 0xf2686fff (0x1000) MX[B]
	[19] -1	0	0xf0000000 - 0xf0ffffff (0x1000000) MX[B](B)
	[20] -1	0	0xd0000000 - 0xdfffffff (0x10000000) MX[B](B)
	[21] -1	0	0xf1000000 - 0xf1ffffff (0x1000000) MX[B](B)
	[22] -1	0	0xf2400000 - 0xf247ffff (0x80000) MX[B]
	[23] -1	0	0x0000ffff - 0x0000ffff (0x1) IX[B]
	[24] -1	0	0x00000000 - 0x000000ff (0x100) IX[B]
	[25] -1	0	0x000030f8 - 0x000030ff (0x8) IX[B]
	[26] -1	0	0x000030d0 - 0x000030df (0x10) IX[B]
	[27] -1	0	0x000030e0 - 0x000030e3 (0x4) IX[B]
	[28] -1	0	0x000030e8 - 0x000030ef (0x8) IX[B]
	[29] -1	0	0x000030e4 - 0x000030e7 (0x4) IX[B]
	[30] -1	0	0x000030f0 - 0x000030f7 (0x8) IX[B]
	[31] -1	0	0x000030c0 - 0x000030cf (0x10) IX[B]
	[32] -1	0	0x00003000 - 0x0000303f (0x40) IX[B]
	[33] -1	0	0x00003040 - 0x0000307f (0x40) IX[B]
	[34] -1	0	0x00003080 - 0x000030bf (0x40) IX[B]
	[35] -1	0	0x00001d00 - 0x00001dff (0x100) IX[B]
(II) LoadModule: "dbe"
(II) Loading /usr/lib/xorg/modules/extensions//libdbe.so
(II) Module dbe: vendor="X.Org Foundation"
	compiled for 1.3.0, module version = 1.0.0
	Module class: X.Org Server Extension
	ABI class: X.Org Server Extension, version 0.3
(II) Loading extension DOUBLE-BUFFER
(II) LoadModule: "extmod"
(II) Loading /usr/lib/xorg/modules/extensions//libextmod.so
(II) Module extmod: vendor="X.Org Foundation"
	compiled for 1.3.0, module version = 1.0.0
	Module class: X.Org Server Extension
	ABI class: X.Org Server Extension, version 0.3
(II) Loading extension SHAPE
(II) Loading extension MIT-SUNDRY-NONSTANDARD
(II) Loading extension BIG-REQUESTS
(II) Loading extension SYNC
(II) Loading extension MIT-SCREEN-SAVER
(II) Loading extension XC-MISC
(II) Loading extension XFree86-VidModeExtension
(II) Loading extension XFree86-Misc
(II) Loading extension XFree86-DGA
(II) Loading extension DPMS
(II) Loading extension TOG-CUP
(II) Loading extension Extended-Visual-Information
(II) Loading extension XVideo
(II) Loading extension XVideo-MotionCompensation
(II) Loading extension X-Resource
(II) LoadModule: "type1"
(WW) Warning, couldn't open module type1
(II) UnloadModule: "type1"
(EE) Failed to load module "type1" (module does not exist, 0)
(II) LoadModule: "freetype"
(II) Loading /usr/lib/xorg/modules//fonts/libfreetype.so
(II) Module freetype: vendor="X.Org Foundation & the After X-TT Project"
	compiled for 1.3.0, module version = 2.1.0
	Module class: X.Org Font Renderer
	ABI class: X.Org Font Renderer, version 0.5
(II) Loading font FreeType
(II) LoadModule: "glx"
(II) Loading /usr/lib/xorg/modules/extensions//libglx.so
(II) Module glx: vendor="NVIDIA Corporation"
	compiled for 4.0.2, module version = 1.0.0
	Module class: X.Org Server Extension
	ABI class: X.Org Server Extension, version 0.1
(II) NVIDIA GLX Module  169.07  Thu Dec 13 19:15:29 PST 2007
(II) Loading extension GLX
(II) LoadModule: "record"
(II) Loading /usr/lib/xorg/modules/extensions//librecord.so
(II) Module record: vendor="X.Org Foundation"
	compiled for 1.3.0, module version = 1.13.0
	Module class: X.Org Server Extension
	ABI class: X.Org Server Extension, version 0.3
(II) Loading extension RECORD
(II) LoadModule: "dri"
(II) Loading /usr/lib/xorg/modules/extensions//libdri.so
(II) Module dri: vendor="X.Org Foundation"
	compiled for 1.3.0, module version = 1.0.0
	ABI class: X.Org Server Extension, version 0.3
(II) Loading extension XFree86-DRI
(II) LoadModule: "nvidia"
(II) Loading /usr/lib/xorg/modules/drivers//nvidia_drv.so
(II) Module nvidia: vendor="NVIDIA Corporation"
	compiled for 4.0.2, module version = 1.0.0
	Module class: X.Org Video Driver
(II) LoadModule: "kbd"
(II) Loading /usr/lib/xorg/modules/input//kbd_drv.so
(II) Module kbd: vendor="X.Org Foundation"
	compiled for 1.3.0, module version = 1.2.1
	Module class: X.Org XInput Driver
	ABI class: X.Org XInput driver, version 0.7
(II) LoadModule: "mouse"
(II) Loading /usr/lib/xorg/modules/input//mouse_drv.so
(II) Module mouse: vendor="X.Org Foundation"
	compiled for 1.3.0, module version = 1.2.1
	Module class: X.Org XInput Driver
	ABI class: X.Org XInput driver, version 0.7
(II) NVIDIA dlloader X Driver  169.07  Thu Dec 13 18:36:37 PST 2007
(II) NVIDIA Unified Driver for all Supported NVIDIA GPUs
(II) Primary Device is: PCI 00:12:0
(WW) NVIDIA: No matching Device section for instance (BusID PCI:0:1:3) found
(--) Assigning device section with no busID to primary device
(--) Chipset NVIDIA GPU found
(II) Loading sub module "fb"
(II) LoadModule: "fb"
(II) Loading /usr/lib/xorg/modules//libfb.so
(II) Module fb: vendor="X.Org Foundation"
	compiled for 1.3.0, module version = 1.0.0
	ABI class: X.Org ANSI C Emulation, version 0.3
(II) Loading sub module "wfb"
(II) LoadModule: "wfb"
(II) Loading /usr/lib/xorg/modules//libwfb.so
(II) Module wfb: vendor="NVIDIA Corporation"
	compiled for 7.1.99.2, module version = 1.0.0
(II) Loading sub module "ramdac"
(II) LoadModule: "ramdac"(II) Module already built-in
(II) resource ranges after xf86ClaimFixedResources() call:
	[0] -1	0	0x00100000 - 0x3fffffff (0x3ff00000) MX[B]E(B)
	[1] -1	0	0x000f0000 - 0x000fffff (0x10000) MX[B]
	[2] -1	0	0x000c0000 - 0x000effff (0x30000) MX[B]
	[3] -1	0	0x00000000 - 0x0009ffff (0xa0000) MX[B]
	[4] -1	0	0xf2200000 - 0xf220ffff (0x10000) MX[B]
	[5] -1	0	0xf2301400 - 0xf23014ff (0x100) MX[B]
	[6] -1	0	0xf2301000 - 0xf23010ff (0x100) MX[B]
	[7] -1	0	0xf2300c00 - 0xf2300cff (0x100) MX[B]
	[8] -1	0	0xf2300800 - 0xf23008ff (0x100) MX[B]
	[9] -1	0	0xf2300000 - 0xf23007ff (0x800) MX[B]
	[10] -1	0	0xf2689800 - 0xf268980f (0x10) MX[B]
	[11] -1	0	0xf2689c00 - 0xf2689cff (0x100) MX[B]
	[12] -1	0	0xf2688000 - 0xf2688fff (0x1000) MX[B]
	[13] -1	0	0xf2684000 - 0xf2685fff (0x2000) MX[B]
	[14] -1	0	0xf2680000 - 0xf2683fff (0x4000) MX[B]
	[15] -1	0	0xf2689400 - 0xf26894ff (0x100) MX[B]
	[16] -1	0	0xf2687000 - 0xf2687fff (0x1000) MX[B]
	[17] -1	0	0xf2689000 - 0xf26890ff (0x100) MX[B]
	[18] -1	0	0xf2686000 - 0xf2686fff (0x1000) MX[B]
	[19] -1	0	0xf0000000 - 0xf0ffffff (0x1000000) MX[B](B)
	[20] -1	0	0xd0000000 - 0xdfffffff (0x10000000) MX[B](B)
	[21] -1	0	0xf1000000 - 0xf1ffffff (0x1000000) MX[B](B)
	[22] -1	0	0xf2400000 - 0xf247ffff (0x80000) MX[B]
	[23] -1	0	0x0000ffff - 0x0000ffff (0x1) IX[B]
	[24] -1	0	0x00000000 - 0x000000ff (0x100) IX[B]
	[25] -1	0	0x000030f8 - 0x000030ff (0x8) IX[B]
	[26] -1	0	0x000030d0 - 0x000030df (0x10) IX[B]
	[27] -1	0	0x000030e0 - 0x000030e3 (0x4) IX[B]
	[28] -1	0	0x000030e8 - 0x000030ef (0x8) IX[B]
	[29] -1	0	0x000030e4 - 0x000030e7 (0x4) IX[B]
	[30] -1	0	0x000030f0 - 0x000030f7 (0x8) IX[B]
	[31] -1	0	0x000030c0 - 0x000030cf (0x10) IX[B]
	[32] -1	0	0x00003000 - 0x0000303f (0x40) IX[B]
	[33] -1	0	0x00003040 - 0x0000307f (0x40) IX[B]
	[34] -1	0	0x00003080 - 0x000030bf (0x40) IX[B]
	[35] -1	0	0x00001d00 - 0x00001dff (0x100) IX[B]
(II) resource ranges after probing:
	[0] -1	0	0x00100000 - 0x3fffffff (0x3ff00000) MX[B]E(B)
	[1] -1	0	0x000f0000 - 0x000fffff (0x10000) MX[B]
	[2] -1	0	0x000c0000 - 0x000effff (0x30000) MX[B]
	[3] -1	0	0x00000000 - 0x0009ffff (0xa0000) MX[B]
	[4] -1	0	0xf2200000 - 0xf220ffff (0x10000) MX[B]
	[5] -1	0	0xf2301400 - 0xf23014ff (0x100) MX[B]
	[6] -1	0	0xf2301000 - 0xf23010ff (0x100) MX[B]
	[7] -1	0	0xf2300c00 - 0xf2300cff (0x100) MX[B]
	[8] -1	0	0xf2300800 - 0xf23008ff (0x100) MX[B]
	[9] -1	0	0xf2300000 - 0xf23007ff (0x800) MX[B]
	[10] -1	0	0xf2689800 - 0xf268980f (0x10) MX[B]
	[11] -1	0	0xf2689c00 - 0xf2689cff (0x100) MX[B]
	[12] -1	0	0xf2688000 - 0xf2688fff (0x1000) MX[B]
	[13] -1	0	0xf2684000 - 0xf2685fff (0x2000) MX[B]
	[14] -1	0	0xf2680000 - 0xf2683fff (0x4000) MX[B]
	[15] -1	0	0xf2689400 - 0xf26894ff (0x100) MX[B]
	[16] -1	0	0xf2687000 - 0xf2687fff (0x1000) MX[B]
	[17] -1	0	0xf2689000 - 0xf26890ff (0x100) MX[B]
	[18] -1	0	0xf2686000 - 0xf2686fff (0x1000) MX[B]
	[19] -1	0	0xf0000000 - 0xf0ffffff (0x1000000) MX[B](B)
	[20] -1	0	0xd0000000 - 0xdfffffff (0x10000000) MX[B](B)
	[21] -1	0	0xf1000000 - 0xf1ffffff (0x1000000) MX[B](B)
	[22] -1	0	0xf2400000 - 0xf247ffff (0x80000) MX[B]
	[23] 0	0	0x000a0000 - 0x000affff (0x10000) MS[B]
	[24] 0	0	0x000b0000 - 0x000b7fff (0x8000) MS[B]
	[25] 0	0	0x000b8000 - 0x000bffff (0x8000) MS[B]
	[26] -1	0	0x0000ffff - 0x0000ffff (0x1) IX[B]
	[27] -1	0	0x00000000 - 0x000000ff (0x100) IX[B]
	[28] -1	0	0x000030f8 - 0x000030ff (0x8) IX[B]
	[29] -1	0	0x000030d0 - 0x000030df (0x10) IX[B]
	[30] -1	0	0x000030e0 - 0x000030e3 (0x4) IX[B]
	[31] -1	0	0x000030e8 - 0x000030ef (0x8) IX[B]
	[32] -1	0	0x000030e4 - 0x000030e7 (0x4) IX[B]
	[33] -1	0	0x000030f0 - 0x000030f7 (0x8) IX[B]
	[34] -1	0	0x000030c0 - 0x000030cf (0x10) IX[B]
	[35] -1	0	0x00003000 - 0x0000303f (0x40) IX[B]
	[36] -1	0	0x00003040 - 0x0000307f (0x40) IX[B]
	[37] -1	0	0x00003080 - 0x000030bf (0x40) IX[B]
	[38] -1	0	0x00001d00 - 0x00001dff (0x100) IX[B]
	[39] 0	0	0x000003b0 - 0x000003bb (0xc) IS[B]
	[40] 0	0	0x000003c0 - 0x000003df (0x20) IS[B]
(II) Setting vga for screen 0.
(**) NVIDIA(0): Depth 24, (--) framebuffer bpp 32
(==) NVIDIA(0): RGB weight 888
(==) NVIDIA(0): Default visual is TrueColor
(==) NVIDIA(0): Using gamma correction (1.0, 1.0, 1.0)
(**) NVIDIA(0): Option "TwinView" "0"
(**) NVIDIA(0): Option "MetaModes" "nvidia-auto-select +0+0"
(**) NVIDIA(0): Enabling RENDER acceleration
(II) NVIDIA(0): Support for GLX with the Damage and Composite X extensions is
(II) NVIDIA(0):     enabled.
(EE) NVIDIA(0): Failed to initialize the NVIDIA kernel module! Please ensure
(EE) NVIDIA(0):     that there is a supported NVIDIA GPU in this system, and
(EE) NVIDIA(0):     that the NVIDIA device files have been created properly. 
(EE) NVIDIA(0):     Please consult the NVIDIA README for details.
(EE) NVIDIA(0):  *** Aborting ***
(II) UnloadModule: "nvidia"
(II) UnloadModule: "wfb"
(II) UnloadModule: "fb"
(EE) Screen(s) found, but none have a usable configuration.

Fatal server error:
no screens found
```

Here is the copy of the xorg.conf:

```
# nvidia-settings: X configuration file generated by nvidia-settings
# nvidia-settings:  version 1.0  (buildmeister@builder26)  Thu Dec 13 18:56:19 PST 2007

Section "ServerLayout"
    Identifier     "Layout0"
    Screen      0  "Screen0" 0 0
    InputDevice    "Keyboard0" "CoreKeyboard"
    InputDevice    "Mouse0" "CorePointer"
EndSection

Section "Files"
    RgbPath         "/usr/X11R6/lib/X11/rgb"
EndSection

Section "Module"
    Load           "dbe"
    Load           "extmod"
    Load           "type1"
    Load           "freetype"
    Load           "glx"
EndSection

Section "ServerFlags"
    Option         "Xinerama" "0"
EndSection

Section "InputDevice"
    # generated from default
    Identifier     "Mouse0"
    Driver         "mouse"
    Option         "Protocol" "auto"
    Option         "Device" "/dev/psaux"
    Option         "Emulate3Buttons" "no"
    Option         "ZAxisMapping" "4 5"
EndSection

Section "InputDevice"
    # generated from default
    Identifier     "Keyboard0"
    Driver         "kbd"
EndSection

Section "Monitor"
    # HorizSync source: edid, VertRefresh source: edid
    Identifier     "Monitor0"
    VendorName     "Unknown"
    ModelName      "AUO"
    HorizSync       30.0 - 75.0
    VertRefresh     60.0
    Option         "DPMS"
EndSection

Section "Device"
    Identifier     "Videocard0"
    Driver         "nvidia"
    VendorName     "NVIDIA Corporation"
    BoardName      "GeForce 7000M / nForce 610M"
EndSection

Section "Screen"
    Identifier     "Screen0"
    Device         "Videocard0"
    Monitor        "Monitor0"
    DefaultDepth    24
    Option         "TwinView" "0"
    Option         "metamodes" "nvidia-auto-select +0+0"
    SubSection     "Display"
        Depth       24
    EndSubSection
EndSection

```

The xorg.conf never changes one bit on reboot.  I even "diff" it just for the sake of science!  I repeat:  the people on this forum are awesome...  Thanks in advance...:)

---

### Post by i_TheDevil_i on 2008-02-21
hmmm..... strange.... the same as my xorg.conf... and the log file too! but i had that log only when i installed official NVIDIA drivers ver 169.09.... =))) then i tried to install nvidia-glx-new from ubuntu repository (they are 100.14.19 version) and all worked fine =) maybe u should try this too...
P.S.: as i read from nvidia forums: some packages need to be removed before installing drivers... linux-restricted-modules is one of them... i tried doing the "right" way (as NVIDIA advices) but no effect... then just installed nvidia-glx-new =)

---

### Post by petterborg on 2008-02-21
Holy swear words!  Cool!  Uninstalling linux-restricted-modules (though from some reason keeping linux-restricted-modules-common was fine) did the trick.  I tried putting in the nvidia-glx-new but that just broke it again.  Perhaps after 3 versions of nVidia drivers there are some linking issues and some libraries that don't want to die.  Whatever the case, I have a working system now.

Thanks 



Aaron

---

### Post by Beowulf.1000 on 2008-02-23
Nice, thank you everybody! I now also have audio on my Acer Aspire 5520-5716. I rebooted after doing the instructions below, audio works great. Ubuntu 7.10 i386 

> **i_TheDevil_i said:**
> **grenier**! you are genius! =)
about the sound problem. i'll give the exact package names to be installed:
open Synaptic Package Manager, then search packages by the name "backport"
you'll see the list in which just check the "linux-backports-modules".. in the description it's written, that "This package will always depend on the latest generic Linux backported
drivers available." so i think it will automatically upgrade the package when the linux kernel is upgraded.
after installing the package i got the sound working! once again thank you grenier!!!


---

### Post by Harry2o on 2008-02-28
> **i_TheDevil_i said:**
> it would be better if i post more than the "Monitor" section.
there is more than one section which have some options for monitor =)

```

Section "Monitor"
    Identifier     "Generic Monitor"
    VendorName     "Generic LCD Display"
    ModelName      "LCD Panel 1280x800"
    HorizSync       31.5 - 50.0
    VertRefresh     56.0 - 65.0
    Gamma           1
    ModeLine       "640x480@60" 25.2 640 656 752 800 480 490 492 525 -hsync -vsync
    ModeLine       "800x600@56" 36.0 800 824 896 1024 600 601 603 625 +hsync +vsync
    ModeLine       "800x600@60" 40.0 800 840 968 1056 600 601 605 628 +hsync +vsync
    ModeLine       "1024x768@60" 65.0 1024 1048 1184 1344 768 771 777 806 -hsync -vsync
EndSection

Section "Monitor"

 # 
    Identifier     "monitor1"
    Gamma           1
EndSection

Section "Monitor"
    Identifier     "Monitor0"
    VendorName     "Unknown"
    ModelName      "AUO"
    HorizSync       30.0 - 75.0
    VertRefresh     60.0
EndSection

Section "Device"
    Identifier     "GeForce 7000M"
    Driver         "nvidia"
    BoardName      "vesa"
    BusID          "PCI:0:18:0"
    Screen          0
EndSection

Section "Device"

 # 
    Identifier     "device1"
    Driver         "vesa"
    BoardName      "vesa"
    BusID          "PCI:0:18:0"
    Screen          1
EndSection

Section "Device"
    Identifier     "Videocard0"
    Driver         "nvidia"
    VendorName     "NVIDIA Corporation"
    BoardName      "GeForce 7000M / nForce 610M"
EndSection

Section "Screen"
    Identifier     "Default Screen"
    Device         "GeForce 7000M"
    Monitor        "Generic Monitor"
    DefaultDepth    24
    SubSection     "Display"
        Virtual     1280 800
        Depth       24
        Modes      "1280x800@60" "1024x768@60" "800x600@60" "800x600@56" "640x480@60"
    EndSubSection
EndSection

Section "Screen"

 # 
    Identifier     "screen1"
    Device         "device1"
    Monitor        "monitor1"
    DefaultDepth    24
EndSection

Section "Screen"
    Identifier     "Screen0"
    Device         "Videocard0"
    Monitor        "Monitor0"
    DefaultDepth    24
    Option         "TwinView" "0"
    Option         "metamodes" "1280x800_60 +0+0; 1024x768@60 +0+0; 800x600@60 +0+0; 640x480@60 +0+0"
EndSection

```

it's kind of mess here, but somehow it works fine =))) there's no 1280x80@60 option here, but i think the key entry is in last "Screen" section ( Option         "metamodes" "1280x800_60 +0+0; 1024x768@60 +0+0; 800x600@60 +0+0; 640x480@60 +0+0")

All it needed for me to run the screen in 1280x800 mode was to change the Virtual line in the "Screen" section. I also have a mode "1280x800@60" there, but I do not have a seperate modeline for 1280x800 in Monitor NOR do I have the metamodes option.
(Ubuntu 7.10, Asus Notebook with GeForce7000M)

---

### Post by alexandru_sorin on 2008-03-03
try this:
sudo -s
sudo nvidia-xconfig
sudo init 6
sudo -s
sudo nvidia-settings
put your resolution, then "save to x configuration file" button


that's it

My problem is wirelees, install good driver, works 2 times ( first time was ok, after shutdown, stops working) after few reboot work again then stops. Seems to work when she want. Any solution will be apreciate. Everything work's in my laptop except wireless.

---

### Post by Virta on 2008-04-05
Hey guys, well today ive finally managed to install ubuntu.  Everything works out of the box (that i need so far) except for the dreaded wireless..I've tried everything on this post plus some googleing (ndiswrapper and mad wifi).  None have worked so far.  Any ideas? (laptop is the 5520 and my card is a AR5BXB63).


and would it be worth it to go and buy a linux compatible wifi card?

---

### Post by petterborg on 2008-04-06
I'm really close to believing that's an option.  Since the ndiswrapper setup consumes unholy amounts of CPU (run "top" on the shell and check out "ntos_wq" the CPU column while and after enabling and disabling ndiswrapper through "modprobe -r ndiswrapper" and "modprobe ndiswrapper"), and its function is erratic, I am really tempted to go get me a PCMCIA...  Even if the madwifi Atheros drivers get finished and working well and I have an extra card, having 2 would be advantageous.  I could use one for two different networks that I want separate (say it's important to be local on one network, but that network happens to be lousy for Internet; I could use another for that).  Since I'm about to take the Acer to rural Guatemala for 3 and a half months for GIS and research, dependability will be a must.  I'll report how it works while or after I'm down there.

BTW I would cook for you people who have provided all these awesome solutions but we are geographically limited!  You can check out my food weblog.  I'm trying to get it made with something more elegant like Django, but for now it's just plain 'ol CSS HTML.  [http://aaronrp.freeshell.org/](http://aaronrp.freeshell.org/)

---

### Post by andradelipe on 2008-04-07
Hi everyone,

I have an aspire 5520-5912 and I've used this topic to set up my Ubuntu 7.10 

I'm very happy to say that almost everithing is working now.

Wireless with ndiswrapper.
Webcam with "cheese" application.
nVidia 7000M  installed with "envy", because "nvidia-glx-new" didin't work properly with me.
Audio with some help here in this topic.

Now, some problems still bugging me:

Microphone is not working, even if I change "Digital" to "Capture" , like someone said here.
In nvidia-settings, I can't see the option to configure "s-video" "tv out".. Just appears one screen.

Someone have this things working?

If the answer is "YES, I'm blessed" ! Please, post an entire "xorg.conf" to help the poor guys like me.. =]

Thanks in advance! :)

---

### Post by Beowulf.1000 on 2008-04-12
> **Virta said:**
> Hey guys, well today ive finally managed to install ubuntu.  Everything works out of the box (that i need so far) except for the dreaded wireless..I've tried everything on this post plus some googleing (ndiswrapper and mad wifi).  None have worked so far.  Any ideas? (laptop is the 5520 and my card is a AR5BXB63). and would it be worth it to go and buy a linux compatible wifi card?

I have a 5520 (5520-5716) and got wifi working the past couple of days using madwifi -- check my two threads from the past few days. I am impressed by madwifi, it works, you just need to follow some steps as outlined in my threads.
[http://ubuntuforums.org/showthread.php?t=750137](http://ubuntuforums.org/showthread.php?t=750137)
[http://ubuntuforums.org/showthread.php?t=751239](http://ubuntuforums.org/showthread.php?t=751239)

---

### Post by backlash88 on 2008-04-22
Yea had the same prob...I move the bars on top and bottom to the sides and moved the window all the way up I was able to click the button...hope that helps

---

### Post by afk on 2008-04-27
so its been a while and no one seems to have the issue i do i run gutsy kde. and for some odd reason the system locks out of nowhere when sitting all alone for a while. i've checked logs. ect but all i see in var/log is where the pc quit reporting logs. and then when i started it back up again. so really i am at a loss. been dealing with this since this thread started i dunno how or what to try but its become enough of an issue i may need to debate a new os i've tried reinstalling ect but same issue anyone else have this issue or can provide any help?

---

### Post by dukeofgp on 2008-05-28
Greetings,
I am new to Ubuntu. I installed 7.10 in my Acer Aspire 5520-5912 and upgraded to 8.04 (64bit). I downloaded and installed a file from Nvidia website try to use Nvidia GeForce 7000M (NVIDIA-Linux-x86_64-169.12-pkg2.run). After I ran nvidia-settings, I don't have any choice to set to higher resolution, the highest resolution is 640 x 480. Any suggestion? Thanks.

---

### Post by Distun on 2008-06-23
I wish i found this thread sooner. Thanks guys!

---

