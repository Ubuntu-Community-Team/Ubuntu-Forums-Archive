---
title: "Acer M5-481TG clickpad/trackpad not working on Ubuntu 11.10/12.04"
date: 2012-08-07
forum: Hardware
---

### Post by vacaloca on 2012-08-07
I recently acquired a new Acer Aspire TimelineU M5-481TG. I tried installing Ubuntu 12.04, and upon bootup, my Synaptics clickpad does not work, even though I hit Fn+F7 to enable/disable it. I get the image of the touchpad on/off OSD, but it does not physically do anything. I attempted to boot the livecd with the following options and their combinations:

1) i8042.nomux=1
2) i8042.noloop=1
3) i8042.reset

No dice. In addition, when I boot into Windows, I find the touchpad has been disabled, so I have to press Fn+F7 to get it recognized in Windows again. Given I could not find a solution, I moved to 11.10...

Edit: This same issue is also present in both 12.10 alpha3, and the latest daily build of 12.10 as of 8/7/2012.

---

On 11.10 live cd, I booted up with the default options and I got a garbled screen -- probably due to nouveau and the newer GK107 based NVIDIA card on this laptop, but I knew the clickpad was active because the screen flickered in all it's garbled glory. Next, I booted the 11.10 livecd as:

boot: live nomodeset

That got me a working display and a somewhat working clickpad. Here is what works and what doesn't:

Works:
1) left click* (a bit erratic if finger is in movement -- tends to select text/icons otherwise -- see 'Does not work' #2)
2) Right click a la Mac (two finger multitouch click)
3) Left click (via tappping anywhere on clickpad)
4) Dragging windows (or any object) via double tap and hold
5) General top/left/right/bottom movements

Does not work:
1) (Emulated) right clicks -- clicks on the lower right portion of touchpad
2) Dragging windows (or any object) via left click
3) Pinch to zoom
4) Two-finger scrolling

Here are my questions:

(A) Are there fixes for the 'Does not work' items in 11.10? If so, what are they?

(B) How do I go about getting my touchpad to work 12.04/12.10 to see if the issues present in 11.10 have been fixed?

Since I have the machine with me, and two flash drives with Ubuntu 11.10/12.04 live CD, I can do further testing via terminal commands as need be and file a bug with any relevant information.

To start, I have attached some output from DebuggingTouchpadDetection page under the heading of: "In case Touchpad features like scrolling, tapping, etc do not work at all." under 11.10.

---

### Post by vacaloca on 2012-08-08
Bump with new information -- this does not seem isolated to Ubuntu distributions. The latest Fedora live CD behaves exactly any of the latest Ubuntu 12.04/12.10 live cd's -- the trackpad does not work at all.

OpenSUSE 12.1 behaves similar to Ubuntu 11.10, but is missing the right-click a la Mac functionality described above.

Also, It surprises me that a well-written post with plenty of information gets no replies... Maybe next time I should start a thread with: 'My trackpad doesn't work' :p

---

### Post by vacaloca on 2012-08-09
bump again, Has anyone else with clickpads had the problem of not being able to move the mouse or have the buttons to anything at all when they boot from a live CD? Once I can actually get it to work, I can try some of the patches that I've seen floating around for 12.04, but having the trackpad do something to begin with is a bit necessary.

---

### Post by vacaloca on 2012-08-09
I marked this as solved since I found a suitable fix. Apparently my idiocy was to try things from a Live CD without updating to newer kernel/packages. I installed and updated Ubuntu 12.04 fully.

Upon updating to kernel 3.2.0-27, clickpad functionality could be enabled/disabled with Fn+F7. I also noticed that xserver-xorg-input-synaptics package was updated to version: 1.6.2-1ubuntu1~precise1.

The new synaptics package supports two-finger scrolling quite well, both horizontally and vertically. Click and drag works. The only thing missing is the right-click functionality, which I have detailed a fix for in the post below.

Other quirks for the M5-481TG laptop and their solutions:

To enable screen brightness settings changing, I had to add ```
acpi_brightness=vendor
``` to the kernel boot options.

To enable the NVIDIA GT640M LE card, I used the current stable version of bumblebee.

Since I could care less about nouveau driver -- I want to run CUDA code using the native NVIDIA driver, and because nouveau seemed to conflict with bumblebee I disabled and blacklisted it. Next, I removed any instances of the nvidia driver that could be found. Then, I add repository for NVIDIA beta drivers. Finally I add bumblebee repository, update and install bumblebee:

```

sudo -i
apt-get --purge remove xserver-xorg-video-nouveau
echo blacklist nouveau > /etc/modprobe.d/blacklist-nouveau.conf
apt-get --purge remove nvidia-current
add-apt-repository ppa:upubuntu-com/nvidia-unstable
add-apt-repository ppa:bumblebee/stable
apt-get update
apt-get install bumblebee bumblebee-nvidia

```

