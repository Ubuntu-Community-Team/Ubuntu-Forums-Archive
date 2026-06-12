---
title: "ATI driver wont install"
date: 2009-08-16
forum: Installation &amp; Upgrades
---

### Post by trampintransit2 on 2009-08-16
I'm pulling my hair out over this!!!!! I have been trying for three hours to install the driver for a radeon 9800. I've read so much and understood so little. The latest is......

"aye@aye-desktop:~/Desktop$ sudo sh ./ati-driver-installer-9-3-x86.x86_64.run
[sudo] password for aye: 
Created directory fglrx-install.NsNbyM
Verifying archive integrity... All good.
Uncompressing ATI Proprietary Linux Driver-8.593...........................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................
==================================================
 ATI Technologies Linux Driver Installer/Packager 
==================================================

Error: ./default_policy.sh does not support version
default:v2:i686:lib::none:2.6.28-14-generic; make sure that the version is being
correctly set by --iscurrentdistro

Removing temporary directory: fglrx-install.NsNbyM

so what is meant by .sh does not support system? I'm going mad here!

Pls assume if replying that you are dealing with an idiot...that's because you are dealing ...with an idiot!

im using 9.04

---

### Post by Support the 2nd on 2009-08-16
You can't as far as I know.  I did a little research and from what I found, there is no working driver as of yet.

---

### Post by ajgreeny on 2009-08-16
I'm pretty sure with that card you are stuck with the open source ati driver that will have been installed at the time you installed Ubuntu.  Are you having any problems with what you have at the moment, or are you just assuming that, in a windows fashion, you will need to install a driver after the operating system?  If the latter, you will need to forget your windows ways and accept that many things are a lot easier with Ubuntu, and hardware is in the main completely enabled directly by the kernel with no further driver installs needed.

---

### Post by trampintransit2 on 2009-08-16
unfortunately it is not working ok. I cant get the res above 1024x768 and i've just bought a widescreen 20" monitor, so at the current res i have a flattened screen..it's doing my head in..am i stuck...do i need to buy a new graphics card?...if so whats the cheap option given that i dont do any photo work or play games or anything like that?

---

### Post by Support the 2nd on 2009-08-16
> **trampintransit2 said:**
> unfortunately it is not working ok. I cant get the res above 1024x768 and i've just bought a widescreen 20" monitor, so at the current res i have a flattened screen..it's doing my head in..am i stuck...do i need to buy a new graphics card?...if so whats the cheap option given that i dont do any photo work or play games or anything like that?

I have a 9600XT, my resolution while on the LiveCD and after install was defaulted to 1920x1080...just like my monitor is.  I don't see why yours didn't.

But even then, whatever is running my video cannot handle changing the screen color without lagging out horribly.

---

### Post by trampintransit2 on 2009-08-16
so did you have to install a driver?

---

### Post by Mark Phelps on 2009-08-16
You grabbed the ATI Catalyst 9.3 driver, which ordinarly, WOULD work with your card -- since ATI dropped support for your card, and lots of others, with Catalyst 9.4.

Problem is, that Catalyst won't work with the XServer embedded in Ubuntu 9.04.

So, no matter HOW you install it (manually, building from source, using ENVY), it's still NOT going to work with Ubuntu 9.04.

As you were already told, the open source driver is the only alternative you have -- and it is installed by default.

And finally, there's no point in waiting for ATI to "fix" this as they don't see it as broken in the first place.  They have dropped support for what they consider legacy cards and clearly indicated in their Release Notes when they did that, that they would NOT be updating future drivers to handle those cards.  So, until the open source community updates the drivers on their own, we have what we have.

---

### Post by Support the 2nd on 2009-08-16
> **trampintransit2 said:**
> so did you have to install a driver?

No.

When I go to system->hardwaredrivers I don't see anything listed either.

---

### Post by trampintransit2 on 2009-08-16
SO how come 'support the 2nd' has a 9600Xt that runs at 1920x1080.....i'm getting lost here? is that not considered a legacy card?

---

