---
title: "Broken ATI Drivers"
date: 2010-10-28
forum: Hardware
---

### Post by Toxcity on 2010-10-28
Evening guys,
I am just having fun and trying to learn as much as I can so this evening I decided I would download some ATI drivers and try and install them. 

Now this seemed all okay until I rebooted and I had both the old and the new drivers installed. Messy! So I tried to uninstall both drivers. Rebooted and now I have broken packages and the like. 

I have no working drivers I can't install or uninstall. I always get an error telling me to "FORCE_ATI_UNINSTALL" but have no idea how to do that.

Any ideas? I would on a quest for more performance but ended up with no performance. :(

```
Warning] Uninstall : inst_path_default or inst_path_override
 does not exist in /etc/ati.  This suggests that the ATI driver
 is not installed, the ATI driver is only partially installed,
 or the current ATI driver installed is an older version than the
 one this script was designed for.  Both files listed above are
 required for determining where installed files are located.
 To force uninstallation of the driver by guessing where the
 uninstallation files are located, set the FORCE_ATI_UNINSTALL
 environment variable and re-run /usr/share/ati/fglrx-uninstall.sh (this is not recommended).
```

---

### Post by Toxcity on 2010-10-28
Got some drivers installed after figuring out the Force command. They are running but have yet to get hardware acceleration back. Working on it. :)

---

