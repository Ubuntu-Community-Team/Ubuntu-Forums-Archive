---
title: "Asus U43JC"
date: 2010-11-07
forum: Hardware
---

### Post by arbrandes on 2010-11-07
**[SIZE="5"]Ubuntu 12.04 Precise Pangolin on an Asus U43JC-X1[/SIZE]**

Edit: Updated for Precise!  This will be edited as known issues are solved.

**[SIZE="4"]Automatic Nvidia Power Management[/SIZE]**

Let's begin by installing bumblebee to handle Nvidia power management as well as Optimus:

```

$ sudo add-apt-repository ppa:bumblebee/stable
$ sudo apt-get update
$ sudo apt-get install bumblebee

```

This makes it so the nvidia card will be disabled automatically on boot (and remain so even after resume from standby), and therefore will not consume any power or generate additional heat.  To test if it worked, reboot, unplug the laptop from the power outlet and do a:

```

$ cat /proc/acpi/battery/BAT0/state

```

The "Present rate" line should be around 13500 mW. With WiFi off, low screen brightness, and no USB devices attached, it should get as low as 11500 mW!

To run opengl applications manually using Nvidia's binary driver, execute:

```

$ optirun <application>

```


**[SIZE="4"]Touchpad Fixup[/SIZE]**

To configure the touchpad beyond what is available in Gnome configuration, we will use the [hotplug-command hook]("http://who-t.blogspot.com/2011/03/custom-input-device-configuration-in.html") available in the new gnome-settings-daemon. Start off by creating this script somewhere in your executable path, such as $HOME/bin:

$HOME/bin/touchpadconf
```

#!/bin/bash
#
# This script is an example hotplug script for use with the various
# input devices plugins.
#
# The script is called with the arguments:
# -t [added|present|removed] <device name>
#	   added ... device was just plugged in
#	   present.. device was present at gnome-settings-daemon startup
#	   removed.. device was just removed
# -i <device ID>
#	   device ID being the XInput device ID
# <device name> The name of the device
#
# The script should return 0 if the device is to be
# ignored from future configuration.
#

args=`getopt "t:i:" $*`

set -- $args

while [ $# -gt 0 ]; do
	case $1 in
	-t)
		shift;
		type="$1"
		;;
	 -i)
		shift;
		id="$1"
		;;
	 --)
		shift;
		device="$@"
		break;
		;;
	*)
		echo "Unknown option $1";
		exit 1
		;;
	esac
	shift
done

retval=0
case $type in
	added|present)
		if [ "$device" == "ETPS/2 Elantech Touchpad" ]; then
			xinput set-prop $id "Synaptics Tap Action" 0, 0, 0, 0, 1, 2, 3
		fi
		;;
	removed)
		;;
	*)
		retval=1
		;;
esac

# All further processing will be disabled if $retval == 0
exit $retval

```

Now make it executable:

```

$ chmod a+x $HOME/bin/touchpadconf

```

Edit the "Synaptics Tap Action" line to whatever you like - that's where the actual configuration is set.  Refer to "man synaptics" for possible keys/values.

Now execute the following to set the hook.  It'll be executed whenever g-s-d is called, be it at startup, after resume, of when you plug/unplug a device.  "touchpadconf" refers to the script you created above.  If it's not in your path, change it to include absolute path information.

```

$ gsettings set org.gnome.settings-daemon.peripherals.input-devices hotplug-command touchpadconf

```

**[SIZE="4"]Fix Suspend[/SIZE]**

We have to unbind the USB buses manually before suspending.  Create /etc/pm/sleep.d/20_custom-asus-u43jc:

```

#!/bin/sh

EHCI_BUSES="0000:00:1a.0 0000:00:1d.0"
XHCI_BUSES="0000:04:00.0"

case "${1}" in
    hibernate|suspend)
        # Switch USB buses off
        for bus in $EHCI_BUSES; do
            echo -n $bus | tee /sys/bus/pci/drivers/ehci_hcd/unbind
        done
        for bus in $XHCI_BUSES; do
            echo -n $bus | tee /sys/bus/pci/drivers/xhci_hcd/unbind
        done
        ;;
    resume|thaw)
        # Switch USB buses back on
        for bus in $EHCI_BUSES; do
            echo -n $bus | tee /sys/bus/pci/drivers/ehci_hcd/bind
        done
        for bus in $XHCI_BUSES; do
            echo -n $bus | tee /sys/bus/pci/drivers/xhci_hcd/bind
        done
        ;;
esac

```

And make it executable:

```

$ sudo chmod a+x /etc/pm/sleep.d/20_custom-asus-u43jc

```


**[SIZE="4"]Fix Hibernation[/SIZE]**

To fix hibernation, simply create /etc/pm/config.d/hibernate_mode with the following contents:

```

HIBERNATE_MODE="shutdown"

```

Reboot, and try it out.  It is kinda slow either hibernating or resuming, so be patient.  This is one of the reasons I plan to get a fast SSD some time in the near future.  


**[SIZE="4"]Fix CPU Frequency Scaling[/SIZE]**

Sometimes the BIOS limits the available CPU frequency to just 1.2GHz, either when on the power cord on on the battery.  Since recent kernels respect this limit (a feature not present in Ubuntu 10.04, for instance), the workaround is to tell the kernel to ignore it.

To check if you have the same problem, do:

```

$ cat /sys/devices/system/cpu/cpu0/cpufreq/bios_limit

```

If it's anything less than 2400000, you got the same problem. The fix is to add "processor.ignore_ppc=1" as a boot parameter to the kernel.  To do so, edit /etc/default/grub and modify the GRUB_CMDLINE_LINUX_DEFAULT parameter so it reads:

```

GRUB_CMDLINE_LINUX_DEFAULT="quiet splash processor.ignore_ppc=1"

```

Then update grub.cfg:

```

$ sudo update-grub

```

Reboot.


**[SIZE="4"]Known Issues[/SIZE]**

* No WiDi out.

---

### Post by arbrandes on 2010-11-07
Hibernation workaround discovered here:

[http://ubuntuforums.org/showpost.php?p=10017280&postcount=188](http://ubuntuforums.org/showpost.php?p=10017280&postcount=188)

Howto updated.

---

### Post by bdkoepke on 2010-11-07
Thanks for mentioning me ;)

---

### Post by arbrandes on 2010-11-07
np, bdkoepke. :)  Without your help, disabling nvidia would've been tough.

btw, howto updated with modprobe configuration for the Elan touchpad.  Solves the sensitivity issue.

---

### Post by arbrandes on 2010-11-07
Just discovered CPU frequency scaling does not work. CPU cores are always stuck at 1.2GHz, no matter what the load on them.

