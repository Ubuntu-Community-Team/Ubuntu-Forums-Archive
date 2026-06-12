---
title: "Canon MF4770n install"
date: 2013-12-19
forum: Hardware
---

### Post by hodad on 2013-12-19
.

---

### Post by hodad on 2013-12-19
I have been trying to get my Canon printer to work, either as a network printer, or as USB connected.  I feel like I've gotten close over the last several days, but have the same problem, whether trying via network or as a USB connected printer:

The printer shows up OK under "System Settings" - "Printer", but when I go to print a test page, I get  a message "Submitted as job xx"; I'm up to job 87 at this point.  So  I have 87 print jobs queued up, but when I bring up "View Print Queue", it show as empty.    Printer is listed as "idle" (see screenshot).  

Also, when I print a test page, Printer state shows: "Idle - src = libcanon_pdlwrapper.c, line = 514, err = 0¥nDEBUG: PID 5870 (gs) exited with no errors".  

When I do the lsusb command on the terminal, I can see the canon printer listed, but nothing prints.  Second screenshot shows results from other printer commands.

Seems to be a problem with the print queue, but I can't figure out how to break things loose, so they'll get to the printer.

---

### Post by QIII on 2013-12-19
Threads merged.

Rather than starting a new thread, please consider updating one you have already started.  That will allow the community to answer the issue in one place rather than having a confusing series of answers in several places.

Thanks.

---

### Post by hodad on 2013-12-21
A little bit of progress made:
I managed to get into the CUPS printer manager  localhost:631, after figuring out how to get past the password conundrum (let me know if you need assistance on that one).
This print manager seems to have more tools available than the stock "System Settings" - "Printer" application; more options and explanations.

I can now get an occasional "beep" out of the printer!  I consider this to be great progress!

Now I've got to figure out where all of the other 128 test prints are piling up.

See attached screenshot...

---

### Post by hodad on 2013-12-23
OK, I got the printer operating off of my USB port.  Basically, I followed the general outline of the documentation provided with the Canon driver download.  However, the instructions were incomplete, and the commands didn't always operate without error messages.

I haven't tried hooking up the printer via ethernet thru my router, but I assume it would work that way as well.

Attached is the outline of what I finally ended up doing in order to get my printer working.  Hopefully the strategy (or something close to it) will work for you.  More than likely, I have left something out, or your particular hardware will introduce differences.  But this should at least get you close...

---

### Post by aeronmonroe on 2014-01-17
I needed to install 
  libxml2:i386      
to get it to work.

---

### Post by wind_racer on 2014-01-22
Glad to see I'm not the only one having issues with printing to my Canon imageCLASS printer with Ubuntu 13.10 (I have the MF4890).

Thanks for documenting the steps you used. However, it seems that ia32-libs have been deprecated in 13.10 so I wasn't able to install them. Using [COLOR=#000000]aeronmonroe's tip to install [/COLOR][COLOR=#000000]libxml2:i386 (and the related packages it brought along) seemed to get me closer! Now, instead of nothing happening when I print a test page, I see "Processing - Connected to Printer" in CUPS, the printer wakes up, the green data receive light flashes, and "printing" appears on the display ... but still nothing happens! It just gets stuck like that.

So close! Any other suggestions?
[/COLOR]

---

### Post by bengy103 on 2014-01-24
Same problem here as OP, but with Pixma MG6450.

I tried the libxml2:i386 routine and I'm sure that I heard something twitch inside once and that was as far as I got.

The really annoying thing is that some time ago I went to the Canon site and downloaded the Linux drivers, stored them on my Nas, and installed them. I printed with no problems at all, and that was with a Wifi setup, no usb first. On the Canon site they say the drivers are for Ubuntu 13.(something), but they worked on 12.04.

Anyway after some really annoying problems - where Ubuntu 12.04 told me we had internal problems - I wiped the whole damned HDD and re-installed Ubuntu 12.04 (because I can't get 13.(something) on a CD) and now the printer won't work.

Maybe I should re-create the internal problems so I can get some DTP on the go!

I know my post is not at all helpful but I feel so much better for getting it off my chest.

regards,

brawd.

---

