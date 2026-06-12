---
title: "NVIDIA GeForce GT 330M GPU"
date: 2010-05-03
forum: Hardware
---

### Post by gnilreps on 2010-05-03
installed 10.4

after that got the advice to install a dedicated driver for the NVIDIA GeForce GT 330M GPU

and after that my display was a mess

what should I do now


Windows7 ?

---

### Post by mrcsft on 2010-05-04
Same problem for me.
I have installed 10.04 32 bit version on a Sony Vaio F based on Intel i5 Core and nvidia GT 330M graphic.
Using the driver provided is very difficult to set the correct resolution, the laptop has a native res of 1920x1080 pixels but in any combination the graphic screen appear bigger than lcd screen...
Using purposed restricted driver system can't start regularly xorg.
I've tried also to install latest driver downloaded from nvidia site (version 195.36.24) with no luck...
I hope to find a way to get right resolution with provided driver (performance is not so important) perhaps trying editing xorg.conf :-k

---

### Post by gnilreps on 2010-05-04
> **mrcsft said:**
> Same problem for me.
I have installed 10.04 32 bit version on a Sony Vaio F based on Intel i5 Core and nvidia GT 330M graphic.
Using the driver provided is very difficult to set the correct resolution, the laptop has a native res of 1920x1080 pixels but in any combination the graphic screen appear bigger than lcd screen...
Using purposed restricted driver system can't start regularly xorg.
I've tried also to install latest driver downloaded from nvidia site (version 195.36.24) with no luck...
I hope to find a way to get right resolution with provided driver (performance is not so important) perhaps trying editing xorg.conf :-k

My laptop is the same type with the same problem: the resolution you see is the resolution of the external monitor about 2000 x 1500. My hope now is that the latest driver (195.36.24 end of April 2010)  will be made available in the 10.4 environment

---

### Post by mrcsft on 2010-05-04
The strange thing is that looking at the list of supported products for the latest 32 bit driver for Linux (195.36.24) NVIDIA GT 330M does not appear...

