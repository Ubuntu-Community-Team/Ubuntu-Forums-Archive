---
title: "Setup Guide: ASUS U36Jc - Ubuntu 11.04 Alpha3 64-bit"
date: 2011-03-12
forum: Hardware
---

### Post by Menthu_Rae on 2011-03-12
I know there are other guides out there for the U36Jc but I thought I'd post this up to help those who really want to be on the bleeding edge running Ubuntu 11.04.

The guide applies to 64-bit versions but should also apply for 32-bit should you wish to run it.

[SIZE="4"]_ASUS U36Jc Setup Guide - Ubuntu 11.04 64-bit_[/SIZE]

[SIZE="3"]_* Reduce Hard Disk Power Cycling_[/SIZE]

If you are running the standard SSH/HDD then you will want to reduce the frequency of head parking so as to not prematurely wear out the drive. You can do this by running:

```
gksu gedit /etc/hdparm.conf
```

Adding in the following text...

**<INSERT BELOW TEXT>**

```
/dev/sda {
	    apm = 254
	    apm_battery = 254
	}
```

[SIZE="3"]_* Enable Palm Detection & Horizontal Scrolling on Touchpad_[/SIZE]

You can enable two-finger scrolling on the touchpad by going to:

```
System > Preferences > Mouse > Touchpad > Scrolling > Two Finger Scrolling [check]
```

Additionally we can enable horizontal scrolling and palm detection by editing the following file:

```
gksu gedit /usr/share/X11/xorg.conf.d/50-synaptics.conf
```

Inserting in the following text before **EndSection**:

**<INSERT BELOW TEXT>**

```
Option "HorizTwoFingerScroll" "on"
Option "PalmDetect" "on"
```

[SIZE="3"]_* Disable NVidia GPU/NVidia Optimus_[/SIZE]

------------------------------------------------------------------------------------------------------------------------------------------------------------

**Important Note:** _Under NO circumstances should you install the nvidia restricted drivers!_

Due to the design of optimus, the NVidia card is unable to be utilised in Linux with the nVidia restricted drivers. People are currently working on enabling Optimus through the use of the open source nVidia drivers, see here for more details [Warning: Links below are **very** experimental, do not attempt if you are not an expert]:

[http://linux-hybrid-graphics.blogspot.com/2011/05/updated-list-of-laptops-with.html](http://linux-hybrid-graphics.blogspot.com/2011/05/updated-list-of-laptops-with.html)

[https://github.com/awilliam/asus-switcheroo](https://github.com/awilliam/asus-switcheroo)

The guide however does not mess with extremely-alpha software (as linked above) and instead will allow you to run **only** on the Intel GPU when using Ubuntu, thus saving power by having the NVidia GPU switched off.

If you are trying to disable Optimus on a laptop *other than* the U36Jc, please read this post:

[http://ubuntuforums.org/showpost.php?p=10557451&postcount=5](http://ubuntuforums.org/showpost.php?p=10557451&postcount=5)
------------------------------------------------------------------------------------------------------------------------------------------------------------

The ASUS U36Jc uses the NVidia Optimus system of switchable graphics. Unfortunately, because NVidia are absolute champions (and because of the hardware design of Optimus/way it functions), this system will likely never be officially supported by NVidia on Linux.

As a result, the NVidia GPU is constantly switched on - although due to the design of Optimus - it is not able to be used. This is bad for battery life since your laptop will be using another ~6W just idling.

So what we need to do is switch off the NVidia GPU so that we can reclaim our battery life whilst making use of the Intel GPU.

So let's get started... make a hidden directory in your home directory and change into it by entering:

```
mkdir ~/.optimus
cd ~/.optimus/
```

Next, let's install git so we can grab the acpi_call module that will let us switch the NVidia GPU off...

```
sudo apt-get install git
git clone http://github.com/mkottman/acpi_call.git
```

Once that's downloaded, let's change into the acpi call directory and make the module.

```
cd acpi_call/
make
```

Now let's insert the module and copy it to the acpi folder for our kernel...

```
sudo insmod ./acpi_call.ko
```

Run this command and take note of the kernel version number...

```
uname -r
```

Copy the module in and run depmod...

```
sudo cp acpi_call.ko /lib/modules/**<UNAME -R VALUE>**/kernel/drivers/acpi/
sudo depmod
```

Now let's edit /etc/modules so that it's loaded on startup...

```
gksu gedit /etc/modules
```

**<INSERT BELOW TEXT>**

```
acpi_call
```

Now that we've done all of that, let's make a "service" that can be started/stopped to turn the GPU on and off for us.

```
gksu gedit /etc/init.d/optimusoff
```

**<INSERT BELOW TEXT>**

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
### END INIT INFO
 
. /lib/lsb/init-functions
 
set -e
 
case "$1" in
start)
#
echo '\_SB.PCI0.PEG1.GFX0._OFF' > /proc/acpi/call
;;
stop)
echo '\_SB.PCI0.PEG1.GFX0._ON' > /proc/acpi/call
;;
*)
echo '\_SB.PCI0.PEG1.GFX0._OFF' > /proc/acpi/call
N=/etc/init.d/optimusoff
echo "Usage: $N {start|stop}\nBy default, 'start' is executed.\n" >&2
exit 1
;;
esac
 
exit 0
```

Now let's make it executable and run at startup.

```
sudo update-rc.d optimusoff defaults 98 02
sudo chmod a+x /etc/init.d/optimusoff
```

Now's a good time to make sure it works... let's check our current power consumption. **Make sure the laptop is running on battery before testing this - otherwise your readings will not be correct.**

```
grep rate /proc/acpi/battery/BAT0/state
```

You should get a value similar to this...

> present rate:            15148 mW

OK so now let's see if we can turn the NVidia GPU off and check how much power we're saving...

```
sudo service optimusoff start
```

Now let's check the power usage again...

```
grep rate /proc/acpi/battery/BAT0/state 
```

You can see if it's working, the power usage has dropped dramatically, by around 54% in my case.

> present rate:            9828 mW

Now lets just make sure to blacklist the nouveau and nvidia modules since they will cause problems if enabled.

```
gksu gedit /etc/modprobe.d/blacklist-nvidia.conf

```

Now we need to insert this text...

**<INSERT BELOW TEXT>**

```
blacklist nouveau
blacklist nvidia
```

Now run this and we're all done for this section!

```
sudo update-initramfs -u
```

[SIZE="3"]_* Fix Suspend/Resume Issues_[/SIZE]

Let's fix some issues with the USB buses and also the NVidia/Intel GPUs when undertaking suspend/resume operations.

```
gksu gedit /etc/pm/sleep.d/20_custom-asus-u36jc
```

**<INSERT BELOW TEXT>**

```
#!/bin/sh

BUSES="0000:00:1a.0 0000:00:1d.0"
BUSES3="0000:07:00.0"

