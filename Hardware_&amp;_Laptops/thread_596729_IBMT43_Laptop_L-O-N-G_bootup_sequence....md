---
title: "IBMT43 Laptop L-O-N-G bootup sequence..."
date: 2007-10-29
forum: Hardware &amp; Laptops
---

### Post by bphunter616 on 2007-10-29
I've installed release 7.10 on my IBM T43 laptop.  Previously running 6.10, I notice the bootup/startup sequence seems to take an incredibly long period of time to complete.  No errors or issues displayed.  Same occurs whether or not I run the proprietary ATI video drivers (currently I am not) and all is fine.  Seems to crawl prior to loading the wireless drivers, then once engaged...  screen becomes active.  Any steps I can take to adjust?  Or do I wait for updates to arrive?  GREAT product by the way!

---

### Post by seanhvw on 2007-10-31
Having same issue. Have you managed to find a fix for it?

---

### Post by bphunter616 on 2007-10-31
No fix yet.  Noted bootup sequence takes just over 121 seconds.  Re-installed Ubuntu looking for any issues in the process.  Did note that the GNOME daemon reported an issue that may affect display, etc.  Further googles on that indicates a possible issue with xserver-xorg.  But I can't find anything else on the subject.

---

### Post by mperry on 2007-10-31
On my T40 thinkpad, it also takes a long time.  I switched to the first virtual console to see what it was thinking about and its looking for a image to restore from after a hibernate event it appears on my laptop.  I have not had time to look more; but this process seems to take about 35 seconds and then it launches the regular boot process which takes about the same amount of time.

You may want to shift over to a virtual console and see what its trying to do.  In my case, I still need to solve it but the boot times are roughly three times as long with this release.

---

### Post by cadamr on 2007-10-31
Open the file at /etc/network/interfaces (i think). Make a backup first!
It should have interface entries for stuff like lo, eth0, eth1, wlan0, ... comment out (add # to the beginning of the line) all the entries except the ones for "lo".  

Make sure your network devices still work when you reboot. Good luck.

---

### Post by seanhvw on 2007-11-01
Okay I changed the resolution in the usplash.conf to 1024x768 and that fixed the issue. Now I just need to fix my freezing issue....  Thanks fot your help.

Sean :)

---

