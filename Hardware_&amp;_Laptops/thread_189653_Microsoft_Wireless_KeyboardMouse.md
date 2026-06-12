---
title: "Microsoft Wireless Keyboard/Mouse"
date: 2006-06-05
forum: Hardware &amp; Laptops
---

### Post by m3pz on 2006-06-05
Hello, I have an issue with my Microsoft Wireless Comfort Keyboard/Mouse set on Dapper Drake. In Windows XP I can use the two by simply connecting the wireless receiver using the USB cable; however, on Ubuntu, I have to connect both the USB and PS/2 cables. (This is not recommended by Microsoft in their [quick-start guide]("http://download.microsoft.com/download/3/3/0/330b80b7-1fd2-4c92-a864-89b0ee4fe728/Wireless_Desktops.pdf"))

The problem is, Windows no longer recognizes the keyboard/mouse when the PS/2 connector is connected.

Is there a way to make Ubuntu recognize the keyboard/mouse via USB only?

Thanks in advance.

---

### Post by eto on 2006-06-05
I too am having this same problem.

After looking at the wireless controller that is plugged in via USB cable, the lights aren't fully on, and are just blinking very lightly.

I would fathom a guess that the USB ports aren't getting enough power through the cable...   (e.g. the driver has turned off the usb power source perhaps?)

I don't know how I would go about fixing this though.. ):

---

### Post by m3pz on 2006-06-06
I didn't realize the blinking, but now that you mention it, yes... the function key light flashes, and when the connect button is pressed, the other two buttons flash in a somewhat bizzare way.

By the way, this particular hardware works just great on the current live CD version of Mandriva.

---

### Post by m3pz on 2006-08-13
Sorry, bump, as I have not yet been able to fix it. I would appreciate any insight into the matter.

Thanks,

m3pz

---

### Post by chazzy on 2006-08-13
I've connected the new 6000' version using both Ps2 connections rather than just the USB, as I found just the USB caused a freeze on boot up. Works fine in this configuration on Ubuntu, and Windows.

---

### Post by ac4000 on 2006-09-10
I see you've fixed this with the new keyboard, but just in case someone else finds this thread and has the same old problem, here's something that *might* help:  If your BIOS isn't set to handle legacy USB keyboards, sometimes they don't work properly.  I know mine had that problem, back when I used Windows, actually; but with it set to legacy mode, everything is fine.  I don't know if that would address every problem with the symptoms you describe, but it's easy enough that it's worth a shot (well, except that it requires a restart--and who restarts anymore?).

---

### Post by tommcd on 2006-09-10
Did you try: system>preferences>keyboard>layouts, then click the 3 dots (...) next to keyboard model? You can scroll down and select "microsoft wireless keyboard". 
Hope this helps.

---

