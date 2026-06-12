---
title: "Logitech G510 Keyboard"
date: 2010-12-24
forum: Hardware
---

### Post by spydon on 2010-12-24
Is there any driver or hack for getting more functions working on the logitech g510 keyboard?

---

### Post by spydon on 2010-12-26
Maybe it is possible to mix some G19 and G15 code, as it has the same color backlight function as G19 and the same screen(?) as the G15?

---

### Post by jsather on 2011-03-10
Just in case you are still interested in this, I have gotten some additional functionality working--basically the extra keys and the LCD.  Here is what I had to do:

Install the g15daemon and dependencies from synaptic.  This will probably fail in a post-install config, but the files will be there.

Now you need to replace libg15.  To do this, go here
[http://sourceforge.net/projects/g15tools/]("http://sourceforge.net/projects/g15tools/") and download the libg15-1.2.7.tar.bz file and extract it.  This is an old version and doesn't have the G510 code.

You will need to have subversion installed to run this command:
[FONT="Courier New"]svn co [https://g15tools.svn.sourceforge.net/svnroot/g15tools/trunk/libg15/](https://g15tools.svn.sourceforge.net/svnroot/g15tools/trunk/libg15/) libg15[/FONT]

Now take the libg15.c and libg15.h from that folder and replace the ones from the sourceforge download.

Now build and install the new lib:
[FONT="Courier New"]./configure
make
sudo make install[/FONT]

You should now be able to start up the g15daemon.
[FONT="Courier New"]sudo g15daemon
[/FONT]

If it worked, the LCD should display the time.  You can run it with -d if you want to make sure it sees the G510.

If you added in the g15stats package, you should be able to run that as a normal user.

I'm still having problems with the media keys.  I'll update if I can get those working.

One side note on the key color--this is hard set in the code.  Look for these lines:
[FONT="Courier New"]if(g15DeviceCapabilities()&G15_DEVICE_G510)
        setG510LEDColor(0, 255, 0);[/FONT]
The default is green.  I changed mine to a light blue.  Just change the 0, 255, 0 to some other color and recompile/reinstall.

---

### Post by Inkanikaido on 2011-03-15
Got my Keyboard to emmit a nice green glow and even the g15stats are  working smoothly. Yet I'm running into errors whenever updating or  installing Packages and the Keyboard resets from time to time (more  often than that, to be honest).
As I'm fairly new to *nix, any debugging help'd be apreciated.

E: g15daemon: Unterprozess installiertes post-installation-Skript gab den Fehlerwert 1 zurück
E: g15macro: Abhängigkeitsprobleme - lasse es unkonfiguriert
E: g15stats: Abhängigkeitsprobleme - lasse es unkonfiguriert

Richte g15daemon ein (1.9.5.3-8.1ubuntu1) ...
Starting g15daemon: .../dev/input/uinput not found ...invoke-rc.d: initscript g15daemon, action "start" failed.

---

### Post by spydon on 2012-08-02
Thank you, it works pretty good now!
The only thing not working correctly is the media buttons and the G13-G15 buttons.

---

