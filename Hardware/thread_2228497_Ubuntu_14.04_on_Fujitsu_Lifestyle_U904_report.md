---
title: "Ubuntu 14.04 on Fujitsu Lifestyle U904: report"
date: 2014-06-07
forum: Hardware
---

### Post by mcarro on 2014-06-07
Dear all,

I recently bought a Fujitsu Lifebook U904 after using a Dell Latitude 6405 (IIRC) for several years.  I was attracted by the slick design, performance, weight, and huge resolution (3200 x 1800) and the possibility of ordering with some specific components (although custom build models take some additional time to be delivered).  In particular, my model has the following hardware:

[LIST]
[*]    - Intel i7-4600U @ 2.1GHz
[*]    - Intel Haswell Mobile
[*]    - 500 Gb disk
[*]    - Touchscreen
[*]    - Fingerprint reader
[*]    - Slot for an LTE SIM
[*]    - SD reader
[*]    - 10Gb RAM (2Gb are soldered to the motherboard, 8Gb are added).
[/LIST]


I installed Ubuntu 14.04 64 bit, and the good news is that most hardware seems to work.  I first used as guide Chris Balls' page:

[http://blog.printf.net/articles/2014/02/02/fujitsu-lifebook-u904-review/](http://blog.printf.net/articles/2014/02/02/fujitsu-lifebook-u904-review/)

I disabled, as advised, secure boot (I do not know if it's necessary or not).  I did not download specific firmware packages, except the general Linux-firmware package.  I am not sure I'd need any specific firmware for some of the untested hardware.

The good:

  [LIST]
[*]  - Installation went flawlessly.
[*]    - Most hardware seems to work.
[*]    - The display resolution is very good.
[*]    - The battery seems to be able to sustain the laptop for some 5:30 hours according to PowerTop (5:50 according to the battery indicator) hours in more or less normal conditions: medium screen light, no movies or music, light text editing with Emacs, internet connection with Dropbox and InSync [Google Drive sync tool] running, no browser activity, ondemand CPU frequency governor.  If I make all the tunables go to the "good" state (see the section on PowerTop below), reduce the screen brightness to the minimum usable, make the CPU governor be powersave, and switch off Bluetooth and wifi) the estimation I get is between 6:45 and 7 hours.  Note that I have *not* measured real time (yet).
[*]    - Speed is OK.  Nothing seems to be incredibly fast in comparison with my previous laptop (except boot and resume time, due, I think, to having less hardware to initialize).  I guess that if I do CPU-intensive work, such as encoding movies, I would see more advantages.
[*]    - The keyboard is OK.  I am still getting used to it.
[*]    - As reported by people who spoke with me over Skype, the microphone sounds good and with good balance.
[*]    - Camera is recognized and, although not thoroughly tested, seems OK.
[*]    - HDMI out (including sound) also works.
[*]    - Bluetooth for data transfer work.
[*]    - External speakers (through jack) work.
[*]    - Suspension and resumption has been working flawlessly so far: no       mouse pointer, sound issues, as reported by Chris -- but I'm      using a newer kernel, so this may be the source of difference.
[*]    - The touchscreen works.  I am not sure it supports all the       gestures it's supposed to, but clicking and dragging windows around works.  I do not see it terribly useful, though.  I always hated touching the screen with my fingers.
[*]    - The touchpad works (see below) including two-finger scrolling.
[*]
[/LIST]

Hardware I have not tested:

[LIST=1]
[*]    - Fingerprint reader
[*]    - Broadband (LTE) connection.
[*]    - SD card reader.
[*]    - Display port in dock station.
[*]    - Microphone through the jack connector.
[/LIST]


There are some things that are not working right now, but I am not sure if they are even possible:

[LIST]
[*]    - Automatic screen dimming according to ambient light (are there  sensors?)
[*]    - Automatic dimming of keyboard backlight (same reason).
[/LIST]


On the other hand, some things that are not so good.  Some can be traced to the hardware itself, and some are software issues.
[LIST]
[*]    - Screen backlight: the maximum is not very high (Dell's screen       was much brighter), and the minimum is extremely low.  I can't think of any condition where this very very little amount of light is useful.  Unless this is the kind of display that one can use under bright light conditions (external light, sun light) by turning backlight down to a minimum, close to zero.
[*]    - The screen is glossy -- *very* glossy.  That can be inadequate       in some situations, especially because the screen is not so bright in maximum brightness conditions.
[*]    - The trackpad is sometimes behaving strangely, but it can that I      am not yet used to it.  Sometimes the mouse jumps unexpectedly probably maybe because of a very light touch, and if the (integrated) buttons and the trackpad are touched simultaneously, the mouse pointer jumps to a corner.  Is anyone else experiencing this?  Are there options / firmware / drivers that can help with this issue?
[*]    - LEDs (for caps lock, num lock) are very small and in a       not-easy-to-see position.  Also the labels are difficult to see in normal light and distance conditions.  Ditto for the labels of disk activity, etc. (but these can be clearly seen).
[*]    - Speakers are very bad -- the worst thing in the laptop.  My      Nexus 5's speakers are much much better, in basses, volume, and about everything.  This surprises me in a machine which is not cheap at all. Is there any recommendation, such as system-wide equalization, to help with this?  I installed a pulseaudio equalizer module but it didn't seem to have any effect on the sound.
[*]    - Bluetooth sounds is so and so; it comes and goes with numerous      glitches (at least from youtube, with more than enough buffered data). The headphones I am using are not high end, but they otherwise work flawlessly with my Android devices.  More investigation is needed here.
[*]    - The big thing is the ultra-high resolution display.  Default      Ubuntu is not prepared to handle it gracefully. As reported elsewhere, the default fonts and icons are tiny, and frankly unreadable for normal use.
[*]      - Unity Tweak an Gnome Tweak Tool can set font sizes and text        scaling.  But this is not a good solution because window bars and the menu / indicator bar on top are not enlarged, which means that the menus don't fit vertically when the fonts are made large enough to be readable.  Icons are not enlarged, either, so they in general look very small.
[*]      - However, the Display control in the System (new in Ubuntu        14.04, AFAIK) has a slider to set the scale factor for text, icons, window bars, and the top menu bar, which is much better.  I am using 1.75 as scaling factor.  The interaction Display control / Gnome tweak tool has been unstable for me: they seem to fight with each other. I'd recommend using Unity tweak instead of Gnome tweak if you need to set additional parameters.  In the "Fonts" RGBA aliasing and "slight" hinting (in Unity Tweak) give IMHO the best readability with the default Ubuntu fonts.
[*]      - Several applications windows  (for        example, some warnings and dialog windows) do not look nice because they were designed for displays with less resolution
[IMG]http://software.imdea.org/~mcarro/images/synaptic_authentication.png[/IMG]
[*]      - Other applications look very bad.  An outstanding example is        Google chrome (I guess that it does not go through gtk for its menus). Fonts for Web page contents can be adjusted in its internal settings, but this does not change tab names and the location bar: the latter is so tiny that it is impossible to read.  Most web pages look OK, but some don't.  A salient example is Google's own search results: they are all small, using only the 1/4 of the screen on the left, and with font sizes which make them look very ugly.  
[IMG]http://software.imdea.org/~mcarro/images/google_search.png[/IMG]
Of course I could use Firefox, which looks better, but my Android devices use chrome and I share bookmarks, etc. and all my passwords are already there (and cannot be imported automatically into Firefox).
[*]	Other applications, like the search engine Recoll, don't use gtk internally and do not seem to have options to change the font size used for the contents. I suppose that in cases like the these it's hopeless as there is no option to change the application's decision of the font size it uses, or to bypass this decision.  For them, does anyone has any idea of how to make the display readable (and aesthetically as pleasant as possible)?  I didn't see any place to for example change the DPI.  This option exists in KDE, but I tried to use KDE several times and for some reason I am not comfortable with it.  I would not mind switching to Gnome 3 or Gnome Flashback, but again I tried it several times and I end up returning to Unity.
[*]      - Likewise, most icons and the cursor do not change their sizes        automatically (the System Options window looks very unbalanced: the text is way larger than the icons; most menu icons are very small in relationship with the space available for them), and there is no option to enlarge it from the configuration tools GUI.  
[IMG]http://software.imdea.org/~mcarro/images/icons.png[/IMG]
I did change the cursor size in a GConf option, but the change was reverted in the next reboot.
[*]
[*]Wish list
[*]
[*]    - I would like to increase the time the battery lasts.  I've read      about laptop mode tools, but I am not sure how useful they are for the case of an SSD disk.  Any idea?
[*]    - PowerTop reports around 500 wakeups / sec.  I guess that      reducing the amount interruptions should help in having longer battery time.  My understanding is that the only way to do this is by looking at the applications / daemons which can be responsible and stop them if they are not relevant -- or maybe start them with different options.  Is there any way to detect from userland when power has been plugged / unplugged?
[*]    - Also in PowerTop, In the tunables section, a lot of entries      appear in "Bad" state -- see linked picture [IMG]http://software.imdea.org/~mcarro/images/powertop.png[/IMG].  Any idea of how safe is it to make them go to the "Good" state, in the sense that hardware suddenly does not work as expected (e.g. usb or bluetooth no connecting or being underperforming when used)?  Nothing seems to happen when I force them change to the "Good" state, but this might cause some malfunction which is difficult to trace.  I understand that PowerTop just sets kernel options -- why aren't these enabled by default?  One thing is that some tunables return to "Bad" state after some time - e.g., when the computer is plugged in again.
[*]    - BTW, something really strange is that PowerTop reports the eth0      ethernet interface to consume 6.36 watts - the largest amount with difference.  That sounds very strange to me, especially because I do not have any ethernet cable connected.
[*]    - A behavior I detected is that it seems that the battery does not      charge (independently of the O.S.) if it has more than 90% charge, more or less.  I guess that this is so in order to reduce the strain of charging the battery many times when only, say, 5% of it has been used because it has been unplugged just for some minutes.  I suppose this will increase the battery lie, but it can be inconvenient in some occasions --- e.g., just before a long flight when one wants to have the battery completely charged.  Any idea if it's possible to force the battery to start charging independently of its status?
[/LIST]

---

### Post by medoc92 on 2014-06-08
> **mcarro said:**
> 
[LIST]
[*]    Other applications, like the search engine Recoll, can't seem to use gtk internally and do not seem to have options to change the font size used for the contents. I suppose that in cases like the these it's hopeless as there is no option to change the application's decision of the font size it uses, or to bypass this decision.  For them, does anyone has any idea of how to make the display readable (and aesthetically as pleasant as possible)?  I didn't see any place to for example change the DPI.  This option exists in KDE, but I tried to use KDE several times and for some reason I am not comfortable with it.  I would not mind switching to Gnome 3 or Gnome Flashback, but again I tried it several times and I end up returning to Unity. 
[/LIST]


Recoll is a Qt app, so, if it does not adopt the desktop default properly (this should be the Qt default), you should be able to change the font size by using the qtconfig tool, available from qt4-qtconfig. Choose a style which is neither desktop default nor gtk+, then adjust the font and save.

Also, apart from the widgets fonts, the font for the result list text is independantly settable from the preferences.

---

### Post by mcarro on 2014-06-08
> **medoc92 said:**
> Recoll is a Qt app, so, if it does not adopt the desktop default properly (this should be the Qt default), you should be able to change the font size by using the qtconfig tool, available from qt4-qtconfig. Choose a style which is neither desktop default nor gtk+, then adjust the font and save.

Also, apart from the widgets fonts, the font for the result list text is independantly settable from the preferences.

Hi. Thanks a lot for your advice.  Actually, the menus and the GUI using the desktop default settings are mostly OK (with the exception that the icons to search, explore, etc. are very small).  Changing the font is not necessary here.  And I cannot find a preferences menu to adjust the application's font size for the contents. In case it helps, I am using Recoll 1.17.3 from the default Ubuntu repository.


Thanks!

---

### Post by medoc92 on 2014-06-12
> **mcarro said:**
> Hi. Thanks a lot for your advice.  Actually, the menus and the GUI using the desktop default settings are mostly OK (with the exception that the icons to search, explore, etc. are very small).  Changing the font is not necessary here.  And I cannot find a preferences menu to adjust the application's font size for the contents. In case it helps, I am using Recoll 1.17.3 from the default Ubuntu repository.


Thanks!

The option to change the result list font has always existed. It is here for 1.17 and later (it is in an analog but slightly different location for 1.16 and earlier):

   Preferences->Query configuration->Result list->Result list font

---

### Post by mcarro on 2014-06-12
> **medoc92 said:**
> The option to change the result list font has always existed. It is here for 1.17 and later (it is in an analog but slightly different location for 1.16 and earlier):

   Preferences->Query configuration->Result list->Result list font

Oh, right. Thank you very much.  I hadn't looked into that menu entry -- the name didn't suggest me that interface configuration was there.  My fault!

Best.

---

### Post by mörgæs on 2014-06-12
Thanks for the report. 

It will benefit users more if you add a **brief** post to the thread [http://ubuntuforums.org/showthread.php?t=1543006](http://ubuntuforums.org/showthread.php?t=1543006) (perhaps linking to this thread).

---

### Post by mcarro on 2014-06-13
> **mörgæs said:**
> Thanks for the report. 

It will benefit users more if you add a **brief** post to the thread [http://ubuntuforums.org/showthread.php?t=1543006](http://ubuntuforums.org/showthread.php?t=1543006) (perhaps linking to this thread).


Done.

---

### Post by mcarro on 2014-08-26
Just realized that Chromium does a better job than either Chrome or Firefox with high DPIs.

---

