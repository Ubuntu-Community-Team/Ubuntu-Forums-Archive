---
title: "Script to mitigate Raspberry Pi USB Issues"
date: 2021-08-11
forum: Hardware
---

### Post by bouncethebox on 2021-08-11
Reaching out in the hopes someone could help me out.  I'm running Ubuntu 20.04 on a few Pi4 Model B units and I can't seem to fix the USB issues I am having with external drives.  I've tried replacing hardware and cables with listed hardware that is supported, quirks, everything; they still drop offline with an I/O Error.  The Pi's seem to be fine for about 4-6hrs before tossing the I/O errors, so I was thinking maybe I could script something that that reboots the Pi's every 3 hours.  In addition, just before rebooting, stop a specific service, shut/close the usb ports with a hub and a drive attached via uhubctl to ensure the Pi comes back up smoothly and doesn't hang enumerating drives.  As the system is starting, opening the ports back up again and start the service again.  

Script to mitigate USB 3 I/0 Errors:

1. Just before rebooting, the script would stop the **acme.service** running and using two specific USB ports.
2. Then, execute the **uhubctl** command '**sudo** **uhubctl -a off -l 1-1 -p  2**' and '**sudo** **uhubctl -a off 1-1 -p 1**' to shut off USB ports 1 and 2 
3. Pi would reboot, and upon coming back up as part of startup, execute as root '**uhubctl -a on -l 1-1 -p  2**' and '**uhubctl -a on -l 1-1 -p  2**' to turn the USB ports back on
4. Start the acme.service script.

If anyone could help me out, that would be great and it would really be appreciated!

---

### Post by TheFu on 2021-08-11
Why not use **autofs** instead?  Then the storage is only mounted when it is actually used.
[https://help.ubuntu.com/community/Autofs](https://help.ubuntu.com/community/Autofs)

I have to say, I don't have any external storage connected to any r-pis here.  They are media playback devices and get media from NFS or DLNA servers on the network.  r-pi aren't meant to be general purpose computers. They are built to be used by kids learning about computers and programming.  I/O is the weakest part of the pi architecture, though the v4 made huge improvements.

And one more thought - are the USB storage devices externally powered?  That's always been a huge problem. Always use USB HDD storage that has external power plugs. That applies to desktops, server, Pis, whatever.  Flash and SSDs can be different, but they bring other issues.

---

