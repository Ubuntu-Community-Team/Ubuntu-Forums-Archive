---
title: "64-bit Karmic + Lenovo Thinkpad T510 Advice"
date: 2010-01-25
forum: Hardware
---

### Post by zengorilla on 2010-01-25
Hello all,

        I'm not sure if this is the right place, but I've spend days scouring forums to get my new Lenovo Thinkpad T510 running on 64-bit Karmic, and I thought I'd dump my findings here.

Here's what I got "out of the box":
-Sound: OK
-Keyboard/Mouse: OK
-Video Card: not detected
-Wifi: not detected

Here's what I did to fix these problems:
Video:
My laptop has the new intel i5 core integrated graphics, and the following output from the command 'lspci -v | grep VGA':

00:02.0 VGA compatible controller: Intel Corporation Arrandale Integrated Graphics Controller (rev 02)

Step 1: Add the xorg-edgers repo, and let your package manager install all updated (do NOT install individual packages manually, their warning states). More info at [https://launchpad.net/~xorg-edgers/+archive/ppa?field.series_filter=karmic]("https://launchpad.net/%7Exorg-edgers/+archive/ppa?field.series_filter=karmic") .

Step 2: Hand-configure xorg.conf to use the intel driver for the video card.
I just opened up my default xorg.conf file, and updated the 'Device' section with the following params:

BusID "PCI:0:2:0"
Driver "intel"

(I got the bus ID from the output from lspci -v)

Step 3: Enable indirect rendering on compiz. Instructions here: [http://farfewertoes.com/stories/2008-07-30-ubuntu-tip-enable-indirect-rendering/](http://farfewertoes.com/stories/2008-07-30-ubuntu-tip-enable-indirect-rendering/)

My system would not boot without this (or, would boot in Gnome, and freeze after a few seconds).

Step 4: Reboot. 

Open Issues: There are some weird screen artifacts every once in a while, especially with the new notification system. I'm hoping these will be fixed when xorg-edgers gets the latest intel driver in their packaging system.

----------------------------

How I got wifi working:

According to lspci -v, my wifi card is
03:00.0 Network Controller: Realtek Semiconductor Co., Ltd. Device 8172 (rev 10)

I first followed the instructions at [https://help.ubuntu.com/community/WifiDocs/Device/Realtek%208172](https://help.ubuntu.com/community/WifiDocs/Device/Realtek%208172) -- unfortunately, the version of the driver there causes a kernel panic for the kernel included in Karmic.

I made this work by getting the latest version of it from realtek's site and installing from source. Here's the page: [http://www.realtek.com.tw/downloads/downloadsView.aspx?Langid=1&PNid=21&PFid=48&Level=5&Conn=4&DownTypeID=3&GetDown=false&Downloads=true](http://www.realtek.com.tw/downloads/downloadsView.aspx?Langid=1&PNid=21&PFid=48&Level=5&Conn=4&DownTypeID=3&GetDown=false&Downloads=true)

Installing from source was straightforward: sudo su, make, make install.

I may have had to install the kernel headers and the build-essential package as well; I honestly don't recall.

Note that I'm using the driver marked on their site as 'rtl8192se', even though lspci reports **8172** -- I'm not sure why this is different, but various people have recommended it on forums. 

-----------------------------------------------------------------------------------------------------

Of course, this is somewhat vague and might break your system, etc etc; it just worked for me and I wanted to share in hopes that someone else wouldn't have to spend so long scouring for information. Good luck!

---

### Post by zengorilla on 2010-01-26
Also, if anyone figures out how to get suspend working, I'd be curious to hear about it :)

---

### Post by zengorilla on 2010-01-26
Here's an update:

My wifi has been dropping in and out, usually a few minutes after connecting. Disabling and re-enabling wireless in general (by right-clicking the wifi tray app in Gnome) fixes the problem, but is irritating.

I found an even newer version of the realtek driver at [https://bugs.launchpad.net/ubuntu/+source/linux/+bug/401126?comments=all](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/401126?comments=all) (someone replied with v14, only v13 is on realtek's website)

Additionally, on someone's advice in that thread, I recursively removed references to -DENABLE_LPS from all makefiles in the driver (it was in a couple different ones, I used grep -r DENABLE_LPS to find them).

This seems to have helped for now. Good luck :).

---

### Post by msrinath80 on 2010-01-29
I plan to get this myself. How about the following, do they work?

1. SD/MMC card reader
2. Modem (if any)
3. HDMI?
4. IEEE firewire
5. Webcam?

Also, are there plans to setup a wiki for this thinkpad on thinkwiki.org?

---

### Post by gnarfle on 2010-01-30
Well I have not had as much luck as you :)

I picked up a Core i3 Acer laptop with the same integrated graphics (although mine is listed as revision 12) and I've had no love. It initially booted to a black screen, although adding i915.modeset=0 to the boot args in grub did get me to boot. I tried the edge packages but it again booted to a black screen, and if I add the modeline arg in it boots into low graphics mode with an error saying the modeset is not defined.

I'm downloading 10.04 just for the heck of it to try, but it seems like in the meantime I'm stuck in windows...

---

### Post by zengorilla on 2010-02-03
msrinath80, sorry, I have not yet tried any of those peripherals. Also, I do not personally have any plans to set up a wiki on thinkwiki, and I'm not sure if others do :).

gnarfle, did you hand-edit the xorg.conf as I did? You might want to try it, my video card was not using the intel drivers by default without doing so. Other than that, I have no idea :(.

---

### Post by gnarfle on 2010-02-04
> **zengorilla said:**
> msrinath80, sorry, I have not yet tried any of those peripherals. Also, I do not personally have any plans to set up a wiki on thinkwiki, and I'm not sure if others do :).

gnarfle, did you hand-edit the xorg.conf as I did? You might want to try it, my video card was not using the intel drivers by default without doing so. Other than that, I have no idea :(.

Yep, I put the same thing in there but as soon as I put graphics in as the intel driver, x crashes and displays a black screen.

I did get the alpha of Ubuntu 10.04 to boot and it recognized the card nicely. Unfortunately it locks up withint minutes of running in X every single time. It does look like ubuntu support is on the way though, hopefully I won't be stuck in Win7 for too much longer.

---

### Post by gnarfle on 2010-02-04
I think my problem might just be unsolvable for the time being...

It seems like my computer is subject to a bug in 9.10 that causes X to crash when using modeset support in the kernel. I can get around that by booting with i915.modeset=0. Unfortunately, the newer xserver intel drivers from the xorg-edgers requires modeset support. I think when I install those and configure the conf file to use them, then I'm being bitten by the modeset bug again. And if I disable modset, then I can't use the drivers...

Unfortunately I haven't found any fix for the black screen issue other than disabling modeset.

---

### Post by stacktracer on 2010-02-07
Try the 2.6.32 kernel (with the xorg-edgers stuff, and without the i915.modeset=0 flag).

Get kernel packages from [http://kernel.ubuntu.com/~kernel-ppa/mainline/](http://kernel.ubuntu.com/~kernel-ppa/mainline/). (It's not an apt repository, unfortunately -- just download the debs and install with dpkg.)

Those mainline kernel packages seem to be just straight vanilla kernels, with no Ubuntu-izations. The only practical difference I've seen so far is that AppArmor doesn't work, which is no big deal for me.

---

### Post by stacktracer on 2010-02-07
Also, even with xorg-edgers and kernel 2.6.32, compiz is unusably crashy. I haven't tried the OP's indirect-rendering trick -- instead I have turned off compiz:

```
gconftool-2 --set /desktop/gnome/session/required_components/windowmanager --type string metacity
```

Of course, you first have to be able to log in ... which is tough with a crashy window manager, and bleeding-edge modesetting. You can boot with the "text" kernel parameter, turn off compiz, then reboot as usual.

---

### Post by peepingtom on 2010-02-07
I have the version with  discrete graphics (nVidia Quadro NVS3100M) and Intel 5300 WiFi Link, and I'm running Lucid 64 bit.

The following devices have no device drivers under Lucid:
Intel AMT (unimportant for most users)
nVidia Audio (HDMI Audio Device)
00:1f.3 SMBus: Intel Corporation 5 Series/3400 Series Chipset SMBus Controller (rev 06)
00:1f.6 Signal processing controller: Intel Corporation 5 Series/3400 Series Chipset Thermal Subsystem (rev 06)


SMBus may be important re: ACPI, and is possibly the reason we can't resume after suspend to ram.
I've tried disabling most hardware in BIOS, no effect on the resume issue.

Here's my results, having followed [https://wiki.ubuntu.com/DebuggingKernelSuspend](https://wiki.ubuntu.com/DebuggingKernelSuspend)

```
[    1.165867] PM: Resume from disk failed.
[    1.165877] registered taskstats version 1
[    1.166693]   Magic number: 0:202:348
[    1.166771]   hash matches /build/buildd/linux-2.6.32/drivers/base/power/main.c:430
```


[https://wiki.ubuntu.com/DebuggingKernelSuspendHibernateResume#Debugging](https://wiki.ubuntu.com/DebuggingKernelSuspendHibernateResume#Debugging) Suspend
I've done this. Edit /etc/default/grub to have this line: GRUB_CMDLINE_LINUX_DEFAULT="text no_console_suspend "
run  sudo update-grub   .Reboot.
GDM will no longer start, computer will boot to VT7. Press crtl+alt+F1 to get login prompt. run   sudo /etc/acpi/sleep.sh
Sleep, wake, wait like 30 seconds. You'll likely have a blinking cursor. Try typing   ```
sudo service gdm start
```
GDM will proably start. If not, shut off computer with power button (or even better alt+sysRq+R E I S U B )

Save relavent parts of kern.log or kern.log.0  


[https://bugs.launchpad.net/ubuntu/+source/linux/+bug/519375](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/519375)
I've filed a bug report re:suspend. Please confirm that we have the same issue betwen t510 revisions.

There is a t410 thread in this forum, at least one person has reported that they have no problems with resume when using proprietary nvidia drivers.

If this is happening because there's no driver for SMBus, I sure hope there is one upstream. Cannonical isn't exactly known for kernel code contributions (not that there's anything wrong with this ;) ).

BTW when it freezes on wakeup, try alt+sysrq+k . It works for me most of the time. You'll still lose all processes running in VT7, so save before suspending.



Also: don't trust those Restore CDs. The program only lets you burn them once, and my first one was a dud on (relatively) expensive media (very little data burned, lenovo's cd creation app didn't complain). I don't think i'll be putting Windows 7 back on this machine without using an MSDN cd :D

---

### Post by jem76msp on 2010-02-09
Could anybody comment on how the NVIDIA NVS 3100m graphic card works under Ubuntu? 

  I called NVIDIA and they told me it's "OEM" and that NVIDIA is not providing the drivers, even for Windows7, that Lenovo provides them. The graphic card is the only thing still holding me back from purchasing this laptop, as long as I can make sure I can take advantage of it under Linux and have 3D graphics working properly I'll be happy.

  Also, the Core i7-620M is supposed to have integrated graphics, has anybody gotten that working yet?

  Thanks everybody for the help.

---

### Post by peepingtom on 2010-02-09
I was hoping that I could use switchable graphics, but it seems it's not possible on the t510. The nvs3100m is a bit of an oddball, i'm having issues with backlight controls when using the propriatary drivers. Right now i'm working on some ACPI debugging, i'll post back once I actually get a chance to play with the card while running propritary drivers.

Not being able to use switchable graphics was a real letdown (Lenovo was advertising them, I should have paid better attention to the officil specs PDFs). I'd say that unless you need a laptop with 1080p screen or 512mb graphics memory go with a t410. At least then you can hedge your bets between the intel open source and nvidia proprietary drivers. I can't even access the gpu built into my i5.

---

### Post by peepingtom on 2010-02-11
[http://live.gnome.org/GPointingDeviceSettings](http://live.gnome.org/GPointingDeviceSettings)

This enables trackpoint scrolling, newer version than the one in Lucid universe.
It kinda sucks that we have separate t510 and t410 wokrking threads, a lot of redundant conversation is happening here an here: 
[http://ubuntuforums.org/showthread.php?t=1383110](http://ubuntuforums.org/showthread.php?t=1383110)

---

### Post by FFFred on 2010-02-14
GMA 4500HD works great with below setup.

- last 2.6.32 kernel debs : [http://kernel.ubuntu.com/~kernel-ppa/mainline/v2.6.32.8/]("http://kernel.ubuntu.com/%7Ekernel-ppa/mainline/v2.6.32.8/")
- with xorg-edgers stuff
- without the i915.modeset=0 flag
- without indirect rendering
- with below /etc/X11/xorg.conf

```

Section "Device"
        Identifier      "Configured Video Device"
        BusID "PCI:0:2:0"
        Driver "intel"
EndSection

Section "Module"
    Load    "glx"
    Load    "dri"
    Load    "extmod"
   Load    "record"
    Load    "dbe"
    Load    "GLcore"
    Load    "xtrap"
    Load    "freetype"
EndSection

Section "Monitor"
        Identifier      "Configured Monitor"
EndSection

Section "Screen"
        Identifier      "Default Screen"
        Monitor         "Configured Monitor"
        Device          "Configured Video Device"
        DefaultDepth    24
EndSection

Section "DRI"
    Mode 0666
EndSection

```

I can confirm wifi is working fine after removing the -DENABLE_LPS tags as zengorilla pointed out.


To be able to use the IBM FN keys to change the brightness, you need to add /etc/modprobe.d/thinkpad-acpi file with below content.
options thinkpad-acpi brightness-enable=1 experimental=1 hotkey=enable,0xffffff

Thanks,
Fred
---
glad owner of the T510 (4313-28U) :D

---

### Post by Prisma on 2010-02-14
Hello guys :)

Don't know if this will help you. I used to have the same problems running Ubuntu 9.04 (64 bits version). I decided to make a clean intall, since I have been updating Ubuntu for the last 2 years with each new release. Well, this time I decided to install 9.10 32bit version, man that solved ALL the wireless issues in my PC, all webcam issues, virtually every issue I used to have. My suggestion: burn the 32bit version in the live CD and reboot, check if everything works. I bet it will. If indeeed works, then backup all your data and do a clean install of the 32bit version.

Hope this helps :)

---

### Post by pferraro on 2010-05-05
> **stacktracer said:**
> Also, even with xorg-edgers and kernel 2.6.32, compiz is unusably crashy. I haven't tried the OP's indirect-rendering trick -- instead I have turned off compiz:

```
gconftool-2 --set /desktop/gnome/session/required_components/windowmanager --type string metacity
```

Of course, you first have to be able to log in ... which is tough with a crashy window manager, and bleeding-edge modesetting. You can boot with the "text" kernel parameter, turn off compiz, then reboot as usual.

To toggle the window manager from compiz to metacity for the login screen:
sudo -u gdm gconftool --set /desktop/gnome/session/required_components/windowmanager --type string metacity

---

### Post by peepingtom on 2010-05-10
[http://www-307.ibm.com/pc/support/site.wss/document.do?lndocid=MIGR-74582](http://www-307.ibm.com/pc/support/site.wss/document.do?lndocid=MIGR-74582)
The most recent BIOS update fixes suspend.

---

### Post by konbs on 2010-07-02
Hey,

I also just bought a Lenovo Thinkpad T510 :) Unfortunately, my WIFI does not work.

```

03:00.0 Network controller: Intel Corporation WiFi Link 6000 Series (rev 35)
	Subsystem: Intel Corporation Device 1111
	Flags: bus master, fast devsel, latency 0, IRQ 35
	Memory at f2000000 (64-bit, non-prefetchable) [size=8K]
	Capabilities: [c8] Power Management version 3
	Capabilities: [d0] Message Signalled Interrupts: Mask- 64bit+ Queue=0/0 Enable+
	Capabilities: [e0] Express Endpoint, MSI 00
	Capabilities: [100] Advanced Error Reporting <?>
	Capabilities: [140] Device Serial Number e0-e8-14-ff-ff-d7-24-00
	Kernel driver in use: iwlagn
	Kernel modules: iwlagn

```

Do you have any suggestions? Thanks!

Kon

EDIT: It was disabled by an almost hidden button ;)

---

