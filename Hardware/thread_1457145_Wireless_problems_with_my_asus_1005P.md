---
title: "Wireless problems with my asus 1005P"
date: 2010-04-18
forum: Hardware
---

### Post by newbmica on 2010-04-18
Hi! I've been googling for a week now without any success, I just bought myself an Asus 1005P netbook and I've had a few problems but most of them are fixed after some googling but the real problem that remains is the wireless network.

I've tried this guide [http://ubuntuforums.org/showthread.php?t=1390856&highlight=1005p](http://ubuntuforums.org/showthread.php?t=1390856&highlight=1005p) wich is ndisgtk and winXP driver but ndisgtk tells me that the hardware isnt present.
I've allso tried [https://wiki.ubuntu.com/HardwareSupport/Machines/Netbooks](https://wiki.ubuntu.com/HardwareSupport/Machines/Netbooks) and [http://martinml.com/en/linux-on-asus-eeepc-1005p](http://martinml.com/en/linux-on-asus-eeepc-1005p) and none of them gives me working wireless, I've tried two more guides wich one inclued backports something that is installed, the backports fixed the microphone problem though.

To be honest I'm out of ideas and google seem to be to, I really hope some smart person can help me get it to work :) it's annoying to use my mobile broadband when I'm at home.

Thank you in advance.

---

### Post by robertfullarton on 2010-05-09
Hi I'm using a 1005p right now on wifi. I used the guide at [http://martinml.com/en/linux-on-asus-eeepc-1005p](http://martinml.com/en/linux-on-asus-eeepc-1005p)

Maybe try working thru the guide again, you may have missed something..

---

### Post by Linker101 on 2010-06-18
> **newbmica said:**
> I've tried this guide [http://ubuntuforums.org/showthread.php?t=1390856&highlight=1005p](http://ubuntuforums.org/showthread.php?t=1390856&highlight=1005p) wich is ndisgtk and winXP driver but ndisgtk tells me that the hardware isnt present.

I had the same problem when I used this guide, but I fixed it. The wording is a little unclear. It says to extract "netathw.inf" from the zip file, but in actual fact you need the other files too. When I extracted the whole zip file and then followed the guide it worked.

Good luck. It took me a whole day searching the internet and trying everything I could find to get wireless working.

---

