---
title: "Radeon HD 6630M &amp; Ubuntu &quot;Experience&quot;"
date: 2012-06-08
forum: Hardware
---

### Post by CybaCowboy on 2012-06-08
When I access the "Additional Drivers" setting (System Settings-->Additional Drivers), Ubuntu indicates that an "ATI/AMD propriety FGLRX graphics driver" is installed, activated and in-use; however when I access "Details" (System Settings-->Details-->Overview), all I see is "Unknown" next to "Graphics".

Furthermore, under the "Graphics" section of the Details screen (System Settings-->Details-->Graphics), my driver is listed as "Unknown" and the "Experience" is listed as "Standard".


How do I ensure that the correct driver is installed for my laptop, how do I change the "Experience" (which I assume is the Ubuntu equivalent of Microsoft's "Aero" in their "Windows" operating systems) to fully utilize the capabilities of my graphics card?


I have a Sony VAIO VPC-CB15FG with an AMD Radeon HD 6630M graphics card, running Ubuntu 12.04.

In terms of Ubuntu experience, I'd be considered a "noob", so go easy on me guys...

---

### Post by daniaix on 2012-06-13
take a look here, maybe it helps. If does, please post again and tell us about. We need to know more about this issue

[http://ubuntuforums.org/showthread.php?t=1930450](http://ubuntuforums.org/showthread.php?t=1930450)

daniaix

---

### Post by N0oki3 on 2012-06-13
Hello there CybaCowboy,

First of all use this command 
```
lspci | grep VGA
```
If you have 2 graphics card (1 is intergrated and the other is discrete as you said radeon HD 6630m)
If you do have, reboot notebook and go into bios. Check if you have option to manually switch between graphic cards. If you do have, select discrete 1 aka radeon HD 6630m)
**If you don't have this option** you can still try it, but it is 90% chance that it won't work, becouse hybrid graphics is quite new thing and it doesn't have full support on linux.

Now....if you run 32-bit ubuntu, than first thing you have to do (just copy paste command by command)
```

sudo apt-get install build-essential cdbs fakeroot dh-make debhelper debconf libstdc++6
sudo apt-get install dkms libqtgui4 wget execstack libelfg0 dh-modaliases
sudo apt-get install linux-headers-generic xserver-xorg-core libgcc1
cd ~/ 
mkdir catalyst12.4
cd catalyst12.4
wget http://www2.ati.com/drivers/linux/amd-driver-installer-12-4-x86.x86_64.run
chmod +x amd-driver-installer-12-4-x86.x86_64.run
./amd-driver-installer-12-4-x86.x86_64.run --extract driver
cd driver/common/lib/modules/fglrx/build_mod/
wget -O fglrx.patch http://ubuntuone.com/5gNgEmVfzs3ytD5QZ2YGCi
patch -p1 < fglrx.patch
cd ~/catalyst12.4/driver/
./ati-installer.sh 8.961 --buildpkg Ubuntu/precise
cd ../
```

Than use the tutorial, which gave you daniaix and follow it from original poster from step
```
sudo dpkg -i fglrx*.deb
```

[I]If you preffer to write commands, help yourself with tabulator key to generate path/name of commands
e.g. ins <tab> -> install[/I]

---

### Post by ratcheer on 2012-06-13
The best way to see exactly what video driver is running on your system is to browse **/var/log/Xorg.0.log** and search repeatedly for the string "LoadModule". After 6 or 8 hits, you will get to it.

Or, try to just search for fglrx. If your driver was installed and in use, that is what you should find. If it's still running the open source driver, it will probably be radeon, instead.

Tim

---

### Post by CybaCowboy on 2012-06-14
> **N0oki3 said:**
> First of all use this command 
```
lspci | grep VGA
```
If you have 2 graphics card (1 is intergrated and the other is discrete as you said radeon HD 6630m)

Here's what I get:
```

00:02.0 VGA compatible controller: Intel Corporation 2nd Generation Core Processor Family Integrated Graphics Controller (rev 09)
01:00.0 VGA compatible controller: Advanced Micro Devices [AMD] nee ATI Whistler [AMD Radeon HD 6600M Series]

```


> **N0oki3 said:**
> If you do have, reboot notebook and go into bios. Check if you have option to manually switch between graphic cards. If you do have, select discrete 1 aka radeon HD 6630m)
**If you don't have this option** you can still try it, but it is 90% chance that it won't work, becouse hybrid graphics is quite new thing and it doesn't have full support on linux.

Nope, there's no option in the BIOS to manually change graphics cards, in fact there's not even a reference to the graphics capabilities of my laptop...


> **N0oki3 said:**
> Now....if you run 32-bit ubuntu

Nope, 64-bit all the way, complete with 16GB of RAM! ;-)

So I take it the commands are different for 64-bit systems then? Any ideas what commands I should use instead?


> **ratcheer said:**
> The best way to see exactly what video driver is running on your system is to browse **/var/log/Xorg.0.log** and search repeatedly for the string "LoadModule". After 6 or 8 hits, you will get to it.

I tried this, but to be honest, I'm not really sure what I should be looking for...

