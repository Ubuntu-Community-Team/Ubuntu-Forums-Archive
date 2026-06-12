---
title: "Primary Monitor Not Detected Until After Logging In"
date: 2020-12-21
forum: Hardware
---

### Post by LinuxDuck on 2020-12-21
I am running into a problem with my dual monitor setup when I reboot. My primary monitor is blank at the login screen. I have to turn it off in order to see the the password prompt appear on my secondary monitor. Once I log in, the primary monitor is detected just fine. This is a minor annoyance, but one I would like to correct if possible. Please let me know if there's any additional information I need to provide.
```

Primary Monitor:
MSI Optix MAG241C
1920x1080
144hz

Secondary Monitor: 
ASUS VE247
1920x1080
60hz

Specs:
OS: Ubuntu 20.04.1 
LTSKERNEL: 5.4.0-58-generic
CPU: AMD Ryzen 5 3600XT 6-Core
GPU: NVIDIA GeForce RTX 2060 SUPER
GPU DRIVER: NVIDIA 455.38

```


Thanks

---

### Post by #&amp;thj^% on 2020-12-21
That happens at times with the Nvidia driver.
Outside of un-installing Nvidia, lets have a look at your set-up.
```
 more /etc/default/grub
```
Paste that back for us to look at please.
Others have reported installing and using lightdm solves the problem also.

---

### Post by LinuxDuck on 2020-12-21
```
GRUB_DEFAULT=0
GRUB_TIMEOUT_STYLE=hidden
GRUB_TIMEOUT=0
GRUB_DISTRIBUTOR=`lsb_release -i -s 2> /dev/null || echo Debian`
GRUB_CMDLINE_LINUX_DEFAULT="quiet splash"
GRUB_CMDLINE_LINUX=""
```

I will try lightdm

---

### Post by #&amp;thj^% on 2020-12-21
Whoa. that just can't be "all"
Please try again with:
```
more /etc/default/grub > grub.txt
```
in your home you will find the "grub.txt" file, paste that back here please.

---

### Post by LinuxDuck on 2020-12-21
Sorry. <-- newbie. Here's the full contents. lightdm sort of works. The login prompt shows up on the secondary screen but the primary display still won't turn on until I log in.

```
# If you change this file, run 'update-grub' afterwards to update
# /boot/grub/grub.cfg.
# For full documentation of the options in this file, see:
#   info -f grub -n 'Simple configuration'

GRUB_DEFAULT=0
GRUB_TIMEOUT_STYLE=hidden
GRUB_TIMEOUT=0
GRUB_DISTRIBUTOR=`lsb_release -i -s 2> /dev/null || echo Debian`
GRUB_CMDLINE_LINUX_DEFAULT="quiet splash"
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

### Post by #&amp;thj^% on 2020-12-21
Well there is no modset. (not sure if that's bad or good for you)
On my hybrid Intel/Nvidia, I use it very differently EG:
in grub I use:
```
nvidia-drm.modeset=1
```
But before you make any change like that, please just try this first:
Add this to /etc/X11/Xwrapper.config :
```

needs_root_rights = yes
```
if you would like it to be automatically updated
again, run the following command as root:
```

 dpkg-reconfigure xserver-xorg-legacy
```

---

### Post by LinuxDuck on 2020-12-21
I tried your suggested solutions but saw no change.

---

### Post by #&amp;thj^% on 2020-12-21
Well let us see this then:
```
lsmod | grep '^drm'
```
**BTW** How do you connect your primary display?

---

### Post by LinuxDuck on 2020-12-21
That returns 

drm_kms_helper        184320  1 nvidia_drm
drm                          491520  9 drm_kms_helper,nvidia_drm

---

### Post by #&amp;thj^% on 2020-12-21
And let me guess, the secondary monitor is connected to the Nvidia card right?

---

### Post by LinuxDuck on 2020-12-21
Yes, it's connected to the card.

---

### Post by #&amp;thj^% on 2020-12-21
Well your set-up is using Nvidia only, that's why you see no screen on primary (AMD)
See if we can convince to see both at login.
Show me this please:
```
more /etc/X11/xorg.conf > xorg.txt
```
same as before in home xorg.txt.

---

### Post by LinuxDuck on 2020-12-21
No such file or directory. Not seeing xorg.conf or xorg.txt

---

### Post by #&amp;thj^% on 2020-12-21
That's a good thing.
Sorry if this is bit tedious, But i use great caution with these driver issues.
One more to see:
```
 more /usr/share/X11/xorg.conf.d/10-nvidia.conf