case "${1}" in
    hibernate|suspend)
	# Switch USB buses off
	for bus in $BUSES; do
	    echo -n $bus | tee /sys/bus/pci/drivers/ehci_hcd/unbind
	done
	# Switch USB 3.0 buses off
	for bus in $BUSES3; do
	    echo -n $bus | tee /sys/bus/pci/drivers/xhci_hcd/unbind
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
	# Switch USB 3.0 buses back on
	for bus in $BUSES3; do
	    echo -n $bus | tee /sys/bus/pci/drivers/xhci_hcd/bind
	done
	# Switch optimus off before resuming, avoids unneccessary power draw
	/etc/init.d/optimusoff start
	;;
esac
```

Next just make it executable and we're done for this section.

```
sudo chmod +x /etc/pm/sleep.d/20_custom-asus-u36jc
```

[Size="3"]_* Fix USB3.0 Port_[/SIZE] (thanks to DeeKey)

To fix the USB 3.0 (Fresco Logic FL1000G) port, we need to update the parameters when launching Ubuntu via GRUB.

```
gksu gedit /etc/default/grub
```

Find the line:

```
GRUB_CMDLINE_LINUX_DEFAULT
```

and add the following within the quotation marks, being sure to separate it with a space from any other entries:

```
pci=nomsi,noaer
```

Now run...

```
sudo update-grub
```

and on the next reboot the USB 3.0 port should work.

[SIZE="3"]_* Fix Camera Issues_[/SIZE]

Let's add a PPA and some updated packages to fix the camera issues.

```
sudo add-apt-repository ppa:libv4l
sudo apt-get update && sudo apt-get install gtk-v4l libv4l-0

