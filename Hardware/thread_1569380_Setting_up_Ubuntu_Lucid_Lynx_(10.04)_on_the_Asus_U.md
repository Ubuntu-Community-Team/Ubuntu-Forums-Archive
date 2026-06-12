---
title: "Setting up Ubuntu Lucid Lynx (10.04) on the Asus U35JC"
date: 2010-09-06
forum: Hardware
---

### Post by Flupke on 2010-09-06
[SIZE="5"]Install a newer kernel[/SIZE]

```
$ sudo add-apt-repository ppa:kernel-ppa/ppa
$ sudo apt-get update
$ sudo apt-get install linux-image-generic-pae-lts-backport-maverick \
                     linux-headers-generic-pae-lts-backport-maverick \
                     build-essential
```

Reboot to use the new kernel (2.6.35-19 at the time of writing).

**Update**: 2.6.35-19 is the best kernel I tried so far regarding battery usage, I can get as low as 8W with it, while newer kernels don't drop below 12W (tried 2.6.35-22 and 2.6.37-7 from the kernel PPA). 

[SIZE="5"]Install acpi_call to disable the Nvidia card[/SIZE]

The Nvidia discrete graphics card doesn&#8217;t work at the time of this writing, so it&#8217;s best to completely disable it to save battery. You&#8217;ll need the acpi_call module to do so:
```
$ git clone http://github.com/mkottman/acpi_call.git
$ cd acpi_call
$ make
```
This builds a kernel module named acpi_call.ko. Try it and see if it works:
```
$ grep rate /proc/acpi/battery/BAT0/state
present rate:            19913 mW
$ sudo insmod acpi_call.ko
$ sudo echo '\_SB.PCI0.PEG1.GFX0._OFF' > /proc/acpi/call
$ grep rate /proc/acpi/battery/BAT0/state
present rate:            12558 mW
```
Copy the module to the current kernel's modules library. You'll need to do this after each kernel upgrade :
```
$ sudo cp acpi_call.ko /lib/modules/`uname -r`/kernel/drivers/acpi/
$ sudo depmod
```
And have it loaded at boot time: edit **/etc/modules** and add an acpi_call line to it. This is how it looks on my system after a fresh install:
```
# /etc/modules: kernel modules to load at boot time.
#
# This file contains the names of kernel modules that should be loaded
# at boot time, one per line. Lines beginning with "#" are ignored.

lp
acpi_call
```
To disable the discrete graphics card at startup, edit /etc/rc.local and add the acpi_call command to it, e.g.:
```

#!/bin/sh -e
#
# rc.local
#
# This script is executed at the end of each multiuser runlevel.
# Make sure that the script will "exit 0" on success or any other
# value on error.
#
# In order to enable or disable this script just change the execution
# bits.
#
# By default this script does nothing.

echo '\_SB.PCI0.PEG1.GFX0._OFF' > /proc/acpi/call

exit 0
```
Last but not least, blacklist the nouveau driver (it caused instability on my system when playing with acpi_call). Create a file named **/etc/modprobe.d/blacklist-nvidia.conf** with this content:
```
blacklist nouveau
blacklist nvidia
```
And regenerate the initramfs image for the current kernel:
```
$ sudo update-initramfs -u
```
Reboot, and verify your power consumption is at its minimum.

To have the acpi_call recompiled after each kernel upgrade, copy the acpi_call source to /usr/local/src: 
```
$ cd .. && sudo mkdir -p /usr/local/src && sudo cp -r acpi_call /usr/local/src
```

Then create a script named /etc/kernel/postinst.d/acpi-call and put the following in it:
```
#!/bin/bash

# We're passed the version of the kernel being installed
inst_kern=$1

if [ ! -e /usr/local/src/acpi_call ] ; then
    echo "acpi_call: WARNING - Failed to find source directory /usr/local/src/acpi_call.  Cannot proceed" >&2
    exit 0
fi

cd /usr/local/src/acpi_call/
rm -f acpi_call.ko
make

if [ ! -e acpi_call.ko ] ; then
    echo "acpi_call: WARNING - Failed to build.  Will not be installed in the new kernel" >&2
    exit 0
fi

cp acpi_call.ko /lib/modules/${inst_kern}/kernel/drivers/acpi/
```
And make it executable:
```
$ sudo chmod 755 /etc/kernel/postinst.d/acpi-call
```

[SIZE="5"]Make the trackpad toggle (Fn+F9) button work[/SIZE]

Edit **/etc/acpi/asus-touchpad.sh** and replace the script with this:
```
#!/bin/sh
[ -f /usr/share/acpi-support/state-funcs ] || exit 0 

. /usr/share/acpi-support/power-funcs

getXconsole

DEVICE_ID=`xinput -list | grep -i touchpad | grep id= | sed 's/.*id=\([0-9]*\).*/\1/' `

if xinput -list-props $DEVICE_ID | grep "Device Enabled" | grep "1$" > /dev/null
then
    xinput set-int-prop $DEVICE_ID "Device Enabled" 8 0
else
    xinput set-int-prop $DEVICE_ID "Device Enabled" 8 1
fi
```

[SIZE="5"]Configure the trackpad for X[/SIZE]

