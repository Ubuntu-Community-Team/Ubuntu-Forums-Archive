---
title: "Asus U31SD"
date: 2011-05-20
forum: Hardware
---

### Post by Humphreybas on 2011-05-20
Since there was no topic about the asus u31 I started this thread to collect fixes.

[SIZE=2][COLOR=DarkSlateGray]**Note: The info in this post is old, please read the whole thread untill I have time to update this**  [/COLOR][/SIZE][COLOR=DarkSlateGray]
[/COLOR] 
[SIZE=2]**Optimus and the NVIDIA GT 520M**  [/SIZE]
Out of the box the nvidia card is consuming power but not doing anything. On top of that desktop effects don't work (no unity no compiz). 
One option is to turn off the nvidia card to save power in case you don't need the nvidia performance. However this might be unnecessary since the  [bumblebee]("https://github.com/MrMEEE/bumblebee/")  project is giving great results. I myself first disabled the Nvidia before trying out the [bumblebee]("https://github.com/MrMEEE/bumblebee/") so I don't know if that disabling step makes any sense if you will use the bumblebee fix.

[SIZE=1][B]Disable NVidia GPU/NVidia Optimus (might not be necassary)
[/B][/SIZE]Execute the steps as described in the following link at the appropriate section:
However where \_SB.PCI0.PEG1.GFX0._OFF is used, use [SIZE=1]**\_SB.PCI0.PEG0.GFX0.DOFF**[/SIZE]   instead and the same holds for \_SB.PCI0.PEG1.GFX0._ON -> [SIZE=1]**\_SB.PCI0.PEG0.GFX0.DON**[/SIZE]
link: [http://ubuntuforums.org/showpost.php?p=10551449&postcount=1](http://ubuntuforums.org/showpost.php?p=10551449&postcount=1)


[SIZE=1]**Using the Bumblebee solution to switch graphics**[/SIZE]
First get the software:
```
sudo apt-get install git 
git clone https://github.com/MrMEEE/bumblebee.git
```Now install it
```
cd bumblebee
sudo bash install.sh
```At the end of the install procedure it gave me an error (something with newline at 743 of install.sh). Ignore this error since all the essential work has been done already. 
Now log off and log on.
Now you should have desktop effects (compiz / unity). And your power usage should be down to 7000-8000:
```
       grep rate /proc/acpi/battery/BAT0/state
  
```[SIZE=2][B]
Suspend and Hibernate[/B][/SIZE]
(adapted from [http://ubuntuforums.org/showpost.php?p=10551449&postcount=1](http://ubuntuforums.org/showpost.php?p=10551449&postcount=1))

The problems are caused by the USB buses (more info elsewhere on the forums).
In the script below also the nvidia card is turned on again, this assumes you have done the "[SIZE=1][SIZE=1]Disable NVidia GPU/NVidia Optimus[/SIZE]**"**[/SIZE] when you use the bumblebee project this might not be necassairy.

```
gksu gedit /etc/pm/sleep.d/20_custom-asus-u31sd
```INSERT BELOW TEXT

```
#!/bin/sh

BUSES="0000:00:1a.0 0000:00:1d.0"

case "${1}" in
    hibernate|suspend)
    # Switch USB buses off
    for bus in $BUSES; do
        echo -n $bus | tee /sys/bus/pci/drivers/ehci_hcd/unbind
    done
    # Switch optimus back on before going to sleep, avoids the "constant on"
    # bug that occurs after 2 suspend/resume cycles (thanks kos888)
    /etc/init.d/optimusoff stop
    ;;
    resume|thaw)
    # Switch USB buses back on
    for bus in $BUSES; do
        echo -n $bus | tee /sys/bus/pci/drivers/ehci_hcd/bind
    done
    # Switch optimus off before resuming, avoids unneccessary power draw
    /etc/init.d/optimusoff start
    ;;
esac
```Next just make it executable
```
sudo chmod +x /etc/pm/sleep.d/20_custom-asus-u31sd
```[SIZE=2]**Issues to be fixed**[/SIZE]
This was written in a hurry and this post is still quite immature, so some of these things might be easy to fix, I just didn't look at it in detail:
-check whether the bumblebee project alone can fix issues with the optimus (not doing the disable thing)
-Get all the fn-keys to work
currently working: sleep (F1) wireless switch (F2) brightness (F5 F6) screen switch (F7)
important not working fn-keys: volume and music player controls
untested: switching external monitor

---

### Post by dugh on 2011-05-21
Even with bumblebee installed in 11.04 though, I don't see any option to enable compiz.  There seems to be an nvidia bug in general with enabling compiz.
I tried the command line tool that is required now to report bugs, and it rejected my bug report because it said I was using the nvidia proprietary driver.

Ubuntu 10.10 worked just fine.  There are so many regressions in 11.04 now that I can't keep track anymore.

---

### Post by Humphreybas on 2011-05-21
Hmm strange, after a fresh install of 11.04, disabling the nvidia and then installing bumblebee did the trick for me. Compiz worked straight away after a reboot (ubuntu classic chosen at startup). Compiz configured with compizconfig settings manager.

---

### Post by somhi on 2011-06-26
I'm interested in buying this laptop, but I couldn't find too much information about it.

Humphreybas & dugh, could you please do an update of the issues you have found/solved working with ubuntu since your initial posts and a little review of it.

Thanks!

---

### Post by Humphreybas on 2011-07-07
With the fixes from the start post you can comfortable run ubuntu. No significant problems whatsoever.

Recently I encounter odd freezes after I closed the lid (no suspend/hibernate just blank screen), the cursor moves fine but clicking and key presses have no effect. You could call that significant but since it started recently I can't really say what the cause is.

---

### Post by somhi on 2011-07-08
Thanks mate,  I'm just waiting from the supplier to have it.

---

### Post by Tuomas Jäntti on 2011-08-12
I have installed Ubuntu 10.04 on my (wifes) new Asus U31SD and have been trying to get the display, battery, hibernate and suspend issues fixed. Thank you for your good information, it gives hope that everything will work fine some day.

I first installed bumblebee from git and the battery consumption went down as intended. But the hibernation and suspend did not work. Actually they did not work before bumblebee installation. Without the Asus-specific script suspend and hibernate resulted in stuck system. Enabling the script did not help me either. The script returned something about non existing devices while trying to shut down usb buses. This prevented the suspend and hibernate scripts from going to sleep if(!) I understood it correctly.

Then I installed TuxOnIce. Now hibernation worked (suspend not) but power consumption was back to big. I could not get bumblebee to work with TuxOnIce. I will wait for the new version of bumblebee before trying more with it. Should be soon:
[https://github.com/Bumblebee-Project/Bumblebee/issues/15]("https://github.com/Bumblebee-Project/Bumblebee/issues/15")

The one thing that I think affects usability even more than power consumption and suspend modes is the video resolution. Has anybody managed to configure Xorg for something near 1366x768? If so, please help. nvidia-closed-source, nouveau, intel-on-board, vesa, anything? I have nouveau installed (Ubuntu default). The screen resolution is always max 1024x768 whatever I try with or without /etc/X11/xorg.conf

Thanks

---

### Post by Tuomas Jäntti on 2011-08-13
Reading through /var/log/Xorg.0.log X always ends up using vesa 1024x768. The correct resolution (1366x768) was correctly reported by the hardware which is positive anyway.

The drivers that are directly supported (installable without extra repositories or other such means) by Ubuntu 10.04 seem to be quite old. The package nvidia-current offers 195.36.24 which does not support gt520m. The open source nv-driver does not seem to recognize the card. Btw. in what package is this driver located? Does an upgrade require upgrade of the whole xorg meta-package?

Several questions have arisen. I wonder if somebody has advice concerning this issues:

1. Distribution and release

I have a feeling that Ubuntu 10.04 is not the right distribution and release because the software needed to run this hardware should be more recent.

I could try with 11.04. Is it worth while? dugh mentioned many regressions in it. 

I can also keep 10.04 and try to install things from alternative sources and git. This probably will not work well due to too many old pieces of software around?

I could also install Arch linux on a separate partition and try things out there. If solutions work are found I might be able to apply them also to the Ubuntu environment. I am not willing to maintain this computer on Arch as a permanent solution because I am not the main user.


2. Display driver

I am still confused with the alternatives and hierarchy of different display related drivers concerned. I am wondering which of the alternatives is the likely way to get things working:

The closed source nvidia driver 270.41.06 supports gt520m according to the download page. Does it work with this optimus setup computer. I know that the optimus features support is developed in the bumblebee project, but does this work otherwise?

There is also this xorg nv-driver. Does some version of this support this hardware? Should I try to upgrade this?

I have xserver-xorg-video-nouveau 1:0.0.15+git201002219+... installed. This is also probably too old if the name contains a date? Should this be upgraded? Does a newer version work for somebody?

What about the other chip Intel GMA HD. Should I do something about that too?

Thanks.

---

### Post by Tuomas Jäntti on 2011-08-14
Replying to my own questions :)

I tried Ubuntu 11.04 with rather good results. I got it working sufficiently well enough for my needs. The following might be helpful for someone who wants to get Ubuntu running quickly on a new Asus. This installation requires an external dvd-player.


1. Download and burn the Installation CD for Ubuntu 11.04. 

Do not select version 10.04. It does not work well on this laptop.

[http://www.ubuntu.com/download/ubuntu/download](http://www.ubuntu.com/download/ubuntu/download)

Install Ubuntu.


2. Partition your disk and install Ubuntu.

I kept the Windows recovery and the Windows installation intact. The windows installation had a data partition ( d:\ ). I deleted that and created an extended partition that contains three logical partitions for swap, root and home.

Here are instructions for partitioning and installing. They are installing a previous version of Ubuntu but it is close enough. I wouldn't try resizing the actual Windows partition ( c:\ ) as they did.

[http://www.dedoimedo.com/computers/dual-boot-windows-7-ubuntu.html]("http://www.dedoimedo.com/computers/dual-boot-windows-7-ubuntu.html")

Start Ubuntu from the installation cd and enable your wlan connection before starting the installation. 

After installation update the system with Update Manager. Btw. system settings can be found by right-clicking the shutdown icon on the top right corner of the screen.


3. What to do about the display driver?

Ubuntu recommends to install the nvidia closed-source driver. It did not work me. I did not try nouveau. Nouveau is installed by default but X used the Intel driver anyway. The default already installed Intel driver works well enough for me for now. Resolution is 1366 x 768 which is the native resolution for the display. 60 fps on glxgears will do. Yes, it is sad on a machine that contains a nvidia chip. Unity also works. The nvidia chip will be turned off in the following chapter.


4. Hibernate, Suspend and Saving Power

Install Tux-on-ice:

[https://launchpad.net/~tuxonice/+archive/ppa](https://launchpad.net/~tuxonice/+archive/ppa)

Proceed as Humphreybas instructs you to in his first post. Skip the bumblebee installation if you are not sure you want to install unstable software that is still under development.

This is the contents of my /etc/init.d/optimusoff:

```
#! /bin/sh
### BEGIN INIT INFO
# Provides: 		optimusoff
# Required-Start: 	$local_fs $syslog
# Required-Stop: 	$local_fs $syslog
# Default-Start: 	2 3 4 5
# Default-Stop: 	0 1 6
# Short-Description: 	Disables/Enables the NVidia graphics card
#			within the NVidia Optimus system
#			
#			Modified for the U36Jc and Ubuntu 11.04
#			using details from
#			
#			http://robbyx.net/blog/?p=190
#
#                       Modified further for the Asus U31SD according to
#                       first post by Humphreybas in
#                       http://ubuntuforums.org/showthread.php?t=1763742
### END INIT INFO
 
. /lib/lsb/init-functions
 
set -e
 
case "$1" in
start)
#
echo '\_SB.PCI0.PEG0.GFX0.DOFF' > /proc/acpi/call
# echo "Started optimusoff."
;;
stop)
echo '\_SB.PCI0.PEG0.GFX0.DON' > /proc/acpi/call
# echo "Stopped optimusoff."
;;
*)
echo '\_SB.PCI0.PEG0.GFX0.DOFF' > /proc/acpi/call
N=/etc/init.d/optimusoff
echo "Usage: $N {start|stop}\nBy default, 'start' is executed.\n" >&2
exit 1
;;
esac
 
exit 0

```
 



The fancy Nvidia GeForce GT 520M will be useful with Bumblebee. Please report here if you get it working. I dare not risk my system until it is more stable.

---

### Post by Tuomas Jäntti on 2011-08-16
Now I am just documenting for myself what I have done to get things working. This post is not at all Asus specific. I can move it somewhere else if it disturbs somebody searching for things Asus U31SD specific. I documented it because it took me a surprising amount of searching to find a solution that did not include about 10 rows of apt-get code.

Setting up DVD support:

libdvdread4 is already installed according to package manager. The installation script needs to be run to get libdvdcss2 support.

```
sudo /usr/share/doc/libdvdread4/install-css.sh
```

Source of information was:
[http://www.dreamingisdigital.com/2011/05/13/how-to-play-dvds-in-ubuntu-11-04/]("http://www.dreamingisdigital.com/2011/05/13/how-to-play-dvds-in-ubuntu-11-04/")

---

### Post by WalrusTusks on 2011-08-30
Ok, I've got a U31SD, and here's what I've done:

**[SIZE=3]1. Install Ubuntu 11.10[/SIZE]**
If you need instructions, look elsewhere. They aren't hard to find. :)
However:
> I wouldn't try resizing the actual Windows partition ( c:\ ) as they did.I've resized NTFS Windows partitions many times, and never had a problem. Just don't touch the 100MB Win 7 system partition.(if you have Win 7)


[B][SIZE=3]2. Install Bumblebee
[/SIZE][/B]****
I previously said not to use bumblebee, but to use ironhide instead. I said that because bumblebee didn't turn your nvidia card off, and wasted power. However, bumblebee now supports power management, so I would advise moving back into the main branch of development. So, to install bumblebee, instructions are here:
[https://wiki.ubuntu.com/Bumblebee](https://wiki.ubuntu.com/Bumblebee)
If you already have ironhide installed, there are instructions to upgrade to bumblebee on that page. However, once you've completed them, you need to do ste2p 2 again, as the script for sleeping has changed. Just open the file, delete everything in there, and paste in the new instructions.[B][SIZE=3][SIZE=1]


[/SIZE] 3. Fix Suspending[/SIZE][/B]

This is almost directly copied from Humphreybas's instructions. Thanks, Humphreybas.

The problems are caused by the USB buses (more info elsewhere on the forums).
With the update to bumblebee, you no longer need to turn the card on/off as you suspend, so I've removed that from the script.

```
gksu gedit /etc/pm/sleep.d/20_custom-asus-u31sd
```INSERT BELOW TEXT

```
#!/bin/sh

BUSES="0000:00:1a.0 0000:00:1d.0"

case "${1}" in
    hibernate|suspend)
    # Switch USB buses off
    for bus in $BUSES; do
        echo -n $bus | tee /sys/bus/pci/drivers/ehci_hcd/unbind
    done
    ;;
    resume|thaw)
    # Switch USB buses back on
    for bus in $BUSES; do
        echo -n $bus | tee /sys/bus/pci/drivers/ehci_hcd/bind
    done
    ;;
esac
```Next just make it executable
```
sudo chmod +x /etc/pm/sleep.d/20_custom-asus-u31sd
```**[SIZE=3]4. Multitouch Scrolling[/SIZE]**

To enable Multitouch scrolling, go to Mouse -> Touchpad and choose Two-finger scrolling.

**[SIZE=3]What Doesn't Work[/SIZE]**

1. HDMI output, I don't think. I only tried it once, and in a bit of a hurry, so didn't have time to check fully. If someone has a chance to try in-depth, and with 11.10, please PM me whatever you find.
2. Not all programs work through optirun.

Thanks heaps to Humphreybas for his instructions. He did most of the work here, I've just adapted his instructions.

---

### Post by Holmen on 2011-09-04
Thanks a bunch for that updated guide!

Got mine U31SD the other day and it is now running Ubuntu 11.10 Beta and everything seem to work. Ironhide, mutlimedia keys,multi touch and so on.

Thank you WalrusTusks and Humphreybas!

---

### Post by somhi on 2011-09-06
working as descrived in Ubuntu 11.04.

Hope it doesn't get broken after updates. I'm working with the stock nvidia driver.  I suppose it is best not to install propietary drivers, right?

I want also say Thank you WalrusTusks and Humphreybas!

regards

---

### Post by WalrusTusks on 2011-09-09
> **somhi said:**
> 
Hope it doesn't get broken after updates. I'm working with the stock nvidia driver.  I suppose it is best not to install propietary drivers, right?
That's great that you have it working! I also hope it doesn't break after updates, but there are no guarantees. If you do have any major problems, don't hesitate to PM me, or something.

The drivers you installed would have been the proprietary drivers,(proprietary just means that nvidia doesn't allow you to modify them) but you don't have the latest development drivers. However, if you have it working and like it, there's no point in going to the dev ones. They usually provide only very slight performance benefits, and often break stuff.

---

### Post by Humphreybas on 2011-09-14
Been away for a while, happy to see that things are looking more positive than before. Thanks for everyone's contribution, will check the ironhide soon!

Since the overall view of Ubuntu+Asus U31SD is very good I can now start nagging about the details :p
Anyone of you experienced that the screen brightness setting is quite unstable (for instance when it is low and you close the lid and reopen it the brightness is suddenly full). Is this fixed in 11.10 ?

---

### Post by WalrusTusks on 2011-09-20
> **Humphreybas said:**
> 
Since the overall view of Ubuntu+Asus U31SD is very good I can now start nagging about the details :p
Anyone of you experienced that the screen brightness setting is quite unstable (for instance when it is low and you close the lid and reopen it the brightness is suddenly full). Is this fixed in 11.10 ?

No, it isn't. I think the problem is that using the keyboard shortcuts doesn't actually update the slider in the settings, so it changes, depending on whether it's set from that, or remembers where it was. I may be fixed by the final release of 11.10. (which does some crazy things at the moment, like when you standby, it occasionally doesn't turn the backlight back on at all)

---

### Post by somhi on 2011-10-16
I've just updated to Ubuntu 11.10.  I've noticed that power consumption is now higher than in 11.04.

Output of:
grep rate /proc/acpi/battery/BAT0/state

in 11.10 ranges from 12000 mW minimum to 17000 max (nvidia enabled)
in 11.04 ranged from 8000 mW minimum to 14000 max (nvidia enabled)

Has anyone else noticed this?

Regarding brightness of screen remains unstable.

Regards

---

### Post by gecka on 2011-10-16
> **somhi said:**
> I've just updated to Ubuntu 11.10.  I've noticed that power consumption is now higher than in 11.04.

Output of:
grep rate /proc/acpi/battery/BAT0/state

in 11.10 ranges from 12000 mW minimum to 17000 max (nvidia enabled)
in 11.04 ranged from 8000 mW minimum to 14000 max (nvidia enabled)

Has anyone else noticed this?

Regarding brightness of screen remains unstable.

Regards

Try this: [http://www.webupd8.org/2011/06/linux-kernel-power-issue-fix.html](http://www.webupd8.org/2011/06/linux-kernel-power-issue-fix.html)

Anyway you're lucky, my asus u30sd can't go bellow 17000 mW (nvidia off) ....

I am curious to know your temp values guys, here are mine:

$ sensors
acpitz-virtual-0
Adapter: Virtual device
temp1:        +53.0°C  (crit = +103.0°C)

coretemp-isa-0000
Adapter: ISA adapter
Physical id 0:  +54.0°C  (high = +86.0°C, crit = +100.0°C)
Core 0:         +54.0°C  (high = +86.0°C, crit = +100.0°C)
Core 1:         +51.0°C  (high = +86.0°C, crit = +100.0°C)

---

### Post by Humphreybas on 2011-10-17
acpitz-virtual-0
Adapter: Virtual device
temp1:        +48.0°C  (crit = +88.0°C)

I just upgraded to 11.10, worked fine.

Power usage sometimes around 13W and sometimes around 17W (used to be at 8 )

After reading a bit trough this post I decided to install ironhide (I was still on bumblebee).
But at the step of ironhide-configuration I didn't pass the the running gears test.

BTW: Tuomas Jäntti, how do you mean DVD support?  for running a DVD from an image file?

---

### Post by WalrusTusks on 2011-10-17
+Somhl: I've noticed the same thing with the increased power usage. Biggest pain, cause my favourite thing about this laptop is the awesome battery life, and now it's getting sucked away to do nothing, I'm assuming.

+Humphreybas: Try using "proxy" instead of "XV" at the ironhide configuration.

---

### Post by gecka on 2011-10-17
I think we may join forces on that bug: [https://bugs.launchpad.net/ubuntu/+source/acpi/+bug/876335](https://bugs.launchpad.net/ubuntu/+source/acpi/+bug/876335) it is for U30SD but hardware seems about similar to US31D

---

### Post by Humphreybas on 2011-10-18
@WalrusTusks: 'initial test' failed but gears worked anyway and seems to run fine now! thank you
@gecka: it seems that this isnt a laptop specific issue: [http://www.phoronix.com/scan.php?page=news_item&px=OTg5NA](http://www.phoronix.com/scan.php?page=news_item&px=OTg5NA)
After some tweaking I got my power usage back to +/-8W read below:

Also: Usually I work 90% of the time with power cord connected. I updated to 11.10 on sunday and didnt notice yet but: the brightness goes insane when you work on battery power, switching between 0% and 100% every 2 seconds or whenever you touch any keys.

**To fix both brightness and power usage** (only shortly tested)
```
sudo gedit /etc/default/grub 
```change
```
GRUB_CMDLINE_LINUX_DEFAULT="quiet splash"
```to
```
GRUB_CMDLINE_LINUX_DEFAULT="quiet splash acpi_osi=Linux acpi_backlight=vendor i915.i915_enable_rc6=1 i915.i915_enable_fbc=1 i915.lvds_downclock=1 pcie_aspm=force"
```(all declarations with 915 fix power issues, all acpi declaration fix the brightness)
and run
```
sudo update-grub2
```now restart your system


Source: [http://www.phoronix.com/scan.php?page=article&item=intel_i915_power&num=1](http://www.phoronix.com/scan.php?page=article&item=intel_i915_power&num=1)
If you encounter any graphical problems afterwards read that.

Source brightness:[http://ubuntuforums.org/showpost.php?p=9056338&postcount=15](http://ubuntuforums.org/showpost.php?p=9056338&postcount=15)

---

### Post by jfarthing84 on 2011-10-18
I can confirm that the HDMI out does not work. Any ideas on how to fix this?

---

### Post by Humphreybas on 2011-10-19
did you try rebooting with hdmi connected?

[http://thecodecentral.com/2011/03/01/switch-to-external-monitor-connected-via-hdmivga-port-in-ubuntu](http://thecodecentral.com/2011/03/01/switch-to-external-monitor-connected-via-hdmivga-port-in-ubuntu)

---

### Post by jfarthing84 on 2011-10-19
Yes. Does this work for you?

---

### Post by Humphreybas on 2011-10-20
I can't test my HDMI out, don't have any fancy tv.

---

### Post by razvanc87 on 2011-11-02
I'm, as of yesterday, the proud owner of an U31SD laptop.

First I want to thank WalrusTusks and Humphreybas for posting the solutions to various problems regarding Ubuntu on this laptop.

What I wanted to ask is if there is a way to find out if the nvidia card is really turned off by ironhide.

That's because I did a cat /proc/acpi/battery/BAT0/stats and the power consumption is the same (around 13000) in the case I run for example "optirun blender" and in the case blender is closed. So I was thinking that maybe the nvidia card is still consuming power and that ironhide is not doing it's job at stopping it, but I don't know of any way to see if the card is really stopped or not.

Thanks a bunch!

---

### Post by razvanc87 on 2011-11-02
I'm, as of yesterday, the proud owner of an U31SD laptop.

First I want to thank WalrusTusks and Humphreybas for posting the solutions to various problems regarding Ubuntu on this laptop.

What I wanted to ask is if there is a way to find out if the nvidia card is really turned off by ironhide.

That's because I did a cat /proc/acpi/battery/BAT0/stats and the power consumption is the same (around 13000) in the case I run for example "optirun blender" and in the case blender is closed. So I was thinking that maybe the nvidia card is still consuming power and that ironhide is not doing it's job at stopping it, but I don't know of any way to see if the card is really stopped or not.

Thanks a bunch!

P.S.
I found out something interesting, but I may be misunderstood some things: I connected my laptop to a video projector and the interesting thing is that although the lsmod | grep nvidia returns nothing (so I guess that nvidia card is not being used) the connection still works. How is this possible? I read that the way things work are: nvidia -> intel -> lcd, and without the nvidia on we have intel -> lcd, but the vga port is connected directly to the nvidia card, so if the nvidia card is not used (confirmed by lsmod...) then how is the video projector still working?

---

### Post by never2far on 2011-11-02
Hello,

Does anyone have problems with the brightness after the login screen if gnome-shell is used? In my situation the brightness is almost 0(i barely see something on the screen). 


I must press Fn+F6 once and from black screen i get the default 100% brightness.

I hope I'll find a solution here. Until now this i what i have tried:

- [http://askubuntu.com/questions/3841/how-to-make-gnome-remember-brightness-setting](http://askubuntu.com/questions/3841/how-to-make-gnome-remember-brightness-setting)
- [https://launchpad.net/~kamalmostafa/+archive/gnome-settings-daemon](https://launchpad.net/~kamalmostafa/+archive/gnome-settings-daemon) -> for dealing with screen saver bug

Thank you.

---

### Post by somhi on 2011-11-04
never2far:    It happens also to me, though I don't find it a major problem.

---

### Post by Humphreybas on 2011-11-08
_@_razvanc87: I don't know how to check wether nvidia is on or off. However I know the power usage on my laptop is 8W on idle with nvidia off. When I run 'optirun gedit' power usage will go up 16W and then will go down to 8 again (gedit still running). This suggest that you cannot really force nvidia on (maybee ironhide is cleverly overiding the optirun command because it is not needed). And when I run 'optirun glxgears' I get 18W but I get the same with just 'glxgears'. So I am not sure when you should use the optirun command because it does not seem to affect the use of the nvidia card.
@Never2Far: same problem here

---

### Post by WalrusTusks on 2011-12-01
> **Humphreybas said:**
> I don't know how to check wether nvidia is on or off. However I know the power usage on my laptop is 8W on idle with nvidia off. When I run 'optirun gedit' power usage will go up 16W and then will go down to 8 again (gedit still running). This suggest that you cannot really force nvidia on (maybee ironhide is cleverly overiding the optirun command because it is not needed). And when I run 'optirun glxgears' I get 18W but I get the same with just 'glxgears'. So I am not sure when you should use the optirun command because it does not seem to affect the use of the nvidia card.

Actually, ironhide isn't THAT smart. (although I really wish it was. What is happening is this: Ironhide checks whether you're on battery, then either runs using the nvidia or intel. So, if you're on battery
 ```
optirun gedit
```isn't running on the nvidia card. Neither is
```
optirun glxgears
```It's just using more power because the processors+intel card have to speed up. To run something on the nvidia card when on battery, use
```
optirun -f gedit
```The "-f" is for force. ;)

---

### Post by Tuomas Jäntti on 2011-12-18
> **Humphreybas said:**
> 
BTW: Tuomas Jäntti, how do you mean DVD support?  for running a DVD from an image file?
I meant playing commercial DVD discs.
Sorry about not answering your question sooner, I have not read this thread for a while as everything has worked fine. (I am still using 11.04)

---

### Post by Humphreybas on 2011-12-18
No problem for me, I was just asking because my asus u31sd has no optical drive at all.

---

### Post by dare92 on 2012-01-12
After installation of Ironhide, I used &quot;sudo ironhide-configuration&quot; in terminal and followed the on-screen steps (by using default and/or recommended settings). After running the config, compiz works fine now.    Now I'm wondering if there's anything new yet about the fn-keys volume up/down/mute and the next/prev/pause/play button?

---

### Post by Humphreybas on 2012-01-27
All the fn-keys you mention are fully working, the volume buttons work in general and the others work for instance with banshee.

Btw, today I needed to use my HDMI port, after some reading and trying (and breaking my xorg.conf file->recovery mode->restoring the backup) I gave up. If anyone else wants to try it, there might be some info here:
[https://github.com/MrMEEE/ironhide/issues/66](https://github.com/MrMEEE/ironhide/issues/66)

---

### Post by dare92 on 2012-01-31
> **Humphreybas said:**
> All the fn-keys you mention are fully working, the volume buttons work in general and the others work for instance with banshee.

Btw, today I needed to use my HDMI port, after some reading and trying (and breaking my xorg.conf file->recovery mode->restoring the backup) I gave up. If anyone else wants to try it, there might be some info here:
[https://github.com/MrMEEE/ironhide/issues/66](https://github.com/MrMEEE/ironhide/issues/66)

Well I'm running Ubuntu 11.04 (with latest updates) and I don't get those fn-keys to work. I've read that they do work in 11.10, but there's no way I'm going to upgrade...

---

### Post by Humphreybas on 2012-01-31
oh yeah, I forgot to mention in 11.10. Why are you unwillingly to update?

---

### Post by dare92 on 2012-02-02
> **Humphreybas said:**
> oh yeah, I forgot to mention in 11.10. Why are you unwillingly to update?

I don't like the Unity interface. Also when installing/using gnome-panel, it gives me a kind of gnome3 idea which I also can't customize.
Although it gave me this opinion during the first days after release, so I haven't checked out  any updates.

Anyone who has experience with "gnome-session-fallback" ??

---

### Post by Vincent_Lin on 2012-02-20
Dear all,

U31SD user as well, but for my wife.  I have another Lenovo i7 12" that works well.

I have a couple of question regarding the setup of this laptop:

1. I installed bumblebee 3.0 and it works well in terms of using optirun or not, as well as better power management.  Sometimes wireless networking is "slow".  I have an N-router and three other laptops (all ubuntu various versions) do not show such slowness.

2. The internal mic is not working.  I installed cheese (the webcam program) and I can record video out of the webcam but the sound is simply not there.  Sound preference would not indicate sound levels neither internal or analog microphone.   

Could someone with U31SD care to comment on these two problems?  Thanks.

Vincent

---

### Post by Humphreybas on 2012-02-21
So you are talking about your wife's U31SD? Or your Lenovo?

1. low download speeds from internet or local? or high response time?
2. I never experienced problems with the mic nor did I hear about problems at this thread. Did you follow the default guides: [https://help.ubuntu.com/community/AudioCapture](https://help.ubuntu.com/community/AudioCapture)

---

### Post by Vincent_Lin on 2012-02-21
Hi Humphreybas,

Thanks for the reply.

Of course it is about this U31SD :)

I am not sure how to distinguish the speed or response time.  Usually, say starting firefox with google.com as default page would take a couple seconds to get it loaded, while all other laptops would pop up almost instantaneously.  youtube video also takes a long while before it starts playing, while all other laptops always almost start to play right away.

Regarding non-functioning mic, I do know the trick in turning up a bit at input section in sound preference page, but I will follow through the link you gave me and investigate a bit more.

Thanks for the reply again.

Vincent

---

### Post by Vincent_Lin on 2012-02-22
Dear all.

Regarding my probelm of internal mic in this u31sd, does any one care to share the contents of /etc/modprobe.d/alsa-base.conf?  Secifically the value for "options snd-hda-intel model="

Networking is still very slow.  Now my wife is complaining.

Vincent

---

### Post by Vincent_Lin on 2012-02-24
Dear all,

One problem down.

I changed my D-Link router's setting from "WPA or WPA2 encryption" to "WPA2 only", and now U31SD is surfing the net at full speed.

Internal microphone is still at trouble.  The recording from the microphone is sort of like "white noise".  Does anyone have any hints about what else I can try?

Thnaks,

Vincent

---

### Post by Humphreybas on 2012-05-08
Did anyone update to 12.04 yet? I am wondering if it went smooth?

Vincent, did you try the microphone with another OS ? Maybee it's just broken..
Anyway here are the contents of the config file you requested: [http://pastebin.com/mQbmLmQS](http://pastebin.com/mQbmLmQS)

---

### Post by villarrealj4344 on 2012-05-10
> **Humphreybas said:**
> Did anyone update to 12.04 yet? I am wondering if it went smooth?

Vincent, did you try the microphone with another OS ? Maybee it's just broken..
Anyway here are the contents of the config file you requested: [http://pastebin.com/mQbmLmQS](http://pastebin.com/mQbmLmQS)

Yeah, I did a fresh install of 12.04.  I had to install Bumblebee and apply the suspend fix.  I think that was it.  Everything is running pretty smoothly so far with no problems.  Also, I tested the microphone and it works fine on 12.04 at least.

---

### Post by somhi on 2012-08-19
I just updated to Ubuntu 12.04 and I came back here to check updated U31SD configuration info.

From the different posts I was not sure about to install Ironhide or bumblebee. 

Finally I installed bumblebee from the software center.
I have not activaded any proprietary nvidia driver though.
 
I also applied the Suspend fix from Humphreybas's first post.
I had to apply also the Brightness fix from post #22. I didn't applied the power usage options as I wasn't sure it were needed with the new Ubuntu.

Comments are welcome-

@Humphreybas, maybe It could be a good idea to update the first post with the latest info, including brightness fix.

Cheers

---

### Post by Humphreybas on 2012-08-20
Hey Somhi, I do agree with you, unfortunately I have very little spare time. I can try to do it one day,  if someone else would do it I can copy his post or link to it in my first post..

---

### Post by somhi on 2012-08-27
Well, see below a first and fast recop of your own information Humphreybas. Hopefully you and others could improve it.

> **Humphreybas said:**
> Hey Somhi, I do agree with you, unfortunately I have very little spare time. I can try to do it one day,  if someone else would do it I can copy his post or link to it in my first post..


Since there was no topic about the asus u31 I started this thread to collect fixes.

[SIZE=2]**Optimus and the NVIDIA GT 520M**  [/SIZE]
Out of the box the nvidia card is consuming power but not doing anything. On top of that desktop effects don't work (no unity no compiz). 
One option is to turn off the nvidia card to save power in case you don't need the nvidia performance. This is acomplished by [bumblebee]("http://bumblebee-project.org/")  project.

[SIZE=1]**Using the Bumblebee solution to switch graphics**[/SIZE]
First get the software:
```
sudo apt-get install bumblebee 

```
Now log off and log on.
Now you should have desktop effects (compiz / unity). And your power usage should be down to 7000-8000:
```
       grep rate /proc/acpi/battery/BAT0/state
  
```[SIZE=2][B]
Suspend and Hibernate[/B][/SIZE]
(adapted from [http://ubuntuforums.org/showpost.php?p=10551449&postcount=1](http://ubuntuforums.org/showpost.php?p=10551449&postcount=1))

The problems are caused by the USB buses (more info elsewhere on the forums).
In the script below also the nvidia card is turned on again, this assumes you have done the "[SIZE=1][SIZE=1]Disable NVidia GPU/NVidia Optimus[/SIZE]**"**[/SIZE] when you use the bumblebee project this might not be necassairy.

```
gksu gedit /etc/pm/sleep.d/20_custom-asus-u31sd
```INSERT BELOW TEXT

```
#!/bin/sh

BUSES="0000:00:1a.0 0000:00:1d.0"

case "${1}" in
    hibernate|suspend)
    # Switch USB buses off
    for bus in $BUSES; do
        echo -n $bus | tee /sys/bus/pci/drivers/ehci_hcd/unbind
    done
    # Switch optimus back on before going to sleep, avoids the "constant on"
    # bug that occurs after 2 suspend/resume cycles (thanks kos888)
    /etc/init.d/optimusoff stop
    ;;
    resume|thaw)
    # Switch USB buses back on
    for bus in $BUSES; do
        echo -n $bus | tee /sys/bus/pci/drivers/ehci_hcd/bind
    done
    # Switch optimus off before resuming, avoids unneccessary power draw
    /etc/init.d/optimusoff start
    ;;
esac
```Next just make it executable
```
sudo chmod +x /etc/pm/sleep.d/20_custom-asus-u31sd
```[SIZE=2]

**To fix both brightness and power usage** (only shortly tested)
```
sudo gedit /etc/default/grub 
```change
```
GRUB_CMDLINE_LINUX_DEFAULT="quiet splash"
```to
```
GRUB_CMDLINE_LINUX_DEFAULT="quiet splash acpi_osi=Linux acpi_backlight=vendor i915.i915_enable_rc6=1 i915.i915_enable_fbc=1 i915.lvds_downclock=1 pcie_aspm=force"
```(all declarations with 915 fix power issues, all acpi declaration fix the brightness)
and run
```
sudo update-grub2
```now restart your system


Source: [http://www.phoronix.com/scan.php?page=article&item=intel_i915_power&num=1](http://www.phoronix.com/scan.php?page=article&item=intel_i915_power&num=1)
If you encounter any graphical problems afterwards read that.

Source brightness:[http://ubuntuforums.org/showpost.php?p=9056338&postcount=15](http://ubuntuforums.org/showpost.php?p=9056338&postcount=15)[/QUOTE]

Note:  It might not be needed to apply the power usage options with the new Ubuntu releases [To be checked]

**Issues to be fixed**[/SIZE]
This was written in a hurry and this post is still quite immature, so some of these things might be easy to fix, I just didn't look at it in detail:
-check whether the bumblebee project alone can fix issues with the optimus (not doing the disable thing)
-Get all the fn-keys to work
currently working: sleep (F1) wireless switch (F2) brightness (F5 F6) screen switch (F7)
important not working fn-keys: volume and music player controls
- HDMI output ?

---

### Post by Humphreybas on 2012-08-28
Hey Somhi, thanks for the merging of all the info!
When I saw your post I tried to insert or link it in my first post to no avail. After some reading on the ubuntuforums I discovered that these guides should be put on the wiki instead of start posts. That is quite brilliant because then you don't need me anyway to update the public guide!

A quite extensive example is this guide:
[https://help.ubuntu.com/community/Asus_U36SD](https://help.ubuntu.com/community/Asus_U36SD)

We could make something similiar (and we might can learn from some of their tricks).

I already converted your forum post to wiki syntax: [http://pastebin.com/TrBiaSM4](http://pastebin.com/TrBiaSM4)
with the tool ([http://bodhizazen.net/tweaks/ubforums2ubwiki.sh.txt](http://bodhizazen.net/tweaks/ubforums2ubwiki.sh.txt)) as quoted in this post [http://ubuntuforums.org/showthread.php?t=1949027](http://ubuntuforums.org/showthread.php?t=1949027)

---

### Post by denarced on 2012-09-23
Hello all,

This is just an update for everyone on the HDMI issue. I'm using bumblebee and 12.04 (32bit) and HDMI does not work. My laptop model is Asus U31SD with specs
[LIST]
[*]Inte core
[*]Intel Core i3-2330M, 2.2GHz
[*]4GB RAM
[*]GeForce GT 520M 1GB
[/LIST]

---