### Post by ajgreeny on 2009-08-16
You could try editing your /etc/X11/xorg.conf file manually with the resolution you need in the following pattern which may get your screen size right, at the very least.
```
Section "Device"
    Identifier    "Configured Video Device"
EndSection

Section "Monitor"
    Identifier    "Configured Monitor"
            HorizSync    30-80
            VertRefresh    50-75
EndSection

Section "Screen"
    Identifier    "Default Screen"
    Monitor        "Configured Monitor"
    Device        "Configured Video Device"
    DefaultDepth    24
    SubSection "Display"
        Modes      "1920x1080"  "1280x1024"
    EndSubSection
EndSection
```
Add your own figures for resolution and refresh rates from your monitor specs, of course.

---

### Post by trampintransit2 on 2009-08-17
yes, this would certainly help......where do i do this? do i just overtype the existing values?

---

### Post by ajgreeny on 2009-08-17
You current xorg.conf file probably looks like this
```
# xorg.conf (X.Org X Window System server configuration file)
#
# This file was generated by dexconf, the Debian X Configuration tool, using
# values from the debconf database.
#
# Edit this file with caution, and see the xorg.conf manual page.
# (Type "man xorg.conf" at the shell prompt.)
#
# This file is automatically updated on xserver-xorg package upgrades *only*
# if it has not been modified since the last upgrade of the xserver-xorg
# package.
#
# Note that some configuration settings that could be done previously
# in this file, now are automatically configured by the server and settings
# here are ignored.
#
# If you have edited this file but would like it to be automatically updated
# again, run the following command:
#   sudo dpkg-reconfigure -phigh xserver-xorg

Section "Device"
    Identifier    "Configured Video Device"
EndSection

Section "Monitor"
    Identifier    "Configured Monitor"
EndSection

Section "Screen"
    Identifier    "Default Screen"
    Monitor        "Configured Monitor"
    Device        "Configured Video Device"
EndSection

```so just open it as root with ```
gksudo gedit /etc/X11/xorg.conf
```and overwrite the part at the bottom starting **Section "Device"** with the contents I showed above in post #10.  Don't forget to backup first, and make sure you use the correct figures.

---

### Post by trampintransit2 on 2009-08-17
gksudo gedit /etc/X11/xorg.confIf i put the above into a terminal it opens a gedit window which is blank?

---

### Post by trampintransit2 on 2009-08-17
gksudo gedit /etc/X11/xorg.conf


if i put this code into a terminal, i dont get anything but an empty gedit window?

---

### Post by trampintransit2 on 2009-08-17
ah, just got the xorg.cong up ( missing out gksudo....dont even know what that means i'm afraid) overtyped the new res figures but got told i dont have permision to change it!

---

### Post by trampintransit2 on 2009-08-17
Ok ..got it.....found help about permissions elswhere in the forums...at last i can use my 'puter...thanks all

---

### Post by ajgreeny on 2009-08-17
So have you got the resolution you wanted?  I assume so from your last post, but just wanted to check.

---

### Post by trampintransit2 on 2009-08-17
yes at last...thanks for your help. I assumed that the correct driver was absolutely neccesary to achieve the higher res. I didn't realise it could be 'forced' in xorg. Thing is i still don't really understand xorg and what it does.... i need to read more..any pointers?

what is the 'etc' in the command gedit /etc/.....

Anyway ..thanks again.

---

### Post by ajgreeny on 2009-08-18
Can't really help with the xorg info any further than suggesting this page [https://help.ubuntu.com/community/Video#Xorg.conf](https://help.ubuntu.com/community/Video#Xorg.conf) I'm afraid, but as for the ```
gksudo gedit /etc/X11/xorg.conf
```gksudo is the equivalent of sudo, except should it be used for applications like gedit (text-editor) that have a gui, instead of sudo.  The /etc/X11/xorg.conf is simply the full filesystem path of the xorg.conf file; burrow down in nautilus from Filesystem in Places and you'll see exactly what I mean.

So, in order to open that file with root privileges so you can edit the contents, you need to use **gksudo**, for the root privileges, **gedit** as the app to use, and **/etc/X11/xorg.conf** as the full pathway of the file to be opened.  Simple really!  In fact, if you install gksu-nautilus from the repos you can just right click on any file in nautilus and choose "Open as administrator" thus avoiding the gksudo command.  If you use the cli, it is just as easy, in my opinion.

---