Here is the link (you have to click on "SUPPORTED PRODUCTS"):
[http://www.nvidia.com/object/linux-display-ia32-195.36.24.html]("http://www.nvidia.com/object/linux-display-ia32-195.36.24.html")

---

### Post by gnilreps on 2010-05-04
The 330M does appear however in the 64 bit driver list!

---

### Post by ysuenaga on 2010-05-04
i have to same problem too. no matter which resolution i set it to, it displays bigger than the screen. i have the Sony Vaio F series with Intel i7 processor and Nvidia GeForce GT 330M and and when i install the driver for the video card, it just messes up the whole display. After the restart, the resolution is stuck on 800x600. its usable but i want to make use of my native resolution which is 1920x108o.

---

### Post by TheRawGod on 2010-05-04
Hi all,

I had the same problem on my Sony Vaio F series once I upgraded to the new kernel, shipped with Lucid, even prior to Lucid was released.

I managed to fix it.

What I found was that Lucid's kernel (I believe all >= 2.6.32 kernels) has built-in driver for nvidia, called "nouveau". This one is built right into initrd image and is the one that causes the workspace to be bigger than the actual screen.

Naturally I though of installing invidia drivers instead of nouveau, but that wasn't easy. I couldn't unload nouveau in any way (I believe because it's built-in and not shipped as module) and with nouveau loaded nvidia's installer would fail.

So what I had to do first, was to disable the nouveau driver. I did it by putting the following parameter to [FONT="Courier New"]/etc/default/grub: GRUB_CMDLINE_LINUX="nouveau.modeset=0"[/FONT]. Then I had to invoke [FONT="Courier New"]sudo update-grub[/FONT].

Having added this parameter, I rebooted and got 800x600 resolution, bacause now there was no driver in kernel to support the 330M GPU (but naughty nouveau was finally gone!). Switching to command--line mode by "[FONT="Courier New"]sudo service gdm stop[/FONT]" and by installing nvidia latest drivers (195.36.24) I almost got it done, but, not yet. Original nvidia driver loaded, but failed to correctly draw anything on the screen. 

After searching a bit I found on the page linked in the bottom of this post that Sony Vaio F's LCD panel EDID isn't recognized by nvidia drivers automatically, so you have to "help" drivers in this matter: after finishing installing nvidia drivers (and before the reboot) you have to add the following lines to "Device" section of xorg.conf:

```

Option         "ConnectedMonitor" "DFP-0"
Option         "CustomEDID" "DFP-0: /proc/acpi/video/NGFX/LCD/EDID"

```

and only then reboot. You'll be happy to see log--in screen in fullhd! :)

NVidia's driver still behaves strangely on my Sony (no sound over HDMI, poorly working display backlight settings, no ability to switch to text mode via CTRL-ALT-N (1--6)), but general functionality is ok, including native fullhd desktop resolution, 3d acceleration etc.

PS A lot of Sony-Vaio F Series related problems in Linux are discussed here: [http://code.google.com/p/vaio-f11-linux]("http://code.google.com/p/vaio-f11-linux")

---

### Post by guiyti on 2010-05-05
Thanks

TheRawGod....

you saved my life!

thanks thanks thanks

---

### Post by skookiesprite on 2010-05-17
Raw God: you rule. I've been working tirelessly on this problem for about a week and a half now and would never have fixed it without your AWESOME (noob-ified - to read: right at my reading level) instructions. I wish this thread were more visible for user of the vaio f11 series with the nvidia display problem (nothing like a good old fashioned display problem that's multi-layered - ie: xorg.conf editing to get the drivers to see the lcd, the removal of the integrated neaveau drivers to make way for the demi-functional 195.36.24), and the spurious (and ancient) comments and info from other users utilizing older software... How can we make your solution more visible? It will save peeps TONS of time... VAIO F11 NVIDIA display problems in ubuntu lynx 64? Something... because your instructions were the only things that got it done for me. The whole counter-intuitive "do this before you reboot" seems to be one of the areas where I went wrong on my own. Anyway, thank you thank you thank you.

Cheers!

---

### Post by TheRawGod on 2010-05-17
You're all welcome!

I've spent myself quite a lot of time trying to find information on how to fix those issues, along with conducting lots of experiments before I got it working, so I'm really glad that my efforts appeared to be useful for others.

As I have written above, you may find reasonable to track changes on these threads: [http://code.google.com/p/vaio-f11-linux/]("http://code.google.com/p/vaio-f11-linux/"). They're updated more or less rapidly and cover most of problematic areas of vaio F + ubuntu integration. Doing so you may expect to be "on the edge", until some time when everything finally starts working as expected :)

---

### Post by fitzdragon on 2010-05-18
> **TheRawGod said:**
> Hi all,

I had the same problem on my Sony Vaio F series once I upgraded to the new kernel, shipped with Lucid, even prior to Lucid was released.

I managed to fix it.

What I found was that Lucid's kernel (I believe all >= 2.6.32 kernels) has built-in driver for nvidia, called "nouveau". This one is built right into initrd image and is the one that causes the workspace to be bigger than the actual screen.

Naturally I though of installing invidia drivers instead of nouveau, but that wasn't easy. I couldn't unload nouveau in any way (I believe because it's built-in and not shipped as module) and with nouveau loaded nvidia's installer would fail.

So what I had to do first, was to disable the nouveau driver. I did it by putting the following parameter to [FONT="Courier New"]/etc/default/grub: GRUB_CMDLINE_LINUX="nouveau.modeset=0"[/FONT]. Then I had to invoke [FONT="Courier New"]sudo update-grub[/FONT].

Having added this parameter, I rebooted and got 800x600 resolution, bacause now there was no driver in kernel to support the 330M GPU (but naughty nouveau was finally gone!). Switching to command--line mode by "[FONT="Courier New"]sudo service gdm stop[/FONT]" and by installing nvidia latest drivers (195.36.24) I almost got it done, but, not yet. Original nvidia driver loaded, but failed to correctly draw anything on the screen. 

After searching a bit I found on the page linked in the bottom of this post that Sony Vaio F's LCD panel EDID isn't recognized by nvidia drivers automatically, so you have to "help" drivers in this matter: after finishing installing nvidia drivers (and before the reboot) you have to add the following lines to "Device" section of xorg.conf:

```

Option         "ConnectedMonitor" "DFP-0"
Option         "CustomEDID" "DFP-0: /proc/acpi/video/NGFX/LCD/EDID"

```

and only then reboot. You'll be happy to see log--in screen in fullhd! :)

NVidia's driver still behaves strangely on my Sony (no sound over HDMI, poorly working display backlight settings, no ability to switch to text mode via CTRL-ALT-N (1--6)), but general functionality is ok, including native fullhd desktop resolution, 3d acceleration etc.

PS A lot of Sony-Vaio F Series related problems in Linux are discussed here: [http://code.google.com/p/vaio-f11-linux]("http://code.google.com/p/vaio-f11-linux")

worked perfectly for me , thank you so much

---

### Post by rax_m on 2010-05-20
Hi 

Do any of you guys experience the following issue on their vaio F11?

[http://code.google.com/p/vaio-f11-linux/issues/detail?id=18](http://code.google.com/p/vaio-f11-linux/issues/detail?id=18)

Thanks
Rax

---

### Post by const451 on 2010-05-20
Thank you very much - it worked!!!!

Quick question: did I have to disable  nouveau driver in grub or setting nvidia in blackmail list as described on [vaio-f11-linux]("http://code.google.com/p/vaio-f11-linux/") google group was sufficient?

Thank you again!

---

### Post by TheRawGod on 2010-05-21
> **const451 said:**
> 
Quick question: did I have to disable  nouveau driver in grub or setting nvidia in blackmail list as described on [vaio-f11-linux]("http://code.google.com/p/vaio-f11-linux/") google group was sufficient?


I'm not sure which way is "cleaner", maybe someone else can provide more info on that.
In the end both approaches do the same thing: prohibit nouveau to load, so you should be ok with any way of doing that.

---

### Post by TheRawGod on 2010-05-21
> **rax_m said:**
> Hi 

Do any of you guys experience the following issue on their vaio F11?

[http://code.google.com/p/vaio-f11-linux/issues/detail?id=18](http://code.google.com/p/vaio-f11-linux/issues/detail?id=18)

Thanks
Rax

Yes, I do.

---

### Post by rax_m on 2010-05-21
> **TheRawGod said:**
> Yes, I do.

Thanks.. at least I'm not the only one! ;) 

Any ideas on how to start debugging this? I'd like to provide useful info to someone to help fix this. :confused:

---

### Post by TheRawGod on 2010-05-21
> **rax_m said:**
> Thanks.. at least I'm not the only one! ;) 
Any ideas on how to start debugging this? I'd like to provide useful info to someone to help fix this. :confused:

I ha no idea how to start debugging it but I believe this has something to do with how brightness is manipulated. So I'd pay attention to understanding how brightness is working in Win7 for the same laptop.

---

### Post by const451 on 2010-05-21
This morning I installed the updates from Ubuntu and ... my monitor was back to 800 x 600. 

The good thing it did not install back the neuveur (sp) driver however it removed NVIDIA proprietary driver. I reinstall the driver and it's back to normal. During the installation, though, it said that the driver was already intalled but I proceeded to uninstall and install. Since the driver was there it was probably just the matter of setting some flag to make it work instead of whole reinstall. 

So, the question is, next time I apply the updates from Ubuntu what would the easiest way to fix the monitor?

---

### Post by TheRawGod on 2010-05-21
> **const451 said:**
> This morning I installed the updates from Ubuntu and ... my monitor was back to 800 x 600. 
[...]
So, the question is, next time I apply the updates from Ubuntu what would the easiest way to fix the monitor?

Probably while updating Ubuntu you also updated the kernel. Proprietary nvidia driver builds special kernel module which is dependent on kernel version. Therefore each time you update the kernel, you'll probably have to re--install the driver which will rebuild the module (or somehow rebuild the module without reinstalling the whole driver, if it's possible, which I'm not sure about).

Anyway, once you know why it happens it shouldn't be a big deal, should it?

---

### Post by const451 on 2010-05-21
I see, thanks, I'll keep reinstalling I guess until I get better with the whole Linux thing.

---

### Post by Vinnare on 2010-05-23
> **TheRawGod said:**
> Hi all,

So what I had to do first, was to disable the nouveau driver. I did it by putting the following parameter to [FONT=Courier New]/etc/default/grub: GRUB_CMDLINE_LINUX="nouveau.modeset=0"[/FONT]. Then I had to invoke [FONT=Courier New]sudo update-grub[/FONT]. 

After this when I rebooted then the laptop didn't boot to 800x600 but default 1200 x 760. And then the following command "[FONT=Courier New]sudo service gdm stop[/FONT]" did something that I couldn't understand. (It went to a screen with certain checks done and [OK] written after that, I couldn't type anything there, neither escape worked.) I'm new to Linux so the only way out I knew was to use the power switch:(. I've even downloaded the drivers from nvidia's site but I don't know how to install them! The .run file doesn't run on its own!!!

> 
Having added this parameter, I rebooted and got 800x600 resolution, bacause now there was no driver in kernel to support the 330M GPU (but naughty nouveau was finally gone!). Switching to command--line mode by "[FONT=Courier New]sudo service gdm stop[/FONT]" and by installing nvidia latest drivers (195.36.24) I almost got it done, but, not yet. Original nvidia driver loaded, but failed to correctly draw anything on the screen. 

After searching a bit I found on the page linked in the bottom of this post that Sony Vaio F's LCD panel EDID isn't recognized by nvidia drivers automatically, so you have to "help" drivers in this matter: after finishing installing nvidia drivers (and before the reboot) you have to add the following lines to "Device" section of xorg.conf:

I don't have a file named xorg.conf but one named xorg.conf.failsafe

> 

```

Option         "ConnectedMonitor" "DFP-0"
Option         "CustomEDID" "DFP-0: /proc/acpi/video/NGFX/LCD/EDID"

```and only then reboot. You'll be happy to see log--in screen in fullhd! :)

NVidia's driver still behaves strangely on my Sony (no sound over HDMI, poorly working display backlight settings, no ability to switch to text mode via CTRL-ALT-N (1--6)), but general functionality is ok, including native fullhd desktop resolution, 3d acceleration etc.

PS A lot of Sony-Vaio F Series related problems in Linux are discussed here: [http://code.google.com/p/vaio-f11-linux](http://code.google.com/p/vaio-f11-linux)

**I have Sony CW26FG with the same GPU- GT330M.**

---

### Post by const451 on 2010-05-24
Here you go:

**[SIZE=3][B][Howto install nVIDIA drivers  manually on Ubuntu 10.04 (Lucid Lynx)]("http://www.ubuntugeek.com/howto-install-nvidia-drivers-manually-on-ubuntu-10-04-lucid-lynx.html")**[/SIZE][/B]

Those instructions are missing a step, you have to stop a gdm service before installling nvidia drivers: sudo service gdm stop


I am new too - started with Linux a few days ago - those instructions worked for me.

---

### Post by const451 on 2010-05-24
When you manually install NVIDIA driver it will create xorg.conf file for you, then you'll have to edit it.

---

### Post by manas0185 on 2010-05-26
awesome thread guys!!! I was having the same trouble with my Ubuntu installation.

Also I realized that the two device options are the most critical to get the display working. So you need not uninstall nouveau drivers... just enable the nvidia  drivers, reboot and when you get that messed up 800X600 resolution, add the two options under device section and reboot again. 
this fixes everything :guitar::guitar:

---

### Post by TheRawGod on 2010-05-27
Hi,

> **manas0185 said:**
> 
[...]
So you need not uninstall nouveau drivers... just enable the nvidia  drivers, reboot and when you get that messed up 800X600 resolution, add the two options under device section and reboot again. 
this fixes everything :guitar::guitar:


The problem is that you can't install proprietary nvidia driver if nouveau is loaded (installer fails). I'm not sure what happens if to install .deb nvidia driver from ubuntu repos, but it may disable nouveau itself, so you don't need to do it manually.

---

### Post by kyanar on 2010-05-27
> **TheRawGod said:**
> 

 so you have to "help" drivers in this matter: after finishing installing nvidia drivers (and before the reboot) you have to add the following lines to "Device" section of xorg.conf:



How do i open that file from command line mode??

Thanks

---

### Post by TheRawGod on 2010-05-27
> **kyanar said:**
> How do i open that file from command line mode??
Thanks

Don't get me wrong, but this is a bit off--topic.

You can use any editor you like, you'd likely have vi installed already. So execute ```
sudo vi /etc/X11/xorg.conf
```

Alternativley, first install midnight commander (mc), and use its built-in editor (via F4).

Or use any other editor available out there, like emacs etc.

---

### Post by ironvital on 2010-05-29
Hi guys:)

> **TheRawGod said:**
> Hi,



The problem is that you can't install proprietary nvidia driver if nouveau is loaded (installer fails). I'm not sure what happens if to install .deb nvidia driver from ubuntu repos, but it may disable nouveau itself, so you don't need to do it manually.

I think I found a way to do that even if nouveau is loaded.
Just right click on desktop, go to Change Desktop Background.
Then click Visual Effects and choose Extra.
This will actually download and install nvidia driver.
When you reboot you will get 800x600.
then you add options to xorg.conf and everything works:)

Thanks:)

---

### Post by youWho on 2010-05-30
[SIZE=2]Hi all. I'm absolutely new here, and new to posting...  hopefully this'll end up in an appropriate place.

I wanted to  describe my experience in getting the display on a new Vaio VPCF116FX  working properly, in case it's helpful to others. I might add that I  decided to try setting up a dual boot scenario of Ubuntu and Windows 7  (though I'll probably never use Windows ;-) ).

Getting the  display to work meant, as far as I understood it, basically 4 things:
-  getting an "EDID" file for the display and putting it somewhere  specific
[/SIZE][SIZE=2]- installing a recent nVidia driver
[/SIZE][SIZE=2]- configuring
- editing xorg.conf to refer to the above  mentioned EDID file

The problem (as I found out the hard way) is  that it can happen that you for example download the newest driver, then  delete all previous nVidia drivers from your system, then can't get the  new one working right. And you end up with a totally non-functioning  display. So the 2nd time around (I ended up reinstalling Ubuntu and  starting over) I instead went to the "System" menu ->  "Administration" -> "Hardware Drivers"; this invoked a gui driver  installer that handled all of the details of getting the driver and  installing it, which I think was the key to everything working in my  case. But I should describe this in a step by step fashion I suppose:

1.  Get an "EDID" file. If you're dual booting with Windows then you can follow the tip  kindly posted by ilfuca here:
[http://forum.notebookreview.com/5820189-post2517.html](http://forum.notebookreview.com/5820189-post2517.html)
Basically, in Windows, you go to the tucows website ([www.tucows.com]("http://www.tucows.com")) find and download a  freeware utility called "Phoenix EDID Designer" and use it to first  extract from Windows, then export in a format Ubuntu can use, an "EDID"  file, which as I understand it essentially describes your display.  Sorry, but if you don't have access to Windows (and who can blame you)  then I don't know where to find this EDID file. Assuming you can get  that essential file, then you should put it someplace---I don't  think it exactly matters where, but an appropriate place to put it would  seem to be in /etc/X11/ (that's where I put mine). Please note that in  the course of getting that EDID file you'll have a chance to name it any  way you like (so long as the file type is "raw" and the name therefor  ends in ".raw") [edit: actually I don't think it matters if the name has that extension.]

2. Use the above mentioned  System->Administration->Hardware Drivers approach to getting and  installing the appropriate nVidia drivers!!! Unless you're either a  Linux expert or a glutton for punishment then I don't know why you'd  want to go about this in any more roundabout way; the "hardware Drivers"  installer thing works fine, and I think more importantly, it's going to  install a driver that's tested, possibly tweaked, and known to work.  Also it'll handle the installation process correctly.

3. Then  you'll need to restart the computer, and when it restarts you'll face a  terribly low resolution display, possibly one that is hardly even usable  (if that happens I can only say that you should patiently try  restarting and futzing until you get at least a usable display---though  it'll still be low resolution). Next you need to run in a  terminal this command:

 sudo nvidia-xconfig

This should, among other things, *create* a file called xorg.conf in /etc/X11, in other words  it'll create /etc/X11/xorg.conf.

4. You should now *as root* open  that xorg.conf file for editing, for example like so from a terminal:

sudo  gedit  /etc/X11/xorg.conf

In that file you'll find a section called  "Device". Add the following lines to that section (I put them at the end  of the section, right before "EndSection"):

    Option          "ConnectedMonitor" "DFP-0"
    Option         "CustomEDID"  "DFP-0:PATH_TO_YOUR_EDID_FILE"

replacing [/SIZE][SIZE=2]"PATH_TO_YOUR_EDID_FILE[/SIZE][SIZE=2]" with the path (with the filename you chose) to your EDID  file of course, so that line would look something like for example:
[/SIZE][SIZE=2]    Option         "CustomEDID"  "DFP-0:[/SIZE][SIZE=2]/etc/X11/sonyEdid.raw"
Save the changes.

Restart  the computer and you should have a fully working display.
[/SIZE]

---

### Post by youWho on 2010-05-30
I'm sorry, I forgot to say (in connection with my previous post about how I got the display working) that I'm using Ubuntu 10.4 Lucid, 64 bit.

---

### Post by youWho on 2010-05-30
One more thought re getting the display to work. In case you are searching for the elusive EDID file, I see that there's one here:

/proc/acpi/video/NGFX/LCD/EDID

*BUT* to be honest I have a hunch that that wasn't there before; that is, I *think* it might be that it was created by the system. I have no idea now whether this is so!!! In any case if you're looking for an EDID file to use in getting your display to work please check and see if there's already one there. If so then you could presumably not bother extracting one from Windows. If you use that one then I'd say the corresponding line that you're adding to xorg.conf would look like:

[SIZE=3]     Option         "CustomEDID"  "DFP-0:/proc/acpi/video/NGFX/LCD/EDID"[/SIZE]

[Edited] I've since learned (I think ;-) ) that the /proc filesystem is a kind of virtual file system, actually being data offered by the kernel. Probably you'll find an edid "file" "there"---you can try it---if no success then you might have to try the exporting from Windows method.

---

### Post by davoudi on 2010-05-31
Nah, it is not working here or I am missing something.

---

### Post by davoudi on 2010-05-31
Oh yeah. I install the new version of driver and everything is fine now. Thanks.

---

### Post by Burfee on 2010-06-17
managed to fix this problem by adding
```
blacklist vga16fb
blacklist nouveau
blacklist rivafb
blacklist nvidiafb
blacklist rivatv
```

to /etc/modprobe.d/blacklist.conf

thanks to [this page]("http://www.ubuntugeek.com/howto-install-nvidia-drivers-manually-on-ubuntu-10-04-lucid-lynx.html")

---

### Post by Pim. on 2010-07-03
I'm kicking an old thread but i to need some help.

I did everything in this post: [http://ubuntuforums.org/showpost.php?p=9234321&postcount=7](http://ubuntuforums.org/showpost.php?p=9234321&postcount=7) and blacklisted the modules in the post above as well so i did:


Changed the /etc/default/grub line into: 
GRUB_CMDLINE_LINUX="i8042.nopnp i915.modeset=0 nouveau.modeset=0"

Changed teh /etc/modprobe/blacklist.conf and added:
blacklist vga16fb
blacklist nouveau
blacklist rivafb
blacklist nvidiafb
blacklist rivatv

downloaded a few nvidia drivers and installed them in text mode

Nothing worked ! 

What i haven't done yet:

edit the xorg.conf device section.
Find a EDID that goes with the monitor, the EDID made by the nvidia drivers just says: <not supported>


When i boot the laptop i get the error that no driver is found and ubuntu goed into 'vesa mode' 

My xorg is now:

> 
# nvidia-xconfig: X configuration file generated by nvidia-xconfig
# nvidia-xconfig:  version 256.35  (buildmeister@builder97.nvidia.com)  Wed Jun 16 19:15:05 PDT 2010


Section "ServerLayout"
    Identifier     "Layout0"
    Screen      0  "Screen0" 0 0
    InputDevice    "Keyboard0" "CoreKeyboard"
    InputDevice    "Mouse0" "CorePointer"
EndSection

Section "Module"
    Load           "glx"
EndSection

Section "InputDevice"
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
    Identifier     "Monitor0"
    VendorName     "Unknown"
    ModelName      "Unknown"
    HorizSync       28.0 - 33.0
    VertRefresh     43.0 - 72.0
    Option         "DPMS"
EndSection

Section "Device"
    Identifier     "Device0"
    Driver         "nvidia"
    VendorName     "NVIDIA Corporation"
EndSection

Section "Screen"
    Identifier     "Screen0"
    Device         "Device0"
    Monitor        "Monitor0"
    DefaultDepth    24
    Option         "NoLogo" "True"
    SubSection     "Display"
        Depth       24
    EndSubSection
EndSection
Hell, i even tried to patch the kernel as i read somewhere but after three days working i would like to find the magic bullet !

thanks


edit, dmesg says:

> 
root@narf:~# dmesg | grep nvidia
[   11.114500] nvidia: module license 'NVIDIA' taints kernel.
[   13.334185] nvidia 0000:01:00.0: power state changed by ACPI to D0
[   13.334244] nvidia 0000:01:00.0: power state changed by ACPI to D0
[   13.334255] nvidia 0000:01:00.0: enabling device (0000 -> 0003)
[   13.334266] nvidia 0000:01:00.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[   13.334276] nvidia 0000:01:00.0: setting latency timer to 64


edit again:

Xorg.0.log says:

> 
[    13.519] (--) PCI: (**0:1:0:0**) 10de:0a2b:104d:905a nVidia Corporation GT216 [GeForce GT 330M] rev 162, Mem @ 0xd0000000/16777216, 0xa0000000/268435456, 0xb0000000/33554432, I/O @ 0x00006000/128, BIOS @ 0x????????/524288

[    13.502] (--) PCI:*(**0:0:2:0**) 8086:0046:104d:905a Intel Corporation Core Processor Integrated Graphics Controller rev 2, Mem @ 0xd1400000/4194304, 0xc0000000/268435456, I/O @ 0x00007078/8
**[    13.750] (II) Primary Device is: PCI 00@00:02:0**



[    13.709] (II) Loading /usr/lib/xorg/modules/drivers/nvidia_drv.so
[    13.731] (II) Module nvidia: vendor="NVIDIA Corporation"
[    13.732]     compiled for 4.0.2, module version = 1.0.0
[    13.732]     Module class: X.Org Video Driver
[    13.744] (II) NVIDIA dlloader X Driver  256.35  Wed Jun 16 18:45:02 PDT 2010
[    13.744] (II) NVIDIA Unified Driver for all Supported NVIDIA GPUs
[    13.744] (++) using VT number 7

[    13.750] (II) Primary Device is: PCI 00@00:02:0
[B][    13.750] (EE) No devices detected.
[    13.750] 
Fatal server error:
[    13.750] no screens found
[/B]




---

### Post by Pim. on 2010-07-04
OK, I have been at this for 3 days now and i'm quit annoyed at Sony. If this machine didn't cost so much i would have broken it in two by now.

I'm tired, frustrated and seriously thinking of going back to Windows. What a mess.... 

Why does everybody have a filled EDID file in /proc and all i see is:

root@narf:~# cat /proc/acpi/video/**GFX0**/LCD/EDID 
<not supported>


I really hope someone can give me a hint because i need to work on this laptop as well and i can't stay fumbling around at this !

---

### Post by Pim. on 2010-07-04
I managed to get the nvidia card working by install the RT kernel (incl, headers and source) NOW MY WIFI IS DISABLED


oh sweet :(

---

### Post by youWho on 2010-07-04
> **Pim. said:**
> OK, I have been at this for 3 days now and i'm quit annoyed at Sony. If this machine didn't cost so much i would have broken it in two by now.

I'm tired, frustrated and seriously thinking of going back to Windows. What a mess.... 

Why does everybody have a filled EDID file in /proc and all i see is:

root@narf:~# cat /proc/acpi/video/**GFX0**/LCD/EDID 
<not supported>


I really hope someone can give me a hint because i need to work on this laptop as well and i can't stay fumbling around at this !

I'm new to Ubuntu too, but I had this problem and found a solution. To be honest I had a couple of false starts because I had tried to "upgrade" to Ubuntu Studio, and in the process lost the display. I don't know why that happened, but in the end I started over and installed then Ubuntu Studio from the DVD. ***I don't think the fact that my display is now working has anything to do with whether Ubuntu Studio is installed or plain ol' Ubuntu!!! What does matter, I think, is that the installation of the nVidia driver has to be done *after* you install Ubuntu (actually after you install the kernel---for most of us that means after we install the system as a whole). I believe that the nVidia driver has settings specific to the way the kernel is configured.*** In my opinion this is one of the main arguments in favor of using the System->Administration->Hardware Drivers menu item: it not only handles choosing exactly the right driver (settings???), it also handles any disabling of nouveau, etc.

But remember that you also have to do, in Terminal, after you install the driver:

sudo nvidia-xconfig

and then edit as root /etc/X11/xorg.conf

But after all you say you've gone through you might have to start over and install Ubuntu from scratch, then go step by step and get the display working. As I say I never got my display working when I had installed one kernel, then switched to another (which happened when I tried to install the Ubuntu Studio things after the display had been working). Even when I uninstalled and reinstalled it never worked. What fixed it was starting with the kernel that I wanted to end up using and just sticking with that one (even now if I boot into another kernel the display won't work properly, though for me now that isn't an issue).

Perhaps this helps???

---

### Post by youWho on 2010-07-04
> **Pim. said:**
> 
Why does everybody have a filled EDID file in /proc and all i see is:

root@narf:~# cat /proc/acpi/video/**GFX0**/LCD/EDID 
<not supported>

I really hope someone can give me a hint because i need to work on this laptop as well and i can't stay fumbling around at this !

If you have access to Windows, which it sounds like you have, you can follow the tips posted up above that tell how to extract/export an EDID file from Windows, though I would first try editing /etc/X11/xorg.conf to point to one that's "located in" /proc.

---

### Post by omarlekphet on 2010-07-14
I Did like you Said 

Option "ConnectedMonitor blaba
OPtion "custom Bla bla 

I can't give you the right sentence because i don't remember

after i add those two lines it boot and then the Screen turn to White with black color in stripes background

please help me

Thank you

---

### Post by omarlekphet on 2010-07-14
I Did like you Said 



I can't give you the right sentence because i don't remember

after i add those two lines it boot and then the Screen turn to White  with black color in stripes background

please help me

Thank you

---

### Post by Loksta on 2010-07-17
Thank you so much for this VERY HELPFUL information. I got it going thanks to this thread.

---

### Post by youWho on 2010-08-02
> **omarlekphet said:**
> I Did like you Said 



I can't give you the right sentence because i don't remember

after i add those two lines it boot and then the Screen turn to White  with black color in stripes background

please help me

Thank you


Sorry for the delayed reply; perhaps you've gotten it to work in the meantime, but if not then I'll try to help *but* unfortunately I won't be in a position to offer much because I'm fully new to Ubuntu, and I don't actually know what went wrong in your installation. Anyway I'll post some thoughts here in case it's at least helpful...

For one thing, I can tell you that I too had what sounds like that symptom when I was trying first to get the nvidia driver installed. Unfortunately I now don't remember(!) exactly when I had that symptom, nor what I did to solve it!! Probably what I did was basically to start over. If you are able to read this, and if you were starting with a fresh installation of Ubuntu when you got into that jam then my opinion would be to start over would likely in the end be less trouble than trying to fix what's wrong now. You might not agree---nor be in a position to start from scratch---and if not then hopefully you can find a different solution---perhaps somebody here who knows more can post some helpful thoughts...

What I think happened to you though was that you lost the use of every graphics driver on your system. WHen I used the "Hardware Drivers" menu item I never had to do any sort of disabling of nouveau; I assume that that was done by the installer of the driver (if necessary).

You could try booting from the installation disc and seeing if you can either delete the xorg.conf file or actually I would try first editing it. One way or another you might be able to get to where you can at least have a low res display, from which you could try to fix the problem.

Hmm. I'm sorry but I guess I don't have much to offer in the way of help. If I think of anything I'll post again though.

Anybody else...???

---

### Post by alessandro_ufms on 2010-08-03
Hot news: 256.44 driver fixed the issue with detection screen. :D

---

### Post by gianluca.pettinello on 2010-08-08
For people with vaio f11 laptop, as I am, I suggest to look google vaio f11 linux, there is a project with all the tips to make linux and therefore ubuntu to work on this marvellous laptop

Gianluca

---

### Post by furi981 on 2010-10-12
Hi to all

I've been looking for a solution for my VGA blank screen after installing Ubuntu 10.10

all posts lead me to no where

i found the solution myself and it was easy

This type of Sony laptop is designed for 64X so i installed Ubuntu 64 X then i installed Nvidia drver from the orginal website and installed it , and everything worked fine

PS i edited the GRUB by adding nomodeset in the boot

Thanks 
hope it work with you

Firas

---

### Post by vmforno on 2010-10-19
If you wanna use the nVidia proprietary driver with 10.10 x64, you should use version 256.53
 
The current version 260.19.12 (Oct 2010) will leave you on a blank screen.

The current steps, I've taken on my laptop Sony CW27FX (i5, 4 GB RAM, nVidia GT330M):

```

sudo apt-get --purge remove nvidia*
sudo apt-get install binutils gcc
sh NVIDIA-Linux-x86_64-256.53.run

```

The first command uninstalled every nvidia package installed with your distro (nvidia-96, nvidia-173, etc). 
Explanation: if you try the nVidia installer it will halt with a error message because there is a small piece of code (script) one some of these packages.

The 2nd will install binutils and gcc. 
Explanation: They are required by the nVidia installer

The 3rd. will install the driver.

Regards,
vm

---

### Post by simar.mohar on 2010-10-20
> **vmforno said:**
> If you wanna use the nVidia proprietary driver with 10.10 x64, you should use version 256.53
 
The current version 260.19.12 (Oct 2010) will leave you on a blank screen.

The current steps, I've taken on my laptop Sony CW27FX (i5, 4 GB RAM, nVidia GT330M):

```

sudo apt-get --purge remove nvidia*
sudo apt-get install binutils gcc
sh NVIDIA-Linux-x86_64-256.53.run

```The first command uninstalled every nvidia package installed with your distro (nvidia-96, nvidia-173, etc). 
Explanation: if you try the nVidia installer it will halt with a error message because there is a small piece of code (script) one some of these packages.

The 2nd will install binutils and gcc. 
Explanation: They are required by the nVidia installer

The 3rd. will install the driver.

Regards,
vm

Wow! worderful
Thanks for the solution..
I had been searching this for past five hours without success.
Isn't it work for i386 32 bit version of maverick ubuntu (10.10)

---

### Post by Iksf on 2010-10-26
Deb of those drivers for 64

[http://dl.dropbox.com/u/737114/vpcs11e7e/nvidia-current_256.53-0ubuntu3_amd64.deb](http://dl.dropbox.com/u/737114/vpcs11e7e/nvidia-current_256.53-0ubuntu3_amd64.deb)

---

### Post by waqar.hameed08 on 2010-10-28
> **vmforno said:**
> If you wanna use the nVidia proprietary driver with 10.10 x64, you should use version 256.53
 
The current version 260.19.12 (Oct 2010) will leave you on a blank screen.

The current steps, I've taken on my laptop Sony CW27FX (i5, 4 GB RAM, nVidia GT330M):

```

sudo apt-get --purge remove nvidia*
sudo apt-get install binutils gcc
sh NVIDIA-Linux-x86_64-256.53.run

```The first command uninstalled every nvidia package installed with your distro (nvidia-96, nvidia-173, etc). 
Explanation: if you try the nVidia installer it will halt with a error message because there is a small piece of code (script) one some of these packages.

The 2nd will install binutils and gcc. 
Explanation: They are required by the nVidia installer

The 3rd. will install the driver.

Regards,
vm

wow! worked perfectly! Ubuntu 10.10 64-bit with NVIDIA 330M ... thnx

---

### Post by nism0o on 2010-10-28
You do not appear to be using the NVIDIA X driver.  Please edit your X configuration file (just run `nvidia-xconfig` as root), and restart the X server.

I got this message. How do i do it? Never tried linux before :\ the driver are active but not in use.

---

### Post by simar.mohar on 2010-10-29
Isn't the above solution works for 32 bit also?

---

### Post by simar.mohar on 2010-10-29
My computer works absolutely fine with linux kernel [http://kernel.ubuntu.com/~kernel-ppa/mainline/daily/2010-10-27-maverick/](http://kernel.ubuntu.com/~kernel-ppa/mainline/daily/2010-10-27-maverick/) without adding nomodeset in boot parameters

---

### Post by youWho on 2011-01-18
> **vmforno said:**
> If you wanna use the nVidia proprietary driver with 10.10 x64, you should use version 256.53
 
The current version 260.19.12 (Oct 2010) will leave you on a blank screen.

The current steps, I've taken on my laptop Sony CW27FX (i5, 4 GB RAM, nvidia GeForce GT 330M):

```

sudo apt-get --purge remove nvidia*
sudo apt-get install binutils gcc
sh NVIDIA-Linux-x86_64-256.53.run

```The first command uninstalled every nvidia package installed with your distro (nvidia-96, nvidia-173, etc). 
Explanation: if you try the nVidia installer it will halt with a error message because there is a small piece of code (script) one some of these packages.

The 2nd will install binutils and gcc. 
Explanation: They are required by the nVidia installer

The 3rd. will install the driver.

Regards,
vm

Thank you so much for the tip. That worked.

If it helps though I should note a few things here that seemed to be necessary in my case (a Sony Vaio VPCF116FX with an nvidia GT 330M, Ubuntu Studio Maverick freshly installed from DVD to a clean partition). The problem I had was that when I installed Ubuntu Studio, and then used the System->Administration->Additional Drivers menu item to install the current nvidia driver, when I rebooted all I ever got was a blank light purple screen, sometimes preceded by a sort of old fashioned looking Ubuntu logo and a row of dots, but always no working display no matter what I tried.

First I should say that I think many of us noobs don't know that in the grub menu at boot you can choose a "recovery" mode, after which you'll have the opportunity to boot into a "failsafe" display mode, which means you'll at least have a working if wrong and low res display.

Anyway, based on the tips here I went to nvidia's web site, found the downloads section for my computer, but didn't download the latest driver, instead I got the version mentioned above, version 256.53. I first uninstalled the nvidia drivers using System->Administration->Additional Drivers, just in case it might help. Then I also followed vmforno's advice for uninstalling from the command line. At the next command it turned out that I already had binutils and gcc, so no worries there. But then when trying to do sudo sh NVIDIA-Linux-x86_64-256.53.run the installer complained that I had to quit X and also to be in a different run level. To be honest I didn't take mental notes, so I'm not sure of the exact sequence, but essentially what I next did was to first follow the advice on nvidia's web site about  how to install---the main thing being that in order to disable nouveau I first created a small text file containing only the lines:

blacklist nouveau
options nouveau modeset=0

saving it as disable-nouveau.conf, then did chown for it to be owned by root:root, then moved it to /etc/modprobe.d/ (that is, you end up with /etc/modprobe.d/disable-nouveau.conf)

After that I think I basically restarted and got into a console style of login, where I ran 

sudo sh NVIDIA-Linux-x86_64-256.53.run

which worked. The display seems all good.

Thanks again everybody here.

---

### Post by ng0ofy on 2011-02-11
OK,*I*see*your*card*is*working*properly,*now.*My*card*worked*without*this*work*(above)*:popcorn:

BUT

What*can*I*do,*if*I*want*to*NOT*USE*the*NVIDIA*Card?*I*want*to*use*only*the*integrated*intel*i5*card*without*nvidia?*If*I*didn"t*install*nvidia*driver*the*ubuntu*doesn"t*use*the*card,*but*turn*it*on*and*the*card*use*power.*From*my*battery.*I*want*to*turn*it*on,*when*I*use*Ubuntu.

In*BIOS*I*have*options,*where*I*can*choose*wich*OP*can*switch*the*graphic*cards.*If*I*set*"Windows",*windows7*can*use*Optimus*and*Ubuntu*can"t*use*nvidia*card,*but*powered*it.*If*I*set*"Others"*windows7*doesn"t*see*any*cards*:confused:,*ubuntu*uses*nvidia!*

"Cheers,*than*your*ubuntu*is*very*nice*and*powerful!"*"Yes,*and*my*laptop*working*only*in*"desktop*mode"*and*I*can*code*in*C*or*java*in*beautiful*3D*Netbeans*:cool:".*However*in*windows**can"t*play*videos*or*games.*I*want*to*switch*it.

Sorry*for*the*crying...

---

### Post by pseudosmart on 2011-03-04
[SIZE=2]I’m completely new to Linux, and I had this same problem on my sony vaio with a GeForce 330M in 10.10, but I found another way to fix the problem before I found this thread. Every time I tried to install the 330M linux driver, I got a message that nouveau was running, and had to be stopped before I could install the nvidia driver. So the instructions I found online said to disable the nouveau driver with [FONT=monospace]'[/FONT]sudo apt-get --purge remove xserver-xorg-video-nouveau'. I was then able to install the proprietary driver for the 330M from nvidia’s website, and I also installed nvidia-settings with ‘sudo apt-get install nvidia-settings’ to control the screen resolution. But the problem I’m having now is that when I installed the updates, the GUI won’t launch at all, I could only access the command line after rebooting. The only thing I knew to do was to completely reinstall Ubuntu, go through the process of disabling nouveau and installing the right driver and nvidia-settings again, and just uninstalling the Update Manager so it wouldn’t notify my about updates that were going to wreck everything I did if I installed them.[/SIZE]
  
  [SIZE=2]Does anyone know if I follow the method described by TheRawGod, and added:[/SIZE]
   
  Option         "ConnectedMonitor" "DFP-0"Option         "CustomEDID" "DFP-0: /proc/acpi/video/NGFX/LCD/EDID"
   
  [SIZE=2][FONT=&quot]to the device section of my xorg.conf, if I would be able to install the updates from the Update Manager without all the problems it seems to cause? Thanks in advance for any help anyone can offer.[/FONT][/SIZE]

---

### Post by youWho on 2011-03-10
To pseudosmart:

I'm not an expert, but I think it's not necessary to remove [SIZE=2]nouveau. I believe it's sufficient to just blacklist it---and that only if you let's say "manually" install a [/SIZE][SIZE=2]proprietary[/SIZE][SIZE=2] nvidia driver. I am still happily using Lucid but also have on another partition, just because I'm noob and wanted to have at least a working everything during the transition, an install of Maverick.[/SIZE][SIZE=2] Anyway booting into maverick had left me with a blank screen, which I think by the way must certainly occur if an nvidia driver isn't working and [/SIZE][SIZE=2]nouveau isn't there at all. So I needed for that to get a slightly older driver from nvidia and install it from the command line. But to blacklist [/SIZE][SIZE=2]nouveau[/SIZE] create a text file containing only these 2  lines:

blacklist nouveau
options nouveau modeset=0

save it as disable-nouveau.conf, then chown it to be owned by   root:root, then move it to /etc/modprobe.d/ (that is, you end up with   /etc/modprobe.d/disable-nouveau.conf).
[SIZE=2]
But I've never had to do even that in Lucid (and I haven't tried recently, but this might be all solved in Maverick too by now (I've just been too busy to check)). Each time I've done a software update that includes a new kernel the display reverts to a low res mode, which I assume is a kind of minimum [/SIZE][SIZE=2]that's as broadly compatible as possible, from nouveau. After the update I simply use System->Administration->Hardware Drivers (I think this is a gui for "jockey") to first remove the proprietary nvidia driver, then re-install it. This seems to be required because the driver also needs to be updated, even though it's as if I'm just uninstalling and re-installing the same thing I had before. After that I still need to do 

sudo nvidia-xconfig

then edit the /etc/X11/xorg.conf file to include the lines that reference the EDID file, but so far that's always resulted in a working display (in Lucid).

Hopefully that helps somehow.
[/SIZE]

---

### Post by pseudosmart on 2011-03-10
Wow youWho, I did exactly what you said, and it worked perfectly. I can't thank you enough, that was so much simpler than the way I was trying to do it. Thanks again.

---

### Post by raj4483 on 2011-04-13
Hi,

My Laptop Sony VAIO model is VPCZ136GG. 

I installed Ubuntu 11.04 Beta.

Laptop Configuration:

Intel® Core&#8482; i5-580M Processor 2.66 GHz with Turbo Boost up to 3.33 GHz
HDD: SSD in 128 GB (64 GB x 2, Serial ATA)

NVIDIA® GeForce® GT 330M, Shader Model 4.1 graphics processor, offering  full compatibility with latest 3D games at high resolutions and fluid  frame rates. NVIDIA® CUDA&#8482; technology accelerates demanding system tasks  like video transcoding.

This laptop have 2 Graphics System

Graphics Accelerator NVIDIA® GeForce® GT 330M GPU(SPEED MODE) / Intel® HD Graphics(STAMINA MODE)

I downloaded driver from nvidia.com
Nvidia Driver version NVIDIA-Linux-x86_64-260.19.44.run and installed after reboot. I am getting blank screen. my Xorg log

:~# tail -f /var/log/Xorg.0.log
[     6.319] (EE) No drivers available.
[     6.319] 
Fatal server error:
[     6.319] no screens found
[     6.319] 
Please consult the The X.Org Foundation support 
     at [http://wiki.x.org]("http://wiki.x.org/")
 for help. 
[     6.319] Please also check the log file at "/var/log/Xorg.0.log" for additional information.
[     6.319]

Nvidia setting file

cat /etc/X11/xorg.conf
# nvidia-xconfig: X configuration file generated by nvidia-xconfig
# nvidia-xconfig:  version 260.19.44  (buildmeister@swio-display-x86-rhel47-08.nvidia.com)  Sun Feb 27 22:59:57 PST 2011

Section "ServerLayout"
    Identifier     "Layout0"
    Screen      0  "Screen0"
    InputDevice    "Keyboard0" "CoreKeyboard"
    InputDevice    "Mouse0" "CorePointer"
EndSection

Section "Files"
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
    Identifier     "Monitor0"
    VendorName     "Unknown"
    ModelName      "Unknown"
    HorizSync       28.0 - 33.0
    VertRefresh     43.0 - 72.0
    Option         "DPMS"
EndSection

Section "Device"
    Identifier     "Device0"
    Driver         "nvidia"
    VendorName     "NVIDIA Corporation"
EndSection

Section "Screen"
    Identifier     "Screen0"
    Device         "Device0"
    Monitor        "Monitor0"
    DefaultDepth    24
    SubSection     "Display"
        Depth       24
    EndSubSection
EndSection

Please help me

---

### Post by realzippy on 2011-04-13
seems as it is an Optimus laptop :
[http://ubuntuforums.org/showthread.php?p=10304516#post10304516](http://ubuntuforums.org/showthread.php?p=10304516#post10304516)

---

### Post by hitmyspot on 2011-04-13
Thanks everyone. I have been having problems for months. Abandoned 10.04 64bit and recently started trying again with 10.10.

Just to confirm, blacklisting nouveau and manual install of nvidia drivers has got my system working. I am running 10.10 32bit on a sony vaio vpcf116fg
:P

---

### Post by pseudosmart on 2011-04-13
hitmyspot, I had the exact same problem, and the same solution worked for me, but I'm on a different vaio model and it's 64bit. I was just curious, are you able to access the command line using ctrl+alt+<F1-F6>? My system is working great after blacklisting nouveau and manually installing the drivers, but I can't access my command line any more, and was wondering if you had the same issue?

---

