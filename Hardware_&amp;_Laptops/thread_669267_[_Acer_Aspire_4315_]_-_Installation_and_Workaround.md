---
title: "[ Acer Aspire 4315 ] - Installation and Workaround"
date: 2008-01-16
forum: Hardware &amp; Laptops
---

### Post by tistaharahap on 2008-01-16
I am writing this tutorial for people who wants to install Ubuntu 7.10 - Gutsy Gibbon on an Acer Aspire 4315 laptop. There are a few things you need to do post installation to enable both compiz and the wireless adapter.

You can do the installation of Ubuntu without a sweat. Just pop in the CD to your CD drive and press F12 at the preliminary boot screen and choose to boot from your CD drive. Install Ubuntu by following the usual methods.

When you boot your laptop the first time, when you have reach your desktop you will notice that the Restricted Drivers Manager is detecting your wireless card inappropriately. I have written a howto regarding the matter to enable the wireless adapter in this following link: [http://ubuntuforums.org/showthread.php?t=662877](http://ubuntuforums.org/showthread.php?t=662877). For the sake of a complete tutorial, I am copy pasting the instructions in this thread:

> 1. Remove any ath_pci driver from the RESTRICTED DRIVERS MANAGER
2. Make sure that you have build-essential package installed, if not, fire up a terminal and type in sudo apt-get install build-essential
3. Navigate your way in Terminal to the directory where you downloaded the archive for the driver
4. Type these to decompress the archive tar xfz madwifi-ng-r2756+ar5007.tar.gz and cd madwifi-ng-r2756+ar5007
5. Type make to compile
6. Type sudo make install to install the driver
7. Type sudo modprobe ath_pci to insert the driver as a kernel module
8. Restart by typing sudo reboot
9. If all goes well, after you restarted, you will find wireless networks in your Network Manager

The next thing to do if you want to enable compiz, you can do a workaround by editing an executable file. But please remember that by doing so, you won't have any video playback unless you disable XV (hardware accelerated playback) in Ubuntu. If you still want to enable compiz, here's the trick:

> 1. Fire up terminal
2. Type these: **mkdir -p ~/.config/compiz/ && echo SKIP_CHECKS=yes >> ~/.config/compiz/compiz-manager**
3. Go to **System -> Preferences -> Appearances** and activate Desktop Effects at the last Tab.
4. If all goes well you will have compiz running.
5. If you want advance compiz configuration (you should), type these in terminal: **sudo apt-get install compizconfig-settings-manager**
6. If you want unaccelerated video playback, run **gstreamer-properties** through terminal and disable XV.

All other functions with the laptop should work out of the box. Good luck and enjoy Ubuntu ;)

---

### Post by Flymo on 2008-02-19
Thanks, that looks like really useful information - we'll give it a try on our 'development' partition of UbuntuStudio - just in case :).   
In any event, it's so helpful to find proffered solutions to the driver problems that seem to plague the laptop world.  

Would you care to comment on why  both Compiz and XV cannot co-exist ?

Best regards, Ben

---

### Post by greg.harvey on 2008-02-22
Awesome thread! Thanks! Just saved me hours of wi-fi pain. ;)

---

### Post by Mahyar on 2008-02-22
Thank you for this information.  This is the first time I've ever been able to run Compiz-Fusion.

I wonder whether you can help me get the multimedia keys working with Amarok?  You know all the keys on the right with the blue icons on them?

Cheers

Mahyar

---

### Post by FrancesL on 2008-02-25
> **tistaharahap said:**
> I am writing this tutorial for people who wants to install Ubuntu 7.10 - Gutsy Gibbon on an Acer Aspire 4315 laptop. There are a few things you need to do post installation to enable both compiz and the wireless adapter.

You can do the installation of Ubuntu without a sweat. Just pop in the CD to your CD drive and press F12 at the preliminary boot screen and choose to boot from your CD drive. Install Ubuntu by following the usual methods.

When you boot your laptop the first time, when you have reach your desktop you will notice that the Restricted Drivers Manager is detecting your wireless card inappropriately. I have written a howto regarding the matter to enable the wireless adapter in this following link: [http://ubuntuforums.org/showthread.php?t=662877](http://ubuntuforums.org/showthread.php?t=662877). For the sake of a complete tutorial, I am copy pasting the instructions in this thread:



The next thing to do if you want to enable compiz, you can do a workaround by editing an executable file. But please remember that by doing so, you won't have any video playback unless you disable XV (hardware accelerated playback) in Ubuntu. If you still want to enable compiz, here's the trick:



All other functions with the laptop should work out of the box. Good luck and enjoy Ubuntu ;)
 Hi ..I just followed all this using copy and paste into a terminal, now my Acer has a grey screen and i had to fire up my agian HP to write this...HELP:confused: I want ot go back to what it was before I made the changes

