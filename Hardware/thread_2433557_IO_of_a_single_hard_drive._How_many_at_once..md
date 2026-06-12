---
title: "IO of a single hard drive. How many at once."
date: 2019-12-20
forum: Hardware
---

### Post by Tadaen_Sylvermane on 2019-12-20
Single hard drive shares over nfs. I use it to store media. How many separate media centers could pull at the same time before I run into trouble. Average file size 1gb

---

### Post by TheFu on 2019-12-21
> **Tadaen_Sylvermane said:**
> Single hard drive shares over nfs. I use it to store media. How many separate media centers could pull at the same time before I run into trouble. Average file size 1gb

It depends.

What sort of HDD?
What sort of HDD-Controller?
What sort of network connection for the server?
What sort of network connection for the clients?
What sort of network switching, routing, firewalls between the clients and server?
Is the server a raspberry-pi v1 or a Ryzen 9?
Are they getting the same file concurrently, synchronized or different files on opposite sides of a slow, portable, 2.5inch, USB2 disk?
Is any transcoding involved for different clients?
Are any connections over the internet?
What protocol is being used to access the storage?  DLNA, CIFS, NFS, something else?  CIFS is known to have stuttering problems in many media center setups.

Out of all that, find the slowest connection, slowest client and run the numbers.  Be certain NOT to confuse MBps and Mbps. Be extremely careful with any units.

It depends.

In general, 2-3 clients getting content from a recent, amd64 computer, using a 3.5inch SATA HDD, over a GigE LAN without firewalls will be fine.  Some home routers have DLNA servers built-in and support connecting USB2 storage. These work fine for 1-2 clients, though I'd never connect a router in that configuration to the internet too. I own a router like that, but use it as a WiFi AP for guests.

It depends.

Do some testing using iperf3, bonnie++, and run the numbers for your specific setup.  Make a theory, test it.

---

### Post by Tadaen_Sylvermane on 2019-12-25
Ok maybe I asked the wrong question. According to DD right now I am reading at 129MB per second from my snapraid pool. 117MB write speed on a single file. Only writes I really have to worry about are MythTV recordings. Everything else is one and done. Pretty sure it's sequential as that is all I really am worried about. I suppose it doesn't matter which disk specifically since everything runs through mergerfs. My question I guess is more about seek times. 

My average movie filesize is 1gb over 2 hours. This works out to .14MBs or 7.14 streams per meg. 129MBx7.14 = 921 active file "streams" at once.

I have a lot of trouble buying that number. Can't believe a standard 5400 rpm drive can do that. At 4-6 machines I am so far under it doesn't even register. Not even hitting the 1MB a second mark. Even with all the overhead and seek times it should be a spec of dust on the measurement. Did I do the math correctly?

* EDIT * I know I'm not streaming specifically. Just unsure of the right word to use. I'm not transcoding or anything, nothing but an NFS share from the pool.

---

