---
title: "Logitech G15/510 installation issue (new to this)"
date: 2010-12-26
forum: Hardware
---

### Post by koyotomonkey on 2010-12-26
Hi,

I bought the G510 keyboard because I like the extended buttons and the LCD extension and of course I would like to use it on Ubuntu.
I run two boxes, one 10.04 and 10.10, both 64-bit.

From what I understood; the G510 is the same as the G15 software wise so the daemon *should* work, however on install (from the repositories) it bombed after it could not find the  /dev/input/uinput folder. Only having a /dev/uinput folder I made a symbolic link and on re-installation it would not start, citing the error message: 
```
Setting up g15daemon (1.9.5.3-8ubuntu1) ...
Starting g15daemon: invoke-rc.d: initscript g15daemon, action "start" failed.
dpkg: error processing g15daemon (--configure):
subprocess installed post-installation script returned error exit status 1
Processing triggers for libc-bin ...
ldconfig deferred processing now taking place
Errors were encountered while processing:
g15daemon
E: Sub-process /usr/bin/dpkg returned an error code (1)
```

From what I understood, I have to add a line of code to the  library source which added my keyboard. I did this and it compiled successfully and installed. However I am a bit of a lose of what to do now. When I compiled the daemon it compiled and installed but was still not able to start. No error message was received. I ran it as root obviously and did precautionary steps to the best of my knowledge but this is quite frustrating. 

Any help would be appreciated.

EDIT: I did remove the symbolic link and tried again just now. No luck.

---

### Post by koyotomonkey on 2010-12-27
Well some progress. I did an lsusb and discovered a typo in the line of code which properly identifies my keyboard. However after the daemon successfully runs it causes the keyboard to hang.

I get an LCD output but the keyboard itself ceases to work.

Anyone have any suggestions?

---

### Post by spydon on 2010-12-27
I got one of those too. It would be very nice to be able to get the color-changing backlight to work too. Maybe it is possible to mix the G15 and G19 driver? Is it the exactly same screen in the G510 as in the G15?

---

### Post by spydon on 2010-12-27
Seems like someone have already fixed it, can't find the patch though... [http://www.g15tools.com/node/715#comment-948]("http://www.g15tools.com/node/715#comment-948")

---

### Post by jsather on 2011-03-10
I posted this to spydon's other post on the forums and thought you might like to see it as well.

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

