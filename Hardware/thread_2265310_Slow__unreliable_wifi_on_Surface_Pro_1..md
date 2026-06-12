---
title: "Slow / unreliable wifi on Surface Pro 1."
date: 2015-02-14
forum: Hardware
---

### Post by Knightwise on 2015-02-14
Hi everyone.

I just installed the 14.04 version of Ubuntu on my Surface pro 1 yesterday and so far most things are working fine.

I do have an issue with the wifi not working "reliably"

- From time to time, at bootup, the wifi won't connect to any wifi network. It SEES the networks in the network manager and when I punch in the correct WPA key it tries to connect, but fails.  This happens with several wifi networks. The problem can be resolved after a reboot (but sometimes I have to try one or two times)

-When the wifi is connected it is sometimes slow (like its dropping packets or something). 

Does anyone know if i need to upgrade the drivers or do something else to get this working properly  ? Because for the rest this is an awesome machine.

---

### Post by kerry_s on 2015-02-14
i've found sometimes you need to delete the wifi history(name & password) then reenter it like it was the first time setting up. after 1 or 2 times you shouldn't have anymore issues.
personally i think its some kind of saving issue, for some reason it don't save right some times.

---

### Post by kerry_s on 2015-02-14
forum hickup, double post

---

### Post by Knightwise on 2015-02-14
Hi,

I've fired up wireshark and taken a look at the traffic the Surface is generating and there are a lot of dropped packets. I've experienced this issue before when I had installed ubuntu on my macbook pro. It turned out it was an incompatibility with my Wifi routers chip and the BG/N network settings on the router. The problem was resolved when I switched my router back to G only. So just to be sure i've now hooked up my surface to a different wifi router (on BG only).

The issue where you have to delete your known wifi networks seems also to help a little bit (i've just tried that and now the Surface connects immediately to the second BG only router).

I'll mess around with it a little more and do some more tests in wireshark to see how the packet drops are doing.

---

### Post by Knightwise on 2015-02-15
I've done a scan with Wireshark and I still see some package drops here and there but overall the connection to the wifi hotspot seems to work.
I'm not getting awesome speeds (about 11mbit on Speedtest.net) 
A buddy of mine suggested that I disable the power management on the card [https://itechscotland.wordpress.com/2011/09/25/how-to-permanently-turn-off-wi-fi-power-management-in-ubuntu/](https://itechscotland.wordpress.com/2011/09/25/how-to-permanently-turn-off-wi-fi-power-management-in-ubuntu/)  So perhaps that also might help. I'll try that one later on today and let you know how it went.

---

### Post by Knightwise on 2015-02-17
Ok , i've done the power management hack .. so disabling powermanagement on the card also increases the performance.

---

### Post by jeremy31 on 2015-02-17
So what wifi chipset is it```
lspci -nnk | grep -iA2 net
```

I wouldn't be surprised if it is intel

---

### Post by Knightwise on 2015-02-17
No response from that command. But its a Marvel card or something. It obviously uses telepathy to communicate with routers rather then TCPIP

---

### Post by cnnr-dhrty on 2015-04-14
When it's doing that dropping packets thing, turn off bluetooth. BAM! it goes away.
This is at least true for my Surface Pro 1 running 14.10

---

