---
title: "Terrible Battery life on Aspire 4733z"
date: 2011-08-16
forum: Hardware
---

### Post by SGAShepp on 2011-08-16
I have an brand new Acer Aspire 4733z. In Windows I can get about 5 hours of battery life general use, less than half that in Ubuntu 11.04.
There are a few things I notice..

#1. The bottom of the laptop gets noticeably warmer in Ubuntu vs win7.
#2. The display brightness slider (fn key) will move the notification slider but will not change the brightness at all (all other fn functions work)
#3. In win 7 the LED back-light with automatically slowly dim and brighten on battery (asside from the manual brightness adjustments) I dont know if this some 'Acer' feature or something that all LED back-lighted displays do, nevertheless it also doesn't work in Ubuntu.
#4 Battery life drains even in standby, I had but it in standby with about 50% battery left and came back 4 hours later to find it was 100% dead.

I have not tried a 64bit version of Ubuntu, with this Pentium T4500 dualcore which I believe is 64bit. Is that the problem or is it something else?

This battery life problem is the ONLY thing holding me back from using Ubuntu as my main OS.
OH. and the battery menu in ubuntu states the battery is at 99.9 capacity. so I doubt that to be the issue.
Please Help I Appreciate it very very much!

---

### Post by SGAShepp on 2011-08-18
Help Pleaseee. or tell me where I can get help for this?

---

### Post by Mars11 on 2011-08-18
It sounds like it might not even go to sleep.

---

### Post by SGAShepp on 2011-08-19
I had thought about that. Though the power light does turn orange. I guess Ubuntu just isn't ready for laptops out of the box. There has to be something..

---

### Post by SGAShepp on 2011-10-13
Please anyone with this issue? its now with 11.10 with the same identical problem. I'm sure its more than just this laptop too. Seems to be an acpi problem, not just with the screen itself. I don't think the CPU uses the same low-power mode as in windows, among other things..
I am getting desperate, I feel like Ubuntu is going to ruin my battery.

I found a way to adjust the brightness by modifying grub, however it seems crude. It doesn't even adjust with the the OSD slider properly.

Any help would be gold.

Thanks!!

---

### Post by Redblade20XX on 2011-10-13
For problem #4, check  if you have WOL (Wake On Lan) enabled in the bios menu. :p