There was a couple of references to "Intel" and "Vesa" alongside references to video drivers, but it still doesn't mean too much to me.

---

### Post by N0oki3 on 2012-06-14
[quote=CybaCowboy]Nope, there's no option in the BIOS to manually change graphics cards, in fact there's not even a reference to the graphics capabilities of my laptop...[/quote]

Have you updated your BIOS to latest version ? 

[quote=CybaCowboy]Nope, 64-bit all the way, complete with 16GB of RAM! 

So I take it the commands are different for 64-bit systems then? Any ideas what commands I should use instead?[/quote]
all of the commands are the same, only OS works a bit diffrently. 

So yes, as you use 64bit ubuntu use that guide we gave you and you shall see if it works or not.

Good luck

---

### Post by CybaCowboy on 2012-06-14
Okay,


So I've done all of the above and Ubuntu looks (slightly) prettier, but is there a way that I can confirm that Ubuntu is now using the AMD Radeon HD 6630M graphics card (or component of the card?)?

The "Details" screen (System Settings-->Details-->Overview) still shows "Unknown" next to "Graphics" and under the "Graphics" section of the Details screen (System Settings-->Details-->Graphics), my driver is still listed as "Unknown", and the "Experience" still is listed as "Standard".

---

### Post by N0oki3 on 2012-06-14
> **CybaCowboy said:**
> Okay,
So I've done all of the above and Ubuntu looks (slightly) prettier, but is there a way that I can confirm that Ubuntu is now using the AMD Radeon HD 6630M graphics card (or component of the card?)?
Logout and you have options Ubuntu and Ubuntu 2D. Login with Ubuntu and type into terminal ```
echo $DESKTOP_SESSION
```
If you get output Ubuntu 2D or something like that, then you are still using intergrated graphic card.

[quote=CybaCowboy](System Settings-->Details-->Graphics), my driver is still listed as "Unknown", and the "Experience" still is listed as "Standard".[/QUOTE]
in terminal type ```
update-pciids
``` and check again under system settings

---

### Post by ratcheer on 2012-06-14
> **CybaCowboy said:**
> 
I tried this, but to be honest, I'm not really sure what I should be looking for...

There was a couple of references to "Intel" and "Vesa" alongside references to video drivers, but it still doesn't mean too much to me.

At the time it said that, it means you were using Intel video (probably on your motherboard), not the ATI card. /var/log/Xorg.0.log is refreshed every time you restart your system (actually, every time you start X), so you can always look at it again to see what you are using at that point in time.

Tim

---

### Post by CybaCowboy on 2012-06-14
> **N0oki3 said:**
> Logout and you have options Ubuntu and Ubuntu 2D. Login with Ubuntu and type into terminal ```
echo $DESKTOP_SESSION
```
If you get output Ubuntu 2D or something like that, then you are still using intergrated graphic card.

All I get is:
```

ubuntu

```


> **N0oki3 said:**
> in terminal type ```
update-pciids
``` and check again under system settings

This is what I see, along with no changes under the system info:
```

update-pciids: /usr/share/misc/pci.ids.new is read-only

```



[i]Edit: I realized that I needed to do it as the root ("sudo") user and sure enough, the code worked fine:
```

Downloaded daily snapshot dated 2012-05-07 03:15:01

```

There's no changes under the system info though - I'll try logging-out and back in, posting an update only if there's changes in the system info...[/i]

---

### Post by N0oki3 on 2012-06-14
> **CybaCowboy said:**
> All I get is:
```

ubuntu

```

This is good! ubuntu = 3D

Download this by selecting some mirror [mesa utils 64bit](http://packages.ubuntu.com/precise/amd64/mesa-utils/download) and download it. Now if you are using firefox to download it, with terminal go to
```

cd /home/**name of pc**/Downloads
chmod +x mesa-something forward (just type mesa and press tab)
sudo dpkg -i mesa-somethingforward.deb 

```
This helped to some people, might help to you too

To test your rendering just simply use
```
 glxinfo
```

---

### Post by CybaCowboy on 2012-06-14
Nice, thanks!

---

### Post by N0oki3 on 2012-06-14
> **CybaCowboy said:**
> Nice, thanks!
No problems lad ! 

Also just for your information :) If you do not like unity bar i guess you know that you can change your desktop :) You can use "mac icons" download it via ubuntu software center -> cairo dock

Or if you preffer gnome, my fav
```

sudo add-apt-repository ppa:gwendal-lebihan-dev/cinnamon-stable
sudo apt-get update
sudo apt-get install cinnamon

```
change desktop session to cinnamon. Voila

[img]http://www.linuxbsdos.com/wp-content/uploads/2012/04/PreciseCinnaDesktop1-600x450.png[/img]

---

### Post by CybaCowboy on 2012-06-14
Believe it or not, I actually quite like the Unity Bar and find myself rarely touching the menu...

It sorta like the "VAIO Gate" software I have in Windows, which is more or less the same thing, except with newsfeed support (VAIO Gate is normally "hidden" like the Unity Bar *can* be, but shows a tiny bit with the headlines of your subscribed newsfeeds).

---

