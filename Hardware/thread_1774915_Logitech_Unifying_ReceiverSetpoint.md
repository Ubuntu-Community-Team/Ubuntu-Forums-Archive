---
title: "Logitech Unifying Receiver/Setpoint"
date: 2011-06-03
forum: Hardware
---

### Post by smcrossman on 2011-06-03
I posted a while back in Absolute Beginner Forum; I'm not sure if I just didn't get things out clearly or if it wasn't the proper place.  I thought I was probably just missing some understanding of installing or accessing something. I am very, very new to Ubuntu and after a couple of decades of Windows indoctrination I'm only slowly beginning to recall some of the very ancient BASIC and such I used way back when.

I am currently using a Logitech Performance Mouse MX and a K250 Keyboard. Both are wireless USB using Logitech's unifying receiver. I have a receiver in my main PC and in my netbook. Both are currently dual boot Win7 & Natty.  The pc is 64 bit and the netbook 32 bit.  Previously (when windows only) I could switch back and forth by turning one off, or unplugging the receiver and then pairing up with the one I was getting ready to work with.

Currently this requires me to boot into Windows and run the unitying program then reboot into Ubuntu.  The keyboard isn't that big of a deal, but the mouse is.  Although I'm starting to get much better with the touchpad (on the netbook). Given enough time this might not be such an issue. 

**Is there a way to get Ubuntu to recognize and allow me to configure this mouse?  I do know that the receiver is being identified by name but as an unknown button in Device Manager.  If one of the batteries die then I have to go into Windows to re-establish pairing. If they are paired then Ubuntu picks them up as basic USB keyboard/mouse.

**I also really miss the full functionality of this mouse. Is there some way to get it to operate as more than just a basic USB mouse?

---

### Post by Pipmeister. on 2011-06-18
Basically the way the unifying system works from my experience is that receivers, rather than a particular computer, are paired with devices. If you simply use one receiver and move it between computers then you should not have to use SetPoint in windows to re-pair the device, no matter what computer you are using. However if you pair your mouse with a different receiver you will have to run the software again if you want to pair it back again. I don't know of a way to pair devices with the receiver in Ubuntu. If you want to set up the extra buttons on your mouse try HIDpoint: [http://www.hidpoint.com/hidpoint/features/features.html](http://www.hidpoint.com/hidpoint/features/features.html) , I haven't actually used it personally but the features look good.

If anyone knows a way of pairing devices in Ubuntu I would be very much appreciative as I am in a very similar situation.

---

### Post by smcrossman on 2011-06-18
Thanks for your response!  Never occured to me that moving the receiver might work...I thought it was somehow paired to the machine as well.  I'll give that a try and see.  Can't hurt anything.

So far I've come up with 2 thoughts one which I couldn't get to work at all.  That is using Wine and installing the software that way.  It was a no go...would error out within seconds of starting. But I just read how you have to take windows drivers and split them into parts and use cerain parts to load them into Ubuntu even using Wine.  Or copy them from the sys file they are stored in in Windows.  Haven't explored how that might translate for the unifying software which is now built into the setpoint program.

My other thought was to try using a VM.  If pairing it in Windows is all it needs for Ubuntu to recognize it then doing the same thing in a VM should work as well. I've not managed to get a VM created yet to try it though.

Keep me posted if you find anything.  and anyone else out there who is familiar with the system please chime in.  IF you aren't familiar with the unifying software you can download the Setpoint driver/control system off the Logitech page if you feel like playing to see if you can get it to work.

---

### Post by taorn on 2011-11-16
Hi there

I just made the configuration througth a Windows xp VM machine and works nice (Maverik and Virtualbox Windows XP VM).

Basically you needs to install logitech software on your VM and then let the VM gain control over the unifying receiver (making rigth click on the virtualbox status bar and selecting the unifying receiver tagged as Logitech receiver [###]).

After that XP will recognice the new hw and let you access to their configuration (by the logitech sw) and you should pair a new device. When you make the pair, the mouse seems to work weridly on the VM, due the fact that the reiver is no longer over ubuntu control but VM contol (movenet fails but buttons works).

When you close your VM ubuntu will take control over the receiver and you'll have your both devices with the same unifying receiver.

P.S. At the begging of the process I had my keyboard and their receiver on my pc and I was adding a new mouse, so in all the I had two mouses... at the end I'd removed the old one...

---

### Post by nightbeast on 2012-01-14
For the earlier idea of the devices being paired to the receiver and all you must do is move the receiver over to the new machine. I did so and am confirming that it works.

---

