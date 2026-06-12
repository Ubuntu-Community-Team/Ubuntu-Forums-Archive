---
title: "How to change monitor brightness, contrast, etc?"
date: 2006-03-24
forum: Hardware &amp; Laptops
---

### Post by fergus.b on 2006-03-24
Hi 

I have an Acer laptop (Aspire 1362LC) and the LCD screen's default setting is too bright / too much contrast. In windows I could go to display settings and adjust the screen gamma down 20% and this would be perfect. Under Linux I can use the keyboard shortcut to bring the brightness down but this just makes the screen duller. I need more fine grained control of the settings. Is there a way to adjust the brightness, contrast, gamma, etc, in X?

Thanks.

---

### Post by saurabhnanda on 2006-03-31
I, too, have an Acer laptop with the same problem. I can use the Fn+Left Arrow to decrease brightness and Fn+Right arrow to increase brightness. I couldn't find anything similar for changing the contrast.

To change the gamma try the following command:
$ xgamma -help

I usually like it with the following settings:
$xgamma -gamma 0.6

---

### Post by 3rdcoast on 2006-04-12
[QUOTE=saurabhnanda]I, too, have an Acer laptop with the same problem. I can use the Fn+Left Arrow to decrease brightness and Fn+Right arrow to increase brightness. I couldn't find anything similar for changing the contrast.

To change the gamma try the following command:
$ xgamma -help

I usually like it with the following settings:
$xgamma -gamma 0.6[/QUOTE]



This really helped me, thanks    :D

---

### Post by grinias on 2006-08-22
I have an Acer laptop too. For permanent change gamma to 0.6 you could add
to the Monitor section of /etc/X11/xorg.conf the line

Gamma 0.6

I tested it with fglrx but i think it works with ati (or any other) driver too.

---

### Post by bluntu on 2006-08-25
how do I change the overall BRIGHTNESS?

My monitor is too bright and it's hurting my eyes. My monitor brightness is at its lowest.. on windows there is a program that I can use to change the overall brightness. How do I do it under Unbuntu?

---

### Post by fatlard on 2006-09-14
I have a Sony Viao Laptop.  I was able to change the brightness on my LCD by going to System, then Power Management.  I was able to bring it to 75%

---

### Post by supergrover on 2006-09-16
Hello,

I have a HP TC1100 Tablet PC. I can't seem to find out how to change the brightness anywhere. Also, I can not get the screen to blank (backlight turned off) either. The screen brightness settings are not listed in the Gnome Power Management Preferences application. I have searched a bit online and other people have stated that it does work, but no one has been able to explain how or why. Does anyone have any recommendations where I should look first to try and get LCD backlight control working?

I am running Dapper 6.06.1 LTS, i386 or i686 kernel (both work), Xgl (works perfectly!!!), and the Nvidia 1.0-8762 drivers.

Thank you in advance!!!

Regards,

Michael

---

### Post by orb9220 on 2006-09-17
Can't remember how but is in the forums.
Did you install nvidia-settings ?
In term type   nvidia-settings
and a panel should popup and select X server Color Correction  and brightness ,Constrast,Gamma are there.

---

### Post by supergrover on 2006-09-17
> **orb9220 said:**
> Can't remember how but is in the forums.
Did you install nvidia-settings ?
In term type   nvidia-settings
and a panel should popup and select X server Color Correction  and brightness ,Constrast,Gamma are there.

Thanks for the tip. While these settings are very important for calibrating the screen, in my case I am trying to control the brightness of the LCD backlight (to save battery life) and also be able to poweroff the display completely when the computer is idle. Under Windows HP/Compaq provided a utility originally called Qmenu to let you control the backlight level with the scroll knob on the side of the tablet. There is a program for Linux called Tabatha to mimic the menu, but, I don't see anything for backlight control. I believe backlight control should be listed in the Gnome Power Manager, but mine doesn't have it listed there.

Thanks!

---

### Post by galileon on 2007-04-02
you could write a script to edit ~/.nvidia-settings-rc, and call nvidia-settings --load-config-only