### Post by Toxcity on 2010-10-28
Cleaned the lot out and reinstalled. Had some kind of visual bling until I installed the drivers from the Ubuntu thingy. Rebooted and back to square one no bling. :(

Tried to enable effects and it gives me an error because it fails. Stuck. :(

---

### Post by tadaskr on 2010-10-29
I had similar problem with 10.04. Now I'm using 10.10 and no problems for now :)

---

### Post by Flcn42 on 2010-10-29
Hi Toxcity,

I had the same warning when I tried to uninstall and reinstall the ATI drivers. I moved the /etc/ati and /usr/share/ati  directories to a different location. The warning message disappeared and I could install without any problems.

The drivers provided by Ubuntu (System->Administration->Additional Drivers) do provide acceleration. The drivers provided by AMD (10.10) don't seem to provide acceleration (it doesn't work on my PC). I believe Ubuntu has some kind of pre-release version that is different from the AMD 10.10 version. So for the time being we should stick with the Ubuntu drivers.

The reason I was playing around with the drivers was because my PC was incredibly slow and I thought it was because of the drivers. However I found that by installing Linux kernel 2.6.36 the PC became much faster (see thread [[ubuntu] 10.10 runs slow and jerky]("http://ubuntuforums.org/showthread.php?t=1592245") post [#93]("http://ubuntuforums.org/showpost.php?p=9962335&postcount=93"). I don't recommend playing around with the kernel unless you're prepared to do a complete reinstall of Ubuntu :(

Hope some of this helps!

---

### Post by Toxcity on 2010-10-29
Thanks for the reply guys! 
I have now got the Ubuntu drivers installed but I get no acceleration what so ever. :( 
With them disabled I get all the prettiness back. Any ideas? :)

---

### Post by Flcn42 on 2010-10-29
Hi Toxcity,

Have you tried ->System->Preferences->Appearance->Visual Effects->Normal?
This works with the Ubuntu drivers. (Extra may be too much for your graphics card.)

---

### Post by Toxcity on 2010-10-29
Hey Flcn42,

Yep, I've tried that. Gives me a nice error saying "Failed to enable desktop effects" after attempting to find a driver (which is installed). 

Stuck! :(

---

### Post by Flcn42 on 2010-10-29
Hi Toxcity,

If you open the ATI Catalyst Control Center (->System->Preferences) Are the fields for OpenGL filled in? (at the bottom of the Information entry). If the fields a blank the installation was not complete. You will need to uninstall (+reboot) and then remove manually any remains of the drivers (directories mentioned in an earlier post by me). You should also preform a clean-up, clear and update of your apt-get cache before reinstalling:

```

sudo apt-get clean
sudo apt-get check
sudo apt-get update

```

Then try to install the drivers again.....

---

### Post by Toxcity on 2010-10-29
Dead on, the OpenGL fields were empty. :)
How do I completely clean all ATI stuff before I reinstall? 

Thanks!

---

### Post by Flcn42 on 2010-10-29
Aha!


The offical way to unistall the driver is described here: [ATI installation instructions]("https://a248.e.akamai.net/f/674/9206/0/www2.ati.com/drivers/linux/linux_cat109-inst.pdf")

Unofficial way 
[LIST=1]
[*]uninstall the drivers   ->System->Administration->Additional Drivers->De-activate
[*]reboot
[*]check and (re-)move any unwanted remains (/etc/ati and /usr/share/ati); I moved both directories to /tmp and later threw them away.
[*]preform the three apt-get steps mentioned in previous post (sudo apt-get clean; sudo apt-get check; sudo apt-get update)
[*]install again using   ->System->Administration->Additional Drivers->Activate
[/LIST]

---

### Post by Toxcity on 2010-10-29
Everything went well, cleaned Cache Cleared configs installed driver (took a while) rebooted and boom. Still not working. :( 

Still nothing in the OpenGL fields. Stuck.. again. :)

---

### Post by Flcn42 on 2010-10-29
bummer  :confused:

What does youe /etc/X11/xorg.conf file look like?

Here is mine:


```
Section "Monitor"
	Identifier   "aticonfig-Monitor[0]-0"
	Option	    "VendorName" "ATI Proprietary Driver"
	Option	    "ModelName" "Generic Autodetecting Monitor"
	Option	    "DPMS" "true"
EndSection

Section "Screen"
	Identifier "aticonfig-Screen[0]-0"
	Device     "aticonfig-Device[0]-0"
	Monitor    "aticonfig-Monitor[0]-0"
	DefaultDepth	24
	SubSection "Display"
		Viewport   0 0
		Depth     24
	EndSubSection
EndSection

Section "Module"
	Load	"glx"
EndSection

Section "ServerLayout"
	Identifier     "aticonfig Layout"
	Screen      0  "aticonfig-Screen[0]-0" 0 0
EndSection

Section "Device"
	Identifier  "aticonfig-Device[0]-0"
	BusID       "PCI:1:0:0"
	Driver	"fglrx"
EndSection

```

It should be identical (automatically generated).

Running out of ideas. I have noticed a lot of threads regarding the ATI drivers...

---

### Post by Toxcity on 2010-10-30
File does not exist. :(

---

### Post by Flcn42 on 2010-10-30
Hi Toxcity,

Well you could try to make it yourself:

```
sudo gedit /etc/X11/xorg.conf
```

And paste mine into the file, reboot and see what happens...

However I suspect there is something else going wrong. Another thing you could try to find out what is going wrong is to uninstall (using ->System->Administration->Additional Drivers->De-activate) and then installing manually:

```

sudo apt-get install fglrx fglrx-amdcccle fglrx-modaliases
```

You should now see any warning and/or error messages (don't forget to reboot afterwards).

---

### Post by Toxcity on 2010-10-30
Going to try that now. Manual editing of the xorg.conf failed. :( 
God, I hate ATI...

---

### Post by Toxcity on 2010-10-30
Sorry for double post.

Manually downloaded the packages but never got the message. Got to the end and nothing happened. Rebooted and the driver isn't install. 

Looking like a full reinstall. :(

---

### Post by gloinar on 2010-10-31
I did several reinstalls of the drivers as described here - no success.

But running

```
sudo aticonfig --initial
``` and restarting Xorg finally got the ati drivers to work. 

I guess you have to purge the drivers (I also deleted all fglrx and ati folders afterwards), reinstall them and run the config tool - that did it for me.

Happy Halloween!

---

