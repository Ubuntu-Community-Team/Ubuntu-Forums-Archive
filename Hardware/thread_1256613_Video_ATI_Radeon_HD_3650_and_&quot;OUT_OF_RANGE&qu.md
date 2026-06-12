---
title: "Video: ATI Radeon HD 3650 and &quot;OUT OF RANGE&quot;"
date: 2009-09-02
forum: Hardware
---

### Post by NoDough on 2009-09-02
Hello All,

I am attempting to install the proprietary ATI FGLRX drivers for a Radeon HD 3650.  The install appears to work fine, but after reboot I get a black screen with the monitor's hardware message "OUT OF RANGE" displayed.

The monitor is an X2gen 19" model MG19MY.  I've tried to lookup its specs but all I can find is horizontal frequency maximum 60Hz, vertical frequency maximum 75Hz.

Even knowing that, I have no idea how to constrain the monitor to those specs while installing the ATI FGLRX drivers.

Any ideas?

Thanks,
NoDough

---

### Post by kingair_six on 2009-09-04
hi,

just abolish the idea of getting fglrx to work with Jaunty in any easy way. let's hope for all poor ATI people with a 3XXX card that ati will get something going for us for the next ubuntu release - having 6 months time to get a driver is enough, i think. 

i had a similar problem - getting rid of all fglrx related packages did the trick, and using vesa as a fallback.

```
sudo apt-get remove fglrx*
```

kingair_six

---

### Post by lildigiman on 2009-09-04
Where are you installing the FGLRX driver from? It makes a huge difference where you install from. 

And all things considered, knowing ATI, you might be better off without the driver at all (unless you use some serious 3d Acceleration). My All in Wonder ATI card works better without drivers, haha.

I Installed my FGLRX for my HD3850 from System > Admin >  Hardware Drivers. Downloading from AMD.com is not recommended.

---

### Post by NoDough on 2009-09-04
Actually, I got it working.

First, I added the following to the "Screen" section of xorg.conf

```
    Subsection "Display"
        Depth       24
        Modes "1280x1024_60" "1024x768_60" "800x600_60" "640x480"
    EndSubsection
```

Then I installed the FGLRX drivers through "System > Administration > Hardware Drivers".  After the drivers successfully installed, I rebooted.

On reboot, I was greeted by a normal login screen, but a screwy desktop.  Using Ctrl+Alt+'-' I was able to get the screen to a point where I could at least see a portion of it.

Now "System > Preferences > Display" allowed me to reset the screen to 1280x1024 @ 60Khz.  And everything works.

However, if I again select "System > Preferences > Display" everything slows to a crawl.  So, I pretty much leave it alone.

Hope this helps someone.

---

### Post by NoDough on 2009-09-06
After getting this card working, it continued to give me problems.

The login screen came up black after reboot.  Never got it to work with the card again.

Any new users I created got a black desktop unless and until you could manipulate the user's display settings.

When initially loading the desktop, the card took nearly 30 seconds to fire up the graphics.

When adjusting display settings the performance was like a 286 until the settings dialog was dismissed, and for about 15 seconds after.

I've finally given up.  Returning the card to NewEgg and looking for an Nvidia to replace it.

---

