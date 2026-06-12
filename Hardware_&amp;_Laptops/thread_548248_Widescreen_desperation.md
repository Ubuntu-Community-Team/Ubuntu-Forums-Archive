---
title: "Widescreen desperation"
date: 2007-09-11
forum: Hardware &amp; Laptops
---

### Post by StrayTheNomad on 2007-09-11
I stuggled most of yesterday and all of today trying to get my screen resolution set for my Widescreen Akai 32" LCT320IAD LCD display to run at any sort of widescreen resolution with my installation of Ubuntu Feisty Fawn 7.04 with an intel 946gz integrated graphics chipset.
I tried editing my xorg.conf file numerous different ways
I tried using 915resolution in numberous combinations
I tried updating my i810 driver to the intel replacement. That killed ubuntu.
I've reinstalled 8 times, but now I've gotten fairly sharp at booting into recovery mode, logging in as root and changing around my configuration using mainly
sudo nano /etc/X11/xorg.conf
and
sudo nano /etc/default/915resolution
with
sudo 915resolution 5c 1280x1024
These commands usually help to recover most of the errors resulting from whatever I'd screw up whenver I'd replace values with widescreen ratios like 1366x768, 1280x800, 1280x768, 1280x720.
Right on the box the TV came in, it says "Native Resolution" 1366x768
When I run Gary's Mod (CS:S) in Vista, the display switches to 1366x768. So my display supports this.
Vista usually runs in 1280x768 for me, but supports 1280x720 as well.
Each time I use 915resolution to achieve different resolutions, my results seem to vary.
1366x768: Leaves me with a black screen, TV's on screen display reads "No Support"
1280x768: Screen was square, but left unused black space to right and bottom was clipped off. The next time, the screen automatically shifted to 648x480 but the desktop was huge. Only the top left corner of the screen fit on desktop with the rest clipped off.
1280x720: Black Screen and OSD "Not Support." Although one time, I'm not sure how, but the on screen display showed up as 1280x768 and the Screen Resolution setting was at 1280x720. There area off screen was just the top and bottom toolbar panels. When I'd drag my mouse to the top or bottom edges, the whole desktop would scroll up or down to show what was off-screen. It was actually pretty neat. But after achieving this, I got overzealous and tried to install compiz-fusion which killed ubuntu.
Installed Ubuntu from scratch.
This time around, still couldn't get it to work. I got side-tracked, trying to install KDE. Killed Ubuntu again.
Now, I started out four days ago as a total Linux newbie. And it seems like everything I do still kills Ubuntu. But I don't think a newbie should really have to get in this far. You don't have to do this kind of work in Vista. As much as I hate to admit it, Vista "Just works" for my widescreen. Ubuntu should too. And this should be a priority.
Also, I can't seem to get full-duplex sound support. I sort of need to have multiple applications recording and playing sound at the same time. And I know it's a big order but it would be great if there was a way to get Ableton Live, Propellerheads Reason, Veoh, and the Steam Engine including Garry's Mod to run in Linux. These are all very specific programs that I run regularly on Vista. And these are the reason I can't just leave Vista and fully convert to Linux. The software available just isn't nearly as capable.
Or am I wrong?
I mean, I love the idea of the General Public License and OpenSource. I have a romantic love for Firefox, and OpenOffice. I've used them in Vista for years, and they work just as well in Ubuntu. And I got to love the Evolution Email program. But is there a Linux program that works just like Veoh? How about the other programs I mentioned?
Is there at least a fix for my resolution?
I want to love Ubuntu. I really do. But it's just not working for me.

---