---

### Post by FrancesL on 2008-02-25
> **FrancesL said:**
> Hi ..I just followed all this using copy and paste into a terminal, now my Acer has a grey screen and i had to fire up my agian HP to write this...HELP:confused: I want ot go back to what it was before I made the changes

Update: I have managed to restart laptop by using power switch, I have used add/remove to remove compiz, I went into command line and reversed the instruction there. hopefully that is all enough

---

### Post by tistaharahap on 2008-03-27
> **Flymo said:**
> Thanks, that looks like really useful information - we'll give it a try on our 'development' partition of UbuntuStudio - just in case :).   
In any event, it's so helpful to find proffered solutions to the driver problems that seem to plague the laptop world.  

Would you care to comment on why  both Compiz and XV cannot co-exist ?

Best regards, Ben

There's an entry at compiz' wiki saying that due to a driver problem, when compiz is enabled if you try to play videos with XV enabled, it'll simply crash the application trying to play the video. Been looking around for solutions without success. It seems to problem is native to the x3100 Intel GMA graphic card.

---

### Post by kutjara on 2008-03-29
I used your method to get wireless working on my 4315 under Hardy beta (for which many thanks). Everything worked fine until I rebooted the machine, at which point it forgot all about the wireless card, until I manually typed  the modprobe instruction again, after which wireless was back. The situation repeated for every subsequent reboot.

While functional, having to retype modprobe at every reboot would soon get tiresome, so I did a bit of searching around, and found a solution in an unrelated thread.

simply type:

sudo gedit /etc/modules

and then append the line:

ath-pci

to the end of the text already there.

That's it. Hardy will now bring up the wireless card at boot-time.

I didn't have to do this under Gutsy, so I'm assuming it's something they've changed with the new release.

Once again, thanks for this invaluable tutorial. I'm loving how fast and functional this pedestrian little machine is with Hardy. My MacBook Pro and fast Windows desktop machines are getting very jealous that I seem to have abandoned them for this $350 wonder. They'd better not cop too much of an attitude, though, or they'll find themselves running Hardy, too. :)

---

### Post by Mahyar on 2008-03-30
Thanks Kutjara.

I'm also using Hardy and have noticed a few quirks which weren't present with Gutsy.

My Power Management isn't consistent.  Sometimes it dims when on battery power and sometimes it doesn't.

With Compiz, my graphics are just slightly choppy, but not when rotating the cube.

I also noticed that the original post had an underscore, but you used a hyphen in ath-pci.  Was that intentional?

Any other Hardy tips you have would be appreciated.

Regards,

Mahyar

---

### Post by kutjara on 2008-03-31
> **Mahyar said:**
> Thanks Kutjara.

I'm also using Hardy and have noticed a few quirks which weren't present with Gutsy.

My Power Management isn't consistent.  Sometimes it dims when on battery power and sometimes it doesn't.

With Compiz, my graphics are just slightly choppy, but not when rotating the cube.

I also noticed that the original post had an underscore, but you used a hyphen in ath-pci.  Was that intentional?

Any other Hardy tips you have would be appreciated.

Regards,

Mahyar

The hyphen is intentional. I can't now remember why I used a hyphen instead of an underscore, but it works. I suspect I may have simply copied what I read in the other thread, but I'll have to dig around to see if I can find it again, to be sure.

Otherwise, Hardy has been very good to me (aside from a bit of unfortunateness under Alpha 5 with the glibc6 bug). I haven't had to tweak much of anything, and my graphics are pretty smooth during normal use (even with quite a lot of the  compiz eyecandy turned on). I did notice quite a bit of tearing, artifacts, and other graphics nastiness when I tried to play Sauerbraten, but I haven't begun to get to the bottom of what's causing that.

