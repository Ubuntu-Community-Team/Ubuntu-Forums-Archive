---
title: "gpilotd cannot communicate with Palm Tungsten T3 via USB"
date: 2005-02-26
forum: Hardware &amp; Laptops
---

### Post by Sirenian on 2005-02-26
I'm a complete linux newbie, so be gentle.

I've followed this article: [http://fedoranews.org/tchung/gnome-pilot/](http://fedoranews.org/tchung/gnome-pilot/)

I've symlink'd /dev/pilot to /dev/ttyUSB1. The pilot-xfer command seems to find my Palm  just fine. When I start gpilotd via the gnome menu and it goes through the process of looking for the Palm, nothing happens. I've tried pressing the hotsync button before I search and after. I've tried a direct USB cable link, using the Palm's Hotsync app to kick it off, as well as the cradle button (the cradle doesn't work with pilot-xfer, so I've given up on that).

Possible reasons I've thought of:
- I've hotsync'd before using this Palm, so it's set to sync with Windows (and therefore the Ubuntu-version of my PC is not its normal primary PC).
- Does gpilotd support PalmOS 5.0+?
- I upset an Ubuntu / GPilot dev in a former life and now it's karma time.

I have run out of solutions for this problem. Can you help me, or am I destined to be a Windows user in my next existence too?

---

### Post by Jorge on 2005-02-27
I followed that article too, but it didn't help me. This is what I did and it worked for me:

1. On the pilot configuration screen, I select "devices" tab, I wrote /dev/ttyUSB1 as the port (the upper/lowercase are very important), then I selected USB as type, with 115000 speed transfer.

2. I change the name from Cradle to Zire71 (which is my Palm, this is not important)

3. I increased the waiting time to 4

4. I went back to "Pilots" tab and I choose "Add" and "get from pilot" (you can customize the name and local directory too).

5. I went to the "Conduits" tab and I activated EAdress, ECalendar, EToDo with a "first time" set for "copy from pilot" in order to get the data for the first time.

Then I select sinchronized on my Palm.

I hope it would help you

As you, I am a newbie and I use my Palm primary on the Windows side (with PalmDesktop), but now I can sinchronize with both PalmDesktop and Evolution. That implies, of course, that I have to be very carefull on changing my data. I only change the info on my palm, and I use the PC-programs for backup and consult.

(English is not my native language nor is the language of my Ubuntu, so be kind to correct any mistakes here).

Jorge

---

### Post by Sirenian on 2005-03-01
You star; that did it.  :)

(Your English is far better than that of some English people I know.)

---

### Post by billjw on 2005-03-07
[QUOTE=Sirenian]You star; that did it.  :)

(Your English is far better than that of some English people I know.)[/QUOTE]
 Great work, worked first time here too. Thanks a heap. Now EVERYTHING works.

Good bye Windoze!

Bill

---

