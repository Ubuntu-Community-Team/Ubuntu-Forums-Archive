---
title: "Recommendations for new video card"
date: 2008-05-18
forum: Hardware
---

### Post by doctorprojector on 2008-05-18
Hi.

I'm considering building myself a new PC system, and I intend to run Ubuntu 7.10 or 8.04 on it.

What I'd like are recommendations for a video card which will work in Big Desktop mode, split over two monitors. Also I'd like the card to be able to, but not all the time, output to my HDTV via component video. Even if it is necessary to disable the Big Desktop mode temporarily.

In the past I've been able to make the Big Desktop work with my elderly ATI video card, but only while using a particular version of Ubuntu (5.04 or 5.10) and a specific version of the proprietary ATI driver.

I've read that the Nvidia cards are easier to set up for this type of thing, but I'm really looking for a what-works-with-what before I go spending the money on the card.

I've no problem with installing the proprietary Nvidia driver, via the Restricted Drivers Manager, if that's what I need to do to make it work.

Thanks.

doctorprojector.

---

### Post by ASULutzy on 2008-05-18
Is this for a desktop machine or a laptop?

I have an ATI 2900XT in my desktop, and it's decent, but way too power hungry. If I could do it over, I'd pick an Nvidia card, the 8800 GTS are pretty afforadable and offer great functionality and overall seem to be better supported in Linux. 

For a laptop it's a much tougher decision of course as you're fairly limited on how powerful a GPU you can get, and as the GPU gets stronger, the battery life goes down. I don't really have any good advice for a laptop GPU, hopefully someone else can answer that one

---

### Post by nicedude on 2008-05-18
Hey Dr you need to just get the best Nvidia card for what you want to spend. Since you stated you will building this desktop I assume you will be porchasing a new motherboard and if I am correct you will 99% chance need a PCI-Express video card for your new machine I would say definatly go with Nvidia over ATI as although they have their cheerleaders as well I have had 10-15 add on video cards in my day from both companies and have installed over 100 easy and I say Nvidia all the way as I have never had issues like I have had with ATI cards ( I have owned a few good ATI as well ). you can buy a card for your purposes anywhere from 50-60$ to over 300-500$ depending on whether you feel you have the newest chipset and such, but I assure you that outside of high performance gaming it becomes just a waste of money to buy the newest chipset as you will cry when you see it in six months for half what you paid :-) . A good tip is to buy from a good online source to get the best price, I suggest newegg.com as they not only have good prices and service they have customer reviews listed for each item ( I dont work for em I just have ordered from them maybe 25 times with no issues but fast good service ). and I suggest you be sure to look through the reviews there to see what problems if any the people have experienced with a given model card ( Even if you buy it somewhere else its a good place to see reviews ).

You should be able to get one for less than 100$ that will handle your dual monitor & TV out via S-video cable ( which you can convert to something else if need be like RCA with a 20$ converter from walmart ). 

So I say Nvidia all the way but I am glad ATI is around to keep the prices down :-)

Hope this helps you out and feel free to PM me if you need advice on any certain model you find and are thinking of buying.

---

### Post by teaker1s on 2008-05-18
+ 1 for nvidia, and yes I have ati too with latest binary driver-smooth sailing it was not.

---

### Post by rated727 on 2008-05-18
I own a 3dfx voodoo3 video card which includes the usual 15 pin VGA output AND an S-video output.

Unfortunately, Ubuntu 8.04 doesn't recognize this high end (but old) card.

The card is fantastic under Windows XP Pro when I got the right drivers (the first 2 drivers that I tried were rejected by XP as "not better" than what XP provided)

My experience that the hottest hardware often requires the most work to get setup and running to its full potential.  And sometimes, I just settled for something less awesome until the operating system caught up with my hardware.

I will start a new thread to seek advice for my problem, but if I don't get a resolution within a few days, the 3dfx voodoo3 will be replaced with an older Matrox card.

good luck,
    rated727

---

### Post by nicedude on 2008-05-19
Here is some info rated727 on your 3dfx voodoo 3 card

Activating the TV-out

