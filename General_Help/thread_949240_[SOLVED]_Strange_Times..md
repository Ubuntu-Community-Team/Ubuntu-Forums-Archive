---
title: "[SOLVED] Strange Times."
date: 2008-10-16
forum: General Help
---

### Post by matdombrock on 2008-10-16
Hello,
I'm having some strange issues with my internet today, I was hoping that you guys could shed some light on them. 

I am using an airport extreme and dsl internet though wave cable (a local company I think). Whats weird is that the airport light is green (that means good to go :]) and my computer says I have a full internet connection. Yet every time I try to load a web page I get the typical "cannot connect" page. 


On my mac (which controls the airport)it gave me some sort of "mac-ish" error about how I don't have an IP address.

If any one has an idea as to whats happening I would be delighted to hear it!



Also, Does this sound like my ISP might have cut our connection? Because I might have been running some watched torrents as of late. 
(We get our cable from them too and it still works.)



Thanks for reading!

---

### Post by wfp on 2008-10-16
I would try to unconnect your modem first for about 30 Seconds then plug in back in. See if that helps. You could be right also that your isp is just down for the moment.

---

### Post by jerome1232 on 2008-10-16
ok well from my quick google search Airpot Extreme = Mac's Wifi Router

To me it sounds like the green light on the Airport Extreme means it's got a WAN connection (internet)

That message on your mac about not getting an ip says LAN problems to me (the connection between the computer and router)

I would first try deleting the network out of your keychain and then reconnecting to your Wireless network (you know what your passphrase is right?)

And look out for various forms of interference (are you next to your fridge or something else large and metal/or has magnets?)

---

### Post by Ocxic on 2008-10-16
I'm an apple tech.. 
Power cycle the airport extreme(turn off and back on after waiting 10 sec.)
check your network IP settings, (apple menu -> system preferences -> network ->
(10.5/leopard)
Airport (on left) -> click advanced -> TCP/IP tab
(10.4/tiger)
Show menu -> airport

Make sure you have an IP address that is not 192.254.x.x (if you do the Airport is not giving your computer an IP, and it's a issue w/ the extreme)
the router IP adress should be that same as your IP but the last number will be 1 
(ex: IPv4: 10.0.1.10
netmask: 255.255.255.0
Router: 10.0.1.1)
Also check the DNS section and make sure there is either nothing set or it's set to the IP of the router.

if your still having issues, try connecting your computer directly to your modem and turn Airport OFF and reboot the computer.
if that works call 1-800-MY-APPLE and they'll get you going w/ your extreme, make sure you mention that the Internet works when you connect directly to the modem that will get you to the wireless department much quicker.

---

### Post by matdombrock on 2008-10-16
Thank you for such an indepth post Ocxic! However my internet seems to be working again. That was so odd. my freind that lives up the street (same isp) had his internet working perfect all day yesterday.

---

