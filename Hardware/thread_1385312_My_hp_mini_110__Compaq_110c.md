---
title: "My hp mini 110 / Compaq 110c"
date: 2010-01-19
forum: Hardware
---

### Post by marty pain on 2010-01-19
I got this netbook the other day, pre-installed with Windows XP and with the 6 cell battery. I thought I would just make a quick thread to say how much I like it!

The 6 cell battery makes the back stick up twice the height of the front, which some may not like. When I first put the battery on I didn't like the look of it, but after I put my hands on it I liked it. Great typing position for me.

I installed UNR last night and very impressed with how well it works! out of the box everything worked apart from the wireless. Bluetooth OK, mic OK, web cam OK, all the Fn keys, switches and lights all work!

I had to install the propriety drivers for the broadcom wireless card, and after a re-boot the wireless was up and running. However, after the wireless was fixed, the bluethooth no longer functioned and mic didn't work.

The mic was an easy fix, following the fix on launch pad [https://bugs.launchpad.net/ubuntu/+source/bcmwl/+bug/385293](https://bugs.launchpad.net/ubuntu/+source/bcmwl/+bug/385293)

It seems however that the bluetooth cannot be fixed as the broadcom drivers conflict with the drivers running the bluetooth. The only way around it would be if someone created and new set of drivers for it (hint hint) or use non-propriety drivers if they exist (if they do please let me know!)

other than that the machine runs really well. There is a noticeable improvement in speed compared to using XP even with all the effects enabled.

The only other thing worth mentioning is that after re-opening the lid after closing it (after it suspends) the screen doesn't light up properly. You can just about make out the icons but that's it. Using the Fn keys to turn up the brightness wakes it back up. This isn't an issue for me as I have turned off the suspend on lid down as I'm not into it anyway.

Hope this helps anyone of thinking of getting one. I would defiantly recommend buying one!

Also, big thanks for UNR! I really like the interface and the way it just works. Massive thanks!:D

---

### Post by Palmerin on 2010-03-25
Hi Marty!

I'm in the same exact situation you were when you posted this, took it out of the box, loved the battery, keyboard is cool, installed UNR and just loved it. The problem is that I can't get the wireless to work. When I go to the manufacturer drivers config, there's nothing listed. I'm also pretty new to linux in general. Can you or anyone else around point me in any direction?

Cheers,

Palmer.

---

### Post by eznug on 2010-03-29
Hi, I have the HP Mini 110c and was looking for the same thing today.

Once UNR is installed go to "System" scroll down and click "Update Manager", however this require some sort of internet connection to get all the updates.

After you have run the update restart the computer as it will ask you to do.

Then go back into "System" and locate "Hardware Drivers" and there should be 2 options for you in there. B43(at least I think it was named that) and Broadcom STA Wireless Driver, choose the later STA driver and click "activate" and follow the instructions and it should be working, but the bluetooth will be disabled after doing this.

> **Palmerin said:**
> Hi Marty!

I'm in the same exact situation you were when you posted this, took it out of the box, loved the battery, keyboard is cool, installed UNR and just loved it. The problem is that I can't get the wireless to work. When I go to the manufacturer drivers config, there's nothing listed. I'm also pretty new to linux in general. Can you or anyone else around point me in any direction?

Cheers,

Palmer.

---

