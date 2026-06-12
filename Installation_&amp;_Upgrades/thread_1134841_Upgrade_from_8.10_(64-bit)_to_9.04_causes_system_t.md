---
title: "Upgrade from 8.10 (64-bit) to 9.04 causes system to not fully boot"
date: 2009-04-24
forum: Installation &amp; Upgrades
---

### Post by tomdkat on 2009-04-24
So, I upgraded to Ubuntu 9.04 from 8.10 (64-bit) today using the upgrade option in the Synaptic Package Manager.

After a lengthy download, the installation went without a hitch. I rebooted and when the system started booting, it stopped with a screen of colored garbage scattered about. I get the same behavior described [here](http://www.nabble.com/Jaunty-install-problem-td22619452.html).

I've got an ATI Radeon XPRESS 200G (RS480) video adapter in the system and I was NOT using the flgrx driver.  I was using the open source "ati" driver, previously, and from what I can tell now, Xorg wants to use the "radeon" driver.

When the colored garbage appears on the screen, no keystrokes work at all and my only option is to use the power button to reboot the system. I *can* use a "recovery mode" boot option to boot to a root login shell with networking support and I can access the Internet in this fashion.

Any ideas on how I can resolve my video problem?  I'm guessing the X server is crashing or hanging, which is why I'm getting the colored garbage.

I've tried issuing these commands to reset Xorg with no luck:

dpkg-reconfigure -phigh xerver-xorg
aticonfig --initial -f

When I issue the aticonfig command, it reports no supported adapters are detected.

I'm posting this from another machine since my primary machine is having this problem.

Thanks!

EDIT:  I almost forgot to mention, during the boot process, I DO see the Ubunty splash screen with the progress bar.  Then, the display changes from that to the colored garbage.  The screen flashes with the colored garbage a few times and then the colored garbage sticks and the boot process stops.  The colored garbage sort of "feels" like the wrong resolution was selected by the video driver but I don't see where that's set in /etc/X11/xorg.conf.

Peace...

---

### Post by prshah on 2009-04-24
> **tomdkat said:**
> The colored garbage sort of "feels" like the wrong resolution was selected by the video driver but I don't see where that's set in /etc/X11/xorg.conf.


I had the same problem (attaching screenshots for clarification), and it was in fact a resolution issue; Jaunty (beta) did not correctly detect the native resolution of my laptop screen. I set it manually by adding the required lines (in red) to xorg.conf> ```

Section "Screen"
        Identifier      "Default Screen"
        Monitor         "Configured Monitor"
        Device          "Configured Video Device"
[color=red]        DefaultDepth    24
        SubSection      "Display"
                Modes   "1280x768@60"
        EndSubSection[/color]
EndSection

```

You will have to know the native resolution of your laptop screen; don't blindly add these lines.

For me too, the splashscreen display perfectly, but X had a problem.

---

### Post by tomdkat on 2009-04-24
> **prshah said:**
> I had the same problem (attaching screenshots for clarification), and it was in fact a resolution issue; Jaunty (beta) did not correctly detect the native resolution of my laptop screen. I set it manually by adding the required lines (in red) to xorg.conf

You will have to know the native resolution of your laptop screen; don't blindly add these lines.

For me too, the splashscreen display perfectly, but X had a problem.Yep, that's basically what I'm seeing.  Thanks for the info.  The thing is, I tried reverting to a previous xorg.conf file and I tried running "X -configure" to let the X server generate a config file and that didn't work either.

I'll try adding the lines you did and will see what happens.

Thanks!

Peace...

---

### Post by tomdkat on 2009-04-24
Well, unfortunately that didn't help.  :(

I've got another monitor laying around I'll try to see if that will work any better.

If you have any other ideas, I would love to hear them.  :)

Thanks again! :)

Peace...

---

### Post by tomdkat on 2009-04-24
Ok, something is definitely wrong with my Ubuntu upgrade.

I've tried 4 different monitors (2 CRT and 2 LCD) and two different video cards (integrated ATI XPRESS 200 and a PCI card with a GeForce2 MX200 chipset) in different card/monitor combinations and I'm not having any luck at all.

So, is it possible for me to re-install the complete xorg package from the command line?

Thanks!

Peace...

---

### Post by prshah on 2009-04-24
> **tomdkat said:**
> 
If you have any other ideas, I would love to hear them.

a) Boot into Windows if you have it, and note the resolution and the refresh rate; then duplicate those entries into your xorg.conf as shown previously.

b) Switch to using a VESA server, and once you get a display, you can use the GUI tools to enable support for restricted drivers.

```
Section "Device"
        Identifier      "Configured Video Device"
[color=red]        Driver          "vesa"[/color]
EndSection
```

