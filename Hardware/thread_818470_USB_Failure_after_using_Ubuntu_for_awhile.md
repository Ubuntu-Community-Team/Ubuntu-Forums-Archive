---
title: "USB Failure after using Ubuntu for awhile"
date: 2008-06-04
forum: Hardware
---

### Post by dapps2k on 2008-06-04
Whenever I'm on Ubuntu for awhile, the mouse stops working.  Clicking gets no response and it doesn't move whatsoever.  Replugging it doesn't do anything either.  At this point, all my other USB devices are still working, but eventually they'll begin to stop working.  I noticed that once replugging in the USB devices, they don't receive any power from the port and typing in lsusb in the terminal results in the terminal window hanging.  Attempting to reboot or restart X would only cause Ubuntu to hang as well.  I can only turn off the computer with hard shut downs.

Usually this happens when my CPU fan works at 100% before dropping down its speed.  I'm currently using a Acer Aspire E360 desktop.  This problem is really preventing me from doing any good work on Ubuntu.

---

### Post by Unix_Slayer on 2008-06-05
> **dapps2k said:**
> Whenever I'm on Ubuntu for awhile, the mouse stops working.  Clicking gets no response and it doesn't move whatsoever.  Replugging it doesn't do anything either.  At this point, all my other USB devices are still working, but eventually they'll begin to stop working.  I noticed that once replugging in the USB devices, they don't receive any power from the port and typing in lsusb in the terminal results in the terminal window hanging.  Attempting to reboot or restart X would only cause Ubuntu to hang as well.  I can only turn off the computer with hard shut downs.

Usually this happens when my CPU fan works at 100% before dropping down its speed.  I'm currently using a Acer Aspire E360 desktop.  This problem is really preventing me from doing any good work on Ubuntu.


The only problem I see on mine, is that the flash drive every now and again resets. Causing the mouse to freeze for like two seconds, Then everything is fine. I haven't found anything that commands a reboot.

---

### Post by stoodleysnow on 2008-06-05
Check the capacitors on your motherboard...
Are they bulging, bent or splurging material?
If so, that is the reason.:neutral:

---

### Post by 2WhEElTeRRoRisT on 2008-06-05
This sounds exactly like the problem I am having as well. When I plug my mouse into the usb it just freezes randomly it seems, but when I use my ps/2 adapter it doesn't seem to have an issue. Just like he said I can't even get ctrl+alt+backspace to work, it just shows the background and hangs there. I haven't noticed it with anything else, but the only other thing I am using through usb is a hard drive that has its own power supply. I never had this issue until I switched to 8.04.

---

### Post by dapps2k on 2008-06-05
> **stoodleysnow said:**
> Check the capacitors on your motherboard...
Are they bulging, bent or splurging material?
If so, that is the reason.:neutral:

The computer's only a year old and I haven't seen any bulging or bent capacitors when I opened it up.  If it were a serious hardware problem, then I would've noticed it doing something in Windows as well.

---

### Post by Unix_Slayer on 2008-06-06
> **dapps2k said:**
> The computer's only a year old and I haven't seen any bulging or bent capacitors when I opened it up.  If it were a serious hardware problem, then I would've noticed it doing something in Windows as well.


It's not the circuit board.

---

### Post by dapps2k on 2008-06-08
Anyone?  This is a real serious problem for me since I need to get programming work done and having the mouse keep dying on me is not helping me.

---

### Post by Unix_Slayer on 2008-06-08
> **dapps2k said:**
> Anyone?  This is a real serious problem for me since I need to get programming work done and having the mouse keep dying on me is not helping me.

Do you have another USB port open? Try plugging it in another spot. If it's a hub, move it somewhere else. Not to another open port in the same hub.

---

### Post by dapps2k on 2008-06-08
Replugging into another port doesn't do anything and I don't have a USB hub.

---

### Post by Unix_Slayer on 2008-06-09
> **dapps2k said:**
> Replugging into another port doesn't do anything and I don't have a USB hub.

Did that system come with a SD card reader? I have a hunch.

Like this ==> Generic 2.0 Reader-CF USB Device
              Generic 2.0 Reader-MS USB Device 
              Generic 2.0 Reader-SD USB Device 
              Generic 2.0 Reader-SM/xD USB Device


I'm getting more complaints like this:

