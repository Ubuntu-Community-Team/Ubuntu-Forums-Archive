---
title: "Wifi an Acer Aspire 5315 - how!?"
date: 2008-02-03
forum: Hardware &amp; Laptops
---

### Post by JustLikeFred on 2008-02-03
Dear Ubuntu pros! 

I am trying to move from OS X to Ubuntu - mostly for "political reasons" - but man, this is NOT easy! Please help! 

YES - I have READ tens of pages about making this work, WITHOUT any luck. ;( 

I have an Acer Aspire 5315 with Atheros AR5006EG 802.11 b/g (according to lshw -C network. However the network is UNCLAIMED (whatever that means). 

  *-network UNCLAIMED
       description: Ethernet controller
       product: AR5006EG 802.11 b/g Wireless PCI Express Adapter
       vendor: Atheros Communications, Inc.
       physical id: 0
       bus info: pci@0000:06:00.0
       version: 01
       width: 64 bits
       clock: 33MHz
       capabilities: cap_list
       configuration: latency=0

What do I do? Use ndiswrapper, MadWifi, or some other magic? 

I hope someone will kindly give a good guidance that even a novice like I can understand. Thanks! :) 

Best regards, 
JustLikeFred

---

### Post by tensop on 2008-02-05
Are you sure you searched? check my posts, i made one regarding this wifi card. And the method i posted works in both hardy and gutsy.

---

### Post by tesseract85 on 2008-02-05
I would go to synaptic and download ndiswrapper. 

pull up a terminal and cd to where you have the windows drivers extracted to.

install the drivers from the terminal via command: ndiswrapper -i (nameofthedriver).inf

If everything goes okay and the command: ndiswrapper -l
lists everything okay. 

then type: modprobe ndiswrapper

then: ndiswrapper -m
followed by: ndiswrapper -ma

should be good to go after that. 

* note: DO NOT MOVE OR DELETE THE DRIVER AFTER YOU HAVE INSTALLED IT!!!!*

---

### Post by scoober on 2008-02-05
hi 

sorry to hijack, but I have the same problem on an Aspire 1360.  I had previously tried another method using ndiswrapper I found on this forum, and a solution involving acer_acpi, neither of which worked.

using your method, when I ndiswrapper -l, it gives m an invalid driver message.  The driver I am using is neti2220.inf (downloaded from the acer website).

Am I doing something wrong?

---

### Post by JustLikeFred on 2008-02-07
Dear tensop! 

Finally my WiFi works - thanks to your explanation! 

Yes, I had seen your post before, but at that time some of your explanations didn't make any sense to me (me being a newbie). 

Also, let me add that when you are new to Ubuntu and Linux and see ten different explanations on the net about how to solve your problem, you have NO way of knowing which solution is the best. 

There should be some kind of quality stamp and all the good explanations should be gathered in one place. Maybe I should not just post such an idea, but use my initiative to make it happen. ;) 

However, now it works - thank you! 

Now I just need to make make mic and WebCam work and Ubuntu is perfect! 

Best regards, 
JustLikeFred

---

### Post by tensop on 2008-02-10
Hmm, my 5315 does not have a webcam :)

Though, it came with a 1.86ghz cpu instead of a 1.73

---