One weird thing I haven't figured out yet is why Hardy won't connect to my home wireless network when the router's SSID broadcast is switched off. Gutsy would work fine once the connection had been manually set up; Hardy pretends to work (even showing the "hidden" network in the network manager applet), but it just won't connect to it. Once I turn SSID broadcast back on, it connects straightaway. Odd. On the plus side, WPA works just fine (I haven't tried WPA2 yet).

---

### Post by abhilashkumar on 2008-04-01
I cant get the wifi to work on my acer 4520 running hardy. The wifi button doesnt seem to do anything. i tried using ndiswrapper and installing the drivers. do you thing the madwifi drivers will work on 4520?

---

### Post by kutjara on 2008-04-01
> **abhilashkumar said:**
> I cant get the wifi to work on my acer 4520 running hardy. The wifi button doesnt seem to do anything. i tried using ndiswrapper and installing the drivers. do you thing the madwifi drivers will work on 4520?

I couldn't get ndiswrapper to work on my 4315, but madwifi does the trick nicely, so it's certainly worth trying.

The wifi button is totally non-functional for me, but that doesn't really bother me because I never turn wifi off on my other machines anyway.

---

### Post by Mahyar on 2008-04-05
Can you please explain how to install the madwifi driver?

---

### Post by Simon Bridge on 2008-04-30
The Acer Aspire 4315 is sold in NZ (and elsewhere) with Ubuntu 7.10 pre-installed. Some of the pre-installation decisions are questionable at best... there is a [web page](http://hbclinux.net.nz/acer4315.html) devoted to an analysis (with fixes) for this exact laptop. The same site has a [Hardy Heron](http://hbclinux.net.nz/acer4315-804.html) install page as well.

There has been feedback that these notes work with other, similar, laptops.

It is the hope that all outstanding issues can be solved (modem and suspend to ram not working, microphone support unstable) and an oem image presented to Acer - especially considering that Acer officially blame "limitations of linux" for non-functioning components.

---

### Post by cibby on 2008-06-14
Fantastic guide - I've got an Aspire 4315, and the madwifi driver works perfectly. I'm running Kubuntu 8.04 and I'm thrilled at how fantastic it looks and runs.

The only problem is that, in Monitor & Display, Kubuntu says that I've got the VESA driver (generic). Without an Intel GMA 965 driver, it seems to run some applications slowly - does anyone else have this problem, or know how to install the GMA 965 driver?

---

### Post by Flymo on 2008-06-23
Not sure about Kubuntu - but the underlying video configuration must be very close to Ubuntu?

So... Our Ubuntu 8.04 on an Acer 4315 just works - full 3D compositing desktop with translucent spinny cube and all.  May not be much practical use, but we find it convinces sceptical people that there is more to Ubuntu than safety and reliability.

fwiw, here are the relevant sections of our xorg.conf:

> Section "Device"
	Identifier	"Configured Video Device"
EndSection

Section "Monitor"
	Identifier	"Configured Monitor"
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Monitor		"Configured Monitor"
	Device		"Configured Video Device"
EndSection

Hope that helps.

All the best, Ben

PS Hi Simon!

---

### Post by Simon Bridge on 2008-07-01
heh - the usual unhelpful xorg.conf that will become annoyingly familiar over the next year or so as everyone adopts it.

Used to be you could

suda dpkg-reconfigure xserver.xorg

or whatever it was - and you'd get a dialog to select card and driver etc. There used to be a menu item too. The result was a populated xorg - with all the modes etc that we were used to.

Best I can come up with is to boot into rescue mode and use the "fix X" option.

---

### Post by Olnex on 2008-07-02
Do you have any Load_Cycle_Count issue on that laptop?

---

### Post by goforlinux on 2008-07-02
I have an Acer Aspire 9410 dual boot was a bit hard with some extra acer boot manager junk got rid of that then once I had Grub working then I did have a problem with the wifi i went into a windows system folder for wifi and I was able to see some files it seemed i was able to adopt it over to linux the button doesnt work for some reason while in Linux but i am able to use wifi idk if this is helpful

---

### Post by Simon Bridge on 2008-07-08
Nope - no issues with Load_Cycle_Count showing up anywhere on my machine.

Note - the Wifi button on the 4315 is odd... it has a hardwired aspect to it which means it is inadvisable to map it to anything other than the wifi and you cannot disable it at all.

Pressing the button produces one of hwe keypress events, you neet xmodmap to map that to a keycode. Then you can assign it pretty much anything. The acer_acpi patches seem to be effective in activating this as well - 2.6.25+ kernels are supposed to have this by default but I've not tested it.

I've had reports that the current intrepid kernel solves all problems.

---