This is probably due to this kernel bug (which points to a possible hardware bug): [https://bugzilla.kernel.org/show_bug.cgi?id=19702](https://bugzilla.kernel.org/show_bug.cgi?id=19702).  There are a few patches there, I'm going to try them out eventually.  Would much prefer a userspace workaround, though...

On launchpad there's a related bug, [https://bugs.launchpad.net/ubuntu/+s...ux/+bug/637845](https://bugs.launchpad.net/ubuntu/+s...ux/+bug/637845).

---

### Post by arbrandes on 2010-11-08
Found out why cpu freq scaling is not working: the BIOS is limiting it at 1.2GHz.  One can check by doing:

$ cat /sys/devices/system/cpu/cpu0/cpufreq/bios_limit

If it's anything less than 2400000, you got the same problem.  The fix is to add "processor.ignore_ppc=1" as a boot parameter to the kernel.  Will update the howto accordingly.

"Why did it work with Ubuntu 10.04?", one might ask.  This is because until very recently, the Linux kernel simply ignored BIOS limitations on cpu frequency.

Some day I'm going to try updating the U43JC's BIOS to see if it helps (there's a new version on Asus's site, number 214 from October 14th), but for now, this workaround will do.

---

### Post by rosencrantz on 2010-11-16
Great howto, thanks a lot!
A few remarks regarding my system (Kubuntu 10.10 on u43jc-X1):
My BIOS limit was 2400000  - the computer shipped from Amazon on Oct 14, so maybe it already has a newer BIOS?

For KDE users: touchpad configuration works out of the box with the psmouse.force_elantech=1 boot option.

---

### Post by arbrandes on 2010-11-16
> **rosencrantz said:**
> the computer shipped from Amazon on Oct 14, so maybe it already has a newer BIOS?

Mine shipped out a week after yours, so I'm guessing its a configuration option somewhere.  Couldn't find it in the BIOS, so it's probably the "Super Hybrid Engine" thing which I turned on in Windows.  I'm gonna try disabling it and booting without the ppc boot parameter.

Could never figure out what that Super Hybrid stuff does, anyhow!

---

### Post by yoslow on 2010-11-28
how do i patch dsdt on linux mint?

---

### Post by dsfitzpat on 2010-12-05
> **arbrandes said:**
> Mine shipped out a week after yours, so I'm guessing its a configuration option somewhere.  Couldn't find it in the BIOS, so it's probably the "Super Hybrid Engine" thing which I turned on in Windows.  I'm gonna try disabling it and booting without the ppc boot parameter.

Could never figure out what that Super Hybrid stuff does, anyhow!

I ran across this thread because my girlfriend is shopping for a new computer and I was wondering how the newer ASUS PCs would run under Ubuntu - esp. regarding the video card.  Anyway, here's my 2 cents about the Super Hybrid stuff:
Assuming it works the same as in the eeePC line (I have an eeePC 1005 that works like a charm with UNE once you do a bit of tweaking) the super hybrid engine is meant to improve battery life by throttling the processor.  My eeePC has 3 modes - performance (no throttling, less than 2 hours battery life), normal, and powersave (3-4 hours of battery life, but the CPU speed is severely capped).
So it could well be that the problem you mentioned has something to do with these settings.  On my eeePC I have a program called the eee control tray installed that lets me toggle this setting while running Ubuntu:
[http://greg.geekmind.org/eee-control/]("http://greg.geekmind.org/eee-control/")
The downsides are that it's not in the repositories and it's meant for the eeePC line so I have no idea if it works for a full size laptop although it sounds like ASUS uses similar technologies in both. It's not mentioned on the website I gave above but there is a ppa for this program - see here:
[http://linux.aldeby.org/eee-control-the-best-device-control-tray-icon-for-eee-pcs.html]("http://linux.aldeby.org/eee-control-the-best-device-control-tray-icon-for-eee-pcs.html")
It's possible it'll solve the CPU problem (it also helps with hotkey support on the eeePC).  I'll add the warning that it's not 100% stable on my machine, and occasionally becomes a runaway and eats CPU.

---

### Post by arbrandes on 2010-12-05
Hey dsfitzpat, thanks for the info!  It turns out the throttling went away when I changed the power saving settings on Windows.  Will give that utility a try; it is somewhat vexing that there are BIOS settings that can only be configured from Windows.  I hope this doesn't become a trend!

---

### Post by dsfitzpat on 2011-01-09
It would be interesting to know if the eee-control-applet works on the full-size Asus notebooks - especially since it seems to me like these are getting better all the time, and usually offer better specs and/or lower prices!  I did a quick search and came across another program called Jupiter that claims to do the same thing, and has the advantage of coming from a PPA:
[http://www.webupd8.org/2010/06/jupiter-take-advantage-of-asus-super.html](http://www.webupd8.org/2010/06/jupiter-take-advantage-of-asus-super.html)

I'm not sure if Asus still calls this Super Hybrid Engine on their notebooks but the above site claims this tool works on any laptop, so maybe it's worth a try.  Somewhere in the Asus Eee support forums they claim there's a version of Super Hybrid Engine for Linux; maybe they ported it to Xandros (the OS on the original Eees) but I haven't come across it.

---

### Post by arbrandes on 2011-01-10
I have jupiter installed on my U43JC, but AFAICT it does nothing.  I hacked its scripts to have visual feedback when enabling/disabling the touchpad (see first post), but that's it.

---

### Post by pmaconi on 2011-01-18
Can you tell me how to go about patching the DSDT.dsl file?

---

### Post by rosencrantz on 2011-02-02
After executing the first code block in the OP's HowTo you should have a DSDT.dsl file. Copy the second block to a file dsdt.diff in the same directory and run patch < dsdt.diff

---

### Post by 23kota on 2011-02-03
Tremendous work! Thanks for this great howto. Mostly everything worked just as described and brought my Asus to live under Ubuntu.

The only thing I noticed stopped working is a cd/dvd drive. It stopped mounting disks with the message:

```
$ sudo mount /dev/cdrom /mnt
mount: unknown filesystem type 'iso9660'
```

It appeared that module isofs (as well as other cd/dvd fs support) was kicked out from my custom kernel. I figured out that the reason they were disabled was the following line in making new kernel configuration:

> $ make localmodconfig

I simply skipped this line and recompiled the kernel with modules from original Ubuntu's /boot/config-VER (adding DSDT of cause) and everything worked.

I suspect there might be other important modules kicked out by localmodconfig, I just did not notice by this time.

---

### Post by rosencrantz on 2011-02-03
I also had trouble with the localmodconfig and used make oldconfig as directed in the HowTo. Takes longer to compile and gets you a few more GB of temp files, if I remember right, but is probably safer. You can also try to speed things up with make -j 4 (after all, we ought to be able to do hyperthreading)

---

### Post by arbrandes on 2011-02-03
Hey dudes,

23kota: I removed the "make localmodconfig" line from the howto, it really was causing more problems than solving them!  Substitute it with 'yes "" | make oldconfig' for better results (but much longer compile times :).

rosenkrantz:  The -j4 thing is taken care of by this on the compilation line: "CONCURRENCY_LEVEL=`getconf _NPROCESSORS_ONLN`"

---

### Post by gravufo on 2011-02-27
Just followed the tutorial and it was great! Very well done!
Thanks so much, it felt way too weird too have a worst battery life on Linux than on Windows lol :P

I have a little question: my battery's "current state" is more in the 19000mW than in the 13000mW.

The first time I followed the tutorial (I've done it twice) and BEFORE I applied the patch to automatically disable the nvidia card, it went exactly around 13000mW. As soon as I applied the patch and reboot, it was back at 19 or so....

BTW, is it normal that we are using a G210m file whereas our card is actually a G310m?

Also, the "jupiter-support-eee" cannot be found through the given command...even the command that the actual site gives me is wrong, I guess the package has been removed...

Anyhow, thanks a lot for all the effort put into this, hopefully my battery life will be much better!

---

### Post by arbrandes on 2011-02-27
Hi gravufo!

What the g210m module does is simply run the acpi_call command automatically at boot (and at resume from suspend).  If you're getting 19000 mW after rebooting, this could mean a couple of things:

1) The module isn't being loaded: run "lsmod | grep g210" and see if it's there.  If it isn't, check your /etc/modules file and see if "nvidia_g210m_acpi" is at the end.

2) The kernel wasn't patched with a custom DSDT, which is required for the U43JC.

It doesn't matter if you have a g310m, by the way (which is what I have).

Will look into the jupiter-support-eee, thing.  Maybe it was renamed?

---

### Post by gravufo on 2011-02-28
> **arbrandes said:**
> Hi gravufo!

What the g210m module does is simply run the acpi_call command automatically at boot (and at resume from suspend).  If you're getting 19000 mW after rebooting, this could mean a couple of things:

1) The module isn't being loaded: run "lsmod | grep g210" and see if it's there.  If it isn't, check your /etc/modules file and see if "nvidia_g210m_acpi" is at the end.

2) The kernel wasn't patched with a custom DSDT, which is required for the U43JC.

It doesn't matter if you have a g310m, by the way (which is what I have).

Will look into the jupiter-support-eee, thing.  Maybe it was renamed?
Hey arbrandes!

Thanks for the explanation

1) the module is loaded, i also did a lsmod | grep acpi_call

