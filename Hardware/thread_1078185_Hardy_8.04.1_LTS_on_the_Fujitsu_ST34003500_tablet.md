---
title: "Hardy 8.04.1 LTS on the Fujitsu ST3400/3500 tablet"
date: 2009-02-23
forum: Hardware
---

### Post by bcw on 2009-02-23
**Installing Hardy**

The maximum RAM for the ST3400 is 192M, and 256M for the ST3500.  The desktop install CD will succeed with the ST3500 but fail with the ST3400 (even though you can get it to boot, as I did).  The alternate CD will work for either.

These tablets will not boot off their USB ports.  There are several schemes for installing - I use a USB CDROM, the Fujitsu floppy drive, and a FreeDOS boot diskette with USB drivers, Linld, and a simple batch file - search elsewhere in the forums or the web if you prefer or require another approach - the howtos are out there.  The FreeDOS diskette allows selection of USB drivers to match the USB CDROM I use, the batch file then calls Linld with the parameters to start the installer, and installation proceeds normally after that.  I posted about this method [[COLOR="Red"]**here**[/COLOR]]("http://ubuntuforums.org/showthread.php?t=244918"), and will post a [[COLOR="Red"]revision[/COLOR]]("http://ubuntuforums.org/showthread.php?t=1083441") in a day or so.

As these machines have modest hardware, I use Xubuntu, but any desktop should work.  My instructions below are written for Xubuntu and you may have to translate for other desktops.

Perform a standard Hardy install and boot into the new system.  If you then access this thread from the machine you're installing to, you can directly copy-and-paste the commands and download the files to the machine you're installing on.

I use aptitude as I've read it offers some better package resolution, but you may substitute 'apt-get' for aptitude in the following commands.  On modest hardware, running 'aptitude' in a console will get a text UI for package selection as well - no GUI necessary.

The files referenced in this HowTo are attached to this post as a tar.bz2 archive.  The link to download this will show at the end of the message.  Download this file somewhere and uncompress it:
```
tar -xjf Stylistic.3400-3500.hardy.tar.bz2
```


**Enabling the Touchscreen**

Install the fpit input driver and the setserial utility for the touchscreen:
```
sudo aptitude install xserver-xorg-input-fpit setserial
```

Configure the Touchscreen as a serial device:
```
sudo nano /etc/serial.conf
```
...add this line:
```
/dev/ttyS1 uart 16450 port 0xfd68 irq 5 low_latency baud_base 115200 spd_normal skip_test
```

At the time this is written, the fpit driver is broken for Hardy, but you need the plumbing that comes with the package so install it anyway.  The fix is to replace one corrected file (provided by [[COLOR="Red"]**this thread**[/COLOR]]("http://ubuntuforums.org/showthread.php?t=763380&highlight=Fujitsu+3500+hardy&page=3")):

```
sudo cp <wherever you uncompressed it to>/fpit_drv.so /usr/lib/xorg/modules/input
```

Back up your working xorg.conf file:
```
sudo cp /etc/X11/xorg.conf /etc/X11/xorg.conf.installed
```

... and substitute this one:
```
sudo cp <wherever you uncompressed it to>/xorg.conf /etc/X11
```

Reboot to pick up the changes and verify it's working.  This xorg.conf does not specify the display card chipset, and will work with both the ST3400 & ST3500.


**Text input**

There are several on-screen keyboards available.  I use XVkbd as it's compact and can also provide a keyboard for login.  I have not gotten GOK to work for logins.  There is also a good useable handwriting recognition app called Xstroke, very reminiscent of Grafitti on the Palm.

**XVkbd**
```
sudo aptitude install xvkbd
```

Among other features, this keyboard uses slides as well as taps.  It's worth reading the documenation - this is a capable little program.

The approach to gaining speed with a physical keyboard is to never look at the keys.  This doesn't translate to an on-screen graphic keyboard, so I don't see any point in perpetuating the QWERTY keyboard layout here.  I modified the fitaly layout provided by Tom Sato with XVkbd to give me all the punctuation keys I need for programming.

If you want to use this layout, copy the file:
```
sudo cp <wherever you uncompressed it to>/XVkbd-fitaly.bcw /etc/X11/app-defaults/
```

... and edit this file:
```
sudo nano /etc/X11/app-defaults/XVkbd
```

