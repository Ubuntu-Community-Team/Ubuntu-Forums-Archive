---
title: "WLAN failed after update"
date: 2009-06-24
forum: Hardware
---

### Post by Raff1 on 2009-06-24
Heya! My WLAN stopped working after my last (automatical/suggested) upgrade of ubuntu and reboot. I had also changed my language settings to english (USA) and updated the folder names. Changing back the system language made no difference however. Should I try to roll back to an earlier package (in that case, how?) or should I try to find out whats wrong with my WLAN-connection/hardware directly (again how..)?

Thanks!
\Raff1

---

### Post by Raff1 on 2009-06-30
Okey, I have solved part of the problem but I can't find any wifi networks though..

I used [this guide]("http://ubuntuforums.org/showthread.php?t=942195") to get this far.

[IMG]http://folk.ntnu.no/hrafnmar/bilder/pic1.jpg[/IMG]

At least I am able to see the grayed out "Wireless Networks" now. However I cant see any wireless networks as I used to.

I get this output from "lshw -C network":
```
*-network               
       description: Ethernet interface
       product: 82541GI Gigabit Ethernet Controller
       vendor: Intel Corporation
       physical id: 7
       bus info: pci@0000:06:07.0
       logical name: eth0
       version: 05
       serial: 00:13:72:66:e6:53
       width: 32 bits
       clock: 66MHz
       capabilities: bus_master cap_list ethernet physical
       configuration: broadcast=yes driver=e1000 driverversion=7.3.20-k2-NAPI firmware=N/A ip=129.241.56.185 latency=32 mingnt=255 module=e1000 multicast=yes

```

I then tried the "Connect to Hidden Wireless Network..." option in the pic above:

[IMG]http://folk.ntnu.no/hrafnmar/bilder/pic2.png[/IMG]

After some time of trying to connect i finally get prompted for the password again:
[IMG]http://folk.ntnu.no/hrafnmar/bilder/pic3.png[/IMG]

I can repeat this step all day if I want to. I don't, however, so I made this post instead. ;) (If I show the password it is not on the form I typed it however, but I dont think that matters.)

I am pretty sure something is wrong when I don't see the network (which is not hidden!) and looking it up manually under hidden networks was pretty much bound to fail...

So I hope my drivers at least are OK, but how can I make the networks show again? I know the network it self is OK, my brother finds it readily.

Regards,
Raff1

---

### Post by Raff1 on 2009-07-14
I repeated the steps in the [guide]("http://ubuntuforums.org/showthread.php?t=942195") and this time I made sure to NOT tu the steps in [COLOR=Red]red[COLOR=Black] as I am not using *Intrepid*. After a reboot my wireless network card was grayed out again, but after I switched the wireless hardware-switch the wireless networks showed up as before! I am on wireless this very moment. Joy!

*Issue solved.*

Regards, Raff1
[/COLOR][/COLOR]

---

