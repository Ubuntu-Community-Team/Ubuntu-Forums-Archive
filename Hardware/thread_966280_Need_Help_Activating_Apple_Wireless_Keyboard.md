---
title: "Need Help Activating Apple Wireless Keyboard"
date: 2008-11-01
forum: Hardware
---

### Post by DaveBear on 2008-11-01
I just purchased a new netbook (the ASUS Eee PC 1000H) and Apple wireless keyboard and installed Ubuntu. I couldn't figure out how to make my keyboard work in Windows mode, and I have the same problem in Ubuntu.

I double-clicked the Bluetooth icon, and it shows two devices - my wireless keyboard and my MacBook Pro (laptop). When I select the keboard and click Forward, it says "Setting up new device...Pairing withi 00-1F-5B-fB-5F-49 failed." I wasn't able to pair it in Windows, either.

Does anyone know how to make it work?

Thanks.

---

### Post by aztechclan on 2008-11-03
I am running a fresh intrepic and I had a similar issue, turned out the problem is that Apple bluetooth keyboard doesn't like to pair with multiple devices and hates to re-pair.  Essentially, my keyboard was stuck in a pairing with OSX on my mbp and just plain refused to pair with the same mbp running under linux.

One symptom of this is that in the bluetooth manager, you will see 'YourName's keyboard' instead of the raw device mac address on the selection screen.  This means pairing is going to fail every time.

So!  I searched around and found people saying that removing the batteries from the keyboard for 15-30 min (ouch!) would sortof 'hard reset' the keyboard back to pairing friendly.  I did this, then the pairing worked on the first try.

Hope that helps, wish these keyboards could multi-pair.

---

