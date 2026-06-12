---
title: "HDMI output gone after completing ubuntu updates"
date: 2015-09-14
forum: Hardware
---

### Post by GoddamnNoise on 2015-09-14
Hi,

I've Ubuntu 14.04 LTS installed on a Toshiba Satellite laptop (it has an integrated Intel video card and an AMD Radeon video card). After installation I was using an external monitor screen connected to the laptop through the HDMI laptop's output. Everything worked fine until the Ubuntu's Software Updater showed me some pending updates. I've made the updates and the next time i restarted the laptop, there was no way to detect the external screen. After googling a lot about this, i couldn't find a solution to my problem. 

This is the output of the xrandr command:

```
Screen 0: minimum 8 x 8, current 1366 x 768, maximum 32767 x 32767
eDP1 connected primary 1366x768+0+0 (normal left inverted right x axis y axis) 344mm x 194mm
   1366x768       60.0*+
   1360x768       59.8     60.0  
   1024x768       60.0  
   800x600        60.3     56.2  
   640x480        59.9  
VIRTUAL1 disconnected (normal left inverted right x axis y axis)

```

As you see, the HDMI output is not shown, but it was shown until the Ubuntu update.

If I go to "System Settings > Software & Updates > Additional Drivers", the message "No propietary drivers are in use" is shown. If I go to "System Settings > Software & Updates > Ubuntu Software" and I check the "Propietary drivers for devices (restricted)" option, then, in the "Additional Drivers" tab the "Continue using a manually installed driver" is checked and three options show up (but they are greyed options I can't select):

- Using X.Org X Server - AMD/ATI display driver wrapper from xserver-xorg-video-ati (open source, tested)
- Using Video driver for  the AMD graphics accelerators from fglrx (propietary)
- Using Video driver for  the AMD graphics accelerators from fglrx-updates (propietary)

How could I solve this problem in a safe way?. Could someone help?. Thanks in advance.

---

### Post by Bucky Ball on 2015-09-14
*Thread moved to **Hardware**.*

Welcome. Unable to help with your issue but you may have more luck here.

---

### Post by SeijiSensei on 2015-09-14
If you reboot, do you see the grub menu?  If so, try choosing an earlier version of the kernel.  You should at least have the option of reverting to the (n-1)th kernel and maybe more.  If that fixes the problem, read this to learn how to make the working kernel the default at boot: [http://ubuntuforums.org/showthread.php?t=2292857](http://ubuntuforums.org/showthread.php?t=2292857)

---

### Post by GoddamnNoise on 2015-09-14
Hi SeijiSensei,

First: thanks a lot for your help. 

I've rebooted and chosed earlier versions of kernel but i haven't seen any changes doing that. I've executed the xrandr command in each of the previous kernel versions with the same results.

I have no experience with these kind of Ubuntu / hardware related issues, but I've been digging deeper, so i've got more information about this problem. It seems that in the past, some people have fixed this kind of problem [reinstalling the xserver-xorg-video intel package]("http://ubuntuforums.org/showthread.php?t=2180388"). I've tried to do that and this is what happened:

sudo apt-get install --reinstall xserver-xorg-video-intel


Reading package lists... Done
Building dependency tree       
Reading state information... Done
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.
The following information may help to resolve the situation:


The following packages have unmet dependencies:
 xserver-xorg-video-intel : Depends: xorg-video-abi-15
                            Depends: xserver-xorg-core (>= 2:1.14.99.902)
E: Unable to correct problems, you have held broken packages.

So,  it's some kind of package-related issue (i've only installed Ubuntu updates after Ubuntu installation)?. Does any more experienced Ubuntu user know how to fix this kind of problem?. Thanks again for your help!.

[B]Update:


[/B]If I try: 

[COLOR=#111111][FONT=Consolas]dpkg --get-selections | grep hold

I get no output. So, is not a package-related issue after all?.[/FONT][/COLOR]

[B]Update:

[/B]Next thing i've tried:

sudo apt-get update
sudo apt-get autoremove

Then, i've rebooted and, when i've used the xrandr command... the HDMI output is there again! :-D

xrandr
Screen 0: minimum 8 x 8, current 1366 x 768, maximum 32767 x 32767
eDP1 connected primary 1366x768+0+0 (normal left inverted right x axis y axis) 344mm x 194mm
   1366x768       60.0*+
   1360x768       59.8     60.0  
   1024x768       60.0  
   800x600        60.3     56.2  
   640x480        59.9  
HDMI1 disconnected (normal left inverted right x axis y axis)
VIRTUAL1 disconnected (normal left inverted right x axis y axis)

So,  i think it's **SOLVED**!.

---

### Post by Bucky Ball on 2015-09-15
Good news. See the first link in my signature and enjoy the OS and forums. :)

Incidentally, autoremove should go first, thus:

```

sudo apt-get autoremove
sudo apt-get update
sudo apt-get upgrade
sudo apt-get dist-upgrade

```	

These commands will NOT upgrade your current release to a newer one, only the software you have installed in your current release.

---

### Post by GoddamnNoise on 2015-09-15
And... It's [B]NOT SOLVED.

[/B]After rebooting, the HDMI output is gone again from the xrandr command's output.

After executing these commands:

```

sudo apt-get autoremove
sudo apt-get update
sudo apt-get upgrade
sudo apt-get dist-upgrade
```

No packets were deleted/updated. No HDMI output when executing xrandr command.

But, when i went to "System Settings > Software & Updates > Ubuntu Software" and I checked the "Propietary drivers for devices (restricted)" option, then, in the "Additional Drivers" tab the "Continue using a manually installed driver" is checked and the three options showed up again but no greyed this time:

- Using X.Org X Server - AMD/ATI display driver wrapper from xserver-xorg-video-ati (open source, tested)
- Using Video driver for the AMD graphics accelerators from fglrx (propietary)
- Using Video driver for the AMD graphics accelerators from fglrx-updates (propietary)

Chosed flgrx driver, rebooted and no HDMI output.
Chosed flgrx-updates driver, rebooted and no HDMI output.
Chosed again X.Org driver, rebooted and Ubuntu crashed while booting. A window appeared to choose between low-graphics mode, text console or trying to fix the problem. I've selected trying to fix the problem. Then, an option to restore previous xorg configuration didn't worked and the option to configure the default configuration didn't worked either. So, i've gone back, selected the text console, rebooted the system and this time, Ubuntu booted but no HDMI output on xrandr command.

Any ideas?.

**Update:**

Digging even deeper. After looking at /var/log/Xorg.0.log and looking for "HDMI" on that file, i've founded these lines:

.....
[     8.233] (II) config/udev: Adding input device HDA Intel HDMI HDMI/DP,pcm=3 (/dev/input/event13)
[     8.233] (II) No input driver specified, ignoring this device.
[     8.233] (II) This device may have been added with another device file.
[     8.233] (II) config/udev: Adding input device HDA Intel HDMI HDMI/DP,pcm=7 (/dev/input/event14)
[     8.233] (II) No input driver specified, ignoring this device.
[     8.233] (II) This device may have been added with another device file.
[     8.233] (II) config/udev: Adding input device HDA Intel HDMI HDMI/DP,pcm=8 (/dev/input/event15)
.....

So, it seems that the HDMI port is detected but ignored because no input driver is specified. So... how could I specify an input driver for that port?.

---

### Post by GoddamnNoise on 2015-09-16
It seems that there is a [bug reported in launchpad for this issue]("https://bugs.launchpad.net/ubuntu/+source/linux/+bug/1490689").

---

### Post by GoddamnNoise on 2015-09-17
As suggested, I've added another bug report on launchpad for this issue: [https://bugs.launchpad.net/ubuntu/+source/linux-lts-utopic/+bug/1496697](https://bugs.launchpad.net/ubuntu/+source/linux-lts-utopic/+bug/1496697)

---

