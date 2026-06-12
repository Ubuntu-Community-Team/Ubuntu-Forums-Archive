---
title: "The infamous 800x600 max screen resolution"
date: 2008-09-09
forum: Hardware
---

### Post by mtbusche on 2008-09-09
My screen resolution maxes out at 800x600 when I should be able to set it to 1920x1200.

Seems like someone posts this problem every few minutes, but the few posts I've read here and on other forums found via google have not yet solved my problem.

I'm using an nVidia GeForce 7600 GS:

> lspci | grep VGA
01:00.0 VGA compatible controller: nVidia Corporation G73 [GeForce 7600 GS] (rev a2)

And here's my original xorg.conf file (less comments):

Section "InputDevice"
        Identifier      "Generic Keyboard"
        Driver          "kbd"
        Option          "XkbRules"      "xorg"
        Option          "XkbModel"      "pc105"
        Option          "XkbLayout"     "us"
EndSection

Section "InputDevice"
        Identifier      "Configured Mouse"
        Driver          "mouse"
        Option          "CorePointer"
EndSection

Section "Device"
        Identifier      "Configured Video Device"
EndSection

Section "Monitor"
        Identifier      "Configured Monitor"
EndSection

Section "Screen"
        Identifier      "Default Screen"
        Monitor         "Configured Monitor"
        Device          "Configured Video Device"
EndSection

Section "ServerLayout"
        Identifier      "Default Layout"
        Screen          "Default Screen"
EndSection

My graphics card is not THAT old and it was certainly popular card in it's day.  I'm surprised to be having this problem.

I've tried several manual manipulations of the xorg.conf file (suggested in various threads I've come across) but to no avail.  I've also poked around in system->administration->hardware drivers and tried enabling the nvidia accelerated hardware drivers, but this didn't open up any higher resolution display settings.

Any suggstions?

Much thanks,

Matt Busche
Denver, Colorado

---

### Post by divague on 2008-09-09
Try installing nvidia-settings and running it with sudo, there you'll have some options you can change like the resolution of your screen

---

### Post by Infinite Indefinite on 2008-09-09
(*Make a backup of xorg.conf first*).

Have you tried adding subsections, such as:

before the end of Section "Monitor"

  modeline  "1920x1280@60" 25.2 640 656 752 800 480 490 492 525 -vsync -hsync
	Gamma	1.0
EndSection

before the end of Section "Screen"

	Defaultdepth	24
	SubSection "Display"
		Depth	24
		Virtual	1920	1280
		Modes		"1920x1280@60"
	EndSubSection
EndSection

Before the end of Section "screen" #       

	SubSection "Display"
		Depth	24
		Modes		"1920x1280@60"
	EndSubSection
EndSection

Before the end of Section "monitor" #       

  modeline  "1920x1280@60" 25.2 640 656 752 800 480 490 492 525 -vsync -hsync
	Gamma	1.0
EndSection

---

### Post by mtbusche on 2008-09-09
divague,

I guess I forgot to mention I'm a Ubuntu noob -- I have no clue how to do what you are suggesting.  Can you provide me a pointer on how to try this?

Thanks.

------------------------------------

Infinite Indefinite,

At your suggestion, I've set my xorg.conf file to the following:

Section "InputDevice"
        Identifier      "Generic Keyboard"
        Driver          "kbd"
        Option          "XkbRules"      "xorg"
        Option          "XkbModel"      "pc105"
        Option          "XkbLayout"     "us"
EndSection

Section "InputDevice"
        Identifier      "Configured Mouse"
        Driver          "mouse"
        Option          "CorePointer"
EndSection

Section "Device"
        Identifier      "Configured Video Device"
EndSection

Section "Monitor"
        Identifier      "Configured Monitor"
        modeline        "1920x1280@60" 25.2 640 656 752 800 480 490 492 525 -vsync -hsync
        Gamma 1.0
EndSection

Section "Screen"
        Identifier      "Default Screen"
        Monitor         "Configured Monitor"
        Device          "Configured Video Device"
        Defaultdepth 24
        SubSection "Display"
                Depth 24
                Virtual 1920 1280
                Modes "1920x1280@60"
        EndSubSection
EndSection

Section "ServerLayout"
        Identifier      "Default Layout"
        Screen          "Default Screen"
EndSection

THIS actually did affect my display so perhaps I'm getting close, but the visible effect was to expand the virtual size of the screen to, I think, 1920x1200, but only a very very small section of the screen was visible (as if I was zoomed in on, perhaps, the upper left quadrant of the screen).  I had no way to launch applications or even restart the computer from the devoid section of the screen I had access to.  Fortunately, I had already setup SSHD and I was able to login from another machine via an xterminal and restore the original xorg.conf file -- otherwise I would have had no clue how to undo what I had done!

I should say I was somewhat confused by your post as the second half of your suggested changes looked like a cut-n-paste of the first half (with the sections reversed in order).  I assume this was an error in your post.  If not you'll have to point out the difference to my inadequate eyes.

Otherwise, let me know if you see any errors in the above or if you have other suggestions.

Thanks,
Matt Busche
Denver, Colorado

---

### Post by cariboo on 2008-09-09
If you are running hardy in a Applications-->Accessories-->Terminal run:

```
sudo displayconfig-gtk
```

This will allow you to setup the proper resolution.

Jim

---

### Post by tuxxy on 2008-09-09
Have a read of this, it seems that card is supported

[https://help.ubuntu.com/community/BinaryDriverHowto/Nvidia](https://help.ubuntu.com/community/BinaryDriverHowto/Nvidia)

If you think that the driver is installed try installing **nvidia-settings** 

```
sudo apt-get install nvidia-settings
```

then run the application as root and see fi you can edit the resolution here

```
sudo nvidia-settings
```

---

### Post by mtbusche on 2008-09-10
Tuxxy,
Cariboo907,

Well it's working now.

It became clear that I had somehow seriously disturbed something in the display subsystem as I was no longer able to enable the nVidia graphics driver.  So I wiped my hard-drive and reloaded Ubuntu.

This time I decided to try the simplest and most obvious thing first and simply went to the hardware drivers facility and downloaded and enabled the nvidia drivers, and then rebooted the system.

Viola!  Worked like a champ!

I don't know what I could have done to mess things up so badly.  The only file I ever touched manually was xorg.conf and I thought I always restored that to its original form after each failed attempt.

I guess I should have poked around in the configuration menus before attempting to manually manipulate xorg.conf but I also think Ubuntu should have done a better job of loading and configuring the most appropriate drivers for me during the install -- or maybe sent me through a dialogue giving me the option to enable the driver on my first login or something.

In any case, thanks for your patience and all your suggestions.

Matt Busche
Denver, Colorado

---

### Post by Infinite Indefinite on 2008-09-11
> **mtbusche said:**
> divague,

Infinite Indefinite,
I should say I was somewhat confused by your post as the second half of your suggested changes looked like a cut-n-paste of the first half (with the sections reversed in order).  I assume this was an error in your post.  If not you'll have to point out the difference to my inadequate eyes.

Thanks,
Matt Busche
Denver, Colorado

Linux is case sensitive, so "Section "Screen" and "Section "screen"" are two separate sections in xorg.conf

---

