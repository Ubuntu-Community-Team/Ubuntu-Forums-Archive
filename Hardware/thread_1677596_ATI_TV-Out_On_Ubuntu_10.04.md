---
title: "ATI TV-Out On Ubuntu 10.04???"
date: 2011-01-29
forum: Hardware
---

### Post by sickened on 2011-01-29
Hi, 
I had installed Ubuntu originally without an actual graphics card, it was just running off the onboard graphics. Which was fine, but I'm sure some of you understand... Ubuntu's pretty cool when you can enable Compiz and play games and do some fun stuff every once in awhile :D So I found this old graphics card sittin' around (ATI Radeon 9200 PRO... yeah, it's an old graphics card, but my computer's also really old). I got the card hooked up inside the computer, and I'll admit, I really don't know what I'm doing after that. I'm aware that I need to install drivers somehow.
  But the problem is, the computer's hooked up to my HDTV via VGA cable (S-video is also an option here), and when I have it running off the actual graphics card, it  won't display anything past the boot screen. In order for me to do anything, I have to set the display back to the onboard graphics again.
  Like I said, I have no idea what I'm doing, and I'm not very comfortable trying to do this on my own...
  I'm running Ubuntu 10.04..
  Help?!?!?!

---

### Post by robert shearer on 2011-01-29
ATI Radeon 9200 PRO is no longer supported by ATI so there are no drivers to install.
Instead the open-source Radeon driver should have been activated automatically when you booted up with the new card.

can you run...
```
glxinfo
```
and..
```
lspci | grep VGA
```
 
in a terminal and post the output here.

---

### Post by sickened on 2011-01-29
> **robert shearer said:**
> ATI Radeon 9200 PRO is no longer supported by ATI so there are no drivers to install.
Instead the open-source Radeon driver should have been activated automatically when you booted up with the new card.

can you run...
```
glxinfo
```
and..
```
lspci | grep VGA
```
 
in a terminal and post the output here.
Running the first command gives me:
"name of display: :0.0
Segmentation fault"

The second command gives me:
"00:01.0 VGA compatible controller: Intel Corporation 82810E DC-133 (CGC) Chipset Graphics Controller (rev 03)
01:0a.0 VGA compatible controller: ATI Technologies Inc RV280 [Radeon 9200 PRO] (rev 01)"

---

### Post by robert shearer on 2011-01-29
> **sickened said:**
> Running the first command gives me:
"name of display: :0.0
Segmentation fault"

The second command gives me:
"00:01.0 VGA compatible controller: Intel Corporation 82810E DC-133 (CGC) Chipset Graphics Controller (rev 03)
01:0a.0 VGA compatible controller: ATI Technologies Inc RV280 [Radeon 9200 PRO] (rev 01)"

Mr Google says that "name of display: :0.0
Segmentation fault" is a known bug so lets forget that for now.

run...
```
dmesg | grep drm
```
and post back.

Just a thought, have you selected the AGP slot in bios as the preferred graphics adaptor ?
> it won't display anything past the boot screen. In order for me to do anything, I have to set the display back to the onboard graphics again.

If, when the screen blanks after boot, you take the vga plug from the ATI card and plug it to the onboard graphics you probably will get signal.
This is almost certain indication that the AGP slot is not selected in bios and the onboard graphics are default.
I am assuming that "boot screen' means the computers post screen and not the Grub/Ubuntu boot screen ??

---

### Post by sickened on 2011-01-29
> **robert shearer said:**
> Mr Google says that "name of display: :0.0
Segmentation fault" is a known bug so lets forget that for now.

run...
```
dmesg | grep drm
```
and post back.

Just a thought, have you selected the AGP slot in bios as the preferred graphics adaptor ?


If, when the screen blanks after boot, you take the vga plug from the ATI card and plug it to the onboard graphics you probably will get signal.
This is almost certain indication that the AGP slot is not selected in bios and the onboard graphics are default.
I am assuming that "boot screen' means the computers post screen and not the Grub/Ubuntu boot screen ??
Running that code gives me this:
"[    0.000000] Linux version 2.6.32-25-generic (buildd@palmer) (gcc version 4.4.3 (Ubuntu 4.4.3-4ubuntu5) ) #45-Ubuntu SMP Sat Oct 16 19:48:22 UTC 2010 (Ubuntu 2.6.32-25.45-generic 2.6.32.21+drm33.7)"

I DO know for a fact that the BIOS is NOT set to read from the slot, only from the onboard graphics at this time, because I did that myself, in order to use the computer  for the time being. You're right about being able to pull the VGA from the ATI and plug it into the onboard to get the display working properly.

