---
title: "kubuntu hardy on hp compaq 6720s - a few problems"
date: 2008-10-19
forum: Hardware
---

### Post by francisc1701 on 2008-10-19
Hi everyone!

I recently installed Kubuntu Hardy (8.04) on my HP Compaq 6720s (see my signature). Almost everything works fine out of the box. These are the things which don't work properly or at least not as I expect them to work:

1. When I close the lid the system freezes. The only thing I can do is to press and hold the power button until it shuts down completely.

I googled a bit and found that I should "echo 1 > /proc/acpi/video/*/DOS". It works, that is, the system no longer freezes when I close the lid, but it doesn't do anything else either - the "When Laptop lid closed" settings in Power Manager have no effect. (to be honest I only tried Lock screen and Suspend, but Suspend from the Log out screen works so I didn't try the Hibernate nor Shutdown).

2. In Power manager I set the brightness to minimum (0%) both in Mains and Battery powered sections and it works, BUT when I log in (either after logging out or after powering up the system) the screen's brightness is at maximum. In Power manager my settings are still there (0% both). If I use the brightness buttons on the keyboard this is what happens:
   - the button which should get the brightness down does nothing
   - the button which should get the brightness up actually gets it down to 10%. I guess the system thinks the brightness is at 0% when it's really at 100%.

3. My laptop is bluetooth-capable, but I don't use bluetooth. KBluetooth starts automatically every time I log in, even though I repeatedly closed it and told it every time not to start automatically.

I googled this problem and I found that I should edit ~/.kde/share/config/kdebluetoothrc like this: in the [General] section, AutoStart=false; the problem is that it was already false and KBluetooth still starts automatically.

4. Not really an issue, but I'm curious: xorg is using the vesa driver, not the intel one. It's not an issue because the vesa driver works fine (as far as I can tell). I manually chose "Intel 965" in "System Settings" -> "Monitor and display" -> "Hardware" tab -> "Configure" (next to the first item that says "Vesa driver (generic) ). The result (after I rebooted) was that kdm would not appear. I had backed up /etc/X11/xorg.conf before this, so it wasn't hard to restore it. The question is why doesn't the i810 driver work?

Any thoughts about the issues above are most welcome.

This is it for now. I hope my rant is clear enough to understand :)

Thanks in advance.

edit: I have 2 GB ram. Do I need 2 GB swap to successfully hibernate?

---

### Post by pelle.k on 2008-10-19
> In Power manager I set the brightness to minimum (0%) both in Mains and Battery powered sections and it works, BUT when I log in (either after logging out or after powering up the system) the screen's brightness is at maximum.
Just turn off backlight preferences, and/or set the backlight yourself at bootup in /etc/rc.local.
you'll probably find a backlight node somewhere in /proc or /sys.
> My laptop is bluetooth-capable, but I don't use bluetooth. KBluetooth starts automatically every time I log in, even though I repeatedly closed it and told it every time not to start automatically.
**sudo chmod -x /etc/init.d/bluetooth**
and start it yourself when you need it
> I have 2 GB ram. Do I need 2 GB swap to successfully hibernate? 
Not necessarily, but yes, in the worst case scenario it could fail. I use a 3GB swap, 2GB for hibernation, and 1 GB should there be a need for soma actual *swap* to be written as well.

---

### Post by francisc1701 on 2008-10-20
Thanks for the advice, pelle.k

About bluetooth: I read /etc/init.d/bluetooth and I saw the runlevels listed in it (default-start and default-stop). That reminded me about "System services" in "System settings" so I didn't do what you said but instead I set "bluetooth" not to start during boot. It works.

> Just turn off backlight preferences, and/or set the backlight yourself at bootup in /etc/rc.local.

I don't know where/how to turn off backlight preferences. I found xbacklight (again by googling) and it successfully sets the backlight brightness, but I don't know how to have "xbacklight -set 0" executed every time I boot, every time I resume from suspend (to ram and to disk) and after the monitor gets switched off automatically due to inactivity.

Since my first post I found another problem: hibernate doesn't work. When I hibernate, the laptop does power off, but when I turn it back on it starts the way it does after a normal shutdown.
Suspend works, though.

Please help, I use hibernate a lot (when it works, anyway).

edit: i noticed that the backlight brightens up to maximum while/after "Loading hardware drivers" at boot. Maybe someone can use this information somehow.

---

### Post by pelle.k on 2008-10-20
> About bluetooth: I read /etc/init.d/bluetooth and I saw the runlevels listed in it (default-start and default-stop). That reminded me about "System services" in "System settings" so I didn't do what you said but instead I set "bluetooth" not to start during boot. It works.
+1

> I don't know where/how to turn off backlight preferences. I found xbacklight (again by googling) and it successfully sets the backlight brightness, but I don't know how to have "xbacklight -set 0" executed every time I boot, every time I resume from suspend (to ram and to disk) and after the monitor gets switched off automatically due to inactivity.
i would have though you disable backlight preferences in guidance (the power manager, a "flash" icon in your tray).
Either way, put it in /etc/rc.local
Also, i just tried another thing; locate your brightness in /sys (find /sys -iname backlight **or maybe** find /sys -iname brightness)
You should be able to set brightness by passing a integer (a value) like this;
```
sudo -i
echo 5 > /sys/whatever/path/to/backlight
```
now, if you found it, you can lock it by settings
```
sudo chmod 0000 /sys/whatever/path/to/backlight
```
So, if you set brightness, then lock it from /etc/rc.local, you will not have these problems any more. Try it out, will you?