2) is there a way to check if the custom DSDT is loaded or what? :D

I rechecked the usage and it was around 18000 mW. Sometimes it touches 17500 mW but it doesn't stay there more than a few seconds!

Thanks a lot for the help :)

EDIT: Tested again and I get 16000mW with screen off (FN-F7), and with wifi off + screen off I get 15885mW! A bit better, but still not near 13000mW.

BTW, what is the usual battery life on linux/ubuntu you get on a full charge since you have used the fix/hack?

---

### Post by arbrandes on 2011-03-01
My rate is around 11475 mW as I write this, with the screen on low brightness, wifi on, touchpad off, and USB trackball connected:

```

$ cat /proc/acpi/battery/BAT0/state

present:                 yes
capacity state:          ok
charging state:          discharging
present rate:            11475 mW
remaining capacity:      81210 mWh
present voltage:         16949 mV

```

If I turn off wifi and disconnect all USB devices, I can sometimes get it to go as low as 10500 mW.

To check if the nvidia card is actually off, this is what I do:

```

$ lspci | grep 310M

01:00.0 VGA compatible controller: nVidia Corporation GT218 [GeForce 310M] (rev ff)

```

If the two characters after "rev" are "ff", you're good to go.  Anything else, the card is still on.

Battery life?  I've never measured it scientifically, but in real life internet use (some Youtube, some reading, some posting), I'm guessing at least 6 hours.

---

### Post by gravufo on 2011-03-01
Damn, you get good battery life, I barely get 3 hours on linux, most probably because of the Nvidia card >.<

I checked the command you gave me and it returned

01:00:0 VGA compatible controller: nVidia Corporation GT218 [GeForce 310M] (rev a2)

I guess it isn't off then...It's extremely odd since everything seems just fine...

Any idea how I could troubleshoot/fix this?

Thanks so much for the help!

---

### Post by arbrandes on 2011-03-01
Run:

```

$ echo '\_SB.PCI0.RP00.VGA._PS3' | sudo tee -a /proc/acpi/call
$ cat /proc/acpi/call

```

You should get a "0x0" in the beginning of the following line.  If so, check if power consumption is low, and also check if the lspci rev is "ff".

If this doesn't work, it means something's not right with your setup: either acpi_call isn't loaded, or the DSDT table is not patched into the kernel, or ... well, there are many reasons.  But one step at a time, right? :)

---

### Post by gravufo on 2011-03-01
Did what you suggested, it does give me a 0x0, but power consumption is still around 16000mW and the rev is still a2 >.<

I'm pretty sure acpi_call is being loaded...might be the custom DSDT though, I wonder... is there no way to check if it actually is the custom one or not without having to redo the whole thing?

---

### Post by arbrandes on 2011-03-02
I don't think there's an easy way to check what DSDT the current kernel is using.  Since there was a kernel update today, you might as well recompile it, double-checking each step to make sure everything's just right.  If I were you I'd also re-dump and re-patch the DSDT from scratch.

If I remember correctly, you will also have to reinstall the acpi_call and 210m modules!

---

### Post by fuduntu on 2011-03-02
> **arbrandes said:**
> 
Will look into the jupiter-support-eee, thing.  Maybe it was renamed?

[http://www.jupiterapplet.org/downloads.html](http://www.jupiterapplet.org/downloads.html)

Unless you have an Eee PC, it may not help though (does your device support Super Hybrid Engine?).  Set acpi_osi=Linux on the kernel line in /boot/grub/grub.conf also if you haven't already.

---

### Post by gravufo on 2011-03-03
> **arbrandes said:**
> I don't think there's an easy way to check what DSDT the current kernel is using.  Since there was a kernel update today, you might as well recompile it, double-checking each step to make sure everything's just right.  If I were you I'd also re-dump and re-patch the DSDT from scratch.

If I remember correctly, you will also have to reinstall the acpi_call and 210m modules!
Hey again,

I recompiled today with the newest source by cross-checking everything I did to make sure it was correct. I then installed the modified kernel and restarted and BAM low battery usage :)

I then restarted again to make sure that it stayed that way, and I tested without the brightness, no Wifi and no usb devices and I got 10665 mW :D

I also did not have to reinstall the 210m module. I did the acpi_call anyway since it was placed in the tutorial before the restart.

Anyhow, thanks so much for all the help and for the great tutorial! I'll finally be able to use Ubuntu as my main OS!

PS: The rev is also FF ;)

PPS: Do I have to do this whole thing every time there is a new kernel update?

---

### Post by arbrandes on 2011-03-03
> **gravufo said:**
> Do I have to do this whole thing every time there is a new kernel update?

Unfortunately, yes.  If you want the kernel fixes, that is!  I myself only recompile every two or three releases, and use the old one in between.

It's too bad Linus decided to do away with initrd support for custom DSDT tables (with which no kernel recompilation would be needed).  I heard it was done as an incentive for kernel developers to make the kernel work out-of-the-box with all BIOS's, even buggy ones.

---

### Post by anjexe on 2011-03-13
dose this device carde reader worke fine on ubuntu?

mine n43 dosent as they are all asus same soloutions may be available

Tnx

---

### Post by rosencrantz on 2011-04-15
> **arbrandes said:**
> The fix is to add "processor.ignore_ppc=1" as a boot parameter to the kernel.  To do so, edit /etc/grub/default and modify the GRUB_CMDLINE_LINUX_DEFAULT parameter so it reads:


Typo: It's /etc/default/grub.

@anjexe: mine works with SD cards.

---

### Post by anjexe on 2011-04-16
> **rosencrantz said:**
> Typo: It's /etc/default/grub.

@anjexe: mine works with SD cards.

what to do for that?
could u tell me

---

### Post by rosencrantz on 2011-04-17
It works out of the box. Did you try different SD cards or testing the reader from an Ubuntu live CD?

---

### Post by anjexe on 2011-04-17
it test diferent cards but not tested whit live media,i will chek and tell u!

is there any soulutions?

could i dl the 11.04 beta and test it?and if it also have any problem tell them to fix it?

---

### Post by gravufo on 2011-04-28
Any news on switchable graphics?

I've followed [http://linux-hybrid-graphics.blogspot.com/](http://linux-hybrid-graphics.blogspot.com/) a bit. Seems they have a beginning of a solution for other laptops including other ASUS laptops that use the same graphics card...so I've been wondering if we could apply the solutions to our laptop too...

BTW, any change in the methodology of your post when applied to Ubuntu 11, Natty?

I also saw there was a new "experimental" driver in the Proprietary drivers page. It will be the default for Ubuntu once they get it to a stable version and will replace the closed-source Nvidia driver...does that experimental driver include graphics switching of some sort?

Thanks a lot for the help!

---

