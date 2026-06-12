---
title: "Installing a Lilliput UM-70"
date: 2009-12-25
forum: Hardware
---

### Post by seebor on 2009-12-25
Hey all,
I am trying to install a Lilliput UM-70 (on Ubuntu 9.10), and was wondering if anyone here had any ideas on how to do it. I tried googling it, but most of the results come up non-english (mostly russian it seems), or are just information about the device itself. If anyone has any ideas, please let me know.

Thanks in advance.

---

### Post by seebor on 2009-12-25
I have been doing a little more poking around, and have (I think) install the DisplayLink drivers (libdlo.freedesktop.org), and the little thing is just sitting here happily displaying a green screen at me... I have no idea where to go from here (or if I am even going in the right direction).

I'll keep at it... hopefully I can figure this out.

---

### Post by rengeek on 2009-12-30
Any luck with this? I'm going through the same thing with little success.

---

### Post by seebor on 2009-12-30
unfortunately, I have had no luck thus far. I have tried three or four different things, but the problem comes down to I don't know exactly if they even apply to what I am trying to do.

I have a sneaking suspicion that a part of this is going to include editing the xorg.conf file. I have made (what I think should be) the edits, but no dice.

I intend to keep looking, but for now all i can say is good luck to you.

---

### Post by brett.a.rogers on 2009-12-31
Quick question regarding the monitor:

Does it require that both USB connections are plugged in, or will it run off of just one?

I am looking at getting one of these, but my USB ports are limited.

TIA,
brett

---

### Post by Skreenname on 2009-12-31
I think I read somewhere that it does work with just one USB plugged in.
But I'd wait until someone who has it responds.


Also, I have a question myself.
Does the Lilliput work as a main monitor?
Briefcase computer would love it if it did.

---

### Post by seebor on 2009-12-31
@brett.a.rogers: I can only answer this in regards to Windows, however I would imagine it is similar in Linux.  It would seem that both USBs need to be plugged in until after you boot your computer, once it is showing a display you can take one of them out.


@Skreenname: In my searching I have read about people using it as a primary display, though I have not tried it myself.

---

### Post by Skreenname on 2009-12-31
Seebor: Awesome, thanks.
So I think I'll take my chances.
Worst case scenario I have an Extra display.

---

### Post by benbois on 2010-01-19
Hi all,