```

---

### Post by LinuxDuck on 2020-12-21
```

Section "OutputClass"
    Identifier "nvidia"
    MatchDriver "nvidia-drm"
    Driver "nvidia"
    Option "AllowEmptyInitialConfiguration"
    ModulePath "/usr/lib/x86_64-linux-gnu/nvidia/xorg"
EndSection

```

---

### Post by #&amp;thj^% on 2020-12-21
Here>>"Option "**AllowEmptyInitialConfiguration**"
Will you try this change:
```
Option "PrimaryGPU" "Yes"
```
And after a reboot, any better?

---

### Post by LinuxDuck on 2020-12-21
No change

---

### Post by #&amp;thj^% on 2020-12-21
> **LinuxDuck said:**
> No change

Just to check, show this:
```
more /usr/share/X11/xorg.conf.d/10-nvidia.conf
```

---

### Post by LinuxDuck on 2020-12-21
```

Section "OutputClass"
    Identifier "nvidia"
    MatchDriver "nvidia-drm"
    Driver "nvidia"
    Option "PrimaryGPU" "Yes"
    ModulePath "/usr/lib/x86_64-linux-gnu/nvidia/xorg"
EndSection

```

---

### Post by #&amp;thj^% on 2020-12-21
Stumped???
I'm missing something here.
```
sudo apt install inxi
```
after install, please show:
```
inxi -G
```

---

### Post by LinuxDuck on 2020-12-21
```

Graphics:
  Device-1: NVIDIA TU106 [GeForce RTX 2060 SUPER] driver: nvidia v: 455.38 
  Display: x11 server: X.Org 1.20.8 driver: nvidia 
  resolution: 1920x1080~60Hz 
  OpenGL: renderer: GeForce RTX 2060 SUPER/PCIe/SSE2 v: 4.6.0 NVIDIA 455.38

