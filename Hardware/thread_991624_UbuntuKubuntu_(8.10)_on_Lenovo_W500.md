---
title: "Ubuntu/Kubuntu (8.10) on Lenovo W500"
date: 2008-11-24
forum: Hardware
---

### Post by gatman3 on 2008-11-24
I just wanted to share some info about running Ubuntu on a Lenovo ThinkPad W500.  I could not find a lot of specific info about Linux on this machine as it is relatively new, so I thought this might be useful to other prospective buyers or new owners who want to use it with Linux and specifically Ubuntu.  The machine I am using is a model 4062 with the Intel Core 2 Duo T9600 at 2.8 GHz, 4 gigabytes of RAM and a 200 gigabyte 7200 RPM Hitachi SATA hard drive.  This machine has the 9-cell battery (highest capacity offered).  I use this machine primarily for professional engineering (IC design) work.

I first installed Kubuntu 8.04, but discovered that the Intel 5100 AGN wi-fi chip is not supported by the kernel shipped with 8.04 (2.6.24, I think).  I can't remember now for sure, but I think that this wi-fi chip isn't supported until 2.6.26.  So I upgraded to an 8.10 beta... and subsequently the released 8.10, and the Intel 5100 AGN wi-fi seems well supported in 8.10.

I have only installed the 32-bit version and haven't had time yet to try the 64-bit build.  Note that with the 32-bit kernel only 3 gig of the physical memory appears to be available.

[EDIT: see further down in this thread for info on 64-bit Ubuntu on this machine; short answer is it works fine.]

Video

My W500 has the 1920x1200 display.  One knock on this display is that it is not terribly bright compared with most other modern laptop LCD displays.  But the high resolution is very nice for detailed graphical applications (logic waveform viewers are my primary concern), and it is very sharp and clear - especially in a dimly lit room, which is how I generally choose to work.

The W500 has "switchable" graphics with both an integrated Intel chipset graphics as well as a discrete ATI Radeon HD 3650 (I have seen it listed in specs as a FireGL V5700, but it reports in lspci as a Mobility Radeon HD 3650).  I have not seen any references to Linux support for switchable graphics, so I have not experimented with it.  In the absence of OS support for switchable graphics, you must select the graphics chip to be used in the power-on BIOS configuration menus. 

The integrated Intel graphics has the advantage of being somewhat lower power than using the ATI graphics, but provides limited 2D acceleration and no 3D acceleration.  The ATI graphics is required for reasonable compiz desktop effects, but burns more power as a tradeoff.  However, I did find that the proprietary fglrx driver consumes substantially less power than the open-source radeon driver.  In addition, I have not been able to get suspend and hibernate working with the Intel graphics, but it seems to work fine with either ATI driver.

Here is a table that shows the tradeoffs between the Intel and ATI graphics chips in the Lenovo W500 based on my experience:

[FONT="Courier New"]```
driver  DRI   2D   3D  power  suspend  hibernate  open source
------  ---  ---  ---  -----  -------  ---------  -----------
intel   yes  yes   no 16-19W     no        no         yes
radeon   no  yes   no 33-44W    yes       yes         yes
fglrx   yes  yes  yes 21-27W    yes       yes          no
```[/FONT]

Note that I have not been able to get suspend and hibernate to resume properly when the KDE4 desktop effects (compiz) are enabled.  Since you can manually disable the desktop effects and then successfully  suspend and resume, a workaround can probably be devised that disables the desktop effects in the acpi suspend scripts using dbus and re-enables them on resume.

I also have not been able to get the KDE display power control features to turn off the backlight after sitting idle for a period of time, although the backlight does turn off when the lid is closed.  I haven't found a way in the manual ACPI controls either, so no workarounds at present.

[EDIT: backlight turns off automatically with screensaver power control after adding Option "DPMS" "True" to the Monitor section in /etc/X11/xorg.conf]

Battery life with the Intel graphics is apx. 4.5 to 5 hours.  With the ATI chip using the proprietary fglrx driver (The Ubuntu 8.l0 version 8.55.2 fglrx in the intrepid repository) the battery life is about 3.5 to 4 hours.  It's more like 2.5 hours with the radeon driver.

