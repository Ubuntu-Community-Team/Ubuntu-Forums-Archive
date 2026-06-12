---
title: "cdrom won't mount after kernel upgrade!"
date: 2008-05-27
forum: Hardware
---

### Post by krlhc8 on 2008-05-27
Hardy upgraded the kernel to 2.6.24-17-generic, which was sweet.  Yet my cdrom fails to function!  I click on Places>>CDROM1 and I get an error message that reads: 

Cannot invoke CheckForMedia on HAL: org.freedesktop.DBus.Error.UnknownMethod: Method "CheckForMedia" with signature "" on interface "org.freedesktop.Hal.Device.Storage.Removable" doesn't exist

Any suggestions?

---

### Post by krlhc8 on 2008-05-27
I have no clue what happened, but it works now.  

Now, Ubuntu can't read DVDs.  MoviePlayer can't read DVDs either, yet VLC can.  Could someone help with this?

---

### Post by krlhc8 on 2008-05-27
I found the solution:
[http://tombuntu.com/index.php/2008/05/13/enable-commercial-dvd-playback-in-ubuntu/](http://tombuntu.com/index.php/2008/05/13/enable-commercial-dvd-playback-in-ubuntu/)

It didn't work right away, then soon after, I got an update from the update manager, wanting to install libdvdcss2.  So I recommend installing this in the synaptic package manager after following the guide in the tombuntu.com url above.

---