Most of the information in this section came from [http://www.linuxnetmag.com/en/issue7/printm7tvout2.html](http://www.linuxnetmag.com/en/issue7/printm7tvout2.html) and the documentation for lm_sensors' bt869 driver.

In common with many cards the TV-out is activated automatically when the PC boots, but loses sync when you change mode eg by starting X. Unlike most of the other cards, reenabling it is not done by the XFree86 driver, but via the card's I2C interface, and requires specialised modelines detailed in the bt869 driver documentation. It requires the Voodoo 3 and Brooktree BT869 I2C drivers.

That info comes from this link
[http://www.realh.ukfsn.org/tvhowto/ar01s08.html](http://www.realh.ukfsn.org/tvhowto/ar01s08.html)

That card is from 1999 and the company went out of buisiness in 2000 so my hat is off to you if you get it to work, but I would suggest replaceing it with a $40US low end Nvidia card like a 4XXX series as it will be the difference of night and day as well as have S-video out for you to use.

Hope that info helps you in the mean time, And good luck :-)

---

### Post by doctorprojector on 2008-05-22
Thanks for all the advice given, as well as the other components to build a complete system, I am now the happy owner of a 'Point Of View 8800GT 512MB GDDR3 256bit Dual DVI PCI-E Graphics Card.'

I've installed Ubuntu 7.1 and the Nvidia proprietary drivers, which enabled the TwinView feature, giving me a 2960x1050 pixel desktop. Which I think is pretty neat.

I haven't tested the HDTV output, because there wasn't a VIVO cable or adapter included in the box. There was a DVI to HDMI adapter, and a DVI to VGA adapter.

So I've bought one of these, which I think is the right part:

[http://cgi.ebay.co.uk/ws/eBayISAPI.dll?ViewItem&item=180242645963](http://cgi.ebay.co.uk/ws/eBayISAPI.dll?ViewItem&item=180242645963)

When it arrives I'll hook it up as soon as I can, and see if I can make it work.

doctorprojector

---

### Post by ASULutzy on 2008-05-22
Yea, not to turn this into an ATI vs Nvidia thread, but I have had some ATI cards that I have absolutely loved. My 9800 pro (agp), my x800xl (possibly the best bang for your buck card I've ever purchased), but lately, Nvidia has just been blowing ATI away. The support is better, the cards are better, the power consumption is better, the price is better. I would definitely go Nvidia.

---

### Post by doctorprojector on 2008-06-03
Background: My HDTV is not on the same desk as my PC (I've ordered a Component Video cable today), so I've been shuttling my PC between desks to sort this out. :-)

The cheap VIVO cable arrived from HK quickly but my tinkering time has been limited. On the first attempt I found that Nvidia's otherwise excellent X Server Settings tool doesn't seem to know about TV-output and the TV out was limited to 480i.

I know the TV is capable of 1080i so I spent some time reading up about how Nvidia's drivers use the xorg.conf file, and I came up with this to configure a HDTV as the single display:

(if you're not using the Advanced Desktop Effects for wibbly windows e.t.c. this may break your configuration)

```

Section "ServerLayout"
    Identifier     "Layout0"
    Screen      0  "Screen0" 0 0
    InputDevice    "Keyboard0" "CoreKeyboard"
    InputDevice    "Mouse0" "CorePointer"
EndSection

Section "Files"
    RgbPath         "/usr/lib/X11/rgb"
EndSection

Section "Module"
    Load           "dbe"
    Load           "extmod"
    Load           "freetype"
    Load           "glx"
EndSection

Section "ServerFlags"
    Option         "Xinerama" "0"
EndSection

Section "InputDevice"

	# generated from default
    Identifier     "Mouse0"
    Driver         "mouse"
    Option         "Protocol" "auto"
    Option         "Device" "/dev/psaux"
    Option         "Emulate3Buttons" "no"
    Option         "ZAxisMapping" "4 5"
EndSection

Section "InputDevice"

	# generated from default
    Identifier     "Keyboard0"
    Driver         "kbd"
EndSection

Section "Monitor"

	# HorizSync source: edid, VertRefresh source: edid
    Identifier     "Monitor0"
    VendorName     "Unknown"
    ModelName      "TV-0"
    HorizSync       30.0 - 81.0
    VertRefresh     56.0 - 75.0
    ModeLine	"1920x1080@50i_man" 74.250 1920 2448 2492 2640 540 542 547 562 +hsync +vsync interlace
    ModeLine	"1920x1080@60i_man" 74.18 1920 2008 2052 2200 540 542 547 562 +hsync +vsync interlace
    ModeLine       "1440x900@60" 106.5 1440 1520 1672 1904 900 901 904 932 -hsync +vsync
    ModeLine       "1440x900@75" 136.5 1440 1536 1688 1936 900 901 904 940 -hsync +vsync
    ModeLine       "1280x800@60" 83.5 1280 1344 1480 1680 800 801 804 828 -hsync +vsync
    ModeLine       "1280x768@75" 103.0 1280 1360 1496 1712 768 769 772 802 -hsync +vsync
    ModeLine       "1280x800@75" 107.2 1280 1360 1496 1712 800 801 804 835 -hsync +vsync
    ModeLine       "1280x720@60" 74.5 1280 1336 1472 1664 720 721 724 746 -hsync +vsync
    ModeLine       "1280x768@60" 80.1 1280 1344 1480 1680 768 769 772 795 -hsync +vsync
    ModeLine       "800x600@75" 49.5 800 816 896 1056 600 601 604 625 +hsync +vsync
    ModeLine       "800x600@72" 50.0 800 856 976 1040 600 637 643 666 +hsync +vsync
    ModeLine       "800x600@60" 40.0 800 840 968 1056 600 601 605 628 +hsync +vsync
    ModeLine       "800x600@56" 36.0 800 824 896 1024 600 601 603 625 +hsync +vsync
    Option         "DPMS"
EndSection

Section "Device"
    Identifier     "Videocard0"
    Driver         "nvidia"
    VendorName     "NVIDIA Corporation"
    BoardName      "GeForce 8800 GT"
EndSection

Section "Screen"
    Identifier     "Screen0"
    Device         "Videocard0"
    Monitor        "Monitor0"
    DefaultDepth    24
    Option         "TVStandard" "HD1080i"
    Option         "AddARGBGLXVisuals" "True"
    Option         "TwinView" "0"
    Option         "metamodes" "1920x1080 +0+0"
    SubSection     "Display"
        Depth       24
        Modes "1920x1080@50i_man"
#              use "1920x1080@60i_man" for watching NTSC material
    EndSubSection
EndSection

Section "Extensions"
    Option         "Composite" "Enable"
EndSection


```

The important parts are the ModeLines for 1920x1080, and may not find these work with your TV. I located a post on another forum from someone else who had found these timings worked for his TV. I the inclusion of the line '*Option  "metamodes" "1920x1080 +0+0"*' keeps your aspect ratio correct.

Once you've established a TV out configuration you're happy with, I think it's a good idea to copy the configuration file so you can restore it the next time you need it:

Make a back-up of your xorg.conf:
```
sudo cp /etc/X11/xorg.conf /etc/X11/xorg.conf.HDTV_working
```

The next time you want the use your HDTV:
```
sudo cp /etc/X11/xorg.conf.HDTV_working /etc/X11/xorg.conf
```

Press Ctrl-Alt-Backspace to re-start X to make it work.

For my set-up, when I want to return to using my monitors on my other desk, I use Nvidia's X Server settings, so I don't bother to keep a back-up of the xorg.conf file for my dual-monitor because it's easy to set-up with the GUI.

doctorprojector

---

### Post by pancakelizard on 2008-06-03
Don't get a Geforce 8500gt series card. I have one and it doesn't work with Linux at all. 


Check out this link:
[http://us.download.nvidia.com/XFree86/Linux-x86/173.14.05/README/appendix-a.html](http://us.download.nvidia.com/XFree86/Linux-x86/173.14.05/README/appendix-a.html)

It shows everything that nvidia supports Linux wise with their driver.

---

### Post by stchman on 2008-06-03
> **doctorprojector said:**
> Hi.

I'm considering building myself a new PC system, and I intend to run Ubuntu 7.10 or 8.04 on it.

What I'd like are recommendations for a video card which will work in Big Desktop mode, split over two monitors. Also I'd like the card to be able to, but not all the time, output to my HDTV via component video. Even if it is necessary to disable the Big Desktop mode temporarily.

In the past I've been able to make the Big Desktop work with my elderly ATI video card, but only while using a particular version of Ubuntu (5.04 or 5.10) and a specific version of the proprietary ATI driver.

I've read that the Nvidia cards are easier to set up for this type of thing, but I'm really looking for a what-works-with-what before I go spending the money on the card.

I've no problem with installing the proprietary Nvidia driver, via the Restricted Drivers Manager, if that's what I need to do to make it work.

Thanks.

doctorprojector.

I have an 8800GT and it works great in Ubuntu.  After you enable the restricted driver you can install nvidia-settings to get a GUI to set up the dual monitors.

Nvidia is the way to go in Linux.  ATI cards can be problems.

---

### Post by NoVista on 2008-06-03
Well well well.
This particular post, unlike sooooo many others, pretty much sums up the situation, and I'm glad I found it.
Thank you pancakelizard for the link.

I have been unable to enjoy Hardy yet, because of the ATI/Compiz/Video issues. I've tried fresh installs/upgrades and I have a seperate Home folder too.I keep images of all my drives, so never a worry if I trash the OS.

We did good to get this far.
On Gutsy, we had our work-arounds.
We installed xgl-server. We had great desktop effects AND clean fast video. We survived.
But ATI/AMD have just taken too long.
So today I decided. I'm giving up on ATI.
It's a done deal. I'm going shopping/researching ASAP.

My situation and my fix:
My agp ATI AIW 800xt will still be used to run an occasional Windows OS on a dual boot though. So what I am going to do is buy a non-ATI PCI based card, to run on Linux.
All I have to do is tell the motherboard BIOS on boot which port to use for video, agp or pci.

So again I thank you pancakelizard for the link.
Whatever PCI based card I decide to purchase, I really really really hope it's an "Outta The Box" experience.
I would think I could find a great deal on a hi-end PCI card for low bucks these days.

Recommendations anyone?

Yes .. the x800xt AIW was a great one. As was the older 8500 ATI AIW.
Bye Bye ATI .. it was a good run.

---

### Post by markbuntu on 2008-06-04
I'm sorry to hear about your ati problems. I was going to get a Nvidia 8800 or the ATI HD3870 but they cost about $180 and my 300w p/s would not support them so it would have been another $100 for a new p/s. Plus the ATI driver does not support their card yet.

Instead I just got a ATI Radeon HD3650 1GB and it works great. My choice at $79, an 8600 with 256m or a HD3650 with 1GB ($50 discount and $40 rebate). I decided to take the chance with ATI and am very satisfied. Worked like a champ right out of the box.

I am running Big Desktop at 3840x1200 with my 24inch and 19 inch monitors using the 8.47.3 ATI driver. Full sreen video works great on the large monitor. I can not test the tv out since I don't own a tv.

I have no problem running compiz even though it is not using dri yet. The latest kernel and firefox updates have soothed the issues of excess cpu usage and firefox crashes.

ATI is working on the compiz problem and results are expected soon. Workarounds are at the compiz fusion forums for use with the new 8.5 driver from ATI which fixes a lot of issues with older cards and many tweaks for the newer ones.

It seems that ATI is stepping up to the plate as as far as supporting linux users. They definitely seem to be far more committed than previously. By the end of the summer I excpect that the ATI poprietary drivers will at the least match Nvidia's if not outperform them and their support of the open source driver community will make all that even better.

Since I plan to keep this card for a while, I am willing to endure the few small issues that I know will soon be fixed.

---

### Post by Unix_Slayer on 2008-06-05
**[SIZE="5"]NVidia[/SIZE]**[IMG]http://http://mysite.verizon.net/mgm_mgm/nvidia_logo.jpg[/IMG]    



The only card you'll need. ATI hasn't kept up with NVidia because they are owned by AMD. AMD is having a tough of a time hanging on to their CPU's against Intel. This gives them no time to devote to their video line. That's all that needs to be said.

Enjoy NVidia.

---

