---
title: "64bit Intrepid HP DV9000 DV9201ca -- install notes"
date: 2009-01-18
forum: Hardware
---

### Post by greenwom on 2009-01-18
I'm just posting this to go over what worked and what didn't on my 
dv9201ca.  This notebook is from the dv9000 series, there is a ton of models in the series with similar specs.  So I went to install the 64 bit version of intrepid and here's the story.

I already had a dual boot setup on this with Vista.   There's tons of steps on shrinking the ntfs partion.    Usually when you do this you'll have to run a check disk when you reboot.  I've never had a problem.

** Burned a 64 bid Intrepid live cd - no special boot options

** no wireless out of the box -- I forgot manufaturer so lspci reveals:
```
03:00.0 Network controller: Broadcom Corporation BCM4311 802.11b/g WLAN (rev 01)
```so I went to the restricted manager  installed the Broadcom STA wireless driver and restarted the machine 

-- Wireless then works fine at 54MBS *You need to watch the speed of connection sometimes this driver has dropped my connection to 1 or 11mbs in the past.  I'll keep an eye on it.  There's a script you can run at startup or you can add a line in one of the /etc config files although I can't remember  but for now it works and that's a good thing.*
The line consisted of something like this ```
iwconfig eth1 rate 54MB
```
The network-manger connects but shows no bars in the applet.  Right click shows the info.  No cares about that for the moment.  I'll look into a fix later.

**  Back to restricted drivers for the Nvidia settings.
I tried to activate the Nvidia graphics driver (rev 177) but ran into a bug: it wouldn't let me activate the driver.  I did a reboot and added the extra repos from synaptic then an "apt-get update".  Then back into the restricted driver manager and for some reason it's really slow almost like it's locked up....  just let it ride it will catch up.  Not sure that caused the delay but it worked.
**  Then reboot and the driver is installed.

Ran ekiga to see if the **webcam** worked... with v4l and v4l2... 
cheese showed no camera found -- nothing  so here's **lsusb** info
```
Bus 001 Device 002: ID 05ca:1810 Ricoh Co., Ltd 
```
I don't use it right now so I'm not going to waste time.  I want to get it working so I can skype with the kids from work.  There's lost of posts on this forum as well as others that points to a dead link for the proper driver.  If I get around to it and find it I'll post the info.

Next came Flash -- There currently isn't a stable 64 bit version.  So I'm off to Adobe labs for the alpha 
[http://labs.adobe.com/downloads/flashplayer10.html](http://labs.adobe.com/downloads/flashplayer10.html)
grab that tarball.  This gives you the direct file that you need to copy over to all of the plug-in folders for the software that you use.
copy the libflashplayer.so file to  ```
/usr/lib/mozilla/plugins
```  so far so good.  Youtube worked.  Make sure you have firefox closed when your copying over the file.

Then I run this to configure laptop-mode```
 sudo apt-get install  laptop-mode-tools laptop-detect cpufreqd cpufrequtils

```
then check this file to see if you want to change anything
```
/etc/laptop-mode/laptop-mode.conf
```

Other thread links for this series 
[http://ubuntuforums.org/showthread.php?t=431815](http://ubuntuforums.org/showthread.php?t=431815)
[http://ubuntuforums.org/showthread.php?t=512059&highlight=hp+dv9000+thread](http://ubuntuforums.org/showthread.php?t=512059&highlight=hp+dv9000+thread)

So as of right now the problems are:
Network manager applet no showing status bars
The Webcam

What else to do?  Hope the notes help.

---

### Post by MikeDK on 2009-03-07
Just wanna say powernowd works just fine with the gnome-cpufreq-applet,

No need to install cpufreqd and cpufrequtils running on a DV9232eu

---

### Post by greenwom on 2009-07-13
Well I just dropped the 32 bit version of jaunty back on this machine...

Everything (minus webcam) working well

By the way these HP laptops stink...

cracked hinge recall (hp honored)
Blow out motherboard on board wireless not working... (HP will not fix)

No more HP's for me...

---