[https://help.ubuntu.com/community/WakeOnLan](https://help.ubuntu.com/community/WakeOnLan)

-Red

---

### Post by Vand3lay on 2011-10-13
[FONT=Arial][SIZE=2]How did you check your battery capacity? I remember my old aspire 4535's battery was lasting less than 10 minutes and ubuntu would give me a warning saying the battery was damaged, so I replaced it with a cheap one on eBay which ended up breaking my laptop, so now I have a 4733z as well. Currently I get about 5hrs on windows (with under clocking to 50% and brightness dimmed as low as possible) which I need since I don't have very many chances to charge during the day. Ubuntu shouldn't ruin your battery and my laptop is running about the same temperature as windows but a reduced life = more charging = more charge cycles which does reduce it's capacity.

The power issue with ubuntu right now is in the linux kernel (according to phoronix they changed something with ACPI) so it affects most distributions and a large number of laptop models, but personally I've never had great battery life with ubuntu and it's always been around half of windows. Here are some manual boot options you can try to fix this with [https://help.ubuntu.com/community/BootOptions#Common_Kernel_Options](https://help.ubuntu.com/community/BootOptions#Common_Kernel_Options)

Some ways I found to extend battery life on Ubuntu were slowing down the processor, this indicator makes it pretty simple [http://auroraos.org/project/jupiter](http://auroraos.org/project/jupiter) you can also try this one, [http://www.omgubuntu.co.uk/2011/02/battery-applet-status-ubuntu/](http://www.omgubuntu.co.uk/2011/02/battery-applet-status-ubuntu/)

To disable a cpu core (I used this back in maverick but it should still work)
echo 0 | sudo tee /sys/devices/system/cpu/cpu1/online
and bring it back up
echo 1 | sudo tee /sys/devices/system/cpu/cpu1/online

Also dimming the brightness all the way which you've done, and for anyone else looking the workaround is here [http://eftakhairul.com/adjust-the-brightness-on-acer-aspire-4740-in-ubuntu/](http://eftakhairul.com/adjust-the-brightness-on-acer-aspire-4740-in-ubuntu/)
Basically just run 
sudo gedit /etc/default/grub 
and make sure the you have these lines
GRUB_CMDLINE_LINUX_DEFAULT="quiet splash"
GRUB_CMDLINE_LINUX="acpi_osi="
and then run 
sudo update-grub

Also changing from Unity3d to Unity2d and disabling any other graphical effects should help, as of now I've been using oneiric for around 20 minutes and my battery has gone down 20%
[/SIZE][/FONT]

---

### Post by Vand3lay on 2011-10-13
A specific case of the power bug reported by phoronix was fixed here and hopefully this is improved with the next release, I agree with you that battery life is the main thing keeping me back from using Ubuntu as my main OS too. [https://bugs.launchpad.net/ubuntu/+source/linux/+bug/760131/comments/201](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/760131/comments/201)

---

### Post by SGAShepp on 2011-10-17
Thanks for the replies!

Vand3lay,

The battery Capacity is indicated at 97.5 in Ubuntu itself (which is kindof surprising considering its brand new!)

I was interested and tried installing the "OMGUbuntu" link you provided. however apparenly its no longer in the repo's or something, it could not be found when I tried installing it :(

However I stumbled upon something interesting while browsing synaptic package manager. 
"apmd - Utilities for Advanced Power Management (APM)"
I am curious if anyone has had luck with this package.

Other than that, Next time I unplug, I'm going to try disabling a core AND run in unity2d as you've suggested and I'll get back with the results!

EDIT:
Here are some pictures of powertop. This is with jupiter on power save mode.
[IMG]https://lh4.googleusercontent.com/-lJ532W2GLpk/TpxEJqTJjDI/AAAAAAAAAMY/gz0ycbSpetA/s800/Screenshot%252520at%2525202011-10-17%25252010%25253A51%25253A36.png[/IMG]
[IMG]https://lh6.googleusercontent.com/-qVfxzIoYAFk/TpxEJseXA_I/AAAAAAAAAMc/CUEmka8NV40/s800/Screenshot%252520at%2525202011-10-17%25252010%25253A51%25253A52.png[/IMG]

---

### Post by Redblade20XX on 2011-10-17
APM was superseded by ACPI if I'm not correct. So unless your computer is really old, APM will work but for newer computers it will lack in power management capabilities.

- Red

---

### Post by SGAShepp on 2011-10-17
> **Redblade20XX said:**
> APM was superseded by ACPI if I'm not correct. So unless your computer is really old, APM will work but for newer computers it will lack in power management capabilities.

- Red

Gotcha.

Well, With running on a single core in 2d mode, powertop now reports a power drain of 10.1 W. as opposed to about 15 W When I first posted and 13.5 in Ubuntu 3d w/ 2 cores. If that's about what everyone else is able to achieve. I guess I can deal with it until they fix the issue.

Any more tips to save power?

Oh.. 2 more thing. is there any way to have it automatically drop a core when i unplug or no.. its probably unreasonably complicated to do so if even possible lol.

---

### Post by Vand3lay on 2011-11-05
Sorry I'm really busy right now, I'm in the middle of midterms, but that's great how well it's working now, I don't know how much power windows uses since I don't know of any powertop equivalents but I found a couple more fixes which should get you very close to if not better life than windows!

As of writing this post I am at 9.45W (~2hrs left with ~50% battery), and I'm still using Unity 3d with all it's nice effects and a bunch of other ones along with cairo dock. However my system is currently a mess as a result of trying pretty much every fix I could and also getting unity to work the way I want (finally happy enough to stick with it) I plan of finding out exactly what works and what didn't after a clean install in a few weeks. Most of my information is coming from [http://www.lesswatts.org/](http://www.lesswatts.org/)

For now here's what I did that seemed to work
Enabled ASPM [http://www.webupd8.org/2011/06/linux-kernel-power-issue-fix.html](http://www.webupd8.org/2011/06/linux-kernel-power-issue-fix.html)
Basicall go back to 
/etc/default/grub
and change 
GRUB_CMDLINE_LINUX_DEFAULT="quiet splash"
to
GRUB_CMDLINE_LINUX_DEFAULT="quiet splash pcie_aspm=force"

This script has some useful commands (some don't work anymore, I just ran the entire script) [http://www.carstenboysenjensen.com/downloads/savebattery.sh](http://www.carstenboysenjensen.com/downloads/savebattery.sh)

I also installed laptop-mode-tools and cpufreqd, I don't remember how well I followed this guide but it has some more useful tips
[http://www.totalnetsolutions.net/2007/08/13/how-to-increase-battery-life-in-ubuntu-or-debian-linux/](http://www.totalnetsolutions.net/2007/08/13/how-to-increase-battery-life-in-ubuntu-or-debian-linux/)

Hopefully Canonical will make some of these fixes automatic in 12.04 LTS since they do tend to focus more on stability and bugs in those releases. We will probably see some improvement but make note of the different tweaks/commands/tools you're using since most will probably still apply.

---

### Post by Vand3lay on 2011-11-05
Sorry I forgot, to drop/add a core on plugging in your charger, I don't know how to trigger an event based on that, there probably is a tool for that but what I did was just put the command in a text file and save it as a shell script (.sh) and just left it on my desktop so I could quickly run it.

---

### Post by SGAShepp on 2011-11-07
Thanks for the reply! I will give you suggestions a shot when I have time. I really appreciate your detailed help, Thanks again.

---