Change it so it has the second line as shown in bold (if you want another keyboard as default, substitute that - there are many layouts in the /etc/X11/app-defaults folder):
```
#include "XVkbd-common"
**#include "XVkbd-fitaly.bcw"**

```
**Xstroke**

From this thread titled '[[COLOR="Red"]**xstroke 0.6**[/COLOR]]("http://ubuntuforums.org/showthread.php?t=69476&highlight=23meg")', '23meg' (thanks, mate) prepared an Ubuntu .deb file you can download and then install:
```
sudo dpkg -i xstroke_0.6.cvs20040921-2_i386.deb
```

Run this to provide full-screen handwriting recognition:
```
xstroke
```

An icon of a green pencil will appear somewhere in your panel - select it and letters 'abc' are superimposed on it to indicate your strokes will be read as text, select again to remove the 'abc' text and your stylus becomes a mere mouse pointer again.

An advantage to Xstroke is that aside from the little icon in the panel, it takes no screen space.


**De-fanging GKsu**

The default graphical sudo with Gnome & XFCE is GKsu.  The default security setting for GKsu is to disable any screen access while accepting a password - so the on-screen keyboard can't be used to enter your password for any command requiring administrative privileges.  To prevent this, edit this file:
```
sudo nano /usr/share/gconf/schemas/gksu.schemas
```

Change the ninth line from:
```
<default>**false**</default>
```
to:
```
<default>**true**</default>
```

Next, run this command to update the schema:
```
sudo gconf-schemas --register /usr/share/gconf/schemas/gksu.schemas
```

KDE does not have this issue.


**Touchscreen log-in**

I use XVkbd as my login keyboard.  Gnome & XFCE use the GDM login manager, and KDE uses KDM.

With GDM, you can't use a Theme - the keyboard won't show.  However you can have a color or image as background.  From the Xubuntu main menu, select '**Applications - Settings - Login Window**'.  In the '**Local**' tab, change the Style to one of the '**Plain**' choices, and Select '**Set position of the window**'.  Enter 100 for x and 5 for y.  Make any other changes you like, such as color or background.  I lock the position of the window and disable showing the title bar (it's just taking up space on screen).  'Alt-C' closes the dialog when you are finished (this dialog's buttons are off screen at the bottom with the SVGA resolution display) or you can just select the 'X' in the title bar.

There is a bug that forces the maximum X value to 100.  If the login window isn't as you like after this, edit the file:
```
sudo nano /etc/gdm/gdm.conf-custom
```

Now you can set the **PositionX** & **PositionY** values as you like without interference.  Setting them in the dialog populates the lines in the file initially, so make the changes in the dialog anyway before editing the file.

Edit this file:
```
sudo nano /etc/gdm/Init/Default
```

