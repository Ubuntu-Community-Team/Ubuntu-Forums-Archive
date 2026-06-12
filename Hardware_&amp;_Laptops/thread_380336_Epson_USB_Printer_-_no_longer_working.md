---
title: "Epson USB Printer - no longer working"
date: 2007-03-09
forum: Hardware &amp; Laptops
---

### Post by BrowneR on 2007-03-09
Hi,
I have been using my epson D68 printer through cups with the gutenprint driver for a while now and it has always worked without fail whenever i plugged it in.

Today when i plugged it in and tried to print nothing happened and on closer inspection the driver was reporting that the printer was not connected.

When i run lsusb the printer is listed along with its name:

*Bus 004 Device 002: ID 04b8:0005 Seiko Epson Corp. Stylus Printer*

Ubuntu's device manager also shows the printer and all its details along with a device node at */dev/usblp0*

On plugging in the printer i get the following in syslog

[I][ 1222.303000] usb 4-2: configuration #1 chosen from 1 choice
[ 1222.313000] drivers/usb/class/usblp.c: usblp0: USB Bidirectional printer dev 3 if 0 alt 0 proto 2 vid 0x04B8 pid 0x0005[/I]

I remember cups was setup to use *USB://EPSON/Stylus D68* as its URI although i don't understand where that comes from.

If i now try to add new printer using *gnome-cups-manager* there are no local printers detected.

I am unsure how the printing system works and what backends cups is using to communicate with my printer. Something has failed somewhere.

Does anyone have any idea how i can fix this? I cant think what i've done that may have broken it.

Any help appreciated, Cheers.

---

### Post by sticksabuser on 2007-03-09
Hey...

I have the same exact issue here too... Only thing though is that I'm using Kubuntu 6.10 (edgy). I have and ALL-in-One Epson Stylus CX3810, and its worked fine since I installed kubuntu. Ever since yesterday however I haven't been able to use/add the printer (same symptoms as above). lsusb shows me the following

```
Bus 002 Device 005: ID 04b8:0818 Seiko Epson Corp.
```

Which I assume is the printer connected via usb. Note that ican still use the scanner (which I had to manually install) and I can still use the check ink script that uses escputil and reads off /dev/usblp0/..

Could this be some kind of software bug and not just user error? Any help is much appreciated...

---

### Post by vyruss on 2007-03-09
> **sticksabuser said:**
> Hey...

I have the same exact issue here too... Only thing though is that I'm using Kubuntu 6.10 (edgy). I have and ALL-in-One Epson Stylus CX3810, and its worked fine since I installed kubuntu. Ever since yesterday however I haven't been able to use/add the printer (same symptoms as above). lsusb shows me the following

```
Bus 002 Device 005: ID 04b8:0818 Seiko Epson Corp.
```

Which I assume is the printer connected via usb. Note that ican still use the scanner (which I had to manually install) and I can still use the check ink script that uses escputil and reads off /dev/usblp0/..

Could this be some kind of software bug and not just user error? Any help is much appreciated...

Same here, with a Konica Minolta PagePro 1300W. It suddenly stopped working today.

---

### Post by vyruss on 2007-03-09
OK I think we found the issue:

