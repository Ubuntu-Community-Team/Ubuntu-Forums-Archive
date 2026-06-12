---
title: "Nvidia 7900 GO Overheating"
date: 2007-04-29
forum: Hardware &amp; Laptops
---

### Post by Tyriel on 2007-04-29
Hey guys, I am currently having this issue where the fan for my graphics card never turns on while I am in gnome.  I only noticed this when I left it running idle and came back and it was really lagging.  When I put my hands on the keyboard I could really feel the heat from graphics card the driver meeter said it was 123 degrees celcius. :shock: 

This was not a problem when I was using Ubuntu Feisty beta or at least I never noticed if it was.  Now it noticably over heats rapidly while just being idle in gnome.

I know DSDT issues have caused problems with sound on this model but I was easily able to fix that.  However this problem I have now even persists with a fresh install.

So does anyone know what causes this issue and how to resolve it?  I would love to hear from anyone who has had any similar experiences.

*Hardware:*
Toshiba Satellite P105-9312
Nvidia 7900 GO
2.16 Core Duo

---

### Post by EXCiD3 on 2007-05-03
How the hell did it get up to 123C?!?!??!

My DV9000 w/7600 Go has never passed 76C even while playing C&C Tiberium Wars for 5 hours straight in WinXP. This aught to have increased the temp WAY higher than Ubuntu would do sitting idle.

That is wierd. Unfortunately I have no idea what is wrong. I will go check this out myself.

---

### Post by mmgv on 2007-05-05
P105-S921 / 7900GS

Same problem here... i'm still working on the "no sound" issue but i can only use ubuntu/kde for a few minutes before overheating really kicks in and i begin to worry.

I'm trying to find anything about sensor and fan control on ubuntu, but no luck yet.

I thought it was controlled by the bios/HW, but obviously that's not exactly the case.

------------------
I think i've solved the problem by reinstalling the nvidia components (including the nvidia-settings package)
the system fan is on and the GPU fan activates from time to time

---

### Post by T*&amp;1p87)v# on 2007-05-06
Same here, Dell inspiron 9400 Nvidia Go 7800 and experiencing up to 80Deg while before I could not get it more than 73. Dunno why, I am using the latest dirvers from nvidia.com

---

### Post by krantix on 2007-05-09
same problem on toshiba p100-PAPAGE....

GPU around 114°...

sound is working after patching dsdt... but gpu fan still off... any clues??

---

### Post by misfitpierce on 2007-05-09
[http://www.linuxhardware.org/nvclock/](http://www.linuxhardware.org/nvclock/)

Nvclock can adjust the fanspeed on lots of GeforceFX/6/7 models but it can't adjust the fanspeed on laptops

Found on other forums

Changes:
# Geforce 7300/7600/7800GS/7900 support
# Smartdimmer suppport for 7600Go laptops
# Fanspeed adjustment support for 7600/7800GS/7900 cards

As for those not knowing how to compile try these debian downloads if you want to try program.... (note: not sure if they work as I run an ATI card and its fine but its worth a shot :) )

[http://packages.debian.org/unstable/x11/nvclock.html](http://packages.debian.org/unstable/x11/nvclock.html)

---

### Post by krantix on 2007-05-09
> **misfitpierce said:**
> [http://www.linuxhardware.org/nvclock/](http://www.linuxhardware.org/nvclock/)

Nvclock can adjust the fanspeed on lots of GeforceFX/6/7 models but it can't adjust the fanspeed on laptops

Found on other forums

Changes:
# Geforce 7300/7600/7800GS/7900 support
# Smartdimmer suppport for 7600Go laptops
# Fanspeed adjustment support for 7600/7800GS/7900 cards

As for those not knowing how to compile try these debian downloads if you want to try program.... (note: not sure if they work as I run an ATI card and its fine but its worth a shot :) )

[http://packages.debian.org/unstable/x11/nvclock.html](http://packages.debian.org/unstable/x11/nvclock.html)

sadly enough....

Error: Your card doesn't support fanspeed adjustments!


so nvclock does not work with nvidia go 7900 (laptop):confused:

---

### Post by EXCiD3 on 2007-05-09
I have never had a problem with the fan on my 7600 Go not working. This is wierd.

---

### Post by krantix on 2007-05-09
7900 seems to have a different fan chip...

---

### Post by EXCiD3 on 2007-05-10
> **krantix said:**
> 7900 seems to have a different fan chip...

That would make a huge difference.

---

### Post by krantix on 2007-05-10
> **EXCiD3 said:**
> That would make a huge difference.

i read that the Maxim MAX6648/MAX6692 Chip isn't supported yet :mad:

---

### Post by RedRedWine on 2007-05-16
Having the same problem but with a Dell E1705, Go 7900 GS.  I found during testing of fan functionality that the processor and video fans receive the same activation signal... essentially they are linked.  This would be a good reason why the video fan does not activate readily.  

     The proc is designed to withstand much higher temperatures, it's fan won't need speed up until it gets really hot.  But when the vid card gets hot, it's fan doesn't speed up ontime.  Might the proc's priority to fan control be overriding the GPU's?  Need help bad!!

---

### Post by nwheavyw8 on 2007-05-30
I have a Toshiba Satellite P105 with a GeForce Go 7900gs (Also, I have BIOS version 3.30 and dual boot Vista which came on it) , and was having the same problem.  I fixed the DSDT to get sound working, but the fan still refused to turn on.  Then, one day, it mysteriously started working.  It stayed on, in Linux, at a constant speed, and stayed around 50-60 degrees only getting a little higher while playing games.  This worked until I completely cut power to the laptop (removed power cord AND battery), but I got it working again by repeating what I did in Vista before it started working.

Here is what I did for anyone who wants to try:
*A lot of these steps probably aren't necessary, but I am listing EVERYTHING I did to get it working just in case.

*Oh yeah, have only the battery in, and not the charger cord.
1) Go into the BIOS setup, find "Thermal Mode Control" or something similar. Change it from "performance" to "silent"

2) Save and exit, then turn the computer off (with power button) when it starts booting again.