The trackpad is recognized correctly as a synaptics device with Maverick&#8217;s (2.6.35) kernel. This has the effect of making the &#8220;multitouch&#8221; functions stop to work. Add this in **/etc/X11/xorg.conf** to bring them back:
```
Section "InputClass"
    Identifier "touchpad catchall"
    MatchIsTouchpad "on"
    MatchDevicePath "/dev/input/event*"
    Driver "synaptics"
    Option "VertTwoFingerScroll" "on"
    Option "HorizTwoFingerScroll" "on"
    Option "CircularScrolling" "off"
    Option "CricularTrigger" "0"
    Option "TapButton1" "1"
    Option "TapButton2" "2"
    Option "TapButton3" "3"
EndSection
```

**Note**: this may not be necessary, my trackpad only stopped to function properly once and I haven't been able to reproduce the issue. You can fix it if it happens to you with this config though.

[SIZE="5"]Fix suspend[/SIZE]

Suspend doesn&#8217;t work out of the box because of a [problem with the USB buses](http://ubuntuforums.org/showthread.php?t=1444822), we need to disable them before going to sleep.

We also need to switch the nvidia card back on before suspending, or it becomes impossible to switch it off with acpi_call after two suspend cycles.

Create a file named **/etc/pm/sleep.d/20_custom-asus-u35jc** and paste this script:
```
#!/bin/sh

BUSES="0000:00:1a.0 0000:00:1d.0"

case "${1}" in
    hibernate|suspend)
        # Switch USB buses off
        for bus in $BUSES; do
            echo -n $bus | tee /sys/bus/pci/drivers/ehci_hcd/unbind
        done
        # Switch nvidia card on before going to sleep, avoids the "constant on"
        # bug that occurs after 2 suspend/resume cycles (thanks kos888)
        echo '\_SB.PCI0.PEG1.GFX0._ON' > /proc/acpi/call
        ;;
    resume|thaw)
        # Switch USB buses back on and nvidia card off
        for bus in $BUSES; do
            echo -n $bus | tee /sys/bus/pci/drivers/ehci_hcd/bind
        done
        echo '\_SB.PCI0.PEG1.GFX0._OFF' > /proc/acpi/call
        ;;
esac
```
Don&#8217;t forget to make it executable :
```
chmod +x /etc/pm/sleep.d/20_custom-asus-u35jc
```

[SIZE="5"]Fix flipped webcam under Skype[/SIZE]

The video comes out flipped upside down. Here is a trick to make it behave correctly under Skype. Create a script, e.g. in /usr/bin/skype-webcam-fixed:
```
#!/bin/sh
export LIBV4LCONTROL_FLAGS=3 
LD_PRELOAD=/usr/lib/libv4l/v4l1compat.so /usr/bin/skype
```
Or on 64 bits systems:
```
#!/bin/sh
export LIBV4LCONTROL_FLAGS=3 
LD_PRELOAD=/usr/lib32/libv4l/v4l1compat.so /usr/bin/skype
```

Make it executable :
```
chmod +x /usr/bin/skype-webcam-fixed
```

Now when you want to run skype use this script instead of /usr/bin/skype.

[SIZE="5"]Things not working[/SIZE]
[LIST]
[*]Hibernate results in a black screen, though it works in single user mode so it should not be too hard to fix. To reboot use the magic SysRq sequence (hold Alt+Print Scr and type R, E, I, S, U, B)
[*]Nvidia card is not working
[/LIST]

[SIZE="1"]This is adapted from my [blog post](http://schawat.wordpress.com/2010/09/01/configuring-the-asus-u35jc-on-ubuntu-lucid-lynx-10-04/), which itself is a compilation of infos from around the internet and this forum.[/SIZE]

---

### Post by Flupke on 2010-09-06
Hibernate works well in single user mode, and at the first login screen. Once logged in it fails, ending with a black screen. Going back to the login screen doesn't help, you have to reboot for it to work again, so it must be some service started after login that makes hibernation fail.

---

### Post by Zeebo on 2010-09-12
Just got this laptop yesterday, and was trying to figure out if both graphics cards were running. Thanks for the information on how to disable the nvidia card, pushed my estimated battery life out ~ 2 hours (was using 14000 mW, down to 8500 mW after disabling the second card)! Really only need the 310m for games in 7, so I'm fine with Intel for Ubuntu.

I'm running the maverick beta (which seems like a bad call now if I'm going to have to make those changes each kernel update...), and after setting the touchpad to be two-finger scroll in the Mouse configuration GUI, it seems to be working fine, I can do the multi-finger taps for different clicks, so I'm happy.

Haven't tried suspend/hibernate yet.

---

### Post by allannk on 2010-09-12
Im buying a new laptop in less than an hour. 

Either this or the UL30VT. 

I havent heard a lot of linux users with this one yet, how is total battery-time?

---

### Post by Flupke on 2010-09-13
> **allannk said:**
> Im buying a new laptop in less than an hour. 

Either this or the UL30VT. 

I havent heard a lot of linux users with this one yet, how is total battery-time?
I get 6-7 hours in continuous usage, I think it's pretty on par with windows.

---

### Post by Zeebo on 2010-09-13
It's probably too late now, but my vote would be for the U35JC, I haven't played with a ul30vt, but I've seen the 14 or 15 inch variant at BestBuy, and they have the worst keyboard support I've ever seen. Pressing on any key makes the entire keyboard flex significantly. The 13" might not have that problem due to a smaller chassis and no optical drive, but I'm not sure.

