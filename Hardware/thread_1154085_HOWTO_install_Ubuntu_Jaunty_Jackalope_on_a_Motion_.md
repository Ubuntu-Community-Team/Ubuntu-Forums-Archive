---
title: "HOWTO install Ubuntu Jaunty Jackalope on a Motion Computing M1400 (&amp; M1300?) tablet"
date: 2009-05-09
forum: Hardware
---

### Post by paledread on 2009-05-09
This HOWTO should describe how I got my Motion Computing M1400
tablet PC operating with it's stylus, in Ubuntu Jaunty Jackalope 9.04.
It is intended to be of use to others who may be stumbling around, as I
was, trying to get back to a functional setup after installing Jaunty,
or perhaps thinking of moving to Jaunty.

Since the tablet had previously been working in Ubuntu Intrepid 8.10 via
setserial and wacom-tools and a custom xorg.conf, this should not be
earth-shattering information, but the upgrade to Jaunty did create
some obstacles and difficulties, and the following notes may be of
assistance to other Ubuntu users on the M1400 (and the M1300?).

The first move that I made was to try and do a distribution upgrade on my tablet, from Intrepid, and via Synaptic. This didn't work for me, but that may be a result of ignorance. All seemed to go well during the upgrade, but when I rebooted, the grub screen froze when it reached "Starting up ...", and would go no further. Perhaps there was something that could have done via the ESC key before the boot reached that point, but not obvious or known to me. 

I was able to boot to the previous Intrepid kernel which was still
available, but since the Jaunty upgrade had wiped my xorg.conf
file, and the setserial settings had also presumably been wiped, was unsuccessful in getting X running. I did make some efforts at reinstating the old Intrepid xorg.conf file to use along with this earlier kernel, but was really groping around in the dark, and had no joy.

So all in all, if you go the dist-upgrade route, good luck. It wouldn't
work for me but YMMV.

A fresh install of Jaunty Desktop from a USB attached CD drive seemed
to be the way forward.

After setting the M1400 BIOS to boot from the CD, the CD started up without a problem. Selected English as a language, and then selected install Ubuntu to the hard drive. This resulted in a blank display and no further forward motion. So play around, and after a while the F6 key, and then selection of "acpid off", allowed the CD to boot and install without any more confusion. Not sure why "acpid off" was necessary, maybe something to do with the external USB CD drive, but it worked. 

While installing, the wifi card was used by the installer to connect to a wireless hub without any input needed from me. Magic.

FWIMBW the kernel installed by Jaunty was 2.6.28-11-generic.

So following the install and the necessary re-boot we should now be at a
log-in screen. If you have the Motion USB keyboard for your tablet
hooked up you can now log in using the keyboard. I'm guessing any other
USB keyboard should also work, but you haven't got an on screen keyboard yet, so you will definitely need a real keyboard hooked up.

After logging in wireless networking worked without any configuration needed, which was a great relief. More magic.

After logging in you need to install wacom-tools via synaptic or
whichever way you choose to install your packages. 

```
sudo apt-get install wacom-tools
```

should work from the command line.

The other package that is certainly needed for the tablet is
xserver-xorg-input-wacom, but that seems to be automatically installed
as part of the Jaunty install so no extra action is needed.

Judging by other posts, the version of wacom-tools installed may be
important. The version that was installed for me was 8.2.2. It seems
likely that earlier versions are not going to work, but Jaunty gave me
8.2.2, so we do know that version is available and worked for me.

Now we get into the one item that was new to me, and didn't seem to be part of my previous Ubuntu installs on the tablet.

You need to enter on a command line :

```
wget -O 50-xserver-xorg-input-wacom.rules
"http://git.debian.org/?p=users/ron/wacom-tools.git;a=blob_plain;f=debian/xserver-xorg-input-wacom.udev;hb=cd7b8f556855d985cd6de46892ffceb333cd03d9"
```

You are collecting this file from Ron's Debian git repository, and we
should all give a vote of thanks to Ron. The file thus downloaded will be
"50-xserver-xorg-input-wacom.rules".

Copy or move the file that you have downloaded to the /etc/udev/rules.d/
directory. The file should have the same ownerships and permissions as
the other files in /etc/udev/rules.d/. Adjust if necessary.