However, I set the BIOS video adapter to read from the slot the ATI card is in, and with the VGA cable plugged into that slot (as I had done before), with the same problem. As I mentioned earlier, the VGA cable is connected to my HDTV. I tried plugging in my old computer monitor instead, and that worked just fine, no real problems with display, although I still wouldn't know what to do to enable the graphics card to actually work. I'm assuming this has something to do with the TV-Out then?
Concerning the boot process, the computer first boots into the GRUB Bootloader, I enter Ubuntu, there's a blinking cursor at the top-left corner for a couple seconds, and then the typical Ubuntu loading screen appears (this is all very normal for my computer boot process as far as I know). The log-in screen should appear then, but this is always where the display stops working properly.

---

### Post by robert shearer on 2011-01-30
OK, obviously the HDTV is not supplying the information to the OS to allow it to configure the display on boot.
We will probably have to produce an xorg file that is static but first lets try this..

(If Ubuntu is the only OS, you may need to press Shift as the computer starts to bring up the GRUB menu.)
Then at the grub screen press "e" to edit.

Navigate using the arrow keys and find the line that ends with "quiet splash".

Type nomodeset after it and then "Ctrl" + "x" to boot.

See if this gets you into a graphical desktop. 

Meantime can you post some details of the tv, make model etc.

---

### Post by sickened on 2011-01-30
The TV is a Sanyo LCD HDTV.. Here's a link with the rest of the specs and what not if you need it: [http://www.walmart.com/ip/Sanyo-19-Lcd-Hdtv/10929987]("http://www.walmart.com/ip/Sanyo-19-Lcd-Hdtv/10929987")

I tried the grub menu edit like you said, with the BIOS set to the ATI card, with the same problem.

Whether this is relevant or not, when I can actually boot into the desktop with the TV (just reading from the onboard graphics) I get this notification in the top right corner right after I log in that says "Could not apply the stored configuration for monitors X server does not support size requested" It's happened since I upgraded to 10.04, but it never bothered me since the desktop still displayed. Maybe it has something to do with it.

---

### Post by robert shearer on 2011-01-30
> **sickened said:**
> The TV is a Sanyo LCD HDTV.. Here's a link with the rest of the specs and what not if you need it: [http://www.walmart.com/ip/Sanyo-19-Lcd-Hdtv/10929987]("http://www.walmart.com/ip/Sanyo-19-Lcd-Hdtv/10929987")

I tried the grub menu edit like you said, with the BIOS set to the ATI card, with the same problem.

Whether this is relevant or not, when I can actually boot into the desktop with the TV (just reading from the onboard graphics) I get this notification in the top right corner right after I log in that says "Could not apply the stored configuration for monitors X server does not support size requested" It's happened since I upgraded to 10.04, but it never bothered me since the desktop still displayed. Maybe it has something to do with it.

Yes, very relevant !.
Wasn't aware you were running an upgraded version.
As of 10.4 Ubuntu sets up the display configuration dynamically at each boot, reading the attached monitor,cards,etc.

Prior to that there was a static xorg file that was edited if changes were made to hardware.
Sounds as though you still have that file in place and it is invoked but doesn't reflect your current hardware.

Can you post the contents of your xorg here.
navigate to /etc/X11/xorg.conf and copy and paste the contents here.(it will be read only)
 If it is a long file then wrap it in code tags)

