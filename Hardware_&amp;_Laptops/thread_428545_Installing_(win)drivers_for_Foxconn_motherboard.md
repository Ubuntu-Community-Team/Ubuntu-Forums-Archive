---
title: "Installing (win)drivers for Foxconn motherboard"
date: 2007-04-30
forum: Hardware &amp; Laptops
---

### Post by Kristian9K on 2007-04-30
Hi,
Just got a new PC featuring this motherboard:
[http://www.foxconnchannel.com/Product/motherboard_detail.aspx?id=en-us0000217](http://www.foxconnchannel.com/Product/motherboard_detail.aspx?id=en-us0000217)

I would of course like to install the drivers for it (located in the left bar), but they seem to be aimed at Windows users. What should I do?

Kristian

PS: I'm on 6.10 if that helps...

---

### Post by kidders on 2007-05-01
Hi there,

I'm not _completely_ sure, but it doesn't look as though there's anything on that motherboard Linux should have a problem with. What's not working?

---

### Post by Kristian9K on 2007-05-02
Hi
Thanks for answering. Everything's working, but from my understanding should work better with drivers, is that right? As this board also does my graphics, I'm of course very interested in having them as good as possible. Right now my max resolution is 1280x1024, which I think should be higher. Overall, my system is not much faster than my old one (should be twice as fast), so I'm looking for things to fine tune it.


Kristian

---

### Post by kidders on 2007-05-02
> **Kristian9K said:**
> Everything's working, but from my understanding should work better with drivers, is that right?Hardware won't work *at all* without drivers. The Linux kernel contains open source drivers for most hardware, with a few major exceptions...
[LIST]
[*]Where a hardware manufacturer refuses to release technical documentation about its products. (eg Canon, Microsoft.)
[*]Where product development happens so quickly that the kernel is an impractical place to put the drivers. (eg high-end graphics & sound cards.)[/LIST]In these cases, it may be necessary to install third-party drivers, to stop Linux using generic or obsolete ones. I would recommend having a look around the web to see what drivers are recommended for your hardware, and double-checking that Ubuntu is using them.

> **Kristian9K said:**
> Right now my max resolution is 1280x1024, which I think should be higher.Unfortunately the link you posted doesn't give away much about your board's graphics capabilities. In general however, integrated graphics adapters tend not to be very high-spec, so I wouldn't be inclined to expect too much. Out of curiosity, what are the specs of your graphics adapter, CPU & RAM? Also, could you post the output of **cat /etc/X11/xorg.conf | grep -i driver** ... just to identify what your X is doing?

In general terms, Linux can optimise itself quite well to a given set of hardware out of the box ... far better than many other OSs.

---

### Post by Kristian9K on 2007-05-02
Kidders, thanks for helping out. I don't expect miracles from my onboard graphics, but would of course like it to perform as good as possible... A google search for "MBname + drivers + linux" appears to give nothing of use..

My specs:
CPU: Intel Celeron 3066MHz S-775
RAM: 1GB DDR2 PC4200 533MHz Kingston  	 
As for the graphics, I'm rathe baffled... the Foxconn page says  "VGA on Die: Integrated" and in the manual I can see that it uses a SIS driver (?)

The output you requested: 
  Driver          "kbd"
  Driver          "mouse"
  Driver        "wacom"
  Driver        "wacom"
  Driver        "wacom"
  Driver          "vesa" --------------> should this say vga or possibly svga?

Kristian

PS: Yes, I agree, that there's a lot of stuff supported out-of-the-box, but when something's amiss, I must admit that I long for the days of inserting the disc that came with the device and thus (usually) solving the problem.... can't have it all, I guess ;)

---

### Post by kidders on 2007-05-02
> **Kristian9K said:**
> Kidders, thanks for helping out.No problem. :-)

> **Kristian9K said:**
> A google search for "MBname + drivers + linux" appears to give nothing of use.Hmm. Oh well!

What you'd be particularly interested in is blog comments, forum posts, etc. written by people who build their own Linux (eg Gentoo users), that might contain specific hardware references & corresponding kernel modules. Chances are that Ubuntu has automatically selected all the best ones, but looking around a bit will help you convince yourself that it has.

