---
title: "How to disable a cordless mouse"
date: 2006-10-03
forum: Hardware &amp; Laptops
---

### Post by ruleboy on 2006-10-03
Hi,

I'm new to Ubuntu, its quite nice, however I have a strange problem. I use a cordless keyboard and mouse, each has its own USB receiver, but the keyboard receiver is picking up signals from another mouse which is used on a different computer. This means Ubuntu is getting signals from TWO mice.

There seems to be no hardware solution to this, I could not get the mouse and keyboard to work on the same USB receiver. Under windows the solution was to disable the additional mouse in the Device Drivers application. 

Can I do a similar thing with Ubuntu?

Thanks, Tim.

---

### Post by ciscosurfer on 2006-10-04
Maybe purchase a corded mouse/keyboard?  

Or, move your computers further apart.

Unplug the other mouse when not in use.

---

### Post by ruleboy on 2006-10-04
Sorry, my question was, is there a way to disable a mouse (or any device) in Ubuntu in a similar fashion to what is possible in Windows?

In Windows you open the device manager, select the mouse (or any other device), right-click and disable. The only device mananger I found in Ubuntu did not seem to have any management functionality, it was more like a device viewer...but alas I'm new to Ubuntu so probably I'm looking in the wrong place.

Thanks.

---

### Post by ciscosurfer on 2006-10-05
I've never had a need to mess with the settings in Device Manager, although from the looks of it, on the Advanced Tab, you may be able to alter the info for a particular device thereby preventing it from loading.  There probably is another way to do this; please keep seaching around, but also try my method.  Sorry I'm not more helpful.

---

### Post by ruleboy on 2006-10-05
That last tip about the Device Manger was actually quite helpful, however in the meantime the Keyboard receiver decided to forget about the other mouse and so the problem solved itself...for now.

What I think the solution could be is, in the device manager:
1/ find the usb device for the mouse receiver
2/ goto advanced tab
3/ select info.capabilites
4/ delete input.mouse from the list of values

or something similar to that. otherwise redirecting or filtering the device file (dev/input/...) could also stop mouse messages from making it to the X system, where I assume they are interpreted.

Now where was I...ah yes ](*,) 

cheers.

---

### Post by ciscosurfer on 2006-10-05
I'm glad that tip helped you out...seems like things worked themselves out for the time being. :D

---