```

Next be sure to edit this file and add in the following text...

```
gksu gedit /etc/environment
```

**<INSERT BELOW TEXT>**

```
LIBV4LCONTROL_FLAGS=2
```

We can also run non-native GTK apps by preloading the updated module.

```
LD_PRELOAD=/usr/lib32/libv4l/v4l1compat.so **<appname>**
```

You can put this in a script, e.g. *appname.sh* and then use *sh* to run said script (e.g. *sh appname.sh*) from a desktop or applications menu link.

[SIZE="3"]OK so that's it! Your U36Jc should be all set up and ready to use. Enjoy Ubuntu 11.04! Hopefully in time Optimus will be able to be used with some "hacking" or native support will be provided for it by providing asus-switcheroo by default in distributions.[/SIZE]

[SIZE="2"]**References:**[/SIZE]

Special thanks/mention to the authors of the following resources who's efforts enabled me to make this guide and get everything working:

*Sergio Fernández Marcos & Andrej Sokol*: [https://help.ubuntu.com/community/Asus_U36JC](https://help.ubuntu.com/community/Asus_U36JC)

*Olivier Robert*: [http://robbyx.net/blog/?p=190](http://robbyx.net/blog/?p=190)

*DeeKey*: [http://ubuntuforums.org/showpost.php?p=10834900&postcount=44](http://ubuntuforums.org/showpost.php?p=10834900&postcount=44)

---

### Post by Peleus on 2011-03-12
This guide is a life saver - Thank you so much!!!!

---

### Post by dugh on 2011-03-13
Thanks, I used these tips to turn off the nvidia optimus card (gt 325m) in my asus n61j series (n61jv) laptop, too.

---

### Post by Trevice on 2011-03-13
so there is no way to use the nvidia card under linux??

---

### Post by Menthu_Rae on 2011-03-13
> **dugh said:**
> Thanks, I used these tips to turn off the nvidia optimus card (gt 325m) in my asus n61j series (n61jv) laptop, too.

Please be careful with this. I have actually omitted the part where you figure out which ACPI call to use to switch off the GPU since this guide is intended **only** for the U36Jc.

If anyone reading this would like to switch off their NVidia GPU in their Optimus-enabled Laptop, I would suggest following this guide below (the ./test_off part) and modifying the calls to echo to /proc/acpi/call.

> [SIZE="3"]**Using acpi_call module to switch on/off discrete graphics card in Linux**[/SIZE]

One of the hybrid-graphics-linux Launchpad team members has 
created a Linux kernel module to call ACPI methods through 
/proc/acpi/call. The code is here:

[http://github.com/mkottman/acpi_call](http://github.com/mkottman/acpi_call)

You can try it by installing the module and calling it like this:

git clone [http://github.com/mkottman/acpi_call.git](http://github.com/mkottman/acpi_call.git)

cd acpi_call

make

sudo insmod acpi_call.ko

./test_off.sh

**Source:** [http://linux-hybrid-graphics.blogspot.com/2010/07/using-acpicall-module-to-switch-onoff.html](http://linux-hybrid-graphics.blogspot.com/2010/07/using-acpicall-module-to-switch-onoff.html)

> **Trevice said:**
> so there is no way to use the nvidia card under linux??

This is correct. The way Optimus works is that the Intel and NVidia GPUs work in tandem (when necessary). Basically the NVidia GPU takes over GPU calculations from the Intel GPU but still writes the results back out (framebuffer) to the Intel GPU.

As a result, drivers for both GPUs need to be loaded (and support Optimus). Unfortunately due to the architecture of Linux in regards to graphics / X / etc - this is not possible (as far as I am aware) :(

The workaround is to use something being developed called "vga_switcheroo" - that restarts X but with the appropriate driver loaded - however, it only works with open source drivers, not the closed nvidia blobs. I'm not sure whether nouveau supports it yet or not.

If anyone knows if any of the above is wrong, please let me know! But that's my understanding of the current situation.

---

### Post by korg91 on 2011-03-14
So you are definitively the best!

I haven't read many guides as clear as yours. 
It seems very clear and complete to me, and I am so happy that a linux user like you got this model so soon. (I am not so happy about the lack of support for optimus on linux, no matter about whose the fault is)

Unfortunately i don't have the u36 yet, because I'm still waiting for the sandy bridge + nvidia 520m refresh (which will hopefully be announced soon -does anyone knows something about this?-).

Anyway, as you saw your guide has already been useful :)

Thank you very much again, when I will apply your guide I will surely write to you!

Happy linux-ing!

---

### Post by macrostheblonde on 2011-03-14
great info.. thanks for that:)

Once you've disabled the nvidia card is it possible to change the amount of memory that the Intel GPU uses or are you stuck with whatever the standard is? Is the Intel GPU powerful enough to run compiz desktop effects
Trying to decide whether to grab it still as this laptop was of interest to me, but the lack of support for optimus / the nvidia card is disappointing.

---

### Post by Menthu_Rae on 2011-03-15
> **macrostheblonde said:**
> great info.. thanks for that:)

Once you've disabled the nvidia card is it possible to change the amount of memory that the Intel GPU uses or are you stuck with whatever the standard is? Is the Intel GPU powerful enough to run compiz desktop effects
Trying to decide whether to grab it still as this laptop was of interest to me, but the lack of support for optimus / the nvidia card is disappointing.

Yes the Intel GPU is perfectly fine with Compiz effects, no slowdown/lag at all - very smooth and snappy.

If you are going to dual-boot with Windows, grab the U36Jc. At least then you can still use the NVidia card where it's needed (games/CAD work).

If you aren't going to dual-boot, and JUST run Ubuntu, grab the U31F. It's the same spec as the U36Jc - just minus the NVidia card. :)

> **korg91 said:**
> So you are definitively the best!

I haven't read many guides as clear as yours. 
It seems very clear and complete to me, and I am so happy that a linux user like you got this model so soon. (I am not so happy about the lack of support for optimus on linux, no matter about whose the fault is)

Unfortunately i don't have the u36 yet, because I'm still waiting for the sandy bridge + nvidia 520m refresh (which will hopefully be announced soon -does anyone knows something about this?-).

Anyway, as you saw your guide has already been useful :)

Thank you very much again, when I will apply your guide I will surely write to you!

Happy linux-ing!

Thanks for the kind words guys - but it's mainly a compilation of other peoples work as noted. Without their help I couldn't have made it work for the U36!

---

### Post by macrostheblonde on 2011-03-15
> **Menthu_Rae said:**
> Yes the Intel GPU is perfectly fine with Compiz effects, no slowdown/lag at all - very smooth and snappy.

If you are going to dual-boot with Windows, grab the U36Jc. At least then you can still use the NVidia card where it's needed (games/CAD work).

If you aren't going to dual-boot, and JUST run Ubuntu, grab the U31F. It's the same spec as the U36Jc - just minus the NVidia card. :)


Thanks for the advice:) I will be running just ubuntu. I had looked at the U31F, but i prefer the look and weight of the U36JC. I don't need to play games / do any CAD work so the Intel GPU should be fine for my purposes. Do you know how much of the system memory the Intel GPU uses?

Thanks!

---

### Post by brolick on 2011-03-25
> **korg91 said:**
> So you are definitively the best!

I haven't read many guides as clear as yours. 
It seems very clear and complete to me, and I am so happy that a linux user like you got this model so soon. (I am not so happy about the lack of support for optimus on linux, no matter about whose the fault is)

Unfortunately i don't have the u36 yet, because I'm still waiting for the sandy bridge + nvidia 520m refresh (which will hopefully be announced soon -does anyone knows something about this?-).

Anyway, as you saw your guide has already been useful :)

Thank you very much again, when I will apply your guide I will surely write to you!

Happy linux-ing!
where did you heard about the Sandy Bridge + Nvidia 520m  ?

---

### Post by LarsEriksson on 2011-03-29
Great guide! Its a bit sad that the nVidia-card does not work though. Is there any other way to enable it? ie. with third part drivers?

And/or is there any way to use the HDMI-port without the nVidia-card enabled? i want to connect 2 external monitors.

---

### Post by anjexe on 2011-03-31
hope to work in n43 too

---

### Post by anjexe on 2011-03-31
> **anjexe said:**
> hope to work in n43 too

Using acpi_call module to switch on/off discrete graphics card in Linux

One of the hybrid-graphics-linux Launchpad team members has 
created a Linux kernel module to call ACPI methods through 
/proc/acpi/call. The code is here:

[http://github.com/mkottman/acpi_call](http://github.com/mkottman/acpi_call)

You can try it by installing the module and calling it like this:

git clone [http://github.com/mkottman/acpi_call.git](http://github.com/mkottman/acpi_call.git)

cd acpi_call

make

sudo insmod acpi_call.ko

./test_off.sh

---

### Post by Aimevous on 2011-04-13
Hi, does the settings change hardware settings?

I'm using a A42JV.

The reason I am asking is that after I only did the following:

> Using acpi_call module to switch on/off discrete graphics card in Linux

One of the hybrid-graphics-linux Launchpad team members has 
created a Linux kernel module to call ACPI methods through 
/proc/acpi/call. The code is here:

[http://github.com/mkottman/acpi_call](http://github.com/mkottman/acpi_call)

You can try it by installing the module and calling it like this:

git clone [http://github.com/mkottman/acpi_call.git](http://github.com/mkottman/acpi_call.git)

cd acpi_call

make

sudo insmod acpi_call.ko

./test_off.sh

and then when I rebooted into Windows, my nvidia card is "missing". It is using purely the intel display.

How can I turn my nvidia card back on?
How I know its off is when I go back to Windows initially, I saw my display resolution was wrong and after a reboot it defaulted back to my Intel driver. Then I refreshed the Windows Experience rating and I saw the score for the graphics drop from 6.4 to 4.9.
Also, when I try to run my nvidia driver installation files, it fails and tells me there is no nvidia hardware.

I tried going into my BIOS (F2) but I dont see any Nvidia settings.

Please help!
Thanks!

---

### Post by duende_2 on 2011-04-15
Menthu_Rae, many thanks for your instructions. They have been extremely  helpful. I actually use Fedora 14,  not  Ubuntu, but I followed the  instructions of the first post with some obvious changes and everything went  very smoothly. I registered to this forum just to say: thank you!

---

### Post by or3x on 2011-04-18
This was a really nice guide!
I've been thinking about getting the asus U36 myself, and this thread made it even more interesting, as hardware support is always difficult and it seemed quite alright on the U36 (except for optimus that is...) 
I just have some questions i hope someone can answer.
Does HDMI work? (I saw someone else ask this without an answer)
Will the nvidia card work properly in windows after disabling it in linux? (I may have to dual boot)

Thanks in advance, or3x

---

### Post by duende_2 on 2011-04-19
or3x, I have my asus u36jc set to dual boot. Nvidia card seems to be working fine in windows after calling optimusoff start service in linux. 
I don't know about  HDMI in linux, I haven't tried it.

I wonder if anyone tried using  vga_switcheroo methods from linux hybrid graphics. They do mention nvidia cards there, but all the examples I have seen seem to be for ATI.

---

### Post by metasequoia on 2011-04-19
I've tried the hdmi once and it doesn't worked for me. I've tried first with my monitor plugged before booting and hot plug. What happend is that the screen deliver a blank screen, but receive a signal because the monitor recognized somehow that it was connected to something. Of course the nvidia card was turned off with acpi_call.

I would also like to know if someone else have actually tried the hdmi port and got the same result.

Sorry for my english.

---

### Post by metasequoia on 2011-04-19
Sorry but my reply is in the wrong thread because i'm still on maverick actually.

---

### Post by Trevice on 2011-04-19
[http://linux-hybrid-graphics.blogspot.com/2011/04/new-asus-switcheroo-module.html](http://linux-hybrid-graphics.blogspot.com/2011/04/new-asus-switcheroo-module.html)

!!

does anyone try it??

It seems there's hope ^^

---

### Post by or3x on 2011-04-20
duende_2 and metasequoia, thank you for taking the time the test and reply, I appreciate it:)
Hopefully there'll be a solution for HDMI soon, and even if not, i might get this laptop anyway:P It just looks so awesome!

---

### Post by ciruman on 2011-04-29
Hi all, first of all thank you very much! It's a very good how-to. But I would like to know I there is another one with my problem. I installed Ubuntu 11.04(final) and sometimes I got black screens, now for example I can't even start the user session.

I don't know if applications like powertop or grano.la are the problem, it's a new laptop, with a ubuntu installation from scratch with just your instructions and the two applications above.

Is it common? 

When I start Win7 it works perfect, so it seems that is not a hardware failure. I don't use M$(I don't like it and it doesn't offer all I need) so using win is not an option to me.

Is there any difference between these instructions and the final release instructions?

Any suggestion.

Thank you in advance!! :D

---

### Post by zynex on 2011-04-29
I have the same problem with 11.04 final. It hangs lots of times when trying to login, not sure why yet. Sometimes everything freezes, and sometime it just stops after the "hard drive icon" fades in. But mouse still works. This was not an issue with the beta release.

---

### Post by ciruman on 2011-05-02
Hi, last Friday I reinstall all and I applied all modifications except optimus tip. I didn't install powertop and grano.la neither. Today I will install powertop and grano.la in order to reduce the energy consumption. I would like to know the origin of the problems.

---

### Post by ciruman on 2011-05-03
I've been using both apps without errors. As soon as I have 1 hour left I will apply the optimus patch and I will see. Is there anyone else with problems? Just 2 victims? :) Hopefully I won't fail again.

---

### Post by metasequoia on 2011-05-05
With my fresh install of Ubuntu 11.04 Stable, I never experienced any hanging, the system is stable. 
I've done everything that is on the first post. I'm using acpi_call to switch off the discrete graphic card at startup.
What is still not working on Natty compared to Maverick : HDMI port (it might be solved by using one of the untested solutions mentionned below)
But what isn't working for me is the USB 3.0 port (it doesn't recognize any usb 2.0 or 3.0 device plugged in) which was working with Maverick.

Is there anyone who have tried the asus-switcheroo module from Alex Williamson to shut down the nvidia (and even use the nvidia) or the Virtual GL trick from Martin Juhl (see Linux Hybrid Graphics site and  [http://www.martin-juhl.dk/2011/05/optimus-on-linux-problem-solved/](http://www.martin-juhl.dk/2011/05/optimus-on-linux-problem-solved/) ) with the Asus U36JC on Natty.
Please report your experiment here in order to improve the installation documentation.

Thanks.

PS : According to my test the title of the tutorial should be changed because the configuration is know valuable for the stable release.

---

### Post by chaltain on 2011-05-05
I'm running Maverick, and I followed the instructions at [https://help.ubuntu.com/community/Asus_U36JC](https://help.ubuntu.com/community/Asus_U36JC). They seemed to cover the same points, but there were no instructions to turn off the NVidia GPU to save power. Do I still need to do that on Maverick? Would the instructions for Maverick be the same as what I see above for Natty?

---

### Post by slipper on 2011-05-09
Hello everyone!
I am trying to make my way through the Ubuntu world, and just bought this wonderful new laptop (U36JC)
I have installed Ubuntu 11.04 and would really like to follow these procedures in order to gain a little bit of battery capacity...
I have a problem though: I can't get further this step:
```
cd acpi_call/ 
make
```because my terminal at this point returns this error:

```
make -C /lib/modules/2.6.38-8-generic-pae/build M=/home/chiara/.optimus/acpi_call modules
make: *** /lib/modules/2.6.38-8-generic-pae/build: File o directory non esistente.  Arresto.
make: *** [default] Errore 2

