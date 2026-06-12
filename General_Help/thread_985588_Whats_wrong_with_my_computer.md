---
title: "Whats wrong with my computer??"
date: 2008-11-17
forum: General Help
---

### Post by swoody on 2008-11-17
Ok, so I installed 8.10 (amd64) on my 64bit desktop where Vista is already installed (but I left 250GBs empty for Ubuntu). I installed it from a DVD that I burnt - I checked the md5sum and the disk for errors, and both were fine. It was installed through the live disc, and selecting "Install using largest continuous free space." 

1)When I restarted the computer it recognized my wireless card and connected to the network fine. Then after about 2 mins it disconnects from the network and I can't get it to reconnect to the internet at all. If I restart the computer its the same 2min story.

2)After the first time I restarted the computer it displayed a bunch of errors about the hard drive and then would start up in read-only mode. I think it was read-only as when it finally would load all the way I couldn't do anything with the computer without getting error messages about being unable to write to xxxxx file. 

3) I can't install the nvidea driver (although this may be related to #1). When I click on "download and install" it shows the process bar but doesn't show anything different when it goes back to the Hardware Drivers window.

Please help me out here guys! Any and all help is GREATLY appreciated!! :D Thanks in advance everyone!

---

### Post by jimbren on 2008-11-18
On issue 1, do you have security enabled on your network?  I would consider disabling your security and testing the connection.  Then you can re-enable and see what happens.  

For issue 2, did you defragment your hard drive in Windows before you installed Ubuntu?  Off the top of my head I would guess that there was a fair amount of fragmentation and now the system is having some problems with that.

---

### Post by anubhavrocks on 2008-11-18
Please post the output of following commands:

hwinfo --wlan
cat /var/log/syslog

---