### Post by arbrandes on 2011-04-29
gravufo, I haven't fooled around with Natty yet.  I will in the near future, I'm sure, and then I'll update the top post (or post a new thread).

Also haven't looked at the hybrid graphics blog in a while, but I certainly hope there are new developments!

About the experimental driver, it's probably the open-source nouveau with 3D stuff finally written in.  Not sure, though, I'll know when I try it. :)

---

### Post by rosencrantz on 2011-04-29
@gravufo I've also followed the hybrid graphics blog  - if I'm reading things right, hardware communication is rather different even with models from the same manufacturer, so I don't think the module will work. As the U43jc is pretty widespread and there are a few users on the mailinglist, I'm confident they will add it to the list as soon as they have a working solution.

---

### Post by avilella on 2011-04-30
> **arbrandes said:**
> gravufo, I haven't fooled around with Natty yet.  I will in the near future, I'm sure, and then I'll update the top post (or post a new thread).

Also haven't looked at the hybrid graphics blog in a while, but I certainly hope there are new developments!

About the experimental driver, it's probably the open-source nouveau with 3D stuff finally written in.  Not sure, though, I'll know when I try it. :)

There is a new switching method that relies on 3 calls to the ACPI: MXMX, MXDS and _DSM. The module is called asus-switcheroo and a bunch of Asus U/UL series laptops have the methods:

     72 03 Asus.U30JC.DSDT.dsl {        MXDS => 2       MXMX => 2       _DSM => 4 }
     73 03 Asus.U33JC.DSDT.dsl {        MXDS => 1       MXMX => 1       _DSM => 1 }
     74 03 Asus.U35JC.DSDT.2.dsl {      MXDS => 2       MXMX => 2       _DSM => 4 }
     75 03 Asus.U35JC.DSDT.dsl {        MXDS => 2       MXMX => 2       _DSM => 4 }
     76 03 Asus.U36JC.DSDT.dsl {        MXDS => 2       MXMX => 2       _DSM => 4 }

You can try it like this:

git clone git://github.com/awilliam/asus-switcheroo.git
cd asus-switcheroo; make; modprobe -r nouveau; insmod ./asus-switcheroo.ko; modprobe nouveau

---

### Post by rosencrantz on 2011-05-01
I've started testing on Natty - the touchpad and hibernation workarounds are still applicable without changes. The rest is on my to-do list, if no one else has found time to upgrade yet.

---

### Post by arbrandes on 2011-05-03
Just upgraded to Natty.  As rosencrantz reported, touchpad fixes still work.  Haven't tested much of the rest, though (I'm still fighting Unity, lol).

However, I did take a look at asus-switcheroo, and unfortunately it seems it will not work with the U43JC in its current form.  It needs two methods that I did could not find in my DSDT (MXMX and MXDS).  I didn't actually try it, but chances are slim.

---

### Post by gravufo on 2011-05-04
Hey guys, thanks for the info.

Well, my hibernation isn't working, it just stays on a black screen and doesn't turn off...

As for the touchpad, the fix doesn't seem to work, it's already applied but yet my two finger click still does the right click...oh well :D

Btw, fighting with unity too ^^ How the heck do u open two instances of the same program?

---

### Post by beew on 2011-05-04
Someone claims he has a solution to the Optimnus problem on Nvidia's Linux forum.