Just a word of advice; without the correct resolution, switching to the vesa driver did not help me at all; I continued to have the same problem.

I do not believe a reinstall of xorg will help in anyway; but if you are determined, maybe this may do the trick```
sudo apt-get install --reinstall xserver-xorg-core
``` but once again, I don't think this will get you anywhere.

My best advice would be to find the correct native resolution of whichever monitor you choose to use, and use that with the vesa driver, and then use the GUI tools to enable (and download) the correct restricted drivers.

---

### Post by fatblueduck on 2009-04-24
I'm having this problem also. I've tried using the vesa driver. I've tried installing the latest ati driver. I've tried setting a modeline in my Xorg.conf

Nothing seems to fix this problem. I've got an ATI Radeon Express 200M.

********************* PROBLEM FIXED

Well, the problem for the 200M is that its no longer supported by ATI :(. The official ATI drivers will not work with this card, either from Ubuntu's repositories or from ATI's download page will. The only option is to do these things: 

1) Completely remove the official drivers.
```
sudo apt-get remove --purge xorg-driver-fglrx
```
if you manually installed the ati drivers outside of apt use the ati un-install script
```
sudo /usr/share/ati/fglrx-uninstall.sh
```
if you created a special xorg.conf file, delete it

2) Reboot

3) Install the open-source radeon drivers.
```
apt-get install xserver-xorg-video-radeon
```

EXTRA NOTES
I pressed 'ESC' during the grub boot process and booted in safe-mode, and when it presented me with options, I chose to be dropped into a terminal as root. You might try this and find that you're not able to use apt because you don't have a wi-fi connection present. Here's what I did to get wifi.

1) type 'iwconfig' to list your wireless devices. Two columns of information will be displayed and the column on the left shows the device. Locate the device that has information available to it in the second column. The device will have a name like, 'ra0', 'wlan0', 'eth1', 'ath1', or something like that.

2) type 'ifconfig $device_name up'. For example, 'ifconfig wlan0 up'.

3) scan available access points by typing 'iwlist scan'. Information will be displayed about access points that your wifi card is seeing. Locate the 'essid' of the access point that you want to connect to. For example, your essid might be 'mshome', 'dd-wrt', 'd-link'.

4) specify the essid for you wireless device by typing iwconfig essid 'iwconfig $device_name essid "$essid"'. For example, 'iwconfig wlan0 essid "dd-wrt"'.

5) type 'dhclient $device_name', For example, 'dhclient wlan0'

This should connect you to the internet.

---

### Post by tomdkat on 2009-04-24
> **prshah said:**
> a) Boot into Windows if you have it, and note the resolution and the refresh rate; then duplicate those entries into your xorg.conf as shown previously.

b) Switch to using a VESA server, and once you get a display, you can use the GUI tools to enable support for restricted drivers.

```
Section "Device"
        Identifier      "Configured Video Device"
[color=red]        Driver          "vesa"[/color]
EndSection
```

Just a word of advice; without the correct resolution, switching to the vesa driver did not help me at all; I continued to have the same problem.Thanks for the help.  I don't have Windows installed on this system so that wasn't an option.  I used the modelines (with refresh rates and resolutions) from the old Xorg.conf file that worked and that didn't help.  I tried two old PCI adapters, one using a ATI Mach64 chipset and one using a GeForce2 MX-200 chipset and got the same results.

And then....

> I do not believe a reinstall of xorg will help in anyway; but if you are determined, maybe this may do the trick```
sudo apt-get install --reinstall xserver-xorg-core
``` but once again, I don't think this will get you anywhere.
I tried this (before reading your post) and IT WORKED!!!!  Except I didn't know about the "--reinstall" option.  I did this:

apt-get autoremove xserver-xorg

Doing that involved restarting hald, which seemed to hang so I used ctrl-alt-del to reboot the system.  After the initial reboot, I tried:

apt-get install xserver-xorg

and was informed I had to run:

dpkg --configure -a

to fix an issue related to my hald "hang" above.  So, I issued that dpkg command and re-issued the

apt-get install xserver-xorg 

command and rebooted.  After this reboot, I got the spinning mouse pointer and I could see the login screen just fine.  Once I logged in, my desktop appeared just as messy as I left it.  :)

So, I'm now back in business.  I'm not happy about this experience but at least I'm operational again.

Thanks again for your help!

Now, I'm off to find out what the hell 'w3m' is and why it's causing my system to thrash.  *sigh*

Peace...

---

### Post by thermobee on 2009-04-24
i have the same problem, but reinstalling the xserver didnt fix the problem and i dont understand how to set the screen resolution. 

Can anyone help me please

---

