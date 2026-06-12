---
title: "Xorg, Nvidia older cards, intrepid Solutions"
date: 2009-03-10
forum: Installation &amp; Upgrades
---

### Post by lesemi on 2009-03-10
I have 4 older desktops that i have been running kubuntu for the kids to use for quite some time.  After upgrading all 4 to Intrepid i ran into some difficulties with the video drivers particularly.  After reading many posts I found it discouraging to see some users moving away from Nvidia for Ati for example or simply giving up on 3d acceleration.

For my two towers with flat screen the problems were resolved quite simply.  I found that by activating the restricted driver after fresh install caused nothing but problems.  Xorg is no longer configurable so i was at a loss.

The easiest solution was to exit to console and terminate xserver (ctrl alt+F1) 
sudo /etc/init.d/kdm stop
sudo cp /etc/X11/xorg.conf /etc/X11/xorg.conf.bak (just in case something gets messed up
sudo apt-get install envyng-qt envyng-core envyng-gtk

envyng is a script written by alberto milane - and i raise my hat to the guy because he has gotten me out of many jams in the past.

then run the script
sudo envyng -t

and select the ati or nvidia restricted driver that is recommended.
Reboot and it should do the trick.
You can always tweak the settings after by running 
sudo nvidia-settings

On a another machine - i had the same video card as on a different tower and for some reason after the fresh install of intrepid and install of nvidia driver - the resolution was set to 640x480 - pretty crappy - 
the driver was installed properly - i always run the game openarena as a test ( a favourite amongst my kids).

It took me a while but i found a post and it solved the issue.

In Xorg.conf - the monitor device section was pretty blank.

I have modified it to look as such: 
Section "Monitor"
	Identifier	"Configured Monitor"
	VendorName	"Unknown"
	ModelName	"LG"
	HorizSync	30.0 - 70.0
	VertRefresh	60.0
EndSection

and that did the trick - of course choose the Horizontal sync that matches your monitor and vert refresh.
The monitor in question is an old crt LG.
After this xorg mod - all resolutions were now available under 
nvidia-settings.

I read in a previous post that old nvidia cards were no longer supported and I find it disturbing that some people write such comments that can turn away users.  Intrepid works incredibly well for me - 3D acceleration and all - on both 64 bit and 32 bit.  I have had to make tweaks but overall it rocks.

To all - keep up the great work.

PS - my kids don't know more how to operate linux than windows

---