```what have I done wrong? :)

I'm sorry for the silly question, but I am really a novice to linux code and when I follow code instructions for linux I have no clue of what these commands are doing...

---

### Post by sokola on 2011-05-13
Hi everyone.

after a disastrous attempt to upgrade from Ubuntu 10.10 I made a fresh install of Ubuntu 11.04, and for the most part, with the above tweaks it seems to be working just fine.

However, upon inserting any Usb device in the Usb 3.0 port the device is not recognized: it still receives power from the computer, but a HDD or Usb stick is not mounted, or a printer is not recognized.

With the previous version of the Kernel it was worse, as the kernel was panicking upon insertion of a device in the port (see [https://bugs.launchpad.net/ubuntu/+source/linux/+bug/757242](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/757242)), so I suspect they might have simply disabled the feature in the current version of the kernel..

Did anyone get the Usb 3.0 port working with the final release of Ubuntu 11.04?

---

### Post by Trevice on 2011-05-13
Hi everyone!

I've tested both optimus solutions in my u36jc, asus-switcheroo and bumblebee (this one basicaly use vglclient to send the nvida's images to the intel card). I can't get the first one working, the sreen freezes whenever I switch to the nvidia (but at least I could use the HDMI with nouveau!). The second one works! It's very easy to install, but you lose some performance. I suppose because the intel card creates a bottleneck at render the nvidia's images, you can test it here:

[https://github.com/MrMEEE/bumblebee](https://github.com/MrMEEE/bumblebee)


also, I recompiled a vanillas kernel, in order to can use the usb3 and optimice performance. If you wanna, you can download the 64bits .deb file here:

[http://www.megaupload.com/?d=YHZPH7OD](http://www.megaupload.com/?d=YHZPH7OD)

---

### Post by metasequoia on 2011-05-14
> also, I recompiled a vanillas kernel, in order to can use the usb3 and  optimice performance. If you wanna, you can download the 64bits .deb  file here:

[http://www.megaupload.com/?d=YHZPH7OD](http://www.megaupload.com/?d=YHZPH7OD)Hi everyone,

Trevice can you please explain us what configuration you've used for your recompiled kernel in order to get usb3 working.
What perfomance optimization have you done ?
It might be nice if you explain how you get it working in order to improve the documentation about this laptop configuration. The usb 3 bug is a hard regression for me and other I think. 
Thank you.

---

### Post by AureiAnimus on 2011-05-15
Thanks a lot. I managed to turn off my Nvidia card on my Asus K53SV, however now my fan keeps spinning at full speed. For some reason i can't enable vga_switcheroo, so athe solution on the ubuntu help page (Hybrid grapics) doesn't work. Any pointers?

---

### Post by Trevice on 2011-05-15
I just left the modules for the asus hardware, removing everything else. As you can see, this kernel is much smaller than the ubuntu's default.

Almost all remaining modules are built inside the kernel, not as a module, so the system boot faster. Only for be compiled in the host machine you get better performance, thats why gentoo people is so interested in compile everything by themselft 

Finaly, as it been compiled in the u36 ussing version 4.6 of gcc in order to use the parameters "-march=corei7 -mtune=corei7" 

to get the usb3 work I just enable that module (xhci), and it works. I tested with a usb3 hdd

I compiled a new version, the 2.6.38.6 one:

[http://www.megaupload.com/?d=Z9YGDRHC](http://www.megaupload.com/?d=Z9YGDRHC)

if you would have any bug just tell me!

---

### Post by DeeKey on 2011-05-15
> **Trevice said:**
> 
if you would have any bug just tell me!

Thanks for your work. The deb file has also kernel configs. Could be useful for these who wants to compile Kernel specifically for their hardware.

I tried the kernel myself, but got problems as I have non standard hardware:
SSD disk Vertex 2 and operation system: brtfs and fat32.

Haven't looked at config file yet, but suppose that support for brtfs is turned off? Or maybe support for SSD is not included?

Although it was not possible to load graphical desctop, my SSD with BRTFS was still mounted. 

Trevice, maybe you have a quick solution?

BTW: with SSD ASUS u36Jc is like a rocket! :)
Here is my personal site where I note configuration steps for myself. Feel free to reuse:
[https://sites.google.com/site/asusu36jc](https://sites.google.com/site/asusu36jc)

---

### Post by sokola on 2011-05-15
Trevice, thank you very much for your work. I installed your kernel, and it seems to be running very smoothly. I can confirm that the USB 3.0 port now works.

P.s. Hopefully it will work out with the SSD drive, I am thinking of getting one myself..

---

### Post by Trevice on 2011-05-15
the kernel will work with a ssd, at least in my case I change the hdd for a intel's x25m sdd, and it's one of the better desitions I've never made ^^

Deekey, it has also support for btrfs and fat32 filesystems, so  it should be other thing...can you send us your dmesg for debugging?

---

### Post by LarsEriksson on 2011-05-16
The stupid nVidia Optimus has forced me to run Windows on my u36jc, since i need to use both the VGA and HDMI-ports (2 external monitors).

The new bumblebee sounds promising though.

Is there anyone who has got both the VGA and HDMI-ports to work under Ubuntu yet?

---

### Post by DeeKey on 2011-05-16
> **Trevice said:**
> the kernel will work with a ssd, at least in my case I change the hdd for a intel's x25m sdd, and it's one of the better desitions I've never made ^^

Deekey, it has also support for btrfs and fat32 filesystems, so  it should be other thing...can you send us your dmesg for debugging?

Trevice, I have attached archive with to text files: dmesg for the Ubuntu generic x64 kernel (dmesg_generic.txt) 2.6.38-8-generic

and the other vanilla-kernel.txt is the dmesg from the kernel you provided.

I also use tmpfs and aufs to prolong the life of my SSD.

All optimizations are described here [https://sites.google.com/site/asusu36jc/](https://sites.google.com/site/asusu36jc/)

---

### Post by Trevice on 2011-05-16
using asus-switcheroo I could use the hdmi with the nouveau driver... but the price was high: I loosed the main screen xD

The optimus support is progresing in several directions, I'm following close (I wanna play my starcraft 2 as well as in windows!) but still needs time

---

### Post by DeeKey on 2011-05-18
Trevice, I also noticed, that my home folder is almost empty when I load your kernel. This could be due to the fact, that I checked "encrypt my home folder" during installation of Ubuntu. Maybe the kernel you provided lacks encryption modules...

---

### Post by DeeKey on 2011-05-18
> **Trevice said:**
> using asus-switcheroo I could use the hdmi with the nouveau driver... but the price was high: I loosed the main screen xD


I briefly looked inside the code and noticed this:

[https://github.com/awilliam/asus-switcheroo/commit/ea2fd38a942958cfc29894816f6a1392680e8826](https://github.com/awilliam/asus-switcheroo/commit/ea2fd38a942958cfc29894816f6a1392680e8826)

As stated in the comment:

Currently only supports "AsusUL30VT".  Also add a mdelay special
command to allow configurable delays after powering on the device.

If someone could provide the information as for AsusUL30VT the problem with blank screen could be solved...

---

### Post by sokola on 2011-05-18
Unfortunately I had to dispose of the customized kernel provided by Trevice. I am using Virtualbox, and DKMS did not find the kernel headers of his recompiled kernel (the folder structure seems to be different from the standard one); as a consequence, I could not run Virtualbox, an absolute criticity for me.

Any chance of fixing the Usb 3.0 issue while keeping the original distro's kernel?

---

### Post by Trevice on 2011-05-18
DeeKey, tomorrow I will work in the kernel to make it work with an encrypt home folder and ssd's optimitations you made

Also, I'm sending reports to Alex Willian (asus-switcheroo's developer), to the best of my acpi's knowledge. The main problem is in order to make optimus work with his module reverse engineering is needed... 

sokola,from tomorrow I will upload the headers, not only the image ;)

---

### Post by DeeKey on 2011-05-19
> **sokola said:**
> 
Any chance of fixing the Usb 3.0 issue while keeping the original distro's kernel?

I've fixed USB 3.0 (Fresco Logic FL1000G) adding this parameters to kernel in the grub menu:

Code:

sudo gedit /etc/default/grub

Add the parameter 
pci=nomsi,noaer

to the line GRUB_CMDLINE_LINUX_DEFAULT

sudo update-grub 
and reboot

I have found the solution in these posts:
[http://ubuntuforums.org/showthread.php?p=10832032](http://ubuntuforums.org/showthread.php?p=10832032)
[http://ubuntuforums.org/showpost.php?p=10831338&postcount=15](http://ubuntuforums.org/showpost.php?p=10831338&postcount=15)

---

### Post by ciruman on 2011-05-19
Since I installed the new ubuntu from scratch I applied all patch and everything works perfect, thanks all!

Just optimus(NVidia) and USB 3.0 left :)

---

### Post by DeeKey on 2011-05-19
> **Trevice said:**
> 
Also, I'm sending reports to Alex Willian (asus-switcheroo's developer), to the best of my acpi's knowledge. The main problem is in order to make optimus work with his module reverse engineering is needed... 

That's very nice! DVI is of extreme importance for every user, as without it is not possible to use this noutbook for watching HD movies on the big screen!

---

### Post by Trevice on 2011-05-19
New Kernel: 2.6.39

after some work no south be able to mount a crypt partition as the generic one.
I also upload the headers ;)

[http://www.megaupload.com/?d=GPK01AAX](http://www.megaupload.com/?d=GPK01AAX)

enjoy!

---

### Post by sokola on 2011-05-19
> **DeeKey said:**
> I've fixed USB 3.0 (Fresco Logic FL1000G) adding this parameters to kernel in the grub menu:

Code:

sudo gedit /etc/default/grub

Add the parameter 
pci=nomsi,noaer

to the line GRUB_CMDLINE_LINUX_DEFAULT

sudo update-grub 
and reboot

I have found the solution in these posts:
[http://ubuntuforums.org/showthread.php?p=10832032](http://ubuntuforums.org/showthread.php?p=10832032)
[http://ubuntuforums.org/showpost.php?p=10831338&postcount=15](http://ubuntuforums.org/showpost.php?p=10831338&postcount=15)

Thank you very much DeeKey, that worked like a charm.

Also, thanx once more to Trevice, once I've got a second, I will try the new Kernel, as it indeed appear to load much faster..

---

### Post by DeeKey on 2011-05-21
> **Trevice said:**
> New Kernel: 2.6.39

after some work no south be able to mount a crypt partition as the generic one.
I also upload the headers ;)

[http://www.megaupload.com/?d=GPK01AAX](http://www.megaupload.com/?d=GPK01AAX)

enjoy!

Crypted folder works, but AUFS I use fot SSD optimisation, still doesn't work... 
USB3 works.

---

### Post by DeeKey on 2011-05-22
> **Trevice said:**
> 
Also, I'm sending reports to Alex Willian (asus-switcheroo's developer), to the best of my acpi's knowledge. The main problem is in order to make optimus work with his module reverse engineering is needed... 


Is there any progress? Can other users help in this case?

---

### Post by lonefoxking on 2011-05-22
Hello...

first of all thank you for your effort, its really amazing what u did.

The thing is I followed on step by step on disabling the nVidia, but now when I load kubuntu i get the main screen loading then after a while _before the login page shows up, the screen turns black_ and there is nothing i can do, I logged to fail safe, tried to revert the settings by deleting all the files i created and re-editing the files, but nothing... i still get this black screen.

How can I revert or fix this?? can you please help? :confused:

cheers

---

### Post by Trevice on 2011-05-23
in order to turn off the nvidia...did you use acpi_call, asus-switcheroo or bumbleble?

make sure you are not using two methods at the same time, and if you arent using bumblebe the nvidia driver is not instaled

---

### Post by lonefoxking on 2011-05-24
Help...

I tried deleting xconf - didint work

apt-get remove nvidia-current
apt-get install nvidia-current - didnt work

I even reinstalled xserver and xorg.. .but nothing

I only get kubuntu loading then a black screen

---

### Post by DeeKey on 2011-05-28
> **Trevice said:**
> in order to turn off the nvidia...did you use acpi_call, asus-switcheroo or bumbleble?

make sure you are not using two methods at the same time, and if you arent using bumblebe the nvidia driver is not instaled

As far as I understand everything good is merging with bumblebee.
( [http://linux-hybrid-graphics.blogspot.com/2011/05/more-bumblebee-updates-automatic.html](http://linux-hybrid-graphics.blogspot.com/2011/05/more-bumblebee-updates-automatic.html) )
I have submitted the issue:
[https://github.com/MrMEEE/bumblebee/issues/175](https://github.com/MrMEEE/bumblebee/issues/175)

There is a merge request which will add asus-switcheroo to bumblebee. It is still under way. Tried it myself, but it does not work yet.

Need correct acpi_call parameter. Provided one does not work for me:
echo _PS0 $(acpi_call "_SB.PCI0.PEG1.GFX0.DOFF")

Error: AE_BAD_PARAMETER

Maybe someone knows the correct sequence?

---

### Post by DeeKey on 2011-05-30
Disabling and enabling nVidia card works!
One needs only bumblebee both for using optimus and turning off/on nVidia.
asus-switcheroo was merged with bumblebee recently.

There are still some bugs in installation script, but most impatient can use it right away. Here is the instruction:

To use it copy sources from here:
[https://github.com/MrMEEE/bumblebee](https://github.com/MrMEEE/bumblebee)

tar xvf the sources
go to the folder and run ./install.sh
after installation copy some scripts

sudo cp ./install-files/bumblebee-enablecard.K42Jc.K52Jc.N53Jf.N53Jg.N71JV.N73JF.P52JC.U30JC.U33JC.U35JC.U36JC /usr/local/bin/bumblebee-enablecard

sudo cp ./install-files/bumblebee-disablecard.K42Jc.K52Jc.N53Jf.N53Jg.N71JV.N73JF.P52JC.U30JC.U33JC.U35JC.U36JC /usr/local/bin/bumblebee-disablecard


sudo chmod +x /usr/local/bin/bumblebee-enablecard 
sudo chmod +x /usr/local/bin/bumblebee-disablecard


To test run:
sudo bumblebee-disablecard
grep rate /proc/acpi/battery/BAT0/state
sudo bumblebee-enablecard
grep rate /proc/acpi/battery/BAT0/state
sudo bumblebee-disablecard

Rate values should be less after disabling nVidia.

---

### Post by DeeKey on 2011-05-31
Bumbleebee is working for me:
- it is possible to turn on/off nVidia card (OFF by default)
- it is possible to use nVidia for running apps (tested only on glxgears)

Propose to test and if successful edit the 1-st page guide section

Disable NVidia GPU/NVidia Optimus  with something like this:
> 
To install the support form Optimus follow the procedure:
1) download source codes of bumblebee from here
2) unpack the tarball and cd to the unpacked folder
3) run
sudo install.sh

NB! As acpi-call and asus-switcheroo are merged to the code of bumblebee one doe's not need them.
If mentioned programs were installed previously uninstall them.

---

### Post by Menthu_Rae on 2011-06-01
> **DeeKey said:**
> Bumbleebee is working for me:
- it is possible to turn on/off nVidia card (OFF by default)
- it is possible to use nVidia for running apps (tested only on glxgears)

Propose to test and if successful edit the 1-st page guide section

Disable NVidia GPU/NVidia Optimus  with something like this:

I don't really want to run bumblebee/etc on my laptop just yet - if someone is willing to write up some more detailed instructions in the format of my first post - I will happily merge them :)

---

### Post by or3x on 2011-06-02
It's really great to see how the support for optimus has developed over the last months, I think it's an awesome example of the power of open source and hard working developers. Thank You!:D
I'm almost certain I'm getting this laptop now, i just wanna know one thing;
Is the HDMI working properly with bumblebee?

Thanks, or3x

---

### Post by sarahsharp on 2011-06-02
> **Menthu_Rae said:**
> 
Let's fix some issues with the USB buses and also the NVidia/Intel GPUs when undertaking suspend/resume operations.

```

    # Switch USB 3.0 buses off
    for bus in $BUSES3; do
        echo -n $bus | tee /sys/bus/pci/drivers/xhci_hcd/unbind
    done

