---
title: "Palm Pilot and ttyUSB"
date: 2005-06-08
forum: Hardware &amp; Laptops
---

### Post by mariuss on 2005-06-08
Hi,

I keep trying to get my Palm Zire up and running with Ubuntu, no luck so far.

For some reason the ttyUSB* device does not show up no matter what. I connect directly to the computer, not through a USB hub.

I can connect a USB flash drive no problem. While it is connected I still don't see any ttyUSB* devices.

Any clues?

Thanks,
Marius

---

### Post by defkewl on 2005-06-08
I think you need a Palm Driver for that. The problem is Palm only makes it for Windows and Mac. I don't think that the newer version of Palm is compatible with Linux Palm Pilot software. CMIIW. I've tried it with my Tungsten T3 and it can't detect it. So I'm back using windows in order to connect to my Palm :)

---

### Post by Bob D. on 2005-06-08
The reason the devices do not show up is that they are only created *during* a HotSync. Then they disappear until the next HotSync. This is related to the use of udev in Ubuntu.
 
I've used the info in my post here: 
 
[http://www.ubuntuforums.org/showpost.php?p=158942&postcount=3]("http://www.ubuntuforums.org/showpost.php?p=158942&postcount=3")
 
to get my Tungsten T syncing with both Ubuntu and Fedora.
 
You may want to search the forums or Google on 'Zire' and 'Palm' or 'HotSync'....I've seen posts where folks have had to make some changes to the 10-local.rules file so it would see their device.
 
Good luck!
 
Bob

---

### Post by mariuss on 2005-06-08
Thanks for the help Bob, I could finally synchronize!

Before I posted this message I also added a 10-custom.rules file as specified in the Unofficial Ubuntu Guide:
[http://www.ubuntuguide.org/#configurepalmosdevices](http://www.ubuntuguide.org/#configurepalmosdevices)

I added the 10-local.rules as you suggested, the symbolic link to /dev/pilot, rebooted, and now it works.

I still can't see any /dev/ttyUSB*, but it works.

Marius

---

### Post by Bob D. on 2005-06-09
You're most welcome Marius, glad I was able to share some helpful info. :) 
 
Be well!
 
Bob

---

### Post by electroglas on 2005-06-23
Blah, Blah, Blah...

---

