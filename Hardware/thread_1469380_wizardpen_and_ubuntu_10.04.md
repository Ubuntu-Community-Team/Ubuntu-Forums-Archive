---
title: "wizardpen and ubuntu 10.04"
date: 2010-05-02
forum: Hardware
---

### Post by teniente on 2010-05-02
after installing
xserver-xorg-input-wizardpen                                               0.7.3-1ubuntu1 
pen pressure works great in gimp, mypaint, synfig,
but not working with pencil and krita...
In Ubuntu 9.10 helped editing the file /etc/hal/fdi/policy/99-x11-wizardpen.fdi
I just added
 "<merge key="info.product" type="string">stylus</merge>
<merge key="input.x11_options.SendCoreEvents"  type="string">true</merge>"
The  fact is that QT does not see device names other than "stylus", "pen" and "eraser".

Tablet - G-Pen 450 (UC-LOGIC Tablet WP5540U)
Any ideas?

---

### Post by Favux on 2010-05-02
Hi teniente,

Welcome to Ubuntu forums!

So you installed the Ubuntu package xserver-xorg-input-wizardpen 0.7.3-1ubuntu1 through Synaptic Package Manager and it works?  Great!  Others like the Aiptek and Waltop tablets aren't as lucky.

Since HAL and .fdi files are no more configuration is through .conf files in xorg.conf.d or in xorg.conf.  You want to check in, I think it is, "/usr/lib/X11/xorg.conf.d/" for a wizardpen.conf.  Post it's name, location and contents and we can see if we can add the options you need to it.  If that fails we can do it through the xorg.conf.

Hope this helps.

---