### Post by chewearn on 2007-09-11
Have you seen this webpage, specifically section "5.4.3 Advanced Configuration Topics":
[http://www.freebsd.org/doc/en_US.ISO8859-1/books/handbook/x-config.html](http://www.freebsd.org/doc/en_US.ISO8859-1/books/handbook/x-config.html)

I recently have to struggle with a widescreen LCD TV as well, and the instruction on using /var/log/Xorg.0.log to extract the LCD EDID really helped.

---

### Post by StrayTheNomad on 2007-09-12
I noticed the part that says...
:Configuration with Intel® i810 integrated chipsets requires the agpgart AGP programming interface for X11 to drive the card. See the agp(4) driver manual page for more information."
So am I to understand tbat since I'm using the i810 chipset, then xorg.conf can't be used unless I get the AGP driver? Because so far the only AGP driver I can find is for an nVidea graphics card. Wil that driver work for me?

---

### Post by chewearn on 2007-09-12
hi StrayTheNomad
I'm still try to understand the inner workings of linux (currently trying to understand compiling the kernel and device drivers configuration).

At the moment, I'm do not know the answer to your question on the AGP part.

However, your specific problem of configuring the Intel integrated graphics to a widescreen LCD TV is quite similar to one I encountered a few weeks ago, and I was finally able to solve it by taking the info from the freebsd website.


1. it is certainly not possible to use nVidia driver with the Intel graphics.

2. you can try the setup using either the i810, or the intel driver; but it says here:
[https://help.ubuntu.com/community/FixVideoResolutionHowto](https://help.ubuntu.com/community/FixVideoResolutionHowto)
that the newer intel driver is better at screen resolution setup; so this is what I used.

3.  After changing the driver to "intel", I still cannot get the widescreen.  This is where the freebsd website helps; here is how:

Once you have the intel driver setup, find a resolution (any resolution) that will get you into the desktop.  Then, open a terminal, and run this command:

```
cat /var/log/Xorg.0.log | grep -A 10 "Supported additional"
```You should see something like this (taking this example from the website):
```
(II) MGA(0): Supported additional Video Mode:
(II) MGA(0): clock: 146.2 MHz   Image Size:  433 x 271 mm
(II) MGA(0): h_active: 1680  h_sync: 1784  h_sync_end 1960 h_blank_end 2240 h_border: 0
(II) MGA(0): v_active: 1050  v_sync: 1053  v_sync_end 1059 v_blanking: 1089 v_border: 0
(II) MGA(0): Ranges: V min: 48  V max: 85 Hz, H min: 30  H max: 94 kHz, PixClock max 170 MHz
```
Then, follow the instruction to add the ModLine into xorg.conf.  Restart gdm, and that's all.

In my case, the desktop is now running at 1280x768 on the LCD TV, except for an annoy problem I have yet to solve; which is, the login screen is still at some weird resolution which can't be displayed.  So I ended up turning the login screen off and let ubuntu use auto-login.

---

### Post by StrayTheNomad on 2007-09-12
I appreciate your help so far.
The command:
> cat /var/log/Xorg.0.log | grep -A 10 "Supported additional
Doesn't do anything in my terminal. I enter the command, no error, no feedback at all. It just moves down a line and gives me a new prompt.

Also, I've looked up my Xorg.0.log file, and it seems like it's full of errors. I can't really make heads or tails of what's happening, but take a look. 
I'd attach the whole file but it's 66.5k, and the forum has a limit.
> (II) I810(0): Broken BIOSes cause the system to hang here.
	      If you encounter this problem please add 
		 Option "DisplayInfo" "FALSE"
	      to the Device section of your XF86Config file.
(WW) I810(0): Extended BIOS function 0x5f64 not supported.
(WW) I810(0): Extended BIOS function 0x5f64 not supported.
(WW) I810(0): Extended BIOS function 0x5f64 not supported.
(WW) I810(0): Extended BIOS function 0x5f64 not supported.
(WW) I810(0): Extended BIOS function 0x5f64 not supported.
(WW) I810(0): Extended BIOS function 0x5f64 not supported.
(WW) I810(0): Extended BIOS function 0x5f64 not supported.
(WW) I810(0): Extended BIOS function 0x5f64 not supported.
(II) I810(0): Currently active displays on Pipe A:
(II) I810(0): 	CRT
(II) I810(0): No active displays on Pipe B.
(==) I810(0): Display is using Pipe A
(--) I810(0): Maximum frambuffer space: 65368 kByte
(II) Loading sub module "ddc"
(II) LoadModule: "ddc"
(II) Reloading /usr/lib/xorg/modules//libddc.so
(II) I810(0): VESA VBE DDC supported
(II) I810(0): VESA VBE DDC Level 2
(II) I810(0): VESA VBE DDC transfer in appr. 1 sec.
(II) I810(0): VESA VBE DDC read failed
(II) I810(0): Will use BIOS call 0x5f05 to set refresh rates for CRTs.
(--) I810(0): Maximum space available for video modes: 12288 kByte 
You'll notice for some reason, it thinks I'm using a CRT, but I'm using an LCD. I'm pretty sure this is why I can't get any reliable info on my refresh rates from most utilities.
Also, The section following that gives long, detailed Mode information, but the resolutions I want aren't listed, even though Windows can use them just fine.
According to the manual of my LCD, I want
> 720p (1280x720) Horizontal frequency: 45.00 kHz, Virtical Frequency: 60.00
I don't know the clock speed, it's not listed. 
So I think I know there IS a problem, I just don't have a clue how to go about fixing it.

---

### Post by chewearn on 2007-09-12
Ok, I can't think of anything else, except if you can go thru the Xorg.0.log and try to figure out the problem.

The aim is to try read the EDID info from the LCD TV (I'm not 100% sure here, but this info should be somewhere in the Xorg.0.log).  Then, there is no guessing about the exactly ModLine to add in xorg.conf

---

### Post by t52wa_r0x on 2008-06-17
Hi:
The 946GZ is supported by the newer "intel" Xorg driver.
You seem to be still using the "i810" driver.
I would strongly recommend using the "intel" driver.
Also, you might want to try the following to see whether it works for you:

**This is copy-and-pasted from somewhere else:**
This worked for me:


Generate desired modeline using the "gtf" command:
"gtf 1280 720 60"
Copy and paste the resulting modeline into "Monitor" section of "/etc/X11/xorg.conf". You could give it a reasonable name like "1280x720_60". (You can name it anything you like.)

Under the "Screen" section, under the subsection "Display", there is a line as follows:
**Modes "XXxXX" "XXxXX" "XXxXX"** (and so on)
You should enter the name of your new modeline (e.g. "1280x720_60") in here.
By right, we would like to put it as the first mode, but that's not necessary (since it won't work automatically, anyway).

Now start the xserver with "startx".
Yes -- the modeline is not working yet.
Don't worry, open a term and do:
"xrandr --output VGA --mode 1280x720_60"

If it works, your screen will switch to the new mode.
Congrats!
If you want to apply "1280x720_60" on every X startup,
please insert the following as the 1st line of "~/.xinitrc":
**xrandr --output VGA --mode 1280x720_60**

---

### Post by chewearn on 2008-06-17
> **t52wa_r0x said:**
> Hi:
The 946GZ is supported by the newer "intel" Xorg driver.
You seem to be still using the "i810" driver.
I would strongly recommend using the "intel" driver.

..[I]edit..
[/I] 


Please read the date of the last post.

.

---

