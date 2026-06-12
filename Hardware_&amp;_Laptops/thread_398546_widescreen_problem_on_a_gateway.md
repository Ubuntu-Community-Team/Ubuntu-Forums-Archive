---
title: "widescreen problem on a gateway"
date: 2007-04-01
forum: Hardware &amp; Laptops
---

### Post by fatinbox on 2007-04-01
Hi there,

I'm a really-really green newcomer to ubuntu; played with various distros for the past month or so, and finally decided on edgy to replace my ever-slower, patchy, and horrific WinXP.

Overall a nice experience (50 secs boot time vs 3.5 minutes, just to give an example), but I ran into 3 big problems I can't get around: Ubuntu can't see widescreen, sound drivers, wireless card. This post is about the first one, and I'll get to the others time permitting. Help is really appreciated.

**To the point**: I have a Gateway 3040GZ laptop; max resolution is 1280 x 768 (i think), but I'm getting an annoying 1024x768 that makes my friends' pictures look freaky, among other unpleasantries. I read all the posts on the matter, and they all say "go to xorg.conf and change it". And here's the weird part for me: nowhere in my xorg.conf does it say anything about 1024. Here's actually what I have in the "screen" section.


Section "Screen"
Identifier "Default Screen"
Device "Intel Corporation 82852/855GM Integrated Graphics Device"
Monitor "Generic Monitor"
DefaultDepth 24
SubSection "Display"
Depth 1
Modes "1280x768"
EndSubSection
SubSection "Display"
Depth 4
Modes "1280x768"
EndSubSection
SubSection "Display"
Depth 8
Modes "1280x768"
EndSubSection
SubSection "Display"
Depth 15
Modes "1280x768"
EndSubSection
SubSection "Display"
Depth 16
Modes "1280x768"
EndSubSection
SubSection "Display"
Depth 24
Modes "1280x768"
EndSubSection
EndSection

Help, anyone ? I really don't want to go back to "windows and gates".

---

### Post by teaker1s on 2007-04-01
Applications>Accessories>Terminal

```
sudo dpkg-reconfigure xserver-xorg
```
**you may also need screen horizontal and vertical (screen technical specs)**
follow the prompts and leave settings alone 
until you get to resolution and you can select ones your screen will do,allow the wizard to save preferences and when you restart you can then go to gnome settings and set your resolution

---

### Post by fatinbox on 2007-04-01
Hi,

Thanks a lot. Did what you said - went through the prompts, left settings unchanged, except for the resolution one where I checked 1280x768, which is what is my  monitor's resolution is (14-inch Widescreen Ultrabright TFT WXGA). 

Restarted the laptop and then, in the gnome settings (is that system/preferences/screen resolution ?) I only had options going to 1024x768. Just as before. What changed was my xorg.conf, which now looks like this:


Section "Screen"
	Identifier	"Default Screen"
	Device		"Generic Video Card"
	Monitor		"Generic Monitor"
	DefaultDepth	24
	SubSection "Display"
		Depth		1
		Modes		"1280x768" "1024x768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		4
		Modes		"1280x768" "1024x768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		8
		Modes		"1280x768" "1024x768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		15
		Modes		"1280x768" "1024x768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		16
		Modes		"1280x768" "1024x768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		24
		Modes		"1280x768" "1024x768" "800x600" "640x480"
	EndSubSection
EndSection

?? Help ?

---

### Post by teaker1s on 2007-04-01
okay well other than xorg configuration and screen the other thing it could be is your graphics driver, we could find out what you have by
```
 lspci |grep VGA
``` post output

---

### Post by fatinbox on 2007-04-01
it's been taken care of, help no longer neede. All I needed was 915resolution. 

Thanks.

---

### Post by eye_doc on 2007-05-07
Sony Vaio PCG TR1MP: Intel 82852/855GM graphics driver.
I too have had a lot of fun trying to get this to work. After trying to edit or configure the xorg.conf either directly or via various "sudo dpkg-reconfigure xserver-xorg" type commands and getting no-where (the xorg.conf file seemed to have no influence over the resolution available via System|Preferences|Screen Resolution) I have it working - except I'm not sure which bits were essential!

I first downloaded and compiled a hack which attach to the post, as it is very hard to find on the net. Save it as 1280patch.c (with thanks to the author, Andrew Tipton)

I used the instructions [_here_]("http://www.linuxquestions.org/questions/showthread.php?p=2728721#post2728721") to compile . The "wget ..." bit didn't work for me (the link was dead)  but you can use the file copied below. You will have to use Synaptic package manager to install the libc6-dev library unless you are already set up to compile stuff. Also for some reason I was unable to do the "echo /usr/local/sbin/1280patch > /etc/rc2.d/S98xpatch" so I just did "sudo gedit S98xpatch" from within the /etc/rc2.d directory,  typed in " /usr/local/sbin/1280patch" and saved, before doing the chmod as in the original article.

I also had to install via Synaptic (System|Administration|Synaptic Package Manager) the 915Resolution (try search "915") and the X-server-xorg-i810 package - this should also come up on the search 915 window in Synaptics.

Finally I hand edited (sudo gedit /etc/X11/xorg.conf and sudo gedit /etc/default/915resolution) as per instructions found in /usr/share/doc/915resolution/README.Debian after you have installed 915resolution. 

Having tried to install with the 915resolution, with i810 driver and with the hack separately, and the 915 and i810 together, and then with the hack and i810 without 915, I've given up trying to work out how much of this is necessary. But this worked for me and I have not found a really good answer anywhere on the fora or the net. In fact I got pretty fed up with all the "all you have to do is edit xorg.cong" answers which simply don't work. 

If anyone understands it (I certainly don't - this is my first day on my first Linux installation as you can probably tell) could you explain what is going on?



Open the attached text file and save it in a file called "1280patch.c"

---

