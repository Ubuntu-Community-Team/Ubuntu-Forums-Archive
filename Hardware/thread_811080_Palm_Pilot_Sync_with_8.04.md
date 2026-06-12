---
title: "Palm Pilot Sync with 8.04"
date: 2008-05-28
forum: Hardware
---

### Post by purachochada on 2008-05-28
I use an older PalmV (serial and ir port) with my Dell Inspiron 6400 (only USB ports) and want to sync with Evolution 2.22.1.

Because of the port mismatch i use a usb-serial cabel converter which in the old windows environment worked perfectly.

I tried the [https://help.ubuntu.com/community/PortableDevices/PalmOS?action=show&redirect=PalmSync](https://help.ubuntu.com/community/PortableDevices/PalmOS?action=show&redirect=PalmSync) to configure gnome-pilot (gpilotd)

The device settings i use are the following
Type: Serial
Device: /dev/ttyUSB0
Speed: 57600

Note: Even though in most of the documentation i found is described that the system starts /dev/ttyUSB0 and /dev/ttyUSB1 (or sometimes /dev/pilot) while synchronizing, this is not the case for me. In my case it ONLY uses /dev/ttyUSB0. 

After some playing around and also trying [https://help.ubuntu.com/community/PalmDeviceSetup]("https://help.ubuntu.com/community/PalmDeviceSetup") i found out, that the sync didn't work because of some strange behavior in the port recognition between the gnome-applet, usb-serial cabel and the palm.

So here is the workaround to make it run.

1) Connect the USB cable to the computer without having started the gnome-applet
2) Start gnome-applet with the device settings above (if you do it for the first time, following the instructions in the gnome-applet)
3) Disconnect the palm USB cable. There must appear a gpilotd error message saying that there is a /dev/ttyUSB0 port error (also the /dev/ttyUSB0 port should disappear....use 'ls -l' command in the terminal)
4) Connect the palm USB cable again (/dev/ttyUSB0 port should appear again)
5) Close the gnome-applet and kill/finalize the gpilotd using the System Monitor or the 'kill' command (ps -A and then kill x, where x is the gpilotd PID)
6) Start the gnome-applet again (both the gpilotd and the gpilotd-control-applet should come up again)
7) Sync pressing the HotSync botton

I don't know if this is a bug or if it has to do with my usb-serial cable or what's the reason for it?

Somebody has a clue.....or may at least the workaround might work for other too??

Final note: it seems that the [https://help.ubuntu.com/community/PalmDeviceSetup](https://help.ubuntu.com/community/PalmDeviceSetup) is not necessary, because after it worked with the workaround i undo the 10-custom-rule and visor module and it's still working!

---

### Post by am15 on 2008-07-14
Thanks a lot.  This really did the trick for me and now my Palm Tungsten C is synching with JPilot & KPilot.  Do you know of any way to get the Memos to synch.  That just won't happen with either.

---

### Post by purachochada on 2008-07-14
Sorry, didn't have problems with this one. The only thing i noticed with the Memos was that the Subject line must be the same as the first Body line, as my Palm interprets the first Body line as Subject, ignoring the Subject of Evolution.

Stupid question: Are you sure you activated the right 'Memos' to synchronize, because i think to remember that there are two similar thinks Memos and Notes are something like that??

cheers

---

### Post by am15 on 2008-07-21
Yes, I did check Memos.  It gets confused though because I found some Notes in Memos when I synched. I am having trouble synching again.  I will have to disconnect and make it detect again.  Its kind of annoying.  I wish this worked better.  Everything else is working quite well.

---

### Post by kgas on 2008-08-09
With gnome I could configure and take a back up of Zire72 in my laptop(Acer TM291Lci). But I could not view any of the files. Jpilot did not work in my case.Search in web also did not give any positive result.There is a possibility to use XP in VMware but I want to do it with ubuntu only, as I just switched from XP to ubuntu 8.04. Any help please...

---

