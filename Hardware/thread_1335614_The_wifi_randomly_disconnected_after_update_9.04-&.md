---
title: "The wifi randomly disconnected after update 9.04-&gt;9.10"
date: 2009-11-23
forum: Hardware
---

### Post by smenik on 2009-11-23
Hi all,
I have the problem of randomly disconneted of my wifi after i was update my ubuntu from 9.04 to 9.10.
My wifi device is: Intel Wifi Link 5100

How can I determinate the problem, it seems that problem with new drivers. I am the nub in the linux. Can somebody help me please?

My notebook is acer 8930g
Thanks

---

### Post by coffeecat on 2009-11-23
I have a laptop with the Intel WiFi Link 5100 and I have found the wireless to be as stable in 9.10 as it was in 9.04. So it is unlikely that there is anything wrong with the driver in 9.10. The only difference is that I did a fresh install of 9.10 whereas you did an upgrade.

So - a few things to look into. Are you sure you are booting into the Karmic 2.6.31 kernel, and not the Jaunty 2.6.28 one? After a dist-upgrade, you will still have a fall-back kernel from the previous version. I don't know whether that would cause the problem, but it is something to check.

Also - make sure that something hasn't happened to your network coincidentally at the time you upgraded. Have you other computers connecting to your router? Are they OK? Another cause of random disconnects is from interference when a new wireless network is set up by a neighbour using the same channel as you. Try changing the channel on your wireless router and see if that helps.

---