3) Turn it back on, boot into windows.

4) Block off the left side and bottom left (Where the GPU fan vents are) so it can't adaquately cool itself.

5) Left click the tray icon that shows a battery icon, change the setting from "Balanced" or "Power Save" to "Performance"

6) Now, proceed to heat up the graphics card by playing games, running 3D benchmark programs, or anything that is graphics intensive.  It doesn't need to completely overheat, it just needs to get so the left side of your laptop feels pretty warm, and the top-left of the laptop's underside (where the vent is) feels pretty hot.
I just wait until I can start noticing a little slowdown in my game, and that is when it is usually hot enough.

7) Quickly shut down Windows (Don't force a poweroff or disconnect the battery though)

8) Reboot into linux, at the point where the fan usually shuts off, it should surprisingly speed up a little and stay that way.

* Afterwards, don't forget to unblock the vents to let it cool.  Also, if you got it to work, it should work until you disconnect BOTH the power cord AND the battery at the same time.

I don't know if this will work for other laptops or not, I am just posting it because it works for mine and it is reproducible (I did it twice)

---

### Post by mikledet on 2007-05-31
Hmmm...  How can I see my gpu's temp?  I'm also on a Dell e1705 and keyboard's top right corner gets hot as hell, pls let me know how I can check the temps (cpu also if possible).

---

### Post by AcidicChip on 2007-09-28
I had the same issue after using Envy to auto install the 100.14.19 drivers.

My specs are as follows:
DELL XPS M1710
nVidia GeForce Go 7900 GTX 512MB

v2007.09.29.10.01
I have had many typos and corrections in this, so I decided to version it. Sorry for any confusion.

I would recommend the following as a possible solution for the over heating. I am a newbie to linux in general, but I have aggressively looked for a solution, because I was sick of the black windows, and having to restart xwindows on every boot because of a Beryl and nVidia conflict (Which 100.14.19+ fixes both of the issues as well, to the best of my knowledge), and this is what I have done to fix the issue, however the Slowdown Threshold is now set to 0c / 0 c / 0°c / 0 °c, and I don't know how to change it. This occurs no matter how I install the 100.14.19 drivers.

First of all, if you are using Beryl, right-click on it's tray icon, can set the Window Manager to Metacity (or other system default).

Uninstall nVidia via Synaptic Package Manager (search nvidia, and completely remove anything selected that has to do with nVidia). If you have Envy installed, uninstall nVidia via Envy. Open terminal and type the following:
```
cd /etc/X11
sudo mv xorg.conf xorg.conf.latest
sudo dpkg-reconfigure -phigh xserver-xorg
```

It'll ask you for a card type, select nvidia, if not listed, then select nv. Select all the known supported resolutions as well, and you're done. Reboot, and xwindows might be low color. Open Envy and have it auto install nVidia drivers. At the end of the install, allow it to modify the xorg.conf, and then reboot.

[i]**NOTE**: If you can not get back into xwindows because of an error, then press CTRL+ALT+F2 login if needed, and type the following:
```
cd /etc/X11
sudo rm xorg.conf
echo Next line is optional but recommended
sudo cp xorg.conf.latest xorg.conf
echo Again, next line is optional but recommended
sudo reboot
```[/i]

When you are back in xwindows, press ALT+F2
And Run: gksudo gedit /etc/X11/xorg.conf

Look under the "Device" section, and make sure that the driver says "nvidia" and not "nv", save it if need be, then open up terminal and type the following:
```
md5sum /etc/X11/xorg.conf | sudo tee /var/lib/x11/xorg.conf.md5sum
sudo nvidia-glx-config enable
sudo nvidia-settings
```

When the nVidia Settings dialog appears, go into the Display Configuration, and set the color depth to Millions of Colors (32 bpp), and Save to X Configuration.

Reboot your computer, and you should be all set. It'll be safe to re-enable Beryl.

---

### Post by maxfacta on 2008-01-18
Hi.
Did anyone solve this issue? Satellite P100, 7900Go, so nearly the same hardware as the original poster. Upgrading to Gutsy has also let my card reach temps in the 120's.

Also, I noticed a few people mentioning that they've patched their DSDT to solve the sound issue; can anyone point me in the direction for this solution? I applied the same patch as I did under Feisty, but it did not work.

cheers.

---

### Post by maxfacta on 2008-01-21
Update: upgrading the BIOS (version 4.20 for Satellite P100-A6A), and upgrading the nVidia driver seems to taken care of the heat problem. nVidia driver 169.07 has a "PowerMizer" powersaving feature. Basically, it autosenses the graphics computation requirements and autoadjusts the graphics card core and memory frequency. Anyway, you can read about it here: [http://aldeby.wordpress.com/2007/12/21/nvidia-powermizer-powersaving/](http://aldeby.wordpress.com/2007/12/21/nvidia-powermizer-powersaving/)

Now, to figure out how to get some sound out of this machine!

---

### Post by anarkiz99 on 2008-04-07
Just for a bit of help, this software can control fan speeds and temperatures on most of the dell inspiron, latitude and precision series[ http://www.diefer.de/i8kfan/index.html]("http://www.diefer.de/i8kfan/index.html") :)

---

