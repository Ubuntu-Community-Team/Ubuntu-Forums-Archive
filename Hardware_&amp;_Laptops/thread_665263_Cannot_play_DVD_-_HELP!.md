---
title: "Cannot play DVD - HELP!"
date: 2008-01-12
forum: Hardware &amp; Laptops
---

### Post by ragashiwala on 2008-01-12
I am trying to play store bought dvd and cannot, no matter what i try to do.  I've Googled until i dropped and tried many suggestions to no avail.  I even tried to logon as root to see if it was a permissions issue but it's not.  I am trying to use mplayer, totem, vlc and xine.  The computer detects the drives and the movies show up on the desktop (7.10) but i cannot play them. There is always a read error-and this is from 2 separate drives. It plays mpeg format movies off a burned dvd but not store bought ones...it always gives a read error.  Any help would be appreciated!

---

### Post by Kevbert on 2008-01-12
Try this link
[http://www.ubuntugeek.com/install-mplayer-and-multimedia-codecs-libdvdcss2w32codecs-in-ubuntu-710-gutsy-gibbon.html#more-279]("http://www.ubuntugeek.com/install-mplayer-and-multimedia-codecs-libdvdcss2w32codecs-in-ubuntu-710-gutsy-gibbon.html#more-279")

You may find you get an error with 
sudo apt-get install w32codecs libdvdcss2
If you get an error just try
sudo apt-get install libdvdcss2

---

### Post by jan quark on 2008-01-12
read through this official documentation 
if it does not help post again :)

[https://help.ubuntu.com/community/RestrictedFormats](https://help.ubuntu.com/community/RestrictedFormats)

---

### Post by ragashiwala on 2008-01-12
I wish it were so easy.  every thing i did according to the link that you posted the message came back that all of the codecs were installed and the newest version, as well as the program itself.  when i go to mplayer and try to play dvd, it says cannot read dvd://1.  Perhaps it is not looking for the dvd in the right place?  but the same thing happens in Kaffeine, and in totem, it says are you trying to play without libdvdcss?  but everything seems to be installed...very frustrating.

---

### Post by SonicSteve on 2008-01-12
I don't know if this will work for you but it did it for me. 

Using the synaptic-package manager, I installed the Kaffeine-Gstreamer package. I don't know why but it then allows me to use the Kaffeine-xine engine properly.
I also installed the totem-xine package which uninstalls totem-gstreamer. 
Hey a bit weird but it seems to have done the trick. Now Totem plays DVD's, and Kaffeine doesn't go un-responsive.


Once the package is installed I tried both engines using Kaffeine, settings>player engine. I found that gstreamer didn't have menu support.

I hope this helps.

---

### Post by ragashiwala on 2008-01-12
I tried what you said...it turns out that I had the totem-xine package installed, and i installed the kaffeine-xine package.  When I start totem, no luck same error, and when I start kaffeine, also error, with both engines.  it's interesting that the errors are different with either engine.  
The error with Kaffeine-xine engine:
04:53:44 AM: xine: cannot find input plugin for MRL [x-nautilus-desktop:///CD-ROM/DVD-ROM Drive.volume]
04:52:16 AM: xine: cannot find input plugin for MRL [dvd://]
04:52:16 AM: xine: input plugin cannot open MRL [dvd://]
04:52:16 AM: xine: found input plugin : DVD Navigator

The error with Kaffeine-GStreamer:
dvdreadsrc.c(229): gst_dvd_read_src_start (): /play/source:
DVDOpen(/dev/dvd) failed: Operation not supported
any other ideas? I appreciate all of the help!!  This one's got me stumped!

---

### Post by SonicSteve on 2008-01-12
Hey I found this in another thread that had a very similar error. I'd give it a try.

sudo apt-get install libdvdread3 libdvdnav4 libdvdplay0 llibdvdcss2
from this thread

[http://ubuntuforums.org/showthread.php?t=482436&highlight=input+plugin+cannot+open+MRL](http://ubuntuforums.org/showthread.php?t=482436&highlight=input+plugin+cannot+open+MRL)

---

### Post by polmir on 2008-01-12
**ragashiwala** --- display:

```
 cat /etc/fstab
```

---

### Post by Crenfinkle on 2008-01-12
Is this a fairly new Sony DVD by any chance? They use a different encyption algorithm than older DVDs.

---