... at the end of the file, add the lines as shown in bold (ok, you don't need the comment):

```
fi

[B]# Provide an on-screen keyboard for logins
sleep 10 && /usr/bin/xvkbd -geometry -5-5 &
[/B]
exit 0
```

Note: If you don't use the 'sleep 10' statement, the keyboard may appear first and then be obscured by the login window.  You might shorten the time after you see how your system behaves.

The geometry arguments are for my keyboard layout, with the login window position I set in the gdm.conf-custom file.  You may want the two windows switched left-to-right (I'm left-handed), or have a different keyboard size.

If you need to tweak this, I recommend attaching a physical keyboard, and using a console (Ctrl-Alt-F1) for editing.  Edit the file from the console as above, then restart GDM:
```
sudo nano /etc/init.d/gdm restart
```

... after the first round in the console, just press the 'up' arrow key twice to get the edit line back.  Repeat as needed...


**KDM**

To have the keyboard appear edit this file:
```
sudo nano /etc/kde3/kdm/Xsetup
```

... add this line after the first few lines:
```
/usr/bin/xvkbd -geometry +260-0 -no-keypad &
```

Change the geometry argument as you like later.

To remove the keyboard after logging in, edit this file:
```
sudo nano /etc/kde3/kdm/Xstartup
```

... add this line after the first few lines:
```
kill `ps -u root | grep xvkbd | cut -b 1-5`
```

KDM does not appear to have problems displaying the keyboard while using a theme.


**Power management**

These machines are old enough to miss the cutoff date, but they do work with acpi.  To enable this, edit this file:
```
sudo nano /boot/grub/menu.lst
```

... find these lines, and add these parameters:
```
## additional options to use with the default boot option, but not with the
## alternatives
## e.g. defoptions=vga=791 resume=/dev/hda5
# defoptions=quiet splash **apm=off acpi=force**
```

Then run this command:
```
sudo update-grub
```


**Useability tips**

**-Add a Window list to the panel**
Both XFCE & KDE provide a panel widget to show a list of the open windows from a drop-down menu (Gnome probably does, but I don't use it and don't know).  I find this very useful for switching windows with a stylus - particularly on the ST3400/ST3500, as I set the bottom panel to auto-hide to reclaim some desktop space.  It's not there by default - you'll have to add it.

**-Side panel**
I create a third panel on the side, set it to Autohide, and put launchers on it for XVkbd and Xstroke, so I can easily restart them if they crash or I push the wrong button.  Other programs can be added - on my ST5032 I have brightness up/down buttons here.  I make my bottom panel large (108) and autohide it, so I move the trashcan to this side panel so it doesn't take so much real estate on the enlarged bottom panel, and I put the 'Show Desktop' widget on the top panel, by the 'Application' button.

**-The on-screen keyboard is in the way**
The on-screen keyboard takes up significant space on these small screens.  The keyboard by design will never accept the focus, and this can be used in combination with the Compositor by setting background windows to be partially transparent.  I do this, and set the keyboard sticky, and also always-on-top.  I also set the windows to shade on double-click.  I can read through the keyboard window (to some extent), and quickly shade it to minimize it, drag it around, and un-minimize it to use for entry, and it's always to hand.  Some window manager themes also provide a shade/un-shade button on the title bar, which is also convenient.

If you don't like the transparency, you might still use the Shade/Un-shade approach to keep the keyboard out of the way.

**-Full-screen text mode in consoles**
The on-screen keyboard does not work in the console sessions, but when I am using them with a physical keyboard (for configuring or repair, usually), I like to have all the screen for text.  To do this, edit this file:
```
sudo nano /boot/grub/menu.lst
```

... find these lines, and add the parameter shown in bold (Note: of course your UUID number will be different from this - they're supposed to be unique):
```
## ## Start Default Options ##
## default kernel options
## default kernel options for automagic boot options
## If you want special options for specific kernels use kopt_x_y_z
## where x.y.z is kernel version. Minor versions can be omitted.
## e.g. kopt=root=/dev/hda1 ro
##      kopt_2_6_8=root=/dev/hdc1 ro
##      kopt_2_6_8_2_686=root=/dev/hdc2 ro
# kopt=root=UUID=a46d7dba-2097-44aa-a716-5af531d90c25 ro **vga=788**
```

Then run this command:
```
sudo update-grub
```

---

### Post by mandrux on 2009-05-07
Hi BCW!
First thanks for yours instructions and sorry for my english.
With  Hardy works great, Intrepid not tested, and with Jaunty 9.04
when i touch the screen the mousepointer dissapear.
 (xserver-xorg-input-fpit 1:1.3.0-1)
P:S
Ubuntu-lite use LXDE desktop (only Hardy at the moment) and work faster as xubuntu
Ciao

---

### Post by HawkeyeGuru on 2009-07-05
Following BCW's instructions, I've got the touch screen working on my 3500.  I've also installed xvkbd and xstroke as well.  

Small problem though,  I only know how to launch  XVkbd and Xstroke from a terminal.
How do I make them launch from an icon on the tool bar?  (or some other practical way)

---

### Post by bcw on 2009-07-07
> **HawkeyeGuru said:**
> Small problem though,  I only know how to launch  XVkbd and Xstroke from a terminal.
How do I make them launch from an icon on the tool bar?  (or some other practical way)

This is addressed in the section titled > -Side panel

Generally, right-click on things to get a menu related to what you can do with the item.  If you do this with one of the panels, you'll find an entry allowing you to edit.  You can add a panel at the side and add a launcher, or just add the launcher to one of the existing panels as you prefer.

Right-click on the launcher to edit it's properties.  Add the same command you use to start the application from a terminal, add a helpful description and icon.  Now use that button to start the application.

Also, remember to read about using slides with xvkbd:
```
man xvkbd
```

Cheers,
bcw

---

