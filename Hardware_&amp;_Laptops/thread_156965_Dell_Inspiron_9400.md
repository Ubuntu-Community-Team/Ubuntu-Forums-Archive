---
title: "Dell Inspiron 9400"
date: 2006-04-08
forum: Hardware &amp; Laptops
---

### Post by ghakko on 2006-04-08
Hello there.

I'm posting this in the hope that it might be helpful to others setting up Ubuntu on a [Dell Inspiron 9400](http://www1.us.dell.com/content/products/productdetails.aspx/inspn_9400?c=us&cs=04&l=en&s=bsd&~section=specs#tabtop) notebook.

A standard Ubuntu Breezy installation does not work too well; I recommend [Dapper (Flight 5 or later)](http://cdimage.ubuntu.com/releases/dapper/flight-5/dapper-install-i386.iso) instead because it has much better support for the hardware on this notebook:
[LIST]
[*] CPU: **Works.** *Intel Core Duo T2400.* Upgrade to kernel "linux-image-2.6.15-22-686" or later; second CPU core does not seem to show up on some earlier kernels. Upgrade "powernowd" to [0.97](http://snapshot.debian.net/archive/2006/03/24/debian/pool/main/p/powernowd/powernowd_0.97-1_i386.deb) or later; earlier versions do not scale frequencies on multicore processors correctly.
[*] Bluetooth: **Works.** *Dell Wireless 350 (optional).* Use Fn-F2 to turn on the built-in controller (which will appear as a USB-to-Bluetooth dongle).
[*] Ethernet: **Works.** *Broadcom BCM4401-B0.*
[*] Video: **Works.** *Intel GMA950.* Upgrade "xserver-xorg-driver-i810" to 1.4.1.3 or later; earlier drivers otherwise do not identify this chipset. Install ["915resolution"](http://www.freshnet.org/debian/hoary/915resolution_0.5-2_i386.deb) to drive LCD display at full (1920x1200) resolution. 3D accelleration, VGA output, DVI output and display cloning all work. Xinerama, dual-head and S-Video support not tested yet.
[*] USB: **Works.** *Intel EHCI.*
[*] IDE: **Works.** *Intel 82801 SATA controller.* Disk spins down correctly when on battery power.
[*] Audio: **Works.** *Intel 82801 HDA.* Upgrade kernel to "linux-image-2.6.15-22-686" or later; PCM channel is stuck on mute with some earlier kernels.
[*] Firewire: **Works.** *Ricoh OHCI.*
[*] Power management: **Works.** *Unknown chipset.* Standby, suspend-to-RAM and suspend-to-disk work.
[*] Touchpad: **Works.** *Synaptics.* Tap-drag and vertical scrolling work correctly; horizontal scrolling is disabled by default.
[*] Wireless networking: **Works.** *Intel 3945ABG (optional).* Upgrade kernel to "linux-image-2.6.15-22-686" and "linux-restricted-modules-2.6.15-22-686" or later.
[*] Memory card slot: **Does not work.** *Ricoh R5C822.*
[/LIST]
The laptop's hard disk comes partitioned in three: an NTFS partition with an OEM-branded copy of Windows XP Home (or optionally, Windows XP Professional), a bootable "Dell utility" partition (used mainly for software restores) and a bootable "MediaDirect" partition (a stand-alone media player that can be started from a cold boot by hitting the "MediaDirect" button). All three can be safely deleted when setting up a Linux-only system.

---

### Post by bluevoter on 2006-04-10
Try here
[http://support.intel.com/support/notebook/sb/CS-006408.htm](http://support.intel.com/support/notebook/sb/CS-006408.htm)

---

### Post by nanotube on 2006-04-10
hi
that's very useful info. 
you might want to post all that info into the laptoptestingteam webpage on the official ubuntu wiki.
link: [https://wiki.ubuntu.com/LaptopTestingTeam](https://wiki.ubuntu.com/LaptopTestingTeam)

---

### Post by sardylan on 2006-04-21
Hi all!!!
Sorry for my English and for my knowledgo of Linux...
I've download the ISO od Kubuntu 5.10 and I've burn it down an a CD... I'va installed it in a 1100 MHz without problems... I've decided to install the same kubuntu disc on my new Dell Inspiron 9400... No problem during installation, but at the end of initialization, when he has to show the login window, he write something like "shutting down KDE" or similar and he show the black screen and he ask me to login like the "Konsole" in command line mode... I hope that you have understand... Someone can help me??? Many thenks to all... Bye!!!

---

### Post by nanotube on 2006-04-22
[QUOTE=sardylan]Hi all!!!
Sorry for my English and for my knowledgo of Linux...
I've download the ISO od Kubuntu 5.10 and I've burn it down an a CD... I'va installed it in a 1100 MHz without problems... I've decided to install the same kubuntu disc on my new Dell Inspiron 9400... No problem during installation, but at the end of initialization, when he has to show the login window, he write something like "shutting down KDE" or similar and he show the black screen and he ask me to login like the "Konsole" in command line mode... I hope that you have understand... Someone can help me??? Many thenks to all... Bye!!![/QUOTE]

hi,
from the console, try running this command:
sudo dpkg-reconfigure xserver-xorg
and making sure settings are correct. 

if that does not work, try the following. edit your /etc/X11/xorg.conf file using the following command:
```
sudo nano /etc/X11/xorg.conf 
```
and find the line that looks like
```
Device "ati"
```
and change to 
```
Device "vesa"
```
save, and try rebooting.

---

### Post by 5-HT on 2006-04-26
[quote=ghakko]Hello there.

I'm posting this in the hope that it might be helpful to others setting up Ubuntu on a [Dell Inspiron 9400]("http://www1.us.dell.com/content/products/productdetails.aspx/inspn_9400?c=us&cs=04&l=en&s=bsd&%7Esection=specs#tabtop") notebook....[/quote] 
Thanks for posting this.
 I'm looking at getting a 9400 and your post was comforting.

---

### Post by PhrankDaChickenGeek on 2006-05-07
[QUOTE=ghakko]
[*] Wireless networking: **Works.** *Intel 3945ABG (optional).* Upgrade kernel to "linux-image-2.6.15-22-686" and "linux-restricted-modules-2.6.15-22-686" or later.
[/QUOTE]

I found the linux-image, but I can't seem to locate the restricted modules. Should I see it if all repositories are enable in the package manager? :confused:

---

### Post by razboinik on 2006-05-08
I Just upgrade to 2.6.15-22 and now my headphone/mic don't work, they used to work with 2.6.15-21, should I add something to alsa config or what the problem may be? any ideas?

---

### Post by spira_mirabilis on 2006-05-10
I have just installed Dapper (Kubuntu Milestone 7) on the Inspiron 9400.
Everything works great, sound, peripherals, (including the media card slot which I heard was not working previously), except the version of the laptop I have has the Intel 950 Integrated graphics controller, (ah if only it was Nvidia...) and I can't seem to make it have a resolution higher than 1024x768, no matter what I do. I have tried tinkering with 915resolution, messing with Xorg config, to no avail. Maybe when 915resolution is included in X, this will work?

I also installed the SMP kernel to make sure I got the most from the Duo Core processor.

Overall, this laptop is well supported by Dapper. I ran all updates as soon as the install was finished. If you have trouble with the display during installation, run the xorg reconfiguration (sudo dpkg-reconfigure xserver-xorg) from the restore mode to "get in the door". I had to do this a few times to log in KDE at first.

PS- I also posted on a related thread : [http://www.ubuntuforums.org/showthread.php?p=1003818](http://www.ubuntuforums.org/showthread.php?p=1003818)

---

### Post by PhrankDaChickenGeek on 2006-05-11
[QUOTE=spira_mirabilis]
I have tried tinkering with 915resolution, messing with Xorg config, to no avail. Maybe when 915resolution is included in X, this will work?
[/QUOTE]


Had the same problem - You need a newer version of 915 Resolution. Grab it here:
[http://www.freshnet.org/debian/hoary/915resolution_0.5-2_i386.deb](http://www.freshnet.org/debian/hoary/915resolution_0.5-2_i386.deb)

You'll have to uninstall the older version, then just open the *.deb file, and it should install for you.


Run ```
 sudo 915resolution -l 
```
to see available modes. You can overwrite a mode by running ```
 sudo 915resolution $MODE $HRES $VRES 
``` Mode will be something like '5c'
Hres and Vres will be something like '1920' and '1200'

I would clean out your xorg.conf file of all other resolutions:
```

sudo gedit /etc/X11/xorg.conf

```
xorg.conf file:
```

Section "Screen"
	Identifier	"Default Screen"
	Device		"Intel Corporation Mobile Integrated Graphics Controller"
	Monitor		"Generic Monitor"
	DefaultDepth	24	
	SubSection "Display"
		Depth		24
		Modes		"1920x1200"
	EndSubSection
EndSection

```

You can test your settings by restarting Gnome: Ctrl+Alt+Backspace

Since the 915resolution modes are cleared on every reboot, you can add the following line to your startup file (adjust as needed):
```

sudo gedit /etc/init.d/bootmisc.sh

```
Add the following line after '[-f /etc/default/rcS ] && . /etc/default/rcS'
(Around line 18 )
```

915resolution 5c 1920 1200

```

& Reboot to test!

Hope it works for you!

---

### Post by spira_mirabilis on 2006-05-11
:confused: I ran through all these steps with the latest 915resolution (for me the mode was 5a for 1920x1200), I cleaned out the modes in the xorg.conf, edited the /etc/default/915resolution file and /etc/init.d/bootmisc.sh and and yet I am still stuck in 1024x768 resolution... 

Oddly, although the xorg.conf shows the resolutions:

```

SubSection "Display"
		Depth		24
		Modes		"1920x1440" "1920x1200" "1440x900"
	EndSubSection

```

I cannot use any of these that are listed..

Thanks for the help!

---

### Post by Rhawi Dantas on 2006-09-30
I have the same problem...
If anyone is lucky just tell me ;)

---

### Post by seanm2x on 2008-07-15
Any chance someone out there has the partition table settings for a Dell Inspiron 100GB HDD? The partition table has become corrupt and I need the proper settings to be able to access the recover partition. If not, if you have a copy or know where I can get a copy of the image files that would be just as helpful. Thanks.

Cheers,
Sean

---