```[SIZE=3]_* Fix USB3.0 Port_[/SIZE] (thanks to DeeKey)

To fix the USB 3.0 (Fresco Logic FL1000G) port, we need to update the parameters when launching Ubuntu via GRUB.

```
pci=nomsi,noaer
```

Why are you unbinding the xHCI driver on suspend?  Does the Fresco Logic host controller not support suspend?  It should.

I'm the USB 3.0 kernel maintainer, and I'd like to help get out-of-the-box support in Natty for your host controller.  Can you please contact the Linux USB mailing list <linux-usb@vger.kernel.org> and cc me (Sarah Sharp <sarah.a.sharp@linux.intel.com>) when you have issues with USB?  That way we can fix your problems rather than you having to work around them. :)

I'm looking for someone to test the following patch against the stock Ubuntu 11.04 kernel, *without* adding the pci=nomsi to their boot parameters:

[http://marc.info/?l=linux-usb&m=130704257816957&w=2](http://marc.info/?l=linux-usb&m=130704257816957&w=2)

That should make it so you don't need to boot with the pci=nomsi parameter.  I don't know if that will help with any suspend issues you are experiencing.

---

### Post by phibuntu on 2011-06-10
Same problem here? USB 3.0 worked on 10.10, but does no longer on 11.04:

[http://ubuntuforums.org/showthread.php?t=1776361&highlight=usb+3+11.04](http://ubuntuforums.org/showthread.php?t=1776361&highlight=usb+3+11.04)

---

### Post by Kettarie on 2011-06-12
Hi all,

thank you for very useful information I will (I hope :) need in some time. But my first problem is, that I still can not install Ubuntu 11.04 on my U36JS! 

I'm trying to use a 8 GB USB stick, made in Unetbootin. It shows me the grub suggesting to install Ubuntu or run it without installation, but I can do neither - I get the blank black screen hanging and hanging and hanging, and nothing more...
Probably it is not possible to use a stick? Or the problem is caused by NVIDIA Optima?

I am very new in Linux, and I would appreciate your help very much... Thank you in advance and excuse me for a silly question.

---

### Post by BlueCase on 2011-06-14
For the USB3/MSI topic I created a bugreport in launchpad.
[https://bugs.launchpad.net/ubuntu/+source/linux/+bug/797455](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/797455)

---

### Post by pulz on 2011-06-16
anyone managed to get VAAPI working 100% on this laptop ?

---

### Post by havier on 2011-06-23
thank you Menthu_Rae!! what an incredible and helpful tutorial are you giving us!:D
I was very sad with my new Asus U36JC and Ubuntu 11.04, thought I'll never be using it with so many hardware drawbacks. Now it works almost like a charm (just waiting for a nvidia optimus workaround);)

---

### Post by lotusflyer on 2011-06-23
A big huge thanks for this. Everything is working the way I would like now. And I have a happy, happy laptop.

---

### Post by Menthu_Rae on 2011-07-02
I think for any future updates, they should be added to the Wiki/Community Help page for the U36Jc:

[https://help.ubuntu.com/community/Asus_U36JC](https://help.ubuntu.com/community/Asus_U36JC)

If I get some time over the next few days I'll see if I can update the page with the info from this guide and others can add to it with their experiences/expertise (looking at sarahsharp from Intel here! :P )

> **sarahsharp said:**
> Why are you unbinding the xHCI driver on suspend?  Does the Fresco Logic host controller not support suspend?  It should.

Am I allowed to say I'm not sure why? As mentioned in the initial post- the guide was hobbled together from other guides to make something that works for the U36Jc and Ubuntu 11.04.

I only have what I would consider a relatively basic understanding of Linux, but I do have a determination to make things work!

Back when I wrote the original post - I think I was one of the first people to have nearly everything up and running in Ubuntu 11.04 on the U36Jc, or at least one of the first to write about it.

If anyone thinks anything I'm doing isn't the best way or isn't right - I'm extremely happy to learn why and would appreciate the input! :)

> **sarahsharp said:**
> I'm the USB 3.0 kernel maintainer, and I'd like to help get out-of-the-box support in Natty for your host controller.  Can you please contact the Linux USB mailing list <linux-usb@vger.kernel.org> and cc me (Sarah Sharp <sarah.a.sharp@linux.intel.com>) when you have issues with USB?  That way we can fix your problems rather than you having to work around them. :)

Good to know someone with your skills and expertise is on the case/job - but is this the best way to get things done? I think most users on here would report the bug on launchpad... I don't know about other users on here but for me, mailing lists seem quite inefficient as a method for solving bugs? Maybe I just think this because I don't use them at all...

But yeah... what in your opinion is the best procedure to follow to ensure that as Ubuntu end-users our USB bugs get solved? :confused:

> **sarahsharp said:**
> I'm looking for someone to test the following patch against the stock Ubuntu 11.04 kernel, *without* adding the pci=nomsi to their boot parameters:

[http://marc.info/?l=linux-usb&m=130704257816957&w=2](http://marc.info/?l=linux-usb&m=130704257816957&w=2)

That should make it so you don't need to boot with the pci=nomsi parameter.  I don't know if that will help with any suspend issues you are experiencing.

What's involved with testing the patch? :confused:

---

### Post by uKev on 2011-07-11
Hello there,

thanks for the work done already!

Does the vga port work with the intel card and nvidia disabled?

If yes, does it work to enable vga without restarting x?

---

### Post by Lima November on 2011-07-21
> **lonefoxking said:**
> Hello...

first of all thank you for your effort, its really amazing what u did.

The thing is I followed on step by step on disabling the nVidia, but now when I load kubuntu i get the main screen loading then after a while _before the login page shows up, the screen turns black_ and there is nothing i can do, I logged to fail safe, tried to revert the settings by deleting all the files i created and re-editing the files, but nothing... i still get this black screen.

How can I revert or fix this?? can you please help? :confused:

cheers

I've had a similar problem. During booting, the screen_ always_ goes black and sometimes, the booting just stops. 

The problem comes from the late boot splash, as explained in the U36 setup guide ([]("https://help.ubuntu.com/community/Asus_U36JC")[https://help.ubuntu.com/community/Asus_U36JC](https://help.ubuntu.com/community/Asus_U36JC)), combined with Ubuntu's disk checking routine during booting. If a hard disk error is detected, Ubuntu shows a message asking the user what it should do (check disk, proceed, ...). However, if the boot splash is too late, this message is not shown, instead the screen remains black. However, Ubuntu is still waiting for the answer... Thus, nothing happens.

The solution is to perform the boot splash correction from the setup guide:

> 
**Boot splash**

 As usual  with Intel cards, Plymouth boot splash will show too late in the boot  process. If you want it to appear earlier, type this in a console  window: 

[I]sudo echo FRAMEBUFFER=y > /etc/initramfs-tools/conf.d/splash
sudo update-initramfs -u
[/I] 
You might get a little bit slower boot, but it will look much consistent (IMHO). 

---

### Post by triphamk2 on 2011-08-05
hi, I followed all of these instruction to tune up my U36JC's battery usage but when I restarted the laptop, Ubuntu screen turned black. Do you have any idea how to fix it? Thank you. Anyway, I install the stable 11.04.

---

### Post by chaltain on 2011-08-22
Everything went fine until I got to the command "sudo apt-get install gtk-v4l". When I run this command, I get the message "Unable to locate package gtk-v4l". Note that I added the repository OK and that I was able to install libv4l-0.

---

### Post by richard.annand on 2011-09-13
Thanks for this guide its made such a difference to my laptop :) just wondering how on earth I can get compiz to work. I dont have the option under appearance like I normally would.

Thanks in advance.

---

### Post by foxy123 on 2011-10-30
I wonder if this guide is relevant for 11.10 64-bit? I tried this one yesterday [https://help.ubuntu.com/community/Asus_U36JC](https://help.ubuntu.com/community/Asus_U36JC), but after following the instructions for  disabling nvidia my laptop started freezing on boot.

---

### Post by bud986 on 2011-11-05
Its better to install bumblebee than disabling the nvidia card :)

---

### Post by trinux_bc on 2012-01-03
Any updates for 11.10 64-bit on the U36JC? Thanks.

trinux_bc

---

### Post by bodymind on 2012-01-23
can u guys check if the nvidia works using this guide:

[http://askubuntu.com/questions/67808/getting-gnome-shell-working-on-nvidia-optimus-notebook/95432#95432](http://askubuntu.com/questions/67808/getting-gnome-shell-working-on-nvidia-optimus-notebook/95432#95432)

It's for an Asus X35S - nvidia GT 520M!

thanks! :popcorn:


P.S. - I'd like to known why u say "[IMPORTANT: DO NOT INSTALL NVIDA RESTRICTED DRIVERS] ", for me it works very nice the bumblebee!

---

### Post by EXYZ1000 on 2012-03-10
Hello,
Asus U36jc + Ubuntu 11.10. 
My major issue so far is the (suspend / Hibernate) -  whenever I select  either one, the screen only locks.. ,  the computer  keeps on running and the disk and fan are working. so i  guess my  question is - Is their a full sleep mode or suspend? 
i looked around and found the fix here [http://ubuntuforums.org/showthread.php?t=1705406](http://ubuntuforums.org/showthread.php?t=1705406)
but that still not working for me.

Let me know if you faced similar issues and if the is a fix..

THANK YOU.
 		                   		  		  		  		  		  	   	 		 [IMG]http://ubuntuforums.org/images/statusicon/user_online.gif[/IMG]  		 		 		[[IMG]http://ubuntuforums.org/images/buttons/report.gif[/IMG]]("http://ubuntuforums.org/report.php?p=11753440") 		 		  	 	 	 	 		  		 			 			[[IMG]http://ubuntuforums.org/images/buttons/edit.gif[/IMG]]("http://ubuntuforums.org/editpost.php?do=editpost&p=11753440")

---

### Post by 23dornot23d on 2012-03-10
I had similar graphics problems .... my card was the Nvidia 540 with Intel Graphics.

mine is a .... ASUS .... K53SV though ....

( Hybrid Graphics are not as easy to set up because they switch between  the two inbuilt graphics cards to save power apparently )

I solved the problem that I had, with this newer system using the [[COLOR=Blue]_**Ironhide driver**_[/COLOR]]("http://www.martin-juhl.dk/2011/10/moving-to-oneironhide/") .....

The solution is documented in this thread ..... it worked for me ...... and a few others too.

[COLOR=Blue][U][B][http://ubuntuforums.org/showthread.php?t=1871226&page=3](http://ubuntuforums.org/showthread.php?t=1871226&page=3)

[/B][/U][/COLOR]> 

keith@keith-K53SV:~$ lspci
00:00.0 Host bridge: Intel Corporation 2nd Generation Core Processor Family DRAM Controller (rev 09)
00:01.0 PCI bridge: Intel Corporation 2nd Generation Core Processor Family PCI Express Root Port (rev 09)
00:02.0 VGA compatible controller: Intel Corporation 2nd Generation Core Processor Family Integrated Graphics Controller (rev 09)
00:16.0 Communication controller: Intel Corporation 6 Series Chipset Family MEI Controller #1 (rev 04)
00:1a.0 USB Controller: Intel Corporation 6 Series Chipset Family USB Enhanced Host Controller #2 (rev 05)
00:1b.0 Audio device: Intel Corporation 6 Series Chipset Family High Definition Audio Controller (rev 05)
00:1c.0 PCI bridge: Intel Corporation 6 Series Chipset Family PCI Express Root Port 1 (rev b5)
00:1c.1 PCI bridge: Intel Corporation 6 Series Chipset Family PCI Express Root Port 2 (rev b5)
00:1c.5 PCI bridge: Intel Corporation 6 Series Chipset Family PCI Express Root Port 6 (rev b5)
00:1d.0 USB Controller: Intel Corporation 6 Series Chipset Family USB Enhanced Host Controller #1 (rev 05)
00:1f.0 ISA bridge: Intel Corporation HM65 Express Chipset Family LPC Controller (rev 05)
00:1f.2 SATA controller: Intel Corporation 6 Series Chipset Family 6 port SATA AHCI Controller (rev 05)
00:1f.3 SMBus: Intel Corporation 6 Series Chipset Family SMBus Controller (rev 05)
01:00.0 VGA compatible controller: nVidia Corporation Device 0df4 (rev ff)
03:00.0 Network controller: Atheros Communications Inc. AR9285 Wireless Network Adapter (PCI-Express) (rev 01)
04:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL8111/8168B PCI Express Gigabit Ethernet controller (rev 06)
keith@keith-K53SV:~$ date && lsb_release -sd || cat /etc/*release && uname -s -r && unity --version && /usr/lib/nux/unity_support_test -p && dpkg -s mesa-utils
Sat Mar 10 10:16:02 CET 2012
Ubuntu 11.04
Linux 2.6.38-13-generic
unity 3.8.16
OpenGL vendor string:   Tungsten Graphics, Inc
OpenGL renderer string: Mesa DRI Intel(R) Sandybridge Mobile 
OpenGL version string:  3.0 Mesa 8.0-devel

Not software rendered:    yes
Not blacklisted:          yes
GLX fbconfig:             yes
GLX texture from pixmap:  yes
GL npot or rect textures: yes
GL vertex program:        yes
GL fragment program:      yes
GL vertex buffer object:  yes
GL framebuffer object:    yes
GL version is 1.4+:       yes

Unity supported:          yes
Package: mesa-utils
Status: install ok installed
Priority: optional
Section: x11
Installed-Size: 148
Maintainer: Ubuntu X-SWAT <ubuntu-x@lists.ubuntu.com>
Architecture: amd64
Source: mesa-demos
Version: 8.0.1+git20110129+d8f7d6b-0ubuntu2
Replaces: xbase-clients (<< 6.8.2-38)
Depends: libc6 (>= 2.4), libgl1-mesa-glx | libgl1, libx11-6
Description: Miscellaneous Mesa GL utilities
 This package provides several basic GL utilities built by Mesa, including
 glxinfo and glxgears.
Homepage: [http://mesa3d.sourceforge.net/](http://mesa3d.sourceforge.net/)
keith@keith-K53SV:~$ 



---

### Post by EXYZ1000 on 2012-03-12
Any one was able to solve the Suspend/Hypernate issue.
I have to shut down Asus u36JC Ubuntu 11.10 every time I don't need to use the computer.

---

### Post by larsemil on 2012-04-03
Same issue here. Anyone solved suspend on 11.10?

---

### Post by zynex on 2012-05-13
Found a working solution for suspend (12.04), posted it here; [http://ubuntuforums.org/showthread.php?t=1979490](http://ubuntuforums.org/showthread.php?t=1979490)

Try this for 11.10, should work there to I think? :)

---

### Post by Metalheadbanger on 2012-08-12
Are there any updates for Asus U36JC running Ubuntu 12.04?

Reagards.

---

### Post by jbarr on 2012-08-20
Thanks for your guide. However, now I have two new problems. 

1. My fan goes to high speed upon resume. 
2. Without attempting suspend, the mouse and keyboard will freeze (rendering the computer unusable). Often this does not happen for 30 minutes, but it is quite frustrating. The only solution is to do a hard reboot.

Any ideas?

Jon

---

### Post by Metalheadbanger on 2012-08-21
hello jbarr,

Could you please state your ubuntu installation scenario? This happened on newly installed ubuntu or after installation of new hardware or software?

Regards.

---