Problems with my Acer Aspire E360 freezing..?
My Acer Aspire E360 continuously crashes and freezes. I thought the problem was related to the hard drive, as there are two of them, yet the larger of the two has nothing on it. When I ctrl+alt+delete and look at the system usage, it is almost constantly at 100%. I have tried defragmenting and cleaning up some useless files, as well as going through some of my system processes to delete some unnecessary ones. Has anyone had this problem? Should I just try moving all of my data from the smaller hard drive to the empty bigger one?

    * 1 year ago

---

### Post by dapps2k on 2008-06-09
> **Unix_Slayer said:**
> Did that system come with a SD card reader? I have a hunch.

Like this ==> Generic 2.0 Reader-CF USB Device
              Generic 2.0 Reader-MS USB Device 
              Generic 2.0 Reader-SD USB Device 
              Generic 2.0 Reader-SM/xD USB Device


I'm getting more complaints like this:

Problems with my Acer Aspire E360 freezing..?
My Acer Aspire E360 continuously crashes and freezes. I thought the problem was related to the hard drive, as there are two of them, yet the larger of the two has nothing on it. When I ctrl+alt+delete and look at the system usage, it is almost constantly at 100%. I have tried defragmenting and cleaning up some useless files, as well as going through some of my system processes to delete some unnecessary ones. Has anyone had this problem? Should I just try moving all of my data from the smaller hard drive to the empty bigger one?

    * 1 year ago

Why, yes I do have an SD card reader.  Windows has the same exact description as the one you posted.

Although I never had problems as severe as crashes or freezes, are you thinking that the multi-card reader is a source of the problems?

---

### Post by Unix_Slayer on 2008-06-09
> **dapps2k said:**
> Why, yes I do have an SD card reader.  Windows has the same exact description as the one you posted.

Although I never had problems as severe as crashes or freezes, are you thinking that the multi-card reader is a source of the problems?

Yes.... Windows handles the faults better in that respect. Linux deals with the USB faults in a way different way. For instance.... I had a bad wire connected to my 7 port Belkin USB hub. Anything I plugged into it would not be found. Then when I would start X11, or shut it down. The screen would be full of USB fault errors running in the backround. I changed the wire that connected it to the motherboards USB, and it stopped. Sure enough, I checked the wire with a meter. Was not good. I checked one end of the wire, and it was worn. So you might not think this would be a problem, and in Windows it doesn't really show. Except if you plugged in a USB drive in Windows, and moved files over to it. If you found errors in the data, or on the drive. You would be scratching your head. USB ports can freeze your system, and cause interruptions with other USB devices. You have to remember that there is 5 volts of current running through it at all times. How old is that Laptop, and did you buy it new? It might be something you have plugged into it, or another USB device that is causing the noise. Or maybe even something you upgraded it with. Like a bad memory module could do it as well. To knock the latter off the list, you should use the memtest from the grub menu, and see if they are ok. Then you can cross that off your list.

---

### Post by dapps2k on 2008-06-09
I bought this desktop at least a year ago.  I'll try removing some USB devices (and the flash reader) and see if one of thems causing faults.  I don't exactly have  a voltmeter or anything to check it with, though.

As for the memtest, I actually used it last night and didn't get any errors.

---

### Post by Unix_Slayer on 2008-06-09
> **dapps2k said:**
> I bought this desktop at least a year ago.  I'll try removing some USB devices (and the flash reader) and see if one of thems causing faults.  I don't exactly have  a voltmeter or anything to check it with, though.

As for the memtest, I actually used it last night and didn't get any errors.

Something is causing a current drop, to make the mouse faulter. If your ps/2 is working without a hitch, I would blame it on that specific mouse. Try another USB mouse and see if it happens.

---

### Post by dapps2k on 2008-06-10
I've also went ahead and upgraded to 8.04 from 7.10, so I'll give you a heads up if the problem occurs again.

---

### Post by Unix_Slayer on 2008-06-10
> **dapps2k said:**
> I've also went ahead and upgraded to 8.04 from 7.10, so I'll give you a heads up if the problem occurs again.

Ok man.... Have a good one.

---

### Post by dapps2k on 2008-06-12
Haha, I *was* going to say that I think it's all fixed in 8.04, but as I was typing the message, the problem came back again...

I think it's a general USB failure than just the mouse since I found out that whatever device is being active when the CPU fan turns on and off would be the first one to fail.  So if I was typing a message when the CPU fan went to 100% speed and down again, the keyboard would fail first, not the mouse.

---