and add a button in tabatha for it...

i also have a tc1100, ill try to do it later...

---

### Post by jjordan on 2007-04-02
To control the LCD Backlight brightness open a terminal and type in the following:

**sudo echo 4 > /proc/acpi/video/GFX0/LCD/brightness**

This will set the LCD Backlight brigtness to midrange on "most" laptops (those that support ACPI control of Backlight brightness)

The range is 1 to 8, 1 being dimest and 8 being brightest.

You can set up a simple script to increment or decrement the number and then call it from a hotkey or menu item.

OK, now lets look at what we are actually doing:

the **sudo** gives you temporary root access, "Super User DO" (not quite this simple but this is good enough for now) You will be asked for a password just use your normal password**
the **echo** is going to write whaterver follows it to the screen (standard out)
the **>** redirects the output to a file instead of the screen causing it to replace what was in the file.
the **4** is what we are writing into the file (this could be anything from 1 to 8 )
the **/proc/acpi/video/GFX0/LCD/brightness** is the file that the acpi damen checks perodically to control the brightness of the screen backlight.


If this does not work for you laptop search for your laptop and "acpi"  to figure out if your laptop supports acpi.  Lastly, your "brightness" file could be located in a slightly different location.

** this assumes you have admin access, if you installed Ubuntu then you should have it.

-j

---

### Post by breals on 2007-04-06
> **grinias said:**
> I have an Acer laptop too. For permanent change gamma to 0.6 you could add
to the Monitor section of /etc/X11/xorg.conf the line

Gamma 0.6

I tested it with fglrx but i think it works with ati (or any other) driver too.

Can someone show me how to make this permanent?

This is my config section for the monitor:
> 
Section "Monitor"
	Identifier	"Generic Monitor"
	Option		"DPMS"
	Gamma		0.6
EndSection

I'm trying to make this: "$xgamma -gamma 0.6" permanent on startup so I don't have to set it everytime. 

Thanks,

Bill

---

### Post by xkrwlng on 2007-04-17
> **jjordan said:**
> To control the LCD Backlight brightness open a terminal and type in the following:

**sudo echo 4 > /proc/acpi/video/GFX0/LCD/brightness**

This will set the LCD Backlight brigtness to midrange on "most" laptops (those that support ACPI control of Backlight brightness)

The range is 1 to 8, 1 being dimest and 8 being brightest.

You can set up a simple script to increment or decrement the number and then call it from a hotkey or menu item.

OK, now lets look at what we are actually doing:

the **sudo** gives you temporary root access, "Super User DO" (not quite this simple but this is good enough for now) You will be asked for a password just use your normal password**
the **echo** is going to write whaterver follows it to the screen (standard out)
the **>** redirects the output to a file instead of the screen causing it to replace what was in the file.
the **4** is what we are writing into the file (this could be anything from 1 to 8 )
the **/proc/acpi/video/GFX0/LCD/brightness** is the file that the acpi damen checks perodically to control the brightness of the screen backlight.


If this does not work for you laptop search for your laptop and "acpi"  to figure out if your laptop supports acpi.  Lastly, your "brightness" file could be located in a slightly different location.

** this assumes you have admin access, if you installed Ubuntu then you should have it.

-j
the "gamma" terminal command previously mentioned barely has any affect at all on my screen brightness...barely noticeable.  All the other solutions offered, including the one quoted above, haven't worked for me.

Why doesn't Ubuntu have a "Brightness/Contrast" option under System>>Preferences?  I find it hard to believe they could have left such an obvious feature out of the operating system. :confused:

---

### Post by galileon on 2007-04-17
there is such an option in kde! i'm by no means a fan of kde myself, but i recently moved my tablet to kubuntu, in preparation for the big move to kde4, and its working charms now.

---

### Post by xkrwlng on 2007-04-17
> **galileon said:**
> there is such an option in kde! i'm by no means a fan of kde myself, but i recently moved my tablet to kubuntu, in preparation for the big move to kde4, and its working charms now.
so, the option is in kubuntu, but not ubuntu?  that kind of sucks...

---

