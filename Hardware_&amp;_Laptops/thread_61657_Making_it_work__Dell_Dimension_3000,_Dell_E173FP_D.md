---
title: "Making it work:  Dell Dimension 3000, Dell E173FP Display, w/i810 display driver"
date: 2005-09-01
forum: Hardware &amp; Laptops
---

### Post by orev on 2005-09-01
Dell Dimension 3000, Dell E173FP Display, w/i810 display driver (82865G Integrated Graphics and A02 BIOS)

To change resolutions and get a nice display image:

Open Terminal, and type:  sudo gedit /etc/X11/xorg.conf

Find the section below:

```
Section "Monitor"
	Identifier	"Dell E173FP"
	Option		"DPMS"
EndSection
```


And change to:

```
Section "Monitor"
	Identifier	"Dell E173FP"
	Option		"DPMS"
	HorizSync       28-49
        VertRefresh     43-72
        DisplaySize     338 273
EndSection
```


Restart x by <ctrl> <alt> <backspace>, or by restarting your computer (recommended).

[Before I changed the xorg.conf, I changed the "Onbroard Video Buffer" from 1MB to 8MB in the BIOS.  To do this, press <F2> on system boot, press <enter> on the "Integrated Devices (LegacySelect Options)", then down arrow to move to the "Onbroard Video Buffer", right arrow to change the 1MB to 8MB, hit <esc> twice, press <return> to save the changes.]

This may also work with Dell E171FP and E172FP displays.  To use with Dell E15FP displays, change the "DisplaySize" to the mm measurements of your display.

---

### Post by Hamman on 2005-09-01
[QUOTE=orev]Dell Dimension 3000, Dell E173FP Display, w/i810 display driver (82865G Integrated Graphics and A02 BIOS)

To change resolutions and get a nice display image:

Open Terminal, and type:  sudo gedit /etc/X11/xorg.conf

Find the section below:

```
Section "Monitor"
	Identifier	"Dell E173FP"
	Option		"DPMS"
EndSection
```


And change to:

```
Section "Monitor"
	Identifier	"Dell E173FP"
	Option		"DPMS"
	HorizSync       28-49
        VertRefresh     43-72
        DisplaySize     338 273
EndSection
```


Restart x by <ctrl> <alt> <backspace>, or by restarting your computer (recommended).

[Before I changed the xorg.conf, I changed the "Onbroard Video Buffer" from 1MB to 8MB in the BIOS.  To do this, press <F2> on system boot, press <enter> on the "Integrated Devices (LegacySelect Options)", then down arrow to move to the "Onbroard Video Buffer", right arrow to change the 1MB to 8MB, hit <esc> twice, press <return> to save the changes.]

This may also work with Dell E171FP and E172FP displays.  To use with Dell E15FP displays, change the "DisplaySize" to the mm measurements of your display.[/QUOTE]

 I don't own any of this hardware, just wanted to encourage you to keep sharing your experiences with the rest of the community!
BTW, shouldn't this be in Customization, Tips and Tricks?

---

### Post by Heliane on 2005-12-16
Hello orev,

I am completely new to Ubuntu/Kubuntu, meaning I would like to be a new user. Unfortunately, my display (Dell E173FP; Dell Dimension 5100) doesn't get round to displaying anything apart from colours and stripes.

I tried Ubuntu 5.04 and, as this didn't work, Kubuntu 5.10, which didn't work either. So I removed both distributions from my hard drive.

As I would really like to use either Ubuntu or Kubuntu (I haven't made up my mind which one yet), can I use the commands you describe in your posting during the installation process of Ubuntu/Kubuntu? If so, how? (A problem might be that I'm used to Windows or MacOS graphical user interfaces.)

Thank you very much and have a fine day,

Heliane

---

### Post by orev on 2005-12-16
[http://ubuntuforums.org/showthread.php?t=55837&highlight=Intel+Graphics+950]("http://ubuntuforums.org/showthread.php?t=55837&highlight=Intel+Graphics+950")

The link above is to another forum posting where someone made the graphics card in their 5100 work.

I would suggest trying the ideas posted here.

Don't give up - ubuntu is worth it!

Also, if you are newer to ubuntu/kunbuntu and/or linux, ubuntu may be a better bet for you to start because it currently has better documentation on the web - so, more help.  You can always install ubuntu and then upgrade to kubuntu.

I run kubuntu 5.10 because I llike the interface and the functionality.

---

### Post by Heliane on 2005-12-16
[QUOTE=orev][http://ubuntuforums.org/showthread.php?t=55837&highlight=Intel+Graphics+950]("http://ubuntuforums.org/showthread.php?t=55837&highlight=Intel+Graphics+950")

The link above is to another forum posting where someone made the graphics card in their 5100 work.

I would suggest trying the ideas posted here.

Don't give up - ubuntu is worth it!

Also, if you are newer to ubuntu/kunbuntu and/or linux, ubuntu may be a better bet for you to start because it currently has better documentation on the web - so, more help.  You can always install ubuntu and then upgrade to kubuntu.

I run kubuntu 5.10 because I llike the interface and the functionality.[/QUOTE]
Sorry, I forgot. My system hasn't an Intel graphics controller but an NVidia GeForce 6800.

---

### Post by Heliane on 2005-12-18
Hello there,

I managed to get both Ubuntu 5.10 and Kubuntu 5.10 live systems running, GUI, Gnome and KDE desktops, and internet connection, and everything.

But when regularly installing Kubuntu 5.10 to my hard drive this is just not possible. Still, I get those colourful stripes and lines and cannot use the GUI whatsoever.

How can I get to the command "sudo gedit /ect/X11/xorg.conf" via the shell?

Please help. I'm desperate and get the feeling that I have to throw out Linux from my hard drive again and use Windows instead. Sorry, but Windows works at least.

Thanks,

Heliane

---

### Post by orev on 2005-12-19
To get your graphics card working, you will need to install some hardware drivers that are not able to be included with ubuntu:

(The info below was copied from [this ubuntu wiki article]("https://wiki.ubuntu.com/InstallingUbuntuOnADellPrecisionM70"))

[B]Installing the Proprietary NVIDIA drivers

It is recommended that you install Ubuntu from scratch. After partitioning your drive appropriately, use the Ubuntu installation CD to make a default configuration. At this stage, be sure that Ubuntu correctly configures your internet connection.

After that, the installation will reboot the computer. Select the standard bootup (the first option). When the GNOME install screen comes up, do not log in. Instead, select the "reboot" option from the bottom of the screen to reboot the computer a second time.

When the GRUB screen comes up again, boot into recovery mode (the second option). A text-only screen will come up. Use this following command to install the new NVIDIA drivers:

```
apt-get install nvidia-glx
```

Then edit the xorg configuration file.

```
pico /etc/X11/xorg.conf
```

Find the word "nv" and change it to "nvidia". Then find the lines

```
Load "GLCore"
Load "dri"
```

Comment them out:

```
# Load "GLCore"
# Load "dri"
```[/B]

---

### Post by Heliane on 2007-11-01
Hello there!
After having installed Gutsy Gibbon, everything works fine, even the newly purchased WLAN USB stick. (Well, apart from the CanoScan LiDE 90. But I'm sure that'll work out in future, too.)
I'm glad being finally independent from Microsoft, and Apple, if it comes to that.
Thanks and good luck to all!
Heliane

---