The fglrx runs glxgears around 2200 FPS with the default window size, 800 FPS in fullscreen mode.  fgl_glxgears averages around 1150 FPS with the default window size (is there a fullscreen mode?  Couldn't find it...)

The W500 has two external graphics connectors: A VGA (D-SUB) connector and a DisplayPort connector.  As far as I can tell, the DisplayPort connector provides a digital graphics output and can be adapted for use with a DVI monitor connection.  Note that only the ATI graphics can drive both the VGA and the DisplayPort/DVI outputs; the Intel graphics only drives the VGA connector (as observed by xrandr).


Other Devices and their support status with Ubuntu/Kubuntu 8.10:

Wi-fi - Intel 5100 AGN works in Ubuntu 8.10, not in 8.04 or older.  I've seen at least one reference to Atheros shipped in the W500, and that required some massaging with ndiswrapper - yuck.

Ethernet - works fine at 1 GBE

sound - works.  ALSA provides separate volume controls for "Front" and "PCM", although they both seem to affect the speakers and the headphone jack, but the Front Mute only mutes the speakers.  Typical ALSA quirks.  The speakers also mute automatically when a headphone jack in inserted.

dvd r/w burner - haven't tried burning yet, works for playing DVDs

1394 - works using dvgrab and kino

integrated webcam - works with kopete.  [EDIT] Although it works with kopete, apparently the UVC video driver is broken in the 2.6.27 kernel for the 17ef:4807 webcam, and other UVC applications like cheese and luvcview do NOT work at this point.  Refer to this link: [https://bugs.launchpad.net/ubuntu/+source/linux/+bug/287888]("https://bugs.launchpad.net/ubuntu/+source/linux/+bug/287888") for more details.  I was unsuccessful in my brief attempt to compile and install the newest drivers, so I guess I'm waiting for an update in the repository.

SD/MMC card reader - works

displayport - haven't tried, although DVI brought out by the Advanced Dock works fine with the ATI graphics option, both radeon and fglrx drivers.

modem - haven't tried

bluetooth - successfully paired with my cellphone and Logitech mouse

fingerprint reader - not working, but I haven't spent much time on it

expresscard slot - haven't tried

Hard drive - The drive shipped in my machine is a 200 gigabyte Hitachi 1.5 Gbps SATA drive with hardware encryption.  The model reported by hdparm is "HITACHI HTS722020K9SA00" with "FwRev=DC4LC75A".  The drive received very high reviews and generally benchmarks as fast or faster than competitors' 3 Gbps drives.  There do not appear to be any options in the BIOS configuration pages for enabling the hardware encryption, and I have not seen any information about Linux support for the encyrption features of this drive... but I haven't researched it very thoroughly.  hdparm provides some ATA security commands, but they preface them with words like "VERY DANGEROUS", and it's not clear if these commands are intended for this particular drive.

[EDIT: After some research, I have read that a BIOS config option to set the disk encryption passphrase can be enabled using a DOS/Windows utility.  You apparently need a DOS boot disk and then run the utility provided by Lenovo.  Disk encryption is always enabled and can't be disabled; the BIOS option enabled by the Lenovo utility only allows setting a password on the disk]

Special keys

Volume - The volume keys work with ALSA out-of-the-box.  However, the mute key has some quirky behavior in that there is no on-screen indication that it has taken effect, and pushing it again while muted does not unmute; only pushing the up or down volume key unmutes.

ThinkVantage - Does nothing in Ubuntu (and we care why?)

Backlight function keys - work

LED keyboard light - works

Media player controls (on the arrow keys) - The pause key pauses Amarok, however pushing it again restarts the track from the beginning.  The skip forward and skip backward keys do advance the track forward or backward.  The stop key has no effect.

Other function keys (lock, battery, sleep, etc.) - seem to have no effect.


Docking Stations

It seems that Lenovo has two primary docking stations for use with the W500: the Mini Dock and the Advanced Dock.  I have an Advanced Dock at work that I use with the W500.  The primary difference between the Mini Dock and the Advanced Dock seems to be that the Advanced Dock includes an internal 16x PCI Express slot, with the implication that you can add a graphics card to the dock.  This would, in theory, allow you to use a PCIe graphics card with a dual (or more) DVI output to drive multiple monitors with a digital signal.  Otherwise, both docks have a VGA and a DVI connector, and dual monitor operation involves one monitor receiving an analog signal (VGA) and the other monitor receiving a digital signal (DVI).  When viewing a dual-monitor setup with mixed analog/digital signals, the differences are quite noticeable in that the VGA signal produces a noticeably blurry result in comparison.  But it's usable.

The PCIe slot in the Advanced Dock seems to be some kind of sick joke on the part of Lenovo.  It does not seem to work with just any off-the-shelf PCIe graphics card.  There are references on Lenovo's website to a Radeon X1300 card designated for use with the Advanced Dock, but this card seems to have been discontinued by Lenovo so one suspects that there were problems with it.  I tried it with a Lenovo branded NVidia NVS 290 card and had mixed results with two different W500 laptops - one running Kubuntu 8.10 and the other running Windows Vista.  We started with a single monitor connected to DVI output #1 from the NVidia card in the dock.  About half of the time (maybe 6 or 8 total boot attempts) we observed the Windows splash screen displayed by the graphics card in the dock, however we were never able to successfully install the NVidia drivers (the Windows control panel reported that the card was using the generic VGA driver).  Whenever the external card graphics booted properly, the dock would kick its fan up into high gear, too.  In any case, after these unsuccessful attempts, we connected the second DVI output to the other monitor but never saw the dock card display to either monitor again before we gave up (2 or 3 more boot attempts).  The other laptop running Ubuntu 8.10 never even showed the boot messages on the dock graphics card, and an lspci dump after booting did not report the card as present.  I don't believe this is a Ubuntu problem, though, because the Vista machine even showed the POST messages on the external card's output - long before the OS starts loading, but this never happened on the Ubuntu laptop.  Basically, just plain flaky at best, and the word in other forums is that few if any are able to make the Advanced Dock work with an external PCIe graphics card using older T-series machines either.  Kind of false advertising on the part of Lenovo, and besides, why even offer an additional dock option with a PCIe slot if you can't make it work.


Other Impressions

- Build quality is very solid.  The display hinges are standard Lenovo solid, tight metal hinges.  Lenovo advertises one-handed opening with the single latch release on the right side of the unit, but this isn't really possible because the display hinges are too tight for the relatively light weight of the unit, so two hands are required to pry the clamshell apart, at least on my machine.

- The matte finish plastic on the top of the unit tends to pick up finger prints frequently and is difficult to clean.

- The keyboard has a very nice feel (apparently a staple of Lenovo machines), although the page up/down keys in the upper right corner are too small, and I often accidentally hit the caps lock for some reason even though it is in the standard position to the left of the A key.

- I could also do without the standard IBM/Lenovo red eraser-head TrackPoint pointing device located between the G, H and B keys.  But that's personal preference.

- The additional three mouse buttons located above the touch pad provides a native middle mouse button, which is nice for Linux copy/paste.  It would have been nice to have a middle mouse button in the lower set of mouse buttons as well, but there are only two.

- The headphone jack is located along with the microphone jack in the front, which is a bad place when using the machine on your lap.  It should be on the side.  But the jack seems to be good quality, sturdy and tight.

- The machine is extremely quiet and cool.  The fan tends to run between 0 and 3000 RPM during normal use, and seems to peak under 4000 RPM with heavy load.  CPU temperature stays between 40 and 55 degrees C during normal use, and up to around 80 degrees C under heavy load.  The fan is extremely quiet even at the higher reported RPMs.

- For several compute intensive engineering applications (verilog logic simulations and logic synthesis) the machine runs core-for-core about 80% of the speed of a 3.0 GHz Xeon server CPU - very fast indeed.

If you have a W500, please share any experiences you have or any suggestions for tweaking.  Thanks!

---

### Post by AeroSigma on 2008-11-24
Thanks for the in-depth review.  I also have a W500, and I'm running Ubuntu 8.10.  It installed out of the box flawlessly, just as gatman3 suggested.  Incidentally it's the only distro that I tried that could boot up into X, It could be the Discreet Graphics setting in the BIOS, which I hadn't changed from 'enable both' to 'Only Discreet' until after Ubuntu was installed.

On that note, It might be important to realize that in order to properly run the fglrx drivers, and desktop effects without any hitch, I had to set the BIOS setting to Discreet graphics instead of Dual, or AutoDetect.  (Vista has the capability to switch between integrated and discreet graphics on the fly, nice for power conservation, but I prefer to always use the discreet graphics...and also linux.)

I am having dificulty with hibernate and suspend, but I haven't tried disabling compiz first, I'll try it.  (thanks for the suggestion.)
Edit: Disabling compiz allows suspend and hibernate to work great, but when I re-enables the desktop effects (set the effects in apperance to extra) it reset my compiz settings.  Is there a way to disable/enable compiz outside of the apearence menu that won't reset the changes I made in compiz-settings-manager?

I am running the 64-bit version and it hasn't given me any problems at all.  Wine runs great too.

I love the trackpoint mouse and have actually disabled the trackpad in the Bios.  Personal preference I guess.  Gatman3, you can disable the trackpoint in the BIOS so that it won't do anything when you bump it.  Unfortunaly I think this disables the upper mouse buttons (including the middle button.)  incidentally, does anyone know how I can change the mapping of the middle mouse button to scroll instead of paste?  Is this a Xorg thing, 'enable three button mouse emulation' perhaps?

I am considering re-compling the Kernel in the next couple of weeks, I guess we'll see how that goes.

---

### Post by benoit2008 on 2008-11-29
Thanks for sharing your experience. Especially the suspend and hibernate stuff, which I missed and didn't search a solution for yet. I'll try what you suggest.

> I could not find a lot of specific info about Linux on this machine

Indeed there's not much to find. [http://www.thinkwiki.org/wiki/Category:W500](http://www.thinkwiki.org/wiki/Category:W500) would have been a good place to start, and to use for your report, rather than a forum. There is also the ubuntu wiki:
[https://wiki.ubuntu.com/LaptopTestingTeam/Lenovo_IBM](https://wiki.ubuntu.com/LaptopTestingTeam/Lenovo_IBM)
from where you could create a page.

BTW, I did that on the French version of the Ubuntu wiki:
[http://doc.ubuntu-fr.org/lenovo_thinkpad_w500](http://doc.ubuntu-fr.org/lenovo_thinkpad_w500)

---

### Post by gatman3 on 2008-11-29
Thanks for the replies.

AeroSigma - I'm not experiencing the same issue with disabling/re-enabling the desktop effects initializing the settings.  I'm using KDE4; are you experiencing that with GNOME?

Benoit2008 - Thanks for the suggestions.  When I get some time I'll look into making a W500 page in one of the wikis as you suggest, unless you get to it first.

Some more info discovered since my initial post:

On suspend/hibernate:  Still no good solution for suspend/hibernate interop with desktop effects enabled.  Note also that I discovered that (1) movie players using the Xv driver (mplayer, cinelerra, etc.) do not work properly when desktop effects are enabled.  The result is extreme flickering during playback.  And (2) after a suspend/resume cycle, attempting to play back video with Xv causes the system to lock up hard.  Ctrl-Alt-F1 doesn't even work.  So, on this machine (W500 with Radeon HD 3650), suspend/hibernate AND fglrx AND (desktop effects OR Xv video) = no joy.  It seems you can have suspend/hibernate AND fglrx or you can have fglrx AND desktop effects... or you can have fglrx AND Xv video... but you can't have it all at the same time.

Also, I installed the 64-bit version of 8.10 as an alternate boot.  Works fine.  I had to use the nspluginwrapper to get the Adobe Acrobat Reader plugin working in Firefox, but otherwise everything else pretty much worked the same as the 32-bit install.  One other oddity - kvpnc with Cisco works fine with 32-bit Ubuntu, doesn't work with 64-bit (won't save the group password for some reason).  I also had trouble with Kompozer from the 32-bit repository, but works fine on 64-bit.

[EDIT: Adobe's new Flash 10 alpha for 64-bit linux works great, so the nspluginwrapper is no longer needed.  Unless... you are a Rhapsody subscriber.  It worked for a few months with Rhapsody, and then Rhapsody changed something and the 64-bit Flash plugin stopped working right near the end of December 2008.  Back to nspluginwrapper if you want Rhapsody on a 64-bit system...]

Here are some W500 (2.8 GHz Intel Core 2 Duo, 4 GB RAM) Ubuntu 8.10 32-bit vs. 64-bit benchmarks using nbench, for whatever it's worth:

```
-----------------------------------------------------------
TEST                : 32-bit Iter/Sec  : 64-bit Iter/Sec  :
--------------------:------------------:------------------:
NUMERIC SORT        :          1215.6  :          1379.7  :
STRING SORT         :          177.44  :          305.92  :
BITFIELD            :      5.3516e+08  :      5.6426e+08  :
FP EMULATION        :           179.8  :           300.8  :
FOURIER             :           35103  :           31060  :
ASSIGNMENT          :          40.567  :          41.494  :
IDEA                :            7936  :          8352.7  :
HUFFMAN             :            2620  :          2806.5  :
NEURAL NET          :          52.276  :           61.95  :
LU DECOMPOSITION    :          1954.1  :          1957.3  :
--------------------:------------------:------------------:
INTEGER INDEX       :          82.785  :         100.845  :
FLOATING-POINT INDEX:          69.750  :          70.901  :
-----------------------------------------------------------
```

(The indices are supposedly relative to a Pentium 90).

glxgears and fgl_glxgears reported nearly identical results between 32-bit vs. 64-bit.

I can't tell any noticeable difference in performance between the two, although it certainly feels better psychologically to get an extra 800 megabytes or so of usable RAM (top reports the available memory with the 32-bit kernel at 3106444k, and with the 64-bit at 3984312k).  However, it also seems that many applications use significantly more memory when running on the 64-bit OS compared with 32-bit (immediately after boot, 64-bit Xorg used 532M versus 445M on 32-bit, gkrellm used a whopping 322M vs. 65M, and overall the identical installations showed a total of 800M used on the 64-bit version versus 630M used on the 32-bit version).  A topic for a different thread, I suppose.

---

### Post by Bashar &quot; on 2008-12-19
i still have the hibernation issue although im using ATI not intel

any other advises?

---

### Post by rcmn on 2008-12-24
I noticed 2 issues and I would like to know if other owner have these issues as well.

-Reboot: 
    If I try to reboot from Kubuntu 8.10 the reboot will stop at the scan device menu(where u can hit esc/F1 to enter Bios). This issue doesn't show with winXP...

-Random freeze after using suspend to disk.
 It took my a little while to noticed that one. But each time i use suspend disk , I will experienced a system freeze .Usually it will happen if i launch a movie, or a big apps.

---

### Post by gatman3 on 2008-12-26
rcmn,

I haven't noticed the first issue.  But I can confirm the second issue, at least a variation of it.  I use the fglrx video driver, and I experience hard lock-ups following suspend or hibernate if I launch an application that uses direct rendering video after resuming.  One typical example is trying to play a video using mplayer with the xv driver after resuming.  Another example is using the KDE desktop effects (compiz), which also uses DRI.  The only workaround I have found is to avoid applications that use DRI after resuming.  That's a pretty lame workaround though.  But I have found that using mplayer with the x11 driver (i.e. "mplayer -vo x11 <filename>") avoids the problem.  Of course, video playback is usually too slow with the x11 driver, so this workaround isn't great, and it only solves the problem in a limited way for video players, not for other DRI applications.  I have experimented with settings in /etc/default/acpi-support but haven't found anything to solve this.  It hasn't been a high enough priority to dig much deeper; I just chalk it up to the crappy suspend/hibernate support in linux.

---

### Post by mkclarke on 2009-01-04
Hey AeroSigma,

Did you ever find anything more about the middle trackpoint button?  I would love to be able to use that to scroll as well.

Thanks to all of you for the great video advice!  I haven't tried hibernate or suspend, but compiz works nicley with the Intel driver.  I'm about to find out what kind of time I get out of my battery now.  With the radeon driver, I got similar results - about 3 hours.

Thanks,

Mike

---

### Post by quackeroni_pizza on 2009-01-08
I'm having trouble with compiz desktop effects and the fglrx driver. When I try to turn on effects, the display renders only a portion of the screen and the rest of it (20% of the right side of the screen) turns black. I have to switch it down to 1440x900 to work. 

Also the highest resolution I'm getting even without desktop effects is only 1680x1050. Do I need to edit xorg.conf?

---

### Post by edkuk13 on 2009-01-08
I have Ubuntu 8.10 installed on 3 computers basicly set up the same way. World of warcraft and flash player are used on all three. Two of the computers are working exceptionally, but the third has a locking problem. The computer locks up usually within 30 minutes of playing WoW or within a couple hours of my son playing on Noggin.com. The only real difference in the problem computer is it is using an LED monitor.

---

### Post by gatman3 on 2009-01-10
> **quackeroni_pizza said:**
> I'm having trouble with compiz desktop effects and the fglrx driver. When I try to turn on effects, the display renders only a portion of the screen and the rest of it (20% of the right side of the screen) turns black. I have to switch it down to 1440x900 to work. 

Also the highest resolution I'm getting even without desktop effects is only 1680x1050. Do I need to edit xorg.conf?


Here's how I would debug this:

First off, make sure you actually got the fglrx driver loaded.  Look in /var/log/Xorg.0.log for something like this:

(II) Module fglrx: vendor="FireGL - ATI Technologies Inc."
        compiled for 1.4.99.906, module version = 8.55.2
        Module class: X.Org Video Driver

Another possibility is that even though you may have installed the fglrx driver, you must be selecting the discrete graphics option in the BIOS config menu; otherwise the integrated Intel graphics chip will be used and xorg will automatically pick the intel driver.  I actually seem to remember that the intel driver defaulted to 1680x1050 graphics, so you should definitely check this; your /var/log/Xorg.0.log will tell you which driver is loaded for sure.  You can also tell with lsmod and grep for fglrx or intel:

```
> lsmod | grep fglrx
fglrx                2135688  34
```

If you're certain the ATI (discrete graphics) chip is selected and the fglrx driver is running, you can also try running the ATI Catalyst control panel and see what it thinks the available resolutions are.  I believe you can run it from a shell as "amdcccle" if you have the fglrx-amdcccle package installed.

With the new xorg installed in Ubuntu 8.10 you shouldn't have to edit your xorg.conf to get the highest resolution.  Don't be offended by the question, but are you certain they sold you a 1920x1200 panel?  If so, you can try forcing it by adding the resolution in your xorg.conf, but again, this shouldn't be necessary, at least with the fglrx driver:

```
Section "Screen"
        Identifier      "Default Screen"
        Monitor         "Configured Monitor"
        Device          "Configured Video Device"
        DefaultDepth    24
        SubSection "Display"
                Viewport  0 0
                Depth     24
                Modes     "1920x1200"
        EndSubSection
EndSection
```

---

### Post by gatman3 on 2009-01-10
x

---

### Post by gatman3 on 2009-01-10
> **edkuk13 said:**
> I have Ubuntu 8.10 installed on 3 computers basicly set up the same way. World of warcraft and flash player are used on all three. Two of the computers are working exceptionally, but the third has a locking problem. The computer locks up usually within 30 minutes of playing WoW or within a couple hours of my son playing on Noggin.com. The only real difference in the problem computer is it is using an LED monitor.

You didn't say, but we're assuming these are W500s?  You said "LED monitor" but presumably you meant LCD with an LED backlight?  I didn't realize that was an option in the W500 (are you in the right thread?)  In any case, if the computers are identical and the installs are identical, but one locks up... try swapping the hard drives around and see if the problem follows the hard drive or stays with the machine.

If the problem follows the hard drive, then you must have something installed differently on that one.  A quick fix (assuming the hardware truly is all identical) is to copy an image of one of the good drives onto the one exhibiting the problem).  Even in a laptop - especially a W500 - it is usually pretty straightforward to swap drives around different identical machines; you may want to consult Lenovo's online manuals for details on removing the drive, but usually they pop out of the bottom of the unit after removing a screw.

If the problem stays with the machine, then perhaps you have a hardware problem.  If these are laptops, as per this thread, then you'll need to contact Lenovo to get the bad one fixed or replaced.  If these were desktops you could try swapping other components around to isolate the bad component. (word of advice: if you get to the point of contacting Lenovo, (1) explain to them like you would a 3-year-old that the machines are identical, the installs are identical, and you've moved the drives around but the same machine keeps locking up, and (2) DO NOT MENTION YOU RUN LINUX; they may claim they do not "support" linux and take it as an excuse not to help you).  

Good luck.

---

### Post by quackeroni_pizza on 2009-01-10
Ok my bad, my screen is WSXGA+ so the 1680x1050 resolution is correct.

However, I still cannot figure out why Compiz won't work at that resolution. Basically, 1440-1680 pixels are just dark. I can move my mouse into the black portion and the card will briefly redraw the region when changing workspaces, but it eventually renders it dark.

I've attached a screenshot...

Here's the output in /var/log/Xorg.0.log
```

(II) Module fglrxdrm: vendor="FireGL - ATI Technologies Inc."
        compiled for 1.4.99.906, module version = 8.56.4
        ABI class: X.Org Server Extension, version 1.1
(--) fglrx(0): Chipset: "ATI Mobility Radeon HD 3650" (Chipset = 0x9591)

```

When I turn off desktop effects I can get a clean screen.

Thanks....

UPDATE: OK I must seriously start drinking more coffee.... I found out I was using imported Compiz settings from an older laptop which did the lower resolution!!!!! Seems like neither of my two problems were real issues after all :)

---

### Post by gatman3 on 2009-01-10
quackeroni,

That's pretty bizarre, I must agree.  I haven't seen that one yet.

So it only happens when compiz is enabled?  You're beyond my expertise, but maybe a few more thoughts just to give you some ideas.

I'm pretty sure that compiz uses direct rendering (DRI).  It almost seems like the DRI never got updated with the proper resolution.  What happens if you play a movie with mplayer in full screen mode using the xv driver (should be the default) without enabling compiz?  Does it occupy the same portion of the screen as what you observe with compiz enabled?  If so, then that would probably confirm some kind of DRI resolution problem, and then you might start googling in that direction.

You could also try experimenting with the xorg.conf.  If you haven't yet, try explicitly setting the resolution in xorg.conf.  You can also try changing the resolution with xrandr after you enable the desktop effects (do a "man xrandr" to get the options, but I think it's something like "xrandr -s 1680x1050").  You also still might try the AMD Catalyst Control Center (amdcccle) and try using it to set the resolution after enabling compiz.  I'm not exactly sure how amdcccle interacts with xorg, but you might find it does the trick.

EDIT:  Just read your first line again.  So did your UPDATE imply that the rest of your post was solved?  Not sure about the order of events there...

---

### Post by quackeroni_pizza on 2009-01-11
Yeah I guess I should've added the update at the end.. :P
It is lame that suspend/resume doesn't work yet..

---

### Post by petschni on 2009-02-02
Is there any solution for the problem with suspend/hibernate yet?

---

### Post by SeePU on 2009-02-02
You are using the fglrx driver on a mobile Radeon HD (ATI) 3650 GPU? 

I'm confused.  I thought that those weren't supported by the proprietary ATI driver.  Can anyone comment?  I was wondering which mobile ATI cards were supported by the proprietary ATI driver (i.e. fglrx driver?).

---

### Post by gatman3 on 2009-02-03
> **SeePU said:**
> You are using the fglrx driver on a mobile Radeon HD (ATI) 3650 GPU? 

I'm confused.  I thought that those weren't supported by the proprietary ATI driver.  Can anyone comment?  I was wondering which mobile ATI cards were supported by the proprietary ATI driver (i.e. fglrx driver?).

I can say for sure that the Radeon HD 3650 is supported by fglrx because that's what I'm using as I type this:

from lspci:

01:00.0 VGA compatible controller: ATI Technologies Inc Mobility Radeon HD 3650

from lsmod:

fglrx                2135688  31 


I get full 3D acceleration too, but only with fglrx not the open source drivers.  You'll have to do some research on fglrx to find out which cards are supported.  They keep releasing new versions of fglrx, too.  Try googling on fglrx.

---

### Post by gatman3 on 2009-02-03
> **petschni said:**
> Is there any solution for the problem with suspend/hibernate yet?

Don't know for sure, but...

I just noticed that on Jan. 29 ATI released a major update to the fglrx driver: Catalyst 9.1.  Here is a link to the release notes:

[http://www2.ati.com/drivers/linux/catalyst_91_linux.pdf](http://www2.ati.com/drivers/linux/catalyst_91_linux.pdf)

The release notes imply that there have been improvements in the wakeup from sleep functionality.  Also says it supports "multiview" now for multi-monitor configurations (I don't know what that is, but maybe it's ATI's answer to NVidia's "TwinView").  I don't have time right now to experiment, but it sounds promising.  I'll probably try it out in a few weeks.  If anybody else gets to it sooner, please share your results.

---

### Post by gatman3 on 2009-02-05
Good news... I think.

I just installed the Catalyst 9.1 driver:

[http://ati.amd.com/support/drivers/linux/linux-radeon.html](http://ati.amd.com/support/drivers/linux/linux-radeon.html)

And it looks promising to have fixed the suspend/hibernate issues.  I say "promising" because, unfortunately, I can't test it in conjunction with the compiz desktop effects at this time because my desktop effects broke after one of the updates that came through in the experimental repository (not sure which).  

(I had switched to the experimental repository so that I could upgrade to KDE 4.2.  That worked fine, and KDE 4.2 is way better than KDE 4.1.  For about a week everything worked great, including desktop effects... but I neglected to unselect the experimental repo, and I accepted some update which I think was to the xserver-xorg which broke desktop effects).

All that said... even though I don't have desktop effects working anymore, I'm pretty sure that is unrelated to the Catalyst 9.1 update.  But now I can suspend to RAM and resume, and mplayer with DRI (the xv driver) works after resume.  That's a MAJOR improvement.  I suspect that this will also fix suspend/hibernate with compiz as well, but I can't be certain because I can't test it.  I have also read mixed results from others with the new Catalyst 9.1 fixing video flickering when desktop effects are enabled, but for some it did the trick.  If I get the desktop effects working again I'll provide an update.

In general, I have observed that the Kubuntu 8.10 release was generally kind of screwed up - at least for the Lenovo W500 - owing to the Xorg deficiencies (lack of DRI2), the default for KDE 4.1 which was totally not ready for prime-time, broken bluetooth and the broken UVC webcam driver in the kernel.  Recent kernel updates fixed the UVC driver, AMD's Catalyst 9.1 update looks like a major improvement, kbluetooth4 is starting to come to life with recent updates in the experimental repo, and KDE 4.2 is out now.  It looks like all that mess is slowly getting sorted out, and I have to think that Ubuntu 9.04 will be much better.

---

### Post by gatman3 on 2009-02-05
Well, my desktop effects are magically working again.  I'm not even sure what I did to get them working, it just seems like I simply tried enabling them again.  The KDE splash screen at login disappears and reappears a couple times while the system services are starting up, which is disconcerting, but then everything seems stable once my desktop appears.  I tried several boot cycles and the system seems stable again with desktop effects enabled.

In any case, suspend/resume is still a no-go with the desktop effects enabled.  Bummer.

On the positive side, though, mplayer doesn't flicker with the desktop effects enabled.  That's an improvement, and I guess should be expected with Catalyst 9.1 because the release notes mention that being fixed.  The system freezes for a second or two when going into fullscreen video playback with desktop effects enabled, but it works.  I can zoom out the "cube" effect with video playing, but video plays back very sluggishly when zoomed out, maybe 1 frame per second.  I tried zooming out in fullscreen video, and it worked once, but the second time my system locked up hard.  So there are some limitations with video playback and desktop effects, although this is a major improvement.

So, it looks like Catalyst 9.1 is a big improvement, but still not the whole shebang.  Now you can have suspend/resume with DRI video playback... or you can have stable unflickering video playback with desktop effects enabled... but you can't combine the desktop effects with suspend/resume.  And beware of fullscreen video playback with desktop effects enabled.  Inches by inches...

---

### Post by geheimrat on 2009-02-06
I have found a discussion which pointed me to the [solution]("http://github.com/techarcana/fglrx-support/tree") for the resume problem. It is more a workaround than a bugfix. I am happy with these scripts. There are not problems on resume on my TP W500 with Ubuntu 8.10 until now.
Sven

---

### Post by petschni on 2009-02-06
@geheimrat: can you post the link to the discussion as well so we can find out what the workaround ist?

@gatman3: i created the ubuntu packages from the driver but when I wanted to install them the system told me that the packages were older than the ones already installed - is that normal?

---

### Post by gatman3 on 2009-02-07
> @gatman3: i created the ubuntu packages from the driver but when I wanted to install them the system told me that the packages were older than the ones already installed - is that normal?

Well, call me a brute, but I didn't bother packaging it, I just ran the installer and let it rip.  Regardless, I wouldn't have expected that, but I'm not a debian package expert so I wouldn't know how to debug that.

I have noticed that since installing the Catalyst 9.1 driver that my system now has trouble shutting down, even without desktop effects enabled.  I no longer get messages during shutdown, just a black screen, and then it hangs.  Usually I can nudge it along to an orderly shutdown by pressing the power switch briefly again at that point, but sometimes it locks hard at that point.  I also noticed that with desktop effects enabled, the system seems stable but a little sluggish.  Clearly there are some issues either with the 9.1 driver or with some of the other experimental updates I have installed recently.

Next step for me is to rebuild my 8.10 system from scratch, get only KDE 4.2 from the experimental repo, install the 9.1 driver... and see if things work any better.  Or maybe I'll just wait for 9.04 in a few months.

---

### Post by gatman3 on 2009-02-09
One more update on Catalyst 9.1 with the HD 3650 (Lenovo W500).

I reinstalled Kubuntu 8.10 (64 bit) on another partition, and I discovered that at least some of my problems must have been caused by upgrading to KDE 4.2 and/or other updates that came through the experimental repo.  From a clean install of 8.10, the 9.1 driver seems fairly stable.  The KDE 4.1 desktop effects work fine, although KDE 4.1 is definitely missing some niceties that I had briefly gotten accustomed to in KDE 4.2.  But, here are a few random observations:

- suspend-to-RAM worked 2 out of 3 attempts.  Better than before, but not reliable yet.
- mplayer can play videos without flicker, although I had one lockup in fullscreen mode out of maybe 3 attempts.
- Twice out of about 10 boots the desktop effects either didn't start (even though the box was checked in the Desktop settings page), or after some period of time they inexplicably just stopped working.

That's enough experimentation for me.  Now I just look forward with hope to the 9.04 release in a few months.

[EDIT]  Looks like suspend does work if KDE desktop effects are disabled, and mplayer even works after resume where previously it would lock the system up after resume (unless using the x11 driver).  However, I could not restore my wireless connection after resume.

Also - the fixes posted a few replies back by geheimrat look promising for compiz users but didn't work for me since I'm just using KDE4 desktop effects, not compiz.  Looks like scripts that disable compiz going into suspend and reenable after resume.  Maybe I'll switch from KDE4 desktop effects to real compiz and try it... although I also seem to have wi-fi problems after resume.

What a mess.

---

### Post by Bashar &quot; on 2009-02-22
I bought DisplayPort->VGA converter couple of months ago and working just fine till two days ago ubuntu upgraded itself and it stopped working for some reason

during boot it works just fine whenever it comes to X it doesn't display anything and even FN + F7 (im using thinkpad W500) it doesn't switch

i think the problem is with FN + F7 that switch between screens because even the normal VGA cable of the monitor when i connect it and hit FN+F7 it doesn't switch between screens like it used todo (before the auto-upgrade)

any advise?

Thank you.

---

### Post by archer6 on 2009-03-09
> **gatman3 said:**
> I just wanted to share some info about running Ubuntu on a Lenovo ThinkPad W500.<snip>
Thank You for your comprehensive reports. I have just purchased a W500 of the exactly same configuration as yours and find the info you have included very valuable. Thanks again for this great contribution. 

Cheers...

---

### Post by quackeroni_pizza on 2009-03-31
Which specific catalyst driver are you folks using? I don't see any listing on the ATI website for the HD3650 on 64-bit Linux.

---

### Post by gatman3 on 2009-04-02
The primary link is:

[http://support.amd.com/us/gpudownload/Pages/index.aspx](http://support.amd.com/us/gpudownload/Pages/index.aspx)

and then when I go through their menu to select the driver version, I select linux x86_64->Radeon->ATI Radeon HD 3xxx Series, although I think they may all end in the same place (don't really know, haven't tried all choices).  That link is:

[http://support.amd.com/us/gpudownload/linux/Pages/radeon_linux.aspx?type=2.4.1&product=2.4.1.3.5&lang=English](http://support.amd.com/us/gpudownload/linux/Pages/radeon_linux.aspx?type=2.4.1&product=2.4.1.3.5&lang=English)

The release notes list "ATI Radeon HD 3600 Series" as supported.  And... it seems to work under 64-bit Kubuntu 8.10, at least for me.

FYI, even on 9.1, I have found that suspend-to-RAM now works reliably, although playing movies with mplayer after resuming still causes a major lock-up.  This may have been fixed in 9.2 or 9.3; I seem to remember reading something in the release notes for one of those versions about that, but I haven't tested it yet.

Also note - I had serious problems once trying to upgrade fglrx verions without first uninstalling my existing driver.  If you are upgrading, I think the best thing to do is log into an F1 console as root, uninstall the existing fglrx driver (all debs), then install the new ones, then reboot.

---

### Post by gatman3 on 2009-04-02
FYI, I got off the dime and went and installed the ATI version 9.3 fglrx driver this morning.  It appears to solve two outstanding problems with previous drivers, as their release notes suggest.  The first problem was video playback after resume from suspend (S3/S4 suspend/hibernate).  That used to cause hard lock-ups, and now it seems to work fine.  The second problem was that X would die after logging out of Ubuntu and you'd get dumped to a console login.  I verified that I can now successfully log out and back in, and X keeps working throughout.

The way I upgraded, which may be overly paranoid, was to first download the driver and build the packages:

```
sudo ./ati-driver-installer-9-3-x86.x86_64.run --buildpkg Ubuntu/8.10
```

This produces 6 .deb files:

fglrx-amdcccle_8.593-0ubuntu1_amd64.deb
fglrx-kernel-source_8.593-0ubuntu1_amd64.deb
fglrx-modaliases_8.593-0ubuntu1_amd64.deb
libamdxvba1_8.593-0ubuntu1_amd64.deb
xorg-driver-fglrx_8.593-0ubuntu1_amd64.deb
xorg-driver-fglrx-dev_8.593-0ubuntu1_amd64.deb

Then - and this may be overly paranoid, but again I recall having serious problems upgrading a previous driver version without first uninstalling the one that was already installed - I killed X (rebooted, since the system would kernel panic for me when killing X with my previous driver) and from a console login as root:

```
dpkg -r fglrx-amdcccle_8.573-0ubuntu1
dpkg -r fglrx-kernel-source_8.573-0ubuntu1
dpkg -r fglrx-modaliases_8.573-0ubuntu1
dpkg -r libamdxvba1_8.573-0ubuntu1
dpkg -r xorg-driver-fglrx_8.573-0ubuntu1
dpkg -r xorg-driver-fglrx-dev_8.573-0ubuntu1

```

(my previous installed version was 9.1, which is version number 8.573)

And then to install the 9.3 driver:

```
dpkg -i fglrx-amdcccle_8.593-0ubuntu1_amd64.deb
dpkg -i fglrx-kernel-source_8.593-0ubuntu1_amd64.deb
dpkg -i fglrx-modaliases_8.593-0ubuntu1_amd64.deb
dpkg -i libamdxvba1_8.593-0ubuntu1_amd64.deb
dpkg -i xorg-driver-fglrx_8.593-0ubuntu1_amd64.deb
dpkg -i xorg-driver-fglrx-dev_8.593-0ubuntu1_amd64.deb
```

You can *probably* get away with skipping the uninstall step because the packages are supposed to uninstall any older version during the install step, but I would at least recommend doing this with X killed.

Then I rebooted, and - voila - video playback works after suspend/resume, and X doesn't die after logouts.

It's good to see continued improvement by the ATI driver for the HD3650 chipset.  In my opinion, fglrx is clearly the way to go for the W500 / HD3650, assuming you have no major philosophical problems with closed-source drivers.

---

### Post by quackeroni_pizza on 2009-04-02
Thanks.. I installed the new Catalyst driver. I am still having trouble with suspend.. I get some weird "bt_usb submission failed messages" when I hit suspend. The computer enters suspend mode but never manages to resume...  Hibernate is hopelessly messed up. If I remove the ATI driver, both resume and hibernate work just fine.

---

### Post by gatman3 on 2009-04-04
Bummer.  Sounds like a bluetooth driver problem.  I know that on my system bluetooth is the one thing at this point that crashes after resume from suspend/hibernate.

You might try killing/removing the bluetooth driver and attempting suspend/resume to see if that is the source of the problem.

Also... make sure you have compiz and/or kwin desktop effects disabled.  I haven't tried in a while, but they used to cause major problems with suspend/resume as well.

Good luck.

---

### Post by quackeroni_pizza on 2009-04-17
Desktop effects seem to have no difference on suspend/hibernate behavior with the ATI driver. Will look into Bluetooth driver soon...

Has anyone recently tried Jaunty on this machine? Last time I tried I had serious display driver problems, but that was months ago...

---

### Post by rcmn on 2009-04-17
I have been running the kubuntu version of jaunty for about 3 to 4 weeks now. I did not notice any video issues. It actually fixed some of the problem i had.

---

### Post by quackeroni_pizza on 2009-04-17
Ahh.. excellent...

Are you using it with the proprietary ATI drivers?

---

### Post by rcmn on 2009-04-17
> **quackeroni_pizza said:**
> Ahh.. excellent...

Are you using it with the proprietary ATI drivers?

yes

---

### Post by quackeroni_pizza on 2009-04-23
I tried upgrading from Intrepid to Jaunty and am no entirely happy.

1. Upgrade over existing install
When upgrading from within Intrepid (update-manager -d), I could not get the display to work.. just got a bunch of weird colored lines...probably some incorrect resolution. I had to uninstall the proprietary drivers from a different/older kernel to get the display working again..

2. Fresh install
However, startup/shutdown performance was terrible so I did a fresh install.. Now things are mostly working as before except the UI feels slightly sluggish (using catalyst driver 8.6 and 9.4). 

Other misc. issues-
When I shutdown, the screen goes blank without the computer actually shutting down. A cursor continues to blink waiting for something to happen. A Ctrl-Alt-Del at this stage coaxes the computer to reboot from this hung state. 

With the latest ati fglrx driver (and desktop effects enabled), suspend and resume return into a weird state with colored lines offset all over the screen... atleast it doesn't drop into a shell now if thats any consolation... just the resolution on wakeup seems messed up:)

UPDATE: I disabled Compiz effects, the UI feels much smoother... and both resume and update are working!

---

### Post by gatman3 on 2009-04-26
Well, you're not alone in your frustration.  I just spent the last few hours wrestling with a fresh 9.04 install on this W500.

My observations so far:


1. Don't make the hare-brained move I did and try to install the same ATI fglrx 9.4 driver packages that you might have laying around from your previous ubuntu 8.10 installation.  BIG mistake.  X wouldn't start, just left random pixels in a band across the top of the screen.  That cost me an hour or two just trying to get X up and running again with the open-source ati driver.  Even after I uninstalled them and built new ones using the --buildpkg option for Ubuntu/jaunty, it still didn't work.


2. Eventually I used the method here:

[http://wiki.cchtml.com/index.php/Ubuntu_Jaunty_Installation_Guide#Restricted_Drivers_Manager](http://wiki.cchtml.com/index.php/Ubuntu_Jaunty_Installation_Guide#Restricted_Drivers_Manager)

and finally enjoyed some success.


3. With desktop effects enabled I see the exact same sluggishness as you, quackeroni.  Kind of a bummer.  I feel like we've been here before, though, with an older ATI driver from 3 or 4 months ago.  But with desktop effects disabled the performance seems actually much faster than with 8.10 (especially noticeable when zooming firefox with ctrl+ and ctrl-)


4. Bluetooth seems to have gotten some TLC for this release, although I have still seen some weirdness.  Bluetooth was completely hosed in KDE in 8.10, and I had to drop back to legacy bluetooth apps.  Oddly, for the first half dozen boots before I started messing with fglrx my bluetooth mouse synced up automatically (the holy grail).  After messing with fglrx, it now doesn't sync automatically at boot up, and I have to delete and add the device again to get it working.  Weird.  Still experimenting...


5. Seems like some good improvements to KDE4.  I was really close to dumping Kubuntu because of how bad 8.10 was with KDE4.  I think it might actually be usable now.


6. Searching for packages in both adept and synaptic is hosed for me.  This is really weird, but when I search for a package in either package manager I only get a small subset of the available packages.  I have actually had to just page up and down through the complete list in synaptic to find desired packages.  In fact, I couldn't load synaptic from adept, leaving me completely crippled because adept couldn't find hardly any packages, and ultimately I had to just do an "apt-get install synaptic" from the command line.  Very weird, still investigating.


7. knetworkmanager is gone and is replaced by a new plasma widget called "Network Management".  That threw me for a while, because somehow I accidentally deleted the widget off my taskbar, and then I was lost in the woods without a compass.  Eventually I figured it out and added another one to my taskbar.  In the end, the interface on it seems nice compared with the klunky knetworkmanager.


That's as far as I have gotten.  Every new ubuntu release has proven to be a wild adventure, and jaunty is certainly no exception.


EDIT: Forgot to mention, I also was experiencing hangs on shutdown and suspend/resume, but after getting fglrx working it finally shuts down OK.  Haven't tried suspend yet.

---

### Post by gatman3 on 2009-04-26
I found a fix for my bluetooth mouse (logitech v470).

It appears that kbluetooth4 has a bug related to remembering whether a mouse is a trusted device.  I found a reference here:

[http://bbs.archlinux.org/viewtopic.php?id=65237&p=3](http://bbs.archlinux.org/viewtopic.php?id=65237&p=3)

that suggests a workaround that involves creating a "trusted" file down in the /var/lib/bluetooth tree.  That didn't work for me.

However, I found that after a suspend/resume cycle (which works, by the way) I received a new popup window telling me that my mouse wanted access, and it asked me whether I always wanted to trust that device.  After clicking "always trust", it seems fixed again.  It has persisted for two reboots, at least.

---

### Post by stalet on 2009-05-09
Im using 9.04 with desktop effects off to make suspend/hibernate work.
Ive tried lots of different configurations with the composite turned on and off to make it work so i could suspend with compiz.

Now it seems that ive gotten into configuration hell with my xorg.conf file, and cant configure it to wake from suspend / hibernate at all - even with compiz turned off.

Could someone with working suspend / hibernate post the content of their xorg.conf file ?

Regards,
-Ståle

---

### Post by gatman3 on 2009-05-10
Here is my xorg.conf.  I believe this is more or less an unmodified out-of-the-box xorg.conf for the W500 running Kubuntu 9.04.  I may have made minor edits on the depth and/or DPMS sections, don't recall for sure, but in any case this is pretty basic:

```
Section "ServerLayout"
        Identifier     "aticonfig Layout"
        Screen      0  "aticonfig-Screen[0]-0" 0 0
EndSection

Section "Files"
EndSection

Section "Module"
EndSection

Section "Monitor"
        Identifier   "aticonfig-Monitor[0]-0"
        Option      "VendorName" "ATI Proprietary Driver"
        Option      "ModelName" "Generic Autodetecting Monitor"
        Option      "DPMS" "true"
EndSection

Section "Device"
        Identifier  "aticonfig-Device[0]-0"
        Driver      "fglrx"
        BusID       "PCI:1:0:0"
EndSection

Section "Screen"
        Identifier "aticonfig-Screen[0]-0"
        Device     "aticonfig-Device[0]-0"
        Monitor    "aticonfig-Monitor[0]-0"
        DefaultDepth     24
        SubSection "Display"
                Viewport   0 0
                Depth     24
        EndSubSection
EndSection

```

(stripped the comments...)

---

### Post by stalet on 2009-05-13
Thanks, but it didn't help :(. It seems that the old configuration I had that _was_ working - only did work sometimes. I could have 2 or 3 good suspends - but on the third it didnt wake up...

With the configuration that you posted it never woke up.

Maybe the specs on the machines are a bit different.
I got the NRB3VMN machine with 2.93 GHz and 320GB disk. The BIOS version installed is 2.07-1.01.
I tried to update it to 3.00-1.03, but that didnt have any effect.

When using the intel card however suspend/hibernate works like a charm. Even with desktop effects enabled. 

Ill keep investigating...

---

### Post by gatman3 on 2009-05-14
stalet -

Sorry, brain fart.  For some reason I thought you were having trouble getting X to just start.  Reread and saw that you are working on suspend/hibernate.  Different story.  I guess I need more sleep.

Here's a brief history of my sordid graphics and suspend/hibernate experiences with the W500.

I first loaded 8.10 on my W500.  The fglrx version shipped with 8.10 was a mess.  Suspend/hibernate did not work, can't remember if compiz worked, but mplayer direct rendering had problems (flickering).  It was a mess.

I updated with the raw driver released each month from ATI's website, and around about driver version 8.12 or 9.1 I started to see major improvements.  By the time I hit 9.03 or so, I had compiz plus suspend/hibernate about 95% reliable.  Still problems with mplayer following a resume, though, but it worked good without suspending.

Then I loaded Ubuntu 9.04, and everything went to hell.  With compiz enabled there is major lag when doing things like resizing windows.  Suspend and hibernate just plain don't work.  Problem is, 9.04 solves several other problems like the completely hosed bluetooth stack in 8.10 (I think that's kernel related).  So I'm reluctant to go back to 8.10, but W500 graphics sure is hosed in 9.04.  I also have periodic hard locks... sometimes kernel panics with the flashing capslock, sometimes not... and I also have various screen redraw problems.  The hard locks usually occur after shutting the lid for a while without suspending.  The hard locks without warning are a total dealbreaker.  Bottom line, Ubuntu 9.04, in my opinion, is totally hosed for the W500.

When I get some time I am going to try a clean install of 9.04 and see if it may be something I screwed up in my fiddling.  Otherwise I may just drop back to 8.10 and live with the bluetooth problems.  Bluetooth is rock solid in 9.04, by the way.  Graphics is, kind of, more important though.

(As an aside, I must confess that I haven't been very impressed with the last two ubuntu releases.  May just be isolated to the W500, who knows, but I don't remember the releases prior to 8.10 being so sloppy with my older machines).

---

### Post by stalet on 2009-05-15
Thanks gatman. The problems you are describing are the same ones i have. Im getting hard freeze which the only way out of is to hold the power button down for 5 seconds. Sometimes it freezes with so i can do the SysRq magic and it reboots.

I got the suspend/hibernate working again by removing all radeon, radeonhd drivers and reinstalling the mesa drivers cleanly. So now it works without compiz - but is no way reliable. 
I also tried to kill compiz in a script in /etc/acpi/suspend.d/ and enabling metacity again - but the computer froze on resume every time.

My compiz effects are also laggy. When minimizing or resizing a window - there is a lag for a second. Ive seen registered bugs for this - seems its like that for all ati cards on 9.04. So i guess i can't configure my way out of that one. The intel card does not have this problem but it is getting kinda slow when using the machine for a few hours.

Previously to this i tried to use fedora 10 on the machine. I had lots of bugs there too and i couldn't use the intel driver either out of the box. But when i finally got everything working on it - it started to kernel panic every now and again... it got so unstable that i went for ubuntu.

Now im unsure if im going to proceede with this. Maybe ill just use the intel driver until things has been fixed for the ati.

---

### Post by gatman3 on 2009-05-16
stalet,

After some research, it appears that the problems we are facing are well documented and active in the ubuntu bug database.  It appears that there are several bugs in play here.  Reference these links:

[http://www.phoronix.com/forums/showthread.php?t=16632](http://www.phoronix.com/forums/showthread.php?t=16632)
[https://bugs.launchpad.net/ubuntu/+source/fglrx-installer/+bug/351186](https://bugs.launchpad.net/ubuntu/+source/fglrx-installer/+bug/351186)
[https://bugs.edge.launchpad.net/ubuntu/+source/fglrx-installer/+bug/372345](https://bugs.edge.launchpad.net/ubuntu/+source/fglrx-installer/+bug/372345)

My take is that an Xorg patch was applied to 8.10 after a few months, but that patch was rolled back again for 9.04 because it has negative side effects with intel graphics.  Sounds like a minor mess, because the patch covers a broader topic (Xorg) but has different results with specific driver sets (fglrx vs. intel).  That's probably why there hasn't been a fix update released yet.

Anyhow, for now you might want to go back to either the open source radeon driver or switch over to intel graphics, as you suggest.  With the open source driver you probably gain suspend/resume but you may lose compiz effects (3D accel) - although I'm not totally sure about that (I believe there have been recent improvements to the open source driver due to ATI/AMD releasing more docs).  I am considering doing the same.  Previously (6 months ago with 8.10) I was not able to get intel graphics to work with suspend/resume, but at least intel graphics burns substantially less power than ati graphics (see earlier posts in this thread).  Maybe fixes have been made to suspend/resume with intel since I tried; if you have success, please post!

Otherwise, I guess we wait for someone to fix this mess.

---

### Post by mdhirsch on 2009-05-17
> **gatman3 said:**
> Here is my xorg.conf.  I believe this is more or less an unmodified out-of-the-box xorg.conf for the W500 running Kubuntu 9.04.  I may have made minor edits on the depth and/or DPMS sections, don't recall for sure, but in any case this is pretty basic:


What resolution do you get?  I can get X to boot with this config, but it ends up in 1024x768.  It looks like it tries to start X 3 times, then gives up and switches to 1024x768.

Once I log in I can get full resolution with xrandr, but I haven't figured out how to get X to the right resolution in the initial startup.

I had no problems with intrepid.  It's just jaunty that is troublesome.

---

### Post by stalet on 2009-05-17
Good to see that someone is fixing this. Looking forward to a real resolvement here.

I just changed back to intel drivers and its all good.
Just logged on as root and ran this command:

dpkg -r fglrx-modaliases xorg-driver-fglrx fglrx-kernel-source libamdxvba1 xorg-driver-fglrx-dev fglrx-amdcccle

Then remove all lines in the xorg.conf file and reboot.
When booting i changed the BIOS setting to use the intel card.

I just did 3 ok suspends and a hibernate after the reboot. All with compiz running. No errors at all.
And this is with a zero configuration xorg.conf.

I guess im going to use it like this for now on - at least until I hear that the bugs are fixed.
Im thinking of making a script to autodetect the bios setting on boot and install / deinstall the ati driver. Shouldnt be that hard. Its nice I ive ever want to play an occasional game and use the ATI driver again. 

mdhirsch: I get 1920x1200 with the xorg.conf.

---

### Post by gatman3 on 2009-05-18
That's good news, stalet.  I am on your heels moving over to the intel driver.

mdhirsch - if all you can get is 1024x768, then I wonder if you aren't getting any driver loaded and it's falling back to vesa.  You should probably disregard my posted xorg.conf and search back for better info on getting the fglrx driver loaded... or one of the others.  Which graphics driver do you intend to use?  Gotta run, but if you're still having problems, post more, and I'll try to help later.

---

### Post by stalet on 2009-05-27
Have anyone tried the new ATI Catalyst™ Display Driver 9.5 ?

---

### Post by gatman3 on 2009-05-28
Yes.  I'm running the 9.5 driver now.  It works fine, except no improvement (for me) with suspend/resume or with the desktop effects bugs (slow resize, etc.)  The release notes don't mention anything about either topic, so I wasn't expecting progress anyway (not sure the desktop effects problems are really an fglrx issue anyway).

I went with intel graphics for a while, but since I use an external monitor and dock at work, and the intel graphics doesn't drive the external connectors, I ultimately had to switch back to ATI.

---

### Post by gatman3 on 2009-05-28
Also, I fixed my instabilities... somehow...  In short, I reinstalled Ubuntu 9.04.  But I did a few other things:  (1) switched back to ext3 from ext4, (2) stopped running skype, and (3) stopped using the xscreensaver.  Not sure which of those may have contributed to my instabilities, but I had some suspicions about #2 and #3 based on other research.  And I went away from ext4 just to remove one more major variable change since my 8.10 install.  Now my machine running Ubuntu 9.04 with the Catalyst 9.5 driver seems back to rock solid shape.  Too bad desktop effects and suspend/resume are still hosed, but at least bluetooth is solid (I use a Logitech bluetooth mouse).

Which brings me to another topic. The RADEON DRIVER IS DANGEROUS!  For a while I tried running ATI graphics with the radeon driver, and I noticed occasional hangs and even refusal to reboot.  Then I discovered that the bottom of the laptop gets absolutely SMOKING HOT when running the radeon driver.

After characterizing it some more, I found that at idle the /proc/acpi/thermal_zone/THM0 and THM1 readings were as high as 95 degrees C !!!  Given that I live at high altitude, I think that's about hot enough to boil water here.  The power consumption reported when running on battery is as high as 45W or 46W!  Compare that to fglrx in the 22W to 26W range, and something is really smoking when running the radeon driver.

Bottom line: DO NOT USE THE RADEON DRIVER WITH THIS LAPTOP, possibly with any ATI HD3650 card, and I worry that you may even damage your machine with it, or at least reduce the lifespan of various components (battery, drive, etc.)

If anyone else has other data on this topic, please share.

EDIT:  I forgot to mention that one way to get the radeon driver under control is to use the DynamicClocks option.  Do a "man radeon" and look for that option to get information.  This apparently does some clock throttling to get the power down.  In my experience it lowers the power with the radeon driver into the 34W to 36W range, so still burning pretty good but perhaps not the total meltdown you might experience with the out-of-the-box radeon settings.  I still see no reason to use the radeon driver unless you (1) need an external monitor, and (2) can't or won't use the proprietary fglrx driver.  I can't see any advantages that the radeon provides over intel graphics for mobile work or the fglrx driver for plugged-in work.

---

### Post by randomlyrandom on 2009-06-22
Hi,

I have installed Ubuntu 8.10 and trying dual monitor setup. My external monitor is of HP L1906 make whose max resolution support is for 1280x1024 @ 60 Hz. When I set this, the display on my monitor is blurr and eyes strain viewing the same. 

Did anyone face the same problem? Please let me know how to fix this. Copied below my Xorg and lspci output

xorg:
------

Section "ServerLayout"
	Identifier     "amdcccle Layout"
	Screen      0  "amdcccle-Screen[1]-0" 0 0
EndSection

Section "Files"
EndSection

Section "Module"
	Load  "glx"
EndSection

Section "ServerFlags"
	Option	    "Xinerama" "off"
EndSection

Section "Monitor"
	Identifier   "Configured Monitor"
EndSection

Section "Monitor"
	Identifier   "amdcccle-Monitor[1]-0"
	Option	    "VendorName" "ATI Proprietary Driver"
	Option	    "ModelName" "Generic Autodetecting Monitor"
	Option	    "DPMS" "true"
EndSection

Section "Device"
	Identifier  "Configured Video Device"
	Driver      "fglrx"
EndSection

Section "Device"
	Identifier  "amdcccle-Device[1]-0"
	Driver      "fglrx"
	BusID       "PCI:1:0:0"
EndSection

Section "Screen"
	Identifier "Default Screen"
	Device     "Configured Video Device"
	Monitor    "Configured Monitor"
	DefaultDepth     24
EndSection

Section "Screen"
	Identifier "amdcccle-Screen[1]-0"
	Device     "amdcccle-Device[1]-0"
	Monitor    "amdcccle-Monitor[1]-0"
	DefaultDepth     24
	SubSection "Display"
		Viewport   0 0
		Depth     24
	EndSubSection
EndSection

pnagral@pnagral-ubuntu:~$ lspci
00:00.0 Host bridge: Intel Corporation Mobile 4 Series Chipset Memory Controller Hub (rev 07)
00:01.0 PCI bridge: Intel Corporation Mobile 4 Series Chipset PCI Express Graphics Port (rev 07)
00:03.0 Communication controller: Intel Corporation Mobile 4 Series Chipset MEI Controller (rev 07)
00:03.2 IDE interface: Intel Corporation Mobile 4 Series Chipset PT IDER Controller (rev 07)
00:03.3 Serial controller: Intel Corporation Mobile 4 Series Chipset AMT SOL Redirection (rev 07)
00:19.0 Ethernet controller: Intel Corporation 82567LM Gigabit Network Connection (rev 03)
00:1a.0 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #4 (rev 03)
00:1a.1 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #5 (rev 03)
00:1a.2 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #6 (rev 03)
00:1a.7 USB Controller: Intel Corporation 82801I (ICH9 Family) USB2 EHCI Controller #2 (rev 03)
00:1b.0 Audio device: Intel Corporation 82801I (ICH9 Family) HD Audio Controller (rev 03)
00:1c.0 PCI bridge: Intel Corporation 82801I (ICH9 Family) PCI Express Port 1 (rev 03)
00:1c.1 PCI bridge: Intel Corporation 82801I (ICH9 Family) PCI Express Port 2 (rev 03)
00:1c.3 PCI bridge: Intel Corporation 82801I (ICH9 Family) PCI Express Port 4 (rev 03)
00:1c.4 PCI bridge: Intel Corporation 82801I (ICH9 Family) PCI Express Port 5 (rev 03)
00:1d.0 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #1 (rev 03)
00:1d.1 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #2 (rev 03)
00:1d.2 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #3 (rev 03)
00:1d.7 USB Controller: Intel Corporation 82801I (ICH9 Family) USB2 EHCI Controller #1 (rev 03)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev 93)
00:1f.0 ISA bridge: Intel Corporation ICH9M-E LPC Interface Controller (rev 03)
00:1f.2 SATA controller: Intel Corporation ICH9M/M-E SATA AHCI Controller (rev 03)
00:1f.3 SMBus: Intel Corporation 82801I (ICH9 Family) SMBus Controller (rev 03)
01:00.0 VGA compatible controller: ATI Technologies Inc Mobility Radeon HD 3650
03:00.0 Network controller: Intel Corporation Wireless WiFi Link 5100
15:00.0 CardBus bridge: Ricoh Co Ltd RL5c476 II (rev ba)
15:00.1 FireWire (IEEE 1394): Ricoh Co Ltd R5C832 IEEE 1394 Controller (rev 04)
15:00.2 SD Host controller: Ricoh Co Ltd R5C822 SD/SDIO/MMC/MS/MSPro Host Adapter (rev 21)
15:00.3 System peripheral: Ricoh Co Ltd R5C843 MMC Host Controller (rev ff)
15:00.4 System peripheral: Ricoh Co Ltd R5C592 Memory Stick Bus Host Adapter (rev 11)
15:00.5 System peripheral: Ricoh Co Ltd xD-Picture Card Controller (rev 11)


Please help me getting dual display up with this monitor.

Regards,
-P

---

### Post by gatman3 on 2009-06-22
Did you create that xorg.conf yourself, or did aticonfig do that for you?

Also, are you running two 1280x1024 external monitors, or are you using the integrated LCD as the primary with one external as the secondary?  Wasn't clear from your post.

I had good success in 8.10 using the amdcccle utility to set up dual monitor configurations.  Try running amdcccle and go to the display manager tab, and mess around with it.  I have only done it with two external monitors at the same resolution, however.  Not sure how well it works with two monitors running different resolutions.

You can also try "xrandr -q" to see what resolution it is trying to run at.  I'm not sure how useful xrandr is for setting up dual monitor configs, though.  By the time xrandr gets the resolution I think the damage has been done by fglrx.

If you are running 8.10, the fglrx driver provided with 8.10 is largely broken.  There have been many improvements in the fglrx driver in the 8 months or so since that driver was released with 8.10.  Try going to ATI's website and getting the latest 9.6 driver, which seems to work pretty good now.  Let us know if you need help installing it; it's pretty simple now, though.  I used the new --buildandinstallpkg option with good success.  After installing the new driver try the amdcccle utility to set up your dual monitors.

---

### Post by seinberg on 2009-06-24
I've been having a difficult time getting my W500 working in Ubuntu 9.04 too.  I tried the 9.6 drivers, but they seemed really sluggish (when I drag windows I see noticeable choppiness).  In addition, when I tried to use the GNome "Display" application to setup dual monitors, my machine's CPU would go crazy.  I think things might be slightly complicated by the fact that I'm using an Advanced Dock, though.  Has anybody got 9.04 and dual monitors working with the proprietary drivers using an Advanced Dock?

---

### Post by gatman3 on 2009-06-25
seinberg,

First of all, on the sluggishness.  Do you have desktop effects enabled?  If so, it sounds like you may be experiencing the bug related to Xorg/fglrx backfill interaction.  Check out this bug report:

[https://bugs.launchpad.net/ubuntu/+source/fglrx-installer/+bug/351186](https://bugs.launchpad.net/ubuntu/+source/fglrx-installer/+bug/351186)

As I understand it, this is a case of something that worked in Ubuntu 8.10, but in 9.04 they put some fix in for Intel cards that happens to hose up the fglrx driver, and it seems like there may be some fingerpointing going on between Xorg and ATI.  In any case, I finally gave up waiting for an update that fixes this, and I successfully got it fixed on my system by installing a version of Xorg that someone compiled for Ubuntu with backfill disabled.  To do this, I added the following lines at the end of my /etc/apt/sources.list:

```
# Xorg fix for window resize/minimize with desktop effects
deb http://ppa.launchpad.net/ubuntu-x-swat/xserver-no-backfill/ubuntu jaunty main
deb-src http://ppa.launchpad.net/ubuntu-x-swat/xserver-no-backfill/ubuntu jaunty main
```

And then run an update with your favorite package manager and pick up the new Xorg.  If this doesn't work and/or you need to revert, just remove those lines from the /etc/apt/sources.list and update again.

On dual monitors... I have used dual monitors with the advanced dock, but only with one running on DVI and the other on VGA; this is basically just a passthrough of the onboard graphics through the dock connectors.  Earlier in this thread I posted on the topic.  Note that the Advanced Dock does NOT support discrete graphics cards reliably, and Lenovo has taken all references to support for graphics cards off their website.

Assuming you are trying the mixed VGA/DVI option, which is the only one I could get to work, all I did was run the amdcccle utility and used it to configure the two monitors.  Make sure you start with an initial unmodified xorg.conf before running amdcccle.  There are ways to do it manually in your xorg.conf but I haven't had to do that in at least 6 months.  Unfortunately, I switched back to a single (larger) monitor more recently, so I don't actually have recent experience with the 9.6 driver with dual monitors.  Another thing you might try is dropping back to something like 9.1 or 9.2; I vaguely remember those drivers working sweet with dual monitors, and I don't think there have been any groundbreaking fixes in fglrx since then that you'll be missing out on.  Good luck.

---

### Post by wilburthemexican on 2009-07-16
Thanks GatMan3.  Installing the ppa xserver-xorg-core fixed the lagging compiz for me.  I was a little confused by your instructions, but I found the page for the patched package [https://launchpad.net/~ubuntu-x-swat/+archive/xserver-no-backfill](https://launchpad.net/~ubuntu-x-swat/+archive/xserver-no-backfill) which explains how to set up the repositories.  Also, in synaptic, I selected "mark for upgrade" on xserver-xorg-core to install the patched version.  After a reboot, the compiz effects are working with out lag.

I'm using the ati driver 9.6 for 64 bit.  To install, I deactivated the ubuntu fglrx propriety drivers in the System->Administration->Hardware Drivers dialogue.  

I downloaded the driver from [http://support.amd.com/us/gpudownload/Pages/index.aspx](http://support.amd.com/us/gpudownload/Pages/index.aspx) and selected my version which is Linux_x86_64->Radeon->ATI Radeon HD 3xxx series.  Then in the download directory i ran:
```
sh ./ati-driver-installer-9-5-x86.x86_64.run
```
This ran the gui installer and i chose the automatic installation options. After it finished with that, I ran
```
aticonfig --initial
```
rebooted and everything was great... Compiz works, no lag, etc.

Except, when I resume from sleep, I can log in, but then i just see the desktop background and I can move my mouse.  I'm don't know crazy kungfu death grip keycommands, but it seems unresponsive.  It sleeps/resumes fine with compiz disabled.  Any suggestion on this?

I'm running 9.04 on my w500.

---

### Post by stalet on 2009-08-20
Finally. It seems all our hopes has been answered. I just tried the new Catalyst 9.8 driver. It was stated in the catalyst blog that:

> 
This release of ATI Catalyst driver for Linux introduces support for the following new operating systems: 

    * RHEL 4.8 production support
    * Ubuntu 9.04 production support


And now suspend/hibernate works even with all dektop effects enabled.

wilburthemexican: this will fix your problem.

---

### Post by wilburthemexican on 2009-08-20
> **stalet said:**
> Finally. It seems all our hopes has been answered. I just tried the new Catalyst 9.8 driver. It was stated in the catalyst blog that:



And now suspend/hibernate works even with all dektop effects enabled.

wilburthemexican: this will fix your problem.

AWESOME.  It works, resume and all! My process for all those that follow...
uninstall old proprietary drivers

```
$ cd /usr/share/ati
$ sudo sh fglrx-uninstall.sh 
```

reboot
download new driver, run these command in the download directory

```
$ sudo sh ati-driver-installer-9-8-x86.x86_64.run --buildandinstallpkg Ubuntu/9.04
```

reboot and it worked.

Thanks so much stalet

---

### Post by gatman3 on 2009-08-21
Thanks for sharing that, stalet and wilbur.  I updated to the 9.8 driver as well and have seen good improvement.  Here are my results:

Suspend-to-RAM seems reliable now.  I saw 5 consecutive successful suspend/resume cycles with desktop effects enabled.  It's FAST, too.  I didn't time it, but it seems like it takes about 3 seconds to suspend and the same to resume.  Only weirdness is that twice out of the 5 resume cycles I got a pop-up window telling me that compositing had been disabled because it was running too slow, but re-enabling with alt-shift-F12 - as the pop-up suggested - worked fine.  Kind of weird.  Based on all of our scars from past drivers, I'm not declaring victory until I see about 100 successful suspend/resume cycles.  But it looks like the most promising attempt by ATI yet.

Hibernate... not so much.  Maybe I'm asking too much.  After my 5 successful suspend/resume cycles I tried hibernate just for grins (I really don't care about hibernate functionality too much, but I was curious to see just how good the new driver is).  It hibernated just fine.  Took a while, but it eventually got itself all shut down.  On resume, it took its sweet time but eventually came up successfully.  Spent a long time sitting there with a black screen hitting the drive, but eventually it repainted the mouse cursor and eventually the whole desktop.  Then I had about 5 seconds of functionality, and then WHAM, kernel panic with flashing caps-lock.

But suspend looks good.  So far.  That's all I really care about anyway.

Thanks again for sharing!

---

### Post by parszab on 2009-08-28
Hi!

A superb thread, great community here! I plan to buy a w500 mainly for software development work, and generic stuff, nothing 3D related. I would turn compiz of, too, it makes me nauseated somehow! :)

I'd like to ask from gatman3, what setup would you suggest for this scenario? To be honest I got a bit confused, that you wrote, the Radeon driver was dangerous, later you mentioned using it, though. Or was that only a test?

So what I need is stable and fast 2D performance, low power consumption. Should I use the fglrx or the radeon driver? Or neither, but the integrated card?

Thanks in advance!
parszab

---

### Post by gatman3 on 2009-08-29
Welcome parszab.  Yes, it is a great community.

The W500 is an excellent machine for software development.  It is certainly one of the most capable notebooks available.  Here are some random thoughts to summarize my experiences:

- The radeon driver is not recommended because, in my experience, it doesn't throttle power very well and the machine runs very hot.  Probably bad for long term reliability.  (This may improve at any time, though, as there is active development on the radeon driver).

- Do you plan to use an external monitor?  If so you will need to run fglrx because the integrated intel graphics does not drive the external interfaces (hmmm... I'm certain that's true of the DVI output, and I'm pretty sure that's true for the VGA as well).  Furthermore, you can go dual monitor with one running VGA and the other DVI, but you can not get two DVI monitors with the W500 (one of the drawbacks of the machine).  If you don't have a docking station, you will need a DisplayPort->DVI adapter (should be cheap though).

- If not using an external monitor... I would recommend the intel driver.  You say that you only need modest 2D acceleration and no 3D.  Then probably go with intel.  You'll have to judge for yourself if the 2D is acceptable, but it probably is for you.  Battery life is best with intel, and the machine runs very cool.

- With the latest Xorg releases, if you install the fglrx driver then Xorg should auto-select between intel and fglrx when you boot up depending on how you set the BIOS config option in the display setting pages (I think it's "integrated" for the intel chip and "discrete" for the ATI chip, or something like that).  Note that no one has gotten on-the-fly switchable graphics working; there seems to be some special sauce required that they have only integrated in with Windows.

- I have had stability problems with a bluetooth mouse.  For development work, consider getting a good Logitech laser mouse with the nano receiver, so that you can leave it in all the time.  I love the feel of the V550, but the V450 is pretty good too but a little lighter.  Lots of ongoing development on bluetooth, though, so maybe it will improve with the next ubuntu release, don't know.

- Have you purchased the machine yet?  If not, a few options worth considering:

1. The 1920x1200 monitor option is excellent for development work because you can obviously fit a lot more edit windows on the screen at once.  Only drawback: it's a little on the dim side.  Note also that it gets better after it warms up for a few minutes.

2. The webcam works great out-of-the-box with Ubuntu.

3. The fingerprint reader has little or no support in linux.

4. Firewire works great in linux.

5. The 5100 wi-fi adapter works great in linux.  Don't know about the other options.

6. The docking station decidedly does NOT support an external video card (major bummer).  Lenovo dropped the ball on this one.  For a while they made it seem like you could use an external video card, but then they removed all references to it on their web site.  I tried several options with the advanced dock but couldn't get anything to work reliably (once or twice I actually got the external card to display boot-up text, but that's about it).

7. Haven't been able to get live dock/undock to work either.  Hangs the system under linux.

8. Build quality is excellent, although the lid picks up fingerprints easily.

One other machine to consider in the same class as the W500 would be the Dell M4400.  It DOES support dual DVI external monitors and has a brighter built-in display (LED backlight option, I think); otherwise the W500 is overall probably a better machine (personally I've had bad experiences with Dell/Compal build quality - although I don't know if the M4400 is a Compal machine or some other notebook ODM - and the M4400 is supposedly a little noisy compared with the quiet-as-a-mouse W500, so it probably runs a little hotter or just has a cheaper cooling subsystem).  Caution, though, because I have no idea how well Linux is supported on the M4400 hardware, although I believe it does have NVidia graphics which is generally well supported in Linux.  Proceed at your own risk, although for a hardcore development machine it is certainly an option worth considering.

---

### Post by Bashar &quot; on 2009-08-30
> **wilburthemexican said:**
> AWESOME.  It works, resume and all! My process for all those that follow...
uninstall old proprietary drivers

```
$ cd /usr/share/ati
$ sudo sh fglrx-uninstall.sh 
```

reboot
download new driver, run these command in the download directory

```
$ sudo sh ati-driver-installer-9-8-x86.x86_64.run --buildandinstallpkg Ubuntu/9.04
```

reboot and it worked.

Thanks so much stalet

worked for me too

Thanks !

---

### Post by stalet on 2009-08-31
The intel driver works with an external video on the VGA output. (I havent tried the dvi output tho). But running my w500 on a videocanon for å keynote using the intel driver works fine. 

If you are looking for a stable resume/suspend i would recommend using the intel driver. I am having problems with resuming from sleep every once in a while using the ati card - and im pretty sure its the driver since im not having problems with the same setup and the intel driver. 

After started using the ati driver after some time using the intel driver - i noticed that the whole machine seems faster. It might be that when using the ati driver it got more responsive. At least when using a IDE and compiling programs in the background - it is still quite responsive. So if you can afford having to hard boot the machine every once in a while - I would definitely go for the ATI driver.

Im hoping for another update to the fglrx driver - to get rid of the last resume bugs...

---

### Post by parszab on 2009-09-02
Thanks a lot for the many details gatman3! Very much appreciated! I haven't yet purchased the mcahine, but see myself doing it very soon. :)

To be honest, the only things I miss form this almost perfect notebook is the regular TV-out or S-video port and very sadly: the e-sata port.

Hope the latter will be a must in forthcoming designs.

---

### Post by Zebra Lord on 2009-09-11
I attempted to install Ubuntu 8.10 64 bit on my new W500.  Everything was going good until it began partitioning the disk.  It went up to 5% and then the computer became non-responsive.  The only thing happening is that the Caplock indicator light is blinking.  What should I do to not risk screwing up my HD?  I am relatively a beginner to linux so please try to simplify things.  By the way, you guys are doing a great job on this forum and it has really helped me out in the past.  Thanks for the help!

---

### Post by gatman3 on 2009-09-11
Yikes.  Flashing capslock means kernel panic, and there's nothing you can do except power cycle the machine.  Did you have other OSes on other partitions that you don't want corrupted?  Or are you partitioning from scratch and are just worried about damaging your hardware or something?

I haven't tried it in many years, but it used to be that if you were repartitioning a drive with an existing OS on it, you needed a utility like Partition Magic to shrink existing partitions and create new ones without (hopefully) destroying data on the existing ones.

If you don't care about the data on the drive, then just power cycle it and try again.  If it locks up the same way you may need some special boot options when you start the linux installer, though I have no idea what they may be.  It would be odd since the W500 seems to work for most people quite well with the out-of-the-box Ubuntu 9.04 distro and no special boot options (like noapic or nolapic; I think newer machines like the W500 generally don't require those workarounds).

Or you could have some faulty hardware, perhaps your drive is malfunctioning.  You could try a surface scan utility.  I can't remember what diagnostic tools are available in the BIOS config pages, may be just a memory test... or nothing at all, but it's worth a look.

Good luck, let us know how it goes.

---

### Post by jvdurme on 2009-10-29
Hi all,

nice to see this topic on the forums!
Just got a W500 with ATI HD3650 video driver on 9.04 Jaunty.

Here are some experiences:

**ATI 3650 HD**
After trying to install a fresh copy of Ubuntu 8.04, which was very reluctant in giving me X, I installed** 9.04 Jaunty** and X worked fine!
For the 3D stuff I googled some and found out about the BIOS Discrete settings. glxgears gave me a stunning 3500FPS on 1920x1200. But because I find this too small for my poor eyes I had to reset to 1440x900, with a drop of glxgears to 1500FPS on average.
Using the latest ATI fglrx driver (8.661) which is in the Catalyst 9.10 package.
3D rendering is great. I'm often viewing molecules in 3D and it it flawless and smooth.

I work with dual head setup at work. Now this was a pain to get it configured.
But it worked (both with and without Xinerama). If anyone is interested in a working xorg.conf file for dual head, just PM me.
The only crap is that suspend/hibernate won't wake up when the external screen is **dis**connected. I use the option SwapScreen (in xorg.conf) and perhaps it is trying to detect the external screen. I really don't know ...

Another funny thing is the mouse with dual screens. When I connect a USB mouse, the pointer can hover from one screen to the other. But when I use the touchpad, when I move the pointer from the primary screen to the secondary, it is trapped on the secondary screen. It won't go back to the first screen. I can untrap it with the USB mouse though. Funny huh? :)

A very good wiki for ATI driver installation, upgrades, etc for Ubuntu can be found at [http://wiki.cchtml.com/index.php/Ubuntu](http://wiki.cchtml.com/index.php/Ubuntu)

[B]Wireless
[/B]Out of the box! Wow, what a relief! In 8.04 I was constrained to the nasty ndiswrapper. Now it's a piece of cake. Just like that.

**Fingerprint reader**
I saw instructions on thinkwiki.org but it's so exhaustive that I immediately gave up.

[B]LCD
[/B]Not as bright as I hoped for, but solid.

**Cover and design**
Fingerprints can indeed easily be seen on the lid, but also under the keyboard fingerprints are easily there (but also easy to clean). 
All USB slots are on the left hand side of the machine, which is annoying for me since I'm right-handed. The mouse cord is just too short.

I'll add some more stuff when it comes to mind.

Cheers to all Thinkers!

---

### Post by quackeroni_pizza on 2009-11-03
I can report a flawless upgrade to Karmic on the W500...  No issues at all... Significantly snappier GUI... So much better than Jaunty... among other niceties... Good luck!

---

### Post by gatman3 on 2009-11-07
I have had a good experience too, for me with a clean install.

Pros:

- Bluetooth mouse is now completely stable, no kernel panics.
- Suspend to RAM is completely reliable with intel graphics.
- Boot time is about 10 to 15 seconds.  (!)
- Machine seems to run a little cooler (3 to 5 deg C).

Cons:

- With ATI graphics (fglrx driver) I still can't suspend/hibernate.
- Xorg/fglrx still has the slow window placement/resize problem, with or without desktop effects enabled.  On 9.04 I had to install a hacked Xorg that disabled backing store (?) to fix this.  Haven't gotten that far yet with 9.10, but it's still broken.  I seem to recall some finger pointing between ATI/AMD and Xorg on this.

I've been running with intel graphics and the experience is excellent.  Although, I'm not using an external monitor (no DVI with intel, only VGA) and I'm not using desktop effects (intel graphics too slow for it).  But having suspend-to-RAM working reliably is downright awesome.  After a resume, the networking comes up properly and even the bluetooth mouse comes back on resume (almost every time; I've had one occasion after about 40 suspends where I lost my bluetooth stack on resume).

Really coming along.

---

### Post by stalet on 2009-11-08
I did an upgrade to karmic from jaunty last weekend. Ive tested suspend several time a day pretty much every day since then without errors using the ATI card. 
The only thing ive noticed so far is that sometimes it may be pretty slow. Ive found out that it is mostly the flashplayer within firefox that pretty much stops the machine after resume - but its only sometimes - and it still works (its just slow - like a minute or two).


I did the xserver update to the karmic xerver-nobackfill as noted here:
[https://launchpad.net/~launchpad-weyland/+archive/xserver-nobackfill](https://launchpad.net/~launchpad-weyland/+archive/xserver-nobackfill)
This fixed the resize problem.


And I am using the 9.10 version of the fglrx driver.
It works great with compiz and emerald enabled.
So like gatman says: its really comming along :)

-S

---

### Post by stalet on 2009-11-10
Well its not completely stable yet. Yesterday it didn't wake up from sleep..](*,). I'm not really sure why though.

-S

---

### Post by gatman3 on 2009-11-11
stalet - my guess is fglrx caused your wakeup problem.  If so, that's a bummer, I'm planning to switch back from intel to fglrx soon because the intel graphics are marginal.  But with intel I still have not seen it ever fail to wake up from sleep, probably over 100 cycles now.  I do see the bluetooth stack (my poor mouse) crash about every 6 or 8 sleep cycles, but that's it for me so far.

---

### Post by wimvanleuven on 2009-12-23
Hello everybody,

wonderful to come across this thread of proud owners of such a wonderful piece of technology: Lenovo W500. Great machine!

My journey into Ubuntu on the W500 is quite painful. I started with the Karmic 64-bits version. Installation was flawless ... at moderate resolution. Trying to get the resolution WUXGA I bought this system for, was however painfull, long and tedious. 

I'm at the point I'm running Karmic, ATI Catalist 9.11 at 1920x1200 with Compiz. 

However, periodically the system just freezes. Hard reboot only solution. The freeze happens all the time when dragging windows around the desktop! Anybody experienced this? Possible solutions? Workarounds?

Thanks in advance,
wim

---

### Post by gatman3 on 2009-12-23
Welcome wimvanleuven!  Gosh, very sorry to hear about your trouble.  I am presently running 64-bit Kubuntu 9.10 without such lockups, so be encouraged that it is possible!

Can you elaborate a little more on any additional out-of-the-ordinary devices you might be using?  For what it's worth, I experienced frequent lockups with 9.04 when using a bluetooth mouse.  Linux lockups are more often than not due to device driver problems.

Here's what I would do to try to isolate this.  Simplify as much as possible and see if you still have lockups.

1.  Drop back to the intel driver.  To do this, enter the BIOS config menus and make sure the "integrated" graphics are selected.

2. Make sure that compiz is not enabled.  It won't work very well with the intel driver anyway.

3. Are you using a wireless and/or bluetooth mouse?  Try using no mouse.

4. Is it still locking up?  Try disabling wireless and see if it still locks up.  You should be able to just boot it up with the wireless slider switch on the front switched into the off position.

Please post more details and we'll see where to go from there.

EDIT: Just noticed that you are using Catalyst 9.11.  Have you tried the fglrx driver in the ubuntu repositories?  That's what I have been using without trouble. Why did you upgrade to 9.11?

EDIT2: One more possibility... although it has never resulted in a hard lockup for me... is the backing store bug in xorg/fglrx.  It results in slow window move/resize.  But not hard lockup.  If you suspect that, there is a solution; let me know and I'll post more, gotta go now.

---

### Post by wimvanleuven on 2009-12-25
Hello gatman3, thanks for the swift reply!!!

I just tried to reproduce the problem without Compiz using ```
sudo metacity --replace
```
but I got it to freeze by dragging some windows around for some time. ](*,)

On the hardware level, I got nothing fancy, actually nothing, attached. I'm a trackpoint adept (touchpad disabled in BIOS) and I did disable bluetooth, firewire, etc already in the BIOS. Only wifi is on. 

I also tried to disable the wifi, but got to freeze also.

One thing to note ... I read somewhere that the drag/freeze issue might be due to framebuffer problems. So I tried to switch between no framebuffer and radeonfb using a dedicated grub menu item. Next on my list will be vesafb-tng framebuffer.

I also noticed a new Catalyst release, so I will be installing that somewhere in the near future.

The reason why I'm running Catalyst? Well, I got this fine piece of machinery here on my lap, so I'd rather be using it to it's full capacity. Glxgears runs at 5K-30K frames in 5.O seconds (Is that even possible?) and 1750 when maximized.

On the other hand, using fglrx OSS drivers, what do I get and what will I miss? I thought I got no 3D, true?

Merry Xmas!
wim

---

### Post by wimvanleuven on 2009-12-25
Oh, BTW, I do have my trackpoint working with middle button to scroll. I haven't read you guys have that working? 

I attached an additional configuration to the HAL by dropping the file [FONT="Courier New"]mouse-wheel.fdi[/FONT] in the [FONT="Courier New"]/etc/hal/fdi/policy[/FONT] folder. 

That file contains following configuration:
```
<?xml versoin="1.0" encoding="UTF-8?>
<match key="info.producT" string="TPPS/2 IBM TrackPoint">
  <merge key="input.x11_options.EmulateWheel" type="string">true</merge>
  <merge key="input.x11_options.EmulateWheelButton" type="string">2</merge>
  <merge key="input.x11_options.XAxisMapping" type="string">6 7</merge>
  <merge key="input.x11_options.YAxisMapping" type="string">4 5</merge>
  <merge key="input.x11_options.ZAxisMapping" type="string">4 5</merge>
  <merge key="input.x11_options.Emulate3Buttons" type="string">true</merge>
</match>
```

---

### Post by gatman3 on 2009-12-27
Well, it sounds like you've ruled out several of the usual suspects: wifi, bluetooth, firewire, compiz.  I guess at this point I'd focus on the graphics driver, as you seem to be doing.

When I asked why you were using Catalyst 9.11, what I was trying to ask is why you are using the newest ATI/AMD driver version 9.11 instead of the custom version of fglrx packaged and tested in the Ubuntu 9.10 repositories?  A few more details if it helps clarify (sorry if this is redundant):

The W500 has two graphics options: integrated intel graphics and discrete ATI graphics.  "integrated" meaning integrated in the intel chip set, and "discrete" meaning a separate ATI graphics chip.  The integrated graphics provides very low power but no external Displayport/DVI and no 3D at all.  The ATI chip burns power like crazy but has excellent 3D performance.

You might try enabling the intel graphics controller, at least just to see if your system hang problems go away.  You would do this in the BIOS menus by selecting "integrated graphics" under the "Display" option, I think.  You may also need to change the driver to "intel" in your /etc/X11/xorg.conf, or possibly just delete the Driver entry completely (I think that xorg figures it out on its own now).  I can understand that you want the far better fglrx graphics support, but try the intel graphics just to narrow down the cause of the hang.

It sounds like you already tried the open-source radeon driver instead of fglrx.  You might also try uninstalling the fglrx (Catalyst 9.11) driver you installed and getting the one out of the Ubuntu repositories.

I don't think the fglrx/xorg backing store problems are causing your lockups.  That problem just causes slow resize, window move, etc.  But if you want to investigate that issue, here are a couple of links that helped me:

[https://bugs.launchpad.net/ubuntu/+source/fglrx-installer/+bug/351186?comments=all](https://bugs.launchpad.net/ubuntu/+source/fglrx-installer/+bug/351186?comments=all)
[http://blog.jasondonenfeld.com/169#comment-404](http://blog.jasondonenfeld.com/169#comment-404)

Sorry, wish I had a magic fix for you.  Maybe someone else will be kind enough to chime in.

---

### Post by wimvanleuven on 2009-12-28
Hello gatman3, 

Don't be sorry. I'm already happy I got someone to share ideas with. 

Just uninstalled the ATI proprietary driver (catalyst e.a.) by disabling/removing it through the[FONT="Courier New"] System > Administration > Hardware Drivers [/FONT]panel. Next removing [FONT="Courier New"]xorg-driver-fglxr[/FONT] via [FONT="Courier New"]apt-get[/FONT]. Is this correct? How to know which driver is used now? [FONT="Courier New"]glxinfo[/FONT] reports SGI and Mesa project.

I restarted and got my proper hi-res display settings, so that is OK. Unfortunately, it seems I do not have compiz support. How can I test this? Glxgears reports 2700-3000 frames/sec. So speed here is less. I tried to reproduce the freeze, but no luck until now. So I'll be running in this mode for some time to make sure the issue is gone by the ATI uninstall. 

The reason that I used the latest ATI version, is because the hardware drivers panel did not provide me the option to install the repository version. So I just grabbed the latest from ATI. That reflection seems to be a Windows habit that I shouldn't just port to Linux, unfortunately.

If the current config seems stable, i'll test the repository version and keep you posted.

---

### Post by gatman3 on 2009-12-29
Ahhh, very good, sounds like progress!  By removing the fglrx driver using apt, you should now be running the open source radeon driver.  That is confirmed by seeing "Mesa" in your glxinfo.

Unfortunately, the open source ATI driver has two problems that you will not be happy with: (1) no 3D support, so no compiz, and (2) poor power management, so battery life will be much worse.  I also even experienced occasional BIOS-commanded shutdowns due to overheating with the open source driver, so it is definitely not recommended for the long term.

By the way, it sounds like you may have experienced the same problem I did with Ubuntu 9.10 when trying to enable the proprietary driver: simply using the System->Hardware Drivers application did not work.  There is obviously a bug in Ubuntu 9.10 preventing this.  To work around this I believe that all I did was use Synaptic to get the xorg-driver-fglrx package installed from the 9.10 repos.  I don't remember any other special setup.

I do remember reading somewhere that the fglrx from the Ubuntu repositories was a pre-released version of the Catalyst 9.10 version, something about the Ubuntu developers needing an early release from ATI because they weren't going to make the cutoff for freezing the 9.10 repositories.  It's possible that there is something else special about that release, not sure.  In any case, it's probably best to start with the fglrx driver from the Ubuntu repos rather than jumping straight in with the latest download from ATI.  In the past, I have used the ATI monthly Catalyst releases directly with varying success.  Roughly a year ago with the Ubuntu 8.10 release the ATI driver had all kinds of problems with flickering video playback and we all tried month by month to see if ATI would fix it; I think it finally got stable around 9.1 or 9.2.  I have had good luck with the Catalyst 9.10 pre-release hybrid from the Ubuntu repos, so I haven't bothered going to get the latest driver from ATI.  Could very well be your problem the last few days.

Again, be encouraged that I use the fglrx driver with the compiz effects and find it to be quite stable.  Note, though, that I am using the KDE version of compiz (Kwin window manager, etc.) not the GNOME compiz/Metacity stuff, so that's a variable too.  I also actually switch frequently to the intel graphics when I want to have better portability; intel burns way less power (gets about 4 to 4.5 hours battery life on my W500) and supports suspend-to-RAM reliably, so it's much more convenient when using the machine down at the coffee shop.  I have only heard of mixed results getting suspend to work with fglrx, if that's even important to you.  The W500 is awesome in that you can have the choice of excellent graphics or low power; I just wish it were easier to switch between them than digging around in the BIOS config menus, but I really can't complain.  It's a fantastic piece of hardware.  And Lenovo keyboards are still the gold standard.

---

### Post by wimvanleuven on 2009-12-30
Hmm Gatman3,

some strange results. 

I did reïnstall [FONT="Courier New"]fglrx[/FONT] through [FONT="Courier New"]synaptic[/FONT]. No result. 
So I tried using the [FONT="Courier New"]Hardwire Drivers[/FONT]. Freeze.
Reinstalled via [FONT="Courier New"]synaptic[/FONT]. Did some investigation: rerun [FONT="Courier New"]aticonfig --initial[/FONT]. Bingo! Compiz runs!!! 
Using [FONT="Courier New"]Appearance[/FONT] to enable Compiz from startup.

Strange thing is that Compiz-fglrx combo seems smoother then metacity, which I always found ... choppy.

For as far as I have used it, this setup seems stable. I'll let you know after some more testing how this works out. I'll also start reenabling some BIOS disabled devices.

However, it seems that the metacity-fglrx combo seems unstable. 
Anybody to confirm this?

I was almost going to give up on Ubuntu/Linux shortly!!! So thanks for helping out!

---

### Post by wimvanleuven on 2009-12-30
Aha ... just found an issue, you guys might be able to help. 

Using Compiz, on maximizing a window and minimizing afterwards, it takes a while to respond (about 1-2 seconds). 

Might this be related to the backing store bug? Any more clues/pointers into this?

Thanks again!
wim

---

### Post by gatman3 on 2009-12-30
wimvanleuven - wonderful, sounds like huge progress.  If you have the problem where there is a few seconds of delay when moving windows, then you have the backing store problem I referred to previously.  This is fixable and to be expected (sadly).

Add the following to your /etc/apt/sources.list file:

```
deb http://ppa.launchpad.net/ubuntu-x-swat/xserver-no-backfill/ubuntu karmic main
deb-src http://ppa.launchpad.net/ubuntu-x-swat/xserver-no-backfill/ubuntu karmic main
```

Then do:

sudo apt-get update
sudo apt-get upgrade

(I think)

Something like that anyway.  You may also need to wget the key for the bugfix repositories, but I can't remember the exact command for that.  You may be able to just ignore the "untrusted" repository for now.  If you have trouble, let me know and I'll dig up the exact sequence.  Basically, you just need to add the extra repositories I listed which have the fix for the backing store bug, and then replace your existing xserver with that one.  This fixed it right up for me.

You can refer to the links I posted a few days ago to monitor for future fix releases that may be more "correct".  I gather from reading the miles and miles of commentary on those links that this fix is somewhat of a hack.

Good luck.

EDIT: Here is the link for the no-backfill bug fix; it has info about how to install it as well.  Click "Technical details about this PPA" and then "Read about installing" for detailed directions...

[https://launchpad.net/~ubuntu-x-swat/+archive/xserver-no-backfill](https://launchpad.net/~ubuntu-x-swat/+archive/xserver-no-backfill)

---

### Post by wimvanleuven on 2010-01-05
Hello gatman3,

not sure my problem is the backfill problem: you talk about moving windows etc. I only experience a 1-2 second lag in maximimizing/restoring windows. Any comment?
-wim

---

### Post by gatman3 on 2010-01-05
I think that window placement (minimize/restore, alt-tab window switching) was one of the problems as well.  I noticed it most when trying to move windows.  I can't remember if I experienced the problem most with window move or window resize.  Might have been resize.  In any case, since the backfill fix was packaged properly, it's fairly straightforward to install it and see if it fixes your problems, and then uninstall it if it has no effect.  To uninstall, just remove the ppa repository from the /etc/apt/sources.list and update/upgrade.

---

### Post by stalet on 2010-01-06
Hi 

If it helps ill post some of my experiences with linux on the w500.

When I tried using the w500 with fedora 10 a while back i ran into similar problems. The machine hung from time to time - I think that happened with the intel card as well. When the hang occurred the caps lock indicator started blinking (i think that indicates a kernel panic).
The machine rendered unusable - so I swapped to ubuntu and the problems disappeared.

However I can confirm that the newest ati driver (9.12) works with karmic koala without problems. Of course you need to use the xserver-no-backfill fix mentioned.
I don't think i've done any other configuration changes to make the machine work and i have not disabled bluetooth or any other devices in the bios.

I think the xserver-no-backfill fix relates to resize and moving windows.
You will notice that the machine uses 100% cpu for a few seconds before resuming normally.

As gatman says you can easily test this. The only drawback by using the xserver-no-backfill fix is some small random glitches in the graphics (but hardly noticeable).

---

### Post by gatman3 on 2010-01-06
Excellent summary stalet!  That summarizes my experiences exactly, although I'll add that additionally I experienced bluetooth related kernel panics (flashing capslock) with Ubuntu 9.04, but 9.10 solved it.  In a way it's reassuring to know that you too, stalet, have found the need to install the no-backfill fix and that I wasn't just imagining these problems.  :)  Sure would be nice to get that one fixed, I'm hoping for 10.04.

---

### Post by wimvanleuven on 2010-02-18
Hey guys! 

Finally made some time to install that PPA. If I looked at installed packages with Synaptic Package Manager, it doesn't seem to have installed. Not sure what I am doing wrong. 

Any suggestion on this?

---

### Post by stalet on 2010-03-09
> **wimvanleuven said:**
> Hey guys! 

Finally made some time to install that PPA. If I looked at installed packages with Synaptic Package Manager, it doesn't seem to have installed. Not sure what I am doing wrong. 

Any suggestion on this?

To install the repository and install the files run these commands
```

sudo add-apt-repository ppa:ubuntu-x-swat/xserver-no-backfill 
sudo apt-get update 
sudo apt-get upgrade

```

and the packages in x should be updated. 
To check which maintainer you are using run this command:
```

dpkg-query -s xserver-common | grep ^Maintainer

```

My output from this is:
Maintainer: Ubuntu X-SWAT <ubuntu-x@lists.ubuntu.com>

If its not - you probably have to try installing that ppa again the manual way.

Edit: added apt repo command

---

### Post by wimvanleuven on 2010-03-13
Hello Stalet,

thanks for ths reply! Just verified using your commands and I'm also reading the same maintainer information as you. So it does seem the backfill fix has installed properly. 

However, my issue remains! To remind: maximizing a window using the window button, takes about 6 seconds before it jumps to the full screen. Very strange as I can not find any other mentions anywhere else. 

Oh, BTW, I did also try the pre-release of GWT-Shell. Seems a fantastic desktop management utility. However, this also just freezes the system (no reaction, but a properly moving mouse). It seems though you are running more recent versions of the video drivers:  ATI ones, no? Do you find the stability and OpenGL support is improved? 

Kind regards,
wim

---

### Post by stalet on 2010-03-15
Yes I am using the Ati Catalyst version 9.12 (8.681) and it has been much more stable than the previous ones - at least when it comes to suspend/resume. For the OpenGL support i guess it always has been good, the reason why is was testing new releases was mainly the resume after suspend problem the earlier versions had.
I tried some games: bzflag, alien arena, tuxracer and i can always play them in full-rez wih highest settings with no problems.

I tried 10.1 as well - but had some problems with the installer so I didnt bother.

Ive never had the problem you are describing tho, maybe you can tweek some settings in compiz to make it work better - or just disable compiz all together.

Good luck 
-S

---

### Post by wimvanleuven on 2010-03-15
Yeah, I could just disable Compiz, but I do like the nice fizz it brings to the desktop. I don't use much of its fancy stuff, just the wobbly windows and spring out when min/max'ing windows. 

I'll look into tuning it a bit, but if that fails, I'll be indeed abandoning it. 

Do you have any experience using the GWT-shell?
-wim

---

### Post by wimvanleuven on 2010-06-28
Hello,

just wanted to share that I have **successfully upgraded to Lucid Lynx** without any issues. Note however that I **deinstalled the proprietary ATI driver** (fglrx)  for starters and reinstalled it after upgrading. That was however kind of a funny install procedure in strange colours and resolutions ;-) With upgrading, my **issues still remain** that metacity freezes my system at irregular intervals. 

Ubuntu now combined with Compiz, a fancy theme (Infinity) from bisigi-project.org (thanks to @litrik from norio.be) and Gnome Do is just a **jaw dropping experience**! Still looking to get **rid of the top Gnome panel** by replacing its functionality completely into Gnome Do for e.g. the applets and some kind of desktop-right-click replacement for the 'Start menu'. Any ideas?

On Lynx's side, I **was expecting some performance improvements** on starting and stopping my system. No major advancements, bus some, as was suggested by the lucid ;-) release notes. Haven't noticed a thing however in this area. Au contraire, to me it seems **it became slower**. And I do **not like the new look and feel** they created for Ubuntu (purpleish). That's why I changed for the other theme. That leaves me the issue to **change boot splash** and stuff. I think I gonna disable it and leave the textual boot (terminal). Looks great to me! Professional, no? :-P

-wim

---

### Post by wimvanleuven on 2010-08-22
Hello everybody,

How's it rolling in Ubuntu/Thinkpad land? 

Must tell that I've found a new issue: playing DVDs results in choppy (video ánd sound) playback. First, I thought this might be a video card issue. But, I tried another one without luck. 

Might this be related to the CD-drive reading to slow? Any suggestions on this matter? Thanks beforehand!
-wim

---

### Post by wimvanleuven on 2010-08-29
Hello all,

while working on that DVD problem, I tried to install additional video codecs etc, breaking my configuration. Finally I uninstalled and tried reinstalling the fglrx drivers from the hardware drivers panel in ubuntu. This fails terribly: it seems everything starts without issues, however the screen is totally blank, not truly white but rather snowy. 

I got no clues anymore on possible causes, so I'm getting desperate. I think that my next step will be a clean reinstall of Ubunty Lucid Lynx. 

Any ideas would be much appreciated!
-wim

---

### Post by gatman3 on 2010-08-30
Wim - sorry, I haven't responded because I don't have any good suggestions.  But perhaps I can at least offer some moral support.  :)

Prior to messing with the video drivers you suggested that the problem could be DVD drive read speed.  I know that you can determine the access speed of hard drives using hdparm -t, perhaps that works on optical drives as well, don't know.  Worth a try.  You could also try ripping the DVD onto your hard drive and playing it from the hard drive.  That would rule out drive speed as the problem.  I would seriously doubt the drive isn't fast enough because DVD-VIDEO only requires about 10 megabits/second (1.3 megabytes/second) off the media, which is glacially slow.  Plus, the instantaneous bit rate varies and most of the time is actually running about half that rate.

My money is on video driver problems.  Unfortunately, I have dropped the ati/fglrx video completely due to advances in the intel driver, which now supports decent 2D acceleration for the KDE desktop effects.  I assume you tried this with both video chips in the W500?

If you rip the DVD to your hard drive you could try playing it back with various engines as well.  I would try mplayer, xine, totem and vlc because I think they all use different playback engines (not completely sure about that, but it won't hurt to try them).

Hopefully you can get your video drivers reinstalled successfully without reinstalling the whole OS.

Good luck.  Sorry I can't be of more help.

---

### Post by wimvanleuven on 2010-08-30
Gatman, thanks for the reply. In the meantime I've found out that video playback should be due to the combination with Compiz and hence seems to be a 'known' issue. 

So, as you said, not a DVD drive speed problem. This also could not have been a codec issue neither, as VLC is fully self supporting in it's codecs and should do DVD playback. 

So the workaround for DVD playback, is to switch to metacity temporarily while playing DVDs. Is perfect for me! I'll try that out, if however I first succeed in getting FGLRX back online, obviously. I'm running in ATI mode for the moment.

You mention the Intel card and advances in the drivers ... for KDE. Does Gnome run properly in 2D. Is that with Compiz enabled or not?

Tnx!
-wim

---

### Post by gatman3 on 2010-08-31
Wim, glad to hear you have a handle on it.  I remember having problems in the past with video playback and compiz desktop effects enabled, something to do with direct rendering not working properly with the effects enabled.  I thought that had been resolved, though.  Apparently not.

I'm not certain about desktop effects in GNOME using the intel driver, but it works well enough for me now in KDE.  My guess is it would work the same under GNOME, although I'm not sure what the difference is though between KDE/KWIN and GNOME/compiz.  You can probably try it out by just commenting out the "driver" section in your xorg.conf file, rebooting into the BIOS config and switching to integrated graphics.  I mainly just use the window translucency and desktop grid effects, and they work just fine with intel graphics now.  The fabulous cube effect even works, although it's a little slower than with ATI graphics.  I can't find much use for it other than taunting my friends running Windows anyway.  I can't remember exactly when all this started working with the intel driver, maybe Ubuntu 9.10.

To me, the advantages with the intel graphics are much lower power and heat, and suspend-to-ram works flawlessly.  The disadvantages are lack of a digital video output (DVI/Displayport) and some games don't run properly.  But I rarely run games, so not a big deal to me.  I run this machine about 50/50 in a dock at work, and it's excellent to be able to suspend to RAM and then dock or undock the machine.  I never got that working with the ati/fglrx graphics.  Seemed like it was always just one more Catalyst driver release away.  I miss my dual monitor setup a little, but overall the user experience with intel has been very good.

Someday I'll get a W510 or something even newer with dual digital video outputs.  :D

---

### Post by quackeroni_pizza on 2010-10-11
I got 10.10 working on a fresh install and an upgrade from 10.04 yesterday. For the upgrade, I must have spent a few hours getting the ati radeon drivers happy and running again.. The upgrade messed up a few things with xserver but nothing serious. Didn't get the display to work with switchable graphics (wasn't the new kernel supposed to support that?) but discrete graphics works fine with some tweaks. With discrete graphics, I have not been able to get fglrx enabled.. look for errors in jockey.log (XorgDriverHandler.enable(): package or module not installed). A few old package names (virtualbox, etc) don't obey new dpkg conventions.. be prepared for some dpkg errors.

---

### Post by gatman3 on 2010-10-15
quackeroni, thanks for the update.  After reading your post I went ahead and upgraded to 10.10.  For the first time I tried the network upgrade rather than a clean install.  The upgrade worked perfectly, so now I'm running 10.10.  I had no dpkg errors, but that could be simply that I didn't have any of the same packages installed that caused problems for you.

In any case, I do have one new problem after upgrading to 10.10.  Suspend-to-RAM no longer works when I shut the laptop lid while running on battery.  This worked perfectly in 10.04, but in 10.10 it puts the machine in a state where the sleep light never stops flashing, and a hard reboot is required to get out of that state.

After some initial research it sounds like there are many people suffering from this problem with 10.10 on a variety of different machines.  Based on one suggestion I read, I have had success working around it using acpitool to suspend, but I still haven't gotten it to work by simply shutting the lid yet.  Weird.

Otherwise 10.10 looks good... so far.

EDIT: Let me add that I am only using intel graphics these days, so I can't confirm or deny the same issues with ATI/fglrx graphics that quackeroni reports.

---

### Post by wimvanleuven on 2010-10-18
Hi,

Yesterday I installed my new SSD and a fresh Maverick Meerkat. No problems whatsoever and no glitches so far. 

Note that I'm running discrete graphics and enabled the hardware drivers. So I got my favourite compiz back with gnome Do/Docky running! Great!!!!
-wim

---

### Post by stalet on 2010-10-18
Wim: does the resume after sleep work ok after upgrading?

-S

---

### Post by gatman3 on 2010-10-19
stalet, while we're waiting on a reply from wim about suspend/resume, I just wanted to point out that I found a workaround for the problem.

I believe this is the bug report that covers the problem.  It was reported on a T500, but the W500 is similar if not identical hardware and the symptoms are the same:

[https://bugs.launchpad.net/ubuntu/+source/linux/+bug/659668](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/659668)

I found that the /usr/sbin/pm-suspend program (link to /usr/lib/pm-utils/bin/pm-action) is not working, but acpitool -s works.  To workaround this I replaced the /usr/sbin/pm-suspend link with a one-liner that invokes acpitool -s.

```
su
apt-get install acpitool
mv /usr/sbin/pm-suspend /usr/sbin/pm-suspend.orig
echo /usr/bin/acpitool -s > /usr/sbin/pm-suspend
chmod ugo+rx /usr/sbin/pm-suspend
```

If you use this workaround, just need to remember to replace the original link if/when this gets fixed correctly.

If you and/or wim find that suspend/resume works properly with no fixes, I'd be curious to hear more about your setup.  Note that I'm using intel graphics and KDE (Kubuntu).

---

### Post by stalet on 2010-10-20
Thanks gatman.
I haven't upgraded yet. Thinking of doing a fresh install this time to finally upgrade from ext3. I will let you know if it works out of the box.

-S

---

### Post by stalet on 2010-10-22
I've just done a clean install of 10.10 and suspend works perfectly out of the box - both on close lid and pressing Fn/F4.
I'm using discrete graphics and installed fglrx driver, and there was no need to use your fix gatman.

First time that everything has worked after installing :)

(I had some problems with the installer tho - which crashed when changing partitions on my HD. But i worked around it doing all the partitioning using system rescue cd)

-S

---

### Post by gatman3 on 2010-10-22
stalet - Glad to hear you had a good install experience, at least except for the partitioning.  I switched to ext4 about a year ago and have had a good experience since then.

I dug a little deeper and it looks to me like the suspend problem only affects intel graphics.  I switched over to ati (not fglrx) and suspend worked fine without the hack.  I had some trouble trying the fglrx driver, though.  Gave me the old death-fade to a white screen on boot-up.  Weird.  Oh well, back to intel with the suspend hack.  Otherwise everything's working great on 10.10 for me, and the suspend hack for intel seems reliable.

---

### Post by wimvanleuven on 2010-10-31
Hello all,

sorry I didn't replied earlier. Didn't get an email notice on new replies on the thread :-(

Just tried the suspend/resume (fn+F4) ... works swimmingly! And super fast with that SSD :-(

I'm running 10.10 on ATI with FGLRX. And I'm not experiencing the horrific fade-to-white screen of death. 

However, itermittently my system just freezes. I presume it's the video driver that causes this. On the other hand, I got no idea how to debug such a problem.

---

### Post by wimvanleuven on 2010-10-31
My previous solution to be able to use the trackpad's middle-button for vertical scroll using the HAL configuration, doesn't work anymore on 10.10, because HAL has been deprecated. 

I just installed the gpointing-device-settings and just configured it graphically. Works OK.

---

### Post by stalet on 2010-11-25
I got a new problem. I dont use my bluetooth mouse very often - but today I did. 

Since it didnt automatically attach - i tried to search it up again. But it did not find the mouse. 

I did a full update (got a new kernel) and rebooted. And i got a message to allow my kensington mouse to use some privilges.
And then the bluetooth icon disappeared.

I run dmesg to see if there were any messages, and i found this:
bluetooth-apple[1768] general protection ip:7f4b1b6312c8 sp:7fffee8563c0 error:0 in libgobject-2.0.so.0.2600.0[7f4b1b606000+49000]

I rebooted again - and the same happened. The bluetooth icon dissapears and the message in the log.

Im not using my mouse very often - but its annoying to not have it working at all. 

Any of you guys knows what to do with this ?

Regards,
Ståle

---

### Post by gatman3 on 2010-11-26
I have also had problems with my bluetooth mouse that started in 10.10.  I'm not sure if my problems are related; I attributed them to the new bluedevil bluetooth stack which, I think, is only part of KDE and is a new ground-up bluetooth stack.  So it may not be related to your problems, stalet.

What I experience is that the bluetooth mouse will not connect automatically.  When I move the mouse for the first time after booting up, a pop-up window appears above the bluetooth system tray icon and says that the bluetooth is asking for permission.  I think the choices are Trust Always, Trust Once, or Deny.  Choosing Trust Always results in the pop-up disappearing and then reappearing a few seconds later, but the mouse still can't connect.  I have been able to fix this by deleting and re-adding the mouse using the Manage Devices choice when right-clicking on the bluedevil icon.  Next time it happens I'll check dmesg to see if it shows the same issue with libgobject.

---

### Post by ekh on 2010-12-14
Hi w500 users,

Great thread !

I have just got a w500 yesterday.
After some of the initial nuisances, it now works almost as I want it to.

I have Ubuntu 10.10 64-bit installed, and T9600, 4G RAM and a HD3690 graphics card.

I run the ATI 8.78.3-100920a-105558C-ATI driver.

The w500 is an "update" of my good old T61 machine, which I use for development.
The CAD programs run fine 2D and 3D, but the video playback only has sound.

Before I updated to the ATI driver the video worked on both mplayer and vlc for .flv, .mov, and .mp4.

With the ATI driver installed, no video playback, just the sound.

Do you have some advice ?
I have used some hours now searching, but no success so far.

ekh

---

### Post by wimvanleuven on 2011-01-15
Hello EKH,

Great to read you bought yourself this wonderful machine. 

You video playback issue probably is totally related to the video driver you installed. 

Is there a specific reason to go for those rather unsupported (not by the community neither by ATI) drivers? 

I'd recommend to uninstall it and go for the FGLRX drivers you can easily install via the System/Administration/Additional Drivers menu. 
-wim

---

### Post by ekh on 2011-01-21
Hello wimvanleuven,

Yes it is a wonderful machine, I love especially the matte 1920x1200 crystal sharp display.

By the way a seller on ebay.de sells it for 999 Euro, just search for "W500".

Unfortunately it has some issues with the graphic card I have not yet resolved.

The graphic system is the cause of my issues.

Power: it consumes 32W with the V5700 card, only approx 15w with the internal Intel graphics. Battery time 2,5 vs 5 hours.

I only have two applications that really need the V5700 card: A PCB layout program and a 3D CAD mechanical drawing program. So off the grid, I really miss the long battery time.

I don't remember the exact time to compile the source for the GCC C++ compiler, but it was fast, actually the hard disk is the bottleneck here.

The computing power also shows off when copying between two encrypted disks with 27MByte/second.

--------

Two days ago I got a hint from a friend that there is an error in the BIOS regarding correct recognition of the graphics card. the FireGL V5700 is recognized as a HD3650 card.

I have updated the BIOS resulting in Linux not recognizing the computer anymore. In the weekend I will try a number of reinstalls on another harddisk to test it a bit more.

It seems that the HW swichable graphics feature is not handled correctly, I have seen the initial boot screen working and not working after login, and I have seen the opposite in another install.

After the BIOS update the graphics became much faster with the free Linux driver, quite acceptable for my use, I'm not a gamer.

So I guess I will get it working well when I disable the switchable graphics, but still, off the grid I really miss the 5 hours battery time :-(

For description of the BIOS error and update see:

[http://www-307.ibm.com/pc/support/site.wss/document.do?sitestyle=lenovo&lndocid=MIGR-70497](http://www-307.ibm.com/pc/support/site.wss/document.do?sitestyle=lenovo&lndocid=MIGR-70497)

[http://www-307.ibm.com/pc/support/site.wss/MIGR-70495.html](http://www-307.ibm.com/pc/support/site.wss/MIGR-70495.html)

ekh

---

### Post by ekh on 2011-01-21
I checked this thread:

[http://asusm51ta-with-linux.blogspot.com/](http://asusm51ta-with-linux.blogspot.com/)

It states vgaswitcheroo is included in Ubuntu 10.10. But I don't see that in the 64-bit kernel I use.

Have I missed something ?

I did not find info about vgaswitcheroo and the 64bit kernel, and not on how to build it to include vgaswitcheroo.

ekh

---

### Post by wimvanleuven on 2011-02-06
Hey EKH,

indeed the system runs with switchable graphics ... not supported by Linux though. So you have to freeze it in the BIOS. I chose the ATI card, as I thought it was a bit silly to have all that power and not using it. I mostly sit connected, so battery time is a lesser issue. 

My setup: ATI + fglrx. Full reso and speed. I like compositing, that desktip sugar like compiz and those productive addons like gnome-do and docky.

However, I'm having an issue on Meerkat now wich is I think related to fglrx (more on that later). So I checked alternatives. There seems to be newer opensource drivers now with proper support however, what I think is a major issue, lacking video/DVD playback.

The issue I'm having: intermittent X freezes forcing me to a hard boot. This of course is very hard to debug. Last couple of hours I've my system in netconsole to remote log my dmesg output. So I'm hoping for a freeze right now ;-)

Not sure what I'm gonna find, neither where to drop a line on this. I'm probably will be heading for the ubuntu forums first. 

HTH
-wim

---