### Post by teniente on 2010-05-03
Hello, Favux!
thanks  for the reply.
To  install the package, I added doctormo repository ([http://ppa.launchpad.net/doctormo/xorg-wizardpen/ubuntu](http://ppa.launchpad.net/doctormo/xorg-wizardpen/ubuntu)).
File 70-wizardpen.conf is located in /usr/lib/X11/xorg.conf.d:

Section "InputClass"
   Identifier "wizardpen"
   MatchIsTablet "on"
   MatchDevicePath "/dev/input/event*"
   MatchVendor "UC-LOGIC|KYE Systems|Ace Cad"
   Driver "wizardpen"
EndSection
Section "InputClass"
   Identifier "wizardpen ignore mouse dev"
   MatchIsTablet "on"
   MatchDevicePath "/dev/input/mouse*"
   MatchVendor "UC-LOGIC|KYE Systems|Ace Cad"
   Driver ""
EndSection

More config files, installed  by this package:

/etc/udev/rules.d/70-xorg-wizardpen-settings.rules
/lib/udev/rules.d/67-xorg-wizardpen.rules
/usr/lib/X11/xorg.conf.d/70-wizardpen.conf
/usr/share/hal/fdi/preprobe/10osvendor/10-wizardpen-devices.fdi
/usr/share/hal/fdi/preprobe/10osvendor/11-wizardpen-config.fdi
/usr/share/hal/fdi/preprobe/20thirdparty/10-wizardpen-devices.fdi
/usr/share/hal/fdi/preprobe/20thirdparty/11-wizardpen-config.fdi

---

### Post by Favux on 2010-05-03
Hi teniente,

> I added doctormo repository 
Great, DoctorMo comes through again!

I don't think you need to worry about:
```
<merge key="input.x11_options.SendCoreEvents" type="string">true</merge>"
```
because I believe Xserver 1.7 assumes that by default now.

For:
```
<merge key="info.product" type="string">stylus</merge>
```
looking at the [XInputConfiguration wiki]("https://wiki.kubuntu.org/X/InputConfiguration") it looks like it may be for the stylus, with luck:
```
ENV{info.product}="stylus"
```
If so it would probably go into the first snippet/section like so:
```
Driver "wizardpen"
ENV{info.product}="stylus"
EndSection
```
Glad you listed the other configuration files.  We might want to look at udev rules for example.

Be sure to back up 70-wizardpen.conf and be ready to restore it from the command line in case we break something.

---

### Post by teniente on 2010-05-03
In this case after  rebooting the X-server does not start...:confused:

---

### Post by Favux on 2010-05-03
Hi teniente,

Sorry.  :(

The format must be wrong, or it's an option not available in a .conf file.  That's why I warned you to back up and linked you to the XInputConfiguration wiki.  Still learning the syntax.

I'm pretty sure that adding xorg.conf sections with say an Identifier "stylus" does give you stylus on 'xinput --list'.

---

### Post by teniente on 2010-05-03
xorg.conf does not exist, create new?

---

### Post by Favux on 2010-05-03
Yes using:
```
gksudo gedit /etc/X11/xorg.conf
```
But first decide what to put in it.  You'll need an appropriate "ServerLayout" in addition to the WizardPen section.

---

### Post by teniente on 2010-05-03
like  this:
Section "InputDevice"
    Identifier    "stylus"
    Option        "SendCoreEvents" "true" 
    Driver        "wizardpen"
    Option        "Device"    "/dev/input9"
    Option        "TopX"        "2799"
    Option        "TopY"        "4259"
    Option        "BottomX"    "30756"
    Option        "BottomY"    "29521"
    Option        "MaxX"        "30756"
    Option        "MaxY"        "29521"
EndSection

Section "ServerLayout"
    Identifier    "Default Layout"
    Screen        "Default Screen"
    InputDevice    "stylus"
EndSection

???

---

### Post by Favux on 2010-05-03
That looks about right, except "ServerLayout" probably should be like:
```
Section "ServerLayout"
	Identifier	"X.org Configured"
InputDevice "stylus"
EndSection

```
Hopefully it'll boot and then 'xinput --list' will show stylus.

---

### Post by teniente on 2010-05-03
sad,  but not yet...

---

### Post by Favux on 2010-05-03
Darn.  I know at least one person said that worked.  OK, time to put the old thinking caps on.  I'll keep an eye peeled in case someone comes up with something.

---

### Post by teniente on 2010-05-03
thanks,  I will also dig further.

---

### Post by al.do on 2010-05-07
Please try with this solution. ["]**_[COLOR="Blue"]Link[/COLOR]_**]("http://ubuntuforums.org/showthread.php?t=1475433)

---

### Post by teniente on 2010-05-08
Thanks, al.do, in my case tablet work, but
"pen pressure works great in gimp, mypaint, synfig,
but not working with pencil and krita...".
"The  fact is that QT does not see device names other than "stylus",  "pen" and "eraser"."
Can You draw with pressure in Krita?

---

### Post by al.do on 2010-05-09
No, I cant. Searching in internet I found about a option in **Settings>Configure_Krita>Tablet** but the "Tablet" option in my Krita version don't appears.

---

### Post by teniente on 2010-05-09
I have the same;
ubuntu 9.10 situation described in message#1;
must inform xinput about the device "stylus"...:confused:

---

### Post by andrew87 on 2010-05-26
Hello

I'm Italian, I'm sorry for my bad English, I hope that you can  understand me...

I've got the Trust TB-6300 tablet + mouse, I minutely followed this  guide:

[]("https://help.ubuntu.com/community/TabletSetupWizardpen")[https://help.ubuntu.com/community/TabletSetupWizardpen](https://help.ubuntu.com/community/TabletSetupWizardpen)

My problem is the sequent: the pen work correctly, but the mouse, when I  try to move, put the cursor in the top left corner of the screen, and  don't move at all... the button seems to work correctly too.

I edited my xorg.conf file (even if this edit don't seems to serve)
I edited my 70-wizardpen.conf file whit the correct addres of device.
I try to change MathIsTablet whit MatchIsPointer too

Nothing... the cursor remains stuck in that damn  corner (only with  mouse).
But I tried to do a particular edit to xorg.conf file:

>  			 				Section "ServerFlags"
        Option "AutoAddDevices" "False" 			 		

And when I rebooted the system, magically the mouse work perfectly!!!!   but the pen and the keyboard didn't work no more...

I'm going crazy... really.. what can I do?

---

### Post by teniente on 2010-05-28
Which version of the Wizardpen?

---

### Post by andrew87 on 2010-06-02
Sorry for my late reply... 
So, I used the latest version, from "lucid" repo...

However, there are some news...
This is my 70-wizardpen.conf file:

> #Section "InputClass"
#Identifier "tablet"
#MatchIsPointer "on"
#MatchDevicePath "/dev/input/event4"
#MatchVendor "UC-LOGIC|KYE Systems|Ace Cad"
#Driver "wizardpen"
#Option "TopX" "0"
#Option "TopY" "0"
#Option "BottomX" "32747"
#Option "BottomY" "32762"
#Option "TopZ" "10"
#Option "BottomZ" "1023"
#EndSection

Section "InputClass"
Identifier "wizardpen ignore mouse dev"
MatchIsTablet "on"
MatchDevicePath "/dev/input/mouse1"
MatchVendor "UC-LOGIC|KYE Systems|Ace Cad"
Driver "mouse"
Option         "ZAxisMapping" "4 5"
EndSection 

As you can see I commented the tablet part, and I added "mouse" rule in driver sections, and now the tablet work perfectly as mouse, but not (of course) as tablet...
If I comment the first part of this file, the pen works and mouse no...
If I remove all comments, the pen works, but the mouse can move the cursor only around the last point where the pen has left it, after, cursor return in that point....
It seems that the can't work contemporaneously... 

Can they work together one day?

p.s. I'm not sure if "comment" is the right verb for indicate adding # character in the beginning of the line

---

### Post by Favux on 2010-06-02
Hi andrew87,

Can you clear something up for me?  Is the mouse a WizardPen tablet mouse?  In other words is the mouse a device that came with the tablet along with the stylus/pen?

---

### Post by andrew87 on 2010-06-03
Of course, the mouse is supplied with the tablet and the pen... and it works only on the tablet...

This is my tablet: [http://www.trust.com/products/product.aspx?artnr=15357](http://www.trust.com/products/product.aspx?artnr=15357)

However  everything works on windows.

---

### Post by Favux on 2010-06-03
Hi andrew87,

So shouldn't:
```
Driver "mouse"
```
be
```
Driver "wizardpen"
```
I'm guessing if you look at Xorg.0.log in /var/log you'll see that the evdev driver has your mouse when using the non-wizardpen driver "mouse".

But over and above that you may be running into a limitation of the .conf files (70-wizardpen.conf).  I'm going to guess that the stylus and mouse signals are multi-plexed over the same channel from the tablet.  That would make one the dependent device of the other.  And in .conf files there is currently a limitation:  you cannot configure the dependent device, only the primary device.  If you're lucky I'm wrong and they are two separate devices on two channels.  Also do you know if the wizardpen driver supports the tablet mouse?  In other words did the tablet mouse work on other versions?

The only way currently to configure dependent devices is to use the xorg.conf.  You say you tried that, what did your xorg.conf look like?

I think the limitation has been addressed and is in Xorg's Xserver git master now, but who knows when or if the fix will make it to Lucid.  Also the driver needs to support the Xserver change and I doubt the current wizardpen driver for Lucid does.

---

### Post by Offoffoff on 2010-07-04
I have [5543:0004] "UC-Logic Technology Corp. Genius MousePen 5x4 Tablet", it is brand name Genius EasyPen i405. WizardPen driver was excellently suitable for me in Ubuntu Linux 9.10, but now in Ubuntu Linux 10.04 I have the same problem as you, guys: pad pointer runs to the left upper corner of screen and stops there. Is it driver problem or...? How to fix it gently?

---

### Post by drpjkurian on 2011-06-10
Install wizardpen tablet support from ubuntu software centre

---