[http://www.nvnews.net/vbulletin/showthread.php?t=162171](http://www.nvnews.net/vbulletin/showthread.php?t=162171)

Don't know if it works or how well it works.

---

### Post by arbrandes on 2011-05-05
gravufo, haven't really tested hibernation yet.

As to the the two-finger-right-click configuration, apparently those two particular touchpad settings weren't included in Natty's gnome-settings-daemon.  Furthermore, yurivkhan's PPA hasn't been updated to support Natty with Unity, apparently.  In any case, a quick search turned up this PPA:

[https://launchpad.net/~o.shybystyi/+archive/gnome-settings-daemon-natty](https://launchpad.net/~o.shybystyi/+archive/gnome-settings-daemon-natty)

It should do what we need, though I haven't tested it yet.

beew, interesting link, but that requires leaving the nvidia card on, which as far as I'm concerned is unacceptable because it drains the battery all the time.  I find it simpler to just boot into Video Game Mode (i.e, Windows :) if I feel the need to do some Portal jumping.  (Ahh, the good ol' days of bootable games...)

[edit]By the way, I tested the DSDT.hex disabling mechanism and it still works as in Maverick.[/edit]

---

### Post by csdaniels on 2011-05-08
> **beew said:**
> Someone claims he has a solution to the Optimnus problem on Nvidia's Linux forum.

[http://www.nvnews.net/vbulletin/showthread.php?t=162171](http://www.nvnews.net/vbulletin/showthread.php?t=162171)

Don't know if it works or how well it works.

yes it works but has some issues.

---

### Post by jonno_wright on 2011-05-12
Hey Guys,
Great instructions. Thanks a lot.

Has nvidia-g210m-acpi stopped working for anyone else? 

It worked great for a couple of months, but has recently stopped working. Now I'm running at about 16W until I do the acpi_call manually by:

$ echo '\_SB.PCI0.RP00.VGA._PS3' | sudo tee -a /proc/acpi/call
$ cat /proc/acpi/call
Then it is back down to 11W or 12W. That means acpi_call is working right?

I tried checking if nvidia-g210m-acpi is loaded, by doing "lsmod | grep g210", and it is.
Any ideas?

---

### Post by arbrandes on 2011-05-12
jonno, I've just installed it in Natty, and can confirm it's working properly.  Have you tried uninstalling the dkms module and installing it again (basically just redoing what's described in the howto)?

---

### Post by jonno_wright on 2011-05-12
> **arbrandes said:**
> jonno, I've just installed it in Natty, and can confirm it's working properly.  Have you tried uninstalling the dkms module and installing it again (basically just redoing what's described in the howto)?

Thanks Arbrandes,
I haven't tried that yet. Is this the correct section of the howto?

$ sudo dkms remove -m nvidia-g210m-acpi -v 0.1.0 --all
$ sudo dkms add -m nvidia-g210m-acpi -v 0.1.0
$ sudo dkms build -m nvidia-g210m-acpi -v 0.1.0
$ sudo dkms install -m nvidia-g210m-acpi -v 0.1.0
$ echo nvidia_g210m_acpi | sudo tee -a /etc/modules

---

### Post by arbrandes on 2011-05-12
Yup, that's it.  Also make sure that the patch is properly applied (it's the step right above it in the Howto).

---

### Post by jonno_wright on 2011-05-13
> **arbrandes said:**
> Yup, that's it.  Also make sure that the patch is properly applied (it's the step right above it in the Howto).

Tried uninstalling nvidia_g210m_acpi last night, and re downloading, patching and installing. It didn't seem to make any difference.

When I reboot, power usage is high, acpi call is loaded and nvidia_g210m_acpi is loaded. When I test acpi call manually, it works, and power usage drops.

Could there be something else interfering with it?

---

### Post by arbrandes on 2011-05-13
I'm not sure what else could be wrong, jonno.  As I wrote, it has worked well for me for both Maverick and Natty.  Are you sure you're booting the right kernel?

---

### Post by TheoJava on 2011-05-14
Is the tutorial in the first post relevant for 11.04? Or would I be better off installing 10.10?

---

### Post by gravufo on 2011-05-14
Did you even bother reading before posting?

He said it still works on Natty 11.04, so you may go on.

BTW @arbrandes, random question, but are you having issues with wireless N like a huge slowdown up to the point it becomes unusable?

I looked it up on google and i found out that its a bug in the intel drivers, but all the comments/posts are from 2009 and it seems nothing has been done since =\

---

### Post by arbrandes on 2011-05-14
theojava, most of the howto applies to 11.04, with the notable exception of the yurivkhan PPA, which should be substituted with this one:

[https://launchpad.net/~o.shybystyi/+archive/gnome-settings-daemon-natty](https://launchpad.net/~o.shybystyi/+archive/gnome-settings-daemon-natty)

gravufo, I haven't used this notebook's wireless-N yet!  All the routers I've encountered so far were still G.  Are there any launchpad bugs opened for the issue?

---

### Post by gravufo on 2011-05-14
@arbrandes I just found the active launchpad bug report: [https://bugs.launchpad.net/ubuntu/+source/linux-firmware/+bug/630748](https://bugs.launchpad.net/ubuntu/+source/linux-firmware/+bug/630748)

though I'm a newbie in this stuff and haven't even had time to read the page so can't make up my mind yet :P

it says "Bug Watch Updater on 2011-05-12 Changed in linux: 
status: 	 Confirmed &#8594; Fix Released"

not sure if that means the bug has been fixed like two days ago? xD

That would be quite epic, I'm gonna try and boot into ubuntu (haven't been using it for quite a while because of that bug) and see if there's any new update!

Thanks a lot

---

### Post by arbrandes on 2011-05-14
gravufo, sometimes it really isn't very clear if a launchpad bug has been fixed or not, and if the fix has really been released.  That is the case with this one!

A cursory read-through was not very reassuring, though.  I see several people saying it was fixed, and a bunch saying it wasn't.  This of course means that there are actually several problems being reported.

Conclusion: try an update, maybe it'll work! :)

---

### Post by gravufo on 2011-05-14
hey again!

I tried and there were no updates, sadly!

I'll wait and see what happens...hopefully they'll actually get it done, because I'm not gonna put my wireless back to G just for that :P

---

### Post by TheoJava on 2011-05-15
Oh sorry, my bad. I did read through the topic before posting, but I guess it may have slipped my mind or something (I was kind of half asleep at the time. =^P).

Anyway, I just now made a new partition, installed Natty on it, and am about to follow through with the howto. I have one question though- is it normal that upon booting up, the system told me Unity is not supported on my hardware, and then automatically loaded Gnome?

Ok, as soon as I try to do the second group of commands in the howto, it tells me "DSDT.dsl.orig: command not found". =^/
Am I supposed to copy that second group of code, and paste it somewhere into the DSDT.dsl file?
(Sorry, I'm very new to any of this).

---

### Post by gravufo on 2011-05-22
it's a patch, not a command!

Try to google it to see how it works.

The basics is to just create a new file with the same name but with .patch at the end, then you can just paste the big code/text in the tutorial and save it. When that is done, you must issue the command "patch" (look it up on how to use it). Of course both files have to be in the same folder!

---

### Post by Kaho on 2011-06-29
Hello all !

I'm considering getting this laptop (like the design and the current price... still hesitating between this one and the U41JF though) and I was trying to find out as much as possible regarding its compatibility with Ubuntu.

I found an user review on a French website and another one on Amazon, both said that Ubuntu worked out of the box on this model... but when I look at the tweaks at the beginning of this thread, I am not so sure now... :p

About the Nvidia Optimus issue, did any of you try the Bumblebee solution ?
[[COLOR="DarkSlateBlue"]https://github.com/MrMEEE/bumblebee[/COLOR]]("https://github.com/MrMEEE/bumblebee")
For those who don't know, it's a simple script which will disable the Nvidia card for you but still allows you to swith to it if needed (not automatically though). 
I've seen that the U43JC is listed in the compatibility list of Bumblebee :)

Finally, I would like to know what can I expect from the U43JC regarding the battery life, _on Ubuntu_.
This model is said to be able to last 10hours, which I don't believe, but 5~6h , with casual use (internet...) will be fairly good for me. (arbrandes in the thread said he achievied something like this)
I know this is highly related to the disabling of the Nvidia card which drains battery life.
I'm really concerned about it as a long battery life is one of the main reason I want to buy a new laptop.

If you could answer my questions, I'd really appreciate it, Thank you :)

---

### Post by arbrandes on 2011-06-29
Kaho,

If you disable Nvidia, the U43JC can really last 5 to 6 hours, naturally depending on how much processor-intensive applications you use, if you have wifi on or off, etc.  However, you can trust me on this: this notebook's battery life is excellent compared to most others I've seen or used.  Fear not!

Regarding bumblebee, it looks great, will certainly try it ASAP!  Thanks!

---

### Post by ArchangeGabriel on 2011-07-07
Hi everybody.

I'm one of the dev working on Bumblebee, and it works very fine !

And guess what ... no further need to compile kernel with as custom DSDT !

I've worked on ACPI this afternoon, and I found why it wasn't working without any modification. In fact, acpi calls to make were a bit more complicated than for other models, but I've found the right ones, so that now you can forget ALL the disabling nvidia section !

---

### Post by arbrandes on 2011-07-07
Excellent news, ArchangeGabriel!!  I'll be sure to try it out as soon as I can!

---

### Post by ArchangeGabriel on 2011-07-07
Ok, just wait for my last commit to be commited in the master repo...

Also, before installing Bumblebee, be sure do undo everything you've make in the "Disable nvidia" section, else you may encounter some problems (you can go back to legacy kernel by the way)...

And for people just wanting to shutdown the nvidia card, here are the calls to make via acpi call :

echo "\_SB.PCI0.RP00.VGA._DSM {0xF8,0xD8,0x86,0xA4,0xDA,0x0B,0x1B,0x47,0xA7,0x2B,0x60,0x42,0xA6,0xB5,0xBE,0xE0} 0x100 0x1A {0x1,0x0,0x0,0x3}" > /proc/acpi/call

and then :

echo "\_SB.PCI0.RP00.VGA._PS3" > /proc/acpi/call

---

### Post by ArchangeGabriel on 2011-07-07
And the commit is commited !

There is also a ppa for an easier use : [The Bumblebee Project : MrMEEE]("https://launchpad.net/%7Emj-casalogic/+archive/bumblebee/")

---

### Post by Kaho on 2011-07-08
Thanks arbrandes for the answer and thanks ArchangeGabriel for putting so much effort in helping the linux communauty with bumblebee :)

I think I will get this laptop afterall... (go ASUS !)

I still have one question though : are the integrated Intel graphics enough to run Compiz  ? 
I don't play games or watch HD movies so I don't really care about using the Nvidia card on Ubuntu but I would like to have at least these desktop effects.
The model I want to buy comes with a core i3-380M instead of the usual i5-450M featured on US models but I was hoping it would be enough nevertheless...

---

### Post by ArchangeGabriel on 2011-07-08
The integrated intel is enough to run compiz (I run compiz with a lot of effects myself, and running on the intel).

I don't know if you want you compter right now, but if you can wait a little, Asus is about to release the new version really enhanced of this computer, the [U43SD](http://www.asus.com/Notebooks/Superior_Mobility/U43SD/).

Processor upgrade to Sandy Bridge (much better integrated graphic card and less power consumption), probably 8 Gb ram instead of 4 and finally nVidia upgraded from 310 to 520.

And all of this make really the difference.

I think it will be available in September.

---

### Post by Kaho on 2011-07-08
Ok, thank you for the information!

Yeah, U43SD looks indeed better but I'm not sure if I will be able to get it anytime soon. I live in France and here only a few models from the ASUS U serie are made available :(
Anyway, considering that the U43JC was sold at around 1000€ at the beginning, I guess that U43SD should be around the same price (if not higher !) and this it a bit to expensive for me as a student...
I don't really need a computer with high performance as my current 3 year-old F6V is already running fine to meet my needs : web surfing and some development mainly... so I guess I can just stick to 2010 processors and save 400€... while still getting a nice-looking laptop :)

---

### Post by ArchangeGabriel on 2011-07-08
Okay, I'm french too, and you're right, in france it would probably not be available before 2012...

---

### Post by gravufo on 2011-07-09
damn, poor you europeans! You pay the same price, but in euros....what a ripoff.

I payed 900$ (+ tax) canadian (I live in Québec and also speak French :P) for this laptop back in december 2010.

I really would like to get the new version of this laptop when it comes out though since I would be able to play games more smoothly or with better graphics. Other than that, the laptop is awesome and has incredible battery life!

The only thing that kinda annoys me is that the part where the CD-ROM is located is pretty flimsy and weak. Also, on the palm rest to the right side, there is a clicking noise when u put relatively low pressure (just putting ur hand when typing does the job) and then take it off... is it only me or does it do it to everyone? If it's only me, I'll probably send it back to repair before the warranty is out.

BTW @arbrandes: IF you do try bumblebee and it works better than the workaround you did with this tutorial, could you please do a small tutorial on how to get to bumblebee too? I'm kinda still newbie to linux so I will probably need some help :D And I'm sure I'm not the only one ^^

Thanks a lot at everyone who contributes, it's really cool ^^

---

### Post by ArchangeGabriel on 2011-07-09
> **gravufo said:**
> damn, poor you europeans! You pay the same price, but in euros....what a ripoff.

I payed 900$ (+ tax) canadian (I live in Québec and also speak French :P) for this laptop back in december 2010.

I really would like to get the new version of this laptop when it comes out though since I would be able to play games more smoothly or with better graphics. Other than that, the laptop is awesome and has incredible battery life!

The only thing that kinda annoys me is that the part where the CD-ROM is located is pretty flimsy and weak. Also, on the palm rest to the right side, there is a clicking noise when u put relatively low pressure (just putting ur hand when typing does the job) and then take it off... is it only me or does it do it to everyone? If it's only me, I'll probably send it back to repair before the warranty is out.

BTW @arbrandes: IF you do try bumblebee and it works better than the workaround you did with this tutorial, could you please do a small tutorial on how to get to bumblebee too? I'm kinda still newbie to linux so I will probably need some help :D And I'm sure I'm not the only one ^^

Thanks a lot at everyone who contributes, it's really cool ^^

So...

It's not european... It's france ! We're paying a lot of taxes :
1) TVA, 19,6% of the price
2) Tax for private copy, ~20€
3) Ten more various taxes
And the governement uses all this money to give it to rich people...

For U43SD, I agree it would have much much better graphic performances (including Dx11 on Windows), better battery life, and I hope Asus will fix some of the design problems (like the one you mentionned, that everyone is facing !), and even more, it could have a matt screen !

Finally, as you speaking of bumblebee to arbrandes, I think that you probably haven't read my post just above, and I giving you just under a guided tour to Bumblebee !

First of all, undo everything you've done within the Disabling nvidia section. I don't exaclty how to remove properly nvidia_g210m_acpi, but for the rest, all you have to do is to boot under the legacy kernel and uninstall the custom one.

After that, just do the followings :
sudo apt-get install ppa-purge
sudo ppa-purge ppa:ubuntu-x-swat/x-updates
sudo ppa-purge ppa:xorg-edgers/ppa
sudo apt-add-repository ppa:mj-casalogic/bumblebee
sudo apt-get update
sudo apt-get install bumblebee

---

### Post by arbrandes on 2011-07-18
Since there was a new kernel update recently, I took the opportunity to test bumblebee from the PPA: it works beautifully.  Thanks a lot ArchangeGabriel, this makes life MUCH easier! :)  The howto was updated accordingly.