The U35JC has newer hardware, with a full power i3 CPU and slightly better graphics (310m is pretty much the same thing as the 210m), but you won't get quite the battery life out of it that you would with the slower clocked ul30vt. The build quality on my U35JC is pretty solid, keyboard flexes a little, but other than that it's built well.

With either one, make sure you disable one of the graphics cards to get optimum battery life.

---

### Post by allannk on 2010-09-14
Hey guys, thanks for the advice. 

I was walking from one to the other several times, but at last I ended up with this - the U35JC. Received it an hour ago, and I can only agree on the build-quality, it seems to be good. 

Thanks for the help :-)

---

### Post by osensei on 2010-09-16
Hey! Thanks for all the tips! I'm waiting for this laptop to arrive.

Have any of you heard a high pitched noise while using this laptop with Ubuntu? It seems many people are hearing it (at least in Windows 7) and I am concerned about it.

---

### Post by aro87 on 2010-09-17
Thanks for the help! Seems that the U35JC is working very well in ubuntu as well! I was wondering; If I disable the graphicscard - would the laptop still be able to render highdef movies without stuttering?

About the high pitched noise; I heard the noise in Windows 7 but, strangly, I cannot hear it in Ubuntu. Either that, or has my hearing been reduced in the last few days :)

---

### Post by Zeebo on 2010-09-17
I think the whine is from the hard drive, I've heard it once or twice in Windows, but have yet to hear it in Ubuntu.

I'm not sure about the specifics on Intel's driver for the Corex chips, but even CPU alone you should be fine playing high def videos. I haven't heard much muttering about the intel driver, so my assumption is it includes hardware acceleration. I know Nvidia's VDPAU works fine in linux for accelerating videos.

Keep in mind, the U35JC has two graphics cards, its a hybrid setup optimized for windows, where it will automatically switch between Intel and Nvidia depending on what you're doing. In Ubuntu, both will be enabled by default, so you'll be using more power than you should be until you disable one or the other.

Have any of you tried out the web cam in Ubuntu? Mine shows upsidedown when I try to use Cheese. Strangely, there's significant delay in Windows using it, but in Ubuntu it's much faster and actually fairly usable.

---

### Post by osensei on 2010-09-17
> **aro87 said:**
> I was wondering; If I disable the graphicscard - would the laptop still be able to render highdef movies without stuttering?

The intel chip is more than capable of rendering HD movies, so don't worry about that. Anyway, Ubuntu is not using the NVIDIA card at all, the purpose of disabling it is to not waste battery power on it, being that it's not being used.

> **aro87 said:**
> About the high pitched noise; I heard the noise in Windows 7 but, strangly, I cannot hear it in Ubuntu. 

It's good to hear that! :) Your words, not the noise ;)

---

### Post by aro87 on 2010-09-18
I disabled the Nvidia card yesterday; and you're correct. The laptop still handles HD movies _very well_ :)

> **Zeebo said:**
> 
Have any of you tried out the web cam in Ubuntu? Mine shows upsidedown when I try to use Cheese. Strangely, there's significant delay in Windows using it, but in Ubuntu it's much faster and actually fairly usable.
About the webcam (mine is also upside down, running Lucid at 64bits) I'm pretty sure this is an usual issue with asus's laptops. Its mentioned [here]("https://launchpad.net/~asus-ul30") at launchpad

---

### Post by kos888 on 2010-09-24
Just wanted to thank the OP for this thread, it helped me get my U35jc set up within an hour or so. If anyone has a fix so that the nvidia card doesn't activate itself after suspend, let us know! It's the only thing missing to make this system perfect (that and hibernating of course)

I also wanted to share another thread with some great tips to save battery life and to fix the Fn F9 combination (toggles the trackpad on/off):

[http://ubuntuforums.org/showpost.php?p=9328344&postcount=110](http://ubuntuforums.org/showpost.php?p=9328344&postcount=110)

---

### Post by kos888 on 2010-09-26
This wake-up script I threw together fixed the Nvidia suspend issue for me - I can suspend an indefinite number of times and the card is switched off upon resumption. (adapted from the wpa script in /etc/pm/sleep.d/ and the suspend fix posted by the OP)

Create a script /etc/pm/sleep.d/20_suspend-dg and enter the following:

```
#!/bin/sh
# File: "/etc/pm/sleep.d/20_suspend-dg".

case "${1}" in
        suspend|hibernate)
                echo '\_SB.PCI0.PEG1.GFX0._ON' > /proc/acpi/call
                ;;
        resume|thaw)
                echo '\_SB.PCI0.PEG1.GFX0._OFF' > /proc/acpi/call
esac
```

Make it executable:

```
sudo chmod +x /etc/pm/sleep.d/20_suspend-dg
```

I know - it's crazy that you have to turn the card on when suspending and then off again when it wakes, but that's the only way I could get it to work. It should apply to hibernating as well if we ever get that fixed.

Please report back on whether the script works for you as well ):P

---

### Post by kos888 on 2010-09-26
Also, maybe the OP can add the toggle-trackpad (Fn+F9) fix to the original post:

