---
title: "Ubuntu troubles - inlcuding a showstopper"
date: 2005-11-03
forum: General Help
---

### Post by mwillems on 2005-11-03
Hi all,

I love 5.10. But it has a few problems, and one real showstopper. I have it running an a 2.4 GHz P4 machine with lots of RAM; dual boot with XP, and p[rety standard hardware. STANDARD desktop install. Radeon 9100 video card with 128 MB RAM. 1 GB system RAM.

Small problems:

- I try to print to my Samba printer from the browser: BANG, browser exits. 

- I cannot get MP3 and AVI. MPG etc drivers to work. This is a MUST for my system!

- Sometimes after nooting Monitor shows just brown screen, nothing else.

- Various other little things I won't bother you with.

CRITICAL:

Randomly (typically overnight) the system locks up completely. I have to reset to get it going again. Not sure what I can do to analyse further?

Michael

---

### Post by mwillems on 2005-11-03
Oh and I checked the logs: when the unit locks up in th emiddle of the night, there is NOTHING In the logs:

Nov  2 22:38:01 ws-office gconfd (root-3527): Resolved address "xml:readonly:/var/lib/gconf/defaults" to a read-only configuration source at position 7
Nov  2 22:46:01 ws-office gconfd (root-3527): GConf server is not in use, shutting down.
Nov  2 22:46:01 ws-office gconfd (root-3527): Exiting
Nov  2 23:05:41 ws-office -- MARK --
Nov  2 23:25:41 ws-office -- MARK --
Nov  2 23:45:41 ws-office -- MARK --
Nov  3 00:05:41 ws-office -- MARK --
Nov  3 00:25:41 ws-office -- MARK --
Nov  3 00:45:41 ws-office -- MARK --
Nov  3 01:05:41 ws-office -- MARK --
Nov  3 01:25:41 ws-office -- MARK --
Nov  3 01:45:41 ws-office -- MARK --
Nov  3 02:05:41 ws-office -- MARK --
Nov  3 02:25:41 ws-office -- MARK --
Nov  3 02:45:41 ws-office -- MARK --
Nov  3 03:05:41 ws-office -- MARK --
Nov  3 03:25:41 ws-office -- MARK --
Nov  3 03:45:41 ws-office -- MARK --
Nov  3 04:05:41 ws-office -- MARK --
Nov  3 04:25:41 ws-office -- MARK --
Nov  3 04:45:41 ws-office -- MARK --
Nov  3 05:05:41 ws-office -- MARK --
Nov  3 05:25:41 ws-office -- MARK --
Nov  3 05:45:41 ws-office -- MARK --
Nov  3 21:50:13 ws-office syslogd 1.4.1#17ubuntu3: restart.

...i.e. it hangs after 5:45 and I reset it (hardware) at 21:50.

---

### Post by az on 2005-11-03
[QUOTE=mwillems]Hi all,

I love 5.10. But it has a few problems, and one real showstopper. I have it running an a 2.4 GHz P4 machine with lots of RAM; dual boot with XP, and p[rety standard hardware. STANDARD desktop install. Radeon 9100 video card with 128 MB RAM. 1 GB system RAM.

Small problems:

- I try to print to my Samba printer from the browser: BANG, browser exits. 

- I cannot get MP3 and AVI. MPG etc drivers to work. This is a MUST for my system!

- Sometimes after nooting Monitor shows just brown screen, nothing else.

- Various other little things I won't bother you with.

CRITICAL:

Randomly (typically overnight) the system locks up completely. I have to reset to get it going again. Not sure what I can do to analyse further?

Michael[/QUOTE]


Do you have any firefox extensions installed (you using firefox?)
Are you using ndiswrapper for wireless?  
Look on the wiki (RestrictedFormats in the UserDocumentation) to learn how to install those codecs.

---

### Post by mwillems on 2005-11-03
>>>Do you have any firefox extensions installed 

No

>>> you using firefox?

Yes

>>>Are you using ndiswrapper for wireless?  

No: wired

>>>Look on the wiki (RestrictedFormats in the UserDocumentation) to learn how to install those codecs.

So much conflicting advice and it only half helps. I am still on it though!

---

### Post by RAOF on 2005-11-04
About multimedia:  Tried [this]("http://help.ubuntu.com/starterguide/C/faqguide-all.html#sect-music-and-movies")?
help.ubuntu.com seems up-to-date, complete, and correct.  Gstreamer0.8-plugins-multiverse is your friend :)

The random overnight freezes seem odd.  Does it ever freeze while you're at the computer (ie: could it be a particular 3d screensaver that kills it)?

---

### Post by aclaunch on 2005-11-04
One thing to check: if you are using xscreensaver, on the "Advanced" tab is a section for power management. Make sure that those options are unchecked (they are enabled by default). I have  a desktop machine and when I first installed Ubuntu I would get up in the morning and the machine was locked up. I finally figured it out and disabled the PM settings and all is well.

Good Luck,
Alan

---

### Post by thechitowncubs on 2005-11-04
What GTK theme are you using?

---

### Post by mwillems on 2005-11-04
I am using the default theme, whichever that is. I have done VERY LITTLE customisation to the box, in fact.

-Michael

---