If that won't open then in a terminal run
```
gksudo gedit /etc/X11/xorg.conf
``` and copy and paste.
(here you will be root so don't alter anything in that file, just copy and close it.)

Depending on what's there it may be as simple as renaming that file so that it isn't read at boot and the dynamic x-setup occurs.

Meantime, if you have a 10.04 or 10.10 live cd handy then boot with that and see if the display is dynamically configured correctly with the new card.
That will tell us if the file rename will work.
If you don't have a cd but do have the bandwidth then do download and burn one as they a very useful for troubleshooting.

---

### Post by sickened on 2011-01-30
I navigated to that folder, but no xorg.conf file seems to be there. Typing the command line into the terminal opens a totally empty file as well. Did a quick Google search, and it seems there are no longer any xorg files in Ubuntu 10.04. *sighs*...

I don't have an Ubuntu boot CD handy at the moment, but I could easily make one, that is, if it's still needed at this point...

---

### Post by robert shearer on 2011-01-30
> **sickened said:**
>  and it seems there are no longer any xorg files in Ubuntu 10.04. *sighs*...

no but we **can** make one and then edit it to add your tv.
Need to think on this some..

> I don't have an Ubuntu boot CD handy at the moment, but I could easily make one, that is, if it's still needed at this point...

Not totally needed but if you have the spare bandwidth then it would be of interest to see the results.

Something **is** strange as the outputs of many of the commands are not what I would expect.
Not sure if this is related to your upgrade process or the tv but possibly the former.

So booting from a known quantity, the live cd and running some diagnostics would help.
See if it will boot first then lets go from there.

---

### Post by Grenage on 2011-01-31
Hi there,

Robert Shearer had a word, so here's what I might add as an xorg.conf; while I've not used ATI drivers in a good while, there's no reason this shouldn't work with the open drivers.

First, create an xorg.conf file:

```
sudo touch /etc/X11/xorg.conf
```

Now edit the file; for ease of use, let's use gedit:

```
gksu gedit /etc/X11/xorg.conf
```

Paste the text below.  It basically has what I believe are the right settings for your monitor, and several resolution options which your monitor can handle:

```
Section "Monitor"
	Identifier "Monitor0"
	VendorName "sanyo"
	ModelName "DP19649"
	HorizSync 31 - 48
	VertRefresh 56 - 75
EndSection

Section "Device"
	Identifier "Device0"
	Driver "ati"
	VendorName "Radeon 9200"
EndSection

Section "Screen"
	Identifier "Screen0"
	Device "Device0"
	Monitor "Monitor0"
	DefaultDepth 24
	SubSection "Display"
		Depth 24
		Modes "1360x768" "1280x720" "1280x768" "1024x768" "800x600" "640x480"
	EndSubSection
EndSection
```

If you reboot and the GUI doesn't load, you simply need to delete or rename the xorg.conf file.  That will get your system back to it's former state.

If the above config doesn't work (it happens), we can specify the exact resolution using a modeline:

```
Section "Monitor"
	Identifier "Monitor0"
	VendorName "sanyo"
	ModelName "DP19649"
	HorizSync 31 - 48
	VertRefresh 56 - 75
Modeline "1360x768_60.00"   84.75  1360 1432 1568 1776  768 771 781 798 -hsync +vsync
EndSection

Section "Device"
	Identifier "Device0"
	Driver "ati"
	VendorName "Radeon 9200"
EndSection

Section "Screen"
	Identifier "Screen0"
	Device "Device0"
	Monitor "Monitor0"
	DefaultDepth 24
	SubSection "Display"
		Depth 24
		Modes "1360x768"
	EndSubSection
EndSection
```

---

### Post by sickened on 2011-02-02
> So booting from a known quantity, the live cd and running some diagnostics would help.
See if it will boot first then lets go from there.

I finally found the time to make a boot CD (sorry I took awhile). I decided to go with the 10.10 CD, figured if I was going to have to install it, it might as well be updated. But, sadly, running that Live CD didn't improve anything. With the BIOS set to read from the graphics card, I didn't get anywhere past the "Run Ubuntu Without Installing" or whatever it says.

> If you reboot and the GUI doesn't load, you simply need to delete or rename the xorg.conf file. That will get your system back to it's former state.

Just out of curiosity, how would I delete/rename the xorg file if I couldn't get the GUI to load? I haven't tried it yet, but I'm totally new to the whole xorg concept, and I was just a little bit "iffy" on that.

---

### Post by Grenage on 2011-02-03
Hi there,

If the GUI fails to load, you'll most likely get a terminal prompt.  You can log in there and issue a delete/move command as per usual:

```
sudo rm /etc/X11/xorg.conf
```

or

```
sudo mv /etc/X11/xorg.conf /etc/X11/xorg.old.conf
```

If for some reason you don't get a prompt, and you end up with graphical corruption, you can press Ctrl-Alt-F1 to get a prompt.

---

### Post by sickened on 2011-02-03
Well luckily none of those extra codes were ever required (: 
By using the first xorg.conf setup you had, I could boot the whole way into the desktop with no problems (running from the graphics card, of course). Of course, I still don't know what kind of drivers I would need, etc. There's nothing in the Proprietary Hardware Drivers, so I'm lost after that.

---

### Post by robert shearer on 2011-02-03
ATI Radeon 9200 PRO is no longer supported by ATI so **there are no drivers to install**.
Instead the open-source Radeon driver will have been activated automatically when you booted up with the new card.

At the moment this is as good as it gets.
The Open-source driver is a work in progress so may continue to improve with future Ubuntu releases.

Good to hear that you now have a desktop using the card and your tv.

---

