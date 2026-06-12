---
title: "intel 945GM express driver"
date: 2006-10-23
forum: Hardware &amp; Laptops
---

### Post by randiz on 2006-10-23
Hello

I am new to this and need help.

installed ubuntu 6.10 rc
I have dell E1705. It has intel 945GM express chip for display.
In XP the res is 14990 x 990 color quality 32 bit works fine.
I get the following error :

---EEI810 : no vedio BIOS mode for chosen depth
---EE1810 screen(s) found , but none have usable config

how can I fix this ?

thanks
randiz

---

### Post by randiz on 2006-10-23
oops i meant 1440x900 resolution .

---

### Post by humphry on 2006-11-27
Try using the following command:

sudo dpkg-reconfigure xserver-xorg

I'm also new to Linux so I only know a little bit.  I have the same laptop and when booting from the liveCD it wouldn't display properly and came up with an evil error screen.  This helped it.  

However, now that everything is installed, I can't get any resolution higher than 1024x768.  Any thoughts on that?

---

### Post by dmartinsca on 2006-11-27
You'll need to install a program called 915resolution. I'd suggest also installing vbetool if it isn't already installed so that 915resolution will configure itself.

A short explanation of 915resolution & why it's needed as far as i understand it: The X Windows system for linux only displays resolutions which are programmed into the BIOS of the video card. The Intel video cards only include standard VESA resolutions in their BIOS -- this doesn't include 1440x900 or 1280x800 or any other common widescreen LCD resolutions. 915resolution writes over one of the pre-programmed resolutions of your video card's BIOS (which you won't use anyways;) )so that Xorg can use it. Now, this change only occurs in memory which is lost when the computer is turned off/rebooted. That means 915resolution needs to run every time linux boots. **_It also means that no harm can be done to your video card, so don't worry 'bout that :)_**

Humphry, what is your video card? Post the output of **lspci** (run from a terminal) if you aren't sure. You may as well post the contents of /etc/X11/xorg.conf as well.

---

### Post by jdong on 2006-11-27
> **dmartinsca said:**
> The Intel video cards only include standard VESA resolutions in their BIOS -- this doesn't include 1440x900 or 1280x800 or any other common widescreen LCD resolutions

More accurate and blunt version: Many laptop manufacturers are not putting their laptop's custom resolutions (such as the widescreen resolutions) into their Video BIOS but instead are shipping with the stock video BIOS that Intel provides as "example code". (I have seen the rare occurrence of a laptop or a BIOS update that has widescreen modes in its video BIOS). Windows Intel VGA drivers have a mechanism for specifying resolutions not in the Video BIOS. This is what 915resolution does for Linux.

However, you should really take the time to yell at your laptop manufacturer to release a BIOS update with the proper resolutions in video BIOS.

---

### Post by humphry on 2006-11-27
Now I'm confused... one of the first steps in the HOWTO told me that I don't need 915resolution and that I can uninstall it...  Here's my card, btw:
```
00:00.0 Host bridge: Intel Corporation Mobile 945GM/PM/GMS/940GML and 945GT Express Memory Controller Hub (rev 03)
00:02.0 VGA compatible controller: Intel Corporation Mobile 945GM/GMS/940GML Express Integrated Graphics Controller (rev 03)
00:02.1 Display controller: Intel Corporation Mobile 945GM/GMS/940GML Express Integrated Graphics Controller (rev 03)

```

I guess since I have the widescreen and a funny resolution that I do need.  

Is there a way to automatically run 915resolution on startup so that I don't have to manually run it every time?

Also, how do I install 915resolution and vbetool?

---

### Post by dmartinsca on 2006-11-27
You can install 915resolution and vbetool the same way you install any software in ubuntu. Either click on System > Administration > Synaptic Package manager, or open a terminal and run **sudo aptitude install 915resolution vbetool**

To make 915resolution available you may need to enable the universe repository, either through Synaptic Package Manager > Settings > Repositories or by editing /etc/apt/sources.list. If you had to enable the universe repository you'll need to update the list of packages by clicking reload in Synaptic or running **sudo aptitude update**

915resolution should automatically start at boot. You can start it now by running **sudo /etc/init.d/915resolution start** then restarting Xorg by logging out and pressing Ctrl+Alt+Backspace. This should start you up in the new resolution as long as it is listed in your /etc/X11/xorg.conf file. If it doesn't work, try rebooting, if still nothing then post the output of **sudo 915resolution -l** and the contents of /etc/X11/xorg.conf

EDIT: I now see the HOWTO you are refering too. Frankly, this is news to me (and possibly good news!) I'll test it out tomorrow night....
[http://ubuntuforums.org/showthread.php?t=281275](http://ubuntuforums.org/showthread.php?t=281275)

---

### Post by jdong on 2006-11-27
Yeah, forgot to mention, xserver-xorg-driver-intel (the intel (NOT i810) driver) supports setting video mode without 915resolution.

However, in my testing, this new video driver is still somewhat unstable. It cannot power my 835-based card, and once in a while glitches my friend's GMA950 to a hard lock.

---

### Post by dmartinsca on 2006-12-01
I've decided not to test this new driver right now. My laptop is running pretty reliably right now & with it being end of semester i need it to do work efficiently, rather than crash randomly :)

---

### Post by amgra on 2006-12-07
> **humphry said:**
> Try using the following command:

sudo dpkg-reconfigure xserver-xorg

I'm also new to Linux so I only know a little bit.  I have the same laptop and when booting from the liveCD it wouldn't display properly and came up with an evil error screen.  This helped it.  

However, now that everything is installed, I can't get any resolution higher than 1024x768.  Any thoughts on that?

Hello, once I changed the Xserver configuration, how do I restart the install liveCD, becuase if I boot again, my changes will be lost?

---

### Post by Allysan on 2007-08-20
> **amgra said:**
> Hello, once I changed the Xserver configuration, how do I restart the install liveCD, becuase if I boot again, my changes will be lost?

You're going to have to install Ubuntu before you can make proper changes such as this one.  As wonderful as the LiveCD is, it really is a very temporary method and you should only use it to see if you like the basic idea of Ubuntu.

I have the same video card as the threadstarter and I'm also trying to install my graphics drivers.  Is 915resolution that driver or do I need to look elsewhere for it?

---

