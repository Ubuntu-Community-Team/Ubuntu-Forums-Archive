---
title: "Motorola H17 Bluetooth Ear-piece"
date: 2010-10-26
forum: Hardware
---

### Post by Joshua on 2010-10-26
I just got a Motorola H17 Bluetooth ear-piece for my phone and I was hoping I could set it up as an audio input/output device to use with Google Voice or some other VOIP system.  Anyone know how to do this?

---

### Post by Joshua on 2010-10-27
I don't know what happened, but it looks like it works now.  I installed the "PulseAudio Device Chooser" application from the software center (it auto installed lots of other stuff, too), but I wasn't sure how to configure it.  So I closed the device chooser windows and went back to the regular volume control icon in Gnome.  Under Sound Preferences, the Motorola H17 just popped up in the input and output tabs.  After I chose it, my speakers went silent and I could make crystal clear calls from the Google Voice web page.

Oh, before I did all of that, I had to sync it with the Bluetooth application under System -> Preferences.  But I didn't have any problems there.  I'm using the Cirago USB Micro Adapter for Bluetooth 3.0.  I think the Model is BTA3310.

---

### Post by Joshua on 2010-10-27
Ok, sorry for the multiple replies, but I just realized I should add more info about my system in case anyone is researching either the Motorola H17 or the Cirago BTA3310 Bluetooth 3.0 USB Micro Adapter.  I couldn't find anything on either of these in the Ubuntu Forums.  Please let me know if there is some other place I should post this to help track Ubuntu hardware compatibility.

I think the relevant stuff from "uname -a" is:
Kernel: 2.6.32-25-generic #45-Ubuntu SMP x86_64

I'm running Gnome and Ubuntu 10.04 (Lucid Lynx).

Also I've added the Medibuntu repositories from "http://packages.medibuntu.org/" to my package source list though I don't think that has anything to do with getting this stuff working.

---