Haven't really run any 3D intensive apps, though.  Thinking about trying it with gource, or some 3D game.  Suggestions? ;)

---

### Post by arbrandes on 2011-07-23
Had some trouble with the latest nvidia update from the bumblebee PPA.  After upgrading and rebooting, my video driver installation was messed up, probably because nvidia-current overwrote xorg.conf.

To fix this, I ran:

```
$ sudo dpkg-reconfigure bumblebee
```

Selected ArchangeGabriel's profile, as usual, rebooted, and voi la!

---

### Post by ArchangeGabriel on 2011-07-23
Yes, it's an actual bug, when you update the nvidia drivers, you have to run bumblebee-configuration again.

---

### Post by Spudgun79 on 2011-08-05
> **ArchangeGabriel said:**
> Ok, just wait for my last commit to be commited in the master repo...

Also, before installing Bumblebee, be sure do undo everything you've make in the "Disable nvidia" section, else you may encounter some problems (you can go back to legacy kernel by the way)...

And for people just wanting to shutdown the nvidia card, here are the calls to make via acpi call :

echo "\_SB.PCI0.RP00.VGA._DSM {0xF8,0xD8,0x86,0xA4,0xDA,0x0B,0x1B,0x47,0xA7,0x2B,0x60,0x42,0xA6,0xB5,0xBE,0xE0} 0x100 0x1A {0x1,0x0,0x0,0x3}" > /proc/acpi/call

and then :

echo "\_SB.PCI0.RP00.VGA._PS3" > /proc/acpi/call

I have a Pegatron (Asus for OEMs) which has an Optimus setup with a GT520m and the above comes up as working when running the acpi_call off_test.sh.  I've set up Bumblebee and followed some guidance about amending the bumblebee-enable/bumblebee-disable scripts to use the correct calls. The impression I get is usually there is one call to enable and one to disable.

If this is the disable call, is anyone aware if there is an enable call? I'm not entirely familiar with the subject, but I have been doing a lot of reading and trying things out. After trying the same command in each script (seeing if it would toggle) nothing untoward happened and running glxgears with and without the optirun command did have a massive effect on reported FPS so it's looking like it is working.

What I'm essentially trying to do is make sure when I'm on intel graphics that the nvidia card is not using unnecessary power for battery/potential excess heat considerations. Is there a way I can tell if the nvidia card is using up unnecessary power or not?

I hope I've explained myself okay, I've only been reading about all this for the last couple of days.

---

### Post by ArchangeGabriel on 2011-08-05
Enable call : echo "\_SB.PCI0.RP00.VGA._PS0" > /proc/acpi/call

For power : unplug AC cord.

grep rate /proc/acpi/battery/BAT0/state

Should be significantly less when the card is disabled.

---

