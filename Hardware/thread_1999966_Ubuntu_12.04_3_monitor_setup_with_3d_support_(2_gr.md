---
title: "Ubuntu 12.04 3 monitor setup with 3d support (2 graphics cards, no SLI)"
date: 2012-06-08
forum: Hardware
---

### Post by arjenzwerver on 2012-06-08
Hello everyone,

I've been looking for about 3 years to find a solution for working with 3 monitors with 3d hardware acceleration in ubuntu. And today I found the best solution, so I'd like to share it with you.

One possible solution is to disable twinview, run 3 seperate x-servers and combine them with Xinerama. The only problem is that compiz will not work and dragging windows from one screen to another can sometimes be buggy.

The solution I found was the next:

 [LIST=1]
[*]Remove your old xorg.conf
[*]Check what the addresses are for your monitors (You can check them in the NVIDIA X Server Settings), it should look like GPU-*.DFP-*
[*]Run the following command from a terminal:
[INDENT]```
sudo nvidia-xconfig --base-mosaic --metamodes="GPU-1.DFP-2: 1680x1050+0+0, GPU-0.DFP-0: 1920x1080+1680+0, GPU-0.DFP-2: 1680x1050+3600+0"
```[/INDENT]
In here you need to set the correct resolutions and positionings. (I had to start with position +0+0, otherwise it went wrong and my left monitor got cloned to my middle monitor)
[*]If you restart X now, everything will be working, but the screen has lots of lag (3 seconds in my case) which is pretty annoying.
[/LIST]

To fix the lag, you need to set a parameter in Grub2

[LIST=1]
[*]Edit /etc/default/grub
[INDENT]```
sudo vi /etc/default/grub
```[/INDENT]
[*]Look for GRUB_CMDLINE_LINUX_DEFAULT=
[*]Add "iommu=pt" to the string after the variable
[INDENT]It will look like:
[INDENT]GRUB_CMDLINE_LINUX_DEFAULT="quiet splash iommu=pt"[/INDENT][/INDENT]
[*]Now save the file and update your grub
[INDENT]```
sudo update-grub2
```[/INDENT]
[*]Now all you have to do is restart your machine and everything should be working!
[/LIST]

I hope I can help a lot of people with this solution. Let me know in the comments below if you have any problems.

---

### Post by Djesurun1 on 2012-06-10
Hi i have a post listed already but I am having a problem that I cannot find a solution to anywhere! I have 2 monitors and i am using Xinerama and for some reason I cannot get any 3d effects to work on my desktop. I am using Gnome and for some reason the hotspot in the top left corner doesnt activate. I dont' have any sort of dash whatsoever...just the applications and places tab on top. I'm using an older Nvidia geforce 210 card. When i check my system setting details it says I am in fallback mode. I don't understand why it wont boot into the regular 3d mode. Unity never seemed to have any eye candy either, which makes me thing i was always in 2d and didn't know it.

---

### Post by arjenzwerver on 2012-06-12
As far as I know Xinerama doesn't support a 3d desktop. You should use Twinview instead to create a multiple monitor desktop with 3d support, or try the solution above if you have multiple graphics cards.

---

### Post by forBiophysics on 2012-06-15
Arjenzwerver, I have also spent an obscene amount of time looking for a solution to the dualhead three monitor linux setup and have spent the last year with a half-baked setup involving two x-screens with twinview. I had almost given up until I ran into your post. I cannot thank you enough; you have made my week.

---

### Post by arjenzwerver on 2012-06-19
I'm glad tot hear that it helped! ;)

---

### Post by aerojh on 2012-06-21
Can I ask what card you're using?

I seem to have misread the documentation for BaseMosaic and thought it was a more general version of SLI Mosaic for nvidia cards, but it seems it's just Quadros and related cards.

---

### Post by arjenzwerver on 2012-06-26
I'm using 2x Nvidia GTX 560 Ti. SLI is not enabled in this configuration.

For SLI mosaic you need an NVIDIA Quadro graphics card which I don't have.

---

### Post by klumhru on 2012-09-01
Fantastic. I have 3head setups at work and at home, and this fixed them right up for me. Now I can use Gnome3, which I prefer to Unity.

Thank you!

---

### Post by homer007 on 2012-09-04
Thank you for posting this!  Works great!!!

3 monitor setup with full acceleration - Kubuntu 12.04 and 2 gtx 550ti's.

---

### Post by pseudonym404 on 2012-09-10
The iommu=pt option didn't help with me, as the iommu on my intel x58 board (shuttle sx58h7) isn't used.

Enabling it with intel_iommu=on leads to x locking up and vt switching not working when the nvidia module is loaded.

I'm not sure if this is the bios at fault (it seems to be doing something dodgy with the onboard audio and the iommu, although the workaround looks like it only affects the onboard audio) or the nvidia module, but either way enabling the iommu doesn't seem to be an option.

Also the 'lag' here was more like 20-30 seconds (gtx 295).

I figured out quite quickly that disabling composite at least got me a setup where xrandr knows what's going on with the 3 monitors (unlike xinerama, or using a triplehead2go).

I then eventually worked out that using xrender instead of opengl for compositing also works round the painful lag (in kubuntu at least). Some effects aren't available, but it looks a whole lot better than without.

Thanks for pointing me in the right direction with the basemosaic option! :)