To get working disable touchpad (Fn+F9) button:


```
sudo gedit /etc/acpi/asus-touchpad.sh

```

delete everything and paste this:

```

#!/bin/sh
[ -f /usr/share/acpi-support/state-funcs ] || exit 0 

. /usr/share/acpi-support/power-funcs

getXconsole

DEVICE_ID=`xinput -list | grep -i touchpad | grep id= | sed 's/.*id=\([0-9]*\).*/\1/' `

if xinput -list-props $DEVICE_ID | grep "Device Enabled" | grep "1$" > /dev/null
then
    xinput set-int-prop $DEVICE_ID "Device Enabled" 8 0
else
    xinput set-int-prop $DEVICE_ID "Device Enabled" 8 1
fi
```

save and close.

---

### Post by Flupke on 2010-09-26
Thanks kos888, I merged your on/off nvidia trick with the USB buses one in a "custom_asus-u35jc" pm-utils script, and also added the fix for the trackpad button.

The tips to save battery life are indeed great, made me win a steady 2W of power. I would prefer them to be activated only when on battery though, but I don't get how /etc/acpi/power.sh works (this is apparently the script called when switching AC/battery)

---

### Post by kos888 on 2010-09-26
> **Flupke said:**
> Thanks kos888, I merged your on/off nvidia trick with the USB buses one in a "custom_asus-u35jc" pm-utils script, and also added the fix for the trackpad button.

The tips to save battery life are indeed great, made me win a steady 2W of power. I would prefer them to be activated only when on battery though, but I don't get how /etc/acpi/power.sh works (this is apparently the script called when switching AC/battery)

Good call on merging the two scripts into one! Also I never thought about the fact that the battery saving methods are constantly on. Will try to do some research into how that might be fixed.

---

### Post by Zaremos on 2010-09-29
Seems that the scale for the display brightness is a bit off which results in a brightness greater than 100% when the ac-power is plugged in, which the display does not like. I fixed this by changing the "Set the display brightness to" setting under the AC-power properties. Changing the brightness over 55-60% with the fn buttons results in a black display for the same reason.

[SOLVED]

This thread really fixed a lot of problems for me, so thank you!

I have encountered another issue and that is that my display dims down to 0 when I plug in the AC power... it brightens up to 100% again when I unplug the AC power. I can't change the brightness with the fn+f5/6 buttons when using AC and fiddling with the display power settings does not seem to help.

Anyone got a solution for this?

---

### Post by flowerdealer on 2010-10-16
Hi, could anyone post updated instructions for 10.10? The apci calls freeze my system. I did not do the kernel installation step, though. Should I follow it? Thanks!

---

### Post by osensei on 2010-10-16
> **flowerdealer said:**
> Hi, could anyone post updated instructions for 10.10? The apci calls freeze my system. I did not do the kernel installation step, though. Should I follow it? Thanks!

Hi flowerdealer, I followed this guide with Ubuntu 10.10 except for the kernel update and the X configuration for the trackpad steps, and had no problem with it.

I haven't had any issue with the acpi_call module and my NVIDIA card is being disabled as expected.

Is your laptop model U35JC-A1?

---

### Post by flowerdealer on 2010-10-16
Yes, the same model... might give it another go though.

---

### Post by osensei on 2010-10-16
I'm not sure whether it could have anything to do with it, but just to let you know... I'm using the 64 bits version of Ubuntu, and I have updated the BIOS to version 208.

If you want to update the BIOS you can download the latest version from [http://support.asus.com](http://support.asus.com). Be aware that if you do it you should use the Winflash utility (I think that was its name) that comes preinstalled in Windows to flash the BIOS (you can download the utility from the support site also). I've read in another forum that people who tried to update the BIOS from the BIOS setup itself, got their laptops bricked.

---

### Post by flowerdealer on 2010-10-17
Ok, so I tried again, and it seems to work now... although how can I tell for sure? As a side note, using ubunut control center with vga switcheroo, I was able to switch to the nvidia card (not with propietary drivers, though). The only problem is that not matter what I tried, I was never able to switch back to integrated graphics, so I actually ended up reinstalling.

Another problem that I have is that I dont get a graphical boot with the ubuntu splash screen, anyone else has gotten this? Thanks.

---

### Post by flowerdealer on 2010-10-17
I really dont know about this one... I have followed the steps above, and they do seem to work, but battery life is still very inferior to windows, at least 2 or 3 hours, and the machine runs a lot hotter and louder. What would be an actual test to see if the gpu is still running or not?

---

### Post by osensei on 2010-10-18
Try running this in a terminal:
```
lsmod | grep acpi_call
```

Does it return anything at all? If it doesn't, it means that the acpi_call module is not loaded, and hence the NVIDIA gpu is not being disabled.

On the other hand, while running on battery close every application, set the display bright to the minimum, and then run this on a terminal and see what it returns:
```
grep rate /proc/acpi/battery/BAT0/state
```

In my case I get a value between 10500 mW and 12500 mW, if you get something much higher than that, then your NVIDIA gpu is for sure not being disabled.

---

### Post by withaar on 2010-10-18
I have an asus U35JC-A1 running ubuntu 10.10. The instructions by an large work for this setup.

For the video inversion - I submitted the info to Hans de Goede (maintainer v4l at Redhat) and he included this machine in the library. There will probably be an update to the libraries in the launchpad soon.

In the meantime this wrapper script works for me for e.g. skype:

```

#!/bin/sh

if [ ! -e ~/.Skype/shared.xml ]; then
  mkdir -p ~/.Skype
  cp /usr/share/skype/shared.xml ~/.Skype/shared.xml
fi

export LIBV4LCONTROL_FLAGS=3
LD_PRELOAD=/usr/lib/libv4l/v4l1compat.so /usr/bin/skype "$@"

```

which is the standard wrapper script in 10.10 with the export line added in.

W

---

### Post by flowerdealer on 2010-10-18
Thanks for your help. According to your instructions, it does seem like the nvidia card is disabled. Still, the battery life seems worse, plus more heat and fan noise. Could it be related to compiz use?

---

### Post by mathews.kyle on 2010-10-25
Hey Folks. Thanks for all your help w/ these scripts. With them, I've got most everything working nicely on my new Asus U35JC running Ubuntu 10.10. One remaining problem is I can't suspend. I've added the script listed by the OA but still when I try to suspend, the screen goes black and I see the following message: "GLib-WARNING **: getpwuid_r(): failed due to unknown user id (0)" and my computer just sits there until I do a hard-reset.

Anyone know what this means and how to fix it?

---

### Post by mathews.kyle on 2010-10-25
False alarm. Fixed it. As it turns out, the Glib warning was a red herring. The real problem, as it turned out, was I left off a letter when I copy/pasted the suspend script... :)