> **Kristian9K said:**
> As for the graphics, I'm rathe baffled... the Foxconn page says  "VGA on Die: Integrated" and in the manual I can see that it uses a SIS driver (?)Yes, your motherboard has an SiS chipset. If you can discover the exact model/version information, you can use that to verify that X, for example, is using the best available drivers.

A useful trick is to try to get Linux to give you the vendor & product codes for the various bits & pieces on your motherboard. Those give you a completely unambiguous way to pair devices & drivers.

For instance, my graphics card is an Nvidia (vendor code 0x10de) 8800 GTS (product code 0x0193). If I google "10de 0193", I get results (quite often bug reports) that discuss exactly the right hardware.

> **Kristian9K said:**
> The output you requested: 
  Driver          "kbd"
  Driver          "mouse"
  Driver        "wacom"
  Driver        "wacom"
  Driver        "wacom"
  Driver          "vesa" --------------> should this say vga or possibly svga?
Speaking of graphics cards, the "vesa" line _will_ cause performance problems. Ubuntu chooses it (a generic, fall-back driver) when it can't think of anything more sensible to do, in an effort to guarantee that X will work out of the box, much as Windows does when it encounters odd graphics hardware.

Now that your installation is over, you can feel free to mess around with other X drivers, and look around the web for tweaks you can make to your graphical environment that might boost performance, or switch on pretty-looking features. Examples:[LIST]
[*]Is X using all your available VRAM?
[*]Does your card support direct rendering, compositing, etc?[/LIST]One word of warning, before you go tinkering with xorg.conf...

At some point or other (possibly even right away!) you will almost certainly break your graphical environment. Don't let failure phase you (X is an *extremely* annoying application to configure!), and always remember to keep a backup of an xorg.conf that you know is working.

Without a graphical environment, you'll have to get pretty good at interacting with your system using a text-only interface. Text-based browsers (eg links, lynx) and text-based editors (eg nano, vi) are very handy. Once you find a set of configuration options that work as well as you feel likely to be able to get, you'll never have to do it again!

> **Kristian9K said:**
>  PS: Yes, I agree, that there's a lot of stuff supported out-of-the-box, but when something's amiss, I must admit that I long for the days of inserting the disc that came with the device and thus (usually) solving the problem.Hehe the open source world is quite a different place, isn't it?! It's funny though... when I used Windows, I used to spend quite a lot of time trying to find ways of *avoiding* using manufacturer-supplied software, because it tended to fill my hard disk up with junk. Perhaps things have improved since then.

Linux's difficulties with graphics cards are usually down to manufacturers who refuse to release decent Linux-compatible drivers, or hardware documentation. It's definitely an annoyance ... but (as I mentioned) at least you only have to go through it once.

---

### Post by Kristian9K on 2007-05-03
Phew! Quite a mouthful ;)

If you know a beginners step-by-step guide somewhere to do these things, feel free to drop a link. Otherwise, I'll try to google my way through it and get back to you in a while.

Kristian

---

### Post by kidders on 2007-05-03
Sorry... I didn't want to get too specific, because I've never had an SiS card, so I'm not sure how different they all are, or what they can do.

