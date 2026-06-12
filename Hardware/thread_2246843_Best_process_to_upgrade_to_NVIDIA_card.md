---
title: "Best process to upgrade to NVIDIA card ?"
date: 2014-10-03
forum: Hardware
---

### Post by sns4rnr on 2014-10-03
Been an Ubuntu user for just under one year.  Fair amount of experience Googling for solutions to various issues and questions.  Not afraid of a little command line stuff, but also not 100% versed in installing and uninstalling driver packages etc...

Hoping someone in the community here has a best bullet-point task list for going about this relative to the current state of drivers and the current state of kernel.  I have my system pretty well established and I really don't want to have to re-install and restore because I can't figure out how to "undo" a goofed and/or wrong video driver installation that results in no display to work from (yes it happened to me more than once on my 11yr old "training" build, though I was much "greener" then).

I need to upgrade my graphics card on my new build to do some moderate gaming (Minecraft primarily)
I'm currently happy with my 14.04 installation otherwise.  System details below.

Gigabyte 970A-DS3P mobo (no on-board GPU)
AMD FX-8320 Black Edition CPU
1 TB HDD
Dual Boot Win 7,  Ubuntu 14.04 LTS - UEFI Mode
IOMMU enabled (was necessary)
Radeon X1300 Graphics card running open source Radeon driver included with 14.04 distribution (This is the card I want to replace)
Acer X223w monitor  (want to replace this too, but one expense at a time I'm afraid)

From my previous build I'm familiar with using the Nouveau driver for NVIDIA.  I could never get proprietary drivers to work on that build.
I already know my monitor is not recognized by Ubuntu and as a result I always have to build my own Xorg.conf file to create a choice of reasonable resolutions to work with.  So I'm comfortable and familiar with that process.

I want to install an NVIDIA GeForce card (probably 630 or 730 series) and run the proprietary drivers for best performance.   I'm not opposed to trying it on Nouveau first to see if it will serve adequately, but my expectation is better performance using NVIDIAs driver direct from their site.

In browsing the various threads, and from my own experience, I fear card recognition problems clean driver installation problems, and/or compiz config problems.
So to be "pre-emptive," I'm seeking a "Point-A to Point-B procedure" to go from my Radeon Open source card/driver to NVIDIA card and proprietary driver to minimize the likelyhood of issues.

Should I remove my custom xorg.conf file, swap the GPU card, reboot, and pray all will work itself out?  Or modify my xorg.conf to use nouveau, power down, swap cards, reboot, then try to install the proprietary drivers.  Should I attempt to install the proprietary drivers from a boot to a non-gui terminal...   while X is running or not running.   etc....   Would I be better off doing the GPU swap with another "recognized" monitor until I have the drivers stable and then tackle updating xorg.conf after that?   Sooo many options....

---

### Post by grahammechanical on 2014-10-03
Step 1: Revert the OS to using the open source video driver
Step 2: Shut down the OS.
Step 3: Power off the machine. Some PSUs have their own on/off switch to remove all power from the motherboard.
Step 4: Swap out the Radeon X1300 for the Nvidia 630 or 730.
Step 5: Reconnect power to the motherboard.
Step 6: Switch the machine on and load Ubuntu.
Step 7: Run Additional Drivers to select and apply the Nvidia proprietary video driver.

You do not have hybrid graphics and that fact keeps things simple and perhaps you are making too much of things.

Modern digital monitors store their settings information in their electronics in something called Extended Display Identification Data (EDID) and Linux uses the graphic adapter to read that information and set the optimum resolution as decreed by the monitor manufacturer. This is done every time we load. No need to mess around with xorg.conf any more.

[http://en.wikipedia.org/wiki/Extended_display_identification_data](http://en.wikipedia.org/wiki/Extended_display_identification_data)

> [COLOR=#333333][FONT=Ubuntu Beta]Computer monitors contain a small binary packet of information called [/FONT][/COLOR]*Extended Display Information Data*[COLOR=#333333][FONT=Ubuntu Beta] (EDID), which describes the monitor's size, modelines, etc. During startup or when a monitor is hotplugged, the X server queries this data from the monitor and uses it to set a resolution.[/FONT][/COLOR]

[https://wiki.ubuntu.com/X/Troubleshooting/Resolution](https://wiki.ubuntu.com/X/Troubleshooting/Resolution)

Regards.

---

### Post by sns4rnr on 2014-10-04
Ordered my EVGA GT 730 today.  Probably take a crack at the install this weekend.  Will see what "Additional Drivers" offers up in terms of driver versions once I get there.

Another note: I found reference in EVGA site indicating that GT 6 series cards do not have UEFI bios, which I presume means such cards may not work in my current UEFI installation.  Though not 100% sure on that.  The GT 7 series are supposed to have UEFI bios support.   Will see how/if that impacts me.


> [COLOR=#000000]Modern digital monitors store their settings information in their electronics in something called Extended Display Identification Data (EDID) and Linux uses the graphic adapter to read that information and set the optimum resolution as decreed by the monitor manufacturer. This is done every time we load. No need to mess around with xorg.conf any more.[/COLOR]


True, however for some reason, my particular monitor is not providing the EDID info OR there's something wrong with the EDID info, so Linux does not recognize the monitor and defaults to only 800x600 and 1024x768 as resolution choices.  So I have to build an Xorg.conf regardless.  I've narrowed that issue down to the monitor itself, but no big deal, I can manage that part as needed.  Though I'll need to find the new driver name to put into the conf file once I get them installed (unless the xorg.conf gets updated itself during the proprietary driver installation).

Update: From my reading, in theory, once Nvidia's proprietary driver is installed, command  nvidia-xconfig should create an xorg.conf "template" that already refers to it's driver.  I expect I'll still have to add my mode lines for added resolutions.

---

### Post by sns4rnr on 2014-10-10
GT730 installed successfully on test installation - finally...    Took quite a bit of fooling around..  
Here's the process I had to go through - which by no means will be the process someone else may have to use - but maybe someone can learn something useful in it.

1.  Because my old Radeon card was on default open-source drivers, I did NOT have to revert or purge any old drivers.  Simply archived and deleted the previous /etc/X11/xorg.conf file, then powered down and removed power cable.
2.  Swapped the video cards, attached power, and reconnected the VGA cable.
3.  On boot, system automatically setup on Nouveau driver as expected and basic function was ok but only 2 low resolution modes were available as expected (again because the EDID won't read directly from either of my monitors)
4.  Ubuntu repositories for nvidia proprietary drivers offer no driver for this card by default.  Latest driver there is 319 series and this card wants the 340 series driver.
5.  Added repository for updated nvidia drivers from xorg-edgers
sudo add-apt-repository ppa:xorg-edgers/ppa 
sudo apt-get update 
6.  NOW - the Additional Drivers utility shows the option for the 340.46 driver as recommended because it was able to find it at the ppa I added.  Installed/activated that driver from the Additional Drivers utility.
7.  Rebooted to be sure the new driver runs from startup
8.  /var/Xorg.0.log shows that nvidia driver runs but does not activate all the good stuff... Acceleration, GLX etc... all fail to initialize.  Logs seem to indicate again this is due to not being able to get the EDID from the monitor.
9.  Ran command  sudo nvidia-xconfig  which updated the xorg.conf file but did not help the edid situation.
10.  Learned that nvidia-xconfig can apply a custom edid.bin file if one is available
11.  FORTUNATELY, I have an old HP desktop on Precise 12.04 32-bit Intel platform that for whatever reason has no problem reading EDID from the same monitors even through a VGA KVM switch.  Also found a utility that can read this info and output it to a file...
SO -   on the alternate HP system I attached my monitor and installed the application  (Which I gather only works on 32bit systems - but not confirmed)
"sudo apt-get install read-edid"
Then I used that app to generate an edidACER.bin file like so:
"sudo get-edid > edidACER.bin"
I used a flash drive to transfer this file to the system with my new GT730 card to /etc/X11/edidACER.bin - Ensure root retains ownership of the file.

13. Used following command to apply the "custom" edid file to xorg.conf
"sudo nvidia-xconfig -o xorg.conf --custom-edid=CRT-0:/etc/X11/edidACER.bin"
14.  Rebooted -   Now getting somewhere - fewer to no complaints in the logs, driver activates all the supported goodies, Greeter/login screen is at my larger resolution 1680x1050 as provided by the edid.  Looks good.. until I login... then my desktop screen image is shifted left 1.5 inches so the Unity launcher is off screen.  Changing to 1440x900 via system settings helps alot, though image is still offset by about 1/8 inch to the right and down.
15.  Run utility  "nvidia-settings" and looked at the X server Configurations.  With Advanced options visible, I find two refresh rate options for resolution mode 1680x1050... The choices are 60 and 60.  yes two options for 60hz...(one mode was provided by xrandr and one from nv-control with veeery slightly different refresh and screen dimensions).  If I choose the first, I had the screen offset issue.  If I choose the second, magic, and the screen is ok... Great, except it goes back to the problem on every reboot, logout, or login, basically anytime the Xsession is started forcing me to run nvidia-settings on every login to fix the screen.
16.  Spent 15+ hours hammering google for every possible way to get that second 60hz refresh rate option to be "persistent" but no amount of fooling with xrandr, xorg,conf, nvidia-settings, .nvidia-settings-rc, etc... could stop the mode from reverting to the "offset screen" problem.
17. In a brief moment of "what the heck" inspired clarity that often occurs when at one's wit's end, I decided to connect the monitor with a DVI cable instead of a VGA cable... Voila - working fine... Go figure.   If I had been on DVI all along, I may have been done at step 13,,, possibly before if the EDID would have read automatically over DVI.

Now I get to do it all over again with my "real" hard drive installed, since this was just a test drive to see if it could even be done without destroying the system or requiring a full re-install just to repair something I couldn't figure out how to fix.    But at least now, I can port over the edid and xorg.conf files that are working.

SO  "Best Process to upgrade to NVIDIA card.......   apparently no such thing exist...   From all the threads and headaches I see from others and from my own experience, every upgrade/install has the makings of a custom adventure, unique to each user's collection of hardware.   A million nvidia driver on linux problem threads out there and not one I could find referring to "duplicate" resolution/refresh rate options.

---

### Post by Vladlenin5000 on 2014-10-10
VGA is older than the guy in my avatar (he's already dead, btw). Why would someone want that having options such as DVI or HDMI?
Although VGA can support current high resolutions, the technology is from the time 800*600 was considered ultra-high definition!!!!

Always prefer digital to analogue for this usage scenario and especially when dealing with newer graphics cards.

---

