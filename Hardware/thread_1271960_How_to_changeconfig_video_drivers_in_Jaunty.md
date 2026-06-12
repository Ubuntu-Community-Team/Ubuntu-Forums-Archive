---
title: "How to change/config video drivers in Jaunty?"
date: 2009-09-21
forum: Hardware
---

### Post by greenstar on 2009-09-21
I no longer have any idea how to do manual video driver config.

Back in the day, I used to just edit xorg.conf with a text editor: ```
sudo gedit /etc/X11/xorg.conf
```Up until a few versions ago, I could also use the following command:```
sudo dpkg-reconfigure xserver-xorg
```Then that was deprecated. Then I read about people using ```
sudo dpkg-reconfigure -phigh xserver-xorg
``` Using that never accomplished anything for me.

I don't know where video driver config is hidden anymore.

Problem is that I have a laptop whose video output is less than desirable and I'd like to try a different video driver than the one currently in use. I no longer know how to do this. I need to know how to do this manually so that I can configure a video driver for any system I work on. Instructions for terminal are preferred, but help in any form will be appreciated.

Thanks for your time & assistance.

---

### Post by greenstar on 2009-09-22
Specifically I'm wanting to test the vesa driver against the sis driver that is currently in use as autodetected and selected during installation. The laptop in question does in fact have a sis chipset, but the driver seems inadequate.

---

### Post by Wlerin on 2009-09-23
I'm also interested in the reply to this, as my xorg.conf no longer seems to contain any useful data.

---

### Post by greenstar on 2009-10-14
Almost 200 views, only 1 person other than myself has replied and still no closer to the answer. There are apparently quite a few people who have the same question. Someone's got to know the answer.

Anyone care to step up and help us out here?

---

### Post by drbobb on 2009-10-14
Ok here's the deal.

You can generate a template xorg.conf by getting a root shell (run `sudo -i' in a terminal) and invoking `X :1 -configure'. You can actually omit the `:1' if you use a text-mode login and shut down gdm/kdm before you do this, but never mind. This will make your screen blank and/or flicker for a moment, but afterwards you will find a file xorg.conf.new or so in root's home dir (/root). Copy that as /etc/X11/xorg.conf and edit to your heart's desire. After you restart X, or reboot, your edits will take effect. If you mess up (a stray comma, or omitted "), X won't start anymore - but you probably know that. For the benefit of other readers: in such a case, just log in to text mode, and move or delete /etc/X11/xorg.conf out of the way. Of course it might be better to fix it, but this will work if you have no idea how to fix it.

Now, if you have a SiS graphics card and see something like

01:00.0 VGA compatible controller: Silicon Integrated Systems [SiS] 661/741/760 PCI/AGP or 662/761Gx PCIE VGA Display Adapter

in the output of `lspci', I have bad news for you. My research indicates that support for those cards has been broken since Intrepid and is not likely to be fixed, ever. I have tried all possible tricks on Jaunty, and no matter what I do, video performance is seriously degraded relative to Hardy. At least on my machine, vesa is unable to provide the correct resolution for my panel (1280x800); the sis driver by itself produces kaleidoscopic colors; what sort of works is running the sis X11 driver in tandem with the sisfb kernel module, but I still get flashing lines at the screen's edges when playing videos or scrolling stuff quickly. Alternatively, you can modprobe sisfb and tell x.org to use the fbdev driver. Video then gets choppy and tends to lag behind sound, esp. in fullscreen mode.

I just verified that these issues persist in Karmic, there has been no improvement.

The bottom line, I'm afraid, is - look forward to shopping for a new laptop.

---

### Post by drbobb on 2009-10-14
Oh and one addendum: currently I am running the xorg core packages from Hardy (SiS video card works correctly) in an otherwise Jaunty system. This causes serious problems though, notably there is some weirdness in keyboard behavior, that I have been able to fix somehow for KDE (but not for Gnome).

---

### Post by jwalit on 2009-12-24
How to enable vesa in uabntu 9.0.4 
               and 
How to set 1024*768 resolution
I Have
01:00.0 VGA compatible controller: Silicon Integrated Systems [SiS] 661/741/760 PCI/AGP or 662/761Gx PCIE VGA Display Adapter

my xorg.conf look like 
===========================
Section "Device"
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

---