---

### Post by mccann.matt on 2012-09-16
Thanks for this! Really a fantastic (and simple) fix.

It took me an unreasonable amount of time to track this down so for future Googlers, time to add some easier to find tags.

XINERAMA MULTI-MONITOR UBUNTU 12.04 FALLBACK MODE GNOME 3

---

### Post by poet_imp on 2012-10-02
Ok, I am not finding the same success that others are having here. Can one of you that have it working please post your working xorg.conf?

---

### Post by emiel1976 on 2012-10-15
I only get 2 screens working.

I have 2 Nvidia GTX 560 TI and 3 monitors.
 I added this because this is what it tells me how the monitors are called.

> sudo nvidia-xconfig --base-mosaic --metamodes="GPU-0.CRT-1: 1920x1080+0+0, GPU-0.DFP-0: 1920x1080+1920+0, GPU-1.DFP-0: 1920x1020+3840+0"

As I do thius in the Terminal I get this.

> emiel@Xubuntu-pc:~$ sudo nvidia-xconfig --base-mosaic --metamodes="GPU-0.CRT-1: 1920x1080+0+0, GPU-0.DFP-0: 1920x1080+1920+0, GPU-1.DFP-0: 1920x1020+3840+0"
[sudo] password for emiel: 

WARNING: Unable to locate/open X configuration file.

Option "BaseMosaic" "True" added to Screen "Screen0".
New X configuration file written to '/etc/X11/xorg.conf'

emiel@Xubuntu-pc:~$ 


Than as I reboot I get only one monitor and as I put that on I get only that one working but not the other monitor working.

I have after reboot only 2 monitors working.

THis is my xorg.conf file.

> # nvidia-xconfig: X configuration file generated by nvidia-xconfig
# nvidia-xconfig:  version 304.43  (buildmeister@swio-display-x86-rhel47-13)  Sun Aug 19 21:19:28 PDT 2012

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
    Option         "BaseMosaic" "True"
    Option         "MetaModes" "GPU-0.CRT-1: 1920x1080+0+0, GPU-0.DFP-0: 1920x1080+1920+0, GPU-1.DFP-0: 1920x1020+3840+0"
    SubSection     "Display"
        Depth       24
    EndSubSection
EndSection



How can I get my 3rd monitor working?
Has someone a working xorg.conf file for me? I use 2 Nvidia GTX 560 ti 2gb cards.

---

### Post by ikariotis on 2012-10-16
This advice was so helpful. My friend has been trying to use Linux with his three-monitor setup for over a year and he was only able to solve his problem with the help of this thread.

On behalf of him, thank you very much for your solution.  :popcorn:

---

### Post by Robstarusa on 2012-10-17
What motherboard/chipset does the OP have?  I don't think IOMMU is supported on most desktop boards.

---

### Post by emiel1976 on 2012-10-19
My hardware.
Intel i7 2600K
Asus Sabertooth p67
2x Nvidia GTX 560 ti 2GB
8 gig ram

Tried this and it din't work. It only made that it didn't see my second GTX 560 and that I had to set the old settings back to get the 3rd monitor back working.

Windows no problems and it runs just great and fast. Xubuntu it is not working, Ubuntu only crashes as I change some settings and Ubuntu 12.10 is just one big bug.
Ubuntu should have better multy monitor suport but the best results I still have with Xubuntu when I run every monitor seperate and than I can't set the different open programs to the different screens.

I will try this with Xubuntu and as it doesn't work, Linux stays of my desktop pc and I will keep it by dualboot on my laptop were I use now Voyager Linux 12.04 that will become 12.10 soon.

---

### Post by AzrieL on 2012-11-09
Thank you so much for this topic! I tore my hair on it!

