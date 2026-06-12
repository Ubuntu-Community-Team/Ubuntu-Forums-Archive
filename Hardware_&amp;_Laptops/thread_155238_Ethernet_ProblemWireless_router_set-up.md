---
title: "Ethernet Problem/Wireless router set-up"
date: 2006-04-04
forum: Hardware &amp; Laptops
---

### Post by beaverjnt on 2006-04-04
I am a newbie so please bear with me. 

I am attempting to set up a wireless router to work with my Earthlink DSL service. My PC will be wired to the router and and my wife's Windows 2000 PC will access the wireless. 

Yesterday I got ahead of the game, connected the modem to the router (Linksys Wireless-G) and attempted the "one-step set-up" button on the router. This of course didn't work. Later I communicated with a linux expert friend who told me how to go about accessing the web to control and set-up the router. 

So, I go home all excited last night to get everything rocking. I did check with Earthlink to see if there was anything specific I should be doing before switching to the router and they said before installing the router that I should change my UHP modem from PPPoE Mode to Bridged Mode, and gave me the url to go to do so (172.16.0.254/config). When I did that I got an error message, Connection was refused when attempting to contact 172...

Curious, I tried going to my homepage ([www.startribune.com](www.startribune.com)) and got a message that it could not be found. Figuring that I am having a connection problem I double checked all cables (wall to modem, modem to PC) and that was all fine. I then in various orders re-booted the PC, the modem, reset the modem, unplugged everything and plugged it all back in, etc., all to no avail.

On the modem itself the DSL Sync light was solid green, the PPPoE light was on at the beginning of the process and then not later on, and the DSL Traffic light would flash green. The Ethernet Traffic and Ethernet link lights never did anything. This leads me to believe that the problem lies between the modem and the PC.

I did check System---->Admin---->Networking to check the Ethernet connection.
Connection -- Ethernet connection is active

Under Default Gateway Device the drop down menu offers eth0 which wouldn't stay chosen, if that means anything. I did try deactivating and activating the Ethernet connection to see if that would enable me to connect and it wouldn't.

As one more check, I started Firestarter, to see in any traffic would ping my system, thus showing me that I was connected. When I clicked Start I got an eror message, failed to start the device eth0 is not ready. Please check your network device settings and make sure your Internet connection is active.

Under Network

Device                           Type
eth0                              Internet not active
sit0                               IPv6 Tunnel not active

So, I am at a loss. Networking reports that the connection is active when it's obviously not. Is there a way to force it to restart? Are there reports that I could run in terminal to diagnose what's happening?

 Is it possible that when I had the router set-up at lunch yesterday and I pushed the "one-step set-up" button on the front of the router that I fried the ethernet card (I hope not) and that is causing the problem?

Thanks for any advice anyone can offer.

John

---

