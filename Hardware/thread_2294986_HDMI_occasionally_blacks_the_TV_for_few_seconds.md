---
title: "HDMI occasionally blacks the TV for few seconds"
date: 2015-09-15
forum: Hardware
---

### Post by simba4 on 2015-09-15
I have a new Motherboard Asus H97M-Plus with on board "Intel®HD Graphics" system.

This Ubuntu OS was created on a previous Dell Laptop RIP, so I just transferred the SSD straight to the current new system. 
All seem to work fine, except the 'on_Board' HDMI outlet.

When  I hook the HDMI to my new Sony 50" LED TV, it shows the picture but  then, every now and then (about 10Minutes) the TV goes black for a few  seconds and then goes back in view.  Most of the Time, it does that  every 5-10 Minutes, but occasionally, it can get into a frenzy, keep  doing that every 10-20 seconds.
BTW, I use that TV to watch movies through KODI (XBMC&#8482; Media Center).

Narrowing the suspects, it seems that the fault lays with the Ubuntu system, and/or the graphic drivers.

Checking the system details it says: Intel® Haswell Desktop
I clicked "Install updates" and it made some "updates" (320M of them) 

After  the update and re_boot, I set to watch some films. For some time it  seems that the problem solved, but then it started again,

I'd be very appreciated if someone can help me with that.

Thanks,

James

Just another thing,


In some (rare) cases, when the TV  blackens out, it doesn't go back to where it was.
 Instead - it brings back  the 'empty' page of the HDMI (read: "HDMI4" on the top of the screen).
Naturally the application get to pops back to the computer screen.

It seems that the computer resets its displays and "forgets" that it has a TV connected to the HDMI port.

Hope that this extra info add to finding a solution.


_James_

---

### Post by TheFu on 2015-09-15
HDMI standards are all over the place. Some devices just don't work together. I have a projector that is incompatible with any HDMI switches, but works fine with good cables. Bad HDMI cables seem to cut the signal strength a little too much too - and it has trouble auto-seeking on the HDMI1 input.

So ... the quick answers are to 
* try a different HDMI cable. 
* 2nd thing to try is forcing only the HDMI-input to be active on the TV, don't let it auto-seek different inputs.

For Ubuntu stuff - please patch the system weekly. 320 updates seems terribly high - weekly there are between 2-15 updates usually. If more are shown, something big is happening and it is worth stopping to see if the system isn't doing something you don't want.  Had a very stable system running the 3.2 kernel - then decided to force it to the 3.16 kernel and WOW ... all the X/Windows stuff was being swapped out!  Lots of updates.  I didn't notice it that morning and it has been 4 months of trying to fix it. I should have just reloaded the OS then, and restored from the prior night's backups. 

Would have been easier. Live and learn.

I didn't do any searching on the specific MB or chips or IGP to look for issues.  But I do have 2 IGP (Intel) connected to HDMI monitors and they are working fine.  Amazon "basic" HDMI cables work.  My monitors are all old - none have the HDMI 1.3 or later specs.  Actually, the main 24in monitor doesn't even support HDMI at all.

---

### Post by simba4 on 2015-09-20
All problems solved by replacing the HDMI cable to hama 5M

Thank you for the good tip

James
[IMG]http://pclab.pl/zdjecia/prasowe/0000032e4e313bd3.jpg[/IMG]

---

### Post by TheFu on 2015-09-20
Please mark this thread as solved to help others.

---

