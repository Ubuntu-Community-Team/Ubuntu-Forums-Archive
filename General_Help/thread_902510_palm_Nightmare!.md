---
title: "palm Nightmare!"
date: 2008-08-27
forum: General Help
---

### Post by woodsyboredom on 2008-08-27
I have found this fix for J-pilot 

[https://help.ubuntu.com/community/PalmDeviceSetup](https://help.ubuntu.com/community/PalmDeviceSetup)

and still no go! 

now when I tfy to sync I get this strange message on J-Pilot:
J-Pilot: sync PID = 9881
J-Pilot: press the hotsync button on the cradle or "kill 9881"

Does anyone have any idea how to fix this? Or what is going on?

:mad:

---

### Post by GrnFrag on 2008-08-27
that's the message i always get from jpilot.   Kill is typed in term to kill process's, 9881 is the current number of the sync process for jpilot (i think).   

I believe the message means, Sync.  If Sync fails, Kill 9881, or kill the sync process.   

try this.   without Jpilot or gnome-pilot running hit sync on your palm.   then, in terminal, type dmesg.   post the last 4 lines or so in here.
while the palm is still trying to connect, type lsusb   post that here too

---

### Post by woodsyboredom on 2008-08-27
Okay thanks. here's dmsg.


[44762.165318] usb 6-3: USB disconnect, address 2
[77805.868923] e1000: eth0: e1000_watchdog: NIC Link is Down
[78838.888309] e1000: eth0: e1000_watchdog: NIC Link is Up 100 Mbps Full Duplex, Flow Control: RX/TX
[78838.888314] e1000: eth0: e1000_watchdog: 10/100 speed: disabling TSO
[78838.890520] ADDRCONF(NETDEV_CHANGE): eth0: link becomes ready
[78855.326370] eth0: no IPv6 routers present

and here's lsusb

Bus 007 Device 006: ID 413c:2003 Dell Computer Corp. 
Bus 007 Device 005: ID 08bb:2900 Texas Instruments Japan PCM2900 Audio Codec
Bus 007 Device 004: ID 03f0:5c11 Hewlett-Packard 
Bus 007 Device 002: ID 0409:005a NEC Corp. 
Bus 007 Device 001: ID 0000:0000  
Bus 006 Device 001: ID 0000:0000  
Bus 005 Device 001: ID 0000:0000  
Bus 003 Device 001: ID 0000:0000  
Bus 002 Device 001: ID 0000:0000  
Bus 001 Device 001: ID 0000:0000  
Bus 004 Device 003: ID 413c:3012 Dell Computer Corp. 
Bus 004 Device 001: ID 0000:0000

---

### Post by GrnFrag on 2008-08-27
i don't see a a palm connecting there.   it should show something like this
[HTML]every1@MoonRock:~$ lsusb
Bus 002 Device 001: ID 0000:0000  
Bus 001 Device 009: ID 0830:0050 Palm, Inc. Palm M130
Bus 001 Device 001: ID 0000:0000  
every1@MoonRock:~$ 
[/HTML]
was the palm still trying to connect when you ran those commands?   Remember, you have to hit your hotsync button then run the command while the palm is trying to connect?   IS it a palm?

---

### Post by woodsyboredom on 2008-08-27
Yes I ran the command when ther hotsync was running. hmmm. It is a palm and older one, an M515, I see so the problem is likely with the Palm cradle's Usb coonection than something in the J-pilot or Evolution configuration.

---

### Post by GrnFrag on 2008-08-28
seems like it.  do other usb devices show up in that list for you?   i can see drivekeys and my ipod that way

---

