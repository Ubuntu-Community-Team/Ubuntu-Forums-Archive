---
title: "Compatibility issues with ASUS Transformer Book Flip TP500L"
date: 2015-03-03
forum: Hardware
---

### Post by FaWzY86 on 2015-03-03
I've been an Ubuntu user since 8.10 and I've installed it either as my primary OS or dual boot it alongside Windows with numerous desktops, laptops and netbooks and I've never had any issues whatsoever.

Today I bought an ASUS Transformer Book Flip TP500L and I was planning to install Ubuntu as its primary OS, weirdly, once I booted it I had all sorts of issues possible with the drivers.
1. GPU: Both the Intel 4400 and the nVidia 840M did not register and the screen started so dim and I couldn't change the brightness no matter what.
2. Network: It couldn't even detect the wireless modem on board, and thus no wi-fi access.
3. Touch pad: It did not register as well as if it didn't exist, no pointer movement or button functions or anything.
4. Screen orientation: I'm not sure if this specific feature is present in Ubuntu or not to be honest, but whenever I flipped it the OS didn't recognize the change in orientation, which means issues with the g-sensor.

Those are the main issues I've faced, which rendered the OS unusable, though strangely enough, the touch screen worked perfectly.

I've then went ahead and installed Windows 8.1 and everything worked just fine, so it's not a hardware issue, and I've scoured the internet looking for Linux drivers for it to no avail, also couldn't find any solution.

I really wish I could receive any help possible because I don't wanna be stuck with Windows.
Thanks in advance!

---

### Post by Mark Phelps on 2015-03-03
Responses ...

1. Could be Nvidia Optimus technology.  Look for information on Bumblebee to get this working.

2. Network: Need to run "lspci" and look for the information on the wireless chip.  You can use that info to browse the Networking section to see what other folks have done to get that chip working.  May have to resort to using NDISWrapper.

3. As with networking, once you have info on touchpad device, you can search this section looking for info on that.

4. Could be very hard to fix.  Once had a 1st-gen Tablet with rotating screen.  Was able to get screen rotation working only by using scripts that were tied to keyboard presses.  Never able to get autorotation to work.

---

