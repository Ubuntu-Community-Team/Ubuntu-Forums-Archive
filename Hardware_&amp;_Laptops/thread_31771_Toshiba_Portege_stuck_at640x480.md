---
title: "Toshiba Portege stuck at640x480"
date: 2005-05-04
forum: Hardware &amp; Laptops
---

### Post by bp_ss on 2005-05-04
I'm a noob so please be gentle  :)

I'm trying to get an old laptop running at 1024x768

When ever I boot into X windows, I'm stuck at 640x480, regardless of my xorg.conf file. Same thing using knoppix (even when fb1024x768 is used).

It's a toshiba protege 7020ct with a NW2200 controller. This doesn't seem to be that uncommon.

1024x768 works in win2k.

Thanks for any help in advance.

---

### Post by Jason DeRose on 2005-09-22
There seems to be some problem with the with the HSync and VSync ranges not being set correctly.  As far as I understand, they are irrellevent on LCD monitors with most video chipsets as they are auto detected, but aparently this one needs the information.

Anyway, I don't know much about the root of this problem as I haven't invistigated further, but here what I did to get it working:

open a terminal and run:
sudo dpkg-reconfigure xserver-xorg

Here is how I answered all the questions:

Attempt to autodetect video hardware?
No

Select the desired X server driver.
neomagic

Enter an identifier for your video card. 
*Just leave it as is*

Please enter the video card's bus identifier. 
PCI:0:4:0

Enter the amount of memory (in kB) to be used by your video card.
*Leave blank*

Use kernel framebuffer device interface?
No

Autodetect keyboard layout?
No

Please select your keyboard layout.
*Just leave it as is*

Please select the XKB rule set to use.
*Just leave it as is*

Please select your keyboard model.
*Just leave it as is*

Please select your keyboard variant.
*Just leave it as is*

Please select your keyboard options.
*Just leave it as is*

Emulate 3 button mouse?
Yes

Enable scroll events from mouse wheel?
Yes

Select the X.Org server modules that should be loaded by default.
*Just leave it as is*

Write default Files section to configuration file?
Yes

Write default DRI section to configuration file?
Yes

Attempt monitor autodetection?
No

Enter an identifier for your monitor.
*Just leave it as is*

Select the video modes you would like the X server to use.
1024x768

Please choose a method for selecting your monitor characteristics.
Medium

Please select your monitor's best video mode.
1024x768 @ 60Hz

Write monitor sync ranges to configuration file?
Yes

Please select your desired default color depth in bits.
16

Then you can reboot your laptop or run:
sudo /etc/init.d/gdm restart

to restart X.

And things then worked fine for me at 1024x768; however, the built-in erasure mouse thingy isn't working.  Haven't got that figured out yet.

Good luck.   ;-)

---