I figured that out when I looked at /var/log/pm-suspend.log and saw that it was complaining about a syntax error in the custom suspend script. I compared that with the original, adding the missing character and suspend started working (albeit w/ the Glib warning still there).

---

### Post by sergu on 2010-11-12
Linux newbie here, Ubuntu 10.10. Thanks a lot for help,  nVIDIA fix  works. However I sometimes have problem with sleep(0r is it suspend?) I have implemented sleep script and on close lids laptop sleep. However on the opening lid I get black screen. Mostly on moving mouse I can get login screen and everything is OK, but other times trackpad freez and I can't not  login.
PS can I get rid of black and login screens on opening lids?
Next question:
I'm trying trackpad fix now, however I don't have xorg.conf file. To create it I need Xorg -configure (?)  and stop X-server(?) . But on the command sudo service gdm stop is causing system hang and crush. Any advices?
Thanks again
PPS all this could be wubi problem. I'll try reinstall into normal partition

---

### Post by sergu on 2010-11-19
Reinstalled 10.10 into partition instead of wubi. Now NVIDIA fix and suspend works both AC and battery. I'm afraid to try multituch fix - generating xorg.conf permanently(!) crush wubi and it's not critical...

---

### Post by Flupke on 2010-12-02
Bump, added a note about best kernel version regarding battery usage.

---

### Post by kos888 on 2010-12-02
> **Flupke said:**
> Bump, added a note about best kernel version.

Thanks for the tip. Can confirm that downgrading to 2.6.35.19 saves 1-2W compared to the .22 kernel.

---

### Post by kos888 on 2010-12-02
> **kos888 said:**
> Thanks for the tip. Can confirm that downgrading to 2.6.35.19 saves 1-2W compared to the .22 kernel.

I should add that I couldn't find .19 in the latest PPA but there are .deb packages of the image & headers here: [https://mirror.umoss.org/ubuntu/pool/main/l/linux/](https://mirror.umoss.org/ubuntu/pool/main/l/linux/)

---

### Post by kos888 on 2010-12-03
New bug under 10.10:

Fn+F9 no longer toggles the touchpad - it has to do with this file: /usr/share/acpi-support/power-funcs