Have a look at this interesting article: [http://mulchman.org/blog/?p=21](http://mulchman.org/blog/?p=21)
Maybe it'll help you..
I'm currently waiting for my Lillput screen, so I can't say that worked for me but..

---

### Post by d98jh on 2010-07-02
I hope all of you have managed to get your screens working. Since this was the first place I looked for info I thought I'd post how I got things working on lucid.

1. Install kernel 2.6.34 (with the new udlfb driver)
32-bit:
```

wget [http://kernel.ubuntu.com/~kernel-ppa/mainline/v2.6.34-lucid/linux-headers-2.6.34-020634_2.6.34-020634_all.deb](http://kernel.ubuntu.com/~kernel-ppa/mainline/v2.6.34-lucid/linux-headers-2.6.34-020634_2.6.34-020634_all.deb)
dpkg -i linux-headers-2.6.34-020634_2.6.34-020634_all.deb

wget [http://kernel.ubuntu.com/~kernel-ppa/mainline/v2.6.34-lucid/linux-headers-2.6.34-020634-generic_2.6.34-020634_i386.deb](http://kernel.ubuntu.com/~kernel-ppa/mainline/v2.6.34-lucid/linux-headers-2.6.34-020634-generic_2.6.34-020634_i386.deb)
dpkg -i linux-headers-2.6.34-020634-generic_2.6.34-020634_i386.deb

wget [http://kernel.ubuntu.com/~kernel-ppa/mainline/v2.6.34-lucid/linux-image-2.6.34-020634-generic_2.6.34-020634_i386.deb](http://kernel.ubuntu.com/~kernel-ppa/mainline/v2.6.34-lucid/linux-image-2.6.34-020634-generic_2.6.34-020634_i386.deb)
dpkg -i linux-image-2.6.34-020634-generic_2.6.34-020634_i386.deb

```
64-bit:
```

wget [http://kernel.ubuntu.com/~kernel-ppa/mainline/v2.6.34-lucid/linux-headers-2.6.34-020634_2.6.34-020634_all.deb](http://kernel.ubuntu.com/~kernel-ppa/mainline/v2.6.34-lucid/linux-headers-2.6.34-020634_2.6.34-020634_all.deb)
dpkg -i linux-headers-2.6.34-020634_2.6.34-020634_all.deb

wget [http://kernel.ubuntu.com/~kernel-ppa/mainline/v2.6.34-lucid/linux-headers-2.6.34-020634-generic_2.6.34-020634_amd64.deb](http://kernel.ubuntu.com/~kernel-ppa/mainline/v2.6.34-lucid/linux-headers-2.6.34-020634-generic_2.6.34-020634_amd64.deb)
dpkg -i linux-headers-2.6.34-020634-generic_2.6.34-020634_amd64.deb

wget [http://kernel.ubuntu.com/~kernel-ppa/mainline/v2.6.34-lucid/linux-image-2.6.34-020634-generic_2.6.34-020634_amd64.deb](http://kernel.ubuntu.com/~kernel-ppa/mainline/v2.6.34-lucid/linux-image-2.6.34-020634-generic_2.6.34-020634_amd64.deb)
dpkg -i linux-image-2.6.34-020634-generic_2.6.34-020634_amd64.deb

```
2. Install X driver
```

sudo apt-get install xserver-xorg-video-displaylink

```
3. Edit /etc/gdm/Init/Default
```

sudo gedit /etc/gdm/Init/Default

```
add the following lines after the gdmwhich definition.

```

XRANDR=`gdmwhich xrandr`
if [ "x$XRANDR" != "x" ] ; then
	$XRANDR -o 0
fi

```
4. Generate xorg.conf (if you don't have one already)
$ sudo X -configure

5. Edit xorg.conf
First add these lines:
```

################ DisplayLink Stuff ###################
Section "Device"
       Identifier      "DisplayLinkDevice"
	Driver 		"displaylink"
       Option  	"fbdev" "/dev/fb1"
EndSection
Section "Monitor"
       Identifier      "DisplayLinkMonitor"
	DisplaySize	152 92
EndSection
Section "Screen"
       Identifier      "DisplayLinkScreen"
	Device          "DisplayLinkDevice"
       Monitor         "DisplayLinkMonitor"
	DefaultDepth	16
	SubSection "Display"
		Viewport   0 0
		Depth     16
		Modes   "800x480"
	EndSubSection
EndSection

```
Then edit your server layout to look something like this

```

Screen		0	"DisplayLinkScreen"
Screen		1	"Screen0" RightOf "DisplayLinkScreen"
Option		"Xinerama" "on"

```
Change the default depth for your other screen to 16.
```

DefaultDepth	16

```
Reboot and enjoy your new sceen :)


Thanks to the people who wrote this:
[http://blogs.aldimna.com/?65a55cf2-3426-4447-b680-d51de33f8064/](http://blogs.aldimna.com/?65a55cf2-3426-4447-b680-d51de33f8064/)
[http://wiki.archlinux.org/index.php/DisplayLink](http://wiki.archlinux.org/index.php/DisplayLink)

---

### Post by swamytk on 2010-07-19
I got it working with minimal steps. Here is how I got it with configuration/log files attached.

[http://karuppuswamy.com/wordpress/2010/07/19/how-to-get-lilliput-displaylink-based-usb-monitor-um-70-17e902a9-working-in-ubuntu-linux/](http://karuppuswamy.com/wordpress/2010/07/19/how-to-get-lilliput-displaylink-based-usb-monitor-um-70-17e902a9-working-in-ubuntu-linux/)

---

### Post by scarf on 2011-03-21
> **d98jh said:**
> I hope all of you have managed to get your screens working. Since this was the first place I looked for info I thought I'd post how I got things working on lucid.


the problem i have with this method is that the kernel there seems out of date and unmaintained.  that doesn't sit well with me.

the problem with the other method mentioned on karuppuswamy.com (as well as d98jh's) is that i do not have an xorg.conf file.  when i try to create one in recovery mode, i get a segmentation fault.

---

### Post by scarf on 2011-03-21
the seg fault was being caused by the displaylink driver, for some reason.  anyway, i uninstalled the displaylink driver (xserver-xorg-video-displaylink) and was able to generate an xorg.conf file.  then i added in the info for the UM-70 and reinstalled the displaylink driver.

this seems to have worked at least in the sense that the UM-70 is now working and has a gdm session running in it.  however, it is defined as 'Screen 0' so it is primary and my main LCD is secondary.  i wanted to reverse this, which i thought would be as easy as changing the layout in the ServerLayout section:

```
Section "ServerLayout"
	Identifier	"Server Layout"
	Screen	0	"Default Screen" 0 0
	Screen  1	"DisplayLinkScreen" RightOf "Default Screen"
	Option		"Xinerama" "Off"
EndSection

```

this makes my main LCD primary gdm login window, but for some reason deactivates the UM-70

---

### Post by STYMIE k on 2011-08-31
Hi D98jH
  I think You've got it apparantly.
Have a couple of questions.
 
3. Edit /etc/gdm/Init/Default

Code:
 
sudo gedit /etc/gdm/Init/Default
My system indicates it does not recognize 'gedit" or command not found in Terminal.
 
add the following lines after the gdmwhich definition.


Code:
XRANDR=`gdmwhich xrandr`if [ "x$XRANDR" != "x" ] ; then	$XRANDR -o 0fi
4. Generate xorg.conf (if you don't have one already)
$ sudo X -configure

5. Edit xorg.conf
First add these lines:

Code:
################ DisplayLink Stuff ###################Section "Device"       Identifier      "DisplayLinkDevice"	Driver 		"displaylink"       Option  	"fbdev" "/dev/fb1"EndSectionSection "Monitor"       Identifier      "DisplayLinkMonitor"	DisplaySize	152 92EndSectionSection "Screen"       Identifier      "DisplayLinkScreen"	Device          "DisplayLinkDevice"       Monitor         "DisplayLinkMonitor"	DefaultDepth	16	SubSection "Display"		Viewport   0 0		Depth     16		Modes   "800x480"	EndSubSectionEndSection
   Assuming If I copied and pasted this above code, what's next? How do I proceed from here or exit out of the terminal? Do I save and exit ? newbie to  Kubuntu 11.04 and Linnux in general. Thanks Much in advance. Been at it for 14 hours now....

---