One question: It works for 4 screens? (always two GPU)

Because I changed the config a bit, but my 4th screen remains stubbornly black.

```
Option         "MetaModes" "GPU-1.DFP-1: 1920x1080+1560+1050,GPU-1.CRT-0: 1680x1050+0+0, GPU-0.CRT-1: 1680x1050+1680+0, GPU-0.CRT-0: 1680x1050+3360+0"
```

---

### Post by sanitycheck on 2012-11-10
Are newer cards like the 560 required for this to work?  I have a pair of GT9500 cards, no SLI, and the third monitor is still not recognized.  The dual monitors on the one card still work fine with the new xorg.conf that was created, however.

Core i5 750
Ubuntu 12.04 64-bit
nVidia driver 304.43 latest with updates from normal repository
Two nVidia 9500GT no SLI

---

### Post by sanitycheck on 2012-11-13
Just out of curiosity, what does the nVidia control panel show for the third monitor on the second GPU* after you get all three screens working*?

In my non-working case, it identifies the card and the monitor attached to it, and shows it as disabled.  The only drop-down option I have is for a second x-screen, as Twinview is grayed out.   This is what it all looked like by default with two working monitors before I made any changes suggested in this thread.

---

### Post by sanitycheck on 2012-11-29
My solution was to throw money at the problem in the form of a single Asus GT640 featuring 4 inputs (2 DVI, 1 HDMI, 1 VGA).  As expected all the monitors showed up in nvidia-settings, so I could set the configuration there.  I have three DVI monitors, so I attached the third monitor with a cable that had DVI on one end and HDMI on the other. 

I wonder if my (and others) dual-card problem is related to the motherboard not supporting SLI.  We're discussing non-SLI configurations here, but maybe SLI support on the board is necessary for the driver to link the multiple cards into one X screen.  My board is an ECS P55H-A, which as I recall supported ATI's version of SLI called Crossfire (or something like that), not SLI.  I wasn't concerned when I bought the board because I knew I wouldn't use SLI, but that may have been a mistake.

---

### Post by dragon042 on 2012-12-19
Thank you so much for the solution!

Finally got 3 monitors to work on my GTX590!

---

### Post by wademac on 2012-12-27
I have a Intel® Core™2 Duo CPU E4500 @ 2.20GHz × 2 with Quadro NVS 290 and a Quadro FX 540 and when I do the following

sudo nvidia-xconfig --base-mosaic --metamodes="GPU-1.DFP-0: 1280x1024+0+0, GPU-1.CRT-0: 1280x1024+1280+0, GPU-0.DFP-0: 1280x1024+2560+0, GPU-0.DFP-1: 1280x1024+3840+0"

and adjust my grub file I only get one not working monitor.. it just boots up with the background and not menu etc.. 

Any advise :)

---

### Post by bshosey on 2013-01-06
I have a Dell Precision T3400 with 2 Nvidia Quatro FX4600 video cards. I am trying to do this so I can have 3-4 montitors. I can not get SLI-Mosaic to enable. Does any one know how to get Mosaic to work with this system?
I can get 3 monitors with xirama but we all no no 3d ecceleration. 

Any help would be appriciated. Thanks

---

### Post by jaheaga on 2013-09-15
Ok, this is great, since I bought my GTX 460 win2, I wasn't able to use one of its gpu due to the lack of 3d support with 2 gpu 2 monitors, now I can do it and able to see the grub and bios, because due to the config I had to put my 2 monitors on the 2nd GPU.

this is my config

sudo nvidia-xconfig --base-mosaic --metamodes="GPU-1.CRT-0: 1280x1024+0+0, GPU-0.CRT-1: 1280x1024+1280+0"

thanks
Jaheaga

---

### Post by gabriel-balint on 2013-09-19
So I have GF GTX 550 TI. It has 3 outputs, I have ubuntu 13.04 and it sees all 3 monitors, but when I try to turn the 3rd one on, it has a weird behavior, like things are overlapping.
Is it not possible to get the 3rd monitor working, without having 2 video cards? Even that seems a hassle.

---

### Post by hermdog on 2014-01-23
So im running to this very same issue.
here are my video cards... and everything i see you guys working on is nvidia... suggestions for this?

03:00.0 VGA compatible controller: Advanced Micro Devices, Inc. [AMD/ATI] Park [Mobility Radeon HD 5430]
05:00.0 VGA compatible controller: Advanced Micro Devices, Inc. [AMD/ATI] Redwood XT [Radeon HD 5670/5690/5730]

---