```

---

### Post by #&amp;thj^% on 2020-12-21
Yep, I missed the fact you are using just one (1) video card.
Try changing the video connectors around, swapping places.

---

### Post by LinuxDuck on 2020-12-21
When I lock the computer, I get no response from the primary monitor no matter which display port I'm using (1x HDMI or 3x DP) unless I swap the display port while the system is locked. Then it decides to work. I'm observing the same behavior with only the primary monitor plugged in and with both. Tested all ports on the GPU and tried HDMI & DP on the monitor itself.

---

### Post by #&amp;thj^% on 2020-12-21
Thanks for checking, and informed reply.
Boy that begs the question or wonder if your cable is good. (Different Vendors set their chips differently.)
Also the no response could be coming from GDM or a very slow wake response.

---

### Post by LinuxDuck on 2020-12-21
I'm getting identical behavior whether using the HDMI or DPs (different cables). I can try waiting a bit to see if it's a slow wake response.

EDIT: It's not a slow wake response. It never wakes. Also noticing *extremely *laggy mouse movement now on the lock screen that isn't present when I reboot. It goes away once I unlock. Very odd.

---

### Post by #&amp;thj^% on 2020-12-21
If this works we can revert all previous changes.
```
sudo nano /etc/default/grub
```
And make this change to that line.
```
GRUB_CMDLINE_LINUX_DEFAULT="quiet splash nouveau.modeset=0"
```
update grub after saving that file.
```
sudo update-grub
```
Yep you guessed it >>>>reboot

---

### Post by LinuxDuck on 2020-12-21
Thanks for trying. I've managed to break my Ubuntu installation pretty hard trying to switch back to gdm from lightdm... I'm stuck on the BIOS screen and can't get get grub to show up. I'm going to do a fresh installation since I've clearly been mucking around too much. I'll just deal with having one display on the lock screen. using lightdm was an acceptable workaround, but I'm still open to suggestions if anyone has ideas.

---

### Post by #&amp;thj^% on 2020-12-21
if your "only" changes came from my suggestions, then it was 'me' that broke your system.
And if that's the case then my apology. :(
But if it was that last change in grub that broke it, you can re-edit it with live installer: [https://howtoubuntu.org/how-to-repair-restore-reinstall-grub-2-with-a-ubuntu-live-cd](https://howtoubuntu.org/how-to-repair-restore-reinstall-grub-2-with-a-ubuntu-live-cd)

---

### Post by LinuxDuck on 2020-12-21
Nope, it was my own tomfoolery that broke it. Thanks for sharing the link. I'll take a look.

---

### Post by mastablasta on 2020-12-22
nvidia is just that idiotic. I've set the autologin. output always goes to TV first, then to monitor. it recognises the monitor correctly, so i know it has it's EDID. i set it as primary, but it still pushes display to TV. it does the same on Windows XP (on the other hard disk). and it does it even if i unplug the TV.

on my kids PC it pretended it doesn't see the monitor. Somehow the connection showed up i just changed the cable with the one from RPi want to connect the. i though the cable that came with monitor was faulty, so i had it tested. it worked ok, i replaced it back and suddenly all works as it should.

you could say that the card doesn't get the edid form monitor correctly, but then again it is repeating this even after getting it, after saving configuration and after creating xorg file. i will likely be getting AMD next time.

---

### Post by #&amp;thj^% on 2020-12-22
> **mastablasta said:**
> nvidia is just that idiotic. I've set the autologin. output always goes to TV first, then to monitor. it recognises the monitor correctly, so i know it has it's EDID. i set it as primary, but it still pushes display to TV. it does the same on Windows XP (on the other hard disk). and it does it even if i unplug the TV.

on my kids PC it pretended it doesn't see the monitor. Somehow the connection showed up i just changed the cable with the one from RPi want to connect the. i though the cable that came with monitor was faulty, so i had it tested. it worked ok, i replaced it back and suddenly all works as it should.

you could say that the card doesn't get the edid form monitor correctly, but then again it is repeating this even after getting it, after saving configuration and after creating xorg file. i will likely be getting AMD next time.

:D Love it!!
It all came back to me last night, I used to use an app named "[disper]("https://launchpad.net/ubuntu/focal/+package/disper")" and worked very well for this, the best part was Very Simple no nvidia-hacking needed. 
alas i can't find it in the repos now...could build it from source though I'd imagine.
My PNY Nvidia 1050TI works perfectly, I feel vendors have a hand in all this madness also.
Usage: Note this is on Arch Linux
```

disper -l
display eDP-1: eDP-1
 resolutions: 320x180, 360x202, 320x240, 432x243, 400x300, 480x270, 512x288, 512x384, 640x360, 640x400, 684x384, 720x405, 640x480, 700x450, 640x512, 800x450, 700x525, 864x486, 840x525, 800x600, 960x540, 960x600, 1024x576, 896x672, 928x696, 960x720, 1024x768, 1280x720, 1280x800, 1368x768, 1440x810, 1280x960, 1400x900, 1280x1024, 1600x900, 1400x1050, 1680x1050, 1920x1080
display HDMI-1: HDMI-1
 resolutions: 640x480, 720x480, 720x576, 800x600, 832x624, 1024x768, 1280x720, 1152x864, 1280x800, 1440x900, 1280x1024, 1600x900, 1680x1050, 1920x1080, 720x400
```
i wanted the laptop to be extended from the Samsung, thus, having the laptop physically top aligned, I wanted them to be also logically top aligned and have their own maximum resolution:
```

disper -d eDP-1,HDMI-1 -r auto -e -t right
```

this has to be read as: (-d) opertate first on SyncMaster then on laptop lcd, (-r) consider auto resolution, (-e) extend the second display [second here is laptop because the -d set display ordering], (-t) extend the second display [laptop] to the right of the first.
Man Page: [https://www.systutorials.com/docs/linux/man/1-disper/](https://www.systutorials.com/docs/linux/man/1-disper/)

---

### Post by LinuxDuck on 2020-12-25
I fixed the issue! copying monitors.xml to /var/lib/gdm3/ was the solution.

```
 sudo cp ~/.config/monitors.xml /var/lib/gdm3/.config 
```

monitors are now displaying perfectly at the login screen.

---

