---
title: "Using the OpenSource drivers with Nvidia graphics"
date: 2017-07-20
forum: Hardware
---

### Post by rdragonrydr on 2017-07-20
I purchased a Dell Inspiron 15 7559 gaming laptop ([http://www.dell.com/en-us/work/shop/productdetails/inspiron-15-7559-laptop/cai157w10ph5716](http://www.dell.com/en-us/work/shop/productdetails/inspiron-15-7559-laptop/cai157w10ph5716) or [http://www.dell.com/en-us/shop/productdetails/inspiron-15-7559-laptop](http://www.dell.com/en-us/shop/productdetails/inspiron-15-7559-laptop)). It has a Nvidia 960M graphics card in it, and I have had little to no luck getting it to work. I can use the proprietary drivers if I can get it to boot, but any attempt to have it only use the Intel graphics to save battery when I am not running a game causes a lockup. Not even the keyboard leds will respond, so the problem is not just visual. I could just leave it with the Nvidia drivers and set it to use the discrete card all the time, but with how buggy it is already and the fact that Nvidia's drivers get worse over time (or so I'm told), I would like to get the nouveau drivers working.

It uses Optimus, so my chances are already bad, and it tends not to boot with the same lockup problem if I don't have the Nvidia drivers enabled. Still, I think the card is at least partially supported by nouveau (from the feature matrix at [https://nouveau.freedesktop.org/wiki/FeatureMatrix/](https://nouveau.freedesktop.org/wiki/FeatureMatrix/)), so how do I get it to work with the nouveau drivers (although, some of it is WIP'd. That might be it...) and whatever the catch-of-the-day card switching application is?

My other option is either dealing with this thing's issues or trying to trade it in for an AMD graphics laptop (the one HP Omen looks nice, and the card is in the list for the Radeon driver).

---

### Post by #&amp;thj^% on 2017-07-20
After installing the Nvidia Drivers Have you tried editing the default grub boot options by typing in the terminal:

```
gksudo gedit /etc/default/grub 
```

Look for the line:

```
GRUB_CMDLINE_LINUX_DEFAULT="quiet splash"
```

and add nomodeset to the end:

```
GRUB_CMDLINE_LINUX_DEFAULT="quiet splash nomodeset"
```

That way you won't have to keep adding it. Then after saving changes and quitting the editor, type in the terminal:

```
sudo update-grub
```

to update your grub configuration.

---

### Post by rdragonrydr on 2017-07-20
I did that to get it to boot far enough to set up the nvidia drivers. Unfortunately, that also kills the Intel GPU, and leaves me with software rendering. I would like to at least get the Intel one to work.

The nvidia ones fix the booting problem, but I don't know about how stable that might be, and I still can't ONLY disable the nvidia card.

My main question is, is it possible/how can I get the card to use the nouveau open source drivers?

---

### Post by #&amp;thj^% on 2017-07-20
> **rdragonrydr said:**
> 

My main question is, is it possible/how can I get the card to use the nouveau open source drivers?
I have no advice for that one my friend.  I have used the Nvidia Drivers for over 10 years now with Great success.
> **rdragonrydr said:**
> I did that to get it to boot far enough to set up the nvidia drivers. Unfortunately, that also kills the Intel GPU, and leaves me with software rendering. I would like to at least get the Intel one to work.
The nvidia ones fix the booting problem, but I don't know about how stable that might be, and I still can't ONLY disable the nvidia card.

There is also the option to switch between the two cards (GPU's) with Prime-Select.
I have two GPU's here and I switch when needed with the "prime-select intel" and "prime-select nvidia"
```
Graphics:  Card-1: Intel HD Graphics 530
           Card-2: NVIDIA GF114 [GeForce GTX 560 Ti]
           Display Server: x11 (X.Org 1.19.3) driver: nvidia
           Resolution: 1920x1080@60.00hz
           OpenGL: renderer: GeForce GTX 560 Ti/PCIe/SSE2
           version: 4.5.0 NVIDIA 381.22

```
You might want to read up on that: [https://askubuntu.com/questions/661922/how-am-i-supposed-to-use-nvidia-prime](https://askubuntu.com/questions/661922/how-am-i-supposed-to-use-nvidia-prime)
Also Here: [https://askubuntu.com/questions/412452/getting-hybrid-graphics-to-work-nvidia-prime-gt650m](https://askubuntu.com/questions/412452/getting-hybrid-graphics-to-work-nvidia-prime-gt650m)
If you do decide to try that method there is the possibility you could then change the **"nomodeset" to "nogpumanager"** in your Grub file.
Example for mine:
```
# If you change this file, run 'update-grub' afterwards to update
# /boot/grub/grub.cfg.
# For full documentation of the options in this file, see:
#   info -f grub -n 'Simple configuration'

GRUB_DEFAULT=0
#GRUB_HIDDEN_TIMEOUT=0
GRUB_HIDDEN_TIMEOUT_QUIET=true
GRUB_TIMEOUT=10
GRUB_DISTRIBUTOR=`lsb_release -i -s 2> /dev/null || echo Debian`
[COLOR="#FF0000"]**GRUB_CMDLINE_LINUX_DEFAULT="quiet splash nogpumanager"**[/COLOR]
GRUB_CMDLINE_LINUX=""

# Uncomment to enable BadRAM filtering, modify to suit your needs
# This works with Linux (no patch required) and with any kernel that obtains
# the memory map information from GRUB (GNU Mach, kernel of FreeBSD ...)
#GRUB_BADRAM="0x01234567,0xfefefefe,0x89abcdef,0xefefefef"

# Uncomment to disable graphical terminal (grub-pc only)
#GRUB_TERMINAL=console

# The resolution used on graphical terminal
# note that you can use only modes which your graphic card supports via VBE
# you can see them in real GRUB with the command `vbeinfo'
#GRUB_GFXMODE=640x480

# Uncomment if you don't want GRUB to pass "root=UUID=xxx" parameter to Linux
#GRUB_DISABLE_LINUX_UUID=true

# Uncomment to disable generation of recovery mode menu entries
#GRUB_DISABLE_RECOVERY="true"

# Uncomment to get a beep at grub start
#GRUB_INIT_TUNE="480 440 1"
```

---

### Post by rdragonrydr on 2017-07-20
I'll have to try that last one, and look up the link. 

I've tried the prime-select command AND the one in the GUI, but both fail to work and leave it unbootable. Weirdly, the prime-select GPU list only shows the Nvidia one, or maybe it shows corrupted data. I forget which.

---

### Post by rdragonrydr on 2017-08-08
The weirdness continues! I at first thought that maybe, since I used the additional drivers window to set up the Nvidia drivers, maybe there was a driver conflict if Nouveau was still installed. So, I blacklisted that (with [COLOR=#6A6A6A][FONT=Roboto]**rd**[/FONT][/COLOR][COLOR=#545454][FONT=Roboto].[/FONT][/COLOR][COLOR=#6A6A6A][FONT=Roboto]**driver**[/FONT][/COLOR][COLOR=#545454][FONT=Roboto].[/FONT][/COLOR][COLOR=#6A6A6A][FONT=Roboto]**blacklist**[/FONT][/COLOR][COLOR=#545454][FONT=Roboto]=[/FONT][/COLOR][COLOR=#6A6A6A][FONT=Roboto]**nouveau)**[/FONT][/COLOR], and tried to use the nvidia control panel to switch to the Intel GPU. No such luck. It hung, as usual.

My next test was to try to remove all the discrete GPU drivers. 
I installed a fresh copy of the OS, disabled nouveau with Grub (since that's as far as it would boot) (nouveau.modeset=0), and tested to see if it would boot to desktop. It actually did, and stated that it was using the Intel GPU.

During this, I discovered by accident that if I disabled the splash during boot, it would not hang, and that the Nvidia GPU could remain enabled. It still stated that it was using the Intel GPU, though. I then followed [https://nouveau.freedesktop.org/wiki/Optimus/](https://nouveau.freedesktop.org/wiki/Optimus/) to run the commands
```

xrandr --listproviders
xrandr --setprovideroffloadsink nouveau Intel

```
Oddly, this did NOT list an Intel GPU, only a modesetting output and the nvidia device. All inputs and outputs went to the modesetting one, despite the fact that glxinfo and system info said that it was using the Intel device. Due to this, and the fact that the modesetting one was ID 0, the last command was "...noveau 0". However, this seemed to work, and when I set DRI_PRIME=1, glxinfo said that it was using the Nvidia GPU. I did not try testing any actual programs to see if there was a noticeable performance change, though.

However, I messed something up. This was working fine, but the moment I tried rebooting the computer, it hung again with the CPU lockup detected for 23 seconds error as usual. Splash was still disabled, and since quiet was also off, I saw nouveau detect the GPU first thing, and then later a process called "Detect the available GPUs and deal with any system changes" seemed to cause the hang. Other times, plymouthd was the culprit, despite splash being off.

During that time, I had also run the commands (in an attempt to use the Nvidia GPU to run for ALL programs, not just those with DRI_PRIME=1) from the same site
```
echo DIGD > /sys/kernel/debug/vgaswitcheroo/switch
echo DIS > /sys/kernel/debug/vgaswitcheroo/switch
```
but they did not seem to do anything. (Although, I am pretty sure that I first had this problem after running vgaswitcheroo the first time, looking back on it...) Please note that the GPU was in DynOff mode, so I should not have needed to echo ON to it.

I am guessing that one of these commands did something weird, since I never had any luck with nosplash again, **despite reinstalling the OS again after I had run into boot issues after this.**

Why would splash removal fix the problem, when it never had before and for some reason never did again? I am especially curious about the Detect the GPUs thread. Maybe it locked up since Nouveau claimed it already?

Anyway, why would it work once, randomly, and then fail to work again, even after a full reinstall and wipe of the disk? How is it even possible for something like that to persist?
How do I undo this mistake, since I have no idea how it started working again (or whether it would have kept doing so after a reboot, commands I ran or no), and a reinstall does not fix it?

---

### Post by efflandt on 2017-08-09
Which Ubuntu version are you running and which nvidia driver package are you using. If you add the graphic-drivers ppa that may have newer drivers than in your Ubuntu version. I don't know which driver version first supported GTX 960M.

Unfortunately my gaming laptop with Nvidia GTX 765M and Intel HD 4600 graphics no longer turns on. But when it did work with Ubuntu 14.04 I could switch which graphics were used from "NVIDIA X Server Settings". Although, I did not use nomodeset (generally required for nvidia desktop drivers) because someone said that did not work on their laptop. Using "NVIDIA X Server Settings" if I switched Nvidia to Intel, I just had to log out of X and log back in (and a reboot would use Intel graphics), but if I switched Intel to Nvidia, I had to reboot before that would take effect.

---

### Post by rdragonrydr on 2017-08-09
I am using 16.04. Sadly, none of that had ever worked for me. I was using either 365 or 367 nvidia drivers (I do not recall precisely which. They were suggested by the additional drivers utility window.)
Any attempt to use the Intel drivers resulted in a hang on bootup or restart. Logging out had exactly the same effect.

I had tried with and without nomodeset. By this, I mean the one specifically for Nouveau, not the general one. The latter would stop the Nvidia drivers from using the GPU as well as the Nouveau ones, plus it even halts the Intel one. I was stuck with software rendering. Either nomodeset command did get it to boot, though. I had to use that after every time I tried to switch to the Intel GPU via the Nvidia settings.

---

