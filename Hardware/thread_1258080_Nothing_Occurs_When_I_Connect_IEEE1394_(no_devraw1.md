---
title: "Nothing Occurs When I Connect IEEE1394 (no /dev/raw1394)"
date: 2009-09-04
forum: Hardware
---

### Post by Spaceman Spiff on 2009-09-04
Hey guys, I am working on installing an digital video adapter that is connected by firewire to my Ubuntu distribution.  Currently, the adapter is drawing power from the firewire, and from the manual, I know that the adapter is working okay (it has a blinking light, which is blinking in the right way.)  I'm running out of ideas on what to search for, this is what I have done so far.

So the first thing I did was I installed libraw1394-8 and libraw1394-dev, I needed both for the library I will be using.  From there I plugged in my device and tried out some sample code, and right away the library did not detect any devices in the 1394 port.  I went to /dev and sure enough there wasn't a node(?) labeled raw1394, which as I understand is what it would appear under.  I researched how to make it appear and came up with this [[COLOR="Blue"]_topic_[/COLOR]]("http://ubuntuforums.org/archive/index.php/t-2792.html").  tail -f /var/log/message however gives me nothing when I disconnect/reconnect my adapter.  After further searching, I found out about dmesg, using it I see comments about ieee1394...

```
[83634.676087] 
ieee1394: Node changed: 0-01:1023 -> 0-00:1023
[83634.676096] ieee1394: Node paused: ID:BUS[0-00:1023]  GUID[0007480040403252]
[83637.736018] ieee1394: Node removed: ID:BUS[0-00:1023]  GUID[0007480040403252]
[83640.804045] ieee1394: Error parsing configrom for node 0-00:1023
[83640.804110] ieee1394: Node changed: 0-00:1023 -> 0-01:1023
[83641.910696] ieee1394: Node added: ID:BUS[0-00:1023]  GUID[0007480040403252]

```

I did a lot more research about "Error parsing...", but I decided it can't be that important.  Everyone who had a problem with that error, had multiple other errors, while I have this positive message "Node added: ..." ...

At this point, I'm at a loss at what to do.  I'm tentative on whether to simply create my own node(?) like the person in topic I linked, thinking that I might not be at that step yet.  Basically, I would like to see some message in my /var/log/messages relating to my firewire port.

Any thoughts are appreciated, thanks for your time.

P.S. I also installed dvgrab, no change/nothing new.

---

### Post by Spaceman Spiff on 2009-09-07
Fixed - added dev1394 and video1394 to my /etc/modules

---