### Post by ArchangeGabriel on 2011-08-23
You could check the new version here : [https://github.com/Bumblebee-Project/Bumblebee](https://github.com/Bumblebee-Project/Bumblebee).

Please not that power-management is removed for now.

---

### Post by arbrandes on 2011-10-18
Folks, I've updated the guide for Oneiric.  Of note:

* I've tested the version of "Project Bumblebee" with power management enabled using ArchangeGabriel's acpi calls, and it works great!  It seems to be a neater package than MrMEEE's previous attempts.

* There is as of yet no PPA-based solution to patch gnome-settings-daemon so that multi-finger touchpad clicking can be configured.

---

### Post by ArchangeGabriel on 2011-10-18
You may remove the change to /usr/share/acpi-support/power-funcs, as the issue as been fixed upstream (it's working out of the box).

By the way, I will receive a HDMI external screen tomorrow, so that I may be able to start work on supporting HDMI output through Bumblebee.

---

### Post by arbrandes on 2011-10-19
Thanks, ArchangeGabriel!  I removed the hack on power-funcs, it really is no longer needed.  Another small step on the way to not needing a howto at all! :)

Good luck on the HDMI endeavor.  I've never used it, not even on Windows.  But as new monitors and TVs come out, I guess it's inevitable!  If you need help in any way, post here and I'll do what I can.

---

### Post by arbrandes on 2011-10-19
Updated the guide so we use the new Gnome 3 "hotplug-command" hook to configure the touchpad.

However, as I described there, I wasn't able to get xinput to make a three-fingered tap be a right-click, independently of gnome-settings-daemon.  Still trying to figure out why.

---

### Post by arbrandes on 2011-10-19
Found the culprit of the three-finger tap problem:

[https://bugs.launchpad.net/ubuntu/+source/xserver-xorg-input-synaptics/+bug/873482](https://bugs.launchpad.net/ubuntu/+source/xserver-xorg-input-synaptics/+bug/873482)

Once we have a patch I'll post instructions on how to apply it.  (Out of the frying pan, into the fire :P).

---

### Post by arbrandes on 2011-10-20
Updated howto with a step-by-step to install [Jason Conti's fix]("https://code.launchpad.net/~jconti/ubuntu/oneiric/xserver-xorg-input-synaptics/bug-873482") for the three-finger tap problem.

---

### Post by jsevi83 on 2011-10-22
I tried the patch on an Asus A52F. I seems to solve the three finger tap issue, but now I lost two finger horizontal scrolling. Do you have the same problem?

---

### Post by gravufo on 2011-11-10
Hey, it's me again!

I tried the new Bumblebee and it doesn't seem to work, but I'm pretty sure I did something wrong.

Here is my question:

When you ask to create "/etc/bumblebee/cardon", do we put what you had in the box or what is in the reference file?

Same thing for the cardoff...

I used the stuff in the reference files (which seemed legit to me since it had structures to make sure it was good and to notify the user) but it doesn't seem to work.

Haven't had time to try doing it only with the stuff in the boxes in ur post.

Anyways, an explanation would be welcome as to why u removed the stuff from the reference files!

Thanks a lot for ur hard work (and to everyone that is committing time for this)

---

### Post by arbrandes on 2011-11-10
Hey gravufo!  I didn't keep the reference files because the acpi calls are specific to each notebook model.  What works for one will definitely not work for the other.  ArchangeGabriel was kind enough to figure out the correct ACPI call for our U43JC, and that is what I used.

Nevertheless, although it is much better packaged, this version of bumblebee still doesn't handle suspend/resume properly (see [this bug]("https://github.com/Bumblebee-Project/Bumblebee/issues/143")), so we need to implement a workaround.  I edited the bumblebee section of the first post to include it, but this is the gist of it:

Create /etc/pm/sleep.d/10_bumblebee with the following content:

```

#!/bin/sh

case "${1}" in
    hibernate|suspend)
        service bumblebee stop
        ;;
    resume|thaw)
        service bumblebee start
        ;;
esac

```

And make it executable:

```

$ sudo chmod a+x /etc/pm/sleep.d/10_bumblebee

```

---

### Post by ArchangeGabriel on 2011-11-11
> **gravufo said:**
> Hey, it's me again!

I tried the new Bumblebee and it doesn't seem to work, but I'm pretty sure I did something wrong.

Here is my question:

When you ask to create "/etc/bumblebee/cardon", do we put what you had in the box or what is in the reference file?

Same thing for the cardoff...

I used the stuff in the reference files (which seemed legit to me since it had structures to make sure it was good and to notify the user) but it doesn't seem to work.

Haven't had time to try doing it only with the stuff in the boxes in ur post.

Anyways, an explanation would be welcome as to why u removed the stuff from the reference files!

Thanks a lot for ur hard work (and to everyone that is committing time for this)

Maybe arbrandes should remove those "references", because they are from IronHide. In bumblebee, you should only put exactly what is in the box.

About suspend, I will add your code, that is in fact the easiest way to do it, thank you arbrandes.

---

### Post by arbrandes on 2011-11-12
References removed! :)

Cool, ArchangeGabriel, glad to be of service!

---

### Post by gravufo on 2011-11-15
hey guys, thanks a lot for the reply!

sorry for the late response, i've been quite busy with university :P

i'll try the suspend workaround and will take off the reference code i put. i hadn't noticed the acpi calls were different, that's why i just used the reference :P

i wa  probably braindead though, oh well!

i'll report back on how it works :)

thanks, cya!

---

### Post by gravufo on 2011-11-18
Hey,

I formatted my ubuntu partition and reinstalled (to test with a fresh install) and it still doesn't seem to work!

I did exactly what was said in the tutorial and after reboot, I'm at 15000mW or more with wifi off, no USB plugged in nor Wifi.

I don't understand what could be the culprit now >.<

Thanks a lot!

---

### Post by Haz0 on 2011-11-18
Longtime Asus U33JC-A1 Ubuntu user, first time poster!

Like Gravufo, followed the instructions by the letter on a fresh install after updates and it doesn't seem to work.

The output I get on battery state at "present rate" is 22000 mW, with wifi on and bluetooth off! Please help!

Thanks for all the hard work up until now and thanks in advance!

---

### Post by ArchangeGabriel on 2011-11-20
> **gravufo said:**
> Hey,

I formatted my ubuntu partition and reinstalled (to test with a fresh install) and it still doesn't seem to work!

I did exactly what was said in the tutorial and after reboot, I'm at 15000mW or more with wifi off, no USB plugged in nor Wifi.

I don't understand what could be the culprit now >.<

Thanks a lot!

I'm also having a 15000 mW (with WiFi on, and one USB device) minimal.

That's a known kernel bug in 3.0, 3.1 and 3.2, power consumption of Intel processors is higher than it should be.

It's fixed in kernel 3.3.

---

### Post by gravufo on 2011-11-21
Hey!

Linux kernel just got updated and it works!!

I'm at 10mW with everything on minimum, Wifi off and stuff :)

It's really awesome!

Thanks so much :)

---

### Post by TheoJava on 2011-11-26
I keep putting off this process. =^/ I should probably buckle down and try again (I'm pretty tired of using Windows =^P).

So far I've been using the 64 bit version of Ubuntu. I just assumed it was the right one to use (considering the hardware); am I correct in this thinking?

---

### Post by ArchangeGabriel on 2011-11-27
> **TheoJava said:**
> I keep putting off this process. =^/ I should probably buckle down and try again (I'm pretty tired of using Windows =^P).

So far I've been using the 64 bit version of Ubuntu. I just assumed it was the right one to use (considering the hardware); am I correct in this thinking?

Use either 64 or 32, both work, I personally prefer 32 as some programs are still not written for 64.

---

### Post by Haz0 on 2011-12-06
> **TheoJava said:**
> I keep putting off this process. =^/ I should probably buckle down and try again (I'm pretty tired of using Windows =^P).

So far I've been using the 64 bit version of Ubuntu. I just assumed it was the right one to use (considering the hardware); am I correct in this thinking?

Installed fresh Xubuntu 11.10 64-bit, updated to latest stable kernel. Followed commands on my Asus U33Jc (same configuration minus DVD drive), getting a present rate of 20K+ kW. Also, the command to fix the CPU freq limit did not work.

Any ideas?

---

### Post by ArchangeGabriel on 2011-12-06
Yep, you can't consider that your computer is the same, because that's wrong.

So the calls aren't the sames.

---

### Post by Haz0 on 2011-12-07
> **ArchangeGabriel said:**
> Yep, you can't consider that your computer is the same, because that's wrong.

So the calls aren't the sames.

Damn! How would I figure those calls out?

---

### Post by ArchangeGabriel on 2011-12-07
By following this procedure : 
[https://github.com/Bumblebee-Project/Bumblebee/wiki/ACPI](https://github.com/Bumblebee-Project/Bumblebee/wiki/ACPI)
(lastest lines)

---

### Post by TheoJava on 2012-02-18
So I reinstalled Ubuntu (in addition to getting fed up with, and ditching Windows all together). I started going through this how-to again, and found that the setting about the power management in bumblebee.conf aren't even in the actual file anymore. I also Googled Bumblebee and found that power management is enabled by default in the latest version...?

Does that make the Nvidia power management section on here unnecessary now? I mean, would I be able to get the same functionality by default after installing bumblebee now, or is there some other process I should go through?

---

### Post by ArchangeGabriel on 2012-02-18
Indeed, Bumblebee 3.0 has automatic support for Power Management. Even suspend is supported. So, installation of bumblebee is the only thing needed.

---

### Post by TheoJava on 2012-02-18
Sweet. =^]

---

### Post by arbrandes on 2012-02-19
That's right, all of that acpi_call and config file stuff is no longer necessary for bumblebee 3.0.  Howto updated accordingly.

---

### Post by arbrandes on 2012-05-18
Updated for 12.04.  Fn+F9 (disabling/enabling touchpad) now works out of the box, as well as 3-fingered tapping (although advanced configuration still requires using the hook).

---

### Post by TheoJava on 2012-05-25
I believe hdmi out is working now. I connected my laptop to an HD display. What happened is it recognized I was connected to 2 displays (the built in one, and the one connected via hdmi). The resolution seemed to fit the external display perfectly, the quality was nice and crisp, and I could move windows from the built in display to the external one.

However my taskbar would only display on the built in screen. I don't know if that's how it's supposed to work, if it's a problem with the distro, or if it's because I'm running Cinnamon. Still, it works! =^]

Also, I didn't bother with the frequency scaling portion of the how-to since my output was >2400000. I just ran the test again and got 2534000. Would I still benefit from it?

---

### Post by arbrandes on 2012-05-25
Hey TheoJava,

Thanks for the HDMI info: I hadn't tested it so I didn't know if it worked or not.

Frequency scaling: you probably won't benefit from it.  The problem happens when certain power-saving features of the BIOS are enabled using Windows-only tools.

Taskbar: I use Cinnamon too, and it's a feature.  I don't think you can configure it to show on two monitors at once.

---

### Post by jbarr on 2012-07-02
**[SIZE="4"]Fix Suspend[/SIZE]**

We have to unbind the USB buses manually before suspending.  Create /etc/pm/sleep.d/20_custom-asus-u43jc:

```

#!/bin/sh

EHCI_BUSES="0000:00:1a.0 0000:00:1d.0"
XHCI_BUSES="0000:04:00.0"

case "${1}" in
    hibernate|suspend)
        # Switch USB buses off
        for bus in $EHCI_BUSES; do
            echo -n $bus | tee /sys/bus/pci/drivers/ehci_hcd/unbind
        done
        for bus in $XHCI_BUSES; do
            echo -n $bus | tee /sys/bus/pci/drivers/xhci_hcd/unbind
        done
        ;;
    resume|thaw)
        # Switch USB buses back on
        for bus in $EHCI_BUSES; do
            echo -n $bus | tee /sys/bus/pci/drivers/ehci_hcd/bind
        done
        for bus in $XHCI_BUSES; do
            echo -n $bus | tee /sys/bus/pci/drivers/xhci_hcd/bind
        done
        ;;
esac

```

And make it executable:

```

$ sudo chmod a+x /etc/pm/sleep.d/20_custom-asus-u43jc

```


* No WiDi out.[/QUOTE]
I followed directions for Fix Suspend and suspend started working. But now on restart my fan runs full speed. It only resets to normal after a complete shutdown and restart from power off. How can I change this code to keep the fan from running full speed? Thanks in advance.

---

### Post by arbrandes on 2012-07-03
jbarr, I have never had this problem.  Are you running an U43JC with Ubuntu 12.04?

---

### Post by simontaylor on 2012-10-05
I've got my bamboo working thanks to this thread and happily so... however, five months in and my touchpad has become annoyingly erratic - I better say that I'm running linux mint 13 cinnamon 64-bit... based on precise, but mint forum has not been so helpful - hence requesting help from this quarter or half or whatever it is of the os. 

I've followed a couple of leads, including the debian wiki [http://wiki.debian.org/SynapticsTouchpad](http://wiki.debian.org/SynapticsTouchpad)
and made probably noob mistakes in the process... which have neither broken the machine nor fixed the problem...

subsequently following the advice at the beginning of this thread I added a folder to HOME/.config called touchpadconf in the absence of a HOME/bin...

probably silliness, for which forgive me, but going crazy trying to fix this... and no advice seems to fit the user case.

Please let me know if you have any insights, experience, recommendations to share.

Best,

Simon

---

### Post by arbrandes on 2012-10-05
Simon, you have to put touchpadconf somewhere in your $PATH, which is not the case with $HOME/.config.  I suggest you create $HOME/bin/ and put it there.

---

### Post by simontaylor on 2012-10-05
thanks...

can you please explain how best to create the directory + file on the executable path?

I've tried adding by creating a new folder and changing permissions to make executable ... and ended up with a bin directory in my home /home/simon/bin

this can't be right. I deleted that...

jumping cursor makes it hard to write this.

I appreciate the help.

Best,

Simon:confused:

---

### Post by arbrandes on 2012-10-08
A bin directory in your home (/home/simon/bin) is exactly what's needed.  It will be automatically included in your executable path.

---

### Post by simontaylor on 2012-10-24
if I may prevail on your patience once more!

what I was doing was not in bin or creating a bin on the path but simply in my home file

where the script needs to go opens in terminal as > /bin $

...

I need to use a terminal command to add the script using sudo... but having saved the script I don't know the command to add it to my existing bin file

...

can you please tell me what command to use to add the script to /bin $ ...?

best,

Simon:confused:

---

### Post by simontaylor on 2012-10-24
so I > sudo mv touchpad from desktop where it was saved to /bin

I check... yes, it's there.

then I > $ chmod a+x /bin/touchpadconf because it wasn't finding the script or directory at > $HOME/bin

and followed the directions for gsettings... rebooted... something strange, reboot gave me a boot menu ... I went through recovery just in case. No probs.

I rebooted and everything opened fine however > xinput returns  > Virtual core pointer                    	id=2	[master pointer  (3)]
&#9116;   &#8627; Virtual core XTEST pointer              	id=4	[slave  pointer  (2)]
&#9116;   &#8627; ImPS/2 Generic Wheel Mouse              	id=13	[slave  pointer  (2)]
 

as before...

---

### Post by TheoJava on 2012-11-07
So about the 12.10 release-

After installing the 64 bit version of Quantal and installing Bumblebee, it didn't take me long to find that the optirun command would only spit out an error. This remained true regardless of any troubleshooting measures I took.

So I've re-installed with the 32 bit version, and installed Bumblebee along with the bumblebee-nvidia package, ie-
```
sudo apt-get install bumblebee bumblebee-nvidia
```It seems to work fine that way, though I haven't tested the power-saving.

Was the script for fixing suspend intended to make it work in general, or does it only apply to a specific use-case involving USB devices or something? Cause so far my suspend seems to work just fine without applying the script.

---