[https://bugs.launchpad.net/ubuntu/+source/libgphoto2/+bug/90724](https://bugs.launchpad.net/ubuntu/+source/libgphoto2/+bug/90724)

I believe they'll fix it quickly :)

---

### Post by heffo_j on 2007-03-09
Did you do a very recent update? My USB printer no longer works after the update.

Regards
John

---

### Post by heffo_j on 2007-03-09
My printer is a USB Kyocera FS-1010; a very Linux friendly printer. The last update has broken my ability to print.

Regards
John

---

### Post by systemgod on 2007-03-09
Same here, 

using an Epson R200 via USB. Always worked without any problems but when I tried printing something today the job just stays in the queue.  The print manager claims no printer is connected, trying to add a new printer reveals 'no printers detected'.

I'm not sure when it stopped working. The last time I printed something was last week.  Must be a recent update.

Help! 

Nico

---

### Post by marklid on 2007-03-09
I'm in the same boat using a HP Deskjet 3550 after dong an update today. Hopefully they will have this fixed soon.

---

### Post by Chris11 on 2007-03-09
EXACTLY the same problem for me too with a SAMSUNG ML-1710, it worked perfectly all day March 7 and failed to work March 8 after restarting in the morning. I made all automatic updates on day March 7...

Chris

---

### Post by kristalsoldier on 2007-03-09
Same here with Epson Stylus 3850DX!

---

### Post by Chris11 on 2007-03-09
theres a other thread on the same issue: 

[http://www.ubuntuforums.org/showthread.php?t=380432&highlight=printer](http://www.ubuntuforums.org/showthread.php?t=380432&highlight=printer)

Chris

---

### Post by BrowneR on 2007-03-09
thanks for digging around guys and pulling up that bug report.

there's a debdiff posted on launchpad that appears to solve the issue so it wont be long before this is resolved.

in the meantime i've downgraded libgphoto to the previous version (2.2.1) and that's got me up and running again.

---

### Post by commonplace on 2007-03-09
> **BrowneR said:**
> 

in the meantime i've downgraded libgphoto to the previous version (2.2.1) and that's got me up and running again.

How can I do this (Ubuntu 6.10)? I desperately need to print and I'm in the same boat as everyone else. Any help would be greatly appreciated! Thanks.

/Kevin

---

### Post by Trsnrtr on 2007-03-09
> **commonplace said:**
> How can I do this (Ubuntu 6.10)? I desperately need to print and I'm in the same boat as everyone else. Any help would be greatly appreciated! Thanks.

/Kevin

I had to delete my printer and then add it back.  I've had to do it twice now.  I think that i lose it if i reboot or something, because it's been working since my last re-install.

---

### Post by commonplace on 2007-03-09
Here's what I did to fix this (it's a workaround, and I'm not certain the longterm repercussions; maybe someone else can chime in as to what this is affecting exactly -- all I know is, it made it so I could print again). From the terminal:

> sudo gedit /etc/group

Look for the line that starts with "plugdev".  At the end of the line, add a comma and "cupsys" (no quotes). My line looks like this ('tracey' and 'kevin' are users on the box in question):

> plugdev:x:46:haldaemon,kevin,tracey,cupsys

Note that, of course, you don't want to just duplicate the line above, as it's specific for my setup. Just make sure you add the ",cupsys" part at the end and save the file. That did it for me. I don't think I even had to restart CUPS, but if you need to, from the terminal:

> sudo /etc/init.d/cupsys restart

Hope this helps someone!

/Kevin

---

### Post by kwarip on 2007-03-09
Thanks Kevin
I had the same problem with a SAMSUNG ML-1610. 
Now my printer is OK!
Thanks again
:guitar: 
kwarip

---

### Post by vyruss on 2007-03-09
> **commonplace said:**
> How can I do this (Ubuntu 6.10)? I desperately need to print and I'm in the same boat as everyone else. Any help would be greatly appreciated! Thanks.

/Kevin

I just went to synaptic, selected libgphoto2-2 and libgphoto2-port0, and then Package -> Force Version. Chose the older one. Applied, done :)

But according to the bug report I posted some posts back, this is known and I guess it will be fixed very shortly. In order to make sure your printing keeps working until then, choose those two packages and Package -> Lock version (so they don't get updated with the broken version again).

---

### Post by marklid on 2007-03-10
Just clicked on the update notification icon, updated installed replacement libgphoto2-2 package, rebooted (don't know if this stage was necessary) and it's all sorted now !

---

### Post by heffo_j on 2007-03-10
Yep, that's the offending file. It has been noted as abug and the authors have ben busy fixing it.

Regards
John

---

### Post by kristalsoldier on 2007-03-10
My printer (Epson Stylus DX 3850) is now working. I uninstalled the  libgphoto2-2 file, reinstalled it (did not force the reinstall of the older version)...all this via synaptic. Rebboted and it works!

Thanks guys!

---

### Post by stucky on 2007-03-10
I love this community. Simple search and everything's working great. Thanks everyone.

---

### Post by luke411 on 2007-03-12
Same here with Brother HL-1440. I did the update for the time change and now can't add a local printer. NICE!!!!!

---

### Post by luke411 on 2007-03-12
Thanks guys. That did it for me too. I had to reboot and I **did ** lock the packages down afterward like someone thoughtfully suggested. Maybe they should add this to a sticky post until they get the problem worked out. It took me forever to find this thread.

---