> Since my first post I found another problem: hibernate doesn't work. When I hibernate, the laptop does power off, but when I turn it back on it starts the way it does after a normal shutdown.
Suspend works, though.
It's supposed to run grub, as it would normally, it's when booting up it should find a resume image, and resume the previous session.
Are you sure it doesn't do that?
Look in /var/log/pm-hibernate.log for clues.

> edit: i noticed that the backlight brightens up to maximum while/after "Loading hardware drivers" at boot. Maybe someone can use this information somehow.
Nope, it's supposed to do that when the "video" module is loaded, and when the backlight control is activated. This is an ACPI problem (read - crappy bios/dsdt, most likely), and will probably need some workaround in the kernel/HAL/guidance-power-manager. It'll probably get fixed with time, say maybe in intrepid...

---

### Post by francisc1701 on 2008-10-21
I put "xbacklight -set 0" in /etc/rc.local (before "exit 0;") but it didn't work. So I went looking for that backlight node and found it: /sys/class/backlight/acpi_video0/brightness. I replaced ```
xbacklight -set 0
``` with ```
echo 0 > /sys/class/backlight/acpi_video0/brightness
chmod 0000 /sys/class/backlight/acpi_video0/brightness
``` (as you suggested) and it works. Thank you.

There is a downside to this, though: the brightness buttons on my keyboard no longer have any effect, nor does Power Manager. As you put it, it's locked. Fortunately, this is not a problem for me - I'm perfectly happy with 0% brightness.

> Look in /var/log/pm-hibernate.log for clues. You're wrong about this one :) - it's pm-suspend.log

Since my previous post I've reinstalled Kubuntu, for a reason unrelated to any of the problems I mentioned here. The first time I installed Kubuntu I also installed all 171 updates suggested by Adept Notifier. After I reinstalled Kubuntu I did not install those updates. Now this fresh installation doesn't freeze when I close the lid (instead it does what I choose in Power Manager). It also hibernates, quite fast too. Could it be that the upgrade to kernel 2.6.24-21-generic broke something in my system?

---

### Post by pelle.k on 2008-10-21
Ah, yes, pm-suspend.log it is :)
Sure, the -21 kernel could be the source of the problem you were having. Don't be afraid to install it though, you could just change the "default" kernel to boot in /boot/grub/menu.lst to some other kernel than "0" (the first in the list)

To install the -19 kernel (or whatever number you would like) do;
```
sudo aptitude install linux-{image,restricted-modules,ubuntu-modules}-2.6.24-**19**-386
```
I'm sure it's self explainatory. It installs kernel image, restricted modules/drivers and regualar modules, all in one go. Notice the "19" in this case as well.

If you want to change brigtness without to much hassle, use this script.
```

#! /bin/sh

if [ "$(whoami)" != "root" ]; then
	echo "You need root privilegies to run this script"	
	exit 1
fi

case $1 in
	[0-9])
		chmod 0644 /sys/class/backlight/acpi_video0/brightness
		echo $1 > /sys/class/backlight/acpi_video0/brightness
		chmod 0000 /sys/class/backlight/acpi_video0/brightness
		;;
	*)
		echo "> Usage: backlight [0-9]"
		;;
esac

```
just save it as "backlight".
do "chmod +x backlight"
and "mv backlight /usr/local/bin"

then just run "sudo backlight 5" if you should need to. Yes, i was feeling a bit creative today :)

---

### Post by francisc1701 on 2008-10-22
> To install the -19 kernel (or whatever number you would like) do;
 
```
sudo aptitude install linux-{image,restricted-modules,ubuntu-modules}-2.6.24-19-386
```
It is indeed self-explanatory but I prefer using Adept (I'm too lazy to type when I can help it :) )

Your script will come in handy should I ever want to set the backlight to anything other than 0. Thanks.

---

### Post by VladNistor on 2008-10-22
> 1. When I close the lid the system freezes. The only thing I can do is to press and hold the power button until it shuts down completely.

I googled a bit and found that I should "echo 1 > /proc/acpi/video/*/DOS". It works, that is, the system no longer freezes when I close the lid, but it doesn't do anything else either - the "When Laptop lid closed" settings in Power Manager have no effect. (to be honest I only tried Lock screen and Suspend, but Suspend from the Log out screen works so I didn't try the Hibernate nor Shutdown).

I had the same problem in Ubuntu 8.04 with that laptop. The issue has been fixed since i upgraded to Intrepid and now works fine and Power Manager does have an effect on what happens now.

---

### Post by francisc1701 on 2008-10-24
VladNistor: I'm glad it's not a problem in Intrepid. I might upgrade. Thank you.

Off-topic but I think it's worth mentioning: since I installed Kubuntu I have had little or no need to boot windows. Isn't that great? :)

---

### Post by pelle.k on 2008-10-24
> since I installed Kubuntu I have had little or no need to boot windows. Isn't that great? 
Oh, i have fond memories of when i discovered kde (and kubuntu) for the first time. I mean, i had run it before, but with kubuntu (6.4 or something) i fell in love.
Even though i'm a gnome person, i always try out kde distros from time to time. Some of the best apps are KDE apps.

I don't boot windows unless i want to play games. It took some time to get there, but eventually, you'll feel so limited by what you can do in windows.
There's always gonna be things that irritate me in linux as well, but for the most part, i'm a happy camper. The worst thing about linux is really hardware support, and that is really hard to do something about.

Glad things are working out for you :)

---