Now you need to set up your xorg.conf file, in similar fashion to previous
tablet installs, but simpler. I should note here that my ignorance
extends to the terms "eraser" and "touch", both of which were configured
in my previous version xorg.conf files. My M1400 stylus does not have an
"eraser" which I understand to be similar to that little rubber knob on
the reverse end of a pencil, and with similar function. If any models of
the M1400 do have an eraser then you will need to include configuration
for this as an input device. This is pretty straightforward, and if any
body wants it I can easily add it to the xorg.conf below. The "touch" is
a complete mystery to me. I tried an xorg.conf with "touch" configured
as an input device, but it seemed to provide no extra function that I
could detect, so I've left it out of the xorg.conf below. Please,
somebody explain what "touch" is, for my benefit, and whether it has any
relevance to the M1400.

So the following xorg.conf is what I ended up with. For clarity I've omitted all the lines that were comments and/or were commented out by the Jaunty install. This leaves quite a short xorg.conf. I'm assuming this xorg.conf should be the same for all M1400 users installing Jaunty, but if that is not correct please let me know.

```
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
	InputDevice "stylus" "SendCoreEvents"
EndSection

Section "InputDevice"
Driver "wacom"
Identifier "stylus"
Option "Type" "stylus"
Option "Device" "/dev/ttyS0"
Option "ForceDevice" "ISDV4"
Option    "Button2"    "3"
EndSection
```

Serious thanks at this point to Favux from who's published xorg.conf this one is poached.

You need to firstly back up your existing Jaunty installed xorg.conf
file, just in case this HOWTO wrecks your computer, and you need to get the original file back on your system.

```
sudo cp /etc/X11/xorg.conf /etc/X11/xorg.conf.JAUNTY 
```

should get it done. Now save the the xorg.conf that is listed above as a plain text file "xorg.conf" in a convenient location, and copy or move it to /etc/X11/ as your new /etc/X11/xorg.conf.

```
sudo cp ./xorg.conf /etc/X11/
```

from the directory where you saved the file should work.

At this point we've finished the set up of the stylus, but I needed an on screen keyboard at the log-in screen to avoid the need to hook up a hard keyboard, and I guess others would like the same. "onboard" on screen keyboard is included in the Jaunty install, and it works very well for me. If you want to use a different keyboard simply adjust the GDM line that we are going to add (see below), to suit your needs. 

We need to add a line to the /etc/gdm/Init/Default file, so using sudo open up this file for editing with your favourite editor. Scroll down to the final line which should be "exit 0". Now ABOVE this line insert a new line :

```
/usr/bin/onboard -s 500x130 -x 15 -y 15 &
```

and save the file.

This should eventually give you a smallish keyboard top left of the login screen. It's about right for me but you may want to play around with the -s -x and -y values until you are satisfied with the keyboard size and
location.

This whole HOWTO is written for GDM, but if you are using Kubuntu then I believe KDM will have taken over the GDM functions, and you will need to adjust a similar file somewhere in (I think) /etc/kdm/. Corrections welcome if this is incorrect.

Now you need to take one more step to make the on screen keyboard visible
at the log-in screen. If you leave the default Jaunty install as is,
then the background to the login screen is a very attractive graphic.
Unfortunately you can't have both the graphic and an on screen keyboard,
so you need to get rid of the graphic. For Gnome (GDM) users this means,
open the Gnome control centre, select "Login Window", and under "Local"
change the "Style" to "plain with face browser" (or "plain"?). Close the login window page and exit the Gnome control centre. For KDE (KDM) users the procedure should be similar, but I don't have the exact moves to hand.

Log out and pray to whomever you find appropriate.

You should now be facing a login screen with an on screen keyboard, and a
working stylus, and all should be plain sailing from this point on.

If your prayers were not answered feel free to let us know.

Profound thanks to Ron, to Favux and to gali98 for making this HOWTO possible; also to hundreds of others who have contributed to making my Ubuntu experience enjoyable in so many ways.

---

### Post by paledread on 2009-05-09
Paledread,

Thanks for this brilliant HOWTO but you are an idiot.

All of this worked for me, but I still have the following issues on my M1400 tablet.

1. I'm sure that I used to get a middle mouse button click from my stylus, but this no longer works. This means that using Openbox I can no longer get the desktop middle-click list of running apps. How can I fix this?

2. When I log out and log in again I have a frozen log-in screen, and I have to reboot. This has always been the case with my M1400 Ubuntu set ups and is not something new in Jaunty. How can I fix this?

3. None of the M1400 right hand side case buttons, except the big one, do anything useful. How can I get these buttons to work in some useful fashion?

If you can't answer these questions then I'll have to hope that someone else will post the answers here.

---