I found a patch here:
[https://bugs.launchpad.net/ubuntu/+source/acpi-support/+bug/314376/+attachment/1694811/+files/power-funcs.patch](https://bugs.launchpad.net/ubuntu/+source/acpi-support/+bug/314376/+attachment/1694811/+files/power-funcs.patch)

If you want to do it manually:

sudo gedit /usr/share/acpi-support/power-funcs

delete this part near the top:

```

getXuser() {
	user=$(who | awk "/:$displaynum)/ { print \$1; exit }")

	if [ x"$user" = x"" ]; then
		user=$(who | awk "/:$displaynum/ { print \$1; exit }")
	fi
	if [ x"$user" != x"" ]; then
        	userhome=`getent passwd $user | cut -d: -f6`
        	export XAUTHORITY=$userhome/.Xauthority
	else
		export XAUTHORITY=""
	fi
}

```

and replace with:

```

getXuser() {
	user=$(who | awk "/:$displaynum)/ { print \$1; exit }")

	if [ x"$user" = x"" ]; then
		user=$(who | awk "/:$displaynum/ { print \$1; exit }")
	fi
	export XAUTHORITY=`ps a | grep -v grep | grep X | sed -n 's/.*-auth \(.*\)/\1/p' | cut -f 1 -d ' '`
}

```

---

### Post by kerezov on 2010-12-06
Everything works perfectly, except I can't fix my Skype camera.

Anyone has any suggestions? I made that script however skype still has me upside down. I am not extremely familiar with Linux, I have some basics down, however.

What I did was make the script using sudo gedit /path/to/file and added the lines you had. 

Am I missing something?

---

### Post by Flupke on 2010-12-07
> **kerezov said:**
> Everything works perfectly, except I can't fix my Skype camera.

Anyone has any suggestions? I made that script however skype still has me upside down. I am not extremely familiar with Linux, I have some basics down, however.

What I did was make the script using sudo gedit /path/to/file and added the lines you had. 

Am I missing something?

The file you created is the script you have to launch to use the fix, e.g. in your example, you now have to launch "/path/to/file" instead of "/usr/bin/skype" (it also has to be executable, i.e. "chmod +x /path/to/file")

---

### Post by kerezov on 2010-12-08
> **Flupke said:**
> The file you created is the script you have to launch to use the fix, e.g. in your example, you now have to launch "/path/to/file" instead of "/usr/bin/skype" (it also has to be executable, i.e. "chmod +x /path/to/file")


Worked perfectly!

Thank you.

---

### Post by _sAm_ on 2010-12-16
Thank you so much Flupke and others for sharing this information - I would be helpless without it! 

Ubuntu is working fine now on my Asus and I don't need Windows7 that came with it.

Looking forward to next Ubuntu, I believe the new dock(unity) will be better on this small screen.

Edit;
Do you know if its possible to get my settings in the "brightness applet" to bee persistent(I use to have it on lowest during lectures, and its always goes back after reboot)?

---

### Post by vittorio.scaravilli on 2010-12-24
Hello, i tried to install ubuntu from an usb drive on my asus u35jc, but i can't get it to work. In my bios setting i can't choose which drive to boot. Can you help me?

---

### Post by buren on 2010-12-25
anyone knows why u sometimes can hear a high pitch sound under windows 7, nothing when running Ubuntu (10.04...). 

Another thing thats seems weird when hearing the sound under windows is that it stops when u open a videofile or play a music file... any ideas?

---

### Post by sergu on 2010-12-29
> **vittorio.scaravilli said:**
> Hello, i tried to install ubuntu from an usb drive on my asus u35jc, but i can't get it to work. In my bios setting i can't choose which drive to boot. Can you help me?

Put USB in, reboot. In the beginning of the boot press esq (I just do it sevral times so not to miss)and you will get menu with usb boot option. That way u can do it without changing bios setting. You can also try wubi(ubuntu in windows file) but wubi have problems with sleep on u35jc.

---

### Post by sergu on 2010-12-29
> **buren said:**
> anyone knows why u sometimes can hear a high pitch sound under windows 7, nothing when running Ubuntu (10.04...). 

Another thing thats seems weird when hearing the sound under windows is that it stops when u open a videofile or play a music file... any ideas?

 That is known prob, but depend on person hearing. Some ppl hear it, some don't. I don't hear it, some reviewers do.

---

### Post by buren on 2011-01-05
> **sergu said:**
> That is known prob, but depend on person hearing. Some ppl hear it, some don't. I don't hear it, some reviewers do.

do u know why thats sound occur in win7?

---

### Post by d98jh on 2011-01-07
Hi guys!

Really happy about my U35JC and how well ubuntu works. Thanks to all who provided info and fixes in this thread!

I have a question though. Is it possible to make the laptop resume when I open the lid? It suspends fine when I close it but I have to open the lid and press the power button to wake it which I didn't need with my previous laptop. Any thoughts?

---

### Post by SolipsistX on 2011-01-22
My thanks all who have contributed to this thread.  I got a U35JC not long ago and this thread was a huge help.

To contribute, here is my kernel postinst script to get acpi_call recompiled each time there is a new kernel.  It will automatically recompile and install the acpi_call.ko kernel module whenever a new kernel package is installed.

This assumes that your acpi_call source directory is under /usr/local/src.  If you put it somewhere else, just change the "cd /usr/..." line below.

Create /etc/kernel/postinst.d/acpi-call and put the following in it:

```

#!/bin/bash

# We're passed the version of the kernel being installed
inst_kern=$1

if [ ! -e /usr/local/src/acpi_call ] ; then
    echo "acpi_call: WARNING - Failed to find source directory /usr/local/src/acpi_call.  Cannot proceed" .&2
    exit 0
fi

cd /usr/local/src/acpi_call/
rm -f acpi_call.ko
make

if [ ! -e acpi_call.ko ] ; then
    echo "acpi_call: WARNING - Failed to build.  Will not be installed in the new kernel" >&2
    exit 0
fi

cp acpi_call.ko /lib/modules/$inst_kern/kernel/drivers/acpi/
```

And I believe you need to make the file executable:

```

$ sudo chmod 755 /etc/kernel/postinst.d/acpi-call
```

This has been through one kernel update  on my machine (just a ubuntu version of the same kernel, but a new directory was created under /lib/modules), so this script has had at least one round of testing.

---

### Post by Flupke on 2011-01-23
Thanks SolipsistX I added your script to the post.

---

### Post by rahman on 2011-01-24
> **Flupke said:**
> 
To have the acpi_call recompiled after each kernel upgrade, copy the acpi_call source to /usr/local/src: 
```
$ sudo cp -r acpi_call /usr/src
```


I think it should be
```
$ sudo cp -r acpi_call /usr/local/src
```

> 
```
 echo "acpi_call: WARNING - Failed to find source directory /usr/local/src/acpi_call.  Cannot proceed" .&2
```


And I think it should be
```
echo "acpi_call: WARNING - Failed to find source directory /usr/local/src/acpi_call.  Cannot proceed" >&2
```

---

### Post by Flupke on 2011-01-24
Fixed, thanks rahman !

---

### Post by SolipsistX on 2011-01-29
After upgrading to 2.6.35-25, I found a problem with the postinit.d script.  It was compiling against the currently running kernel (instead of the new one), which may or may not cause a problem with these minor updates.  Luckily it did this time so I noticed the problem.  v0.2 of /etc/kernel/postinst.d/acpi_call:

```

#!/bin/bash

# We're passed the version of the kernel being installed
inst_kern=$1

if [ ! -e /usr/local/src/acpi_call ] ; then
    echo "acpi_call: WARNING - Failed to find source directory /usr/local/src/acpi_call.  Cannot proceed" .&2
    exit 0
fi

cd /usr/local/src/acpi_call/
rm -f acpi_call.ko
make KDIR=/lib/modules/$inst_kern/build clean
make KDIR=/lib/modules/$inst_kern/build

if [ ! -e acpi_call.ko ] ; then
    echo "acpi_call: WARNING - Failed to build.  Will not be installed in the new kernel" >&2
    exit 0
fi

cp acpi_call.ko /lib/modules/$inst_kern/kernel/drivers/acpi/

```

And related to kernel 2.6.35-25, does any one else see a significant increase in power usage from this kernel?  I'm seeing 15W at idle where as 2.6.35-24 was 11W or 10W at idle.  I've found and installed 2.6.35-19, which some people say gives them the lowest power usage, but I'm getting 15W from it too.  And I know the nvidia card is off because I can turn it back on and the power draw goes up over 20W.

---

### Post by SolipsistX on 2011-01-29
> **SolipsistX said:**
> 
And related to kernel 2.6.35-25, does any one else see a significant increase in power usage from this kernel?  I'm seeing 15W at idle where as 2.6.35-24 was 11W or 10W at idle.  I've found and installed 2.6.35-19, which some people say gives them the lowest power usage, but I'm getting 15W from it too.  And I know the nvidia card is off because I can turn it back on and the power draw goes up over 20W.

Never mind, I figured it out.  It was the cpu scaling.  After reading /etc/init.d/ondemand, it looks like the computer must start out at full speed, and then 60 seconds after the freq scaling service starts, it moves it to the ondemand state, where it scales down to 933 MHz most of the time.  I was rebooting, logging in, and checking the battery fast enough that I was measuring it with the CPU at full speed.

Once I measured all the kernels at at the same CPU speed (933 MHz), I found that 2.6.35-19 is actually better.  The others (-22, -24, -25) were 12-13W, while -19 was 10-11W.

---

### Post by Sisco88 on 2011-02-01
Running this on bootup hangs startx, i run 2.6.37-ARCH.
disabling the card after i started X works fine but not right after boot, if i run the disable script during boot and then try to run X it hangs.

anyone?

---

### Post by ubuntoide on 2011-03-04
Hi guys, I found a little error in the postinst.d building script on the acpi_call section. The make file provided from acpi_call git runs against the kernel currently in use (as you can see from the line (shell uname -r). This could lead to some problem as I found installing a different kernel (2.6.38) and not just a sub-version of the same kernel (2.6.whatever-xx)

Is there a clean way to pass the variable inst_kern created in the automatic script directly to the makefile?

---

### Post by SolipsistX on 2011-03-04
See my reply for an updated script [http://ubuntuforums.org/showpost.php?p=10409151&postcount=50](http://ubuntuforums.org/showpost.php?p=10409151&postcount=50).  The original summary post hasn't been updated.

---

### Post by ubuntoide on 2011-03-05
not noticed that post, thank you for the reply :D

---

### Post by buren on 2011-03-23
> **SolipsistX said:**
> See my reply for an updated script [http://ubuntuforums.org/showpost.php?p=10409151&postcount=50](http://ubuntuforums.org/showpost.php?p=10409151&postcount=50).  The original summary post hasn't been updated.

I have the exact same issue, with the new kernel (2.6.35-25). When idle: ~15-16mW, graphic card On: ~>20mW......

---

### Post by flowerdealer on 2011-04-24
Has anyone here tried the asus switcheroo with this model? [https://github.com/awilliam/asus-switcheroo/blob/master/README](https://github.com/awilliam/asus-switcheroo/blob/master/README)

---

### Post by monsieurweller on 2011-05-29
Hello !
So, the nvidia card finally works with bumblebee !!!!

First, you have to remove all you've done with acpi_call : 
```
sudo modprobe -r acpi_call
```

And edit the file /etc/rc.local to remove the line you've previously added.
```
sudo gedit /etc/rc.local
```
Remove the line
echo '\_SB.PCI0.PEG1.GFX0._OFF' > /proc/acpi/call
download the archive in here :
[HTML]https://github.com/MrMEEE/bumblebee[/HTML]
(click on the download button)

Then, extract the content, run a terminal, go in the bumblebee folder (the one you have just extracted) and run :
```
sudo bash install.sh
```

Follow the instruction (for the laptop model, chose 10, and for the second choice, choose 4).
Reboot.

To launch an app with the nvidia card, juste run, for 64 bit apps (ut2004, trine...) :
```
optirun64 app
```
Or, for a 32 bit app (for exemple : lugaru, quake3... AND WINE)
```
optirun32 app
```

---

### Post by monsieurweller on 2011-05-29
> **monsieurweller said:**
> Hello !
So, the nvidia card finally works with bumblebee !!!!

First, you have to remove all you've done with acpi_call : 
```
sudo modprobe -r acpi_call
```And edit the file /etc/rc.local to remove the line you've previously added.
```
sudo gedit /etc/rc.local
```Remove the line
echo '\_SB.PCI0.PEG1.GFX0._OFF' > /proc/acpi/call
download the archive in here :
[HTML]https://github.com/MrMEEE/bumblebee[/HTML](click on the download button)

Then, extract the content, run a terminal, go in the bumblebee folder (the one you have just extracted) and run :
```
sudo bash install.sh
```Follow the instruction (for the laptop model, chose 10, and for the second choice, choose 4).
Reboot.

To launch an app with the nvidia card, juste run, for 64 bit apps (ut2004, trine...) :
```
optirun64 app
```Or, for a 32 bit app (for exemple : lugaru, quake3... AND WINE)
```
optirun32 app
```

There is a support for automatic enable/disable the card, but it require to edit a script with laptop custom settings, and i didn't have the knowledge to do that.
So guys, i count on you ! :D



Edit : another tips.
If you want to set up a working dual-screen with the intel chipset, without turning mad, install the app **arandr** (if the one from the repository fail to launch, download the git version and compile it), which is a GUI for xrandr.
It's pretty easy to use, and you can do cool stuff with : define resolutions, place a screen on the left/right/up/down of the other, rotate the screen (but no cloning it seems).
Wayyyyyyyyy better than the crappy gnome/ubuntu screen manager (gnome-display-properties).

---

### Post by monsieurweller on 2011-05-31
Wow ! The latest bumblebee source provides scripts for our laptop ! And it works well !  So you have to do that :  ```
 sudo cp ./install-files/bumblebee-disablecard.K42Jc.K52Jc.N53Jf.N53Jg.N71JV.N73JF.P52JC.U30JC.U33JC.U35JC.U36JC /usr/local/bin/bumblebee-disablecard 
```  ```
 sudo cp ./install-files/bumblebee-enablecard.K42Jc.K52Jc.N53Jf.N53Jg.N71JV.N73JF.P52JC.U30JC.U33JC.U35JC.U36JC /usr/local/bin/bumblebee-enablecard 
```  I've made an histogram to show the progress (well... It's in french, so just compare the difference between the two left bars and the two right bars ; lower is better) [[IMG]http://pix.toile-libre.org/upload/img/1306854951.png[/IMG]]("http://pix.toile-libre.org/?img=1306854951.png")

---

### Post by bertbiker on 2011-06-02
Thanks for this very useful posting on disabling NVIDIA. It works pretty well, also in Debian squeeze. The only issue was that checking discharge rate from the command line did not work:

bertos@debian:~/acpi_call$ grep rate /proc/acpi/battery/BAT0/state
grep: /proc/acpi/battery/BAT0/state: No such file or directory

From the Power Statistics application under the battery icon in gnome it was clear that the discharge rate dropped from around 17 W to 11 W at light use.

---

### Post by monsieurweller on 2011-06-03
Well probably that your system give another name to the battery. So it must be /proc/acpi/battery/nameofthebattery/stat in place of /proc/acpi/battery/BAT0/state .

---

### Post by bananafeller on 2011-06-18
EDIT: boy do i feel stupid... the laptop was plugged in......
hi
 i have a u30jc and in 10.10 this tutorial worked perfectly for me. now i installed 11.04 and my battery rate is 44 mW which is crazy high. and its not decreasing. if someone can give me a hand it would really appreciate it.

---

### Post by buren on 2011-06-29
bumblebee has fixed open-source nvidia optimus support check these links out:

[https://github.com/MrMEEE/bumblebee/commit/a047be85247755cdbe0acce6#diff-1](https://github.com/MrMEEE/bumblebee/commit/a047be85247755cdbe0acce6#diff-1)
[http://www.omgubuntu.co.uk/2011/06/bumblebee-gets-a-ppa-brings-nvidia-optimus-graphics-switching-to-ubuntu/](http://www.omgubuntu.co.uk/2011/06/bumblebee-gets-a-ppa-brings-nvidia-optimus-graphics-switching-to-ubuntu/)

---

### Post by Z06Gal on 2011-07-01
It is working great for me! ;)

---

### Post by auburn on 2011-10-15
The suspend fix, /etc/pm/sleep.d/20_custom-asus-u35jc had worked great for me until I upgraded to oneiric 11.10. But removing the script made suspend work again. IOW, with oneiric on an asus u35, suspend just works!

---

### Post by larsemil on 2012-04-13
> **auburn said:**
> The suspend fix, /etc/pm/sleep.d/20_custom-asus-u35jc had worked great for me until I upgraded to oneiric 11.10. But removing the script made suspend work again. IOW, with oneiric on an asus u35, suspend just works!

That was acctually the case for me as well. :)

---