I also had to change a few lines in /etc/bumblebee/bumblebee.conf slightly with the help of other posts I found. The 304.22 driver module name changed from "nvidia-current" to "nvidia", and thus the changes below are needed:

1) Change "Driver=" (auto-detect) to "Driver=nvidia"
2) Change KernelDriver=nvidia-current to KernelDriver=nvidia

Also in /etc/bumblebee/xorg.conf.nvidia I had to change the line:

```
Option "ConnectedMonitor" "DFP"
```

with either of the following:

```
Option "ConnectedMonitor" "CRT-0"
Option "UseDisplayDevice" "none"
```

These last changes fixed the error I was experiencing when running "optirun glxgears" to test bumblebee. The error itself was: [ERROR]Cannot access secondary GPU - error: [XORG] (EE) NVIDIA(0): Failed to assign any connected display devices to X screen 0

---

So with those changes, the brightness up/down keys work, NVIDIA card can be used to run apps/programs via optirun, and touchpad problems are pretty much all fixed -- click and drag is still a little bit wonky, but I'm sure it will get better with newer xserver-xorg-input-synaptics releases. :)

Oh, one more thing. <sarcasm> Thanks for the help everyone! :p </sarcasm>

That being said, I'm glad other people had the problem with bumblebee, otherwise I would have never figured out how to make it work correctly.

---

### Post by vacaloca on 2012-08-09
Figured I'd make one last post on the subject in re: fixing the right-click behavior:

From the synaptics man page: ```
man synaptics
```

```
       Option "SoftButtonAreas" "RBL RBR RBT RBB MBL MBR MBT MBB"
              This  option is only available on ClickPad devices.  Enable soft
              button click area support on ClickPad devices.  The  first  four
              parameters  are  the  left, right, top, bottom edge of the right
              button, respectively, the second four parameters are  the  left,
              right,  top, bottom edge of the middle button, respectively. Any
              of the values may be given as percentage of the  touchpad  width
              or height, whichever applies.  If any edge is set to 0, the but&#8208;
              ton is assumed to extend to infinity  in  the  given  direction.
              Setting  all  values to 0 disables soft button areas.  Property:
              "Synaptics Soft Button Areas"

```

