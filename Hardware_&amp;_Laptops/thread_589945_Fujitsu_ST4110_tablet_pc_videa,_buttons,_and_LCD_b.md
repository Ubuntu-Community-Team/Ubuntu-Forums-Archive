---
title: "Fujitsu ST4110 tablet pc: videa, buttons, and LCD brightness"
date: 2007-10-24
forum: Hardware &amp; Laptops
---

### Post by phenest on 2007-10-24
This is now a tutorial for the Fujitsu Siemens Stylistic ST4110 tablet pc running Ubuntu 7.10 (Gutsy).

If you are installing via the LiveCD, you may find the 'Video' and 'Stylus' sections relevant.

**Video**
For some reason, the Intel driver doesn't work properly. I had to resort to the i810 driver instead.
```
sudo /etc/init.d/gdm stop
sudo dpkg-reconfigure xserver-xorg
```
Then select the i810 driver and skip through the rest. Press Ctrl-Alt-Backspace, then...
```
sudo /etc/init.d/gdm start
```

**Stylus**
For some unknown reason, the stylus does not work in Gutsy, whereas it did in Feisty. Here's why:
```
sudo nano /etc/X11/xorg.conf
```
At the bottom of the file, you will see 3 lines commented out and a mention to this fact. You only need to uncomment the Stylus line. If you already have a graphical screen, then press Ctrl-Alt-Backspace.

**Boot screen**
There is no boot screen after installing Gutsy, even though the LiveCD has one. To fix this:
```
sudo apt-get install startupmanager
```
...and this is then found under System>Administration. Set the resolution to 1024x768 and close.


**Panel Buttons**
Download the drivers from [here]("http://sourceforge.net/projects/fjkey-st4000/"), and install as per the authors instructions.

**Miscellaneous**
1. I can change the brightness from root using
```
echo 1 > /proc/acpi/video/VGA/LCD/brightness
```
(1 = Dim 8 = Bright)
...but the gnome panel applet won't work. Any ideas?


**EDIT:** I have sold my Fujistu tablet (in favour of keeping the Compaq TC1100), so I won't be continuing with this tutorial. If anyone else wishes to continue the work here, be my guest.

---

### Post by phenest on 2007-10-26
If I run:
```
sudo dpkg-reconfigure xserver-xorg
```
...when it auto detects my video card, it selects 'intel' but it doesn't work. All I get is vertical white lines that fade in into very bright white lines. If I maually select 'i810' the video works, but is this a good idea and and does this support 3D on an Intel 82830 video card? If not, what should it be?

Having no boot screen is annoying.

Not having a proper way to adjust the brightness is annoying and it doesn't dim when using the battery.

And has anyone got these buttons to work on one of these tablets? If so, how?

---

### Post by phenest on 2007-10-27
Boot screen fixed using startupmanager and setting resolution to 640x480 @ 8 bit, or add vga=769 to the boot options.

---

### Post by hoborocket on 2007-11-01
I have this same issue, but setting the video to i810 worked. How did you get the pen to work? And can you get higher than 640x480?

---

### Post by phenest on 2007-11-01
I don't believe the i810 driver is the correct one, but it does work. As for the resolution, I ran dpkg-reconfigure xserver-xorg without gdm runninig, and made sure the only resolution available was 1024x768. The pen should work OOTB with Feisty, but with Gutsy you need to uncomment a few lines in xorg.conf (it shows you which ones).

---

### Post by hoborocket on 2007-11-06
i810 works fine for me. I even got beryl to work fine, if slowly.

How do you login with the pen? is there a way to get an onscreen keyboard on the login window or did you just rig up autologin first thing? And how does one gksudo? it just locks me out of all background windows x.x

---

### Post by phenest on 2007-11-06
Look at my signature and check the TC1100 guide for adding an On Screen Keyboard.

---

### Post by phenest on 2007-11-07
And why do the buttons work fine in Grub, but I cannot get them to work in Gutsy?

---

### Post by hoborocket on 2007-11-21
They don't work in Feisty either. There's also no way to rightclick that I can find.

---

### Post by hoborocket on 2007-11-21
I've found a solution to the right click problem. It's a ghetto solution, and there really should be a better option, but it works.

Make a new launcher and stick it in your top gnome-panel. Have it execute the following command:

xmodmap -e "pointer = 3 2 1 4 5 6 7"


Make another one, and make it execute this:

xmodmap -e "pointer = 1 2 3 4 5 6 7"

I'd put them next to eachother, but placement and such is your own decision.

The first one swaps mouse buttons 1 and 3, which are left and right. The second one swaps them back. You hit swap, click and do as you must, then swap back. Messy, but it works.

---

### Post by phenest on 2007-11-21
> **hoborocket said:**
> I've found a solution to the right click problem. It's a ghetto solution, and there really should be a better option, but it works.

Make a new launcher and stick it in your top gnome-panel. Have it execute the following command:

xmodmap -e "pointer = 3 2 1 4 5 6 7"


Make another one, and make it execute this:

xmodmap -e "pointer = 1 2 3 4 5 6 7"

I'd put them next to eachother, but placement and such is your own decision.

The first one swaps mouse buttons 1 and 3, which are left and right. The second one swaps them back. You hit swap, click and do as you must, then swap back. Messy, but it works.

Why do all this. It all worked fine for me in Ubuntu 7.10. Press the stylus button toward the tip for a middle click, and away from the tip for a right click. If you need a work around then something is wrong with your setup.

---

### Post by hoborocket on 2007-11-23
Those buttons have never worked for me, in any OS. Maybe I got a bad pen. (This thread is #1 result for most ST4110 google searches now, which is how I found out there was a new reply :p)

Does the onboard wireless work for you? Nothing I do has managed to beat it into life, including ndiswrapping the XP drivers.

---

### Post by phenest on 2007-11-23
I have actually sold mine now (too many computers at home), but while I had it, I did get everything working in Gutsy.

---

### Post by The Neelz on 2008-02-12
@ Phenest; you cannot imagine how much your post has helped me getting those damn tablets to work.

Since I had to use an USB stick for installing a distro and pendrivelinux.com had some handy tuts using Window$ for getting a bootable stick, Linux Mint ended up being the best working distro. Based on Ubuntu and loaded with all the codecs you need it just works :rolleyes:

So my advice is to go with Mint, use the information from the first post and please find out how to rotate the screen and keeping the mouse settings correctly and then tell me ;-)

One other problem without a solution is getting out of suspend (which works fine) without locking the screen. This a known issue and there is a post out there about this small yet annoying inconvenience.

---

### Post by phenest on 2008-02-12
> **The Neelz said:**
> One other problem without a solution is getting out of suspend (which works fine) without locking the screen. This a known issue and there is a post out there about this small yet annoying inconvenience.

It's not an issue. Open Configuration Editor and browse to /apps/gnome-power-manager/lock/suspend and uncheck.

---

### Post by The Neelz on 2008-02-13
> **phenest said:**
> It's not an issue. Open Configuration Editor and browse to /apps/gnome-power-manager/lock/suspend and uncheck.

Thanks. Again.
I must have been searching in all the wrong places.

---