Here's my /etc/X11/xorg.conf, for instance (with stuff unrelated to my display taken out). Creating it was a _**real**_ pain ... and a bug in the driver I'm using didn't make life any easier!
```
Section "ServerLayout"
    [SIZE=1][Irrelevant][/SIZE]
EndSection

Section "Files"
    [SIZE=1][Irrelevant][/SIZE]
EndSection

Section "Module"
    Load           "i2c"
    Load           "bitmap"
    Load           "ddc"
    Load           "extmod"
    Load           "freetype"
    Load           "glx"
    Load           "int10"
    Load           "vbe"
    Load           "dri"
    Load           "dbe"
EndSection

Section "InputDevice"
    [SIZE=1][Irrelevant][/SIZE]
EndSection

Section "Monitor"
        Identifier      "Hanns G LCD"
        Option          "DPMS"
EndSection

Section "Device"
        Identifier      "Generic Video Card"
        Driver          "nvidia"
        Option          "UseDisplayDevice" "DFP-0"
        Option          "UseEdidFreqs"
        Option          "ConnectedMonitor" "DFP"
        Option          "IgnoreDisplayDevices" "CRT, TV"
        Option          "SLI" "Auto"
        Option          "TripleBuffer" "true"
EndSection

Section "Screen"
    Identifier     "Default Screen"
    Device         "Generic Video Card"
    Monitor        "Hanns G LCD"
    DefaultDepth    24
    Option         "AddARGBVisuals" "True"
    Option         "AddARGBGLXVisuals" "True"
    Option         "NoLogo" "True"
    SubSection     "Display"
        Depth       16
        Modes      "1440x900"
    EndSubSection
    SubSection     "Display"
        Depth       24
        Modes      "1440x900"
    EndSubSection
EndSection

Section "DRI"
        Mode 0666
EndSection
```Yours will probably turn out quite differently, but I'm hoping this'll give you an idea of the sort of thing I'm talking about.

The most important line is in the "Driver" directive in the "Device" section. As you mentioned, Google will help you choose the right one. You may also find other things ...[LIST]
[*]My xorg.conf is hard-wired to use only one screen resolution (1440x900), that both my monitor & graphics card support ... and that I like the look of. You mentioned that you were unhappy with yours, so this is one way of making sure you get the results you want.
[*]In my "Module" section, I've loaded some advanced features that, again, I know my graphics card can support. You'll have to check what yours is capable of, and find a balance between pretty-looking and fast, that suits you.[/LIST]For me, the basic procedure was...[LIST=1]
[*]Discover something interesting on the web that I want to try (eg how to turn on direct rendering, maybe).
[*]Back up xorg.conf, open it up, and make some changes.
[*]Hit CTRL+ALT+Backspace, cross my fingers & hope X doesn't break.[/LIST]If X dies, /var/log/Xorg.0.log usually tells you why. You can then use a text-only web browser & text editor to try to figure out how to fix it. Then, doing a **sudo /etc/init.d/**[?]**dm restart** (depending on your display manager) will cause X to relaunch. Of course, if you get fed up, you can always restore your xorg.conf backup, and go back to the way things were. You can also use **sudo dpkg-reconfigure -phigh xserver-xorg** to force Ubuntu to restore X to its original configuration.