Got this property from here: [http://ubuntuforums.org/showpost.php?p=11877900&postcount=4](http://ubuntuforums.org/showpost.php?p=11877900&postcount=4)

Just the addition of the SoftButtonAreas setting in the post linked above worked for me, but you can change the values according to your particular tastes.

I added the setting in /usr/share/X11/xorg.conf.d/50-synaptics.conf
For me, the values are acceptable, so I'm calling the right-click issue solved as well.

---

### Post by mrenganathan on 2012-08-23
I am facing the same problem and i am new to ubuntu. Could you please let me know how you update the kernel. Thanks in advance

---

### Post by vacaloca on 2012-09-04
> **mrenganathan said:**
> I am facing the same problem and i am new to ubuntu. Could you please let me know how you update the kernel. Thanks in advance

Sure, it's pretty easy to update the kernal and the rest of the system. Once you've installed it and reboot into the system installed to the hard disk, open up a terminal window and type:

```
sudo apt-get update && sudo apt-get upgrade
```

Edit:

The usual PPA that has the latest (non-beta) NVIDIA drivers has been updated with the latest drivers that support CUDA 5. In post #4, it is suggested to replace:

```
sudo add-apt-repository ppa:upubuntu-com/nvidia-unstable
```
with:
```
sudo add-apt-repository ppa:ubuntu-x-swat/x-updates
```

Also, important, sometimes even with the updates installed, the mouse does not work upon a reboot. If this is the case, power off and power on again, and Fn+F7 key (or the key that enables/disables your clickpad should make it work.

---

### Post by jlapier on 2012-09-30
vacaloca, thanks SO much for posting your fixes. If not for you, I'd be stuck using Windoze on my new Acer. 

One quesiton I have - what file did you change to add the brightness settings?

> **vacaloca said:**
> 
To enable screen brightness settings changing, I had to add ```
acpi_brightness=vendor
``` to the kernel boot options.


I put this in /etc/default/grub (in the GRuB_CMDLINE_LINUX_DEFAULT line) and ran update-grub and I can see it if I hit 'e' at the grub menu, but it's not having any effect.

One more thing to add, as far as the touchpad spottiness goes: what I have discovered is that I have to turn on the touchpad (fn-f7) BEFORE I log in; in other words, when it boots to the password prompt, that's when I have to hit it. If I log in and then try to hit it, the key has no effect. 

Everything else - nvidia drivers, right-click (two-finger double tap mac style), two-finger scrolling - working great!

---

### Post by evilhiryu on 2012-10-03
> **jlapier said:**
> vacaloca, thanks SO much for posting your fixes. If not for you, I'd be stuck using Windoze on my new Acer. 

One quesiton I have - what file did you change to add the brightness settings?



I put this in /etc/default/grub (in the GRuB_CMDLINE_LINUX_DEFAULT line) and ran update-grub and I can see it if I hit 'e' at the grub menu, but it's not having any effect.

One more thing to add, as far as the touchpad spottiness goes: what I have discovered is that I have to turn on the touchpad (fn-f7) BEFORE I log in; in other words, when it boots to the password prompt, that's when I have to hit it. If I log in and then try to hit it, the key has no effect. 

Everything else - nvidia drivers, right-click (two-finger double tap mac style), two-finger scrolling - working great!


Hello friend, I have the same problem with the touchpad I have to press fn + F9 to start the machine to work.

've found a solution for this?

Thank you.

---

### Post by evilhiryu on 2012-10-03
type this in a console

```
sudo gedit /etc/default/grub 
```and the line 

 GRUB_CMDLINE_LINUX_DEFAULT "quiet splash"

put this 

```
GRUB_CMDLINE_LINUX_DEFAULT "quiet acpi_brightness=vendor"
```

save, update grub and restart O:)
(that works for me)


if anyone knows how to sort out "fn + f7" on startup. I would appreciate. :P

---

### Post by jlapier on 2012-10-07
So odd... adding ```
acpi_brightness=vendor
``` did not work for me. The keys were working and you could see the brightness indicator go up and down, but the actual screen brightness did not change.

I changed it to: ```
acpi_backlight=vendor
``` and that worked (found here: [http://askubuntu.com/questions/128463/brightness-controls-dont-work-on-an-acer-4741g](http://askubuntu.com/questions/128463/brightness-controls-dont-work-on-an-acer-4741g)). I don't know if this is a difference between Ubuntu versions or something else odd. I'm running 12.04, 64bit.

---

### Post by fcastillo on 2012-10-17
I just bought the same laptop. I updated my machine and now everything is working perfectly. I do have a question regarding how you installed Ubuntu.
This is the first machine I buy with a SSD and HDD drives, I didn't want to delete windows completely for warranty just in case. So I partitioned the hard drive to keep windows but with very little space. I'm just not sure what the SSD drive has in it, since it came partitioned, and I'm not sure what I should install there. It's not a really big drive, but enough for Ubuntu to be installed and /home to be in the HDD. Is this the best configuration?
How can I use the SSD for my advantage for fast boot, or/and fast hibernation/sleep?
Is there a particular configuration I should do to make my laptop extremely fast?

---

### Post by fcastillo on 2012-10-18
> **jlapier said:**
> 
One more thing to add, as far as the touchpad spottiness goes: what I have discovered is that I have to turn on the touchpad (fn-f7) BEFORE I log in; in other words, when it boots to the password prompt, that's when I have to hit it. If I log in and then try to hit it, the key has no effect. 

Everything else - nvidia drivers, right-click (two-finger double tap mac style), two-finger scrolling - working great!

Has anybody found a solution for this? This is still unacceptable behaivor. Quatal was released today, I tried the live cd and the mouse didn't work, mainly because there isn't a log in window.
In the case I have automatic log in (and this is always the case for me) my laptop's touchpad never works!
Is there a way to fix this? Anybody?

---

### Post by vacaloca on 2012-10-22
> **jlapier said:**
> So odd... adding ```
acpi_brightness=vendor
``` did not work for me. The keys were working and you could see the brightness indicator go up and down, but the actual screen brightness did not change.

I changed it to: ```
acpi_backlight=vendor
``` and that worked (found here: [http://askubuntu.com/questions/128463/brightness-controls-dont-work-on-an-acer-4741g](http://askubuntu.com/questions/128463/brightness-controls-dont-work-on-an-acer-4741g)). I don't know if this is a difference between Ubuntu versions or something else odd. I'm running 12.04, 64bit.

This is correct, I looked back at my settings and indeed had ```
acpi_backlight=vendor
``` I wrote my last post in a bit of a hurry, ha!

> **fcastillo said:**
> Has anybody found a solution for this? This is still unacceptable behaivor. Quatal was released today, I tried the live cd and the mouse didn't work, mainly because there isn't a log in window.
In the case I have automatic log in (and this is always the case for me) my laptop's touchpad never works!
Is there a way to fix this? Anybody?

File a bug for us :) I'm not sure what's at fault, but it might be the kernel.

---

### Post by vacaloca on 2012-10-22
> **fcastillo said:**
> I just bought the same laptop. I updated my machine and now everything is working perfectly. I do have a question regarding how you installed Ubuntu.
This is the first machine I buy with a SSD and HDD drives, I didn't want to delete windows completely for warranty just in case. So I partitioned the hard drive to keep windows but with very little space. I'm just not sure what the SSD drive has in it, since it came partitioned, and I'm not sure what I should install there. It's not a really big drive, but enough for Ubuntu to be installed and /home to be in the HDD. Is this the best configuration?
How can I use the SSD for my advantage for fast boot, or/and fast hibernation/sleep?
Is there a particular configuration I should do to make my laptop extremely fast?

For ubuntu, unless there are any Intel Rapid Start drivers (I do not believe so) the fast resume from sleep done from the MSATA SSD would not be possible. The first partition on the SSD is the hibernation partition, that stores the 'deep sleep' information in windows when Rapid Start is enabled. The second partition on the SSD by default is used by disk caching software in Windoze, and same thing applies... do not think there are equivalent Linux drivers to accomplish the same thing, as the company's software looks pretty closed source.

I frankly replaced both hard drives... my main drive is a Samsung 930, my secondary a (much bigger) MSATA SSD -- 256 GB. I recreated the hibernation partition on it for Windoze, and installed Ubuntu on part of the rest, leaving the remaining space accessible between Windows/Linux as a data partition.

---

### Post by animeking77 on 2012-10-29
Just wanted to let you guys know that I use Linux Mint, and for me to get the mouse to work (I have the same laptop) I just pressed "ctrl+fn+f7." I saw that solution somewhere awhile ago, and it happened to work for me.

---

### Post by sean.leber on 2012-11-04
So, I noticed some inconsistency with the touchpad out of the box with ubuntu 12.10, however, once I updated the kernel to 3.6.3 I had no problems (just remember to do CTRL+Fn+F7 in order to turn on the touchpad, Fn+F7 won't do it on its own).

I'm using an Aspire TimelineU 481 with the elantech touchpad, its working just fine now - the only thing i have to do is the CTRL+Fn+F7 after rebooting in order to get the touchpad back.

--- I WAS GOING TO GIVE INSTRUCTIONS ON HOW TO UPDATE THE KERNEL, BUT UBUNTU FORUMS DOESN'T RECOMMEND THAT PEOPLE USE SCRIPTS FROM UNTRUSTED SITES ---

So follow these instructions at your own risk (they worked for me):
[http://hashprompt.blogspot.com/2012/10/upgrading-linux-kernel-363-stable.html](http://hashprompt.blogspot.com/2012/10/upgrading-linux-kernel-363-stable.html)

Also, I installed linux mint on my laptop, and it was a mess.  I like the gnome 3 interface (I know, I might be the only one) but it was nearly impossible to get it installed with mint 13, which was disappointing (and apparently is a known issue - there is a conflict between gdm and mdm, which 'mate' uses.)

---

### Post by jim.basilio on 2012-11-07
just got this laptop and wanted to say the acpi_backlight=vendor for backlight adjustment and cntrl-fn-F7 for touchpad worked wonderfully!  thank you!!

Also, if you don't know how to add kernel parms, I found this link:
[https://wiki.ubuntu.com/Kernel/KernelBootParameters](https://wiki.ubuntu.com/Kernel/KernelBootParameters)

thanks to you guys my new laptop is running perfectly now!!

---

### Post by beidl on 2013-01-10
I got myself a M5-481TG 2 days ago because I was a little bit pissed off of AMDs support for switchable graphics on laptops,
somehow I trust a community driven hack like Bumblebee more than AMD (and OMG that thing works nicely!!).
The trackpad being disabled after every reboot was a bit annoying, so I dug around the interwebs and found out that the acer_wmi kernel module is known to disable touchpads on init.
So, the quick fix for this was:
```
echo "blacklist acer_wmi" | sudo tee /etc/modprobe.d/acer-wmi.conf
```
Luckily, on the M5-481TG the function keys for brightness, volume etc are managed by the hardware.
Disabling the touchpad also still works, but with acer_wmi disabled there's no notification shown when toggling it.

---

### Post by whoever30 on 2013-06-20
> **beidl said:**
> 
The trackpad being disabled after every reboot was a bit annoying, so I dug around the interwebs and found out that the acer_wmi kernel module is known to disable touchpads on init.
So, the quick fix for this was:
```
echo "blacklist acer_wmi" | sudo tee /etc/modprobe.d/acer-wmi.conf
```.

:idea:THIS SOLUTION SHOULD BE STICKY ON A BETTER PLACE OF THE FORUM!:idea:

thx 'homie' (thus between quotation marks) 4the solution:!:

---