Anyhow, like you said, Google is your best bet. For instance, when I searched for "xorg.conf sis", I found some interesting pages (eg [http://ftp.x.org/pub/X11R6.9.0/doc/html/SiS2.html](http://ftp.x.org/pub/X11R6.9.0/doc/html/SiS2.html) ), along with some posts by other users on this forum, that also have SiS cards.

I hope some of that is a little more helpful.

---

### Post by Kristian9K on 2007-05-04
After some fooling around, this is the what I came up with...

```
root@kristian-desktop:/home/kristian# lspci -n
00:00.0 0600: 1039:0662 (rev 01)
00:01.0 0604: 1039:0003
00:02.0 0601: 1039:0966 (rev 59)
00:02.5 0101: 1039:5513 (rev 01)
00:02.7 0401: 1039:7012 (rev a0)
00:03.0 0c03: 1039:7001 (rev 0f)
00:03.1 0c03: 1039:7001 (rev 0f)
00:03.3 0c03: 1039:7002
00:05.0 0101: 1039:1183 (rev 02)
00:06.0 0604: 1039:000a
00:07.0 0604: 1039:000a
00:0e.0 0200: 10ec:8139 (rev 10)
00:1f.0 0604: 1039:0004
01:00.0 0300: 1039:6330 (rev 04)
root@kristian-desktop:/home/kristian# lspci 
00:00.0 Host bridge: Silicon Integrated Systems [SiS] Unknown device 0662 (rev 01)
00:01.0 PCI bridge: Silicon Integrated Systems [SiS] SiS AGP Port (virtual PCI-to-PCI bridge)
00:02.0 ISA bridge: Silicon Integrated Systems [SiS] Unknown device 0966 (rev 59)
00:02.5 IDE interface: Silicon Integrated Systems [SiS] 5513 [IDE] (rev 01)
00:02.7 Multimedia audio controller: Silicon Integrated Systems [SiS] AC'97 Sound Controller (rev a0)
00:03.0 USB Controller: Silicon Integrated Systems [SiS] USB 1.0 Controller (rev 0f)
00:03.1 USB Controller: Silicon Integrated Systems [SiS] USB 1.0 Controller (rev 0f)
00:03.3 USB Controller: Silicon Integrated Systems [SiS] USB 2.0 Controller
00:05.0 IDE interface: Silicon Integrated Systems [SiS] Unknown device 1183 (rev 02)
00:06.0 PCI bridge: Silicon Integrated Systems [SiS] PCI-to-PCI bridge
00:07.0 PCI bridge: Silicon Integrated Systems [SiS] PCI-to-PCI bridge
00:0e.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL-8139/8139C/8139C+ (rev 10)
00:1f.0 PCI bridge: Silicon Integrated Systems [SiS] PCI-to-PCI bridge
01:00.0 VGA compatible controller: Silicon Integrated Systems [SiS] 661/741/760/761 PCI/AGP VGA Display Adapter (rev 04)

```

So, my graphics are 1039:6330 and my chipset is...?

I also tried setting switching the "vesa" driver to "sis" in Xorg, which made the active parts of the screen flicker.... right now, I'm trawling for "1039 6330" and drivers via google.... 

Am I on the right track here? ;)
 
Kristian

---

### Post by kidders on 2007-05-05
> **Kristian9K said:**
> Am I on the right track here?Yep! :-) Now that you've posted all that detail (which is fabulous), I was able to take a more specific look around for you. It looks as though your graphics adapter isn't particularly good, and Xorg's SiS driver _might_ not support direct rendering for it. That means you may not be able to boost graphics performance by very much. If this turns out to be true, using fancy UI features (eg compiz, beryl, etc.) will be impractically processor-intensive. :-(

Additionally, I've noticed some suggestions that the SiS driver may not be particularly stable. Perhaps Ubuntu didn't make such a bad decision after all, when it opted for the generic driver?

On the positive side, that driver *does* seem to support your hardware, so you should be able to use it to increase your maximum screen resolution. Check your monitor & graphics adapter manuals to see what the maximum usable resolution is, and give it a shot.

> **Kristian9K said:**
> I also tried setting switching the "vesa" driver to "sis" in Xorg, which made the active parts of the screen flicker.Hmm. Could this be a problem with your refresh rate? It's hard to judge without actually being able to *see* it. :-(

---

### Post by Kristian9K on 2007-05-10
Found the max resolution and changed Xorg accordingly. Thanks for this tip. And yes, this is a low-end system, but it feels so much better to know that it's configured right - which it should be now. Last thing I miss is the VRAM thing, which I will get back to you about if I can't figure it out myself.

As for the slightly disappointing performance of my pc, I've noticed that my (old) HD is making "those" noises :(. So the next logical step is figuring out how to check it for errors... will do that now. Again, thanks for guiding me through this, and I hope our conversation here can help others.

PS: how do I update Linux' SiS driver so I can test it from time to time?

---

### Post by kidders on 2007-05-10
> **Kristian9K said:**
> it feels so much better to know that it's configured rightYay! :-) Guard that xorg.conf with your life! Hehe. I'm glad I was able to help.

> **Kristian9K said:**
> I've noticed that my (old) HD is making "those" noisesOh dear. You can use **fsck** to check your filesystems. _Be sure to read the man pages first though_. You might also be interested in one of the various SMART tools (assuming your hard disks support SMART), or a hard disk temperature monitor.

> **Kristian9K said:**
> how do I update Linux' SiS driver so I can test it from time to time?Assuming you're using the kernel driver, it will be updated along with the rest of your Ubuntu, as new kernels are released. This is one of the (many) reasons your bootloader menu gets longer and longer as time goes by ... Ubuntu is very reluctant to delete old kernels without being instructed to do so ... if an update breaks something (eg your graphics), you can revert immediately to the previous kernel.

---

